# 베이스라이트 릴리즈 노트 5.0.9940 (2017-11-08)



## New Features Since Baselight 5.0.9853

### Formats

* A new Scene Setting (initialised from Setup and Scene Templates) controls the auto-update behaviour of Scene formats when opening a scene. You can choose to automatically update a Scene format whenever the corresponding Job or Global formats that was previously the same as that Scene format has been edited since the scene was last saved \[bug 44817]
* When saving changes made to a Job or Global format that is the same as a corresponding Scene format, the Scene format is automatically updated if auto-updating is enabled, otherwise you are given the option to update the Scene format with the same changes \[bug 44816]
* When creating a new format from the New Scene dialog, you can now choose to create a Job or Global format instead of a Scene format \[bug 44818]
* When creating a new format from the New Scene dialog, you can now set the format resolution from the format selected in FLUX Manage View \[bug 44819]
* The Input Format menu on Sequence parameters now shows all formats that match the resolution of the input media at the top of the list \[bug 44824]
* WARNING: The above changes have necessitated a modification to how formats are stored - therefore scenes created or saved in this build will _not_ be able to be loaded into older versions of the software.

### Miscellaneous

* Added options to the preferences to change cursor colours \[bug 43419]
* Added an option to blend highlights in Photo RAW files, which avoids the loss of highlight details that can occur by clipping. The new option is available in the Photo RAW Parameters operator, and is set to blend by default for new operators \[bug 43600]
* Added support for reading P2 XML metadata from Panasonic QuickTime movies. This enables colour space detection from metadata for some colour spaces, e.g. V-Log \[bug 44721]
* Increased the amount of metadata that is shown from OpenEXR files \[bug 40100]
* Added support for nvme-based RAID-0 cache \[bug 43802]
* The command line utility for issuing KDMs, fl-kdmtool, now has parameters to set the valid time interval and type of the new KDM. It also attempts to use the default generated certificates for decrypting the input KDM and issuing the new KDM, reducing the amount of information that needs to be specified in many use cases. Run 'fl-kdmtool' with no options to get a summary of the available parameters, or run 'fl-kdmtool -h' for more information \[bug 42879]
* Added diagnostic that warns if share volumes are defined without a fully-qualified hostname, since this can cause access via /vol to fail \[bug 40476]
* The way in which legal-range images (notably ProRes movie files) are treated has changed. There is now a "Legal to Full Scale" toggle button on the Sequence parameters which allows you to specify whether the data stored in the file is squashed into legal range. This allows ProRes files containing full-range data (e.g. Panasonic V-Log) to be correctly used. This option can be used for any input file except those for which an Automatic Input Colour Space is offered. Legal-range colour spaces are no longer recommended for any purpose in the application \[bug 44539]
* Added tooltips to the Copy Destinations section of FLUX Manage View, so long paths can be distinguished \[bug 44979]
* The Canon RAW SDK is now used to decode Canon RAW media (RMF and CRM files). This adds support for C200, C700 etc. Existing scenes using RMF media are unaffected \[bug 41280]
* Added support for drag and drop to the Shots View. Sequences can now be inserted into the scene by dragging from FLUX Manage View to the Shots View \[bug 44651]
*   Audio Channel Mixing

    You can now mix multiple audio channels into a single audio channel when rendering to a movie or audio file.

    In the Edit Layout dialog, accessed via the Audio Channels settings in the Render View, you can specify one or more source audio channels to route into an output audio channel.

    If multiple audio channels are assigned to one output channel, those audio channels will be summed together \[bug 38888]
*   Added support for controlling which local volumes and local media are advertised to other Baselight systems.

    By default on a system in a zone, all local volumes and media are advertised; on a system not in a zone no local volumes and media are advertised. To change this behaviour, create the file /vol/.support/etc/advertise.conf containing either

    volumes\_public = \[set ...]; -or- volumes\_private = \[set ...];

    where each entry in the set is either the name of a local volume (e.g. "bl999-images") or a regular expression that's used to match against the volume names.

    For example

    volumes\_public = \[set "bl999-images"]; advertises only /vol/bl999-images and nothing else.

    volumes\_public = \[set #SAN#]; advertises all local volumes which contain "SAN" in their name, and nothing else.

    volumes\_private = \[set "bl999-secret"]; advertises all local volumes except /vol/bl999-secret.

    Similarly, use media\_public or media\_private to control advertising of local media volumes.

    media\_public = \[set "My Data"]; advertises a local media volume called "My Data" (if it is connected) but no other local media.

    media\_private = \[set #^Backup#]; advertises all local media except any media volume whose name starts with "Backup".

    Note that you must restart the advertise service on the zone master after making any changes to advertise.conf \[bug 29426]
* In previous versions, strip caching would cache the output of a strip at the working format resolution. If the image and the working format were different sizes the cached image would be padded with black. The black padding changed the behaviour of certain operations, in particular boost contrast. An option has been added to cache just the active image area. This is the default for all new scenes. Older scenes retain the original behaviour and this can be changed in Scene Settings. \[bug 42092]
* Added option to set grid space on scopes \[bug 45265]

## Bug Fixes Since Baselight 5.0.9853

* Fixed behaviour of scene referred renderings from scenes using DRTs with BlackOffset. This bug caused a mismatch of scene referred renders compared to the actual grading stack when viewed through the same DRT \[bug 45344]
* Fixed Boost Shadows bug that gave different results with large viewing formats \[bug 44597]
*   Fix for Denoise with negative XYZ values.

    The original Tone setting put the XYZ values through a gamma curve. The XYZ values clipped at zero. There is no meaning to negative XYZ, and some colour spaces may also clip at zero. Nevertheless, on some unusual scenes, the tone clip at zero has been seen to raise the dark tones, giving milky shadows.

    The new Denoise tone curve is an offset gamma curve with a linear region below zero. This does not clip, so should it should preserve negative values. The offset is a fixed value set from the Denoise version number. Old strips have a zero offset and a clip, so they will render as before \[bug 44467]
* Fix for Boost Shadows with matte. This was giving a cross and an error message when the controls were set to the defaults \[bug 44558]
* Improved performance of undo/redo in scenes with many changes \[bug 43872]
* Improved performance of editing in very large scenes \[bug 44478]
* Invalid SMPTE timecode values (with hours or frames > 39) are no longer written to DPX files \[bug 44484]
* Fixed Matte reference to upstream layer mattes \[bug 44700]
* Fixed browsing for a burnin image in Formats editor \[bug 44735]
* Fixed error when saving a global format in Formats editor after adjusting an opacity slider \[bug 44639]
* Fixed crash when recalling groups in an empty scene \[bug 44731]
* Fixed incorrect application of Mastering Colour Space to exported BLG source images \[bug 44746]
* Fixed failures when a Shader's definition specifies an invalid colour space \[bug 42995]
* Fixed bug in BLG export which could cause keyframes to slip incorrect in Baselight for Nuke when exporting multi-input BLGs \[bug 44805]
* Fixed an issue that prevented thumbnails for encrypted DCPs from being shown in the Sequence Browser, even when a valid self-KDM was present \[bug 44814]
* Fixed Replace Grades With LUTs which was failing when including the Grade but not the Input Colour Space \[bug 44807]
* Fixed a DCP render issue where invalid KDM parameters or certificates would not trigger errors until the end of the render. All KDM parameters and certificates are now checked at the beginning of the render to fail early. This fix also improve the error messages to include the name of the problematic certificate where possible \[bug 42780]
* Fixed issue with AJA HDMI output not generating a valid signal \[bug 44834]
* Fixed failure of fl-cp to copy secondary files for some sequences, notably run-on R3D files \[bug 44617]
* Fixed Wipe Layout display on SDI output on macOS \[bug 44841]
* Fixed format mapping inside/outside setting not being preserved correctly \[bug 44854]
* Fixed the keyframing of transform effects in FCP7 xmls when constant retimes are applied \[bug 44428]
* Fixed intermittent Cubix Xpander diagnostic failure \[bug 44241]
* Fixed an issue that could flag KDM validity dates in the render panel as incorrect when they were not. The check has also been improved to better detect invalid dates and times \[bug 44832]
* Added support for reading Avid 1:1x encoded QuickTimes \[bug 33505]
* A KDM for the issuing certificate (self-KDM) is now always created when rendering encrypted DCPs. The self-KDM is no longer listed in the render panel. To create an encrypted package without the self-KDM, the file named kdm\_fl\_self.xml must be manually removed from the rendered DCP. A warning will be presented in the render panel if any specified filename collides with that of the hidden self-KDM. This warning may occur for existing scenes where the self-KDM is not hidden, but can in that case be safely ignored \[bug 44752]
* Fixed display of shots with missing source timecode in Shots View \[bug 44647]
* Fixed crash resizing some windows (e.g. fl-queue) \[bug 44983]
* Fixed a problem where online licencing would fail if you clicked the 'activate' button too quickly \[bug 44966]
* Fixed incorrect colour space for thumbnails in FLUX Manage when colour space is set to "From Metadata" \[bug 44540]
* Fixed crash if the filename template in a sequence is edited to "/vol" \[bug 44568]
* Increased speed of reading uncompressed half-float RGB/RGBA OpenEXR files \[bug 44604]
* Renamed "Rec.2100: HLG 1.2 Gamma / Rec.2020 / Preview SDR Conversion 200 nits (on 1000 nits)" colour space to have a name with a more sensible length \[bug 44739]
* Fixed behaviour of "Fix DRT Behaviour" button when opening a scene with a custom/legacy DRT \[bug 44720]
* Fixed issue with mouse click not working when in dual stereo display mode in stereo scenes \[bug 35347]
* Fixed the "Stereo Corr" button on Blackboard 2 \[bug 44852]
* Fixed issue in Paint crashing when switching between operators \[bug 44351]
* Fixed issue in Paint where the last stroke colour was still editable in read-only scenes \[bug 44634]
* Fixed crash in Mattetool with non default configuration \[bug 44633]
* Fixed crash in CDL grade when using group grade reset \[bug 44989]
* Fixed Paint layer opacity and exposure slider not interactively updating \[bug 44803]
* Fixed an issue that prevented some QuickTime files from being opened, e.g. screenrecordings made on iOS 11 \[bug 45008]
* Blackboard devices can now be selected in bl-prefs \[bug 44972]
* Fixed rare crash when gallery scene could not be opened \[bug 44580]
* Fixed issue with Matte tool crashing when new stages are added and removed \[bug 44990]
* Fixed Group Grade Reset behaviour for CDL Grade \[bug 44638]
* Fixed bug where changing the burnin font setting would have no effect \[bug 44080]
* Changed Text operator to show increased list of font options in Font menu \[bug 44081]
* Fixed crash when joining shots \[bug 44676]
* Fixed 48fps timeline timecodes becoming 30fps after re-opening the scene \[bug 45099]
*   Fixed incorrect naming of "mount" volumes in a zone when they are advertised to other systems.

    PLEASE NOTE: this fix may break existing scenes that use an unqualified volume path to access "mount" volumes remotely. This can be fixed by editing your volume.cfg file; please contact baselight-support@filmlight.ltd.uk for more information \[bug 45065]
* Fixed the network interface which is used to access an advertised volume not listed in the local volume.cfg file \[bug 45065]
* Fixed crash when cancelling a drag from a layer view with escape \[bug 45042]
* Fixed incorrect creation of /images1 directory when installing Baselight before running fl-setup-pfs on a Baselight ONE with no SSD storage \[bug 41207]
* Fixed crash in stereo scenes when clicking on the tracker list dropdown \[bug 44778]
* Fixed default burnin font \[bug 45118]
* Fixed issue with Apply from a Blackboard or Slate not taking the correct poster frame time \[bug 44860]
* Improved the Colour Space Journey View message when converting from display-referred colour scene to a scene-referred viewing colour space \[bug 39726]
* Fixed crash in FLUX Manage View if the Setup uses a saturated Error Cross Colour \[bug 45201]
* Fixed artefacts in thumbnails sometimes seen when using Linearised image transform settings \[bug 43951]
* Fixed incorrect timecode adjustment when splitting Bars and similar strips in a single-stack stereo scene \[bug 44787]
* Fixed issue with paint strokes in scenes with formats that have non square pixels \[bug 44719]
* Fixed memory leak when rendering paint or grid warp \[bug 45248]
* Fixed an issue where scenes created using templates were not picking up Shots View tab and filter settings from template \[bug 45178]
* Fixed bug in VTRE where the "VTRE Deck Control" tab no longer appeared \[bug 45313]
* Fixed bug in Denoise which could sometimes raise the black level of images, especially when colour spaces were incorrectly tagged \[bug 44467]
* Fixed usage of ARRI Look files on multi-gpu systems \[bug 43912]
* Improved speed of diagnostic tests \[bug 45078]
* Variable retimes from FCP7 xmls now placed after transforms, meaning that transform keyframing is correctly reproduced \[bug 44871]
