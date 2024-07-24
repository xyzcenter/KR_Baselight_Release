# 😀 Baselight Release 5.3.18465 (2023-08-22)

## New Features Since Baselight 5.3.18123

* Updated AJA SDK to v16.2. This adds support for AJA IO X3 devices \[bug 60491]
* BRAW movie files can now be trimmed in Consolidate \[bug 58461]
* Added support for decoding XF-AVC Long GOP 4:2:2 10-bit (xfga) in QuickTime and MP4 files \[bug 64793]
* Dolby Metafier can now be used to validate Dolby Vision XML during export. Metafier is a command line utility bundled with Dolby Vision Professional Tools. The location of Metafier must be set in Preferences->Advanced->Dolby Vision Validation for Metafier Validation to work \[bug 64364]
* Added NVIDIA RTX 6000 Ada Lovelace as a supported GPU \[bug 65355]
* Added support for HP Z2 Mini G9 UI host \[bug 62887]
* Added support for Generation VIII Baselight TWO and Baselight X systems \[bug 65268]

## Baselight 5.3.18123 이후의 새로운 기능

* <mark style="background-color:green;">AJA SDK가 v16.2로 업데이트</mark>되었습니다. 이를 통해 <mark style="background-color:green;">AJA IO X3 장치를 지원</mark>합니다 \[버그 60491].
* 이제 <mark style="background-color:green;">BRAW 무비 파일을 Consolidate에서 자를(트림)</mark> 수 있습니다 \[버그 58461].
* <mark style="background-color:green;">QuickTime 및 MP4 파일에서 XF-AVC Long GOP 4:2:2 10-bit (xfga) 디코딩을 지원</mark>합니다 \[버그 64793].
* 이제 Dolby Metafier를 사용하여 내보내기 중에 Dolby Vision XML을 검증할 수 있습니다. Metafier는 Dolby Vision Professional Tools와 함께 제공되는 명령줄 유틸리티입니다. Metafier 검증을 작동하려면 Preferences->Advanced->Dolby Vision Validation에서 Metafier의 위치를 설정해야 합니다 \[버그 64364].
* <mark style="background-color:green;">NVIDIA RTX 6000 Ada Lovelace가 지원되는 GPU로 추가</mark>되었습니다 \[버그 65355].
* <mark style="background-color:green;">HP Z2 Mini G9 UI 호스트를 지원</mark>합니다 \[버그 62887].
* <mark style="background-color:green;">Generation VIII Baselight TWO 및 Baselight X 시스템을 지원</mark>합니다 \[버그 65268].



## Bug Fixes Since Baselight 5.3.18123

* Fixed "Could not find OFX plugin" error during pre-render \[bug 64697]
* Fixed handling of rotated ProRes RAW media (e.g. media recorded by Atomos Ninja V) \[bug 64795]
* Fixed Tape and Clip metadata in ARRI media \[bug 64839]
* Fixed Dolby Vision HDMI Tunneling in UHD on Kona 4 \[bug 64797]
* Fixed "Unknown colour space in doAffine" failure \[bug 64698]
* Fixed crash when rapidly adjusting an OFX parameter \[bug 64908]
* Fixed an accuracy issue that occurred when rapidly rotating the Blackboard Classic jog wheel \[bug 65009]
* Blackboard Classic Wacom tablets will now reconnect without restarting the desk service \[bug 65122]
* Fixed very slow behaviour with CLF LUTs \[bug 65096]
* "Averaged Frames" metadata is now shown for ARRI media \[bug 65198]
* Fixed slow performance of multi-part OpenEXR media on some filesystems (e.g. CVFS SAN on a macOS client) \[bug 65093]
* Fixed crash in Frame.io package when downloading comments made by anonymous users \[bug 65351]
* Fixed hang when rendering or playing and caching large format images \[bug 65041]
* Fixed crash when pressing Apply, with a Tracker strip and protect paste categories \[bug 64724]

## Baselight 5.3.18123 이후의 버그 수정

* 프리렌더 중 “OFX 플러그인을 찾을 수 없습니다” 오류를 수정했습니다 \[버그 64697].
* 회전된 ProRes RAW 미디어(예: Atomos Ninja V로 녹화된 미디어)의 처리를 수정했습니다 \[버그 64795].
* ARRI 미디어의 Tape 및 Clip 메타데이터를 수정했습니다 \[버그 64839].
* <mark style="background-color:green;">Kona 4에서 UHD Dolby Vision HDMI 터널링을 수정</mark>했습니다 \[버그 64797].
* "doAffine에서 알 수 없는 색상 공간” 오류를 수정했습니다 \[버그 64698].
* OFX 파라미터를 빠르게 조정할 때 발생하는 충돌을 수정했습니다 \[버그 64908].
* Blackboard Classic 조그 휠을 빠르게 회전할 때 발생하는 정확도 문제를 수정했습니다 \[버그 65009].
* Blackboard Classic Wacom 태블릿이 데스크 서비스를 다시 시작하지 않고도 재연결되도록 수정했습니다 \[버그 65122].
* CLF LUTs 사용 시 매우 느린 동작을 수정했습니다 \[버그 65096].
* <mark style="background-color:green;">ARRI 미디어에 대해 “평균 프레임” 메타데이터가 이제 표시</mark>됩니다 \[버그 65198].
* 일부 파일 시스템(예: macOS 클라이언트의 CVFS SAN)에서 멀티파트 OpenEXR 미디어의 느린 성능을 수정했습니다 \[버그 65093].
* 익명 사용자가 작성한 댓글을 다운로드할 때 Frame.io 패키지에서 발생하는 충돌을 수정했습니다 \[버그 65351].
* 대형 포맷 이미지를 렌더링하거나 재생 및 캐싱할 때 발생하는 중단 문제를 수정했습니다 \[버그 65041].
* Tracker 스트립과 보호 붙여넣기 카테고리를 사용할 때 적용 버튼을 누르면 발생하는 충돌을 수정했습니다 \[버그 64724].

***
