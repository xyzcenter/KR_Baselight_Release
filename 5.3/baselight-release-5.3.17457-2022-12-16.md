# Baselight Release 5.3.17457 (2022-12-16)



## New Features Since Baselight 5.3.17366

### Frame.io Integration 1.1.13

*   A new version of the Frame.io Integration is available.

    To install the update, open Scripts View, select the 'Packages' tab, choose the 'filmlight-frameio' package, and click Upgrade Package.

    Please note: Do not upgrade if you currently have scenes with active Frame.io assets.

    The Frame.io upload dialog now supports folder-level selection and creation, and the download dialog now supports folder-level selection.

    Uploading multiple shots as individual files is now possible. If the selected Deliverable Preset generates multiple uniquely-named files, typically a file per shot, these will be uploaded separately.

    It is now possible to select what is uploaded to Frame.io using the Selections menu to choose between Selected, Current Shot, Category or Filter. This allows upload of a subset of shots as multiple files, or a range of shots as a single file for review.

    * Use the 'Metadata' setting when creating a Deliverable Preset to define whether the upload files contain Rec or File Timecode. You may want to use the File option when uploading multiple files like dailies, to maintain original timecode.
    * To upload selections as multiple files, ensure that the Deliverable Preset generates unique filenames for each file.
    * For a single file upload, like a programme approval, you may prefer to use Rec Timecode to match your scene.

    A new "Manage Asset References" menu is on the Frame.io Actions menu with the following commands:

    * Scan for Missing Asset References This will find any assets that are in the scene but no longer available in Frame.io due to deletion or archival. These references can be deleted.
    * Delete All Asset References This removes all asset references from the current scene \[bug 62300]

### Conform

* Support added to read timeline and Locator marks from CMX EDLs. Use the Apply Marks setting to control if marks should be used. In EDLs timeline marks use the selected Baselight category while Locators use the colour category specified in each locator. The results of any marks found are reported in the summary area \[bug 41142]
* Conforming an Avid AAF will now use the assigned Avid Locator colours for both timeline and shot marks. By default the Baselight marks are assigned to categories that match the Avid colours. The results of any marks found are reported in the summary area \[bug 60704]
* New dialog Assign Mark Categories, available from Conform View when applying marks, or from the Marks menu. Use this menu to map colour named marks to other Baselight mark categories so when a conform is completed any assigned mark categories are automatically applied \[bug 60808]
* Added option to toggle the layout of Media Settings/Summary in Conform View between top/bottom and left/right. Using left/right is helpful to show all the settings while configuring a conform, the default is top/bottom and the current layout is remembered \[bug 60814]

### Dolby Vision HDMI tunnelling

*   Support has been added to the application to enable Dolby Vision output on compatible televisions using an HDMI output from a compatible AJA device.

    The following AJA devices have been tested and verified as being compatible with Dolby Vision HDMI tunnelling: Kona 4, Kona 5, Io 4K plus, T-TAP Pro.

    To activate Dolby Vision HDMI tunnelling:

    * A scene must be configured to use Dolby Vision.
    * The signal type in the setup must be set to Dolby Vision.
    * A viewing colour space matching the configured Dolby Mastering Display must be used in the cursor.

    When all of these conditions are met, a Dolby Vision signal will be sent to the television otherwise an 8 bit RGB signal will be sent.

    Limitations: SDI output is not supported when using HDMI tunnelling.

    Not all Dolby Vision enabled televisions are compatible with tunnelling and we are not able to guarantee or provide any list of supported devices. (For further details please contact Dolby)

    HDMI Tunnelling should only be used to review the final effect of trims on a consumer device and should never be used as a reference device when applying or editing trims.

    For more information on Dolby Vision HDMI tunnelling, please refer to https://professionalsupport.dolby.com/s/article/HDMI-Tunneling \[bug 53974]

### Miscellaneous

* Added "Fujifilm: F-Log2 / F-Gamut" colour space to FilmLight website \[bug 62083]
* The Interleaved / Discrete setting now appears in Render View for QuickTime deliverables using 5.1 + 2.0 channel audio. The Discrete option will produce a file with a single channel per track with the default audio channel labels being Left and Right for channels 7 and 8 respectively. The Interleaved option will produce separate 5.1 and 2.0 audio tracks as before \[bug 61335]
* Added a "%C" button to browser tabs in FLUX Manage View, to go to the current scene's container \[bug 61534]
* fliotest output values are now given in MiB/s \[bug 61566]
* The "Compiling shaders" phase of the Linux installer is now considerably faster when upgrading from a previous build \[bug 61670]
* Added "Update all cursors to use these settings" and "Update all cursors in the same gang group to use these settings" to the Cursors View action menu \[bug 61681]
*   The flioinfo tool has some new options to improve results when testing performance of network filesystem mounts:

    \-t Can be used to increase the test time from the 10s default. This is useful when read performance is significantly faster than write performance

    \-d This option instructs flioinfo to drop the system buffer cache before each test (Linux systems only)

    \-p This option instructs flioinfo to run the given script before each test pass. This is a more powerful version of -d, and can be used to run a script that clears the buffer cache on the server

    \-r This option sets the number of parallel threads to use when reading the file sequence. It can be specified multiple times. The default is to test with 1, 2 and 4 threads \[bug 61567]
* Added read support for additional codecs in QuickTime files \[bug 61843]
* Added Quarter Bumps (Shift + Numeric Keypad Bump Key). Base Grade Numeric Keypad Mode (in "Customise") can now specify its usage ("RGB | CMY" or "Custom Bumps | Zone Selector") \[bug 61631]
* Dialog boxes for Change Container, Change Timecode Rate, Mismatched Rates and Apply LUT now include a Cancel button to stop the action \[bug 55118]
* NVIDIA driver version 510.85.02 is now accepted without warnings from fl-diag or the installer \[bug 62443]
* Updated to ARRI Image SDK 7.0.4. This addresses some minor bugs and memory issues \[bug 61719]
*   Updated to Blackmagic RAW SDK 2.6. This includes the following:

    * Support for Blackmagic RAW media from these cameras:
      * Blackmagic Design Pocket Cinema Camera 6K G2
      * Fujifilm GFX100, GFX100S and XH2s
      * Panasonic Lumix GH5S, BS1H and BGH1
      * Leica SL2-S
    * Improved white balance accuracy for Panasonic S1H, S1, S5

    PLEASE NOTE: this version of the Blackmagic RAW SDK is not compatible with FilmLightOS 6.4. Blackmagic RAW media is therefore no longer supported on FilmLightOS 6.4. Please contact FilmLight Support to discuss upgrade paths to FilmLightOS 8 \[bug 58995]
* Exported Dolby Vision Metadata v4 now includes a "Level6" (MaxCLL and MaxFALL) entry with zero values, to match v2.9 behaviour and satisfy certain downstream QC tools \[bug 56297]
* On a Blackboard Classic display added the hostname of the connected Baselight system (Blackboard Classic firmware update needed) \[bug 58721]
* Frame.io download dialog now supports folder-level selection \[bug 62189]
* Frame.io upload dialog now supports folder-level selection and creation \[bug 61502]
* Many improvements have been made to OFX plugin support, including:
  * Cuda and Metal rendering is now supported in many plugins
  * Reset buttons are shown for each parameter
  * Improved tooltips
  * Plugins can now show and hide parameters dynamically
  * Stability fixes \[bug 62164]
*   Added "Increment" option for custom Integer metadata columns.

    This allows values in an Integer column to auto-increment per frame across a sequence. These values can be used in burn-ins and in filename expressions for renders.

    To enable the Increment option, right-click on a custom Integer column heading in Shots View and select the "Set Increment" option. Setting the value to 1 will increment the value by 1 for each frame in the sequence \[bug 62327]
* Added a button to Conform View to reset individual media filters, and also included a reset in the Sequence Filter dialog by selecting Do Not Apply \[bug 51047]

## Bug Fixes Since Baselight 5.3.17366

* Added filtering to Tangent Elements Kb panel to prevent accidental selection by touching an encoder \[bug 61038]
* Fixed bug that would cause burnin edit controls to be drawn over the wrong image in 2x2, 3x3 etc. layouts \[bug 61318]
* Fixed bug which would cause thumbnails to be drawn incorrectly in the Shape operator's Quickshape menu when a Blackboard/Slate is connected \[bug 61405]
* Moved the option to 'Goto This Shot' out of the 'Navigate' submenu within the right-click menu of Cuts View \[bug 61407]
* Fixed incorrect results from multiple-deliverable renders where deliverables have different Bypass Categories \[bug 61408]
* Fixed issue with Gallery export and import whereby it would incorrectly perform staging at /tmp when /vol/images is available and wouldn't notify if writes to the archive failed in the summary dialog \[bug 59868]
* Fixed Ctrl-Alt-Arrow shortcuts on modern Linux platforms \[bug 61942]
* Fixed a crash on exit after using GPU JPEG 2000 acceleration \[bug 61478]
* Fixed occasional failure in scopes when in Wipe Layout \[bug 61572]
* Fixed issue that could cause IMF package renders to fail after switching between output types in Render View \[bug 61591]
* Fixed crash when accessing very large images \[bug 54259]
* Marks added using the right-click menu in the Timeline are now added at the current cursor position. Added separate options to add a Mark to Grade, Shot and Timeline \[bug 54215]
* Reduced occurrences of "exclusive access to SDI" error messages \[bug 61632]
* Fixed "Attempting to add duplicate item" warnings on console when the "Database hosts" preference contains hosts that are also discovered on the local network \[bug 61535]
* Fixed Kona 5 UHD 120p display mode \[bug 61739]
* Added support for the indexing of AWS S3 storage that is mounted as a volume \[bug 61774]
* Legacy codecs IMX, MPEG 30, MPEG 40 and MPEG 50 are no longer available as options in Render View \[bug 47052]
* Fixed issue with some AVC-Intra 4:4:4 12-bit MXF files being decoded incorrectly \[bug 61853]
* Fixed delay in image update when turning overlays off/on from Cursors View during playback \[bug 61776]
* Fixed an issue with indexed volumes for EXR sequences with channels that are not present in the first few frames \[bug 59387]
* Fixed behaviour when viewing other eye in stereo scene in Dual Output Layout \[bug 61880]
* Fixed crash when inserting gestural overlay \[bug 61881]
* Improved behaviour of display menu so that you no longer need to restart software when changing between stereo and mono video modes \[bug 61917]
* Fixed issue in the perspective operator where the overlays would not update correctly during playback \[bug 61775]
* Improved message in Marks View when parked on a client mark not present in the current/bottom stack. Also added Timeline right click context menu option to delete client marks \[bug 61926]
* Fixed crash when the scratchpad grabs an original version with copy protected input strips \[bug 58441]
* Fixed issue with missing audio channels and broken audio in MXF files containing multiple audio tracks with multiple channels \[bug 62068]
* Fixed issue with Histogram or Scopes not clearing when the last scene in the application is closed \[bug 62008]
* Improved Colour Space Journey View warnings relating to ARRI ALF-2 DRT \[bug 62129]
* Fixed crash when releasing and reacquiring SDI devices on macOS \[bug 62118]
* Fixed "File is not an image file" error when reading DWA-compressed OpenEXR media \[bug 62104]
* Dolby Vision Metadata export now correctly uses Image Area (L5) metadata from the lowest Dolby Vision Analysis strip in each shot's stack \[bug 61814]
* Fixed issue which could cause long delays when Look files are accessed on some network filesystems \[bug 61563]
* Fixed crash when reading ARRI media that has missing or zero pixel aspect ratio metadata \[bug 61782]
* Fixed Stereo output modes on Blackmagic Design SDI devices \[bug 62154]
* Fixed Audio Corruption on some Blackmagic Design SDI devices \[bug 62035]
* Fixed crash starting Baselight from bl-setups \[bug 62176]
* Fixed occasional crash starting playback on macOS \[bug 62060]
* Improved support for ShaderToy GLSL shaders \[bug 61763]
* Fixed an issue in indexed XFS volumes that could prevent new directories from being added to the index \[bug 61929]
* Fixed issue reading QuickTime movies with ima4 encoded audio \[bug 61413]
* Improved behaviour when there is an error in cloud.cfg or volume.cfg configuration files \[bug 62211]
* Fixed issue with audio caused by invalid Dolby Atmos parameters \[bug 62226]
* Fixed issue with the Audio Display Offset setting in Setups not having any effect \[bug 62239]
* Fixed issue exporting CMX EDLs that could cause the Shots View to hang \[bug 62096]
* Fixed crash when previewing audio-only media in FLUX Manage View \[bug 62112]
* Fixed restrictions applied to Display View picking after picking an area in a Denoise operator \[bug 61837]
* The application installer on Linux no longer automatically creates volume.cfg if there is no /mnt/disk1/images1 directory \[bug 54938]
* Fixed issue where removing a keyframe in paint would unlink its tracker \[bug 62130]
* Fixed a bug which could potentially cause a crash when scrubbing a Shape operator with multiple control points selected \[bug 62273]
* Improved behaviour when volume.cfg references an unknown zone \[bug 25076]
* Fixed "FLAPI: Couldn't save sessions" error when quitting the application \[bug 53910]
* Stopped Scratchpad recall original version from using paste protection categories \[bug 55137]
* Fixed issue preventing decode of some DNxHR 444 encoded QuickTime movies \[bug 62343]
* Grid Warp no longer tries to put the grid back in the same place after a new plane creation \[bug 62312]
* Added options for 48, 50, 59.94 and 60 fps timecode rate in Audio Sync View \[bug 62266]
* Fixed a problem where incorrect SDI options were presented in the Setups view if the Primary Video Output had been changed \[bug 61268]
* Fixed issue with some SDI modes on Kona 5 after a firmware switch \[bug 62268]
* Fixed an issue where an invalid SDI setup could lead to a difficult to escape loop \[bug 58470]
* The "PCI card slots" diagnostic module has been removed to resolve issues when a NVIDIA ConnectX-6 Ethernet adapter is installed in Baselight TWO/X systems \[bug 62420]
* Enabled flit-daemon on macOS 13 Ventura \[bug 62534]

***
