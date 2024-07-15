# Baselight Release 5.3.16724 (2022-05-17)



## New Features Since Baselight 5.3.16687

* To accommodate Dolby Vision workflows where deliverables use different formats and/or masking, the Dolby Vision Analysis operator now stores the Analysis Area. This area is then used to generate the L5 Image Aspect Ratio for content mapping and for XML export, based upon the viewing/rendering format and mask that is in use. It is important that the current cursor's viewing format and mask when XML is exported match the render format and mask for the HDR master deliverable \[bug 60357]

## Bug Fixes Since Baselight 5.3.16687

* Fixed GPU memory issues caused by bl-render starting remote rendering on FLUX Store systems \[bug 60466]
* Fixed failure on startup on a multi-GPU system using an NVIDIA driver older than version 418 \[bug 60528]
* Fixed crash when starting playback \[bug 60550]
* Fixed crash when a Dolby Vision Trim operator has no target display set \[bug 60551]
* Fixed crash rendering IMF packages on macOS \[bug 60549]

***
