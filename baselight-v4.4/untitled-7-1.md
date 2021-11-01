# Baselight Release 4.4.6201 (2013-09-03)



## New Features Since Baselight 4.3.6187

### Single Stack Stereo

*   Single stack stereo is a new way of organising the timeline when dealing with stereo projects. It removes the need to have two separate stacks, one for each eye. Single stack stereo allows there to be only one stack, where each strip that needs to be different is "split", allowing changes to occur separately per eye.

    To put a scene into single stack stereo mode, use the Stereo tab on the Scene Settings View. There are four stereo modes:

    * Not Stereo
    * Left Eye on Top
    * Right Eye on Top
    *   Single Stack Stereo

        Eye on top modes allow a mixture of single stacks and split stacks,

        (still obeying the old rules for stereo). Single stack only allows

        single stacks, while still being allowed to join two different

        stacks.

    Each cursor now has an eye mode (Left or Right) in stereo scenes. This mode is displayed on the switching button in the cursor view, on the menu bar and also in the Pane Description when the mode is switched.

    An inside/outside layer or strip can be split using the "3D" button next to the bypass button. There is also an indicator of the operator's stereo status inside the grid selector and on the timeline strip. Both operators and strips can be split with the exception of a few special cases Reference and Audio.

    The Sequence can also be swapped right eye for left and vice versa, using the Swap Eyes button.

    In the Edit menu the new Combine/Separate Stereo Stacks command allows the combination or separation of the selected stacks. This can be used to batch combine a conformed scene containing two separate tracks, or to separate a stack that has become complex and needs to be processed with one stack per eye.

    Shots View now follows the cursor's active eye.

    The Gallery can now store single stacks and recall to both single stacks and dual stack stereo stacks.

### Layer Blending and Compositing

*   Every (Inside/Outside) layer in Baselight now has additional controls that allow you to easily blend the output of that layer with other layers further up the stack. You can also blend a layer's output with a different grade not currently in the stack, or even a completely different source sequence. The amount of blending to apply can be varied as well as the blend mode to use.

    The Result Blending section for each layer is located below the grade selection grid and consists of three controls:

    * A slider for adjusting the amount of blending to apply.
    * A 'Type' menu for selecting the blending operation to use.
    *   A 'Source' menu for selecting what the output of the layer is

        to be blended with.

    On a Blackboard 2 the slider is always mapped to the encoder between the centre and right trackballs. On a Blackboard 1 holding down the 'Inside/Outside' button will temporarily take over the second screen and its encoders/buttons, with the rightmost encoder mapped to the blend amount slider.

    By default, the blend type is set to 'Mix' and the source is set to 'Input Image'. This means that changing the amount slider will mix between the output of the layer and the input to that layer. This is useful for quickly de-emphasizing the grade operations within a layer without having to go through each one adjusting its parameters individually.

    The Result Blending 'Source' menu is for selecting what the output of the layer is to be blended with. It has four options available:

    Input Image - The result of the layer is blended with the input to the layer (the default).

    Raw Image - The result of the layer is blended with the raw, ungraded image at the top of the stack.

    Numbered Layer - The result of the layer is blended with another numbered layer number from further up the stack. Selecting this option adds an additional button which, when pressed, will pop up a thumbnail menu for selecting the layer to blend with.

    Second Input - Selecting this option adds a new Reference strip above the layer titled 'Blend Source'. This strip is used exclusively for blending with the layer. New grade strips may be added (or pasted) directly below this strip to create a different look not currently in the stack for blending with the layer.

    ```
                 By default, the blend source strip is a reference
                 to the raw sequence, but it can easily be swapped
                 for a different sequence to blend into the layer (a
                 texture, for example). To do this, select the blend
                 source strip and press the 'Swap For Sequence Strip'
                 button. This will bring up the Sequence Browser for
                 selecting the new sequence to blend with.
    ```

    By default, the result/output of the layer is blended with the entire blend source image. However, if the layer has a matte associated with it, the blending can be forced to occur only through the layer's matte using the 'Use Matte: For Blend' toggle button.

    On a Blackboard 2 (in standard layout) there is a dedicated 'Blend Controls' button next to the right trackball that, when pressed, latches the second screen (and its buttons/encoders) into a mode for adjusting blend paramters. In this mode the right screen's buttons can be used to select the current blend source and inside grade source (see below). Also, the rightmost encoder can be used to select the blend type. Pressing the 'Blend Controls' button again cancels the mode.

    The Blackboard 1 has similar controls, but these are only available while the 'Inside/Outside' button is held down.

    **The 'Inside Source' Menu**

    This option is only available for layers which have a matte.

    Previously in Baselight, grading stacks were typically constructed by cascading grades one layer below another. However, it is sometimes desirable to not grade over the result of the previous layer, instead choosing a layer further up the stack as a grade source. The 'Inside Source' menu is used for selecting that source.

    By default 'Inside Source' is set to 'Input Image'. This means that all the grading operators in the 'Inside' column will be applied to the input of the layer (the same source as the 'Outside' column). In this confuguration layers behave the same way they have in previous versions of Baselight.

    However, selecting one of the other menu options will change what is used as the source for the inside grade operators, effectively "punching a hole through the matte" up the stack to the layer specified.

    **The 'Layer Mode' Menu (For Grading/Compositing)**

    Layers can now be classified as either 'Inside/Outside' (grading) layers or 'Composite' layers. An Inside/Outside layer grades either an entire source image or an area of a source image specified using a matte. A compositing layer takes foreground and background images and uses a matte to replace one with the other. By default, layers are configured as Inside/Outside layers. This menu lets you quickly change this, setting up layers for a number of different compositing scenarios described below.

    Background Replacement:

    Matte From Key - This option may be used where the stack contains a sequence with areas you wish to replace with another (e.g. a classic 'sky replacement') using a keyer to isolate those areas. Selecting this option reconfigures the layer to contain a keyer and launches the Sequence Browser to select the new (background) replacement sequence. Once this is done, the keyer strip will be automatically selected, ready to pull a key on areas to be replaced in the foreground sequence.

    Matte From Shape - As above, except a Shape strip is inserted to isolate areas of the foreground to replace.

    Composite:

    Matte From - This option may be used when the stack contains Foreground Key a background sequence onto you wish to composite a different foreground sequence (e.g. a green screen sequence). Selecting this option will reconfigure the layer to contain a keyer and launch the Sequence Browser to select the foreground. Once this is done, the keyer strip will be selected ready to pick/remove transparent areas of the new foreground.

    Matte From - As above, except a Shape strip is inserted to Foreground Shape isolate areas of the foreground sequence.

    Matte From - This option may be used where the stack Foreground Alpha contains a (background) sequence on top of which you wish to composite another (foreground) sequence that has already has an emebedded alpha channel to specify areas of transparency (e.g. a TIFF title sequence). Selecting this option will reconfigure the layer and launch the Sequence Browser to select the foreground. Once this is done, a reference strip will be inserted to enusre the embedded alpha is used as a matte for the layer.

    ```
                     Note: If the foreground sequence image data has
                     already been multiplied by its alpha, ensure
                     the 'RGBA: Premultiplied' toggle button is
                     enabled in the foreground sequence strip for
                     correct results.
    ```

    Matte From - This option is only available if the top Background EXR sequence in the stack is OpenEXR. It can be Channel used when that single sequence contains multiple (image) tracks and mattes (alpha channels) for layered compositing. Selecting this option will launch a dialogue for selecting the foreground track and alpha channel from that OpenEXR. Once this is done, two reference strips will be added above the layer; one referencing the alpha channel and one referencing the track/fill.

    If there is a stack above the current stack, an additional toggle option 'Use Stack Above As Background' will be available which, if enabled, will _not_ prompt for a new foreground sequence when a compositing option is selected. Instead, the stack above will be used as the background sequence, and the current stack as the foreground.

    Once in 'Composite' mode, the layer itself has different options and behaviour from 'Inside/Outside' mode: The Inside/Outside grade columns become Foreground/Background grade columns. Additional transforms are automatically added to these columns allowing the foreground and background elements to be repositioned relative to each other. Also, the blend amount slider is replaced with a Foreground Opacity slider. There is also a toggle button (on by default) that ensures any foreground transforms applied are also applied to the layer's matte input.

    **Additional Notes**

    For options above which automatically insert a keyer, the default keyer to use can be set from the Inside/Outside's 'Customise' menu.

    Some of these options are only available if the strips above that contribute to the layer are horizontally aligned on the timeline.

    Options to toggle a layer's composite mode off/on without adjusting the stack in any other way are available from the 'Layer Mode' menu via the Shift modifier. These options should only be used if you're comfortable with manually moving/inserting strips to obtain a valid stack.

### Reference Strips

Reference strips now support more options for referencing strips from further up the stack. Also, the controls have been reorganised to simplify the options available, only presenting certain controls when appropriate.

The 'Reference' menu is always available and is used to select the type of reference the strip makes. The options available in this menu may change depending on the strip's position in the stack (for example, a reference on the foreground input of a composite layer will have more options than one used in a simple keyed grade layer).

Depending on the type of reference selected, the options on the 'Using' line will change (or the line may disappear altogether).

Some example new reference options available are:

*   The ability to reference any numbered layer above the current

    one in the stack.
*   The ability to reference tracks and channels from OpenEXR

    sequences at the top of the stack.

### Colour Spaces

*   Baselight now supports generalised colour spaces, defined by their RGB primaries and tone curve.

    Earlier versions of Baselight supported only a fixed set of "colour spaces" (Log, Linear, Video etc) which only affected the tone curve, having no defined RGB primaries. These colour spaces continue to be supported, and are now defined to use Rec.709 (sRGB) primaries.

    Colour space conversions are automatically applied where necessary.

    A Convert Colour Space strip is available to perform an explicit colour space conversion. For information on how to access this strip please contact baselight-support@filmlight.ltd.uk.

    Custom colour space definitions can be added to Baselight when required. Please contact baselight-support@filmlight.ltd.uk if you are interested in using a colour space that is not currently available in Baselight.
* Legacy (pre-Baselight 4.4) colour spaces are shown in orange and are not available in new scenes, except when using old formats which use them.
* The colour space set in a format can now be overridden in the Working Format, the cursor's Viewing Format, the Render View's Output Format and the Sequence's Input Format. This will reduce the number of formats that need to be created.
* The scene's Working Colour Space (the colour space used in a scene) can be overridden in Scene Settings. The Working Colour Space for new scenes is configured in Setups.
*   The colour space assigned to the input data of a Sequence can now be changed using a menu beside the Input Format menu:

    Automatic - For certain image formats (currently RED R3D, Sony F5/F55/F65 RAW, ALEXA ARRIRAW, DNG) Baselight can fix the Decode settings to generate image data in a known colour space, which is then converted to the output format's colour space. Some Decode settings are disabled when using this option. From Metadata - For certain image formats (e.g. ProRes QuickTimes written by an ARRI ALEXA) Baselight can guess the the correct colour space using metadata in the file. Use Input Format - The image data is converted from the input format's colour space to the output format's colour space. No Conversion - No input-to-output colour space conversion is applied. The image data is assumed to be in the output format's colour space. Named space - The image data is assumed to be in the named colour space, and is converted from that to the output format's colour space.
* A default setting has been added to the scene and setups to specify what the input space should be, either Automatic or From input format. This allows the Automatic setting to be turned off if it is not desirable.
* The colour space used by each Baselight cursor can now be changed to be different from that of the viewing format. Typical usage will be to use a display colour space (e.g. DCI X'Y'Z', P3, Rec.709 Video, sRGB).
* The default colour space for cursors can be stored with the initial cursor behaviour for the scene or job using the menu on the Cursor View.
* A display transform (such as an ACES RRT) can be set in Scene Settings. This is applied whenever the colour space changes from a scene-referred colour space to a display colour space (or vice versa). The display transform for new scenes is configured in Setups.
* The Cuts View now ignores the viewing colour space and Truelight settings of the current cursor and instead renders the thumbnails to the sRGB colour space which is suitable for UI monitors. The old behaviour can be restored using the right-click menu in the Cuts View. sRGB viewing can also be enabled for Gallery Views using the right-click menu.
* The Sequence Browser now allows colour management of the images it displays.
*   A 'Grade Result' colour space may be specified in the Scene Settings (and a default value for new scenes in Setups).

    By default, Baselight expects the output of a scene's grade stacks to be in the working colour space of the scene itself. Baselight will then apply an appropriate transform from the working colour space to the (cursor's) viewing colour space for display.

    However, it can sometimes be preferable to manually apply a grade to convert from the working colour space to the viewing colour space in the grade stacks themselves (grading the image to look 'right' on the display without explicitly specifying a viewing colour space). For this workflow, the 'Grade Result Space' option should be used to tell Baselight the colour space the scene has been graded into.

    On initial selection of a new grade result colour space Baselight will set the cursor's viewing colour space to match. As the two colour spaces are the same, no conversion is necessary and the image will not change. Once the image has then been graded into grade result space, Baselight will then correctly apply appropriate downstream conversions where necessary (when rendering out different deliverables, for example).

### Rendering

* The Render View (also used in bl-render) has been simplified so that most options are hidden until you change them.
* Multiple deliverables can now be specified and rendered together in an efficient manner. The render presets used in Baselight 4.3 are now known as "Deliverable Presets". New "Deliverable Set Presets" allow groups of deliverables to be stored and recalled as presets.
* Renders are now submitted to a queue which is processed by Baselight and bl-render. You can submit renders to any queue in your Baselight network. The queue is persistent (i.e. it retains its contents after quitting Baselight).
* Submitting a scene for rendering takes a snapshot of the scene; you can continue to edit and work on the scene while the snapshot is rendered. You can even delete the original scene.
* You can monitor the progress of renders in the queue from Baselight (in the new Queue Monitor View), from bl-render (push the Operations button at the bottom if it's not visible) or from the new standalone fl-queue application. When you're in Baselight you can jump to frames where warnings or errors occurred.
* From the queue monitor in Baselight or bl-render, you can re-open a scene, with the render settings used for a given render, by double-clicking on the entry in the operations list, or using the Open/Edit button beneath.
* A completed or failed render may be restarted using the Restart button.
* bl-render commandline does not use the render queue unless you use the new -queue option to specify a zone name.
* bl-render supports rendering on remote systems as well as on the local system; this is required for rendering on a headless FLUX Store for example.
* Quitting rendering while output movies are in progress will cause those movies to be discarded and later restarted by the next renderer which starts; you are warned about this in Baselight.
* Baselight will only process renders queued by the current user; any renders added to the queue by other users will not progress until Baselight is run as that user, or bl-render is run as any user.
* The Q menu on the Baselight menu bar allows queue rendering to be paused and resumed.
* Rendering of the queue has lower priority that background caching; you may wish to pause background caching to allow rendering to proceed.

### File Formats and Codecs

* The Decoder Pack One licence is no longer used; all the formats for which it was previously needed are now read natively in Baselight:
  * MPEG MXF, including XDCAM HD
  * AVC-Intra MXF, including Panasonic P2
  * JPEG2000 codestream (.j2c)
  * Long-GOP MPEG2 MP4 (e.g Sony F3)
  * Codex Digital JPEG2000-compressed DPX
* The Sequence operator now allows the Medium and Low resolutions of many movie decodes to be chosen for decode quality, rather than using the medium/low proxy resolution from the Input Format. Typically this will use half-resolution for Medium and quarter-resolution for Low. This is useful, for example, with R3D media which is commonly used at half-resolution for speed.
* The alpha channel of a ProRes 4:4:4:4 QuickTime movie can now be read without using a Baselight Kompressor \[bug 24154]
* Added support for reading Sony FS700 RAW files \[bug 24002]
* Rendering of H264 QuickTime movies on Linux now uses multiple threads, to greatly improve encoding speed \[bug 22425]
* Added support for reading ProRes MXF files \[bug 20476]
* Added support for images with premultiplied alpha, using the Premultiplied button on the Sequence operator.
* Added support for reading Avid IMX codec in QuickTime \[bug 23930]
* Updated to latest Sony-supplied white balance colour transforms for Sony F5 RAW and Sony F55 RAW. Note that this will result in small colour changes in this material compared with Baselight 4.3.
*   Added support for writing DCI compliant JPEG2000 files. Valid resolutions for 2K compliant files are:

    * 2048 by 1080 or less
    *   2048 or less by 1080

        Files matching these resolution criteria will be created with DCI 2K

        profile markers. Valid resolutions for 4K compliant files are:
    * 4096 by 2160 or less
    *   4096 or less by 2160

        Files matching these resolution criteria will be created with DCI 4K

        profile markers. Maximum file sizes will be determined using the

        output format frame rate and the selected bitrate.

    Three different bitrates are provided:

    *   250 Mbit/s, corresponding to the Digital Cinema System

        Specification, Version 1.2
    *   125 Mbit/s, which is half of the above rate to be used for left or

        right eye stereoscopic sequences
    *   500 Mbit/s, corresponding to the High Frame Rates Digital Cinema

        Recommended Practice

    The output colour space must be set to DCI X'Y'Z' for the produced files to be DCI compliant.
* Added support for writing DCI compliant JPEG2000 files at resolutions 2048x1080 and 4096x2160. The output colour space must be set to DCI X'Y'Z' for the produced files to be DCI compliant.
* Added support for reading ARRIRAW Black+White files \[bug 24777]
*   Updated to RED SDK v4.4, RED Rocket driver v1.4.33.0 and RED Rocket firmware v1.1.17.3.

    This adds:

    *   Support for the Mysterium-X Monochrome sensor in the Epic-M

        Monochrome and Epic-X Monochrome cameras (only with RED Rocket

        disabled at this time)
    * DRX is now available on the RED Rocket
    * Additional metadata support, including user-defined metadata

    Users of RED Rocket cards installed in Baselight Linux systems will need to update the RED Rocket card's firmware using the rocketup\_1.1.17.3 utility included with Baselight. Ensure that all systems hosting the RED Rocket cards are shut down and restarted after updating the firmware.

    Users of RED Rocket cards installed in Baselight Kompressor systems will need to:

    1. update the Rocket driver using the installer package REDrocket\_Driver\_OSX\_v1.4.32.0.pkg that can be found in the /Applications/Baselight/Current/Utilities/Resources/etc folder.
    2. update the RED Rocket card's firmware using the rocketup\_1.1.16.11 utility included with Baselight (be aware that a bug in this utility causes it to report the wrong version number while it is running; do not be alarmed by this).

    Ensure the Kompressor is shut down and restarted after updating the firmware.
* ProRes QuickTime movies read by Baselight now produce full-range data (in Baselight 4.3 and earlier they produced legal-range data) \[bug 24939]
* Added support for reading AVC-Intra (non-avc1) QuickTime movies on Linux \[bug 23928]
* The QuickTime ProRes codecs now expect to be given full-range images (in Baselight 4.3 and earlier they expected legal-range data). You should ensure this by using either a full-range Output Colour Space (such as Rec.709 Video) or the Legal to Full Scale Video LUT. The Render View will warn if it appears you are using inappropriate settings \[bug 24939]

### Disparity Histogram

*   There is a new view called disparity histogram. It shows you your disparity/depth distribution in your stereo scene. Only works with stereo scenes. Disparity histogram is useful for stereoscopic QC or in general for verifying your depth budget.

    The scene setting allows you now to specify a so called "comfort zone" which corresponds to the disparity zone that is usually associated to a pleasant stereo viewing experience. The zone range is specified in percentage of scene format width and is displayed in the histogram by two dotted red lines.

    The disparity values in the histogram are in cinema space.

    The histogram allows two different sampling methods:

    Regular = samples are taking on a regular grid and the grid size is specified by the sampling rate the lower the rate the tighter the grid.

    Edge based = Sample points are taken on image edges that have been detected using an edge filter. Image edges usually correspond to sample points with very high confidence.

    The confidence of the overall result is encoded in the colour of the graph. A white graph means high confidence (>70%), yellow graph means medium confidence (>= 20% < 70%) and finally a red graph means low confidence (<20%).

    If the graph is red it can be a indication there is a problem in your stereo setup potentially a large vertical misallignment or timing mismatch between the two eyes.

### Stereo Colour Matching

*   Added Stereo Colour Matching operator. It is accessible either from the 'Insert' menu or from Inside/Outside.

    It corrects colours locally on one eye, by taking from the other one in order to minimize the colour differences between the stereo pair. Only works with stereo scenes. It can correct the colour on the left eye, the right eye or using a second image input for the Dual Stack mode. It uses the following parameters:

    * Quality: Specifies the amount of processing. Increasing the quality will increase both the precision and the processing time.
    * Correction Type: Determines the desired treatment localness. It can be set to Localized, Intermediate or Global.
    * Border: This option applies a specific treatment on the image boundaries. It allows to exclude problematic regions on the boundaries where occlusions can append. The chosen region is represented by a red rectangle, which can be specified using the mouse, or can be set up to one of the default settings. (Default or Current Cursor Mapping).

### StereoGrade

*   StereoGrade blackboard controls have been reworked to allow an easier and more streamlined control on the floating window. Users no longer have to be aware on which eye they are currently located on as the trackball controls adapt automatically to the selected eye and therefore always act the same way.

    New blackboard trackball behaviour is as follows:

    ```
    Left Trackball Y-Axis moving downwards will pull left floating
                   window towards the viewer
    Left Trackball Y-Axis moving upwards will push left floating
                   window away from the viewer

    Middle Trackball Y-Axis moving downards will increase the
                     convergence pulling the scene towards the
                     viewer
    Middle Trackball Y-Axis moving upwards will decrease the
                     convergence pushing the scene away from
                     the viewer

    Right Trackball Y-Axis moving downwards will pull right floating
                   window towards the viewer
    Right Trackball Y-Axis moving upwards will push right floating
                   window away from the viewer
    ```
* Automatic floating window adjustment when changing convergence can be switched on/off
* Convergence can now applied to only a single eye if desired (hero eye mode)
* Pick mode now reflects the correct internal state of the strip
* Added additional blackboard control surface buttons to increase/decrease left/right floating window by one pixel
* Added the ability to soften the floating window edge
* Added ability to change the sensitivity of the blackboard trackballs
* Have a quick small/medium/large floating window preset for left/right floating windows
* Added numerical keypad for grading support: KeyPad-NumLock Decrease left floating window by 1 pixel KeyPad-Home Increase left floating window by 1 pixel KeyPad-Left Reset left floating window KeyPad-/ Decrease convergence KeyPad-Up Increase convergence KeyPad-5 Reset convergence KeyPad-\* Decrease right floating window by 1 pixel KeyPad-PgUp Increase right floating window by 1 pixel KeyPad-Right Reset right floating window KeyPad-End Set preset small left/right window KeyPad-Down Set preset medium left/right window KeyPad-PgDown Set preset large left/right window KeyPad-Insert Toggle between left/right window

### Miscellaneous

* Baselight no longer supports 32-bit operating systems.
* Added support for redesigned hardware encoders between trackballs on newer revision Blackboard 2 desks.
* Added "Magnify Values At Wheel Centre" option to "Customise" menu of video and film grade operators. When enabled, small offsets at the centre of the colour wheel are magnified, making it easier to spot grade changes when quickly navigating the timetime.
* Proxy containers can now be seen on Scene Settings without having to change a preference \[bug 23109]
* Added new Baselight formats for ARRI ALEXA, for ARRIRAW and ProRes material \[bug 23536]
* Added 1.5x speed to Play Controls \[bug 22846]
* Baselight now attempts to create PostgreSQL database users where necessary.
* Added a Bypass button to the inside/outside to allowing individual operators to be bypassed. There are also controls on the Blackboard and Blackboard 2.
* Background caching can now be paused/resumed by clicking on the progress spinner in the timeline (or menu bar) \[bug 20643]
* Added Tangent and Euphonix desk support to StereoGrade and Stereo Fix \[bug 24346]
* Added Chalk action for Align Timeline Vertically command \[bug 24168]
* Added Video LUT "Full to Legal Scale (Unclipped)" option for rendering to a legal-range output but without clipping the scaled pixel colour values to legal range \[bug 24944]
* Added Y vs Y (luma) curve to curve grade. This curve works in YCC colour space downstream of all the other curves. Unlike the RGB master curve, it allows you to make luminance changes to an image without affecting the saturation/colour balance \[bug 25048]
* Added 2 new control groups to FilmGrade for bumping overall contrast and overall saturation \[bug 24380]
* For the initial release of Baselight 4.4, we have disabled the "Update FCP XML with Baselight grades" and the "Update Avid AAF with Baselight grades" EDL Export options. This is simply because the release of the 4.4 release of the Baselight Editions for FCP7 and Avid Media Composer/Symphony will slightly lag the 4.4 release of full Baselight. These options will be restored once the 4.4 versions of the Editions are restored.
* In EDL Import, when the Time Type is "Source", a new option appears: "Source, as frame number relative to matching sequence/movie start", with possible values of "No", "Yes", and "". This conform option is useful when your EDL's frame numbers or timecodes represent an offset into a sequence or movie, rather than an absolute frame number or timecode. This often occurs in workflows where editorial are liasing with VFX vendors, who often re-number sequences and lose metadata. When your source times are timecodes, the timecode hour the start timecode hour is treated as 0, where as the ending timecode hour is reduced by the same amount.

## Bug Fixes Since Baselight 4.3.6187

* Baselight would occasionally freeze on older Supermicro H8QM3 systems. This release adjusts the MTRR register on such systems to avoid the freeze \[bug 24723]
* Fixed small colour shift in QuickTime movies using ProRes and some other codecs, when read or written on Mac OS X (e.g. via a Baselight Kompressor) \[bug 22366]
* Fixed crash reading some JPEG2000 DPX files \[bug 18277]
* Fixed error handling of damaged frames in H264 and MPEG QuickTime movies on Linux \[bug 22086]
* Fixed issue where some Blackboard 2 ONE buttons were labeled incorrectly \[bug 23708]
* Fixed failure to read remote images containing '@' in the filename \[bug 23140]
* Format mappings that only apply a fixed-pixel crop or translation (with no scaling, and no sub-pixel translation) no longer cause an image transform to be applied \[bug 21304]
* "option kompressor" in cloud.cfg now correctly sets the current zone to use no Kompressor \[bug 22798]
* Encoder readout values on Blackboard 2 now display same number of decimal places for negative values, and added +/- signs when value could be above or below zero \[bug 23869]
* Support for QuickTime movies with edits described by edts-atoms has been improved on Linux. Video offset and trimming are now handled, and support for audio offset has been added for movies with single track audio. Apparent length and frame rate of affected movies will change to better match QuickTime on Mac \[bug 22276]
* The handling of QuickTime movies with variable frame duration has changed to avoid frame repetition and skipping where possible. For movies with significant speed changes, e.g. those shot by mobile phones, an option to read the movie in 'frame by frame' mode will now appear in the sequence panel. This change can alter the frames displayed and affect the apparent length and frame rate of movies with variable frame duration \[bug 21844]
* Image files whose filenames contain the } character can now be copied using flux and fl-cp \[bug 23908]
* Hidden formats are no longer shown in the Mappings section of the formats editor unless Show Hidden is enabled \[bug 23933]
* Changing the screen layout while running Baselight or any related application no longer causes a crash on Mac OS X 10.7 Lion or later \[bug 23935]
* Encoding QuickTime movies on Linux using Motion JPEG A codec no longer squeezes progressive material into the top half of the frame \[bug 22351]
* Multipaste now retains the explicit caching setting of any strips copied \[bug 22667]
* Fixed bug which prevented toggling of strip caching/bypassing when more than one strip selected \[bug 22667]
* Fix for crash when selecting "Control Raw Video I/O" via Machine Control icon when Tangent Element/Wave desk is attached \[bug 24079]
* Removed 10 Area Track limitation per strip \[bug 22974]
* Changed the Area Track overlay's behaviour. Holding 'Ctrl' or 'Shift' allows to select the dotted rectangle using the mouse when this one is behind the plain rectangle. The rectangle selection using the mouse is now only performed from its edges \[bug 21632]
* Increase maximum number of disk cache entries \[bug 22239]
* Removed various engineering debug preferences \[bug 22640]
* Fixed width of codec parameters dialogs \[bug 24224]
* Cuts View now updates when formats are edited \[bug 11693]
* Fixed Blackboard 1 desk functionality where strip marks of different categories can be toggled by holding Mark button and using numeric keypad buttons specified in preferences panel \[bug 22772]
* Fixed crash which could occur if the trackballs were nudged while moving strips \[bug 20532]
* Fix for issue where prolonged usage of Tangent Element or Wave desks could lead to out of memory errors \[bug 24426]
* 8-bit PNG images are no longer converted to 16-bit when copied using fl-cp or flux.
* Fixed image corruption which occured when transforming a Northlight Alpha Channel \[bug 24509]
* Fixed potential crash when moving strips immediately after deleting a layer from the Blackboard \[bug 24523]
* Enabled 'Remote Conform' to be the default mode of operation for conform, ensuring less memory use on the host \[bug 10869]
* Fixed reading RMD files with unusual HDR data \[bug 24586]
* Improved speed of copying movie files onto a Baselight FOUR/EIGHT.
* Fixed stereo display of blanks on multinode systems \[bug 24778]
* Older Phantom Cine files which have no colour matrix stored in the file now have the camera's default colour matrix applied, which should bring them to Rec.709 primaries \[bug 24345]
* Fixed crash opening Spirit view when system has a Blackboard ONE or Blackboard TWO control surface \[bug 24003]
* Fixed render failure with error "Insufficient tiles to complete render" \[bug 24895]
* Fixed crash which could occur when rendering QuickTimes on Linux using the ffmpeg\_mpg4 codec \[bug 17089]
* R3D decode parameters are no longer shown on Sequence parameters in scenes that were created in Baselight 4.1 \[bug 24958]
* Fixed bug which could cause a crash when disabling scratchpad "Show Versions" mode if simultaneously moving a trackball \[bug 24176]
* Fix for slider bars for Hue Angle and Six Vector appearing at the wrong size on Blackboard 1 & 2 rear screens \[bug 24952]
* Fixed crash when verifying or performing an AAF relink following a render \[bug 23534]
* Added %L for strip name as an option for file names when generating LUTs from grades \[bug 22139]
* Ensured bl-render and the render view within Baselight always check for updated Truelight profiles or cubes when submitting a render \[bug 22780]
* Fixed occasional crash on exit \[bug 20972]
* EDL conform now warns when media is ignored because there are no formats for its resolution \[bug 24996]
* Reduced memory usage when generating proxies from the Job Manager \[bug 19661]
* Improved speed of caching when playing short sequences \[bug 24577]
* The psql utility bundled with Baselight now includes readline support \[bug 21695]
* The system precompiles shaders via a background service to avoid a delay in the first start of Baselight after installation \[bug 25066]
* Fixed bug which would stop grouped grading from working if the cursor was parked past the end of the currently selected parameter strip \[bug 25115]
* Fixed a problem on the pre-render service on OS X that would create too many log files \[bug 25060]
* Fixed timecode reported from QuickTime movies which claim to have 60fps drop-frame timecode \[bug 25133]
* Changing the name or length of a strip no longer forces the strip's frames to be re-cached \[bug 23182]
* OpenEXR images are defragmented as sequences; previously they were treated as individual files \[bug 22870]
* flood filesystem driver uses no more than 1/8 of physical memory (and at most 2GB) for its internal buffers \[bug 21526]
* Fixed gallery grab of sequences using custom Track settings, notably BLG files inserted onto the timeline \[bug 25018]
* fldm (X window manager) recognises FLUX Store and starts X without a connected display \[bug 23709]
* Fix xfs attribute maintenance \[bug 25219]
* Fix issue with copying tracking data between two shapes \[bug 25251]
* Fixed crash issue with colour space parser \[bug 25426]
