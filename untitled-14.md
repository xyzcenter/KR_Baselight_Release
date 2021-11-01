# Baselight Release 4.3.5238 (2012-03-21)

## New Features Since Baselight 4.2

### Caching Improvements

*   Caching is no longer controlled on a per-cursor basis; it has been replaced by a toggle button on the scene settings panel: 'Timeline Caching'. When this option is enabled, stacks (excluding those containing a single, raw sequence input strip) will be written to the cache during playback and in the background during idle time.

    The default caching state for newly created scenes can be set from the 'System' page of the preferences editor (using the 'Enable timeline caching for new scenes' control). There is a separate preference in the 'Player' page, for scenes created in the Truelight Player where the default behaviour is not to cache.
* When adjusting a strip in a stack, the inputs to that strip are automatically cached in memory. This can result in dramatically improved interactive grading performance, as the entire stack does not have to be rendered every time a grade parameter is changed.
*   Explicit Strip Caching

    The output of every strip can now optionally be cached locally to disk. This is controlled using the 'C' icon button (located at the top right of the Parameters View). Once enabled, a 'C' indicator will be drawn on the corresponding strip in the timeline.

    Strip caching is useful in a couple of scenarios:

    * The stack you are working on has grown to a point where grading/ playback performance at the bottom of the stack has started to degrade noticeably. In this scenario, turning on strip caching at/near the bottom of the stack will, in effect, reset performance at that point (because any strips below will be working from a cached sequence on local storage).
    *   You are working with input strips containing sequences which cannot be read/decoded acceptably fast enough to work with natively. In this scenario, turning on strip caching for those problematic input strips will ensure you're working from decoded images on local storage.

        Input strips can be configured to have strip caching enabled automatically based on their sequence type from the preferences editor ('System' page, 'Cache' section).

    Strips with explicit caching enabled will be cached (written to disk) when the stack in which they reside is either played through, or processed by the background caching.

    Modifying a strip above an explicitly cached strip will result in that strip's cache being invalidated (requiring a new version to be written to disk next time the stack is played or background cached).
*   Background Caching

    During idle time, Baslight will now attempt to cache (the bottom of) the current cursor's scene. It will first cache the stack/shot the cursor is parked in, before moving on to the rest of the scene.

    The current status of the scene caching is indicated by colour coding the horizontal separator bar between the strip and timecode display areas of the timeline. Regions of the bar can be one of 4 colours:

    Grey : The region of the timeline has not yet been processed by the background caching. Green : The region of the timeline has been processed and the result is stored in the timeline cache. Purple : The region of the timeline contains a single raw sequence input strip and has not been cached because this is not usually required for playing raw sequences. However smooth playback cannot be guaranteed due to potential variations in sequence decode performance, file location etc. If caching is required for a raw sequence, explicit strip caching should be enabled for its input strip (see above). Red : Baselight has attempted to cache a region, but the rendering has failed.

    While the background caching is in operation a green spinner is drawn on either the left or right of the timeline (to indicate where the background caching is currently taking place relative to the timeline window).

    The green line & spinner displays on the timeline can be turned off from the 'System' page of the preferences editor (or from the right click context menu of the timeline itself). When disabled, these indicators are replaced by a small icon on the application menu bar (which changes depending on the background caching status).

    Background caching can be disabled altogether from 'System' page of the preferences editor.

### Gallery & Cut View

* A second Gallery view has been added to Baselight - to see it, simply insert it into your current workspace in the usual manner:(right-click on a Splitter), Windows+right click (Ctrl+ right-click on Mac) and select "Gallery 2".
* The open scenes in the Gallery are now shown as tabs above the scrolling thumbnail areas, making it possible to switch between gallery scenes without needing to use the right-click context menu. It's also possible to close a gallery scene by clicking the "X" control on the right-hand side of each tab.
* The way Baselight Galleries load scenes has been substantially improved. The behaviour is controlled from the "Gallery Autoloads" and "Gallery 2 Autoloads" sections on the "Cuts View, Gallery & Scratchpad" page of the preferences. Each Gallery has three autoloading slots, allowing it to automatically load three different types of galleries at once. For example, by default, the first Gallery View will automatically load a gallery for the current user and a per-job gallery as a new job is encountered when a scene is loaded into the Timeline View. Gallery 2 is set up to have no autoloads by default, but if you wanted your per-job gallery to live in Gallery 2, you can simply select a per-job option in one of Gallery 2's autoload slots and switch off the per-job obtain in the first gallery. The arcane substitution-based gallery scene naming scheme is largely hidden now, but is still available by selecting "Custom" from an autoload slot's dropdown. An edit box then appears, allowing you to type in a specific template.
* It's now possible to have either/both of the galleries contain a tab which maps to the current cursor, essentially giving you a second Cut View (without the ability to scroll lock, however). This gallery will share DBS location and "red square" selection state with the Cut View. To set up such a tab, simply set on of Gallery/Gallery 2's autoloading slots to "Current Cursor".
* The Gallery Views now contain a '+' menu to the right of the gallery tabs. It contains the following options:
  *   "Load Missing Autoload Galleries": If you've closed autoloaded

      Galleries, or had autoloading disabled for a while, you can get

      them back by selecting this option. It simply evaluates the

      current autoload preferences for the Gallery and loads anything

      which isn't already present.
  *   "Disable Autoloading": Disables autoloading. Useful if you want

      to quickly load a scene into the timeline and don't want a

      per-job gallery autoload to slow you down.
  *   "Current Cursor": Adds a tab which reflects the state of the

      current cursor, in effect making the Gallery a Cut View when

      that tab is selected.
  *   "Open Scene..": Bring up a Job Manager to load an explict scene

      into the Gallery. Any type of scene can be loaded, including

      scenes which currently have timeline cursors associated with

      then.
  *   A list of the last 5 scenes which have been opened in either

      Gallery.
* The host and job which store gallery scenes is now specified in the "Gallery Job" preference in the "Gallery" section.
* If a gallery scene has failed to load (perhaps due to being locked by another user), a "Retry" button now appears below the error text. This allows the user to resolve the problem and then load the scene without needing to restart Baselight.
* In previous versions of Baselight, locking the DBS to the current cursor would update the DBS location as the current shot changed and also cause the Cut View to scroll to keep the current cursor location centred. These two behaviours have now been split into separate locks: "DBS Lock" and "Scroll Lock". This allows the user to position the DBS on a desired shot and leave it there, whilst still having the Cut View scroll along with the current cursor position.
* By default, the Cuts View will now switch on "DBS Lock" and "Scroll Lock" as soon as playback begins. Either/both of these behaviours can be switched off using the preferences located in the "Cuts View" section of the "Cuts View, Gallery & Scratchpad" page.
* The DBS left/right/up/down buttons are now active when the "View" button is held down, allowing the DBS to be moved whilst viewing. This functionality was previously only available on the trackballs.
* The DBS left/right/up/down buttons and the trackball can now be used whilst the "Try" button is down, allowing the user to try a large number of grades on the current shot simply by holding down "Try" and moving the DBS position.
* When the "Goto DBS", "View" or "Try" buttons are down, any of the trackball rings can be used to scrub within the shot, replicating functionality which was previously only available on the jog wheel.
* It's now possible to select multiple shots in the Gallery using exactly the same mechanism as used in the Cut View. This allows the users to remove multiple shots in the gallery at once.
* Cuts and Gallery views now report rendering errors (eg missing files) to the standard Baselight message log, making it much easier to work out why a given thumbnail is displaying an "X".
* It's now possible to change the width of the borders around thumbnails used to represent the DBS and selected shots. The relevent preference is in the "General" section of the "Cuts View, Gallery & Scratchpad" page. In addition, the default value has been reduced from 7 pixels to 5.
* The Cuts and Gallery Views now support inertial scrolling, giving a feel of inertia when scrolling, allowing more rapid navigation of large scenes. The specific feel of the inertial scrolling can be controlled by adjusting the sliders in the "Inertial Scrolling" section of the "Cuts View, Gallery & Scratchpad" page.
* It is now possible to re-order shots in the Cuts and Gallery views simply by dragging and dropping into the space between thumbnails in the same view: a green "dumbbell" will appear showing the insertion point. Multiple shots can be moved by dragging a selected thumbnail (red square).
* Drag and Drop can be used to quickly grab multiple shots to a Gallery. Simply red-select multiple thumbnails in the Cut View and drag and drop into a gallery. Again, a green "dumbbell" will appear, allowing you to specify where the newly grabbed thumbs will appear.
* Drag and Drop can also be used to apply the grade from one thumbnail to another, simply by dropping directly on top of another shot (from either Cut View or Gallery). The Drag and Drop apply obeys all of the current Paste/Apply settings. A grade can be applied to multiple shots simply by red-selecting them, switching on group grading and then dragging onto one of them.
* Pressing the 'Esc' key during any of the above drag-and-drop operations cancels the drag.
* Since there can now be three possible owners of the DBS (Cut View, Gallery & Gallery 2), the "Cut View/Gallery" button on the Blackboard now has "Alt+Tab"-style behaviour in that pressing that button slowly simply toggles between the last two DBS owners. Only if pressed rapidly will it cycle through all the possible owners.
* The Cuts and Gallery view are now capable of displaying various pieces of metadata beneath each thumbnail. To enable this metadata display, simply right-click on a thumbnail and tick the desired pieces of metadata in the "Metadata Display" sub-menu. The Cuts View, Gallery and Gallery 2 all have separate metadata display preferences, so each can be configured to display separate metadata. Most of the metadata types are read-only, the only exception being "Comment (Editable)". This is especially useful in the Galleries, as it's a convenient way to add a label to a gallery thumbnail.
* Cut/Gallery Views who don't currently own the DBS now have a "ghost" (semi-transparent) DBS drawn, showing where the DBS would be if they were to receive DBS focus.
* The three separate "Select", "Deselect" and "Invert" sub-menus in the Cut View's right-click context menu have been all been consolidated into a single "Select Multiple" menu.
* The Cut View now displays the position of all cursors within the current scene. Each cursor is drawn with a numeric label making the cursor position much easier to see.

### User Interface Improvements

*   Baselight can now support up to 3 UI monitors. Workspaces can be configured to dock any view on any of the 3 monitors.

    This functionality is only supported on Baselight TWO, FOUR and EIGHT systems, and requires a UI host with an NVIDIA Quadro NVS 450 GPU. On the Quadro NVS 450, the UI monitors must be plugged into ports 1-3, and the Blackboard plugged into port 4.

    The tablet on a Blackboard only maps to one UI monitor at a time. To cycle the tablet between UI monitors, use "Tablet Mon" on a Blackboard 2, double-tap "UI Image" on a Blackboard 1, or use Ctrl-Shift-Esc on the keyboard.
* Added inertial panning to all controls which pan across a larger area. These controls can now be panned using a middle mouse button drag anyway within the panning area, obviating the need to use the scroll bar in most situations. However, if a control embedded within a panner also responds to the middle mouse button (e.g. graphs within CurveGrade), the embedded control will win and panning will not occur.
* Improved mouse wheel support throughout Baselight, making it work in places it previously didn't and utilising inertial scrolling, allowing more subtle scrolling. The "feel" of inertial scrolling can be adjusted in the "Inertial Scrolling" section of the "UI" tab of the Baselight preferences.
* The CtrlLock+pen drag panning metaphor used in Timeline View has now been extended generally throughout Baselight, including the Cuts and Gallery views.

### Scopes and Histogram Improvements

*   Baselight now has several new views available when using the GPU Vectorscope - a vectorscope plotting Rec 709 chroma (Cb, Cr) as (x, y), with reticules showing the targets for Rec 709/SMPTE colour bars.

    Luma Waveform - a Rec 709 luma waveform.

    RGB Parade - three waveforms of the red, green and blue components of the image.

    Y'CbCr Parade - three waveforms of a Rec 709 Y'CbCr conversion of the image.

    These can be displayed in monochrome or colour mode, by right-clicking on the scope (excluding the Luma Waveform).

    Additionally, a high-resolution histogram is now generated on the GPU. This has a number of additional features, which can be selected by right clicking on the Histogram view:

    The orientation of the histogram can be made horizontal or vertical by changing the aspect ratio of the histogram view. The orientation can be locked in place so the orientation doesn't change when the view is resized.

    The histogram has three different filtering modes, none, low and high. As the resolution is higher, you may see high frequency peaks and troughs when working with limited bit-depth input imagery (10-bits or less). Increasing the filtering will make the histogram easier to read in these cases.

    An option to fill the space below the histogram curve.

    When picking colour values on the image, corresponding points will be displayed on the vectorscope/waveforms and histogram.

    The scopes and histogram match the output setting from the combiner, i.e. no-conversion, full-to-legal, clip, soft-clip.

### Timeline Alignment View

*   It is now possible to clean up the vertical alignment of all the shots in a Baselight scene. In the "Views" menu, simply select "Timeline Alignment" - a new view will pop up containing the following options:

    * Align: Specifies how to align within each track: "Stack": Either the tops or bottoms of the stacks within each track will be aligned. "Selected Strips Within Each Stack": The selected strips within each stack will be aligned. Any stacks without selected strips will be moved out of the way either "Upwards" or "Downwards".
    * Derive Tracks: Alignment occurs by putting all the shots in the timeline into a track and then aligning within each track. This setting specifies how shots are matched to tracks: "By Flattening": Shots are placed in the lowest possible track which isn't already occupied by a shot below them. "From Original Conform Tracks": Shots are placed in the same track as they were in when the scene was conformed. If the scene was conformed prior to Baselight 4.3, the behaviour will be the same as "By Flattening". "By Row Snapping": Shots are placed in tracks alongside other shots lying at a similar height in the timeline.
    * Empty Rows: The number of empty rows which are desired below and/or above each track.
    * Gap Above Lower Eye: The number of empty rows between lower and upper eyes in stereo scenes. This option won't appear in non-stereo scenes.
    * Remove Unreferenced Strips: "Yes" or "No". Whether or not to remove strips (or parts thereof) which don't contribute to the final image (ie, the semi-transparent strips in the Baselight Timeline View). It's a useful setting for simplifying a complex multi-track timeline.

    Once the alignment options have been set, simply press "Align" to vertically align the strips. Via the "Customise" menu, it's possible to store common alignment settings in tabs for quick retrieval.
* The current Timeline Alignment settings can quickly applied by pressing the ';' (semicolon) button. The Timeline Alignment view can be popped up/popped down using the Win+';' accelerator (Ctrl+';' on Mac).
* For "Rendering Avid Media and Updating AAF" and "Rendering Quicktime Media and Updating FCP XML" workflows, Timeline Sort now ensures that the original conform ranges of all shots are all present post-sort. This means that the user is free to simplify complex multi-format timelines for grading by removing unreferenced strips (in the new Timeline Alignment view) without fear of it causing Modify AAF or Modify XML problems later.

### Strip Categories

*   Strips can now be tagged with one or more categories defined on the 'Timeline' page of the preferences editor. Strip categories can be set/unset from either the UI or the Blackboard:

    From the UI: Right clicking on a strip brings up a context menu for that strip. The 'Set Strip Categories' menu option allows you to choose which categories are associated with the strip.

    ```
              The strip context menu can also be used to set
              categories for multiple strips in one go. To do this,
              select all the strips you wish to categorise, enable
              grouped grading and right click on any of the
              selections (this method also works for selections made
              in the Cutview).

              You can also toggle a default strip category using
              the keyboard shortcut 'J' or the Mark/Strips menu
              'Toggle Strip Catergory' option. The default strip
              category settings are also configured from this menu.
    ```

    Blackboard: On a Blackboard 1 the 'Mark/Strips' menu contains an option for switching the behaviour of the panel's 'I' button between toggling a default mark and toggling a default strip category.

    ```
              On a Blackboard 2 there is a dedicated button for
              toggling a default strip category (below the toggle
              mark 'I' button). This button dynamically changes its
              appearance depending on the (default) category status
              of the shot/grade strip at the current cursor
              position.
    ```
*   The 'Bypass All' toggle behaviour can be set to not bypass strips tagged with particular categories. This is useful, for example, when your stacks contain transform strips (to re-rack your shots) which you do not want to disable when viewing your stacks bypassed/without their grades.

    To specify which strips are not bypassed, select the 'Timeline' page in the Preferences editor. On that page there is a 'Category Groups' section which contains a set of categories called 'Don't bypass strips of category'. This set can also be overridden on a per-scene basis from the 'Category Groups' tab of the scene settings panel.
*   Rendering shots only containing strips of a particular category is now supported. To select these shots for rendering from the render panel, use the 'Select Frames' dropdown menu and select the categories from the 'Shots Containing Categories' sub-menu.

    For command line rendering, categories can be specified using the '-render scats:A,B,C' option (run 'bl-render --help' for more).
* Shots View allows the displayed shots to be filtered by the category of the Input Layer.

### Thumbnail Generation

*   Thumbnail generation is now completely automatic for both images and movies; Baselight no longer writes thumbnail images to disk.

    For speed, thumbnail images are cached in a separate cache directory (/vol/images/.baselight-tn-cache by default) and will regenerate as required if the source material changes. This directory is created automatically by the installer and administered in the same manner as the render cache via preferences and bl-reset-cache -thumb

    Proxy generation from the Job Manager and bl-proxygen no longer creates thumbnail images.

### Area Tracker

*   Baselight now includes a new type of tracker designed to simplify tracking areas of an image sequence. 'Area Tracks' can be created from within shape and transform strips using the 'New Area Track' UI button (or 'New AT' Blackboard key). They can also be created from an existing tracker strip (on the 'Area Tracks' page) for use later (by using 'Copy Name To Clipboard' and then pasting that name into a shape/transform 'Current Track' text box).

    Once an area track has been created, the rectangular track region can be refined by dragging the centre cross or one of the corner hotspots on the image. On the Blackboard the middle trackball is used to adjust position. The right trackball can be used to adjust the overall size and the ring to modify the X/Y size independently if required. When a keyframe is set up, the left trackball can be used either for changing the position of the result rectangle, or when holding down the ctrl key for the scale. The ring allows the rotation modification.

    The area tracker supports the same tools for refining a track as the previous point tracker. For example, if a track is lost part way through a shot (because the target object becomes occluded) it is possible to continue that track by using 'New Reference' to pick up a (still visible) part of the same object. Also, if the target goes offscreen existing track results can be extrapolated to approximate new results.

### Y'CbCr Video Grade

*   The Video grade now has a new page: Y'CbCr. This page contains new

    controls to change Lift, Gamma and Gain in Y'CbCr space. On the RGB

    page there is also a new control "Y' Lift, Gamma, Gain" which allows

    editing of the luma channel while controlling the RGB values with

    the trackballs. The Black and White points have been combined into a

    single control to allow space for the new Y' control. On switching

    to the Y'CbCr page the RGB graph changes to Y' correct graph. All

    Y'CbCr corrections are affected by the selected mode (CDL, Graphs or

    FilmLight).

### Stereo Geometry Fix

*   The Stereo Geometry Fix strip now supports a new 'Automatic' alignment mode (as well as the previous semi-automatic mode).

    To align the left/right images of a stereo pair in automatic mode, simply press the 'Analyze frame' button. This will align the images based on the default transform type. However, once the frame has been analyzed (and the images aligned) the transform type can be changed (from the dropdown) to one of the following:

    None : Disable image alignment.

    Translate : Align the current eye image to the other using only a best fit vertical translation.

    Translate,Rotate, : Align the images using a transform that includes Scale vertical translation, 2D Rotation and XY-Scaling.

    Perspective : Use a perspective transform to align the images.

    Translate, Rotate, : Align the images in 2 passes. The first pass uses Scale + Perspective a best fit translate, rotate & scale transform. A second pass performs an addition perspective pass to further refine the alignment.

    Translate, Rotate : As above but without the scaling on the first pass.

    * Perspective

    Note: The last 2 options use 2 passes to minimize potential distortion introduced by a single perspective transform.

    The 'Display alignment features' can be used to display all the matched features computed during analysis. When enabled, this mode can also be used to delete matched features. Usually this is not necessary unless there are very few features (where a single bad match might skew the results). A feature can be deleted by clicking on it in the image display with the shift key held down.

    Grayed out crosses indicate features that the transform fitting algorithm thought are too far out to correspond with the best chosen transform. This does not necessarily indicate they are wrong (but could be an indication they might be).

    Automatic alignment mode also supports grouped grading for aligning multiple shots at the same time. To use this, select all the shots you wish to align (in one eye), enable grouped grading (so all the shots flash) and press 'Analyze frame'. A progress bar will be displayed while the alignment of all the shots progresses.

### EDL Import and Timeline Sort

* When Transforms are added by the EDL Import View, they are now embedded in an Inside/Outside layer, thus allowing a layer number to be assigned to the Transform. The default layer number is 99, but this may be changed to any desired number via the edit field in the "Apply Image Transforms" row. Higher layer numbers are useful if you want to keep the transform at the bottom of the grading stack, as grading layers inserted via layer number will be inserted between the top strip and the transform.
* Transform strips inserted by the EDL Import View may now be tagged with a strip category. By default the "Editorial" category will be used, but it's possible use any category, simply toggling categories on/off in the "Category" menu in the "Apply Image Transforms" row of the EDL Import settings.
*   Timeline Sort now has a new setting allowing the user to remove strips tagged with a given strip category. By default, strips tagged with "Editorial" will be removed, however any category can be used simply by toggling the categories displayed in the "Marked by Category" dropdown in the "Remove Strips" row of the Timeline Sort settings.

    When rendering movies for the Avid AAF or FCP XML workflows, it is important the transforms generated by the EDL Import View are removed. Failing to so will mean that the Transforms are burnt into the rendered media, giving the appearance of the transform being applied twice once back in Avid/FCP.

### StereoGrade

*   Baselight now includes a new strip called StereoGrade that includes common stereoscopic workflow tools for making convergence adjustments and adding floating windows.

    As well as using sliders or dragging overlays to make adjustments, Stereograde supports making changes from the Blackboard trackballs using the following mappings:

    Left trackball : Controls the left floating window edge. Left trackball ring : Controls the tilt of the floating window edge. Middle trackball : Changes the stereo convergence. Right trackball : Controls the right floating edge window. Right trackball ring : Controls the tilt of the floating window edge.

    Stereograde includes 2 custom picking modes for measuring or adjusting convergence by clicking on the image directly. These modes are:

    "Zero convergence plan" : Moves the zero disparity plane to the selected point clicked on the image. "Display convergence" : Displays a numerical value of the computed disparity (in pixels) at the point clicked on on the image. This value will be displayed in one of three colours; Green if the disparity is positive, yellow if the disparity is negative and red if the system is unconfident of the calculated value (this might happen, for example, if the selected point is either occluded in the other eye image, the vertical disparity between the feature in both images is too large etc.).

    When an adjustment is made, Stereograde will automatically add an equivalent strip to the other eye.

    Convergence changes will automatically adjust the floating window positions so there is no need to correct them afterwards

### Matte Tool

* A collection of matte operators have been placed together in a single operator. This operator, Matte Tool, is used in place of the Blur operator. It can be configured to contain Blur, Threshold, Erode/Dilate, Median and the new Matte Curve. These can be placed in any order and as many times as is required within the Matte Tool. The Blackboard is configured to contain all the effects on available panels so each operator can be edited at the same time.
* The Matte Curve is a simplified curve grade, which is intended to only work on mattes. It is restricted to 2 control points, or a simple auto handles mode. It is intended to allow the user to have more control over the S-curve like drop-off.
* The In/Out Blur is a new blur operator which only blurs inwards or outwards from the matte. It is intended to allow the user more control over the shape of the matte during bluring.
* The Blur functionality on the Blackboard has been taken over by the Matte Tool. So when the blur button is hit, a Matte Tool plugin with only the Blur tab enabled will be inserted. This only works when the blur button is hit inside a matte. For Layers the blur functionality remains the same.

### LUT export from Shots View

*   Added LUT export format to the Export from Shots View. This provides

    options to generate LUT files equivalent to grades in the current

    scene. Grades within the scene can be replaced with Truelight strips

    using the newly generated LUT files.

### Miscellaneous

* Added Nyquist Filter strip. This can be used to reduce various forms of high-frequency noise in images. This strip was previously available as part of the Baselight Restoration option.
* Added ability to use Transform as an operator in Layers (inside/outside strips).
* Improved startup speed on machines running 260.x or greater video driver by usage of precompiled GLSL shaders.
* Shots View now has buttons that move the selection up and down in the list of shots. This can be used with a category filter, for example, to allow stepping through shots of a particular category.
* In poster frame navigation mode ("Swap Next/Prev Cut/Poster Controls" ticked on Navigate menu), Shots View will move the cursor to the shot poster frames, rather than the first frame.
* Shots View can now be navigated using Tab and Shift+Tab, and vertically (when the cursor is in a text field) using the Up and Down keys.
* Shots View now allows textual columns to be resized.
* bl-shots and bl-containers can now provide information on older scenes without requiring them to be updated in Baselight.
* The Timeline View's cursor icons now match those used within the Cut and Gallery views.
* Added ability to modify strength of "notches" on Blackboard 2 Jog Shuttle to "Blackboard 2 Setup" dialog.
*   The Output Format selected in a Sequence operator now causes the colour space conversion (from the Output Format's colour space to the cursor's format's colour space) to be applied after all any other operators in the Input Layer.

    This means, for example, that when you use OpenEXR material in a log-format scene and put an EXR Exposure operator in the Input Layer, the EXR Exposure can be made to operate in linear space by choosing in the Sequence an Output Format that is set to linear colour space.
* Added updated version of the FilmLight EDL Specification to include asc\_sat optical. It's FL-GN-TN-0476-FLESpec.txt.
* QuickTime and AVI movies with incorrect or no file extension are now correctly identified.
* Select Missing Material (on Shots View) now shows a progress panel.
* Added an option to use tetrahedral interpolation when applying cubes or profiles in a Truelight strip. Enabling tetrahedral interpolation can give more accurate results for applying LUTs, and this is the default setting for Truelight strips inserted using the Shots View's Export and conversion of grades to LUTs. This form of interpolation is slower to process so otherwise the default setting for inserting Truelight strips is not to use this.
* On MC Color desks the default encoder page is now the right hand page. The two encoder pages can still be switched using the "< Page" and "Page >" buttons.
* Added Shift+W shortcut for inserting an R3D Params strip.
* Blackboard Shift+'Mark Toggle' now removes all marks at the current cursor position. 'Join Stacks' has been moved to Control+Shift+'Mark Toggle'.
* The "Grab To Gallery" button on Blackboard 1 & 2 now grabs to the gallery view with DBS focus, or the first gallery view if none currently have focus.
* Added support for using % variable substitutions when editing the Tape column in the Shots View.
* Added support for using %W variable when changing Tape, Clip or Name fields in the Shots View. This is substituted for the source filename for a shot with the extension removed.
* Added support for ARRIRAW files from ALEXA Studio cameras utilising a neutral density filter.

## Bug Fixes Since Baselight 4.2

* Fixed paste of Layer 0 operators to a empty destination causing crash \[bug 18804]
* Fixed bug in Baselight exit where unsaved preferences changes were not correctly enumerated.
* Fixed bug which could cause a crash if the trackballs were moved while a layer was being moved up/down the stack at the same time \[bug 12579]
* Fixed "Layer 0 Op" removing all the layers when Paste mode was replace \[bug 19072]
* Fixed issue with wdaemon failing to identify certain types of wacom tablet \[bug 19071]
* Fixed bug which allowed addition of marks before start of timeline \[bug 17805]
* Copying & pasting a single Curve Grade curve now copies across the 'Auto Handles' state \[bug 17776]
* Layer number is now updated when a selected strip is moved up/down within its stack \[bug 14322]
* Fixed problem where BB keypad was being left in layer mode after a parameter paste \[bug 11643]
* Fixed thumbnails in the Layer view when gallery material was offline \[bug 19002]
* Fixed bug that caused the Apply button to lock the keypad into layer mode \[bug 17336]
* Fixed bug which could result in a crash when moving/renumbering a layer within a (single stack) dissolve \[bug 18042]
* Fixed Gallery to always show as much of the Gallery thumbnails as possible, especially when the Gallery View is large enough to show all of them.
* Fixed bug which caused two menus to pop up when a Windows+right click was performed on a docked Job Manager.
* Occasional sluggishness in the Baselight UI when having a large number of visible thumbnails in the Cut View.
* Fixed incorrect Paste/Apply behaviour when the "Replace" paste mode was used with Grouped Grading. The error occurred when a stack had separate explicit (yellow) and group grading (red) selections.
* Fixed bug where "Apply" wouldn't obey the "Paste Keyframes" preference.
* Fixed bug in Gallery View where the view would scroll to the top of the gallery if the last thumbnail in the Gallery was removed.
* Fixed occasional weird inertial scrolling in Timeline View. It occurred when undertaking a very rapid pan, stopping suddenly and then delaying before releasing the mouse button.
* Fixed in Cut View/Gallery where the thumbnail image wasn't being correctly restored to the poster frame at the end of a scrub.
* A Gallery autoload will no longer create or load a per-job/ per-scene gallery for any scene lying within the gallery job.
* Increased the width of the Tape column in Shots View \[bug 17651]
* 'Clear Undo History' now removes any references to categories no longer used in the scene's timeline \[bug 19562]
* Fixed the default movie output filename to not include scene folder names \[bug 19593]
* Fixed issue with installing Baselight on cluster systems with Nvidia 290.10 driver \[bug 19653]
* Fixed occasional slowdown in Baselight UI if a gallery failed to load \[bug 18305]
* Fixed occasional crash which could occur when closing a scene when a gallery failed to load \[bug 19619]
* Fixed issue with bl-config-xorg not generating correct xorg.conf file on Gen1-Gen3 Baselight ONEs \[bug 19645]
* Fixed cropping of Burnin text when it extends beyond a transformed image \[bug 19440]
* Fixed hang on startup on Baselight systems with Nvidia 290.10 driver \[bug 19607]
* Fixed flux failure to copy files with  characters in their filenames \[bug 4452]
* Fixed crash on Mac when monitors added/removed from the machine whilst Baselight application is running \[bug 19694]
* Fixed crash on Mac when running with Blackboard 2 enabled in the prefs \[bug 19692]
* Fixed issue with bl-config-xorg not generating correct config for UI hosts with Nvidia Quadro NVS450 GPUs.
* Fixed issue with bl-config-video failing if it was required to restart X11 \[bug 19738]
* Fixed issue where Matte tab would be temporarily inaccessible after removing current matte strip via 'undo' \[bug 19796]
* Use of the soft keyboard cursor keys will not not close the keyboard when in "transient" mode \[bug 19591]
* "Seed" value for Camera Shake can now be modified via encoder on Blackboard 1 & 2 \[bug 19703]
* Fixed crash with primaries Apply with no primaries in the stack \[bug 19870]
* Added grouped grading support to image transform settings
* Fixed Layer Output mode to work with Blanks and Bars \[bug 19914]
* Fixed GPU memory accounting on GEN4 Baselight ONE systems \[bug 19894]
* Fixed node memory monitoring on busy systems \[bug 13385]
* Truelight profile and cube directory listings no longer check any dotfiles in the default directories \[bug 19340]
* Prevented crash on recovery of scene containing a Matte Tool \[bug 19691]
* Changed the behaviour of Truelight Local Display Settings in Setups. If Local Display is set to 'from profile', or a profile with 'use local display' disabled is selected in the cursor, the Brightness and Flare values in Setups are not applied, leaving the values from the profile unchanged \[bug 19919]
* Fixed problem with the ordering of events when removing stages from the Matte Tool \[bug 19986]
* Fixed a crash in tl-player in no database mode, when inserting a movie or sequence with an unknown format \[bug 19427]
* Moved MatteMerge button to below matte element buttons on Matte tab \[bug 20029]
* Fixed crash from rendering scenes containing a Y'CbCr video grade from bl-render \[bug 20006]
* Improved handling of spurious parallel barrier ('flint') interrupts in flos 2.1, to fix 'connection timed out errors' on gen2 platforms \[bug 19485]
* Fixed a issue where when pressing "Play Backwards" on Blackboard or MC Transport desks while playing forwards would leave the "Play Forwards" button illuminated \[bug 19706]
* Improved MC Color desk support for Transform operator. Common actions are now mapped to the CG/PG button area \[bug 19705]
* Fixed issue where desk displays on MC Color desks could occasionally appear corrupt when using Videograde \[bug 20003]
* Fixed crash in Matte Tool is all the stages are deleted \[bug 20073]
* Fixed slow updates to Truelight values in Setups when there are large numbers of profiles and cubes in the default Truelight directories \[bug 20080]
* Fixed MatteCurve click off setting handle to zero \[bug 20089]
* Fixed problem with deleting Matte Tool then reinserting \[bug 20040]
* Fixed problem with deleting the last stage then undoing \[bug 20078]
* Fixed crash hitting the gallery buttons with no scene open \[bug 20156]
* Fixed bug when applying a scratchpad slot to outgoing shot of dissolve \[bug 13240]
* Fixed crash while moving the encoder while switching to the Matte Tool \[bug 20177]
* Added preset drop down to the Matte Tool Matte Curve \[bug 20092]
* Fixed crash when doing a stereo sync operator when the destination strip does not contain an inside outside \[bug 20096]
* Fixed crash when toggling Auto handles in Matte Tool matte curve \[bug 20185]
* Fixed crash on Blackboard 2 when using "Ctrl"+"Shift"+"End" shortcut to switch off desk lights \[bug 20211]
* Reduced amount of Blackboard 2 related chatter in log. Now only reports firmware revision and diverts error messages to stderr \[bug 19605]
* Fixed stereo stack sync so that stereo operators correctly invert parameters
* Fixed StereoGrade in an inside outside doesn't turn purble when convergence changed \[bug 20215]
* Fix for issue with desk encoder movements sometimes being lost when editing control points in Matte Tool Matte Curve \[bug 20140]
* Fix for rightmost screen on Blackboard 2 not being cleared when closing current scene \[bug 20197]
* Fixed the gallery getting locked into a "Try" state if the "Gallery/ Cut View" button was pressed whilst "Try" was down \[bug 20208]
* Fixed behaviour of "Alt" keys on Blackboard 2 \[bug 20243]
* Fixed StereoGrade disparity display should be in parallax/theater space \[bug 20260]
* Fixed crash caused by very large LUTs applied to the cursor \[bug 19356]
* Fixed bug which could potentially cause a crash when using 'Try'/'Apply' with 'Include Input Strip' paste option \[bug 20216]
* Added test to prevent moving strips above the paste destination if there is enough space to fit the resultant stack \[bug 20221]
* Fixed bug which could cause a crash after many (specific) grade 'try' actions from the Cutview or Gallery \[bug 9633]
* Fixed apply being applied to incorrect stack in an AB dissolve \[bug 20305]
* Added check on selected strip to prevent crash on apply \[bug 20271]
* DFuse and Sharpen now appear correctly on Blackboard 1 & 2 when used in an Inside/Outside strips \[bug 20293]
* Removed Grade/Matte switch from Baselight Transfer application, where matte operations are not available \[bug 20298]
* Fixed crash in applying from an empty stack with primaries on \[bug 20320]
* Improved error message when renders fail on Baselight FOUR/EIGHT systems, for example when the output disk is full \[bug 18542]
* Fixed issue with audio playback not working on systems with RME Hammerfall HDSP PCI cards \[bug 20322]

Release history prior to Baselight 4.3 has been removed to prevent this file becoming too large. If you believe you need access to this, please contact baselight-support@filmlight.ltd.uk.
