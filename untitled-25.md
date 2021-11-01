# Baselight Release 4.3.5524 (2012-08-03)



## New Features Since Baselight 4.3.5416

*   This release has required a database version increment. This will

    prevent scenes saved from this version of Baselight from being

    opened in previous versions of Baselight.

### Area Tracker

* It is now possible to rotate the tracking rectangles on keyframes. This can be done by either dragging the tracking box pivot overlay or by using the middle trackball ring.
* The 'new AT' button on the shape strip can now create a rotated rectangle to best fit the original shape.
* The 'Trackers' and 'Area Trackers' tabs in the tracker strip are now highlighted in purple when they contain trackers.
* You can now link a tracker to an existing shape or a transform using by:
  * Selecting the tracker you want to copy.
  *   Tapping 'Copy' on the Blackboard (or Ctrl+Shift+C on the

      keyboard).
  * Selecting the shape/transform you want to apply the tracker to.
  * Tapping 'Paste' on the Blackboard (or Ctrl+V on the keyboard).

### Sander

*   Added new Sander operator. It is accessible either from the 'Insert' menu or the Matte Tool.

    Sander allows to remove speckles (white regions inside a black one) and holes (black regions inside a white one) without modifying the geometry of the matte. It uses the following parameters:

    * Search Size: Distance in pixels from the central pixel, defining region to consider. The search size varies from 0 to 4, with 0 doing nothing. Increasing the size tends to remove bigger holes and speckles. The maximum radius can be increased to 10 using 'Extended Ranges'.
    * DSpeckle: Threshold allowing to select the speckles in the matte for removal. Increasing this value will remove more speckles.
    * DHole: Threshold allowing to select the holes in the matte for removal. Increasing this value will remove more holes.
    * Colour Difference: Threshold allowing to control the amount of work produced by the two previous thresholds. Increasing the Colour Difference increase the amoung of work done by the previous threshold.

### Scopes Improvements

* Pan/Zoom: The scopes can reflect the visible portion of the image when panned & zoomed in the display. This is user selectable by selecting the Pan/Zoom option on any of the scopes right-click context menus.
* Truelight/Combiner: The scopes can reflect either the raw image, with the cursor's Truelight profile applied, or both Truelight and combiner settings.
* Luma/Chroma waveform: The Luma Waveform has an optional Luma/Chroma mode, which displays the chroma components overlaid on the luma. (This can't be used at the same time as the Y'CbCr Parade though and that view will display an error cross).
* Vectorscope rotation: The Vectorscope can be rotated +/- 180 degrees. To match the default trackball orientation, apply a rotation of -13 degrees.
* Chromaticity scope: Variant of the Vectorscope, selectable from the Vectorscope context menu. This maps colours within the selected gamut, either Rec709, EBU, SMPTE-C, or P3 (either RGB or XYZ) mapped onto a CIE xy plot.
* Video Legal Overlay: The waveform overlays can be set to display either video legal or full range markings.

### Performance Improvements

* Improved performance of reading movies that are stored on the PFS (parallel file system) of a Baselight FOUR/EIGHT. A fast-access read-only view of /vol/images is now available under /pfs/images for this purpose. (This functionality requires FLOS 2.1 or later.)
* Increased speed of browsing scenes using Job Manager and bl-lsscenes, particularly when accessing jobs stored on remote database servers and/or calculating scene sizes.
* Improved performance of intermediate caching on Baselight FOUR/EIGHT systems.

### Image Decode Improvements

*   Improved smoothness of ARRIRAW ALEXA tone curve

    The previous LUT-based tone curve has been replaced by a function. This is very similar to the earlier tone curve but smoother.
*   Added Nyquist Filter 'Coloured pixels' option

    De-mosaiced images can show coloured features on bright highlights and sharp edges. Here, the brightness changes over a pixel or two, and there is not enough data to reliably guess the missing colour values. You can also get strange colour values when de-mosaicing images with chromatic aberration, as the colour channels are not correlated accurately.

    The new filter is like a median filter on the chroma channels. It will make a pixel neutral if it has a neutral neighbour. This removes much of the strange coloured fringes. This will remove real image detail too, so if you use it, check the effect on the rest of your image.
*   Improved Colour Crosstalk Reduction filter

    Most digital cameras have alternate lines of red and green pixels, and green and blue pixels. If there is some A/D conversion difference between odd and even lines, this can give 'maze' patterns on the de-mosaiced image.

    The de-mosaic crosstalk filter will average the values if the green values are some threshold outside the range of the green values of the neighbouring lines. Turn up the filter threshold and the 'maze' patterns should go away. This can remove some real image detail too, so if you use it, check the effect on the rest of your image.
*   Improved SIV support

    SIV files now apply the default Silicon Imaging colour transform to bring the colour primaries to Rec.709.

    Log-format SIV files are now converted to linear when read into Baselight in order to be able to correctly apply the white balance and colour transform.
*   Improved de-mosaic algorithm

    The de-mosaic algorithm (used on RAW images such as ARRIRAW, Phantom Cine, SIV etc) has been modified slightly to give better results for sharply-varying features very close to highlights.
*   Improved CR2 support

    Some previously unreadable "RAW" still files (e.g. Canon sRAW/mRAW) are now supported. (These files contain lossless Y'CbCr subsampled data rather than raw sensor data.)
*   Added CinemaDNG support

    Baselight can now read CinemaDNG MXF files.
*   Improved DNG support

    DNG (Adobe Digital Negative) files are now decoded using the Adobe reference SDK. A new DNG Decode operator allows control of exposure, shadow clipping and colour temperature.

    PLEASE NOTE this may change the appearance of existing scenes that use DNG files. You may wish to finish work on these scenes using your previous Baselight version rather than update them.
*   Correction to F65 RAW tone curves

    The exposure of Sony F65 RAW material decoded to Linear and Log (previously called ACES Log) tone curves has been corrected to make them slightly darker.

    PLEASE NOTE this will change the appearance of existing scenes that use F65 RAW material with Linear or ACES Log tone curves. You may wish to finish work on these scenes using your previous Baselight version rather than update them.

### Miscellaneous

* Directory and filename templates in Render View and bl-render can now use %{ISODate} to insert the current date. Several existing % substitutions now have %{...} alternatives which can be used for clarity, as shown in bl-render command-line help, or the help panel on the Render View.
* Added ability to set Reference strip's default input mode to "Previous Layer's Output" and "Previous Layer's Input Image" from the preferences ("Plugins" page).
* Added bookmarks menu to Job Browser.
* When run on the command line, fl-diag now shows module identifiers.
* Added support for reading high frame-rate (HFR) Sony F65 MXFs.
* Added support for DCI 2048x1080 48p and HD 1920x1080 48p display modes.
*   Added initial support for writing Sony SStP MXF files.

    PLEASE NOTE due to restrictions in the Sony libraries used by Baselight, this functionality currently only works on machines with Intel CPUs, which means it will not currently work on older Baselight hardware which used AMD CPUs. This restriction also applies to SStP MXF decoding.

    PLEASE NOTE SStP writing should be considered "beta" functionality until advised otherwise. If you encounter issues please report them to baselight-support@filmlight.ltd.uk
* Added ctrl+0 shortcut for Gang Cursors (previously available in Truelight Player but not in Baselight).
* The preference "In-memory image cache size" which specifies the amount of memory used for caching images has been changed from an absolute value to a percentage of available memory. This change allows better default memory usage across a range of hardware.
* When conforming from ALE, Scene and Take metadata are now set in Shots View.
* Shots View can now be sorted by Clip.
* After long deliberation and due to popular demand, drag-and-drop shot movement in the Cuts View is now disabled by default. It can be re-enabled by switching on "Allow Drag-and-Drop Shot Movement" in the "Cuts View" section of the preferences.
* Added support for Nvidia GTX 680 GPUs.
* Added MP4 to the "Sequence types cached in input strips" preference.

## Bug Fixes Since Baselight 4.3.5416

* Multi-Insert now turns "Use Timecode 2" on if the browser was set to "List Timecode 2" \[bug 20930]
* Uptime now correctly reported in bl-nodemon \[bug 20717]
* Fixed bug which would cause strips with explicit caching enabled to be cached during playback when Timeline Caching set to "Disabled" \[bug 20964]
* Diagnostic network tests are now bidirectional \[bug 20795]
* Fixed problem exporting LUTs from the Shots view when image sequences had Orientation set to Flip or Flop \[bug 21019]
* Fixed conform issue when using 'Tape Name in Header' and remote conform was in use \[bug 20803]
* Fixed Mattetool so it now uses the trackballs \[bug 21105]
* Fixed crashes caused by invalid filename templates in a Sequence \[bug 21110]
* Fixed rendering of Dissolve through matte when one source image is empty \[bug 20868]
* Fixed crash in MatteTool when added without a Blackboard attached \[bug 21123]
* Fixed errors when reading SIV files over 4GB in length.
* Removed the Burnin settings from the tl-player Cursor View as the Player licence does not support burnins \[bug 21136]
* Fixed crash in shapes which occured after creating a tracker from a large shape \[bug 20279]
* Fixed crash with changing multiple stages in the Mattetool while changing the gang \[bugs 20290, 20384]
* Fixed issue where bl-config-xorg could fail to identify when a Blackboard 2 desk was connected \[bug 21060]
* Worked around write hang in StorNext 4.2.2 SAN driver \[bug 21034]
* Fix for Flow Degrain with a matte and bypassed \[bug 21212]
* Fixed incorrect pulldown renders when using explicitly cached strips \[bug 21204]
* Fixed issues with VTRE using DDR decks \[bug 17426]
* Fixed "Raw Image Alpha Channel" in Reference strip when it is used as a matte input to a strip at the bottom of the stack, or as an input to a Dissolve \[bug 18107]
* Fixed several issues using bl-proxygen on compressed OpenEXR files \[bug 21238]
* Fixed failure to show a folder containing a single folder when browsing for a folder (e.g. EDL search directory) \[bug 21154]
* Fixed tone curve shift caused in a Matte Tool using a Matte Curve before a Blur \[bug 21245]
* Fixed occasional render out hangs when rendering to many short movies \[bug 21256]
* Fixed bug in playback cache icon when toggling input strip caching on/off with Timeline Caching disabled \[bug 21272]
* Fixed bug which could result in unrecoverable scenes if Blackboard toggle keyframe button pressed while creating a second shape in a Shape strip \[bug 21280]
* Fixed loss of alpha channel when copying 8- or 10-bit RGBA DPX files using flux or fl-cp.
* Stereo Geometry Fix - fixed additional X/Y-translate not working for very small translations without having a prior fix \[bug 21337]
