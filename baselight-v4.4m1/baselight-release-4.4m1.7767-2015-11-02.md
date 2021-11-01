# Baselight Release 4.4m1.7767 (2015-11-02)



## New Features Since Baselight 4.4m1.7687

* Added support for reading CinemaDNG files with lossy compression (e.g. from Blackmagic URSA) \[bug 33130]
* Added support for reading and writing 4:2:2 and 4:4:4 Y'CbCr DPX files, at 8-, 10- and 16-bit depths \[bug 33775]
* It is now possible to render to QuickTime movies using Apple ProRes codecs of any width \[bug 30699]
* Added a View Luma option to the Cursors menu and the Cursor View "View Channel" control \[bug 33815]
* Added filename templates to CDL ccc file export \[bug 33841]
* Added "Expo Demo" for Blackboard 2 and Slate desks. Activate with "-deskdemo" command line parameter, or adding "Expo Demo" Action in Chalk. Note: Cannot be exited when launched from command line, otherwise press & hold any desk button to exit
* The Gallery View now stores an EXR still frame when a movie file is grabbed to the gallery. This means that if the original media is no longer available, the gallery will continue to show a thumbnail, which can be scrubbed to show a full-resolution image. \[bug 26004]
* Added new "Rec.2084: ST 2084 PQ / Rec.2020" colour space. This colour space can be used for grading on HDR monitors. Please be aware that all standard DRTs will compress the image so they cannot be used with this colour space. Please contact Baselight Support if you want to do film-style grading for HDR displays \[bug 33925]
*   Updated to RED SDK v6.0.4. This includes bug fixes and:

    * Weapon 8K and Raven 4K support
    * Support for Mysterium-X Monochrome decoding on RED Rocket
    * Rec.2020 colourspace support
    *   Minimum required Rocket-X driver is 2.1.24.0 with firmware

        1.3.19.40
    *   Minimum required Rocket driver is 2.1.23.0 with firmware 1.1.18.0

        \[bug 33479]

    PLEASE NOTE: the RED SDK does not support GPU decoding on FilmLightOS 2.1. If your system is running FilmLightOS 2.1 you will need to upgrade it to FilmLightOS 6.4 to be able to read R3D media using GPU acceleration.
* Added Inside/Outside button to Chalk for Blackboard 2 (in Button Categories: Stack Manager) \[bug 34095]

## Bug Fixes Since Baselight 4.4m1.7687

* New splinePoints{5} default for Looks \[bug 33111]. This can be overridden by adding a splinePoints{..} argument in the Look profile. The Look was used well beyond the range of the data points so there is no complete fix, but this helps
* Fixed bug where bypassing a layer would give an incorrect result when 'Inside Source' dropdown was set to anything other than 'Layer Input' \[bug 33783]
* Improved the error message shown when QuickTime write fails e.g. due to no space left on device \[bug 33761]
* Versioned Denoise to allow old scenes to be openened \[bug 33521]
* Fixed reading of some badly-formatted QuickTime movies written by ARRI cameras \[bug 33818]
* Fixed incorrect display of Matte Merge strip icons on Blackboard and Slate desks \[Bug 33826]
* Fixed an issue where QuickTime files with broken edit lists were handled differently on Linux and Mac \[bug 33821]
* Fixed bug where having a viewing format different from the working format would cause trackers and keyers to fail \[bug 33820]
* Rendering to Apple ProRes using Video LUT: Clip to Legal or Video LUT: Soft Clip to Legal now infers that the images are legal-range and scales them correctly \[bug 33842]
* Fix bl-config-video on systems with NVIDIA GTX 285 GPU \[bug 33877]
* Reverted changes to audio TC tracks for MXFs, as this broke Relink & ALE merge in Avid Media Composer. Audio tracks in MXFs rendered from Baselight & Daylight will now have the same timecode as the video track. Sound TC must be merged into the bin using ALE \[bug 33319]
* Fixed bug that prevented rendering to MXF when the source material included keycode \[bug 34028]
* Fast Start QuickTime movies are no longer written with compressed header atoms, since this can cause issues in other software packages \[bug 33639]
* Fixed incorrect subtitle font kerning \[bug 33888]
* Fixed bug where grabbing to the gallery via drag-and-drop from the Cut View in "Display sRGB" mode would produce thumbails which would use an sRGB colour space when scrubbing. \[bug 33903]
* Fixed an issue where the timecode atom in some QuickTime files could cause the file to take a long time to open on Linux \[bug 33909]
* Fixed minor issues in the "Dolby: ST 2084 PQ / P3 D65" colour space \[bug 33925]
* Fixed problem with keyer picking when a viewing colourspace conversion was applied \[bug 33931]
* Selected strips with differing names can now be renamed together from the "Name" field at the top of Parameters View if Grouped Grading is enabled \[bug 22863]
* Fixed crash where trackers would crash on clusters \[bug 33932]
* Reduced benign error message output with hotfix script on netbooted hosts \[bug 33936]
* Fixed copy failues in Flux to and from Kompressor volumes \[bug 33819]
* Fixed decode of DVCPROHD in QuickTime files on Linux \[bug 31596]
* Fixed an issue that caused frames to repeat in some long QuickTime and AVI files on Linux \[bug 33990]
* Fixed consolidate errors with Canon MXF files \[bug 34029]
* Fixed issues with 3.4k ARRIRAW files using ARRI Decode \[bug 34016]
* Fixed failure in AAF export that produced 'Could not lookup component' error message \[bug 30825]
* Fixed an issue that caused the image to freeze when working with XDCAM \[bug 33529]
