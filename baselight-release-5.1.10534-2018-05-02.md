# 베이스라이트 릴리즈 노트 5.1.10534 (2018-05-02)



## New Features Since Baselight 5.1.10418

* Added "Show All Hosts" option to Job Manager which causes every Baselight system on your local network to be shown as a database host \[bug 47258]
* Generation VII Baselight ONE/ASSIST systems are now supported.
*   Due to Baselight for Avid now supporting the rendering of temporal operators in the Avid timeline, checking for temporal operators has been removed from the "Update Avid AAF with Baselight Grades" EDL Export option for progressive scenes. So, it's now possible to export AAFs containing Denoise, Deflicker and other temporal operators.

    Because Baselight for Avid doesn't support temporal operators in interlaced projects, the check has been retained for interlaced scenes. \[bug 47362]
* Added "Full Area" Guide option to Cursor View \[bug 46071]
* Time vs Time variable retimes in AAF files are now supported \[bug 39721]
* Added option to the "Marks" menu to delete all marks in the scene of a specific category \[bug 46667]
*   Added Tangent Setup view that allows control over

    * Trackball Sensitivity & Acceleration
    * Trackball Ring Sensitivity & Acceleration
    * Encoder Sensitivity & Acceleration

    The Tangent Setup view is accessible via the Baselight or Daylight menu when Tangent control surfaces are enabled in Preferences \[bug 37429]

## Bug Fixes Since Baselight 5.1.10418

* Improved temporal degrain performance on Gen VII machines \[bug 47301]
* Updated the format of the 'ACLR' atom written when rendering DNx codecs into QuickTime. This fixes an issue where Avid Media Composer version 8.6.5 and later would decode the resulting files very slowly. The legal field in the atom is now set correctly instead of always being set to full range. This fix also ensures that the 'ADHR' atom correctly indicates bit depth and RGB/YCC \[bug 45092]
* Fixed crash in bl-mkscene \[bug 47413]
* Fixed crash when adjusting Truelight parameters in cursor \[bug 44775]
* Fixed incorrect frame time/offset calculation of strips above layers containing only unmodified grading operators in misaligned stacks \[bug 47340]
* Fixed crash selecting OFX operator from the right-click menu on a layer \[bug 47437]
* Fixed crash from using Boost Shadows with DRT with no inverse. \[bug 47406]
* Fixed precision loss when generating Autodesk CTF from cube with a very non-linear input gamut LUT. \[bug 46363]
* Fixed an issue where some AVC-LongGOP encoded MXF files would be very slow to decode \[bug 47425]
* Fixed an issue that caused rendering to DNxHR HQ, LD & SQ codecs to fail with a message about precision of input component being too low \[bug 47372]
* Fixed an issue that caused some MXF-files to be unsupported \[bug 46658]
* Fixed inaccuracies in constant retimes in AAF files \[bug 41072]
* Fixed crash when importing FCP7 XMLs with variable retimes \[bug 46464]
* Fixed issue whereby the keyframes of variable retimes in AAFs were placed incorrectly if the frame rate of the clip with the retime differed from the primary frame rate of the AAF. \[bug 46186]
* Fixed crash when importing FCP7 XMLs with retimes of speed 0.0 \[bug 45884]
* Fixed issue with Wacom not being configured correctly \[bug 40613]
* Fixed issue that prevented Baselight or Daylight from playing back on macOS when the system hostname is set to something that cannot be resolved to an IP address \[bug 47441]
* Fixed DVI/HDMI/DisplayPort output from processing gpus \[bug 40543]
* Fixed clipping issue when playing or rendering from movies or audio files containing normalised audio data \[bug 28217]
* Changed the default Image Transform Colour Treatment to Native, because this gives better results on modern wide-gamut camera media than the Linearised setting. You can revert to Linearised in Setups or by editing your Scene Templates \[bug 32821]
* Fixed crash on Consolidate \[bug 47273]
* Fixed repeated import of the same DRT every time a BLG is inserted \[bug 47311]
* Fixed a bug in bl-conform's handling of the --template option \[bug 47422]
* Fixed issue with invalid/missing audio output on AJA SDI hardware on macOS \[bug 47480]
* Updated keyboard shortcut documentation \[bug 47482]
* Fixed changes to Ref TC column or Circle Take column in Shots view not taking effect \[bug 47385]
* Fixed AAF import issue whereby multiple 3D Warp effects caused unintended warnings and could not be applied in some cases \[bug 47471]
* Fixed failure when using Dolby Vision analyse on a shot with missing media \[bug 47502]
* Fixed Dolby Vision strips incorrectly showing "Found analysis data in another Dolby Vision strip" \[bug 47504]
* Fixed Dolby Vision analysis of a black frame reporting "This shot has not been analysed" \[bug 47505]
* Fixed slow Dolby Vision analysis \[bug 47503]
* Fixed crash when trying to link an existing one point track \[bug 47439]
* Fixed performance reduction in stacks containing a mixture of ColourSpace operators and References to upstream grading layers \[bug 47479]
* Fixed thumbnails of ProRes 444 media \[bug 47237]
* Fixed an issue that prevented the render panel from working with DCPs using multiple reels \[bug 47515]
* Fixed an issue where some DCP parameters were not cleared properly when unset \[bug 47517]
* Fixed bug in "Update Avid AAF with Baselight Grades" when checking for stacks containing multiple Sequence strips \[bug 47362]
* Fixed bug which prevented the output image from updating when changing a layer's "Inside Source" mode (if none of the layer's operators had been modified) \[bug 47513]
* Fixed ARRIRAW chromaticities being written into rendered OpenEXR files \[bug 46107]
* Fixed crash when applying an operator preset \[bug 47477]
* Fixed issue where some operations (e.g. Dolby Vision analysis, Cache All Cursors) would occasionally pause unless the mouse was moved \[bug 47545]
* Fixed bug which could result in incorrect frame ranges being calculated when rendering based on shot category \[bug 47590]
* Fixed crash when using Prepare For Review on a scene with a basic working format \[bug 47642]
* Fixed the operations queue sometimes failing to progress, due to a pre-render task not correctly completing \[bug 47638]
* Fixed hang when rendering with RAW input media and burnins \[bug 47631]
* Fixed incorrect errors when exporting Dolby Vision XML from scenes with Dissolve strips \[bug 47664]
* Fixed issue when after linking an area tracker to a shape, and modifying its position or size, the shape would jump \[bug 47078]
