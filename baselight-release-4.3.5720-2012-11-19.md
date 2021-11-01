# Baselight Release 4.3.5720 (2012-11-19)



## New Features Since Baselight 4.3.5617

### Chalk - for Blackboard 2

*   A customisation tool for use with the Blackboard 2 control surface to control the position and functionality of buttons. It allows users to select between preset layouts, create their own unique layouts and edit the functionality of individual buttons.

    Layouts can be transferred between systems via USB storage devices.

    The Chalk tool is opened via "Chalk - for Blackboard 2" in the "Baselight" menu.

    For detailed user instructions please refer to "Chalk Setup" in Chapter 5 of the Baselight Reference Manual.

### ALE Functionality

* Conform from Avid Log Exchange (ALE) files is now available on all Baselight systems (and no longer requires a preference change to enable it).
* "Lab Roll", "Camera Roll", "Camera", "Shoot Date" and "Comments" columns are now read from ALE files.
* There is now an option for a "Duration" column to be written in ALE files. The duration is the timecode difference between the "Start" and "End" columns.

### Scene Compare View

*   There is a new view, Scene Compare, which compares 2 scenes for differences in the render. This can be used as a QA tool to find shots that changed in different versions of a scene. You can select different rendering modes and categories to include or exclude.

    For detailed user instructions please refer to "Rendering and deliverables" in Chapter 4 of the Baselight Reference Manual.

### Miscellaneous

* Baselight software on Mac OS X (Baselight PORTABLE and Baselight Kompressor) is now 64-bit.
* Added burnin metadata for shot length in frames (i.e. the length of the topmost strip in the stack).
* Added support for reading and writing MXF movies using the DNxHD "DNx100" codec.
* Shots View's "Fixup" operation fixes up a Sequence strip's Timecode and Keycode by reading the file headers of a sequence of images. It is now statistical in nature, determining all the chunks of timecode and keycode within a sequence of frames and picking the largest ones to apply to the entire strip. This is especially useful in film dailies workflows, where the first few frames of a clip may have invalid keycode, due to the time taken for the scanner's keycode reader to switch between camera rolls.
* Timecode 2 is now generated for Phantom cine movie files, using the same time-of-day algorithm as other sofware. However the Resolve timecodes vary depend on the frame rate of the project. At present Baselight always generates 30fps timecodes. A future Baselight release may allow this to be adjusted.
* Timecode frame rate for movies (when it is known, for example for Phantom cine) is now shown on the Sequence Browser.
* Avid MXF exports now include Labroll.
* Added the option to set a movie's Clip name from the Camera Roll metadata.
* Added options to select marked frames by category on Render View and in bl-render.
* Added support for writing AVI movies using the "10 bit packed YUV 4:2:2 (v210)" codec.
* Added ability to playback just the selected shots.
* Updated four-port combiner firmware adds support for 720p at 30, 29.97, 25, 24, and 23.976 fps. Use the bl-combiner-upgrade tool to upgrade the firmware if you require this functionality.

## Bug Fixes Since Baselight 4.3.5617

* Baselight and Truelight Player no longer crash when run on a Baselight Kompressor \[bug 21855]
* Fix potential crash in stereo geometry fix when input format and scene format are very far apart in width & height \[bug 21571]
* Licence diagnostic no longer warns about using "master" as a server name \[bug 21723]
* Using the "Change" button to replace a sequence no longer prevents it from being used with Modify AAF/XML workflow \[bug 21761]
* Tetrahedral Interpolation mode in Truelight strips can now be updated using Group Grading \[bug 21217]
* Added a Disable switch to the Truelight controls in the Cursor view. This allows enabling and disabling of an active profile or cube without having to change the list selection \[bug 21700]
* Fixed bug where pressing the UI/Image button when starting Baselight could cause the application to crash \[bug 21496]
* Fixed crash using Mattetool with Euphonix desk \[bug 21451]
* Fixed crashes caused by Cuts View retaining control over the Blackboard balls after finishing a preview \[bug 21719]
* Fixed right-click Reset Operator Entry on the current selection in Inside/Outside \[bug 21391]
* Matte Tool now selects a newly-created stage \[bug 21378]
* Fixed crashed caused by switching between Matte Tool while changing values on the Blackboard \[bug 21166]
* Fixed bug which could cause a crash if 'trying' a grade from the Cuts View/Gallery while simultaniously adjusting an encoder from the Blackboard \[bug 20945]
* Fixed crash when selecting a new preset for a strip with grouped grading enabled \[bug 20981]
* Fixed bug which could cause crash on 'Try' key from the Blackboard \[bug 21601]
* Fixed bug which could cause a crash if turning encoders whilst simultaneously switching pages in HueShift \[bug 18781]
* Disabled the cache size warning popup when timeline caching is set to 'Disabled' \[bug 21590]
* Fixed crash when 'try'ing a grade from the cutsview/gallery containing a shape strip (have to explicitly select the shape strip while the 'try' button held down) \[bug 20435]
* flux/fl-cp now continues to copy non-image files after encountering a copy error \[bug 21950]
* Fixed clipped text for Videograde "Black & White Pivots" on Blackboard 2 \[bug 21278]
* Fixed bug where Blackboard 2 Layer Graph View would sometimes not update when switching between scenes \[bug 21086]
* Added support for bl-export to export an empty job, and for bl-import to import it \[bug 21974]
* Baselight no longer runs diagnostics when started with -i, -help or --help options \[bug 21977]
* Fixed signal masking for replay \[bug 21899]
* Avid MXFs are now written using Shot Keycode, taking account of its gearing \[bug 11027]
* Fixed events showing as zero-length in some ALE files \[bug 21939]
* In Stereo ALE export, fixed up the "Start/End Timecode" option appearing blank when it first popped up \[bug 21938]
* In Stereo ALE export, fixed the "Labroll\_l" and "Labroll\_r" columns not being populated properly \[bug 21938]
* Fixed a crash in ALE export with 3:2 pulldown \[bug 21939]
* Fixed a bug in ALE export where, when "Retain ALE Import Metadata" was switched on, columns which had been explicitly disabled still appeared in the exported ALE, if they were present in the ALE the scene was conform from \[bug 21938]
* Fixed failure to read some MXF files (e.g. from Sony F3) \[bug 21969]
* Fixed errors with GPU rendered histogram \[bug 21967]
* Added support for 'fluxstore' flag in cloud.cfg \[bug 21988]
* Modified the Truelight strip user interface to provide a drop down list of profiles and cubes in the default folders, along with a browse button to access other files \[bug 21776]
* Fixed crash when reading a damaged JPEG2000 DPX file \[bug 21996]
* Fixed incorrect render of stacks containing cached strips when cropping to a mask \[bug 21943]
* Fixed issue with Curve Grade when creating a discontinuous Hue curve and colours with zero saturation \[bug 22004]
* Fixed "discontinuous timecode" warning when rendering using Record timecode \[bug 21409]
* Fixed timecode writing to QuickTime on Mac OS X when the timecode rate is different from the movie frame rate \[bug 21750]
* Fixed handling of negative timecodes in QuickTime movies by wrapping them at 24h \[bug 21386]
* Fixed reading QuickTime movies with two timecode tracks on Linux \[bug 21386]
* Fixed capitalisation of Shoot Date in Avid MXF export.
* Fixed crash occuring with particular resolutions (e.g. 1998x1080) when using strip caching \[bug 18433]
* Fixed R3D timecodes for movies running at over 30fps \[bug 22019]
* Fixed format editor behaviour when editing the translation of a reverse mapping that had non-unity scaling \[bug 22028]
* Added toggle for reversing direction of Blackboard 2 Jog Shuttle control, to use with new redesigned hardware \[bug 21953]
* Fixed issue where fl-diag would occasionally complain about a lack of valid display when connected to a Blackboard 2 ONE \[bug 20916]
* Fixed timecode range in Sequence Browser (and set as Shot Timecode) when using "List Timecode 2" \[bug 22044]
* Changed QuickTime timecode reading on Linux to wrap at 24h to match behaviour of Mac OS X. This will change timecode read from some Canon 5D movies for example \[bug 21075]
* Fixed loss of channels and/or BLG information when copying multichannel OpenEXR images with flux/fl-cp \[bug 22057]
* Fixed error when inserting proxy-resolution sequences to a scene, and then adding full-resolution images \[bug 22084]
* Fixed issues with GPU resource not being returned to Baselight after two bl-render commands are run \[bug 22091]
* Updated DVI2SDI firmware addresses failure to genlock. Use the bl-combiner-upgrade tool to upgrade the firmware if you require this functionality \[bug 21896]
* Fixed issue with Bars not rendering in bl-render to certain formats \[bug 22096]
* Fixed bug which could result in incorrect renders at the start of a temporal degrain through a matte (could also cause a crash if background caching enabled) \[bug 21230]
* Fixed bug which would prevent marks from being displayed for sequences with a frame increment of 0 \[bug 22099]
* Fixed reported duration of QuickTime/MP4 files with negative information in stts atoms \[bug 22151]
* Fixed hang when rendering with "Use Input Format" \[bug 22153]
* Increased speed of copying OpenEXR files \[bug 21966]
* Fixed crash in renderer with Feathered Shapes and invalid render string \[bug 22024]
* Fixed memory leak in matte tool menu building \[bug 22186]
* Fixed memory leak in video grade menu building \[bug 22188]
* Fixed crash when switching to Y'CbCr in CDL mode \[bug 21968]
* Fixed conform failure when using media accessed via a Baselight Kompressor \[bug 22137]
* Fixed crash in colour match \[bug 22181]
* Fixed Edge Crop CPU rendering misbehaving using Temporal Degrain and DSpot in the same stack \[bug 22217]
* Fixed issue with memory usage growing over time when selecting and unselecting Matte Tool strips \[bug 22192]
* Fixed issue where "Keyboard" button on Blackboard 2 desks could obscure characters of the soft keyboard when enabled \[bug 22175]
* Underscore key is now always displayed on Blackboard 2 Soft Keyboard \[bug 21557]
* Added a diagnostic to flag if USB connection to a Blackboard 2 ONE running at a slower speed than required \[bug 21575]
* Fixed functionality of Delete All Marks and Split/Join Strips on Toggle Mark button on Blackboard 2 \[bug 22235]
* Enabled Sharpen operators in the Input strip in Truelight Player and Baselight TRANSFER \[bug 22235]
* Fixed crash caused by reading a damaged DNG file \[bug 22344]
