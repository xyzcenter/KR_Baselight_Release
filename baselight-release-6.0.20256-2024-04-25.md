# Baselight Release 6.0.20256 (2024-04-25)

##

### New Features Since Baselight 6.0.19915

#### Shape Control Point Transforms

*   It's now possible to transform (scale, rotate and translate) explicitly selected shape control points. To do this, first sweep select multiple (shape) control points. Holding down the `Win` modifier (or `Ctrl` on a Mac) will then popup a yellow transform box which can be used to transform those control points.

    Additionally, holding down `Ctrl` (`Cmd` on a Mac) and dragging the box centre can be used to adjust the centre of rotation/scale.

    On a Blackboard 1/Classic the `Ctrl Lock` key can be used to popup the yellow transform box. On any FilmLight desk, while the yellow transform box is visible/active the following trackball mappings apply:

    * Middle Trackball : Translate the selected control points.
    * Middle Trackball Ring : Rotate the selected control points.
    * Right Trackball : Translate the pivot/centre of rotation.
    * Right Trackball Ring : Scale the selected control points. Bug 67681

#### DRT Black Offset Compensation

*   Some DRTs map a negative linear light value to 0.0 in display-referred values. When a DRT defines this offset in its `BlackOffset` parameter, a new "Compensate For DRT Black Offset" control is shown below the DRT selection in Scene Settings View. When enabled, Baselight adds a compensatory flare before and after several modern grading operators. These operators are:

    * Base Grade (compensation was already present in Baselight 5)
    * Boost Detail
    * Boost Shadow
    * Chromogen
    * Colour Crosstalk in "Calculate In Linear" mode
    * Compress Gamut
    * Curve Grade
    * Hue Angle
    * Look (with looks using formulae or triangles)
    * X Grade

    This change should improve the colour grading behaviour of all of these operators when used in combination with such DRTs. Bug 67883

#### Miscellaneous

* Added support for the NVIDIA 550.76 driver. Bug 68044
* Added support for new FilmLight CONNECT traffic routing scheme. Bug 68056
* QuickTime metadata with reverse-DNS naming (e.g. `com.apple.quicktime.model`) is now copied from QuickTime source media to QuickTime rendered output media. Bug 68112



### Baselight 6.0.19915 이후 새로운 기능

**Shape Control Point Transforms**

• 이제 선택한 쉐이프 컨트롤 포인트를 변형(확대, 회전, 이동)할 수 있습니다. 먼저 여러 (쉐이프) 컨트롤 포인트를 선택한 후, Win 수정자(또는 Mac에서는 Ctrl)를 누르면 노란색 변형 상자가 나타나 이 상자를 사용해 컨트롤 포인트를 변형할 수 있습니다.

• 또한, Ctrl(Cmd on Mac)을 누른 상태에서 상자 중심을 드래그하면 회전/확대 중심을 조정할 수 있습니다.

• Blackboard 1/Classic에서는 Ctrl Lock 키를 사용해 노란색 변형 상자를 팝업할 수 있습니다. FilmLight 데스크에서는 노란색 변형 상자가 활성화된 동안 다음 트랙볼 매핑이 적용됩니다:

• 중간 트랙볼: 선택한 컨트롤 포인트를 이동.

• 중간 트랙볼 링: 선택한 컨트롤 포인트를 회전.

• 오른쪽 트랙볼: 회전 중심을 이동.

• 오른쪽 트랙볼 링: 선택한 컨트롤 포인트를 확대/축소. (버그 67681)

**DRT Black Offset Compensation**

• 일부 DRT는 음의 선형 광량 값을 디스플레이 참조 값에서 0.0으로 매핑합니다. DRT가 BlackOffset 매개변수에서 이 오프셋을 정의할 때, 씬 설정 보기의 DRT 선택 아래에 새로운 “DRT 블랙 오프셋 보상” 컨트롤이 표시됩니다. 이를 활성화하면 Baselight는 여러 최신 그레이딩 연산자 전에 보상 플레어를 추가합니다. 해당 연산자는 다음과 같습니다:

• Base Grade (보상은 이미 Baselight 5에 존재)

• Boost Detail

• Boost Shadow

• Chromogen

• “Calculate In Linear” 모드의 Colour Crosstalk

• Compress Gamut

• Curve Grade

• Hue Angle

• Look (공식 또는 삼각형을 사용하는 룩)

• X Grade

• 이 변경 사항은 이러한 DRT와 함께 사용할 때 모든 연산자의 색상 그레이딩 동작을 개선할 것입니다. (버그 67883)

**기타**

• NVIDIA 550.76 드라이버 지원이 추가되었습니다. (버그 68044)

• 새로운 FilmLight CONNECT 트래픽 라우팅 스킴 지원이 추가되었습니다. (버그 68056)

• 역-DNS 명명법(예: com.apple.quicktime.model)을 사용한 QuickTime 메타데이터가 QuickTime 소스 미디어에서 QuickTime 렌더링 출력 미디어로 복사됩니다. (버그 68112)

\


### Bug Fixes Since Baselight 6.0.19915

* Fixed rendering of web admin UI. Bug 67006
* The hotfix service no longer unmounts NFS volumes. Bug 66517
* Fixed issues on Intel macOS systems with empty or incorrect scopes, and related issues in Display View. Bug 65932
* Fixed error message when creating a new FilmLight CONNECT session via the Client Sessions view. Bug 66626

### Baselight 6.0.19915 이후 버그 수정 사항

• 웹 관리자 UI 렌더링 문제를 수정했습니다. (버그 67006)

• 핫픽스 서비스가 더 이상 NFS 볼륨을 언마운트하지 않습니다. (버그 66517)

• Intel macOS 시스템에서 빈 범위 또는 잘못된 범위 문제 및 디스플레이 보기의 관련 문제를 수정했습니다. (버그 65932)

• 클라이언트 세션 보기에서 새로운 FilmLight CONNECT 세션을 만들 때 발생하는 오류 메시지를 수정했습니다. (버그 66626)
