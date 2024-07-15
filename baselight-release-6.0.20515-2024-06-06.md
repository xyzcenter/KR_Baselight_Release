# Baselight Release 6.0.20515 (2024-06-06)

##

### New Features Since Baselight 6.0.20380

* Added NVIDIA 470.223.02 as a supported NVIDIA driver. Bug 68314
* Added support for decoding XF-AVC 4:2:2 10-bit (xfia) in QuickTime and MP4 files. Bug 68368
* Updated to use AJA SDK 16.2.6 and latest Kona 5 firmware. Bug 67183
* Added diagnostic support for Broadcom MR9580 RAID controller. Bug 67610

### Bug Fixes Since Baselight 6.0.20380

* Fixed bug when exporting a cube from scenes that use a DRT with black offset. Bug 68332
* Fixed a crash after repeatedly switching the cursor to the SDI with the X Grade operator selected. Bug 65410
* Fixed UI slowdown which could occur when playing back or when background caching in scenes with strips overlapping multiple shots, especially when zoomed out a long way. Bug 68411
* Improved performance of Blackboard 2 Timeline View in situations where some strips spanned across multiple shots (e.g. an offline strip above the grading conform). Bug 68414
* Fixed a memory leak in the Baselight UI process when background caching in some scenes. Bug 67852
* Improved UI interactivity when working with galleries in "Current Cursor" mode. Bug 68020
* Fixed an issue with the gallery that could cause slow updates. Bug 68434
* Fixed issue causing Chromogen/Flare update to become sluggish over time. Bug 68452
* Greatly improved performance when inserting/removing layers with a large Cuts View present in the UI. Bug 68419
* Removed 'Gallery' and 'Gallery 2' Shots View filters that would appear after adding the Current Cursor to Gallery View. This prevents crashes that could occur after removing these tabs. Bug 68475
* Slightly improved responsiveness when a Layer View is present in the UI and the timeline contains complex stacks. Bug 68478
* Fixed issue causing a crash in the Presets View for certain layer stacks. Bug 67802
* Performance improvements for X Grade operator. Bug 68497

\
