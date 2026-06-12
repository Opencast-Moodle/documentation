# Moodle Opencast JWT Authentication Guide

## How It Works (High-Level Overview)

The JWT authentication mechanism covers two primary user-facing touchpoints:

1. Resource Access: When the LMS directly requests protected media streams and static video files.
2. External Apps & Services: When a user accesses interactive external Opencast applications such as Studio, Editor, or the Annotation Tool.

JWT applies strictly to these two scenarios, primarily by appending an ephemeral `jwt` query parameter string to the outbound request. Opencast then intercepts and validates this token.

> ℹ️ Important Backend Distinction: Core backend administrative tasks-such as event creation, starting workflow, series and events listing, and background metadata updates etc. remain completely unchanged. They continue to run securely over standard API authorization channels using your existing API Username and Password configurations.

## Opencast Version Requirements

While Opencast has featured foundational JWT support for several releases, Opencast 18 introduced robust Access Control List (ACL) evaluation and dynamic role claim mapping. Opencast 19 further revolutionized this stack by significantly simplifying the internal Spring Security configuration.

To ensure full compatibility with modern cryptographic signing and simplified admin setups, it is strongly recommended to have Opencast 19 or newer when switching to JWT authentication.

---

## How to Configure JWT

Follow this step-by-step deployment guide to establish token authorization between your LMS and your Opencast instance.

### Step 1: Generate an Elliptic Curve Key Pair

First, you need to create a secure Private Key to paste into Moodle's administrative configuration settings. From that key, you will generate a matching Public Key formatted as a JSON Web Key (JWK) payload, which you will place in an accessible web path for Opencast and Octoka to read.

> ℹ️ **Note:** If you are already familiar with generating private keys via asymmetric elliptic curve signing algorithms and compiling them into `jwks.json` structures manually, you may skip this configuration step.

Instead of writing complex and error-prone native `openssl` terminal commands, you can use an interactive command-line utility to handle the cryptographic operations. Run the following command in your local terminal:

```bash
npx jwk-cli-tool

```

The tool will prompt you with an interactive text menu. Follow the questionnaire exactly as outlined below, ensuring you select **EC** (Elliptic Curve) as your core key type family:

1. **What would you like to do?**
* Use your arrow keys to select: `Generate new PEM key pair` and press **Enter**.


2. **Select the key type family:**
* Select **`EC`** (Elliptic Curve) and press **Enter**.


3. **Select the specific signature algorithm:**
* Select **`ES256`** (utilizing the `prime256v1` curve) and press **Enter**.
* *Note: While the tool supports other elliptic options like `ES384` or `EdDSA`, `ES256` is the recommended default for this integration.*


4. **Enter a file name prefix for your keys:**
* Type **`opencast`** and press **Enter**.



Once the PEM files are created, run the tool again (or continue the active prompt wizard) and select **`Generate JWK JSON files`** to convert those new keys into public JSON keys.

The utility automatically saves your resources into two clean local directories:

* **`keys/opencast_private.pem`**: Your raw private key file (used later in Step 6).
* **`outputs/opencast_public.jwk.json`**: The newly generated matching public key payload formatted as a standard JWK.

#### ⚠️ The JWKS Wrapper Requirement

There is a small structural catch here: Opencast's token authentication layer expects public keys delivered as a JSON Web Key **Set** (JWKS) array, whereas the tool outputs a single standalone JSON Web Key (JWK) object.

To resolve this, you must wrap your generated key inside a `keys` array wrapper. Create a file named **`jwks.json`** and structure it exactly like the template below, pasting the complete text block from your generated `opencast_public.jwk.json` file directly into the placeholder:

```json
{
    "keys": [
        { // This object should be replaced.
            "kty": "EC",
            "use": "sig",
            "alg": "ES256",
            "crv": "P-256",
            "x": "...",
            "y": "..."
        }
    ]
}

```

This final `jwks.json` file is what you will host on your server in Step 2.

### Step 2: Publish Your JWKS Endpoint

Host your newly generated `jwks.json` file on your LMS web server so it can be automatically fetched over HTTPS by external validators. It should resolve at a standard public location, typically matching a well-known path structure:

`https://{your-moodle-domain}/.well-known/jwks.json`


```bash

# Create the .well-known directory if it doesn't exist
sudo mkdir -p /var/www/html/.well-known

# Move and rename your public JWKS file there
sudo cp jwks.json /var/www/html/.well-known/jwks.json

# Set correct permissions so Nginx can read it
sudo chown -R www-data:www-data /var/www/html/.well-known
sudo chmod 644 /var/www/html/.well-known/jwks.json

```

Configure Nginx:

```bash
...
server {
    ...
    location /.well-known/jwks.json {
        default_type application/json;
        # Optional: Add CORS headers if external APIs need to fetch it
        add_header Access-Control-Allow-Origin "*";
    }
}
...
```


### Step 3: Install and Verify Octoka

Install and configure the [Octoka](https://github.com/opencast/octoka) validation proxy component on your Opencast delivery cluster node. Before proceeding, execute a configuration dry-run to ensure the proxy environment connects to your key infrastructure properly:

```bash
octoka check
# or
octoka run

```

### Step 4: Configure Opencast Spring Security

Update your Opencast cluster's internal security parameters by following the official [Opencast Spring Security JWT Configuration Guide](https://docs.opencast.org/r/19.x/admin/#configuration/security.jwt/#spring-security-configuration).

> Ensure that the Static File Protection option is fully active on your file-serving components. See [Securing Static Files in Opencast](https://docs.opencast.org/r/19.x/admin/#configuration/serving-static-files/#securing-static-files) for exact structural steps.

### Step 5: Provision the Unknown User Context in Opencast

When Opencast receives a stateless JWT request that does not map directly to a pre-existing local administrative account, it requires a fallback guest context to successfully initialize app frameworks like Studio or Editor.

Log into your Opencast Admin UI, navigate to the Users module, and provision a fallback record matching this exact structural data:

 Username: `unknown-jwt-user`

 Name: `unknown-jwt-user`

 Email: `no-mail@jwt.invalid`

 Roles: `ROLE_JWT_USER`, `ROLE_USER`, `ROLE_USER_UNKNOWN_JWT_USER`, `ROLE_STUDIO`, `ROLE_EDITOR`

### Step 6: Apply the Private Key within Moodle

Log into Moodle as an Administrator and navigate to the `tool_opencast` configuration page.

1. Enable `JWT` Authentication.
2. Select your corresponding Signing Algorithm (e.g., `ES256`).
3. Copy the entire raw text string from your `private.pem` file (generated in step 1) and paste it directly into the Private Key text area field.

Save your settings. Your Moodle instance is now fully configured to issue cryptographically signed, stateless tokens.

---

## Dynamic Claim Mapping: Permissions & Capabilities

The JWT integration relies on a tight mapping between native Moodle user capabilities and Opencast Access Control Lists (ACLs).

When an authenticated user views a player or fires up an application, Moodle packages their course environment attributes inside a custom array token parameter named `oc-roles`. Opencast parses this claim array and contrasts the values against the explicit permissions assigned to that video event, series, or playlist.

To mirror traditional LTI workflows seamlessly, the plugin translates Moodle capabilities into standard Instructor and Learner contexts:

- `tool/opencast:learner`

  - **Moodle Context**: Assigned to typical students, guests, or audited accounts inside a specific course page.

  - **Opencast Mapping**: Translates directly to the Learner role inside token claims.

  - **Granted Rights**: `read` access right only (grants video asset streaming/playback permission).

- `tool/opencast:instructor`

  - **Moodle Context**: Assigned to teachers, non-editing instructors, course creators, and platform managers.

  - **Opencast Mapping**: Translates directly to the Instructor role inside token claims.

  - **Granted Rights**: Joint `read` and `write` access rights (grants streaming playback, direct recording uploads, processing workflow execution, and interactive metadata modifications).

> ⚠️ Admin Note: Ensure that your global Opencast Series and Event ACL templates are updated to explicitly parse and grant permissions to these custom incoming `oc-roles` strings. If your backend templates are not monitoring these specific roles, users will trigger an unmapped `403 Forbidden` exception regardless of a successful cryptographic handshake. Keep in mind this ACL roles handling model may evolve in upcoming Opencast architectural updates.
