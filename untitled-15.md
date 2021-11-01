# Baselight Release 4.3.5245 (2012-03-23)



## New Features Since Baselight 4.3.5238

* Importing scene and job archives now restores folder structure from the saved scenes.
* Added support for reading movie files where the image data is split over several MXF files (e.g. Canon XF305).

## Bug Fixes Since Baselight 4.3.5238

* Fixed failure to load scene containing missing formats \[bug 19713]
* Upgraded scenes are now saved immediately after upgrade. This prevents the scene from becoming unrecoverable if Baselight crashes before the scene is next saved.
* Video grades created in new scenes will now remember their last selected tab page \[bug 20329]
* Fixed XML conform issue with old v4 FCP XML files \[bug 19592]
