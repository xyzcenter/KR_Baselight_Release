# Baselight Release 4.4m1.9418 (2017-05-30)



## New Features Since Baselight 4.4m1.9286

* Updated to ARRI Metadata Bridge 1.1.0.1. This SDK manages the transfer of metadata from ARRIRAW input media to OpenEXR output media \[bug 41456]
* Updated to DNxHD/DNxHR SDK version 2.3.3. This includes bug fixes and adds CRC integrity checking of DNx data \[bug 41552]
* Added additional movie frame rate options to Render View \[bug 41699]
* Added "Show SDK Versions" button to About dialog to display version numbers of 3rd-party SDKs \[bug 41740]
*   The Sony XAVC Encoder SDK has been updated to version 1.1.6, and the Sony SMDK Toolkit has been updated to version 4.12. This adds support for the following new 10-bit XAVC operating points:

    * XAVC QFHD Long422 100           @ 23.98p, 25p, 29.97p
    * XAVC QFHD Long422 140           @ 23.98p, 25p, 29.97p, 50p, 59.94p
    * XAVC QFHD Long422 200           @ 23.98p, 25p, 29.97p, 50p, 59.94p

    The XAVC-encoder update also brings a picture quality improvement for HDR content, and updated AVC-essence colour space tags for SLog3 and PQ / Rec.2020 \[bug 41772]

## Bug Fixes Since Baselight 4.4m1.9286

* Fixed black point and white point setting in ACEScct.flspace. This does not change the transformation itself, but only where lines are displayed in the histogram \[bug 41494]
* Prevented the mona lisa symbol from disappering when the previous selected strip has the same matte configuration than the new one \[bug 40108]
* Fixed crash when an audio filename entered on Scene Settings View does not contain a / \[bug 41144]
* Improved text shown when dragging buttons in Chalk \[bug 41170]
* Fixed swapped colour channels in rotated Canon RMF media \[bug 41168]
* Fixed a crash on shutdown that could occur after reading JPEG 2000 material without a GPU JPEG 2000 acceleration licence \[bug 41194]
* Fixed hang when selecting stack bottoms left and having the timeline cursor off the end in filler \[bug 41215]
* Fixed issue creating a zero-area area tracker from a zero-area shape \[bug 39048]
* Fixed crash when tracking some very large material \[bug 39209]
* Relaxed the per colour component bitrate restriction when rendering DCI compliant JPEG 2000 material at 4K using GPU acceleration. This can improve image quality somewhat in a few cases. A progression order change (POC) has also been added to the codestream for this essence type to improve compliance with the 4K digital cinema profile \[bug 41292]
* Fix crash importing CDL \[bug 41365]
* Fixed reading of subsampled JPEG 2000 files using GPU JPEG 2000 acceleration, and added support for bitdepths other than 8 or 16 \[bug 41420]
* Fixed possible crash in Multi-Paste View when doing "Restore Config to Defaults" \[bug 41316]
* Fixed hang reading damaged JPEG2000 files \[bug 41178]
* Fixed issue where OFX plugins could become unavailable \[bug 41554]
* Fixed an issue where the GPU JPEG 2000 decoder could grab GPU memory when it shouldn't, e.g. when using the sequence browser, generating thumbnails or when the acceleration parameter was set to CPU only \[bug 41681]
* Fixed incorrect colour space warnings on Render View when using "Use Input Format" \[bug 41697]
* GPU JPEG 2000 acceleration is no longer done on the GPU in image server processes. CPU acceleration will still be used if a licence is available \[bug 41700]
* The GPU JPEG 2000 licence dialog no longer appears in Baselight CONFORM \[bug 41345]
* Fixed dpm (disk performance monitoring in fl-diag) enumerating the incorrect devices on Gen VI systems due to a change in the way Adaptec formats device data on later RAID controllers \[bug 41753]
*   The XAVC Encoder SDK has been updated to version 1.1.6, which fixes an issue where the encoder was prone to hang at the end of the render. Rendering to XAVC LongGOP codecs is now enabled again. The supported XAVC LongGOP operating points are:

    1280x720:

    * XAVC HD Long422 50     @ 50p, 59.94p

    1920x1080:

    * XAVC HD Long422 25     @ 50i, 59.94i, 23.98p, 25p, 29.97p
    * XAVC HD Long422 35     @ 50i, 59.94i, 23.98p, 25p, 29.97p, 50p, 59.94p
    * XAVC HD Long422 50     @ 50i, 59.94i, 23.98p, 25p, 29.97p, 50p, 59.94p

    3840x2160:

    * XAVC QFHD Long 60     @ 23.98p, 25p, 29.97p
    * XAVC QFHD Long 100    @ 23.98p, 25p, 29.97p
    * XAVC QFHD Long 150    @ 50p, 59.94p
    * XAVC QFHD Long422 100 @ 23.98p, 25p, 29.97p
    * XAVC QFHD Long422 140 @ 23.98p, 25p, 29.97p, 50p, 59.94p
    * XAVC QFHD Long422 200 @ 23.98p, 25p, 29.97p, 50p, 59.94p

    \[bug 39814]
* Improved error messages shown when the advertise service is not running \[bug 41812]
* Fixed appearance of tooltip glow when the control being highlighted is scaled down \[bug 41903]
* Fixed an issue where the QuickTime 'glbl'-atom was not handled correctly when encoding and decoding the FFV1 codec, resulting in invalid files being rendered and decode failures on read \[bug 31971]
* The identification of XDCAM essence in MXF-files has been improved. Some files that previously identified the source simply as "MPEG" now identifies it as "XDCAM HD/EX". Files with a picture essence coding label matching XDCAM HD 422 specifically will now present the source as "XDCAM HD 422" \[bug 42043]
* Files with the source codec "XDCAM HD 422" now correctly identifies the writer codec as XD42, allowing use of the "Prefer Source Codec" option when rendering \[bug 42045]
* Fixed an issue where bl-reset-cache refused to reset the cache if it contained Apple '.\_' resource files \[bug 41281]
* Fixed a bug which prevented bl-reset-cache from hard-resetting an SSD array on a cache-only BL1 \[bug 41106]
* Fixed display of 8 bit 420 YCrCb disk cache files on OSX \[bug 39375]
* Fixed errors using ARRIRAW media with a 2868x2152 resolution in a 2880x2160 sensor \[bug 40649]
* Fixed errors decoding ARRIRAW media at proxy resolutions using CPU rendering \[bug 42541]
* Fixed incorrect use of %R resolution directory when conforming media with multiple resolutions, e.g. ARRIRAW files \[bug 42642]
* The libraw library, used to decode camera RAW files, has been updated to version 0.18.2. This adds support for a number of new cameras, and also improves decode of some existing formats, e.g. reading of correct black levels from Sony SR2-files. NB: This can alter the look of RAW-files in existing scenes \[bug 42628]
* Fixed issue with 5.0 operators stored in the matte tool configuration crashing when adding a matte tool in 4.4m1 \[bug 42116]
* Fixed corruption at node boundaries on BL4/BL8 when viewing in floating point format \[bug 42696]
* Fixed errors setting filmlight user's home directory in macOS installer \[bug 42543]
* Allow an empty hostname to be used in the preference database dialog box \[bug 42701]
* Fixed an issue where ProRes rendered to QuickTime could be missing up to a seconds worth of audio at the end of the file \[bug 35642]
* Fixed incorrect interactive render of very small blurs \[bug 41662]
* Fixed errors decoding RED media on a system with a RED Rocket or RED Rocket X card, when the media is unsupported by the card, notably from 8K Helium sensors \[bug 41201]
* Fixed failures when rendering on a multi-GPU FLUX Store \[bug 42871]
* Fixed an issue where DCPs with missing entries in the ASSETMAP could cause dcpproxy to crash \[bug 42998]
