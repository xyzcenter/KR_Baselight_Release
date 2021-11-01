# Baselight Release 4.4.6441 (2014-01-09)



## New Features Since Baselight 4.4.6396

* Added support for Quadro K600 and Geforce GTX 780 Ti graphics cards \[bug 26406]
* Added access to "Wipe" and "1x1" display modes via buttons above left trackball when in View mode on Slate desks \[bug 26326]
* Added Gang Cursors button to Display Slate layout \[bug 26227]
* Added Show Versions button to Keypad Slate layout \[bug 26329]
* Changed Setups so that the default Input Colour Space for new scenes is now "No Conversion". To return to previous Baselight 4.4 behaviour change this to "Automatic/From Metadata"; to emulate Baselight 4.3 behaviour change it to "From Input Format" \[bug 26246]

## Bug Fixes Since Baselight 4.4.6396

* Fixed issue where Slate could appear unresponsive if the same Slate Layout was activated simultaneously on both sides of the desk \[bug 26321]
* Fixed issue where tracking was slow with some large resolution material \[bug 26393]
* Fixed occasional Slate-related crash when opening and closing "DBS" Slate Layout \[bug 26321]
* Fix for crash when undoing stereo splitting of strip \[bug 26221]
* Fixed crash when an image thumbnail is missing in the layer view \[bug 26213]
* Fixed crash deleting a matte from the matte selector \[bug 25729]
* Corrected the sRGB colour space which had a minor error in one direction of the transfer function (affecting the blacks in conversions to sRGB) \[bug 26425]
* Fixed hang in Baselight when reading images from movie files or round-robin files on cluster systems or via the network \[bug 26463]
* Fix for incorrect updating of Slate FilmGrade trackball reset buttons when panel not in "Home" mode \[bug 26429]
* Fixed crash when bl-shots is run on a scene with single input and use matte turned on \[bug 26358]
* Fixed LUT export when the scene's working colour space is not the working format's default \[bug 26369]
* Fixed failure to render certain gallery thumbnails due to a colour space error \[bug 26484]
* Fixed black/white point lines on histogram not moving when cursor colour space changes \[bug 26166]
* Fixed a small offset error in the sub-blacks region of the convertToLinear functions of the Sony colour spaces \[bug 26502]
