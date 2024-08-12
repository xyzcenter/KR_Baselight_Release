# Baselight Release 6.0.20910 (2024-08-08)

## Baselight Release 6.0.20910 (2024-08-08)



## Important Notes

Baselight 6.0 no longer supports **FilmLightOS 6**. Please contact [FilmLight Support](mailto:baselight-support@filmlight.ltd.uk) to discuss upgrading to FilmLightOS 8. Bug 60176

**RED Rocket** hardware is no longer supported. Bug 65725

Using a **Grade Result Colour Space** is deprecated and this functionality may be removed in a future release. [Please watch this video](https://filmlight.ltd.uk/graderesult) for information about recommended workflows for telecine-style grading. Bug 64729

**Dolby Vision external CMU devices** are no longer supported. Bug 62581

The **vtre** application is no longer included. Bug 66448

Many colour spaces have been updated with higher precision matrices. Scenes upgraded from Baselight 5.3 will use the older colour spaces and warn about that in the console. Visual output is consistent between original and new colour spaces. Bug 67302



## New Features Since Baselight 6.0.20612

### JPEG-XS Caching

*   A new JPEG-XS timeline cache compression option is available on Linux. The compression significantly reduces the disk bandwidth required for cached playback, so it is particularly useful when working at high resolutions such as UHD8K, at high frame rates and/or when the cache is located on non-solid-state drives.

    JPEG-XS caching is an optional purchase due to the codec SDK licensing fee; please contact your FilmLight sales representative to discuss. Bug 61823

### Flexi Effects

*   #### Face Tracker and RIFE Retimer

    These Machine Learning effects are now supported on the Intel Mac platform. The effects will need to be installed on the system using the filmlight-flexi-effects installer, which is available in the support section of the FilmLight website. Bug 66459
*   #### MiDaS Depth Map

    MiDaS Depth Map is now available as an additional Flexi installer, serving as an example Flexi effect.

    MiDaS computes relative inverse depth from a single image, using a Flexi effect to run the machine learning algorithm. This effect will need to be installed on the system using the midas-flexi-effect installer, which is available in the support section of the FilmLight website.

    It can be added from the "Insert" menu by choosing "Flexi Effect" or via "Flexi Effect" in the layer operator grid. MiDaS is particularly useful when used in conjunction with the Bokeh operator, as it provides per-pixel depth information which can be used to drive the amount of Bokeh. Bug 67398

### FilmLight REMOTE

*   FilmLight REMOTE is a new application for receiving network video streams (encoded as HEVC or JPEG-XS) from FilmLight products. It supports local colour management of the video streams, and output via AJA and Blackmagic Design SDI hardware.

    It can also integrate with NICE DCV for remote operation of Baselight or Daylight systems.

    Please see the included FilmLight REMOTE User Guide in the Baselight Help menu for more information on its configuration and usage. Bug 61988

### Image Viewer

*   The Image Viewer is a new view that mirrors the SDI output on a UI monitor. It supports interaction with operator overlays, allowing creation/editing of shapes, painting on the image etc. without the need to switch the cursor over to the SDI.

    The Image Viewer can be popped-up/floated from the "Views" menu. There is also a new "Image Viewer" workspace that's pre-configured with a docked Image Viewer. Ctrl+F8 can be used to toggle a full screen Image Viewer on the primary UI monitor (regardless of whether it's currently visible in the UI).

    While the Image Viewer is visible in the UI, the SDI output can be switched to "Clean Output" mode. When Clean Output mode is enabled, the SDI will always display an image rendered from the bottom of the stack, regardless of the render line position, bypass mode etc. Clean Output can be enabled/disabled from the "Display" menu. It can also be mapped to the Slate and Blackboard 2 via the "Toggle Clean Primary Output" action in Chalk.

    Image Viewer is not enabled by default. The Image Viewer is enabled in Display > Image Viewer in the Baselight Preference, please check the help text for further information. Bug 61988

### Workspace Switching/Cycling

*   The F8 key now toggles between the last 2 selected workspaces. Holding the "Win" key and pressing F8 cycles through the available workspaces (Win+Shift+F8 cycles through the wokspaces backwards).

    On the Slate and Blackboard 2, there is an equivalent custom button available from Chalk in the "Workspaces" button category: "Toggle/Cycle Workspaces". Once mapped, it will either toggle between the last 2 workspaces, or cycle through the available workspaces if the desk's "Windows" key is held down. Bug 61988

### Timeline Improvements

*   Added the ability to merge tracks to the track panel's right-click menu. The available options are:

    * Merge In Track Above
    * Merge In Track Below
    * Merge In All Other Tracks.

    All these options obey grade locking - any merging will occur only up to and not including the first grade locked track. Bug 66357
* In Timeline Alignment view, added the "Create New Tracks" setting to give users the option of not creating new tracks when aligning the timeline, thus restoring the behaviour seen in previous versions of Baselight. Bug 67574
* In Timeline Alignment view, added option to "Remove Gaps in Stacks". When turned on, this option will remove all vertical gaps within a stack. It is especially useful when cleaning up a timeline after tracks have been merged. Bug 60211
* By default, the cursor is now centred in the Timeline View during playback, unless the playback range fits completely in the area between the scroll regions. Cursor centring can be disabled using the new "Centre cursor during playback" preference. In addition, the speed of the animation which centres the cursor when playback starts can be controlled with the "Centre cursor during playback animation length" preference. Bug 61283
* The "Horizontal jump scrolling" preference is now turned on by default, making Baselight's default scrolling behaviour more familiar to new users familiar with other systems. Bug 68651
* In Timeline Alignment View, changed "Derive Tracks" to "Derive Alignment" to prevent confusion now that Baselight uses the word "Track" in lots of other places in the UI. Bug 68626
* Added "Minimum Track Height" preference to allow the user to control how small the track name text and icons get when zoomed out vertically in the Timeline. The default setting allows the track text to reduce slightly in size when zooming out, but if this isn't desired, a value of 1.0 will ensure that track text and icons always stay the same size. Bug 67305
* In the track panel right-click menu, the "Move Track Up" and "Move Track Down" items now obey the "Allow Vertical Movement of Grade-Locked Strips" preference. Similarly the "Remove Track" and "Remove All Empty Tracks" options now obey the "Allow Removal of Grade-Locked Strips" preference. Bug 68703
* Improved the behaviour of binary strips used as part of a stack when edit locking is turned on. Now, a binary strip will be treated as a grade strip (and hence subject to grade locking rather than edit locking) if the timeline extent of its first input lies completely within the timeline extent of its second input. Bug 68396

### Editing Improvements

* Added new "Trim to Cursor" button to the Timeline Bar. When clicked with edit points visible, an edit is performed to align the edit point (start edit point if multiple edit points are visible) with the current cursor position without needing to drag use multiple keystrokes. It's also available by pressing R when in Edit Mode. Bug 68705
* When locked into Move Shot, Slip or Slide edit modes, it's now possible to drag the start or end brackets in addition to the central drag handle to affect the edit. In addition, the central drag handles are now always drawn when locked into these modes, to make it clear what can be dragged. Bug 68711
* Added "Move Cursor During Edits" option to the Timeline Bar cog menu. It defaults to on (the behaviour in previous versions of Baselight 6.0), meaning the cursor is moved to align with the edit point in the Ripple/Roll/Move Start/Move End edit modes. When turned off this no longer occurs, matching the editing behaviour of Baselight versions prior to 6.0. Bug 68592
* Added "Update Edit Points on Cursor Movement" option to the Timeline Bar cog menu. It defaults to on (the behaviour in previous versions of Baselight 6.0), meaning that locked edit points are updated to lie on the new shot when the cursor is moved. When turned off this no longer occurs, matching the editing behaviour of Baselight versions prior to 6.0. Bug 68713
*   Changed Timeline behaviour in the following ways when there are locked edit points based on an explicit (yellow) strip selection:

    * The edit points are now _never_ updated on cursor movement in this situation.
    * The current parameter strip is now _never_ updated in this situation, so that one now never gets a parameter strip lying outside the range of the edit point brackets.

    These two changes mean that the user can now safely move the cursor to lie outside the edit point range without needing to worry about the editing or selection state being unexpectedly changed. This makes Baselight 6.0 behave more like previous versions of Baselight whose editing was based on explicit selections. Bug 68712
* The "Handle Protection" and "Use Display View To Show Edit Multi-View While Editing" edit-mode menu items are now persisted between restarts of Baselight, as is the state of the snap button. Bug 68593

### Conform

* Baselight now handles image sequences and still images when conforming from FCP 7 XMLs generated by Adobe Premiere. Bug 12898
*   DaVinci Resolve expresses image sequences using a Resolve-specific syntax in the `<pathurl>` element of FCP 7 XMLs. E.g:

    ```
    <pathurl>file://localhost/some_dir/seq.[1234-2345].png</pathurl>
    ```

    Baselight now properly handles this syntax. Bug 68803

### Academy Metadata Files

* Added support for Academy Metadata Files (AMFs). AMFs are XML files which are capable of representing the precise setup of an ACES pipeline, including specifying Input Device Transforms (IDTS), Color Decision List (CDL) grades, Look Management Transforms (LMTs), Reference Rendering Transforms (RRTs) and Output Device Transforms (ODTs). Bug 31389
* AMFs can be inserted via FLUX Manage simply by double clicking the file. This will cause the Insert AMF Grade dialog, containing the following settings:
  * **CLF Directory**: Additional directory in which to look for CLF LUT files referenced by the AMF, in addition to the directory containing the AMF, which is always searched.
  * **CCC Directory**: Additional directory in which to look for CCC files containing CDL grades referenced by the AMF, in addition to the directory containing the AMF, which is always searched.
  * **Obey Applied**: Whether or not to obey the "applied" attribute associated with each transform - if "Yes" and "applied" is "true" in the AMF, then an equivalent transform will _not_ be applied in the Baselight stack generated from the AMF, because it is assumed that the input already has the transform baked in. ([https://docs.acescentral.com/guides/amf/#the-applied-attribute](https://docs.acescentral.com/guides/amf/#the-applied-attribute))
  * **Mark Working Location with Category**: The optional `<aces:workingLocation>` tag in AMFs specifies where additional look transforms should be placed if the AMF is modified. This setting allows the working location to be marked in the Baselight stack generated from the AMF using a category. Any existing strips in the stack will be placed at the working location. If not specified, the working location will be assumed to be directly after the input transform.
  * **Starting CDL Layer Number**: Settings which specify the desired layer number, strip colour and category for any CDL Grade strips inserted. (**Note**: specifying a layer number does **not** change the ordering of operators generated from the AMF.)
  * **Starting CLF Layer Number**: Settings which specify the desired layer number, strip colour and category for any LUT strips inserted to apply CLF LMTs.
  * **Starting Gamut Compress Layer Number**:Settings which specify the desired layer number, strip colour and category for any Compress Gamut strips inserted.
  * **Apply**: Allows the user to narrow down precisely what transforms in the AMF should be applied to the Baselight stack:
    * **Input Transform**: If set, will either specify the Input Colour Space of the Sequence operator _or_ insert a LUT operator if the input transform was specified with a CLF. **Note**: The input colour space will _not_ be set if the Sequence operator is in `Automatic` mode.
    * **CDL Look Transforms**: If set, CDL Grade operators will be inserted.
    * **CLF Look Transforms**: If set, LUT operators referencing CLF files will be inserted.
    * **CDL Working Space**: If set, then the CDL working space will be used to set the working space of the scene.
    * **Output Transform ODT**: If set, the cursor's Viewing Colour Space will be set.
    * **Output Transform RRT**: If set, the scene's Display Rendering Transform will be set.
* `AMF_NAME` and `AMF_UUID` columns have been added to Shots View. These columns are used to match against specific AMFs. They are also populated when conforming:
  * ALE files ([https://docs.acescentral.com/guides/amf/#avid-log-exchange-ale-support](https://docs.acescentral.com/guides/amf/#avid-log-exchange-ale-support))
  * CMX3600 files ([https://docs.acescentral.com/guides/amf/#edit-decision-list-edl-support](https://docs.acescentral.com/guides/amf/#edit-decision-list-edl-support))
* AMFs can also be inserted via Multi-Paste using the new "Academy Metadata File (AMF)" source option. When turned on, the following settings appear or are relevant:
  * **AMF Directory**: Directory in which to search for AMFs.
  * **Mark Working Location with Category**: See above.
  * **LUT Directory**: Equivalent to `CLF Directory` above.
  * **Match By**: The new `AMF_NAME` and `AMF_UUID` matching options can be used to match these columns against the metadata in AMFs.
* AMFs can also be exported from Baselight using the new "Export AMFs" option in the Shots View. This export dialog contains the following options:
  * **Description**: String describing the contents of the AMF.
  * **Author Name**: String containing the name of the AMF author.
  * **Author Email**: String containing the email address of the AMF author.
  * **Generate Clip ID**: Whether or not to generate `<aces:clipid>` metadata in the AMF. This metadata is used when one wishes to associate an AMF with a specific media file.
  * **Clip Filename**: If clip id metadata is being generated, specifies whether the full path should be written to the AMF or just the filename.
  * **Set Applied**: Whether the `applied` flag should be set to `true` in all transforms in the AMF.
  * **Working Location Categories**: Specifies the category which defines the working location in the stack, and thus where the `<aces:workingLocation>` tag will lie in the AMF.
  * **Input Space with no ACES Equivalent**: Specifies the behaviour when a shot's Input Colour Space doesn't have a equivalent ACES transform. If "Use a Fallback ACES Transform Where Possible" is set, then, where possible, a fallback transform will be substituted. A fallback transform will typically have the same colour primaries as the Baselight space, but a different, more popular tone curve, thus conveying the make of the camera which generated the input media. If there is no fallback available or if "Always generate a CLF Transform" is specified, then a CLF LUT representing the conversion from the input space to ACES AP0 linear will be generated instead.
  * **Generate Output Transform**: The `<aces:outputTransform>` tag is optional, so this setting specifies whether it is to be included. If `Yes`, then a display-referred colour space can be selected.
  * **CLF File Handling**: If the Baselight stack references a CLF file, specifies whether the AMF file should refer to the CLF in its existing location or if it should be copied into the AMF output directory and be referred to only by filename.
  * **Update Source Metadata**: Whether or not to write the `AMF_NAME` and `AMF_UUID` columns in the scene metadata. Writing the metadata is useful if one wishes to later export an ALE or CMX3600 EDL referring to the generated AMFs.

### Miscellaneous

* The libraw library, used to decode camera RAW files, has been updated to version 0.21.2. This adds support for additional cameras and formats, notably Canon EOS R8. Bug 67237
* Updated Photon to version 4.9.5. This can detect additional issues in rendered IMF packages. Bug 67366
* Updated to Blackmagic RAW SDK 4.0. This adds support for media from:
  * Panasonic Lumix G9II, GH5S and BGH1
  * Blackmagic URSA Cine 12K LF. Bug 68404
* Updated to Canon RAW SDK 2.9R5. This adds support for new and upcoming cameras, including the EOS C400. Bug 67857
* Added ability to add/create Reference and Shape inputs directly from the Matte Merge operator interface. Bug 50427
* Updated to ARRI Image SDK 8.1.0. This improves behaviour with B+W media. Bug 63602
* Updated to Codex HDE SDK 5.2.0. This significantly improves decoding speed. Bug 65128
* Added the ability to view and edit the Sequence operator's Offset parameter as source timecode in addition to the existing frames and seconds options. Bug 59317
* Enabled .cdl file export in the CDL Export dialog. Bug 59491
*   Added support for sshfs volumes to use a custom remote user. An sshfs volume by default connects as the `filmlight` user. Adding a `limit sshuser` line to `volume.cfg` allows this to be changed:

    ```
    zone mybaselight
    share testvol @servername.domain /path
    limit testvol sshuser=example
    ```

    Specifying `sshuser=$USER` will cause the ssh connection to be made as the user who is causing the volume to be mounted. This can be useful when working with Avid NEXIS for example. Please note that this mechanism only uses the user at the time the volume is mounted. If it remains mounted when another user accesses the volume, the remote access will continue to use the first user's identity.

    The diagnostic test for sshfs volumes has been extended to verify that all defined volumes can be accessed as the appropriate user.

    `fl-setupssh` has been extended with a `-U` option to specify the remote username. Bug 67579
* In Update AAF and Modify AAF workflows the output AAF filename is now used to set the name of the sequence in the AAF. Bug 67920
* Added "Slate Button Reference" documentation to the Help menu when a Slate is connected. Bug 67952
* Keep the Scope Overlays submenu in X Grade open to allow multiple items to be changed. Bug 67934
* Additional metadata is now read from ICC profiles embedded in JPEG, TIFF and PNG files. Bug 68254
* The ability to render Pixspan compressed files with an additional licence has been removed. Bug 67611
* The Edge Crop operator now shows the coordinates of the last visible image pixel/row, and also the cropped image width and height. Bug 68195
* Crash reports are now only sent by https. The older http and email options are no longer supported. See the `fl-report` tool for configuration information. Bug 68078
* Improved the appearance of media source directory path text in the Conform View for very long paths. Bug 64681
* Improved behaviour when restarting Baselight immediately after a previous run has terminated. Bug 68379
* Updated the Comprimato SDK used for GPU JPEG 2000 acceleration to version 2.8.4. This adds minor performance improvements and fixes an issue with TODO comments written to the console. Bug 68421
* On systems using FilmLightOS, the sytemd packages are updated to fix an issue that would sometimes stop the image RAID from mounting at boot time. Bug 67092
* On systems using FilmLightOS, the flos-tools, fl-network and fl-database RPM packages are updated to the most current versions (8.4.19833, 8.4-20638 and 8.2.19409). On systems not using FilmLightOS, the fl-config-master, fl-host and fl-verify-network commands have been added to the application utilities. These updates provide various fixes and new features. Release notes for these packages can be found in the documentation directory. Bug 65701
* When importing scenes in Job Manager, the name of the imported scene is now shown, the scene is now selected, and it can easily be opened. Bug 68532
* Changed default Colour Space in Stills Export to be "sRGB Display: 2.2 Gamma / Rec.709". Bug 68521
* Added OCIO config for Truelight Colour Spaces and TruelightCAM v3. The config is available as download [here](https://www.filmlight.ltd.uk/support/customer-login/colourspaces/colourspaces.php). Bug 60556
* RGBA OpenEXR deliverables can now be rendered with straight (unpremultiplied) RGB. This is contrary to the OpenEXR specification, but matches the behaviour offered by other applications. Straight RGB deliverables are written with the metadata attribute "unassociatedAlpha=1" to allow them to be identified. Bug 68347

### FLAPI

* Added new `insert_amf_stack` method to the `Shot` interface, allowing an AMF file to be applied to a shot.
* Added new `input_colour_space_derived_from_media` method to the `Shot` interface, allowing the caller to determine if Baselight was able to automatically determine the shot's input colour space from the metadata in the media file.
* Added new `aces_idt_for_input_colour_space` method to the `Shot` interface. This method returns an ACES transform URN equivalent to the shot's Sequence operator's input colour space.
* The `Export` interface now supports AMF export via the new `do_export_AMF` method.
* The `MultiPaste` interface now support AMF multi-paste.
*   In the `SceneSettings` interface converted the following attributes to use value types rather than strings:

    * `MasteringColourSpace`
    * `MasteringOperation`
    * `MasteringWhitePoint`
    * `StereoMode`
    * `TimelineCaching`
    * `HDRClipBehaviour`
    * `DolbyVisionMode`
    * `TemporalSamplingMode`

    This greatly improved documentation quality and assignment validation. Bug 68049
* Fixed `OpticalFlowQuality` and `OpticalFlowSmoothing` attributes of the `SceneSettings` interface to use the correct value type, meaning that they not longer cause internal errors on assignment. Bug 68049
* Fixed bug in `FLAPI JobManager get_scenes()` method where scene names containing a space would be returned incorrectly when inside a folder. Bug 68212

###

## Bug Fixes Since Baselight 6.0.20612

* Changed the name of 108 and 300 nits PQ colour spaces to group colour spaces with cinema intent (dark surround and 48 nits creative white) and to separate them from PQ spaces with home intent (dim surround and 100 nits creative white). Bug 67301
* Fixed potential crash on Scratchpad grab when using old 5.3 gallery scenes. Bug 67113
* Timecode ranges for audio media are no longer shown in FLUX Manage Metadata Pivot. Bug 67185
* GPU JPEG 2000 acceleration is now only shown as supported in the About dialog when its NVIDIA driver version requirements are met. Bug 67003
* Prevent crash when resetting Paint layers. Bug 67253
* Fixed issue with invalid timecode rate in supplemental IMF packages. Bug 67246
* Improved some behaviour with interlaced media, for example Shape animation. Bug 64527
* Removed the largely-obsolete "Switch configuration" and "Switch errors" diag test. Bug 67044
* Fixed issue with shots having the wrong number of audio channels after using Audio Sync with stems. Bug 67361
* Fixed issues with poor Canon RAW image quality on macOS. Bug 67240
* Fixed issue with "Composite Paint Strokes Separately" and Paint on the outside of an inside/outside. Bug 67471
* Fixed hang reading temporally compressed media. This particularly affected low resolution QuickTime files using H.264 compression. Bug 67469
* The ramsize diagnostic now correctly warns when a DIMM does not report a size, rather that crashing. Bug 67523
* Fixed crash using tracking after setting up IMF deliverables in Render View. Bug 67564
* Fixed timeline not updating correctly after changing "Source Alpha" option on an OFX operator. Bug 67636
* QuickTime metadata with reverse-DNS names, such as that in Apple ProRes RAW media, is now written to OpenEXR output files. Bug 67635
* Fixed slowdown when repeatedly switching to/from Flare or Chromogen on systems with Blackboard/Slate control surfaces. Bug 67595
* Fixed "Full Area" Mask or Guide Mask in a cursor being reset incorrectly, for example when another cursor's Viewing Format is changed. Bug 67657
* Fixed behaviour of Nikon RAW (NEV) files which have no colour temperature metadata. Bug 67669
* LUT export now correctly recognises several new operators that cannot be used for LUT generation, such as Bokeh. Bug 66995
* Fixed order of channels when rendering interleaved AAC encoded audio. Attempting to use more than six channels with this codec now gives an error message instead of producing an invalid file. Bug 57461
* Fixed possible crash reconforming updated scenes. Bug 67799
* Fixed incorrect chroma ordering when using HFR on certain SDI cards. Bug 67613
* Fixed issue with incorrect number of channels reading AAC encoded audio in QuickTime and MP4 files. Bug 67875
* Fixed issue with Mask being reset to "None" when setting the Master CPL for a Supplemental IMF deliverable in Render View. Bug 67891
* Still frames are now added as sequences lasting approximately one second, rather than always 24 frames. Bug 67874
* Improved behaviour of temporal OFX plugins which handle RoI/RoD negotiation, for example when used in a stack with an animated transform. Bug 67823
* Fixed scaling of Text when grabbed to gallery. Bug 63684
* Fixed incorrect handling of negative values in matte channels, in some stacks. Also fixed incorrect behaviour when referencing and transforming four or more matte channels from the same input sequence. Bug 62744
* Fixed rare crash when using Hue Angle with a Slate control surface. Bug 67960
* Fixed crash when an OFX plugin behaves incorrectly. Bug 67632
* Fixed crash which could occur if pressing "Mark In" whilst the numeric keypad navigation overlay was active. Bug 68038
* OpenEXR media containing 32-bit float channels is now read as 32-bit when the scene's Display setting is "32-bit Floating-Point RGB" or "32-bit Floating-Point RGBA". Bug 68171
* Fixed issues in some situations when a Reference operator set to "Ignore Colour Conversion" refers to an image in a cached strip. Bug 68171
* Fixed incorrect behaviour when dragging the current cursor lozenge and when clicking in the tray at the top of the timeline - when clicking near the edge of the lozenge or tray, it sometimes behaved as though the click had occurred outside. Bug 66759
* Fixed bug in strip bypass where any selected strip being locked would prevent unlocked strips from having their bypass state being modified. Bug 66982
* Files copied from macOS removable media mounted with 'ignore permissions' are now assumed to be owned by the user doing the copy, not the 'unknown' user, when the 'preserve permissions' copy option is enabled. Bug 68137
* Fixed incorrect behaviour when changing the colour space settings in a Bars operator. Bug 68282
* Fixed issue with fl-fsr stopping early if a file being relocated on disk has a length but occupies no disk blocks (is entirely sparse). Bug 68256
* Fixed FLUX Manage thumbnail failure for 10-bit 4:2:2 JPEG 2000 media. Bug 68330
* Fixed issue where the Edge Filter wouldn't match 5.3 renders and produce some artefacts. Bug 68339
* Fixed audio mark related crash on scene open. Bug 66091
* Fixed issue with invalid options causing render failures after changing the file type of Sequences deliverables in Render View. Bug 68276
* Fixed crash when using an operator which has overlay controls in a layer. Bug 67910
* Fixed issue where preset buttons might not reflect the current selection state. Bug 67911
* In the Conform View the media Filter and Reset buttons are kept disabled until a scene is opened. Bug 68386
* Fixed missing thumbnails in the Conform View Sequence Filter dialog. Bug 68442
* Improved information presented in error messages when OFX plugins are not correctly found, notably when rendering on a FLUX Store or Baselight RENDER system. Bug 68426
* Fixed issues with transforms and OFX operators, particularly flips and flops. Bug 68465
* Fixed failures when reading DNx media which has changing codec settings. Bug 68458
* Fixed issue causing occasional crash in X Grade when using a control surface. Bug 64758
* Fixed failure to load v5 gallery scenes containing shots grabbed from a scene configured with an external CMU. Bug 68484
* Camera metadata in ARRI ProRes MXF files is now read correctly and used to set the media orientation. Bug 68508
* Improved flit-daemon performance on Intel macOS systems. Bug 62048
* Fixed font size issue on Blackboard Classic in the Lens Correction operator. Bug 64105
* Improved responsiveness when scrubbing a timeline containing OFX plugins. Bug 58525
* Fixed occasional "Truelight: No CPU implementation" error messages when using Image Viewer or Client View. Bug 68558
* Fixed an error that occurs when using Multi-Paste with LUTs and a LUT directory that does not exist. Bug 68046
* 'Dual Output Layout' display mode is now available in non-stereo scenes. This mode is only visible only in 'Dual' output setups. Bug 64570
* Fixed clamping of HDR image values in a stack with a CPU OFX operator and a Transform. Bug 68554
* Fixed bug where toggling operator bypass in layers was possible via the keyboard even when grade or edit locked. Bug 68230
* Fixed bug which prevented Client View streaming from being disabled in "Network Stream" primary video output setups. Bug 68603
* Fixed cursor selection at the end of edits where folded shots/layers were force-unfolded, thus making subsequent edit drags made without changing the selection work as expected. Bug 68590
* A new Flexi package filmlight-flexi-effects installer is available in the support section of the FilmLight website. It fixes an issue in RIFE ML Retime's VRAM management, resulting in red errors in the console. Bug 68650
* Fixed issue reading trimmed HEVC encoded QuickTime files. Bug 68616
* Fixed incorrect VRAM warnings from some Flexi effects. Bug 67933
* Fixed unmodified/reset Transform operators in scenes with certain working formats incorrectly showing as modified after saving and reopening the scene. Bug 68516
* Fixed "Vertical Zoom to Fit Stacks" not dealing correctly with empty tracks at the top of the timeline. Bug 68669
* Fixed occasional crash in Timeline Alignment when deriving alignment "From Original Conform Tracks". Bug 68709
* Fixed issues with scopes or histograms in operator interfaces being affected by output clipping or Truelight options. Bug 68630
* Improved burnin performance. Bug 68499
* Fixed an issue with non-Latin subtitle text (specifically including Chinese, Japanese and Korean) failing to appear. Bug 68775
* DNxHR media with an alpha channel is now read correctly from QuickTime and MXF files. Note that some 3rd-party applications do not correctly write metadata indicating video/full range and/or premuliplication, so some media may be imported with these settings not matching the media. Bug 54108
* Fixed Shots View not updating correctly when swapping/moving a single shot into the bottom stack from above. Bug 68754
* Fixed crash using the Remove Strips of Category option when exporting an updated AAF. Bug 67039
* Changed default 'Low Rolloff' of 'Lows' preset in HueAngle from 0.0 to 0.1. Bug 67717
* Fixed issue where edge shapes would ignore the 'Paste Keyframes' option. Bug 68817
* Fixed an issue where grabbing from a scene with a different frame rate would show the wrong frame in the gallery. Bug 68553
* Fixed issue where docked scope views would initially be blank in some multi-screen configurations on macOS. Bug 64656
* Fixed incorrect rendering in some rare situations, for example a complex grade including a blurred shape being used as a grade matte above a Transform. Bug 68799
* Fixed keyer bugs that allowed them to be modified (via picking etc.) in read only scenes and locked strips/tracks. Bug 67186
* Improved performance when navigating the timeline with a large number of strips selected and not in edit mode. Bug 68873
* Fixed an issue where Chromogen rendered incorrectly on Intel Macs. Bug 68892
* Fixed LUT operators in imported BLGs, where the LUT file was originally stored in %C. Bug 63613
* Fixed straight/premultiplied RGBA options not being shown correctly for movie deliverables. Bug 68917
* Fixed occasional crash in BLG Export. Bug 67691
* Ensure the index service does not start until after remote filesystems are mounted. Bug 68919
* Fixed rare crash when using X Grade. Bug 69033

## Known Issues

* Significant image corruption is seen on Intel macOS systems running macOS 13 Ventura, especially when using RED and ARRIRAW media. This appears to be fixed in macOS 14 Sonoma. Bug 62237
*   Volumes shared from macOS systems may fail when accessed from remote systems due to a bug in macOS. To work around this issue:

    * Open System Preferences from the Dock or the Apple menu
    * Choose "Security & Privacy"
    * Click the padlock icon and use your password or Touch ID to allow changes to be made
    * Select "Full Disk Access" in the list on the left
    * Click the `+` button on the right to open a file browser
    * On your keyboard, press `/` to open the "Go to the folder" dialog
    * Enter `/sbin` and click `Go`
    * Select the file called `nfsd` and click `Open`

    After restarting your Mac, the volume(s) should now work correctly. Bug 62601
* Saturated areas in Photo RAW files can acquire a colour tint when adjusting the exposure slider in the Photo RAW Parameters operator while blending highlights. Bug 44769
* The Relight operator currently has unexpected behaviour when dragging to set global scale. Bug 63798
* Blackboard Classic control surfaces exhibit occasional flickering when switching between operators. This will be fixed in a future beta release. Bug 62406
* Shots using RIFE ML Retime (either in a Sequence or a Retime operator) behave as if Process in Working Format is selected. This can result in lower-quality output if the Render Format is larger than the Working Format. These shots also crop the image to the Working Format. Bug 66016
* Using "Network Stream" as the Primary Video Output on Intel Mac Pro systems with AMD GPUs is currently unsupported. This will be addressed in a future release of Baselight 6.0. Bug 68727
* On Intel Mac systems with multiple GPUs, the MiDaS Flexi effect can sometimes produce a flickering matte when combined with some spatial operators. To work around this issue, enable the strip cache on the MiDaS strip. Bug 69040



