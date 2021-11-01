# Baselight Release 4.4.6871 (2014-07-16)



## New Features Since Baselight 4.4.6814

* Added LUT export formats Autodesk 1D half float (for Flame 2015), Colorfront 1D and Colorfront 3D.
* Added bl-reset-cache '-hardssd' option which can improve performance of the Baselight cache when it is hosted on a Solid State Drive array by secure-erasing the raw drives, hence restoring them to their factory state \[bug 28009]
* Improved the information shown on colour space menus:
  * tooltips are now presented to describe each space
  *   a warning icon indicates when a space is not ideal for use as a

      working/grading colour space
  *   Cursor View warns when the viewing colour space does not match the

      full/legal setting of the Combiner SDI Output (when no Truelight

      is applied) \[bug 28114]

## Bug Fixes Since Baselight 4.4.6814

* Fixed occasional bright pixels in dark areas of Phantom cine images \[bug 28164]
* Improved error message when trying to render FFMpeg ProRes at a resolution whose width and/or height is not even \[bug 27512]
* Data in the timeline cache is now used where possible for RGB renders, when the cache has enough precision and the render settings match those of the cursor used to fill the cache \[bug 20666]
* Scenes with long folder/scene names can now be opened as galleries \[bug 26299]
* Fixed decode of ALEXA Open Gate material using ARRI SDK \[bug 28254]
* Fixed a random crash on exit issue \[bug 27900]
* Fixed Input Colour Space setting on conformed sequence, when Scene Setting specifies a named colour space \[bug 28283]
* Fixed crash in EDL Import, which occurred when loading DLEDLs containing "DLEDL: PATH:" lines lying after an invalid CMX event \[bug 22214]
* Fix for crash after deleting buttons in Chalk then switching layouts \[bug 28165]
* Fixed issue where Slate screen updates could lag behind UI display \[bug 28223]
* Fixed glitching playback when pressing "Ctrl" on Blackboard 2 or Slate desks \[bug 27850]
* Fixed crash when driving Blackboard 2 from graphics card which does not support glXSwapIntervalEXT \[bug 28245]
* Improved startup time of many applications and tools when there are many Truelight profiles on the system \[bug 28326]
* Improved appearance of tooltips \[bug 28156]
* Fixed reading of some Avid legacy format MXF files \[bug 28372]
* Added support for reading Apple ProRes 4444 XQ QuickTime movies on Linux \[bug 28344]
* The About Baselight dialog now shows the current user \[bug 28085]
* Fixed 'connection timeout waiting for nodes' error due to interrupt routing issues on Generation IV hardware running Flos 6.4. NOTE: this needs a full reboot of all nodes in a Baselight FOUR/EIGHT after installation \[bug 27855]
* On Flos 6.4 systems the user's path now has the Baselight bin directory before the Truelight one \[bug 27293]
* Fixed NVIDIA driver version diagnostic on systems without a Myricom NIC \[bug 28131]
* Fixed crash on mouse left button click in the layer view \[bug 28180]
* The strip name can no longer be edited when multiple strips with different names are selected \[bug 22863]
* Fixed incorrect area picks in all keyers \[bug 28355]
* Fixed playback stall on Baselight EIGHT \[Bug 28382]
* Log DPX files are no longer assigned ADX Log colour space by default \[bug 28427]
* Fixed crash report setup on new systems \[bug 28438]
