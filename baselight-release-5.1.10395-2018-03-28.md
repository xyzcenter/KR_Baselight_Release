# 베이스라이트 릴리즈 노트 5.1.10395 (2018-03-28)



## New Features Since Baselight 5.0.10254

*   Baselight 5.1 builds will remain compatible with each other, and ensure a grade that can be reliably reproduced using BLG data in all other FilmLight 5.1 products such as Prelight, Daylight and Editions. This grade exchange compatibility will be retained across all 5.1 builds. When a new feature is added that could break this compatibility, a 5.2 release will be made available across all FilmLight products.

    Scenes created or modified in a Baselight 5.1 build will not open in Baselight 5.0 or earlier.

    In order to make use of files and resources on other FilmLight systems in your local cloud, all systems will need to have a Daylight or Baselight 5.1 build installed \[bug 45713]

### File Trimming

*   Some camera movie files can now be trimmed during Consolidate and

    FLUX Manage copy. Currently the supported file types are:

    * RED R3D files (except some very old RED ONE files)
    * Vision Research Phantom Cine files
    * Sony XAVC MXF files
    * Sony RAW MXF files (F65, F55, F5 etc) \[bug 20962]

### Boost Range

*   Added new Boost Range operator. This boosts the dynamic range of an SDR image to HDR.

    Example usage:

    * Create a scene using the FilmLight Scene Template
    * Set cursor Colour Space to match the display (ideally HDR)
    *   Insert SDR video footage, with its Input Colour Space correctly

        set to Rec.1886, and Input DRT set to None
    * Insert a Boost Range operator, set Boost to 1.0 \[bug 43192]

### Look

*   The updated Look operator offers a selection of colour-space-aware

    creative looks. Many of the supplied Looks are optimised to work

    with the Truelight CAM DRT, in both SDR and HDR grades. Please see

    the tooltips in the Look operator for information on each Look. If

    you wish to explore creating your own Looks please contact FilmLight

    Support \[bug 44050]

### DKey

*   DKey has been reworked to perform better with modern wide gamut

    colour spaces:

    *   The picking precision has been improved, particularly for small

        volumes
    *   The radius and softness sliders are now logarithmic based, with a

        finer granularity. Their maximum value can be altered using an

        extended range button \[bug 46380]

### Client View

*   Added Client View, which is a web-based presentation of the current

    shot accessible to clients using their phone/tablet/laptop. Use the

    phone icon in the menu bar to enable this functionality and to set a

    passcode for security \[bug 45052]

### Shots Layout

*   Added Shots Layout options, which display a shots grid on the main

    image display, either 1x1 using the whole display or 1x2 showing the

    current cursor's image above. The metadata and categories shown can

    be set using the Customise menu in Shots View. If "Fit Information

    Text To Home Area" is enabled then the 1x1 Shots Layout will scale

    to fit the shape of the current cursor's format. Note this feature

    is only available when using an external display, and is not

    available on Baselight FOUR/EIGHT systems \[bug 45119]

### Strip Selection

*   Added ability to select all strips of a specific type (or the type of the current operator strip) and navigate forwards & backwards through them.

    To select strips of a specific type, use the Select menu's new submenu: "Select Strips Of Specific Type". This submenu is automatically populated with the types of all the strips in the scene.

    The Select menu also contains another new option: "Select All XXX Strips". This will select all strips that are the same type as the current parameter strip (XXX in this example).

    To navigate through the selections, use the Navigate menu's "Next Selected Strip" and "Prev Selected Strip" options.

    There are also Blackboard 2 and Slate actions for these operations. These can be found in the "Transport" action category \[bug 46148]
*   Added ability to navigate to the previous/next strip with the same type as the current strip. This is available from the Navigate menu's "Next XXX Strip" and "Prev XXX Strip" options. These can also be accessed using the Ctrl+DownArrow and Ctrl+UpArrow keyboard shortcuts.

    There are also Blackboard 2 and Slate actions for these operations. These can be found in the "Transport" action category \[bug 46387]

### Strip Locking

*   Added ability to lock strip operator parameters based on the

    categories associated with that strip. The categories which

    determine the strips that are locked can be set from the Scene

    Settings View (on the "Category Groups" tab). Strips with locked

    parameters are drawn with a lock icon on the timeline \[bug 12949]

### Categories

* A new Bypass Categories option is available on Cursor View and Render View; this allows strips to be bypassed based upon their categories \[bug 46299]
* Added the option to show categories on Cuts View, Gallery View, Burnins and Counters \[bug 43910, bug 45259]

### File Formats

* Improved speed and image quality of Apple ProRes 422 media read from QuickTime and MXF. Note that Sequence operators added in older Baselight builds will continue to perform and render as they did; this improvement only affects newly-added media \[bug 46567]
* Improved colour of Phantom Cine files \[bug 35214]
* Added support for crop areas in Phantom Cine files \[bug 45652]

### Security

*   'sudo' permissions have been tightened. Baselight on FilmLightOS is configured by default to allow users to run commands as root using 'sudo'. Although convenient for many installations there are sites where this may not be desirable.

    To optionally tighten security at sites that do not wish their users to run general commands as root, Baselight now includes a pro-forma 'sudoers' configuration file listing the command lines it (and its diagnostics) need to run as root in normal operation (without the need for a password). This is copied by the installer into /etc/sudoers.d/sudo\_baselight-.

    When this file is active, all other 'sudo' commands require the root password. (They are not blocked completely because using 'sudo

    ' is a useful, documented approach to system maintenance.)

    The Baselight diagnostics verify the 'sudo' rules in action allow at least the commands required by the Baselight version being run.

    In addition rsh, rexec and rlogin have been disabled and replaced with similar ssh functionality and ssh has been configured to use host-based authentication: a user logged into any machine in the local zone can ssh to this machine (as the same user) without a password, but everything else needs a password.

    A new script - share/fl-make-secure - is provided to apply the configuration changes described above. Use

    **/usr/fl/baselight/share/fl-make-secure -secure**

    to enable sudo command checking; and

    **/usr/fl/baselight/share/fl-make-secure -insecure**

    to return to the original configuration \[bug 6138]

### Multi-Paste

*   Added "EDL/ALE files" source option to Multi-paste. It is now possible to use .edl, .ale, .aaf or .xml EDL files as a source of data for Multi-paste. This is primarily for use with the new "Paste Metadata" option, which allows you to merge metadata from these sources with shots in the current scene.

    If the EDL or ALE contains ASC CDL SOP and SAT values, these can be pasted as grades into the scene using the "Load CDL from EDL" option, and setting "Paste Grades" to "Yes" \[bug 44034]
*   Added "Paste Metadata" option to Multi-paste. It is now possible to paste metadata from any supported data source (Scenes, Copy buffer, BLGs, EDLs) into the current scene.

    You can specify which columns in the destination scene you wish to update with metadata using the "Metadata Columns" setting.

    You can control whether columns containing existing data are preserved or overwritten using the "Overwrite Existing Metadata" setting.

    You can merge new columns of metadata into the scene using the "Add Extra Metadata" setting. This allows you to merge new columns of data into the scene from sources such as ALEs, or other scenes \[bug 32449]
*   Added ability to detect grade changes to multi-paste. This can be enabled using the "Detect Grade Changes" option on the Multi-Paste View. Once enabled, if the stack being pasted has a different grade to the existing grade stack, the stack's shot strip will be tagged with the category specified.

    Additionally, the "Remove If Unchanged" option can be used to remove the category from the shot strip if the grade being pasted matches the existing one \[bug 45160]

### Colour Spaces

* Added "DJI: D-Log / D-Gamut" Colour Space to Baselight. This colour space is used by DJI X5s and DJI X7 in ProRes recording \[bug 44885]
* Added P3 D65 colour space to Baselight \[bug 40214]

### Miscellaneous

* Added ability to install and run on macOS 10.13 High Sierra. See Known Issues for support on older hardware \[bug 44949]
* Added the ability to control the type of KDMs issued with a DCP, making it possible to issue SMPTE KDMs with Interop DCPs, and Interop KDMs with SMPTE DCPs. The default type of KDM issued with Interop DCPs has changed from Interop to SMPTE. When issuing a SMPTE KDM for an Interop DCP, a so called MT1 (Modified Transitional 1) KDM is written. It is not possible to use the Content Authenticator field when issuing SMPTE KDMs for Interop DCPs, nor Interop KDMs for SMPTE DCPs \[bug 39580]
* Enable daily backups of Database on Mac. Backups are stored on local disk in /Library/PostgreSQL/9.3.4/backup \[bug 45110]
* On Blackboard 2 and Slate, added the ability to cycle backwards through available display layouts by holding Shift as well as Control \[bug 44729]
* Added option to show shot-relative frame number on the cursor bar on Timeline View \[bug 45183]
* Added shot-relative frame number as a Counter \[bug 45183]
* Added optional table outline to PDF reports \[bug 45580]
* AAC audio encoding is now enabled (without the need for an additional licence) when writing to QuickTime/MP4 files \[bug 45561]
* Added search option in preferences. Clicking on the magnifying glass in the preference window will open a search dialog. Once a preference is selected the preference window will switch to that tab, scroll to the preference section and highlight the label \[bug 45322]
* In Chalk for Blackboard 2 and Slate, added new Actions allowing the creation of desk buttons for Base Grade, Denoise, Paint, and over 30 other new operators. Note that Chalk layouts containing these new Actions will not be recognised in Baselight 4.4m1, and may not be recognised in earlier Baselight 5.0 builds \[bug 45600]
* The Job Manager now shows the user, time and software version of when the scene was last opened \[bug 46137]
* Added new "Left Eye", "Right Eye", and "Stereo Split/Join" desk buttons for Blackboard 2 and Slate. These can be found in the new "Stereo" Button Category in Chalk \[bug 45971] \[bug 45972]
* Colour Space Journey View now shows layer numbers, Truelight operator information and the colour space where grading operations occur \[bug 46015]
* Added low-level logging of AJA audio playback pci register (Linux) to help to diagnose occasional glitches when playing from external storage \[bug 46057]
* Added a new mode to Auto strip selection called "Deselect on Stack Change". This acts similar to Strip Auto Select On except when the stack is changed the selected strip is changed to the bottom of the new stack. The Auto selection has also been moved to a new section in the cursor controls. The default preference has also been updated \[bug 46219]
* Added additional options to each keypad key in the "Mark/Shot Keypad Setup" dialog. Now individual keypad keys can be configured to:
  * Add/Remove categories to/from a shot
  * Add/Remove categories to/from the currently selected strip
  * Add/Remove a mark to/from a shot
  * Add/Remove a mark to/from the currently selected strip
  * Add/Remove a mark to/from the timeline \[bug 46147]
* Added keyboard shortcut to edit strip name \[bug 46255]
* Added ability to easily create composite layers which use a reference to an existing layer in the stack as a foreground image (rather than a new sequence). To enable this, select the "Foreground/Background From Reference" toggle in the "Layer Mode" menu before selecting the the type of composite (from the same menu) \[bug 46430]
* It is now possible to perform searches of the 'Buttons' and 'Actions' lists in Chalk. To do this, click the small filter icon at the top-right of the respective list. A new Action Category ('All'), which shows the full list of all Actions available for use on desk buttons, has been added to facilitate searching for available Actions \[bug 46525]
* When "Auto Update When Job/Global Formats Change" is changed to be active (on Scene Settings View), you are now given the option to update any scene formats that differ from the corresponding job/global/factory format \[bug 46673]
* You can now use the Job Manager to compact jobs. This reclaims unused space in the PostgreSQL database for that job. Select a job, and from its action menu choose "Compact Job" \[bug 46656]
* The database backup script, bl-backupdb has gained new functionality. You can now use a config file to specify multiple hosts to back-up. This is useful for including a central backup server in the nightly scheduled backups. The command can also be run from the shell to perform manual backups. Run 'bl-backupdb -i' for detailed usage information \[bug 46281]
* Compaction of jobs is now more robust and usually faster \[bug 46409]
* Job Manager now shows the version of scenes that were last saved in a version (ignoring build number) different from the current version. Scenes saved from newer versions (e.g. 5.2 when running 5.1) are indicated in orange \[bug 47108]

## Bug Fixes Since Baselight 5.0.10254

* Changed default BaseGrade Contrast Pivot to 0.0 \[bug 45251]
* Fixed an issue where DCP options set in the render panel could persist when switching scenes \[bug 45116]
* Fixed issue with stacks with dissolves not combining correctly in stereo scenes \[bug 45108]
* Added support for Avid 3D Warp and FrameFlex effects in AAF files. Many 3D Warp parameters are read, and implemented as either a transform or perspective strip in Baselight. Non-keyframed FrameFlex is replicated using a set of transformations, taking into account the Baselight format selected for the clip \[bug 24187]
* Fixed ordering of Baselight grade and FrameFlex when exporting AAF files \[bug 33787]
* Fixed crash when creating a new folder in FLUX Manage if the folder name ends in / \[bug 45197]
* The bl-delete help text is updated to reflect the fact that the command can delete jobs as well as scenes \[bug 46408]
* The Job Manager will now show the user and software build of when the scene was last saved \[bug 45973]
* Fix potential crash when upgrading 4.4m1 jobs \[bug 46883]
* Fixed rendering issue with a paint operator using an invalid perspective transform \[bug 45162]
* Fixed (blank) Blackboard 1 displays when using the Grid Warp operator \[bug 45123]
* Fixed single frame offset when conforming CMX EDLs containing keyframed SDL events \[bug 36141]
* Updated the audio reading library to include the latest bugfixes. This fixes an issue that prevented some wav-files from being read \[bug 44300]
* Fixed crash adding custom columns to Shots View \[bug 44266]
* Fixed font size of burnins and Text operators to match previous Baselight versions \[bug 45215]
* Fixed crash doing audio sync \[bug 43537]
* Add limited diagnostics to Mac build \[bug 33703]
* Speed up reading of diagnostic results \[bug 45239]
* Clearing undo history will also remove undo history from tagged renders in the scene, which can potentially reclaim a significant amount of database storage space \[bug 45241]
* Fixed an issue in stereo scenes which could cause the 1x1 display button on Blackboard 2 and Slate to toggle incorrectly \[bug 44729]
* Fixed undo/redo of toggling stereo grade's "Automatically Adjust Windows". Separated out setting of the default value (via the "Customise" menu) from the setting of the currently selected op's value (via a toggle button below the sliders) \[bug 45187]
* Restored the  option in the Text operator to allow selection of fonts that are not in the default font folders \[bug 45133]
* Fixed the gestural editing of ganged controls. Editing more than one of the controls in the group using gestures no longer leads to incorrect values for those previously edited \[bug 39068]
* Fixed issue with group grading not changing the other eye when editing the input colour space of a sequence \[bug 45145]
* Moved the CDL grade power value to be between 0-10 \[bug 45173]
* Fixed coloured lines appearing in over-exposed Phantom Cine footage \[bug 45147]
* Fixed out-of-range values in Dolby Vision analysis and XML export \[bug 45144]
* Fixed bug which would cause strips not contributing to the image to not be greyed out in the timeline when in stereo viewing modes (in single stack stereo scenes) \[bug 45192]
* To make the paint cursor more visible, it has been made thicker and the soft brush has been made less transparent \[bug 45326]
* Fixed matte paint strokes causing square artifacts \[bug 45035]
* Fixed issue that created duplicate .fltransform files \[bug 44740]
* Fixed behaviour of rescan DRT button \[bug 44740]
* Fixed bl-codecs so it correctly saves settings \[bug 45049]
* Fixed error rendering from some scenes to 12-bit or 16-bit DPX files \[bug 45357]
* When selecting a stereo OpenEXR file in FLUX Manage, the View now defaults to "Automatic left/right" \[bug 45354]
* Fixed timeline alignment issues in single stack stereo scenes when removing unreferenced strips \[bug 45192]
* Fixed crash when shots had a negative frame increment and no source timecode \[bug 44671]
* Fixed missing colour space mapping when "Show Source Input Image" enabled in Grid Warp's "Source" tab \[bug 44512]
* Enabled overlays in both eyes when in a stereo viewing mode and fixed cursor only appearing in the left eye \[bug 40313]
* Fixed crash when previewing audio file \[bug 45413]
* Fixed layer config not applied when inserting a layer from the keyboard, the insert layer blackboard key and the insert menu \[bug 45220]
* The NCLC primaries tag and Dolby Vision XML metadata has been corrected for the colour space "Dolby: ST 2084 PQ / XYZ / 108 nits" \[bug 45404]
* Fixed issue when multi-pasting metadata only \[bug 45435]
* Improved text / burnin rendering speed \[bug 45046]
* Fixed issue where selected metadata columns in Multi-Paste view were not being restored correctly after restarting the software \[bug 45539]
* Fixed crash when multipasting from an EDL with overlapping events \[bug 45547]
* Fixed issue with adding strokes to a keyframed layer after it had been reset \[bug 45500]
* Enhanced Filename matching in conform operations to allow filenames to match if only the extension is different \[bug i45307]
* Fixed operator names shown on Blackboard 2 and Slate, e.g. for Boost Contrast operator \[bug 45499]
* Fixed handling of matte merge with values outside 0 to 1 \[bug 45333]
* Added %0S to Render View help \[bug 45548]
* When inserting a mark in follow-mode, Baselight now returns the lock back to the master \[bug 46045]
* Render View help text now uses a clearer font for the "%" substitutions, to make %I clearer \[bug 45384]
* Fixed bug which could cause "Join Adjacent Strips" to fail when joining (input) strips containing audio operators set to "No Audio" \[bug 45567]
* Fixed crash which could occur when doing a "Pick" drag in Base Grade with a corrupted colour space \[bug 44813]
* OpenEXR tracks containing X, Y and Z channels are now read as RGB rather than just the Y channel as luma \[bug 45451]
* Fixed crash in Multi-Paste which could occur if a strip overlapped multiple shots \[bug 36924]
* Fixed appearance of old ARRI camera media (e.g. from D21 camera) \[bug 45619]
* Fixed an issue identifying and reading certain Scanity DPX-Y 10-bit single channel DPX files, that previously incorrectly identified as containing 3x10 bit image data \[bug 45650]
* Fixed crash in Multi-Paste which could occur if the source shot lay above a destination shot but contained a bottom-most strip which didn't overlap the destination shot \[bug 45573]
* Fixed Source In timecode of certain clips with retimes in FCP7 XMLs \[bug 45263]
* Moved crash report flushing from system bootup script to a background task. This improves boot time on Linux-based systems \[bug 44986]
* Fixed failure to export scenes and jobs where the job name contains unusual characters \[bug 36293]
* Fixed an Area Tracker issue, where the tracking box corners could not be moved around using the overlay \[bug 45690]
* Fixed cached strips being needlessly re-cached when the cursor viewing colour space changes \[bug 45679]
* Fixed an issue where the shape keyframe mode changed after inserting a tracker \[bug 45452]
* Added standard masks to UltraHD 3840x2160 format \[bug 45671]
* Fixed failure of temporal effects (e.g. Denoise) when applied to the last frame of a movie file \[bug 45597]
* In Paint, added a cross to small brushes cursors to help identify the cursor at large resolutions \[bug 45156]
* When an RGBA Sequence is marked as Premultiplied, the RGB values are no longer clipped to \[0,1] when unpremultiplying, to fix issues when compositing HDR images. To update the behaviour in existing Sequence operators turn Premultipled off then on again \[bug 45691]
* Fixed Mastering Colour Space menu not showing some colour spaces in older scenes \[bug 45617]
* Fixed Mastering Colour Space menu not updating correctly after opening an older scene \[bug 45011]
* Fixed failure to delete Chalk layout files whose names contain spaces \[bug 45704]
* Fixed failure to copy sidecar files when using fl-cp to copy from a non-/vol path \[bug 45697]
* Fixed unexpected layer renumbering in an overlap edit when changing the start for an entire stack. Also preserved the layer number of strips moving in a different context (a different sub branch or stack) \[bug 45590]
* Fixed green drag-and-drop highlighting being left on-screen after dropping onto Timeline View or Cuts View \[bug 45415]
* Added reset buttons to the Paint layer exposure and opacity controls \[bug 45712]
* New gallery folders are now browsable by FLUX Manage \[bug 44038]
* Per-scene galleries no longer report an error when the scene is within a folder \[bug 46431]
* Fixed failure when loading a P3-space QuickTime movie \[bug 45720]
* Improved behaviour when Blackboard is disconnected while application is running \[bug 43022]
* Fixed potential file permissions problem reading multi-part OpenEXR files \[bug 45117]
* Added Colour Space Journey View warning if using DCI: 2.6 Gamma / X'Y'Z' as a Mastering Colour Space \[bug 45205]
* Cuts View and Shots View no longer show burnins when they are enabled in Cursor View \[bug 45348, bug 45349]
* Fixed omission of some OpenEXR metadata \[bug 45379]
* Fixed the pane description shown on Display View when scrubbing a thumbnail in Shots View \[bug 45381]
* Fixed crash on macOS when switching away from the application and back again \[bug 45385]
* Fixed some buttons not responding correctly to repeated mouse clicks \[bug 45437]
* Fixed "temporary failure in name resolution" errors caused by DNS server configuration issues \[bug 45476]
* Fixed crash pasting sequence template paths with stereo colour matching \[bug 45543]
* Fixed missing CPU diagnostic on Baselight TWO and Baselight X systems \[bug 45588]
* Made baselight more robust against machines disappearing from the network \[bug 43434]
* Consolidate View now explains the reasons why it cannot show an example path \[bug 45735]
* Fixed diag test for Blackboard 2 \[bug 45709]
* Fixed crash opening read-only a scene using OFX \[bug 45751]
* Fixed Read only and locked strip issues in Paint \[bug 45753]
* Fixed layer 0s toggling broken when a tracker is in the stack \[bug 45766]
* Correct SMPTE MXF tags and embedded colour tags in the XAVC essence are now used when writing XAVC encoded Sony MXF files. The legal range flag embedded in XAVC essence is now interpreted when reading XAVC encoded MXF files, and the default value of the 'Legal to Full Scale' option on the input strip set accordingly \[bug 45109]
* Fixed wrong Layer 0 insertion at the bottom current cursor's stack after pressing the Layer 0 key when there is no strip selection on it \[bug 45591]
* Added Find Stereo Correspondence to the Paint operator \[bug 45765]
* Fixed incorrect Text scale and position when viewing format is changed \[bug 45746]
* Added Blackboard 2 firmware 1.1.48.76 (original LCD screens) and 2.0.2.76 (new LCD screens) which handles broken DVI modes better. Displays a message on the back LCD screens if the DVI mode is invalid \[bug 41719]
* The image dimensions of Sony ILCS-7SM2 ARW files are interpreted as slightly larger than some other applications, e.g. Flame and Photoshop. These files are now read with an additional crop that matches the image interpretation of Flame and Photoshop \[bug 45273]
* Fixed bug in giving random noise on right hand and bottom edge for integer 3 frames Denoise. Versioned so old scenes do not change \[bug 45572]
* Fixed bug which could cause potential crash on exit depending on the strip selected at the time \[bug 45776]
* Fixed error when using Texture Equaliser with matte \[bug 45332]
* Fixed inconsistent Merge/Replace pasting to multiple strip selections \[bug 45818]
* The thumbnail size of Shots View grid and Shots Layout can now be adjusted using ctrl-middle button drag \[bug 45649]
* Fixed bug which could cause shapes to shift slightly vertically when "Lock Y Positions" option enabled \[bug 45933]
* Fix perspective crash when toggling between tabs \[bug 45816]
* Fixed crash related to duplicated colour spaces imported onto a system under more than one name \[bug 42971]
* Fixed playback glitch when adding marks to the timeline \[bug 46033]
* Fixed crash when a custom fltransform file refers to an unknown colour space \[bug 46005]
* Fix crash when inserting a new tracker after copying a strip \[bug 46049]
* Fixed ordering of five-digit build numbers in 'fl-vers' tool \[bug 46012]
* Fixed locked status not being transfered when doing a multi-paste \[bug 46151]
* Changed behaviour when linking / unlinking a tracker. The keyframes and their animations will be kept \[bug 46236]
* Prevented a crash during a paste operation (from the cut view or the paste key) when no destination stack is selected \[bug 46173]
* Fixed multi-paste of LUTs (also Apply LUTs in EDL Import) when the same LUT was used on multiple shots \[bug 45778]
* Fixed use of up/down arrow keys to adjust Offset in frames in Sequence parameters \[bug 46307]
* Changes to the strip name now only apply to the current strip, unless Grouped Grading is enabled \[bug 46341]
* Fixed crash when stereo splitting an edge shape, which is linked to a two point tracker \[bug 46389]
* Fixed incorrect positioning of some Gallery shots, when the grabbed stack contains cached strips \[bug 46390]
* Fixed bug when viewing Stereo Grade strips in the gallery \[bug 46390]
* Fixed bug which prevented 'Home' & 'End' shortcuts from working with multiple selected strips \[bug 46455]
* Fixed issue where stereo split was not obeying group grading \[bug 46391]
* Fixed bug in Shapes where using the middle trackball to translate a perspective shape with "Lock Y Positions" enabled would sometimes cause the shape to move vertically \[bug 46452]
* Enabled 3D toggle button on the UI and panel when the strip was locked \[bug 46445]
* Desk buttons formed from the "Toggle Overlay" Action in Chalk now work as expected in stereo \[bug 46457]
* When navigating from a tracker section inside an operator (for example shapes) to the tracker strip, only the current tracker overlay will be displayed when appropriate \[bug 46386]
* Fixed tracker issue when linking a one point or two point track the shape would move \[bug 46292]
* Fixed crash exporting an EDL to a read only file system \[bug 45886]
* Fixed crash when having the paint transform overlay on and deselecting the paint strip \[bug 46103]
* Fixed crash when dragging a layer to a layer view \[bug 46008]
* Disabled the Paint layer opacity button when the strip is locked \[bug 45872]
* Disabled the menu in Matte tool when the strip is locked \[bug 45749]
* Fixed issue with the preference search highlight moving the text \[bug 45732]
* Fixed outdated DRT assigned when using a Scene Template \[bug 46200]
* Fixed MXF timecodes for 60@30 drop-frame, 50@25 and 48@24 timecode frame rates \[bug 46602]
* Fixed permissions of cache directory created from Preferences browser \[bug 46003]
* Improved performance when multiple Sequence or Reference operators in the same stack each read different channels from the same OpenEXR file \[bug 46109]
* Fixed the loading of AAF files in which the timeline resolution is not specified \[bug 46099]
* Fixed issue with bl-config-xorg selecting the appropriate tablet mappings for Blackboard 2 control surfaces without keyboards. bl-config-xorg will now ask if your BB2 has an integrated keyboard. and apply the appropriate tablet mapping \[bug 30516]
* Improved playback reliability when using DVI or Display Port outputs \[bug 46819]
* Fixed slowdown caused by Truelight operators with long lists of cubes \[bug 46726]
* Improved playback reliability when using DVI or Display Port outputs \[bug 46819]
* Fixed diag test for ssh volumes \[bug 46825]
* Fixed issue with dragging from FLUX Manage View to an empty Shots View \[bug 45791]
* Improved playback from disk cache. This fix has caused the format of the disk cache files to change. Cache files from previous versions are no longer valid and are deleted by this version. All scenes will need to be recached \[bug 46872]
* Fixed loading of cursor settings from job \[bug 45811]
* Added Shutter Angle metadata from R3D files \[bug 46321]
* Fixed crash renaming custom columns \[bug 46596]
* Fixed paint clone bug with very small strokes disappearing under transforms \[bug 46254]
* Fixed unresponsive mouse and keyboard when playing at 60+ fps with Scene Settings View visible \[bug 46093]
* bl-import can now import legacy scenes to databases using a FQDN hostname \[bug 45804]
* Fixed FLUX Manage incorrectly making resolution directories when copying movie files \[bug 46869]
* Updated xfs driver to fix fl-fsr failure to defragment image sequences \[bug 46890]
* Fixed crash when dragging from the layer view into a popup layer view \[bug 45988]
* Fixed mastering colour space application to input media when mastering white space is set to "(from Mastering Colour Space)". Note this fix does not change existing scenes, it only applies to Sequence operators added in version 5.1 or later \[bug 47003]
* Fixed use of ":" in volume.cfg to allow mounting a volume with a space in its name \[bug 41219]
* Fixed tabbing between fields in the Shots View causing unintended edits \[bug 45029]
* Fixed crash which could occur when exporting BLG of stereo scenes with an empty row in the input layer \[bug 46361]
* Improved error message when a scene cannot be loaded due to an unknown operator \[bug 47120]
* Fixed "This render will not proceed" warnings when submitting a render, notably to a FLUX Store \[bug 45786]
* Fixed failures when a user is a member of a very large number of supplementary groups \[bug 46826]
* Fixed incorrect transforms if resolutions didn't match when conforming from FCP7 XML files \[bug 46552]
* Fix corrupted audio output when using Stems for audio and audio channel mappings \[bug 46962]
