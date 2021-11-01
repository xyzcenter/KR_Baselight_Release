# Baselight Release 4.4.6753 (2014-05-07)



## New Features Since Baselight 4.4.6689

### Chalk for Slate

*   Chalk for Slate enables users to customise button layouts for Slate desks. Users can select between preset button layouts, make their own unique layouts and edit functionality of individual buttons.

    Each main Layout is comprised of one Home Layout and multiple Slate Layouts.

    The Home Layout offers access to per-strip buttons (e.g. Gang and Reset operators) and is used as a conduit to access the various Slate Layouts.

    Slate Layouts are used as a container for any type of button and a number of commonly used Slate Layout presets are provided: E.g. DBS, Keypad, Layers, Transport, etc.

    Layouts can be exported to a USB stick for easy transferring between facilities.

### BLG and Baselight Editions

* Re-enabled "Update Avid AAF with Baselight Grades" and "Update FCP XML with Baselight Grades" options in the EDL Export panel, now that 4.4 builds of Baselight for Avid and Baselight for FCP are available for testing.
* Added "Lock Grade" option to BLG Export, as well as to the "Update Avid AAF with Baselight Grade" and "Update FCP XML with Baselight Grades" EDL Export options. When set to "Yes", then any exported grades loaded into any of the Baselight Editions (Baselight for Nuke etc) will have the Layer Manager drop-down disabled and set to Layer 0. This will allow the user to change the input/output colour space processing, but not examine or change the grade layers themselves. However, it should be noted that switching on this option will not prevent grades being visible when loaded into full Baselight.

### Colour Spaces

* Added generalised colour space support to "Update Avid AAF with Baselight Grades" and "Update FCP XML with Baselight Grades", allowing the user whether or not to include Input Colour Spaces, the Viewing Colour Space or current Truelight setting in the Baselight grades written to the AAF/XML.
* Added generalised colour space support to the "Apply Baselight Grades" setting in the EDL Import view. Now, when Baselight Grades are detected in an EDL, a setting appears to the right of the Yes/No dropdown, allowing the user to specify which colour space settings (Sequence Input Colour Spaces, Cursor Viewing Colour Space, Cursor Truelight Settings) are to be applied. Having them all on should make the grade look identical to who it looked in the exported Avid/FCP/Baselight, so long as the media is the same. If the AAF/XML was exported from an NLE, then it is possible that each grade could have different Working Colour Spaces, Viewing Colour Spaces - in this situation, Baselight works out the most common value for each setting and assigns that, adding per-event warnings for those events whose values don't match.
* A new option on Scene Settings allows the Display Rendering Transform to apply only on conversions from scene-referred to display-referred colour spaces, having no effect for the reverse display-to-scene conversion. This is initially enabled for new scenes (via Setups) \[bug 27295]
* The Scene Settings and Setups default Input Colour Space control now allows a specific colour space to be chosen \[bug 26665]
* Added support for Display Rendering Transforms defined using functions instead of cubes \[bug 27436]
* New Colour Space Journey View shows details of all colour space conversions in the current cursor's stack, and the colour space at the current cursor position \[bug 27635]

### File Formats and Codecs

* Unencrypted, non-stereoscopic DCP packages can now be created. The option lists as 'Digital Cinema Package' under the Movies Video Only and Movies Video+Audio categories in the render panel. Package title, creator and issuer are read from the scene settings metadata. Bitrates from 250 Mbit/s to 500 Mbit/s are supported by adjusting the codec parameters. Maximum reel file sizes can also be set \[bug 16821]
* Unencrypted, non-stereoscopic DCP packages can now be opened and read. The ASSETMAP file in the DCP directory is treated as if it was a movie file
* Added support for reading and writing unenctryped, non-stereoscopic DCI compliant MXF files containing JPEG2000 compressed frames.
* Updated to RED SDK v5.0. This addresses some issues in earlier SDK releases, and adds:
  * DRAGONcolor color space
  * REDgamma4 gamma option
  * Updated RED Rocket-X firmware and driver
* Added support for reading 16-bit planar TIFF images.
* Writing of compressed file formats now makes better use of available system resources, which improves speed \[bug 24875]
* Timecodes in MXF files are now indicated with their correct frame rate in the Sequence Browser \[bug 27257]
* The fabricated Timecode 2 from Phantom cine files now uses the same fps as the embedded per-frame timecode \[bug 27375]
* Added support for reading DNxHD QuickTime movies with mixed codec settings. Files with more than one setting are shown as being compressed using the setting of the first frame, with an appended '+' to indicate that mixed settings occur in the file \[bug 26652]

### Miscellaneous

*   fl-code now supports -m option to show metadata for image files as

    well as for movies \[bug 27526]

## Bug Fixes Since Baselight 4.4.6689

* Fixed crash in "Update Avid AAF with Baselight Grades" EDL Export option, which could occur when the "Input Filename" was an AAF which didn't match the conformed timeline \[bug 26286]
* Fixed bug in EDL Import which could cause switching between multiple conform tabs to be slower and use more memory.
* Fixed bug in EDL Import in which the count of events containing was occasionally wrong.
* Fixed bug in EDL Export where removing strips based on categories didn't work for "Update Avid AAF with Baselight Grades".
* In EDL Import view, removed a now-spurious warning ("None of the possible formats for this event match the preferred input colour space.") which would appearing during conform using a working colour space which is different from the input formats'.
* Fixed typo in Technical Manual pg\_dumpall section \[bug 27284]
* Fixed excessive PostgreSQL warnings in log files \[bug 27340]
* Fixed issue with database permissions \[bug 27332]
* Fixed stereo rendering problem where upper eye track was failing to render correctly \[bug 27406]
* Fixed EDL export missing the left eye in single stack stereo scenes \[bug 27393]
* Allowed the scene compare to terminate when it's running in the background if another operation has started \[bug 27242]
* Rendering speed of ProRes encoded movies is now improved on Linux \[bug 19384]
* When changing movie file type when rendering with audio, the audio codec is no longer left in an invalid state \[bug 27109]
* Fixed crash when applying to a paste protected stack, with a matte \[bug 27287]
* Remove hotfix which replaces /etc/mtab with a symlink to /proc/mounts because this breaks CXFS bind mounts. Modify fuse library to disable /etc/mtab updates since it uses invalid mount options which cause /pfs automount to fail \[bug 27019]
* Fixed crash in Sequence Browser when using List Keycode option with sequences with invalid keycode \[bug 27497]
* Fixed expansion of %{} keys in Truelight operators \[bug 27449]
* Added confirm/cancel dialogue on close scene/quit if a conform is in progress \[bug 27525]
* Fixed problem where audio timecode and metadata were not being set correctly when an audio file was added to a shot or to the timeline via the Sequence Browser \[bug 27504]
* Fixed problem where changing the Audio FPS for a shot via Shots View was incorrectly changing the shot's audio timecode \[bug 27504]
* Fixed crash loading DPX file containing Northlight alpha channel \[bug 27529]
* Prevented new burnin creation from Cursor View overwriting an existing burnin with the same name \[bug 27538]
* Improved performance of Blackboard 2 rendering \[bug 22510]
* Fixed bug which could, on rare occasions, cause a scene to become unopenable \[bug 27558]
* Fix for slow timeline refresh rate on Gen5 machines with a Blackboard 2 \[bug 27450]
* Added latest version of Blackboard 2 One firmware (8.0.68.74) \[bug 27453]
* Changes to Blackboard 2 Fan Speed in "Blackboard2 Setup" are now persisted across sessions \[bug 27446]
* Replacing Inside/Outside layer operator with an "Add Grain" now shows "Add Grain" on Blackboard 2/Slate instead of "Grain2" \[bug 26254]
* Enabled user editing of "Shift & Alt" Action slot in Chalk for Blackboard 2/Slate \[bug 27186]
* Fixed bug which prevent image from being updated on initial slider drags of matte tool parameters \[bug 27580]
* Fixed problem where the stereo eye mode was not toggling correctly when the render line was not in the bottommost stack \[bug 27569]
* UI/Image/Tablet related buttons on Blackboard 2 One desks are now disabled if not applicable \[bug 27346]
* DKey encoder parameters now display correctly on Artist Color desks \[bug 26201]
* Moved display of "No current, single selection" on Blackboard 2 One desks by a few pixels to ensure it's not hidden behind physical blanking of screen \[bug 25896]
* Fixed incorrect disabling of R3D Params controls when ACES Linear is selected then disabled, fixed ACES Linear controls enabled when using Automatic \[bug 27625]
* Fixed pulldown removal \[bug 27629]
* Fixed crash applying a deliverable set preset with Output Format: Use Input Format \[bug 25473]
* Fixed crash that could occur when pressing "UI 1" or "UI 2" buttons on the Blackboard \[bug 27577]
* Fixed crash when opening Shot View when scene contains a shot with audio but no valid audio timecode \[bug 27552]
* Fixed text input issues related to some Blackboard 2 desks \[bug 27355]
* Fixed bug which could result in the Scratchpad becoming unopenable due to undefined formats \[bug 27652]
* Improved network performance diagnostic to capture link failure statistics \[bug 27070]
* Fixed crash when cancelling the "Add New Burnin" dialog \[bug 27646]
* /vol automounter will use tcp when connecting to a remote pfs2 server and pfs2 server will negotiate 1MB rsize/wsize nfs/tcp where possible \[bug 26799]
* /vol automounter will negotiate 1MB rsize/wsize nfs/tcp where possible \[bug 27261]
* Prepare For Review is now disabled when the disk cache is unavailable \[bug 27395]
* Fix a 'division by 0' alert when conforming using RED material and overwriting the tape name \[bug 22677]
* Fix for crash when pressing Ctrl + Escape with no desk attached \[bug 27643]
* Fix for crash after using Layer View on Slate desks \[bug 27687]
* Fixed bug which could cause the Blackboard's 'Undo' button to be temporarily disabled immediately after a tracking operation \[bug 27697]
* Fixed bug where timecodes were not read from some AAF files \[bug 27611]
* Fixed bug where encoder displays on Artist Color desks were not showing \[bug 26201]
* Fixed bug where some Shape buttons could fail to appear on Slate desks \[bug 27704]
