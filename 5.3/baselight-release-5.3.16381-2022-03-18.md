# Baselight Release 5.3.16381 (2022-03-18)

## New Features Since Baselight 5.3.16162

### Miscellaneous

* Updated to Sony RAW SDK version 4.0.0. This adds support for Sony VENICE 2 cameras \[bug 58366]

## Bug Fixes Since Baselight 5.3.16162

* Fixed a failure to conform when using an AAF and the media to be conformed is not MXF and there is an index available \[bug 60037]
* Fixed potential crash in operators with tracking controls when no tracker is linked \[bug 59742]
* Fixed failures reading OpenEXR sequences when not all files in the sequence have the same "view" attributes \[bug 59921]
* Fixed failures generating FLUX Manage thumbnails for some Sony MXF files \[bug 59787]
* Fixed an intermittent failure in disk performance diagnostic \[bug 59970]
* OpenEXR media with non-standard 'version' attributes no longer fails to read \[bug 59989]
* Fixed "No shot start frame available for %E" error when rendering with "Render Format: Use Input Format" \[bug 59988]
* Fixed hang in Consolidate when there are Retime operators in use, and improved accuracy of the frame ranges that are consolidated \[bug 59642]
* Fixed FLAPI bindings for Node.JS. Tested with Node 10.24.0 \[bug 60024]
* Fixed failure when reading some ARRI QuickTime media \[bug 60031]
* Fixed crash with Point Trackers which were added in previous versions (5.2 and older) \[bug 60035]
* OpenEXR media with non-standard and/or incorrect 'chunkCount' attributes no longer fails to read \[bug 60065]
* Fixed "Convert Basic Format" not saving the new format into Job or Global Formats, causing warnings when the scene is opened later \[bug 59349]
* Fixed swapped behaviour of "ADA-5 SW" and "ADA-5 HW" in ARRIRAW Params when using the ARRI v7 SDK - please note that this may slightly change the appearance of ARRIRAW media using the v7 SDK in existing scenes \[bug 59945]
* Fixed "delta is in progress" error caused by Six Vector operator \[bug 28167]
* Fixed potential crash when exporting an EDL \[bug 58587]
* Fixed incorrect console message "Unable to use Blackmagic RAW SDK: nvidia driver too old" on some Baselight ONE systems \[bug 60083]
