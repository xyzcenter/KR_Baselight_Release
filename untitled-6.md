# 베이스라이트 릴리즈 노트 5.2.11313 (2019-01-15)



## Important Notes

### Compatibility With 5.1

Due to changes listed below, notably the new Image Transform Settings, scenes saved in 5.2 will no longer open in 5.1.

So as to ensure consistent image decoding access to remote Baselight, Daylight or FLUX Store systems also require a 5.2 release installed.

BLG files exported from 5.2 cannot be used by 5.1 products, including Baselight Editions.

### Baselight FOUR and EIGHT

Baselight 5.2 is the last version that is supported on Baselight FOUR and Baselight EIGHT systems. Baselight 5.3 and later will not install or run on such systems.

### Baselight CONFORM

Running on macOS 10.9, 10.10 or 10.11 is no longer supported

## New Features Since Baselight 5.1.11140

### Texture Highlight Operator

*   Added new Texture Highlight operator. This can be used to reduce

    modulation (contrast) in higher frequencies to avoid unnatural sharp

    highlights. This is a common problem for HDR deliveries where bright

    specular highlights produce an over-sharp image. The operator can

    also be used to smooth out small clipped highlights. It is designed

    to be applied in scene-referred colour grading workflows and is

    colour space aware \[bug 46352]

### Panorama

*   Baselight now includes a new tool called "Panorama" that enables common Baselight viewing and grading operations on 360 degree panoramic images.

    This tool is able to:

    * Given a user defined scene working format, activate a cursor based "Panorama Viewing Mode" that allows camera navigation about the projected scene.
    * Grade a particular region of interest in the scene directly in Panorama mode using a "Panorama Sandwich", free from the characteristic distortions of a 360 LatLong texture.

    **Panorama Scene Setup**

    To enable Baselight's Panorama functionality, material needs to be tagged as being panoramic.

    This is done by creating a new format of the appropriate resolution with the new "Projection" setting set to "Panorama" and then setting the Input Format of a Sequence to this format. The new format resolution should have the same pixel aspect ratio as the sequence dimensions to avoid distortion artefacts.

    The Working Format and Viewing Format of the scene should also be set to this same panorama format.

    **Panorama Viewing Mode**

    If the Viewing Format of current cursor is a panorama format, then the corresponding "Panorama" toggle button in the Cursor View is also enabled.

    This button switches between two viewing modes - rectangular (default) and panorama. When toggled on, the image is rendered in a spherical manner. The usual pan and zoom mouse controls are now reinterpreted as rotations around the scene and as changes in the camera field of view respectively.

    Toggling back into the normal rectangular format returns the mouse controls to the normal pan and zoom mode.

    * Mouse middle button: With the middle button pressed, mouse movements rotate the camera vertically and horizontally around the screen.
    * Ctrl + Mouse middle button: The Ctrl modifier lets the mouse middle button change the camera field of view.
    * Ctrl + Mouse wheel: The default camera height is at the centre of the sphere (cf. Fig 1). The combination Ctl + Mouse wheel allows the camera height to be adjusted inside the Panorama Viewer (cf. Fig 2). This control helps adjusting the panorama image if the original physical camera was not exactly at the centre of the scene.
      * .     \*
        * .       \*
        * .        \*
        * o-->     \*
        * .        \*
        * .       \*
      *   . \*

          Figure 1 - Default camera vertical position.
      * .     \*
        * o-->    \*
        * .        \*
        * .        \*
        * .        \*
        * .       \*
      *   .     \*

          Figure 2 - Change the camera vertical position.
    *   Alt + Mouse wheel: The combination Alt + Mouse wheel allows a cutoff correction at the bottom of the sphere (cf. Fig 3). A black circle appears at the bottom of the projected view indicating the point at which the truncation is applied.

        (NOTE) Not all footage corresponds to a complete spherical view of the world. Some images are truncated at the bottom to hide physical camera support equipment which might otherwise be visible in the scene.

        Wrongly assuming the physical camera view to be perfectly spherical results in a compressed image at the poles of the panorama projection. This can be detected by visual inspection of the projected image and noticing a merging artefact of the texture at the bottom of the sphere.

        *   .     \*

            * .       \*
            * .        \*
            * o-->     \*
            * .        \*

            Figure 3 - Change the sphere bottom cutoff.

    **Panorama Sandwich**

    Due to the large amount of distortion, most Baselight tools like Shapes, Trackers, Paint etc don't work well when applied directly to panoramic (LatLong) images - a tool to remove the distortion is required. This tool is the "Panorama Sandwich".

    The Panorama Sandwich is a pair of Panorama projection strips. The first strip projects the LatLong image onto a spherical surface. The second strip inverts the operation and maps the projected texture back into the original LatLong image. Any grading applied between these two operators will be restricted to the region in the LatLong texture the camera is looking at.

    (NOTE) The projection necessarily magnifies the region of the LatLong image into the viewing format resolution. Conversely, the inverse projection will minify the projected texture back into the LatLong image. Both of these projections will involve a filtering step applied by the renderer and may therefore affect the projected region of the LatLong image.

    A Panorama Sandwich is constructed by inserting two consecutive Panorama operators and enabling the "Invert Projection" mode of the second one. The later will synchronise the camera state with the former and apply the invert projection at the correct position in the LatLong image. Inside this pair, any grading will be restricted to the area at which the camera of the top Panorama strip is looking. This is made easy by the "Smart Panorama" macro (Shift+J), which conveniently creates a "Panorama Sandwich" beneath the current selection and sets the projection state of each Panorama strip accordingly. For convenience, Smart Panorama copies the camera state of the current cursor, as long as it is in "Panorama" mode.

    * Details of the settings of the Panorama operator:
      * Camera View Controls "Left/Right View" : Rotate the camera view horizontally. "Down/Up View" : Rotate the camera view vertically. "Field of View" : Change the camera field of view. "Camera Home View" : Reset the camera state. "Camera Control" : Display an camera control overlay which allows its control using the mouse. The mouse controls are the same as in Viewing Mode. "Extended Ranges" : Increase the range of camera rotations.
      *   Camera Position Controls "Camera" : Change the camera vertical position. "Dome" : Change the sphere bottom cutoff value.

          "Invert Projection" : Set the strip mode to invert the projection back onto the original LatLong texture. This will disable the strip controls and will set the strip to look up for its Panorama partner strip to read its camera state.
      *   As well as using sliders and overlays to control the camera, Panorama also supports using the Blackboard/Slate trackballs and encoders using the following mappings:

          "Middle trackball" : Rotate the camera view. "Middle trackball ring" : Change the camera field of view.

          "Up/Down encoder" : Rotate the camera vertically. "Left/Right encoder" : Rotate the camera horizontally. "Zoom encoder" : Change the camera field of view. "Camera encoder" : Change the camera vertical position. "Dome encoder" : Change the sphere button cutoff value.

### 레이러 블랜딩

*   Added new popup panel used to simplify the configuration of a layer's blend-related options.

    Previously, these options were set via a few (opaque) buttons and menu options. Now, they've been collected together in a single graph- style display, accessed from the "graph" icon button next to a layer's blend type dropdown.

    This graph has nodes illustrating:

    * Where the layer's grade operators are applied
    * Where the blend operation is applied
    * Where the final mix is applied

    How these nodes relate to each other can also be configured via this panel. For example, in a default layer the grade ops are applied and then fed directly to the final mix. However, you can move the grade ops over to the "Blend Type" node's input simply by clicking the 'tick' above the node itself.

    There are also node menus and buttons for setting the sources for various inputs/nodes, blend mode selection etc \[bug 32897]
*   Added new layer blend mode "Texture Blend". This allows you to restrict the grading operations in a layer to the lower or higher frequencies of an image.

    To grade lower frequencies:

    * Select "Texture Blend" as the blend type.
    * Set the result blending amount slider to \~50%.

    To grade higher frequencies:

    * Select "Texture Blend" as the blend type.
    *   Popup the blend configuration panel and move the layer's grade

        operators to the other input of the blend node (by clicking on

        the grey tick).
    *   Set the panel's "Mix" slider (or the result blending slider) to

        \~50% \[bug 48277]
*   Added nine new blend modes (to inside/outside layers and explicit blend strips) to match later versions of Adobe Photoshop:

    Linear Burn Darker Colour Lighter Colour Vivid Light Linear Light Pin Light Hard Mix Exclusion Divide
* Reversed the sense of "Colour Dodge" and "Colour Burn" to match Adobe Photoshop \[bug 41614]
* Changed the "Soft Light" algorithm to match Adobe Photoshop \[bug 41614]
* The "Subtract" algorithm is now a simple subtraction (A - B) to match later versions of Adobe Photoshop \[bug 41614]
* Changed the ordering and spacing of the blend mode drop-down in the Inside/Outside Layer and Blend parameter UIs to match Adobe Photoshop.

### MaxCLL/MaxFALL 분

*   Added the ability to analyse rendered frames and produce MaxCLL (content light level) and MaxFALL (frame average light level) numbers for the entire deliverable, and/or CLL and FALL numbers for each rendered frame.

    The deliverable analysis numbers are recorded in the render operation's log in the queue, and are written to an XML file in standard  format that also includes the colour space parameters for the Mastering Colour Space, if set \[bug 33887]

### Relight 오퍼레이

*   The Relight operator is a new spatial grading operator that works with additional world position and normal information to allow the casting of virtual lights within the 3D space that is represented by the image. The virtual light uses physically-based lighting and surface material appearance equations to compute a contribution of this virtual light that then can be mixed with the input image in various ways.

    To make this operator work, the stack needs to be set up in a certain way so that the operator receives the correct input information. If the world position and normal passes are al stored in a single large OpenEXR sequence or similar multi-track image format, the simplest way to achieve this is to use the "Smart Insert Relight3D" macro, which is available in the "Insert" menu. It uses an internal dictionary of OpenEXR track names that represent the corresponding compositing channels. If none of these track names can be found in the sequence it will ask the user to specify the name of the track with the option to be added to the internal dictionary at the same time.

    Alternatively, to set up the stack manually, it needs have the following order: Input (Raw Sequence or grading stack) Reference to the normal surface data or an image sequence Reference to the world position data or an image sequence Relight3D operator

    You must ensure that for both the surface normal data and world position data there are no colour space conversions which could modify the data and distort the results. The easiest way to do this is to ensure that the "Ignore Colour Conversion" toggle is set in the Reference strips.

    Similarly, you should ensure that the working format of the scene is set to be the same as the format of the OpenEXR sequence being relit. This is required to prevent resizing of the normal and world position inputs, which can cause odd lighting effects.

    Once the stack has been set up correctly and the operator has been inserted successfully, the first thing the operator will ask you to do is to define the global unit size. Often with computer generated imagery, the size of the world and the scale of the units (mm, cm, meters, inches, feet) are not well defined or not clear. This information tends to be lost once it has reached the later stage of production. Unfortunately, this can lead to very confusing setups where an object might appear very small or very large in the image but its actual size in terms of 3D unit world scale could be tiny or enormous. To balance this out and to make setting the later lighting parameters easier, you can set the global scene scale. This can be done by just dragging a line in the image viewer from one point representing a part to the scene to another part. While doing the actual size of one unit will be displayed next to it. If you do not want to define a unit scale simply off click "Pick Scale Distance" button and the global scale stays 1.0. The global scale can also be changed at any time by either click on the "Pick Scale Distance" again or change the "World Global Scale" value manually in the user interface. If the scene contains multiple different sequences with roughly the same unit scale the current active scale can be stored as default for all future Relight3D operators via the "Customise" menu.

    Placing a light source is typically done in the Display View. Simply click on the position in the image you want to be lit and the light will automatically move to a point along the normal from the clicked point. The distance along the normal is specified by the "Target Distance".

    This works very well if only a diffuse contribution of the light is required. Making a specular highlight appear at the same point is a bit trickier as it depends not only on the light direction but also the virtual camera viewing direction. One has to shift the light facing direction to match up with the virtual camera viewing direction. To help to achieve this, there is a second click-mode that can be engaged by changed by changing the "Diffuse Hotspot at Mouse Position" setting to "Specular Highlight at Mouse Position". When engaged, the light will be positioned to ensure a specular highlight at the point clicked. For convenience, holding "Shift" when dragging will engage the alternative click mode during the drag. The specular highlight colour is determined by the light colour which is white by default. It can be changed in the user interface by selecting a colour from the colour wheel or alternatively a colour can be picked from the image by holding Control (Cmd on the Mac) and clicking in the image viewer at the same time. This is very useful when needing to match the specular colour of existing lights in the scene.

    The surface material in the Relight3D operator is based on a mixture of a Lambertian diffuse appearance model plus a Cook Torrance specular model on top of that. This allows the emulation of materials ranking from very matte surfaces (e.g. matte wall paint and fabrics) to semi-glossy (e.g. plastic, skin) to highly glossy surfaces, (e.g. untreated metals). The material parameters can be influenced by three settings in the UI: The "Diffuse Amount" determines how much diffuse/lambertian reflection the surface should exhibit. The "Specular Amount" determines how much specular/glossy reflection the surface should exhibit and finally the "Roughness" determines how rough/smooth the surface and therefore indirectly how glossy the surface should be. A high roughness values leads to a more diffuse-acting surface while low roughness lead to a nearly perfect mirror-like surface. As mentioned previously, the specular colour is determined by the light colour. However, the diffuse material colour is determined by the "Colour Source" and "Colour Use" options in the UI. By default, these are set to "Raw Input" and "Use Colour Source" respectively. This means the operator takes the pixel colour from the raw input images as the underlying diffuse material colour. This is not necessarily ideal as the raw image colour already contains baked-in lighting information so the whole process acts as a multiplier, which can look strange on occasion. Therefore, the other option is to "Use Colour Channel Input" this will allow to use an additional track in the OpenEXR (if available) as the per-pixel diffuse material colour instead. Alternatively, if everything is to be lit by a single unique diffuse material colour, "Use Colour Source" can be switched to "Use Single Colour" and an additional colour well will appear in the UI, allowing the diffuse colour to be specified.

    At the moment the Relight3D operator supports three different light types:

    *   Omnidirectional Point Light: An infinitely small light that

        casts light in all directions with the same strength.
    *   Directional Spot Light: An infinitely small spot light that

        only casts light within a given spotlight cone anle. The maximum

        intensity occurs within the "Hotspot Cone" and falls off to

        nothing at the "Spotlight Cone".
    *   Area Light: A rectangular light that casts light onto surfaces

        lying in front of the rectangle. It is possible to set the width

        and height of the rectangle, making it useful when needing to

        mimic real lights in a scene (e.g. strip lights or tube lights).

        Be aware, however, that increasing the surface area also will

        increase the total flux of the light at the same time.

    Area lights are always physically accurate and therefore always use an inverse square falloff, which means that doubling the distance of the light from a surface will result in the surface receiving only a quarter of the previous intensity. For area lights, this parameter (labelled as "Quadratic" in the "Falloff" drop down) cannot be changed. For point lights and spot lights there is no such restriction - the falloff can be changed to either "Linear" or even "None". Switching off light falloff is useful when simulating distance objects like the sun.

    The "Apply Type" control determines how the result from the virtual light should be mixed with the raw input image:

    *   Add the lighting result to the input image, simulating adding

        an additional light to the scene.
    * Multiply the lighting result with input image.
    * Subtract the lighting result from input image.
    * Replace the input image with the lighting result

    Out of the box, the Relight3D operator tries to extract the virtual camera position data from the metadata stored in the OpenEXR sequence. This data is required for computing the virtual viewing direction that is needed for the specular lighting contributions. If no such metadata can be retrieved from the OpenEXR sequence, the operator will try to solve the camera position automatically based on the 3D information stored in the normal and world position tracks. This process is not guaranteed to come up with a successful solution, but should work most of the time. In some rare cases the camera data stored in the OpenEXR sequence might be incorrect - if this is the case, there is the option to "Ignore Stored Camera Data" to force a solve of the camera position instead.

    The world position and normal inputs only contain a single value per pixel. Unfortunately, this can potentially introduce sharp/jaggy edges in the lighting result, especially if the light lies at a grazing angle to a surface. To soften this effect, the Relight3D operator allows one to use the "Edge Smoothing" slider to smooth edges and high frequency areas of the lighting result before it gets mixed with the input image.

    Rather than manipulating the light position in the Display View, the light position, light direction and some other lighting parameters can also be controlled using the "Point Cloud" tab. The controls of the point cloud views are identical to the ones that can be found in MatteXYZ.

    A control surface like Blackboard/Slate/Tangent Wave etc can be used to control certain light parameters via the trackballs and rings. When a control surface is available, the overlay in the image view will look slightly different, providing additional hints for the trackball controls. The trackballs are mapped to do following operations:

    *   The left trackball controls the orientation of the light. On the

        image viewer, this is symbolised by the two rings close to the

        light widget. The red ring represents the directional change that

        is will occur when rolling the trackball horizontally. Rolling

        left is symbolised by a darker red and rolling right is

        symbolised by a lighter red. The green ring represents the

        directional change that is going to happen when rolling the

        trackball vertically. Rolling up is symbolised by a lighter green

        and rolling down by a darker green. Additionally, pressing one of

        the "Axis Lock" buttons will restrict the movement to one axis

        when moving the trackballs. The trackball movements represent the

        movements on a sphere that surrounds the light position. At the

        extreme positions of the sphere (the poles) only one axis will

        have a real affect on the light direction. The left ring controls

        the light distance.
    *   The middle trackball controls the X/Y position of the light on

        the screen. The middle ring moves the light into/out of the

        screen.
    *   The right trackball controls the area light size. The right ring

        controls the light intensity.

### Upgrading of 4.4m1 Jobs and Scenes

*   Previously, Baselight 5 required a special installation of 4.4m1 to be able to read and upgrade old scenes and jobs. This it no longer required - Baselight can now import and upgrade 4.4m1 scenes directly.

    You can now also upgrade a single 4.4m1 scene "on the fly". Select it in the Job Manager and open it. Baselight will prompt you for a v5 job so it can make an upgraded copy of the scene.
*   The bl-upgrade command-line tool usage flags have changed. It can now create a new job when upgrading. It can also rename the 4.4m1 job so that the v5 job has the same name as the original. Run "bl-upgrade -i" for full instructions.

    When upgrading 4.4m1 jobs, scenes will be auto-unlocked whenever it is safe to do so.

    Baselight 5 is not able to recover autosave edits from 4.4m1 scenes. If this is required, open the scene in a copy of 4.4m1 first, recover the unsaved edits and save. Once that has been done, Baselight 5 will be able to read the scene \[bug 39321]

### Text 오퍼레이터&#x20;

*   The Text operator has been substantially updated, allowing a much greater flexibility and creativity in the positioning and motion of text in a scene.

    This includes the following improvements over previous versions:

    *   Support for transforms and perspective planes with the Text

        operator itself, in a manner similar to Shape and Paint
    * Support for trackers, including perspective tracking
    * Colour space aware colour picking
    * Significant performance improvements, particularly for large text
    * Improvements in the handling of extreme transforms \[bug 46958]

### Y'CbCr Matrices

*   The matrix (also known as "coding equations") used to convert between RGB and Y'CbCr when:

    * reading Y'CbCr-encoded input media
    * writing Y'CbCr-encoded output media
    *   displaying images via 4:2:2 SDI

        can now be switched between Rec.709, Rec.601 and Rec.2020.

    The Sequence operator allows the input matrix to be chosen; by default this is determined using the metadata obtained from the input media itself.

    The Render View allows the output matrix to be chosen; by default this is determined using the colour primaries of the render colour space.

    The Setup editor allows the display matrix to be chosen; you should set this to match the Y'CbCr-to-RGB matrix used by your display device.

    The Colour Space Journey View indicates which matrices are used by Sequence operators and SDI output.

    Sequences and deliverables in older scenes are unaffected, and will use the incorrect matrix for Rec.2020 media unless they are manually changed \[bug 45891]

### 이미지 트랜스폼 설정&#x20;

* Five new image transform modes have been added:
  * Circle Average. This is good for reducing an image by 3:1 or greater. The averages are a soft-edged circles that touch at the diagonals. It is sharp, but blurs the centre of a starburst chart where other options may give aliasing.
  * Square Average. This is not as good as the Circle sampling. It is a bit sharper but may alias on diagonal features.
  * Fixed Simon. This uses a fixed set of weights similar to "Cubic" but a bit sharper.
  * Adaptive. This is like the old "Adaptive" mode but adds a blur if Sharpness < 1.0. This was desired because the "Adaptive" filter cannot handle low Sharpness values with large reductions \[bug 46004]
  * Sharp Edge. This is a specialised mode that can be used for resizing titles or images containing other sharp features \[bug 33630]
* Image transform modes menus now show only the most useful items; use the Shift key to see the whole list. There are tooltips for each mode if you hover the mouse over the menu.

### 미디어 임포트 룰 Media Import Rules

*   A Media Import Rules View has been added. This view allows the setting up of rules that are applied whenever media is inserted into a scene. The rules are specified in the same way as Shots View filters are specified. When a rule matches a shot a number of actions can be taken:

    * File specific metadata can be mapped to a column in the scene
    * Decode parameters can be overridden
    * Certain parameters from the sequence operator can be overridden

    The view can be accessed via the Views menu or via shortcut buttons in the EDL Import and FLUX Manage views \[bug 33033]

### File System Indexing - beta functionality

When enabled, Linux Baselight systems will maintain an index of the local images volume that is continually updated as new material is introduced to or removed from the volume.

This feature will improve the speed of conform and other file system browsing operations. This feature is in beta test, and the configuration and operation is covered in the separate 'file\_system\_index.beta.txt' file in the 'baselight/doc' folder.

### 디스플레이와 타임라인 캐쉬 Display And Timeline Cache

* Added support for 12-bit Integer RGB caches \[bug 49395]
* Caching at 10-bit Integer RGB or 8/10-bit Integer 4:2:2 Y'CrCb can now store data uncompressed or encoded in Apple ProRes \[bug 49395]

### IMF 랜더링 IMF Rendering

*   Added support for writing IMF profile JPEG 2000 codestream (J2C) files. 2K, 4K and 8K variants of single-tile (lossy) profile and reversible profile, as defined in ISO 15444-1:2016 (amendment 8), are supported. Mainlevel 0-11 is supported for every profile, and sublevel 0-9 is supported for lossy profiles. Reversible profile is always encoded at sublevel 0 (no bitrate constraint). The mainlevel specifies a maximum sample rate and a maximum sublevel:

    * Mainlevel 0:       Unspecified | Unspecified
    * Mainlevel 1:     65 MSamples/s | Max sublevel 1
    * Mainlevel 2:    130 MSamples/s | Max sublevel 1
    * Mainlevel 3:    196 MSamples/s | Max sublevel 1
    * Mainlevel 4:    260 MSamples/s | Max sublevel 2
    * Mainlevel 5:    520 MSamples/s | Max sublevel 3
    * Mainlevel 6:   1200 MSamples/s | Max sublevel 4
    * Mainlevel 7:   2400 MSamples/s | Max sublevel 5
    * Mainlevel 8:   4800 MSamples/s | Max sublevel 6
    * Mainlevel 9:   9600 MSamples/s | Max sublevel 7
    * Mainlevel 10: 19200 MSamples/s | Max sublevel 8
    *   Mainlevel 11: 38400 MSamples/s | Max sublevel 9

        The sample rate is determined by the image format and the frame

        rate; sample rate = width x height x (components per pixel) x

        (frames per second). Each sublevel specifies a maximum bitrate:
    * Sublevel 0: Unspecified
    * Sublevel 1: 200 MBits/s
    * Sublevel 2: 400 MBits/s
    * Sublevel 3: 800 MBits/s
    * Sublevel 4: 1600 MBits/s
    * Sublevel 5: 3200 MBits/s
    * Sublevel 6: 6400 MBits/s
    * Sublevel 7: 12800 MBits/s
    * Sublevel 8: 25600 MBits/s
    *   Sublevel 9: 51200 MBits/s

        This information is also available in the render panel, in the

        dropdown selector for each type of level. NB: The sublevel selector

        has no effect when using reversible profile. 2K, 4K or 8K profile is

        automatically set based on the rendered resolution. 2K up to a

        maximum resolution of 2048x1556, 4K up to 4096x3112 and 8K up to

        8192x6224. Higher resolutions than 8K can not be rendered using IMF

        profile.

    Support for writing Broadcast Contribution profile JPEG 2000 codestream (J2C) files has also been added. All three Broadcast Contribution profiles defined in ISO 15444-1:2016 (amendment 8) are available; single-tile, multi-tile and multi-tile reversible. Level ranges from 0-11 are supported for single-tile and multi-tile profiles, while multi-tile reversible is always level 7. Each level specifies a maximum sample rate and a maximum bitrate. The rates for each level of single-tile and multi-tile profile are:

    * Level 0 :      Unspecified | Unspecified
    * Level 1 :    65 MSamples/s |   200 MBits/s
    * Level 2 :   130 MSamples/s |   200 MBits/s
    * Level 3 :   195 MSamples/s |   200 MBits/s
    * Level 4 :   260 MSamples/s |   400 MBits/s
    * Level 5 :   520 MSamples/s |   800 MBits/s
    * Level 6 :  1200 MSamples/s |  1600 MBits/s
    * Level 7 :  2400 MSamples/s |  3200 MBits/s
    * Level 8 :  4800 MSamples/s |  6400 MBits/s
    * Level 9 :  9600 MSamples/s | 12800 MBits/s
    * Level 10: 19200 MSamples/s | 25600 MBits/s
    *   Level 11: 38400 MSamples/s | 51200 MBits/s

        This information is also available in the render panel, where the

        desired level is selected. Multi-tile reversible profile level 7 has

        a maximum sampling rate of 520 MSamples/s and no bitrate limit. NB:

        The level selector has no effect when using multi-tile reversible

        profile.

    The ASDCP library has been updated from version 1.12.51 to version 2.7.19. This adds the capability to write AS-02 MXF-files, as used with IMF. It also fixes an issue where the SubDescriptors label written to DCI compatible MXF-files was incorrect.

    The string "JPEG2000" has been replaced with "JPEG 2000" in error messages and codec descriptions \[bug 41312]
*   SMPTE ST 2067-20/21 defines 7 different colorimetry systems, COLOR.1 to COLOR.7, that an IMF picture track MXF can be tagged with. The render panel will show an entry for 'IMF Colour Tag' in the 'Video' selector when rendering to the IMF MXF file type. Tags will be applied when valid files are created. The IMF Colour Tag entry contains a text field which shows which tag will be applied, if any. It also has a 'Change...' button to assist in setting up output for the different colorimetry systems.

    *   COLOR.3 will be tagged when:

        Using a matching colour space, e.g.

        * "Rec.709 Camera: \~1.95 Gamma / Rec.709"
        *   "Rec.1886: 2.4 Gamma / Rec.709"

            Using a bitdepth of 8 or 10 bits.

            Using RGB (legal or full) or YCC 422 (legal) values.
    *   COLOR.4 will be tagged when:

        Using a matching colour space, e.g.

        *   "sRGB: \~2.2 Gamma / Rec.709"

            Using a bitdepth of 8 or 10 bits.

            Using YCC 422 and legal range values.
    *   COLOR.5 will be tagged when:

        Using a matching colour space, e.g.

        *   "Rec.2020: 2.4 Gamma / Rec.2020"

            Using a bitdepth of 10 or 12 bits.

            Using RGB (legal or full) or YCC 422 (legal) values.
    *   COLOR.6 will be tagged when:

        Using a matching colour space, e.g.

        *   "Dolby: ST 2084 PQ / P3 D65"

            Using a bitdepth of 10, 12 or 16 bits.

            Using RGB legal or full range values.
    *   COLOR.7 will be tagged when:

        Using a matching colour space, e.g.

        *   "Rec.2084: ST 2084 PQ / Rec.2020"

            Using a bitdepth of 10, 12 or 16 bits.

            Using RGB (legal or full) or YCC 422 (legal) values.

    Legal range values can be created by using a video LUT. The IMF colour tags are read and used for selecting the colour space from metadata on read \[bug 41931]

### 파일 포맷 File Formats

*   Additional metadata is now read from JPEG 2000 files (J2C, JP2, etc). Files with a defined JPEG 2000 profile will have a 'Profile' metadata entry naming the profile, as well as any level and sublevel if applicable. Up to two comments will be read from files with embedded comments into metadata entries named 'Comment' and 'Comment2'. JPEG 2000 encoded MXF-files with valid JPEG 2000 subdescriptors now also have a 'Profile' metadata entry with profile and level information.

    Rendered files will now contain information about software version, profile, level and compression ratio as applicable in an embedded comment. Files encoded using GPU JPEG 2000 acceleration will contain two comments, the first identifying the compression SDK, the second containing the information added by the software \[bug 31956]
* Added an option to not clip highlights in DNG files. For new sequences, the default highlight handling is now 'Unclipped' rather than 'Clipped'. The highlight handling can be controlled via the DNG Params operator. A slider to control highlight reconstruction is also available when using 'Unclipped' \[bug 32481]
* Four additional colour spaces are now recognised from NCLC-atom metadata when reading QuickTime movies; 'Rec.2100: HLG 1.2 Gamma / Rec.2020 / 1000 nits', 'Rec.1886: 2.4 Gamma / Rec.709', 'CGI: Linear / Rec.709' and 'sRGB: \~2.2 Gamma / Rec.709'. Range will also be picked up from the ACLR-atom when reading files using DNx codecs \[bug 47377]
* Added support for reading Panasonic Varicam LT and EVA1 RAW CinemaDNG files using the V-Log colour space \[bug 37851]
* Added Sensor Rate metadata for ARRIRAW media \[bug 48693]
* ARRIRAW aperture metadata is now shown as a T-stop rather than an f-stop \[bug 48389]
*   Apple ProRes codecs always work with legal-range data. Previously a hidden scaling was done, and renders had to provide full-range data. For consistency and transparency this scaling is no longer applied, and image data sent to an Apple ProRes codec should be made video-legal using a Video LUT.

    This change also enables non-standard Apple ProRes movies to be created with full-range image data, should this be required.

    PLEASE NOTE: Deliverables in existing scenes, and deliverables created using older scene templates, will continue to use the old ranging behaviour. If you perform renders to Apple ProRes using the bl-render commandline, you will need to use the new "-v 1" option to retain the old ranging behaviour \[bug 26117]

### 유저 인터페이스 User Interface

* Popup menus (from the menu bar, or popup controls, or right-click menus) can now be filtered using the keyboard while the menu is open. For example, in a Formats menu, type "p" to show only formats with a "p" in their name. Press Escape to clear the filtering \[bug 48821]
* A popup tooltip will appear on a layer strip when the mouse is hovering over it, showing all the active grades within that layer. Popup info will not distinguish between inside/outside grades, if there are any \[bug 34105]
* The size and position of most file- and scene/job-choosing dialogs is now remembered the next time they are opened \[bug 29598]
* Custom (user-supplied) DRTs are now indicated with a user icon on menus, in the same manner as custom colour spaces \[bug 46338]
* The brightness of some displayed elements (picked colours, pane descriptions, snapshot descriptions and fps) now matches the brightness set for the pane indicators, which prevents them being too bright on an HDR display \[bug 46149]

### 블랙보드/ 슬레이트/ 초크 Blackboard / Slate / Chalk

* Chalk for Blackboard 2 and Slate has been updated to be faster and more user-friendly:
  *   when a modifier key (e.g. Control, Shift, Alt) is pressed, the

      display on the Chalk GUI and on the desk will update to more

      accurately reflect what would be displayed in the application

      under the same modifiers
  *   every layout modification is now undo/redo compatible.

      This includes adding, duplicating, deleting and renaming

      buttons and Slate Layouts, adding and removing Actions to

      and from buttons, and renaming (but not deleting) layouts.
  *   while Chalk is open, the standard undo/redo keyboard shortcuts

      can be used for layout modifications - Ctrl+Z to undo and

      Ctrl+Shift+Z to Redo (⌘+Z, ⌘+Shift+Z on Mac OS), and pressing

      Backspace or Delete on the keyboard will remove the selected

      button from the desk
  * it is now possible to rename a Custom Button \[bug 47864]
* Added "Lock Y Position" and "Find Stereo Correspondence" buttons to Slate. These appear on the Home layout at the far left on the second-from-top row when a Shape strip is selected \[bug 46514]
* Added desk controls on Slate for 17 operators: Blank, Camera Shake, DSpot, Erode/Dilate, Dissolve, EXR Exposure, Sander, Median, Motion Blur, Reference, Stereo Colour Matching, Switch, Threshold, and the Spirit grading operators (Spirit Noise Reduction, Spirit Primary, Spirit Six Vector and Spirit Spatial) \[bug 46697]
* Added a "Pick" button to Blackboard, Blackboard 2 and Slate desks. This mirrors the "Pick" toggle in the BaseGrade user interface. It will appear next to 'Ext Rng' in the operator-specific area of the desk when the BaseGrade operator is selected \[bug 45489]
* Added a "Balance Exposure" button to Blackboard, Blackboard 2 and Slate desks. This mirrors the "Balance Exposure" toggle in the Film Grade user interface. It will appear next to 'Ext Rng' in the operator-specific area of the desk when the Film Grade operator is selected \[bug 35455]
* Added Actions for "Smart Dissolve" and "Smart Dissolve Shot" in Chalk \[bug 34845]
* Added an Action for "Insert Layer Above" in Chalk \[bug 46742]
* On Blackboard 2 and Slate, layer and operator buttons now appear hatched, when the operator or layer to which they correspond is bypassed, like on the main user interface \[bug 46529]
* Added a control point bump feature to Grid Warp. When working on Grid Warp with a Blackboard or Slate, pressing the control key will toggle the arrow keys to bump keys. The default pixel bump amount can be set in the Grid Warp customise menu \[bug 48573]

### SDK 업데이트 SDK Updates

* Updated to Sony XAVC encoder SDK version 1.1.8, which improves image quality when encoding XAVC Long GOP formats and brings minor improvements to encoding speed and quality \[bug 47547]
* Updated to DNxHD/DNxHR SDK version 2.3.7.46. This includes bug fixes \[bug 48244]
* Updated to Canon RAW SDK version 2.2R2. This includes a bug fix addressing incorrect exposure of clips with a specific ISO Speed or Gain \[bug 49413]
* Updated to OpenEXR SDK version 2.2.1. There are no user-visible changes as a result \[bug 46009]
* Updated to FFMPEG SDK version 3.4.2. This SDK is used to read and write various video codecs in MXF and QuickTime containers. This update adds support for reading additional codecs, as well as minor speed and quality improvements both when reading and rendering. Existing scenes will still use the older SDK version to ensure that rendering does not change \[bug 39813]
* Updated to OpenJPEG SDK version 2.2. This brings a minor improvement in encoding and decoding speed of JPEG 2000 material without a GPU JPEG 2000 acceleration license \[bug 38662]

### Miscellaneous

*   The following multi-resolution operations are now scalable:

    * Boost Range
    * Denoise
    * Deflicker
    * Streak Filter
    * Texture Blend
    * Texture Equaliser
    * Texture Highlight

    These should now look similar when rendered at different resolutions. The fine detail is still handled at the local pixel resolution, but the longer-range effects should scale with the image rather than being a fixed number of pixels. The original scene resolution render is unchanged. We do not expect an exact match when rendering at other resolutions, but it should be closer than before. This is versioned, so old strips will not change \[bug 46966]
* Added "Apply Foreground Blurs To Matte" (Customise menu) option to composite layers. If enabled, any blurs applied to the foreground operators will also applied to the layer's matte input \[bug 46728]
* Added two new looks to Truelight Scene Looks:
  * C-104 Bipack is a spectral simulation of a two strip process from the \~ 1950. As it is a two strip process it does not render greens, but shifts the look to a distinct cyan/orange axis.
  * C-202 ALF-2 emulates the appearance of the ARRI ALF-2 DRT Family, matching viewing condition Video-100 \[bug 48843]
* Added negative clamps in the "Sodium High Pressure Lamp" and "Xenon Arc Lamp" looks. This prevents the looks from producing NaNs in some cases \[bug 48542]
* Added support for the NVIDIA Quadro M620 UI GPU \[bug 45506]
* You can now use the Job Manager to compact jobs. This reclaims unused space in the PostgreSQL database for that job. Select a job, and from its action menu choose "Compact Job" \[bug 46656]
* Baselight will now auto-compact jobs as part of the nightly backup task \[bug 47110]
* Improved error reporting when renaming jobs \[bug 47717]
* bl-export will now enforce a "bljob" or "blscene" file extension \[bug 47501]
* bl-export has improved help text \[bug 48393]
* bl-export has improved progress output \[bug 38209]
* Colour spaces which are only ever suitable for use as an Input Colour Space (typically those specific to a particular camera) are no longer offered in other colour space menus \[bug 43832]
* Added "Resolution" and "Quality" options to Still Export \[bug 46313]
* Changed automatic Mastering Colour Space for VideoWide and OfficeWide viewing conditions to DCI: 2.6 Gamma / P3 D65 \[bug 48247]
* Added new "Transform Alarm Overlay" feature (available from the "Display" menu). Once enabled, if a transform is introduced into the stack (explicitly or via a format conversion) that results in pixels outside the original image being introduced into the result image, those pixels will be displayed in a custom colour (also set from the "Display" menu) \[bug 28017]
* The Shots View now supports 2 modes of selection (from the "Customise" menu):
  *   Select Cuts View Shots : In this mode, selecting a shot in the

      Shots View will also (red square) select the shot in the Cuts View

      (and vice-versa).
  *   Select Stack Top Strips : In this mode, selecting a shot in the

      Shots View will also explicitly select the top/input strip of the

      corresponding stack in the timeline (and vice-versa) \[bug 45486]
* The command line tool for KDM creation, fl-kdmtool, now provides improved control over forensic mark flags and the authorised devices list. The built in help text has been updated accordingly, see the output of 'fl-kdmtool -h' \[bug 46023]
* Added bl-encryptshaders tool which enables Shader authors to create encrypted versions of their shaders for distribution \[bug 36745]
* Queue Monitor now shows elapsed time and overall fps for renders, and overall MB/s for copy operations \[bug 30623]
* 50fps frame rate is now offered on frame rate popups \[bug 48350]
* Added "Clip Negative Inputs" as an option for HDR Value Handling (in Scene Settings). This prevents negative values in VFX images from entering the grading stack \[bug 46796]
* When inserting from FLUX Manage View with Timecode 2 selected, sequences with no Timecode 2 now use the sequence Timecode for the Shot Timecode \[bug 47880]
* A folder of sequences can now be dragged from FLUX Manage View onto Shots View or Cuts View \[bug 49005]
* Added option to Shape strip "Customise" menu for setting the default keyframe bar display mode \[bug 49070]
* Added help text to DCI: 2.6 Gamma / X'Y'Z' space \[bug 48784]
* Added the ability to export left and right eye BLGs at the same time during BLG Export. Simply select the new "Both Eyes in Separate BLGs" option in the "Stereo" setting \[bug 49110]
* A deliverable preset defined with the same Render Frame Rate as the scene's Working Frame Rate no longer applies this frame rate when it is used in a scene with a different Working Frame Rate \[bug 45124]
* fl-make-secure will now stop with an error if it is not run on FilmLightOS 6 \[bug 48962]
* Added "Constant Bitrate" option to Apple ProRes QuickTime renders, to produce rendered files which are compatible with third-party video editing tools \[bug 46983]
* Client View is now available in Baselight CONFORM \[bug 47391]
* Added reference sub-stacks inside copy and destination subsets while using Blackboard copy and paste or DBS Apply (see Smart Dissolve or composite layer with foreground reference) \[bug 44095]
* Cmd+H now hides the application on macOS \[bug 49048]
* Numeric metadata such as %{Event} can now be padded in render filename templates, using the same syntax as for frame numbers: %.8{Event} will pad Event with leading zeros up to 8 digits \[bug 49106]
* The "Clip to Legal" and "Soft Clip to Legal" video LUT options are not recommended and are now hidden in the Render View and Display menus; they can be revealed by pressing Shift \[bug 49109]
* The controls for Dual Colour Spaces Layout have been changed. Two Viewing Colour Spaces are now shown on Cursor View with a toggle button next to each to control which is used for scopes, histogram and overlays \[bug 49254]
* The timeline "Display All Note Text" option can be toggled on to permanently display all of the mark note text in the timeline simultaneously \[bug 43750]
* LUT Export: Added option to export Left and Right LUTs simultaneously when using the Export LUTs dialog in Shots View \[bug 49094]
* LUT Export: Full path to expected filename is now shown \[bug 49090]
* Added new "Copy Files and Trim Sections From Movies" option to Consolidate. This creates multiple consolidated movies when more than one section of a movie file was used in the original scene \[bug 45757]
* Added Truelight to "Strip colours" preference \[bug 46498]
* The Truelight 'zview' application is now included with Baselight \[bug 48299]
* Added support for 48@24 fps and 50@25 fps timecodes when reading ALE and CMX EDLs \[bug 46246]
* Added bl-dump-edids utility, which can be used to save the EDID for monitors/projectors attached to the display and rendering GPUs on Linux systems. EDIDs are written into /usr/fl/etc/edids \[bug 46978]
* Added mechanism that allows OFX plugins to improve their colour space handling \[bug 49695]
* Added caching and compression to the internal operation of Paint, to improve the drawing speed \[bug 41546]

## Bug Fixes Since Baselight 5.1.11140

* Shadow Boost gave a small jump in the histogram when the controls moved off the default settings. This is fixed for new Shadow Boost strips, but old ones are as before \[bug 46870]
* Fixed an issue in Chalk which could cause multiple buttons to turn blue on the desk diagram \[bug 45873]
* Fixed an issue that could cause the scratchpad scene to behave slowly over time \[bug 46228]
* Scene loading performance is improved, particularly with scenes that contain complex trackers \[bug 46310]
* Fixed rare crash that could occur when switching in/out of follow-mode or when cancelling an edit \[bug 49469]
* The Job Manager will now show the user and software build of when the scene was last saved \[bug 45973]
* bl-backupdb could fail with a mkdir error when running in test mode. It will now report the missing directory as an error instead \[bug 45976]
* bl-shots and bl-containers can now be used on scenes that are currently open for editing \[bug 47775]
* Fixed bug which could cause shapes to shift slightly vertically when "Lock Y Positions" option enabled \[bug 45933]
* Fixed rare crash when reading from job database \[bug 47395]
* Fixed rare crash when performing Save-As \[bug 48778]
* Fixed possible cursor jump when performing Save-As \[bug 46500]
* Cursor settings are now preserved when upgrading 4.4m1 jobs \[bug 48097]
* Fixed crash with multiple spaces in a ccc file \[bug 45880]
* Fixed a potential memory leak in disparity histogram \[bug 45955]
* Renamed the Actions for the "Render Line Up" and "Render Line Down" desk buttons to be more consistent with their equivalents in the Navigate menu \[bug 45480]
* Fixed an issue on Slate which could cause the Slate Layout toggle button to display a nonexistent Slate Layout \[bug 29876]
* Fixed a potential memory leak in stereo geometry fix \[bug 45957]
* Fixed a potential memory leak in MatteXYZ \[bug 45956]
* Fixed a perspective operator issue which occurred when tracking was done in the 'In' side. After a stack split or a stack copy, it was left in an incorrect state \[bug 46032]
* Fixed a potential crash when swapping 2 layers in the timeline \[bug 45707]
* Added all cache formats to Display And Timeline Cache entry in Setups editor \[bug 46128]
* Fixed issue which prevented using the 375.66 NVIDIA Driver with GTX 980, Quadro NVS 810, Quadro K6000, M4000, M5000 and M6000 GPUs \[bug 46135]
* Fixed bug in 'Find Stereo Correspondence' when the working and viewing formats differed \[bug 46165]
* Fixed thumbnails for movies which have an orientation of +/- 90 degrees \[bug 46153]
* Fixed potential cause of cached playback slowdown with huge scenes \[bug 46238]
* The Blackboard 2 jog wheel can no longer move the cursor back beyond the start of the timeline \[bug 45593]
* Fixed paint clone bug with very small strokes disappearing under transforms \[bug 46254]
* Fixed crash when inserting a Pan\&Scan operator into a scene after using it in another scene that uses a format unknown to the current scene \[bug 46301]
* Fixed picking display in semi-automatic Stereo Geometry Fix not taking colour space transforms into account \[bug 46177]
* Fixed group grading the stereo split state of a set of strips. Now it will only change the state if it matches the parameter strip \[bug 46515]
* Speed up (grouped grade) 3D stereo splitting of multiple selected strips \[bug 46340]
* Fixed incorrect colour space when FLUX Manage Preview is used with the colour space set to Unknown and a scene is open \[bug 46545]
* Fixed flash of a sequence's first frame when entering FLUX Manage Preview \[bug 46542]
* Fix potential hang and disparity histogram picking display not working with certain grading stacks \[bug 46532]
* Fixed naming of erase operations from FLUX Manage \[bug 46546]
* The "Audio Toggle" desk button now works correctly on Slate: a short key press toggles Mute and a long key press pops up a transient volume adjustment panel \[bug 34069]
* Detection of corrupt scene databases is improved \[bug 46657]
* Fixed issue with Paint strokes not updating after resetting a transform \[bug 46576]
* Improved grouped paste error handling \[bug 46645]
* Image orientation is now interpreted when reading QuickTime files written by ARRI cameras \[bug 46761]
* Select next/previous strip of the currently selected type now obeys (Shots View) playback/navigation filtering \[bug 46891]
* Fixed potential crash when adjusting shape "Inner Scale" encoder \[bug 45303]
* Fixed an issue where an incorrect index for a temporally compressed movie could crash the movie reader. This situation will now produce an error message about a bad index for the affected frames instead \[bug 46745]
* Fixed render issue where the render frame rate was different to the working frame rate and the stack contained temporal effects \[bug 46782]
* Changed ganging behaviour of scale parameters in a transform strip such that the aspect ratio is maintained \[bug 44898]
* Fixed issue with Apply skipping strips if the mode was set to "Primaries" and contained copy protected strips \[bug 46972]
* Fixed crash toggling the Paint layer opacity keyframe button \[bug 46975]
* Added colour space selection to the paint colour brush colour selection tool to allow picking colours in a defined colour space \[bug 46273]
* The Colour Panel now allows a colour space to be specified when setting the colour of Text \[bug 46134]
* The Area Tracker and Area Tracker Perspective have been reworked to work better with non-planar motions, like faces \[bug 44762]
* On Mac OS X, the Cmd, Alt and Ctrl buttons on Slate now show the correct text \[bug 46312]
* Fixed issue with Paint when resetting a layer caused keyframes to be added \[bug 47162]
* Fixed an issue where rendering to XDCAM could fail to encode video when images were noisy \[bug 38728]
* Fixed rare crash which could occur when loading some old 4.4m1 BLGs containing Shapes \[bug 47043]
* Fixed crash on drag and drop in the layer view \[bug 47246]
* Extended BMD cube import to cope with special case of cubes with range and shaper LUTs but no 3D LUT \[bug 47405]
* Added limits to colourspace transforms to prevent infinite or illegal values, tone curves with negative slope, etc. The colour space transforms are the same over the useful range \[bug 43827]
* Added a separate erase brush to the paint operator \[bug 46372]
* Fixed issue with Try not using the correct poster frame \[bug 47229]
* Fixed issue in paint when the "All Strokes" Tab was enabled but no strokes were present \[bug 47373]
* Truelight operator parameters are now correctly disabled when in a locked strip or read-only scene \[bug 47481]
* The "End Alpha" parameter in Dissolve now resets to 1.0, not 0.0 \[bug 46708]
* Improved the display of small numeric values on Blackboard 2 and Slate, such as "Amount" in the Soften operator, which now displays to three decimal places rather than two \[bug 29317]
* Fixed an issue where Sony VENICE files with resolutions other than 4096x2160 were incorrectly marked as trimmable \[bug 47307]
* Fixed issue with the Layer View not updating if the stack changed during a drag action \[bug 37310]
* Paint stroke should no longer cause a shift from the centre when scaling down/up from the working format \[bug 46945]
* Avid "Color Adapter" effects are removed from AAFs when Remove Avid CCs is selected during AAF update \[bug 47535]
* Fixed potential crash when importing a BLG containing shapes that have cloned curves \[bug 47247]
* Fixed an issue where the ScreenAspectRatio element in Interop DCPs could contain values other than 1.33, 1.66, 1.77, 1.85, 2.00 and 2.39 \[bug 47612]
* Paint matte no longer will be cut off when changing viewing format if it is larger than working format \[bug 47585]
* On Blackboard 1, Blackboard 2 and Slate, the "Return to Strip" desk button in the Tracker operator has been updated to work with all the correct strip types \[bug 47332]
* Improved smoothness of scene open progress panel \[bug 47404]
* Fixed an issue on Blackboard 2 and Slate where the "Inside/Outside" desk button would go blank if there was no matte \[bug 47743]
* Fixed bug which could result in negative event numbers being written to a CMX3600 when exporting an EDL for selected shots in a sorted Shots View tab \[bug 46924]
* Fixed crash when group grading a Matte Tool containing an Edge Filter while in a stereo scene \[bug 44990]
* Fixed next/previous poster frame navigation when timeline filtering enabled \[bug 46486]
* Fixed bug which could cause the cursor to jump when 'Try'ing a grade from the DBS with timeline filtering enabled \[bug 46357]
* Reduce console output when opening old scenes \[bug 46535]
* Fixed Scratchpad "Original Version" toggling when playback filtering enabled \[bug 46356]
* Fixed an issue that could cause conform to fail with an error message when a source sequence had keycode embedded in it \[bug 47826]
* Re-aligned the layer view matte selection highlight \[bug 47525]
* Fixed issue with the layer view changing the cursors rendering mode and not setting it back \[bug 47688]
* Fixed bug which could cause incorrect matte (or matte overlay) mode display for composite layers with bypassed operators \[bug 47909]
* The ASSETMAP and ASSETMAP.xml files present in DCPs are no longer recognised as movie files. Use the corresponding CPL-file instead \[bug 47687]
* Apply SDL Events conform option is no longer given for files that are not a .edl containing SDL data \[bug 47998]
* Made the Tracker numbering better in the Layer View \[bug 29030]
* Clone paint no longer slows down rendering when there is an extreme perspective transform but instead causes a render failure \[bug 47653]
* Stopped doing any layer number or reference layer number consistency checking on broken stacks \[bug 48125]
* Fixed issue with the cursor position in the cutview not being correct \[bug 48105]
* Fixed the "Next Ungraded Shot" and "Previous Ungraded Shot" Actions \[bug 48171]
* Layer button double-tap behaviour on Blackboard, Blackboard 2 and Slate has been changed. By default, a double-tap will select the bottom layer in the stack. Alternative behaviour of selecting a higher-numbered layer on double-tap can be accessed via the "Layer Selection Double Tap" preference, which has moved to the Timeline section of the application preferences dialog \[bug 44494]
* Allow timecode and keycode columns to be resized in Shots View \[bug 48264]
* Fixed issue with the the shots view displaying the incorrect CDL values \[bug 48257]
* Prevented the paint parameters being changed when a stroke is being drawn \[bug 47329]
* Fixed several issues with Prepare For Review \[bug 43435]
* When copying a file sequence in FLUX Manage, the destination directory is refreshed to show the copied sequence \[bug 47041]
* Fixed crash reading a TIFF file that is 1 pixel high \[bug 47727]
* Improved Colour Space Journey View warning when there is no DRT selected \[bug 47756]
* Fixed crash in Queue Monitor View when rapidly clicking \[bug 47759]
* Fixed failure to start flux service when preferences database cannot be contacted \[bug 47821]
* Added Colour Space Journey View warning when Input and Stack colour space are both DCI: 2.6 Gamma / X'Y'Z' \[bug 47850]
* Fixed crash when Cuts View has a specific size \[bug 47926]
* Fixed behaviour when cancelling a directory search in FLUX Manage \[bug 47963]
* Improved reduction in scene size after using Clear Undo History on a scene that has been rendered many times \[bug 48008]
* The Colour Space menu on FLUX Manage View now shows the colour spaces as the Input Colour Space menu, which can be edited from Manage Colour Spaces \[bug 48205]
* Fixed crash in renderer \[bug 32792]
* Fixed import of Circle Take metadata \[bug 48039]
* Fixed crash when picking in BaseGrade with a colour space that couldn't be evaluated \[bug 47207]
* Fixed Job Manager host list not updating after editing \[bug 48210]
* Fixed tnd service not starting if its cache folder has been deleted \[bug 48203]
* Fixed paint rendering error on MultiGPU systems when using small strokes and non-working format viewing formats \[bug 48246]
* Desk firmware updates now prevent the user from putting the wrong firmware on the version of hardware already present by making sure that the major version numbers of installed and proposed firmware match \[bug 46100]
* Using Flip and/or Flop in a Sequence operator no longer softens the image, nor crops the edge \[bug 25159]
* The "Keyframe Toggle" desk button can now control keyframes in DKey \[bug 48514]
* Added conform option for FrameFlex layer number \[bug 48417]
* Digital Cinema Packages (DCP) and JPEG 2000 MXF files now set the DCI\_XYZ colour space from metadata when inserted \[bug 48304]
* Fixed issue with FrameFlex scale not matching Avid for some AAFs \[bug 48416]
* Fixed issue with FrameFlex not matching Avid for some media formats \[bug 48278]
* Ensure correct tracker strip tab selected when adding a new perspective track to a primitive (eg. a shape) \[bug 48726]
* Fixed issue in paint where clone and colour strokes were being placed into the same layer \[bug 48774]
* FrameFlex strip is no longer added when no transform is necessary, crop operator is reset correctly \[bug 48704]
* Support for keyframed FrameFlex effects has been added \[bug 47509]
* Fixed an issue where fl-kdmtool incorrectly changed unrecognised key types in the XML metadata to 'MDIK'. This affected e.g. 'MDEK'-type keys for Dolby Atmos audio \[bug 48827]
* Fixed failure with temporal operators (e.g. Denoise) applied at the start or end of a sequence, when there is was a cached operator above the temporal operator \[bug 48867]
* Clone brush paint shifts wrongly when using a perspective transform and switching to a viewing format that is larger than the working format \[bug 48771]
* Fix clone brush not working correctly with interlaced material \[bug 48157]
* Added substitutions to LUT Export for: Source Frame Number - %M, Source Timecode as Frame Number - %H Event Number - %E \[bug 47184]
* Fixed crash when drawing a paint stroke and holding the pen still at the end of the stroke \[bug 48939]
* Fixed an issue where some 1080i DNxHD encoded MXF files would appear to have a height of 2160 \[bug 48933]
* Added preference to select Dissolve strip added when the Smart Dissolve macro is executed \[bug 46168]
* The Compress Gamut operator parameters are now mapped to the trackball rings of any control surface \[bug 38304]
* Reinstated %nW substitution syntax in Shots View. When %W is used as a column value or expression it is substituted with the Shot Filename. If %5W is used for example, the first five characters of Shot Filename are substituted \[bug 47193]
* ASC CDL data can now be read from sub-clips in .aaf files \[bug 49054]
* Fixed crash when cancelling the progress panel when dropping a folder from FLUX Manage View onto Timeline View \[bug 49005]
* Fixed issue with exporting a LUT in a stereo scene failing silently \[bug 46592]
* Fixed issue with exporting a LUT in a stereo scene failing when the scene contains spatial operators, like Stereo Alignment, that are in 3D mode (with separate parameters for left and right eyes) \[bug 49071]
* Improved text rendering performance (including burnin) \[bug 48341]
* Fixed issue with dragging to the end of the Cut View when a playback navigation filter is active \[bug 48872]
* Fixed an issue on Blackboard, Blackboard 2 and Slate which caused inside grades to be incorrectly copied to the outside on RGBKey, MatteXYZ and Paint mattes. This behaviour is now fully controlled by "Automatically initialise outside grades" in the application preferences \[bug 48578]
* During conform the tape name of another clip isn't applied to clips with a blank tape name \[bug 46275]
* During conform tape names are now read from sequence metadata when not specified in the EDL \[bug 49066]
* Fixed "Use Cursor Settings" button in Still Export View not correctly transferring Truelight settings \[bug 48871]
* Fixed quoting of strings sourced from Media Decode Parameters \[bug 49040]
* Fixed a crash after recalling a group with shot(s) no longer in the timeline and turning the grouped grading on \[bug 48180]
* Fixed Smart Paste and Smart Paste Grouped when the selected strip was a matte \[bug 48048]
* Clip wrapped AES and BWF audio in MXF can now be read, and decode performance of clip wrapped audio has been improved \[bug 49188]
* Creative LUT files which are referenced by R3D movie files and are in the same folder as the R3D files are now copied when the R3D files are copied or consolidated \[bug 49021]
* Fixed flickering status messages sometimes seen at the top of file browser columns \[bug 45373]
* Menus with submenus are now positioned to the left of their parent menu if they're too close to the right edge of the screen \[bug 9785]
* Grid Warp Blackboard Overlay button now disables only the Grid Warp Overlays \[bug 48892]
* Enabled resizing of Shots View columns Tint, Length, Event, and Thumbnail \[bug 46322]
* Fixed poster frame positions not being copied when pasting \[bug 49270]
* Fixed failure to load scenes after updating an OFX plugin to a version that no longer uses one or more parameters \[bug 49305]
* Fixed crash when doing a blackboard paste or an Apply on a empty location in the timeline \[Bug 48756]
* Fixed appearance of open scenes in Job Manager \[bug 40018]
* Fixed corruption seen when decoding 6054-pixel width Sony VENICE media at half-resolution \[bug 48358]
* Fixed crash when setting render filename template to some unusual values \[bug 48929]
* Fixed creating of /vol/images symlink on macOS \[bug 49172]
* Fixed incorrect reading of OpenEXR files which have a Display Window that is the same width as the Data Window, but a shorter height, when using the Data Window as the Input Format \[bug 49275]
* Fixed issue with paint picking selecting the wrong colour due to the viewing format being different \[bug 49210]
* Removed non-functional preference "Swap Next/Prev Cut/Poster Controls." In order to do this, use the menu entry in Navigate menu instead \[bug 49152]
* Fixed "Sequence types cached in input strips" preference for ARRIRAW and Sony RAW \[bug 49150]
* Fixed Job Manager crash which could occur if one chose "Sort Jobs by Size" before any jobs had been shown \[bug 49298]
* Fixed BaseGrade's Contrast having no effect below 0.5 and above 1.5 \[bug 42255]
* Removed restrictions on gallery job and scene names - Upper case characters and periods can now be used. This also fixes the issue where using %J in the Gallery Job didn't work properly if a job name contained upper case characters \[bug 47045]
* Fixed missing "Snapshot" text on the image when a snapshot has been taken \[bug 46149]
* Fixed potential hang when jumping to previous poster frame \[bug 47867]
* Fixed failures when DRT cube files are stored in subfolders in /vol/.support/etc/colourspaces \[bug 49418]
* OFX operators and Shader operators with optional inputs can no longer be 3D-split in a stereo scene, to prevent crashes \[bug 49429]
* Changed lower limit of UI font size preference \[bug 49358]
* Scratchpad grab and recall now obey the copy and paste protect categories \[bug 35792]
* Fixed potential crash when deleting a mark/strip category \[bug 40235]
* Fixed "Legal to Full Scale" option on Sequence being incorrectly cleared when changing the sequence \[bug 49272]
* Fixed frame numbers reported in "Scene has sections that have not been analysed for Dolby Vision" error when exporting Dolby Vision XML \[bug 49184]
* Fixed failures in Cuts View when using some OFX plugins on a system with a low-VRAM UI GPU \[bug 49431]
* Increased maximum sensitivity of trackballs, trackball rings, and encoders to 5 to allow for greater freedom when adding acceleration and normalised Tangent gearings to better match the Blackboard 1, Blackboard 2, and Slate \[bug 48310]
* Fixed incorrect assignment of %C when a file path uses a longer folder name (e.g. with the container set to /vol/abc and using media from /vol/abc-2) \[bug 49594]
* Fixed aspect ratio metadata written to Avid OP-Atom MXF files which are neither 4:3 nor 16:9 shaped \[bug 49553]
* Fixed an issue where the interlaced XAVC frame rates available for rendering were doubled due to a discrepancy between Sony and FilmLight notation. Supported interlaced XAVC operating points are: 1920x1080:
  * XAVC HD Intra Class100 @ 25i, 29.97i
  * XAVC HD Long422 25     @ 25i, 29.97i
  * XAVC HD Long422 35     @ 25i, 29.97i
  *   XAVC HD Long422 50     @ 25i, 29.97i

      \[bug 49591]
* Ensure any unused categories in a scene are deleted when clearing that scene's undo history \[bug 48822]
* Fixed issue which caused clip lengths to be calculated incorrectly when updating an AAF \[bug 49554]
* Fixed appearance of burnin text when the Viewing or Render Format has a different pixel aspect ratio from that of the Working Format \[bug 48425]
* DCI compliant JPEG 2000 essence will now be created using the maximum allowed number of DWT decomposition levels. This fixes an issue where the GPU accelerated JPEG 2000 encoder would use fewer DWT decomposition levels than the non-accelerated encoder, and also means that 4K essence will now use 6 levels instead of 5 \[bug 49616]
* Added diagnostic support for Adaptec 315x series raid controller. These controllers also need Flos 6.4.11159 or later \[bug 49476]
* DCI compliant JPEG 2000 essence using a bitrate too close to the limit of 250 Mbit/s can cause issues with some DCP players. To accommodate this, the default bitrate of this essence has been reduced by 2%. Control of the bitrate of DCI compliant J2C files has been improved and it can now be manually specified \[bug 49433]
* Fixed crash when resetting a legacy DNG Parameters operator \[bug 49443]
* Connecting removable media while FLUX Manage is open now opens a new browser tab rather than changing the current one \[bug 48806]
* Improved the description of H.264- and HEVC-encoded source media in QuickTime containers. Bit depth and subsampling information is now part of the source description. AVC Profile and AVC Level metadata entries are now added when available \[bug 49638]
* No longer crash when conforming some CMX3600 EDLs with overlapping strips, instead attempt to resolve the strips into multiple tracks \[bug 49507]
* When picking from the image the colour panel and colour well will interactively update \[48938]
* Fixed crashes in Audio Waveform View when audio media has more than 16 channels \[bug 46662]
* Added an option to Timeline Sort View to simplify a scene so that it is able to be opened by Daylight. This option can also check if a scene is able to be opened by Daylight \[bug 45848]
* Fixed occasional crash when importing BLG resources \[bug 47627]
* bl-shots no longer fails when used on a scene containing an unknown OFX operator \[bug 47133]
* Fixed incorrect behaviour when double-clicking on a tile in the FLUX Manage tile library \[bug 47136]
* Fixed tooltip on the Input Colour Space control \[bug 47143]
* Fixed crash when scrubbing the timeline very quickly \[bug 48303]
* Fixed potential crash after deleting a Slate layout from Chalk \[bug 45642]
* Fixed issue with the stereo split button still being active in a read-only scene \[bug 46510]
* Fixed recognition of 60@30 fps drop-frame, 50@25 fps and 48@24 fps timecodes in MXF media \[bug 49685]
* Fixed failure to correctly update a Sequence's DRT when importing a BLG \[bug 47020]
* Fixed an issue causing thumbnails to not be displayed on the first run after installing a licence. Services are now restarted after installing a licence \[bug 46668]
* Fixed mattes being too bright when set to "Use Viewing Colour Space White Point" and viewed in an HDR Viewing Colour Space \[bug 47046]
* Fixed bug preventing some UI elements (like ganging state, extended ranges etc) from being restored when a grade is stored as a BLG and then recalled \[bug 45632]
* The handling of MXF indexes and partitions has been restructured. This fixes an issue where MXF-files with many partitions could be slow to open. It also adds decode support for some previously unsupported MXF flavours, e.g. AS-11 \[bug 34020]
* Fixed issue with Chalk for Slate when importing from a file would wipe all non-Home customisation \[bug 45705]
* Fixed issue with temporal operators and rendering at frame rates that are different to the scene's working frame rate \[bug 46781]
* Fixed issue causing variable retime option to be missing when conforming from FCP7 XMLs \[bug 49709]
* Fixed issue affecting Blend Controls on Blackboard and Slate \[bug 46604]
* Improved naming on some blackboard and slate buttons \[bug 45840]
* Added function to rename Chalk layouts \[bug 46042]
* Added Blackboard and Slate action to reset the Matte XYZ \[bug 46731]
* Added Blackboard and Slate actions to reset and select the Matte Sequence and Matte Reference operators \[bug 47028]
* Corrected the text display when adding an "Insert Layer" button to the Slate using Chalk \[bug 47071]
* Support nvme-based cache on Z840 (as a replacement for SSD cache) \[bug 49629]
* Fixed a reference issue in the context of a composite layer. A reference could not point at any foreground layer when the foreground layer 0 was a reference itself (e.g Alpha reference or Dkey reference) \[bug 46441]
* Fixed rendering of 4:2:2 Apple ProRes movies when zooming \[bug 49623]
* Lowered the sensitivity of encoders to make them more user friendly \[bug 37298]
* Removed the Default Stack Colour Space option from Scene Settings because using it incorrectly can easily cause errors in colour pipelines \[bug 49772]
* Improved the behaviour of some OFX plugins using dialogs (e.g. Sapphire Preset Browser) \[bug 34954]
* Fixed failure of DRTs which use other cube formats \[bug 49628]
* Fixed bug which meant that only one GPU was used on a Mac with multiple GPUs, if the Mac was configured as a 'ws' in its cloud.cfg \[bug 49618]
* Fixed missing Shot Timecode metadata for Audio Renders when audio file is specified as Scene Audio in Scene Settings \[bug 49674]
* Improved Colour Space Journey View for OFX operators \[bug 49695]
* Fix crash in paint operator with non-existent matte resource \[bug 46095]
* Fixed occasional crash in Multi-Paste with weird stack morphologies \[bug 48409]
* Fixed FLUX Manage failing to cache thumbnails \[bug 49856]
* Fix 'Bind Failures' in Denoise using the optical flow option. It will only have an effect in newly created operators \[bug 47091]
* Fixed performance issues when using Truelight cubes (in Cursor View or a Truelight operator) located in folders with very many cube files \[bug 49909]
* Fixed an issue where the "Legal to Full Scale" option on Sequence could be incorrectly set when reading MXF-files with certain transfer functions, notably "Rec.709" \[bug 49952]
