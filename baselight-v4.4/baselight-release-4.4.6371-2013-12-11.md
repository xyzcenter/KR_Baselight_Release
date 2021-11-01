# Baselight Release 4.4.6371 (2013-12-11)



## New Features Since Baselight 4.4.6317

* Added "Pick Corners For Manual Adjustment" button to Stereo Fix semi-automatic page for picking the 4 image corners for manual adjustment.
* Added "Metadata" tab to Scene Settings, to allow scene metadata to be edited. The default values for scene metadata can be set in the job from Scene Settings. Initially the only metadata controlled from this tab is the Project written into Avid MXF files \[bug 17524]
* Added new 'Blend Grade Source' layer mode. When selected, the layer's grade operators are applied to the blend source (when this mode is selected, the 'Blend Source' dropdown moves up to sit below the 'Layer Mode' dropdown to indicate that the layer's operators are applied to it) \[bug 26147]
* Added options to show Viewing Colour Space and Display Rendering Transform as metadata on Gallery View \[bug 26149]
* On Slate  +  now selects Layer 31 \[bug 26051]
* On Blackboard 2  +  now selects Layer 21 \[bug 26051]

## Bug Fixes Since Baselight 4.4.6317

* Fixed functionality of trackball reset buttons on Tangent panels \[bug 26072]
* Fixed failures copying image sequences from non-/vol locations to /vol/images on a Baselight FOUR or EIGHT \[bug 26084]
* Removed the fixed width restriction on the System column in "fl-systemmonitor -live" output \[bug 26089]
* Fixed occasional crash when dealing with certain Truelight profiles on display \[bug 25598]
* Fixed premature exit from commandline (non-queued) bl-render when rendering to more than one movie (e.g. with %L or %E) \[bug 26112]
* Fixed crash when using blur and very large transform scales; also restricted available transform scale \[bug 26110]
* Fixed memory leak, render cancellation and render hang issues on Baselight FOUR/EIGHT systems \[bugs 26071,25974,25847,25781]
* Fixed occasional commandline (non-queued) bl-render hangs when rendering to movies \[bug 25982]
* Fixed crash when changing the frame rate of Reference Timecode on Shots View \[bug 26064]
* Fixed bug in Stereo Fix strip's "Show Input" mode when in a stack with upstream transforms & cached strips (the transforms could be applied twice) \[bug 26122]
* Fixed issue with artifacts in underexposed RAW files \[bug 25786]
* Fixed crash reading interlaced VC-3 (DNxHD) MXF files \[bug 26137]
* Fixed Multi-Insert of split-file MXF movies (e.g. C300) \[bug 26144]
* Fixed read failure of intra-frame encoded MPEG MXF files such as D-10 IMX \[bug 26143]
* Fixed incorrect gallery images when the stack has cached strips and the stack was grabbed from a scene with a different working format from the gallery scene \[bug 23197]
* Fixed various issues with gallery grabs resulting in incorrect colour spaces being applied when previewed on the display monitor \[bug 25620]
* Fixed the top-left thumbnail shown in Cuts and Gallery View occasionally using the wrong colour space.
* Fixed incorrect gallery images when the stack was grabbed from a scene with a different DRT from the gallery scene.
* Fixed various issues with Gallery Current Cursor mode.
* Fixed occasional flickering rear and button screens on Slate desks \[bug 26150]
* Fixed crash when recalling from or to a stereo split sequence operator \[bug 26047]
* Fixed BLG export of stacks containing Look operators with no look selected \[bug 26151]
* Fixed errors overwriting gallery files due to restrictive file permissions on original files \[bug 26165]
* Fixed crash in stereo grade \[bug 25840]
* Fixed incorrect application of Truelight profiles on the cursor when they only contain a 1D LUT \[bug 26162]
* Fixed bug which could cause the incorrect keyframe to be highlighted on keyframe bar in edit left/right modes \[bug 26000]
* Fixed errors when double-clicking on a scene in the Save As dialog \[bug 26199]
* Fixed problem with combiner genlock at 4096x2160 on GTX 680 GPUs \[bug 25923]
* Fixed problem with audio-related metadata not appearing in Shots View or ALEs exported from Shots View \[bug 25837]
* Fixed crop rectangle read from Canon HRAW (.RMF) files \[bug 26220]
* Fixed render failure "Insufficient tiles to complete this render" \[bug 25668]
* Fixed problem with more than 2.1 billion repeated lines causing log files to become too large \[bug 26232]
* Fixed Modify AAF renders never being shown as completed \[bug 26239]
* Fixed an issue that caused short H.264 QuickTime movies on Linux to be empty \[bug 25942]
* Fix for issue when +-ing from and to Baselight which resulted in the Slate desk displaying buttons as though the  key was still held \[bug 26216]
* Reordered input devices in Preferences->System \[bug 25898]
* Fixed bug which left Blackboard undo/redo buttons temporarily disabled after a Curve Grade encoder control point adjustment \[bug 26264]
* Fixed "phantom" trackball movement on Slate desks which could prevent caching from working correctly \[bug 26209]
* Updated Blackboard 2 firmware (1.1.44.60) to improve response time of button presses (now updates at 200Hz as opposed to 33Hz). Install new firmware by running "/usr/fl/baselight/bin/bl-update-bb2" at the command line \[bug 26183]
* Fixed race condition in renderer that could cause black stripes to be visible in on clusters \[bug 26197]
* Fixed recall of cursor Colour Space when loading scene \[bug 26296]
* Fixed a logging problem with long-but-different lines being considered to be the same \[bug 26232]
* The operations queue database is now vacuumed overnight prior to the database backup, which should improve performance \[bug 25844]
* Fixed errors in View 5-9 modes when using cached strips \[bug 26081]
* Fixed excessive memory usage on render-to-cache \[bug 26319]
* Fixed bug which could cause crash with some burnin settings in stacks with explicitly cached strips \[bug 26336]
