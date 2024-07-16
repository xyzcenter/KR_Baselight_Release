# Baselight Release 6.0.19342 (2023-12-12)

### New Features Since Version 5

#### X Grade Operator

*   X Grade is a new primary colour grading tool which operates in floating-point linear light. As with all our newly developed tools, it is colour space aware and will convert from the stack colour space to its internal linear light colour space as well as processing the colour changes in a newly developed opponent colour space designed for natural colour grading.

    You can interact with X Grade using both the mouse and panels. The primary user interface is a scope-like canvas which shows the current image as a point cloud on the canvas, but it is also quick and easy to modify colours directly from the image display.

    The scope can be panned and zoomed just as with an image.
*   **Strokes**

    Strokes are the fundamental element used to manipulate colours in X Grade. Creating them is very easy:

    * **On the Scope**: use the mouse to select a colour to adjust; click and drag in the direction that you want to push the chosen colour. This action will create a stroke - an arrow with a start and end point.

    The colour at the base of the stroke will be pulled in the direction of the arrow - the pull strength fades with distance from the array. The scope will show the boundaries of the change caused by the currently selected stroke.

    Multiple strokes can be created on the layer by clicking and dragging, or to edit an existing stroke, click on either the base or the head of the stroke's arrow. To delete an existing stroke, hold down `Shift` while clicking on it.

    * **On the Image**: you can also create strokes directly from the image, and this is usually the most efficient way of working. When on the image, the scope will show a circular cursor representing the position corresponding to the colour under the mouse pointer. Clicking with the mouse acts as if you were clicking at the point shown by the circular cursor, and the subsequent drag will drag the colour as if you were dragging on the scope. In practical terms, you rarely need to look at the scope - just click on the colour you want to adjust, and drag the mouse until it's how you want it. Note: while working directly on the image, it's useful to know whether clicking will adjust an existing stroke or create a new one. The image cursor shows a small + in the top-right corner when clicking would create a new stroke. Note that to avoid creating a large number of strokes that would be hard to manage, the tool errs on the side of editing an existing stroke if there's one reasonably close-by, but you can force the creation of a new stroke with the `Alt` modifier (`Option` on Mac).

    For fine tuning, as well as the start and end points, each stroke has two additional parameters you can adjust:

    * **Exposure**: this allows a stroke to modify brightness as well as hue and saturation. It is visualised as a contour plot around the stroke, similar to contour plots in topographical maps. As well as modifying the slider, it can be directly edited while dragging a colour by using the `Win` modifier (`Ctrl` on Mac).
    * **Width**: this extends the influence of the stroke. It can be directly edited with the mouse with the modifier `Alt+Win` (`Option+Ctrl` on Mac).
*   **Pins**

    Pins allow you to pin certain colours so they will not be affected by strokes. You can think of them as constraining the influence of strokes so that they cannot propagate past the pin. They are indicated as crosses (X) on the UI, and you can also see their influence on the outline for the selected stroke.

    By default, each layer is created with a pin on the neutral axis as this is usually a colour you will want to avoid changing. (You can turn this off in the Customise menu).

    You can create pins by pressing `Ctrl` (`Cmd` on Mac) while clicking with the mouse, move existing pins by clicking and dragging them, or delete them by pressing `Shift` and clicking.
*   **Layers**

    X Grade supports multiple layers (where each layer has its own set of strokes and pins). Layers are managed in the Layer Section in the top right corner of the X Grade user interface.

    Each layer can be assigned a Zone, using the same Ansel Adams Zone System as used by Base Grade. A layer can have one of three zone types:

    | Type   | Description                                                  |
    | ------ | ------------------------------------------------------------ |
    | Master | The layer will affect the whole exposure range               |
    | Dim    | The layer will affect the exposure range below a pivot point |
    | Light  | The layer will affect the exposure range above a pivot point |

    In addition, layers can be completely bypassed, have their opacity adjusted (to reduce the effect of a layer), and renamed (by double clicking on the layer name).

    If the selected layer is set to either Dim or Light zone mode, additional sliders for the pivot and falloff will appear in the layer section.

    When not using the Master zone, the effect of a stroke will be attenuated for pixels whose exposure falls outside the selected zone. When working directly on the image, this can cause confusion (e.g. when using the Dim zone, picking a very bright colour and dragging it will have very little effect on that colour). To help with this, the cursor colour will change from white through orange and finally red as the pixels under the cursor fall further out of the exposure range for the layer.
*   **Scope**

    The scope uses an opponent colour space where the x-axis corresponds to the green-red axis and the y-axis to the yellow-blue axis. The coloured background reflects the spectral locus. A small cross marks the white point. A line from light blue to orange represents the thermal or Planckian Black Body Locus. The gamut hulls of the mastering and viewing colour space are also shown as a reference. These overlays can be turned on and off in the X Grade customise menu.
*   **Desk Mapping**

    X Grade is designed as a primary grading tool, which means all functions can be accessed via a Blackboard or Slate control surface.

    One trackball is used for positioning the mouse pointer - by default this is the left hand trackball but can be swapped to the right from the Customise menu. We will refer to the ball controlling the mouse pointer as the **Mouse** trackball and the opposite ball as the **Far** trackball. The Middle and Far balls are used to move the start and end points of the current stroke. If there is no current stroke a stroke will be created - this happens immediately when the pointer is on the Image screen, but a click is required when interacting with the UI scope to protect against accidentally creating strokes while working.

    The Zone parameters for the Layer and the Exposure and Width settings for the selected stroke can also be directly modified from the panel encoders, and the Exposure and Layer Opacity parameters are also mapped to the Middle and Far rings of the panel.
*   **Technical Notes**

    It is essential to understand that the effect of the strokes is additive, and they are applied in the order created. The additive nature of the strokes is more suited to intuitive grading (you can generally just drag what you want to change without worrying about previous strokes) and generates a more robust result because folds can be avoided even if strokes cross each other. But it does have the drawback that the strokes do not represent the net result of the change for a given point but the history of strokes you added. Bug 49114

#### Chromogen

*   Chromogen is a ground-breaking framework for look development based on human perception. Look development is usually performed before principal photography. Together with the Director of Photography, the colourist can use Chromogen to create a unique look for a specific project. Chromogen is designed to work in a scene-referred colour management workflow. It is both Working Colour Space and DRT agnostic. However, if the DRT already incorporates a prominent look component, it will be harder to produce novel looks or to escape the look of the DRT. Chromogen is colour space aware and operates in its own perceptual colour space called Eab. **E** stands for Exposure and **a/b** are the colour opponent axes, where **a** encodes the green/red axis and **b** encodes the blue/yellow axis.

    To build a look, **stages** are stacked on top of each other. There are ten different types of stage a user can choose from. Each stage type is a simple tool providing look development functionality. Complex looks are produced by adding many simple stages together. All stages are performed at once on the GPU in floating-point precision. This ensures the highest image quality and best performance. Looks created with Chromogen can be exported as LUTs for preview purposes (for On Set visualisation), but it is recommended to apply the look via the Chromogen operator for the final grade to ensure the highest image quality and flexibility.
*   **Presets**

    It is best to start a look development session from one of the presets shipped with Chromogen. However, completely new looks can be created from scratch, too.

    Chromogen ships with the following presets (see "Operator Presets" section below):

    * **Alternia**: basic look with subtle saturation boost in the shadows and prominent skin tone bleaching
    * **Optera**: influenced by the C-105 Vision look
    * **Kulthea**: influenced by the C-102 Japanese look
    * **Viena**: influenced by the C-104 Bipack look
    * **Eternia**: a novel version of a teal and orange look
    * **Motavia**: a modern approach to a sepia look.
    * **Botany**: a strong dystopian look.
    * **Ireta**: an intense look with distinct colour stylisation.
    * **Lithia**: a look with strong colour skews.

    When adding a new Chromogen operator you are taken directly to the operator's Presets page, to allow you to choose a preset to start from.

    Selecting a Chromogen preset activates the **Append** button in the Presets page. When you use **Append**, instead of the current Operator being replaced by the Preset, the stages in the Preset contents are appended to the current Chromogen operator.
*   **Stages**

    The different stages are managed using the **Stages** area on the right side of the UI. Adding new stages, duplicating and deleting them are accessed by a context menu (brought up by right-clicking in the stages area). There are ten different stage types; each type can be added more than once. The stages are divided into three main categories: fundamental, advanced and sector stages:

    **Fundamental Stages** are stages used in almost every look. They build the foundation of the look process.

    * **Colour Saturation**: This tool allows the saturation along the two colour opponent signals to be modified independently. It is influenced by the theory of colour contrast adaptation.
    * **Colour Crosstalk**: This tool introduces crosstalk between the two colour opponent signals. The tool is motivated by crosstalk effects in the visual cortex, like lateral inhibition.
    * **Highlight Bleach**: This tool is for desaturating or bleaching highlights. Most looks desaturate the highlights to give a non-uniform saturation tracking. The four different sides of the colour space can be bleached individually.
    * **Contrast Boost**: This tool allows adding contrast around mid grey, but slightly reduces the brightness of very bright colours. This gives a unique contrast boost found in many popular looks.

    **Advanced Stages** are used for very specific operations.

    * **Brilliance Reduction**: This tool allows a reduction of exposure of colours which are too bright for their saturations, according to reflected colours. See [this video](https://vimeo.com/333078338) for more information on this topic.
    * **Neutral Tint**: This tool allows you to tint the neutral axis. Many popular looks have a coloured neutral axis, such as blue in the shadows and orange in the highlights.

    **Sector stages** operate on half of the colour volume but focus on the sector's centre with a soft roll-off.

    * **Sector Brightness**: modifies the brightness of the selected sector.
    * **Sector Saturation**: modifies the saturation of the selected sector.
    * **Sector Skew**: skews or distorts the colours of the selected sector.
    * **Sector Squash**: squashes or stretches the colours of the selected sector.
*   **Modulation**

    Most stages can be modulated to focus their effect on either darker or brighter colours using the **Zone** and **Pivot** controls in the **Modulation** section. Also, the effect can be focused on either saturated or pastel colours using the **Chroma** modulation control.

    All tools are, intentionally, very broad in terms of the colours they affect; even the sector tools still operate on half of the colour space. Broad edits will produce more robust, pleasing, and general looks, which work across many shots.
*   **Parameters**

    Once a stage is selected, its parameters are shown on the left side of the UI. The coloured slider backgrounds are designed to illustrate the function of each slider.
*   **Graphical Visualisation**

    Below the sliders, there are two graphical representations. The left one is the **Point Cloud**, which indicates the combined modification of all stages. The right side UI element changes depending on the selected stage and provides specific feedback for that stage.

    The default **Point Cloud** representation, **Eab Radial** shows a radial view onto the Eab colour space. This is the recommended view, but the **Eab Cube** and **RGB Cube** representations may be useful for the final evaluation.

    You can pan, rotate, scale, and zoom the point cloud to examine your look from all sides using the mouse and modifier keys. The maximum gamut of the point cloud can also be modified between Eab, LMS, Rec.2020 and Rec.709. The most useful is the Eab gamut. To see specific colours from the image in context to the Point Cloud, it is possible to highlight a specific colour range. Enable the **Pick** button next to the View and pick in the image. This will make all points in the clouds smaller except the picked points.
*   **Desk Mapping**

    When a desk is connected, a secondary stage selection appears next to the primary one. With the two-stage selections, two stages are mapped simultaneously to the encoders of the control surface. The left and right trackballs can also modify essential parameters of the primary selected stage. The two leftmost buttons above the left trackball allow moving the primary stage selection up and down. The middle buttons above the left trackball allow moving stages up and down to rearrange the stage ordering. Buttons above the right trackball allow doing the same for the secondary selection. The middle trackball and ring, in combination with the buttons above and ring, allow you to pan, rotate, scale and zoom the Eab Point Cloud. Bug 53354

#### User Interface

*   **Refreshed Appearance**

    Baselight 6.0 sports a refreshed user interface, with a less obtrusive, flatter appearance:

    * Toggle and radio buttons are now visually distinct from one other and have a highlight when activated.
    * Active tabs are indicated with a clear blue underline.
    * There is a now a standardised colour palette across the application.
    * The **Customise** menu button has been replaced with an icon button showing three sliders.
    * A number of icons have been upgraded, amongst them Reset, Bypass, Cache Strip, Slider Gang and Split Strip.
    * List selections are now blue.
    * Redesigned Keyframe Navigation Bar with larger keyframe indicators.
    * Replaced Mona Lisa icons with text **Grade** and **Matte**.
    * Adding browser or filter tabs to FLUX Manage is now included in single dropdown menu button.
    * Toggle icons are now dimmer when turned off.
    * User interface elements are now laid out more tightly.
    * Radio buttons, toggle check buttons, and button roundness now scale better with different text sizes.
    * Splitter bars are now thicker and the splitters used to separate views now have rounded connectors.
    * Tile group boxes and buttons have had their borders removed and made slighly brighter.
*   **Timeline Bar**

    A top row of controls has been added above the Timeline View. This contains play controls, playback filtering, paste/apply options, and timeline editing tools.

    * Play Controls View has been removed from all default workspaces and custom workspaces that also contain a Timeline View.
    * Controls for playback range, loop mode, and play all frames are now displayed in the Timeline View toolbar and no longer contained in a menu.
    * Playback Speed now displays decimals rather than fractions.
    * Includes a new toggle button for entering and exiting Timeline Edit Mode.
    * All Copy / Paste / Apply options can be accessed from controls in the Timeline Bar when it isn't in Edit Mode:
      * Dropdown menu displays the current state of Paste / Apply options.
      * Four top-level toggle icons for **Protect Destination Mattes**, **Paste Only Primaries**, **Paste Keyframes**, and **Maintain Tracks**.
      * Paste / Apply options are now shared between Galleries and Cuts View.
    * This means that remaining Cuts View controls are now contained in a small floating panel and the option for thumbnail display has been moved to the right-click menu. Bug 64271

#### Face Tracker

*   Added a new 3D Machine Learning tracker, designed specifically for detecting and tracking faces. It can be found in the new **Face** tab inside the Tracker strip.

    The Face Tracker differs from other trackers in that face detection needs to be performed before tracking. It will attempt to detect all faces in an image without the need to specify a tracking area. This produces closed 3D mesh geometry for every detected face, geometry that can be tracked and filtered like other tracking types.

    Face detection may be affected by very dark images or faces that are partially occluded. The following options found in the 'Face' tab's cog menu could improve detection and tracking:

    * **Face Detect Threshold**. Lowering the value will help to detect faces not previously detected. Setting the value too low may detect faces where there are none.
    * **Face Tracking Smoothing Threshold**. Increasing the value before tracking might help with jitter on some problematic material.

    Although face tracking results can't be modified or offset like other trackers, occlusions can be handled using the **Detect Reference** functionality.

    If the **Auto select face reference** option is on, the system will pick the most similar face in that frame based on the geometry. If the option is off and it detects multiple faces, the user will have the option to select the correct face.

    The Face Tracker can be used in two different contexts, Face Warp and Face Perspective.
*   **Face Warp**

    Face Warp is only available in Shapes and Matte Paint - it uses the 3D mesh generated during the face detection phase to warp mattes to fit the face. They will be constrained to the 3D Mesh. Edge shapes are not supported.

    Face detection is performed by clicking the **Face Warp** button in the Shape or Paint operator, or the **Detect Faces** button in the Tracker strip. This must be done before any shapes or strokes are added. After detection, the detected faces can be selected from the tracker list. Faces will have a 3D mesh displayed over the face. Shapes or paint strokes can now be added to the linked face. Face Warp-specific Quick Shapes are available in the Shape operator.

    When using Face Warp, mattes are defined in 'UV' space, which can be thought of as a 2D space representing the unwrapped face. The 3D Mesh is used to project the mattes onto a 3D representation of the face. After shapes or paint strokes are linked to a Face Warp Tracker, changing to a different face will automatically reposition the shape or paint strokes onto the newly selected face.

    Face Warps cannot be unlinked or deleted because, since the matte is defined in the UV 'face' space, they doesn't make sense when not linked to a face - the only valid operation is linking to another face.

    The **Show UV** button will display a side by side view of the image and a 'flattened' view in UV space. This view can be useful to place shapes and paint strokes, because, as it is independent of the pose of the face, it remains roughly constant as the face moves.

    The **Face Zoom** button will zoom to the selected face, allowing for more precise edits.
*   **Face Perspective**

    Used to perform perspective transforms based on 3 points positioned on a a face's 3D mesh. These points are used to to derive a plane which is then used to generate perspective transformations. It can be used with all operators which support Perspective Trackers (i.e. Shapes, Paint, Text, Grid Warp and Perspective). The 3 points are displayed as a blue triangle on the image when the Tracker strip is selected and can be edited there.

    To use the Face Perspective Tracker, the desired Shape, Paint stroke, Text or Grid Warp is created first and then linked to the Perspective Tracker.

    After choosing a Face Perspective track, changing to a different face perspective track will reposition the controls onto the selected face. Unlike Face Warp tracks, Face Perspective tracks can be unlinked and deleted.
*   **Copy and Paste**

    To enhance workflows, the Face Tracker works differently to the other tracker types when being applied to other shots. When a stack contains tracked faces, applying the stack will check the destination shot to see if any tracked faces are already present in a Tracker strip. If so, the grade will be relinked to one of the existing faces. If not, a face detection is performed, and the grade is linked to one of the newly detected faces.

    If the incorrect face was selected, one can go to the relevant operator and simply select the correct face from the tracker list. Any operators will be automatically remapped to the new selection.
*   **Technical Details**

    The machine learning models used to implement the Face Tracker are part of a separate filmlight-flexi-effects installer, which is available in the support section of the FilmLight website.

    Face Tracker does not currently run on Intel macOS systems. Bug 51467

#### Timeline

* **New Appearance**
  * **Modern Look**: The new timeline's cleaner, brighter look aims to make strips and their colours more distinct and easier to interpret.
  * **Context-aware strip roundness**: Strip roundness is now used to make it clear which strips contribute to a layer, by only the top-most and bottom-most strips of a layer being rounded.
  * **Node Graph**: To assist users in visualising the actual graph structure represented by a grading stack, a node graph is now superimposed over the shot, when space allows. In this node graph, blue nodes and lines represent RGBA image data flowing down through the graph, whilst white nodes and lines represent nodes that contribute to a single-channel matte input to a layer. Dotted lines represent references to image data further up the stack, outside of the normal implicit tree structure. When a layer/shot is folded, the layer's folded nodes are arranged horizontally beside the layer's node, their colouring allowing the user to see a layer's internal structure, even when folded.
* **Layer / Shot Folding**
  * **Layer Folding**: It is now possible to fold a layer's mattes down into a layer's grade strip, reducing the vertical space used by the layer. A layer's folding state can be toggled either by clicking the triangular folding icon on the right-hand side of the strip or by using the `\` shortcut with one or more layer strips selected. To toggle the folding state of all layers in a shot, select strips in one or more shots and press `Ctrl+\` (`Cmd+\` on Mac).
  * **Shot Folding**: It is also possible to fold all of a shot's grading strips up into the shot's top strip, providing a greatly simplified view of the timeline. A shot's folding state can be toggled by clicking the triangular folding icon on the right-hand side of the shot's top strip or by selecting a strip in one or more shots and pressing `Alt+\`.
*   **Timeline Tracks**

    It is now possible to vertically subdivide a scene's timeline into several tracks. From an image processing point-of-view, this is mostly cosmetic as image data flows down through the strips in the timeline in the same way, regardless of whether they all sit in one track or are split across several. Tracks, however, are very useful in organising complex timelines, allowing the user to divide their grades into separate tracks, each with a different role ("HDR", "Subtitles", "Sky Replacement", "Stereo Floating Windows" etc). All the track functionality is accessed using the Track UI panel on the left-hand side of the timeline:

    * **Context Menu**: Right-clicking anywhere in the track panel provides options to:
      * Insert a new track above/below the track under the mouse pointer.
      * Move the track under the mouse pointer up/down in the timeline
      * Remove the track under the mouse pointer.
      * Remove all empty tracks
    * **Renaming a Track**: By default, tracks are automatically named using a scheme where track numbers increase going downwards (to match layer numbering direction). To rename a track, simply double-click on the track name to enter edit mode and enter a new name.
    * **Track UI Icons**: Each track has four icons on the panel:
      * **Bypass**: Toggle button which, when turned on, will bypass every strip in the track.
      * **Squash**: Toggle button which, when turned on, will squash the track down to be much smaller than normal, showing only the bottom- most strip in each stack. This is useful in reducing timeline clutter by hiding tracks which aren't immediate needed, allowing the user to concentrate on what is important right now. The height of strips in a squashed track can be controlled by the **Squashed Track Height** preference. It's also possible to toggle squashing of all other tracks in the timeline by `Ctrl+clicking` (Mac: `Cmd+click`) the squash track icon.
      * **Edit Lock**: Toggle button which, when turned on, will mark all shot Layer 0 strips as being edit locked. See the "Edit Locking" section below for more details.
      * **Grade Lock**: Toggle button which, when turned on, will mark all grading strips as being grade locked. When inserting or pasting strips, any grade locked tracks will be ignored. `Ctrl+click` (`Cmd+click` on Mac) on the grade lock icon will result in the track being "soloed", whereby it will be unlocked and all other tracks will be grade locked. This is very useful if one wishes to force all strip insertion to occur on a given track. See the "Grade Locking" section below for more details.
    * **Maintain Tracks Paste Option**: The new **Maintain Tracks** paste option controls whether or not the application attempts to maintain a source strip's track when it is pasted. Source and destination tracks are matched by name - if **Maintain Tracks** is on and a source strip's track doesn't exist in the destination scene, it won't be pasted.
    * A **Maintain Tracks** button has been added to the Blackboard Classic, Blackboard 2 and the Slate. It can be found on the "Apply All" button on the Blackboard Classic and in Chalk.
    * **Render Line Movement**: By default, moving the render line up and down will move it between tracks. Using `Shift+up` will force the render line to remain within the current track, which is useful if one wishes to insert additional strips at a sub-row above the highest sub-row in a track. On a Blackboard or Slate `Shift+Up Arrow` has the same behaviour.
*   **Edit Locking**

    It's now possible to edit lock a shot's layer 0 strip, meaning that the shot's horizontal position in the timeline can't be changed and neither can its frame offset within the image/sequence or movie, frame increment etc. This is very useful if one needs to prevent a carefully constructed conform from being accidentally changed. In Edit mode, edit locked strips will show a grey bracket or region indicating that they are edit locked.

    A layer 0 strip can be marked as edit locked in two ways:

    * By edit locking the track in which the strip resides.
    * By assigning a category in **Scene Settings** > **Category Group** > **Edit lock strips of category** to a strip.
*   **Grade Locking**

    Baselight grade locking functionality has been enhanced. Now, in addition to preventing its parameters from being modified, grade locking a strip prevents a grading strip from being moved vertically up/down within a shot.

    A layer 0 strip can be marked as grade locked in two ways:

    * By grade-locking the track in which the strip resides.
    * By assigning a category in **Scene Settings** > **Category Group** > **Grade-lock strips of category** to a strip.

    To allow users used to Baselight 5.3 to restore the previous strip-locking behaviour, two new preferences have been added in the new **Strip Locking** section of the Timeline preferences:

    * **Allow Removal of Grade-Locked Strips**.
    * **Allow Vertical Movement of Grade-Locked Strips**. Bug 65603
*   **Zoom Management**

    The Timeline View now contains a zoom menu at the top right that displays the current zoom percentage relative to the default zoom amount seen on start-up. This menu allows for various methods of zooming the Timeline: - **Zoom In** / **Zoom Out**: Zoom in and out in increments. - **Max Zoom**, **100%**, **50%**, or **10%**: Set horizontal zoom level to one of a number of pre-configured zoom levels. - **Zoom to Selected**: Will zoom to the extent of explicitly selected strips or, if Edit Mode is on, it will zoom to the extent of any edit tool that is set. - **Zoom to Fit Scene**: Zooms out horizontally to show the entire scene. If toggled off the timeline will return to the previous horizontal zoom level. - **Vertical Zoom to Fit Stacks**: Zooms out vertically enough to show all the strips in the scene. If toggled off the timeline will return to the previous vertical zoom level. - **Default Vertical Zoom**: Return to the default vertical zoom level. Bug 59781
*   **JKL Keyboard Accelerators for Playback**

    After many requests and to match the conventions defined by other systems, the JKL keys on the keyboard now map to Play Backwards, Stop Playback and Play Forwards. Repeated presses on J and L will keep doubling the play speed up to a maximum of 32x.

    This change has necessitated changes to the following keyboard accelerators:

    | New Accelerator                     | Old Accelerator | Action                             |
    | ----------------------------------- | --------------- | ---------------------------------- |
    | `V`                                 | `K`             | Toggle Counters                    |
    | `Win+F` (Mac:`Ctrl+F`)              | `F`             | Toggle FPS display                 |
    | `M`                                 | `L`             | Toggle Mark                        |
    | `Shift+M`                           | `Shift+L`       | Delete All Marks Under Cursor      |
    | `Shift+Ctrl+M` (Mac:`Shift+Cmd+M`)  | `Shift+Ctrl+L`  | Delete All Marks                   |
    | `F`                                 | `J`             | Toggle Category                    |
    | `B`                                 | `N`             | Edit Mode Mark In                  |
    | `Shift+B`                           | `Shift+N`       | Remove Mark In                     |
    | `N`                                 | `M`             | Edit Mode Mark Out                 |
    | `Shift+N`                           | `Shift+M`       | Remove Mark Out                    |
    | `Ctrl+N` (Mac: `Cmd+N`)             | `Ctrl+M`        | Mark Selection/Shot/Gap In and Out |
    | `Shift+Ctrl+N` (Mac: `Shift+Cmd+N`) | `Shift+Ctrl+N`  | Clear Mark In and Out              |
    | Removed                             | `M`             | Add Median strip                   |
    | Removed                             | `Shift+M`       | Add Soften strip                   |

    Bug 65270
* To match, the **Reverse Play Direction** toggle has been removed from the Timeline Bar and replaced with a dedicated **Play Backwards** icon, which toggles between playing backwards and stopped. As a result, the **Play** icon will now always play forwards. Bug 66316
* The Keyboard Shortcut PDF files available from the Help menu have now been updated for Baselight 6.0. Bug 66327

#### Edit Mode

*   Baselight 6.0 brings extensive improvements to Timeline Editing.

    The new Edit Mode can be toggled on/off via the **Toggle Timeline Edit Mode** button in the Timeline Bar. It can also be toggled on/off via the **Edit** > **Edit Mode** menu item or via the `Shift+Enter` keyboard shortcut.

    Once Edit Mode is turned on, the Timeline Bar will change to display a variety of icons which provide bits of editing functionality. Each icon can be hovered over to display a tooltip which describes what the icon does along with its equivalent keyboard shortcut.
*   **Shot-Based Editing v.s Selection-Based Editing**

    If there are no explicitly selected strips in the Timeline, the various editing functions will automatically work out the strips which should be affected (typically those strips lying under a top strip).

    On the other hand, if there are explicitly selected strips, then the editing functionality will work based on those selected strips.
*   **Trim Mode and Move Mode\*\***

    The first two icons on the left select what editing mode the timeline is set to. Switching between the two modes will change the available edit tools located to the right of the mode icons.

    **Trim Mode**

    This mode allows the use of editing tools that are related to trimming, rolling, slipping or Sliding a shot. When it is selected, the tool icon section to the right of the mode icons will be occupied with the following five tool icons:

    * **Trim Left**: Trims the left edge of a shot or strip, rippling the strips right of the trim.
    * **Roll**: Trims one edge of a shot or strip whilst extending the other.
    * **Trim Right**: Trims the right edge of a shot or strip, rippling the strips right of the trim.
    * **Slip**: Slips the source media of the shot left or right.
    * **Slide**: Slides the source media of the shot left or right, whilst consuming or extending adjacent strips.

    When these icons are selected, coloured bracket(s) will appear indicating the side(s) of the shot or strip that the edit will affect. The colours of these brackets can be changed in the Preferences, in the **Edit Mode Settings** of the **Timeline** tab. If the edit is based on a cut (e.g. **Trim Left**), the edit brackets will appear at the cut nearest to the current cursor. If the edit is based on a shot or strip (e,g **Slip**), the edit brackets will appear at the shot or strip that the cursor is on. The cursor will follow the edit when trimming a shot at a cut point.

    **Move Mode**

    This mode allows the use of editing tools that are related to trimming and moving a shot. When it is selected, the tool icon section to the right of the mode icons will be occupied with the following 3 tool icons:

    * **Trim Left**: Trims the left edge of a shot or strip, bouncing strips out of the way, if required.
    * **Move Shot**: Moves a shot or strip left or right, bouncing strips out of the way, if required.
    * **Trim Right**: Trims the right edge of a shot or strip, bouncing strips out of the way, if required.

    When these icons are selected, blue bracket(s) will appear indicating the side(s) of the shot or strip that the edit will affect, based on the shot or strip that the cursor is on.
*   **Trim Buttons**

    The following 4 icons to the right of the edit tool icons are dedicated to performing 1-frame or 10-frame trims to the left or right, based on the Edit Tool that is currently selected.
*   **Other Editing Tools**

    The last remaining Edit Mode icons offer several useful tools for editing:

    * **Lift**: When a Mark In and a Mark Out point is set, it removes any strips that lie within the interval and warps the cursor to the Mark Out point.
    * **Extract**: Performs a **Lift**, and ripples the gap that is created by it.
    * **Cut Stack/Selection At Cursor**: Cuts the stack at the cursor if there are no explicitly selected strips. If there are selected strips, they are at the cursor location.
    * **Mark In**: Sets a Mark In at the current cursor position. If there is one already present, it removes it.
    * **Mark Out**: Sets a Mark Out at the current cursor position. If there is one already present, it removes it.
    * **Mark Selection/Shot/Gap In And Out**: Sets a Mark In and a Mark Out on the current selection, or the shot at the current cursor, or the gap at the current cursor, in that order of precedence.
    * **Snap To Nearest Edge/Mark/Cursor while dragging**: Enables/disabled snapping behaviour, which is triggered when a brack is dragged close to the edge of a strip, make or cursor.
*   **Customise Menu**

    The final Edit Mode icon contains a customise menu where several default behaviours can be toggled on or off:

    * **Handle Protection**: When on, it prevents editing operations from going outside of a shot's available media. The size of handles left in frames will be displayed above the edit brackets whilst editing is in progress. When there is media left, the available handles will be displayed in green, whereas if the shot references missing media, the size of missing media will be displayed in red.
    * **Use Display View To Shot Multi-View While Editing**: When on, the Display View will be taken over while editing to show the relevant In and Out points of the edit.
*   **Editing with the Mouse**

    To begin editing with the mouse, simply hover over the desired strips or shots in the Timeline. As you do so, various edit brackets will appear with the corresponding tool highlighted in the Edit toolbar. Which tool appears when you hover is arranged in the same left to right order that the Edit Tools are, based on whether you are in **Trim Mode** or **Move Mode**.

    Clicking on brackets will "lock" the edit point, allowing keyboard accelerators to be used to move the edit point. Clicking again away from the edit point will unlock it again.
*   **FLUX Manage Insertion**

    The insertion button at the bottom right corner of FLUX Manage has been changed to reflect the new editing functionality. It will now contextually show up to 4 buttons:

    * **Append**: Appends the FLUX Manage selection to the end of the Timeline and warps the cursor to it.
    * **Ripple**: Ripples the FLUX Manage selection at the cursor, or within a Mark In and a Mark Out point, if they are set.
    * **Overwrite**: Overwrites the FLUX Manage selection at the cursor, or within a Mark In and a Mark Out point, if they are set.
    * **Overlap**: Overlaps the FLUX Manage selection at the cursor, or within a Mark In and a Mark Out point, if they are set.
*   **Keyboard Shortcuts**

    The following table shows a list of keyboard shortcuts that are mapped to the various pieces of edit mode functionality described above.

    | Keyboard Shortcut              | Edit Mode Functionality                                            |
    | ------------------------------ | ------------------------------------------------------------------ |
    | `T`                            | Trim Mode                                                          |
    | `Y`                            | Move Mode                                                          |
    | `Q`                            | Ripple left of Cursor (Trim Mode)/Trim left of Shot (Move Mode)    |
    | `W`                            | Rolling (Trim Mode) / Move Shot (Move Mode)                        |
    | `E`                            | Ripple right of Cursor (Trim Mode)/ Trim right of Shot (Move Mode) |
    | `S`                            | Slip                                                               |
    | `Shift+S`                      | Slide                                                              |
    | `C`                            | Cut Stack/Selection                                                |
    | `U`                            | Lift                                                               |
    | `I`                            | Extract                                                            |
    | `N`                            | Mark In                                                            |
    | `Shift+N`                      | Clear Mark In                                                      |
    | `M`                            | Mark Out                                                           |
    | `Shift+M`                      | Clear Mark Out                                                     |
    | `Control/Cmd+M`                | Mark Selection/Shot/Gap In And Out                                 |
    | `,`                            | Edit 1 Frame Left                                                  |
    | `Shift+,`                      | Edit 10 Frames Left                                                |
    | `.`                            | Edit 1 Frame Right                                                 |
    | `Shift+.`                      | Edit 10 Frames Right                                               |
    | `Alt+Backspace`                | Ripple Delete                                                      |
    | `Shift+Enter`                  | Toggle Edit Mode On/Off                                            |
    | `/` and `*` (Mac: `=` and `/`) | Toggle Edit Mode On/Off and rotate trim/move modes                 |

    Note that when **Edit Mode** is turned on, the standard grading-related shortcuts originally mapped to will be swapped out to the ones shown above.

    Turning **Edit Mode** off will restore the original keyboard shortcuts. Additional information about the shortcuts may be found by hovering over the relevant icons in the Edit Tools UI. Bug 45266
*   **Performance**

    Greatly improved performance when doing Trim Start/End (Ripple) edits in Edit mode, as well as when doing `Alt+arrow` (Bounce) edits with a large number of selected strips. Bug 53320

#### Alpha (Opacity) Support

* Baselight 6.0 adds extensive support for compositing and working with images with opacity information, normally stored in the alpha channel of RGBA images. Bug 54001
* The Sequence operator **Input RGBA** setting is enabled when the input media has an alpha channel, and allows control over whether to treat the RGB channels as premultiplied by alpha or not, and if premultiplied, whether the multiplication was done in linear or in the native colour space. Bug 62993
*   The Sequence operator **Stack RGBA** setting controls processing of the images entering the grading stack. For RGBA media:

    | Stack RGBA                  | Behaviour                                                  |
    | --------------------------- | ---------------------------------------------------------- |
    | RGBA                        | Passes the RGBA data into the stack unchanged              |
    | RGB (ignoring alpha)        | Discards the alpha channel and makes the image opaque      |
    | RGB (composited onto black) | Scales RGB by the alpha channel and makes the image opaque |

    RGB media is always treated as opaque; Stack RGBA controls the transparency at the edges of the image and the behaviour of operators such as Blur:

    | Stack RGBA | Behaviour                                                                                               |
    | ---------- | ------------------------------------------------------------------------------------------------------- |
    | RGB        | Matches Baselight 5: the area outside the image is opaque black, and remains opaque when blurred        |
    | RGBA       | The area outside the image is transparent, and the image becomes transparent at the edges when blurred. |
*   Cursors View has a new **View RGBA** control which affects Display View and Cuts View:

    | View RGBA                       | Behaviour                                                                                                                                                                    |
    | ------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
    | RGB (composited on black)       | <p>Treats the alpha channel of the image as opacity and composites the image onto black<br>This is equivalent to rendering a premultiplied image</p>                         |
    | RGB (composted on chequerboard) | Treats the alpha channel of the image as opacity and composites the image onto a chequerboard.                                                                               |
    | RGB (ignoring alpha)            | <p>Matches Baselight 5, ignoring the alpha channel<br>Can be misleading because it shows colour in areas that are entirely transparent (where alpha is zero or negative)</p> |

    The default View RGBA behaviour can be set in Preferences under Display/Appearance. Bug 62992

    The **View Channel** control now includes Alpha. The keyboard and desk shortcuts for View Channel have been updated accordingly. Bug 63337
*   Added new options for handling single-channel media, using a new **Treat Single Channel As** setting which replaces the **Stack RGBA** setting when the Sequence uses single-channel media or has a single channel selected.

    | Treat Single Channel As | Behaviour                                                                                                                                                                                                               |
    | ----------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
    | Matte                   | Keep media as single channel, which will be treated as a linear matte.                                                                                                                                                  |
    | Monochrome RGB          | <p>Copy single channel to R,G,B channels to make a monochrome image in the Input Colour Space.<br>Spatial operators like Transform and Blur will treat the image as having hard edges with no transparency outside.</p> |
    | Monochrome RGBA         | <p>Copy single channel to R,G,B channels to make a monochrome image in the Input Colour Space.<br>Spatial operators like Transform and Blur will treat the image as being transparent outside its edges.</p>            |
    | Alpha                   | Copy single channel to A channel of a 100-nits white image in the Input Colour Space.                                                                                                                                   |

    For the two Monochrome options, if 1.0 in the Input Colour Space is brighter than 100 nits, a warning is shown because the resulting RGB/RGBA image may be unacceptably bright. Bug 63002
* Render View now shows a **Channels and Alpha** option when rendering to a file format or codec which supports four-channel output (RGBA or Y'CbCrA). File types which only support straight (unpremultiplied) RGB do not permit rendering with premultiplied RGB and vice versa. Bug 62992
* Scene Settings View now has RGBA options in **Display And Timeline Cache**. These allow alpha channel values to be seen when clicking on the image in Display View, but will increase the disk space needed for cache files and could impact performance. Bug 54001
* Scene Settings View also now has a **Strip Caching** option to choose between RGBA and RGB. Caching as RGBA will maintain alpha information, but will increase the disk space needed for cache files and could impact performance. Caching as RGB will cause the output of each cached strip to be made opaque, discarding any alpha information. Bug 60717
*   The Layer UI's "Layer Mode" menu has been streamlined. Selecting a composite mode will now simply composite the foreground image over the background using the alpha channel from the foreground.

    If the foreground doesn't have valid alpha, an area of the foreground image can be isolated by adding any of the matte operators (Shape, DKey etc) to a composite layer (using the standard desk, keyboard or UI buttons/accelerators). Bug 63014
* A layer with a matte can now be set to **Combine Matte With Alpha**, which uses the matte to modify the alpha channel of the input image (before it passes through the operators in the layer). Bug 60900
* Added "Initialise Composite Foregrounds To RGBA" option to the layer "Customise" menu (and the general "Insert" menu). If enabled, when a layer is switched to composite mode, the/any foreground sequence will have its "Stack RGBA" mode automatically switched to "RGBA" (avoiding the need to do so manually when creating a picture in picture effect, for example). Bug 63987
*   The Blend operator has five new modes which use alpha data to combine foreground (FG) and background (BG) images:

    | Blend Mode | Output                                                                                                 |
    | ---------- | ------------------------------------------------------------------------------------------------------ |
    | Over       | Standard composite: FG where FG is opaque and revealing more of BG as FG alpha decreases               |
    | In         | FG colour where both FG and BG alpha are opaque                                                        |
    | Out        | FG colour where FG is opaque but BG is transparent                                                     |
    | Atop       | Similar to Over but retains the opacity of the BG image                                                |
    | Xor        | Transparent where either FG or BG is opaque, FG where BG is transparent and BG where FG is transparent |

    These modes are also available in layers for Result Blending and Composite Settings. Bug 60776
* The new **Alpha From Matte** operator allows an image to have its alpha channel modified by a matte, for example a Shape or a key. Bug 61393
* The Edge Crop operator's Crop Colour option now offers **Transparent** to make the area outside the visible image transparent. Bug 62885
* The Blank operator now has an Alpha parameter. Bug 53221
* The Shuffle operator now specifies what is shuffled into the output alpha channel. Bug 53220
* Many operators have been updated to handle images with transparency. To ensure that Baselight 5 scenes continue to render as they did, operators inserted in earlier versions will often behave differently from operators inserted in Baselight 6.0. Bug 62013
* The preview images in BLG files now contain alpha channels. Bug 63675
* The right-click menu for thumbnails in FLUX Manage View now allows RGBA images to be viewed composited on black or chequerboard. Bug 60569
* The Grid Warp operator now has a **Transparent Outside** option. Bug 63026
* The Lens Correction operator now has a **Transparent Outside** option. Bug 62014

#### RIFE ML Retime

*   An improved Retime sampling mode **RIFE ML Retime** is now available.

    Real-Time Intermediate Flow Estimation for video frame interpolation (RIFE ML Retime) uses a Flexi effect to run the machine learning algorithm. This effect will need to be installed on the system using the filmlight-flexi-effects installer, which is available in the support section of the FilmLight website.

    Similar to the Optical Flow sampling mode, RIFE ML Retime has a quality setting 'Medium', 'High', 'Best'.

    RIFE ML Retime will always be using **Process in Working Format**.

    RIFE ML Retime does not currently run on Intel macOS systems. Bug 57701

#### Operator Presets

*   Operator presets provide a quick and easy way of storing operators as presets. The Presets View is accessed using the **P** icon in the Parameters View (just to the left of the **3D** icon). In this view, you see thumbnails for the presets defined for the current operator; double clicking on a preset or pressing **Apply** will replace the current operator with the selected preset.

    Note that a preset stores the entire operator, including keyframes (but excluding trackers). Applying a preset will remove any keyframes in the current operator and replace them with any that are stored in the preset.

    You can leave the Presets View by clicking the **P** icon again or by pressing the backwards triangle button at the left of the preset toolbar.

    You can also toggle the Presets View using the hotkey `Win+P` (`Ctrl+P` on Mac) and there is also a Blackboard/Slate shortcut (`Ctrl+DBS Try` by default).

    The **Create** button stores a copy of the current operator as a preset (after asking for desired name and optional comment). Presets are stored with keyframes but trackers are removed.
*   **Preset Storage Hierarchy and Locations**

    There is a hierarchical structure for Preset storage with the following levels:

    * Factory presets that ship with the product and cannot be altered.
    * Site level presets accessible by everyone on site
    * Job level presets accessible to everyone working on a particular job.
    * Scene level presets local to the current scene.
    * User level presets that are specific to a particular user.

    Factory presets are stored in a private read-only database.\
    Job and Scene presets are stored in the appropriate Baselight scene/job.\
    The Site and User presets are stored in special scenes whose locations are defined in the preferences (under **System > Database**).

    You will generally want to point these to the same location on a central database host so they are accessible from all machines.

    In the Presets View, there is a dropdown (that by default will be showing **User**) showing the current storage level - this determines where newly created presets will be stored.

    By default presets in 'higher' storage levels than the current level are also displayed but you can control this using the **Include Presets Above** toggle. Similarly, if you have two presets of the same name (e.g. a Site level preset and a Job level preset both called "Banana"), you can choose whether the 'lower' item hides the 'higher' one or whether both are displayed with the **Hide Overridden Presets** toggle.

    At the right hand side of the Presets View is another dropdown (by default showing **View Selected**) to control whether the thumbnails show the result of the preset on the entire stack, or only the output from the current operator.

    The cog menu at the far right allows moving and copying Presets between storage levels, and also has a toggle **Close on Apply** to control whether applying a preset should automatically turn off the Presets View.
*   **Old Operator Presets**

    We are now deprecating the old operator preset mechanism. You will only be able to use the old mechanism to access existing legacy presets and we recommend you save them using the new mechanism and then remove the old presets.

#### Flare

*   Flare is a tool for adding lens flares to scenes by creating a list of stages that can be combined to produce convincing flare effects.

    Flare is colour space aware and operates in an internal colour space chosen so that the Red and Blue components correspond better with the perceived end colours of the typical spectrum.

    To build a flare, **stages** are stacked on top of each other.
*   **Stages**

    The different stages are managed using the **Stages** area on the right side of the UI. Adding new stages, duplicating and deleting them are accessed by a context menu (brought up by right-clicking in the stages area). In Flare, this area also supports multiple selection of stages.

    There are eleven different stage types; each type can be added more than once. Nine of these can be thought of as Flare **elements** that simulate various phenomena caused by lens optics.

    However there are two important stage types that are used to organize and control the elements rather than directly defining an effect in their own right:

    **Group and Light Stages**

    * **Group**: This stage allows you to group flare elements hierarchically.\
      \
      This makes it easier to take effects that you've created (which may contain multiple elements) and control their appearance or package them as presets.\
      \
      Group controls affect all the elements in the group. There are two tabs:
      * **Basics**: Contains colour and brightness controls (applied multiplicatively) and a scale factor applied to the size of child elements.
      * **Axis**: sets the _axis_, which controls the position of rendered elements in combination with the lights. You do not have to define a group - elements not inside a group get a default axis at the center of the screen (that cannot be edited). Conceptually, you can think of the entire Flare effect being contained in a non-editable group.\
        \
        Notes: Moving elements in/out of groups is accomplished by moving them up and down. Moving an element directly below a stage up will move it into that stage. Moving the bottom element in a stage down will move it out of the stage.
    * **Light**: In Flare, elements are rendered in conjunction with lights.\
      \
      This is useful because you can drive a set of elements with multiple lights, for example a pair of car headlights, and you will automatically get two sets of matching flares that follow the lights realistically.\
      \
      In addition, the position where an element is rendered is calculated based on the position of the light and axis. In particular, in tools with a distance parameter, the effect is positioned on a line joining the light to the axis, (with distance = 0 meaning positioned at the light, and distance = 1 meaning positioned at the axis).\
      \
      Note: _Lights inside a group only affect elements inside that group, and only the elements below them, never above._\
      **It is important to realise that an element has no effect unless it is acted on by a light.**\
      \
      There are 3 tabs:
      * **Light**: Allows setting of the light colour, brightness and position. For matching the light position to a moving object, you have access to the Baselight tracker controls. This will allow you to track a moving light source in the image and apply the tracking information to the Light Stage. The available trackers are the 1 Point, 2 Point and Area trackers.
      * **Glare**: Use this to add a glare effect to the light - note that if this is not used, the light is not in itself visible (although it has a visible effect on flare elements).
      * **Animation**: This tab allows the light brightness to be automatically animated to produce a flickering light effect.

    **Flare Element Stages**: these are the tools simulating various flare phenomenon.

    * **Sun**: as the name suggests, this element simulates the glare provided by the Sun, but is also often useful to use in conjunction with the Starburst element in shots where bright artificial lights are in shot. Note: the **Glare** tab in the Light stage in fact just applies a **Sun** effect.
    * **Airy**: this tool replicates an Airy Disk - the diffraction pattern caused by light passing through a circular aperture.
    * **Rays**: this tool simulates Crepuscular Rays - the effect created when sunlight shines through openings (gaps in clouds, foliage or buildings) in a hazy atmosphere.\
      Note: because this effect works best when the effect center is a long way off screen, the **Distance** and **Direction** parameters allow for adjusting the position of the source without actually needing on screen interaction.
    * **Lens Ghosts**: this tool simulates the multiple 'ghost' images of the lens iris caused by reflections in the optics. There are 3 tabs:
      * **Basics**: allows control of the basic appearance and positioning of the ghosts.
      * **Exit Aperture**: simulates the occlusion of parts of the reflection by the final lens aperture.\
        Note that the R, G, B parameters in this tab control the way the occlusion is applied to the RGB channels - they do not represent an RGB colour.
      * **Randomness**: allows control over how much random variation is applied. For example, setting the Distance here to 0 will cause the ghosts to be spaced equally, rather than randomly.\
        The Noise settings add some random noise to the effect as typically seen in real life ghosts.
    * **Starburst**: this tool simulates the diffraction effect caused by the lens iris, causing a 'Star' pattern. There are 2 tabs:
      * **Basics**: contains the tools you will most commonly want to adjust.\
        \
        The **Blades** parameter controls the number of blades (sides) in the iris being simulated, and therefore the number of points in the star pattern. Note that Baselight simulates a real iris and so an odd number of blades actually produces two sets of points with one set at a reduced amplitude. This amplitude is controlled by the **Secondary** parameter.\

      * **Advanced**: contains less frequently used parameters.\
        \
        **Blade Stretch** and **Dir Stretch** are used for making anamorphic star patterns. **Blade Stretch** adjusts the length of blades without changing their direction, while **Dir Stretch** stretches the actual directions of the blades.\
        \
        Under the **Randomness** heading, **Angle** and **Size** allow some random variation in the size and direction of the blades. **Noise** and **Noise Frequency** can be used to add some random noise to the shading of the blades.
    * **Chroma Flare**: this tool can be used for creating rainbow like effects.\
      Two parameters may need explanation:\
      \
      **Filaments** control how much the effect looks solid as opposed to made up from filaments.\
      \
      **Spread** controls how much the 3 colour components are spread out.\

    * **Anamorphic**: this tool can be used for simulating the elongated flares typically associated with anamorphic lenses. There are 3 tabs:
      * **Basics**: contains the basic appearance and position of the flare.\
        \
        The **Offset** parameters are provided to easily offset the effect relative to the light position.\
        \
        **Size** defines the overall size of the flare, **Falloff** how quickly it falls off in the anamorphic direction. The smaller the falloff, the more stretched out the flare is.
      * **Core**: this allows adding a "central core" flare with a different shape and brightness.
      * **Sidebands**: This allows easy creation of smaller 'sideband' flares that echo the central flare.
    * **Light Leak**: this tool produces a simple light leak effect. It is essentially a radial gradient effect modulated by noise.\
      \
      The colour gradient is defined by the 3 colours **Center**, **Middle**, **Outer**, with the **Midpoint** parameter defining where the middle colour lies in the gradient.\
      \
      **Size** determines the overall size of the effect, while **Scale** controls the scaling of the noise pattern.\
      \
      **Threshold** controls the point at which the noise function fully modulates the Gradient effect.\
      \
      **Detail** controls the way multiple levels of detail are combined in the noise function - increasing detail changes the effect from being fairly smooth to a much more fractal like noise.
    * **Confetti**: this tool provides a way of quickly adding a large number of randomly positioned lens ghosts. While many uses will be somewhat frivoulous, it can also be useful for simulating dust on the camera lens. There are two tabs:
      * **Appearance**: controls relating the the basic appearance of each ghost element.\
        These controls parallel the controls of the same name in the **Lens Ghosts** tool.
      * **Duplication**: controls affect the way the ghosts are randomly duplicated.\
        \
        **Count**, **Size** and **Concentration** control the number of ghosts, the size of the area in which they are duplicated, and how much the ghosts are concentrated in the center of that area.\
        \
        **Distance** controls the positioning of the generation area.\
        \
        **Brightness** and **Size** (under the **Randomness** heading) control the random variation of element brightness and size.

    **Some General Notes on Using Flare Efficiently**

    * **Colour**:
      * While Flare has a custom internal colourspace, user colours are defined in Rec.2020.
      * All Stages allow you to define a colour for that Stage. The Group, Light and Element colours interact _multiplicatively_. For this reason, choosing strong colours for Group or Light stages may have unexpected consequences (e.g. a pure red light combined with a pure blue element will not have any effect).
      * Right-clicking on a colour well in Flare will provide an extensive set of preset palette colours to choose from as a starting point
    * **General**
      * Realistic flares will usually be subtle, however the default stage settings are purposely set to be easily visible when first applied, use the brightness setting in the stage to change how the flare sits in the image.
      * Although the Group stage allows you to shift the axis, the default setting will generally provide the most realistic movement of elements relative to the lights.
      * You can use multiple stages to construct more complex flares; save these as presets that can be used to build new flares (in Presets View you can use the Append option to add the preset to your current Flare instead of replacing it). Bug 54453

#### Halation

* Halation simulates light scattering in a film camera. It adds a coloured halo around the highlights. Bug 62840

#### Sharpen Luma Operator

* The new Sharpen Luma operator is similar to Sharpen but is colour space aware and its sharpening is based on the luminance channel. In addition, there are controls that limit sharpening:
  * **Shadow Threshold**: controls the sharpening of darker tones
  * **Contrast Threshold**: controls the sharpening of high contrast areas in order to reduce ringing
  * **Noise Threshold** controls the sharpening of low contrast areas to reduce noise and compression artefacts. Bug 52969

#### Boost Detail Operator

*   The new Boost Detail operator boosts local detail. Smaller detail is boosted more than larger detail. **Gain** sets how much boost, **Scale** sets an upper limit on the detail size to be boosted, and **Threshold** sets a contrast limit, so we can make images look crisper, but not introduce noise into skies and other flat areas.

    The sum of all the boosted details at the different scales may go outside the normal image range. **Shadow Threshold** fixes negative values using a smooth tone curve for image values either side of zero, with a range of **Shadow Threshold** \* **Gain**. If the range is zero or less it gives a hard clip at zero. Bug 56701

#### Bokeh

* Bokeh simulates an aperture-like defocus effect by convolving the linear image with a shape. The most important parameter is **Radius**, which sets the maximum bokeh radius as a fraction of the image height.
*   **Depth Matte**

    The radius of the bokeh effect at each pixel can be controlled by using a **Depth Matte**, where values between 0 and 1 define the depth of each pixel. A depth matte can be as simple as a Shape or as complex as a machine-learning-derived per-pixel depth map. Once the Bokeh operator has been provided with a depth matte, the following parameters control its behaviour:

    * **Depth Mode**: Determines how the 0-1 values of the depth matte are interpreted. There are four possible values:
      * **Ignore**: There is a depth map but it is ignored. The whole image gets the maximum bokeh size. This allows the effect of the depth matte to be assessed without needing to change the stack structure.
      * **Far: 0**: Z (pixel depth) is the depth matte value. This is used for artificial depth mattes where the value goes from 0 (far) to 1 (near).
      * **Far: 1**: Z is 1 - the depth matte value. This is used for artificial depth mattes where the value goes from 0 (near) to 1 (far).
      * **Far: infinity**: Z is 1.0 / the depth matte value. Map values go from 1.0 to infinity. 1.0 is the aperture. Values less than 1.0 are clipped. This is often used with actual depth data.
    * **Focus**: The point within the 0-1 depth matte range which is in focus. When using a depth matte, the bokeh size varies with the difference between the Focus and the depth Z calculated from the depth matte value. If Z matches Focus then the bokeh size is zero, and the output is sharp. It is also possible to set the focus by simply clicking on the image.
    * **Depth**: The depth of focus around the focus point. Smaller values will result in the bokeh size increasing more quickly as the depth value moves away from the focus point.
    * **Lock Focus Pick**: When turned on, clicking on the image no longer sets the focus point.
    * **Foreground Blur**: Used in situations where there are pixels whose depth is in front of the focus point. When enabled, these foreground pixels are grown, allowing for a softer, more realistic edge. Required because we don't have access to the occluded pixels which are needed to achieve a physically realistic foreground blur.
*   **Bokeh Shape**

    The shape with which the image is convolved is controlled by the **Bokeh Shape** section:

    * **Shape**: Sets the bokeh shape, with the following behaviour:
      * 0.0 gives a circle.
      * 1.0 gives a straight-sided polygon.
      * Between 0.0 and 1.0 gives a convex polygon.
      * Beyond 1.0 gives a concave polygon, and then finally a star.
    * **Sides**: For Shape values above 0.0, gives the number of sides of the polygon or points in the star.
    * **Angle**: Used to rotate the polyon/star.
    * **Anamorphic**: Used to squash the bokeh shape, simulating an anamorphic lens.
*   **Advanced Parameters**

    Some more advanced settings are included to aid in tweak the Bokeh appearance for a given shot:

    * **Max Radius**: A setting which trades bokeh quality for processing speed. Below this radius, the bokeh is calculated at a lower resolution and then upscaled.
    * **Depth Threshold**: Threshold which allows the size of the in-focus area around the focus point to be increased a little, reducing artefacts when using noisy depth maps.
    * **Foreground Edge**: If **Foreground Blur** is turned on, this control specifics how large the soft edge of the foreground object is.

#### Curve Grade Operator

*   The Curve Grade operator has been completely reworked. It now includes enhanced colour space aware curve processing that provides accurate, floating-point, HDR-ready grading.

    The user interface has also been overhauled with new layout options, curve histograms, improved trackball support etc. Bug 50691
*   Curve Grade's "Control Point Per Trackball" mode has been substantially improved. These improvements include better behaviour when editing multiple control points simultaneously, automatic graph control point selection on undo/redo etc.

    Tangent Tk panels also now support the following button mappings:

    | Button                    | Behaviour                                                   |
    | ------------------------- | ----------------------------------------------------------- |
    | `A`                       | 'Control' modifier                                          |
    | `B`                       | 'Shift' modifier                                            |
    | Trackball reset 1         | Reset/add default control point                             |
    | Trackball reset 2         | Toggle add/remove trackball control point to/from selection |
    | `A` + Trackball reset 1/2 | Assign previous/next control point to trackball             |
    | `B` + Trackball reset 1   | Delete trackball control point.                             |

    Bug 50722

#### Hue Angle Keyer

*   The Hue Angle keyer has been upgraded to use a new, perceptually-uniform colour space that provides more consistent, accurate keys. The user interface has also been substantially improved and now includes:

    * Interactive channel bars with integrated histograms (and a colour wheel vectorscope).
    * Improved presets that provide tighter keys by default.
    * Improved initial rolloff settings when picking on the image.
    * The new **Pick Rolloff Behaviour** option (available from the customise menu) to expand the rolloffs to cover the entire range when picking, resulting in an initially 'soft' key. The rolloffs can then be refined/tightened using the (new) shift+click/drag image interaction that subtracts the region selected from the current rolloff settings.

    There is also an **Expand Rolloffs** button which immediately expands the rolloffs (regardless of the default mode).

    Note: To grow the key to include additional colours, use `Ctrl+click/drag` (`Cmd+click/drag` on Mac) on the image. Bug 47062

#### Paint

* The Paint operator now takes advantage of alpha to produce an RGBA image. It has a **Transparent Background** toggle to either output the paint strokes composited over the input or on their own over a transparent background.
* The new **Composite Paint Strokes Separately** button will split the Paint layer into its constituent elements, with the strokes rendered onto a transparent background and composited separately with the input image. This enables the use of any grading operator to modify the paint strokes before they are composited. Bug 48372

#### Text

* The Text operator now has an **RGBA** option which produces an RGBA image which can be composited separately. The **Composite** option renders the text directly onto the input image. The **Matte** option produces a matte image which can be used for compositing. Bug 50774

#### Updated Gallery View

* Some the Shots View functionality has now been integrated into Galleries, allowing them to be sorted, searched and filtered.
* Additional metadata is now captured at grab time:
  * Shots View Metadata
  * Grab Date and Time
  * Grab User
  * Grab Source
  * Grabbed Record Timecode
* Sorting is available via the **Sort** menu within Gallery View and contains the following options:
  * Storyboard - this matches the behaviour of previous versions of Baselight, allowing gallery grabs to be reordered by drag-and-drop.
  * Tape + Source TC (C Mode) sort
  * Sort by any available metadata
  * Change sort order
  * Apply a secondary sort
* Galleries can be searched using a new **Search** button within Gallery View which displays a text edit field for searching the current Gallery. By default this searches within comment, but it can be changed to search within tape or clip names.
* Users can now create and store complex filters that persist between Galleries and are available via a drop-down menu. By default this menu contains the option to display all shots, or Gallery Quick Slots as well as options to create, edit, or remove filters. Choosing to create a new filter shows a modal dialog where filters are defined in the same manner as Shots View. The dialog requires a filter name that will be added to the list of filters. Available filters can be cycled using the '+' and '-' keys on a Blackboard or Slate in Gallery keypad mode.
* Galleries can now be viewed as a list like in Shots View, with columns displaying all available metadata.
* Galleries now display a scroll bar as well as information on how many events are currently shown.
* Added ability to export BLGs or CDLs directly from the current Gallery Scene. Bug 51442
* Control-clicking a Gallery thumbnail will now jump to the grabbed record timecode in the current scene. The modifier for this can be changed via the 'Navigation' submenu. Jumping to the grabbed record timecode can also be achieved by right-clicking a Gallery thumbnail.
* Added 'View', 'Gallery', and 'Recall' as available default keypad modes for the Blackboard or Slate.
* Grabbing multiple shots to the Gallery can now be cancelled.
* Grabbing multiple shots to the Gallery can now be undone in one go. Bug 62925

#### Multi-Paste

* Multi-Paste supports shots which span multiple timeline tracks. When multi-pasting, the new **Maintain Tracks** option determines whether the tracks of source shot strips are maintained in the destination or whether they are pasted into the destination top strip's track. Bug 53121
* When multi-pasting from multiple scenes, Multi-Paste will now stop with a more informative error message if any of the source scenes can't be opened (previously it would simply skip over unopenable scenes). Bug 66110

#### Colour Science

*   **Truelight CAM v3**

    Added a new version of Truelight CAM DRT family, called "Truelight CAM v3". This makes the first two versions of Truelight CAM obsolete.

    Changes since Truelight CAM v2:

    * Better shadows details
    * Highlight bleach is less intense
    * Highlights between SDR and HDR look more similar
    * Improved inverse transform
    * The ARRI, Academy and RED scene looks have been modified to work with Truelight CAM v3. The matching target for these new scene looks is between SDR and HDR at 200 nits - this produces a more balanced match between SDR and HDR. Bug 59379
* Added ARRI-2022 scene look (based on ARRI REVEAL DRT) for Truelight CAM v3. The matching target for the new scene looks is between SDR and HDR at 200 nits, this produces a more balanced match between SDR and HDR. Bug 63398
*   **Chromatic Adaptation Transforms**

    A Chromatic Adaptation Transform (CAT) is used when converting images between colour spaces. It converts the white point of one colour space to another, e.g, from D65 to D60.

    In Baselight 5.3, a fixed CAT was used (XYZ Scaling), but workflows like ACES specify different CATs which produce slightly different colours; the resulting errors are small but could flag issues in QC.

    In Baselight 6.0, a new Chromatic Adaptation Transform option (in the advanced section of the Format & Colour tab on Scene Settings View) allows the CAT to be set for all colour space conversions in the scene (except the mastering white point shift, see below).

    The CAT options are:

    * ACES Workflow (Dynamic)
    * Bradford
    * CIECAT02
    * von Kries
    * XYZ (Legacy)

    Bradford, CIECAT02, von Kries and XYZ describe the colour space used for the chromatic adaptation. The ACES Workflow setting dynamically switches between Bradford and CIECAT02 depending on the colour spaces being converted, to match the ACES specification.

    The CAT used for each conversion is shown in Colour Space Journey View.

    For the Mastering White Point colour shift, Baselight uses a different CAT, scaling in the Mastering Colour Space, to prevent colours from being moved out of the mastering gamut by a white point shift. Bug 56121
*   **New Colour Spaces**

    Added "FilmLight: Linear / EGamut 2" and "FilmLight: TLog / EGamut 2" colour spaces. EGamut 2 is changed slightly to include modern camera colour spaces. There is no noticeable difference from a colour grading perspective. Bug 66101
* Added "Apple: Apple Log / Rec.2020" colour space. Bug 65637

#### Dolby Vision

*   Dolby Vision Content Mapping v5.2 features are now supported in scenes using "Internal CMU (v4)" content mapping.

    **Analysis Tuning**

    In the Dolby Vision section in Scene Settings View, the **Analysis Tuning** control adjusts the spatial filtering used by Dolby Vision analysis. This can be used to reduce the impact of specular highlights, noise, compression and digital artifacts. Note that this control only affects subsequent analysis operations; it has no effect on analysis that has already been performed.

    **Long Play Analysis Usage**

    In Dolby Vision Analysis operators which have been analysed in a Baselight release supporting this functionality, the **Analysis Usage Mode** control can be set to **Long Play** to allow the image analysis values to vary across the duration of the operator. This can give better results when a single shot has a large change in lighting, or when using a single Dolby Vision Analysis strip under multiple shots. Bug 64588
* Colour space menus now show Dolby's names for Dolby Vision mastering and target displays, rather than the names of the corresponding colour spaces. Bug 65979

#### Contrast-aware Image Transform Settings

* When HDR images with sharp features are resized in a linear colour space, artefacts can result in several of the image transform modes. A new **Linearised (contrast-aware)** Colour Treatment option reveals a **Local Contrast Damping** slider that reduces or removes these artefacts. This option is shown on Scene Settings View, the Image Transform Settings operator and the Setups editor. Bug 43838

#### 'Explicit Strip' Reference Strip Mode

* Added a new mode for selecting an explicit, upstream strip in the stack to reference. Once enabled, the 'Pick Strip' button allows picking of a strip to use/reference directly from the timeline (strips unavailable to reference from the Reference strip will be greyed out). Bug 51119

#### Loupe Tool

* The Loupe Tool provides a convenient means of zooming in for fine control when doing precision operations such as editing shapes. Dragging with the loupe is 'geared' to make it easier to make precise adjustments. Bug 51930
* The loupe is activated/deactivated with the keyboard shortcut `Win+Esc` (`Control+Esc` on Mac) while the mouse is the image window; certain tools have an "Auto Loupe" button to allow the loupe to turn on automatically for that tool.
* The level of zoom can be adjusted with the mouse scroll wheel.
* Loupe settings are accessible from the Display menu. **Centred** means that the loupe will be centred over your mouse, whereas **Offset** means the loupe will be offset so that it doesn't overlap with the mouse position.
* The Loupe is currently only available with the 1x1 Layout; this limitation will be removed in a future release.

#### SDK Updates

* Added support for reading Nikon RAW (.NEV) media. Bug 60943
* Updated to Sony SMDK Toolkit version 4.23. Bug 64622
* Updated to Canon RAW SDK 2.8. This adds support for newer cameras, and now uses CUDA on Linux and Metal on macOS for increased performance. Bug 61196
* Updated to Blackmagic RAW SDK 3.5. This adds support for media from:
  * Blackmagic Cinema Camera 6K, URSA Mini Pro 12K OLPF and Micro Studio Camera 4K G2
  * Fujifilm X-H2, X-T5, X-S20 and GFX100 II
  * Panasonic LUMIX S5II, S5IIX and GH6
  * ZCam E2, E2-M4, E2-S6, and E2-F6. Bug 63775
* Updated the Comprimato SDK used for GPU JPEG 2000 acceleration to version 2.8.1. This adds support for NVIDIA Ada GPUs. Bug 65980
* The old v5 ARRIRAW decoding SDK is no longer available except for very old media and media inserted in older builds. Note that the v5 SDK remains unavailable on Apple Silicon systems. Bug 66334
* Updated to DNx SDK 2.7.5. This fixes some internal behaviours. Bug 66465

#### Volume Indexing

*   In Baselight 6.0 and future releases, volume indexing is out of beta and is automatically enabled on Linux Baselight systems.

    "Indexing" is the action of reading and storing the metadata for a volume.

    The index service will automatically extract metadata from the movies and sequences on the local '/vol/images' volume and store them in a PostgreSQL database.

    The database is kept up to date to match the contents of the volume.

    This can improve the speed of existing operations, such as conform or browsing for media, and it can enable otherwise impractical operations such as finding all media of a particular encoding, or by a particular director, or over a certain length etc.

    The first time that the index service starts after installation it will run in the background and take some time to fully populate the index database with the metadata of the volume contents.

    When a volume index is available it will be visible in FLUX Manage, indicated by a white star next to the volume selector.

    A white star indicates an index is available and being used, whereas an orange outline indicates an index is available but not being used, either because the user has chosen not to use it, or because it is not fully available due to indexing not being complete.

    In FLUX Manage and Conform View, clicking on the star icon next to the path in the interface will allow selective use of the index. Disabling the index allows the user to read metadata directly from the raw media.
*   **Examining a Volume Index Using the Command Line**

    To check the status of volume indexes use the `fl-lsvol` command - this will display all available volumes and indicate if an index is available on a volume, as well as the status of the index.

    ```
    > fl-lsvol
    /vol/bl1234-images
    /vol/bl1119-images    [Indexed]
    ```

    From the command line, the `fsdb-ls` command is a useful tool to list the contents of directories. If an index is configured `fsdb-ls` will automatically use it.

    However, should you wish to ignore the index and scan the filesystem directly, you can override this behaviour using the 'server' option:

    ```
    > fsdb-ls --server <indexed|regular>
    ```

    For example to summarise all sequences using the index:

    ```
    > fsdb-ls -R --server indexed /vol/images
    ```

    To summarise all sequences by not using the index (i.e by scanning the filesystem - this will take a **lot** longer):

    ```
    > fsdb-ls -R --server regular /vol/images
    ```

    The `fl-lsvol` command will also show an indicator of the current state of the index:

    ```
    > fl-lsvol
    /vol/ghibli-images  "QC - Ghibli Baselight TWO"  [Indexed]
    ```

    Further information is available in the User Guide.
*   **Disabling the index service**

    In previous releases, the index service needed to be explicitly enabled for a volume. In Baselight 6.0 and future releases it is automatically enabled. It can however be explicitly disabled if required.

    This requires an additional 'limit' line in the configuration file 'volume.conf' like so:

    ```
    zone mybaselight
    dir images /mnt/disk1/images1
    label images "Demo Room"
    limit images index=0
    ```

    The service will need to be restarted to accept this change.

    If your system is a Baselight TWO, login to the master node, e.g.:

    ```
    > ssh filmlight@n0
    > sudo fl-service restart index
    ```

#### Miscellaneous

* Added support for macOS 14 Sonoma; the minimum supported version is now macOS 12 Monterey. Bug 65665
* Operator image overlays now update/draw in sync with the images themselves when scrubbing through the timeline. Bug 61376
* Added ACES Reference Gamut Compression to the Compress Gamut operator. Compress Gamut now has three operation types: FilmLight, ACES Reference and ACES Variable. Bug 58234
* Added support for a new "ab" chromaticity mode in Scope - Vectorscope/Chromaticity View. This new method will plot the image point cloud and all loci in the chroma plane of Eab - a new opponent colour space developed by FilmLight. Eab will present colour distances in a perceptually uniform way (large-step colour uniformity) in all areas of the colour space. Because of this perceptual uniformity, RGB gamuts are no longer triangle shaped. Bug 58292
* Legacy DNxHD codecs are now hidden in Render View Codec menu unless `Shift` is pressed. Bug 60557
* The Radius sliders in the Blur operator and in the Blur and In/Out Blur stages of the Matte Tool operator are now non-linear. This makes it easier to set smaller radii using the sliders. Bug 35919
* Mute Audio keyboard shortcut has been changed from `Control+Shift+M` to `Alt+M` to prevent overlaps with Mark insertion keybindings when Edit Mode is on. Bug 64008
* Added an option to set the Blank colour to black, 18% grey and white based on the colour space set in the operator. Bug 63951
* CLF files that use the "ACES2065-1" colour space now correctly set the ACES: Linear / AP0 colour space into a LUT operator. Bug 64412
* Added FLUX Manage filter tile for "Is RGBA" to select media that has 4 channels. Bug 64526
* When inserted, the Blank operator now generates black in the working colour space. Bug 64080
* OFX plugins must now use the new Draw Suite for drawing overlays. Bug 62260
* Viewing or scrubbing a thumbnail in the gallery will now always use the viewing colour space from the current cursor. Bug 62759
* Added icon to shot strips to indicate they contain client notes (and changed frame client note markers to use the same icon). \[Bug 62278]
* Added a horizontal cursor line displayed at the bottom of thumbnails in Cuts View. Bug 53689
* The keyboard accelerator for increase/lower proxy resolution is now `Shift+Ctrl/Cmd+Minus/Equals`, allowing the simpler `Ctrl/Cmd+Minus/Equals` to be used for Timeline Zoom In/Out. Bug 65149
* Scene Settings now has an option to clamp images to \[0,1] before applying an inverse DRT. This can fix issues with display-referred media, for example caused by unpremultiply or Legal to Full scaling. A new option on the Sequence operator allows separate control of clamping when a DRT override is chosen. Bug 63701 Bug 66259
* Added category selection to the 'Prompt For Note And Category' dialog when adding Marks. Bug 59360
* Added `Win+Shift+M` (`Control+Shift+M` on Mac) keyboard shortcut to show/hide Marks And Client Events view. Bug 59360
* The "Zones" diagnostic now checks whether every system in the cloud has the same setting for its global preferences database, and that the 'filmlight' user has the same UID. Bug 65471
* Added a help window for Numbering Expressions in Render View. Bug 65498
* Submitting a render to a remote system now warns if there is nothing running on that system which will process the render (i.e. Baselight/Daylight/bl-render or, on a FLUX Store or Baselight RENDER system, the render service). Bug 65311
* Added tooltips to help buttons in Render View. Bug 65589
* Blend strips and Layer strips in composite mode now show the blend mode in the strip name. Bug 64457
* Added 180 degree Lat-Long support to the Panorama operator. Bug 65552
* In the Panorama operator's "Camera Control" mode, `Alt`+left mouse button can now used to pan the image, whilst `Ctrl+Alt`+left mouse (`Cmd+Alt`+left mouse on Mac) can be used to change the field of view. Bug 65552
* On macOS, several utility applications are now located in Utilities/Tools rather than alongside the Baselight application itself. Bug 61795
* In order to prevent accidental reduction of image quality due to upscaling, strip caching is now ignored when the Viewing Format or Rendering Format has a mapping from the Working Format which causes a scale-up. When this is detected, strip caching is ignored, and the cache button at the top of Parameter View and the cache icons on Timeline View are shown in orange. This behaviour can be disabled in Scene Settings View if necessary. Bug 53184
* "Texture Filename" metadata is now shown for ARRIRAW media. Bug 66628
* An NVMe raid based on Xinnor xiRAID is now supported. Bug 66049
* Reduced coloured artefacts in highlights of DNG media sequences. A new Highlight Filtering control on the DNG Params operator allows this filtering to be adjusted. Bug 66149
* Added "FilmLight: Linear / EGamut 2" and "FilmLight: TLog / EGamut 2" colour spaces. EGamut 2 is changed slightly to include modern camera colour spaces. There is no noticeable difference from a colour grading perspective. Bug 66101
* Added support for subrip (.srt) and Avid subcap (.txt) subtitle formats. Bug 62374
* Improved conversion from subtitle timecode to corresponding frame number. Bug 66729
* Gallery scene names now always have a suffix representing their version number (e.g. "\_v6") added to the end of the name. When a version 6.0 gallery scene was created by automatically copying a gallery scene from an earlier version of Baselight, that original gallery will remain, allowing easy switching between Baselight builds with different version numbers. Bug 66767
* OpenEXR renders from RED media now include `lens_cooke_i_dynamic` and `lens_cooke_i_static` metadata. Bug 66773
* Added support to conform using clip name in a CMX EDL, the EDL must contain `* FROM CLIP NAME:` or `*FROM CLIP NAME:` entries for events to enable the option in the Match Events By selection menu. Bug 64579
* The scene's working frame rate is now shown in the scene name drop-down menu. Bug 57284
* Apple ProRes and many other movie files are now read considerably faster than in previous builds. This can enable additional media to play at rate without caching. Bug 64439
* When conforming from the timeline add "Clip Name In Path Or Filename" to the Match Events By list if clip names are present. The `bl-conform --Filter` option now includes ClipName. Bug 57729
* Additional metadata is now read from PNG image files. Bug 65131
* Automatic white point adjustments made by Sequence operators when converting between the Input and Stack colour spaces are now shown on Colour Space Journey View. Bug 64683
* Added an option 'Apply Input Format Mapping' when conforming FCP/XMLs with Image Transforms. When set to yes, if the resolution and pixel aspect ratio of the working and input formats do not match, the transform is adjusted to compensate for the difference. Bug 64760
* Updated Photon to version 4.9.4. This can detect additional issues in rendered IMF packages. Bug 65555
* Added support for reading IPCM audio in QuickTime and MP4 files. Bug 65581
* Added command line tool for mapping the Blackboard Classic Wacom tablet. Bug 57119
* When performing an Update Avid AAF with Baselight grades a warning is now shown if no grades are exported. Bug 65686
* Added an option to export v5 Dolby Vision Metadata when rendering HDR IMF packages and Dolby Vision Mezzanine MXF files. Bug 60060
* Added `%u` or `%{ShotStartTimelineTimecode}` as a render filename template substitution which is the timeline (rec) timecode of the start of the current shot, as a number. Bug 65762
* The Working Format is now shown at the top of the list when creating a new format mapping. Bug 65896
* DRTs which are implemented using CLFs are now supported. Please contact `baselight-support@filmlight.ltd.uk` for more information. Bug 65098

### Bug Fixes Since Version 5

* Newly-inserted Blend operators using Linearised Colour Treatment now correctly use the colour space of their input, not the Working Colour Space. Bug 55995
* Fixed rare crash in Curve Grade where the working colourspace was indeterminate. Bug 56815
* Fixed issue preventing render of Dolby Atmos and Dolby Vision Mezzanine MXFs. This also fixes an issue where created movies could have the wrong permissions. Bug 64109
* Fixed rare crash with group grading inside a layer. Bug 64295
* Newly-inserted Blend operators using Linearised Colour Treatment now correctly use the colour space of their input, not the Working Colour Space. Bug 55995
* Fixed a potential scene loading error in DSpot and Switch Dust strips. Bug 64125
* Fixed crash pasting onto a Shader layer. Bug 64099
* Fixed crash on exit when cursor on image display. Bug 64030
* Fixed error messages for misconfigured Scratchpad. Bug 64131
* All strips with a missing reference input are now indicated by a red X on the strip. Bug 64600
* Fixed issue with pasting to a stack with protected mattes. Bug 63901
* Fixed an issue where applying a grade would sometimes shift strips upwards. Bug 63902
* Improved behaviour of sliders and desk controls in the (standalone) Blur and In/Out Blur tools. Bug 64628
* Improved trackball behaviour when adjusting parameters with non linear response curves. Bug 64679
* Viewing or scrubbing a thumbnail in the gallery will now always use the viewing colour space from the current cursor. Bug 62759
* Displaying a bypassed stack in Layer View no longer covers the scroll bar. Bug 64231
* Increased the size of the 'gang' icon and added a splitter bar to Hue Shift to separate Hue Controls from Saturation/Value controls. Bug 64229
* Fixed image issues seen with some Shader and OFX operators followed by a Transform. Bug 64386
* Fixed issue with Merge Apply with Protect Existing Destination Strips and Tracker strips causing a crash from overlapping strips. Bug 64505
* Improved trackball behaviour when adjusting parameters with non linear response curves. Bug 64679
* Fixed issue in Matte Tool where moving an encoder knob would enable the currently selected tool instead of the one linked to the encoder. Bug 64601
* Fixed sliders with non linear response curves not updating their position when extended range is toggled. Bug 64685
* Improved sensitivity of some controls in Matte Tool. Bug 64802
* Fixed crash when pressing Apply. Bug 64333
* Group grading now inserts strips in the correct track to maintain layer ordering. Bug 64672
* Improved mail queue diagnostic report for cases where there is exactly one mail message in the queue. Bug 64687
* Added reset buttons in the Blur and In/Out Blur tools. Bug 64716
* Fixed issue where renaming a stage in Matte Tool. Bug 64880
* Ensure 'New Shape' mode disabled/cancelled in a read only scene. Bug 64847
* Fixed bug where Matte Tool would not check for mismatched parameters
* before allowing its strips to be joined. Bug 64894
* Fixed a bug which could cause the keyframe bar to be empty for an operator containing keyframes. Bug 64843
* Fixed failure to render 8-bit Y'CbCrA images to JPEG 2000 Broadcast Contribution Profile YCC 422. Bug 65117
* Reduced fade in and fade out times of the Blackboard Classic. Bug 65356
* Ensure Avid (conform) categories are hidden on menus where appropriate. Bug 59360
* Fixed crash while tracking after switching scene. Bug 64864
* Added support for reading IRIDAS cubes written by the ARRI Reference Tool. Bug 66074
* Some dialogs which could become unusable if there were too many lines of text now use a scroll bar. Bug 65442
* Fixed non-standard positioning of reset and gang buttons in various tools including OFX, Matte Tool, and Blur. Bug 65449
* Made the bars between column headings more visible within tables and changed tables to always use horizontal scrolling when columns can be resized. Also fixed a regression causing column headers in the Manage Colour Spaces dialog to not be correctly aligned. Bug 65569
* Flipped bypass stripes in Layer View and Parameter View to match Timeline View's strip bypass. Bug 64557
* Fixed precision issues in the Timeline when fully zoomed-in and cursor was located several hours up the timeline. Bug 65726
* Fixed a hang caused by scrolling in Cuts View while editing the Comment (Editable) field of a thumbnail. Bug 64555
* Fixed clipped highlights in Cuts View when using BRAW media at a high ISO or exposure. Please use "bl-reset-cache -thumb" to remove incorrect thumbnails from the cache. Bug 65765
* Fixed inability to sort or reposition several columns in FLUX Manage View. Bug 65698
* When inserting the first Sequence into a scene from Conform or FLUX Manage, you are now prompted to change the scene's container and/or timeline timecode rate even when there are non-Sequence strips already in the scene. Bug 65755
* Added **Hue Safety** control in Curve Grade's customise menu for adjusting the built-in saturation modulation for adjustments based on hue. Bug 64626
* Fixed potential crash on scene close when Text operator selected. Bug 65605
* Fixed bug that prevented new layer insertion if a stack contained unresolved Reference strips. Bug 66056
* Added three additional buttons to the Tracker Desk Selection preference in Preferences -> Operators. This will allow users to map three additional trackers which will be accessible from the Blackboard/Slate. The old tracker controls will be visible on the panel when holding down Ctrl. Bug 65188
* Removed the option on macOS to use Apple ProRes compression with 10-bit Integer timeline caching. Bug 64264
* Fixed a rare issue whereby grabbing a composite grade to the Gallery could result in a render error if the media was taken offline. Bug 66063
* Fixed Multi-Paste bug which could occur when "Paste Groups" was on and the destination scene had no groups, resulting in one of the pasted groups occupying the "\\\<unsaved>" group slot and thus being liable to be overwritten. Bug 66116
* Fixed Multi-Paste bug which could occur when multiple source clips were judged as being equally likely to match a destination shot, resulting in the choice being essentially random and non-deterministic. Now, the source shot whose record time is closest to that of the destination shot is chosen. Bug 66125
* Fixed crash which could occur when closing the current scene whilst in the middle of a mouse-based editing operation. Fixed by blocking scene close in that situation. Bug 66177
* Fixed infinite scrolling which could occur when doing edit drags using the mouse on some Linux systems. This also fixed scrolling not being stopped appropriately early when scrolling to the left. Bug 65972
* Fixed scrolling in the timeline occurring when doing slip edits using the mouse. Bug 65972
* Fixed Timeline Sort to generate modern versions of Bars and Text. Bug 63936
* Fixed issue with cursor lag on SDI outputs. Bug 66241
* Fixed drag and drop from FLUX Manage to the Timeline View so that the drop zones always reflect the state of FLUX Manage's current insertion buttons. This allows it to offer "Replace", Audio and BLG insertion. Bug 63795
* Fixed an issue that caused a magenta image on the AJA Kona SDI or HDMI outputs when restarting Baselight, switching setups or running external tools such as bl-setups. Bug 66443
* Fixed crash when changing stream resolution in Client Sessions View. Bug 66170
* Fixed issues with data alignment when processing image files stored on an xfs disk with 4k logical sectors. Removed the FLIX\_AUTO\_FIX environment variable which is no longer required. Bug 4285
* Fixed missing UI in Dolby Vision Trim operator in Internal CMU (v2.9) mode. Bug 66488
* Tables now have a larger separation between columns and have better alignment. Also removed the 'Thumbnail' title text from Shots View and Gallery. Bug 65638
* Fixed background caching not triggering when changes to a strip's caching state were undone/redone. Bug 53320
* Fixed a diagnostic issue for Generation VIII systems that have a NVME boot disk. Bug 66529
* Added UI Saturation control in the Hue Angle Customise menu for adjusting the saturation of the wheel and histograms. Bug 66151
* Fixed a bug that could cause a crash exporting marks. Bug 66319
* Fixed an issue where Matte Tool panel interaction could become unresponsive when simultaneously adjusting encoders and trackballs. Bug 66360
* Fixed bug in Curve Grade where moving a single encoder quickly after another could result in 2 control points being edited simultaneously. Bug 66290
* Fixed issue with the Blackboard Classic not updating Shape Quickshape menu. Bug 65933
* Fixed potential crash when scrolling a long list by repeatedly clicking on a scrollbar. Bug 66491
* Fixed issue with keyboard focus in the Create and Edit Presets dialog. Bug 66397
* Improved conform of CMX EDLs with locator marks, allow case-insensitive colour names. Bug 66550
* Fixed memory leak when decoding ARRIRAW v7 images via CPU renderer. Bug 66420
* Fixed issue with over sensitive Wacom pen in FilmLightOS 8. Bug 66379
* Fixed crash that could occur from the Gallery when closing scenes. Bug 66499
* Fixed crash when movie decodes are continually failing. Bug 66566
* Fixed potential crash when deselecting a Curve Grade operator while simultaneously dragging a control point. Bug 20295
* Fixed crash which could sometimes occur when closing a scene whilst timeline scrolling is occurring. Bug 65663
* Fixed crash when attempting to modify some OFX parameters with explicit strip caching enabled. Bug 66600
* Fixed failure to generate FLUX Manage thumbnails for some DNxUncompressed media. Bug 66546
* Fixed crashes in Text Macros Panel. Bug 63190
* Fixed new-scene Timeline Caching setting, which has now moved from Preferences to Setups. Bug 65192
* Fixed audio error messages when using a frame increment of zero. Bug 60928
* Fixed crash in Client Sessions view when creating a new session without copying the existing stream settings to the new session. Bug 66132
* Fixed crash in Client Sessions view when creating a new session whilst an existing session is in progress. Bug 66000
* Fixed crash in Client Sessions view when the Stream Settings for a session have invalid values. Bug 64254
* The "Resend Invites" button in Client Sessions view is no longer displayed for local sessions. Bug 66160
* Fixed potential crash when removing a client from the Client Sessions View. Bug 66632
* Fixed an issue with zero-opacity shape matte. Bug 58022
* Fixed green value in chromaticities metadata when writing OpenEXR files using an EGamut colour space. Bug 65007
* Fixed a range of failures that could be caused by repeated application runs which never read any movie files, especially on a multi-GPU system. Bug 66629
* Fixed crash when resetting a Bars operator. Bug 66619
* Improved UI update speed when working with Dolby Vision. Bug 66681
* Prevented grabbing of stacks with (explicit) references to strips outside the stack to the gallery. Bug 64561
* Added a menu button to the layer list in Chromogen/Matte Tool (the older method of using right-click to bring up the menu still works as well). Bug 66620
* In Chromogen, Matte Tool and Flare, the Panel displays now show the user name for the stage rather than always showing the default stage name. Bug 66627
* Fixed an issue whereby the strip bypass button could be incorrectly disabled after inserting a matte. Bug 66425
* Fixed issue where trackers get unlinked after an Undo. Bug 66500
* Fixed missing cursor on NDI output, and improved responsiveness when picking or interacting with overlays on the NDI output. Bug 66576
* Fixed failures using Invizigrain OFX plugin at high resolution on some systems. Bug 66533
* The fragmentation diagnostic and overnight defragmentation service now ignore solid state devices. Bug 66710
* Fixed error where a CPU OFX operator could fail to render when it is in a stack beneath another CPU OFX operator which is cached. Bug 65730
* Fixed potential Blackboard 2 related crash on complex stacks. Bug 64703
* Fixed blank image when reading from some uncompressed OpenEXR files. Bug 65702
* Fixed per-frame metadata from ARRI and Sony MXF media, for example `%{Tilt}` and `%{Roll}`. Bug 65823
* Fixed an issue with the index service creating idle connections to the Postgres database. Bug 65886
* Fixed issue with XDCAM encoded MXF files rendered by the application not being readable in some third-party tools. Bug 65850
* Fixed issue where tracker keyframes could incorrectly be moved, and couldn't be deleted left/right. Bug 65993
* Fixed crash when overlapping strips were creating using Apply in merge mode. Bug 66008
* Fixed behaviour of keyframe buttons in OFX operators. Bug 66046
* Fixed a memory leak when reading XML files. Bug 63964
* Fixed "Stack output is too large" errors for example when using some OFX plugins. Bug 65681
* ARRIRAW media now uses the colour space metadata in the file to determine whether to use AWG3 or AWG4 for automatic decoding. This should reduce incidences of colour mismatches against decodes performed using other tools. Bug 66510
* Fixed behaviour of monochrome Lasergraphics DPX files. Bug 61013
* Fixed issue where trackers get unlinked after an Undo. Bug 66500
* Fixed issues with some OFX plugins in galleries. Bug 66526
* Removed edge repetition in Matchbox Shader for: CROK Beauty, CROK Fisheye, crok\_chroma\_warp, crok flicker, crok heathaze, crok kuwahara. Bug 64538
* Fixed AJA T-TAP Pro UHD RGB output. Bug 64432
* Fixed `SceneNameOnly` substitution to cope with multiple folders. Bug 64585
* Fixed crash when selecting operator in an inside outside from the desk. Bug 59151
* Fixed crash when selecting DCI 8K resolution output. Bug 59853
* Fixed crash in Paint. Bug 50465
* Improved application interactivity/performance when the Shots View is visible. Bug 64745
* Fixed crash reading 4:2:2 JPEG 2000 files with alpha. Bug 63673
* Fixed issue where DNxHD/DNxHR encoded QuickTime files rendered by the application could be incorrectly identified as interlaced instead of progressive in e.g. Clipster. Bug 65123
* Fixed crash in Frame.io package when downloading comments made by anonymous users. Bug 65351
* Fixed possible crash in Text operator loading a new font style for an existing font name. Bug 65557
* Fixed clipped highlights in Cuts View when using RED media at a high ISO or exposure. Please use `bl-reset-cache -thumb` to remove incorrect thumbnails from the cache. Bug 62978
* Fixed issue with `%{RandomUUID}` variable substitution when rendering with "Render Format: Use Input Format". Bug 65817
* Fixed naming of cropped input formats in FLUX Manage View when the crop is only in one dimension. Bug 65712
* Fixed issue with slow renders and the application becoming unresponsive when monitoring Dolby Atmos audio beyond the end of the source media. Bug 65815
* Improved speed of some renders with multiple deliverables, notably multiple audio files. Bug 65490
* Fixed clipping of OpenEXR media in gallery grab. Bug 64668
* Fixed hang when using "Prepare Noise Profile" in Neat Video when the OFX operator is in a cache strip. Bug 65752
* Fixed issue with GPU JPEG 2000 acceleration not working when decoding MXF files. Bug 65983
* Fixed issue with shot marks always applied to the bottom sequence when conforming AAFs. Bug 65975
* Fixed crash when reconfiguring NDI output device. Bug 65398
* Fixed issue that could generate corrupt files during unsuccessful MXF file trimming. Bug 66118
* Fixed crash caused by invalid Resolution setting for a stream in Client Sessions View. Bug 64254
* Fixed MXF UIDs appearing in the `bl-conform` output by default, only output with the `--verbose` option. Bug 65771
* Fixed crash when changing stream resolution in Client Sessions View. Bug 66170
* Fixed crash when applying a stack to itself when there are strips that are protected from being copied. Bug 66135
* The bitrate of DCI compliant JPEG 2000 essence has been reduced by 5% to avoid issues with older DCP players and third-party validation tools. Bug 66359
* Fixed display of custom column expression icon in Shots View. Bug 66075
* Fixed an issue that could affect Wacom pen sensitivity in FilmLightOS 8. Bug 66379
* Fixed issue when copying an input with additional operators. Bug 66684
* Fixed crash when using apply with auto selection off. Bug 58653
* Fixed a hotfix issue that could stop UI hosts from booting. Bug 66785