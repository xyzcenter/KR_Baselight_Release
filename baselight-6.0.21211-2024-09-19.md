---
icon: square-x
---

# Baselight 릴리스 6.0.21211 (2024-09-19)

## Baselight 릴리스 6.0.21211 (2024-09-19)

### Important Notes

Baselight 6.0 no longer supports **FilmLightOS 6**. Please contact [FilmLight Support](mailto:baselight-support@filmlight.ltd.uk) to discuss upgrading to FilmLightOS 8. Bug 60176

**RED Rocket** hardware is no longer supported. Bug 65725

Using a **Grade Result Colour Space** is deprecated and this functionality may be removed in a future release. [Please watch this video](https://filmlight.ltd.uk/graderesult) for information about recommended workflows for telecine-style grading. Bug 64729

**Dolby Vision external CMU devices** are no longer supported. Bug 62581

The **vtre** application is no longer included. Bug 66448

Many colour spaces have been updated with higher precision matrices. Scenes upgraded from Baselight 5.3 will use the older colour spaces and warn about that in the console. Visual output is consistent between original and new colour spaces. Bug 67302



### 중요 참고 사항 <a href="#undefined" id="undefined"></a>

Baselight 6.0은 더 이상 **FilmLightOS 6**을 지원하지 않습니다. FilmLight 지원 팀에 연락하여 FilmLightOS 8로 업그레이드에 대해 논의하시기 바랍니다. 버그 60176

**RED Rocket** 하드웨어는 더 이상 지원되지 않습니다. 버그 65725

**Grade Result Colour Space** 사용은 더 이상 권장되지 않으며, 이 기능은 향후 릴리스에서 제거될 수 있습니다. 텔레시네 스타일 그레이딩에 대한 권장 워크플로에 대한 정보는 이 비디오를 참조하십시오. 버그 64729

**Dolby Vision 외부 CMU** 장치는 더 이상 지원되지 않습니다. 버그 62581

**vtre** 애플리케이션이 더 이상 포함되지 않습니다. 버그 66448

많은 컬러 스페이스가 더 높은 정밀도의 매트릭스로 업데이트되었습니다. Baselight 5.3에서 업그레이드된 장면은 이전 컬러 스페이스를 사용하며 콘솔에 경고 메시지가 표시됩니다. 시각적 출력은 원본과 새로운 컬러 스페이스 간에 일관성을 유지합니다. 버그 67302

### New Features Since Baselight 6.0.20910

#### Miscellaneous

* Restored ability to set "Timeline Scroll Region" to 100%. Bug 69129
* DPX media with an orientation flag specifying a rotation can be slow to read. To enable this media to be read without applying the rotation, if a file called "ignore\_dpx\_orientation" is present in the folder with the DPX media, any orientation flag will be ignored. Note that this file is checked once per run, and is sought by the index service when the media is indexed. Bug 69142
* Added support for Apple ProRes and AAC encoded QuickTime files that are written using fragments. This fixes an issue where these files appeared to have fewer frames than actually available. Bug 68970
* Updated the fl-network package to version 8.5-21020. This provides various fixes and new features. Release notes for fl-network can be found in the documentation directory. Bug 69260
*   In FilmLight REMOTE, sessions owned by another user which your account has been invited to join are now listed in the CONNECT Sessions tab.

    You can also join a session using the email invite link by using the "Join with Invite" button in the CONNECT Sessions tab. The "Paste from Clipboard" button allows you to fill out the required information to join the session by copying the link from your email. Bug 69368
* Updated to Apple ProRes RAW SDK version 20240502. This adds support for _ProRes RAW plug-ins_, which let camera makers provide their own camera-specific processing. Bug 67795
* Added a new option in Render View to render to the Input Area mask, but not cropped to the Render Format. This allows the entire input area to be rendered, regardless of its mapped position in the Working and Render Formats. Bug 69475

### Baselight 6.0.20910 이후의 새로운 기능

기타

* "타임라인 스크롤 영역"을 100%로 설정할 수 있는 기능이 복원되었습니다. 버그 69129
* 회전 플래그가 지정된 방향을 가진 DPX 미디어는 읽는 속도가 느릴 수 있습니다. 이 미디어를 회전 적용 없이 읽을 수 있도록 하기 위해, DPX 미디어가 있는 폴더에 "ignore\_dpx\_orientation"이라는 파일이 있으면 방향 플래그는 무시됩니다. 이 파일은 실행당 한 번만 확인되며, 미디어가 인덱싱될 때 인덱스 서비스에서 확인합니다. 버그 69142
* Apple ProRes 및 AAC로 인코딩된 QuickTime 파일에서 프래그먼트를 사용하여 기록된 파일에 대한 지원이 추가되었습니다. 이 문제는 해당 파일이 실제로 사용 가능한 프레임보다 적은 프레임을 가지고 있는 것처럼 보이는 문제를 해결합니다. 버그 68970
* fl-network 패키지가 버전 8.5-21020으로 업데이트되었습니다. 이는 다양한 수정 사항과 새로운 기능을 제공합니다. fl-network의 릴리스 노트는 문서 디렉토리에서 확인할 수 있습니다. 버그 69260
* FilmLight REMOTE에서 다른 사용자가 소유하고 계정이 초대된 세션이 이제 CONNECT 세션 탭에 표시됩니다.
* 또한 "초대로 참여" 버튼을 사용하여 이메일 초대 링크를 통해 세션에 참여할 수 있습니다. "클립보드에서 붙여넣기" 버튼은 이메일에서 링크를 복사하여 세션 참여에 필요한 정보를 자동으로 채울 수 있도록 합니다. 버그 69368
* <mark style="color:red;">Apple ProRes RAW SDK 버전 20240502로 업데이트</mark>되었습니다. 이를 통해 카메라 제조사가 고유의 카메라 전용 프로세싱을 제공할 수 있는 ProRes RAW 플러그인 지원이 추가되었습니다. 버그 67795
* Render View에 입력 영역 마스크로 렌더링할 수 있는 새로운 옵션이 추가되었으며, Render Format으로 잘리지 않습니다. 이를 통해 입력 영역 전체가 작업 및 렌더 포맷에 매핑된 위치와 관계없이 렌더링될 수 있습니다. 버그 69475

### Bug Fixes Since Baselight 6.0.20910

* Fixed crash opening scenes containing existing, unrecognised OFX plugins. Bug 69113
* Fixed bug with negative ('Shift' modifier) picking in DKey operator. Bug 69133
* Fixed incorrect rendering when a blurred shape being used to matte a keyer is moved entirely outside the image area. Bug 69168
* Fixed Image Viewer cursor guide top/right edge line positioning. Bug 67772
* Added a fix to ensure that 'Grouped Grade Both Eyes' only affects stereo scenes. Bug 65879
* Reduced latency of cursor movement and grading on still frames for Network Stream outputs via FilmLight REMOTE when the image is being displayed via AJA or Blackmagic SDI output devices. Bug 69057
* Fixed resource leak caused by FLAPI SequenceDescriptor.get\_for\_template() if a path to a non-existing file or directory is used. Bug 69203
* Fixed issue reading audio-only MXF files. Bug 69204
* Automounts under /local are now compatible with FilmLightOS 8.8 and Rocky/Alma distributions. Bug 69200
* fl-diag no longer reports DDR5 RAM as 'Unknown'. Bug 69215
* Fixed an issue where the Gallery would prompt to upgrade autoloaded scenes when an upgraded version was already available. Also fixed a related issue causing Baselight to pause on 'Creating Gallery'. Bug 68474
* Fixed ProRes RAW Params behaviour when using Grouped Grading. Bug 69155
* Fixed incorrect images and crashes when working with ProRes RAW media on a Mac containing a ProRes hardware decoder (e.g. M1 Pro/Max). Bug 67794
* Fixed audio sync issues during scrubbing. This fixes incorrect application of the Audio Display Offset and prevents audio from the next frame from playing while scrubbing. Bug 69079
* Fixed bug resulting in incorrect (keyframed) shape control point handle behaviour/animation after they'd been explicitly transformed. Bug 69232
* Fixed issues with some OFX plugins, for example colour space identification in LiveGrain. Bug 69167
* Fixed potential crash on releasing the `Win` modifier (`Ctrl` on a Mac) key while transforming shape control points. Bug 68380
* Fixed incorrect colours reading some PNG files. Bug 69253
* Fixed crash when adjusting ProRes RAW parameters on macOS. Bug 69224
* Fixed image corruption seen in HDE-compressed ARRIRAW media on macOS. Bug 69226
* When rendering from OpenEXR media to an OpenEXR deliverable, any `compressionName` metadata is no longer copied from the source, as this may be confusing when writing with a different compression. Bug 69186
* Fixed incorrect cropping when Subtitles are transformed. Bug 69234
* Fixed issue that blocked mouse interactions in the Audio Waveform View. Bug 69290
* Fixed Baselight's laser pointer position on connected Client Views when the client stream resolution didn't match the working format. Bug 69297
* On Mac, fixed FilmLight REMOTE crash which could occur when dragging the window between monitors. Bug 69298
* Fixed crash when starting or stopping Client Sessions via the FilmLight CONNECT server. Bug 67314
* Fixed issue where Base Grade histograms would sometimes be drawn as 3 separate RGB channels instead of a single monochrome histogram. Bug 69136
* Fixed various Scope/Thumbnail related bugs when viewing the second colour space in Dual Colour Space display layouts. Bug 69269
* Fixed incorrect zoom/pan behaviour in Image Viewer. Bug 69272
* Issues with Apple ProRes RAW media occasionally decoding using the wrong settings appear to have been fixed by the updated Apple ProRes RAW SDK. Bug 66772
* Fixed crash when right-clicking in FLUX Manage View. Bug 69397
* Fixed "Resend Invites" button in Client Sessions view being disabled when clients are selected but not modified. \[Bug 69333]
* Fixed repeated pixels and cursor alignment in some DCI formats. Bug 69295
* Fixed an issue preventing comma separated CDL values in Adobe Premiere EDLs from being conformed. Bug 59139

### Baselight 6.0.20910 이후 버그 수정 사항

* 기존에 인식되지 않은 OFX 플러그인이 포함된 장면을 열 때 발생하던 충돌이 수정되었습니다. 버그 69113
* DKey 연산자에서 음수('Shift' 수정자)를 선택할 때 발생하던 버그가 수정되었습니다. 버그 69133
* 블러 처리된 형태가 키어에 매트로 사용될 때, 이미지 영역 밖으로 완전히 이동하면 잘못된 렌더링이 발생하던 문제가 수정되었습니다. 버그 69168
* 이미지 뷰어에서 커서 가이드 상단/오른쪽 가장자리 선 위치가 수정되었습니다. 버그 67772
* 'Grouped Grade Both Eyes'가 이제 스테레오 장면에만 영향을 미치도록 수정되었습니다. 버그 65879
* AJA 또는 Blackmagic SDI 출력 장치를 통해 이미지를 표시할 때 FilmLight REMOTE를 통해 네트워크 스트림 출력에 대한 정지 프레임의 커서 이동 및 그레이딩 지연이 줄어들었습니다. 버그 69057
* FLAPI SequenceDescriptor.get\_for\_template()가 존재하지 않는 파일이나 디렉토리의 경로를 사용할 때 발생하는 리소스 누수가 수정되었습니다. 버그 69203
* 오디오 전용 MXF 파일을 읽을 때 발생하던 문제가 수정되었습니다. 버그 69204
* /local의 자동 마운트가 이제 FilmLightOS 8.8 및 Rocky/Alma 배포판과 호환됩니다. 버그 69200
* fl-diag에서 DDR5 RAM이 더 이상 '알 수 없음'으로 보고되지 않습니다. 버그 69215
* 이미 업그레이드된 버전이 있음에도 갤러리에서 자동 로드된 장면을 업그레이드하라고 요청하는 문제를 수정했습니다. 또한 'Creating Gallery'에서 Baselight가 일시 중지되는 관련 문제도 수정되었습니다. 버그 68474
* Grouped Grading을 사용할 때 발생하던 ProRes RAW 매개변수 동작이 수정되었습니다. 버그 69155
* ProRes 하드웨어 디코더(e.g. M1 Pro/Max)를 포함한 Mac에서 ProRes RAW 미디어 작업 시 잘못된 이미지 및 충돌이 발생하던 문제가 수정되었습니다. 버그 67794
* 스크러빙 중 오디오 동기화 문제가 수정되었습니다. 이 수정은 오디오 디스플레이 오프셋이 잘못 적용되던 문제를 해결하고, 스크러빙 중 다음 프레임의 오디오가 재생되는 것을 방지합니다. 버그 69079
* 변환된 후 키프레임이 설정된 형태 제어점 핸들의 잘못된 동작/애니메이션을 유발하던 버그가 수정되었습니다. 버그 69232
* 일부 OFX 플러그인, 예를 들어 LiveGrain의 색상 공간 식별 문제를 수정했습니다. 버그 69167
* Win 수정자(Mac에서는 Ctrl) 키를 눌렀다가 해제할 때 발생할 수 있는 충돌을 수정했습니다. 버그 68380
* 일부 PNG 파일을 읽을 때 색상이 잘못 표시되던 문제가 수정되었습니다. 버그 69253
* macOS에서 ProRes RAW 매개변수를 조정할 때 발생하던 충돌을 수정했습니다. 버그 69224
* macOS에서 HDE 압축된 ARRIRAW 미디어에서 발생하던 이미지 손상 문제가 수정되었습니다. 버그 69226
* OpenEXR 미디어에서 OpenEXR 출력물로 렌더링할 때, 다른 압축 방식으로 쓰는 경우 혼란을 줄 수 있으므로 더 이상 compressionName 메타데이터가 소스에서 복사되지 않습니다. 버그 69186
* 자막을 변환할 때 잘못된 크롭이 발생하던 문제가 수정되었습니다. 버그 69234
* 오디오 파형 보기에서 마우스 상호작용을 차단하던 문제가 수정되었습니다. 버그 69290
* 클라이언트 스트림 해상도가 작업 포맷과 일치하지 않을 때, 연결된 클라이언트 뷰에서 Baselight의 레이저 포인터 위치가 수정되었습니다. 버그 69297
* Mac에서 모니터 간 창을 드래그할 때 FilmLight REMOTE 충돌 문제가 수정되었습니다. 버그 69298
* FilmLight CONNECT 서버를 통해 클라이언트 세션을 시작하거나 중지할 때 발생하던 충돌이 수정되었습니다. 버그 67314
* Base Grade 히스토그램이 때때로 3개의 개별 RGB 채널로 그려지던 문제를 수정하여 단일 흑백 히스토그램으로 표시되도록 했습니다. 버그 69136
* 이중 색상 공간 디스플레이 레이아웃에서 두 번째 색상 공간을 볼 때 발생하던 다양한 Scope/Thumbnail 관련 버그가 수정되었습니다. 버그 69269
* 이미지 뷰어에서 잘못된 줌/팬 동작이 수정되었습니다. 버그 69272
* Apple ProRes RAW 미디어가 잘못된 설정으로 디코딩되는 문제가 Apple ProRes RAW SDK 업데이트로 해결된 것으로 보입니다. 버그 66772
* FLUX 관리 보기에서 마우스 오른쪽 클릭 시 발생하던 충돌이 수정되었습니다. 버그 69397
* 클라이언트가 선택되었지만 수정되지 않은 경우에도 Client Sessions 보기에서 "Resend Invites" 버튼이 비활성화되는 문제가 수정되었습니다. 버그 69333
* 일부 DCI 형식에서 반복된 픽셀과 커서 정렬 문제가 수정되었습니다. 버그 69295
* Adobe Premiere EDL에서 쉼표로 구분된 CDL 값을 정합할 수 없던 문제가 수정되었습니다. 버그 59139

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
* The Relight operator currently has unexpected behaviour when dragging to set global scale. Bug 63798
* Blackboard Classic control surfaces exhibit occasional flickering when switching between operators. This will be fixed in a future beta release. Bug 62406
* Shots using RIFE ML Retime (either in a Sequence or a Retime operator) behave as if Process in Working Format is selected. This can result in lower-quality output if the Render Format is larger than the Working Format. These shots also crop the image to the Working Format. Bug 66016
* Using "Network Stream" as the Primary Video Output on Intel Mac Pro systems with AMD GPUs is currently unsupported. This will be addressed in a future release of Baselight 6.0. Bug 68727
* On Intel Mac systems with multiple GPUs, the MiDaS Flexi effect can sometimes produce a flickering matte when combined with some spatial operators. To work around this issue, enable the strip cache on the MiDaS strip. Bug 69040

### 알려진 문제

* macOS 13 Ventura를 실행하는 Intel macOS 시스템에서, 특히 RED 및 ARRIRAW 미디어를 사용할 때 심각한 이미지 손상이 발생합니다. 이 문제는 macOS 14 Sonoma에서 해결된 것으로 보입니다. 버그 62237
* macOS 시스템에서 공유된 볼륨이 원격 시스템에서 접근할 때 macOS의 버그로 인해 실패할 수 있습니다. 이 문제를 해결하려면:
  1. Dock 또는 Apple 메뉴에서 시스템 환경설정을 엽니다.
  2. "보안 및 개인 정보 보호"를 선택합니다.
  3. 자물쇠 아이콘을 클릭하고 암호 또는 Touch ID를 사용하여 변경을 허용합니다.
  4. 왼쪽 목록에서 "전체 디스크 접근"을 선택합니다.
  5. 오른쪽에서 + 버튼을 클릭하여 파일 탐색기를 엽니다.
  6. 키보드에서 / 키를 눌러 "폴더로 이동" 대화 상자를 엽니다.
  7. /sbin을 입력하고 이동을 클릭합니다.
  8. nfsd라는 파일을 선택하고 열기를 클릭합니다.
  9. Mac을 다시 시작하면 볼륨이 정상적으로 작동할 것입니다. 버그 62601
* Relight 연산자는 현재 글로벌 스케일을 설정할 때 예기치 않은 동작을 보입니다. 버그 63798
* Blackboard Classic 제어 표면은 연산자 간 전환 시 가끔 깜박임 현상이 발생합니다. 이는 향후 베타 릴리스에서 수정될 예정입니다. 버그 62406
* RIFE ML Retime(시퀀스 또는 Retime 연산자에서 사용)의 샷은 "작업 포맷에서 처리"가 선택된 것처럼 동작합니다. 이로 인해 렌더링 포맷이 작업 포맷보다 큰 경우 품질이 낮아질 수 있으며, 이러한 샷은 이미지를 작업 포맷으로 자릅니다. 버그 66016
* Intel Mac Pro 시스템에서 AMD GPU를 사용하는 경우 "Network Stream"을 기본 비디오 출력으로 사용하는 것은 현재 지원되지 않습니다. 이는 Baselight 6.0의 향후 릴리스에서 해결될 예정입니다. 버그 68727
* 다중 GPU를 사용하는 Intel Mac 시스템에서 MiDaS Flexi 효과는 일부 공간 연산자와 결합될 때 가끔 깜박이는 매트를 생성할 수 있습니다. 이 문제를 해결하려면 MiDaS 스트립에서 스트립 캐시를 활성화하십시오. 버그 69040
