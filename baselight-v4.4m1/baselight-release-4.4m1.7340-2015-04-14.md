# Baselight Release 4.4m1.7340 (2015-04-14)



## New Features Since Baselight 4.4m1.7323

* Added min/max display range limiter for disparity histogram \[bug 31595]
* Added numeric keypad grading to CDL Grade Exposure \[bug 29026]

## Bug Fixes Since Baselight 4.4m1.7323

* Fixed warning when using old R3D colour science with GPU decoding \[bug 31909]
* Fixed DNxHR QuickTime writing \[bug 31877]
* Now defaults to lower track if content missing in AAF files. Adds a warning to the clip rather than an error \[bug 31535]
* Fixed crash selecting reference strips if viewing and working formats have different widths \[bug 31957]
* Fixed problem that could cause EXR files to be identfied as plain files rather than a sequence when copying \[bug 31969]
* Fixed naming of colour spaces in Arri Look operator \[bug 31968]
* Fixed corruption when rendering 6K RED movies \[bug 32016]
* Fixed bad images being generated for RED movies when insufficient GPU memory is available \[bug 32026]
* Fixed file descriptor leak importing Truelight cubes \[bug 32038]
* Fixed failures when stopping and resuming multiple-deliverable render operations writing to more than one movie/audio deliverable \[bug 31991]
* Fixed errors in muxed stereo renders \[bug 32005]
* Fixed loss of Scanity dirt mattes when copying DPX files \[bug 31941]
* Fixed deliverable formats in scene templates \[bug 31987]
* Ensure dates set in Daylight display correctly in Shots View \[bug 32079]
