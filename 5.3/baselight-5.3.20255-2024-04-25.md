# 😀 Baselight 릴리스 5.3.20255 (2024-04-25)

## Important Notes

Baselight 5.3 no longer supports the following legacy hardware and OS platforms:

* Baselight FOUR and Baselight EIGHT systems
* DVI-to-SDI Convertors or Combiners performing that function
* RME Hammerfall audio cards
* Tape deck control within Baselight (the standalone VTRE application remains available)
* Spirit telecine control
* NVIDIA Quadro NVS 450 GPU (as a User Interface display card)
* macOS 11 Big Sur and earlier

Generation V systems using DVI-to-SDI Convertors or Combiners need to either be upgraded to the Baselight Ultra High Definition option (see data sheet) which includes an AJA Kona 4 PCIe card or revert to GPU DVI output. Earlier generation systems are now constrained to a GPU DVI output only.

Please contact Baselight support to discuss upgrading from a NVS 450 if required.

FilmLightOS 8 or later is required to use GPU JPEG 2000 acceleration with NVIDIA Ampere GPUs, and to use Blackmagic RAW media

Truelight Player (tl-player) is no longer available.

When running Baselight CONFORM or Daylight on macOS with AJA devices, AJA Software v16.x is required.



## **중요 참고 사항**

Baselight 5.3는 다음과 같은 구형 하드웨어 및 OS 플랫폼을 더 이상 지원하지 않습니다:

* Baselight FOUR 및 Baselight EIGHT 시스템
* DVI-to-SDI 변환기 또는 조합기
* RME Hammerfall 오디오 카드
* Baselight 내 테이프 덱 제어 (독립형 VTRE 애플리케이션은 계속 제공됨)
* Spirit 텔레시네 제어
* NVIDIA Quadro NVS 450 GPU (사용자 인터페이스 디스플레이 카드로서)
* macOS 11 Big Sur 및 이전 버전

DVI-to-SDI 변환기 또는 조합기를 사용하는 Generation V 시스템은 Baselight Ultra High Definition 옵션(데이터 시트 참조)으로 업그레이드하여 AJA Kona 4 PCIe 카드를 포함하거나 GPU DVI 출력을 사용해야 합니다. 이전 세대 시스템은 이제 GPU DVI 출력만 사용할 수 있습니다.

NVS 450에서 업그레이드가 필요한 경우 Baselight 지원에 문의하십시오.

NVIDIA Ampere GPU로 GPU JPEG 2000 가속 및 Blackmagic RAW 미디어를 사용하려면 FilmLightOS 8 이상이 필요합니다.

Truelight Player (tl-player)는 더 이상 제공되지 않습니다.

macOS에서 AJA 장치를 사용하는 Baselight CONFORM 또는 Daylight를 실행할 때는 AJA 소프트웨어 v16.x가 필요합니다.



## New Features Since Baselight 5.3.19778

* Updated to R3D SDK 8.5.1. This fixes several bugs, and adds support for V-RAPTOR \[X] media. Note that Extended Highlights is beta functionality and is not yet available \[bug 67193]
* Added support for NVIDIA 550.76 driver \[bug 68044]
* Added support for new FilmLight CONNECT traffic routing scheme \[bug 68056]

## **Baselight 5.3.19778 이후 새로운 기능**

• R3D SDK 8.5.1로 업데이트되었습니다. 이 업데이트는 여러 버그를 수정하고 V-RAPTOR \[X] 미디어를 지원합니다. 참고로 Extended Highlights는 베타 기능으로 아직 사용 가능하지 않습니다 \[버그 67193].

• NVIDIA 550.76 드라이버 지원이 추가되었습니다 \[버그 68044].

• 새로운 FilmLight CONNECT 트래픽 라우팅 스킴 지원이 추가되었습니다 \[버그 68056].



## Bug Fixes Since Baselight 5.3.19778

* Fixed crash in flapid when adding an image item to a FormatBurnin via FLAPI \[bug 67724]
* Fixed extremely slow reading of some BLG files, in particular those using the "ACES RRT 1.1+" DRT \[bug 33064]
* Fixed issue with shot length for sequences inserted into 23.976fps scenes using FLAPI \[bug 67774]
* QuickTime metadata with reverse-DNS names, such as that in Apple ProRes RAW media, is now written to OpenEXR output files \[bug 67635]
* Removed the CPU speed test from fl-diag as it had become increasingly less useful \[bug 67227]
* Fixed error message when creating a new FilmLight CONNECT session via the Client Sessions view \[bug 66626]

## **Baselight 5.3.19778 이후 버그 수정**

• FLAPI를 통해 FormatBurnin에 이미지 항목을 추가할 때 flapid에서 발생하는 충돌을 수정했습니다 \[버그 67724]

• 특히 “ACES RRT 1.1+” DRT를 사용하는 일부 BLG 파일을 매우 느리게 읽는 문제를 수정했습니다 \[버그 33064]

• FLAPI를 사용하여 23.976fps 장면에 삽입된 시퀀스의 샷 길이 문제를 수정했습니다 \[버그 67774]

• Apple ProRes RAW 미디어와 같이 역-DNS 이름이 포함된 QuickTime 메타데이터가 이제 OpenEXR 출력 파일에 기록됩니다 \[버그 67635]

• 유용성이 점점 떨어져 fl-diag에서 CPU 속도 테스트를 제거했습니다 \[버그 67227]

• 클라이언트 세션 보기를 통해 새로운 FilmLight CONNECT 세션을 만들 때 발생하는 오류 메시지를 수정했습니다 \[버그 66626]

## Known Issues

* Significant image corruption is seen on Intel macOS systems running macOS 13 Ventura, especially when using RED and ARRIRAW media. This appears to be fixed in macOS 14 Sonoma \[bug 62237]
* Volumes shared from macOS systems may fail when accessed from remote systems due to a bug in macOS. To work around this issue:
  * open System Preferences from the Dock or the Apple menu
  * choose "Security & Privacy"
  * click the padlock icon and use your password or Touch ID to allow changes to be made
  * select "Full Disk Access" in the list on the left
  * click the "+" button on the right to open a file browser
  * on your keyboard, press "/" to open the "Go to the folder" dialog
  * enter "/sbin" and click "Go"
  * select the file called "nfsd" and click "Open" After restarting your Mac, the volume(s) should now work correctly \[bug 62601]
* Saturated areas in Photo RAW files can acquire a colour tint when adjusting the exposure slider in the Photo RAW Parameters operator while blending highlights \[bug 44769]
* Setting the Resampling Method in a strip to "Optical Flow" will force a transform to the scene's Working Format, similar to the "Process in Working Format" option. Please consider this when rendering to formats larger than the Working Format \[bug 54652]

## **알려진 문제**

• Intel macOS 시스템에서 macOS 13 Ventura를 실행할 때 특히 RED 및 ARRIRAW 미디어를 사용할 때 심각한 이미지 손상이 발생할 수 있습니다. 이 문제는 macOS 14 Sonoma에서 해결된 것으로 보입니다 \[버그 62237].

• macOS 시스템에서 공유된 볼륨이 원격 시스템에서 접근할 때 실패할 수 있는 문제가 있습니다. 이 문제를 해결하기 위해 다음 단계를 수행하십시오:

* Dock 또는 Apple 메뉴에서 시스템 환경설정을 엽니다.
* “보안 및 개인 정보 보호”를 선택합니다.
* 자물쇠 아이콘을 클릭하고 비밀번호 또는 터치 ID를 사용하여 변경을 허용합니다.
* 왼쪽 목록에서 “전체 디스크 접근”을 선택합니다.
* 오른쪽의 “+” 버튼을 클릭하여 파일 브라우저를 엽니다.
* 키보드에서 “/“를 눌러 “폴더로 이동” 대화 상자를 엽니다.
* “/sbin”을 입력하고 “이동”을 클릭합니다.
* “nfsd” 파일을 선택하고 “열기”를 클릭합니다. Mac을 재시작한 후, 볼륨이 올바르게 작동해야 합니다 \[버그 62601].

• Photo RAW 파일의 포화 영역이 Photo RAW Parameters 연산자에서 노출 슬라이더를 조정할 때 색상 틴트를 얻을 수 있습니다 \[버그 44769].

• 스트립의 리샘플링 방법을 “Optical Flow”로 설정하면 “작업 포맷으로 처리” 옵션과 유사하게 장면의 작업 포맷으로 변환을 강제합니다. 작업 포맷보다 큰 포맷으로 렌더링할 때 이를 고려하십시오 \[버그 54652].

***
