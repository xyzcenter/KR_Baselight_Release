# Baselight Release 4.3.5877 (2013-03-14)



## New Features Since Baselight 4.3.5769

### File Formats and Codecs

* Added support for reading Sony F55 RAW and F5 RAW files \[bug 21942]
* Added support for Linear RAW DNG files (e.g. Ikonoskop) \[bug 22973]

### Input Devices

* Added support for Tangent and Euphonix/AVID panels to Technical Grade \[bug 22650]
* Added trackball support on Pan & Scan for Tangent and Euphonix/AVID panels \[bug 22688]
* Added support for Tangent and Euphonix/AVID panels to Matte Tool \[bug 22753]

### Miscellaneous

* Added System Monitor View to monitor FilmLight applications accessing the disks on the local system \[bug 23056]
* Added the ability to generate sequence thumbnails from the medium- or low-resolution proxy images, for use in workflows where the high-resolution sequences are not available. This is set in Scene Settings View; new scenes take this setting from the current Setup \[bug 20820]
* Added support for variables such as %{Job} and %{Scene} in Truelight strip commands \[bug 21104]
* Added the ability for grabs to the Gallery to be made when running at Medium/Low proxy resolutions, when the High resolution media is missing \[bug 22810]
* Added -E option to pfs-verify to fix OpenEXR files previously rendered to a remote Baselight FOUR/EIGHT \[bug 22803]
* Added support for reading packed 12-bit DPX files \[bug 5458]
* Updated ALE export to support the the following new keycode gearings: 35mm 4 perf frame offset (35.1) 35mm 2 perf (35.2) 35mm 8 perf (35.8) 35mm 12 perf (35.12) 16mm 40 perfs/foot (16.40) 65mm 4 perf (65.30) 65mm 5 perf (65.24) 65mm 8 perf (65.15) 65mm 10 perf (65.12) 65mm 15 perf (65.8) The number in brackets is what will be written into the "KN Film" column for each gearing. Since the ALE spec has never supported any of these gearings, we had to invent these values by extrapolating from the existing keycode gearings: 35mm 4 perf (35.4) 35mm 3 perf (35.3) 16mm (16.20) We did these using the following rules:
  *   35mm formats: 35., other than 35mm 4 perf frame

      offset, which is a special case where frames are written into

      the DPX header's perf field by some scanners.
  * Other formats: ..
* Gallery grabs no longer fail if one or more of the input images are not present. This restriction was loosened to stop bypassed external mattes pointing to non-existant material preventing gallery grabs \[bug 22908]
* Added support for Nvidia GTX650 and GTX680 GPUs \[bug 21259]
* Added Truelight profile support to stereo viewing modes (interleaved, anaglyph, chequer & difference) \[bug 22905]
* Shots View can now be sorted by strip name \[bug 22933]
* Improved speed of reading unstriped image files (e.g. ARRIRAW) on Baselight FOUR/EIGHT systems \[bug 22931]
* Baselight will automatically apply the correct audio resampling ratio when rendering a scene to a movie where the final movie frame rate differs from the output format frame rate (ie 23.976p movie from a 24.000p scene) \[bug 22817]
* The on-disk image cache size preference can now be set as high as 50TB \[bug 22991]
* Updated combiner firmware for DVI2SDI, Reduced Four Port Combiners, Framestores and Original Four Port Combiners to support GTX 680 and GTX 650 GPUs. Systems with these GPUs will require the latest firmware installed on the combiners and framestores.
* Added option '-A' to pfs-verify to fix or regenerate pfs2 internal handle attributes \[bug 22975]

## Bug Fixes Since Baselight 4.3.5769

* Added additional node memory and cpu logging \[bug 22588]
* Kill processes if machine is using half the available swap space
* Improved Gallery data structures to greatly improve grab speed in large galleries. Old galleries are updated to the new gallery structure when they are loaded into this version of Baselight. This, however, means that loading new-style gallery scenes into older versions of Baselight will result in the viewing format of thumbnails in the gallery being incorrect, if they were different from the gallery's native format \[bug 20521]
* Prevented R3D thumbnails from being rendered using a RED Rocket, which will improve performance when playing and also addresses some thumbnail corruption issues \[bug 21514]
* Fixed "Select" -> "Select By Strip Category" submenu category list (previously showed categories relevant only to marks) \[bug 22615]
* Fixed potentially unlimited memory usage in image servers if network send is slower than data generation \[bug 22652]
* Fixed reference counting in image servers that prevented render cancellation \[22652]
* Fixed memory leak in GPU renderer \[bug 22652]
* Fixed incorrect red stripe icon shown in Sequence Browser for OpenEXR files on Baselight FOUR/EIGHT systems \[bug 22702]
* Fixed error in Matte curve which was causes a colour shift when a matte operator followed \[bug 21245]
* Fixed problem that prevented -omit\_last\_recovery\_delta from working if the last delta could not be processed \[bug 22767]
* Fixed race condition that could cause Baselight to crash during startup \[bug 18754]
* Fixed issues with on-demand rendering in OFX plugins \[bug 22785]
* Fixed incorrect decode of RAW stills shot in rotated orientation with an odd number of pixels in one dimension \[bug 22711]
* Fixed sensitivity of Tangent panel trackballs when editing shape parameters \[bug 22752]
* Fixed reading Phantom Cine files with missing image header information \[bug 22811]
* Fixed reading MPEG2 MXFs from nanoFlash \[bug 22814]
* Fixed memory usage when reading some movies, notably R3D files read using a RED Rocket \[bug 22744]
* Input focus handling has changed. The text entry caret and selection highlight should no longer disappear \[bug 22047]
* Fixed "missing image" errors after switching the Input Format of a sequence to change resolution from high res to proxy or vice versa. Newly-inserted material should behave correctly; to fix existing sequences use the Update Sequence Behaviour button \[bug 20820]
* Fixed corruption of Northlight alpha data when copying or rendering DPX file to a remote Baselight FOUR/EIGHT \[bug 22687]
* Fixed creation of damaged OpenEXR files when rendering to a remote Baselight FOUR/EIGHT. In addition, Baselight can now read these damaged files without error \[bug 22687]
* Fixed bug where pressing and holding the directional keys on Blackboard desks didn't scroll the DBS \[bug 22488]
* Fixed problems with audio when playing 23.976 fps scenes on a 24.000 fps display device \[bug 21414]
* Fixed bug in Timeline Sort's "Sort By" setting, causing weird behaviour when attempting to use multiple sort criteria.
* Fixed bug that prevented fl-diag from completing when one or mode nodes are down \[bug 22707]
* Upgraded to libsamplerate 0.1.8, which improves audio resampling performance \[bug 22815]
* Fix crash on startup when Tangent panels are enabled \[bug 22749]
* Fixed colour shift on files from older Phantom cameras \[bug 22840]
* Increased timeout for clients connecting to a licence server, to reduce errors under load \[bug 22555]
* Fixed a bug in Timeline Sort's "Stack Repeats Vertically" which was causing the full merged extent of all repeats to not be included \[bug 20986]
* Fix bl-nodemon which could wrongly show a node as unavailable \[bug 19484]
* Fix bl-nodemon which could consume memory when left in display mode for a long time \[bug 22420]
* Updated to xfs\_repair-3.1.9 \[bug 22703]
* Fixed issue with TangentHub service that could prevent Tangent control panels from functioning on Linux systems \[bug 22857]
* Fix crash when picking on an image with a Truelight profile enabled which did not load for some reason (error in profile or licensing) \[bug 22827]
* Increased range of scope gain control \[bug 22934]
* Renamed scope gain control to intensity and increased range. Added scale control (equivalent to gain control on hardware vectorscope) \[bug 22934]
* Separated scopes playing and grading resolutions. Playing resolution will take priority when playing & grading \[bug 22972]
* Fixed problem with Nvidia Version diagnostic failing to work on systems with 177.70.33 drivers \[bug 22930]
* Fixed issue with installer complaining when installing on systems with new Nvidia driver versions \[bug 22929]
* Fixed reading 50@25 and 60@30 fps timecode from MXF \[bug 22422]
* Fixed /vol/images reads failing with an IO error if a processing node returns an invalid nfs reply \[bug 22954]
* Fixed UI lock-up in flux, bl-browse etc when dragging a slider and moving the mouse beyond the edge of the window \[bug 22881]
* Fixed problem in Scene Compare when comparing with cached strips. It no longer flags an error when strips are cached. However strips that are cached will be flagged if the corresponding strip is uncached as this could cause render differences \[bug 22876]
* Fixed crash when using scene compare with an empty scene \[bug 22946]
* Fixed Render View not updating scene name after Save As \[bug 22964]
* Fixed issue in "Modify AAF" workflow, where large speed changes were combined with very small handle sizes, resulting in errors like "Unable to replace MXF clip in AAF file: Clip extent (xxx frames) too small" when producing the modified AAF. Timeline Sort now adds sufficient extra handles to speed-changed shots to ensure that they can be rendered and updated properly \[bug 22666]
* Fixed issue with flickering black lines on Baselight FOUR/EIGHT combiner/framestore output when using GTX 680 GPUs \[bug 22984]
* Fixed AAF relinking with swapped out clips, when the swapped in clip has different tracks from the conformed MXF \[bug 21761]
* Fixed bug that would remove progress logs of processes that were running for more than 30 days \[bug 22907]
* Fixed combiner firmware diagnostic check to validate correct firmware is installed when using GTX 650/680 GPUs \[bug 22963]
* Fixed bug where using "Change" in the Sequence UI to swap in a new movie/image sequence (eg dropping in a VFX shot) would cause the Modify AAF workflow to fail \[bug 21761]
* Removed the Audio Parameters and Audio Ratio menus from the Render View \[bug 22817]
* Fixed the AVID Artist Color panel so that the transport buttons now work \[bug 22822]
* Fixed behaviour of pop-up menus which cover the button that causes them to appear \[bug 22953]
* Fixed application hang and large memory usage when scanning some AIFF and WAV files \[bug 22926]
* Fixed caching of scenes after "Save as" \[bug 23010]
* Fixed slow copying of uncompressed OpenEXR files \[bug 22740]
* Fixed diagnostic that checks network switch configuration \[bug 23037]
* Scenes using movies now begin playback more smoothly and shouldn't stutter \[bugs 21005, 23059, 23138]
* Fixed importing FCP EDLs with empty clip names \[bug 22823]
* Added support for Revision C of HP S5820X SFP+ switch \[bug 23075]
* Added warning to fl-cp when copying OpenEXR files which aren't suitable for fast access in Baselight (RGB or RGBA half-float uncompressed with equal data and display windows) \[bug 22740]
* Added additional debugging to detect spurious license failures \[bug 22555]
* Fixed dotted line along left edge of CPU demosaic \[bug 23117]
* Fixed hang in fl-cp when copying a directory tree containing several copies or versions of the same MXF media \[bug 23190]
* Fixed delay starting up fl-ls \[bug 23165]
* Fixed problem with configuring video modes when starting Baselight \[bug 23187]
* On Supermicro H8DAi-2 systems, the hotfix service will now set up a MTRR register for NVIDIA graphics cards. This should improve reliability on this platform, after the next reboot \[bug 22947]
* Improved memory usage after pressing play and then stop in the Sequence Browser \[bug 23206]
* Improved stablity when grouped grading many R3D movies \[bug 23216]
* Fixed handling of RGBA OpenEXR files loaded from PFS \[bug 23247]
* Handle errors checking licences caused by unreadable .flic files in the licence directory \[bug 22555]
* Fixed occasional connection failures in fl-diag \[bug 23284]
* Fixed renderer crash with "Insufficient tiles to complete this render" \[bug 22782]
* Fixed hang when scanning certain Phantom Cine files \[bug 23405]
* Fixed crash in audio resampling code that could occur during playback when scene frame rate and display frame rate do not match \[bug 23133]
* Fixed failure to generate thumbnails and/or low/medium resolution proxy images for input files supporting marker rectangles (Canon RMF and Sony RAW) \[bugs 22775, 23257]
* Fixed crash scrubbing an empty thumbnail in Cuts View \[bug 23408]
* Adjusted cache parameters for flood filesystem to improve performance on gen3 hardware \[bug 23363]
