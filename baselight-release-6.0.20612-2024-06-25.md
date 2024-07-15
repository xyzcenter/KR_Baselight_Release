# Baselight Release 6.0.20612 (2024-06-25)

##

### Important Notes

Baselight 6.0 no longer supports **FilmLightOS 6**. Please contact [FilmLight Support](mailto:baselight-support@filmlight.ltd.uk) to discuss upgrading to FilmLightOS 8. Bug 60176

**RED Rocket** hardware is no longer supported. Bug 65725

Using a **Grade Result Colour Space** is deprecated and this functionality may be removed in a future release. [Please watch this video](https://filmlight.ltd.uk/graderesult) for information about recommended workflows for telecine-style grading. Bug 64729

**Dolby Vision external CMU devices** are no longer supported. Bug 62581

The **vtre** application is no longer included. Bug 66448



### 중요한 사항들

• Baselight 6.0은 더 이상 FilmLightOS 6를 지원하지 않습니다. FilmLightOS 8로 업그레이드에 대해 논의하려면 FilmLight Support에 문의하세요. Bug 60176

• RED Rocket 하드웨어는 더 이상 지원되지 않습니다. Bug 65725

• Grade Result Colour Space 사용은 폐기 예정이며, 이 기능은 향후 릴리즈에서 제거될 수 있습니다.[ 이 비디오](https://filmlight.ltd.uk/graderesult)를 시청하여 추천 워크플로우에 대한 정보를 확인하세요. Bug 64729

• Dolby Vision 외부 CMU 장치는 더 이상 지원되지 않습니다. Bug 62581

• vtre 애플리케이션은 더 이상 포함되지 않습니다. Bug 66448

### New Features Since Baselight 6.0.20515

* Added a command-line option `-p` to flit-daemon to enable parallel access to NFS volumes which can improve copy performance. The option is disabled by default because it can result in corrupted data when enabled with some storage implementations. Bug 68462

### Baselight 6.0.20515 이후 추가된 새로운 기능들

• flit-daemon에 NFS 볼륨에 대한 병렬 접근을 가능하게 하는 명령줄 옵션 -p가 추가되었습니다. 이 옵션은 일부 스토리지 구현에서 데이터 손상을 초래할 수 있어 기본적으로 비활성화되어 있습니다. Bug 68462

### Bug Fixes Since Baselight 6.0.20515

* Fixed missing cursor on Blackmagic Design SDI outputs when using 12-bit video formats. Bug 68417
* Metadata is now only copied from input QuickTime media to QuickTime deliverables when it is the same for every frame of the deliverable. In addition, to avoid misidentification of colour spaces, colour information metadata is now only copied when "Use Input Colour Space" is selected. Bug 68278
* Fixed failures in Dolby Vision Analysis with some combinations of Analysis Area and Working Format, e.g. 2.0:1 at UHD. Bug 68561
* Fixed initial 'Category' menu setting in 'Set Mark Note Text/Category' dialog when invoked from a numeric keypad shortcut. Bug 68599
* Fixed issue rendering audio with negative offsets when 'Movie Frame Rate' differs from 'Render Frame Rate'. Bug 67123
* Fixed `%C` not being used in paths to LUT files contained in RED and other media. Bug 68625
* Opening Presets View no longer causes the timeline cache to be re-checked. Bug 68515

### 베이스라이트  6.0.20515 이후 버그 수정 사항

• 12비트 비디오 포맷을 사용할 때 Blackmagic Design SDI 출력에서 커서가 보이지 않던 문제를 수정했습니다. (버그 68417)

• 이제 메타데이터는 QuickTime 미디어 입력에서 QuickTime 배급물로 복사될 때, 배급물의 모든 프레임에 동일할 때만 복사됩니다. 또한 색상 공간의 오인식을 방지하기 위해 “입력 색상 공간 사용”이 선택된 경우에만 색상 정보 메타데이터가 복사됩니다. (버그 68278)

• 일부 분석 영역과 작업 포맷 조합에서 Dolby Vision Analysis가 실패하던 문제를 수정했습니다. 예: UHD에서 2.0:1. (버그 68561)

• 숫자 키패드 바로가기를 사용하여 ‘마크 노트 텍스트/카테고리 설정’ 대화 상자를 호출할 때 초기 ‘카테고리’ 메뉴 설정 문제를 수정했습니다. (버그 68599)

• ‘영화 프레임 속도’가 ‘렌더 프레임 속도’와 다를 때 음성을 렌더링하는 과정에서 발생하던 음성 오프셋 문제를 수정했습니다. (버그 67123)

• RED 및 기타 미디어에 포함된 LUT 파일 경로에 %C가 사용되지 않던 문제를 수정했습니다. (버그 68625)

• 프리셋 보기 열기가 더 이상 타임라인 캐시를 다시 확인하지 않도록 수정했습니다. (버그 68515)

### Known Issues

* Significant image corruption is seen on Intel macOS systems running macOS 13 Ventura, especially when using RED and ARRIRAW media. This appears to be fixed in macOS 14 Sonoma. Bug 62237
*   Volumes shared from macOS systems may fail when accessed from remote systems due to a bug in macOS. To work around this issue:

    * Open System Preferences from the Dock or the Apple menu
    * Choose "Security & Privacy"
    * Click the padlock icon and use your password or Touch ID to allow changes to be made
    * Select "Full Disk Access" in the list on the left
    * Click the `+` button on the right to open a file browser
    * On your keyboard, press `/` to open the "Go to the folder" dialog
    * Enter `/sbin` and click `Go`
    * Select the file called `nfsd` and click `Open`

    After restarting your Mac, the volume(s) should now work correctly. Bug 62601
* Saturated areas in Photo RAW files can acquire a colour tint when adjusting the exposure slider in the Photo RAW Parameters operator while blending highlights. Bug 44769
* The Relight operator currently has unexpected behaviour when dragging to set global scale. Bug 63798
* Blackboard Classic control surfaces exhibit occasional flickering when switching between operators. This will be fixed in a future beta release. Bug 62406
* Shots using RIFE ML Retime (either in a Sequence or a Retime operator) behave as if Process in Working Format is selected. This can result in lower-quality output if the Render Format is larger than the Working Format. These shots also crop the image to the Working Format. Bug 66016



### 알려진 문제

• Intel macOS 시스템에서 macOS 13 Ventura를 실행할 때, 특히 RED 및 ARRIRAW 미디어를 사용할 때 심각한 이미지 손상이 발생합니다. 이 문제는 macOS 14 Sonoma에서 해결된 것으로 보입니다. (버그 62237)

• macOS 시스템에서 공유된 볼륨이 원격 시스템에서 접근할 때 macOS의 버그로 인해 실패할 수 있습니다. 이 문제를 해결하기 위한 방법:

1\. Dock 또는 Apple 메뉴에서 시스템 환경설정을 엽니다.

2\. “보안 및 개인정보 보호”를 선택합니다.

3\. 자물쇠 아이콘을 클릭하고 비밀번호 또는 Touch ID를 사용하여 변경을 허용합니다.

4\. 왼쪽 목록에서 “전체 디스크 접근”을 선택합니다.

5\. 오른쪽의 + 버튼을 클릭하여 파일 브라우저를 엽니다.

6\. 키보드에서 /를 눌러 “폴더로 이동” 대화 상자를 엽니다.

7\. /sbin을 입력하고 이동을 클릭합니다.

8\. nfsd 파일을 선택하고 열기를 클릭합니다.

9\. Mac을 재시작한 후 볼륨이 정상적으로 작동할 것입니다. (버그 62601)

• Photo RAW 파일에서 노출 슬라이더를 조정할 때, 강조된 영역이 색조를 띠게 되는 문제가 발생합니다. (버그 44769)

• Relight 연산자를 사용할 때, 전역 스케일 설정 시 예상치 못한 동작이 발생합니다. (버그 63798)

• Blackboard Classic 제어 표면은 연산자 간 전환 시 가끔 깜빡이는 문제가 있습니다. 이 문제는 향후 베타 릴리스에서 수정될 예정입니다. (버그 62406)

• RIFE ML Retime을 사용하는 장면(시퀀스 또는 Retime 연산자 내)은 작업 포맷에서 처리되는 것처럼 동작합니다. 렌더 포맷이 작업 포맷보다 클 경우, 이로 인해 품질이 낮아질 수 있습니다. 이러한 장면은 또한 이미지를 작업 포맷으로 자릅니다. (버그 66016)

\
