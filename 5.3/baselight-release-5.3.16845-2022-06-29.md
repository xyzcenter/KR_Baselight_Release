# Baselight Release 5.3.16845 (2022-06-29)



## New Features Since Baselight 5.3.16724

### Miscellaneous

*   IMF package deliverables are now rendered using the 2020 version of the standard, SMPTE ST 2067-21:2020 - Application #2E.

    The video track in an IMF package can now be split into multiple parts to conform with requirements of maximum file duration or size. Video parts are listed in a table and can be double-clicked to navigate to the start frame of the corresponding part.

    The default names of the files comprising the IMF package have been updated and are now shown in Render View. If modified, the new naming style will persist and be applied to any new files or IMF package deliverables. The substitution %{RandomUUID} can now be used in Render View to create filenames including randomised UUIDs. UUIDs encoded in filenames will be applied to the corresponding contents.

    Rows in the Scene Differences dialog that appears when comparing a master scene to the current scene in a Supplemental IMF deliverable can now be double-clicked to navigate to the start of the corresponding entry.

    The timecode in rendered IMF packages now always starts at 00:00:00:00.

    The list of audio languages has been updated to include those defined in Netflix Branded Delivery Specifications v4.1 \[bug 58586]
* Restored the Modify AAF render workflow behaviour so that an AAF is written even if Baselight cannot update the media file paths \[bug 58093]
* Insert At Sequence Timecode now supports the FLUX Manage View "Use Frame Number" timecode option \[bug 60521]
* Conform View now has a Move Existing Strips option, which controls whether existing strips (typically from earlier conforms) are always moved upwards, or only when they would overlap with new strips \[bug 60213]

## Bug Fixes Since Baselight 5.3.16724

* Fixed issue with missing thumbnails on Blackboard 2 on systems using a Quadro T2000 Mobile UI GPU \[bug 60252]
* Fixed errors and crashes when using ProRes RAW media \[bug 60697]
* Added filter for Blackboard Classic encoder noise \[bug 60671]
* Fixed failure reading 16-bit lossless UHD IMF packages \[bug 60837]
* Fixed issue with tracking in a stack with multiple sequences, resulting in trackers working off the wrong sequence \[bug 60879]
* Fixed network issues caused by multiple systems on the network using the same local IP address for a Blackboard connection \[bug 59094]
* Fixed artefacts in right-to-left subtitle text \[bug 60641]
* Improved colour spaces set from metadata for Canon CRM files \[bug 57997]
* Fixed Sequence Version detection when inserting sequences or refreshing existing sequence versions \[bug 60834]

***
