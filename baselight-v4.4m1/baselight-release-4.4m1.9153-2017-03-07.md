# Baselight Release 4.4m1.9153 (2017-03-07)



## New Features Since Baselight 4.4m1.9103

* Updated Linear Colour Space Package on Support Website, to reflect latest MetaData updates \[bug 39435]
* Added "ACEScct: ACEScct / AP1" colour space. This is a improved working colour space for grading in an ACES Workflow. It is similar to ACEScc in the midtones and highlights, but has a "toe" in the shadow region of the curve \[bug 38783]
* The command line utility for creating KDMs, formerly called 'dcptool', has been renamed to 'fl-kdmtool' \[bug 38946]
* Added Photo RAW Params dialog for handling control of exposure, camera white balance and colour space of camera RAW files. Automatic colour space selection now works for camera RAW files as well. PLEASE NOTE: Scenes using this new operator cannot be opened in previous versions of the software \[bug 32363]
* fl-imageinfo -v now reports pixel aspect ratio when it is not 1:1 \[bug 39324]
* Added support for writing little endian PCM audio to QuickTime files on Linux \[bug 26720]
* Added diagnostic for Cubix Xpander chassis \[bug 36457]
* The New Workspace command now requests a workspace name \[bug 40258]
* Added support for additional codec identifiers in QuickTime, MP4 and AVI containers. 'h264', 'H264', 'x264', 'X264', 'h265', 'H265', 'x265', 'X265' fourCC codes are now recognised \[bug 40377]
* Baselight 4.4m1 will no longer allow a job to be created if a 5.0- format job of the same name exists \[bug 36816]
* The lists of reels and KDMs in the DCP render tab are no longer displayed in a small scrollable window, instead expanding to always show the full list of entries. A number of additional columns that can be optionally displayed have been added as well \[bug 40715]
* The GPU JPEG 2000 acceleration can now be controlled via the DCP Params strip when reading DCPs. Options to control its usage have also been added when rendering supported J2C-files, DCI compliant MXFs and DCPs. The different settings only have an effect on machines with a GPU JPEG 2000 license \[bug 40581]
* Updated ACES and Telecine Scene Templates. The templates now use %w for filename and folder name in shot-based deliveries. The ACES template now uses ACEScct as its Working Colour Space \[bug 39079]
* Updated Apple ProRes library. It now encodes additional internal metadata, but has no visual or performance changes \[bug 39611]
* The colour space of some QuickTime files with known 'nclc' and 'gama' tags is now assigned appropriately \[bug 39480]
* This release adds the ability to respond to a version 5.0 or later application running on another system \[bug 39384]

## Bug Fixes Since Baselight 4.4m1.9103

* Fixed crash exporting a LUT including the Input transform for a stereo input sequence \[bug 38918]
* Fixed issues with gallery grabs from cloud media \[bug 39114]
* Fixed comments read from ARRIRAW files, particularly ALEXA Mini MXF files \[bug 39148]
* fl-imageinfo now shows "full sensor" resolution of files, to match Sequence Browser \[bug 39168]
* Updated MPEG-4/SStP libraries, making rendering of these codecs available on Mac again \[bug 37707]
* Fixed crash verifying some scenes \[bug 39454]
* Fixed warning message when quitting bl-render while a movie render is in progress \[bug 39810]
* Fixed bug stopping .LUT-CLUT files being included in cube file lists \[bug 39825]
* Fixed an issue with the bitrate selection dialog when rendering DCI compliant JPEG 2000 files, where the dialog did not update to reflect the selected bitrate \[bug 39851]
* Timecode 2 is now displayed from OpenEXR sequences written by FilmLight tools \[bug 39927]
* Fixed failure to write OpenEXR files from some ARRIRAW source files that had bad timecode metadata \[bug 39038]
* Fixed an issue that could cause a crash when annotations to a DCP could not be parsed for display in the render panel \[bug 40201]
* When editing the size of burnin text by dragging on the image, the text height is now constrained to the same limits as on the Formats editor \[bug 40349]
* DCP related movie writing parameters no longer clutter the render command after visiting the DCP render tab. This also fixes an issue where an error dialog would appear when setting movie writing parameters for a codec other than DCP after visiting the DCP tab. The 'dcp\_bitrate' movie writing parameter has been deprecated in favor of using 'dci\_bitrate' for DCI MXF and 'dcp\_video\_bitrate' for DCP to achieve the same effect \[bug 38859]
* Disabled the Discrete / Interleaved audio setting in the DCP render tab as it is determined by the format and thus has no effect \[bug 39844]
* Fixed use of the keyboard Escape key to trigger the Cancel button on modal dialogs \[bug 40546]
* Sliders for R3D Parameters controls that have no effect in Automatic decode mode are now disabled \[bug 40628]
* Fixed crash with dragging and dropping a cut view thumbnail when the mouse cursor was in filler and there was no strip selected \[bug 36988]
* Fixed an issue where the default number of threads displayed in the QuickTime H264 codec parameters dialog did not match the number of threads actually used. The default number of threads displayed is now 0 to signify that the value will be determined automatically \[bug 40702]
* Fixed potentially incorrect colour space conversions between strips in misaligned stacks \[bug 40729]
* Added support for reading timecode from Sony XAVC MP4-files with realtime metadata tracks \[bug 40706]
* Improved the wording of a warning on the Colour Space Journey View \[bug 39725]
* Fixed excessive CPU usage by cleaner service \[bug 40066]
* Improved help text for fl-setupssh \[bug 40196]
* Prevented illegal hostnames for preference database \[bug 40541]
* Fixed hang/crash changing "Display and Timeline Cache" format \[bug 40975]
* Fixed crash in MXF reader when audio read fails, e.g. from Panasonic Varicam files \[bug 40968]
* Fixed bug where saved cursor settings for a Truelight profile or cube were not correctly reloaded on reopening the scene \[bug 40880]
* Fix a problem that prevented a job being exported on OS X and then re-imported \[bug 40935]
* Improved performance when reading large multi-part OpenEXR files. Note that this improvement only affects newly-inserted OpenEXR sequences; to apply to existing sequences use the Update sequence button on the Sequence operator \[bug 41123]
* Fixed an issue where KDMs created using fl-kdmtool could contain empty ContentAuthenticator and DeviceListDescription tags \[bug 41156]
* Fixed resolutions offered when conforming media with crop resolutions \[bug 40370]
* Fixed resolutions read from some QuickTime movies with badly-formed clean-aperture metadata \[bug 41164]
* Improved Chalk for Slate button lists \[bug 37281]
* Fixed incorrect warnings about linear colour spaces in the Colour Space Journey View \[bug 39434]
* Fixed a crash on shutdown that could occur after reading JPEG 2000 material \[bug 41194]
* Added Chalk for Slate save-to and load-from file \[bug 37394]
* Updated parts of RED SDK to version 6.2.2 \[bug 41209]
* Fixed failure to decode some ARRIRAW media at half-resolution when using CPU rendering \[bug 40368]