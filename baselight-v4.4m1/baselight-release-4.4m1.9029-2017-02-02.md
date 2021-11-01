# Baselight Release 4.4m1.9029 (2017-02-02)



## New Features Since Baselight 4.4m1.8951

### EDL Import

*   We are now able to read the following additional metadata columns from CMX3600, AAF and ALE files: ASC\_CC\_XML Filename of a CDL/CCC colour correction XML file, or the name of a correction within a CCC XML file. LUT Filename of a 3D LUT file. LUT2 Filename of an additional 3D LUT file.

    When in CMX3600 EDLs, they are represented as comments. For example: 002 Day04A021L3CG V C 09:24:53:07 09:24:54:17 10:00:04:21 10:00:06:06

    * LUT: input\_A021C006\_121018\_L3CG.new.01\_4.cub
    * LUT2: output\_A021C006\_121018\_L3CG.new.01\_4.cub
    * ASC\_CC\_XML: shot1.cdl
* The ASC\_SOP, ASC\_SAT, ASC\_CC\_XML, LUT and LUT2 columns are now shown in the EDL Import's scrolling metadata, when present.
* The ASC\_CC\_XML, LUT and LUT2 columns can now be selected for display in the Shots View.
* When LUT metadata is present in an EDL, the "Apply LUTs" option become available. If "Yes" is selected, then EDL Import will search a specified directory looking for LUT files whose filename matches the contents of the LUT column. If found, a layer containing a Truelight operator referencing the LUT will be inserted. Additional controls allow the user to specify the layer number, colour and categories of the inserted layer.
* Similarly, when LUT2 metadata is present, the "Apply LUT2s" option appears - it's behaviour is identical to "Apply LUT".
* When ASC\_CC\_XML metadata is present in an EDL, the "Apply CCC/CDL XMLs" option become available. If "Yes" is selected, then EDL Import will search a specified directory looking for CCC/CDL XMLs files whose filename matches the contents of the LUT column. If a matching file isn't found, it will look for a match in the description field of corrections within the CCC XML files. If found, a layer containing a CDL operator representing the correction will be inserted. Again, controls allow the user to specify the layer number, colour and categories of the inserted layer.
* It is now possible to specify the layer number, strip colour and categories of strips inserted by the "Apply ASC CDL Grades" option.

### Multi-Paste

* Added the following additional "Match By" filters: Source LUT Source LUT2 Source Scene Source Scene & Take Source Camera Roll Source Lab Roll Source Camera Source ASC\_CC\_XML
*   Added the ability to multi-paste 3D LUT files and CDL/CCC XML files, in a similar way to how BLGs are pasted now. When either of these options is selected, options appear to allow the user to select the directory to search for the files, as well as the layer number, colour and categories of any inserted strips.

    The functionality is that same as that offered during EDL Import, but more flexible because multi-paste can paste LUTs/XML files by matching against any column.

### Miscellaneous

* Added Big Metadata View which provides an easily-visible display of metadata on the UI monitor \[Bug 19640]
* Updated to RED SDK v6.2.2. This includes bug fixes and the following changes:
  * 8K sensor support.
  * New colour primaries option "RED Wide Gamut RGB".
  * New tone curve option "Log 3G10".
  * Minimum Rocket-X driver version is now 2.1.34.0
  * Minimum Rocket-X firmware version is now 1.4.22.18 \[bug 38924]
* In HD/2K video modes, the image output is now cloned across all outputs on AJA Kona 4 and Io4K devices. This is particularly useful on Mac OS X where some applications will use SDI 3/4 for HD video output whereas FilmLight applications use SDI 1/2 \[bug 33661]
* "fl-queuetool log" now shows the operation's progress and last action \[bug 37924]
* Added "%w" substitution for render filenames. This expands to the filename prefix, defined as the filename up to the last set of digits, if present, omitting a '.', '-' or '_' character before the digits. If the digits are at the start of the filename they are removed, along with a following '.', '-' or '_' character and the filename extension \[bug 38369]
* Added additional metadata to OpenEXR output files identifying the scene DRT and the Input, Working, Grade Result and Viewing (Render) Colour Spaces \[bug 38493]
* Added Draft quality option in Cursor View and Render View. This option selects a faster lower-quality decode for large ARRIRAW media \[bug 37062]
* Black or chequer frames produced during renders as replacements for error frames now use the black and white levels of the render colour space \[bug 37925]
* Added "ACEScct: ACEScct / AP1" colour space. This is a improved working colour space for grading in an ACES Workflow. It is similar to ACEScc in the midtones and highlights, but has a "toe" in the shadow region of the curve \[bug 38783]
* Added Colour Space Journey View info for OFX plugins \[bug 38752]
* Added new sequence output type "FLYCC". This writes files which are optimised for efficient playback when the file variant matches the scene's Display And Timeline Cache setting \[bug 36543]
* Render which are in progress in the Operations Queue when an application crash occurs are no longer automatically resumed when the application is next launched, to reduce the likelihood of a repeated application crash \[bug 33472]
* Added 'Tetrahedral' option to Truelight settings in Render panel to specify high-quality Tetrahedral interpolation for profiles/cubes applied via the Render panel \[bug 29283]
* Improved workflow for rendering on FLUX Store systems. It is no longer necessary to run bl-render on another system; a worker service runs on the FLUX Store to process operations submitted to its queue \[bug 33791]
* Updated to ARRIRAW SDK 5.3.0.12. This includes performance and image quality improvements \[bug 38923]
* Updated to Sony RAW SDK v2.4.0. This improves image quality and addresses some minor bugs, notably with X-OCN decoding \[bug 38910]
* Added support for writing little endian PCM audio to QuickTime files on Linux \[bug 26720]
* Added diagnostic for Cubix Xpander chassis \[bug 36457]
* Dolby Vision functionality is now included in Baselight without a licence since Dolby now handle licensing in their CMU \[bug 40334]
* Baselight 4.4m1 will no longer allow a job to be created if a 5.0- format job of the same name exists \[bug 36816]
* Added support for reading of an additional variant of AVC-Intra MXF files as created by e.g. Airspeed/Nexis \[bug 40556]
* AJA SDI monitoring is now enabled for Baselight CONFORM on macOS \[bug 39146]
* GPU accelerated JPEG 2000 encoding and decoding is now available with an additional license on systems equipped with at least one Titan X GPU. Resolutions up to full frame 4k (4096x2160) will be handled on the GPU. Formats larger than 4k may fall back to a CPU implementation which is significantly faster than what is available without the additional license. Acceleration is supported for DCP, JPEG 2000 codestream files (J2C) and JPEG 2000 encoded MXF movie files at this time \[bug 32939]

## Bug Fixes Since Baselight 4.4m1.8951

* Reverted Disk Performance Monitoring (dpm) to test with small files on 3ware equipped systems so that latency figures and their thresholds are consistent with previous versions \[bug 37490]
* Fixed pixel aspect ratio of QuickTime movies on Mac OS X \[bug 37551]
* Fixed error when verifying a both-eyes render \[bug 37629]
* Fix support for AJA Kona 4 and Io4K devices when using UFC firmware \[bug 37770]
* Improved Truelight file list generation to prevent delays when first opening a scene which uses a Truelight directory with a large number of LUT files \[bug 36826]
* Fixed incorrect deliverable duration when rendering using "All Frames" and with a Render Frame Rate different from the scene's Working Frame Rate \[bug 37861]
* Fixed LUT export problem when exporting more than one LUT per shot, when the input colour space conversion could be included in all LUTs when only selected for the first \[bug 37881]
* MXF files with ARRI LogC tone curve are now assumed to be in Wide Gamut and are assigned an appropriate colour space \[bug 36916]
* Fix to Compress Gamut for all negative values \[bug 37826]
* Fixed crash on exit related to changes in formats \[bug 37996]
* Fixed labels on pivots in FilmGrade's graph not appearing when hovering over the pivot lines \[bug 38164]
* Fixed incorrect animation when splitting some strips, including Edge Crop strip \[bug 38284]
* Fix copying and pasting parameters in Colour Space, Look, Image Transform Settings and Dolby Vision strips \[bug 38283]
* Fixed an issue that prevented reading of MXF files with CBR indexed material spread across multiple file partitions, e.g. some MXF files with DNxHD essence \[bug 37808]
* Fixed crash reading a specific badly-formed AAF file \[bug 38441]
* Fixed incorrect errors reported when reading some TIFF files (e.g. from DVS Clipster) \[bug 38514]
* Fixed channel and track handling from multi-part OpenEXR files written by Nuke \[bug 38431]
* The "Maximum number of entries in on-disk image cache" preference can now be increased to 4 million \[bug 36553]
* Fixed crash viewing single eye in a stereo scene (while scrubbing) \[bug 36012]
* Fixed errors rendering both-eye stereo when there is an error on the right eye \[bug 37860]
* Fixed flioinfo read failure: no such file or directory \[bug 38537]
* Fixed incorrect frames being rendered at shot boundaries when rendering at a much slower frame rate than the working frame rate \[bug 38601]
* Fixed "Waiting for in-use movie to be closed" error when two deliverables write to the same output movie filename \[bug 33767]
* Fixed "Movie is not open" error during rendering on some system configurations \[bug 39231]
* Fixed failures when using OpenEXR files with very large numbers of channels \[bug 38716]
* Fixed decode of QuickTime movies with rotated video, as created by for example iPhones \[bug 38249]
* Limited warnings about screen layout changes on OS X to only report when screen resolutions or layouts have actually changed \[bug 36194]
* Fixed an issue that prevented some MXFs with broken footer partitions from being read, e.g. some files containing ARRIRAW \[bug 38842]
* Fixed an issue where renders of XAVC to Sony MXF could sometimes leave a 'Processing index' progress message less than 100% after completion \[bug 38844]
* Fixed crash due to invalid mask settings being retained from one scene to another \[bug 35026]
* Fixed issue which could cause movie renders not to restart after being suspended (e.g. during playback) \[bug 35514]
* Reduced sequence fragmentation when rendering files, which can significantly improve playback speed \[bug 37892]
* Fixed reading of MXF files without given duration but with CBE-index, making it possible to determine duration from essence size \[bug 38866]
* Fixed an issue where KDMs created by the command line utility dcptool did not correctly transfer forensic mark flags and authenticated devices from the DKDM \[bug 39173]
* The fix to bug 36285, full range 4:2:0 data in MP4 and QuickTime containers was squashed to legal range on read, did not preserve the behaviour of existing scenes. Behaviour preservation is now restored. This in turn may change the behavior of some existing scenes created in release 4.4m1.8720 or later. Behaviour in those scenes can be restored by updating sequences to match media \[bug 39176]
* Fixed failures copying using fl-cp to a non-volume directory local to the current machine \[bug 38180]
* Fixed various issues preventing EDL conform and subsequent Modify AAF/Modify XML rendering when the EDL and/or the source or rendered movies are on cloud media \[bug 31869]
* Reduced video memory usage to fix playback slowdowns
* Fixed issue which could cause scenes to be marked as needing saving immediately after opening \[bug 37260]
* Fixed reading of 10-bit RGB from AVC-encoded MXF files \[bug 39359]
* Fixed progress updates when consolidating large files \[bug 32517]
* Fixed bug which could cause the UI to become sluggish when temporal effects were placed at the bottom of very complex stacks \[bug 39390]
* Fixed freetype error message on application startup \[bug 39493]
* Fixed mask drawing so the top line of the image is no longer visible outside the mask at 4K \[bug 34378]
* Encrypted Interop DCPs were previously created using the wrong signing algorithm; SHA256 instead of SHA1. This affected Interop DCPs, corresponding KDMs and the certificates used to create and sign these packages. Two separate certificates are now created on install, one for SMPTE and one for Interop. The SMPTE one is named fl-certificate-chain as before, and the interop one is named fl-interop-certificate-chain. Both are stored in /usr/fl/etc/cert on Linux or /Library/Application Support/FilmLight/etc/cert/ on Mac. A new preference for specifying default Interop certificate has been added. Preferences have also been simplified to remove the need to specify the public certificate separate from the chain of trust, as the chain of trust is commonly appended to the public certificate \[bug 39035]
* Fixed a bug where Interop KDMs were written with SMPTE formatted cipherdata payloads. The cipherdata payload in all KDMs also referenced an incorrect certificate reference \[bug 39665]
* Fixed reading of MXF OpAtom files where the index is split over multiple segments \[bug 39700]
* Fixed a broken path to the openssl command in fl-certgen on Mac \[bug 39775]
* Fixed crash when using some OFX plugins \[bug 39590]
* Fixed "Internal error - bad movie type" error when rendering on commandline \[bug 39566]
* Fixed fl-diag error in X11 configuration test on FLUX Store systems \[bug 39818]
* Fixed crash editing burnin in a newly-created format \[bug 39830]
* Fixed crash Analysing Dolby Vision sequences \[bug 39667]
* Improved LUT file reading to minimise delays \[bug 39692]
* Fixed an issue that could cause the sequence browser to fail to find the default self-KDM on encrypted DCPs \[bug 39881]
* Fixed failures with some OpenEXR files with non-standard channel naming schemes \[bug 39544]
* Fixed an issue where the PackingList (PKL) file in DCP packages had mismatched values for the asset Type-tags. Interop values were used for SMPTE DCPs, and SMPTE values were used for Interop DCPs \[bug 40263]
* Ensure that the tnd service is started after the vol service \[bug 39897]
* Ensure that the render service is started after the xorg service \[bug 40115]
*   Fixed bug where rendering to Movie+Audio with channels set to Auto would not create any audio channels in the rendered movie in the following situations:

    * a movie with audio was inserted into the timeline
    * audio was set in the Scene Settings using an audio/movie file
    * audio was set in the Scene Settings using stem files

    Baselight will now correctly determine the source audio channel count in these situations \[bug 39836]
* Fixed bug where rendering to Audio file with channels set to Auto would fail with poor error message \[bug 39887]
* Fixed interpretation of Circle Take values when importing a scene from Daylight. Circle Take flags from Daylight are converted into "Y" or "N" in Baselight Shots View and in Burnins \[bug 37324]
* Fixed incorrect colour space assignment to some varieties of ARRIRAW media \[bug 40489]
* The Subtitle reader will additionally look for its fonts in the directory containing the subtitle xml file \[bug 38899]
* The default number of threads used to encode ProRes and H264 written to QuickTime movies now has an upper limit of 16. This fixes an intermittent issue with slow encoding speeds of H264 on newer Linux systems \[bug 40641]
* A dissolve that used a colour space name longer than 22 characters could cause a fatal error, usually during the conform process \[bug 40725]
* Fixed render corruption on systems running 304/319 nvidia drivers \[bug 38365] \[bug 38459] \[bug 39902]
