# Baselight Release 4.4m1.7936 (2015-12-22)



## New Features Since Baselight 4.4m1.7767

* Added support for Display Rendering Transforms which use tetrahedrally-interpolated cubes \[bug 34042]
* Added "Next/Previous Ungraded Shot" actions to Navigate menu and Chalk for Blackboard 2/Slate \[bug 34083]
* Enabled RGBCMY encoder mode in the Curve Grade operator on a Slate (from the RGBY controls page). This maps the right 6 encoders and their buttons to red, green, blue, cyan, magenta & yellow respectively \[bug 34078]
* Added JPEG render quality option \[bug 34086]
* Added option to set the Display Window in OpenEXR files using the Mask specified in the Render View \[bug 34122]
* The entire image contained in the Data Window of OpenEXR files can now be accessed by choosing an Input Format which is the same resolution as the data window. Note that this functionality is only available when the data window is larger than the display window, and entirely contains the display window \[bug 29766]
* The Timeline View can now be panned and zoomed without using the middle mouse button in the same way as the Display View, using Alt+Click or Ctrl+Alt+Click (Option+Click or Command+Option+Click on Mac) \[bug 24511]
* Dissolve now clamps its input images to \[0,1] by default, to prevent negative or >1 pixel values entering the dissolve \[bug 34116]
* Audio can now be read from cloud media \[bug 32259]
* Added performance logging to disk i/o subsystem and GPU renderer \[bug 34405] \[bug 34526]
* Added support for BLX 4 x Adaptec RAID configuration \[bug 34154]

### Gallery

* The Gallery View's right-click context menu now includes options to use the viewing format (and masks), viewing colour space or Truelight settings of the current cursor when rendering thumbnails or when scrubbing. This makes comparison of shots authored with different formats or viewing colour spaces much more convenient \[bug 21955]
* If a normal scene is explicitly loaded into a gallery, then any default cursor settings stored via the cog menu of the Cursor View are respected. For example if you set a viewing colour space different to the working colour space and save that as the default for the scene, it will look the same when loaded into a gallery \[bug 34291]

### Miscellaneous

*   Added a preference for the default behaviour of Matte Merge strips

    \[bug 29568]

## Bug Fixes Since Baselight 4.4m1.7767

* Cubes for DRTs which are shipped with 4.4m1 are no longer included in BLG files exported with "Version Compatibility: v4.4m1" \[bug 34024]
* Fixed encoding of keycode when rendering to Avid MXF Op-Atom to allow 35mm 3perf keycode to be interpreted correctly in Avid MediaComposer \[bug 34031]
* Fixed problem with Apply and paste protection causing overlapping strips. this occured when the source stack was part of the destination selection \[bug 34047]
* Added checks to ensure disk cache size is not automatically increased beyond the free space available on the disk \[bug 23199]
* Fixed an issue that caused the image to freeze when working with XDCAM \[bug 33529]
* Improved Fast-Start QuickTime compatibility with PIX \[bug 33639]
* When formats are chosen in the Sequence Browser, scene formats and job formats are now chosen ahead of global formats \[bug 32529]
* Fixed crash pressing UI3 button on a 2-UI-monitor system \[bug 34057]
* Fixed bug which prevented image to UI monitor switching from working at 4K resolution when screen switching pref set to "Image Left" \[bug 34062]
* Cursor settings saved into a scene from Cursor View are now retained when that scene is used as a Scene Template \[bug 32222]
* bl-mkscene now retains all scene settings when using a Scene Template \[bug 32222]
* Fixed select/delete of Layers 21-24 added using Chalk \[bug 34068]
* Fixed keycode metadata from movie files shown in Sequence Browser \[bug 34081]
* Replaced use of the term "Inside/Outside" with "Layer" when referring to Layer strips \[bug 34096]
* Fixed orientation of flipped/flopped ARRIRAW sequences \[bug 33960]
* Fixed numeric precision issues in some automatic mappings which could lead to unnecessary image resampling \[bug 34124]
* Fixed Prepare For Review when preparing more than one scene at once \[bug 27510]
* Fixed failures in bl-proxygen \[bug 34150]
* Fixed bug which could cause a crash when picking in the Hue Angle keyer with "Display And Timeline Cache" scene setting set to floating-point \[bug 34101]
* Fixed crash with DisplayPort/DVI/HDMI output on Baselight TWO systems with multiple GPUs \[bug 34168]
* Fixed crash when configuration the resolution of an external monitor when using DisplayPort/DVI/HDMI output \[bug 34167]
* Fixed ordering of GPUs in multi-GPU Baselight systems \[bug 34166]
* Fixed inability to Multi-Paste from Daylight scenes \[bug 34151]
* Fixed bug that required the application to be restarted before newly saved layer configs were applied \[bug 34161]
* Fixed bl-applyblg tool \[bug 34177]
* Fixed problem with Replace with Protect Mattes removing the destination stacks' mattes \[bug 29039]
* Improved fl-diag DPM (Disk Performance Monitoring) latency and throughput reporting for Adaptec RAID controllers \[bug 33641]
* Fixed duplicated entries in Colour Space Journey View when Sequence Resampling is Optical Flow or Mix Nearest Frames \[bug 34201]
* Fixed issue using DisplayPort/DVI/HDMI output on Baselight ONE systems \[bug 34168]
* Fixed audio glitch when adding marks during playback \[bug 34195]
* Resources for overridden DRTs used by Sequence operators are now stored in exported BLG files \[bug 31881]
* Fixed failure to import some FCP XML EDLs \[bug 33730]
* Increased the amount of memory dedicated to thumbnails on Baselight systems with a UI host to 20% of available RAM. This allows more thumbnails to be kept in memory, reducing thumbnail re-rendering when scrolling \[bug 34183]
* Fixed crash starting image output on FLOS 2.1 Baselight ONE systems \[bug 34168]
* Fixed bug where the "sRGB Display (Ignore Truelight & Viewing Colour Space)" (now renamed to ""Use sRGB for Thumbnails") would have no effect in some galleries \[bug 33145]
* Fixed bug where normal scenes loaded into galleries wouldn't sometimes wouldn't scrub using the current viewing colour space \[bug 29231]
* Fixed bug where the current cursor's mask and guide mask settings sometimes weren't being applied when scrubbing in a gallery. Now, as long as the user elects to turn on the "Viewing Format and Masks" options in the Gallery's right-click context menu, any current mask or guide mask should always be applied when scrubbing. \[bug 34117]
* Fixed bug which could occur when a mask, burnin and a Truelight profile were switched on in the current cursor and the user scrubbed in a gallery thumbnail which was grabbed with a different viewing format which didn't contain a mask of the same name \[bug 23458]
* Fixed crash when grabbing a movie to the gallery if the user the Baselight UI was running as didn't have permission to read the movie \[bug 26004]
* Fixed bug which cause shape overlays to not match the rendered shape image when adding/modifying keyframes \[bug 34376]
* Fixed crash when tracking with timeline cache set to 16-bit Floating-Point RGB \[bug 31320]
* Fixed a crash in Cuts View drag and drop, when attempting to drag an incomplete stack \[bug 34480]
* Improved playback performance on systems displaying via a Kona card \[bug 34489]
* Fixed bug where gallery grabs from scenes with non-default containers would sometimes be "offline" after Baselight was restarted \[bug 21976]
* Fixed issue where gallery thumbnails would change slightly when switching between cursors of different frame rates \[bug 34553]
* Fixed occasional out-of-memory errors when rendering \[bug 34226]
* Improved 'disk read limited' playback on Generation V hardware caused by i/o buffer contention \[bug 34629]
