# Baselight Release 4.4m1.9103 (2017-02-20)



## New Features Since Baselight 4.4m1.9029

*   Added new NCLC Tagging for Quicktime Exports. Quicktime NCLC Tags

    can now but specified in the .flspace file. This should fix current

    Gamma Shifts when Quicktime Movie Files are viewed in a ColorSync

    managed Application like Quicktime X and Safari \[bug 31853]

## Bug Fixes Since Baselight 4.4m1.9029

* Fixed an issue that caused the GPU accelerated JPEG 2000 decoder to attempt decoding other codec types as well, resulting in error messages printed to the console \[bug 40857]
* Fixed crash in bl-applyblg \[bug 40881]
* Fixed a decoder failure that could occur when attempting to read XDCAM encoded MXF files with missing reference frames in the stream \[bug 40851]
* Fixed reading QuickTime clean aperture (crop rectangle) metadata on Mac OS X \[bug 36665]
* Fixed hang/crash changing "Display and Timeline Cache" format \[bug 40975]
* The GPU accelerated JPEG 2000 encoder now sets the correct value of the rsiz capabilities parameter in the codestream \[bug 41087]
* Fixed dragging and dropping between galleries \[bug 39529]
