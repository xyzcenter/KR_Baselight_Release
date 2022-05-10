# Baselight Release 5.3.16657 (2022-04-29)

## Important Notes

Baselight 5.3 no longer supports the following legacy hardware and OS platforms:

* Baselight FOUR and Baselight EIGHT systems
* DVI-to-SDI Convertors or Combiners performing that function
* RME Hammerfall audio cards
* Tape deck control within Baselight (the standalone VTRE application remains available)
* Spirit telecine control
* NVIDIA Quadro NVS 450 GPU (as a User Interface display card)
* macOS 10.14 and earlier

Generation V systems using DVI-to-SDI Convertors or Combiners need to either be upgraded to the Baselight Ultra High Definition option (see data sheet) which includes an AJA Kona 4 PCIe card or revert to GPU DVI output. Earlier generation systems are now constrained to a GPU DVI output only.

Please contact Baselight support to discuss upgrading from a NVS 450 if required.

FilmLightOS 8 or later is required to use GPU JPEG 2000 acceleration with NVIDIA Ampere GPUs

Truelight Player (tl-player) is no longer available.

When running Baselight CONFORM or Daylight on macOS 11.x Big Sur with AJA devices, AJA Software v16.x is required.







## New Features Since Baselight 5.3.16616

### Apple Silicon

*   Baselight now natively supports Apple Silicon hardware in M1 Mac systems.

    This is the first release of Baselight offering this support; please contact baselight-support@filmlight.ltd.uk if you encounter any unexpected issues on Apple Silicon hardware.

    Please note that support for the following functionality has not been made available by the respective 3rd-party suppliers:

    * ARRIRAW decoding using the older (v5) ARRI SDK
    * CineForm reading
    * BMD Cintel reading
    * Sony MPEG-4 SStP reading and writing
    * Sony XAVC writing.

### Marks View

*   Added a new view for viewing/editing marks in the timeline.

    This view comprises 2 main sections. On the left is the marks list section that displays all the marked frames in the scene. On the right is a section for editing marks at the current frame.

    By default, each mark entry in the marks list shows summary icons indicating the types of marks at that frame:

    S - Indicates shot marks G - Indicates grade marks T - Indicates timeline marks

    At the top of the marks list is a toggle button which can be used to expand the mark entries to include more detailed information for each mark (category indicator and any note text).

    The mark edit section on the right contains tabs for the 3 mark types. If there is a mark of a specific type at the current frame, the corresponding tab text will be displayed blue.

    These tabs can be used to edit existing marks, as well as adding new marks (of the selected tab type) using the 'Create Mark' controls at the bottom of the section.

    By default, the Marks View selection follows the current cursor frame. When the cursor lies on a marked frame, the mark entry in the marks list will be highlighted in blue. When the selection is following the cursor, the 'Follow Cursor' toggle button at the bottom of the view will be enabled.

    Explicitly clicking on a mark entry will select it and disable follow cursor button. The explicitly selected mark entry will be highlighted in grey.

    Once a mark entry has been explicitly selected, the cursor can be warped to that selection using the 'Warp Cursor > Selection' button. Alternatively, the cursor can also be warped directly to a mark entry by holding down the 'Ctrl' modifier while clicking on it.

    The selection can be set back to follow the cursor by re-enabling the 'Follow Cursor' button.

    The top of the Marks View also contains controls for filtering which marks are displayed in the Marks View as well as the timeline itself \[bug 53862]

### IMF Audio Tracks

*   IMF packages can now be created with an arbitrary number of audio tracks, making it possible to create more complex audio track arrangements than before. For IMF deliverables, Render View now has a list of audio tracks. The number of channels, channel mapping, channel labels, language, etc can be configured per track.

    Descriptive notes can be added per track and will be stored as annotations in the CPL metadata. This makes the notes persistent and available when creating supplemental packages.

    The Audio Content Kind setting has been moved out of Codec Parameters and is now a separate setting populated with a selection of common values.

    Supplemental IMF audio tracks are handled using one of four different modes:

    * New: Renders audio for the full duration of the supplemental package and creates a new audio track in the Supplemental CPL. No resources are referenced from the Master package.
    * Remove: A track present in the Master CPL using this mode will not be present in the Supplemental CPL.
    * Update: Any modified audio will be rendered and used by the Supplemental CPL. Unmodified audio will be referenced from the Master package.
    * Preserve: A track present in the Master CPL will be present in the Supplemental CPL, but no new audio will be created. This setting can be used to avoid unintentional changes to audio. The duration of the Supplemental CPL must not be longer than the Master CPL when using this mode \[bug 58363]

### SDK Updates

* Updated to RED SDK 8.2.2. This includes fixes and performance improvements \[bug 60305]
* Updated to Canon RAW SDK 2.7. This adds support for Canon EOS C70 and future cameras \[bug 58960]
* Updated to OpenEXR SDK 3.1.5. This improves behaviour with damaged and non-conforming OpenEXR media which was previously reported as unreadable \[bug 60270]
* The libraw library, used to decode camera RAW files, has been updated to version 202110. This adds support for additional cameras and formats, notably Canon EOS R5 \[bug 60414]

### Kona/Blackmagic Design

* Added support for fast firmware switching on AJA Kona 5. Two Kona 5 cards will be visible in the Setups View. Select the 8K card when using 8K setups and the other Kona 5 card when using setups that require 3G A or B signalling \[bug 58266]
* Added support for embedding static HDR metadata in SDI and HDMI signals on Blackmagic Design devices that support it. This means that PQ and HLG signals will be correctly reported \[bug 59894]
* Added support for Blackmagic Design DeckLink Studio 4K devices \[bug 59805]
* Added support for 12 bit RGB output from Blackmagic Design devices that are capable of this format \[bug 56746]

### Miscellaneous

* Added an option to 'Expand Sequences to Stills' to view individual images in a sequence. Be aware that this option when used on folders with large sequences will cause a thumbnail for each frame, which can add a delay to thumbnail generation \[bug 29836]
* The LUT operator now supports CLF (AMPAS/ACES Common LUT Format) files, which are a standard way to encode 1D LUTs, 3D LUTs and/or a variety of formula-based colour transforms. All CLF 3.0 features are supported except "halfDomain" and "rawHalfs" \[bug 38782]
* Added "Insert At Sequence Timecode" option to FLUX Manage View, which causes media to be inserted at the location of its timecode on the timeline \[bug 57158]
* Shot selection options are now consistent between views. To view selection options, right-click in Cuts View, Shots View, or Gallery. The main Select menu has been updated and the redundant 'Select/Deselect All Shots' menu item has been removed \[bug 53705]
* Playing or scrubbing movies with audio in FLUX Manage now plays audio \[bug 42275]
* On macOS, Apple ProRes encode and decode now uses hardware acceleration when available \[bug 59903]
* Playback fps is now shown on Playback Monitor View \[bug 59768]
* FLUX Manage progress dialogs, e.g. when preparing a copy, now show text on multiple lines to aid readability \[bug 59770]
* Added options for AAC encoded audio at bitrates 256kbps and 320kbps when writing to QuickTime/MP4 \[bug 60000]
* Improved support for the Tangent Bt Panel, use the button above B to now change pages of controls \[bug 58893]
* Added "Track at viewing resolution" option to the tracker. When the viewing resolution is wider than 4096 pixels, deselecting the option will use a scaled down version of the image to perform the track \[bug 59556]
* Added Compatibility controls to ProRes RAW Params operator, to allow decoded images to match those from other software which decodes Apple ProRes RAW media differently \[bug 60021]
* Tracking is now faster on multi-GPU systems than before \[bug 60045]
* Added a 'skewed' indicator to flioinfo which appears if concurrent access to the underlying storage is detected during measurement; the disk\_performance diagnostic also warns about concurrent access \[bug 60001]
* A new screen layout can now be selected during application startup by clicking the Options button \[bug 60173]
* A new "Network Connectivity" diagnostic is included to check network issues including MTU mismatches \[bug 57001]
* The cursor is now automatically hidden if it is over the image when playback starts. It will reappear when playback stops or, if the mouse/pen moves during playback, it will switch over to the UI monitor \[bug 54900]
* Improved indication and control over audio monitoring level in the Audio Monitoring View \[bug 60190]
* Added "Clear Poster Frame" to the Navigate menu. This will clear the poster frame of the current shot to the default poster frame. If group grading is enabled, it will clear all of the poster frames within the group \[bug 57103]
* Added "Modify Categories" to the Marks menu \[bug 55409]

## Bug Fixes Since Baselight 5.3.16616

* The Baselight cache directory diagnostic now includes the cache directory name when reporting success or failure \[bug 59671]
*   The flos-tools package (for FilmLightOS 6.4) has been updated to 6.4.16095. fl-config-master now has a 'panel' clause available for blackboard interface lines in cloud.cfg. This can be used to configure support for Blackboard Classic panels. Add "panel " to the line, where is the MAC address of the particular Blackboard. For example (on one line):

    interface eth1 blackboard mac 00:01:02:03:04:05 panel 05:04:03:02:01:00

    This matches the functionality on FilmLightOS 8 \[bug 58651]
* "fl-report -detect" now uses ssh instead of rsh, for compatibility with FilmLightOS 8. It can now better detect HTTP connections on Baselight TWO/X systems \[bug 60040]
* Fixed Adaptec firmware check when using 8TB or 12TB drives \[bug 59712]
* fl-diag now properly runs the correct set of tests on Linux systems that are not running FilmLightOS. In addition, the fl-diag "-list" option now only shows tests that are appropriate for the machine instead of all tests for all platforms \[bug 60180]
* Fixed database backup diagnostic errors \[bug 59720]
* Fixed an intermittent issue that could prevent audio monitoring from working \[bug 59680]
* Setting the Scene Audio type to 'File or Movie' or 'Stems' without selecting a file now produces an improved error message \[bug 53755]
* Improved performance when a scene is set to use Apple ProRes caching but timeline caching is disabled \[bug 56954]
* Fixed "Warning: calling nels(a NULL)" error which could sometimes appear in the console when loading some AAFs (bug 59813)
* Fixed option to select SDI card as an Audio Output when "No External Output" is chosen as Video Output \[bug 59791]
* Fixed issues with inserting control points in Curve Grade when hue is on the x-axis \[bug 56441]
* Fixed issue on macOS with the Slate diagnostics failing when a Slate is connected \[bug 59694]
* Fixed issue with audio playback when switching between cursors in different scenes \[bug 59980]
* Fixed crash reading OpenEXR media with "autodeskColorSpace" metadata set to "LogC (v3-EI800) / Film" \[bug 59835]
* Fixed crash in flit-daemon during interface negotiation \[bug 59942]
* Audio played while scrubbing now applies the Audio Display Offset configured in Setups \[bug 60005]
* Fixed issue with audio sync when changing the cursor position \[bug 59939]
* Fixed Sequence operator not showing the correct Frame Rate and Field Order for single-channel (monochrome or matte) media \[bug 60018]
* Fixed issue with audio playback when Audio Display Offset is set to a large value in Setups \[bug 60022]
* Fixed issue that could prevent renders of Dolby Vision Mezzanine MXF files when using shot start frame (%E) in the filename \[bug 59984]
* Fixed issue with the desk service taking a long time to stop \[bug 59925]
* Reduced audio glitches on the SDI output during playback \[bug 60032]
* Fixed issue with the Slate UI being offset \[bug 27657]
* The FLUX Manage "Remember These Settings For Future Copies" option now correctly persists across application restarts \[bug 59965]
* Fixed potential (gallery related) crash on shutdown \[bug 42663]
* Fixed issue with Shapes where removing the last "Shape Motion" keyframe would unlink the tracker \[bug 59794]
* On FilmLightOS 6.4, Baselight now edits /etc/sysctl.conf to change the net.ipv4.tcp\_tw\_recycle setting to 0. The previous value was causing connections from MacOS systems to occasionally timeout \[bug 59528]
* Renders that would result in a DCP or IMF deliverable being split over multiple directories will now fail during pre-render \[bug 47959]
* Fixed issue where some QuickTime files were not recognised \[bug 60115]
* Fixed Kona 4 HDMI outputting black when RGB is selected in conjunction with quadrants transport \[bug 60019]
* Fixed crash in FLUX Manage View when changing selection while previewing \[bug 60123]
* On macOS, scrolling with a trackpad or mouse wheel is more precise \[bug 58834]
* Fixed crash inserting a Subtitles operator \[bug 59926]
* Improved error message when an image is on an unknown volume, e.g. when it is needed in a Burnin \[bug 60121]
* The burnin set on Cursor View is now saved and restored with the scene/job cursor settings \[bug 60167]
* Fixed direction of the desk encoders for Dolby Vision Trim secondary hue controls \[bug 60007]
* Denoise picking now limits the pick area to the pixels that will be measured, and the analysis is now considerably faster \[bug 59605]
* Improved playback startup behaviour, particularly when using high-resolution compressed media (e.g. 8K UHD Apple ProRes) \[bug 59918]
* Addressed issues related to rendering and tracking hanging when working with 8K RED media on Linux \[bug 59917]
* Reduced audio glitches on the SDI output during playback \[bug 60032]
* Fixed issue with audio sync when changing the cursor position \[bug 59939]
* Fixed a "Scene is older than this software version" error that could occur when opening scenes that were upgraded from 4.4m1 \[bug 57564]
* Removed some spurious shell output from bl-import on el8 platforms \[bug 60161]
* Fixed audio glitch on the Linux SDI output at playback startup \[bug 60077]
* Fixed issue where the pixel aspect ratio was not written into encoded DNxHR. This fix also changes the encoded codec id for DNxHR media at resolutions 1280x720 and 1920x1080. This fixes a problem with linking DNxHR QuickTime output files into Avid Media Composer \[bug 60099]
* Fixed crash when using Apple ProRes RAW media on macOS, e.g. when enabling Clamp Negative Values \[bug 51436]
* Fixed right-aligned burnin text horizontal position jiggling at some font sizes \[bug 60048]
* Fixed issue with HDR metadata not updating correctly on HDMI output from AJA SDI devices \[bug 58632]
* Fixed a rare "overlapping strips" crash which could occur in Multi-Paste \[bug 59526]
* Fixed incorrect frame numbers shown in some messages in Playback Monitor View \[bug 60120]
* Fixed problem archiving scenes with a trailing slash on their scene container \[bug 60178]
* Fixed an issue with loading saved conform presets that caused media scans to fail \[bug 59885]
* Fixed an issue that could cause out of date diagnostics from a FLUX Store system to be reported on other systems \[bug 59909]
* Reduced GPU memory usage on multi-GPU systems \[bug 60207]
* Improved Reference Timecode fps given to sequences that have ambiguous timecode rates; it will now use the scene's Start Timecode fps if that is valid for the media's timecode \[bug 60259]
* Fixed an issue where some scenes could cause the application to hang when opening Render View \[bug 60236]
* Fixed incorrect scaling of thumbnails for ARRIRAW HDE sequences \[bug 60117]
* Fixed crash in the tracker widget when deleting trackers with a "Missing tracker strip" message \[bug 57911]
* Fixed failure when submitting an operation to a remote queue when the machines each have a "virbr" interface with the same IP address \[bug 60303]
* Fixed problem licensing Archiving option \[bug 60304]
* Improved colour space and exposure of DJI DNG media \[bug 57252]
* Fixed the list of Masks presented in Render View for a Dolby Vision scene that has older Dolby Vision Analysis strips without L5 mask options \[bug 60313]
* The list of Masks presented for a Dolby Vision scene that uses L5 now includes all format masks, to allow a Dolby Vision scene to be rendered with content mapping and a smaller mask \[bug 60341]
* The "Input Area" mask option no longer crops the image to the Working Format after mapping from the Input Format; in particular this addresses issues with the resolution of deliverables using "Crop Image to Mask" \[bug 59864]
* Disabled client note editing in read only scenes \[bug 60352]
* Fixed DSpot reset indicator when used in a layer \[bug 60369]
* Fixed bug where Client Views connected to machine "B", following a scene open on machine "A", would not update correctly when client notes were modified on machine "A" \[bug 59181]
* Cached strips now accelerate Dolby Vision analysis when using "Selected Analysis Strips" or "Entire Scene" \[bug 60367]
* Fixed issue where trackers would be unlinked after doing copy, delete and paste of a strip \[bug 60281]
* Fixed crash with some RED media on macOS \[bug 60228]
* Maximum driver version for the NVIDIA GTX 980 series GPUs on FilmLightOS 6 is now 418.56 \[bug 60283]
* Removed the driver version limit for the NVIDIA GTX 980 series GPUs on FilmLightOS 8 \[bug 60427]

## Known Issues

* When running Baselight CONFORM or Daylight on macOS 10.15 Catalina, local volumes which are defined in volume.cfg within /Volumes can result in "Stale NFS file handle" errors. This is due to a bug in macOS. To work around this issue:
  * open System Preferences from the Dock or the Apple menu
  * choose "Security & Privacy"
  * click the padlock icon and use your password or Touch ID to allow changes to be made
  * select "Full Disk Access" in the list on the left
  * click the "+" button on the right to open a file browser
  * on your keyboard, press "/" to open the "Go to the folder" dialog
  * enter "/sbin" and click "Go"
  * select the file called "nfsd" and click "Open" After restarting your Mac, the volume(s) should now work correctly \[bug 53073]
* Saturated areas in Photo RAW files can acquire a colour tint when adjusting the exposure slider in the Photo RAW Parameters operator while blending highlights \[bug 44769]
* Baselight 5 enables GPU acceleration in OFX plugins. This improves performance but may introduce new issues depending on the 3rd-party plugin implementation \[bug 47224]
* Canon RAW media added to scenes in Baselight 5.1.10836 or earlier using the tone curve setting "Canon Log" may now fail to decode with an error message stating "Invalid function parameter". Changing the tone curve will allow images to decode, but will change their look \[bug 50371]
* Setting the Resampling Method in a strip to "Optical Flow" will force a transform to the scene's Working Format, similar to the "Process in Working Format" option. Please consider this when rendering to formats larger than the Working Format \[bug 54652]

***
