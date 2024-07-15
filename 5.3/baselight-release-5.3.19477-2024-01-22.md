# Baselight Release 5.3.19477 (2024-01-22)



## New Features Since Baselight 5.3.18523

* Added support to conform using clip name in a CMX EDL, the EDL must contain \* FROM CLIP NAME: or \*FROM CLIP NAME: entries for events to enable the option in the Match Events By selection menu \[bug 64579]
* The scene's working frame rate is now shown in the scene name drop-down menu \[bug 57284]
* Apple ProRes and many other movie files are now read considerably faster than in previous builds. This can enable additional media to play at rate without caching \[bug 64439]
*   When conforming from the timeline add "Clip Name In Path Or Filename" to the Match Events By list if clip names are present.

    The bl-conform --Filter option now includes ClipName \[bug 57729]
* Additional metadata is now read from PNG image files \[bug 65131]
* Automatic white point adjustments made by Sequence operators when converting between the Input and Stack colour spaces are now shown on Colour Space Journey View \[bug 64683]
* Added an option 'Apply Input Format Mapping' when conforming FCP/XMLs with Image Transforms. When set to yes, if the resolution and pixel aspect ratio of the working and input formats do not match, the transform is adjusted to compensate for the difference \[bug 64760]
* Updated Photon to version 4.9.4. This can detect additional issues in rendered IMF packages \[bug 65555]
* Added support for reading IPCM audio in QuickTime and MP4 files \[bug 65581]
* Added command line tool for mapping the Blackboard Classic Wacom tablet \[bug 57119]
* When performing an Update Avid AAF with Baselight grades a warning is now shown if no grades are exported \[bug 65686]
* Added an option to export v5 Dolby Vision Metadata when rendering HDR IMF packages and Dolby Vision Mezzanine MXF files \[bug 60060]
* Added %u or %{ShotStartTimelineTimecode} as a render filename template substitution which is the timeline (rec) timecode of the start of the current shot, as a number \[bug 65762]
* The Working Format is now shown at the top of the list when creating a new format mapping \[bug 65896]
* DRTs which are implemented using CLFs are now supported. Please contact baselight-support@filmlight.ltd.uk for more information \[bug 65098]
* Added support for macOS 14 Sonoma; the minimum supported version is now macOS 12 Monterey \[bug 65665]
* Updated to R3D SDK 8.4.0. This fixes several bugs, and improves IPP2 demosaic edge interpolation on strong colour transitions \[bug 67060]

## Bug Fixes Since Baselight 5.3.18523

* Removed edge repetition in Matchbox Shader for: CROK Beauty, CROK Fisheye, crok\_chroma\_warp, crok flicker, crok heathaze, crok kuwahara \[bug 64538]
* Fixed AJA T-TAP Pro UHD RGB output \[bug 64432]
* Fixed SceneNameOnly substitution to cope with multiple folders \[bug 64585]
* Fixed crash when selecting operator in an inside outside from the desk \[bug 59151]
* Fixed crash when selecting DCI 8K resolution output \[bug 59853]
* Fixed crash in paint \[bug 50465]
* Improved application interactivity/performance when the Shots View is visible \[bug 64745]
* Fixed crash reading 4:2:2 JPEG 2000 files with alpha \[bug 63673]
* Fixed issue where DNxHD/DNxHR encoded QuickTime files rendered by the application could be incorrectly identified as interlaced instead of progressive in e.g. Clipster \[bug 65123]
* Fixed crash in Frame.io package when downloading comments made by anonymous users \[bug 65351]
* Fixed possible crash in Text operator loading a new font style for an existing font name \[bug 65557]
* Fixed clipped highlights in Cuts View when using RED media at a high ISO or exposure. Please use "bl-reset-cache -thumb" to remove incorrect thumbnails from the cache \[bug 62978]
* Fixed issue with %{RandomUUID} variable substitution when rendering with "Render Format: Use Input Format" \[bug 65817]
* Fixed naming of cropped input formats in FLUX Manage View when the crop is only in one dimension \[bug 65712]
* Fixed issue with slow renders and the application becoming unresponsive when monitoring Dolby Atmos audio beyond the end of the source media \[bug 65815]
* Improved speed of some renders with multiple deliverables, notably multiple audio files \[bug 65490]
* Fixed clipping of OpenEXR media in gallery grab \[bug 64668]
* Fixed hang when using "Prepare Noise Profile" in Neat Video when the OFX operator is in a cache strip \[bug 65752]
* Fixed issue with GPU JPEG 2000 acceleration not working when decoding MXF files \[bug 65983]
* Fixed issue with shot marks always applied to the bottom sequence when conforming AAFs \[bug 65975]
* Fixed crash when reconfiguring NDI output device \[bug 65398]
* Fixed issue that could generate corrupt files during unsuccessful MXF file trimming \[bug 66118]
* Fixed crash caused by invalid Resolution setting for a stream in Client Sessions View \[bug 64254]
* Fixed MXF UIDs appearing in the bl-conform output by default, only output with the --verbose option \[bug 65771]
* Fixed crash when changing stream resolution in Client Sessions View \[bug 66170]
* Fixed crash when applying a stack to itself when there are strips that are protected from being copied \[bug 66135]
* The bitrate of DCI compliant JPEG 2000 essence has been reduced by 5% to avoid issues with older DCP players and third-party validation tools \[bug 66359]
* Fixed display of custom column expression icon in Shots View \[bug 66075]
* Fixed an issue that could affect Wacom pen sensitivity in FilmLightOS 8 \[bug 66379]
* Fixed issue when copying with Layer 0 selected with additional operators in layer 0 \[bug 66684]
* Fixed crash when using apply with auto selection off \[bug 58653]
* Fixed crash when applied categories don't exist in the current scene \[bug 56226]
* Fixed flit service (used for FLUX Manage file copies) on macOS 14 Sonoma \[bug 67023]
* Fixed a range of failures that could be caused by repeated application runs which never read any movie files, especially on a multi-GPU system \[bug 66629]

***
