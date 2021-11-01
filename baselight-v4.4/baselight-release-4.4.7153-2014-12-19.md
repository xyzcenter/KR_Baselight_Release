# Baselight Release 4.4.7153 (2014-12-19)



## New Features Since Baselight 4.4.7137

* Film Grade now has a neutral exposure balancing function. When the Balance Exposure button is pressed, picking a colour (or an area of colours) from the image will change the Exposure to make that colour neutral \[bug 30487]
* Added support for ARRIRAW files from Alexa 65 camera (using Baselight decode only) \[bug 30292]
* Scene Detect now has a Pixel Threshold slider. This adjusts the level of difference between corresponding pixels in adjacent frames which is necessary in order for the pixels to be counted as different. This can be useful on low-contrast material \[bug 30442]
* When using the filter button in a browser, the filter text is now selected for text entry, saving you a click \[bug 18010]
* The scroller buttons shown when tabs do not fit in a window now scroll the tabs left and right continually while the button is pressed \[bug 30425]

## Bug Fixes Since Baselight 4.4.7137

* Prevented custom colour spaces containing errors from causing crashes \[bug 30455]
* Fixed Smart Dissolve to preserve strip caching and bypass states on both sides of the dissolve \[bug 30461]
* Fixed right-click in the area below the last entry in a text list (e.g. on Jobs Manager) \[bug 30428]
* Fixed crash when using a Tangent Element panel \[bug 30364]
* Fixed bug which may have prevented picking on the image when a scene was initially opened \[bug 30492]
* Fixed crash when enabling Anaglyph or Interlaced stereo display modes on Baselight FOUR/EIGHT systems using AJA Kona 4 display hardware \[bug 30382]
* Fixed initialisation of Kona 4 SDI outputs when switching between between HD/2K, stereo HD/2K and 4K display modes \[bug 30436]
* Fixed 12-bit stereo SDI output support on systems with AJA Kona 4 display hardware \[bug 30448]
* Fixed an issue where MXF OpAtom files written by Avid could not be read \[bug 30472]
* Improved handling of conflicts between user/host/site preferences for control panels, user preferences now override host/site preferences \[bugs 29660, 30432]
* Fixed render failure "Render swaps 200 tiles: only 100 tiles may be swapped" \[bug 28314]
