# Configuration of the Duplicate Workflow
To use the backup and restore functionality, you need to specify a duplication workflow within the Moodle settings. However, there is no out of the box workflow defined in Opencast, which allows, to duplicate a series.

## Own workflows
If you want to create your own workflow, here are the descriptions of the general restore process:

In the restore process, we first create a new opencast series for the new course. Afterwards, for each event UID of the
backup a 'duplicate' workflow is started, while the new series UID is given as a configuration parameter to the start workflow call. The variable, used to store the series ID, is 'seriesId'.
In our workflow definition example from above, the first workflow *lms-automated-duplicate* will duplicate the event and will start a new workflow for the new event. This second workflow *lms-publish-duplicate* then assigns the series of the new course to the new event.

In order to be able to select your duplicate workflow within Moodle, you need to assign the *'api'* tag to it, since the viable duplicate workflows are filtered by that.

## Important changes
Prior to version v4.1-r1 of the plugin, the following workflows must use "seriesID" instead of "seriesId". It is highly recommended/necessary to update these variables from "seriesID" to "seriesId" in your workflows if you are planing to use this feature with the latest version of the plugin.

#### Important Opencast database change
In addition to the steps above, if the above mentioned issue is applied to your system, then you might encounter the issue of unsuccessful duplication for old videos when using the new workflows with "seriesId", for that to be fixed, you have to manually perform the following SQL database queries against your Opencast database:

1. To make sure that "oc_assets_properties" table has any record of "seriesID":

`SELECT * FROM oc_assets_properties where property_name='seriesID';`

2. If the above query indicates that "seriesID" exists, you have to perform the following SQL query to delete it from the table:

`DELETE FROM oc_assets_properties WHERE property_name='seriesID';`

## Workflow examples
The workflow that is triggered by Moodle:

```
<?xml version="1.0" encoding="UTF-8" ?>
<definition xmlns="http://workflow.opencastproject.org">

  <id>lms-automated-duplicate</id>
  <title>LMS Upload aus dem LMS duplizieren</title>
  <tags>
    <tag>api</tag>
  </tags>

  <operations>

    <!-- Create the new events -->
    <operation
      id="duplicate-event"
      fail-on-error="true"
      exception-handler-workflow="partial-error"
      description="Duplicate Event">
      <configurations>
        <configuration key="source-flavors">*/source,*/prepared,*/search+preview,dublincore/*,*/player+preview,*/feed+preview,*/timeline+preview,smil/*,security/xacml+series</configuration>
        <configuration key="number-of-events">1</configuration>
        <configuration key="target-tags">+copied</configuration>
        <configuration key="property-namespaces">org.opencastproject.assetmanager.security, org.opencastproject.workflow.configuration</configuration>
        <configuration key="copy-number-prefix">Kopie</configuration>
      </configurations>
    </operation>

    <!-- Start new workflow -->
    <operation
      id="start-workflow"
      fail-on-error="true"
      retry-strategy="hold"
      max-attempts="5"
      exception-handler-workflow="partial-error"
      description="Start workflow on duplicate">
      <configurations>
        <configuration key="workflow-definition">lms-publish-duplicate</configuration>
        <configuration key="media-package">${duplicate_media_package_1_id}</configuration>
        <configuration key="seriesId">${seriesId}</configuration>
      </configurations>
    </operation>

    <!-- Cleanup the working file repository -->
    <operation
      id="cleanup"
      fail-on-error="false"
      description="Remove temporary processing artifacts">
      <configurations>
        <configuration key="preserve-flavors">security/*</configuration>
        <configuration key="delete-external">true</configuration>
      </configurations>
    </operation>

  </operations>

</definition>
```

The first workflow triggers this second workflow on the duplicated *mediapackage*.

```
<?xml version="1.0" encoding="UTF-8" ?>
<definition xmlns="http://workflow.opencastproject.org">
  <id>lms-publish-duplicate</id>
  <title>Publish a duplicate of an LMS upload</title>

  <operations>

    <!-- Apply the default workflow configuration -->

    <operation
      id="defaults"
      description="Applying default configuration values">
      <configurations>
        <configuration key="straightToPublishing">true</configuration>
        <configuration key="flagForCutting">false</configuration>
        <configuration key="flagForReview">false</configuration>
        <configuration key="flagQuality360p">false</configuration>
        <configuration key="flagQuality480p">false</configuration>
        <configuration key="flagQuality720p">true</configuration>
        <configuration key="flagQuality1080p">false</configuration>
        <configuration key="flagQuality2160p">false</configuration>
        <configuration key="publishToEngage">true</configuration>
        <configuration key="publishToApi">true</configuration>
        <configuration key="publishToOaiPmh">true</configuration>
        <configuration key="publishToYouTube">false</configuration>
        <configuration key="publishToAws">false</configuration>
        <configuration key="uploadedSearchPreview">false</configuration>
        <configuration key="publishLive">false</configuration>
        <configuration key="thumbnailType">0</configuration>
        <configuration key="thumbnailPosition">1</configuration>
      </configurations>
    </operation>


    <!-- Apply series -->

    <operation
      id="series"
      exception-handler-workflow="partial-error"
      description="Apply series metadata and acl">
      <configurations>
        <configuration key="series">${seriesId}</configuration>
        <configuration key="attach">*/*</configuration>
        <configuration key="apply-acl">true</configuration>
        <configuration key="copy-metadata">isPartOf</configuration>
      </configurations>
    </operation>

    <operation
      id="tag"
      description="Tagging metadata catalogs for publication">
      <configurations>
        <configuration key="source-flavors">dublincore/*,security/*</configuration>
        <configuration key="target-tags">+engage-download,+archive</configuration>
      </configurations>
    </operation>

    <!-- Archive -->

    <operation
      id="snapshot"
      description="Archive updated duplicate">
      <configurations>
        <configuration key="source-tags">archive</configuration>
      </configurations>
    </operation>

    <!-- Encode and publish -->

    <operation
      id="include"
      description="Publish the recording">
      <configurations>
        <configuration key="workflow-id">partial-publish</configuration>
      </configurations>
    </operation>

    <!-- Archive after publish -->

    <operation
      id="snapshot"
      description="Archive publish information">
      <configurations>
        <configuration key="source-tags">archive</configuration>
      </configurations>
    </operation>

    <!-- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -->
    <!-- Cleanup                                                           -->
    <!--                                                                   -->
    <!-- Remove work artifacts.                                            -->
    <!-- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -->

    <!-- Clean the system from work artifacts -->

    <operation
      id="cleanup"
      fail-on-error="false"
      description="Remove temporary processing artifacts">
      <configurations>
        <configuration key="preserve-flavors">security/*</configuration>
        <configuration key="delete-external">true</configuration>
      </configurations>
    </operation>

  </operations>
</definition>
```
