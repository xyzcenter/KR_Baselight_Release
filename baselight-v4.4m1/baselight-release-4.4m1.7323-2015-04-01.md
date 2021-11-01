# Baselight Release 4.4m1.7323 (2015-04-01)



## New Features Since Baselight 4.4.7317

*   **Formats**

    Formats have been significantly changed in this release.

    Formats no longer hold colour space, frame rate, field order, black/white points or black/white alarm points; they are purely the resolution of an image, with a set of masks and burnins.

    Colour space, frame rate and field order information is set elsewhere in the scene where it is required.

    Many formats were only necessary to bring in sequences and movies at a range of frame rates or colour spaces. These formats are no longer required since the frame rate and colour space are no longer in the formats.

    **Basic Formats**

    There is no longer a need to create a new format for each size of material; conform and the Sequence Browser will automatically make a Basic Format (with a choice of square or 2:1 anamorphic pixels) which can be used as the input format for a Sequence.

    **Automatic mappings**

    Where no mapping is defined between a pair of formats, the automatic mapping (which used to be 1:1 at top-left) now fits the width of the source image to the width of the destination format. This makes Basic Formats suitable for most uses.

    **Scene behaviour**

    The New Scene panel allows the choice of any working frame rate and working field order in addition to a working format. The working format and working field order (but not the working frame rate) can be modified in Scene Settings View. The default settings come from the Setup.

    Old scenes require an upgrade on load, which will discard the undo history. Old formats in the scene are read and their colour space, frame rate and field order are used to update the scene (including working colour space, working frame rate and working field order, grade result space, default input colour space, render colour space, frame rate and field order, and all operators which use colour spaces, frame rates or field orders).

    Frozen Formats no longer exist. No format-related dialogs are presented when scenes are loaded.

    **Sequence**

    The Sequence operator has been reorganised to group settings together and move commands to an action menu. It now has separate frame rate and field order options, and a stack colour space option.

    The Sequence Input Colour Space can be "No Conversion", "Automatic/From Metadata" or a named space; the Stack Colour Space can be "No Conversion", "Working Colour Space" or a named space.

    When there is a conversion from the Input Colour Space to the Stack Colour Space, a Display Rendering Transform may be specified.

    Sequence now knows whether its images are single-channel; if they are then it assumes they are mattes and applies no colour space conversion

    When a sequence uses a Basic format as its Input Format, the actions menu allows a real format to be created and used; this is necessary if you want to define mappings, masks or custom proxy resolutions.

    **Conform**

    Conform no longer warns about frame rate or colour space mismatches. It no longer requires formats to be created for all the media resolutions.

    **Sequence Browser**

    Sequence Browser now has controls to specify frame rate, field order and colour space, including an option to use the scene's default colour space setting. These settings are applied to inserted Sequences.

    The frame rate and field order are set automatically from movies, but can be locked to prevent automatic changes.

    Sequence Browser assumes sRGB viewing colour space when its colour management option is enabled.

    **Render**

    Render View now shows Output Frame Rate. This is used to determine the pulldown options available.

    Rendering with Output Format: Use Input Format now only uses the Input Format geometry, not its frame rate, colour space or field order.

    bl-render has new options: -rate, -progressive, -interlace lower, -interlace upper (all of these default to the scene's working settings).

    **Formats hierarchy and storage**

    Baselight supplies a new small set of system formats, which should cover most requirements for scene working formats and render deliverables.

    Global formats are stored in a database whose location is stored in preferences, defaulting to the local system. This allows shared host/site formats to be configured far more easily.

    Formats can now be held in jobs. Job formats are accessible to all scenes in the job. When creating a new scene, the job's formats are included in the Working Format menu.

    There are no longer per-user formats.

    **Formats editor**

    The formats editor now shows a tab for each format set (global, current scene's job and current scene). Formats on other systems and in other jobs can be opened. Formats can be copied and pasted between different hosts and jobs.

    Legacy user formats can be loaded to copy them into global or job formats.

    Job and global formats can be reloaded to allow format edits made by others (to global or job formats) to be recognised. Reloading formats can result in formats disappearing; if a deleted format is required by a scene it is automatically converted to a scene format.

    Formats can now be deleted. They can be exported to a file and opened from a file.

    Thumbnail resolution sizes for formats are now always automatically generated, and cannot be edited in the formats editor.

    **Other format-related changes**

    The Display tab in Setups now allows a default initial Viewing Colour Space to be set to match the display.

    Technical Grade no longer shows a menu for its output format; it is now purely a grade operator. Note that this change could affect scene behaviour in scenes using Technical Grade operators.

    Pan\&Scan no longer converts the image to the colour space of its output format. Note that this change could affect scene behaviour in scenes using Pan\&Scan operators.
*   **Scene Templates**

    When creating a new scene you can now select a Scene Template which is used to set up the new scene's Scene Settings and Render View.

    A number of FilmLight scene templates are shown at the top of the menu; you can select a job containing additional scenes which are added to the list.

    Any existing scene can be used to set up a new scene using the "New Scene Using Scene Template" option on the Job Manager.

    Baselight ships with 3 Scene Templates that should give a starting point of how to setup a standard Baselight scene. These Templates should cover most of the grading workflows used in the industry (also explained in greater detail at: [http://www.filmlight.ltd.uk/workflow/truelight.php](http://www.filmlight.ltd.uk/workflow/truelight.php))

    The three Templates are

    **ACES Template**

    This should set up a scene in a ACES recommended fashion

    The following settings are set:

    Scene Settings: • Timeline Caching: Full • Display And Timeline Cache: 10-bit Integer RGB • Working Colour Space: ACEScc: ACEScc / AP1 • Grade Result Colour Space: From Stack • Display Rendering Transform: ACES RRT 1.0 • Colour Treatment: Native (as we have a HDR Working Format)

    You should set your Image Container to the Project/Job level in the file structure in order to get the deliverables to work properly.

    Render Deliverables are included that should cover most of the deliverables needed in a production:

    • Dailies Avid graded • VFX Plates ungraded • VFX Plates graded • QT for Approval • P3 Deliveries • DCI XYZ Deliverable • ACES Archive • rec709 Deliverable

    **Telecine Template**

    This should set up a scene in an "Telecine"-like setup

    Scene Settings: • Timeline Caching: Full • Display And Timeline Cache: 10-bit Integer RGB • Working Colour Space: ARRI: LogC / WideGamut (can be substituted with any log like HDR Camera Colour Space) • Grade Result Colour Space: Rec.709: 2.4 Gamma / Rec.709 (can be substituted with your primary grading display) • Display Rendering Transform: None • Colour Treatment: Native (as we have a HDR Working Format)

    You should set your Image Container to the Project/Job level in the file structure in order to get the deliverables to work properly.

    Render Deliverables are included that should cover most of the deliverables needed in a production:

    • Dailies Avid graded • VFX Plates ungraded • VFX Plates graded • QT for Approval • rec709 Deliverable • P3 Deliveries • DCI XYZ Deliverable • VFX Plates graded log

    **Video Template**

    This should set up a scene for a Video-like grade, where most of the input footage is already "low dynamic range" Rec.709.

    Scene Settings: • Timeline Caching: Full • Display And Timeline Cache: 10-bit Integer RGB • Working Colour Space: Rec.709: 2.4 Gamma / Rec.709 • Grade Result Colour Space: from Stack • Display Rendering Transform: Truelight Video 1 (this is only used if you bring a HDR Camera Format in the scene) • Default Image Transformation / Colour Treatment: Linearized (as we have a LDR Working Format)

    You should set your Image Container to the Project/Job level in the file structure in order to get the deliverables to work properly.

    Render Deliverables are included that should cover most of the deliverables needed in a production:

    • Dailies Avid graded • VFX Plates graded • QT for Approval • rec709 Deliverable • DCI XYZ Deliverable
*   **Colour Space operator**

    The Colour Space operator allows (a) explicit conversion of colour space in a grading stack, optionally with an explicit Display Rendering Transform, and (b) explicit assertion of an image's colour space (e.g. following a Truelight operator).

    Inserting a BLG adds Colour Space operator strips where required to match the colour spaces and DRT in use when the BLG was created.
*   **Retime operator**

    Retimes can be added to a stack from the 'Insert' menu or by editing existing operators in a layer (typically the input layer/strip).

    Graph Modes:

    The Retime operator has 2 explicit graph modes: 'Velocity vs. Time' (the default) and 'Time vs. Time'. The graph for each mode is maintained separately & can be selected from the 'Graph Mode' dropdown. In both modes the X axis of the graph represents the output time (in strip start relative frames).

    In 'Velocity vs. Time' mode the Y axis represents the (percentage) velocity at the corresponding X axis output time. By default this graph has a constant value of 100%. Because the graph is constant, dragging the graph line up or down will set a new velocity for the entire shot. To vary the velocity during the shot, keyframes must be added at the desired times on the graph (using the toggle keyframe icon button, Blackboard key or keyboard shortcut). Additionally, a constant frame offset can be applied to adjust the input start time.

    In 'Time vs. Time' mode the Y axis represents the input time at the corresponding X axis output time. By default this graph has 2 keyframes (at the start & end of the shot) that make a diagonal line mapping output time to the same input time.

    Sampling modes:

    The Retime operator has 3 sampling modes that control how the output image is rendered (when the input time is between 2 frames):

    Snap To Frame - The output frame is the input frame at the input time rounded down to the nearest frame. Mix Nearest Frames - The output frame is a mix of the 2 frames on either side of the input time. Optical Flow - Frames on either side of the input time are processed using an optical flow based algorithm to produce a single output frame. In this mode additional parameters are provided to fine tune the rendering: Quality - Specifies the amount of processing. Increasing the quality will increase both the precision and the rendering time. Smoothing - Controls the amount of smoothing applied to compensate for incorrect motion vectors.

    A default sampling mode for any new Retimes can be set from the operator's "Customise" menu.

    Blackboard controls:

    The Blackboard can be used to make adjustments to the current curve using the following trackball mappings:

    Right Trackball - Move the graph/current control point up or down (adjusting the input time). If the graph has keyframes, the trackball's buttons can be used select next/previous keyframes. Middle Trackball - Move the current control point (if any) left or right (adjusting the output time). Left Trackball - Adjusts the frame offset when the graph mode is "Velocity vs. Time".

    Keyboard shortcuts:

    If 'Numeric Keypad For Grading' is enabled (from the 'Edit' menu) the following numeric keypad shortcuts become active when a Retime operator is selected:

    '-' - Toggle keyframe at the current time. '+' - Move the graph/current keyframe up by either 10% or 10 frames (depending on the graph mode). If the 'Ctrl' modifier is held down, then the change applied is reduced to either 1% or 1 frame. 'Enter' - Move the graph/current keyframe down by either 10% or 10 frames (depending on the graph mode). If the 'Ctrl' modifier is held down, then the change applied is reduced to either 1% or 1 frame. 'Del' - Reset the graph/current keyframe to it's default value. 'Insert' - Toggle the graph editor's zoom level between it's default and +/- 10 output frames.

    Sequence Operator Resampling Modes:

    The input strip's Sequence operator now offers 4 resampling modes: 'From Scene', 'Snap To Frame', 'Mix Nearest Frames' and 'Optical Flow'.

    In 'From Scene' mode, the mode to use is derived from the scene settings (which is in turn initialised from the appropriate Setup when the scene is created).

    The 3 other modes are described in the 'Retime Operator' section above.

    Resampling modes come into play when a fractional 'Frame Increment' setting and/or input to viewing format frame rate mismatch result in a fractional input sequence frame number. When this occurs, the resampling mode is used to control how frames on either side of this frame number are combined to generate a single result frame.

    Note: 'Frame Repeat Count' values other than 1 are only supported in 'Snap To Frame' mode.
* Baselight is now able to read non-linear speed changes in AAF files and convert them to Retime operators, if the "Variable Timing" option is set to "Yes" in the EDL Import panel \[bug 25912]
*   **Colour Matrix operator**

    The Colour Matrix operator will transform the current image using a matrix and an offset. When transforming from rgb to RGB...

    R = Rr_r + Rg_g + Rb_b + Roffset G = Gr_r + Gg_g + Gb_b + Goffset B = Br_r + Bg_g + Bb\*b + Boffset

    The user interface has three groups of four sliders to control the four parameters for each of the three outputs. The desk controls come in groups of three, so to make things neat, the offsets have all been moved to their own group.

    There is a scale slider at the bottom. This will scale all these parameters, and so scale all the output image values.

    There is an Invert button. When Invert is Enabled, the plug-in will do the inverse transform. If the transform cannot be inverted (set scale to zero for example), you will get an error message.

    You can use this plug-in to perform grades in a crude luminance-chrominance space as follows...

    L: Rr=+0.6 Rg=+0.3 Rb=+0.1 Roffset=0.0 a: Gr=+0.5 Gg=-0.5 Gb=+0.0 Goffset=0.5 b: Br=+0.0 Bg=+0.5 Bb=-0.5 Boffset=0.5

    Copy and paste the ColourMatrix strip. On the second copy, select Invert Enable. This should restore you to the original image coordinates.

    If you do a grade between these two strips, the grade will be working in a luminance-chrominance space.
*   **CDL Grade operator**

    CDL Grade now replaces the Video Grade operator for all CDL values imported into or exported from Baselight.

    The Grade operator is split up into 3 separate tabs: CDL, Film Grade and Video Grade. The CDL tab presents the grade using Slope Offset Power, the Film grade presents Exposure Power Contrast, and the Video Grade presents the same grade using Lift Gamma Gain. The saturation control remains the same between the 3 tabs.

    The text entry field below displays the current values in a CDL format. Values can then be copied to a file from the text, or entered into the text field to change the operator's values.

    In the customise menu there is an option to import a ".ccc" XML file, this will set the CDL operator's parameters to the values stored in the file.
*   **Feet+Frames**

    Feet+Frames can now be used as an option for timeline units. The timeline start footage and gearing can be set in Scene Settings.

    A new %{TimelineFootage} substitution can be used in burnins and Text strips to insert the timeline feet+frames.

    The "Keypad 'go to' default mode" preference can be set to default to navigating using Feet+frames, or to swap to Feet+frames when 0 is pressed \[bug 18516]
*   **ARRI Look operator**

    A new operator has been added to allow the import of ARRI look xml files. This operator will apply the ARRI look colour space conversion and tonemap to the image as well as any CDL, printer lights or saturation values present in the look file.

    The operator can also toggle each ARRI look operator or set the desired output colour space. Any colour space changes will be reflected in the colour space journey view
*   **Subtitling**

    Added support for Digital Cinema Interop (CineCanvas(TM)) version 1.1 subtitling. The subtitle XML file is presented as an RGB movie with alpha.

    To add a subtitle overlay, create a new layer; set Layer Mode to "Matte From Foreground Alpha"; and select the subtitle XML file as the source.
*   **LUT export**

    LUT export has been updated to handle Colour Space conversions as well as grade operations. There is a separate Export LUTs option in the Shots View menu which gives options for up to three LUTs to be exported per shot.

    Each LUT can contain a combination of the Input Transform (any colour space conversion in the Sequence strip), Grade operations (from the Input strip and any grade strips) and an Output Transform, with a specified Output Colour Space.

    There are now also resolution options for the exported LUT: default settings use standard values but these can be overridden if required.
*   **Movie/RAW Decode Quality**

    The way by which decode resolutions are chosen for movie and/or RAW files has been simplified. There are now two options:

    * Optimised: this decodes at the closest resolution to the cursor/render resolution (e.g. half-res when decoding 4K input material with an HD cursor/render)
    * Max Quality: this decodes at the highest available resolution (which will then be scaled down as necessary by Baselight to the required cursor/render resolution)

    At "Medium" and "Low" resolution, Optimised decoding is used. At "High" resolution, the default behaviour for cursors and renders is that Max Quality decoding is used. This can be changed on Cursor View and Render View on the Resolution line.

    The behaviour can be overridden on individual Sequences by using the "Always Decode At Max Quality" button. For example this might be necessary if you use Optimised decoding but are scaling up an image using a Transform or mapping.

    ARRIRAW sequences decoded using ARRI Decode now always decode at Max Quality; this removes previous resolution-dependent switching between ARRI Decode and Baselight Decode methods.

    The Sequence "Medium/Low Res." option has been removed \[bug 28655]
*   **ACES 1.0**

    Added support for the latest ACES 1.0 Specification. The Academy has introduced a "Target Conversion Transform" (TCT) or "Render Intent" (Dim Surround and Dark Surround). In order to be fully compatible with the Truelight Colour Space System two DRTs have been added to accommodate both Render Intents. Also two new working colour spaces have been added.

    **ACES RRT 1.0 Dark Surround**

    ACES RRT 1.0 Dark Surround should be used in combination with "theatrical" Display Colour Spaces like "DCI: 2.6 Gamma / DCI P3", "ACES: 2.6 Gamma / DCI D60" or "DCI: 2.6 Gamma / X'Y'Z'"

    **ACES RRT 1.0 Dim Surround**

    ACES RRT 1.0 Dim Surround should be used in combination with "video" Display Colour Spaces like "Rec.709: 2.4 Gamma / Rec.709" or "Rec.2020: 2.4 Gamma / Rec.2020"

    **ACEScc: ACEScc / AP1**

    "ACEScc: ACEScc / AP1" is a colour space designed by the Academy for colour correction. It has a "pure log" tone curve and a new set of primaries called AP1 (ACES Primaries 1). The tone curve has no black compression on the bottom end and the reference black point is defined as CV 0.0. It is the "full range" version of "ACES Proxy" and should be used as a Working Colour Space within Baselight. AP1 spans a colour gamut slightly larger then Rec.2020. It should give more sensible control for colour grading compared to the bigger ACES AP0 Primaries.

    **ACEScg: ACEScg / AP1**

    "ACEScg: ACEScg / AP1" is a colour space designed by the Academy for computer graphics works. It is has a linear-light transfer function and the same AP1 primaries. This colour space should be used in a compositing context but not for colour grading.
*   **New DRTs and Colour Spaces**

    **Truelight Film 1 DRT**

    Truelight Film 1 is a DRT based on the "generic film" Truelight profile. It is designed to introduce a filmic colour rendering, as produced by a typical modern print film. The inverse DRT Transformation is greatly improved to allow an artifact-free inverse transformation for Rec.709 or DCI P3 Footage.

    **FilmLight: Printing Density Log / \~ADX Colour Space**

    This colour space is similar to the Academy "ADX" colour space but with more focus on robustness and invertibility. It is designed as connection space for the Truelight Film 1 DRT, and should not be used as grading colour space for digital content. However if your footage is primarily camera negative log scans you can use this space as Input and Working Colour Space in combination with the Truelight Film 1 DRT.

    **Truelight Video 1 DRT**

    This new DRT is designed to introduce a soft "video-ish" or "telecine-ish" colour rendering. It is designed for colourists who wants to grade HDR data in a display colour space. The DRT introduces a soft colour rendering without compressing too much data. But it can also be used as a Display Rendering on output.

    It does a slight highlight roll off and a gamut compression which starts at 90% saturation, so most colours should be unmodified. The inverse transform is robust. The gamut re-compression was skipped in the inverse function to gain robustness. So very saturated colours might be reproduced inaccurately. The DRT is parametrized, so it is possible to build custom DRTs based on Truelight Video 1 - please contact baselight-support@filmlight.ltd.uk if you need more information.

    **ARRI Photometric v2 DRT**

    This DRT is identical to the ARRI Photometric DRT but has an improved inverse transform to allow artifact-free inverse conversion for Rec.709 or DCI P3 Footage.
*   **Colour Spaces - New Naming convention**

    There is a new standard naming convention for colour spaces, which uses {Standard or Manufacturer}: {Transfer function} / ${Primaries} / {Optional information like creative whitepoint etc}

    Examples are • ACES: Linear / AP0 • ARRI: LogC / WideGamut • Sony: Slog3 / SGamut3.Cine • DCI: 2.6 Gamma / DCI X'Y'Z' / Creative D60 • Rec.1886: 2.4 Gamma / Rec.709

    In order to be fully compatible with the current practice and correctly refer to standards, we have renamed some of the colour spaces. In particular Baselight 4.4 used "Rec.709" to refer to colour spaces actually using Rec.1886.

    Some of the important colour space name changes are:

    4.4 Rec.709 Video 4.4m1 Rec.1886: 2.4 Gamma / Rec.709

    4.4 Rec.709 Video legal 4.4m1 Rec.1886: 2.4 Gamma Legal/ Rec.709

    4.4 Legacy Video 4.4m1 Rec.709 Camera: \~1.95 Gamma / Rec.709

    4.4 P3 Native White 4.4m1 DCI: 2.6 Gamma / P3 DCI

    4.4 P3 D60 White 4.4m1 ACES: 2.6 Gamma / P3 DCI / Creative D60
*   **Colour Space Hints**

    Hints, warnings and recommendations are shown in the Colour Space Journey View when Baselight detects a non-optimal setup of Colour Space Choices, defined by a set of rules. A Truelight Colour Space Icon is shown in the menu bar when there is a message in the Colour Space Journey View, clicking on it will open the View.

### Miscellaneous

* Added support for the new Generation VI Baselight hardware platforms.
* bl-power has been updated. There is a new -sleep option that powers down the nodes on a Baselight FOUR/EIGHT system. It no longer scans the network for available systems, but connects to the local zone only. This stops a lot of zeroconf-related errors \[bug 20586]
* bl-power is now better able to restart the system after a startup failure \[bug 14294]
* The Blank operator now has a colour space option. This allows colours to be specified in a known colour space.
* Added support for reading OP-1b MXF files with internal essence containers (e.g. Panasonic Varicam) \[bug 26422]
* Added support for reading AVC-Intra LT MXF files from Panasonic Varicam \[bug 31237]
* Added support for reading XAVC LongGOP MXF files \[bug 27921]
* When writing QuickTime movies on Mac OS X, codecs that expect legal-range data will now show a warning in the render panel if a full-range colour space is selected \[bug 25506]
* Added support for reading XAVC S MP4 files \[bug 26436]
* Improved Stereo Geometry Fix two-phase transform, decreasing stereoscopic distortion. Added two new transform mode options: Translate + Scale and Translate + Scale + Perspective \[bug 28893]
* Added Scratchpad preference to enable grab/recall of input layer operators \[bug 25163]
* Added ability to change operator type across multiple strips using grouped grading \[bug 29332]
* Added icon to strips to indicate if any of their operators have keyframes \[bug 19774]
* Render View options for image types (e.g. the compression applied to an OpenEXR render) are now specified in a separate Image section under the File Type row \[bug 30851]
* Render View "Do Not Read Cache" option has been replaced by a new "Disable Cache" option. This has the same effect as changing Timeline Caching to Disabled on Scene Settings View. This option may change the appearance of scenes if strips are cached. It is particularly useful when rendering a scene that uses strip caching to a format larger than the scene's Working Format \[bug 28941]
* Deliverables can now be enabled and disabled from the tab titles in Render View \[bug 30041]
* Added Pan & Scan to layer operators \[bug 30021]
* Audio Encoding is now shown for QuickTime movies \[bug 28489]
* Added "I/O 5" Stack Manager button to Chalk to optionally allow quick access to 5th Inside/Outside operator \[bug 30305]
* bl-mkscene now takes options for colour space, frame rate and scene template \[bug 30298]
* When editing directory preferences, the browser now allows new directories to be created \[bug 30366]
* bl-shots now uses a tab character between each column of its output, and does not use quotation marks \[bug 28759]
* The Matte Merge operator now defaults to Union rather than Intersection \[bug 29568]
* Edit boxes are now more prominent when they have input focus \[bug 29037]
* Added option to Consolidate View to choose whether or not to update the scene container \[bug 30718]
* Baselight is now able to read Resize operators out of AAF files and convert them into Transform operators, if the "Apply Image Transforms" options is set to "Yes" in the EDL Import view. The interpolation on animated transforms can be specified in the "Interpolation" drop-down to the right of the "Apply Image Transforms" option \[bug 24187]
* Vectorscope now has a new contrast control. This allows the user to bring out more detail in the scope \[bug 28801]
* Setups have been changed to disable use of a Baselight Kompressor by default \[bug 31010]
* Alexa 65 ARRIRAW files can now be decoded using ARRI Decode mode \[bug 30913]
* Added "List File Size" and "Sort By Size" options to Sequence Browser \[bug 31626]
* Colour space metadata is read from many QuickTime codecs (notably h.264) and is used to select a legal/full-range colour space as appropriate \[bug 24964]

## Bug Fixes Since Baselight 4.4.7317

* Fixed a bug where QuickTime movies read in Y'CbCr 4:2:0 on Linux were upconverted to 4:4:4 by a third-party library \[bug 25972]
* Fixed a bug where QuickTime movies read on Linux in full-range Y'CbCr were converted to RGB by a third-party library \[bug 25477]
* Fixed an issue where some QuickTime movies, particularly some XDCAM and Canon C300 files, would decode extremely slowly \[bug 27002]
* Fixed appearance of thumbnails in Cuts View when the stack uses Northlight alpha channels \[bug 29237]
* Fixed change in appearance of variable feather shapes when switching between an interlaced or anamorphic cursor/output format and a progressive or isomorphic one. Note that this may change the drop-off rate (but not the overall shape) of shapes created using an earlier Baselight release \[bug 22561]
* Changes to Timeline Caching on Scene Settings View can now be undone.
* Sequences with % characters in their path no longer cause render failures \[bug 27618]
* Ensure matte inputs to grades are clamped from 0 to 1 (useful if grading through OpenEXR matte channels with out-of-range values) \[bug 28426]
* Fixed incorrect application of transform in pan & scan when "Output Format Only" mode enabled (now renamed to "When Viewing Format Matches Output Format") \[bug 29959]
* Fixed incorrect thumbnail image in Cuts View when transforming an image as a matte for a composite \[bug 26048]
* Fixed failure in ramsize diagnostic \[bug 28867]
* fl-diag will no longer report an error if the PFS is conigured to work with the yfs kernel module \[bug 22694]
* Fixed behaviour of cached strips in interlaced formats \[bug 28929]
* Fixed occasional crash when applying Scratchpad slots \[bug 28668]
* Increased sensitivity of encoder when changing Blend Type via encoder on Blackboard 2 / Slate \[bug 29054]
* Replaced unusable "Confirm Version" button with "Original Version" for Scratchpad on Slate desks \[bug 30305]
* Fixed failures when using Undo/Redo to re-create operators that use formats which no longer exist \[bug 11868]
* Multi-Insert no longer treats movie files as proxies \[bug 30370]
* Stereo (left+right track) renders now render the two tracks at the same time rather than using multiple passes through the scene. This should improve render speed for scenes using stereo colour matching \[bug 25856]
* Input from desk trackballs, rings and encoders is now disabled when an edit box has focus \[bug 29037]
* Allow renumbering of layers that span more than one stack \[bug 30636]
* ARRI metadata "CameraClipName" is now used to populate Clip metadata \[bug 29596]
* Improved the read performance of temporally compressed movie files \[bug 15023]
* QuickTime internal data references are no longer resolved, to avoid hanging when opening certain files \[bug 28755]
* Fixed loss of alpha channels using Generate Proxies from the Job Manager \[bug 30702]
* To address occasional issues with database permissions, all connections to job databases are now made as the 'filmlight' database user. The bl-fixdb command can be used to reset permissions on all scenes on a database host. When older scenes are upgraded to Baselight 4.4m1 their database ownership is changed to 'filmlight' \[bug 30735]
* Baselight now reacts better if you overwrite a movie file that it is using, and will read the updated file for future images \[bug 30799]
* Fixed crash when Importing/Exporting Chalk layouts on Mac OS X \[bug 30669]
* Add minimum allowed OS check to Mac OS X installer \[bug 30842]
* Fixed bug which prevented layer operator bypass from working if there was only a single operator in a layer and the layer had a matte \[bug 29932]
* If the database it not running, the prerender service will wait a few seconds and re-attempt connection. Previously it would sometimes fail to start up at boot time \[bug 31000]
* The prerender service will now restart itself after losing connection to the database, or any other type of error \[bug 31004]
* Improved activation of tooltips when using a tablet \[bug 28225]
* Fixed a bug where some QuickTime files opened on Mac listed internal fourcc codes as metadata \[bug 28756]
* 10-bit Packed YUV QuickTime codecs on Linux ('v410' and 'v210') no longer automatically squashes the output image to legal range. Instead, a warning will be presented in the render panel if a full range colour space is selected \[bug 26007]
* Fixed crash when subtitle xml file references a missing png file \[bug 30965]
* Fixed an issue which could cause temporally compressed movies to decode with broken images \[bug 30985]
* Browsing for an output directory on Render View now expands all % substitutions in the path (e.g. %J) \[bug 31023]
* Fixed drag and drop from Cuts View not obeying the All, Primaries, Layer 0 drop-down \[bug 31082]
* Fixed failures caused by the 'postgres' database user not being a superuser; added a diagnostic test to check this \[bug 31094]
* Fixed crash in conform using "Apply Baselight Grades" when the scene uses a non-global working format \[bug 31106]
* Fixed issue with Cuts View always redrawing during playing or shot jumping \[bug 30592]
* Fixed error when importing cdl files into the CDL operator \[bug 31129]
* Fixed bug where BLG Export from the Shots View was not correctly setting the Viewing Colour Space \[bug 31144]
* There is no longer a large performance drop when decoding RED material using CPU on a system that has a RED Rocket or RED-capable GPU installed, compared to systems without such hardware.
* Load nvidia driver before enumerating the GPUs \[bug 30232]
* Improve NVIDIA driver version selection logic to allow for a maximum NVIDIA driver version for systems with FilmLight DVI2SDI or Framestore hardware \[bug 31190]
* Inverted the CDL power parameter so moving up on any slider reduces the value, and moving on the hue wheel has an inverted effect on the values \[bug 31274]
* Fixed bug which would cause the first newly inserted Film Grade operator to have incorrect pivot/bump values if they had been changed from the defaults \[bug 31326]
* Fixed Timecode 2 reported from Phantom camera .cine movies. It should now match what other software reports as the "time of day" timecode, taking the recording timezone into account. Timecode 1 continues to report the definitive per-frame timecode stored in the file \[bug 31367]
* Fixed calculation of sequence frame numbers for various source, working and viewing frame rates \[bug 31357]
* Fixed crash when using Display and Timeline Cache "16 bit Floating Point RGB" on non-combiner systems BL4/BL8 \[bug 31320]
* Fixed pasting layer 0 to include the format (if the resolution are the same) and the colour space information \[bug 24817]
* Fixed audio playback via AJA Kona 4 SDI card \[bug 31460]
* Subtitle painter correctly handles right-to-left written Unicode characters \[bug 31448]
* Removed incorrect colour conversion applied to matte input of subtitle composite layers \[bug 31449]
* Fixed bug when referencing a non-inside/outside layer's matte from a downstream reference strip \[bug 31491]
* Fixed bug which would cause the wrong frames to be displayed for sequences with a speed change in resampling modes other than "Snap To Frame" \[bug 31424]
* Fixed a bug that could cause a lengthy initial delay to commands such as fl-ls and bl-browse on some OS X systems \[bug 31411]
* Fixed bug which caused Baselight to display an old file when a newer one was available on disk \[bug 26208]
* Grades which have Clip enabled now clip the image even when the grade's settings make no other change to the image \[bug 28368]
* The Orientation of the power control in CDL grade has been flipped \[bug 31095]
* Fixed failures when working with very long R3D clips using many run-on .R3D files \[bug 12724]
* File system usage information is now reported for cloud media and other volumes \[bug 31588]
* Fixed a bug that caused custom bitrates for DCP and DCI MXF codecs to be interpreted as bits per second rather than megabits per second \[bug 31606]
* Fixed colour space for VRW (Panasonic Varicam RAW) files \[bug 31549]
* Fixed multi-insert to calculate correct file size for R3D files \[bug 31373]
* Fixed "output %d Nan" warning messages when generating cubes from a stack and added more informative error messages \[bug 31680]
* Fix hang on shutdown in SDI output \[bug 31736]
* Fix LUT export for files with spaces in the name \[bug 31739]
* Fixed diagnostic test for NVIDIA driver version on systems with FilmLight DVI2SDI or Framestore hardware \[bug 31776]
* Fixed RGB 4:4:4 12-bit SDI output via AJA Kona 4 \[bug 31816]
* Due to an update to the ARRI SDK, ARRI-mode decoding of ARRIRAW files is no longer available on FLOS 2.1. If your system is running FLOS 2.1 and you need to use ARRI decoding of ARRIRAW files, you will need to upgrade to FLOS 6.4 \[bug 31828]
* Fixed stereo display via AJA Kona 4 \[bug 31689]
