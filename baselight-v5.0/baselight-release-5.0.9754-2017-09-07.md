# 베이스라이트 릴리즈 노트 5.0.9754 (2017-09-07)



## New Features Since Baselight 4.4m1.9553

### PLEASE NOTE: Upgrading Scenes

*   Baselight 5.0 currently cannot open scenes from earlier releases of the software. Instead, existing jobs need to be upgraded to the new database storage back-end (see "Scene Storage" below).

    To do this upgrading, Baselight 5.0 uses Baselight 4.4m1.9747 as a helper application. You must have this 4.4m1 build installed on your system if you wish to upgrade or import pre-v5.0 scenes & jobs.

    This requirement will be removed in a later Baselight 5.0 release.

### Base Grade

* Base Grade is a new grading operator which works in a linear colour space modeled on human perception, thus ensuring that changes to tint and saturation have the same apparent effect regardless of the colour they are applied to.
*   Base Grade is colour-space aware, converting appropriately to its internal space, so it retains the same feel regardless of the working colour space. However, this makes it extremely important that the user is accurate when tagging input material with a colour space - if input material is incorrectly tagged, then Base Grade will use an incorrect conversion to/from its internal grading space and will therefore feel odd.

    For this reason, Base Grade is often used first in a stack, when the input to the Base Grade operator accurately reflects the working space of the scene. If you wish to use Base Grade lower down the stack, after something which makes a large contrast change, it will likely be necessary to insert a ColourSpace operator in "Identify" mode before the Base Grade to ensure that the Base Grade performs the correct conversions. So, for example, if the stack contains a Truelight operator which converts from ARRI LogC Wide Gamut to P3, then a Colour Space operator in "Identify" mode with "Convert To" set to "DCI: 2.6 Gamma / P3 DCI" should be inserted after the Truelight operator and before the Base Grade.
* Base Grade has four settings which affect the entire image:
  *   Flare: Sets the zero level by modifying the lower part of the

      ```
         tone curve. Everything lying at the zero level will be
         unaffected by exposure changes.
      ```
  * Balance: Overall exposure and two tint axes.
  *   Contrast: The overall contrast of the image, around the

      ```
         Control Pivot setting.
      ```
  * Saturation: The overall colourfulness of the image.
* In addition, there are 4 additional "zones", each representing a part of the tone curve - Dark, Dim, Light and Bright. Each zone has the following settings:
  *   Exposure + Tint: Localised exposure and tint change applied

      ```
         to the zone. The full effect is only realised once past
         the falloff area.
      ```
  *   Pivot: Point in the tone curve where the localised changes

      ```
         begin to take effect.
      ```
  *   Falloff: How quickly the full localised effect of the zone

      ```
         correction is reached.
      ```
  * Saturation: The colourfulness of the zone.
* All Exposure and Pivot values are expressed in stops relative to the 18% grey card. This scale was chosen because it is familiar to both cinematographers and colourists.
* The axes of the graph representing the effect of the Base Grade are also expressed in stops relative to 18% grey.
* A luma waveform, again expressed in stops relative to 18% grey, is drawn behind the graph and pivot lines. This makes it very easy to position pivot points in areas of the tone curve which have very few pixels, allowing large changes in a zone's exposure to be made without introducing artefacts.
* When in trackball mode, all of the parameters relevant for a given zone can be manipulated directly from a single trackball. By default, the trackball ring controls the Exposure. However the Pivot, Falloff and Saturation can be temporarily manipulated by holding down the modifier buttons lying directly above the trackball.
* Base Grade introduces a new on-screen colour wheel control, with the following advantages:
  *   Dragging in the colour wheel area now applies a smaller relative

      change, rather than exactly following the mouse cursor. This

      makes making subtle corrections using only the mouse much more

      convenient.
  *   There is now a virtual trackball ring around the colour wheel,

      any part of which can be dragging in a clockwise/ anti-clockwise

      fashion to raise/lower the exposure in a zone.
  *   The size of the master correction is now shown as a blue arc

      drawn superimposed over the left hand side of the virtual

      trackball ring. This is much more visible than the old standard

      slider and also saves space.
  *   Secondary parameters for a zone like Pivot, Falloff and

      Saturation are represented by text boxes to the bottom-right of

      the virtual trackball. They can be directly manipulated by using

      the new gestural grading functionality.
*   Base Grade supports colour matching, making match-grading of similar shots much more convenient. Below the graph, there is a colour well representing the colour to match against - by default it is 18% grey. To change the match colour, simply enable the "Pick" toggle and drag in the image viewer - it will sample pixels from the _output_ of the Base Grade and store the average of the drag in the colour well. If you want to edit this colour, or match a specific sRGB colour, simply click the colour well to launch Baselight's standard view.

    To match this colour, enable the "Match" toggle (it will switch on automatically after a successful "Pick" drag) and in the same or another Base Grade instance, simply drag in the image viewer - the Base Grade settings will be updated to make the average colour of the dragged area match the previously picked colour.

### FLUX Manage

*   A new graphical file manager replaces the Sequence Browser and the flux application.

    The main FLUX Manage view shows tabs on one or both sides of an information area.

    The tabbed views are where the file system searching, filtering and management is controlled.

    **Browser Tab**

    The initial Browser Tab shows a standard volume and file browser at the top with a view below showing the sequences found in the selected directory.

    The file browser allows multiple selection using ctrl-click (command-click on Mac).

    The controls at the top of the sequence view are:

    * view buttons which change the display between a grid of sequence thumbnails, a list of sequences showing additional metadata and a list of non-sequence files.
    * a Pivot button which shows the breakdown of all the metadata in the displayed sequences, and allows selection based on metadata. Double-clicking opens a new filter tab using the selected sequences.
    * a filter button which creates a filter tab using all the sequences and adds a filename filter to allow selection by filename.
    * a draggable tile representing all the sequences. On the left side of this tile is a pin which allows these sequences to be retained and added to another search from another browser directory.
    * a Descend button which causes all subdirectories of the selected directory to be searched. This can be slow on an unindexed filesystem.
    * a refresh button to re-scan the directory.

    Under this are the sequences, with a control at the top right to select which metadata is displayed.

    **Managing Sequences**

    Anything which represents one or more sequences (including a thumbnail, multiple selected thumbnails, any sequence tile, a scene or a job from the Job Manager, a directory from the file browser) can be right-clicked or dragged in order to filter the selection or to perform an action on the sequences, such as copying them to another location or erasing them.

    * drop onto a directory in the file browser at the top to copy to that directory.
    * drop onto a directory in the Copy Destinations area to copy to that directory.
    * drop onto the Action Bar which appears at the bottom of the window to filter, convert, copy or erase.

    **Filter Tab**

    FLUX Manage introduces a powerful filtering mechanism to allow you to locate precisely the sequences you wish to find, with an intuitive graphical filter editor.

    A Filter Tab is started with a collection of sequences you wish to filter. This can be done in several ways:

    * right-click on a sequence thumbnail, or any tile representing a set of sequences and choose "View or Filter".
    * drag sequences to the Action Bar and drop on "View or Filter".
    * drag a filter tile from the Tile Library over the sequence view.
    * drag a metadata name over the sequence view.
    * double-click a value in the Pivot view.
    * press the F key to start creating a filter from the keyboard.
    * press the S key to start creating a sort filter from the keyboard.

    A Filter Tab shows, from top to bottom:

    * a draggable tile representing the result of the filter. This tile contains the specific sequences which are the result of the filter; this collection of sequences will not change if the filesystem changes.
    * a Recalculate button which clears the calculated filter results and regenerates them. This may be a slow operation if it requires scanning the file system, or scenes.
    * Undo and Redo buttons which step through your changes in the filter editor.
    * the Filter Editor.
    * a sequence view which is very similar to the sequence view on a Browser Tab, but without some of the additional controls on the top bar.

    Double-click on the tab itself to rename it.

    **Filter Editor**

    The Filter Editor is where FLUX Manage filters are constructed.

    Drag a tile over an existing tile in the Filter Editor to add it to the filter.

    Often a tile can be applied in more than one way (e.g. the Tape filter can either filter the sequences by Tape, or sort the sequences by Tape) - if so the tile is split into drop zones which are described above the tile.

    Right-click on a tile to edit or remove it. Many tiles also allow double-click to edit.

    Many filters can be applied using a variety of tests. Numeric filters such as Width can use less-than, greater-than, equal-to etc. Textual filters such as Tape can use equal-to, not-equal-to and regular expression comparison to look for parts of words (e.g. matching Tape against A will show all sequences whose Tape contains the letter A). Regular expression syntax such as ^A\d may be used.

    Filters may be dropped to expand ("or") or restrict ("and") the selection, or to refine the sort order ("then").

    Sequence tiles may be dropped to add ("plus") or subtract ("except") the sequences. This allows filters like "all sequences in these three directories except the ones used by these scenes".

    Dropping a single sequence offers the "Match Metadata" drop zone to quickly filter to match by one or more metadata value.

    **The Information Area**

    The information area contains, from top to bottom:

    * a button to open the Tile Library, a text field for searching the Tile Library, and view buttons to control whether a tabbed view is shown to the left, right or on both sides. Having two views can be useful when copying media from one volume to another.
    * the Tile Library (initially hidden) containing draggable filter tiles which can be used to construct filtering operations.
    * a draggable tile representing the currently selected sequence(s).
    *   metadata for the currently-selected sequence. If more than one sequence is selected, metadata is shown for the last-clicked sequence, indicated by a dashed selection box.

        Most metadata names (e.g. Encoding, Tape etc) can be dragged to create a filter matching the value of that metadata for the selected sequence.
    * a list of keyboard shortcuts that are currently available.
    * Copy Destinations, where directories can be dropped for ease of access.
    * Operation History, where queued operations submitted from FLUX Manage are shown, and from which the Queue Monitor View can be opened.
    * Preview and Play buttons which present the currently-selected sequence(s) on the main Baselight display.

    **File Operations**

    Operations to copy, convert and erase sequences are submitted to the Operations Queue and performed by the flux service (just as Consolidate copies were in Baselight 4.4m1). There is no need to leave FLUX Manage or Baselight running while these operations are in progress.

    **Using FLUX Manage to insert Sequences in Baselight**

    * double-clicking on a sequence thumbnail inserts it into the scene.
    * double-clicking on an all-sequence tile inserts all the sequences into the scene.
    * sequences can be dragged and dropped onto the Timeline View or Cuts View to insert into the scene.
    * scrubbing a thumbnail displays the sequence on the main Baselight display, in the same way as scrubbing in the Gallery View or Cuts View.

    A row of controls at the bottom of FLUX Manage View allows:

    * Channel/Track and View options which show the OpenEXR channels/layers and views for the selected sequences and which both change all thumbnails to use these settings and control the behaviour of the sequences when inserted into a scene
    * Colour Space, Format and Frame Rate options to control the behaviour of the sequences when inserted into a scene.
    * Insert button to insert the selected sequence(s) into the scene.

### Compress Gamut

*   The new Compress Gamut operator fixes strange colour effects in saturated colours from very small or negative RGB values. Turn up the threshold to see the effect. 0.1 is a typical threshold setting.

    Suppose you point a camera at a scene with a bright yellow light. The camera records sensible raw red and green signals from the yellow light, but the raw blue may be little more than noise. When the raw signals are converted to image RGB, the blue channel may be very noisy, clipped, or negative. Subsequent grades may make this worse.

    In this yellow light case, Compress Gamut picks up when the B value is much less than max(R,G), and applies a smooth function to map all small and negative values onto small positive values.

### Texture Equaliser

*   The new Texture Equaliser operator divides the image into a set of spatial frequency bands.

    Each frequency band has a separate Gain control. Each Gain control scales the signal in its frequency band. This can be used to smooth or enhance textures such as flesh tones in each band. The default 1.0 setting gives no scaling.

    The Threshold setting puts a soft limit on the gain. Sharp features such as edges have a large component in each band. We do not usually want to change the gain on these features. The default setting lets us change our textures, without changing the sharp features too much.

    Example: If we reduce the Gain on the 2:1, 4:1 and 8:1 bands, this will smooth skin tones, but preserve the texture of the pores and other fine detail. Increasing the Gain on the 16:1 band may restore some of the shadow modelling. Use a mask to restrict the filter to the face we wish to smooth.

### Texture Blend

*   The new Texture Blend operator divides each image into a set of

    spatial frequency bands. Each frequency band has a separate Blend

    control. This allows you to get a smooth join between two images

    with a sharp-edged matte.

### Denoise

*   A new, third-generation Denoise operator replaces the earlier Denoise function seen in Baselight 4.4m1. The controls have been re-arranged to give a better separation between the spatial and the temporal passes. The controls are disabled until you pick your sample region. The pick should give better performance with the default settings. There are options to track moving detail using optical flow; this can give better results, but is slower.

    The denoiser tries to remove noise while preserving features like edges that extend over many pixels, and/or several frames. The first and last frames may not have the full set of neighbours, so start on a frame in the middle of a sequence before setting the controls.

    Denoise can be used anywhere in the stack, but is best used on raw image data, before any colour or spatial operations. If your image has a fixed pattern, a filter tuned to remove this pattern will do a better job than this general purpose filter, and this will give the denoiser a better chance. You might usefully put something like the Nyquist filter before Denoise. If your sequence has filter options, you may want to try those too: a filter for a specific camera may be more effective than a general tool.

    The Denoise tool starts off disabled, with Pick set to 'None'. You need to drag a rectangle over a featureless region on the image to sample the noise. This rectangle must be bigger than 16x16 pixels, but does not have to be huge. A second drag will overwrite the previous one. If you are happy with you pick, set Pick to 'Locked'. This will protect it against accidental overwrites if you click on the image.

    You may get a warning about detail within the pick. There may be some texture or fine detail that you could not see until the noise was removed. Or you may deliberately pick some subtle features that are on the limits of the ones you want to keep. If you are happy with what the filter is doing, you can ignore this warning. If there are problems, click on the Pick '?' help button for more details.

    Next, set the Denoise Level control. A larger value takes out more noise, but may remove image detail too.

    Removing noise from an image can make it look softer, even if no real detail has gone. Resharpen may restore some of the look of the original image.

    The Temporal filter has several modes. The 3-frame integer fit is the fastest option that gives good results. The flow options are slower, but can give better results with steadily moving features. The 1-frame setting turns off all temporal processing. This is faster, but not as good at removing noise. It is mainly used as a diagnostic to distinguish the Spatial filtering from the Temporal filtering.

    The Temporal filter uses the Frame Threshold. Increasing this removes more noise, but you may lose sharpness, or introduce 'ghost' edges from other frames. The default value is good for the 3-frame modes, but this setting becomes more critical when you use more frames.

    For most material, that should be all you need to do.

    There are three sections of Advanced settings. These parameters were used for development, and have been retained as they may help with exceptional images.

    Advanced Colour sets the luma-chroma colour space the Denoiser works in. Quiet scales all the internal colour space values. Tone Bias changes the power law, favouring the highlights or the shadows. Chroma bias scales the chroma values, so you can denoise the chroma channels more than the luma. There are also three sliders for blending a fraction of the original image in this luma-chroma colour space.

    Advanced Spatial sets up the Denoise first pass that works on a single frame. Advanced Temporal sets the Denoise second pass that can use several frames.

### Boost Contrast

*   The new Boost Contrast operator boosts the contrast in the midtones. The effect is similar to a Sharpen with a very large radius, but it is rolled off for the highlight and shadow tones to keep the fringe values in gamut.

    The Gain control varies the amount of sharpening. A zero value gives no effect. A negative value makes the image softer.

    The blur radius is set to a useful default value for the gain. You can scale the blur radius using the Scale control in the Advanced settings. A Scale of zero gives no effect. This filter uses very large blurs: if you are not hitting rate, try a smaller Scale setting.

    The anamorphic control can be used to correct for non-square pixels. This may not be necessary: even if you are working with 2:1 anamorphic material the elliptical correction can look good.

### Boost Colour

*   The new Boost Colour operator boosts the saturation for the

    mid-gamut colours in the usual way, but this boost is rolled off

    toward the gamut limits, so we do not get unrealistic saturation in

    highlights, bright colours, and flesh tones.

### Boost Shadows

*   The new Boost Shadows operator scales the dark values in extended

    shadows. This is to simulate our eyes' adaption as they scan from

    highlights to shadows in the original scene with the original

    extended contrast radius.

### Shader

*   The new Shader operator allows Autodesk Matchbox shaders to be used in Baselight. This provides a powerful way to extend Baselight's functionality using a simple established cross-platform mechanism.

    A set of "crok" shaders from logik-matchbook.org are installed with Baselight. Please note that these shaders are not supported by FilmLight, and that bugs or incompatibilities may prevent them from working in Baselight.

    Additional shaders may be downloaded from logik-matchbook.org, but note in particular that many of these shaders are not licensed for commercial use \[bug 32178]

### Grid Warp

*   The Grid Warp operator can be used to warp/distort areas of a sequence by modifying 2 grids of control points (CPs): the "Source" grid & "Destination" grid. These 2 grids are accessed separately from the 2 tabs in operator's parameter controls.

    Image pixels under the CPs of the source grid will be warped to the position of the matching CP of the destination grid.

    Both the source & destination grids share a transform (which can be tracked). You can toggle between editing the grid CPs & the transform by clicking in the space between the CPs.

    You can also explicitly drag out a rectangle for the grid's transform on the image using the "Set New Transform Rectangle" button.

    **Adding/Removing Control Points & Grid Lines**

    Both grids always have the same number of CPs. You can add a new CP by holding the Windows keyboard modifier (Ctrl on a Mac) & clicking where you want to add a CP. A complementary CP will be automatically added to the other grid.

    You can remove a CP (or grid line) by holding down the Windows+Shift modifiers and clicking on the CP (or grid line).

    **Editing Control Points & Handles**

    By default, CP handles are hidden and automatically calculated based on the position of the CP itself. Handles can be manually edited by switching off the "Auto Handles" option. Once disabled, handles become visible & draggable. Handles can be individually adjusted by holding down the Ctrl modifier (Cmd on a Mac) whilst dragging a handle endpoint.

    Multiple CPs can be selected for movement by dragging out a selection rectangle. Additional CPs can be added to the selection by holding down the Ctrl modifier & dragging out another rectangle. CPs can be removed from the selection by holding down Shift & dragging out a rectangle over the CPs to be excluded.

    To reset the selection, drag out a small rectangle between the CPs.

    **Blackboard/Slate Support**

    These desks have additional controls for streamlining common grid editing operations. For example:

    Left Trackball Modify the position of the currently selected control point (or control points). Middle Trackball Modify the translation/rotation of the grid's transform. Right Trackball Modify the scale of the grid's transform.

    There are also explicit buttons/encoders for selecting/modifying rows and columns of control points, hiding overlays etc.

    **Example Workflows**

    1. Modify the destination grid/transform only - For basic warps, the source grid/tab can be ignored completely. Simply position the (destination) transform to cover the image area to warp and add/modify CPs on the grid to achieve the desired result.
    2.  Setup source/destination CPs _before_ warping the image - To do this, first go to the "Source" page. You will see an additional toggle button - "Sync Destination Grid To Source" When enabled, any modifications you make to the source grid will be automatically copied to the destination grid. When the 2 grids are the same, the warp has no effect on the image. So, with this option enabled you can use the source grid to initially position/add/remove CPs in & around areas you wish to affect without modifying the image.

        To then warp the image, return the the destination grid & adjust the CPs from there.

### Paint

*   A new Paint operator has been added. It has two distinct modes, Matte and Composite.

    **Matte Mode**

    Much like the Shape operator it can be used to add or remove areas from the matte using paint strokes.

    Each stroke is defined by a brush, where the width, hardness, and opacity can be set.

    The Paint operator can be added with the 'e' shortcut, selecting it from the Matte Operators grid or from the Blackboard/Slate. This means that the Dilate and Soften hotkey has been moved to shift-m from shift-e.

    Once the operator is added, strokes can be drawn directly onto the monitor (make sure the render mode is displaying matte channels). Layers can be managed by right clicking on the layer control. Brush size and softness can be adjusted via the brush controls but will only affect the next newly created stroke. The existing stroke's brush can be edited in the 'Existing Stroke' tab. This will change all the values in the current layer by a relative amount. The 'Previous Stroke' tab will just change the previous strokes brush values.

    Strokes creation can be animated in the layer controls, so motion can be created with the addition and removal of areas. To turn the brush into an eraser click on the button next to the style drop down or press q.

    When drawing a stroke you can force the current line to be a straight line by holding down the shift key.

    Each layer also has a separate opacity control which can be keyframed.

    Each layer can be transformed and the transformation can be animated independently of each other. Each layer transform can also be attached to trackers allowing each layer to follow a different feature on the original image. This also allows the use of perspective planes. A perspective plane can be drawn and the 'area perspective' tracker used to define a 3d plane throughout the duration of the strip. Once a perspective plane has been defined then the cursor will follow the perspective plane and all stroke will be drawn in perspective. You can define a different perspective plane per layer. When creating a new layer the currently selected layer's perspective plane will be copied onto the new layer. This can be removed or adjusted with the perspective controls.

    **Composite Mode**

    Paint can also be used in composite mode with the clone or colour brush. You can add a paint strip as a layer, click on the comp button, and start painting on the image. In Colour mode the colour can be selected by holding down the meta key and moving the mouse. The colour selected will match your mouse location. When in Clone mode the offset can be set by holding meta key and click and dragging out from the clone source to the desired painting location. You can add to your current offset by holding Meta + shift. If you have set a time offset then holding meta will show your source frame.

    Composite brush modes also have an additional parameter called exposure. This allows adjustment of the exposure values of the clone and colour strokes, so they can be match graded into place. This can be done either by setting an initial value or by switching to the 'Previous Stroke' or 'Existing Strokes' Tab and editing the exposure values of the existing strokes. This is the same for other values of the brush as explained above in the Matte section. This allows to match grade the stroke in place on the image.

    The layer also has a separate keyframable exposure setting.

    The time offset can be set as an absolute value from the start of the strip, or as a relative offset from the current frame. To set the value either enter it in frames, move the mouse to the correct frame and click set, or hold down ctrl and windows key and drag the mouse left and right

### Perspective

*   The Perspective operator allows an image to be transformed in perspective by specifying four points (In Corners) and their corresponding Out Corners.

    This operator is available through the 'Layer Mode' Menu in the Inside/Outside operator, by choosing 'Matte From Shape', 'Matte From Foreground Shape', or 'Matte From Foreground Alpha'. It can also be inserted as the last foreground operator or as a standalone strip, via the 'Insert' menu.

    The Perspective operator has 3 tabs:

    *   'In Corners', used to defined four independent screen corners

        representing a plane. They can be edited interactively, or via

        sliders. The 'New Quad' option can be used to define an axis

        aligned rectangle on the screen using dragging. The corners can be

        animated.
    *   'Transform' tab, a standard Transform used to reposition, scale,

        or rotate the image without affecting the In or Out planes.
    *   'Out Corners', used to defined the four independent screen

        corners, representing a plane. They can be edited the same way

        as the 'In Corners' tab.

    The 'Crop to Out Rectangle' option will turn on cropping to the Out Corners.

    The 'Show Grid' option displays an overlay which helps to position the quad according to the scene's natural geometry.

    The 'New Seq. Pick' option allows us to define a quadrilateral using four sequential picks (left click) on the image. The current picks can be discarded using right click if the quadrilateral is not complete.

    The Motion Blur option is designed to reintroduce blur due to motion.

    **Tracking**

    The 'In Corners' and 'Out Corners' can be tracked independently using Perspective Trackers.

    A new 'Perspective Tracks' tab has been added to the tracker operator, which encapsulates either four Point Trackers on a perspective plane or a Perspective area tracker.

    **Blackboard/Slate Support**

    These desks have additional controls to edit the quadrilateral in the In / Out tabs or the standard transform in the Transform tab:

    Left Trackball Modify the selected corner position (In / Out tabs), of the currently selected control point (or control points).

    Middle Trackball Modify the translation (All tabs) / rotate (Transform tab)

    Right Trackball Modify the scale in X and Y / the scale in X (All tabs).

    There are also explicit buttons for selecting the desired corner to modify using the left Trackball.

### Perspective Plane

*   Shapes, Grid Warp and Paint now have the ability to define a plane to work in perspective.

    The 'New Seq. Pick' option is used to define the plane using four sequential picks (left click) on the image. The current picks can be discarded using right click if the quadrilateral is not complete.

    The 'Show Grid' option displays an overlay to help positioning the quadrilateral according to the scene's natural geometry.

    The 'Plane' option will display/hide the plane overlay.

### Tracker

*   The Tracker strip now supports Perspective Trackers to track / lock controls to planes in 3D. This information is available in the 'Perspective' tab.

    The Perspective information of the scene is extracted using one of two types of tracker: the '4 Point Persp.' or the 'Area Persp.'. Both work with reference to one plane, albeit in a different manner:

    *   The four Point Trackers can be positioned anywhere in that plane,

        as long as the tracked area stays still relative to that plane.
    *   The Area Tracker created from a 'Area Tracker Persp.' will

        compute the motion using a perspective model in the selected

        area, the same way the Area Tracker extracts a 2D motion.

    The Perspective Track can be created only from within strips that support it, e.g., Shape, Perspective, Paint and Grid Warp. When the Perspective Track is linked to the current frame, the latter will not move and it will be used as a reference to obtain the relative position of the previous and next frames respectively.

    The Perspective Track can be converted from a Perspective Area Tracker to a four Point Tracker and vice versa.

    The Tracking widget (available in Shape, Transform, Paint and Grid Warp) has a new dropdown list indicating the trackers available to the tracker strips above the selected strip. Hovering the mouse over an entry will display the corresponding tracker overlay.

### Mastering Colour Space

*   Baselight is a floating-point colour corrector, and in the near future most DRTs will be formula-based. This means that the user can (and will) generate values outside of the display colour space used while grading. This happens when contrast and saturation are added to an image: strong saturated colours will be pushed far outside of the display colour space. While grading the signal is clipped on the SDI output signal. As this is an integer device, 'Out Of Gamut' colours will be clipped. But if the image gets rendered to a bigger colour space after grading (for example generating 'DCI XYZ' after grading in 'DCI P3') colours may be encoded in the deliverable which were not seen while grading. This is especially crucial in Telecine- or Video-Style Grading.

    In Baselight 5.0, a Mastering Colour Space can be specified which acts as the maximum allowed gamut. After the DRT or after the "Grade Result Colour Space", Baselight now clips to the gamut of the Mastering Colour Space. Its behaviour can be thought of as a 3D Colour Limiter. This clipping only applies in the display pipeline if the cursor or render colour space is a display-referred colour space.

    The Mastering Colour Space is set in the Scene Setting for the whole scene. However when changing the display viewing condition, the user may also wish to change the Mastering Colour Space (e.g. because there is a different gamut for 48 nits vs 1000 nits). To simplify this, a specific Mastering Colour Space (and Mastering White Point) can be defined per in a DRT Family. Baselight then automatically chooses the Mastering Colour Space and Mastering White Point based on the Cursor or Deliverable colour space.

    The Mastering Colour Space setting can be found in the 'Advanced' Section of 'Scene Settings' -> 'Formats and Colour' \[bug 35216]
*   In Baselight 4.4 the handling of the neutral axis was neglected. In the most cases, Baselight performed an implicit white-point remapping, but in some cases Baselight performed a white-point shift at the end of the chain (for display-referred colour spaces with a creative white-point). This meant that it was impossible for the colour grading operations to know what the white point in a given step was and that what R=G=B actually meant was not defined.

    This changes in Baselight 5.0. In the 'Mastering Colour Space' section the user specifies a 'Mastering White Point' for the scene. This tells the system what R=G=B in the stack should actually mean.

    This introduces several advantages:

    *   White-Point Handling on the Output

        By knowing what R=G=B should mean from a creative standpoint, Baselight can displays the neutral axis consistently over a variety of actual display-referred colour spaces and automatically perform a correct white-point shift for displays which have a different white-point from the Mastering White Point.

        That also means Baselight no longer needs display-referred colour spaces with "creative white points", so they are removed in Baselight 5.0.
    *   White-Point Handling on the Input

        If scene-referred data is imported, it is rational to assume that R=G=B in the data should be mapped to R=G=B in the stack colour space. Thus it follows that scene-referred to scene-referred colour space conversions do not alter the neutral axis.

        If display-referred data is imported into a scene-referred stack, Baselight assumes that the source will be graded. Thus it follows that display-referred to scene-referred colour space conversions do not alter the neutral axis.

        If display-referred data is imported into a display-referred stack, Baselight assumes that the user wants to see the image as it was authored. Thus it follows that display-referred to display-referred colour space conversion take the white-point of the input data and the white-point of the scene into account.

        The Colour Space Journey View shows the Mastering Colour Space and Mastering White Point in use \[bug 35922]

### DRT Families

*   With the development of wide-gamut and High Dynamic Range displays, the visual difference between displays is getting larger and a single Display Rendering Transform (DRT) is no longer sufficient to ensure a similar viewing experience across displays.

    A DRT Family is a collection of DRTs that will elicit a similar visual result on different displays. Baselight automatically uses the appropriate DRT based on the ViewingCondition tag in display-referred colour spaces.

    DRT Families are identified with a 'multiple-curve' icon in DRT menus. Normal DRTs have a 'single-curve' icon. If a DRT Family is selected another menu appears, where an individual DRT from the Family can be selected. However an 'Automatic' mode can be used, so that the correct DRT is chosen based on the colour space used by the Cursor or Deliverable.

    The Colour Space Journey View shows the selected DRT.

    This release includes two DRT Families:

    *   Truelight CAM (Colour Appearance Model)

        This is a newly-developed parametrised DRT. Its aim is to achieve a robust colour reproduction based on human perception of colour. It does not include any pleasing or preferred colour reproduction like a 'Film Look'. But it models the apparent colours on a given display.
    *   ACES RRT 1.0.1

        This reflects the RRT 1.0.1 and the tone-mapping parts of the different ODTs to elicit the same result as a given RRT + ODT combination \[bug 35538]

### Matte XYZ

*   Matte XYZ is a new matte operator that works with additional compositing channel information to extract a matte using world position information. This allows matting a specific volume in 3D space, using image data often generated in 3D CG pipelines and rendered into floating point image formats.

    To set up the stack correctly, a sequence that contains world position information should be inserted. Ensure that there are no colour space conversions affecting the sequence and no non-floating point caching on the input sequence strip, as that will clip and alter the pure floating point data, leading to potentially skewed results.

    The position of the matte volume can be manipulated using the four central 3D viewports displayed in the main UI. These have following controls:

    * Clicking on the little arrow buttons will expand/collapse the current viewport to a single viewport or back to the four viewports.
    * The home button will reset the viewport camera back to its initial position.
    * Holding the middle mouse button and dragging will pan the camera left/right/up/down.
    * Holding the middle mouse button and control-dragging left/right will zoom in/out.
    * Holding the middle mouse button and shift-dragging in free camera view will rotate the camera around a specific point in space.
    * Right-clicking will bring up a context menu for changing some operator and viewport parameters.
    * Left-clicking will put the gizmo location to the nearest position to that point.
    * In all views except the free camera, dragging allows selection of an volume around the displayed gizmo location.
    * Dragging on any of the gizmo arrows will move the gizmo in the direction pointed by the arrow.

    Alternatively it is possible to select the volume in the main output display area, by simply left clicking on the centre of the area you want the volume to be initially positioned. Selecting the volume in the main output works in the same fashion as in any of the other matte key operators.

    Currently MatteXYZ has the option of two different matte volumes: a sphere with arbitrary radius, and a 3D box.

### New Shots View

*   Baselight's Shots View has now been replaced with the one from Daylight. The new Shots view includes improvements such as:

    *   The ability to set up multiple tabs, each with a different

        list of shots from the scene based on custom filter criteria

        (e.g. "all graded shots from camera A").
    *   Improved shot metadata handling, including the ability to add

        new custom metadata columns, column metadata expressions etc.
    *   Much improved performance/interactivity in scenes with large

        numbers of shots.

    By default, the Shots view has 3 shot tabs: "All Shots", "Graded" and "Current Tape". At the bottom of the view there's a "Filtering" section which determines the shots that are visible in the current tab. As "All Shots" is selected by default, there are no filter options set. However, if you select "Graded" or "Current Tape" you will see these options change to ensure the appropriate shots are listed in that tab.

    The current tab's shot list can be locked using the lock icon button at the top of the view. This ensures shots are not added to/removed from the shot list - even if they're altered to no longer match the filter criteria (e.g. a shot transitioning from ungraded to graded).

    A tab's shot list can also be sorted based on columns other than event number by clicking on the header/title of the column you wish to sort by. Clicking a second time on the column header will reverse the sorted order.

    The current tab's filtered shots (and ordering) can also be applied to the timeline for playback and navigation. This can be enabled by either:

    *   Enabling the "Playback/Navigation" toggle at the bottom of the

        Shots View.
    *   Selecting a tab page from the "Playback Filtering" section of

        the play controls.
    *   Holding down the Windows key (Ctrl on the Mac) and pressing the

        Tab key to cycle through the tab pages.

    Once enabled, the timeline will grey out/darken areas containing shots not in the current tab's filtered shot list. Also, during playback those areas will be skipped. Jumping between shots (and stepping frames) will also ignore filtered out areas of the timeline.

    Which columns are visible can also be customised per-tab (using the dropdown to the right of the column headers) as well as their display order (by dragging and dropping the column header text). All of these tab customisations are saved along with the scene.

    Timeline strip selections can be synced to the selected shots using the "Sync Strip Selections To Shots" option (available from the "Customise" and right-click menus). Once enabled, the Shots View will attempt to automatically select all strips in the timeline that constitute the red square selected shots in the Shots View.

    If (while this mode is enabled) a new, explicit strip selection is made in the timeline that doesn't match the current shot selection, a message will be displayed at the bottom of the Shots View, together with a 'Resync' button. Pressing this will synchronise the timeline strip selection to the shot selection again.

    The timeline's selected strips can also be synchronised with the selected shots without enabling this mode from the "Select" menu's "Select Strips For Selected Shots" option (or the Ctrl+R shortcut) \[bug 40156]

### Formats

*   Edits to formats can be undone and redone along with all other scene edits. If a remote session is following, it will also see changes to formats as they are made.

    The Formats editor window left pane lists all formats and shows the levels at which they are defined. Icons to the right of the format name represent factory, global, job and scene formats. The icon is white if the format definition is different from the higher-level definition, or dimmed if it is the same. It is absent if the format is not defined at that level. There are buttons to hide a format from the format list, create a new format, and to reload the global/job format sets to pick up changes made elsewhere.

    The right side of the Formats window shows the details of the selected format. Use the bottoms at the top to see the format's definition at each level at which it is defined. At the bottom right, the Format Actions pop-up menu is used to perform various actions on the selected format.

    To edit a factory, global or job format, it must first be copied into the scene. If the "Scene Format" button is disabled, select a definition that is enabled, and choose Edit Format from the actions menu. The fields in the editor will become active and you can make changes. The changes occur live, and you can undo or redo as required.

    When the format is defined and working correctly in a scene, it might be desired to share it with other scenes in the job, or even other jobs. To do this, copy the format from the scene-level up to the job or global level using the Format Actions menu. Once copied to the higher level, it is then available for use by other scenes. It can be copied into other scenes via the Format Actions menu, or by simply using the format for the first time at which point it is automatically copied into the scene.

    A format may be deleted from a scene, but only if it is not currently being used in the scene.

### Deflicker

*   The Deflicker operator removes inter-frame flicker from an image sequence.

    When you insert a Deflicker operator, it will deflicker the sequence using the default settings. Most other Baselight operators have no effect when they are first inserted.

    The 'Scale' parameter scales the flicker correction. There should be a setting that gives minimum flicker. If you have a simple flicker with a period between 2 and 4 frames, 'Scale' should be between 1.0 and 2.0, and 'Frame Step' should be left at 1. If your flicker has a period longer than 4 frames, you should increase the 'Frame Step' parameter. If you have a complex or irregular flicker, add a second or third filter with different 'Frame Step' settings.

    Most ordinary images will not need the 'Advanced' settings.

    The 'Show' mode, under the 'Advanced' settings, shows the flicker signal to be subtracted. You should see a smooth flicker signal. If you see a lot of image features in this mode, you may need to increase the 'Blur' or the 'Pyramid depth' setting, under 'Advanced' controls. Use the 'Scale' control to increase the contrast if the flicker is hard to see.

    The deflicker tool can be used anywhere in the stack, but it is best used on the raw image data, before any colour or spatial operations. The only operations you might put above it are filters that remove noise or other details that may make the flicker easier to recognise.

### Text

*   The Text operator has been updated and now uses the high quality

    rendering used in the Subtitle operator. Fonts can be selected from

    files in a variety of standard formats. Outline and shadow options

    have been added to the existing lozenge and rectangle border

    options, and the blend level can now be adjusted. Burnins have also

    been updated to use the high quality text rendering.

### Colour Matrix

*   The Colour Matrix operator transforms the current image using a matrix and an offset. When transforming from rgb to RGB...

    R = Rr_r + Rg_g + Rb_b + Roffset G = Gr_r + Gg_g + Gb_b + Goffset B = Br_r + Bg_g + Bb\*b + Boffset

    The user interface has three groups of four sliders to control the four parameters for each of the three outputs. The desk controls come in groups of three, so to make things neat, the offsets have all been moved to their own group.

    There is a scale slider at the bottom. This will scale all these parameters, and so scale all the output image values.

    There is an Invert button. When Invert is Enabled, the plug-in will do the inverse transform. If the transform cannot be inverted (set scale to zero for example), you will get an error message.

    You can use this plug-in to perform grades in a crude luminance-chrominance space as follows...

    L: Rr=+0.6 Rg=+0.3 Rb=+0.1 Roffset=0.0 a: Gr=+0.5 Gg=-0.5 Gb=+0.0 Goffset=0.5 b: Br=+0.0 Bg=+0.5 Bb=-0.5 Boffset=0.5

    Copy and paste the ColourMatrix strip. On the second copy, select Invert Enable. This should restore you to the original image coordinates.

    If you do a grade between these two strips, the grade will be working in a luminance-chrominance space.

### Streak Filter

*   The Streak Filter operator is designed to remove the low-amplitude horizontal and vertical streak noise that you can get in underexposed digital camera images. The filter can be used anywhere in the stack, but is probably best used close to the top of the stack, before any colour or spatial operations.

    You will need to increase Threshold from the default zero setting to see any filter effect. The other settings can be left at their default values. These parameters were used in development, and have been retained in case they have some application for new images.

    The filter may make the image look softer, even if no useful image detail has gone. You may want to add a Sharpen strip after the denoiser to restore the appearance.

### Scene Storage

* Baselight's scene storage back-end has been improved to offer much improved performance, especially when loading and saving large scenes. This new back-end is incompatible with existing Baselight 4.4m1 (and earlier) jobs, so all 5.0 scenes need to created inside new jobs. Baselight 5.0 jobs will _not_ be visible inside Baselight 4.4m1 and earlier.
* It is now possible to open a scene which is already open on another Baselight system. If the other system has a write lock, then the local user will be asked if they wish to open in "follow mode" - if they agree, any changes made by the remote user will be instantly reflected in the local timeline. When in follow mode, the local user only has a read lock on the scene - they will be unable to modify the scene in any way. If the media is available on both Baselights, this allows remote grading, where a remote read-only viewer can follow the grading changes made by a colourist on another system.
* When a scene is opened and a format which it used has been edited or deleted, a Scene Format is created to maintain the previous behaviour of the scene. A dialog box is now presented when a scene is opened to explain this \[bug 34467]
* A new backup script, bl-backupdb, can be used to manually backup all jobs on a host. Linux-based Baselight systems will automatically backup the local database. The script can be run from cron to backup other systems if required. Run "bl-backupdb -i" for usage info.

### Reports View

*   Baselight now includes Daylight's report editor & generator.

    The report editor can be accessed from the "Reports" view under the Views menu.

    It currently supports PDF & CSV report generation.

    Multiple report templates can be defined for a scene. The report templates are copied into new scenes when you create a new scene based on a Template Scene. Therefore we advise that you create your report templates inside a Template Scene, so that they are automatically propagated to new scenes.

    Each report template can source its data from one of the tabs defined in the Shots View. Using a tab from Shots View allows you to specify which columns of data you wish to be included in the report, and how the events should be filtered and sorted.

    For example, you can define a tab which filters only shots that are marked as "Circle Takes", and sorts them by tape name and timecode. If you select this tab as the basis for the report, only the events that match the filter will be included in the report, and they will be sorted in the order specified by the tab.

    A PDF report currently consists of the following elements:

    *   Cover page

        This can include a cover image, and multiple "Fields" with associated labels & values.

        The labels & values are arranged into columns. You can split a column to start a new column by putting the value '\n' as the Label for a Field.

        The value for a field can include variables which are substituted to include information from the current scene. See the section below on Variables.
    *   Summary page

        The summary page can collate various values based on the media in your scene.

        The shots in the scene are grouped based on specific criteria, such as "Tape", "Mag ID", etc. Baselight can then calculate the count, total size, total duration, etc of all the shots in the same group.

        For example, if you choose to group based on Tape, you will get summary groups as follows:

        Tape Shots Duration Size A100RX23 10 01:02:03:04 132.25 GB A101RX23 12 00:59:58:02 125.04 GB
    *   Event pages

        The event pages contain columns of data for the shots to be included in the report. The list of events to include in the report, and their sort order, are determined by the Shots View tab that the report is based on.

        You can include thumbnails with each event, and specify the size of the thumbnails.
    *   Headers/footers

        You can specify an image & label to use for the header/footer, and how the header/footer should be aligned. The labels for the header & footer can also include variable expressions.

    A CSV report will use the columns for the Shots view tab specified by the "Based On" parameter. You can specify the value delimiter to use, and what unit to use for formatting file sizes (using one unit allows file sizes to be summed easily in external tools/scripts). Columns that use two timecodes (like Source TC) will be split into two values i.e. "Source TC Start" and "Source TC End".

    **Variables**

    The report system supports the following variables:

    Token Description

    %J Baselight job name for the current scene %S Baselight scene name for the current scene %{Page} Current page number (only in header/footer) %{Pages} Total number of pages (only in header/footer) %{Date} Current date, the format of which is controlled by the "Date Presentation Format" in the Scene Settings. %{IsoDate} Current date in ISO format: YYYY-MM-DD %{Time} Current time when report is exported. %{SummaryShots} Number of shots in the report %{SummarySize} Total size of shots, formatted as MB/GB/TB %{SummaryFrames} Total number of frames of all shots %{SummaryFeet} Equivalent to SummaryFrames formatted as feet of 35mm/4perf film %{SummaryDuration} Length of all shots, formatted as hh:mm:ss %{SummaryTapes} List of tape names referenced in the scene %{SummaryTapeCount} Number of tapes referenced in the scene %{SummaryMags} List of camera magazines referenced in the scene %{SummaryMagCount} Number of camera magazines referenced in the scene

    Also included are any variables defined in the Scene Settings "Metadata" tab, such as "Project", "Director", "DoP", "DIT", etc \[bug 40156]

### Still Export View

*   Added "Still Export" view and "Export Still" shortcut (Cmd-Shift-E).

    The Still Export view allows you to specify settings for exporting still frames from your current scene.

    You can specify:

    * Which frames to export, options:
      * Current Frame Only
      * Poster Frames
        * All Shots
        * Selected Shots
      * Marked Frames
        * All Shots
        * Selected Shots
      * Marked Frames of Category
        * All Shots
        * Selected Shots
    * Output directory
    *   Filename, which can include variable name expressions. See the

        Help text for the list of supported variable names.
    * File Type (JPEG, TIFF, DPX, OpenEXR, etc)
    * Colour Space
    * Resolution

    The Still Export settings are saved in the scene. You can save the settings in a template scene, and any new scenes created from the template scene will inherit the Still Export settings. The "Export Still" shortcut uses the current settings from the Still \[bug 40156]

### Layer View

*   The Layer View is now a dockable view and will update dynamically to represent the stack at the current cursor position. It can be used to select layers and mattes.

    As well as displaying layers in a stack, the Layer View can be used to re-order the current stack or copy layers from one stack to another. This can be done by dragging and dropping layer thumbnails.

    A dragged layer thumbnail can be dropped onto the same stack (between thumbnails) to reorder layers.

    Additionally, hovering over a Cuts view thumbnail with a dragged layer thumbnail will pop-up the destination stack's Layer view. The dragged layer can then be dropped on the destination Layer view to insert between or replace existing layers \[bug 40156]

### Truelight Colour Spaces

* Modified Layout in 'Scene Settings' -> 'Format and Colour' to simplify the overall operation of Truelight Colour Spaces. In the standard section there are only the three most common Settings (Working Colour Space, Grade Result Colour Space and Display Rendering Transform). All other settings have been moved to an 'Advanced' Section below the main settings \[bug 36008]
*   Added a new Colour Space 'Filmlight: T-Log / E-Gamut' (Truelight Log, Enhanced Gamut). This colour space is specifically designed to be used as a Working Colour Space (for camera-agnostic colour workflows).

    In addition 'Filmlight: Linear / E-Gamut' was added to provide a colour space for linear light VFX Renderings, using the same primaries as the working colour space. EXRs rendered to this colour space are automatically detected correctly on input \[bug 38165]
* Added new HDR colour spaces for different max brightness levels. Mathematically each set of spaces are the same, but have different clip levels and belong to different display viewing conditions
  * Dolby: ST 2084 PQ / P3 D65 / 108 nits
  * Dolby: ST 2084 PQ / P3 D65 / 1000 nits
  * Dolby: ST 2084 PQ / P3 D65 / 2000 nits
  * Dolby: ST 2084 PQ / P3 D65 / 4000 nits
  * Rec.2020: ST 2084 PQ / Rec.2020 / 108 nits
  * Rec.2020: ST 2084 PQ / Rec.2020 / 1000 nits
  * Rec.2020: ST 2084 PQ / Rec.2020 / 2000 nits
  * Rec.2020: ST 2084 PQ / Rec.2020 / 4000 nits \[bug 35538]
*   With the development of wide-gamut and High Dynamic Range displays, the visual difference between displays is getting larger. In order to adapt to those differences, all display-referred colour spaces in Baselight 5.0 store more colourimetric information about the given display. This then allows for a more advanced display colour pipeline, notably by other functions in Baselight like 'DRT Families' and 'Mastering Colour Space'.

    The following information has been added to display-referred colour spaces:

    * 'RGB\_XYZ' is a matrix which specifies X'Y'Z' values, which should be used instead of the 'mat' Matrix for display-referred colour spaces.
    * 'White\_XYZ' describes the maximum X'Y'Z' Tristimulus a display-referred colour space can represent. It describes what R=G=B=1.0 means in a given colour space.
    * 'Creative\_XYZ' (optional) describes the desired value the display should elicit for R=G=B=1.0 in linear light.
    * 'Clip\_XYZ' (optional) describes the maximum allowed code value the colour space should receive. This value is incorporated when the colour space is used as a Mastering Colour Space.

    A new command-line tool 'tl-utils TcsMatrix' can be used to generate all the needed colourimetric information.

    *   ViewingCondition' (optional) is a tag to group certain colour spaces together. The ViewingCondition tag is used to select the correct DRT from a DRT Family (see below). Currently Baselight understands these viewing conditions:

        "Cinema-48" "Cinema-108" "Video-100" "VideoWide-100" "Office-100" "OfficeWide-100" "VideoWide-600" "VideoWide-1000" "VideoWide-2000" "VideoWide-4000"

        Additional Viewing Condition tags can be specified in a text file located at /usr/fl/etc/colourspaces/extraviewingconditions.txt, with one tag per line \[bug 31392]

### Mark/Shot Categories keypad mode

*   Added new numeric keypad mode: "Mark/Shot Categories". Once selected (from the 'Edit -> Numeric Keypad Mode' menu) the numeric keypad can be used to add/remove marks as well as set/unset shot categories.

    By default, the '1' key adds a mark to the current shot (of category 'Generic Mark') and the '2' key sets the current shot category to 'Default Strip Category' ('Shift'+'1' and 'Shift'+'2' remove the mark and shot category respectively). However, the 9 keypad keys can be customised to add marks/set shot categories as required using the setup panel accessed via the menu option 'Edit -> Numeric Keypad Mode -> Configure Mark/Shot Keypad Keys'.

    The new mode also supports the following keypad keys:

    '-' : Remove all marks at current position. 'Shift' + '-' : Remove all categories associated with current shot \[bug 40156]

### Layer Numbering

*   The way layer numbers in dissolve/composite stacks are assigned has been improved. Previously, layer numbers within a stack were assigned sequentially from the top down. This meant, for example, if a stack consisted of a single dissolve of two primary graded shots, the top shot's grade would be assigned layer 1 and the bottom shot's grade would be layer 2.

    Now, each of the 2 shots' grading layers ('sub-stacks') that feed into the dissolve are numbered separately, so both of these shots' grade layers will be assigned layer 1. This allows you to easily identify & navigate sub-stacks within a single stack comprising multiple elements.

    Similarly, in a composite stack the foreground shot sub-stack will be numbered separately from the background.

    When operations act on layers in other stacks (e.g. grouped grading) and there are multiple uses of the same layer number within a stack, Baselight will try to match the current selection with an equivalent selection in other stacks.

    Repeatedly selecting the same layer number from the desk will cycle through all layers with the same number in the current stack.

    **Copy and Paste**

    The "Copy - Paste/Apply Options" (on the "Edit" menu) have been simplified. There are now only 3 paste/apply options:

    "Replace" - Layers in the destination stack will be completely replaced by the layers in the copy buffer. "Below" - All layers in the copy buffer will be pasted below the bottom-most layer of the destination stack. "Merge" - Merges the copy buffer and destination stacks, according to the layer numbers of the layers.

    ```
            Layers present only in the copy buffer stack will be
            copied into the destination stack.

            Layers present only in the destination stack will be
            left unchanged.

            Layers which exist in both copy buffer and destination
            stacks are resolved according to the "Protect Existing
            Layers" option. If set, then layers which exist in both
            stacks will be left alone. If not set, these layers will
            be overwritten with their equivalent layer from the copy
            buffer stack.
    ```

    When copying, only the sub-stack containing the currently selected strip in the timeline is copied to the copy buffer.

    Similarly, when pasting in "Replace" and "Merge" modes, the timeline strips affected will be those in the sub-stack containing the currently selected strip \[bug 43047]

### BLG Improvements

* Improvements have been made to the BLG file format to allow additional functionality:
  *   Input, Working and Viewing formats used by the Baselight stack

      are now stored inside the BLG. This means that in plugins like

      Baselight for Nuke, the complete image transform applied to an

      image in full Baselight can now be replicated.
  *   The Sequence operator's "Orientation" option is now supported

      within BLG files, including the additional "Centered on Mask"

      option.
  *   EXR Channel/Track references in full Baselight stacks are now

      stored inside BLGs. This means that plugins where the host

      supports EXR image channels (like Baselight for Nuke) can now

      load BLGs referencing matte channels or non-default image

      tracks.
  *   Stacks containing multiple input Sequences can now be represented

      within a BLG. This means the stacks containing composites

      (e.g. sky replacements etc) can now be represented within

      compliant plugins (e.g. Baselight for Nuke), simply by linking

      in additional inputs to the node.
  *   The "Stack Colour Space" and "Input Display Rendering Transform"

      options are now included in BLG files.
  *   Locked BLG files are now encrypted. In addition, it is now

      no longer possible to load locked BLGs into full Baselight or

      Daylight, thus preventing the internal structure of a locked

      BLG from being examined. Locked BLGs are intended to be

      distributed to VFX/Editorial partners for use in Baselight for

      Nuke and/or Baselight for Avid.
* When inserting BLGs in the timeline, Baselight is now more clever about when it inserts additional ColourSpace operators. It now only adds them when:
  *   There are existing grades in the stack. If there aren't, it

      directly modifies the Sequence operator's Stack Colour Space

      and Input Display Rendering Transform settings instead

      \[bug 43801]
  *   When the BLG were exported from a scene whose Grade Result

      Colour Space differed from that of the scene being inserted

      into \[bug 34932]
* Operator versioning in Baselight has changed to become per-operator in v5.0. By this we mean that older builds of v5.0 will still be able to load scenes/BLGs produced by later builds, as long as the operators used in the BLG/scene have not had their individual version numbers incremented. This makes it much more likely that a given BLG will be able to be loaded by older software. For this reason, the "Version Compatibility" option has been removed from the "BLG Export" and "EDL Export" settings \[bug 42401]
* Changed the "Quick Grab BLG" keyboard accelerator to be Ctrl+Alt+e (or Cmd+Alt+e on the Mac) to avoid clashing with the Alt+e (Insert Paint on second matte column) accelerator \[bug 44210]

### LUT Export

* Updated LUT export with Extended Ranges support for HDR input. Truelight cubes and the newly added Autodesk CTF format support an extra input LUT for mapping high dynamic range inputs. There is now an option to include this in the LUT export dialog \[bug 33499]
* LUT export also now includes an option to override the input colour space, replacing the one used for a sequence with one specified for the LUT export. This allows LUTs to be generated for use in other applications using images that have been converted to a different colour space \[bug 33157]
* LUT export has been extended to include options for the Input Display Rendering Transform when the Input Colour Space is set to anything other than the Sequence Input Colour Space. Previously the Input DRT was not handled in the LUT export \[bug 35118]

### Miscellaneous

* OFX plugins using OpenGL rendering are now supported \[bug 25574]
* The layout of the Insert menu can now be changed between the new structured version and the legacy unstructured version \[bug 42207]
*   Added a new "FilmLight" Scene Template. This sets up a scene in a scene-referred recommended fashion. The following Scene Settings are defined:

    * Timeline Caching: Full
    * Display And Timeline Cache: 10-bit Integer RGB
    * Working Colour Space: FilmLight: T-Log / E-Gamut
    * Grade Result Colour Space: From Stack
    * Display Rendering Transform: Truelight CAM
    * Colour Treatment: Native (as we have a HDR Working Format)

    You should set your Image Container to the Project/Job level in the file structure in order to get the deliverables to work properly. Render Deliverables are included that should cover most of the deliverables needed in a production:

    * Dailies Avid graded
    * VFX Plates ungraded
    * VFX Plates graded
    * QT for Approval
    * P3 Deliveries
    * DCI XYZ Deliverable
    * DSM Archive
    * Rec709 Deliverable \[bug 39561]
* Added new colour spaces:
  *   Dolby: ST 2084 PQ / X'Y'Z' / 108 nits

      This space is needed to export a Dolby Vision Cinema DCDM
  *   Rec.2100: HLG 1.2 Gamma Legal Range/ Rec.2020 / 1000 nits

      This space is needed to import legal range HLG content. It is not intended to be used as Cursor or Render Colour Space.
  *   Red: Log3G10 / REDWideGamut and RED: Linear / REDWideGamut

      These colour spaces are RED's new default wide gamut colour spaces. They build the foundation of the upcoming RED IPP2 DRTs.
  *   Rec.2100: HLG 1.2 Gamma / Rec.2020 / 1000 nits and Rec.2100: HLG 1.2 Gamma / Rec.2020 / Preview SDR Conversion (on 1000nits)

      Technically they are identical to the ad hoc colour spaces published on FilmLight's webpage 'Rec.2390 Hybrid Log-Gamma package'. Just the naming was changed to reflect the recent ITU Specification ITU.BT.2100 \[bug 38751]
* Added tl-utils LcmsList function. This converts ICC profiles to Truelight list transforms using the Little CMS library. This library supports the full ICC v4.3 standard, so it should be able to convert profiles that use the new v4.3 features. LcmsList complements but does not replace the existing ICCtransform or TcsDisplay: these will probably make a better conversion on a display profile, and display profiles rarely use the new ICC v4 features \[43671]
* Added new fltransform constant "BlackOffset". This value is useful to specify which linear light (LMS) scene referred value is mapped onto 0.0 on the display signal. Some DRTs map negative values onto 0.0. That results in linear light scene referred 0.0 to be mapped into a positive value greater than 0.0. Modern grading tools like Base Grade operate in the linear domain and linear light scene referred 0.0 is the anchor point of those tools. Base Grade in combination with a DRT that maps linear light scene referred 0.0 onto a positive value on display would cause a strange behaviour using Base Grade, as a user could not reach true 0.0 on the display signal. The "BlackOffset" value in the DRT is used to offset Base Grade's working point. Base Grade does this dynamically based on the DRT in use in the stack \[bug 40650]
* Renamed "ACES: 2.6 Gamma / P3 D60" colour space to "DCI: 2.6 Gamma / P3 D60", to reduce confusion in Non-ACES Workflows \[bug 41192]
* Added option to sort jobs by size (note that this feature is not available when browsing jobs on FLOS 2.1 systems) \[bug 5208]
* Added support for 12-bit encoding in the DNxHR HQX codec \[bug 34868]
* Added support for reading multi-part OpenEXR files (except where the display window is not the same for all parts) \[bug 34972]
* Added support for reading multi-view OpenEXR files. This includes automatically selecting left/right views in stereo scenes for both the image and any referenced matte channels \[bug 35059]
* Updated to RED SDK v6.1.0. This includes three new HDR Output Tone Curve options: HDR-2084, Rec.1886 and Log 3G12 \[bug 35054]
* The Manage Colour Spaces dialog now allows more fine-grained choices of which colour spaces to hide in which menus - e.g. a colour space may be hidden from the Working Colour Space menu but still visible in the Render Colour Space menu \[bug 35147]
* Added support for NVIDIA driver 352.63 on systems with GTX 580, GTX 680, GTX 780, GTX 980 and GTX TITAN X GPUs. This driver is compatible with systems using an AJA Kona 4 or direct GPU display. This driver is NOT compatible with systems using FilmLight DVI2SDI or Framestore SDI display hardware \[bug 33008]
* Added support for NVIDIA driver 340.96 on systems with GTX 680 and GTX 780 GPUs and DVI2SDI or Framestore SDI display hardware \[bug 35367]
*   Added ability to specify how shapes are combined within a single shape strip.

    Each shape in a shape strip is drawn in order based on its position within a 'draw list'. The currently selected shape's position in that list is indicated in the 'Shape Management' section (e.g. 'Shape 3 Of 5 Selected'). The shape's position in the list can be adjusted by the up/down arrow buttons next to the position indicator.

    How the shape is combined with any shapes already drawn is controlled from the 'Operation' dropdown. 3 different operations are available:

    Union The shape is unioned/merged with any shapes already drawn. Subtract The shape cuts a hole in any shapes already drawn. This is useful, for example, when a graded object passes behind another ungraded object. Stamp The shape is stamped on top of any shapes already drawn. In this mode the 'Opacity' (slider) value is replaced by 'Intensity'. This mode is useful, for example, when you have foreground objects (partially) obscuring background objects and you want a grade to affect the foreground less then the background.

    Additionally, when soft edge shapes overlap in 'Union' mode (the equivalent of the old shape rendering behaviour), where the shapes intersect there will be a less visible band \[bug 32582]
* All the default setups have been updated to reflect modern grading workflows:
  *   Default Working Colour Space is changed to "FilmLight: T-Log /

      E-Gamut"
  * Default Display Rendering Transform is changed to "Truelight CAM"
  * SDI Output "Clip to Legal" is changed to "Full to Legal"
  *   Default HD Viewing Colour Space is changed to "Rec.1886: 2.4 Gamma

      / Rec.709"
  *   Default UHD Viewing Colour Space is changed to "Rec.2020: 2.4

      Gamma / Rec.2020"
  *   Default DCI Viewing Colour Space is changed to "DCI: 2.6 Gamma /

      P3 DCI" \[bug 34406]
* Added the concept of a "cursor group" to the cursor drop-down in the Cursor View. Each cursor can now be a member of one of three groups: Cyan (the default), Yellow or Magenta. This is helpful because:
  *   When using the Wipe, 2x1, 1x3 etc display modes, only cursors

      from the current cursor's group are displayed. Thus, for

      example, if you have cursors 1, 2 & 3, it is possible to

      display 1 & 3 side-by-side simply by using a 2x1 display

      mode and having cursors 1 & 2 being in a different group to

      cursor 2.
  *   Each cursor group has a separate gang state, so you can have

      some cursors ganged together whilst leaving others alone

      \[bug 27050]
* Added ability to cycle through different numeric keypad modes by holding down the Windows key (Ctrl on the Mac) and pressing 0 on the numeric keypad \[bug 40156]
* Added recall stack -2 to +2 actions to Chalk \[bug 33306]
* fl-diag zones test no longer warns about volumes which are not defined on all systems \[bug 39273]
* fl-diag zones test no longer warns about minor internal differences in other systems \[bug 39272]
* On Flos 6.4 systems, the PostgreSQL work\_mem setting will be changed from the default (1MB) to 32MB \[bug 43135]
* All numeric edit control controls now support gestural grading. To use it, simply click in the edit control and drag clockwise or anti-clockwise in a circular manner. This change means that to sweep-select text in an numeric control, you'll need to first click in the edit control to obtain the input focus, after which you can sweep select \[bug 38973]
* Updated to ARRIRAW SDK v4.5. This adds additional colour space options including Rec.2100, for compatibility with ARRI's camera Software Update Package 5.0 \[bug 43457]
* Added support for Retina displays on Mac OS X.
*   Added "SDI Full Range Levels" option to SDI setups editor. This option specifies how full range data is mapped to the SDI outputs of the AJA Kona 4.

    It has two options:

    * "0-1023 (Full)" : Full range data is passed unmodified to the SDI output. Code values below 4 and above 1019 in a 10-bit range (below 16 and above 4076 in a 12-bit range) are clipped. This is the default behaviour and corresponds to the existing behaviour in Baselight.
    * "4-1019 (SMPTE Full)" : Full range data is scaled to the range 4-1019 for 10-bit signals, or 16-4076 for 12-bit signals. No data is clipped, but display devices must be configured to handle full range data to be mapped to SDI SMPTE Full Range \[bug 44060]
* Added support for reading stereoscopic DCPs and stereoscopic JPEG 2000 encoded MXF-files \[bug 30322]
*   When pasting shots between scenes that use different containers, there is now the option to keep the original container paths when pasting into the destination scene.

    If you choose to preserve the paths within the original container, the pasted shots will use absolute paths to the original image/movie/audio files so that the media is still accessible in the destination scene. This is useful if you then wish to Consolidate material using the destination scene container.

    You can set the default behaviour for remapping containers when you paste shots using the "When Pasting Between Scenes" setting in the Image Container section of Scene Settings.

    This setting has three options:

    * "Ask Before Updating File Paths": A dialog will be shown after pasting shots between scenes if the source scene and destination scene use different containers, asking whether you wish to keep the paths within the original scene's container, or use paths relative to the destination scene's container. This is the default behaviour.
    * "Keep Source Container Paths": Always keep the original paths within the source container. The sequences pasted into the destination scene will use absolute paths so that the original material can be found.
    * "Use Destination Container Paths": Use paths relative to the destination scene's container \[bug 20250]
* Since Baselight for FCP7 is no longer supported, the "Update FCP XML with Baselight Grades" option has now been removed from the EDL Export panel \[bug 43787]
* Added Border Colour option for burnins, which allows you to change the colour of the border behind text elements in a burnin \[bug 44618]

## Bug Fixes Since Baselight 4.4m1.9553

* Denoise cannot work if you pick a completely flat region. The error message has been changed to something more helpful if this happens \[bug 43883]
* Fix for problem with blur + grain + flip transform. This was a very strange special case where the flip disappeared when the blur went above a certain threshold, but only when the grain was applied \[bug 43449]
* New softer pyramid option used in Texture Blend, Texture Equaliser, and Streak Filter, with versioning so old scenes are unchanged. This gives a smoother result if you have large filter changes between one level and the next \[bug 41584]
* Changed HLG black point to 0.0. This prevents crushed blacks. Changed the clipping within the from\_lin function. This fixes some artefacts with strong saturated blues. Changed the to\_lin function of the HLG Preview space. This fixes a bug with this space in combination with an active Mastering Colour Space \[bug 41781]
* Colour Temperature now bypasses all processing when there is no temperature shift and all other controls are at the default settings. Prior to this we got some small colour shifts due to precision errors in the colour space transforms \[bug 41943]
* Fixed incorrect colour space conversions which were applied when two inputs to a Matte Merge operator had different colour spaces. Please note this may change the appearance of Baselight 4.4m1 scenes using Matte Merge operators when upgraded to Baselight 5.0 \[bug 38916]
* Fixed black point and white point setting in ACEScct.flspace. This does not change the transformation itself, but only where lines are displayed in the histogram \[bug 41494]
* Fixed flickering at right and bottom edges occasionally seen when blurring with large radii \[bug 2359]
* Increased the amount of memory dedicated to thumbnails on Baselight systems with a UI host to 25% of available RAM. This allows more thumbnails to be kept in memory, reducing thumbnail re-rendering when scrolling \[bug 34183]
* Fixed LUT export which was failing for Shots with Hue Angle and Matte Tool Blur \[bug 34225]
* Fix new files being reported as zero size over /pfs (flood) interface when they were written using flux \[bug 28121]
* Improved accuracy of warning counter on EDL Import View \[bug 34284]
* Sequences on cloud media are no longer reported as missing when using Verify on a render \[bug 32311]
* Fixed crash starting image output on FLOS 2.1 Baselight ONE systems \[bug 34168]
* Fixed bug where the "sRGB Display (Ignore Truelight & Viewing Colour Space)" (now renamed to "Use sRGB for Thumbnails") would have no effect in some galleries \[bug 33145]
* Fixed bug where normal scenes loaded into galleries sometimes wouldn't scrub using the current viewing colour space \[bug 29231]
* Fixed bug where the current cursor's mask and guide mask settings sometimes weren't being applied when scrubbing in a gallery. Now, as long as the user elects to turn on the "Viewing Format and Masks" options in the Gallery's right-click context menu, any current mask or guide mask should always be applied when scrubbing \[bug 34117]
* Fixed bug which could occur when a mask, burnin and a Truelight profile were switched on in the current cursor and the user scrubbed in a gallery thumbnail which was grabbed with a different viewing format which didn't contain a mask of the same name \[bug 23458]
* Fixed crash when grabbing a movie to the gallery if the user the Baselight UI was running as didn't have permission to read the movie \[bug 26004]
* Fixed alpha channels in thumbnails of ProRes 4444 media \[bug 34334]
* Fixed keyboard accelerator for changing Edit Type on Mac \[bug 34336]
* Fixed error with zero handling in "Dolby: ST 2084 PQ / P3 D65" colour space \[bug 34382]
* Fixed bug which cause shape overlays to not match the rendered shape image when adding/modifying keyframes \[bug 34376]
* Fixed intermittent crash related to periodic events in the user interface \[bug 34305]
* You can now use the same expressions available in the Shots view in burn-ins and the render panel. For example, you can now use %\[FileMetadata.ISO} in a burn-in, or %{MyCustomColumn} in a path in the render panel \[bug 36888]
* Added option to specify the font to use for burn-ins. The software can use any Truetype font (extension .ttf) \[bug 41562]
*   Improved font search paths. The software will search a set for Truetype fonts in a set of per-user and system directories.

    On macOS the font search directories are:

    * /Library/Application Support/FilmLight/fonts
    * $HOME/Library/Fonts
    * /Library/Fonts

    On Linux the font search directories are:

    * /usr/fl/fonts
    * $HOME/.fonts
    * /usr/share/fonts/truetype \[bug 41562]
* To reduce confusion which was caused by the introduction of correct QuickTime colour space tagging in Baselight 4.4m1.9029, the Render View now offers the choice to use "Legacy" tagging. This tags output QuickTime movies as Rec.709, PAL or NTSC based purely on the resolution of the image. The new behaviour which tags the movie using information from the render colour space is available by selecting "Automatic" tagging \[bug 31853]
* Fixed remote rendering on a multi-GPU FLUX Store \[bug 40086]
* Added mechanism for white-listing non-standard GPUs \[bug 42852]
* Fixed cp\_sync slowdown accessing NFS volume on OSX \[bug 41248]
* MJPEG encoded material in MXF files is no longer stretched from legal to full on read \[bug 34402]
* Fixed screen switching by double tapping the UI/Image button on systems with both multiple monitors and a Blackboard 1 \[bug 32511]
* Updated the ACES Scene Template to use ACES Cineon Log / AP0 as a working colour space, due to issues with ACEScc \[bug 34051]
* Fixed bug setting up floating-point cubes that take negative values. This gave visible pixels in regions that should be fully dark. Such cubes are not used outside development work, so we do not expect current Baselight jobs to be affected \[bug 34465]
* Fixed Group Grading of several operator parameters \[bug 34407]
* Fixed issues with Cloud Media connected to the node of a Baselight TWO system \[bug 34297]
* A missing source file will no longer cause a Consolidate operation to abort \[bug 34240]
* Adaptec web interface no longer requires an SSL connection because many browsers refuse its self-signed certificate \[bug 31422]
* BLG export using unavailable filename templates (e.g. %P when the shot has no clip name) now correctly report the error \[bug 30551]
* Fixed an issue that prevented interop DCPs being rendered via command line \[bug 31693]
* Rendering a DCP now finishes with 'Wrote DCP package', to better indicate the completed status of the render job \[bug 31967]
* Fixed an issue that could cause frames to be repeated in MP4 movies with frame rates of 100 fps or higher \[bug 34594]
* Fixed occasional out-of-memory errors when rendering \[bug 34226]
* Fixed excessive file searching when opening some R3D movie files \[bug 34690]
* Adjusted calculation of max frame size in JPEG 2000 compressed MXF files to avoid introducing minor bitrate overshoots when creating DCPs in e.g. Clipster \[bug 31622]
* Fixed LUT export for a LUT transforming from a Log Colour Space to a Linear Colour Space, which previously clamped output values to 1.0 \[bug 34423]
* Fixed LUT export for shots with pixel aspect ratio other than 1.0 \[bug 34611]
* Fixed broken handling of some parameters when rendering H264 to MP4 or Quicktime containers. These parameters would previously generate warnings about undefined parameters on the console, and their settings would be ignored if set to something other than the default value. The affected settings are "Weighted prediction for P-frames", "early SKIP detection on P-frames" and "Transform coefficient thresholding on P-frames" \[bug 34825]
* Added aspect ratio information to Dolby EDR Metadata \[bug 32794]
* Deleting a format which overrides another format no longer removes some mappings to the remaining format \[bug 34920]
* Fixed crash when activating a licence from a downloaded file \[bug 33708]
* Improve licensing dialog and activation process \[bug 33418]
* Improvements to Licence window layout \[bug 34464]
* Updated to latest version of fl-setup-vol, which removes support for Avid Unity filesystems (superseded by Avid ISIS) \[bug 34599]
* Fixed an issue that could cause decode failures, frame offsets and incorrect frame ordering in MXF files with start-position offsets. This particularly affected XDCAM encoded files \[bug 33591]
* Improved error message when trying to open an encrypted DCP or MXF \[bug 34979]
* Fixed reading audio from split-file MXF media \[bug 34903]
* Improved cursor lag on image display when using AJA SDI output hardware \[bug 34357]
* Fixed reading audio from some MXF files \[bug 30294]
* Fixed 100% quality JPEG output \[bug 35034]
* Fixed deselect on paste still clearing the selection when it was turned off \[bug 25917]
* Improved Baselight decode of ARRIRAW media so the levels more closely match the ARRI decode. Note that this only affects newly-added Sequences to prevent changes to existing scenes; to update existing scenes use the Update button on the Sequence parameters \[bug 35043]
* Fixed crash when pasting a tracker strip having a two point track with no tracker linked to it \[bug 35046]
* Updated the default Setup behaviour so that new scenes are created using the ARRI Photometric v2 DRT. This replaces the legacy ACES RRT 0.7 which was previously used \[bug 35086]
* Avoid running overnight disk defragmentation process twice on Baselight TWO systems \[bug 34925]
* Errors are no longer generated if there are AppleDouble files in the colourspace directories (e.g. .\_foo.flspace) \[bug 35053]
* Reduced risk of GPU memory errors when working with large RED media (e.g. 8K WEAPON) \[bug 35041]
* Fixed bug which caused incorrect cache size warnings on multi node systems \[bug 23199]
* Updated preview features licence support \[bug 34539]
* Diagnostics no longer reject hostnames that are the same as the system zone name. This helps integration with certain 3rd-party SANs \[bug 31174]
* Diagnostics now report detection of Intel EIST technology \[bug 25667]
* Fixed problem with copy protect categories on the input strip preventing the strip directly underneath from being pasted to the destination \[bug 35174]
* Fixed CDL grades not appearing in the bl-shots -ascsop and -ascsat options \[bug 35204]
* Colour Space Journey View no longer displays entries for bypassed strips \[bug 34977]
* Fixed a memory allocation issue which could cause subtitles not to appear in DCP output \[bug 35012]
* Fixed temperature query tool 'sdi-info -temp' bug \[34978]
* Fixed Input Colour Space shown on Sequence Parameters when a BLG is inserted onto the timeline \[bug 35220]
* The Reference strip no longer converts its input to the Working Colour Space and Working Format. Note that since this can affect grading behaviour, this change only applies to newly-added Reference strips; old scenes retain their old behaviour \[bug 35206]
* Truelight resources used by operators inside layers with mattes are now correctly included in exported BLG files \[bug 35240]
* Fixed an issue where the Blackboard 'Undo' functionality was no longer available after a Tracker modification using any blackboard trackball or ring \[bug 35192]
* Fixed a problem with retime node in Optical Flow mode, where cluster machines would render differently than single node machines \[bug 35091]
* The Job Manager "Move Scene Into Folder" command now prevents moving a scene into a folder which already has a scene of the same name \[bug 35278]
* Fixed issues with Dolby Vision Mastering Display \[bug 35268]
* Fixed a problem with Optical Flow retime, where Baselight FOUR and EIGHT systems would render incorrectly \[bug 35091]
* Fixed decode of ARRIRAW Open Gate (3414x2198 or 3424x2202) media using ARRI decode mode \[bug 34605]
* Fixed a crash that could occur while setting the time on KDMs in the render panel \[bug 43034]
* Internal /media/\_mnt\_slot\* volumes are now hidden from cloud media \[bug 35300]
* Fixed crashes reading some 16-bit RGBA TIFF files \[bug 35357]
* Bypassed Dolby Vision strips are no longer exported with EDR XML \[bug 35356]
* Fixed order of gestural grading gang controls \[bug 35352]
* Fixed export format of .cc files \[bug 34345]
* Prevented Consolidate overlapping-sequences warning dialog from getting too large \[bug 35227]
* Fix playback and render errors when Audio Sequence operator has a negative offset \[bug 35375]
* Fixed bug with fl-service xorg service running on IO node of cluster systems \[bug 35409]
* Don't attempt to stop Adaptec raid verification at Baselight startup because it may cause a kernel panic \[bug 35345]
* Fixed an issue with the bitrate selection dialog when rendering DCI compliant JPEG 2000 files, where the dialog did not update to reflect the selected bitrate \[bug 34844]
* The sequence operator now correctly displays a selection dialog for handling frame duration when reading a movie file with uneven frame duration \[bug 32262]
* Bundle a newer version of xfs\_repair (4.3.0) \[bug 35186]
* Fixed render hang on BL4/BL8 \[bug 35453]
* Fixed bug in the Gallery which could occur when grabbing RAW media (e.g. R3D, ARRIRAW etc) when multiple debayer parameter operators were in the stack. When the original media disappeared, the grabbed frame could have been generated using the incorrect debayer parameters \[bug 35511]
* Updated pivot point in CDL grade to match FG. Also fixed the maximum slope value \[bug 35464]
* Improved serial number and licence file validation support \[bug 35363]
* Fix application hang caused by Audio Waveform view \[bug 35512]
* Fix behaviour of "Reset All To Camera Metadata" on R3D Params operator \[bug 35516]
* Select Missing Material now reports that it cannot check material which is on remote cloud media \[bug 35523]
* Fixed decode of ARRIRAW Alexa Plus anamorphic (2578x2160 or 2592x2160) media using ARRI decode mode \[bug 33915]
* Negative button in Video Grade now works as expected \[bug 17462]
* A failover routine has been added when encountering missing reference frames in XDCAM MXF-files. This will allow reading valid XDCAM essence from MXF-files with invalid indexes \[bug 35633]
* Added support for a number of QuickTime codec tags, including 'aivx' for XAVC \[bug 35615]
* Fixed failure to read some QuickTime files with badly-formatted metadata \[bug 35761]
* Update licensing to allow appropriate licenses to be installed \[bug 35896]
* Fixed an issue that caused blocky artefacts and green frames when decoding XDCAM \[bug 36016]
* Fixed conform / re-conform issue that caused failure with overlapping sequence strips \[bug 36344]
* The 'Tracker Zoom' functionality now correctly takes into account the viewing format, when it differs from the working format \[bug 33995]
* Fixed stereo geometry fix not working on scenes that contain a DRT in their colour space scene settings \[bug 40870]
* Fixed possible crash in Multi-Paste View when doing "Restore Config to Defaults" \[bug 41316]
* MPEG-4/SStP codecs are not currently available for rendering on Mac, pending a library update from Sony \[bug 36974]
* Stopped spurious "Multi-Paste Settings have changed" warning when closing Baselight \[bug 27308]
* Fixed crash which could occur after a Timeline Sort was done when Cuts View selections were removed by the sort \[bug 41482]
* Updated ACEScg tooltip text \[bug 41047]
* Fixed bug which would prevent shape control points from animating correctly when manually keyframed \[bug 41760]
* Fixed bug which prevented keyframes from automatically being added to a shape's feathering & opacity when dragging control points \[bug 41778]
* Fixed an issue causing the tracker strip 'show input' button to be modified when coming from a shape or transform strip \[bug 41919]
* Fixed crash in layer view drag and drop on replace \[bug 42082]
* Stop burnin opacity from being reset on scene open \[bug 42682]
* Fixed a memory leak in the QuickTime and MXF movie reading proxies \[bug 42683]
* Ensured that movie, image and header counts are shown on conform results \[bug 40110]
* Fix an issue that prevented conforming with TapeName or ClipName in Path or Filename from working \[bug 41206]
* Fixed display of media counts when doing a conform \[bug 41203]
* Fixed floating layer views initially appearing empty \[bug 41442]
* Fixed flicking green line when inserting layer in the layer view drag and drop \[bug 42693]
* JPEG 2000 Params strips are now automatically inserted for JPEG 2000 encoded files and MXFs \[bug 42829]
* Fixed spurious changing of ganged cursor positions if "Always Restore Cursor Position on Undo/Redo" was switched on \[bug 41938]
* Fixed an issue where DCPs with missing entries in the ASSETMAP could cause dcpproxy to crash \[bug 42998]
* Fixed bl-conform which was failing to detect existing jobs and to create new jobs \[bug 43055]
* Added support for reading audio from Op1B MXF-files. Previously, these files tended to cause movie reader crashes when attempting to read audio \[bug 43113]
* Fixed an issue with missing metadata that prevented the consolidate function from working correctly with DCP packages \[bug 39846]
* The "Grouped Grade Stacks Above/Below" (edit) menu option has now been replaced with "Grouped Grade Both Eyes". This option is only available in stereo scenes \[bug 42917]
* Updated the QuickTime library to prevent crashes produced by malformed files \[bug 43585]
* Fixed copying of compressed TIFF files resulting in much larger uncompressed files in the destination \[bug 43305]
* Linking a tracker to a transform strip for a stabilisation no longer resets the transform parameters \[bug 43638]
* Fixed an issue that could prevent some Op1A MXF files with CBE essence from being decoded correctly. This affected at least one type of AVC-Intra MXF \[bug 43440]
* Fixed keyframing errors which could occur when BLGs were exported from stacks with misaligned start frames \[bug 44104]
* Fixed Gamma and Gain being swapped in dissolve shots in Dolby EDR export \[bug 42200]
* Fixed Mac numeric keypad behaviour \[bug 43808]
* Fixed a problem where rendering XAVC or XDCAM to Sony MXF did not set the duration correctly in the file header \[bug 43464]
* Updated the QuickTime library to prevent crashes produced by malformed files \[bug 43585]
* Improved the handling of XAVC LongGOP, making random access much more efficient. This type of media can now be used for grading \[bug 32458]
* Fixed Mac installer to ensure Truelight displays and profiles folders are writable by all users \[bug 44163]
* Fixed bug with burnin rendering that would cause incorrect black levels in borders outside the image area when images are rendered with a Video LUT applied \[bug 43855]
* Fixed a crash that could occur when reading QuickTime files with invalid comment atoms \[bug 43905]
* bl-reset-cache no longer resets the thumbnail cache by default \[bug 43753]
* Fixed an issue where the frame count of some QuickTime movies could become very high \[bug 44200]
* Premiere XMLs with reversed clips, and old XMLs, now start on the correct frame \[bug 32377]
* Unreadable effects in XMLs are now simply ignored, rather than giving the warning "Speed change ignored" \[bug 40945]
* XMLs with unknown effects now give a warning that the effects are not supported in Baselight \[bug 34891]
* Fixed crash when unlinking trackers \[bug 44142]
* Linking a tracker to an already keyframed control no longer deletes any existing motion keyframes \[bug 43221]
* Changed pop up window when unlinking a tracker, which now has simplified options and text message \[bug 43458]
* Fixed bug where it became impossible to close a scene after hitting "Cancel" in the discard confirmation dialog \[bug 44375]
* Improved error message when verifying a render that includes a gap in the timeline \[bug 44258]
* Fixed possible increased sluggishness when using keyboard bumps with "Maintain Density" being off \[bug 43632]
* The Subtitles operator is now detected and rejected during BLG Export \[bug 44195]
* In FCP XMLs sources with empty reel names no longer generate a warning \[bug 44475]
* Fixed tracker issue, where the point tracker preview box was showing an incorrect image when the "show input" button was on \[bug 43734]
* Fixed corrupted warning message on SDI output when GPU is in use by another application \[bug 43351]
* Added support for variable retimes from FCP7 XML files \[bug 44427]
