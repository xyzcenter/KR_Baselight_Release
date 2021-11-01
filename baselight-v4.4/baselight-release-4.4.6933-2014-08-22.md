# Baselight Release 4.4.6933 (2014-08-22)



## New Features Since Baselight 4.4.6871

*   Added new substitutions to Gallery Autoloads, allowing more flexibility for those users who use folders to organise their work. The new substitutions are %1F, %2F etc up to %9F (F stands for "Folder" here). For example, say your project hierarchy is typically:

    ::::

    and you wish to have a fresh gallery for every combination of customer, colourist and date. In this situation, an autoload template of:

    %J_%1F_%2F

    would be suitable \[bug 28554]

## Bug Fixes Since Baselight 4.4.6871

* Fixed delay in starting playback when scene is set to 16-bit floating point caching \[bug 28378]
* Fixed bug in Gallery where thumbnails could disappear when re-loading the gallery, if the input image path didn't contain a resolution directory \[bug 22959]
* Fixed Y-Y curve grade on DNx444 movies \[bug 28540]
* JPEG 2000 files without specified colourspace but with subsampling are now treated as YUV rather than RGB \[bug 28534]
* Turning the jog wheel on a Blackboard 2 will now stop playback when in frame-step mode \[bug 28512]
* Fix problem with configuring Baselight ONE systems to use DVI/HDMI output from main processing GPU on FLOS 6.4 \[bug 28595]
* Fix problem that causes intermittently Baselight to fail to launch on Baselight ONE systems running FLOS 6.4 \[bug 27501]
* Fix problem with selecting certain custom video modes added via the Available Video Modes option in bl-prefs \[bug 28593]
* Fixed colour grading operations inside Layer 0 being incorrectly burnt into the "Source" layer of BLG EXR files \[bug 28564]
* Fixed the "Source" layer of BLG EXR files not having the correct mapping applied when the input format was a different resolution to the working format \[bug 28564]
* Fixed the "Source" layer of BLG EXR files sometimes having an input colour space to viewing colour space conversion incorrectly applied \[bug 28564]
* Fixed BLG EXR files having the incorrect resolution (and sometimes aspect ratio) when the cursor viewing format was different to the scene working format \[bug 28564]
* Fixed the Input Colour Space not being set in the Sequence when importing BLG EXRs onto the Timeline \[bug 28564]
* For some image formats, Baselight is unable to write proxies (an example is ARRIRAW). This meant that if such a shot was grabbed to gallery and the original media went off-line, you would get an X in the gallery. This is no longer the case - the Gallery will now fall back to auto thumbnail generation in these cases \[bug 25480]
* Fixed issue where filtered columns in file browsers could vanish when changing directories \[bug 28603]
* Set hfsplus umask=0 to allow writing to Mac-formatted USB drives \[bug 28037]
* Fixed fl-fsr 'file placed out of sequence' warnings caused by xfs driver failing to allocate from known free space \[bug 28383]
* Fixed conform issue affecting fractional frame rates \[bug 28648]
* Added support for %X (tape name as file name) and %Y (clip name as file name) in conform to aid prefiltering of sequences, useful in some workflows \[bug 28648]
* Added support for filtering by ClipName in filename or path when using FCP XML \[bug 28681]
* Fixed bug which could result in incorrect cache status reporting \[bug 28676]
* Fixed failure to open scenes in bl-render after closing a scene using a scene-local output format \[bug 28728]
* Resetting the cache on clusters was silently failing as a side effect of support for SSD's \[bug 28730]
* Fixed crash when adjusting pivot points in Film Grade or Video Grade \[bug 28754]
* Disable touch sensitivity on Wacom tablets \[bug 28281]
* Add '-cache' option to fl-setup-pfs and fl-setup-3ware to limit actions to SSD-based array only \[bug 28746]
* Add fl-check-product-version script for use by installer \[bug 27520]
* Skip known SAN volumes when scanning for removable volumes at boot time \[bug 28747]
* Disable network interfaces which are marked as 'off' in cloud.cfg \[bug 28679]
* Added LSI RAID controller support to dpm.
* Fixed bug in 59.94 conform from CMX3600 EDLs \[bug 28806]
* Fixed magenta stripes on letterboxed renders for certain movie formats \[bug 28673]
* Fixed artefacts in highlights in some Phantom cine files \[bug 28917]
* Fixed Phantom cine decoding which was slightly too dark. Note that this change only affects newly-inserted sequences; existing sequences are unchanged unless you use the Update Sequence Behaviour button \[bug 28917]
* Reduced flfsd (pfs2 filesystem daemon) virtual memory consumption \[bug 27953]
* Fixed ARRI Decode of ARRIRAW files on FilmLight OS 2.1 and Mac OS X \[bug 28573]
* Fixed crash when using Cuts View Selection playback \[bug 28945]
* Fixed a problem on systems other than a Baselight ONE that caused configuration files to not be properly linked \[bug 28810]
