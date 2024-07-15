# Baselight Release 5.3.16948 (2022-08-05)



## New Features Since Baselight 5.3.16845

* When rendering to a Dolby Vision colour space, colour metadata written to output media (i.e. 'mastering display colour volume' in QuickTime and 'chromaticities' in OpenEXR) now uses values supplied by Dolby Vision, for consistency with the values stored in Dolby Vision XML data \[bug 61195]

## Bug Fixes Since Baselight 5.3.16845

* Fixed support for tiled DVI/HDMI/DisplayPort outputs \[bug 60705]
* Fixed issue with Scene Timecode option not being available in Conform View \[bug 61009]
* Fixed an issue with the 'Use Indexes Where Possible' option for conform and file system browsing \[bug 59570]
* Fixed a kernel version detection issue that was causing NFS mounts to be made without the 'nconnect' option \[bug 61072]
* Fixed crash on startup when the current workspace doesn't contain a timeline \[bug 60530]
* Fixed a problem where attempting to run Baselight again immediately after exiting produced an "Unable to gain exclusive access to SDI" error dialog \[bug 61182]
* Fixed an issue preventing GPU JPEG 2000 acceleration from working with 16-bit IMF packages \[bug 60994]
* Fixed crash that reported "FLGPU\_ExactVirtualRectPool::alloc" to the console \[bug 54035]
* Fixed crash rendering very large image files \[bug 61118]

***
