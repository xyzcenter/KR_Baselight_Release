# Baselight Release 4.3.5371 (2012-05-28)



## New Features Since Baselight 4.3.5343

* Baselight now remembers the selected visible audio channels in the Audio Waveform view.
* Baselight now remembers the selected Audio Timecode Sync FPS on a per-job basis, and will use the last selection when creating new scenes within a job.
* It is now possible to perform clap detect on an audio sequence from the Audio Sequence operator in the Input node.
*   There are now 3 timeline caching modes (available from the scene settings panel & preferences editor). These replace the "Timeline Caching" Enabled/Disabled toggle in previous versions. The new modes are:

    "Disabled" - Timeline disk caching is disabled. "Cache Strips Only" - Only strips with caching explicity turned on are cached. "Full" - Stack bottoms and strips with caching explicity turned on are cached (equivalant to enabling timeline caching in previous versions).

    "Cache Strips Only" is a new mode, with different cache bar colour coding in the timeline: Areas with no explicitly cached strips are drawn in dark grey. Areas with explicitly cached strips that have not been fully cached are drawn in light grey. Areas with explicitly cached strips that have been cached are drawn in blue.
* You can now switch between displaying the audio offset in Frames or Seconds in the Audio Sequence operator, Audio Waveform view and Scene Settings view.
* REDCINE luma, red, green and blue curves are now read and applied from RMD files into the R3D Decode operator. Note that the curves are not displayed and cannot be edited in Baselight.

## Bug Fixes Since Baselight 4.3.5343

* Six Vector now displays Layer matte correctly \[bug 20719]
* QuickTime movies with multiple mono audio tracks are now read correctly \[bug 17772]
* Stacks containing cached strips now display Layer Matte and Selection Output render modes correctly \[bug 20455]
* Matte Merge now correctly passes metadata from its uppermost input strip \[bug 20736]
* Fixed unordered stack when inserting external mattes first, then adding a layer and pressing Use Matte \[bug 20465]
* The file panel no longer automatically descends into directories when browsing for a directory \[bug 18494]
* When an error is encountered during Scene Detect, the cursor is now moved to the location of the error.
* Fixed bug which could cause a category-related crash on scene open \[bug 20375]
* Fixed issue with dragging the playhead in the Audio Waveform view leading to an open delta that cannot be closed \[bug 20530]
* Fixed issue with changing audio position & offset from the Audio Waveform view when using scene audio \[bug 20710]
* Fixed issue with scrolling audio waveform view when dragging the playhead past the start or end of the current visible audio region.
* You can now set correctly negative audio offsets in frames/seconds in the Audio Sequence operator, Scene Settings view and Audio Waveform view \[bug 15697]
* fl-cp and flux sync options now consider file sizes to help solve problems caused by failed previous copies, or bad filesystems. Movies and files will be re-copied when their timestamps match if their sizes differ \[bug 19997]
* Sub-second timings are no longer read from JPEG files and THM sidecar files accompanying QuickTime movies, to match Canon plugin behaviour. This will change File Timecode but not Shot Timecode in existing scenes that use such files \[bug 15963]
* Fixed bug which could cause a crash if trackballs are moved while closing a scene with the save/discard dialog visible \[bug 20773]
* Categories selected in the "Shots Containing Categories" list on Render View now remain selected the next time the list is opened \[bug 20698]
* Disable background caching while rendering from inside Baselight \[bug 20699]
* Fixed bug which would cause re-valdiation of timeline cache status bar on a render panel setting change \[bug 20713]
* Fixed bug which could cause crash if scene quickly closed after opening with 'Initial verification pass on scene load' Background Caching preference enabled \[bug 20763]
* Fixed bug where udev would complain about 'unknown keys' when applying rules for Blackboard 2 / ONE \[bug 20768]
* Fixed bug where Baselight would complain about ftdi driver on shutdown when Blackboard 2 / ONE is selected in prefs \[bug 20768]
* Fixed flux progress text when copying multiple files \[bug 19624]
* Optimised Blackboard 2 display rendering. Screens are now rendered using single-buffering to reduce texture memory consumption and to allow partial redrawing of the surface \[bug 20376]
* Enabled audio levels display during playback on Blackboard 2
* Fixed issue with Spirit HD/2K/4K control not working \[bug 19549]
* Fixed crash when opening Spirit view for a scene that uses a Spirit Preset that has been deleted. The Spirit View will keep the current settings, but resetting any parameters will reset them back to the values from the "Default" Spirit Preset \[bug 15022]
* Fixed ranges of Spirit Lift, Gamma and Gain controls in Spirit View and Spirit Primary operator in timeline. It is now possible to reach the maximum extents of the correction for each parameter. For example, pushing the colour wheel to the maximum extents along the Red vector will create a correction of (1.0, -1.0, 1.0), yielding negative values for the green and blue channels \[bug 19100]
* Fixed crash when using nudge buttons in Audio Waveform button to change Audio Offset in Scene Settings \[bug 20832]
* Fixed inconsistent stickiness of Blackboard 2 'UI Views' button. A long hold when the button is latched now disengages the mode. Same change also made for 'Keyboard' button \[bug 20812]
* Fixed rendering scenes not being shown in top-right scene list on menu bar \[bug 20842]
* Fixed RME Hammerfall HDSPe AIO card settings file not being copied over when new Baselight versions are installed \[bug 19684]
* Fixed colour shift on older ALEXA ARRIRAW files. Existing scenes are unaffected; re-insert or re-conform the .ari files to change the colours.
* Fixed reset in ganged parameters not returning to zero correctly in the mattetool \[bug 20853]
* Fixed error message when nudging audio offset left/right when audio is embedded in movie file \[bug 20832]
* Fixed behaviour of Ctrl + Top Left Trackball button on Blackboard desks to reset state of current parameter strip \[bug 20849]
