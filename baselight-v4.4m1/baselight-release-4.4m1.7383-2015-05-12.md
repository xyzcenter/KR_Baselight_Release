# Baselight Release 4.4m1.7383 (2015-05-12)



## New Features Since Baselight 4.4m1.7340

* fl-queuetool's "list" "log" and "tasks" commands now have a -w option for full-width output \[bug 32114]
* fl-queuetool's "tasks" command now outputs only 150 tasks by default; it has new -a and -n options to change this \[bug 32202]
* Added an option to the new LUT generation to replace grade operations in the scene with the new LUTs. This option is only available for LUTs that don't include Input or Output colour space conversions \[bug 32033]
* Added "-set" option to bl-render to allow deliverable sets to be submitted for rendering from the command line \[bug 24457]
* Added "-template" option to bl-conform to allow use of a Scene Template \[bug 32271]

## Bug Fixes Since Baselight 4.4m1.7340

* Fixed failures after resetting a Colour Space operator \[bug 32113]
* On Mac, Num Lock (or Clear) no longer blocks any keypress when using numeric keypad grading \[bug 32102]
* Fixed error handling in LUT export and improved detection of shapes \[bug 32097]
* Fixed failure to export LUTs on multi-node systems \[bug 32035]
* Fixed failure to export LUTs from ARRIRAW material \[bug 32140]
* Fixed consolidate to a non-/vol location \[bug 31797]
* Can no longer create a scene with a 0x0 working format when an audio file is selected in Sequence Browser \[bug 31868]
* Fixed a bug that could cause reading of temporally compressed movies to hang \[bug 31893]
* Fixed an issue that created broken h.264 QuickTime movies when using rate control with framerates of 23.976 or 29.97 \[bug 32143]
* Fixed crash when group grading a CDL Grade \[bug 32162]
* Improved error reporting for LUT export failures \[bug 32188]
* Added warning to LUT export when overwriting cubes \[bug 32179]
* Added warning for duplicate cube file names in LUT export \[bug 32175]
* Fixed failure to decode some AVC-Intra 4:2:2 MXF files \[bug 32151]
* Replaced ACES RRT 0.1.1 inverse cube. This fix changes the render of old scenes that used the old cube. The old cube had incorrect values outside the forward RRT gamut boundary that gave banding for extreme colours. The new cube matches the old cube within the forward RRT gamut, but is continuous throughout so gives no banding. If you did not see banding in an old scene, the change should not be visible \[bug 31952]
* Fixed reading cursor settings stored in jobs \[bug 32001]
* Enabled Grouped Grading for Film Grade Balance Exposure \[bug 32023]
* Fixed the 'zones' diagnostic which could hang on Baselight Kompressor \[bug 32187]
* Fixed Cuts View thumbnails for 2048x1080 Sony RAW media \[bug 29923]
* Fixed occasional render hang when rendering to multiple deliverables where the first deliverable is not a movie and another deliverable is a movie \[bug 32200]
* Fixed failures to decode some images (e.g. F65 RAW) at a crop/marker resolution \[bug 32220]
* Updated DNxHD SDK. This addresses failures to read some QuickTime DNxHD files \[bug 31975]
* Fixed occasional corruption on render out \[bug 32208]
* Fixed bug which could cause the timeline to crash when referencing mattes in one layer from another layer's matte \[bug 32241]
* Fixed failure in fl-systemmonitor -live \[bug 32263]
* LUT export no longer leaves open a temporary scene showing a test chart image \[bug 32260]
* Fixed inaccuracy in audio timecode when synchronising images to broadcast wave files \[bug 32264]
* Added support for rendering audio without resampling when source audio file is 48048 Hz, scene is 24 fps, and rendered movie frame rate is 23.976 fps \[bug 32273]
* Fixed many issues in bl-conform \[bug 32271]
* Fixed failure scanning a directory containing a zero-length WAV file, and include scanner errors in fsdb-ls output \[bug 32281]
* Fixed bug where SDI scaling mode was not being correctly applied when the software starts \[bug 32002]
* Fixed possible corruption on render of R3D files \[bug 31946]
* Fixed problems with playback glitching at particular frame rates \[bug 32216]
* Fixed display of mattes while interactively grading \[bug 32293]
* Fixed crash when using the numeric keypad to enter numbers when group grading is active \[bug 32324]
