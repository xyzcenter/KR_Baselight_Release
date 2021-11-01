# Baselight Release 4.3.5617 (2012-09-24)



## New Features Since Baselight 4.3.5546

* Added 48fps and 48@24fps timecode options.
* Added additional metadata support (including timecode) when reading CinemaDNG files.
* Sony SStP MXF files can now be read and written on older Baselight hardware which used AMD CPUs.
* Added ability to write Sony MXF using SStP/L2 SR HQ 4:4:4 at 10- and 12-bit, and for writing 2048x1080 in SStP/L2 SR SQ 4:4:4 at 12-bit.
* Significant improvements to DNG decoding quality, speed and user controls. Existing strips can be updated using the "Update Sequence behaviour" button (next to the Sequence File Name).
* QuickTime and MP4 movies can now be optimised for "fast start" (streaming) playback. This will increase rendering time, particularly when rendering long movies.
*   Added support for reading Indiecam RAW data stored in QuickTime movies. Because the movie contains nothing that distinguishes it from a "v210" uncompressed 4:2:2 movie, a new Indiecam Decode operator is added in Baselight to allow you to choose the encoding and camera model.

    PLEASE NOTE This should be considered "beta" functionality until advised otherwise. Support for white balance, tone curve, sharpening etc may be added in a later release. If you encounter issues please report them to baselight-support@filmlight.ltd.uk
* The de-mosaic algorithm has been improved. The algorithm preserves the original mosaic values, but the interpolations look sharper and have fewer coloured artefacts. The cross-coupling filter has the same effect with the same threshold values; but turning the filter up may now undo our new sharpness, so we recommend only turning up the cross-coupling filter for the images that need it. Chromatic aberration in the camera can still give some patterns, but the effects are now more subtle.
* The ARRIRAW default crosstalk setting has been changed from 0.0 to 0.3. This is enough to remove the maze patterns seen in pinks and some other colours in the worst cases we have met. Increasing the crosstalk filter setting further will lose some high-frequency information. If your images have fine detail, and no flat patches of saturated colour, then you may want to reduce the crosstalk setting.
* Inserting ARRIRAW files now adds a Sharpen operator to the Input Layer. This should give a similar sense of sharpness to ARRI's ARC tool. If you remove the Sharpen then the image will contain the original mosaic pixel values.

## Bug Fixes Since Baselight 4.3.5546

* Fixed crash in video grade when set to CDL mode and hitting reset on the Blackboard \[bug 21533]
* Fixed edge errors from Pan\&Scan of ARRIRAW material \[bug 21556]
* Fixed errors after deleting and then recreating a job \[bug 21606]
* Fixed job deletion after unlocking scenes \[bug 21615]
* Improved robustness of shader cache \[bug 21618]
* Fixed issue when using scopes with a viewing mask on multi-node systems \[bug 21485]
* Fixed increasing memory usage when reading movies on multi-node systems \[bug 21715]
* Fixed hang after an error rendering to QuickTime via a Baselight Kompressor \[bug 21728]
* Fixed black stripes on clusters when interactively editting above a cached strip \[bug 21729]
* Fixed crash when using %c substitution in Shots View \[bug 21732]
* Fixed regression in VectorScope rendering \[bug 21733]
* Disabled background caching when mouse/pen in motion on image display \[bug 20635]
* Fixed crash on startup when running bl-render on Mac OS X 10.5 Leopard \[bug 21467]
* Fixed render failures in scenes using temporal strips (Temporal Degrain, DSpot etc) under explicitly cached strips \[bug 20871]
* Fixed crash in flux/fl-cp when converting movies without a "." in their filename \[bug 21736]
* Fixed reading Avid MJPEG 2:1p MXF files.
* Fixed bug which could cause a scene to be un-openable after applying a stack from another scene containing strips with marks \[bug 21806]
* Added 0203 Keycode prefix.
