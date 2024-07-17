# 🥳 Baselight 릴리스 6.0.19881 (2024-03-20)

### New Features Since Baselight 6.0.19514

#### Sapphire for Baselight

*   FilmLight has partnered with Boris FX to create **Sapphire for Baselight**. This is the long-established Sapphire suite of OFX plug-ins, optimised for use in Baselight and now sold and supported by FilmLight.

    On Linux systems, Boris FX Sapphire is no longer supported in Baselight 6.0 or Daylight 6.0, instead you can purchase a subscription for Sapphire for Baselight directly from FilmLight.

    Sapphire for Baselight is not yet available for macOS systems; Baselight CONFORM and Daylight on macOS will continue to support Boris FX Sapphire until Sapphire for Baselight is released on macOS.

    If you have an existing Boris FX Sapphire licence, please contact your FilmLight sales representative. Bug 61703

## Baselight 6.0.19514 이후의 새로운 기능

### Sapphire for Baselight

• FilmLight는 Boris FX와 협력하여 Sapphire for Baselight를 만들었습니다. 이는 Baselight에서 사용하기 위해 최적화된 오래된 Sapphire OFX 플러그인 모음으로, 이제 FilmLight에서 판매 및 지원합니다.\
Linux 시스템에서는 Baselight 6.0 또는 Daylight 6.0에서 Boris FX Sapphire가 더 이상 지원되지 않습니다. 대신 FilmLight에서 직접 Sapphire for Baselight 구독을 구매할 수 있습니다.\
Sapphire for Baselight는 아직 macOS 시스템에서 사용할 수 없습니다. macOS의 Baselight CONFORM 및 Daylight는 Sapphire for Baselight가 macOS에 출시될 때까지 Boris FX Sapphire를 계속 지원할 것입니다.\
기존 Boris FX Sapphire 라이선스가 있는 경우 FilmLight 영업 담당자에게 문의하시기 바랍니다. (버그 61703)

#### SDK Updates

* Updated the Sony SMDK Toolkit to version 4.24 and Sony RAW SDK to version 5.0.0. This adds support for media from the Sony BURANO camera. Bug 64882

**SDK 업데이트**

Sony SMDK 툴킷을 버전 4.24로, Sony RAW SDK를 버전 5.0.0으로 업데이트했습니다. 이를 통해 Sony BURANO 카메라의 미디어 지원이 추가되었습니다. 버그 64882

#### Miscellaneous

* Added an option to the parade Scope Views to hide the scope title drawn in the lower-left corner of the scope. Bug 54786
* Added simple filtering to the Presets View. Bug 65559
* Added diagnostic support for Broadcom MR9580-8i8e RAID controller. Bug 65173
* Added support for Generation VIII Baselight ONE systems. Bug 67225
* Added support for reading XAVC H encoded MXF files. Bug 67210
* Added "Ctrl" modifier support to Shape opacity desk encoder press to reset its value to 0. Bug 26767

### 기타

* 파레이드 스코프 뷰에 스코프 제목을 숨길 수 있는 옵션을 추가했습니다. (버그 54786)
* 프리셋 뷰에 간단한 필터링을 추가했습니다. (버그 65559)
* Broadcom MR9580-8i8e RAID 컨트롤러에 대한 진단 지원을 추가했습니다. (버그 65173)
* Generation VIII Baselight ONE 시스템에 대한 지원을 추가했습니다. (버그 67225)
* XAVC H로 인코딩된 MXF 파일을 읽는 기능을 추가했습니다. (버그 67210)
* Shape 불투명도 데스크 인코더에 "Ctrl" 수정키 지원을 추가하여 값을 0으로 재설정할 수 있습니다. (버그 26767)

### Bug Fixes Since Baselight 6.0.19514

* Fixed large size of cache files for BLG media. Bug 66724
* Fixed gallery thumbnail related crash on scene close. Bug 66499
* Fixed crash in Flare when using `Ctrl` and the middle track ball to pan the image. Bug 66816
* Fixed a bug that could result in slight image differences in stacks that use "Texture Blend" layer blending mode in scenes upgraded from v5.3. Bug 66796
* Stopped the Composite Paint Strokes Separately button updating the timeline during the operation. Bug 66752
* Fixed crash on first run after installation on some Mac systems. Bug 50126
* Fixed issue in Shape overlays with Face Warp where the shape outline wouldn't represent the matte accurately. Bug 66832
* Fixed colour shifts seen when using 10-bit Integer 4:2:2 Y'CbCr caching. If you are using this caching option please run `bl-reset-cache` to remove older cached frames. Bug 32705
* Fixed crash exporting Dolby Vision XML from a scene without Dolby Vision Trim strips. Bug 66949
* Fixed issues with Dolby Vision Analysis of pure-black frames. Bug 66953
* Fixed issues with Dolby Vision 2.9 Tone Detail Weight control for 100-nit target displays. Bug 66807
* Fixed issue where matte generated using face warp would end up with holes when the face is bigger than the image. Bug 66959
* Fixed issue in the Tracker strip where clicking "Return to XXX" after copy and pasting an operator containing faces would select a wrong layer. Bug 66890
* Fixed crash using Presets in stereo strips. Bug 66531
* Improved help text in Flare operator. Bug 66851
* Fixed issue where the Presets View would list all presets saved from OFX effects in the same page, and a similar issue for presets saved from Shader effects.\
  **Important: This change will remove access to previously saved OFX and Shader presets**. Bug 65999
* Fixed issue where Tracker strips would lose their categories when copy and pasting and operator containing faces. Bug 66955
* Fixed crash when bypassing an inside outside operator. Bug 67001
* QuickTime/MP4 media rendered with Legacy colour space tagging no longer includes mastering display (`mdcv`) metadata. Bug 54320
* Fixed crash using Dolby Vision Analysis of Current Frame. Bug 67015
* Fixed errors on console when reading interlaced PNG media. Bug 67018
* Fixed issue where the Area Tracker couldn't be rotated on keyframes. Bug 67007
* Fixed invalid 'scene already exists' issue when opening a gallery scene and making a copy with the `_v6` suffix. Gallery scene names now require the full `_v6` suffix, before only `v6` was required. Also changed the dialog that shows when opening an old gallery to remove any mention of 'beta'. Bug 65463
* Fixed crash removing a cursor. Bug 17548
* Fixed crash when clicking between the thumbnail and filename columns of the sequence list within FLUX Manage. Bug 66631
* Fixed crash when ctrl-dragging on a control point in Matte Curve. Bug 67058
* Fixed crash when pressing "Composite Paint Strokes Separately" and the paint operator was on the outside of a layer. Bug 67059
* Fixed behaviour of the Discard option when quitting the application with multiple unsaved scenes. Bug 67055
* Updated behaviour to respect the convention that colour channels in OpenEXR media are premultiplied by alpha. This is now respected when inserting and rendering OpenEXR media. Bug 67048
* Fixed issue where upgrading Paint operators from 5.3 scenes would lose their trackers. Bug 67021
* Fixed issue where the face tracker would stop too often with motion blur, when the tracking quality is still good. Bug 67089
* Fixed issue where the left edges of text would sometimes not correctly align in some table columns. Bug 67067
* Fixed issue where the dialog prompting to make a copy of an old gallery would continue showing after choosing not to open the scene. Bug 67065
* Fixed 'missing global blur radius' error reported when Flip / Flop is used with Sander, Median or Erode / Dilate operator. Bug 49971
* Fixed behaviour when conforming AAFs so shot marks are not missing and are applied to the correct track. Bug 66633
* Fixed issue rendering DCI Audio using the 'Sequences + Audio File' option in Render View. Bug 67154
* Fixed an issue in Chromogen where changing layer on a default Chromogen would bring up the Presets View. Bug 66822
* Fixed an issue in the Gallery when showing the Current Cursor where the Gallery would scroll to the current cursor when the cursor moves to another shot. Bug 67209
* Fixed an issue with the XFS filesystem driver which could cause the system to reboot without notice. Bug 60706
* Improved Blackboard Classic detection in bl-config-xorg. Bug 58687
* Changed the design of colour wells to be more visible. Bug 67284
* Fixed failure to insert a Matchbox Shader that specifies a custom colour space file. Bug 67161
* Fixed issue only seen on macOS Sonoma, where the edges of images incorrectly had rectangular areas of black or white pixels. Bug 67341
* Removed the CPU speed test from fl-diag as it had become increasingly less useful. Bug 67227
* Fixed issue in FLUX Manage where dragging in the sequence list or non-media file list would scroll instead of performing a drag. Bug 67350
* Fixed a crash when conforming ALEs with possibly undefined keycode gearing values. Bug 61029
* Fixed crash in Flare occurring in Timeline Sort, moving or splitting strips. Bug 67102
* Fixed a render failure that would occur when rendering out shots from a v6.0 gallery scene. Bug 67420
* Fixed crash after deleting a Stereo Colour Matching strip. Bug 67082
* A new Flexi package filmlight-flexi-effects installer is available in the support section of the FilmLight website. It fixes a VRAM allocation issue on NVIDIA Ada GPUs. Bug 67033
* Fixed depth scaling issue with faces that would negatively affect Face Perspective. Bug 67490
* Fixed defunct fl-clean-shm processes on Linux. Bug 67516
* Fixed errors setting up the vol service on macOS 14 Sonoma. Bug 67498
* Fixed hang when generating a report preview or exporting a report containing a large number of shots. Bug 67598
* Fixed hang when using some OFX operator features (e.g. Sapphire Preset Browser) when the OFX operator is beneath another OFX operator. Bug 67661
* Updated the DPM diagnostic to include temperature range checks for NVMe devices. Bug 67429

### 버그 수정 사항 (Baselight 6.0.19514 이후)

* BLG 미디어에 대한 캐시 파일 크기 문제를 수정했습니다. (버그 66724)
* 장면 종료 시 갤러리 썸네일과 관련된 크래시를 수정했습니다. (버그 66499)
* Ctrl과 가운데 트랙 볼을 사용하여 이미지를 이동할 때 발생하는 Flare 크래시를 수정했습니다. (버그 66816)
* v5.3에서 업그레이드된 장면에서 "Texture Blend" 레이어 블렌딩 모드를 사용하는 스택에서 발생할 수 있는 미세한 이미지 차이 문제를 수정했습니다. (버그 66796)
* Composite Paint Strokes Separately 버튼이 작동 중 타임라인을 업데이트하지 않도록 수정했습니다. (버그 66752)
* 일부 Mac 시스템에서 설치 후 첫 실행 시 발생하는 크래시를 수정했습니다. (버그 50126)
* Face Warp를 사용하는 Shape 오버레이에서 쉐이프 윤곽이 매트를 정확하게 나타내지 않는 문제를 수정했습니다. (버그 66832)
* 10비트 Integer 4:2:2 Y'CbCr 캐싱을 사용할 때 발생하는 색상 변화 문제를 수정했습니다. 이 캐싱 옵션을 사용하는 경우, bl-reset-cache를 실행하여 이전에 캐시된 프레임을 제거하십시오. (버그 32705)
* Dolby Vision Trim 스트립이 없는 장면에서 Dolby Vision XML을 내보낼 때 발생하는 크래시를 수정했습니다. (버그 66949)
* 순수 검은색 프레임의 Dolby Vision Analysis 문제를 수정했습니다. (버그 66953)
* 100니트 타겟 디스플레이에 대한 Dolby Vision 2.9 Tone Detail Weight 제어 문제를 수정했습니다. (버그 66807)
* Face Warp를 사용하여 생성된 매트가 얼굴이 이미지보다 클 때 구멍이 생기는 문제를 수정했습니다. (버그 66959)
* Tracker 스트립에서 얼굴을 포함하는 연산자를 복사하여 붙여넣은 후 "Return to XXX"를 클릭하면 잘못된 레이어가 선택되는 문제를 수정했습니다. (버그 66890)
* 스테레오 스트립에서 프리셋을 사용할 때 발생하는 크래시를 수정했습니다. (버그 66531)
* Flare 연산자의 도움말 텍스트를 개선했습니다. (버그 66851)
* 프리셋 뷰에서 OFX 효과로 저장된 모든 프리셋이 같은 페이지에 나열되는 문제와 Shader 효과로 저장된 프리셋과 관련된 유사한 문제를 수정했습니다. 중요한: 이 변경으로 이전에 저장된 OFX 및 Shader 프리셋에 접근할 수 없습니다. (버그 65999)
* Tracker 스트립에서 얼굴을 포함하는 연산자를 복사하여 붙여넣을 때 카테고리를 잃는 문제를 수정했습니다. (버그 66955)
* 인사이드 아웃사이드 연산자를 바이패스할 때 발생하는 크래시를 수정했습니다. (버그 67001)
* Legacy 색상 공간 태그가 있는 QuickTime/MP4 미디어가 마스터링 디스플레이 (mdcv) 메타데이터를 포함하지 않도록 수정했습니다. (버그 54320)
* 현재 프레임의 Dolby Vision Analysis를 사용할 때 발생하는 크래시를 수정했습니다. (버그 67015)
* 인터레이스된 PNG 미디어를 읽을 때 콘솔에 나타나는 오류를 수정했습니다. (버그 67018)
* Area Tracker에서 키프레임에 회전할 수 없는 문제를 수정했습니다. (버그 67007)
* 갤러리 장면을 열고 \_v6 접미사로 복사할 때 발생하는 '장면이 이미 존재합니다' 오류를 수정했습니다. 이제 갤러리 장면 이름은 전체 \_v6 접미사를 필요로 하며, 이전에는 v6만 필요했습니다. 또한, 이전 갤러리를 열 때 '베타' 언급을 제거하는 대화 상자를 변경했습니다. (버그 65463)
* 커서를 제거할 때 발생하는 크래시를 수정했습니다. (버그 17548)
* FLUX Manage 내 시퀀스 목록에서 썸네일과 파일명 열 사이를 클릭할 때 발생하는 크래시를 수정했습니다. (버그 66631)
* Matte Curve에서 컨트롤 포인트를 Ctrl-드래그할 때 발생하는 크래시를 수정했습니다. (버그 67058)
* 레이어 외부에 페인트 연산자가 있을 때 "Composite Paint Strokes Separately"를 누를 때 발생하는 크래시를 수정했습니다. (버그 67059)
* 여러 개의 저장되지 않은 장면이 있을 때 애플리케이션을 종료할 때 Discard 옵션의 동작을 수정했습니다. (버그 67055)
* OpenEXR 미디어의 색상 채널이 알파에 의해 프리멀티플라이된다는 규칙을 준수하도록 동작을 업데이트했습니다. 이는 OpenEXR 미디어를 삽입하고 렌더링할 때 적용됩니다. (버그 67048)
* 5.3 장면에서 업그레이드된 페인트 연산자가 트래커를 잃는 문제를 수정했습니다. (버그 67021)
* 얼굴 트래커가 모션 블러로 인해 너무 자주 멈추는 문제를 수정했습니다. 트래킹 품질이 여전히 좋을 때도 마찬가지입니다. (버그 67089)
* 일부 테이블 열에서 텍스트의 왼쪽 가장자리가 올바르게 정렬되지 않는 문제를 수정했습니다. (버그 67067)
* 오래된 갤러리의 복사본을 만들도록 요청하는 대화 상자가 장면을 열지 않기로 선택한 후에도 계속 표시되는 문제를 수정했습니다. (버그 67065)
* Sander, Median 또는 Erode / Dilate 연산자와 함께 Flip / Flop을 사용할 때 보고된 '전역 블러 반경 누락' 오류를 수정했습니다. (버그 49971)
* AAF를 적합하게 만들 때 샷 마크가 누락되지 않고 올바른 트랙에 적용되도록 동작을 수정했습니다. (버그 66633)
* Render View에서 'Sequences + Audio File' 옵션을 사용하여 DCI 오디오를 렌더링할 때 발생하는 문제를 수정했습니다. (버그 67154)
* 기본 Chromogen에서 레이어를 변경할 때 프리셋 뷰가 나타나는 문제를 수정했습니다. (버그 66822)
* 갤러리에서 현재 커서를 표시할 때 커서가 다른 샷으로 이동하면 갤러리가 현재 커서로 스크롤되는 문제를 수정했습니다. (버그 67209)
* 시스템이 예고 없이 재부팅될 수 있는 XFS 파일 시스템 드라이버 문제를 수정했습니다. (버그 60706)
* bl-config-xorg에서 Blackboard Classic 감지를 개선했습니다. (버그 58687)
* 색상 웰의 디자인을 더 잘 보이도록 변경했습니다. (버그 67284)
* 사용자 지정 색상 공간 파일을 지정하는 Matchbox Shader를 삽입할 수 없는 문제를 수정했습니다. (버그 67161)
* macOS Sonoma에서만 발생하는 이미지 가장자리에 검은색 또는 흰색 사각형 영역이 나타나는 문제를 수정했습니다. (버그 67341)
* fl-diag에서 CPU 속도 테스트를 제거했습니다. 이는 점점 유용성이 감소하고 있었습니다. (버그 67227)
* FLUX Manage에서 시퀀스 목록 또는 비미디어 파일 목록을 드래그할 때 스크롤이 발생하는 대신 드래그가 수행되는 문제를 수정했습니다. (버그 67350)
* 정의되지 않은 키코드 기어링 값이 있을 수 있는 ALE를 적합하게 만들 때 발생하는 크래시를 수정했습니다. (버그 61029)
* 타임라인 정렬, 이동 또는 스트립 분할 시 발생하는 Flare 크래시를 수정했습니다. (버그 67102)
* v6.0 갤러리 장면에서 샷을 렌더링할 때 발생하는 렌더 실패를 수정했습니다. (버그 67420)
* 스테레오 색상 맞추기 스트립을 삭제한 후 발생하는 크래시를 수정했습니다. (버그 67082)
* 새로운 Flexi 패키지 filmlight-flexi-effects 설치 프로그램이 FilmLight 웹사이트 지원 섹션에 제공되었습니다. 이 패키지는 NVIDIA Ada GPU의 VRAM 할당 문제를 해결합니다. (버그 67033)
* 얼굴의 깊이 스케일링 문제를 수정하여 Face Perspective에 부정적인 영향을 미치지 않도록 했습니다. (버그 67490)
* Linux에서 비정상적인 fl-clean-shm 프로세스를 수정했습니다. (버그 67516)
* macOS 14 Sonoma에서 vol 서비스를 설정할 때 발생하는 오류를 수정했습니다. (버그 67498)
* 많은 샷을 포함하는 보고서 미리보기 생성 또는 보고서 내보내기 시 발생하는 멈춤 문제를 수정했습니다. (버그 67598)
* 다른 OFX 연산자 아래에 OFX 연산자가 있을 때 일부 OFX 연산자 기능(예: Sapphire Preset Browser)을 사용할 때 발생하는 멈춤 문제를 수정했습니다. (버그 67661)
* NVMe 장치의 온도 범위 검사를 포함하도록 DPM 진단을 업데이트했습니다. (버그 67429)
