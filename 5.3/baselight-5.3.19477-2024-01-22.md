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

Baselight 5.3.18523 이후 버그 수정

\


• Matchbox Shader에서 CROK Beauty, CROK Fisheye, crok\_chroma\_warp, crok flicker, crok heathaze, crok kuwahara에 대한 에지 반복을 제거했습니다 \[버그 64538].

• AJA T-TAP Pro UHD RGB 출력 문제를 수정했습니다 \[버그 64432].

• 여러 폴더를 처리하기 위한 SceneNameOnly 치환을 수정했습니다 \[버그 64585].

• 데스크에서 인사이드 아웃사이드에서 연산자를 선택할 때 발생하는 충돌을 수정했습니다 \[버그 59151].

• DCI 8K 해상도 출력을 선택할 때 발생하는 충돌을 수정했습니다 \[버그 59853].

• 페인트에서 발생하는 충돌을 수정했습니다 \[버그 50465].

• 샷 뷰가 표시될 때 응용 프로그램의 상호작용성/성능을 개선했습니다 \[버그 64745].

• 알파와 함께 4:2:2 JPEG 2000 파일을 읽을 때 발생하는 충돌을 수정했습니다 \[버그 63673].

• 응용 프로그램에서 렌더링된 DNxHD/DNxHR 인코딩된 QuickTime 파일이 Clipster 등에서 프로그레시브 대신 인터레이스로 잘못 식별될 수 있는 문제를 수정했습니다 \[버그 65123].

• 익명 사용자가 작성한 댓글을 다운로드할 때 Frame.io 패키지에서 발생하는 충돌을 수정했습니다 \[버그 65351].

• 텍스트 연산자가 기존 글꼴 이름에 새 글꼴 스타일을 로드할 때 발생할 수 있는 충돌을 수정했습니다 \[버그 65557].

• RED 미디어를 높은 ISO나 노출에서 사용할 때 Cuts View에서 하이라이트가 클립되는 문제를 수정했습니다. 캐시에서 잘못된 썸네일을 제거하려면 “bl-reset-cache -thumb”을 사용하십시오 \[버그 62978].

• “Render Format: Use Input Format”으로 렌더링할 때 %{RandomUUID} 변수 치환 문제를 수정했습니다 \[버그 65817].

• FLUX Manage View에서 잘린 입력 포맷의 이름 지정 문제를 수정했습니다 (크롭이 한 차원에서만 일어날 때) \[버그 65712].

• 소스 미디어의 끝을 넘어서 돌비 애트모스 오디오를 모니터링할 때 발생하는 느린 렌더링 및 응용 프로그램이 응답하지 않는 문제를 수정했습니다 \[버그 65815].

• 여러 딜리버러블, 특히 여러 오디오 파일이 포함된 일부 렌더링의 속도를 개선했습니다 \[버그 65490].

• 갤러리에서 OpenEXR 미디어의 클립 문제를 수정했습니다 \[버그 64668].

• Neat Video의 “Prepare Noise Profile”을 사용할 때 OFX 연산자가 캐시 스트립에 있을 때 발생하는 중단 문제를 수정했습니다 \[버그 65752].

• MXF 파일을 디코딩할 때 GPU JPEG 2000 가속이 작동하지 않는 문제를 수정했습니다 \[버그 65983].

• AAFs를 컨폼할 때 샷 마크가 항상 하단 시퀀스에 적용되는 문제를 수정했습니다 \[버그 65975].

• NDI 출력 장치를 재구성할 때 발생하는 충돌을 수정했습니다 \[버그 65398].

• 실패한 MXF 파일 트리밍 중 손상된 파일이 생성될 수 있는 문제를 수정했습니다 \[버그 66118].

• 클라이언트 세션 보기에서 스트림의 잘못된 해상도 설정으로 인한 충돌을 수정했습니다 \[버그 64254].

• 기본적으로 bl-conform 출력에 나타나는 MXF UID를 수정하여, –verbose 옵션을 사용할 때만 출력되도록 했습니다 \[버그 65771].

• 클라이언트 세션 보기에서 스트림 해상도를 변경할 때 발생하는 충돌을 수정했습니다 \[버그 66170].

• 복사할 수 없도록 보호된 스트립이 있을 때 스택을 자체에 적용하면 발생하는 충돌을 수정했습니다 \[버그 66135].

• 오래된 DCP 플레이어와 타사 검증 도구에서 발생하는 문제를 피하기 위해 DCI 준수 JPEG 2000 에센스의 비트레이트를 5% 줄였습니다 \[버그 66359].

• 샷 뷰에서 사용자 정의 열 표현 아이콘의 표시 문제를 수정했습니다 \[버그 66075].

• FilmLightOS 8에서 Wacom 펜 감도에 영향을 미칠 수 있는 문제를 수정했습니다 \[버그 66379].

• 레이어 0을 선택한 상태에서 레이어 0에 추가 작업자와 함께 복사할 때 발생하는 문제를 수정했습니다 \[버그 66684].

• 자동 선택을 끈 상태에서 적용할 때 발생하는 충돌을 수정했습니다 \[버그 58653].

• 현재 장면에 적용된 카테고리가 없을 때 발생하는 충돌을 수정했습니다 \[버그 56226].

• macOS 14 소노마에서 FLUX 관리 파일 복사에 사용되는 flit 서비스를 수정했습니다 \[버그 67023].

• 특히 다중 GPU 시스템에서 반복적인 응용 프로그램 실행으로 인해 영화 파일을 읽지 않는 경우 발생할 수 있는 다양한 실패를 수정했습니다 \[버그 66629].

***
