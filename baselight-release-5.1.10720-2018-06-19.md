# 베이스라이트 릴리즈 노트 5.1.10720 (2018-06-19)



## New Features Since Baselight 5.1.10637

* Added a "Pick" button to Blackboard, Blackboard 2 and Slate desks. This mirrors the "Pick" toggle in the BaseGrade user interface. It will appear next to 'Ext Rng' in the operator-specific area of the desk when the BaseGrade operator is selected \[bug 45489]
* In Chalk for Blackboard 2 and Chalk for Slate, import/export of desk layouts to USB is now handled via the "Load..." and "Save As..." dialogs. To import a desk layout from USB, click "Load...", select the drive from the volumes drop-down, then locate and open the layout file. To export, click "Save...", select the drive as before, choose a save location and click OK \[bug 46405]
* MXF files containing audio tracks which are linked to an MXF video file are now added to an Audio operator when the video is inserted into a scene from FLUX Manage. This also applies to audio files with the same name as the first frame of an image sequence, e.g. an audio file 000100.wav will be added when it is found alongside an image sequence starting 000100.dpx \[bug 47800]
* Added an IPP2 tab to R3D Params, which contains controls for these recently-added settings:
  * Exposure Adjust
  * Tone Map
  * Highlight Roll Off
  * HDR Peak Nits
  * CDL \[bug 46379]
* bl-render -set can now be used without -queue to perform a multiple-deliverable render on the command-line \[bug 47896]
* In the "Update Avid AAF with Baselight Grades" EDL Export panel, the "Input Video LUT" option has been renamed "Input Legal to Full Scale" to match what the setting is called in full Baselight. The options have also been changed: "No": No legal to full scale will be applied. "Leave Unchanged": The state of the "Legal to Full Scale" toggle in the Sequence operator will be left unchanged (the default). "Yes": A legal to full scale will applied. \[bug 47766]
* Added new "Quick Guide" documentation to the Help menu \[bug 47990]
* Added ability to read input "Legal to Full Scale" values from BLG payloads when applying Baselight Grades from AAF files \[bug 47807]

## Bug Fixes Since Baselight 5.1.10637

* Fixed copy operations hanging in the Operations Queue when the application build used to submit the operation is not installed on the system hosting the queue \[bug 47770]
* Add support for upgrading Adaptec firmware on Gen VII deskside \[bug 47726]
* Adaptec raid diagnostic now warns instead of failing if an array is degraded \[bug 45932]
* Fixed Params operators not working if used in a layer containing no other active operators \[bug 47803]
* Fixed an issue where 3X10 DPX files written by Scanity would incorrectly identify as being 1X10 DPX-Y after being copied by fl-cp \[bug 47809]
* Fixed burnin text opacity \[bug 47404]
* Fixed an issue where some XDCAM MXF files were not properly recognised, resulting in the error message 'Unindexed movie' \[bug 47732]
* Creating a new cursor now correctly copies the quality (max quality, optimised, draft) of the previous cursor \[bug 46334]
* The overlay colour set on Cursor View is now saved and restored with the scene/job cursor settings \[bug 46146]
* Added logic to detect and improve performance of incorrectly indexed XDCAM MXF-files created by Avid software \[bug 47000]
* Fixed an issue where a crashing movie reader could sometimes cause the application to hang \[bug 46916]
* Fixed multipasting of Circle Take Metadata \[bug 45868]
* Fixed Scratchpad "Original Version" toggling when playback filtering enabled \[bug 46356]
* Fixed issue causing some sequences not to be recognised during AAF import \[bug 47748]
* Fixed a crash during EDL import when "Add extra metadata" is enabled \[bug 45666]
* Fixed renderer crash when updating xml files with an empty  element \[bug 45285]
* Allowed the user to enable the Layer Matte rendering mode (in the cursor view) in a read only scene \[bug 38443]
* Fixed sudo diagnostic failure when custom rules are added to /etc/sudoers \[bug 47836]
* Fixed occasional crash in BaseGrade "Match" picks \[bug 47841]
* Improved scene database compaction \[bug 47708]
* Improved smoothness of scene open progress panel \[bug 47704]
* Fixed occasional delays in screen updates on Linux, for example after scrolling thumbnails in FLUX Manage \[bug 47757]
* Fixed rendering masks whose sizes are not defined in whole pixels (e.g. 2.39:1 mask in HD format) \[bug 47871]
* Fixed masks and guides shown in Display View so they accurately represent the pixels that will be masked in a (high-resolution) render \[bug 47871]
* Fixed crash when trying to link a One Point Track or Two Point Track, when an underlying tracker is missing \[bug 47564]
* Shot timecode/keycode no longer changes after a Consolidate \[bug 47886]
* Fixed crash if FLUX Manage View is closed (using a keyboard shortcut) during a drag \[bug 47903]
* Fixed crash when playing a scene containing an unknown OFX operator \[bug 47906]
* Fixed exporting of A/B dissolves in CMX3600 EDLs \[bug 44631]
* Fixed crash reading a truncated ARRIRAW MXF file \[bug 47921]
* Dolby CM Metadata can no longer be exported from a scene whose Dolby Vision strips have not been analysed \[bug 47874]
* Fixed incorrect behaviour of "REDgamma 2" and "Hybrid Log Gamma" colour space options in R3D Decode Params \[bug 47771]
* Fixed incorrect Mastering White Point sometimes shown on Colour Space Journey View \[bug 47944]
* Fixed bug in conform when using '%W' when conforming against similarly named movies \[bug 47946]
* Fixed crash when using GPU OFX plugins on a multi-GPU Baselight system \[bug 47934]
* Fixed hang when dragging scenes/jobs from Job Manager into FLUX Manage \[bug 47893]
* Fixed behaviour of directory browsing on Render View when choosing an output path that starts with the scene's container (e.g. choosing /vol/a\_b when container is /vol/a) \[bug 47601]
* Fixed file permission issues in FLUX Manage, notably when accessing a remote NFS volume that uses root\_squash \[bug 47720]
* Fixed file mode and timestamp preservation when copying sequences to a remote NFS volume that uses root\_squash \[bug 48015]
* Corrected behaviour of 'preserve' mode when copying media; it preserves timestamps and permissions but now can only preserve user/group ownership if running as root (matching the behaviour of cp -p) \[bug 48015]
* Fixed incorrect treatment of Legal to Full Scale when (a) grabbing to gallery, resulting in incorrect images when a gallery shot is viewed with the source media offline, and (b) when exporting BLGs, resulting in incorrect images if the BLG file itself is inserted into a timeline \[bug 46654]
* Fixed default size of disk cache to make better use of the full capacity of an SSD cache drive on a Baselight ONE \[bug 47510]
* Fixed performance regression reading Sony RAW media on Generation VII Baselight ONE systems \[bug 47961]
* Controls on Look operators are now correctly disabled in read-only scenes and locked strips \[bug 45750]
* Changed Gen VII BL1 current\_clocksource to tsc to reduce read\_hpet overhead on large system with many CPUs \[bug 46792]
* Improved performance of Scopes, and of image display on multi-GPU systems \[bug 47804]
* Change sudo diagnostic to 'warn' instead of 'fail' if custom sudoers rules conflict with Baselight rules \[bug 47836]
* Fixed application startup slowdown due to ssh handshake overhead \[bug 47790]
* Fixed crash when using temporal clone in paint \[bug 47993]
* Fixed bug where input colour space values were not being read in EDL Import when applying Baselight grades.
* Fixed a crash in Shots View when entering an invalid time code \[bug 48064]
* Fixed issues when many FLUX Manage browser tabs and/or file browsers are opened \[bug 48096]
* Reduced fl-diag NVNe SSD write / overwrite performance warning thresholds to reflect performance after extended use \[bug 46973]
