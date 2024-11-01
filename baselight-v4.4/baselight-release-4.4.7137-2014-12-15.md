# Baselight Release 4.4.7137 (2014-12-15)



## New Features Since Baselight 4.4.7079

* Updated to ARRI SDK v4.6. This adds support for the "ADA-5 SW" DeBayer Mode for ARRIRAW files.
* Added 32x playback speed option \[bug 28785]
* Added support for Canon LUT formats.
* Added support for reading Panasonic Varicam VRW files \[bug 28919]
* Added 'clip' option to Reference strips when used to reference a matte \[bug 29965]
* Avid ISIS workspaces mounted on a Baselight system are now made available as Cloud Media \[bug 27852]
* Blackboard Stack Manager can now access more than 5 Inside/Outside operators by holding  \[bug 22737]
* A warning is now presented in the render UI when creating a DCP with a non-standard framerate \[bug 28528]
* Digital Cinema Packages (DCP) can now be created either using the current SMPTE standard, or the older Interop standard. When creating a SMPTE package, the audio channel format label used can be configured in the codec parameters dialog \[bug 28410]
* The version label used when creating DCPs can now be configured in Scene Settings under the Metadata tab \[bug 29045]
* Added support for reading and writing OpenEXR files using DCT compression options.
* Updated to RED SDK v5.2. This addresses some issues in earlier SDK releases, and adds support for monochrome clips on RED Rocket-X. Updated RED Rocket-X firmware is included.
* 'Grab Poster' now grabs a new poster frame for the (DBS) shot being previewed when used with the 'View' key held down \[bug 11645]
* Added support for Codex Action Cam RAW (.cdx) files \[bug 29565]

## Bug Fixes Since Baselight 4.4.7079

* Fixed renderer crash "m\_pPhysical != \_\_null" \[bug 20611]
* Fixed crash changing Truelight on cursor \[bug 26515]
* Fixed an issue where the frame rate calculation of some QuickTime files was slightly off on Mac \[bug 29371]
* Fixed some issues with using apply onto source stack with dissolves \[bugs 29319, 29038]
* Fixed TechGrade's starting contrast being 2.0 - it is now 1.0, a value which means that TechGrade's default values do not affect the image at all \[bug 29349]
* Fixed problems editing long text in short text fields, notably in the Render View \[bug 29221]
* Added progress panel when creating a new job \[bug 29395]
* On a single-screen system, full screen mode now only hides the cursor until the mouse moves \[bug 29466]
* The point tracker can now track cached material \[bug 28095]
* Added an option 'show input' in the tracker, which determines whether Display View shows the tracker's input image or its output \[bug 28714]
* Fixed errors rendering to movies containing '@' in their path or filename \[bug 29512]
* Update xfs\_repair to upstream version 3.2.1 \[bug 28793]
* Fixed pfs-verify 'bad fsid in nfs handle' assertion \[bug 29391]
* Consolidate now uses the cursor's proxy resolution, to fix issues when working with proxy-resolution material \[bug 29408]
* Improved the error message reported when QuickTime movies fail to open on Linux \[bug 29485]
* Updated the tooltip for the h.264 Quantizer parameter on Linux to reflect the actual default value \[bug 29599]
* Fixed Consolidate of reversed sequences \[bug 29634]
* Fixed crash when leaving an edited Six Vector \[bug 29640]
* Conversion of grades to LUTs now forces the cubes to be reloaded in the new Truelight strips. Existing Truelight strips which use cubes that have been overwritten can be updated using the Reload option in the Truelight UI \[bug 27802]
* Fixed reading of AVID RGBPacked Codec QuickTime movies on Baselight Kompressor \[bug 29710]
* Fixed occasional crash when dragging actions onto buttons in Chalk \[bug 27576]
* Toggle off curve grade animation on removal of last keyframe \[bug 28071]
* Fixed crop rectangle position drawn on Sequence Browser \[bug 29772]
* Layer/Track option is no longer shown on Render View when rendering to cache \[bug 29779]
* Fixed problem with conform panel and search directory choices from previous attempts being intermixed \[bug 29796]
* Don't attempt to use SDI output devices on Mac if no SDI Display licence present \[bug 29809]
* Fixed incorrect colours from Sony RAW MXF when using proxy resolution decoding \[bug 29832]
* Fixed licence diagnostic expiry calculation which could be a day short due to daylight saving time \[bug 29866]
* Fixed crash when moving DBS with 'Try' button held down \[bug 24928]
* Fixed failure to set AudioConverter priming info when rendering AAC audio via Kompressor \[bug 29788]
* Fixed thumbnails for some Sony RAW MXF files \[bug 29923]
* Fixed an issue where DCPs were written using SMPTE XML metadata but Interop tags in the MXF files \[bug 28455]
* Fixed crash when using the Blackboard to navigate around the Layer View \[bug 26127]
* Fixed behaviour of View 5 and View 6 when there are inactive tracks higher up the timeline \[bugs 29933, 29560]
* Colour Space Journey View now indicates video LUTs applied on AJA card SDI output \[bug 30121]
* Conforming 25@50 fps material could fail when an event has a timecode but no end timecode, and a speed of 0 \[bug 30145]
* Conforming from a volume that is not the default would result in strips not having a %C container prefix \[bug 30154]
* A race condition in the file scanner could cause it to exit with SIGPIPE when scanning was complete \[bug 30024]
* Flux now allows browsing media connected to a UI host of a Baselight TWO/FOUR/EIGHT system \[bug 30172]
* You are now prompted for confirmation when deleting an EDL Import View setting \[bug 30194]
* User group and supplemental groups were not being applied when file browsing and conform \[bug 30198]
* Fixed failures when using media on a removable drive connected to n0 (on a Baselight TWO) or io (on a Baselight FOUR/EIGHT) \[bug 30199]
* On Flos 2.1 systems the user's path now has the Baselight bin directory before the Truelight one \[bug 27293]
* Fixed issues with image files with long numbers (e.g. 11 digits) \[bug 30212]
* Fixed poor behaviour of file scanner when it encounters non-image files that look like a sequence \[bug 30204]
* Fixed bl-conform --container \[bug 28200]
* Fixed support for using the Quadro K600 as a UI card on Baselight ONE systems \[bug 30173]
* Added support for using Quadro K620 as a UI card on Baselight ONE systems. Requires NVIDIA driver 340.32 or later \[bug 30265]
* Added support for using Quadro 410 as a UI card on Baselight ONE systems. Requires NVIDIA driver 304.117 or later \[bug 30265]
* Fixed problem with SDI output synchronising when using stereo display modes via the AJA Kona 4 display card \[bug 30153]
* Stereo HDMI output is now available when using the Stereo 1920x1080 and Stereo 2048x1080 resolutions via the AJA Kona 4 display card \[bug 30268]
* Fixed crash on switching to 9 up or showing version on the display \[bug 30263]
* Fixed bl-config-xorg problem which prevented FLUX Store systems running FLOS 6.4 from performing rendering \[bug 28317]
* Fixed fl-gpustresstest, fl-retracecountertest and fl-updowntest when running on FLOS 6.4 machines with NVIDIA driver 340.32 \[bug 30079]
* Fixed fl-cp and fl-mv when using a subsequence or when renumbering \[bug 30299]
* Fixed Soften strip insert action for Slate/Blackboard 2 \[bug 28731]
* Fixed incorrect render of stereo scenes containing cached strips \[bug 30336]
* Fixed crash when two desks are simultaneously marked as active in bl-prefs. An error message is now displayed \[bug 29660]
* Fixed White Balance: Ignore File Values for Phantom.
* Fixed access to sequences on cloud media which are contained in resolution directories \[bug 30340]
* Fixed Multi-Insert not adding %R \[bug 30386]
* Fixed bug with grey border around the active image region when the image is zoomed/scaled down \[bug 30193]
* Fixed crash at Baselight application startup on Linux when in a multiple monitor configuration \[bug 30295]
* Fixed glitch in cursor rendering on the image display via AJA Kona 4 display hardware \[bug 30303]
* Fixed crash when inserting Audio Sequence via the Insert menu (no longer supported) \[bug 29891]
* Fixed configuration of tablet buttons on Blackboard TWO and 2ONE hardware. The button nearest the tip of the pen is now equivalent to the middle mouse button, and the button further away from the tip is now equivalent to right mouse button \[bug 27047]
* Fixed behaviour of worker service which would cause it to delete disk cache entries if a user's preferences had a larger disk cache size than the default setting \[bug 30444]
* Fixed tape name reading in sequences without timecode \[bug 30454]
* Fixed %W in conform to be case-insensitive \[bug 30457]
* Fixed issues with flux and external drives \[bug 30277]
