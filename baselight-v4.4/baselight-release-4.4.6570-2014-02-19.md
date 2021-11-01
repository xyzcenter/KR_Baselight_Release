# Baselight Release 4.4.6570 (2014-02-19)



## New Features Since Baselight 4.4.6441

* Baselight now supports FilmLight OS (FLOS) 6.4.
* Baselight no longer supports FilmLight OS (FLOS) 1.3.
* Added colour space "Sony S-Log3 SGamt3.Cine" and support to recognise this space in the metadata of Sony XAVC files \[bug 26423]
* Added support for conforming filtering by clip name \[bug 25695]
* Added support for reading clip names from AAF files. Note that Baselight 4.3 used the clip name as the filename, which wasn't right as some AAF files have the filename stored in the filename field, and others have the filename in the clipname field. Baselight now supports reading both fields and conforming by either \[bug 25695]
* Added colour space "Adobe RGB (1998)" \[bug 26522]
* TIFF and JPEG files with embedded ICC profiles now show the profile name in the Sequence Browser. If the profile is Adobe RGB (1998), sRGB or Facebook's "c2" (sRGB equivalent) then the corresponding colour space can be automatically associated with the image in the Sequence operator \[bug 26522]
* ICC profiles are written into TIFF and JPEG files when rendering to Adobe RGB (1998) or sRGB colour spaces \[bug 26591]
* Additional Exif information is now shown for digital camera files. Exif information is now read from TIFF files \[bug 18633]
* Exposed Stack Manager controls for matte manipulation as Chalk Actions in "Layer Mattes" category.
  * Matte 1 - Select Shape
  * Matte 1 - Reset Shape
  * Matte 1 - Select DKey
  * Matte 1 - Reset DKey
  * etc \[bug 26606]
* The Operations Queue (shown in Baselight's Queue Monitor, bl-render and fl-queue) now has an optional column indicating the size that each operation occupies in the database. Archiving or deleting an operation reduces its size.
* Added support for writing DNxHD encoded QuickTime files on Linux \[bug 25779]
* A new fl-diag module, "runlevel", will check each machine is running at the proper runlevel \[bug 26714]
* The Grade Result Space option "From Working Colour Space" is now named "From Stack" to more accurately reflect its behaviour.
* Added support for reading and writing 60@30 timecode to and from QuickTime movies, mimicking the way it is handled by Final Cut Pro \[bug 26426]
* Edit Left & Right keyframing modes no longer automatically add keyframes unless the preference "Automatically add keyframes in Edit Left/Right modes" (on the Plugins tab) is enabled \[bug 26728]
* Added a counter for Shot Comment. This counter supports long comments and will wrap to 80 character width \[bug 26794]
* Added scale factor display for remove border in stereograde \[bug 26808]

## Bug Fixes Since Baselight 4.4.6441

* Fixed a crash caused by reading certain TIFF files \[bug 26251]
* Fixed a problem where variable rate QuickTime movies could be misinterpreted to have too high frame rates \[bug 26357]
* Fixed a crash that could occur when reading audio from certain MXF movie files \[bug 25398]
* Fixed "flix write: : Invalid argument" error when writing to a cxfs volume \[bug 26472]
* Fixed several issues with OFX plugins: 1. removed incorrect application of DRT; 2. fixed white-point clipping of images passed to plugins; 3. fixed format of images passed to plugins to use floating-point where possible \[bug 26381]
* Fixed problem with reading audio from MXF files at 1.001 frame rates (such as 23.976, 29.97, 59.94 fps) \[bug 26428]
* Fixed problem with image store and root filesystems appearing in a users trashbin - a diagnostic will now fail if this occurs, and a hotfix will remove incorrect entries at login time if it is detected \[bug 20911]
* Fixed show disparity pick not taking current convergence value into account in stereograde \[bug 26542]
* Fixed conform of MXF material when there are audio and video files sharing the same material UID \[bug 26549]
* Fixed failures when rendering with Output Format: Use Input Format \[bug 26554]
* Fixed crash in EDL Import, which could occur with ", as frame numbers relative to the matching sequence/movie start" set to "Yes" \[bug 26544]
* Fixed bug in reference strip where Blackboard alpha "Invert" button would incorrecly remain available in some modes, causing Baselight to crash if pressed \[bug 26547]
* Fixed bug which would cause shape control point to be selected when enabling custom inner/outer curves \[bug 26568]
* Added Nvidia driver 319.60 and 319.76 as acceptable to installer and diagnostic tests \[bug 26589]
* Fixed bug which would cause an error when changing video modes on newer video cards (GTX 680, GTX 780 Ti) \[bug 26589]
* Improved UI/system performance when playing through complex stacks (particularly those containing explicitly cached strips)
* Fixed problem with a reference strip not updating its layer selection thumbnails \[bug 26594]
* Fixed repeated 'Select failed; error code 9' errors on console when a PosgreSQL database server stops \[bug 26584]
* Operations can now be restarted from the fl-queue application, as they can in Baselight and bl-render \[RT 45028]
* Improved behaviour of prerender service and rendering when the system has no network connections and its hostname is unresolvable \[bug 26566]
* Fixed stereo grade edge softness not reseting to default value \[bug 26610]
* Fixed a crash reading corrupt AvidRGB MXF \[bug 26504]
* Fixed issue when copying some AT data from a shape or a transform into an other shape/transform \[bug 26638]
* Fixed bug which could cause crash when blening layers in stacks with missing strips \[bug 26508]
* Fixed missing shot metadata in burnins when the image does not cover the area of a node on a FOUR/EIGHT \[bug 26611]
* Fixed inability to join split sequence strips after save and reload of the scene \[bug 26639]
* Fixed a small offset error in the sub-blacks region of the convertToLinear functions of the Sony colour spaces \[bug 26502]
* DPM diagnostic no longer erronously reports PASS if there is no 3ware hardware on the machine \[bug 24262]
* fl-diag now checks for the correct Myricom driver version when using an Nvidia GTX 580 or newer GPU \[bug 21483]
* pfs-verify will recreate a missing zero-byte file on a node if all its siblings are zero-byte files \[bug 16265]
* Fix X11 server config on systems with GTX285 GPUs \[bug 26635]
* Fixed a crash reading corrupt Avid RGB MXF files \[bug 26504]
* Changed test for xorg service in bl-config-video \[bug 26654]
* Fixed crash opening Chalk \[bug 26553]
* Fixed crash in bl-config-xorg and bl-config-video when running on older GPUs (7600 GT, 9800) \[bug 26663]
* Fixed unclosable panel after using Prepare For Review on an empty scene \[bug 26633]
* Removed -colourspace option from bl-shots since it was only correct when the Input Colour Space was set to From Format \[bug 26667]
* Fixed problem that prevented user changing the Timecode Frame Rate for the Reference Timecode in Shots view \[bug 26705]
* Fixed problem with layer view with no scenes open \[bug 26711]
* Fixed Bypass categories not working with split strips \[bug 26034]
* Fixed Replace paste mode with protected categories not removing unprotected strips \[bug 25887]
* Fixed render commandline printed when using Modify AAF \[bug 26723]
* Fixed crash reading subsampled JPEG2000 files \[bug 26732]
* Fixed a problem modifying AAF files with reduced handles on fast reverse clips \[bug 25277]
* Fixed issue with incorrectly interpreting speed changes during conform \[bugs 25691, 25343]
* Fixed issue where AAF relinking moved content around on contingent clips when rendering both clips with the same grade \[bug 26278]
* Fix issue conforming AAF files where the EDL contains multiple paths, but the content to conform against is in a single directory \[bug 25904]
* Fixed permissions issues when working with newer database servers (e.g. on FLOS 6) \[bug 23696]
* Fixed failure to export jobs containing a folder or scene whose name includes a ' character \[bug 26696]
* Improved speed of some fl-cp/flux copies \[bug 25863]
* Fixed crashes splitting and joining some sequence strips \[bug 26719]
* Fixed potential crash when closing scene while playback in progress \[bug 20974]
* Fixed crash rendering with pulldown \[bug 26806]
* Added bl-power support for Flos 6.4 clusters \[bug 26758]
* Fixed problem with Multi-Pasting BLG files where the difference between the start & end frame number doesn't match the difference between start & end timecodes \[bug 26814]
* Added Flos 6.4 support to fl-node-repair \[bug 26716]
* Fix for crash when starting application with Slate specified in preferences but no desk attached \[bug 26761]
* Fixed bug where Add Grain would fail to animate from frame to frame \[bug 26872]
* Fixed crash when pasting a matte from the Blackboard \[bug 26874]
* Fixed layer result blending slider colour space bug ("Blend/Composite In Linear Space" Customise menu option was being incorrectly evaluated) \[bug 26928]
