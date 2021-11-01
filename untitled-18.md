# Baselight Release 4.3.5343 (2012-05-11)



## New Features Since Baselight 4.3.5327

*   Added support for Blackboard 2 One desk on Baselight ONE systems. The desk is driven entirely over USB and uses a fixed mapping of buttons similar to the original Blackboard.

    To enable support for the Blackboard 2 One on a Baselight ONE system, enable "USB" for the "Blackboard 2 / One" option in the System preferences tab.
* "UI Views" button added for Blackboard 2 desks. Allows fast switching of Workspace views (Standard, Simple, Scopes, etc) and toggling of view windows (Job Manager, Shots, Scene Settings, etc)
* "Cycle Cursors" button added for Blackboard 2 & Blackboard 2 One desks. Allows quick switching of active cursor with left hand.
* "Delete Strips" button added for Blackboard 2 & Blackboard 2 One desks. Removes need to flip up keyboard, or use soft keyboard to delete currently selected strips.
* Added the ability to enable/disable drag-and-drop shot movement in the Cut and Gallery views. In the Cut View preferences, the "Allow Drag-and-Drop Shot Movement" setting is a simple toggle button. In the Gallery View preferences, on the other hand, the user is able to disable shot movement completely, allow it only for true gallery scenes, or allow it always.
* Added a "Cancel" button to the "Create New Gallery" dialog, which allows the user to elect not to create a gallery.
* Updated the Truelight library to include the internal HD Rec1886 display calibration: Rec709 primaries, 2.4 gamma tone curve, as described in ITU document R-REC-BT.1886-0-201103-I.PDF-E.pdf
* Added ability to Multi-Paste by "Record Frame Number" or "Record Timecode", which is useful when one wishes to paste grades between scenes where the cut points are the same but the source media or metadata has changed in some way between two cuts. Note that since "Copy Grades" in the EDL Import via uses Multi-Paste internally, the "Record Frame Number" and "Record Timecode" options are also available there.
* Added support for reading Sony F65 RAW Lite MXF files.
* Added support for reading SStP/L2 4:4:4 MXF files.
* "Cursor" mode on Blackboard 2 key pad now highlights current cursor and shows active cursor slots.
* "Cache" button on Blackboard 2 and Blackboard 2 One allows quick toggling of per-strip caching.

## Bug Fixes Since Baselight 4.3.5327

* Fixed problem with the Temporal Degrain, where if the threshold was set to zero and had a matte, the plugin was not bypassed correctly \[bug 17227]
* Fixed crash toggling hide Overlay when the cursor view was hidden \[bug 20374]
* Fixed double grab to gallery from Blackboard 1 \[bug 20401]
* Fixed colour shift on older ALEXA ARRIRAW files. Existing scenes are unaffected; re-insert or re-conform the .ari files to change the colours.
* Fixed problem with old scenes containing Hue Angles, by disabling the new colour space UI \[bug 17395]
* Fixed scenes becoming unloadable after using strip category names containing the " character \[bug 20618]
* Fixed crash when using an MC Color or MC Transport panel alongside a remote device \[bug 20619]
* The Baselight hotfix script will disable PostgreSQL logging to syslog, as we have found it can slow down the server under heavy log load \[bug 15484]
* Removed acceleration from Blackboard 2 / One jog wheel \[bug 20416]
* Fixed invalid state change in GPU renderer \[bug 20394]
* Fixed occasional crash when re-ordering shots in the Cut View/ Gallery using drag-and-drop \[bug 20624]
* Fixed error using strip caching above temporal strips \[bug 20636]
* Fixed crash in Gallery View which would occur when an autoloaded gallery could not be created \[bug 20418]
* Fixed bug in Cut/Gallery Views which could cause the incorrect thumbnail to be selected if the metadata display was switched on and the view was zoomed out a substational amount \[bug 20340]
* Fixed occasional assertion in Cut View/Gallery \[bug 19950]
* Fixed crash using an invalid render filename template (e.g. %-10W) \[bug 20654]
* Fixed MatteTool always pasting keyframes \[bug 20558]
* Fixed thumbnails when using Make Matte: Alpha \[bug 20514]
* Fixed problem with large audio latency on systems with Hammerfall HDSPe AIO audio cards \[bug 20653]
* Fixed crash when modifying parameters in the Spirit view \[bug 20633]
* Fixed preservation of alpha channel in proxy images \[bug 10162]
* Fixed the Timeline Alignment view causing re-evaluation of the timeline cache state (the green line in the Timeline), even though an alignment can't change the actual image produced by a given frame \[bug 18983]
* Fixed opening scenes using unavailable OFX plugins.
* Fixed bug which could cause a crash if the trackballs were knocked while moving strips in a scene \[bug 20647]
* An invalid line in volume.cfg no longer crashes Baselight startup \[bug 20393]
* Fixed problem with Unset/Set keyframes crash \[bug 20671]
* Fixed DCI 4K 23.976p display mode when used with NVIDIA 8800, 9800, GTX285 and GTX580 GPUs \[bug 20346]
* R3D sequences with the "Do Not Use RED Rocket" option no longer cause the decode to happen on the CPU of the machine containing the RED Rocket \[bug 20676]
* Fixed adjusting the MatteCurve and switching scenes \[bug 20671]
* Fixed bug which could cause an edit to remain open when switching scenes whilst adjusting an encoder \[bug 20684]
* Fixed bug which could cause crash on set/unset keyframe when using a Hue Shift \[bug 20693]
* Categories selected in the "Shots Containing Categories" list on Render View now remain selected the next time the list is opened \[bug 20698]
* Disable background caching while rendering from inside Baselight \[bug 20699]
