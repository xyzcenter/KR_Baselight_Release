# Baselight Release 5.3.18123 (2023-06-13)

## New Features Since Baselight 5.3.17711

### [Disney IMF Presets](baselight-release-5.3.18123-2023-06-13.md#disney-imf)

*   Added IMF presets for HDR and SDR variants of Disney Mastering and Distribution packages. These are based on Disney specifications v1.13.2 as available from mediatechspecs.disney.com.

    The following constraints are applied when a Disney IMF preset is selected:

    * JPEG 2000 Bitdepth, Mainlevel and Sublevel are set to the values dictated by the selected preset.
    * Timecode starts at 00:00:00:00.
    * Audio in supplemental packages is preserved by default and cannot be updated, i.e. no 'audio inserts'.
    * Dolby Atmos tracks are not available.
    * MaxFALL and MaxCLL are not included in the package.
    * Min Luma is set to 0.0001 or 0.005 for 1000 nit and 4000 nit Mastering Displays respectively.

    Video, Audio, OPL and PKL names should be left at the default values to comply with Disney requirements.

    A warning will be shown if a lossless UHD video reel exceeds 80 minutes. Video can be split into parts in Render View.

    Warnings will appear in Render View if any setting in the current deliverable does not comply with the delivery specification for the selected preset.

    The package type selector has been divided into type and subtype for easier overview. It is now also possible to select Netflix and Disney presets for supplemental IMF packages \[bug 61119]

## Baselight 5.3.17711 이후의 새로운 기능

### Disney IMF 프리셋

* Disney 마스터링 및 배포 패키지의 HDR 및 SDR 변형을 위한 IMF 프리셋이 추가되었습니다. 이 프리셋은 mediatechspecs.disney.com에서 제공되는 Disney 사양 v1.13.2를 기반으로 합니다.\
  Disney IMF 프리셋이 선택되면 다음 제약 조건이 적용됩니다:
  * JPEG 2000 비트 깊이, 메인 레벨 및 서브 레벨이 선택된 프리셋에서 지정한 값으로 설정됩니다.
  * 타임코드는 00:00:00:00에서 시작합니다.
  * 보충 패키지의 오디오는 기본적으로 유지되며 업데이트할 수 없습니다. 즉, ‘오디오 삽입’이 없습니다.
  * 돌비 애트모스 트랙은 사용할 수 없습니다.
  * MaxFALL 및 MaxCLL은 패키지에 포함되지 않습니다.
  * 최소 휘도는 각각 1000니트 및 4000니트 마스터링 디스플레이에 대해 0.0001 또는 0.005로 설정됩니다.

비디오, 오디오, OPL 및 PKL 이름은 Disney 요구 사항을 준수하기 위해 기본 값으로 유지해야 합니다.

무손실 UHD 비디오 릴이 80분을 초과하면 경고가 표시됩니다. 비디오는 Render View에서 부분으로 나눌 수 있습니다.

현재 제공물의 설정이 선택된 프리셋의 전달 사양을 준수하지 않는 경우 Render View에 경고가 표시됩니다.

패키지 유형 선택기가 유형과 하위 유형으로 나누어져 있어 더 쉽게 개요를 볼 수 있습니다. 이제 보충 IMF 패키지에 대해 Netflix 및 Disney 프리셋을 선택할 수 있습니다 \[버그 61119].



### [Frame.io Integration](baselight-release-5.3.18123-2023-06-13.md#frame.io)

*   A new version of the Frame.io Integration is available.

    To install the update, open Scripts View, select the 'Packages' tab, choose the 'filmlight-frameio' package, and click Upgrade Package.

    Please note: Do not upgrade if you currently have scenes with active Frame.io assets \[bug 63660]
* When uploading to Frame.io, dialogs now restore, when possible, last selections for account, team, project, folder, and render deliverable. Install the latest integration package to use this feature \[bug 63575]
* Frame.io app and server scripts now log errors when attempting to connect to the API server or FilmLight authentication server. This should make it easier to troubleshoot configuration issues. Install the latest integration package to use this feature \[bug 63723]

### Frame.io 통합

* <mark style="background-color:green;">새로운 버전의 Frame.io 통합이 제공</mark>됩니다.\
  업데이트를 설치하려면 Scripts View를 열고 ‘Packages’ 탭을 선택한 다음 ‘filmlight-frameio’ 패키지를 선택하고 Upgrade Package를 클릭하세요.\
  주의: 현재 활성 Frame.io 자산이 있는 장면이 있는 경우 업그레이드하지 마세요 \[버그 63660].
* Frame.io에 업로드할 때 계정, 팀, 프로젝트, 폴더 및 렌더 제공물에 대한 마지막 선택 항목을 가능한 경우 복원하는 대화상자가 추가되었습니다. 이 기능을 사용하려면 최신 통합 패키지를 설치하세요 \[버그 63575].
* Frame.io 앱 및 서버 스크립트는 이제 API 서버 또는 FilmLight 인증 서버에 연결을 시도할 때 오류를 기록합니다. 이를 통해 구성 문제를 더 쉽게 해결할 수 있습니다. 이 기능을 사용하려면 최신 통합 패키지를 설치하세요 \[버그 63723].

###

### [Cache Input Format Area](baselight-release-5.3.18123-2023-06-13.md#undefined-1)

* The Strip Caching setting on Scene Settings View now has a "Cache Input Format Area" option. Choosing this option makes the cached area the whole of the Sequence's Input Format area (when mapped into the Working Format), including any parts which are mapped outside the Working Format. This allows later Transform operators to reveal the image in these areas, instead of black \[bug 35947]

### 입력 형식 영역 캐시

* Scene Settings View의 스트립 캐싱 설정에 이제 “<mark style="background-color:green;">Cache Input Format Area” 옵션이 추가</mark>되었습니다. 이 옵션을 선택하면 캐시된 영역이 작업 형식으로 매핑될 때 시퀀스의 입력 형식 영역 전체가 됩니다. 여기에는 작업 형식 외부로 매핑되는 부분도 포함됩니다. 이를 통해 나중에 변환 연산자가 이 영역의 이미지를 검정 대신 표시할 수 있습니다 \[버그 35947].

###

### [Miscellaneous](baselight-release-5.3.18123-2023-06-13.md#undefined-3)

*   On Linux platforms (except FilmLightOS 6), image sequence file I/O is now implemented with direct I/O (DIO), when the files reside on a NFS server. This has a performance benefit.

    On all platforms, DIO can be enabled or disabled on a per-volume basis using the new "directio" flag in volume.cfg. For example:

    zone bl0999 dir images /mnt/disk1/images1 limit images directio=write

    If the flag is set to "off", DIO will not be used for the volume. If it is set to "on", DIO will be used for both reads and writes. If it is set to "read", DIO will only be used for reads. If it is "write", DIO will only be used for writes.

    The setting will typically only need to be considered for NAS and SAN volumes that might not support DIO, or for performance reasons.

    The "nodirect" flag is equivalent to "directio=off", and is now deprecated \[bug 61840]
*   On Linux platforms (except FilmLightOS 6), it is now possible to use the /etc/nfsmount.conf file to specify default mount options for NFS filesystems under /vol. This can be useful when a UI host requires different mount options than the main node of a Baselight TWO/X, or when different systems in the cloud require different mount options but use a single, shared volume.cfg file.

    To specify mount options in nfsmount.conf, the recommended way is to use a "MountPoint" entry. For example:

    \[ MountPoint "/vol/bl0999-images" ] proto=rdma

    You can also use a "Server" entry to apply to all mounts for that host. Because auto.vol mounts by IP address, you must use the the IP address of the server and not the hostname. For example:

    \[ Server "10.81.183.30" ] proto=tcp nconnect=8

    The /etc/auto.vol script will refrain from adding default options if it finds matching section in nfsmount.conf. It will add any options from volume.cfg, if they are present.

    To test the options, access the path under /vol and look at the file /proc/mounts. It will list the mounted filesystems and show the mount options in-use \[bug 62532]
*   Added a new submenu to the "Marks" menu: "Delete From Selected Strips". This contains 4 options:

    * "Scene Detect Marks" removes all marks from the selected strips implicitly created from the Scene Detect view.
    * "Categorised Marks" removes all marks from the selected strips explicitly added from the application.
    * "Client Frame Marks/Notes" removes all client added frame marks/notes from the selected strips.
    * "Client Shot Notes" removes all per-shot client notes from the selected strips.

    Note: The last 2 options CANNOT be undone \[bug 61927]
* Updated to ARRI MXF SDK version 4.1.1. This fixes issues with trimming some newer ARRIRAW media \[bug 63603]
* Added a "%C" button to the Select Image Search Directory dialog in Conform View, to go to the current scene's container \[bug 62677]
* The Help menu includes "Blackboard 2 Button Reference" when a Blackboard 2 is in use \[bug 63781]
* Added a button to the Colour Space Journey View to copy a text version of the colour space journey to the clipboard \[bug 28851]
* Added "ARRI REVEAL DRT" family to FilmLight website \[bug 62698]
* When dragging sequences from FLUX Manage View, Timeline View now shows the same sort of drop area as FLUX Manage View \[bug 62310]
* Dolby Metafier can now be used to validate rendered IMF packages with Dolby Vision. This feature is enabled in Render View by selecting the 'Metafier Validation' entry in the 'IMF' selector. Errors or warnings from Metafier will produce a warning in the operation log. Dolby Metafier, part of Dolby Vision Professional Tools, must be installed and its location set in Preferences->Advanced->IMF Validation for Metafier Validation to work \[bug 54964]
* Baselight CONFORM now lists FLUX Store and Baselight RENDER systems at the top of the submission list on Render View \[bug 62837]
* It is now possible to read supplemental IMF packages stored using Netflix best practices folder structure \[bug 63231]
* Added 'OFX Filter' option to layer's matte selector control \[bug 63528]
* Added new "Marks and Client Events" and "Queue Monitor" desk buttons, these can be found in the "UI Views" Button Category in Chalk \[bug 62566]
* Updated Photon to version 4.9.1. This can detect additional issues in rendered IMF packages \[bug 63774]
* Updated to Codex HDE SDK 4.0.3. This adds support for monochrome .arx media \[bug 63858]
* Updated to ARRI Image SDK 7.1.1. This adds support for decoding to ARRI LogC4 (and thereby ARRI's REVEAL Colour Science) for the ALEXA 65, ALEXA LF and Mini LF, and all previous ALEXA models, including the ALEXA Mini and the AMIRA. It also improves monochrome media support \[bug 62918]
* The Scene Differences dialog now shows removed audio tracks and additional audio track info when comparing a master scene to the current scene for supplemental IMF package deliverables \[bug 64122]
* In a Dolby Vision scene, the cursor's mask and guide can now be set to "Dolby Vision L5" to reflect the image aspect ratio of the Dolby Vision analysis \[bug 59905]
* The "Special Chars in Tape Name" option in the Export EDL dialog no longer implicity replaces the space character with "\_" when this option is set to "Yes" \[bug 29347]
* The OFX plugin dialog now has a Filter button \[bug 64267]
* To allow OFX plugins to better understand FilmLight system architecture, a new FilmLight Suite is now available, please read OFX\_in\_Baselight.txt in the documentation folder \[bug 63659]
* Improved support for TTC fonts allowing selection of any alternative styles embedded in the font files \[bug 62291]
* Added support for quad link UHD at 120Hz when using a Blackmagic Decklink 8k Pro \[bug 61738]
* Added an option to write closed GOP XDCAM in Sony MXF deliverables. This behaviour can be enabled using Codec Params in Render View \[bug 64402]



### 기타

* Linux 플랫폼(영화LightOS 6 제외)에서 <mark style="background-color:green;">이미지 시퀀스 파일 I/O가 이제 NFS 서버에 파일이 있을 때 직접 I/O(DIO)로 구현</mark>되었습니다. 이는 성능 향상에 도움이 됩니다.\
  모든 플랫폼에서, DIO는 이제 volume.cfg의 새로운 “directio” 플래그를 사용하여 볼륨 단위로 활성화하거나 비활성화할 수 있습니다. 예를 들어:\
  zone bl0999 dir images /mnt/disk1/images1 limit images <mark style="background-color:orange;">directio=write</mark>\
  <mark style="background-color:green;">플래그가 “off”로 설정되면 해당 볼륨에 대해 DIO가 사용되지 않습니다. “on”으로 설정되면 읽기 및 쓰기에 대해 DIO가 사용됩니다. “read”로 설정되면 읽기만 DIO가 사용됩니다. “write”로 설정되면 쓰기만 DIO가 사용됩니다.</mark>이 설정은 일반적으로 DIO를 지원하지 않을 수 있는 NAS 및 SAN 볼륨에 대해 고려해야 하거나 성능 이유로 필요합니다.\
  “nodirect” 플래그는 “directio=off”와 동일하며 이제 더 이상 사용되지 않습니다 \[버그 61840].
*   Linux 플랫폼(영화LightOS 6 제외)에서 이제 /vol 하위의 NFS 파일 시스템에 대해 기본 마운트 옵션을 지정하기 위해 /etc/nfsmount.conf 파일을 사용할 수 있습니다. 이는 UI 호스트가 Baselight TWO/X의 메인 노드와 다른 마운트 옵션을 필요로 하거나 클라우드의 다른 시스템이 단일, 공유된 volume.cfg 파일을 사용하는 경우 유용할 수 있습니다.

    nfsmount.conf에서 마운트 옵션을 지정하려면 권장 방법은 “MountPoint” 항목을 사용하는 것입니다. 예를 들어:\
    \[ MountPoint "/vol/bl0999-images" ] <mark style="background-color:green;">proto=rdma</mark>\
    또한 해당 호스트의 모든 마운트에 적용할 “Server” 항목을 사용할 수 있습니다. auto.vol은 IP 주소로 마운트하기 때문에 서버의 호스트 이름이 아닌 IP 주소를 사용해야 합니다. 예를 들어:\
    \[ Server "10.81.183.30" ] proto=tcp nconnect=8\
    /etc/auto.vol 스크립트는 nfsmount.conf에서 일치하는 섹션을 찾으면 기본 옵션을 추가하지 않습니다. volume.cfg의 옵션이 있는 경우 해당 옵션을 추가합니다.\
    옵션을 테스트하려면 /vol 하위 경로에 액세스하고 /proc/mounts 파일을 확인하십시오. 사용 중인 마운트 옵션과 함께 마운트된 파일 시스템이 나열됩니다 \[버그 62532].
* “Marks” 메뉴에 “선택된 스트립에서 삭제”라는 새 하위 메뉴가 추가되었습니다. 여기에 4가지 옵션이 포함됩니다:
  * “Scene Detect Marks”는 Scene Detect 보기에서 암시적으로 생성된 선택된 스트립의 모든 마크를 제거합니다.
  * “Categorised Marks”는 애플리케이션에서 명시적으로 추가된 선택된 스트립의 모든 마크를 제거합니다.
  * “Client Frame Marks/Notes”는 선택된 스트립에서 모든 클라이언트 추가 프레임 마크/노트를 제거합니다.
  * “Client Shot Notes”는 선택된 스트립에서 모든 샷 별 클라이언트 노트를 제거합니다.\
    주의: 마지막 두 옵션은 실행 취소할 수 없습니다 \[버그 61927].
* <mark style="background-color:green;">ARRI MXF SDK 버전 4.1.1로 업데이트</mark>되었습니다. 이를 통해 일부 최신 <mark style="background-color:green;">ARRIRAW 미디어 트리밍 문제를 해결</mark>할 수 있습니다 \[버그 63603].
* Conform View의 이미지 검색 디렉토리 선택 대화 상자에 현재 장면의 컨테이너로 이동하기 위한 “%C” 버튼이 추가되었습니다 \[버그 62677].
* Blackboard 2를 사용할 때 도움말 메뉴에 “Blackboard 2 버튼 참조”가 포함됩니다 \[버그 63781].
* 컬러 공간 여정 보기에서 텍스트 버전의 컬러 공간 여정을 클립보드에 복사할 수 있는 버튼이 추가되었습니다 \[버그 28851].
* <mark style="background-color:green;">FilmLight 웹사이트에 “ARRI REVEAL DRT” 패밀리가 추가</mark>되었습니다 \[버그 62698].
* FLUX Manage View에서 시퀀스를 드래그할 때, 이제 Timeline View가 FLUX Manage View와 동일한 종류의 드롭 영역을 표시합니다 \[버그 62310].
* Dolby Metafier를 사용하여 Dolby Vision을 사용한 IMF 패키지의 렌더링을 검증할 수 있습니다. Render View에서 ‘IMF’ 선택기에서 ‘Metafier Validation’ 항목을 선택하여 이 기능을 활성화할 수 있습니다. Metafier의 오류나 경고는 작업 로그에 경고를 생성합니다. Dolby Vision Professional Tools의 일부인 Dolby Metafier가 설치되어 있어야 하며, Metafier 검증을 작동하려면 Preferences->Advanced->IMF Validation에서 위치를 설정해야 합니다 \[버그 54964].
* Baselight CONFORM은 이제 Render View에서 제출 목록의 맨 위에 FLUX Store 및 Baselight RENDER 시스템을 나열합니다 \[버그 62837].
* Netflix 모범 사례 폴더 구조를 사용하여 저장된 보충 IMF 패키지를 읽을 수 있습니다 \[버그 63231].
* 레이어의 매트 선택 제어에 ‘OFX 필터’ 옵션이 추가되었습니다 \[버그 63528].
* 새로운 “Marks and Client Events” 및 “Queue Monitor” 데스크 버튼이 추가되었습니다. 이 버튼들은 Chalk의 “UI Views” 버튼 카테고리에서 찾을 수 있습니다 \[버그 62566].
* <mark style="background-color:green;">Photon이 버전 4.9.1로 업데이트</mark>되었습니다. 이를 통해 렌더링된 IMF 패키지에서 추가적인 문제를 감지할 수 있습니다 \[버그 63774].
* <mark style="background-color:green;">Codex HDE SDK 4.0.3으로 업데이트</mark>되었습니다. 이를 통해 모노크롬 .arx 미디어를 지원합니다 \[버그 63858].
* <mark style="background-color:green;">ARRI Image SDK 7.1.1로 업데이트</mark>되었습니다. 이를 통해 <mark style="background-color:green;">ALEXA 65, ALEXA LF 및 Mini LF와 모든 이전 ALEXA 모델, 포함하여 ALEXA Mini 및 AMIRA를 위한 ARRI LogC4(따라서 ARRI의 REVEAL 컬러 과학)로 디코딩을 지원</mark>합니다. 또한 <mark style="background-color:green;">모노크롬 미디어 지원이 향상</mark>되었습니다 \[버그 62918].
* Scene Differences 대화 상자는 이제 보충 IMF 패키지 제공을 위해 마스터 장면과 현재 장면을 비교할 때 제거된 오디오 트랙 및 추가적인 오디오 트랙 정보를 표시합니다 \[버그 64122].
* Dolby Vision 장면에서 커서의 마스크 및 가이드를 “Dolby Vision L5”로 설정하여 Dolby Vision 분석의 이미지 종횡비를 반영할 수 있습니다 \[버그 59905].
* Export EDL 대화 상자의 “Tape Name에 특수 문자 포함” 옵션이 “Yes”로 설정된 경우 이제 공백 문자를 “\_“로 암시적으로 대체하지 않습니다 \[버그 29347].
* OFX 플러그인 대화 상자에 필터 버튼이 추가되었습니다 \[버그 64267].
* OFX 플러그인이 FilmLight 시스템 아키텍처를 더 잘 이해할 수 있도록 새로운 FilmLight Suite가 제공됩니다. 자세한 내용은 문서 폴더의 OFX\_in\_Baselight.txt를 참조하세요 \[버그 63659].
* TTC 폰트에 대한 지원이 개선되어 폰트 파일에 포함된 모든 대체 스타일을 선택할 수 있습니다 \[버그 62291].
* Blackmagic Decklink 8k Pro를 사용할 때 120Hz에서 쿼드 링크 UHD를 지원하는 옵션이 추가되었습니다 \[버그 61738].
* Sony MXF 제공물에서 폐쇄 GOP XDCAM을 작성하는 옵션이 추가되었습니다. 이 동작은 Render View의 Codec Params를 사용하여 활성화할 수 있습니다 \[버그 64402].



## Bug Fixes Since Baselight 5.3.17711

* Fixed incorrect image being sent to the user interface of OFX plugins (e.g. Neat Video) which are part of a dissolve or composite \[bug 63615]
* Fixed issues when OFX operator has no inputs, or attempts to access a frame beyond the end of the strip \[bug 63614]
*   SMB volumes listed in volume.cfg can now be accessed from macOS clients. The special volume options "username", "domain" and "password" can be used to specify authentication. Other options are described in the mount\_smbfs(8) man page. The automounter script will also auto-correct Linux-style "file\_mode" and "dir\_mode" to the macOS-style "filemode" and "dirmode" options.

    For example, a volume entry might look like: share bigserver server.lan G$ smb username=bob,password=XYZ

    To include a space in a mount option, use the octal \040 form \[bug 13252]
* Fixed issue with some AVC-Intra MXF files not being recognised \[bug 63642]
* Fixed bug which could cause Video Grade's 'Extended" (range) button state to be incorrectly saved/applied \[bug 46674]
* Fixed bug which would cause DSpot's keyframes to fail to copy and paste \[bug 62613]
* OpenEXR media with metadata indicating a FilmLight viewing colour space of "ARRI: Linear / Wide Gamut" or "ARRI: LogC / Wide Gamut" is now correctly imported using the recently-renamed versions of those colour spaces \[bug 62594]
* Fixed issue with some trimmed ALEXA Mini MXF files not being recognised \[bug 63745]
* Fixed a fatal assertion failure that could occur while interacting with the user interface \[bug 63778]
* Fixed a crash that could occur with OFX plugins which access images in the application UI \[bug 63452]
* Fixed "Launch Web Interface" button in Adaptec RAID diagnostics in fl-diag on FilmLightOS 8 systems \[bug 62530]
* Fixed issue which prevented Adaptec RAID diagnostics from running on Linux Daylight systems \[bug 62525]
* Improved recognition of anamorphic ratios in RED media \[bug 64093]
* When making a new scene from a scene template, every Scene Format from the scene template is now copied into the new scene, even if that format is not used by the scene template \[bug 64110]
* Fixed Tape metadata in renders to QuickTime/MP4 when there is no timecode. This media holds the Tape metadata in the timecode track, so timecode starting at 00:00:00:00 is now used \[bug 63960]
* Fixed an issue that could cause job format changes to be written to the wrong job after performing a Save-As to a new job \[bug 63661]
* Baselight now makes fewer connections to the database server when opening a scene. This reduces scene-open time, particularly with remote database servers \[bug 63661]
* Fixed issue with Text operator when fonts not found \[bug 61457]
* Renamed "EDL Import" to "Conform" in the Chalk UI Views list \[bug 35909]
* Blackboard and Slate Bypass Operator button now shows the operator bypass state \[bug 62553]
* Fixed crash when using Media Ingest View \[bug 61998]
* Fixed crash in Stereo Grade and Stereo Geometry Fix in Semi-Automatic mode \[bug 63021]
* Fixed potential crash when deselecting a Transform operator with grouped grading enabled \[bug 54553]
* Added new strips to the Chalk actions \[bug 62695]
* Added default Level 11 metadata to Dolby Vision HDMI signal \[bug 63145]
* Fixed "Apply Media" popups appearing when ingesting without creating scenes \[bug 61151]
* Fixed potential crash identifying marks in AAFs when conforming \[bug 63343]
* Fixed crash in Edge Crop when it was cropping the entire image \[bug 62537]
* Fixed issues with MXF media that has Sony camera marker metadata \[bug 62800]
* Fixed the colour space behaviour of the Bars operator when initially added to a scene \[bug 63276]
* Fixed Switch Dust operator on multi-GPU systems \[bug 63175]
* Fixed inability to use the "Dolby: ST 2084 PQ / P3 D65 / 108 nits" Dolby Vision viewing/rendering colour space \[bug 63150]
* Fixed typo in arriraw/exposureIndex raw metadata \[bug 63492]
* Fixed issues with OFX plugins including BorisFX Silhouette \[bug 63452]
* Fixed where menus on the Display View (e.g. when editing Text or Burnins) sometimes filled the whole screen \[bug 62704]
* Fixed a bug which could cause a scene with a area tracked shape to fail to open \[bug 38825]
* Fixed "Launch Web Interface" button in Adaptec RAID diagnostics in fl-diag on FilmLightOS 8 systems \[bug 62530]
* Fixed issue which prevented Adaptec RAID diagnostics from running on Linux Daylight systems \[bug 62525]
* Fixed clipping of highlights when using a CPU OFX plugin with a rotated transform \[bug 63910]
* Fixed a bug which would incorrectly enable the "Use Matte" button of a layer's Curve Grade operator when a modifier was pressed \[bug 60857]
* Reduced the amount of time required to calculate checksums when rendering IMF packages \[bug 61120]
* Fixed crash while monitoring Dolby Atmos audio \[bug 61613]
* Fixed crash while editing lines in Lens Correction \[bug 64103]
* Fixed crash when creating a new gallery with an invalid Gallery Job preference \[bug 64112]
* Sony per-frame camera posture metadata is now read correctly \[bug 64058]
* Reduced unwanted information printed to console when using some ARRI camera media \[bug 64074]
* Exported Dolby Vision XML now no longer contains "Level 5" entries for shots whose image aspect ratio matches the most-common image aspect ratio given in the XML \[bug 62250]
* BRAW raw metadata now includes timecode \[bug 63657]
* Fixed issue where audio would turn to noise when reading IMF CPL files \[bug 64148]
* Fixed rare crash in Curve Grade where the working colourspace was indeterminate \[bug 63967]
* Improved feedback for user when using Dolby Vision HDMI tunneling \[bug 64179]
* Fixed issue where extra spaces in Metafier Arguments could cause Metafier Validation to fail \[bug 64208]
* The tnd service can now support FLUX Manage in Baselight 6.0 \[bug 64242]
* NVIDIA driver version 525.116.03 is now accepted without warnings from fl-diag or the installer. This adds support for Ada Lovelace generation GPUs \[bug 64218]
* Improved performance of OFX plugins that have no effect on the image (e.g. Neat Video before it has been configured) \[bug 64275]
* Fixed OFX and Shader rendering errors in Gallery View when the gallery scene's working format is different from the working format of the scene where the grab was made \[bug 64277]
* Improved compatibility of DCI-compliant JPEG 2000 media to avoid potential issues with legacy cinema players and validation warnings in 3rd-party software \[bug 64288]
* Fixed OFX GPU memory issues when running on a Mac with a large-VRAM GPU and either a second GPU or SDI output \[bug 64232]
* Fixed Slate not displaying the Offset All state \[bug 39900]
* The incorrect warning about changed job or global formats is no longer shown when first opening a scene that has been imported or saved-as into a different job \[bug 63772]
* The Clip metadata option is now only shown in Render View for deliverable types that support Clip metadata \[bug 63965]
* Reference operator buttons which are invalid for the current mode are now hidden. Previously, clicking one of these buttons when they should be hidden would cause a crash \[bug 63166]
* Fixed vertical distortion during playback when Paint is applied to an interlaced source \[bug 64235]
* Stopped gap appearing after pasting a Tracker strip \[bug 64259]
* Improved behaviour of monochrome ARRIRAW media \[bug 64337]
* Fixed issue causing some AAFs not to be recognised during Conform, producing internal error messages and possibly crashing \[bug 62504]
* The "Offset All" button now flashes on the Slate \[bug 64296]
* Fixed an issue with Texture Equalizer and Transform when applied to an interlaced scene \[bug 64401]
* Disk performance diagnostic no longer verifies small file size and thread count configurations \[bug 59969]
* Tuned cache access thread count and transfer queue depth on FilmLightOS 8 platform \[bug 59969]

***
