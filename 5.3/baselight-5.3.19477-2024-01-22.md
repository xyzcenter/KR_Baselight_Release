# Baselight 릴리스 5.3.19477 (2024-01-22)



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

\


**Baselight 5.3.18523 이후 새로운 기능**

• CMX EDL에서 클립 이름을 사용하여 컨폼하는 기능이 추가되었습니다. EDL에는 이벤트 옵션을 활성화하기 위해 \* FROM CLIP NAME: 또는 \*FROM CLIP NAME: 항목이 포함되어야 합니다 \[버그 64579].

• 장면 이름 드롭다운 메뉴에 장면의 작업 프레임 속도가 표시됩니다 \[버그 57284].

• Apple ProRes 및 많은 다른 영화 파일이 이전 빌드보다 훨씬 빠르게 읽힙니다. 이를 통해 추가 미디어를 캐싱 없이 재생할 수 있습니다 \[버그 64439].

• 타임라인에서 컨폼할 때 클립 이름이 있으면 Match Events By 목록에 “Clip Name In Path Or Filename”을 추가합니다.

• bl-conform –Filter 옵션에 ClipName이 포함되었습니다 \[버그 57729].

• PNG 이미지 파일에서 추가 메타데이터가 읽힙니다 \[버그 65131].

• 입력 색 공간과 스택 색 공간 간의 변환 시 Sequence 연산자가 자동으로 수행하는 백색점 조정이 Colour Space Journey View에 표시됩니다 \[버그 64683].

• FCP/XML과 이미지 변환을 컨폼할 때 ‘Apply Input Format Mapping’ 옵션이 추가되었습니다. 예로 설정하면 작업 포맷과 입력 포맷의 해상도와 픽셀 종횡비가 일치하지 않을 경우 변환이 차이를 보상하도록 조정됩니다 \[버그 64760].

• Photon이 버전 4.9.4로 업데이트되었습니다. 이는 렌더링된 IMF 패키지에서 추가 문제를 감지할 수 있습니다 \[버그 65555].

• QuickTime 및 MP4 파일에서 IPCM 오디오 읽기 지원이 추가되었습니다 \[버그 65581].

• Blackboard Classic Wacom 태블릿을 매핑하기 위한 명령 줄 도구가 추가되었습니다 \[버그 57119].

• Baselight 그레이드로 Avid AAF 업데이트를 수행할 때 그레이드가 내보내지 않으면 경고가 표시됩니다 \[버그 65686].

• HDR IMF 패키지 및 Dolby Vision Mezzanine MXF 파일을 렌더링할 때 v5 돌비 비전 메타데이터를 내보내는 옵션이 추가되었습니다 \[버그 60060].

• 렌더 파일 이름 템플릿 치환으로 %u 또는 %{ShotStartTimelineTimecode}가 추가되어 현재 샷의 시작 타임라인(녹화) 타임코드를 숫자로 표시합니다 \[버그 65762].

• 새 포맷 매핑을 생성할 때 작업 포맷이 목록 상단에 표시됩니다 \[버그 65896].

• CLF를 사용하여 구현된 DRT가 이제 지원됩니다. 자세한 내용은 baselight-support@filmlight.ltd.uk로 문의하십시오 \[버그 65098].

• macOS 14 Sonoma 지원이 추가되었습니다. 지원되는 최소 버전은 이제 macOS 12 Monterey입니다 \[버그 65665].

• R3D SDK 8.4.0으로 업데이트되었습니다. 여러 버그를 수정하고 IPP2 디모자이크 엣지 인터폴레이션을 개선했습니다 \[버그 67060].

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
