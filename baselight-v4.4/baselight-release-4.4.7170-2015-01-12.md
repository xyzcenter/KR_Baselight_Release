# Baselight Release 4.4.7170 (2015-01-12)



## New Features Since Baselight 4.4.7153

* The bl-dvs-upgrade script can now be used on systems with Atomix LT cards. The DVS firmware & SDK has also been updated to the latest stable revision.
* Baselight disk-cache loading performance has been improved for very big caches. In addition, the cache load progress is shown in the Baselight splash screen \[bug 13891]
* Added fl-queuetool for command-line inspection and modification of the Operations Queue \[bug 30564]

## Bug Fixes Since Baselight 4.4.7153

* Blur button for Layer 0 is now enabled on Blackboard 2 & Slate desks \[bug 30312]
* A conform bug was causing the wrong movie to be selected when there were several alternatives with the same name but at a different filesystem path available \[bug 30439]
* Fixed incorrect marks when splitting some strips (e.g. Text, Bars) \[bug 30561]
* Fixed issue with saving cursor settings in a scene when the name of the Viewing Format contains unusual characters \[bug 25278]
* Fixed an issue with 'Import EDL' which after selecting an XML file would fail when browsing for a subsequent file \[bug 29828]
* Fixed empty dialog issue when attempting to duplicate masks and burnins in the Formats window \[bug 30371]
* Fixed reading DNx444 MXF files from ARRI ALEXA \[bug 30617]
* Fixed the 'blgwcspace' value in BLG files being incorrectly set. It is now set to the working colour space of the scene being exported from \[bug 29444]
* fl-diag now no longer reports an error message when checking DVS fimware version \[bug 30631]
* The Machine Control edit mode now defaults to auto-edit, which is more reliable and used on all modern VTRs \[bug 28541]
* In some cases, VTRE operations would stall whilst locating. These have been found and fixed \[bug 28327, 29288]
* The vtre-server now line-buffers its log output, so it can be monitored in real-time with "tail -f" \[bug 26846]
* Fixed potential "overwriting global function log() with array" crash in vtre-server \[bug 29329]
* Baselight will now tell you if you have an unsupported %-escape in a ingest/playout filename template \[bug 28268]
* Fixed issue with large 'fl-cp' and 'flux' operations consuming resources and appearing to 'hang' \[bug 30610]
* Fixed issue that was causing conform to fail if a new search directory was selected whilst a conform attempt was in progress \[bug 29889]
