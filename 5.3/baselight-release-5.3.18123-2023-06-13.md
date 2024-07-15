# Baselight Release 5.3.18123 (2023-06-13)



## New Features Since Baselight 5.3.17711

### Disney IMF Presets

*   Added IMF presets for HDR and SDR variants of Disney Mastering and Distribution packages. These are based on Disney specifications v1.13.2 as available from mediatechspecs.disney.com.

    The following constraints are applied when a Disney IMF preset is selected:

    * JPEG 2000 Bitdepth, Mainlevel and Sublevel are set to the values dictated by the selected preset.
    * Timecode starts at 00:00:00:00.
    * Audio in supplemental packages is preserved by default and cannot be updated, i.e. no 'audio inserts'.
    * Dolby Atmos tracks are not available.
    * MaxFALL and MaxCLL are not included in the package.
    * Min Luma is set to 0.0001 or 0.005 for 1000 nit and 4000 nit Mastering Displays respectively.

    Video, Audio, OPL and PKL names should be left at the default values to comply with Disney requirements.

    A warning will be shown if a lossless UHD video reel exceeds 80 minutes. Video can be split into parts in Render View.

    Warnings will appear in Render View if any setting in the current deliverable does not comply with the delivery specification for the selected preset.

    The package type selector has been divided into type and subtype for easier overview. It is now also possible to select Netflix and Disney presets for supplemental IMF packages \[bug 61119]

### Frame.io Integration

*   A new version of the Frame.io Integration is available.

    To install the update, open Scripts View, select the 'Packages' tab, choose the 'filmlight-frameio' package, and click Upgrade Package.

    Please note: Do not upgrade if you currently have scenes with active Frame.io assets \[bug 63660]
* When uploading to Frame.io, dialogs now restore, when possible, last selections for account, team, project, folder, and render deliverable. Install the latest integration package to use this feature \[bug 63575]
* Frame.io app and server scripts now log errors when attempting to connect to the API server or FilmLight authentication server. This should make it easier to troubleshoot configuration issues. Install the latest integration package to use this feature \[bug 63723]

### Cache Input Format Area

* The Strip Caching setting on Scene Settings View now has a "Cache Input Format Area" option. Choosing this option makes the cached area the whole of the Sequence's Input Format area (when mapped into the Working Format), including any parts which are mapped outside the Working Format. This allows later Transform operators to reveal the image in these areas, instead of black \[bug 35947]

### Miscellaneous

*   On Linux platforms (except FilmLightOS 6), image sequence file I/O is now implemented with direct I/O (DIO), when the files reside on a NFS server. This has a performance benefit.

    On all platforms, DIO can be enabled or disabled on a per-volume basis using the new "directio" flag in volume.cfg. For example:

    zone bl0999 dir images /mnt/disk1/images1 limit images directio=write

    If the flag is set to "off", DIO will not be used for the volume. If it is set to "on", DIO will be used for both reads and writes. If it is set to "read", DIO will only be used for reads. If it is "write", DIO will only be used for writes.

    The setting will typically only need to be considered for NAS and SAN volumes that might not support DIO, or for performance reasons.

    The "nodirect" flag is equivalent to "directio=off", and is now deprecated \[bug 61840]
*   On Linux platforms (except FilmLightOS 6), it is now possible to use the /etc/nfsmount.conf file to specify default mount options for NFS filesystems under /vol. This can be useful when a UI host requires different mount options than the main node of a Baselight TWO/X, or when different systems in the cloud require different mount options but use a single, shared volume.cfg file.

    To specify mount options in nfsmount.conf, the recommended way is to use a "MountPoint" entry. For example:

    \[ MountPoint "/vol/bl0999-images" ] proto=rdma

    You can also use a "Server" entry to apply to all mounts for that host. Because auto.vol mounts by IP address, you must use the the IP address of the server and not the hostname. For example:

    \[ Server "10.81.183.30" ] proto=tcp nconnect=8

    The /etc/auto.vol script will refrain from adding default options if it finds matching section in nfsmount.conf. It will add any options from volume.cfg, if they are present.

    To test the options, access the path under /vol and look at the file /proc/mounts. It will list the mounted filesystems and show the mount options in-use \[bug 62532]
*   Added a new submenu to the "Marks" menu: "Delete From Selected Strips". This contains 4 options:

    * "Scene Detect Marks" removes all marks from the selected strips implicitly created from the Scene Detect view.
    * "Categorised Marks" removes all marks from the selected strips explicitly added from the application.
    * "Client Frame Marks/Notes" removes all client added frame marks/notes from the selected strips.
    * "Client Shot Notes" removes all per-shot client notes from the selected strips.

    Note: The last 2 options CANNOT be undone \[bug 61927]
* Updated to ARRI MXF SDK version 4.1.1. This fixes issues with trimming some newer ARRIRAW media \[bug 63603]
* Added a "%C" button to the Select Image Search Directory dialog in Conform View, to go to the current scene's container \[bug 62677]
* The Help menu includes "Blackboard 2 Button Reference" when a Blackboard 2 is in use \[bug 63781]
* Added a button to the Colour Space Journey View to copy a text version of the colour space journey to the clipboard \[bug 28851]
* Added "ARRI REVEAL DRT" family to FilmLight website \[bug 62698]
* When dragging sequences from FLUX Manage View, Timeline View now shows the same sort of drop area as FLUX Manage View \[bug 62310]
* Dolby Metafier can now be used to validate rendered IMF packages with Dolby Vision. This feature is enabled in Render View by selecting the 'Metafier Validation' entry in the 'IMF' selector. Errors or warnings from Metafier will produce a warning in the operation log. Dolby Metafier, part of Dolby Vision Professional Tools, must be installed and its location set in Preferences->Advanced->IMF Validation for Metafier Validation to work \[bug 54964]
* Baselight CONFORM now lists FLUX Store and Baselight RENDER systems at the top of the submission list on Render View \[bug 62837]
* It is now possible to read supplemental IMF packages stored using Netflix best practices folder structure \[bug 63231]
* Added 'OFX Filter' option to layer's matte selector control \[bug 63528]
* Added new "Marks and Client Events" and "Queue Monitor" desk buttons, these can be found in the "UI Views" Button Category in Chalk \[bug 62566]
* Updated Photon to version 4.9.1. This can detect additional issues in rendered IMF packages \[bug 63774]
* Updated to Codex HDE SDK 4.0.3. This adds support for monochrome .arx media \[bug 63858]
* Updated to ARRI Image SDK 7.1.1. This adds support for decoding to ARRI LogC4 (and thereby ARRI's REVEAL Colour Science) for the ALEXA 65, ALEXA LF and Mini LF, and all previous ALEXA models, including the ALEXA Mini and the AMIRA. It also improves monochrome media support \[bug 62918]
* The Scene Differences dialog now shows removed audio tracks and additional audio track info when comparing a master scene to the current scene for supplemental IMF package deliverables \[bug 64122]
* In a Dolby Vision scene, the cursor's mask and guide can now be set to "Dolby Vision L5" to reflect the image aspect ratio of the Dolby Vision analysis \[bug 59905]
* The "Special Chars in Tape Name" option in the Export EDL dialog no longer implicity replaces the space character with "\_" when this option is set to "Yes" \[bug 29347]
* The OFX plugin dialog now has a Filter button \[bug 64267]
* To allow OFX plugins to better understand FilmLight system architecture, a new FilmLight Suite is now available, please read OFX\_in\_Baselight.txt in the documentation folder \[bug 63659]
* Improved support for TTC fonts allowing selection of any alternative styles embedded in the font files \[bug 62291]
* Added support for quad link UHD at 120Hz when using a Blackmagic Decklink 8k Pro \[bug 61738]
* Added an option to write closed GOP XDCAM in Sony MXF deliverables. This behaviour can be enabled using Codec Params in Render View \[bug 64402]

## Bug Fixes Since Baselight 5.3.17711

* Fixed incorrect image being sent to the user interface of OFX plugins (e.g. Neat Video) which are part of a dissolve or composite \[bug 63615]
* Fixed issues when OFX operator has no inputs, or attempts to access a frame beyond the end of the strip \[bug 63614]
*   SMB volumes listed in volume.cfg can now be accessed from macOS clients. The special volume options "username", "domain" and "password" can be used to specify authentication. Other options are described in the mount\_smbfs(8) man page. The automounter script will also auto-correct Linux-style "file\_mode" and "dir\_mode" to the macOS-style "filemode" and "dirmode" options.

    For example, a volume entry might look like: share bigserver server.lan G$ smb username=bob,password=XYZ

    To include a space in a mount option, use the octal \040 form \[bug 13252]
* Fixed issue with some AVC-Intra MXF files not being recognised \[bug 63642]
* Fixed bug which could cause Video Grade's 'Extended" (range) button state to be incorrectly saved/applied \[bug 46674]
* Fixed bug which would cause DSpot's keyframes to fail to copy and paste \[bug 62613]
* OpenEXR media with metadata indicating a FilmLight viewing colour space of "ARRI: Linear / Wide Gamut" or "ARRI: LogC / Wide Gamut" is now correctly imported using the recently-renamed versions of those colour spaces \[bug 62594]
* Fixed issue with some trimmed ALEXA Mini MXF files not being recognised \[bug 63745]
* Fixed a fatal assertion failure that could occur while interacting with the user interface \[bug 63778]
* Fixed a crash that could occur with OFX plugins which access images in the application UI \[bug 63452]
* Fixed "Launch Web Interface" button in Adaptec RAID diagnostics in fl-diag on FilmLightOS 8 systems \[bug 62530]
* Fixed issue which prevented Adaptec RAID diagnostics from running on Linux Daylight systems \[bug 62525]
* Improved recognition of anamorphic ratios in RED media \[bug 64093]
* When making a new scene from a scene template, every Scene Format from the scene template is now copied into the new scene, even if that format is not used by the scene template \[bug 64110]
* Fixed Tape metadata in renders to QuickTime/MP4 when there is no timecode. This media holds the Tape metadata in the timecode track, so timecode starting at 00:00:00:00 is now used \[bug 63960]
* Fixed an issue that could cause job format changes to be written to the wrong job after performing a Save-As to a new job \[bug 63661]
* Baselight now makes fewer connections to the database server when opening a scene. This reduces scene-open time, particularly with remote database servers \[bug 63661]
* Fixed issue with Text operator when fonts not found \[bug 61457]
* Renamed "EDL Import" to "Conform" in the Chalk UI Views list \[bug 35909]
* Blackboard and Slate Bypass Operator button now shows the operator bypass state \[bug 62553]
* Fixed crash when using Media Ingest View \[bug 61998]
* Fixed crash in Stereo Grade and Stereo Geometry Fix in Semi-Automatic mode \[bug 63021]
* Fixed potential crash when deselecting a Transform operator with grouped grading enabled \[bug 54553]
* Added new strips to the Chalk actions \[bug 62695]
* Added default Level 11 metadata to Dolby Vision HDMI signal \[bug 63145]
* Fixed "Apply Media" popups appearing when ingesting without creating scenes \[bug 61151]
* Fixed potential crash identifying marks in AAFs when conforming \[bug 63343]
* Fixed crash in Edge Crop when it was cropping the entire image \[bug 62537]
* Fixed issues with MXF media that has Sony camera marker metadata \[bug 62800]
* Fixed the colour space behaviour of the Bars operator when initially added to a scene \[bug 63276]
* Fixed Switch Dust operator on multi-GPU systems \[bug 63175]
* Fixed inability to use the "Dolby: ST 2084 PQ / P3 D65 / 108 nits" Dolby Vision viewing/rendering colour space \[bug 63150]
* Fixed typo in arriraw/exposureIndex raw metadata \[bug 63492]
* Fixed issues with OFX plugins including BorisFX Silhouette \[bug 63452]
* Fixed where menus on the Display View (e.g. when editing Text or Burnins) sometimes filled the whole screen \[bug 62704]
* Fixed a bug which could cause a scene with a area tracked shape to fail to open \[bug 38825]
* Fixed "Launch Web Interface" button in Adaptec RAID diagnostics in fl-diag on FilmLightOS 8 systems \[bug 62530]
* Fixed issue which prevented Adaptec RAID diagnostics from running on Linux Daylight systems \[bug 62525]
* Fixed clipping of highlights when using a CPU OFX plugin with a rotated transform \[bug 63910]
* Fixed a bug which would incorrectly enable the "Use Matte" button of a layer's Curve Grade operator when a modifier was pressed \[bug 60857]
* Reduced the amount of time required to calculate checksums when rendering IMF packages \[bug 61120]
* Fixed crash while monitoring Dolby Atmos audio \[bug 61613]
* Fixed crash while editing lines in Lens Correction \[bug 64103]
* Fixed crash when creating a new gallery with an invalid Gallery Job preference \[bug 64112]
* Sony per-frame camera posture metadata is now read correctly \[bug 64058]
* Reduced unwanted information printed to console when using some ARRI camera media \[bug 64074]
* Exported Dolby Vision XML now no longer contains "Level 5" entries for shots whose image aspect ratio matches the most-common image aspect ratio given in the XML \[bug 62250]
* BRAW raw metadata now includes timecode \[bug 63657]
* Fixed issue where audio would turn to noise when reading IMF CPL files \[bug 64148]
* Fixed rare crash in Curve Grade where the working colourspace was indeterminate \[bug 63967]
* Improved feedback for user when using Dolby Vision HDMI tunneling \[bug 64179]
* Fixed issue where extra spaces in Metafier Arguments could cause Metafier Validation to fail \[bug 64208]
* The tnd service can now support FLUX Manage in Baselight 6.0 \[bug 64242]
* NVIDIA driver version 525.116.03 is now accepted without warnings from fl-diag or the installer. This adds support for Ada Lovelace generation GPUs \[bug 64218]
* Improved performance of OFX plugins that have no effect on the image (e.g. Neat Video before it has been configured) \[bug 64275]
* Fixed OFX and Shader rendering errors in Gallery View when the gallery scene's working format is different from the working format of the scene where the grab was made \[bug 64277]
* Improved compatibility of DCI-compliant JPEG 2000 media to avoid potential issues with legacy cinema players and validation warnings in 3rd-party software \[bug 64288]
* Fixed OFX GPU memory issues when running on a Mac with a large-VRAM GPU and either a second GPU or SDI output \[bug 64232]
* Fixed Slate not displaying the Offset All state \[bug 39900]
* The incorrect warning about changed job or global formats is no longer shown when first opening a scene that has been imported or saved-as into a different job \[bug 63772]
* The Clip metadata option is now only shown in Render View for deliverable types that support Clip metadata \[bug 63965]
* Reference operator buttons which are invalid for the current mode are now hidden. Previously, clicking one of these buttons when they should be hidden would cause a crash \[bug 63166]
* Fixed vertical distortion during playback when Paint is applied to an interlaced source \[bug 64235]
* Stopped gap appearing after pasting a Tracker strip \[bug 64259]
* Improved behaviour of monochrome ARRIRAW media \[bug 64337]
* Fixed issue causing some AAFs not to be recognised during Conform, producing internal error messages and possibly crashing \[bug 62504]
* The "Offset All" button now flashes on the Slate \[bug 64296]
* Fixed an issue with Texture Equalizer and Transform when applied to an interlaced scene \[bug 64401]
* Disk performance diagnostic no longer verifies small file size and thread count configurations \[bug 59969]
* Tuned cache access thread count and transfer queue depth on FilmLightOS 8 platform \[bug 59969]

***
