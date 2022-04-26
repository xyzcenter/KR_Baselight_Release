# Baselight Release 5.3.16162 (2022-02-16)

## Bug Fixes Since Baselight 5.3.16147

* Fixed an issue which could cause fl-cp to omit the first file in a sequence \[bug 59912]

***

Baselight Release 5.3.16147 (2022-02-14)

## New Features Since Baselight 5.3.15966

### Dolby Vision

* Improved support for "L5" Image Aspect Ratio in the Dolby Vision Analysis operator. This sets the area of the image that is analysed for Dolby Vision, and the area which is then modified by the Content Mapping process (in Baselight, in an eCMU box, or in a consumer TV or cinema projection device). Note that the area is specified only as an aspect ratio, and therefore always extends to the full width or height of the image. This replaces the previous "Restrict Analysis To Cursor Mask/Guide Area" option \[bug 57869]
* When rendering from a Dolby Vision scene without Content Mapping (i.e. to a colour space that is not a Dolby Vision target display), the L5 Image Aspect Ratio can be chosen as a Mask on Render View. This is recommended when rendering the HDR master deliverable.
* When rendering to a Dolby Vision target display colour space, the treatment of the image area outside the L5 Image Aspect Ratio must be selected using the Mask setting on Render View; this area will either be masked or can have a fixed trim applied, for example to retain subtitling outside the image.
* Additional 48-nits cinema target displays are now supported. Target displays in Dolby Vision Trim operators now show "Home" or "Cinema" depending on their intended application. Trims for Home are not applied when viewing/rendering a Cinema target and vice versa.
* In Scene Settings View the APO (L11) Content Type and White Point can be selected. These setting have no effect on behaviour in Baselight; they are simply passed as L11 metadata and are used by consumer TVs which support this information.
* In Shots View, the "Export Dolby EDR Metadata" command is now labelled "Export Dolby Vision Metadata", and there is now an option to export v5 metadata. This option must be used if the scene has a non-default APO (L11) Content Type or White Point, or if any Dolby Vision Trim strips in the scene use a Cinema target display.
* The Dolby Vision v4 Analysis algorithm now gives improved Content Mapping of a Dissolve to or from black \[bug 57854]
* The UI and desk Dolby Vision v4 Trim Secondary Trim controls (Hue/Saturation) now match the layout and behaviour of the Hue Shift operator \[bug 59050]

### Media Ingest Improvements

* Media Ingest can now copy without creating scenes \[bug 58101]
* Added the option to perform a Media Ingest without appending to any existing scenes. The option 'Create scene(s)' will always ensure scenes created for this ingest have a unique name that does not affect any existing scenes. The option 'Create or append to scene(s)' will append to any scenes existing scenes defined by the scene naming field \[bug 58647]
* Is is no longer possible to append to existing scenes which have a differing container to that of the current ingest. If an existing scene is detected with a differing container when ingesting using the option 'Create or append to scene(s)', a dialog will appear notifying of the issue and will provide details on how to avoid this. This fixes an issue whereby ingesting into existing scenes would change the container without the users knowledge \[bug 57795]
* Ingesting using the option 'Rebuild Directory Structure' will now ignore any sequences at the source location that do not match any Media Import Rule defined by the chosen scene template, this allows for ingest to copy only specific media from the source. To ensure all media at the source location is copied in this case, ensure an empty rule is defined that will match all media. Note that this should be defined as the first rule in Media Import Rules \[bug 59117]
* The summary dialog once an ingest has finished submitting copies to the queue is now more relevant and is longer titled 'Ingest Complete' \[bug 57320]
* The summary dialog once an ingest has finished submitting copies to the queue now states the number of scenes that have been edited and/or created, if any \[bug 58573]
* The scene naming field for Media Ingest no longer includes a shoot day custom variable as its default \[bug 58560]
* Multiple audio files are now correctly inserted next to one another in a ingest scene rather than on top of each other when ingesting using Baselight \[bug 58900]
* Along with these changes is a redesigned UI for Media Ingest which aims to make the options clearer and ingests more understandable \[bug 58944]

### Audio Monitoring View

*   Audio Monitoring View provides control over the channel mapping used to drive the audio monitoring output and has two sets of VU meters: Input meters showing the audio in the scene and output meters showing the audio being sent to the monitoring output.

    Each channel on the input meters has a Solo button which can be used to temporarily map that channel to monitoring outputs 1+2.

    Custom channel mappings can be created and saved in addition to a predefined set of common mappings.

    Note: Custom audio channel mappings created in earlier versions of the application are no longer available \[bug 57495]

### Miscellaneous

* Added option to select shots between the DBS and cursor to Cuts View's right click menu (in the 'Select Multiple' submenu) \[bug 58909]
* Added %{WeekDay} and %{WeekDayAbr} substitutions to Render View, Exporters & Burnins \[bug 58885]
* Forensic marking for video and audio can now be enabled when creating KDMs for encrypted DCPs. When enabled, the KDM will instruct D-Cinema players to apply watermarking to video and audio accordingly \[bug 58819]
* Changed the appearance of the DBS and red shot selection to have a less prominent colour gradient. Selecting a shot range between the cursor & DBS using 'Sel/Des. All' from the desk is now possible when the DBS is within Shots View, this is now consistent with the DBS in Cuts View. Fixed issue whereby the DBS Stack in Layer View wasn't the correct stack when the DBS was locked and placed within Shots View \[bug 58887]
* The libraw library, used to decode camera RAW files, has been updated to version 0.20.2. This adds support for additional cameras and formats, notably Canon CR3 \[bug 54986]
* The Cursor View clip alarm now obeys the "Matte/Cursor/Controls Brightness" setting, to prevent it appearing at maximum brightness on an HDR display \[bug 59275]
* Added %{SceneNameOnly} substitution to Reports View \[bug 59292]
* Renders that would result in mixed-resolution images being written to the same movie file are now failed before they start \[bug 58895]
* In Conform View, now only those strips that lie on or after the start frame of the conform will be bounced up out of the way, thus making it more convenient to load multiple EDLs back-to-back \[bug 59316]
* Updated to DNxHD/DNxHR/DNxUncompressed SDK version 2.7.2. There should be no visible effects from this update \[bug 59333]
* Added the ability to enable/disable events in Conform view by clicking the new small tick to the left of the event metadata. Disabling an event has the effect of making the event act like no suitable matching media was found. This is useful in situations where none of the matching media is appropriate for the event, so the user doing the conform might prefer that no media was linked, making it clear that additional work is required \[bug 59294]
* The Transform operator now supports input from the numeric keypad when set to Grading mode. Use 2, 4, 6, or 8 to translate, 1 or 3 to scale and 7 or 9 to rotate. To reset all transforms press 5, or to reset a specific transform operation press shift and one of the keys used to perform the operation. Pressing divide will switch between image and camera transforms. The default bump amounts have been changed and holding control allows for smaller bump amounts \[bug 59361]
* The codec description of AVC and HEVC encoded MXF files now includes bit depth \[bug 59421]
* Updated to RED SDK 8.1.1. This includes:
  * improved support for V-RAPTOR sensors
  * improved IPP2 demosaic with more detail, improved shadows and highlight extension
  * support for external metadata and IMU gyro metadata (currently visible with 'fl-imageinfo -raw' and in OpenEXR renders)
  * fixes for some corruption and stability issues
  * half-res "good" decoding is no longer supported; half-res decodes are now always "premium". This can reduce performance, especially on older hardware \[bug 58963]
* Added a Go To button to the file browser (including in FLUX Manage) to allow a folder path to be typed or pasted \[bug 59252]
* The Formats editor now indicates the Working Format of the current scene (in green), and the Viewing Format of each cursor in the current scene \[bug 54077]
* Updated to OpenEXR SDK 3.1.3. This accelerates reading of OpenEXR files, especially those with many parts and large amounts of metadata, and with some compression types such as PIZ. Also a new Zip Compression Level setting is available when writing OpenEXR files using Zip-1 and Zip-16 compression \[bug 57334]
* Improved macOS System Integrity handling. macOS users must provide explicit authorisation (via a dialog interaction) to read files from external volumes, system directories, and from protected directories such as 'Documents' and 'Desktop'. Baselight pops up a dialog when necessary but services, which don't have a graphical interface, cannot request the necessary authorisation. Services now share the Baselight 'Files & Folders' and 'Full Disk Access' settings. Users should consider granting Baselight 'Full Disk Access' permission (via System Preferences / Security & Privacy) if files are accessed remotely while the system is unattended \[bug 50856]
* Added an option to Edge Crop which allows the ability to set masks and aspect ratios from the current cursor's Viewing Format \[bug 59286]
* Added a diagnostic to ensure Adaptec firmware version and expander timeout value are appropriate for Data60 storage; bundle firmware version 3.53 \[bug 58329]
* Improved speed of ARRIRAW decoding using the ARRI v7 SDK \[bug 59754]
* Categories and Marks can now be added/removed during conform, using the options in the Marks menu, right-clicking in the timeline, the Marks/Categories numeric keypad mode and the various desks \[bug 59790]

## Bug Fixes Since Baselight 5.3.15966

* Fixed issues on Linux when access to files relies upon a user's extended group membership: these can now be read and written as expected \[bug 48571]
* Fixed console warnings when a user has a very large number of extended groups \[bug 48571]
* Slightly changed ACES 1.1+ RRT to reach 0.0 in PQ based display spaces. This is a slight deviation from the ACES reference implementation but not visually noticeable. Contact FilmLight Support for more information \[bug 58592]
* Fixed potential crash if saved Quickshape definitions become corrupted \[bug 58828]
* Selecting a shot range between the cursor & DBS ('Sel/Des. All' from the desk) will now respect any playback filtering/sorting currently applied to the timeline \[bug 55764]
* Fixed previous/next mark navigation when the shot and timeline frame rates don't match \[bug 58817]
* Fixed crash when painting a matte outside of the image \[bug 58805]
* Fixed a rare issue that could cause fl-services to be incorrectly reported as failed by systemd \[bug 58889]
* On CentOS 8/FilmLightOS 8, fl-service will display a warning if the service was setup under a different software build \[bug 58397]
* On CentOS 8/FilmLightOS 8, fl-service will no longer report that a finished service has failed \[bug 58927]
* Fixed potential crash when all DBS-related views are removed and a View, Try, or Apply is attempted \[bug 58879]
* Fixed crash when switching audio output devices \[bug 58943]
* Allow long notes to span multiple lines when exported as a PDF report \[bug 58971]
* Fixed crash when selecting an audio-only file type in bl-codecs \[bug 59024]
* Fixed failure to decode some JPEG 2000 files when using GPU acceleration \[bug 59033]
* Fixed issue where a keyframed, feathered shape would render differently after splitting the Shape strip \[bug 58980]
* Fixed a bl-accept service crash on macOS \[bug 59010]
* Fixed failure to decode some VRAW media \[bug 56211]
* Fixed problem switching to stereo setup \[bug 56849]
* Improved appearance of dialogs allowing selection of multiple categories \[bug 59004]
* Fixed failure to generate some thumbnails when using a cropped Input Format \[bug 59070]
* Fixed occasional Baselight segmentation fault on exit \[bug 38057]
* Fixed issue where trackers couldn't be deleted from the tracker strip after deletion of the shape strip using it \[bug 59118]
* Fixed various errors with ARRI metadata read from .ari .mxf and .mov files when writing to OpenEXR, and when using "fl-imageinfo -raw" \[bug 58237]
* Removed 'Cannot generate a checksum for this copy' warnings from certain copies that don't currently use checksumming, such as copies from FLUX Manage \[bug 59121]
* Fixed crash closing the Licence dialog \[bug 59246]
* Stopped the remote Slate from taking a long time to disconnect \[bug 58810]
* Improved memory management when decoding Blackmagic media \[bug 59125]
* Fixed crash in Timeline Sort when a scene has an OFX operator using an unknown OFX plugin \[bug 59019]
* Fixed behaviour of the mask black level control on Render View when changing the file type to or from OpenEXR \[bug 58983]
* Fixed NodeApp hanging on exit on FLOS 8 \[bug 58911]
* Fixed issue when selecting a range in Shots View whereby existing selections would be deselected \[bug 59299]
* The Tracker operator Customise menu now allows control of the "Show Input" setting for Perspective and Transform operators \[bug 58966]
* Fixed Dolby Vision export failure when the scene contains a Dolby Vision Trim operator with no target display set \[bug 58991]
* Fixed behaviour of popup menus to prevent them from being accidentally triggered immediately after opening \[bug 58953]
* Fixed 'cannot compare disparate types' error from occurring due to events in Shots View that are not part of the bottom stack in the timeline \[bug 59393]
* Fixed issue with stuttering audio while changing volume \[bug 59374]
* Fixed issue that could cause corruption of preferences \[bug 59273]
* Fixed behaviour of LUTs with tetrahedral interpolation when applied to single-channel images \[bug 59383]
* Fixed bug which would result in an unselected operator when inserting a new layer from the desk \[bug 59384]
* Fixed bug which would cause Scratchpad's show/compare version modes to display incorrect results if a scene's Grade Result Colourspace had been explicitly set \[bug 58946]
* Scene Detect Fixes:
  * Correct output of statistics when applying Scene Detect to multiple clips
  * Fixed Scene Detect hanging when applied to one frame clips
  * Made Scene Detect a dockable view in Daylight \[bug 59241]
* Report Export View now correctly exports ALL marks when no Mark Categories are selected. There is now an additional toggle to enable or disable all mark exports \[bug 59006]
* Report Export View now gives option to set the Delimiter \[bug 56725]
* Fixed error when using fl-cp to copy to / \[bug 58869]
* Improved quality of MXF and QuickTime renders using DNxHR HQ, DNxHR SQ and DNxHD LB codecs \[bug 59351]
* Improved chroma subsampling when rendering to 4:2:2 codecs in Avid MXF, Sony MXF, QuickTime, IMF and JPEG2000, and to 4:2:0 XAVC in Sony MXF \[bug 59351]
* Fixed spurious inclusion of keycode information in some crash reports \[bug 59280]
* Fixed crash when closing a scene after closing Render View \[bug 47100]
* Added explicit support for 'Match events by Avid UID' when using an index. Select the option from the conform option and start the conform. Only movies with a matching UID will be considered during the conform operation \[bug 58928]
* Fixed an issue with Sony MXF files where the capture frame rate would be used instead of the format frame rate \[bug 59516]
* Fixed crash rendering from ProRes RAW on a FLUX Store \[bug 59435]
* Improved behaviour of monochrome ARRIRAW media (but note the ARRI v7 SDK does not yet support monochrome) \[bug 59160]
* Fixed decode of rotated ProRes 422 encoded QuickTime files \[bug 59536]
* Using XML escape characters in DCP or IMF text fields no longer causes the rendered CPLs to be invalid \[bug 59537]
* Fixed crash caused by Media Ingest View when the chosen job or scene template's host isn't reachable \[bug 59553]
* In Multi-Paste fixed strips being moved out of the way to make space when "Paste Grades" is "No" \[bug 59564]
* Fixed issue with slate diagnostic disconnecting during firmware number comparison, causing a false warning of out of date firmware \[bug 59586]
* Fixed an issue causing unchanged video to be rendered when creating supplemental IMF packages using interlaced formats \[bug 59607]
* Fixed creation of supplemental IMF packages where the Master Scene starts with a gap \[bug 59608]
* Fixed reduced speed when rendering more than 500 frames of a scene using camera media (e.g. RED, ARRIRAW) \[bug 59410]
* Ensured the vol service can start properly when the /etc/auto.vol file is empty \[bug 58276]
* Fixed the maximum value of CDL power to match the UI \[bug 59628]
* Fixed an issue which prevented shaders being compiled at install time on FLOS 8 workstation \[bug 58149]
* Fixed an occasional crash on quit with the Formats window open \[bug 59629]
* Fixed issue that caused many Cuts View thumbnails failing to render when one shot has a "Too many strips are cached in this stack" error \[bug 59322]
* Updated build of PostgreSQL server on macOS to fix linking issue with PostgreSQL command-line utilities \[bug 55907]
* Fixed an issue that could cause helper processes, notably the tnd service, to use large amounts of memory on Linux \[bug 51693]
* Fixed RAID detect diagnostic incorrectly reporting a failure when the sudo configuration diagnostic fails \[bug 59296]
* Fixed an issue that could cause the index service and its database to become incorrect when a volume fails to be read. This particularly affected Avid storage when the fuse driver fails \[bug 49990]
* Fixed missing thumbnails for some resolutions of ProRes RAW media \[bug 59655]
* To reduce the chance of errors due to too many open files, various programs now run with a higher limit \[bug 56107]
* Removed spurious output that might occur when setting up the desk service on Baselight TWO/X systems \[bug 59659]
* Fixed an issue in the NVMe diagnostic that affected earlier FLOS 6.4 systems that have retro-fitted NVME cards \[bug 59656]
* Fixed issue with Blackboard Classic not connecting to the service after being restarted or turned on \[bug 59657]
* Fixed failure to read LUTs when using bl-render from the command line \[bug 59682]
* Reduced undesirable delays in image/SDI updates when toggling "Bypass All" (and changing render modes) by temporarily suspending background caching \[bug 59668]
* Fixed crash when using OpenEXR media which reports an empty track name \[bug 59666]
* Fixed issue that meant cached strips would not be read when using a Video LUT (e.g. to Apple ProRes), which could cause slower rendering \[bug 59718]
* Fixed database backup diagnostic errors \[bug 59720]
* Fixed bugs where Conform, Multi-Paste & Media Import Rules wouldn't use the custom Inside/Outside layer config for a given layer number when inserting CDL Grade, Transform, Perspective or LUT operators \[bug 59037]
* Fixed filename-based sequence versioning not working in Conform \[bug 59784]
* Reduced the diagnostic threshold for solid state drive raw read speed because some newly formatted devices appear slow due to the underlying blocks being unallocated \[bug 58786]
* Added support for Quadro T1000 GPU for UI hosts \[bug 59709]
* Fixed issue that could cause Pixspan-compressed command-line renders to fail \[bug 59385]
* Fixed memory leak decoding ARRIRAW material with CPU rendering \[bug 59857]
