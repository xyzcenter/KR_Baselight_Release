# Baselight Release 5.3.17711 (2023-03-14)



## New Features Since Baselight 5.3.17567

* Updated Photon to version 4.8.2. This can detect additional issues in rendered IMF packages \[bug 63415]
* Added additional OFX support to allow Neat Video and other plugins to perform better on Baselight TWO hardware \[bug 22455]

## Bug Fixes Since Baselight 5.3.17567

* Fixed potential crash when opening a scene containing a Stereo Geometry Fix operator \[bug 63209]
* Fixed issue with incorrect essence descriptor tags being written to 2K and HD resolution IMF packages \[bug 63417]
* Fixed indexing issue with non-XFS volumes when the associated fuse driver fails \[bug 62919]
* Fixed issue that could prevent some IMF CPLs from being read \[bug 63491]
* Fixed issue where 'Audio Track Names' metadata was not set correctly for some WAV files \[bug 62900]
* Fixed issue causing some IMF CPLs to be unreadable \[bug 63191]
* Fixed potential playback glitch when overlays were disabled from the Transform operator's UI \[bug 63472]
* Added Aperture metadata to ARRI MXFs converted from Linear Iris metadata \[bug 63548]
* Fixed issue displaying unnamed accounts in Frame.io integration package \[bug 63127]
* The Formats editor no longer allows edits to reverse mappings from a format which is not a Scene format, to avoid unexpected behaviour \[bug 63542]
* Fixed issue with unnecessary segmentation in supplemental IMF deliverables using 'Preserve' mode audio tracks \[bug 63230]
* Fixed issue loading some 1D cube files \[bug 63563]

***
