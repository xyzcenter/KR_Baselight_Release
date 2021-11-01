# Baselight Release 4.4m1.8489 (2016-07-22)



## New Features Since Baselight 4.4m1.8289

### File Formats

* Added support for reading ARRIRAW MXF files as written by the Alexa Mini camera \[bug 34960]
*   Added support for writing XAVC Intra and LongGOP to MXF. The following operating points are supported:

    1280x720:

    * XAVC HD Intra Class100 @ 50p, 59.94p
    * XAVC HD Long422 50     @ 50p, 59.94p

    1920x1080:

    * XAVC HD Intra Class100 @ 50i, 59.94i, 23.98p, 25p, 29.97p, 50p, 59.94p
    * XAVC HD Long422 25     @ 50i, 59.94i, 23.98p, 25p, 29.97p
    * XAVC HD Long422 35     @ 50i, 59.94i, 23.98p, 25p, 29.97p, 50p, 59.94p
    * XAVC HD Long422 50     @ 50i, 59.94i, 23.98p, 25p, 29.97p, 50p, 59.94p

    2048x1080:

    * XAVC 2K Intra Class100 CBG @ 23.98p, 24p, 25p, 29.97p, 50p, 59.94p
    * XAVC 2K Intra Class100 VBR @ 23.98p, 24p, 25p, 29.97p, 50p, 59.94p

    3840x2160:

    * XAVC QFHD Intra Class300 CBG @ 23.98p, 25p, 29.97p, 50p, 59.94p
    * XAVC QFHD Intra Class300 VBR @ 23.98p, 25p, 29.97p, 50p, 59.94p
    * XAVC QFHD Intra Class480 CBG @ 23.98p, 25p, 29.97p, 50p, 59.94p
    * XAVC QFHD Intra Class480 VBR @ 23.98p, 25p, 29.97p, 50p, 59.94p
    * XAVC QFHD Long 60            @ 23.98p, 25p, 29.97p
    * XAVC QFHD Long 100           @ 23.98p, 25p, 29.97p
    * XAVC QFHD Long 150           @ 50p, 59.94p

    4096x2160:

    * XAVC 4K Intra Class300 CBG @ 23.98p, 24p, 25p, 29.97p, 50p, 59.94p
    * XAVC 4K Intra Class300 VBR @ 23.98p, 24p, 25p, 29.97p, 50p, 59.94p
    * XAVC 4K Intra Class480 CBG @ 23.98p, 24p, 25p, 29.97p, 50p, 59.94p
    * XAVC 4K Intra Class480 VBR @ 23.98p, 24p, 25p, 29.97p, 50p, 59.94p

    Rec.709, Rec.2020 and S-Log colour spaces are tagged in the file metadata \[bug 28628]

### Miscellaneous

*   ARRIRAW files are now decoded using the ARRI SDK, to maximise compatibility with other software tools including Daylight. (This only applies to newly-added Sequences; existing scenes continue to behave as they did before.)

    On a system using GPUs with 3GB or more VRAM, ARRIRAW media up to 5K in width is decoded using the GPU. On a system using GPUs with 4GB or more VRAM, ARRIRAW media 5K or wider (e.g. ALEXA 65) is decoded using the GPU.

    On Linux, the GPU cannot be used for ARRIRAW decoding if the NVIDIA driver is older than version 340. See the About Baselight dialog for information \[bug 33118]
* Updated to RED SDK v6.1.0. This includes three new HDR Output Tone Curve options: HDR-2084, Rec.1886 and Log 3G12 \[bug 35054]
* R3D media can be decoded using the GPU only if the GPU has 3GB or more VRAM. See the About Baselight dialog \[bug 37071]
* When reading XAVC Intra tagged with Rec.709 or Rec.2020, the colour space is assumed to be full range rather than video legal, as recommended by Sony \[bug 28628]
* The Manage Colour Spaces dialog now allows more fine-grained choices of which colour spaces to hide in which menus - e.g. a colour space may be hidden from the Working Colour Space menu but still visible in the Render Colour Space menu \[bug 35147]
* fl-config-master has error message improvements for Baselight CONFORM \[bug 19086]
* fl-config-master has been updated to deprecate network-layout 1 \[bug 34452]
* Updated fl-setup-raid / fl-setup-pfs for BLX, they both now support '-force' when checking tgtd \[bug 35162]
* fl-setup-database has been updated to increase the database server memory setting, for improved performance \[bug 12676]
* fl-host produces an appropriate error when there is no cloud.cfg file \[bug 35039]
* fl-setup-adaptec no longer hangs on some systems at script end \[bug 34301]
* Added support for sending crash logs to baselight when unexpected failures occur, and for trimming log directories to size \[bug 36517]
* Improved EDL Import and Export of AAF EDLs to support Baselight for Avid effect payloads larger than 64kb (the limit is now 1.2MB) when working with 4.4m1 Version Compatability. This means that the "The grade data was too large to fit inside an AAF event" error produced by "Update Avid AAF with Baselight Grades" is now much, much less likely to occur \[bug 35138]
* Updated to AJA SDK 12.3 and updated AJA Kona 4 firmware \[bug 35288]
* Added support for 3G-SDI Level A RGB output via AJA Kona 4 \[bug 31835]
* Added support for independent 4K to HD downscaling on SDI and HDMI outputs of AJA Kona 4. There are now separate HDMI and SDI Downscaling options that are available in the Setups editor when the master resolution is 3840x2160 or 4096x2160 \[bug 35289]

## Bug Fixes Since Baselight 4.4m1.8289

* Addressed R3D GPU decoding errors, including errors at application startup and CL\_OUT\_OF\_HOST\_MEMORY failures \[bug 35489]
* Fixed reading audio from split-file MXF media \[bug 34903]
* Fixed reading audio from some MXF files \[bug 30294]
* Improved Baselight decode of ARRIRAW media so the levels more closely match the ARRI decode. Note that this only affects newly-added Sequences to prevent changes to existing scenes; to update existing scenes use the Update button on the Sequence parameters \[bug 35043]
* Fixed crash when pasting a tracker strip having a two point tracks with no tracker linked to it \[bug 35046]
* Updated the default Setup behaviour so that new scenes are created using the ARRI Photometric v2 DRT. This replaces the legacy ACES RRT 0.7 which was previously used \[bug 35086]
* Errors are no longer generated if there are AppleDouble files in the colourspace directories (e.g. .\_foo.flspace) \[bug 35053]
* Diagnostics no longer reject hostnames that are the same as the system zone name. This helps integration with certain 3rd-party SANs \[bug 31174]
* Fixed problem with copy protect categories on the input strip preventing the strip directly underneath from being pasted to the destination \[bug 35174]
* Fixed CDL grades not appearing in the bl-shots -ascsop and -ascsat options \[bug 35204]
* Colour Space Journey View no longer displays entries for bypassed strips \[bug 34977]
* Fixed temperature query tool 'sdi-info -temp' bug \[34978]
* Fixed Input Colour Space shown on Sequence Parameters when a BLG is inserted onto the timeline \[bug 35220]
* The Reference strip no longer converts its input to the Working Colour Space and Working Format. Note that since this can affect grading behaviour, this change only applies to newly-added Reference strips; old scenes retain their old behaviour \[bug 35206]
* Truelight resources used by operators inside layers with mattes are now correctly included in exported BLG files \[bug 35240]
* The Job Manager "Move Scene Into Folder" command now prevents moving a scene into a folder which already has a scene of the same name \[bug 35278]
* Internal /media/\_mnt\_slot\* volumes are now hidden from cloud media \[bug 35300]
* Fixed crashes reading some 16-bit RGBA TIFF files \[bug 35357]
* Bypassed Dolby Vision strips are no longer exported with EDR XML \[bug 35356]
* Fixed order of gestural grading gang controls \[bug 35352]
* Fixed export format of .cc files \[bug 34345]
* Prevented Consolidate overlapping-sequences warning dialog from getting too large \[bug 35227]
* Fix playback and render errors when Audio Sequence operator has a negative offset \[bug 35375]
* Fixed an issue with the bitrate selection dialog when rendering DCI compliant JPEG 2000 files, where the dialog did not update to reflect the selected bitrate \[bug 34844]
* The sequence operator now correctly displays a selection dialog for handling frame duration when reading a movie file with uneven frame duration \[bug 32262]
* Bundle a newer version of xfs\_repair (4.3.0) \[bug 35186]
* Fixed bug in the Gallery which could occur when grabbing RAW media (eg R3D, ARRIRAW etc) when multiple debayer parameter operators were in the stack. When the original media disappeared, the grabbed frame could have been generated using the incorrect debayer parameters \[bug 35511]
* Updated pivot point in CDL grade to match FG. Also fixed the maximum slope value \[bug 35464]
* Select Missing Material now reports that it cannot check material which is on remote cloud media \[bug 35523]
* Fixed decode of ARRIRAW Alexa Plus anamorphic (2578x2160 or 2592x2160) media using ARRI decode mode \[bug 33915]
* Negative button in Video Grade now works as expected \[bug 17462]
* A failover routine has been added when encountering missing reference frames in XDCAM MXF-files. This will allow reading valid XDCAM essence from MXF-files with invalid indexes \[bug 35633]
* Added support for a number of QuickTime codec tags, including 'aivx' for XAVC \[bug 35615]
* Fixed failure to read some QuickTime files with badly-formatted metadata \[bug 35761]
* Fixed a possible issue reading frame metadata from CFHD encoded QuickTime files with frame rates of 100 fps or higher \[bug 35934]
* Fixed an issue where incorrect frames could be returned from temporally compressed QuickTime and MP4 files \[bug 35933]
* Fixed a flfsd (pfs2 daemon) assertion error caused by a udp mount affecting the maximum tcp transfer size \[bug 35902]
* Fixed issue where some changes made in Manage Colour Spaces would not be remembered \[bug 35987]
* Certain preference files on Mac no longer include the hostname in the filename, to prevent these files changing when the hostname changes (i.e. when changing between networks) \[bug 36023]
* Fixed hang when a scaled shape has fewer than three distinct points \[bug 35135]
* Fixed Transform operator's "Show Grid" option \[bug 36159]
* Fixed bug that prevented Scene and Take metadata being read from audio files when they are synced with an image sequence (via Audio Sync, or manually via the Sequence Browser) \[bug 35689]
* Fixed an issue that prevented 60 fps timecode to be written to files of type Sony MXF \[bug 36092]
* Fixed handling of negative audio offsets in QuickTime movies. Audio tracks that start after the video will now synchronise correctly. This fix includes a change to fix how negative integer values are handled in QuickTime headers \[bug 36205]
* Added support for DNxHD essence stored in Op1A and Op1B MXF containers written by Resolve \[bug 36184]
* Fix detected size and bit depth of MXF files encoded with AVC-Intra 4:4:4 containing RGB data \[bug 36260]
* Rearranged the CDL bumps and added Exposure and Constant overall bumps \[bug 32239]
* Fixed Slate key pressing not registering long holds, especially "View" and "Try" \[bug 28094]
* Fixed an issue where full range 4:2:0 data in MP4 and QuickTime containers was squashed to legal range on read \[bug 36285]
* Fixed reading of open-GOP material in QuickTime and MP4 containers. The problem could prevent e.g. XDCAM in MP4 containers from being decoded \[bug 34258]
* Fixed reading compressed multi-view OpenEXR files \[bug 36480]
* Fixed missing metadata from movies when accessed from Text operator or Burnin \[bug 36486]
* Fixed selection being cleared after apply \[bug 25917]
* Fixed reading of some MXF files with CBR indexes split over multiple partition indexes \[bug 36452]
* Fixed a data race which could cause renders to fail with an 'unknown movie' error \[bug 36426]
* Fixed a problem seen when copying a section from a long play strip and pasting into the timeline \[bug 26573]
* Changed USB handling that caused the Slate to use a lot of CPU \[bug 35563]
* Fixed crash on Multi-GPU machines when quickly stepping between cuts \[bug 36590]
* The "Channel" selector on the Sequence Browser no longer offers Alpha for some images where there is no accessible alpha channel \[bug 36645]
* Updated Adaptec controller firmware installer to version 7-9.0. This firmware fixes a machine crash seen occasionally when running the arcconf utility \[bug 35244]
* Fixed problem where multiple pivot point edit lines got added to the Film grade page of the CDL grade operator \[bug 33400]
* Fixed crash when there was no selection and the blackboard paste key was pressed \[bug 33947]
* Fixed interlaced image display via Kona 4 when viewing still frame \[bug 34929]
* Fixed playback of audio via Kona 4 when scrubbing \[bug 32983]
* Fixed incorrect image on Kona 4 HDMI output when using 4K to HD downscaling \[bug 31351]
* Fixed crash using 1D LUTs \[bug 36608]
* Fixed crash at startup when using DVI/HDMI/DP output on systems without an AJA Kona SDI card, caused by attempts to route audio playback via the AJA SDI card \[bug 35958]
* Fixed a problem that could cause a vertical line to appear on images at different resolutions \[bug 36598]
* Resolution directories are no longer considered when choosing possible formats for ARRIRAW sequences \[bug 37200]
* Fixed a pfs2 assertion error during stale handle recovery \[bug 37242]
* Baselight will no longer attempt to use DVS Atomix cards for display output \[bug 37262]
* Fixed quality issues with scopes \[bug 36694]
* Updated ARRIRAW metadata "Clip" and "Camera" to match Daylight. Added ShutterAngle and Recorder metadata \[bug 37467]
