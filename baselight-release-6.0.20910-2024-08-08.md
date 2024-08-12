# Baselight Release 6.0.20910 (2024-08-08)

## Baselight Release 6.0.20910 (2024-08-08)



## Important Notes

Baselight 6.0 no longer supports **FilmLightOS 6**. Please contact [FilmLight Support](mailto:baselight-support@filmlight.ltd.uk) to discuss upgrading to FilmLightOS 8. Bug 60176

**RED Rocket** hardware is no longer supported. Bug 65725

Using a **Grade Result Colour Space** is deprecated and this functionality may be removed in a future release. [Please watch this video](https://filmlight.ltd.uk/graderesult) for information about recommended workflows for telecine-style grading. Bug 64729

**Dolby Vision external CMU devices** are no longer supported. Bug 62581

The **vtre** application is no longer included. Bug 66448

Many colour spaces have been updated with higher precision matrices. Scenes upgraded from Baselight 5.3 will use the older colour spaces and warn about that in the console. Visual output is consistent between original and new colour spaces. Bug 67302





## 중요 참고 사항

Baselight 6.0은 더 이상 **FilmLightOS 6**을 지원하지 않습니다. FilmLight 지원 팀에 연락하여 FilmLightOS 8로 업그레이드에 대해 논의하시기 바랍니다. 버그 60176

**RED Rocket** 하드웨어는 더 이상 지원되지 않습니다. 버그 65725

**Grade Result Colour Space** 사용은 더 이상 권장되지 않으며, 이 기능은 향후 릴리스에서 제거될 수 있습니다. 텔레시네 스타일 그레이딩에 대한 권장 워크플로에 대한 정보는 이 비디오를 참조하십시오. 버그 64729

**Dolby Vision 외부 CMU** 장치는 더 이상 지원되지 않습니다. 버그 62581

**vtre** 애플리케이션이 더 이상 포함되지 않습니다. 버그 66448

많은 컬러 스페이스가 더 높은 정밀도의 매트릭스로 업데이트되었습니다. Baselight 5.3에서 업그레이드된 장면은 이전 컬러 스페이스를 사용하며 콘솔에 경고 메시지가 표시됩니다. 시각적 출력은 원본과 새로운 컬러 스페이스 간에 일관성을 유지합니다. 버그 67302







## New Features Since Baselight 6.0.20612

## Baselight 6.0.20612 이후의 새로운 기능



### JPEG-XS Caching

*   A new JPEG-XS timeline cache compression option is available on Linux. The compression significantly reduces the disk bandwidth required for cached playback, so it is particularly useful when working at high resolutions such as UHD8K, at high frame rates and/or when the cache is located on non-solid-state drives.

    JPEG-XS caching is an optional purchase due to the codec SDK licensing fee; please contact your FilmLight sales representative to discuss. Bug 61823

### JPEG-XS 캐싱

새로운 JPEG-XS 타임라인 캐시 압축 옵션이 Linux에서 사용할 수 있습니다. 이 압축 기능은 캐시된 재생을 위한 디스크 대역폭을 크게 줄여주며, 특히 UHD8K와 같은 고해상도 작업이나 높은 프레임 속도 작업, 또는 캐시가 비(非) SSD 드라이브에 위치한 경우에 유용합니다.

JPEG-XS 캐싱은 코덱 SDK 라이선스 비용으로 인해 선택적 구매 항목이며, 이에 대한 논의를 위해 FilmLight 영업 담당자에게 문의하시기 바랍니다. 버그 61823

### Flexi Effects

*   #### Face Tracker and RIFE Retimer

    These Machine Learning effects are now supported on the Intel Mac platform. The effects will need to be installed on the system using the filmlight-flexi-effects installer, which is available in the support section of the FilmLight website. Bug 66459
*   #### MiDaS Depth Map

    MiDaS Depth Map is now available as an additional Flexi installer, serving as an example Flexi effect.

    MiDaS computes relative inverse depth from a single image, using a Flexi effect to run the machine learning algorithm. This effect will need to be installed on the system using the midas-flexi-effect installer, which is available in the support section of the FilmLight website.

    It can be added from the "Insert" menu by choosing "Flexi Effect" or via "Flexi Effect" in the layer operator grid. MiDaS is particularly useful when used in conjunction with the Bokeh operator, as it provides per-pixel depth information which can be used to drive the amount of Bokeh. Bug 67398

### Flexi Effects(플랙시 이펙트)

* Face Tracker와 RIFE Retimer

이 머신 러닝 효과들은 이제 Intel Mac 플랫폼에서 지원됩니다. 이 효과들은 FilmLight 웹사이트의 지원 섹션에서 제공되는 filmlight-flexi-effects 설치 프로그램을 사용하여 시스템에 설치해야 합니다. (버그 66459)\


* MiDaS Depth Map

MiDaS Depth Map은 추가적인 Flexi 설치 프로그램으로 제공되며, Flexi 효과의 예시로 사용됩니다. MiDaS는 머신 러닝 알고리즘을 실행하기 위해 Flexi 효과를 사용하여 단일 이미지에서 상대적 역(반대적)깊이를 계산합니다. 이 효과는 FilmLight 웹사이트의 지원 섹션에서 제공되는 midas-flexi-effect 설치 프로그램을 사용하여 시스템에 설치해야 합니다.

이 효과는 “Insert” 메뉴에서 “Flexi Effect”를 선택하거나 레이어 오퍼레이터 그리드에서 “Flexi Effect”를 통해 추가할 수 있습니다. MiDaS는 Bokeh 오퍼레이터와 함께 사용할 때 특히 유용하며, 픽셀 단위의 깊이 정보를 제공하여 Bokeh 양을 조절하는 데 사용할 수 있습니다. (버그 67398)



### FilmLight REMOTE

*   FilmLight REMOTE is a new application for receiving network video streams (encoded as HEVC or JPEG-XS) from FilmLight products. It supports local colour management of the video streams, and output via AJA and Blackmagic Design SDI hardware.

    It can also integrate with NICE DCV for remote operation of Baselight or Daylight systems.

    Please see the included FilmLight REMOTE User Guide in the Baselight Help menu for more information on its configuration and usage. Bug 61988

### FilmLight REMOTE (필름라이트 리모트)

FilmLight REMOTE는 FilmLight 제품에서 네트워크 비디오 스트림(HEVC 또는 JPEG-XS로 인코딩)을 수신하기 위한 새로운 애플리케이션입니다. 이 애플리케이션은 비디오 스트림의 로컬 색상 관리를 지원하며, AJA 및 Blackmagic Design SDI 하드웨어를 통해 출력할 수 있습니다.

또한 Baselight 또는 Daylight 시스템의 원격 작업을 위해 NICE DCV와 통합될 수 있습니다.

구성 및 사용에 대한 자세한 내용은 Baselight 도움말 메뉴에 포함된 FilmLight REMOTE 사용자 가이드를 참조하십시오. (버그 61988)

### Image Viewer

*   The Image Viewer is a new view that mirrors the SDI output on a UI monitor. It supports interaction with operator overlays, allowing creation/editing of shapes, painting on the image etc. without the need to switch the cursor over to the SDI.

    The Image Viewer can be popped-up/floated from the "Views" menu. There is also a new "Image Viewer" workspace that's pre-configured with a docked Image Viewer. Ctrl+F8 can be used to toggle a full screen Image Viewer on the primary UI monitor (regardless of whether it's currently visible in the UI).

    While the Image Viewer is visible in the UI, the SDI output can be switched to "Clean Output" mode. When Clean Output mode is enabled, the SDI will always display an image rendered from the bottom of the stack, regardless of the render line position, bypass mode etc. Clean Output can be enabled/disabled from the "Display" menu. It can also be mapped to the Slate and Blackboard 2 via the "Toggle Clean Primary Output" action in Chalk.

    Image Viewer is not enabled by default. The Image Viewer is enabled in Display > Image Viewer in the Baselight Preference, please check the help text for further information. Bug 61988

### Image Viewer(이미지 뷰어)

Image Viewer는 UI 모니터에서 SDI 출력을 미러링하는 새로운 보기 기능입니다. 이 기능은 오퍼레이터 오버레이와의 상호작용을 지원하여, 커서를 SDI로 전환하지 않고도 도형 생성/편집, 이미지 페인팅 등을 할 수 있습니다.

Image Viewer는 “Views” 메뉴에서 팝업 또는 플로팅 형태로 사용할 수 있습니다. 또한, 도킹된 Image Viewer가 사전 구성된 “Image Viewer” 작업 공간이 새롭게 추가되었습니다. Ctrl+F8을 사용하여 기본 UI 모니터에서 전체 화면 Image Viewer를 토글할 수 있으며, 이는 UI에서 현재 보이지 않더라도 가능합니다.

\


Image Viewer가 UI에 표시되는 동안 SDI 출력은 “Clean Output” 모드로 전환할 수 있습니다. Clean Output 모드가 활성화되면, SDI는 항상 스택의 맨 아래에서 렌더링된 이미지를 표시하며, 렌더 라인 위치나 바이패스 모드 등에 관계없이 적용됩니다. Clean Output은 “Display” 메뉴에서 활성화/비활성화할 수 있으며, “Toggle Clean Primary Output” 작업을 통해 Slate 및 Blackboard 2에도 매핑할 수 있습니다.

\


Image Viewer는 기본적으로 활성화되어 있지 않으며, Baselight 환경설정의 Display > Image Viewer에서 활성화할 수 있습니다. 자세한 내용은 도움말 텍스트를 참조하십시오. (버그 61988)

### Workspace Switching/Cycling

*   The F8 key now toggles between the last 2 selected workspaces. Holding the "Win" key and pressing F8 cycles through the available workspaces (Win+Shift+F8 cycles through the wokspaces backwards).

    On the Slate and Blackboard 2, there is an equivalent custom button available from Chalk in the "Workspaces" button category: "Toggle/Cycle Workspaces". Once mapped, it will either toggle between the last 2 workspaces, or cycle through the available workspaces if the desk's "Windows" key is held down. Bug 61988

### 작업 공간 전환/순환

이제 F8 키를 사용하면 마지막으로 선택된 두 작업 공간 간에 전환할 수 있습니다. “Win” 키를 누른 상태에서 F8을 누르면 사용 가능한 작업 공간을 순환하며 전환할 수 있고, Win+Shift+F8을 사용하면 작업 공간을 역방향으로 순환합니다.

\


Slate 및 Blackboard 2에서는 “Workspaces” 버튼 카테고리의 Chalk에서 “Toggle/Cycle Workspaces”라는 맞춤 버튼을 사용할 수 있습니다. 이 버튼을 매핑하면 마지막 두 작업 공간 간에 전환하거나, 데스크의 “Windows” 키를 누르고 있으면 사용 가능한 작업 공간을 순환할 수 있습니다. (버그 61988)

### Timeline Improvements

*   Added the ability to merge tracks to the track panel's right-click menu. The available options are:

    * Merge In Track Above
    * Merge In Track Below
    * Merge In All Other Tracks.

    All these options obey grade locking - any merging will occur only up to and not including the first grade locked track. Bug 66357
* In Timeline Alignment view, added the "Create New Tracks" setting to give users the option of not creating new tracks when aligning the timeline, thus restoring the behaviour seen in previous versions of Baselight. Bug 67574
* In Timeline Alignment view, added option to "Remove Gaps in Stacks". When turned on, this option will remove all vertical gaps within a stack. It is especially useful when cleaning up a timeline after tracks have been merged. Bug 60211
* By default, the cursor is now centred in the Timeline View during playback, unless the playback range fits completely in the area between the scroll regions. Cursor centring can be disabled using the new "Centre cursor during playback" preference. In addition, the speed of the animation which centres the cursor when playback starts can be controlled with the "Centre cursor during playback animation length" preference. Bug 61283
* The "Horizontal jump scrolling" preference is now turned on by default, making Baselight's default scrolling behaviour more familiar to new users familiar with other systems. Bug 68651
* In Timeline Alignment View, changed "Derive Tracks" to "Derive Alignment" to prevent confusion now that Baselight uses the word "Track" in lots of other places in the UI. Bug 68626
* Added "Minimum Track Height" preference to allow the user to control how small the track name text and icons get when zoomed out vertically in the Timeline. The default setting allows the track text to reduce slightly in size when zooming out, but if this isn't desired, a value of 1.0 will ensure that track text and icons always stay the same size. Bug 67305
* In the track panel right-click menu, the "Move Track Up" and "Move Track Down" items now obey the "Allow Vertical Movement of Grade-Locked Strips" preference. Similarly the "Remove Track" and "Remove All Empty Tracks" options now obey the "Allow Removal of Grade-Locked Strips" preference. Bug 68703
* Improved the behaviour of binary strips used as part of a stack when edit locking is turned on. Now, a binary strip will be treated as a grade strip (and hence subject to grade locking rather than edit locking) if the timeline extent of its first input lies completely within the timeline extent of its second input. Bug 68396

### 타임라인 개선 사항

\


1\. 트랙 병합 기능 추가

트랙 패널의 오른쪽 클릭 메뉴에 트랙 병합 기능이 추가되었습니다. 사용할 수 있는 옵션은 다음과 같습니다:

• 위 트랙에 병합

• 아래 트랙에 병합

• 다른 모든 트랙에 병합

이러한 옵션은 그레이드 잠금을 준수하며, 병합은 첫 번째 그레이드 잠금 트랙까지(해당 트랙 제외) 발생합니다. (버그 66357)

2\. 타임라인 정렬 뷰에서 새로운 트랙 생성 옵션 추가

타임라인을 정렬할 때 새로운 트랙을 생성하지 않도록 선택할 수 있는 “새로운 트랙 생성” 설정이 추가되었습니다. 이를 통해 이전 Baselight 버전에서 보았던 동작을 복원할 수 있습니다. (버그 67574)

3\. 타임라인 정렬 뷰에서 스택 내 간격 제거 옵션 추가

“스택 내 간격 제거” 옵션이 추가되었습니다. 이 옵션을 켜면 스택 내의 모든 수직 간격이 제거됩니다. 특히 트랙을 병합한 후 타임라인을 정리할 때 유용합니다. (버그 60211)

4\. 기본적으로 재생 중에 타임라인 뷰에서 커서가 중앙에 위치

재생 범위가 스크롤 영역 사이의 영역에 완전히 맞지 않는 한, 기본적으로 재생 중에 타임라인 뷰에서 커서가 중앙에 위치하게 됩니다. 커서 중앙 맞추기를 비활성화하려면 새로운 “재생 중 커서 중앙 맞추기” 환경 설정을 사용할 수 있습니다. 또한, 재생이 시작될 때 커서를 중앙으로 맞추는 애니메이션의 속도는 “재생 중 커서 중앙 맞추기 애니메이션 길이” 환경 설정으로 제어할 수 있습니다. (버그 61283)

5\. “수평 점프 스크롤” 기본 활성화

“수평 점프 스크롤” 환경 설정이 기본적으로 켜져 있으며, 다른 시스템에 익숙한 신규 사용자들에게 Baselight의 기본 스크롤 동작이 더 친숙하게 느껴지도록 합니다. (버그 68651)

6\. 타임라인 정렬 뷰에서 “Derive Tracks”를 “Derive Alignment”로 변경

Baselight의 UI에서 “트랙”이라는 용어를 여러 곳에서 사용하게 되어 혼동을 방지하기 위해 “Derive Tracks”를 “Derive Alignment”로 변경했습니다. (버그 68626)

7\. “최소 트랙 높이” 환경 설정 추가

사용자가 타임라인에서 수직으로 축소할 때 트랙 이름 텍스트와 아이콘이 얼마나 작아질지를 제어할 수 있도록 “최소 트랙 높이” 환경 설정이 추가되었습니다. 기본 설정은 축소할 때 트랙 텍스트 크기가 약간 작아지도록 하지만, 원하지 않는 경우 값 1.0을 설정하면 트랙 텍스트와 아이콘이 항상 동일한 크기를 유지합니다. (버그 67305)

8\. 트랙 패널의 오른쪽 클릭 메뉴에서 트랙 이동 및 제거 기능 개선

“Move Track Up” 및 “Move Track Down” 항목이 이제 “Allow Vertical Movement of Grade-Locked Strips” 환경 설정을 준수합니다. 마찬가지로 “Remove Track” 및 “Remove All Empty Tracks” 옵션은 이제 “Allow Removal of Grade-Locked Strips” 환경 설정을 준수합니다. (버그 68703)

9\. 스택의 일부로 사용되는 바이너리 스트립의 동작 개선

편집 잠금이 켜져 있을 때 스택의 일부로 사용되는 바이너리 스트립의 동작이 개선되었습니다. 이제, 바이너리 스트립의 첫 번째 입력의 타임라인 범위가 두 번째 입력의 타임라인 범위 내에 완전히 포함되는 경우, 바이너리 스트립이 그레이드 스트립으로 처리되어 그레이드 잠금의 영향을 받습니다. (버그 68396)

### Editing Improvements

* Added new "Trim to Cursor" button to the Timeline Bar. When clicked with edit points visible, an edit is performed to align the edit point (start edit point if multiple edit points are visible) with the current cursor position without needing to drag use multiple keystrokes. It's also available by pressing R when in Edit Mode. Bug 68705
* When locked into Move Shot, Slip or Slide edit modes, it's now possible to drag the start or end brackets in addition to the central drag handle to affect the edit. In addition, the central drag handles are now always drawn when locked into these modes, to make it clear what can be dragged. Bug 68711
* Added "Move Cursor During Edits" option to the Timeline Bar cog menu. It defaults to on (the behaviour in previous versions of Baselight 6.0), meaning the cursor is moved to align with the edit point in the Ripple/Roll/Move Start/Move End edit modes. When turned off this no longer occurs, matching the editing behaviour of Baselight versions prior to 6.0. Bug 68592
* Added "Update Edit Points on Cursor Movement" option to the Timeline Bar cog menu. It defaults to on (the behaviour in previous versions of Baselight 6.0), meaning that locked edit points are updated to lie on the new shot when the cursor is moved. When turned off this no longer occurs, matching the editing behaviour of Baselight versions prior to 6.0. Bug 68713
*   Changed Timeline behaviour in the following ways when there are locked edit points based on an explicit (yellow) strip selection:

    * The edit points are now _never_ updated on cursor movement in this situation.
    * The current parameter strip is now _never_ updated in this situation, so that one now never gets a parameter strip lying outside the range of the edit point brackets.

    These two changes mean that the user can now safely move the cursor to lie outside the edit point range without needing to worry about the editing or selection state being unexpectedly changed. This makes Baselight 6.0 behave more like previous versions of Baselight whose editing was based on explicit selections. Bug 68712
* The "Handle Protection" and "Use Display View To Show Edit Multi-View While Editing" edit-mode menu items are now persisted between restarts of Baselight, as is the state of the snap button. Bug 68593

### 편집 개선 사항

\


1\. “Trim to Cursor” 버튼 추가

타임라인 바에 새로운 “Trim to Cursor” 버튼이 추가되었습니다. 이 버튼을 클릭하면 편집 포인트가 현재 커서 위치에 맞춰집니다(여러 편집 포인트가 보이는 경우 시작 편집 포인트와 일치). 이제 여러 번의 키스트로크 없이 편집이 가능합니다. 이 기능은 편집 모드에서 R 키를 눌러서도 사용할 수 있습니다. (버그 68705)

2\. Move Shot, Slip, Slide 편집 모드에서의 개선

Move Shot, Slip, Slide 편집 모드로 잠겨 있을 때 중앙 드래그 핸들 외에도 시작 또는 종료 브래킷을 드래그하여 편집을 조정할 수 있게 되었습니다. 또한, 이러한 모드로 잠겨 있을 때 중앙 드래그 핸들이 항상 표시되며, 드래그할 수 있는 위치를 명확하게 보여줍니다. (버그 68711)

3\. “Move Cursor During Edits” 옵션 추가

타임라인 바의 톱니바퀴 메뉴에 “Move Cursor During Edits” 옵션이 추가되었습니다. 기본적으로 켜져 있으며(Baselight 6.0 이전 버전의 동작), Ripple/Roll/Move Start/Move End 편집 모드에서 커서가 편집 포인트와 일치하도록 이동됩니다. 이 옵션을 끄면 커서가 이동하지 않으며, 이는 Baselight 6.0 이전 버전의 편집 동작과 일치합니다. (버그 68592)

4\. “Update Edit Points on Cursor Movement” 옵션 추가

타임라인 바의 톱니바퀴 메뉴에 “Update Edit Points on Cursor Movement” 옵션이 추가되었습니다. 기본적으로 켜져 있으며(Baselight 6.0 이전 버전의 동작), 커서를 이동하면 잠긴 편집 포인트가 새 샷에 맞춰 업데이트됩니다. 이 옵션을 끄면 더 이상 업데이트되지 않으며, Baselight 6.0 이전 버전의 편집 동작과 일치합니다. (버그 68713)

5\. 타임라인 동작 변경 사항

명시적(노란색) 스트립 선택에 기반한 잠긴 편집 포인트가 있을 때 타임라인 동작이 다음과 같이 변경되었습니다:

• 이 상황에서는 커서 이동 시 편집 포인트가 더 이상 업데이트되지 않습니다.

• 이 상황에서는 현재 파라미터 스트립이 더 이상 업데이트되지 않으므로, 이제 편집 포인트 브래킷 범위 외부에 파라미터 스트립이 위치하는 일이 발생하지 않습니다.

### Conform

* Baselight now handles image sequences and still images when conforming from FCP 7 XMLs generated by Adobe Premiere. Bug 12898
*   DaVinci Resolve expresses image sequences using a Resolve-specific syntax in the `<pathurl>` element of FCP 7 XMLs. E.g:

    ```
    <pathurl>file://localhost/some_dir/seq.[1234-2345].png</pathurl>
    ```

    Baselight now properly handles this syntax. Bug 68803

Conform (컨펌)

이제 Baselight는 Adobe Premiere에서 생성된 FCP 7 XML 파일을 통해 이미지 시퀀스와 정지 이미지를 정상적으로 처리할 수 있습니다. (버그 12898)

DaVinci Resolve의 FCP 7 XML 파일의 요소에서 Resolve 전용 구문을 사용한 이미지 시퀀스. 예를 들어:

```
<pathurl>file://localhost/some_dir/seq.[1234-2345].png</pathurl>
```

이제 Baselight에서 이 구문을 올바르게 처리할 수 있습니다. (버그 68803)

### Academy Metadata Files

* Added support for Academy Metadata Files (AMFs). AMFs are XML files which are capable of representing the precise setup of an ACES pipeline, including specifying Input Device Transforms (IDTS), Color Decision List (CDL) grades, Look Management Transforms (LMTs), Reference Rendering Transforms (RRTs) and Output Device Transforms (ODTs). Bug 31389
* AMFs can be inserted via FLUX Manage simply by double clicking the file. This will cause the Insert AMF Grade dialog, containing the following settings:
  * **CLF Directory**: Additional directory in which to look for CLF LUT files referenced by the AMF, in addition to the directory containing the AMF, which is always searched.
  * **CCC Directory**: Additional directory in which to look for CCC files containing CDL grades referenced by the AMF, in addition to the directory containing the AMF, which is always searched.
  * **Obey Applied**: Whether or not to obey the "applied" attribute associated with each transform - if "Yes" and "applied" is "true" in the AMF, then an equivalent transform will _not_ be applied in the Baselight stack generated from the AMF, because it is assumed that the input already has the transform baked in. ([https://docs.acescentral.com/guides/amf/#the-applied-attribute](https://docs.acescentral.com/guides/amf/#the-applied-attribute))
  * **Mark Working Location with Category**: The optional `<aces:workingLocation>` tag in AMFs specifies where additional look transforms should be placed if the AMF is modified. This setting allows the working location to be marked in the Baselight stack generated from the AMF using a category. Any existing strips in the stack will be placed at the working location. If not specified, the working location will be assumed to be directly after the input transform.
  * **Starting CDL Layer Number**: Settings which specify the desired layer number, strip colour and category for any CDL Grade strips inserted. (**Note**: specifying a layer number does **not** change the ordering of operators generated from the AMF.)
  * **Starting CLF Layer Number**: Settings which specify the desired layer number, strip colour and category for any LUT strips inserted to apply CLF LMTs.
  * **Starting Gamut Compress Layer Number**:Settings which specify the desired layer number, strip colour and category for any Compress Gamut strips inserted.
  * **Apply**: Allows the user to narrow down precisely what transforms in the AMF should be applied to the Baselight stack:
    * **Input Transform**: If set, will either specify the Input Colour Space of the Sequence operator _or_ insert a LUT operator if the input transform was specified with a CLF. **Note**: The input colour space will _not_ be set if the Sequence operator is in `Automatic` mode.
    * **CDL Look Transforms**: If set, CDL Grade operators will be inserted.
    * **CLF Look Transforms**: If set, LUT operators referencing CLF files will be inserted.
    * **CDL Working Space**: If set, then the CDL working space will be used to set the working space of the scene.
    * **Output Transform ODT**: If set, the cursor's Viewing Colour Space will be set.
    * **Output Transform RRT**: If set, the scene's Display Rendering Transform will be set.
* `AMF_NAME` and `AMF_UUID` columns have been added to Shots View. These columns are used to match against specific AMFs. They are also populated when conforming:
  * ALE files ([https://docs.acescentral.com/guides/amf/#avid-log-exchange-ale-support](https://docs.acescentral.com/guides/amf/#avid-log-exchange-ale-support))
  * CMX3600 files ([https://docs.acescentral.com/guides/amf/#edit-decision-list-edl-support](https://docs.acescentral.com/guides/amf/#edit-decision-list-edl-support))
* AMFs can also be inserted via Multi-Paste using the new "Academy Metadata File (AMF)" source option. When turned on, the following settings appear or are relevant:
  * **AMF Directory**: Directory in which to search for AMFs.
  * **Mark Working Location with Category**: See above.
  * **LUT Directory**: Equivalent to `CLF Directory` above.
  * **Match By**: The new `AMF_NAME` and `AMF_UUID` matching options can be used to match these columns against the metadata in AMFs.
* AMFs can also be exported from Baselight using the new "Export AMFs" option in the Shots View. This export dialog contains the following options:
  * **Description**: String describing the contents of the AMF.
  * **Author Name**: String containing the name of the AMF author.
  * **Author Email**: String containing the email address of the AMF author.
  * **Generate Clip ID**: Whether or not to generate `<aces:clipid>` metadata in the AMF. This metadata is used when one wishes to associate an AMF with a specific media file.
  * **Clip Filename**: If clip id metadata is being generated, specifies whether the full path should be written to the AMF or just the filename.
  * **Set Applied**: Whether the `applied` flag should be set to `true` in all transforms in the AMF.
  * **Working Location Categories**: Specifies the category which defines the working location in the stack, and thus where the `<aces:workingLocation>` tag will lie in the AMF.
  * **Input Space with no ACES Equivalent**: Specifies the behaviour when a shot's Input Colour Space doesn't have a equivalent ACES transform. If "Use a Fallback ACES Transform Where Possible" is set, then, where possible, a fallback transform will be substituted. A fallback transform will typically have the same colour primaries as the Baselight space, but a different, more popular tone curve, thus conveying the make of the camera which generated the input media. If there is no fallback available or if "Always generate a CLF Transform" is specified, then a CLF LUT representing the conversion from the input space to ACES AP0 linear will be generated instead.
  * **Generate Output Transform**: The `<aces:outputTransform>` tag is optional, so this setting specifies whether it is to be included. If `Yes`, then a display-referred colour space can be selected.
  * **CLF File Handling**: If the Baselight stack references a CLF file, specifies whether the AMF file should refer to the CLF in its existing location or if it should be copied into the AMF output directory and be referred to only by filename.
  * **Update Source Metadata**: Whether or not to write the `AMF_NAME` and `AMF_UUID` columns in the scene metadata. Writing the metadata is useful if one wishes to later export an ALE or CMX3600 EDL referring to the generated AMFs.

### Academy Metadata Files (AMFs) 지원 추가

\


1\. AMF 지원 개요

Baselight는 이제 Academy Metadata Files (AMFs)를 지원합니다. AMFs는 ACES 파이프라인의 설정을 정확하게 표현할 수 있는 XML 파일로, Input Device Transforms (IDTs), Color Decision List (CDL) 그레이드, Look Management Transforms (LMTs), Reference Rendering Transforms (RRTs), Output Device Transforms (ODTs) 등을 지정할 수 있습니다. (버그 31389)

2\. AMF 삽입

AMFs는 FLUX Manage에서 파일을 더블 클릭하여 삽입할 수 있습니다. 삽입 시 “Insert AMF Grade” 대화상자가 나타나며, 다음과 같은 설정을 포함합니다:

• CLF Directory: AMF에 참조된 CLF LUT 파일을 검색할 추가 디렉토리입니다. AMF가 포함된 디렉토리는 항상 검색됩니다.

• CCC Directory: AMF에 참조된 CDL 그레이드가 포함된 CCC 파일을 검색할 추가 디렉토리입니다.

• Obey Applied: 각 변환에 연관된 “applied” 속성을 준수할지 여부를 설정합니다. 만약 “Yes”로 설정되어 있고, AMF에서 “applied”가 “true”로 지정된 경우, 동일한 변환은 Baselight 스택에 적용되지 않습니다. 이는 입력에 해당 변환이 이미 적용되어 있다고 가정하기 때문입니다. 자세한 내용은 [AMF 문서의 “applied” 속성 섹션](https://docs.acescentral.com/guides/amf/#the-applied-attribute)을 참조하십시오.

• Mark Working Location with Category: AMF가 수정될 경우 추가적인 룩 변환이 배치될 위치를 지정하는 [aces:workingLocation](aces:workingLocation) 태그를 Baselight 스택에 카테고리로 표시합니다.

• Starting CDL Layer Number: 삽입된 CDL Grade 스트립에 대해 원하는 레이어 번호, 스트립 색상, 카테고리를 지정합니다.

• Starting CLF Layer Number: 삽입된 LUT 스트립에 대해 원하는 레이어 번호, 스트립 색상, 카테고리를 지정합니다.

• Starting Gamut Compress Layer Number: 삽입된 Compress Gamut 스트립에 대해 원하는 레이어 번호, 스트립 색상, 카테고리를 지정합니다.

• Apply: AMF에서 Baselight 스택에 적용할 변환을 정확하게 지정할 수 있습니다.

3\. Shots View 업데이트

Shots View에 AMF\_NAME 및 AMF\_UUID 열이 추가되었습니다. 이 열들은 특정 AMFs와 일치하도록 사용되며, ALE 파일 또는 CMX3600 파일을 사용할 때도 채워집니다.

4\. Multi-Paste를 통한 AMF 삽입

Multi-Paste에서 새로운 “Academy Metadata File (AMF)” 소스 옵션을 사용하여 AMFs를 삽입할 수 있습니다. 이 옵션을 활성화하면 다음 설정이 나타나거나 관련됩니다:

• AMF Directory: AMFs를 검색할 디렉토리입니다.

• Mark Working Location with Category: 위에서 설명한 대로 설정됩니다.

• LUT Directory: 위의 CLF Directory와 동일한 역할을 합니다.

• Match By: AMF\_NAME 및 AMF\_UUID 일치 옵션을 사용하여 AMFs의 메타데이터와 일치시킬 수 있습니다.

5\. AMF 내보내기

Shots View에서 새로운 “Export AMFs” 옵션을 사용하여 AMFs를 내보낼 수 있습니다. 이 내보내기 대화상자에는 다음과 같은 옵션이 포함됩니다:

• Description: AMF의 내용을 설명하는 문자열입니다.

• Author Name: AMF 작성자의 이름을 포함하는 문자열입니다.

• Author Email: AMF 작성자의 이메일 주소를 포함하는 문자열입니다.

• Generate Clip ID: AMF에 [aces:clipid](aces:clipid) 메타데이터를 생성할지 여부를 설정합니다.

• Clip Filename: 클립 ID 메타데이터를 생성할 경우, 전체 경로 또는 파일 이름만 AMF에 기록할지 지정합니다.

• Set Applied: AMF의 모든 변환에 대해 applied 플래그를 true로 설정할지 여부를 결정합니다.

• Working Location Categories: 스택에서 작업 위치를 정의하는 카테고리를 지정합니다.

• Input Space with no ACES Equivalent: 샷의 Input Colour Space에 해당하는 ACES 변환이 없을 때의 동작을 지정합니다.

• Generate Output Transform: [aces:outputTransform](aces:outputTransform) 태그를 포함할지 여부를 지정합니다.

• CLF File Handling: Baselight 스택이 CLF 파일을 참조하는 경우, CLF 파일을 기존 위치에서 참조할지 또는 AMF 출력 디렉토리로 복사할지 지정합니다.

• Update Source Metadata: 장면 메타데이터에 AMF\_NAME 및 AMF\_UUID 열을 기록할지 여부를 설정합니다. 이는 나중에 생성된 AMFs를 참조하는 ALE 또는 CMX3600 EDL을 내보낼 때 유용합니다.

### Miscellaneous

* The libraw library, used to decode camera RAW files, has been updated to version 0.21.2. This adds support for additional cameras and formats, notably Canon EOS R8. Bug 67237
* Updated Photon to version 4.9.5. This can detect additional issues in rendered IMF packages. Bug 67366
* Updated to Blackmagic RAW SDK 4.0. This adds support for media from:
  * Panasonic Lumix G9II, GH5S and BGH1
  * Blackmagic URSA Cine 12K LF. Bug 68404
* Updated to Canon RAW SDK 2.9R5. This adds support for new and upcoming cameras, including the EOS C400. Bug 67857
* Added ability to add/create Reference and Shape inputs directly from the Matte Merge operator interface. Bug 50427
* Updated to ARRI Image SDK 8.1.0. This improves behaviour with B+W media. Bug 63602
* Updated to Codex HDE SDK 5.2.0. This significantly improves decoding speed. Bug 65128
* Added the ability to view and edit the Sequence operator's Offset parameter as source timecode in addition to the existing frames and seconds options. Bug 59317
* Enabled .cdl file export in the CDL Export dialog. Bug 59491
*   Added support for sshfs volumes to use a custom remote user. An sshfs volume by default connects as the `filmlight` user. Adding a `limit sshuser` line to `volume.cfg` allows this to be changed:

    ```
    zone mybaselight
    share testvol @servername.domain /path
    limit testvol sshuser=example
    ```

    Specifying `sshuser=$USER` will cause the ssh connection to be made as the user who is causing the volume to be mounted. This can be useful when working with Avid NEXIS for example. Please note that this mechanism only uses the user at the time the volume is mounted. If it remains mounted when another user accesses the volume, the remote access will continue to use the first user's identity.

    The diagnostic test for sshfs volumes has been extended to verify that all defined volumes can be accessed as the appropriate user.

    `fl-setupssh` has been extended with a `-U` option to specify the remote username. Bug 67579
* In Update AAF and Modify AAF workflows the output AAF filename is now used to set the name of the sequence in the AAF. Bug 67920
* Added "Slate Button Reference" documentation to the Help menu when a Slate is connected. Bug 67952
* Keep the Scope Overlays submenu in X Grade open to allow multiple items to be changed. Bug 67934
* Additional metadata is now read from ICC profiles embedded in JPEG, TIFF and PNG files. Bug 68254
* The ability to render Pixspan compressed files with an additional licence has been removed. Bug 67611
* The Edge Crop operator now shows the coordinates of the last visible image pixel/row, and also the cropped image width and height. Bug 68195
* Crash reports are now only sent by https. The older http and email options are no longer supported. See the `fl-report` tool for configuration information. Bug 68078
* Improved the appearance of media source directory path text in the Conform View for very long paths. Bug 64681
* Improved behaviour when restarting Baselight immediately after a previous run has terminated. Bug 68379
* Updated the Comprimato SDK used for GPU JPEG 2000 acceleration to version 2.8.4. This adds minor performance improvements and fixes an issue with TODO comments written to the console. Bug 68421
* On systems using FilmLightOS, the sytemd packages are updated to fix an issue that would sometimes stop the image RAID from mounting at boot time. Bug 67092
* On systems using FilmLightOS, the flos-tools, fl-network and fl-database RPM packages are updated to the most current versions (8.4.19833, 8.4-20638 and 8.2.19409). On systems not using FilmLightOS, the fl-config-master, fl-host and fl-verify-network commands have been added to the application utilities. These updates provide various fixes and new features. Release notes for these packages can be found in the documentation directory. Bug 65701
* When importing scenes in Job Manager, the name of the imported scene is now shown, the scene is now selected, and it can easily be opened. Bug 68532
* Changed default Colour Space in Stills Export to be "sRGB Display: 2.2 Gamma / Rec.709". Bug 68521
* Added OCIO config for Truelight Colour Spaces and TruelightCAM v3. The config is available as download [here](https://www.filmlight.ltd.uk/support/customer-login/colourspaces/colourspaces.php). Bug 60556
* RGBA OpenEXR deliverables can now be rendered with straight (unpremultiplied) RGB. This is contrary to the OpenEXR specification, but matches the behaviour offered by other applications. Straight RGB deliverables are written with the metadata attribute "unassociatedAlpha=1" to allow them to be identified. Bug 68347

### 기타 업데이트 사항

\


1\. libraw 라이브러리 업데이트

카메라 RAW 파일을 디코딩하는 데 사용되는 libraw 라이브러리가 0.21.2 버전으로 업데이트되었습니다. 이로 인해 Canon EOS R8을 포함한 추가 카메라 및 포맷 지원이 추가되었습니다. (버그 67237)

2\. Photon 업데이트

Photon이 4.9.5 버전으로 업데이트되었습니다. 이로 인해 렌더링된 IMF 패키지에서 추가적인 문제를 감지할 수 있습니다. (버그 67366)

3\. Blackmagic RAW SDK 업데이트

Blackmagic RAW SDK가 4.0 버전으로 업데이트되었습니다. 이로 인해 다음 미디어의 지원이 추가되었습니다:

• Panasonic Lumix G9II, GH5S 및 BGH1

• Blackmagic URSA Cine 12K LF (버그 68404)

4\. Canon RAW SDK 업데이트

Canon RAW SDK가 2.9R5 버전으로 업데이트되어, EOS C400을 포함한 새로운 카메라 및 곧 출시될 카메라를 지원합니다. (버그 67857)

5\. Matte Merge 오퍼레이터 인터페이스 개선

이제 Matte Merge 오퍼레이터 인터페이스에서 참조 및 모양 입력을 직접 추가/생성할 수 있습니다. (버그 50427)

6\. ARRI Image SDK 업데이트

ARRI Image SDK가 8.1.0 버전으로 업데이트되어 흑백 미디어의 동작이 개선되었습니다. (버그 63602)

7\. Codex HDE SDK 업데이트

Codex HDE SDK가 5.2.0 버전으로 업데이트되어 디코딩 속도가 크게 개선되었습니다. (버그 65128)

8\. Sequence 오퍼레이터의 Offset 파라미터

Sequence 오퍼레이터의 Offset 파라미터를 기존의 프레임 및 초 단위 옵션 외에도 소스 타임코드로 표시하고 편집할 수 있는 기능이 추가되었습니다. (버그 59317)

9\. .cdl 파일 내보내기 기능 활성화

CDL 내보내기 대화상자에서 .cdl 파일 내보내기 기능이 활성화되었습니다. (버그 59491)

10\. sshfs 볼륨에 대한 사용자 정의 원격 사용자 지원

이제 sshfs 볼륨에서 사용자 정의 원격 사용자를 사용할 수 있습니다. 기본적으로 sshfs 볼륨은 filmlight 사용자로 연결됩니다. volume.cfg 파일에 limit sshuser 라인을 추가하여 이를 변경할 수 있습니다. (버그 67579)

11\. AAF 파일 작업 시 개선 사항

Update AAF 및 Modify AAF 워크플로우에서 출력 AAF 파일 이름이 AAF 내 시퀀스의 이름으로 설정되도록 개선되었습니다. (버그 67920)

12\. Slate 버튼 참조 문서 추가

Slate가 연결된 경우, 도움말 메뉴에 “Slate Button Reference” 문서가 추가되었습니다. (버그 67952)

13\. X Grade에서 Scope Overlays 서브메뉴 개선

Scope Overlays 서브메뉴가 열린 상태에서 여러 항목을 변경할 수 있도록 개선되었습니다. (버그 67934)

14\. JPEG, TIFF 및 PNG 파일에 포함된 ICC 프로필 메타데이터 추가 읽기

JPEG, TIFF 및 PNG 파일에 포함된 ICC 프로필에서 추가적인 메타데이터를 읽을 수 있게 되었습니다. (버그 68254)

15\. Pixspan 압축 파일 렌더링 기능 제거

추가 라이센스로 Pixspan 압축 파일을 렌더링하는 기능이 제거되었습니다. (버그 67611)

16\. Edge Crop 오퍼레이터 개선

Edge Crop 오퍼레이터가 마지막으로 보이는 이미지 픽셀/행의 좌표와 잘린 이미지의 너비와 높이를 표시하도록 개선되었습니다. (버그 68195)

17\. 충돌 보고서 전송 방식 개선

이제 충돌 보고서는 https를 통해서만 전송됩니다. 이전의 http 및 이메일 옵션은 더 이상 지원되지 않습니다. fl-report 도구에서 설정 정보를 참조하십시오. (버그 68078)

18\. 타임라인 보기에서 미디어 소스 디렉토리 경로 텍스트 개선

타임라인 보기에서 매우 긴 경로의 미디어 소스 디렉토리 경로 텍스트의 표시가 개선되었습니다. (버그 64681)

19\. Baselight 재시작 시 동작 개선

이전 실행이 종료된 직후 Baselight를 재시작할 때의 동작이 개선되었습니다. (버그 68379)

20\. Comprimato SDK 업데이트

GPU JPEG 2000 가속을 위한 Comprimato SDK가 2.8.4 버전으로 업데이트되었습니다. 이로 인해 성능이 약간 개선되고 콘솔에 작성된 TODO 주석과 관련된 문제가 수정되었습니다. (버그 68421)

21\. FilmLightOS 사용 시스템의 시스템 업데이트

FilmLightOS를 사용하는 시스템에서 systemd 패키지가 업데이트되어, 부팅 시 이미지 RAID가 마운트되지 않는 문제를 해결했습니다. (버그 67092)

또한 flos-tools, fl-network, fl-database RPM 패키지들이 최신 버전으로 업데이트되었으며, FilmLightOS를 사용하지 않는 시스템에서는 fl-config-master, fl-host, fl-verify-network 명령이 애플리케이션 유틸리티에 추가되었습니다. 이 업데이트들은 다양한 수정 및 새로운 기능을 제공합니다. 해당 패키지들의 릴리스 노트는 문서 디렉토리에서 확인할 수 있습니다. (버그 65701)

22\. Job Manager에서 장면 가져오기 시 개선 사항

Job Manager에서 장면을 가져올 때, 가져온 장면의 이름이 표시되며 장면이 선택되고 쉽게 열 수 있도록 개선되었습니다. (버그 68532)

23\. 스틸 내보내기 기본 색상 공간 변경

스틸 내보내기의 기본 색상 공간이 “sRGB Display: 2.2 Gamma / Rec.709”로 변경되었습니다. (버그 68521)

24\. Truelight 색상 공간 및 TruelightCAM v3용 OCIO 구성 추가

Truelight 색상 공간 및 TruelightCAM v3용 OCIO 구성이 추가되었습니다. 해당 구성은 여기에서 다운로드할 수 있습니다. (버그 60556)

25\. RGBA OpenEXR 렌더링 기능 개선

이제 RGBA OpenEXR 납품물이 직선(비프리멀티플라이) RGB로 렌더링될 수 있습니다. 이는 OpenEXR 사양과는 다르지만, 다른 애플리케이션에서 제공되는 동작과 일치합니다. 직선 RGB 납품물은 메타데이터 속성 “unassociatedAlpha=1”로 작성되어 이를 식별할 수 있습니다. (버그 68347)

### FLAPI

* Added new `insert_amf_stack` method to the `Shot` interface, allowing an AMF file to be applied to a shot.
* Added new `input_colour_space_derived_from_media` method to the `Shot` interface, allowing the caller to determine if Baselight was able to automatically determine the shot's input colour space from the metadata in the media file.
* Added new `aces_idt_for_input_colour_space` method to the `Shot` interface. This method returns an ACES transform URN equivalent to the shot's Sequence operator's input colour space.
* The `Export` interface now supports AMF export via the new `do_export_AMF` method.
* The `MultiPaste` interface now support AMF multi-paste.
*   In the `SceneSettings` interface converted the following attributes to use value types rather than strings:

    * `MasteringColourSpace`
    * `MasteringOperation`
    * `MasteringWhitePoint`
    * `StereoMode`
    * `TimelineCaching`
    * `HDRClipBehaviour`
    * `DolbyVisionMode`
    * `TemporalSamplingMode`

    This greatly improved documentation quality and assignment validation. Bug 68049
* Fixed `OpticalFlowQuality` and `OpticalFlowSmoothing` attributes of the `SceneSettings` interface to use the correct value type, meaning that they not longer cause internal errors on assignment. Bug 68049
* Fixed bug in `FLAPI JobManager get_scenes()` method where scene names containing a space would be returned incorrectly when inside a folder. Bug 68212

### **FLAPI 업데이트**

1. **AMF 스택 삽입 메서드 추가**\
   Shot 인터페이스에 새로운 `insert_amf_stack` 메서드가 추가되어, AMF 파일을 샷에 적용할 수 있습니다.
2. **입력 색상 공간 자동 감지 메서드 추가**\
   Shot 인터페이스에 새로운 `input_colour_space_derived_from_media` 메서드가 추가되어, Baselight가 미디어 파일의 메타데이터에서 샷의 입력 색상 공간을 자동으로 감지할 수 있는지 확인할 수 있습니다.
3. **ACES IDT 반환 메서드 추가**\
   Shot 인터페이스에 새로운 `aces_idt_for_input_colour_space` 메서드가 추가되었습니다. 이 메서드는 샷의 Sequence 오퍼레이터의 입력 색상 공간에 해당하는 ACES 변환 URN을 반환합니다.
4. **AMF 내보내기 지원**\
   Export 인터페이스에서 새로운 `do_export_AMF` 메서드를 통해 AMF 내보내기를 지원합니다.
5. **AMF 멀티 페이스트 지원**\
   MultiPaste 인터페이스에서 AMF 멀티 페이스트를 지원합니다.
6. **SceneSettings 인터페이스 속성 업데이트**\
   SceneSettings 인터페이스에서 다음 속성들이 문자열 대신 값 유형을 사용하도록 변경되었습니다:
   * MasteringColourSpace
   * MasteringOperation
   * MasteringWhitePoint
   * StereoMode
   * TimelineCaching
   * HDRClipBehaviour
   * DolbyVisionMode
   * TemporalSamplingMode\
     이를 통해 문서화 품질과 할당 검증이 크게 향상되었습니다. (버그 68049)
7. **OpticalFlow 속성 수정**\
   SceneSettings 인터페이스에서 `OpticalFlowQuality` 및 `OpticalFlowSmoothing` 속성이 올바른 값 유형을 사용하도록 수정되었습니다. 이로 인해 할당 시 내부 오류가 발생하지 않게 되었습니다. (버그 68049)
8. **JobManager에서 장면 이름 반환 버그 수정**\
   FLAPI의 JobManager에서 `get_scenes()` 메서드가 폴더 내에 있는 장면 이름에 공백이 포함된 경우 잘못 반환되는 문제를 수정했습니다. (버그 68212)

###

## Bug Fixes Since Baselight 6.0.20612

* Changed the name of 108 and 300 nits PQ colour spaces to group colour spaces with cinema intent (dark surround and 48 nits creative white) and to separate them from PQ spaces with home intent (dim surround and 100 nits creative white). Bug 67301
* Fixed potential crash on Scratchpad grab when using old 5.3 gallery scenes. Bug 67113
* Timecode ranges for audio media are no longer shown in FLUX Manage Metadata Pivot. Bug 67185
* GPU JPEG 2000 acceleration is now only shown as supported in the About dialog when its NVIDIA driver version requirements are met. Bug 67003
* Prevent crash when resetting Paint layers. Bug 67253
* Fixed issue with invalid timecode rate in supplemental IMF packages. Bug 67246
* Improved some behaviour with interlaced media, for example Shape animation. Bug 64527
* Removed the largely-obsolete "Switch configuration" and "Switch errors" diag test. Bug 67044
* Fixed issue with shots having the wrong number of audio channels after using Audio Sync with stems. Bug 67361
* Fixed issues with poor Canon RAW image quality on macOS. Bug 67240
* Fixed issue with "Composite Paint Strokes Separately" and Paint on the outside of an inside/outside. Bug 67471
* Fixed hang reading temporally compressed media. This particularly affected low resolution QuickTime files using H.264 compression. Bug 67469
* The ramsize diagnostic now correctly warns when a DIMM does not report a size, rather that crashing. Bug 67523
* Fixed crash using tracking after setting up IMF deliverables in Render View. Bug 67564
* Fixed timeline not updating correctly after changing "Source Alpha" option on an OFX operator. Bug 67636
* QuickTime metadata with reverse-DNS names, such as that in Apple ProRes RAW media, is now written to OpenEXR output files. Bug 67635
* Fixed slowdown when repeatedly switching to/from Flare or Chromogen on systems with Blackboard/Slate control surfaces. Bug 67595
* Fixed "Full Area" Mask or Guide Mask in a cursor being reset incorrectly, for example when another cursor's Viewing Format is changed. Bug 67657
* Fixed behaviour of Nikon RAW (NEV) files which have no colour temperature metadata. Bug 67669
* LUT export now correctly recognises several new operators that cannot be used for LUT generation, such as Bokeh. Bug 66995
* Fixed order of channels when rendering interleaved AAC encoded audio. Attempting to use more than six channels with this codec now gives an error message instead of producing an invalid file. Bug 57461
* Fixed possible crash reconforming updated scenes. Bug 67799
* Fixed incorrect chroma ordering when using HFR on certain SDI cards. Bug 67613
* Fixed issue with incorrect number of channels reading AAC encoded audio in QuickTime and MP4 files. Bug 67875
* Fixed issue with Mask being reset to "None" when setting the Master CPL for a Supplemental IMF deliverable in Render View. Bug 67891
* Still frames are now added as sequences lasting approximately one second, rather than always 24 frames. Bug 67874
* Improved behaviour of temporal OFX plugins which handle RoI/RoD negotiation, for example when used in a stack with an animated transform. Bug 67823
* Fixed scaling of Text when grabbed to gallery. Bug 63684
* Fixed incorrect handling of negative values in matte channels, in some stacks. Also fixed incorrect behaviour when referencing and transforming four or more matte channels from the same input sequence. Bug 62744
* Fixed rare crash when using Hue Angle with a Slate control surface. Bug 67960
* Fixed crash when an OFX plugin behaves incorrectly. Bug 67632
* Fixed crash which could occur if pressing "Mark In" whilst the numeric keypad navigation overlay was active. Bug 68038
* OpenEXR media containing 32-bit float channels is now read as 32-bit when the scene's Display setting is "32-bit Floating-Point RGB" or "32-bit Floating-Point RGBA". Bug 68171
* Fixed issues in some situations when a Reference operator set to "Ignore Colour Conversion" refers to an image in a cached strip. Bug 68171
* Fixed incorrect behaviour when dragging the current cursor lozenge and when clicking in the tray at the top of the timeline - when clicking near the edge of the lozenge or tray, it sometimes behaved as though the click had occurred outside. Bug 66759
* Fixed bug in strip bypass where any selected strip being locked would prevent unlocked strips from having their bypass state being modified. Bug 66982
* Files copied from macOS removable media mounted with 'ignore permissions' are now assumed to be owned by the user doing the copy, not the 'unknown' user, when the 'preserve permissions' copy option is enabled. Bug 68137
* Fixed incorrect behaviour when changing the colour space settings in a Bars operator. Bug 68282
* Fixed issue with fl-fsr stopping early if a file being relocated on disk has a length but occupies no disk blocks (is entirely sparse). Bug 68256
* Fixed FLUX Manage thumbnail failure for 10-bit 4:2:2 JPEG 2000 media. Bug 68330
* Fixed issue where the Edge Filter wouldn't match 5.3 renders and produce some artefacts. Bug 68339
* Fixed audio mark related crash on scene open. Bug 66091
* Fixed issue with invalid options causing render failures after changing the file type of Sequences deliverables in Render View. Bug 68276
* Fixed crash when using an operator which has overlay controls in a layer. Bug 67910
* Fixed issue where preset buttons might not reflect the current selection state. Bug 67911
* In the Conform View the media Filter and Reset buttons are kept disabled until a scene is opened. Bug 68386
* Fixed missing thumbnails in the Conform View Sequence Filter dialog. Bug 68442
* Improved information presented in error messages when OFX plugins are not correctly found, notably when rendering on a FLUX Store or Baselight RENDER system. Bug 68426
* Fixed issues with transforms and OFX operators, particularly flips and flops. Bug 68465
* Fixed failures when reading DNx media which has changing codec settings. Bug 68458
* Fixed issue causing occasional crash in X Grade when using a control surface. Bug 64758
* Fixed failure to load v5 gallery scenes containing shots grabbed from a scene configured with an external CMU. Bug 68484
* Camera metadata in ARRI ProRes MXF files is now read correctly and used to set the media orientation. Bug 68508
* Improved flit-daemon performance on Intel macOS systems. Bug 62048
* Fixed font size issue on Blackboard Classic in the Lens Correction operator. Bug 64105
* Improved responsiveness when scrubbing a timeline containing OFX plugins. Bug 58525
* Fixed occasional "Truelight: No CPU implementation" error messages when using Image Viewer or Client View. Bug 68558
* Fixed an error that occurs when using Multi-Paste with LUTs and a LUT directory that does not exist. Bug 68046
* 'Dual Output Layout' display mode is now available in non-stereo scenes. This mode is only visible only in 'Dual' output setups. Bug 64570
* Fixed clamping of HDR image values in a stack with a CPU OFX operator and a Transform. Bug 68554
* Fixed bug where toggling operator bypass in layers was possible via the keyboard even when grade or edit locked. Bug 68230
* Fixed bug which prevented Client View streaming from being disabled in "Network Stream" primary video output setups. Bug 68603
* Fixed cursor selection at the end of edits where folded shots/layers were force-unfolded, thus making subsequent edit drags made without changing the selection work as expected. Bug 68590
* A new Flexi package filmlight-flexi-effects installer is available in the support section of the FilmLight website. It fixes an issue in RIFE ML Retime's VRAM management, resulting in red errors in the console. Bug 68650
* Fixed issue reading trimmed HEVC encoded QuickTime files. Bug 68616
* Fixed incorrect VRAM warnings from some Flexi effects. Bug 67933
* Fixed unmodified/reset Transform operators in scenes with certain working formats incorrectly showing as modified after saving and reopening the scene. Bug 68516
* Fixed "Vertical Zoom to Fit Stacks" not dealing correctly with empty tracks at the top of the timeline. Bug 68669
* Fixed occasional crash in Timeline Alignment when deriving alignment "From Original Conform Tracks". Bug 68709
* Fixed issues with scopes or histograms in operator interfaces being affected by output clipping or Truelight options. Bug 68630
* Improved burnin performance. Bug 68499
* Fixed an issue with non-Latin subtitle text (specifically including Chinese, Japanese and Korean) failing to appear. Bug 68775
* DNxHR media with an alpha channel is now read correctly from QuickTime and MXF files. Note that some 3rd-party applications do not correctly write metadata indicating video/full range and/or premuliplication, so some media may be imported with these settings not matching the media. Bug 54108
* Fixed Shots View not updating correctly when swapping/moving a single shot into the bottom stack from above. Bug 68754
* Fixed crash using the Remove Strips of Category option when exporting an updated AAF. Bug 67039
* Changed default 'Low Rolloff' of 'Lows' preset in HueAngle from 0.0 to 0.1. Bug 67717
* Fixed issue where edge shapes would ignore the 'Paste Keyframes' option. Bug 68817
* Fixed an issue where grabbing from a scene with a different frame rate would show the wrong frame in the gallery. Bug 68553
* Fixed issue where docked scope views would initially be blank in some multi-screen configurations on macOS. Bug 64656
* Fixed incorrect rendering in some rare situations, for example a complex grade including a blurred shape being used as a grade matte above a Transform. Bug 68799
* Fixed keyer bugs that allowed them to be modified (via picking etc.) in read only scenes and locked strips/tracks. Bug 67186
* Improved performance when navigating the timeline with a large number of strips selected and not in edit mode. Bug 68873
* Fixed an issue where Chromogen rendered incorrectly on Intel Macs. Bug 68892
* Fixed LUT operators in imported BLGs, where the LUT file was originally stored in %C. Bug 63613
* Fixed straight/premultiplied RGBA options not being shown correctly for movie deliverables. Bug 68917
* Fixed occasional crash in BLG Export. Bug 67691
* Ensure the index service does not start until after remote filesystems are mounted. Bug 68919
* Fixed rare crash when using X Grade. Bug 69033





**Baselight 6.0.20612 이후 버그 수정 사항**

1. **PQ 색상 공간 이름 변경**\
   108 및 300 nits PQ 색상 공간의 이름을 변경하여 시네마 의도를 가진 색상 공간(어두운 주변과 48 nits 창의적 화이트)과 가정용 의도를 가진 PQ 공간(어두운 주변과 100 nits 창의적 화이트)을 구분했습니다. (버그 67301)
2. **Scratchpad 관련 잠재적 충돌 수정**\
   이전 5.3 갤러리 장면을 사용할 때 Scratchpad를 캡처하는 동안 발생할 수 있는 충돌을 수정했습니다. (버그 67113)
3. **FLUX Manage에서 오디오 미디어의 타임코드 범위 제거**\
   오디오 미디어의 타임코드 범위가 이제 FLUX Manage Metadata Pivot에 표시되지 않도록 수정되었습니다. (버그 67185)
4. **GPU JPEG 2000 가속 지원**\
   NVIDIA 드라이버 버전 요구 사항이 충족될 때만 GPU JPEG 2000 가속이 지원된다고 About 대화상자에 표시되도록 수정되었습니다. (버그 67003)
5. **Paint 레이어 초기화 시 충돌 방지**\
   Paint 레이어를 초기화할 때 발생할 수 있는 충돌을 방지했습니다. (버그 67253)
6. **IMF 패키지의 잘못된 타임코드 속도 수정**\
   보충 IMF 패키지에서 잘못된 타임코드 속도와 관련된 문제를 수정했습니다. (버그 67246)
7. **인터레이스 미디어에서의 동작 개선**\
   인터레이스 미디어에서의 Shape 애니메이션과 같은 동작을 개선했습니다. (버그 64527)
8. **오래된 "Switch configuration" 및 "Switch errors" 진단 테스트 제거**\
   대부분 사용되지 않는 "Switch configuration" 및 "Switch errors" 진단 테스트를 제거했습니다. (버그 67044)
9. **오디오 채널 수 문제 수정**\
   오디오 싱크 작업 후 샷이 잘못된 오디오 채널 수를 가지는 문제를 수정했습니다. (버그 67361)
10. **macOS에서의 Canon RAW 이미지 품질 문제 수정**\
    macOS에서 Canon RAW 이미지 품질이 저하되는 문제를 수정했습니다. (버그 67240)
11. **Paint 관련 문제 수정**\
    "Composite Paint Strokes Separately" 옵션과 Inside/Outside 외부의 Paint 관련 문제를 수정했습니다. (버그 67471)
12. **시간 압축된 미디어 읽기 시 발생하는 문제 해결**\
    시간 압축된 미디어를 읽을 때 발생하는 문제가 해결되었습니다. 특히 H.264 압축을 사용하는 저해상도 QuickTime 파일에 영향을 미쳤습니다. (버그 67469)
13. **DIMM 메모리 진단 오류 수정**\
    ramsize 진단에서 DIMM이 크기를 보고하지 않을 때 경고가 발생하도록 수정했으며, 더 이상 충돌하지 않도록 했습니다. (버그 67523)
14. **IMF 납품 설정 후 추적 사용 시 충돌 문제 수정**\
    Render View에서 IMF 납품물을 설정한 후 추적을 사용할 때 발생하는 충돌 문제를 수정했습니다. (버그 67564)
15. **타임라인 업데이트 문제 해결**\
    OFX 오퍼레이터에서 "Source Alpha" 옵션을 변경한 후 타임라인이 올바르게 업데이트되지 않는 문제를 해결했습니다. (버그 67636)
16. **QuickTime 메타데이터 처리 개선**\
    Apple ProRes RAW 미디어와 같은 역방향 DNS 이름이 포함된 QuickTime 메타데이터가 이제 OpenEXR 출력 파일에 올바르게 기록됩니다. (버그 67635)
17. **Flare 및 Chromogen 전환 시 속도 저하 문제 수정**\
    Blackboard/Slate 제어 표면이 있는 시스템에서 Flare 또는 Chromogen으로 전환할 때 발생하는 속도 저하 문제를 수정했습니다. (버그 67595)
18. **마스크 및 가이드 마스크 문제 해결**\
    "Full Area" 마스크 또는 가이드 마스크가 다른 커서의 Viewing Format이 변경될 때 잘못 리셋되는 문제를 수정했습니다. (버그 67657)
19. **Nikon RAW 파일 처리 문제 수정**\
    색온도 메타데이터가 없는 Nikon RAW (NEV) 파일의 동작을 수정했습니다. (버그 67669)
20. **LUT 내보내기 문제 수정**\
    LUT 생성에 사용할 수 없는 여러 새로운 오퍼레이터(Bokeh 등)를 LUT 내보내기에서 올바르게 인식하도록 수정했습니다. (버그 66995)
21. **오디오 채널 순서 문제 수정**\
    AAC 인코딩 오디오를 렌더링할 때 채널 순서가 잘못된 문제를 수정했습니다. 이 코덱으로 6개 이상의 채널을 사용하려고 할 때 이제 오류 메시지가 나타나며 잘못된 파일이 생성되지 않습니다. (버그 57461)
22. **재컨포밍 시 충돌 문제 수정**\
    업데이트된 장면을 재컨포밍할 때 발생할 수 있는 충돌 문제를 수정했습니다. (버그 67799)
23. **SDI 카드에서 HFR 사용 시 색상 순서 문제 해결**\
    특정 SDI 카드에서 HFR을 사용할 때 발생하는 색상 순서 문제가 해결되었습니다. (버그 67613)
24. **AAC 인코딩 오디오 읽기 문제 해결**\
    QuickTime 및 MP4 파일에서 AAC 인코딩 오디오를 읽을 때 채널 수가 잘못되는 문제를 해결했습니다. (버그 67875)
25. **보충 IMF 납품물 설정 시 마스크 리셋 문제 수정**\
    Render View에서 보충 IMF 납품물의 Master CPL을 설정할 때 마스크가 "None"으로 리셋되는 문제를 수정했습니다. (버그 67891)
26. **스틸 프레임 시퀀스 문제 해결**\
    이제 스틸 프레임이 항상 24 프레임이 아닌 약 1초 동안 지속되는 시퀀스로 추가됩니다. (버그 67874)
27. **OFX 플러그인 성능 개선**\
    RoI/RoD 협상을 처리하는 OFX 플러그인의 동작이 개선되었습니다. 특히 애니메이션된 변환과 함께 스택에서 사용될 때 유용합니다. (버그 67823)
28. **갤러리에 텍스트 가져오기 문제 해결**\
    텍스트를 갤러리에 가져올 때 크기 조정 문제를 해결했습니다. (버그 63684)
29. **매트 채널의 음수 값 처리 문제 해결**\
    일부 스택에서 매트 채널의 음수 값을 잘못 처리하는 문제를 수정했습니다. 또한, 동일한 입력 시퀀스에서 4개 이상의 매트 채널을 참조하고 변환할 때 발생하는 잘못된 동작을 수정했습니다. (버그 62744)
30. **Slate 제어 표면에서 Hue Angle 사용 시 드문 충돌 문제 수정**\
    Slate 제어 표면에서 Hue Angle을 사용할 때 발생할 수 있는 드문 충돌 문제를 수정했습니다. (버그 67960)
31. **OFX 플러그인 동작 오류 수정**\
    OFX 플러그인이 잘못된 동작을 할 때 발생하는 충돌 문제를 수정했습니다. (버그 67632)
32. **숫자 키패드 네비게이션 오버레이 문제 수정**\
    숫자 키패드 네비게이션 오버레이가 활성화된 상태에서 "Mark In"을 누를 때 발생할 수 있는 충돌 문제를 수정했습니다. (버그 68038)
33. **OpenEXR 미디어의 32비트 처리 문제 해결**\
    32비트 부동 소수점 채널이 포함된 OpenEXR 미디어가 장면의 Display 설정이 "32-bit Floating-Point RGB" 또는 "32-bit Floating-Point RGBA"인 경우 32비트로 읽히도록 수정되었습니다. (버그 68171)
34. **참조 오퍼레이터 문제 해결**\
    캐시된 스트립의 이미지를 참조할 때 발생하는 잘못된 동작 문제를 수정했습니다. 특히 "Ignore Colour Conversion"으로 설정된 참조 오퍼레이터에서 문제가 발생했습니다. (버그 68171)
35. **타임라인 커서 문제 수정**\
    현재 커서 로젠지를 드래그하거나 타임라인 상단 트레이에서 클릭할 때 발생하는 문제를 수정했습니다. 로젠지나 트레이의 가장자리 근처에서 클릭할 때 클릭이 외부에서 발생한 것처럼 잘못 작동하는 경우가 있었습니다. (버그 66759)
36. **스트립 바이패스 문제 해결**\
    선택된 스트립이 잠겨 있는 경우, 잠금 해제된 스트립의 바이패스 상태가 수정되지 않는 문제를 해결했습니다. (버그 66982
37. **macOS에서 이동식 미디어 복사 시 파일 소유권 문제 해결**\
    'ignore permissions' 옵션으로 마운트된 macOS 이동식 미디어에서 파일을 복사할 때, 'preserve permissions' 옵션이 활성화된 경우 이제 파일 소유자가 'unknown'이 아닌 복사 작업을 수행하는 사용자로 간주됩니다. (버그 68137)
38. **Bars 오퍼레이터에서 색상 공간 설정 변경 시 발생하는 문제 수정**\
    Bars 오퍼레이터에서 색상 공간 설정을 변경할 때 발생하는 잘못된 동작을 수정했습니다. (버그 68282)
39. **디스크에서 파일 이동 중 중단되는 문제 수정**\
    디스크에서 파일을 이동하는 중 파일 크기는 있지만 디스크 블록을 차지하지 않는(전체가 희소) 파일이 있는 경우 fl-fsr이 중간에 중단되는 문제를 해결했습니다. (버그 68256)
40. **FLUX Manage에서 10비트 4:2:2 JPEG 2000 미디어의 썸네일 생성 실패 문제 해결**\
    FLUX Manage에서 10비트 4:2:2 JPEG 2000 미디어의 썸네일이 생성되지 않는 문제를 해결했습니다. (버그 68330)
41. **Edge Filter와 5.3 렌더 일치 문제 수정**\
    Edge Filter가 5.3 렌더와 일치하지 않으며 일부 아티팩트를 생성하는 문제를 수정했습니다. (버그 68339)
42. **장면 열기 시 오디오 마크와 관련된 충돌 문제 해결**\
    장면을 열 때 오디오 마크와 관련된 충돌 문제를 수정했습니다. (버그 66091)
43. **Render View에서 파일 형식 변경 시 렌더 실패 문제 해결**\
    Render View에서 시퀀스 납품물의 파일 형식을 변경한 후 발생하는 렌더 실패 문제를 해결했습니다. (버그 68276)
44. **레이어 내 오퍼레이터 사용 시 충돌 문제 수정**\
    레이어 내 오버레이 컨트롤이 있는 오퍼레이터를 사용할 때 발생하는 충돌 문제를 수정했습니다. (버그 67910)
45. **프리셋 버튼의 선택 상태 문제 수정**\
    프리셋 버튼이 현재 선택 상태를 반영하지 않는 문제를 해결했습니다. (버그 67911)
46. **Conform View의 미디어 필터 및 리셋 버튼 활성화 문제 수정**\
    Conform View에서 장면이 열릴 때까지 미디어 필터 및 리셋 버튼이 비활성화된 상태로 유지되도록 수정했습니다. (버그 68386)
47. **Conform View Sequence Filter 대화상자에서 썸네일 누락 문제 해결**\
    Conform View Sequence Filter 대화상자에서 썸네일이 누락되는 문제를 해결했습니다. (버그 68442)
48. **OFX 플러그인을 찾지 못할 때의 오류 메시지 개선**\
    FLUX Store 또는 Baselight RENDER 시스템에서 렌더링할 때 OFX 플러그인을 올바르게 찾지 못할 경우 표시되는 오류 메시지를 개선했습니다. (버그 68426)
49. **Transform 및 OFX 오퍼레이터 관련 문제 수정**\
    특히 플립 및 플롭과 관련된 Transform 및 OFX 오퍼레이터 문제를 해결했습니다. (버그 68465)
50. **변경된 코덱 설정을 가진 DNx 미디어 읽기 문제 해결**\
    코덱 설정이 변경된 DNx 미디어를 읽을 때 발생하는 실패 문제를 해결했습니다. (버그 68458)
51. **X Grade 사용 중 제어 표면에서 발생하는 충돌 문제 해결**\
    제어 표면을 사용할 때 발생하는 X Grade에서의 드문 충돌 문제를 해결했습니다. (버그 64758)
52. **외부 CMU가 설정된 장면에서 v5 갤러리 로드 문제 해결**\
    외부 CMU가 설정된 장면에서 캡처된 샷이 포함된 v5 갤러리 장면을 로드할 때 발생하는 문제를 해결했습니다. (버그 68484)
53. **ARRI ProRes MXF 파일의 카메라 메타데이터 처리 문제 수정**\
    ARRI ProRes MXF 파일의 카메라 메타데이터가 올바르게 읽히고 미디어 방향 설정에 사용되도록 수정했습니다. (버그 68508)
54. **Intel macOS 시스템에서 flit-daemon 성능 개선**\
    Intel macOS 시스템에서 flit-daemon의 성능을 개선했습니다. (버그 62048)
55. **Blackboard Classic에서 Lens Correction 오퍼레이터의 글꼴 크기 문제 수정**\
    Blackboard Classic에서 Lens Correction 오퍼레이터의 글꼴 크기 문제를 해결했습니다. (버그 64105)
56. **OFX 플러그인이 포함된 타임라인 스크러빙 시 반응성 개선**\
    OFX 플러그인이 포함된 타임라인을 스크러빙할 때 반응성을 개선했습니다. (버그 58525)
57. **Image Viewer 또는 Client View 사용 시 발생하는 오류 메시지 수정**\
    Image Viewer 또는 Client View 사용 시 간헐적으로 발생하는 "Truelight: No CPU implementation" 오류 메시지를 수정했습니다. (버그 68558)
58. **존재하지 않는 LUT 디렉토리와 함께 Multi-Paste 사용 시 오류 수정**\
    존재하지 않는 LUT 디렉토리와 함께 Multi-Paste를 사용할 때 발생하는 오류를 수정했습니다. (버그 68046)
59. **비입체 장면에서 'Dual Output Layout' 표시 모드 사용 가능**\
    이제 비입체 장면에서도 'Dual Output Layout' 표시 모드를 사용할 수 있습니다. 이 모드는 'Dual' 출력 설정에서만 표시됩니다. (버그 64570)
60. **HDR 이미지 값의 클램핑 문제 수정**\
    CPU OFX 오퍼레이터와 Transform이 포함된 스택에서 HDR 이미지 값의 클램핑 문제를 해결했습니다. (버그 68554)
61. **레이어에서 오퍼레이터 바이패스 토글 문제 수정**\
    키보드를 통해 레이어에서 오퍼레이터 바이패스를 토글할 수 있었던 문제를 해결했습니다. 이 문제는 그레이드나 편집이 잠긴 경우에도 발생했습니다. (버그 68230)
62. **Client View 스트리밍 비활성화 문제 해결**\
    "Network Stream" 기본 비디오 출력 설정에서 Client View 스트리밍을 비활성화할 수 없었던 문제를 해결했습니다. (버그 68603)
63. **편집 끝에서의 커서 선택 문제 해결**\
    접힌 샷/레이어가 강제로 펼쳐지는 편집 끝에서의 커서 선택 문제를 해결했습니다. 이로 인해 선택을 변경하지 않고 수행된 후속 편집 드래그가 예상대로 작동하게 되었습니다. (버그 68590)
64. **새로운 Flexi 패키지 설치 프로그램 제공**\
    FilmLight 웹사이트의 지원 섹션에 새로운 Flexi 패키지 filmlight-flexi-effects 설치 프로그램이 제공됩니다. 이 설치 프로그램은 RIFE ML Retime의 VRAM 관리 문제를 해결하여 콘솔에 빨간색 오류가 발생하는 문제를 수정했습니다. (버그 68650)
65. **HEVC 인코딩 QuickTime 파일 읽기 문제 해결**\
    잘린 HEVC 인코딩 QuickTime 파일을 읽을 때 발생하는 문제를 해결했습니다. (버그 68616)
66. **일부 Flexi 효과에서 잘못된 VRAM 경고 문제 수정**\
    일부 Flexi 효과에서 잘못된 VRAM 경고가 표시되는 문제를 해결했습니다. (버그 67933)
67. **저장 후 장면을 다시 열 때 수정되지 않은 Transform 오퍼레이터 문제 해결**\
    특정 작업 형식이 있는 장면에서 수정되지 않은 Transform 오퍼레이터가 저장 후 장면을 다시 열 때 잘못 수정된 것으로 표시되는 문제를 해결했습니다. (버그 68516)
68. **"Vertical Zoom to Fit Stacks" 문제 해결**\
    타임라인 상단의 빈 트랙에서 "Vertical Zoom to Fit Stacks"가 올바르게 작동하지 않는 문제를 해결했습니다. (버그 68669)
69. **타임라인 정렬에서 드문 충돌 문제 수정**\
    "From Original Conform Tracks"에서 정렬을 파생할 때 타임라인 정렬에서 드문 충돌 문제가 해결되었습니다. (버그 68709)
70. **오퍼레이터 인터페이스에서 출력 클리핑 또는 Truelight 옵션의 영향을 받는 문제 수정**\
    오퍼레이터 인터페이스에서 스코프 또는 히스토그램이 출력 클리핑 또는 Truelight 옵션의 영향을 받는 문제를 해결했습니다. (버그 68630)
71. **Burnin 성능 개선**\
    Burnin 성능을 개선했습니다. (버그 68499)
72. **비라틴 자막 텍스트 문제 해결**\
    중국어, 일본어, 한국어를 포함한 비라틴 자막 텍스트가 나타나지 않는 문제를 해결했습니다. (버그 68775)
73. **DNxHR 미디어의 알파 채널 처리 문제 수정**\
    DNxHR 미디어의 알파 채널이 포함된 QuickTime 및 MXF 파일이 이제 올바르게 읽힙니다. 일부 서드파티 애플리케이션은 비디오/풀 레인지 및/또는 프리멀티플리케이션을 나타내는 메타데이터를 올바르게 기록하지 않으므로, 미디어가 이러한 설정과 일치하지 않을 수 있습니다. (버그 54108)
74. **Shots View 업데이트 문제 해결**\
    Shots View에서 단일 샷을 상단에서 하단 스택으로 이동할 때 올바르게 업데이트되지 않는 문제를 수정했습니다. (버그 68754)
75. **AAF 업데이트 내보내기 시 충돌 문제 수정**\
    AAF 업데이트 내보내기 시 "Remove Strips of Category" 옵션을 사용할 때 발생하는 충돌 문제를 해결했습니다. (버그 67039)
76. **HueAngle 프리셋 수정**\
    HueAngle의 'Lows' 프리셋에서 기본 'Low Rolloff' 값을 0.0에서 0.1로 변경했습니다. (버그 67717)
77. **Edge Shapes에서 'Paste Keyframes' 옵션 무시 문제 수정**\
    Edge Shapes가 'Paste Keyframes' 옵션을 무시하는 문제를 해결했습니다. (버그 68817)
78. **다른 프레임 속도의 장면에서 갤러리로 캡처 시 문제 해결**\
    다른 프레임 속도의 장면에서 갤러리로 캡처할 때 잘못된 프레임이 표시되는 문제를 수정했습니다. (버그 68553)
79. **macOS에서 도킹된 스코프 뷰 문제 해결**\
    일부 멀티스크린 구성에서 도킹된 스코프 뷰가 초기에는 빈 상태로 표시되는 문제를 해결했습니다. (버그 64656)
80. **복잡한 그레이드 및 변환 위의 블러 처리된 Shape 문제 해결**\
    예를 들어 블러 처리된 Shape를 그레이드 매트로 사용하는 경우와 같은 일부 드문 상황에서 잘못된 렌더링 문제가 수정되었습니다. (버그 68799)
81. **Keyer 관련 문제 해결**\
    읽기 전용 장면 및 잠긴 스트립/트랙에서 Keyer가 수정될 수 있는 문제(픽킹 등을 통해)를 해결했습니다. (버그 67186)
82. **타임라인 탐색 성능 개선**\
    선택된 스트립이 많고 편집 모드가 아닌 상태에서 타임라인을 탐색할 때의 성능을 개선했습니다. (버그 68873)
83. **Intel Mac에서 Chromogen 렌더링 문제 해결**\
    Intel Mac에서 Chromogen이 잘못 렌더링되는 문제를 수정했습니다. (버그 68892)
84. **LUT 오퍼레이터 문제 수정**\
    %C에 원래 저장된 LUT 파일이 있는 가져온 BLGs에서 LUT 오퍼레이터 문제를 해결했습니다. (버그 63613)
85. **무비 납품물의 RGBA 옵션 문제 수정**\
    무비 납품물의 직선/프리멀티플라이드 RGBA 옵션이 올바르게 표시되지 않는 문제를 해결했습니다. (버그 68917)
86. **BLG 내보내기 시 간헐적 충돌 문제 해결**\
    BLG 내보내기 시 발생하는 간헐적 충돌 문제를 해결했습니다. (버그 67691)
87. **인덱스 서비스 시작 문제 해결**\
    원격 파일 시스템이 마운트될 때까지 인덱스 서비스가 시작되지 않도록 수정했습니다. (버그 68919)
88. **X Grade 사용 시 드문 충돌 문제 수정**\
    X Grade 사용 시 발생하는 드문 충돌 문제를 해결했습니다. (버그 69033)



## Known Issues

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
* Using "Network Stream" as the Primary Video Output on Intel Mac Pro systems with AMD GPUs is currently unsupported. This will be addressed in a future release of Baselight 6.0. Bug 68727
* On Intel Mac systems with multiple GPUs, the MiDaS Flexi effect can sometimes produce a flickering matte when combined with some spatial operators. To work around this issue, enable the strip cache on the MiDaS strip. Bug 69040



## **알려진 문제 사항**

1. **macOS 13 Ventura에서 이미지 손상 문제**\
   Intel macOS 시스템에서 macOS 13 Ventura를 실행할 때, 특히 RED 및 ARRIRAW 미디어를 사용할 때 심각한 이미지 손상이 발생할 수 있습니다. 이 문제는 macOS 14 Sonoma에서 해결된 것으로 보입니다. (버그 62237)
2. **macOS 시스템에서 공유된 볼륨 접근 문제**\
   macOS의 버그로 인해 원격 시스템에서 macOS 시스템에서 공유된 볼륨에 접근할 때 실패할 수 있습니다. 이 문제를 해결하려면 다음 단계를 수행하십시오:
   * Dock 또는 Apple 메뉴에서 시스템 환경설정을 엽니다.
   * "보안 및 개인정보 보호"를 선택합니다.
   * 자물쇠 아이콘을 클릭하고 비밀번호 또는 Touch ID를 사용하여 변경을 허용합니다.
   * 왼쪽 목록에서 "전체 디스크 접근"을 선택합니다.
   * 오른쪽의 + 버튼을 클릭하여 파일 브라우저를 엽니다.
   * 키보드에서 / 키를 눌러 "폴더로 이동" 대화상자를 엽니다.
   * /sbin을 입력하고 이동을 클릭합니다.
   * nfsd라는 파일을 선택하고 열기를 클릭합니다.
   * Mac을 재시작하면 볼륨이 정상적으로 작동해야 합니다. (버그 62601)
3. **Photo RAW 파일의 색상 왜곡 문제**\
   Photo RAW Parameters 오퍼레이터에서 하이라이트를 블렌딩하면서 노출 슬라이더를 조정할 때, Photo RAW 파일의 포화된 영역이 색상 틴트를 얻을 수 있습니다. (버그 44769)
4. **Relight 오퍼레이터의 예기치 않은 동작**\
   Relight 오퍼레이터에서 글로벌 스케일을 설정하기 위해 드래그할 때 예기치 않은 동작이 발생할 수 있습니다. (버그 63798)
5. **Blackboard Classic 제어 표면 깜박임 문제**\
   오퍼레이터 간 전환 시 Blackboard Classic 제어 표면이 간헐적으로 깜박일 수 있습니다. 이 문제는 향후 베타 릴리스에서 수정될 예정입니다. (버그 62406)
6. **RIFE ML Retime 사용 시 품질 저하 문제**\
   RIFE ML Retime을 사용하는 샷(Sequence 또는 Retime 오퍼레이터에서)이 'Process in Working Format'이 선택된 것처럼 동작합니다. 이로 인해 렌더링 포맷이 작업 포맷보다 큰 경우 출력 품질이 저하될 수 있으며, 이 샷들은 또한 이미지를 작업 포맷으로 자릅니다. (버그 66016)
7. **Intel Mac Pro 시스템에서 네트워크 스트림 사용 불가**\
   AMD GPU가 장착된 Intel Mac Pro 시스템에서 'Network Stream'을 기본 비디오 출력으로 사용하는 것은 현재 지원되지 않습니다. 이 문제는 Baselight 6.0의 향후 릴리스에서 해결될 예정입니다. (버그 68727)
8. **MiDaS Flexi 효과의 깜박이는 매트 문제**\
   다중 GPU를 장착한 Intel Mac 시스템에서 MiDaS Flexi 효과가 일부 공간 오퍼레이터와 결합될 때 깜박이는 매트를 생성할 수 있습니다. 이 문제를 해결하려면 MiDaS 스트립에서 스트립 캐시를 활성화하십시오. (버그 69040)



