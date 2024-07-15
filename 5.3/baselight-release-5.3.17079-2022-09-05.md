# Baselight Release 5.3.17079 (2022-09-05)



## New Features Since Baselight 5.3.16948

* Updated to ARRI Image SDK 7.0.1. This adds support for:
  * support for ALEXA 35 cameras
  * additional metadata in ARRI MXF media (ARRIRAW and Apple ProRes) from ALEXA 35
  * support for HDE-compressed ARRIRAW MXF media
  * the "ARRI: LogC4 / ARRI Wide Gamut 4" colour space \[bug 59994]

## Bug Fixes Since Baselight 5.3.16948

* Improved speed of ARRIRAW v7 decoding on macOS \[bug 59795]
* When writing OpenEXR files from OpenEXR source media, the "name" attribute is now preserved \[bug 61044]
* Fixed presentation of rectangles in raw metadata JSON \[bug 57536]
* Fixed reported resolution of 3424x2202 ALEXA Mini MXF media \[bug 61213]
* Fixed issue with incorrect audio in supplemental IMF deliverables using 'Preserve' mode audio tracks \[bug 61501]
* Fixed crash in date metadata handling \[bug 61444]

***
