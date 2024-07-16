# Baselight 릴리스 6.0.19342 (2023-12-12)

### New Features Since Version 5

#### X Grade Operator

*   X Grade is a new primary colour grading tool which operates in floating-point linear light. As with all our newly developed tools, it is colour space aware and will convert from the stack colour space to its internal linear light colour space as well as processing the colour changes in a newly developed opponent colour space designed for natural colour grading.

    You can interact with X Grade using both the mouse and panels. The primary user interface is a scope-like canvas which shows the current image as a point cloud on the canvas, but it is also quick and easy to modify colours directly from the image display.

    The scope can be panned and zoomed just as with an image.

**버전 5 이후 새로운 기능**

**X Grade 연산자**

* X Grade는 부동 소수점 선형 광원에서 작동하는 새로운 기본 색상 그레이딩 도구입니다. 모든 새로 개발된 도구와 마찬가지로 색상 공간을 인식하며 스택 색상 공간에서 내부 선형 광원 색상 공간으로 변환하고, 자연스러운 색상 그레이딩을 위해 새로 개발된 상보 색상 공간에서 색상 변경을 처리합니다. \
  X Grade는 마우스와 패널을 모두 사용하여 상호작용할 수 있습니다. 주요 사용자 인터페이스는 현재 이미지를 캔버스에 포인트 클라우드로 표시하는 스코프와 같은 캔버스이며, 이미지 디스플레이에서 직접 색상을 빠르고 쉽게 수정할 수 있습니다.\
  스코프는 이미지와 마찬가지로 팬 및 줌할 수 있습니다.
*   **Strokes**

    Strokes are the fundamental element used to manipulate colours in X Grade. Creating them is very easy:

    * **On the Scope**: use the mouse to select a colour to adjust; click and drag in the direction that you want to push the chosen colour. This action will create a stroke - an arrow with a start and end point.

    The colour at the base of the stroke will be pulled in the direction of the arrow - the pull strength fades with distance from the array. The scope will show the boundaries of the change caused by the currently selected stroke.

    Multiple strokes can be created on the layer by clicking and dragging, or to edit an existing stroke, click on either the base or the head of the stroke's arrow. To delete an existing stroke, hold down `Shift` while clicking on it.\
    \
    **\* 스트로크**

    \


    스트로크는 X Grade에서 색상을 조정하는 데 사용되는 기본 요소입니다. 스트로크를 만드는 것은 매우 쉽습니다:



    • **스코프에서**: 마우스를 사용하여 조정할 색상을 선택한 다음, 선택한 색상을 밀고 싶은 방향으로 클릭하고 드래그합니다. 이 동작은 시작점과 끝점이 있는 화살표 형태의 스트로크를 만듭니다.

    스트로크의 시작점에 있는 색상은 화살표 방향으로 당겨지며, 당겨지는 강도는 화살표에서 멀어질수록 약해집니다. 스코프는 현재 선택된 스트로크로 인해 발생하는 변경의 경계를 보여줍니다.

    여러 스트로크를 레이어에 만들려면 클릭하고 드래그하거나, 기존 스트로크를 편집하려면 스트로크 화살표의 시작점이나 끝점을 클릭합니다. 기존 스트로크를 삭제하려면 Shift 키를 누른 상태에서 스트로크를 클릭합니다.\


    * **On the Image**: you can also create strokes directly from the image, and this is usually the most efficient way of working. When on the image, the scope will show a circular cursor representing the position corresponding to the colour under the mouse pointer. Clicking with the mouse acts as if you were clicking at the point shown by the circular cursor, and the subsequent drag will drag the colour as if you were dragging on the scope. In practical terms, you rarely need to look at the scope - just click on the colour you want to adjust, and drag the mouse until it's how you want it. Note: while working directly on the image, it's useful to know whether clicking will adjust an existing stroke or create a new one. The image cursor shows a small + in the top-right corner when clicking would create a new stroke. Note that to avoid creating a large number of strokes that would be hard to manage, the tool errs on the side of editing an existing stroke if there's one reasonably close-by, but you can force the creation of a new stroke with the `Alt` modifier (`Option` on Mac).
    * **이미지에서** : 이미지에서 직접 스트로크를 만들 수도 있으며, 이는 보통 가장 효율적인 작업 방법입니다. 이미지에서 작업할 때, 스코프는 마우스 포인터 아래의 색상에 해당하는 위치를 나타내는 원형 커서를 표시합니다. 마우스로 클릭하면 원형 커서가 표시된 지점을 클릭하는 것처럼 작동하며, 이후 드래그하면 스코프에서 드래그하는 것처럼 색상을 이동시킵니다. 실질적으로 스코프를 볼 필요는 거의 없으며, 조정하고 싶은 색상을 클릭하고 마우스를 원하는 대로 드래그하면 됩니다. 참고: 이미지를 직접 작업할 때 클릭이 기존 스트로크를 조정할지 새로운 스트로크를 만들지 여부를 아는 것이 유용합니다. 이미지를 클릭하면 새로운 스트로크를 만들 때 이미지 커서의 오른쪽 상단에 작은 + 기호가 표시됩니다. 관리하기 어려울 정도로 많은 스트로크를 만드는 것을 피하기 위해, 도구는 가까이에 기존 스트로크가 있을 경우 이를 편집하는 쪽으로 작동합니다. 그러나 Alt 키(맥에서는 Option 키)를 사용하면 새로운 스트로크를 강제로 생성할 수 있습니다.

    For fine tuning, as well as the start and end points, each stroke has two additional parameters you can adjust:

    * **Exposure**: this allows a stroke to modify brightness as well as hue and saturation. It is visualised as a contour plot around the stroke, similar to contour plots in topographical maps. As well as modifying the slider, it can be directly edited while dragging a colour by using the `Win` modifier (`Ctrl` on Mac).
    * **Width**: this extends the influence of the stroke. It can be directly edited with the mouse with the modifier `Alt+Win` (`Option+Ctrl` on Mac).

&#x20;       세부 조정, 시작점과 끝점 외에도, 각 스트로크에는 조정할 수 있는 두 가지 추가 매개변수가 있습니다:\
&#x20;       • **노출(Exposure)**: 이 매개변수는 스트로크가 밝기뿐만 아니라 색조와 채도를 수정할 수 있게 합니다. 이는 등고선 지도와 유사하게 스트로크 주위에 윤곽선으로 시각화됩니다. 슬라이더를 수정하는 것 외에도, Win 키(맥에서는 Ctrl 키)를 사용하여 색상을 드래그하는 동안 직접 수정할 수 있습니다.

&#x20;       • **너비(Width)**: 이는 스트로크의 영향을 확장합니다. Alt+Win 키(맥에서는 Option+Ctrl 키)와 함께 마우스를 사용하여 직접 수정할 수 있습니다.

*   **Pins**

    Pins allow you to pin certain colours so they will not be affected by strokes. You can think of them as constraining the influence of strokes so that they cannot propagate past the pin. They are indicated as crosses (X) on the UI, and you can also see their influence on the outline for the selected stroke.

    By default, each layer is created with a pin on the neutral axis as this is usually a colour you will want to avoid changing. (You can turn this off in the Customise menu).

    You can create pins by pressing `Ctrl` (`Cmd` on Mac) while clicking with the mouse, move existing pins by clicking and dragging them, or delete them by pressing `Shift` and clicking.\

*   **핀(Pins)**



    핀을 사용하면 특정 색상을 고정하여 스트로크의 영향을 받지 않도록 할 수 있습니다. 핀은 스트로크의 영향을 제한하여 핀을 넘어 전파되지 않도록 합니다. UI에서는 X자로 표시되며, 선택된 스트로크의 윤곽선에서도 그 영향을 확인할 수 있습니다.

    기본적으로 각 레이어는 중립 축에 핀이 하나 생성되는데, 이는 일반적으로 변경을 피하고 싶은 색상이기 때문입니다. (맞춤 설정 메뉴에서 이를 끌 수 있습니다.)

    핀을 만들려면 Ctrl 키(맥에서는 Cmd 키)를 누른 상태에서 마우스를 클릭합니다, 기존 핀을 이동하려면 클릭하고 드래그합니다,  핀을 삭제하려면 Shift 키를 누른 상태에서 클릭합니다.
*   **Layers**

    X Grade supports multiple layers (where each layer has its own set of strokes and pins). Layers are managed in the Layer Section in the top right corner of the X Grade user interface.

    Each layer can be assigned a Zone, using the same Ansel Adams Zone System as used by Base Grade. A layer can have one of three zone types:
* **레이어(Layers)**

&#x20;      X Grade는 여러 레이어를 지원하며, 각 레이어는 고유한 스트로크와 핀 세트를 가집니다. 레이어는 X Grade 사용자 인터페이스의 오른쪽 상단에 있는 레이어 섹션에서 관리됩니다.

각 레이어는 Base Grade에서 사용되는 Ansel Adams Zone System과 동일한 시스템을 사용하여 하나의 존(Zone)을 할당받을 수 있습니다. 레이어는 다음 세 가지 존 타입 중 하나를 가질 수 있습니다:

<table><thead><tr><th width="125">Type</th><th>Description</th></tr></thead><tbody><tr><td>Master</td><td>The layer will affect the whole exposure range<br>레이어는 전체 노출 범위에 영향을 미칩니다.</td></tr><tr><td>Dim</td><td>The layer will affect the exposure range below a pivot point<br>레이어는 피벗 포인트 아래의 노출 범위에 영향을 미칩니다.</td></tr><tr><td>Light</td><td>The layer will affect the exposure range above a pivot point<br>레이어는 피벗 포인트 이상의 노출 범위에 영향을 미칩니다.</td></tr></tbody></table>

In addition, layers can be completely bypassed, have their opacity adjusted (to reduce the effect of a layer), and renamed (by double clicking on the layer name).

If the selected layer is set to either Dim or Light zone mode, additional sliders for the pivot and falloff will appear in the layer section.

When not using the Master zone, the effect of a stroke will be attenuated for pixels whose exposure falls outside the selected zone. When working directly on the image, this can cause confusion (e.g. when using the Dim zone, picking a very bright colour and dragging it will have very little effect on that colour). To help with this, the cursor colour will change from white through orange and finally red as the pixels under the cursor fall further out of the exposure range for the layer.

레이어는 완전히 우회될 수 있으며, 불투명도를 조정하여 레이어의 효과를 줄일 수 있고, 레이어 이름을 더블 클릭하여 이름을 변경할 수 있습니다.

선택된 레이어가 Dim 또는 Light 존 모드로 설정된 경우, 레이어 섹션에 피벗 및 폴오프(pivot and falloff)를 위한 추가 슬라이더가 나타납니다.

마스터 존을 사용하지 않을 때, 선택된 존의 노출 범위를 벗어나는 픽셀에 대해서는 스트로크의 효과가 약해집니다. 이미지에서 직접 작업할 때, 이는 혼란을 초래할 수 있습니다 (예: Dim 존을 사용할 때 매우 밝은 색상을 선택하여 드래그하면 해당 색상에 거의 영향을 미치지 않음). 이를 돕기 위해, 커서 아래의 픽셀이 레이어의 노출 범위를 더 많이 벗어날수록 커서 색상이 흰색에서 주황색, 최종적으로 빨간색으로 변합니다.

*   **Scope**

    The scope uses an opponent colour space where the x-axis corresponds to the green-red axis and the y-axis to the yellow-blue axis. The coloured background reflects the spectral locus. A small cross marks the white point. A line from light blue to orange represents the thermal or Planckian Black Body Locus. The gamut hulls of the mastering and viewing colour space are also shown as a reference. These overlays can be turned on and off in the X Grade customise menu.\

*   **스코프(Scope)**

    스코프는 반대 색 공간을 사용하며, x축은 녹색-빨간색 축에 해당하고 y축은 노란색-파란색 축에 해당합니다. 색상 배경은 스펙트럼 위치를 반영합니다. 작은 십자가는 백색점을 나타냅니다. 연한 파란색에서 주황색으로 이어지는 선은 열 또는 플랑크 흑체 궤적을 나타냅니다. 마스터링 및 뷰잉 색 공간의 색역 헐도 참조로 표시됩니다. 이러한 오버레이는 X Grade 맞춤 설정 메뉴에서 켜고 끌 수 있습니다.
*   **Desk Mapping**

    X Grade is designed as a primary grading tool, which means all functions can be accessed via a Blackboard or Slate control surface.

    One trackball is used for positioning the mouse pointer - by default this is the left hand trackball but can be swapped to the right from the Customise menu. We will refer to the ball controlling the mouse pointer as the **Mouse** trackball and the opposite ball as the **Far** trackball. The Middle and Far balls are used to move the start and end points of the current stroke. If there is no current stroke a stroke will be created - this happens immediately when the pointer is on the Image screen, but a click is required when interacting with the UI scope to protect against accidentally creating strokes while working.

    The Zone parameters for the Layer and the Exposure and Width settings for the selected stroke can also be directly modified from the panel encoders, and the Exposure and Layer Opacity parameters are also mapped to the Middle and Far rings of the panel.
*   **데스크 매핑(Desk Mapping)**

    X Grade는 기본 그레이딩 도구로 설계되어, 모든 기능을 Blackboard 또는 Slate 컨트롤 표면을 통해 접근할 수 있습니다.

    한 개의 트랙볼은 마우스 포인터의 위치를 지정하는 데 사용되며, 기본적으로 왼쪽 트랙볼이지만 맞춤 설정 메뉴에서 오른쪽으로 변경할 수 있습니다. 마우스 포인터를 제어하는 트랙볼을 ‘마우스 트랙볼’로, 반대쪽 트랙볼을 ‘원거리 트랙볼’로 지칭합니다. 가운데와 원거리 트랙볼은 현재 스트로크의 시작점과 끝점을 이동하는 데 사용됩니다. 현재 스트로크가 없는 경우, 스트로크가 생성됩니다. 이미지 화면에서 포인터가 있는 경우 즉시 생성되지만, UI 스코프와 상호작용할 때는 작업 중 실수로 스트로크가 생성되지 않도록 클릭이 필요합니다.



    레이어의 존 파라미터와 선택된 스트로크의 노출 및 너비 설정도 패널 인코더에서 직접 수정할 수 있으며, 노출과 레이어 불투명도 파라미터는 패널의 가운데 및 원거리 링에도 매핑되어 있습니다.
*   **Technical Notes**

    It is essential to understand that the effect of the strokes is additive, and they are applied in the order created. The additive nature of the strokes is more suited to intuitive grading (you can generally just drag what you want to change without worrying about previous strokes) and generates a more robust result because folds can be avoided even if strokes cross each other. But it does have the drawback that the strokes do not represent the net result of the change for a given point but the history of strokes you added. Bug 49114
*   **기술 참고 사항(Technical Notes)**

    스트로크의 효과는 더해지며, 생성된 순서대로 적용된다는 점을 이해하는 것이 중요합니다. 스트로크의 더해지는 특성은 직관적인 그레이딩에 더 적합합니다 (일반적으로 이전 스트로크에 대해 걱정하지 않고 변경하고 싶은 대로 드래그할 수 있음) 또한 스트로크가 서로 교차하더라도 접힘을 피할 수 있기 때문에 더 견고한 결과를 생성합니다. 그러나 이러한 특성은 주어진 지점에서 변화의 순수한 결과가 아니라 추가한 스트로크의 이력을 나타낸다는 단점이 있습니다. \[버그 49114]

## Chromogen

* Chromogen is a ground-breaking framework for look development based on human perception. Look development is usually performed before principal photography. Together with the Director of Photography, the colourist can use Chromogen to create a unique look for a specific project. Chromogen is designed to work in a scene-referred colour management workflow. It is both Working Colour Space and DRT agnostic. However, if the DRT already incorporates a prominent look component, it will be harder to produce novel looks or to escape the look of the DRT. Chromogen is colour space aware and operates in its own perceptual colour space called Eab. **E** stands for Exposure and **a/b** are the colour opponent axes, where **a** encodes the green/red axis and **b** encodes the blue/yellow axis.\
  \
  To build a look, **stages** are stacked on top of each other. There are ten different types of stage a user can choose from. Each stage type is a simple tool providing look development functionality. Complex looks are produced by adding many simple stages together. All stages are performed at once on the GPU in floating-point precision. This ensures the highest image quality and best performance. Looks created with Chromogen can be exported as LUTs for preview purposes (for On Set visualisation), but it is recommended to apply the look via the Chromogen operator for the final grade to ensure the highest image quality and flexibility.\


## 크로모젠(Chromogen)

* 크로모젠은 인간의 인식을 기반으로 한 획기적인 룩 개발 프레임워크입니다. 룩 개발은 일반적으로 본 촬영 전에 수행됩니다. 촬영 감독과 함께 컬러리스트는 크로모젠을 사용하여 특정 프로젝트에 고유한 룩을 만들 수 있습니다. 크로모젠은 씬 참조 색상 관리 워크플로우에서 작동하도록 설계되었습니다. 이는 작업 색상 공간 및 DRT에 구애받지 않습니다. 그러나 DRT가 이미 두드러진 룩 구성 요소를 포함하고 있다면, 새로운 룩을 생성하거나 DRT의 룩에서 벗어나는 것이 어려워집니다. 크로모젠은 색상 공간을 인식하고, **Eab**라는 자체 인지 색상 공간에서 작동합니다. E는 노출을, **a/b**는 색상 반대 축을 나타내며, **a**는 녹색/빨간색 축을, **b**는 파란색/노란색 축을 인코딩합니다.\
  \
  룩을 구축하기 위해 **스테이지**가 서로 위에 쌓입니다. 사용자는 열 가지 다른 유형의 스테이지 중에서 선택할 수 있습니다. 각 스테이지 유형은 룩 개발 기능을 제공하는 간단한 도구입니다. 복잡한 룩은 여러 간단한 스테이지를 함께 추가하여 생성됩니다. 모든 스테이지는 GPU에서 부동 소수점 정밀도로 한 번에 수행됩니다. 이는 최고 품질의 이미지와 최고의 성능을 보장합니다. 크로모젠으로 생성된 룩은 미리보기 목적으로 LUT로 내보낼 수 있지만(현장 시각화를 위해), 최종 그레이드에서는 크로모젠 연산자를 통해 룩을 적용하는 것이 최고 품질의 이미지와 유연성을 보장하기 위해 권장됩니다.
*   **Presets**

    It is best to start a look development session from one of the presets shipped with Chromogen. However, completely new looks can be created from scratch, too.

    Chromogen ships with the following presets (see "Operator Presets" section below):

    * **Alternia**: basic look with subtle saturation boost in the shadows and prominent skin tone bleaching
    * **Optera**: influenced by the C-105 Vision look
    * **Kulthea**: influenced by the C-102 Japanese look
    * **Viena**: influenced by the C-104 Bipack look
    * **Eternia**: a novel version of a teal and orange look
    * **Motavia**: a modern approach to a sepia look.
    * **Botany**: a strong dystopian look.
    * **Ireta**: an intense look with distinct colour stylisation.
    * **Lithia**: a look with strong colour skews.

    When adding a new Chromogen operator you are taken directly to the operator's Presets page, to allow you to choose a preset to start from.

    Selecting a Chromogen preset activates the **Append** button in the Presets page. When you use **Append**, instead of the current Operator being replaced by the Preset, the stages in the Preset contents are appended to the current Chromogen operator.\

*   **프리셋(Presets)**

    룩 개발 세션을 시작할 때는 Chromogen에 내장된 프리셋 중 하나를 사용하는 것이 좋습니다. 그러나 완전히 새로운 룩도 처음부터 만들 수 있습니다.

    Chromogen은 다음 프리셋과 함께 제공됩니다 (아래 “Operator Presets” 섹션 참조):



    • Alternia: 그림자에 미묘한 채도 증가와 두드러진 피부톤 표백이 있는 기본 룩

    • Optera: C-105 Vision 룩에 영향을 받은 룩

    • Kulthea: C-102 Japanese 룩에 영향을 받은 룩

    • Viena: C-104 Bipack 룩에 영향을 받은 룩

    • Eternia: 청록색과 주황색 룩의 새로운 버전

    • Motavia: 현대적인 세피아 룩 접근법

    • Botany: 강한 디스토피아 룩

    • Ireta: 독특한 색상 스타일링이 있는 강렬한 룩

    • Lithia: 강한 색상 왜곡이 있는 룩



    새로운 Chromogen 연산자를 추가하면, 연산자의 프리셋 페이지로 바로 이동하여 시작할 프리셋을 선택할 수 있습니다.

    Chromogen 프리셋을 선택하면 프리셋 페이지에서 **Append** 버튼이 활성화됩니다. **Append**를 사용하면 현재 연산자가 프리셋으로 교체되는 대신, 프리셋 내용의 스테이지가 현재 Chromogen 연산자에 추가됩니다.
*   **Stages**

    The different stages are managed using the **Stages** area on the right side of the UI. Adding new stages, duplicating and deleting them are accessed by a context menu (brought up by right-clicking in the stages area). There are ten different stage types; each type can be added more than once. The stages are divided into three main categories: fundamental, advanced and sector stages:\

*   **스테이지(Stages)**

    다양한 스테이지는 UI의 오른쪽에 있는 **스테이지** 영역에서 관리됩니다. 새로운 스테이지를 추가하거나 복제 및 삭제하는 기능은 컨텍스트 메뉴(스테이지 영역에서 오른쪽 클릭으로 불러올 수 있음)를 통해 접근할 수 있습니다. 총 열 가지의 서로 다른 스테이지 유형이 있으며, 각 유형은 여러 번 추가할 수 있습니다. 스테이지는 크게 세 가지 주요 카테고리로 나뉩니다: 기본 스테이지, 고급 스테이지, 섹터 스테이지:\


    **Fundamental Stages** are stages used in almost every look. They build the foundation of the look process.

    * **Colour Saturation**: This tool allows the saturation along the two colour opponent signals to be modified independently. It is influenced by the theory of colour contrast adaptation.
    * **Colour Crosstalk**: This tool introduces crosstalk between the two colour opponent signals. The tool is motivated by crosstalk effects in the visual cortex, like lateral inhibition.
    * **Highlight Bleach**: This tool is for desaturating or bleaching highlights. Most looks desaturate the highlights to give a non-uniform saturation tracking. The four different sides of the colour space can be bleached individually.
    * **Contrast Boost**: This tool allows adding contrast around mid grey, but slightly reduces the brightness of very bright colours. This gives a unique contrast boost found in many popular looks.

    \
    **기본 스테이지(Fundamental Stages)**

    기본 스테이지는 거의 모든 룩에서 사용되며, 룩 프로세스의 기초를 형성합니다.

    • **색상 채도(Colour Saturation)**: 이 도구는 두 색상 반대 신호의 채도를 독립적으로 수정할 수 있게 합니다. 색상 대비 적응 이론에 영향을 받았습니다.

    • **색상 크로스토크(Colour Crosstalk)**: 이 도구는 두 색상 반대 신호 사이에 크로스토크를 도입합니다. 이 도구는 시각 피질에서의 크로스토크 효과, 예를 들어 측면 억제에 의해 동기 부여되었습니다.

    • **하이라이트 표백(Highlight Bleach)**: 이 도구는 하이라이트의 채도를 낮추거나 표백하는 데 사용됩니다. 대부분의 룩은 불균일한 채도 추적을 제공하기 위해 하이라이트의 채도를 낮춥니다. 색상 공간의 네 가지 다른 면을 개별적으로 표백할 수 있습니다.

    • **대비 증가(Contrast Boost)**: 이 도구는 중간 회색 주변에 대비를 추가하면서, 매우 밝은 색상의 밝기를 약간 줄입니다. 이는 많은 인기 있는 룩에서 발견되는 독특한 대비 증가를 제공합니다.

    \
    **Advanced Stages** are used for very specific operations.

    * **Brilliance Reduction**: This tool allows a reduction of exposure of colours which are too bright for their saturations, according to reflected colours. See [this video](https://vimeo.com/333078338) for more information on this topic.
    * **Neutral Tint**: This tool allows you to tint the neutral axis. Many popular looks have a coloured neutral axis, such as blue in the shadows and orange in the highlights.

    **고급 스테이지(Advanced Stages)** 는 매우 특정한 작업에 사용됩니다.

    • **광택 감소(Brilliance Reduction)**: 이 도구는 반사된 색상에 따라 채도에 비해 너무 밝은 색상의 노출을 줄일 수 있습니다. 이 주제에 대한 자세한 내용은 이 비디오를 참조하십시오.

    • **중립 틴트(Neutral Tint)**: 이 도구는 중립 축에 색조를 추가할 수 있습니다. 많은 인기 있는 룩은 중립 축에 색상이 포함되어 있으며, 예를 들어 그림자에는 파란색, 하이라이트에는 주황색이 있습니다.\
    \


    **Sector stages** operate on half of the colour volume but focus on the sector's centre with a soft roll-off.

    * **Sector Brightness**: modifies the brightness of the selected sector.
    * **Sector Saturation**: modifies the saturation of the selected sector.
    * **Sector Skew**: skews or distorts the colours of the selected sector.
    * **Sector Squash**: squashes or stretches the colours of the selected sector.



**섹터 스테이지(Sector Stages)**는 색상 볼륨의 절반을 대상으로 하지만 섹터의 중심에 부드러운 롤오프를 적용하여 집중적으로 작동합니다.

• **섹터 밝기(Sector Brightness)**: 선택된 섹터의 밝기를 수정합니다.

• **섹터 채도(Sector Saturation)**: 선택된 섹터의 채도를 수정합니다.

• **섹터 왜곡(Sector Skew)**: 선택된 섹터의 색상을 왜곡하거나 비틉니다.

• **섹터 압축(Sector Squash)**: 선택된 섹터의 색상을 압축하거나 늘입니다.



*   **Modulation**

    Most stages can be modulated to focus their effect on either darker or brighter colours using the **Zone** and **Pivot** controls in the **Modulation** section. Also, the effect can be focused on either saturated or pastel colours using the **Chroma** modulation control.

    All tools are, intentionally, very broad in terms of the colours they affect; even the sector tools still operate on half of the colour space. Broad edits will produce more robust, pleasing, and general looks, which work across many shots.
* **변조(Modulation)**\
  대부분의 스테이지는 **변조** 섹션의 **존(Zone)** 및 **피벗(Pivot)** 컨트롤을 사용하여 더 어두운 색상이나 더 밝은 색상에 효과를 집중하도록 조정할 수 있습니다. 또한 **크로마(Chroma)** 변조 컨트롤을 사용하여 효과를 채도 높은 색상이나 파스텔 색상에 집중시킬 수 있습니다.\
  모든 도구는 영향을 미치는 색상 범위가 매우 넓도록 의도적으로 설계되었습니다. 심지어 섹터 도구도 여전히 색상 공간의 절반을 다룹니다. 넓은 범위의 편집은 더 견고하고, 만족스러우며, 일반적인 룩을 만들어 여러 샷에 걸쳐 잘 작동합니다.\

*   **Parameters**

    Once a stage is selected, its parameters are shown on the left side of the UI. The coloured slider backgrounds are designed to illustrate the function of each slider.
* 파라미터(Parameters)\
  스테이지가 선택되면 해당 파라미터가 UI의 왼쪽에 표시됩니다. 색상이 있는 슬라이더 배경은 각 슬라이더의 기능을 시각적으로 설명하기 위해 설계되었습니다.\

*   **Graphical Visualisation**

    Below the sliders, there are two graphical representations. The left one is the **Point Cloud**, which indicates the combined modification of all stages. The right side UI element changes depending on the selected stage and provides specific feedback for that stage.

    The default **Point Cloud** representation, **Eab Radial** shows a radial view onto the Eab colour space. This is the recommended view, but the **Eab Cube** and **RGB Cube** representations may be useful for the final evaluation.

    You can pan, rotate, scale, and zoom the point cloud to examine your look from all sides using the mouse and modifier keys. The maximum gamut of the point cloud can also be modified between Eab, LMS, Rec.2020 and Rec.709. The most useful is the Eab gamut. To see specific colours from the image in context to the Point Cloud, it is possible to highlight a specific colour range. Enable the **Pick** button next to the View and pick in the image. This will make all points in the clouds smaller except the picked points.
* **그래픽 시각화(Graphical Visualisation)**\
  슬라이더 아래에는 두 가지 그래픽 표현이 있습니다. 왼쪽은 모든 스테이지의 결합된 수정 사항을 나타내는 포인트 클라우드(**Point Cloud**)입니다. 오른쪽 UI 요소는 선택된 스테이지에 따라 변경되며, 해당 스테이지에 대한 구체적인 피드백을 제공합니다.\
  \
  기본 **포인트 클라우드** 표현인 **Eab Radial**은 Eab 색상 공간에 대한 방사형 보기를 보여줍니다. 이 뷰가 권장되지만, 최종 평가를 위해 **Eab Cube** 및 **RGB Cube** 표현도 유용할 수 있습니다.\
  \
  마우스와 수정 키를 사용하여 포인트 클라우드를 팬, 회전, 확대/축소하여 모든 측면에서 룩을 검사할 수 있습니다. 포인트 클라우드의 최대 색역은 Eab, LMS, Rec.2020 및 Rec.709 사이에서 변경할 수 있습니다. 가장 유용한 것은 Eab 색역입니다. 포인트 클라우드에서 이미지의 특정 색상을 문맥에 맞게 보기 위해 특정 색상 범위를 강조 표시할 수 있습니다. View 옆의 Pick 버튼을 활성화하고 이미지를 클릭하면, 선택된 포인트를 제외한 모든 클라우드 포인트가 작아집니다.\

*   **Desk Mapping**

    When a desk is connected, a secondary stage selection appears next to the primary one. With the two-stage selections, two stages are mapped simultaneously to the encoders of the control surface. The left and right trackballs can also modify essential parameters of the primary selected stage. The two leftmost buttons above the left trackball allow moving the primary stage selection up and down. The middle buttons above the left trackball allow moving stages up and down to rearrange the stage ordering. Buttons above the right trackball allow doing the same for the secondary selection. The middle trackball and ring, in combination with the buttons above and ring, allow you to pan, rotate, scale and zoom the Eab Point Cloud. Bug 53354
* **데스크 매핑(Desk Mapping)**\
  데스크가 연결되면 기본 스테이지 선택 옆에 보조 스테이지 선택이 나타납니다. 두 개의 스테이지 선택을 통해 두 개의 스테이지가 동시에 제어 표면의 인코더에 매핑됩니다. 왼쪽과 오른쪽 트랙볼은 기본 선택된 스테이지의 주요 매개변수를 수정할 수 있습니다. 왼쪽 트랙볼 위의 가장 왼쪽 두 버튼은 기본 스테이지 선택을 위아래로 이동할 수 있게 합니다. 왼쪽 트랙볼 위의 중간 버튼은 스테이지의 순서를 재배열하기 위해 스테이지를 위아래로 이동할 수 있게 합니다. 오른쪽 트랙볼 위의 버튼은 보조 선택에 대해 동일한 작업을 수행할 수 있게 합니다. 가운데 트랙볼과 링은 위의 버튼 및 링과 조합하여 Eab 포인트 클라우드를 팬, 회전, 확대/축소할 수 있게 합니다. \[버그 53354]



### User Interface

*   **Refreshed Appearance**

    Baselight 6.0 sports a refreshed user interface, with a less obtrusive, flatter appearance:

    * Toggle and radio buttons are now visually distinct from one other and have a highlight when activated.
    * Active tabs are indicated with a clear blue underline.
    * There is a now a standardised colour palette across the application.
    * The **Customise** menu button has been replaced with an icon button showing three sliders.
    * A number of icons have been upgraded, amongst them Reset, Bypass, Cache Strip, Slider Gang and Split Strip.
    * List selections are now blue.
    * Redesigned Keyframe Navigation Bar with larger keyframe indicators.
    * Replaced Mona Lisa icons with text **Grade** and **Matte**.
    * Adding browser or filter tabs to FLUX Manage is now included in single dropdown menu button.
    * Toggle icons are now dimmer when turned off.
    * User interface elements are now laid out more tightly.
    * Radio buttons, toggle check buttons, and button roundness now scale better with different text sizes.
    * Splitter bars are now thicker and the splitters used to separate views now have rounded connectors.
    * Tile group boxes and buttons have had their borders removed and made slighly brighter.

### 사용자 인터페이스(User Interface)

* 새로워진 외관(Refreshed Appearance)\
  Baselight 6.0은 덜 눈에 띄고 더 평평한 외관으로 새로워진 사용자 인터페이스를 제공합니다:
  * 토글 및 라디오 버튼이 서로 시각적으로 구별되며, 활성화되면 하이라이트가 표시됩니다.
  * 활성 탭은 명확한 파란색 밑줄로 표시됩니다.
  * 애플리케이션 전반에 걸쳐 표준화된 색상 팔레트가 도입되었습니다.
  * 맞춤 설정 메뉴 버튼이 세 개의 슬라이더가 있는 아이콘 버튼으로 교체되었습니다.
  * 여러 아이콘이 업그레이드되었으며, 그중에는 재설정, 우회, 캐시 스트립, 슬라이더 갱 및 분할 스트립 아이콘이 포함됩니다.
  * 목록 선택이 이제 파란색으로 표시됩니다.
  * 키프레임 탐색 막대가 더 큰 키프레임 표시기로 재설계되었습니다.
  * 모나리자 아이콘이 텍스트 Grade 및 Matte로 교체되었습니다.
  * FLUX Manage에 브라우저 또는 필터 탭을 추가하는 기능이 단일 드롭다운 메뉴 버튼에 포함되었습니다.
  * 토글 아이콘이 꺼졌을 때 더 어둡게 표시됩니다.
  * 사용자 인터페이스 요소가 더 밀집하게 배치되었습니다.
  * 라디오 버튼, 토글 체크 버튼 및 버튼의 둥근 모양이 다른 텍스트 크기에 더 잘 맞게 조정되었습니다.
  * 스플리터 막대가 더 두꺼워졌으며, 보기를 분할하는 데 사용되는 스플리터가 이제 둥근 연결부를 가집니다.
  * 타일 그룹 상자와 버튼의 테두리가 제거되고 약간 더 밝아졌습니다.\

*   **Timeline Bar**

    A top row of controls has been added above the Timeline View. This contains play controls, playback filtering, paste/apply options, and timeline editing tools.

    * Play Controls View has been removed from all default workspaces and custom workspaces that also contain a Timeline View.
    * Controls for playback range, loop mode, and play all frames are now displayed in the Timeline View toolbar and no longer contained in a menu.
    * Playback Speed now displays decimals rather than fractions.
    * Includes a new toggle button for entering and exiting Timeline Edit Mode.
    * All Copy / Paste / Apply options can be accessed from controls in the Timeline Bar when it isn't in Edit Mode:
      * Dropdown menu displays the current state of Paste / Apply options.
      * Four top-level toggle icons for **Protect Destination Mattes**, **Paste Only Primaries**, **Paste Keyframes**, and **Maintain Tracks**.
      * Paste / Apply options are now shared between Galleries and Cuts View.
    * This means that remaining Cuts View controls are now contained in a small floating panel and the option for thumbnail display has been moved to the right-click menu. Bug 64271
*   **타임라인 바(Timeline Bar)**

    타임라인 보기 위에 새로운 제어 행이 추가되었습니다. 여기에는 재생 제어, 재생 필터링, 붙여넣기/적용 옵션 및 타임라인 편집 도구가 포함됩니다.

    * 재생 제어 보기(Play Controls View)가 모든 기본 작업 공간 및 타임라인 보기를 포함하는 사용자 지정 작업 공간에서 제거되었습니다.
    * 재생 범위, 루프 모드 및 모든 프레임 재생 제어가 이제 메뉴에 포함되지 않고 타임라인 보기 도구 모음에 표시됩니다.
    * 재생 속도는 이제 분수 대신 소수로 표시됩니다.
    * 타임라인 편집 모드로 들어가고 나가는 새로운 토글 버튼이 포함되었습니다.
    * 복사/붙여넣기/적용 옵션은 편집 모드가 아닐 때 타임라인 바의 제어에서 접근할 수 있습니다:
      * 드롭다운 메뉴는 현재 붙여넣기/적용 옵션 상태를 표시합니다.
      * **보호 대상 매트(Protect Destination Mattes), 기본 색상만 붙여넣기(Paste Only Primaries), 키프레임 붙여넣기(Paste Keyframes) 및 트랙 유지(Maintain Tracks)**를 위한 네 개의 상위 레벨 토글 아이콘
      * 붙여넣기/적용 옵션은 이제 갤러리와 컷 보기 사이에서 공유됩니다.
    * 따라서 남아 있는 컷 보기 제어는 이제 작은 떠 있는 패널에 포함되며, 썸네일 표시 옵션은 오른쪽 클릭 메뉴로 이동되었습니다. \[버그 64271]

#### Face Tracker

*   Added a new 3D Machine Learning tracker, designed specifically for detecting and tracking faces. It can be found in the new **Face** tab inside the Tracker strip.

    The Face Tracker differs from other trackers in that face detection needs to be performed before tracking. It will attempt to detect all faces in an image without the need to specify a tracking area. This produces closed 3D mesh geometry for every detected face, geometry that can be tracked and filtered like other tracking types.

    Face detection may be affected by very dark images or faces that are partially occluded. The following options found in the 'Face' tab's cog menu could improve detection and tracking:

    * **Face Detect Threshold**. Lowering the value will help to detect faces not previously detected. Setting the value too low may detect faces where there are none.
    * **Face Tracking Smoothing Threshold**. Increasing the value before tracking might help with jitter on some problematic material.

    Although face tracking results can't be modified or offset like other trackers, occlusions can be handled using the **Detect Reference** functionality.

    If the **Auto select face reference** option is on, the system will pick the most similar face in that frame based on the geometry. If the option is off and it detects multiple faces, the user will have the option to select the correct face.

    The Face Tracker can be used in two different contexts, Face Warp and Face Perspective.

### 얼굴 추적기(Face Tracker)

*   새로운 3D 머신 러닝 추적기가 추가되어 얼굴을 감지하고 추적하는 데 특화되었습니다. 이 추적기는 Tracker 스트립 내의 새로운 Face 탭에서 찾을 수 있습니다.

    \
    얼굴 추적기는 다른 추적기와 달리 추적 전에 얼굴 감지를 수행해야 합니다. 추적 영역을 지정할 필요 없이 이미지 내 모든 얼굴을 감지하려고 시도합니다. 이는 감지된 모든 얼굴에 대해 닫힌 3D 메쉬 기하학을 생성하며, 이 기하학은 다른 추적 유형처럼 추적 및 필터링할 수 있습니다.



    얼굴 감지는 매우 어두운 이미지나 부분적으로 가려진 얼굴에 영향을 받을 수 있습니다. ‘Face’ 탭의 톱니바퀴 메뉴에서 다음 옵션을 통해 감지 및 추적 성능을 향상시킬 수 있습니다:



    • **얼굴 감지 임계값(Face Detect Threshold)**: 값을 낮추면 이전에 감지되지 않은 얼굴을 감지하는 데 도움이 됩니다. 값이 너무 낮으면 얼굴이 없는 곳에서도 얼굴을 감지할 수 있습니다.

    • **얼굴 추적 평활화 임계값(Face Tracking Smoothing Threshold)**: 추적 전에 값을 높이면 일부 문제 있는 자료의 흔들림을 줄이는 데 도움이 될 수 있습니다.



    얼굴 추적 결과는 다른 추적기처럼 수정하거나 오프셋할 수는 없지만, Detect Reference 기능을 사용하여 가려짐을 처리할 수 있습니다.

    **자동 얼굴 참조 선택(Auto select face reference)** 옵션이 켜져 있으면, 시스템은 기하학을 기반으로 해당 프레임에서 가장 유사한 얼굴을 선택합니다. 옵션이 꺼져 있고 여러 얼굴이 감지되면 사용자가 올바른 얼굴을 선택할 수 있습니다.



    얼굴 추적기는 Face Warp와 Face Perspective라는 두 가지 다른 컨텍스트에서 사용할 수 있습니다.\

*   **Face Warp**

    Face Warp is only available in Shapes and Matte Paint - it uses the 3D mesh generated during the face detection phase to warp mattes to fit the face. They will be constrained to the 3D Mesh. Edge shapes are not supported.

    Face detection is performed by clicking the **Face Warp** button in the Shape or Paint operator, or the **Detect Faces** button in the Tracker strip. This must be done before any shapes or strokes are added. After detection, the detected faces can be selected from the tracker list. Faces will have a 3D mesh displayed over the face. Shapes or paint strokes can now be added to the linked face. Face Warp-specific Quick Shapes are available in the Shape operator.

    When using Face Warp, mattes are defined in 'UV' space, which can be thought of as a 2D space representing the unwrapped face. The 3D Mesh is used to project the mattes onto a 3D representation of the face. After shapes or paint strokes are linked to a Face Warp Tracker, changing to a different face will automatically reposition the shape or paint strokes onto the newly selected face.

    Face Warps cannot be unlinked or deleted because, since the matte is defined in the UV 'face' space, they doesn't make sense when not linked to a face - the only valid operation is linking to another face.

    The **Show UV** button will display a side by side view of the image and a 'flattened' view in UV space. This view can be useful to place shapes and paint strokes, because, as it is independent of the pose of the face, it remains roughly constant as the face moves.

    The **Face Zoom** button will zoom to the selected face, allowing for more precise edits.
*   **얼굴 왜곡(Face Warp)**

    얼굴 왜곡 기능은 Shapes 및 Matte Paint에서만 사용할 수 있으며, 얼굴 감지 단계에서 생성된 3D 메쉬를 사용하여 얼굴에 맞게 매트를 왜곡합니다. 이는 3D 메쉬에 제약을 받으며, 가장자리(shape) 형태는 지원되지 않습니다.

    얼굴 감지는 Shape 또는 Paint 연산자에서 Face Warp 버튼을 클릭하거나 Tracker 스트립에서 Detect Faces 버튼을 클릭하여 수행됩니다. 이는 어떤 shape 또는 stroke를 추가하기 전에 수행해야 합니다. 감지 후, 감지된 얼굴을 추적기 목록에서 선택할 수 있습니다. 얼굴에는 3D 메쉬가 표시됩니다. 이제 얼굴에 링크된 shape 또는 paint stroke를 추가할 수 있습니다. Face Warp 전용 Quick Shapes는 Shape 연산자에서 사용할 수 있습니다.

    Face Warp를 사용할 때 매트는 ‘UV’ 공간에서 정의되며, 이는 펼쳐진 얼굴을 나타내는 2D 공간으로 생각할 수 있습니다. 3D 메쉬는 매트를 얼굴의 3D 표현에 투사하는 데 사용됩니다. Shape 또는 paint stroke가 Face Warp Tracker에 연결된 후 다른 얼굴로 변경하면 shape 또는 paint stroke가 자동으로 새로 선택된 얼굴에 재배치됩니다.

    얼굴 왜곡은 링크 해제되거나 삭제될 수 없습니다. 매트가 UV ‘얼굴’ 공간에서 정의되기 때문에 얼굴에 연결되지 않으면 의미가 없기 때문입니다. 유효한 작업은 다른 얼굴에 연결하는 것입니다.

    Show UV 버튼은 이미지와 UV 공간에서 ‘펼쳐진’ 뷰를 나란히 표시합니다. 이 뷰는 얼굴의 자세와 독립적이기 때문에 얼굴이 움직일 때도 대체로 일정하게 유지되므로 shape와 paint stroke를 배치하는 데 유용할 수 있습니다.

    Face Zoom 버튼은 선택된 얼굴을 확대하여 더 정확한 편집을 할 수 있도록 합니다.\

*   **Face Perspective**

    Used to perform perspective transforms based on 3 points positioned on a a face's 3D mesh. These points are used to to derive a plane which is then used to generate perspective transformations. It can be used with all operators which support Perspective Trackers (i.e. Shapes, Paint, Text, Grid Warp and Perspective). The 3 points are displayed as a blue triangle on the image when the Tracker strip is selected and can be edited there.

    To use the Face Perspective Tracker, the desired Shape, Paint stroke, Text or Grid Warp is created first and then linked to the Perspective Tracker.

    After choosing a Face Perspective track, changing to a different face perspective track will reposition the controls onto the selected face. Unlike Face Warp tracks, Face Perspective tracks can be unlinked and deleted.
*   **얼굴 관점(Face Perspective)**

    얼굴 관점은 얼굴의 3D 메쉬에 위치한 3개의 점을 기반으로 원근 변환을 수행하는 데 사용됩니다. 이러한 점들은 평면을 도출하는 데 사용되며, 이를 통해 원근 변환을 생성합니다. 이는 Perspective Trackers를 지원하는 모든 연산자(예: Shapes, Paint, Text, Grid Warp 및 Perspective)와 함께 사용할 수 있습니다. 트래커 스트립이 선택되면 3개의 점이 이미지에 파란색 삼각형으로 표시되며, 이곳에서 편집할 수 있습니다.

    얼굴 관점 트래커를 사용하려면 원하는 Shape, Paint stroke, Text 또는 Grid Warp를 먼저 생성한 후 Perspective Tracker에 링크합니다.

    얼굴 관점 트랙을 선택한 후, 다른 얼굴 관점 트랙으로 변경하면 제어가 선택된 얼굴에 재배치됩니다. 얼굴 왜곡 트랙과 달리 얼굴 관점 트랙은 링크 해제 및 삭제할 수 있습니다.\

*   **Copy and Paste**

    To enhance workflows, the Face Tracker works differently to the other tracker types when being applied to other shots. When a stack contains tracked faces, applying the stack will check the destination shot to see if any tracked faces are already present in a Tracker strip. If so, the grade will be relinked to one of the existing faces. If not, a face detection is performed, and the grade is linked to one of the newly detected faces.

    If the incorrect face was selected, one can go to the relevant operator and simply select the correct face from the tracker list. Any operators will be automatically remapped to the new selection.
*   **복사 및 붙여넣기(Copy and Paste)**

    워크플로우를 개선하기 위해 얼굴 추적기는 다른 추적기 유형과 다르게 작동하여 다른 샷에 적용됩니다. 스택에 추적된 얼굴이 포함된 경우, 스택을 적용하면 대상 샷의 Tracker 스트립에 이미 추적된 얼굴이 있는지 확인합니다. 이미 추적된 얼굴이 있으면 그레이드가 기존 얼굴 중 하나에 다시 연결됩니다. 그렇지 않으면 얼굴 감지가 수행되며, 그레이드가 새로 감지된 얼굴 중 하나에 연결됩니다.

    잘못된 얼굴이 선택된 경우, 관련 연산자로 이동하여 추적기 목록에서 올바른 얼굴을 선택하기만 하면 됩니다. 모든 연산자는 자동으로 새로운 선택에 맞게 재매핑됩니다.\
    \

*   **Technical Details**

    The machine learning models used to implement the Face Tracker are part of a separate filmlight-flexi-effects installer, which is available in the support section of the FilmLight website.

    Face Tracker does not currently run on Intel macOS systems. Bug 51467
*   **기술 세부 사항(Technical Details)**

    얼굴 추적기를 구현하는 데 사용된 머신 러닝 모델은 별도의 filmlight-flexi-effects 설치 프로그램의 일부로, FilmLight 웹사이트의 지원 섹션에서 이용할 수 있습니다.

    얼굴 추적기는 현재 Intel macOS 시스템에서는 실행되지 않습니다. \[버그 51467]

#### Timeline

* **New Appearance**
  * **Modern Look**: The new timeline's cleaner, brighter look aims to make strips and their colours more distinct and easier to interpret.
  * **Context-aware strip roundness**: Strip roundness is now used to make it clear which strips contribute to a layer, by only the top-most and bottom-most strips of a layer being rounded.
  * **Node Graph**: To assist users in visualising the actual graph structure represented by a grading stack, a node graph is now superimposed over the shot, when space allows. In this node graph, blue nodes and lines represent RGBA image data flowing down through the graph, whilst white nodes and lines represent nodes that contribute to a single-channel matte input to a layer. Dotted lines represent references to image data further up the stack, outside of the normal implicit tree structure. When a layer/shot is folded, the layer's folded nodes are arranged horizontally beside the layer's node, their colouring allowing the user to see a layer's internal structure, even when folded.

### 타임라인(Timeline)

* **새로운 외관(New Appearance)**
  * **모던 룩(Modern Look)**: 새 타임라인은 더 깨끗하고 밝은 외관을 제공하여 스트립과 그 색상을 더 명확하고 쉽게 해석할 수 있도록 설계되었습니다.
  * **문맥 인식 스트립 둥글기(Context-aware strip roundness)**: 이제 레이어에 기여하는 스트립을 명확히 하기 위해 레이어의 가장 위와 가장 아래에 있는 스트립만 둥글게 표시됩니다.
  * **노드 그래프(Node Graph)**: 사용자가 그레이딩 스택에 의해 나타나는 실제 그래프 구조를 시각화할 수 있도록, 공간이 허용되는 경우 샷 위에 노드 그래프가 중첩됩니다. 이 노드 그래프에서 파란색 노드와 선은 그래프를 통해 흐르는 RGBA 이미지 데이터를 나타내며, 흰색 노드와 선은 레이어에 단일 채널 매트 입력을 기여하는 노드를 나타냅니다. 점선은 정상적인 암시적 트리 구조 외부에서 스택 위쪽으로 더 올라간 이미지 데이터에 대한 참조를 나타냅니다. 레이어/샷이 접힌 경우, 레이어의 접힌 노드는 레이어의 노드 옆에 수평으로 배열되며, 색상을 통해 사용자가 접힌 상태에서도 레이어의 내부 구조를 볼 수 있습니다.



* **Layer / Shot Folding**
  * **Layer Folding**: It is now possible to fold a layer's mattes down into a layer's grade strip, reducing the vertical space used by the layer. A layer's folding state can be toggled either by clicking the triangular folding icon on the right-hand side of the strip or by using the `\` shortcut with one or more layer strips selected. To toggle the folding state of all layers in a shot, select strips in one or more shots and press `Ctrl+\` (`Cmd+\` on Mac).
  * **Shot Folding**: It is also possible to fold all of a shot's grading strips up into the shot's top strip, providing a greatly simplified view of the timeline. A shot's folding state can be toggled by clicking the triangular folding icon on the right-hand side of the shot's top strip or by selecting a strip in one or more shots and pressing `Alt+\`.
*   **Timeline Tracks**

    It is now possible to vertically subdivide a scene's timeline into several tracks. From an image processing point-of-view, this is mostly cosmetic as image data flows down through the strips in the timeline in the same way, regardless of whether they all sit in one track or are split across several. Tracks, however, are very useful in organising complex timelines, allowing the user to divide their grades into separate tracks, each with a different role ("HDR", "Subtitles", "Sky Replacement", "Stereo Floating Windows" etc). All the track functionality is accessed using the Track UI panel on the left-hand side of the timeline:

    * **Context Menu**: Right-clicking anywhere in the track panel provides options to:
      * Insert a new track above/below the track under the mouse pointer.
      * Move the track under the mouse pointer up/down in the timeline
      * Remove the track under the mouse pointer.
      * Remove all empty tracks
    * **Renaming a Track**: By default, tracks are automatically named using a scheme where track numbers increase going downwards (to match layer numbering direction). To rename a track, simply double-click on the track name to enter edit mode and enter a new name.
    * **Track UI Icons**: Each track has four icons on the panel:
      * **Bypass**: Toggle button which, when turned on, will bypass every strip in the track.
      * **Squash**: Toggle button which, when turned on, will squash the track down to be much smaller than normal, showing only the bottom- most strip in each stack. This is useful in reducing timeline clutter by hiding tracks which aren't immediate needed, allowing the user to concentrate on what is important right now. The height of strips in a squashed track can be controlled by the **Squashed Track Height** preference. It's also possible to toggle squashing of all other tracks in the timeline by `Ctrl+clicking` (Mac: `Cmd+click`) the squash track icon.
      * **Edit Lock**: Toggle button which, when turned on, will mark all shot Layer 0 strips as being edit locked. See the "Edit Locking" section below for more details.
      * **Grade Lock**: Toggle button which, when turned on, will mark all grading strips as being grade locked. When inserting or pasting strips, any grade locked tracks will be ignored. `Ctrl+click` (`Cmd+click` on Mac) on the grade lock icon will result in the track being "soloed", whereby it will be unlocked and all other tracks will be grade locked. This is very useful if one wishes to force all strip insertion to occur on a given track. See the "Grade Locking" section below for more details.
    * **Maintain Tracks Paste Option**: The new **Maintain Tracks** paste option controls whether or not the application attempts to maintain a source strip's track when it is pasted. Source and destination tracks are matched by name - if **Maintain Tracks** is on and a source strip's track doesn't exist in the destination scene, it won't be pasted.
    * A **Maintain Tracks** button has been added to the Blackboard Classic, Blackboard 2 and the Slate. It can be found on the "Apply All" button on the Blackboard Classic and in Chalk.
    * **Render Line Movement**: By default, moving the render line up and down will move it between tracks. Using `Shift+up` will force the render line to remain within the current track, which is useful if one wishes to insert additional strips at a sub-row above the highest sub-row in a track. On a Blackboard or Slate `Shift+Up Arrow` has the same behaviour.
*   **Edit Locking**

    It's now possible to edit lock a shot's layer 0 strip, meaning that the shot's horizontal position in the timeline can't be changed and neither can its frame offset within the image/sequence or movie, frame increment etc. This is very useful if one needs to prevent a carefully constructed conform from being accidentally changed. In Edit mode, edit locked strips will show a grey bracket or region indicating that they are edit locked.

    A layer 0 strip can be marked as edit locked in two ways:

    * By edit locking the track in which the strip resides.
    * By assigning a category in **Scene Settings** > **Category Group** > **Edit lock strips of category** to a strip.
*   **Grade Locking**

    Baselight grade locking functionality has been enhanced. Now, in addition to preventing its parameters from being modified, grade locking a strip prevents a grading strip from being moved vertically up/down within a shot.

    A layer 0 strip can be marked as grade locked in two ways:

    * By grade-locking the track in which the strip resides.
    * By assigning a category in **Scene Settings** > **Category Group** > **Grade-lock strips of category** to a strip.

    To allow users used to Baselight 5.3 to restore the previous strip-locking behaviour, two new preferences have been added in the new **Strip Locking** section of the Timeline preferences:

    * **Allow Removal of Grade-Locked Strips**.
    * **Allow Vertical Movement of Grade-Locked Strips**. Bug 65603
*   **Zoom Management**

    The Timeline View now contains a zoom menu at the top right that displays the current zoom percentage relative to the default zoom amount seen on start-up. This menu allows for various methods of zooming the Timeline: - **Zoom In** / **Zoom Out**: Zoom in and out in increments. - **Max Zoom**, **100%**, **50%**, or **10%**: Set horizontal zoom level to one of a number of pre-configured zoom levels. - **Zoom to Selected**: Will zoom to the extent of explicitly selected strips or, if Edit Mode is on, it will zoom to the extent of any edit tool that is set. - **Zoom to Fit Scene**: Zooms out horizontally to show the entire scene. If toggled off the timeline will return to the previous horizontal zoom level. - **Vertical Zoom to Fit Stacks**: Zooms out vertically enough to show all the strips in the scene. If toggled off the timeline will return to the previous vertical zoom level. - **Default Vertical Zoom**: Return to the default vertical zoom level. Bug 59781
*   **JKL Keyboard Accelerators for Playback**

    After many requests and to match the conventions defined by other systems, the JKL keys on the keyboard now map to Play Backwards, Stop Playback and Play Forwards. Repeated presses on J and L will keep doubling the play speed up to a maximum of 32x.

    This change has necessitated changes to the following keyboard accelerators:

    | New Accelerator                     | Old Accelerator | Action                             |
    | ----------------------------------- | --------------- | ---------------------------------- |
    | `V`                                 | `K`             | Toggle Counters                    |
    | `Win+F` (Mac:`Ctrl+F`)              | `F`             | Toggle FPS display                 |
    | `M`                                 | `L`             | Toggle Mark                        |
    | `Shift+M`                           | `Shift+L`       | Delete All Marks Under Cursor      |
    | `Shift+Ctrl+M` (Mac:`Shift+Cmd+M`)  | `Shift+Ctrl+L`  | Delete All Marks                   |
    | `F`                                 | `J`             | Toggle Category                    |
    | `B`                                 | `N`             | Edit Mode Mark In                  |
    | `Shift+B`                           | `Shift+N`       | Remove Mark In                     |
    | `N`                                 | `M`             | Edit Mode Mark Out                 |
    | `Shift+N`                           | `Shift+M`       | Remove Mark Out                    |
    | `Ctrl+N` (Mac: `Cmd+N`)             | `Ctrl+M`        | Mark Selection/Shot/Gap In and Out |
    | `Shift+Ctrl+N` (Mac: `Shift+Cmd+N`) | `Shift+Ctrl+N`  | Clear Mark In and Out              |
    | Removed                             | `M`             | Add Median strip                   |
    | Removed                             | `Shift+M`       | Add Soften strip                   |

    Bug 65270
* To match, the **Reverse Play Direction** toggle has been removed from the Timeline Bar and replaced with a dedicated **Play Backwards** icon, which toggles between playing backwards and stopped. As a result, the **Play** icon will now always play forwards. Bug 66316
* The Keyboard Shortcut PDF files available from the Help menu have now been updated for Baselight 6.0. Bug 66327

#### Edit Mode

*   Baselight 6.0 brings extensive improvements to Timeline Editing.

    The new Edit Mode can be toggled on/off via the **Toggle Timeline Edit Mode** button in the Timeline Bar. It can also be toggled on/off via the **Edit** > **Edit Mode** menu item or via the `Shift+Enter` keyboard shortcut.

    Once Edit Mode is turned on, the Timeline Bar will change to display a variety of icons which provide bits of editing functionality. Each icon can be hovered over to display a tooltip which describes what the icon does along with its equivalent keyboard shortcut.
*   **Shot-Based Editing v.s Selection-Based Editing**

    If there are no explicitly selected strips in the Timeline, the various editing functions will automatically work out the strips which should be affected (typically those strips lying under a top strip).

    On the other hand, if there are explicitly selected strips, then the editing functionality will work based on those selected strips.
*   **Trim Mode and Move Mode\*\***

    The first two icons on the left select what editing mode the timeline is set to. Switching between the two modes will change the available edit tools located to the right of the mode icons.

    **Trim Mode**

    This mode allows the use of editing tools that are related to trimming, rolling, slipping or Sliding a shot. When it is selected, the tool icon section to the right of the mode icons will be occupied with the following five tool icons:

    * **Trim Left**: Trims the left edge of a shot or strip, rippling the strips right of the trim.
    * **Roll**: Trims one edge of a shot or strip whilst extending the other.
    * **Trim Right**: Trims the right edge of a shot or strip, rippling the strips right of the trim.
    * **Slip**: Slips the source media of the shot left or right.
    * **Slide**: Slides the source media of the shot left or right, whilst consuming or extending adjacent strips.

    When these icons are selected, coloured bracket(s) will appear indicating the side(s) of the shot or strip that the edit will affect. The colours of these brackets can be changed in the Preferences, in the **Edit Mode Settings** of the **Timeline** tab. If the edit is based on a cut (e.g. **Trim Left**), the edit brackets will appear at the cut nearest to the current cursor. If the edit is based on a shot or strip (e,g **Slip**), the edit brackets will appear at the shot or strip that the cursor is on. The cursor will follow the edit when trimming a shot at a cut point.

    **Move Mode**

    This mode allows the use of editing tools that are related to trimming and moving a shot. When it is selected, the tool icon section to the right of the mode icons will be occupied with the following 3 tool icons:

    * **Trim Left**: Trims the left edge of a shot or strip, bouncing strips out of the way, if required.
    * **Move Shot**: Moves a shot or strip left or right, bouncing strips out of the way, if required.
    * **Trim Right**: Trims the right edge of a shot or strip, bouncing strips out of the way, if required.

    When these icons are selected, blue bracket(s) will appear indicating the side(s) of the shot or strip that the edit will affect, based on the shot or strip that the cursor is on.
*   **Trim Buttons**

    The following 4 icons to the right of the edit tool icons are dedicated to performing 1-frame or 10-frame trims to the left or right, based on the Edit Tool that is currently selected.
*   **Other Editing Tools**

    The last remaining Edit Mode icons offer several useful tools for editing:

    * **Lift**: When a Mark In and a Mark Out point is set, it removes any strips that lie within the interval and warps the cursor to the Mark Out point.
    * **Extract**: Performs a **Lift**, and ripples the gap that is created by it.
    * **Cut Stack/Selection At Cursor**: Cuts the stack at the cursor if there are no explicitly selected strips. If there are selected strips, they are at the cursor location.
    * **Mark In**: Sets a Mark In at the current cursor position. If there is one already present, it removes it.
    * **Mark Out**: Sets a Mark Out at the current cursor position. If there is one already present, it removes it.
    * **Mark Selection/Shot/Gap In And Out**: Sets a Mark In and a Mark Out on the current selection, or the shot at the current cursor, or the gap at the current cursor, in that order of precedence.
    * **Snap To Nearest Edge/Mark/Cursor while dragging**: Enables/disabled snapping behaviour, which is triggered when a brack is dragged close to the edge of a strip, make or cursor.
*   **Customise Menu**

    The final Edit Mode icon contains a customise menu where several default behaviours can be toggled on or off:

    * **Handle Protection**: When on, it prevents editing operations from going outside of a shot's available media. The size of handles left in frames will be displayed above the edit brackets whilst editing is in progress. When there is media left, the available handles will be displayed in green, whereas if the shot references missing media, the size of missing media will be displayed in red.
    * **Use Display View To Shot Multi-View While Editing**: When on, the Display View will be taken over while editing to show the relevant In and Out points of the edit.
*   **Editing with the Mouse**

    To begin editing with the mouse, simply hover over the desired strips or shots in the Timeline. As you do so, various edit brackets will appear with the corresponding tool highlighted in the Edit toolbar. Which tool appears when you hover is arranged in the same left to right order that the Edit Tools are, based on whether you are in **Trim Mode** or **Move Mode**.

    Clicking on brackets will "lock" the edit point, allowing keyboard accelerators to be used to move the edit point. Clicking again away from the edit point will unlock it again.
*   **FLUX Manage Insertion**

    The insertion button at the bottom right corner of FLUX Manage has been changed to reflect the new editing functionality. It will now contextually show up to 4 buttons:

    * **Append**: Appends the FLUX Manage selection to the end of the Timeline and warps the cursor to it.
    * **Ripple**: Ripples the FLUX Manage selection at the cursor, or within a Mark In and a Mark Out point, if they are set.
    * **Overwrite**: Overwrites the FLUX Manage selection at the cursor, or within a Mark In and a Mark Out point, if they are set.
    * **Overlap**: Overlaps the FLUX Manage selection at the cursor, or within a Mark In and a Mark Out point, if they are set.
*   **Keyboard Shortcuts**

    The following table shows a list of keyboard shortcuts that are mapped to the various pieces of edit mode functionality described above.

    | Keyboard Shortcut              | Edit Mode Functionality                                            |
    | ------------------------------ | ------------------------------------------------------------------ |
    | `T`                            | Trim Mode                                                          |
    | `Y`                            | Move Mode                                                          |
    | `Q`                            | Ripple left of Cursor (Trim Mode)/Trim left of Shot (Move Mode)    |
    | `W`                            | Rolling (Trim Mode) / Move Shot (Move Mode)                        |
    | `E`                            | Ripple right of Cursor (Trim Mode)/ Trim right of Shot (Move Mode) |
    | `S`                            | Slip                                                               |
    | `Shift+S`                      | Slide                                                              |
    | `C`                            | Cut Stack/Selection                                                |
    | `U`                            | Lift                                                               |
    | `I`                            | Extract                                                            |
    | `N`                            | Mark In                                                            |
    | `Shift+N`                      | Clear Mark In                                                      |
    | `M`                            | Mark Out                                                           |
    | `Shift+M`                      | Clear Mark Out                                                     |
    | `Control/Cmd+M`                | Mark Selection/Shot/Gap In And Out                                 |
    | `,`                            | Edit 1 Frame Left                                                  |
    | `Shift+,`                      | Edit 10 Frames Left                                                |
    | `.`                            | Edit 1 Frame Right                                                 |
    | `Shift+.`                      | Edit 10 Frames Right                                               |
    | `Alt+Backspace`                | Ripple Delete                                                      |
    | `Shift+Enter`                  | Toggle Edit Mode On/Off                                            |
    | `/` and `*` (Mac: `=` and `/`) | Toggle Edit Mode On/Off and rotate trim/move modes                 |

    Note that when **Edit Mode** is turned on, the standard grading-related shortcuts originally mapped to will be swapped out to the ones shown above.

    Turning **Edit Mode** off will restore the original keyboard shortcuts. Additional information about the shortcuts may be found by hovering over the relevant icons in the Edit Tools UI. Bug 45266
*   **Performance**

    Greatly improved performance when doing Trim Start/End (Ripple) edits in Edit mode, as well as when doing `Alt+arrow` (Bounce) edits with a large number of selected strips. Bug 53320

#### Alpha (Opacity) Support

* Baselight 6.0 adds extensive support for compositing and working with images with opacity information, normally stored in the alpha channel of RGBA images. Bug 54001
* The Sequence operator **Input RGBA** setting is enabled when the input media has an alpha channel, and allows control over whether to treat the RGB channels as premultiplied by alpha or not, and if premultiplied, whether the multiplication was done in linear or in the native colour space. Bug 62993
*   The Sequence operator **Stack RGBA** setting controls processing of the images entering the grading stack. For RGBA media:

    | Stack RGBA                  | Behaviour                                                  |
    | --------------------------- | ---------------------------------------------------------- |
    | RGBA                        | Passes the RGBA data into the stack unchanged              |
    | RGB (ignoring alpha)        | Discards the alpha channel and makes the image opaque      |
    | RGB (composited onto black) | Scales RGB by the alpha channel and makes the image opaque |

    RGB media is always treated as opaque; Stack RGBA controls the transparency at the edges of the image and the behaviour of operators such as Blur:

    | Stack RGBA | Behaviour                                                                                               |
    | ---------- | ------------------------------------------------------------------------------------------------------- |
    | RGB        | Matches Baselight 5: the area outside the image is opaque black, and remains opaque when blurred        |
    | RGBA       | The area outside the image is transparent, and the image becomes transparent at the edges when blurred. |
*   Cursors View has a new **View RGBA** control which affects Display View and Cuts View:

    | View RGBA                       | Behaviour                                                                                                                                                                    |
    | ------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
    | RGB (composited on black)       | <p>Treats the alpha channel of the image as opacity and composites the image onto black<br>This is equivalent to rendering a premultiplied image</p>                         |
    | RGB (composted on chequerboard) | Treats the alpha channel of the image as opacity and composites the image onto a chequerboard.                                                                               |
    | RGB (ignoring alpha)            | <p>Matches Baselight 5, ignoring the alpha channel<br>Can be misleading because it shows colour in areas that are entirely transparent (where alpha is zero or negative)</p> |

    The default View RGBA behaviour can be set in Preferences under Display/Appearance. Bug 62992

    The **View Channel** control now includes Alpha. The keyboard and desk shortcuts for View Channel have been updated accordingly. Bug 63337
*   Added new options for handling single-channel media, using a new **Treat Single Channel As** setting which replaces the **Stack RGBA** setting when the Sequence uses single-channel media or has a single channel selected.

    | Treat Single Channel As | Behaviour                                                                                                                                                                                                               |
    | ----------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
    | Matte                   | Keep media as single channel, which will be treated as a linear matte.                                                                                                                                                  |
    | Monochrome RGB          | <p>Copy single channel to R,G,B channels to make a monochrome image in the Input Colour Space.<br>Spatial operators like Transform and Blur will treat the image as having hard edges with no transparency outside.</p> |
    | Monochrome RGBA         | <p>Copy single channel to R,G,B channels to make a monochrome image in the Input Colour Space.<br>Spatial operators like Transform and Blur will treat the image as being transparent outside its edges.</p>            |
    | Alpha                   | Copy single channel to A channel of a 100-nits white image in the Input Colour Space.                                                                                                                                   |

    For the two Monochrome options, if 1.0 in the Input Colour Space is brighter than 100 nits, a warning is shown because the resulting RGB/RGBA image may be unacceptably bright. Bug 63002
* Render View now shows a **Channels and Alpha** option when rendering to a file format or codec which supports four-channel output (RGBA or Y'CbCrA). File types which only support straight (unpremultiplied) RGB do not permit rendering with premultiplied RGB and vice versa. Bug 62992
* Scene Settings View now has RGBA options in **Display And Timeline Cache**. These allow alpha channel values to be seen when clicking on the image in Display View, but will increase the disk space needed for cache files and could impact performance. Bug 54001
* Scene Settings View also now has a **Strip Caching** option to choose between RGBA and RGB. Caching as RGBA will maintain alpha information, but will increase the disk space needed for cache files and could impact performance. Caching as RGB will cause the output of each cached strip to be made opaque, discarding any alpha information. Bug 60717
*   The Layer UI's "Layer Mode" menu has been streamlined. Selecting a composite mode will now simply composite the foreground image over the background using the alpha channel from the foreground.

    If the foreground doesn't have valid alpha, an area of the foreground image can be isolated by adding any of the matte operators (Shape, DKey etc) to a composite layer (using the standard desk, keyboard or UI buttons/accelerators). Bug 63014
* A layer with a matte can now be set to **Combine Matte With Alpha**, which uses the matte to modify the alpha channel of the input image (before it passes through the operators in the layer). Bug 60900
* Added "Initialise Composite Foregrounds To RGBA" option to the layer "Customise" menu (and the general "Insert" menu). If enabled, when a layer is switched to composite mode, the/any foreground sequence will have its "Stack RGBA" mode automatically switched to "RGBA" (avoiding the need to do so manually when creating a picture in picture effect, for example). Bug 63987
*   The Blend operator has five new modes which use alpha data to combine foreground (FG) and background (BG) images:

    | Blend Mode | Output                                                                                                 |
    | ---------- | ------------------------------------------------------------------------------------------------------ |
    | Over       | Standard composite: FG where FG is opaque and revealing more of BG as FG alpha decreases               |
    | In         | FG colour where both FG and BG alpha are opaque                                                        |
    | Out        | FG colour where FG is opaque but BG is transparent                                                     |
    | Atop       | Similar to Over but retains the opacity of the BG image                                                |
    | Xor        | Transparent where either FG or BG is opaque, FG where BG is transparent and BG where FG is transparent |

    These modes are also available in layers for Result Blending and Composite Settings. Bug 60776
* The new **Alpha From Matte** operator allows an image to have its alpha channel modified by a matte, for example a Shape or a key. Bug 61393
* The Edge Crop operator's Crop Colour option now offers **Transparent** to make the area outside the visible image transparent. Bug 62885
* The Blank operator now has an Alpha parameter. Bug 53221
* The Shuffle operator now specifies what is shuffled into the output alpha channel. Bug 53220
* Many operators have been updated to handle images with transparency. To ensure that Baselight 5 scenes continue to render as they did, operators inserted in earlier versions will often behave differently from operators inserted in Baselight 6.0. Bug 62013
* The preview images in BLG files now contain alpha channels. Bug 63675
* The right-click menu for thumbnails in FLUX Manage View now allows RGBA images to be viewed composited on black or chequerboard. Bug 60569
* The Grid Warp operator now has a **Transparent Outside** option. Bug 63026
* The Lens Correction operator now has a **Transparent Outside** option. Bug 62014

#### RIFE ML Retime

*   An improved Retime sampling mode **RIFE ML Retime** is now available.

    Real-Time Intermediate Flow Estimation for video frame interpolation (RIFE ML Retime) uses a Flexi effect to run the machine learning algorithm. This effect will need to be installed on the system using the filmlight-flexi-effects installer, which is available in the support section of the FilmLight website.

    Similar to the Optical Flow sampling mode, RIFE ML Retime has a quality setting 'Medium', 'High', 'Best'.

    RIFE ML Retime will always be using **Process in Working Format**.

    RIFE ML Retime does not currently run on Intel macOS systems. Bug 57701

#### Operator Presets

*   Operator presets provide a quick and easy way of storing operators as presets. The Presets View is accessed using the **P** icon in the Parameters View (just to the left of the **3D** icon). In this view, you see thumbnails for the presets defined for the current operator; double clicking on a preset or pressing **Apply** will replace the current operator with the selected preset.

    Note that a preset stores the entire operator, including keyframes (but excluding trackers). Applying a preset will remove any keyframes in the current operator and replace them with any that are stored in the preset.

    You can leave the Presets View by clicking the **P** icon again or by pressing the backwards triangle button at the left of the preset toolbar.

    You can also toggle the Presets View using the hotkey `Win+P` (`Ctrl+P` on Mac) and there is also a Blackboard/Slate shortcut (`Ctrl+DBS Try` by default).

    The **Create** button stores a copy of the current operator as a preset (after asking for desired name and optional comment). Presets are stored with keyframes but trackers are removed.
*   **Preset Storage Hierarchy and Locations**

    There is a hierarchical structure for Preset storage with the following levels:

    * Factory presets that ship with the product and cannot be altered.
    * Site level presets accessible by everyone on site
    * Job level presets accessible to everyone working on a particular job.
    * Scene level presets local to the current scene.
    * User level presets that are specific to a particular user.

    Factory presets are stored in a private read-only database.\
    Job and Scene presets are stored in the appropriate Baselight scene/job.\
    The Site and User presets are stored in special scenes whose locations are defined in the preferences (under **System > Database**).

    You will generally want to point these to the same location on a central database host so they are accessible from all machines.

    In the Presets View, there is a dropdown (that by default will be showing **User**) showing the current storage level - this determines where newly created presets will be stored.

    By default presets in 'higher' storage levels than the current level are also displayed but you can control this using the **Include Presets Above** toggle. Similarly, if you have two presets of the same name (e.g. a Site level preset and a Job level preset both called "Banana"), you can choose whether the 'lower' item hides the 'higher' one or whether both are displayed with the **Hide Overridden Presets** toggle.

    At the right hand side of the Presets View is another dropdown (by default showing **View Selected**) to control whether the thumbnails show the result of the preset on the entire stack, or only the output from the current operator.

    The cog menu at the far right allows moving and copying Presets between storage levels, and also has a toggle **Close on Apply** to control whether applying a preset should automatically turn off the Presets View.
*   **Old Operator Presets**

    We are now deprecating the old operator preset mechanism. You will only be able to use the old mechanism to access existing legacy presets and we recommend you save them using the new mechanism and then remove the old presets.

#### Flare

*   Flare is a tool for adding lens flares to scenes by creating a list of stages that can be combined to produce convincing flare effects.

    Flare is colour space aware and operates in an internal colour space chosen so that the Red and Blue components correspond better with the perceived end colours of the typical spectrum.

    To build a flare, **stages** are stacked on top of each other.
*   **Stages**

    The different stages are managed using the **Stages** area on the right side of the UI. Adding new stages, duplicating and deleting them are accessed by a context menu (brought up by right-clicking in the stages area). In Flare, this area also supports multiple selection of stages.

    There are eleven different stage types; each type can be added more than once. Nine of these can be thought of as Flare **elements** that simulate various phenomena caused by lens optics.

    However there are two important stage types that are used to organize and control the elements rather than directly defining an effect in their own right:

    **Group and Light Stages**

    * **Group**: This stage allows you to group flare elements hierarchically.\
      \
      This makes it easier to take effects that you've created (which may contain multiple elements) and control their appearance or package them as presets.\
      \
      Group controls affect all the elements in the group. There are two tabs:
      * **Basics**: Contains colour and brightness controls (applied multiplicatively) and a scale factor applied to the size of child elements.
      * **Axis**: sets the _axis_, which controls the position of rendered elements in combination with the lights. You do not have to define a group - elements not inside a group get a default axis at the center of the screen (that cannot be edited). Conceptually, you can think of the entire Flare effect being contained in a non-editable group.\
        \
        Notes: Moving elements in/out of groups is accomplished by moving them up and down. Moving an element directly below a stage up will move it into that stage. Moving the bottom element in a stage down will move it out of the stage.
    * **Light**: In Flare, elements are rendered in conjunction with lights.\
      \
      This is useful because you can drive a set of elements with multiple lights, for example a pair of car headlights, and you will automatically get two sets of matching flares that follow the lights realistically.\
      \
      In addition, the position where an element is rendered is calculated based on the position of the light and axis. In particular, in tools with a distance parameter, the effect is positioned on a line joining the light to the axis, (with distance = 0 meaning positioned at the light, and distance = 1 meaning positioned at the axis).\
      \
      Note: _Lights inside a group only affect elements inside that group, and only the elements below them, never above._\
      **It is important to realise that an element has no effect unless it is acted on by a light.**\
      \
      There are 3 tabs:
      * **Light**: Allows setting of the light colour, brightness and position. For matching the light position to a moving object, you have access to the Baselight tracker controls. This will allow you to track a moving light source in the image and apply the tracking information to the Light Stage. The available trackers are the 1 Point, 2 Point and Area trackers.
      * **Glare**: Use this to add a glare effect to the light - note that if this is not used, the light is not in itself visible (although it has a visible effect on flare elements).
      * **Animation**: This tab allows the light brightness to be automatically animated to produce a flickering light effect.

    **Flare Element Stages**: these are the tools simulating various flare phenomenon.

    * **Sun**: as the name suggests, this element simulates the glare provided by the Sun, but is also often useful to use in conjunction with the Starburst element in shots where bright artificial lights are in shot. Note: the **Glare** tab in the Light stage in fact just applies a **Sun** effect.
    * **Airy**: this tool replicates an Airy Disk - the diffraction pattern caused by light passing through a circular aperture.
    * **Rays**: this tool simulates Crepuscular Rays - the effect created when sunlight shines through openings (gaps in clouds, foliage or buildings) in a hazy atmosphere.\
      Note: because this effect works best when the effect center is a long way off screen, the **Distance** and **Direction** parameters allow for adjusting the position of the source without actually needing on screen interaction.
    * **Lens Ghosts**: this tool simulates the multiple 'ghost' images of the lens iris caused by reflections in the optics. There are 3 tabs:
      * **Basics**: allows control of the basic appearance and positioning of the ghosts.
      * **Exit Aperture**: simulates the occlusion of parts of the reflection by the final lens aperture.\
        Note that the R, G, B parameters in this tab control the way the occlusion is applied to the RGB channels - they do not represent an RGB colour.
      * **Randomness**: allows control over how much random variation is applied. For example, setting the Distance here to 0 will cause the ghosts to be spaced equally, rather than randomly.\
        The Noise settings add some random noise to the effect as typically seen in real life ghosts.
    * **Starburst**: this tool simulates the diffraction effect caused by the lens iris, causing a 'Star' pattern. There are 2 tabs:
      * **Basics**: contains the tools you will most commonly want to adjust.\
        \
        The **Blades** parameter controls the number of blades (sides) in the iris being simulated, and therefore the number of points in the star pattern. Note that Baselight simulates a real iris and so an odd number of blades actually produces two sets of points with one set at a reduced amplitude. This amplitude is controlled by the **Secondary** parameter.\

      * **Advanced**: contains less frequently used parameters.\
        \
        **Blade Stretch** and **Dir Stretch** are used for making anamorphic star patterns. **Blade Stretch** adjusts the length of blades without changing their direction, while **Dir Stretch** stretches the actual directions of the blades.\
        \
        Under the **Randomness** heading, **Angle** and **Size** allow some random variation in the size and direction of the blades. **Noise** and **Noise Frequency** can be used to add some random noise to the shading of the blades.
    * **Chroma Flare**: this tool can be used for creating rainbow like effects.\
      Two parameters may need explanation:\
      \
      **Filaments** control how much the effect looks solid as opposed to made up from filaments.\
      \
      **Spread** controls how much the 3 colour components are spread out.\

    * **Anamorphic**: this tool can be used for simulating the elongated flares typically associated with anamorphic lenses. There are 3 tabs:
      * **Basics**: contains the basic appearance and position of the flare.\
        \
        The **Offset** parameters are provided to easily offset the effect relative to the light position.\
        \
        **Size** defines the overall size of the flare, **Falloff** how quickly it falls off in the anamorphic direction. The smaller the falloff, the more stretched out the flare is.
      * **Core**: this allows adding a "central core" flare with a different shape and brightness.
      * **Sidebands**: This allows easy creation of smaller 'sideband' flares that echo the central flare.
    * **Light Leak**: this tool produces a simple light leak effect. It is essentially a radial gradient effect modulated by noise.\
      \
      The colour gradient is defined by the 3 colours **Center**, **Middle**, **Outer**, with the **Midpoint** parameter defining where the middle colour lies in the gradient.\
      \
      **Size** determines the overall size of the effect, while **Scale** controls the scaling of the noise pattern.\
      \
      **Threshold** controls the point at which the noise function fully modulates the Gradient effect.\
      \
      **Detail** controls the way multiple levels of detail are combined in the noise function - increasing detail changes the effect from being fairly smooth to a much more fractal like noise.
    * **Confetti**: this tool provides a way of quickly adding a large number of randomly positioned lens ghosts. While many uses will be somewhat frivoulous, it can also be useful for simulating dust on the camera lens. There are two tabs:
      * **Appearance**: controls relating the the basic appearance of each ghost element.\
        These controls parallel the controls of the same name in the **Lens Ghosts** tool.
      * **Duplication**: controls affect the way the ghosts are randomly duplicated.\
        \
        **Count**, **Size** and **Concentration** control the number of ghosts, the size of the area in which they are duplicated, and how much the ghosts are concentrated in the center of that area.\
        \
        **Distance** controls the positioning of the generation area.\
        \
        **Brightness** and **Size** (under the **Randomness** heading) control the random variation of element brightness and size.

    **Some General Notes on Using Flare Efficiently**

    * **Colour**:
      * While Flare has a custom internal colourspace, user colours are defined in Rec.2020.
      * All Stages allow you to define a colour for that Stage. The Group, Light and Element colours interact _multiplicatively_. For this reason, choosing strong colours for Group or Light stages may have unexpected consequences (e.g. a pure red light combined with a pure blue element will not have any effect).
      * Right-clicking on a colour well in Flare will provide an extensive set of preset palette colours to choose from as a starting point
    * **General**
      * Realistic flares will usually be subtle, however the default stage settings are purposely set to be easily visible when first applied, use the brightness setting in the stage to change how the flare sits in the image.
      * Although the Group stage allows you to shift the axis, the default setting will generally provide the most realistic movement of elements relative to the lights.
      * You can use multiple stages to construct more complex flares; save these as presets that can be used to build new flares (in Presets View you can use the Append option to add the preset to your current Flare instead of replacing it). Bug 54453

#### Halation

* Halation simulates light scattering in a film camera. It adds a coloured halo around the highlights. Bug 62840

#### Sharpen Luma Operator

* The new Sharpen Luma operator is similar to Sharpen but is colour space aware and its sharpening is based on the luminance channel. In addition, there are controls that limit sharpening:
  * **Shadow Threshold**: controls the sharpening of darker tones
  * **Contrast Threshold**: controls the sharpening of high contrast areas in order to reduce ringing
  * **Noise Threshold** controls the sharpening of low contrast areas to reduce noise and compression artefacts. Bug 52969

#### Boost Detail Operator

*   The new Boost Detail operator boosts local detail. Smaller detail is boosted more than larger detail. **Gain** sets how much boost, **Scale** sets an upper limit on the detail size to be boosted, and **Threshold** sets a contrast limit, so we can make images look crisper, but not introduce noise into skies and other flat areas.

    The sum of all the boosted details at the different scales may go outside the normal image range. **Shadow Threshold** fixes negative values using a smooth tone curve for image values either side of zero, with a range of **Shadow Threshold** \* **Gain**. If the range is zero or less it gives a hard clip at zero. Bug 56701

#### Bokeh

* Bokeh simulates an aperture-like defocus effect by convolving the linear image with a shape. The most important parameter is **Radius**, which sets the maximum bokeh radius as a fraction of the image height.
*   **Depth Matte**

    The radius of the bokeh effect at each pixel can be controlled by using a **Depth Matte**, where values between 0 and 1 define the depth of each pixel. A depth matte can be as simple as a Shape or as complex as a machine-learning-derived per-pixel depth map. Once the Bokeh operator has been provided with a depth matte, the following parameters control its behaviour:

    * **Depth Mode**: Determines how the 0-1 values of the depth matte are interpreted. There are four possible values:
      * **Ignore**: There is a depth map but it is ignored. The whole image gets the maximum bokeh size. This allows the effect of the depth matte to be assessed without needing to change the stack structure.
      * **Far: 0**: Z (pixel depth) is the depth matte value. This is used for artificial depth mattes where the value goes from 0 (far) to 1 (near).
      * **Far: 1**: Z is 1 - the depth matte value. This is used for artificial depth mattes where the value goes from 0 (near) to 1 (far).
      * **Far: infinity**: Z is 1.0 / the depth matte value. Map values go from 1.0 to infinity. 1.0 is the aperture. Values less than 1.0 are clipped. This is often used with actual depth data.
    * **Focus**: The point within the 0-1 depth matte range which is in focus. When using a depth matte, the bokeh size varies with the difference between the Focus and the depth Z calculated from the depth matte value. If Z matches Focus then the bokeh size is zero, and the output is sharp. It is also possible to set the focus by simply clicking on the image.
    * **Depth**: The depth of focus around the focus point. Smaller values will result in the bokeh size increasing more quickly as the depth value moves away from the focus point.
    * **Lock Focus Pick**: When turned on, clicking on the image no longer sets the focus point.
    * **Foreground Blur**: Used in situations where there are pixels whose depth is in front of the focus point. When enabled, these foreground pixels are grown, allowing for a softer, more realistic edge. Required because we don't have access to the occluded pixels which are needed to achieve a physically realistic foreground blur.
*   **Bokeh Shape**

    The shape with which the image is convolved is controlled by the **Bokeh Shape** section:

    * **Shape**: Sets the bokeh shape, with the following behaviour:
      * 0.0 gives a circle.
      * 1.0 gives a straight-sided polygon.
      * Between 0.0 and 1.0 gives a convex polygon.
      * Beyond 1.0 gives a concave polygon, and then finally a star.
    * **Sides**: For Shape values above 0.0, gives the number of sides of the polygon or points in the star.
    * **Angle**: Used to rotate the polyon/star.
    * **Anamorphic**: Used to squash the bokeh shape, simulating an anamorphic lens.
*   **Advanced Parameters**

    Some more advanced settings are included to aid in tweak the Bokeh appearance for a given shot:

    * **Max Radius**: A setting which trades bokeh quality for processing speed. Below this radius, the bokeh is calculated at a lower resolution and then upscaled.
    * **Depth Threshold**: Threshold which allows the size of the in-focus area around the focus point to be increased a little, reducing artefacts when using noisy depth maps.
    * **Foreground Edge**: If **Foreground Blur** is turned on, this control specifics how large the soft edge of the foreground object is.

#### Curve Grade Operator

*   The Curve Grade operator has been completely reworked. It now includes enhanced colour space aware curve processing that provides accurate, floating-point, HDR-ready grading.

    The user interface has also been overhauled with new layout options, curve histograms, improved trackball support etc. Bug 50691
*   Curve Grade's "Control Point Per Trackball" mode has been substantially improved. These improvements include better behaviour when editing multiple control points simultaneously, automatic graph control point selection on undo/redo etc.

    Tangent Tk panels also now support the following button mappings:

    | Button                    | Behaviour                                                   |
    | ------------------------- | ----------------------------------------------------------- |
    | `A`                       | 'Control' modifier                                          |
    | `B`                       | 'Shift' modifier                                            |
    | Trackball reset 1         | Reset/add default control point                             |
    | Trackball reset 2         | Toggle add/remove trackball control point to/from selection |
    | `A` + Trackball reset 1/2 | Assign previous/next control point to trackball             |
    | `B` + Trackball reset 1   | Delete trackball control point.                             |

    Bug 50722

#### Hue Angle Keyer

*   The Hue Angle keyer has been upgraded to use a new, perceptually-uniform colour space that provides more consistent, accurate keys. The user interface has also been substantially improved and now includes:

    * Interactive channel bars with integrated histograms (and a colour wheel vectorscope).
    * Improved presets that provide tighter keys by default.
    * Improved initial rolloff settings when picking on the image.
    * The new **Pick Rolloff Behaviour** option (available from the customise menu) to expand the rolloffs to cover the entire range when picking, resulting in an initially 'soft' key. The rolloffs can then be refined/tightened using the (new) shift+click/drag image interaction that subtracts the region selected from the current rolloff settings.

    There is also an **Expand Rolloffs** button which immediately expands the rolloffs (regardless of the default mode).

    Note: To grow the key to include additional colours, use `Ctrl+click/drag` (`Cmd+click/drag` on Mac) on the image. Bug 47062

#### Paint

* The Paint operator now takes advantage of alpha to produce an RGBA image. It has a **Transparent Background** toggle to either output the paint strokes composited over the input or on their own over a transparent background.
* The new **Composite Paint Strokes Separately** button will split the Paint layer into its constituent elements, with the strokes rendered onto a transparent background and composited separately with the input image. This enables the use of any grading operator to modify the paint strokes before they are composited. Bug 48372

#### Text

* The Text operator now has an **RGBA** option which produces an RGBA image which can be composited separately. The **Composite** option renders the text directly onto the input image. The **Matte** option produces a matte image which can be used for compositing. Bug 50774

#### Updated Gallery View

* Some the Shots View functionality has now been integrated into Galleries, allowing them to be sorted, searched and filtered.
* Additional metadata is now captured at grab time:
  * Shots View Metadata
  * Grab Date and Time
  * Grab User
  * Grab Source
  * Grabbed Record Timecode
* Sorting is available via the **Sort** menu within Gallery View and contains the following options:
  * Storyboard - this matches the behaviour of previous versions of Baselight, allowing gallery grabs to be reordered by drag-and-drop.
  * Tape + Source TC (C Mode) sort
  * Sort by any available metadata
  * Change sort order
  * Apply a secondary sort
* Galleries can be searched using a new **Search** button within Gallery View which displays a text edit field for searching the current Gallery. By default this searches within comment, but it can be changed to search within tape or clip names.
* Users can now create and store complex filters that persist between Galleries and are available via a drop-down menu. By default this menu contains the option to display all shots, or Gallery Quick Slots as well as options to create, edit, or remove filters. Choosing to create a new filter shows a modal dialog where filters are defined in the same manner as Shots View. The dialog requires a filter name that will be added to the list of filters. Available filters can be cycled using the '+' and '-' keys on a Blackboard or Slate in Gallery keypad mode.
* Galleries can now be viewed as a list like in Shots View, with columns displaying all available metadata.
* Galleries now display a scroll bar as well as information on how many events are currently shown.
* Added ability to export BLGs or CDLs directly from the current Gallery Scene. Bug 51442
* Control-clicking a Gallery thumbnail will now jump to the grabbed record timecode in the current scene. The modifier for this can be changed via the 'Navigation' submenu. Jumping to the grabbed record timecode can also be achieved by right-clicking a Gallery thumbnail.
* Added 'View', 'Gallery', and 'Recall' as available default keypad modes for the Blackboard or Slate.
* Grabbing multiple shots to the Gallery can now be cancelled.
* Grabbing multiple shots to the Gallery can now be undone in one go. Bug 62925

#### Multi-Paste

* Multi-Paste supports shots which span multiple timeline tracks. When multi-pasting, the new **Maintain Tracks** option determines whether the tracks of source shot strips are maintained in the destination or whether they are pasted into the destination top strip's track. Bug 53121
* When multi-pasting from multiple scenes, Multi-Paste will now stop with a more informative error message if any of the source scenes can't be opened (previously it would simply skip over unopenable scenes). Bug 66110

#### Colour Science

*   **Truelight CAM v3**

    Added a new version of Truelight CAM DRT family, called "Truelight CAM v3". This makes the first two versions of Truelight CAM obsolete.

    Changes since Truelight CAM v2:

    * Better shadows details
    * Highlight bleach is less intense
    * Highlights between SDR and HDR look more similar
    * Improved inverse transform
    * The ARRI, Academy and RED scene looks have been modified to work with Truelight CAM v3. The matching target for these new scene looks is between SDR and HDR at 200 nits - this produces a more balanced match between SDR and HDR. Bug 59379
* Added ARRI-2022 scene look (based on ARRI REVEAL DRT) for Truelight CAM v3. The matching target for the new scene looks is between SDR and HDR at 200 nits, this produces a more balanced match between SDR and HDR. Bug 63398
*   **Chromatic Adaptation Transforms**

    A Chromatic Adaptation Transform (CAT) is used when converting images between colour spaces. It converts the white point of one colour space to another, e.g, from D65 to D60.

    In Baselight 5.3, a fixed CAT was used (XYZ Scaling), but workflows like ACES specify different CATs which produce slightly different colours; the resulting errors are small but could flag issues in QC.

    In Baselight 6.0, a new Chromatic Adaptation Transform option (in the advanced section of the Format & Colour tab on Scene Settings View) allows the CAT to be set for all colour space conversions in the scene (except the mastering white point shift, see below).

    The CAT options are:

    * ACES Workflow (Dynamic)
    * Bradford
    * CIECAT02
    * von Kries
    * XYZ (Legacy)

    Bradford, CIECAT02, von Kries and XYZ describe the colour space used for the chromatic adaptation. The ACES Workflow setting dynamically switches between Bradford and CIECAT02 depending on the colour spaces being converted, to match the ACES specification.

    The CAT used for each conversion is shown in Colour Space Journey View.

    For the Mastering White Point colour shift, Baselight uses a different CAT, scaling in the Mastering Colour Space, to prevent colours from being moved out of the mastering gamut by a white point shift. Bug 56121
*   **New Colour Spaces**

    Added "FilmLight: Linear / EGamut 2" and "FilmLight: TLog / EGamut 2" colour spaces. EGamut 2 is changed slightly to include modern camera colour spaces. There is no noticeable difference from a colour grading perspective. Bug 66101
* Added "Apple: Apple Log / Rec.2020" colour space. Bug 65637

#### Dolby Vision

*   Dolby Vision Content Mapping v5.2 features are now supported in scenes using "Internal CMU (v4)" content mapping.

    **Analysis Tuning**

    In the Dolby Vision section in Scene Settings View, the **Analysis Tuning** control adjusts the spatial filtering used by Dolby Vision analysis. This can be used to reduce the impact of specular highlights, noise, compression and digital artifacts. Note that this control only affects subsequent analysis operations; it has no effect on analysis that has already been performed.

    **Long Play Analysis Usage**

    In Dolby Vision Analysis operators which have been analysed in a Baselight release supporting this functionality, the **Analysis Usage Mode** control can be set to **Long Play** to allow the image analysis values to vary across the duration of the operator. This can give better results when a single shot has a large change in lighting, or when using a single Dolby Vision Analysis strip under multiple shots. Bug 64588
* Colour space menus now show Dolby's names for Dolby Vision mastering and target displays, rather than the names of the corresponding colour spaces. Bug 65979

#### Contrast-aware Image Transform Settings

* When HDR images with sharp features are resized in a linear colour space, artefacts can result in several of the image transform modes. A new **Linearised (contrast-aware)** Colour Treatment option reveals a **Local Contrast Damping** slider that reduces or removes these artefacts. This option is shown on Scene Settings View, the Image Transform Settings operator and the Setups editor. Bug 43838

#### 'Explicit Strip' Reference Strip Mode

* Added a new mode for selecting an explicit, upstream strip in the stack to reference. Once enabled, the 'Pick Strip' button allows picking of a strip to use/reference directly from the timeline (strips unavailable to reference from the Reference strip will be greyed out). Bug 51119

#### Loupe Tool

* The Loupe Tool provides a convenient means of zooming in for fine control when doing precision operations such as editing shapes. Dragging with the loupe is 'geared' to make it easier to make precise adjustments. Bug 51930
* The loupe is activated/deactivated with the keyboard shortcut `Win+Esc` (`Control+Esc` on Mac) while the mouse is the image window; certain tools have an "Auto Loupe" button to allow the loupe to turn on automatically for that tool.
* The level of zoom can be adjusted with the mouse scroll wheel.
* Loupe settings are accessible from the Display menu. **Centred** means that the loupe will be centred over your mouse, whereas **Offset** means the loupe will be offset so that it doesn't overlap with the mouse position.
* The Loupe is currently only available with the 1x1 Layout; this limitation will be removed in a future release.

#### SDK Updates

* Added support for reading Nikon RAW (.NEV) media. Bug 60943
* Updated to Sony SMDK Toolkit version 4.23. Bug 64622
* Updated to Canon RAW SDK 2.8. This adds support for newer cameras, and now uses CUDA on Linux and Metal on macOS for increased performance. Bug 61196
* Updated to Blackmagic RAW SDK 3.5. This adds support for media from:
  * Blackmagic Cinema Camera 6K, URSA Mini Pro 12K OLPF and Micro Studio Camera 4K G2
  * Fujifilm X-H2, X-T5, X-S20 and GFX100 II
  * Panasonic LUMIX S5II, S5IIX and GH6
  * ZCam E2, E2-M4, E2-S6, and E2-F6. Bug 63775
* Updated the Comprimato SDK used for GPU JPEG 2000 acceleration to version 2.8.1. This adds support for NVIDIA Ada GPUs. Bug 65980
* The old v5 ARRIRAW decoding SDK is no longer available except for very old media and media inserted in older builds. Note that the v5 SDK remains unavailable on Apple Silicon systems. Bug 66334
* Updated to DNx SDK 2.7.5. This fixes some internal behaviours. Bug 66465

#### Volume Indexing

*   In Baselight 6.0 and future releases, volume indexing is out of beta and is automatically enabled on Linux Baselight systems.

    "Indexing" is the action of reading and storing the metadata for a volume.

    The index service will automatically extract metadata from the movies and sequences on the local '/vol/images' volume and store them in a PostgreSQL database.

    The database is kept up to date to match the contents of the volume.

    This can improve the speed of existing operations, such as conform or browsing for media, and it can enable otherwise impractical operations such as finding all media of a particular encoding, or by a particular director, or over a certain length etc.

    The first time that the index service starts after installation it will run in the background and take some time to fully populate the index database with the metadata of the volume contents.

    When a volume index is available it will be visible in FLUX Manage, indicated by a white star next to the volume selector.

    A white star indicates an index is available and being used, whereas an orange outline indicates an index is available but not being used, either because the user has chosen not to use it, or because it is not fully available due to indexing not being complete.

    In FLUX Manage and Conform View, clicking on the star icon next to the path in the interface will allow selective use of the index. Disabling the index allows the user to read metadata directly from the raw media.
*   **Examining a Volume Index Using the Command Line**

    To check the status of volume indexes use the `fl-lsvol` command - this will display all available volumes and indicate if an index is available on a volume, as well as the status of the index.

    ```
    > fl-lsvol
    /vol/bl1234-images
    /vol/bl1119-images    [Indexed]
    ```

    From the command line, the `fsdb-ls` command is a useful tool to list the contents of directories. If an index is configured `fsdb-ls` will automatically use it.

    However, should you wish to ignore the index and scan the filesystem directly, you can override this behaviour using the 'server' option:

    ```
    > fsdb-ls --server <indexed|regular>
    ```

    For example to summarise all sequences using the index:

    ```
    > fsdb-ls -R --server indexed /vol/images
    ```

    To summarise all sequences by not using the index (i.e by scanning the filesystem - this will take a **lot** longer):

    ```
    > fsdb-ls -R --server regular /vol/images
    ```

    The `fl-lsvol` command will also show an indicator of the current state of the index:

    ```
    > fl-lsvol
    /vol/ghibli-images  "QC - Ghibli Baselight TWO"  [Indexed]
    ```

    Further information is available in the User Guide.
*   **Disabling the index service**

    In previous releases, the index service needed to be explicitly enabled for a volume. In Baselight 6.0 and future releases it is automatically enabled. It can however be explicitly disabled if required.

    This requires an additional 'limit' line in the configuration file 'volume.conf' like so:

    ```
    zone mybaselight
    dir images /mnt/disk1/images1
    label images "Demo Room"
    limit images index=0
    ```

    The service will need to be restarted to accept this change.

    If your system is a Baselight TWO, login to the master node, e.g.:

    ```
    > ssh filmlight@n0
    > sudo fl-service restart index
    ```

#### Miscellaneous

* Added support for macOS 14 Sonoma; the minimum supported version is now macOS 12 Monterey. Bug 65665
* Operator image overlays now update/draw in sync with the images themselves when scrubbing through the timeline. Bug 61376
* Added ACES Reference Gamut Compression to the Compress Gamut operator. Compress Gamut now has three operation types: FilmLight, ACES Reference and ACES Variable. Bug 58234
* Added support for a new "ab" chromaticity mode in Scope - Vectorscope/Chromaticity View. This new method will plot the image point cloud and all loci in the chroma plane of Eab - a new opponent colour space developed by FilmLight. Eab will present colour distances in a perceptually uniform way (large-step colour uniformity) in all areas of the colour space. Because of this perceptual uniformity, RGB gamuts are no longer triangle shaped. Bug 58292
* Legacy DNxHD codecs are now hidden in Render View Codec menu unless `Shift` is pressed. Bug 60557
* The Radius sliders in the Blur operator and in the Blur and In/Out Blur stages of the Matte Tool operator are now non-linear. This makes it easier to set smaller radii using the sliders. Bug 35919
* Mute Audio keyboard shortcut has been changed from `Control+Shift+M` to `Alt+M` to prevent overlaps with Mark insertion keybindings when Edit Mode is on. Bug 64008
* Added an option to set the Blank colour to black, 18% grey and white based on the colour space set in the operator. Bug 63951
* CLF files that use the "ACES2065-1" colour space now correctly set the ACES: Linear / AP0 colour space into a LUT operator. Bug 64412
* Added FLUX Manage filter tile for "Is RGBA" to select media that has 4 channels. Bug 64526
* When inserted, the Blank operator now generates black in the working colour space. Bug 64080
* OFX plugins must now use the new Draw Suite for drawing overlays. Bug 62260
* Viewing or scrubbing a thumbnail in the gallery will now always use the viewing colour space from the current cursor. Bug 62759
* Added icon to shot strips to indicate they contain client notes (and changed frame client note markers to use the same icon). \[Bug 62278]
* Added a horizontal cursor line displayed at the bottom of thumbnails in Cuts View. Bug 53689
* The keyboard accelerator for increase/lower proxy resolution is now `Shift+Ctrl/Cmd+Minus/Equals`, allowing the simpler `Ctrl/Cmd+Minus/Equals` to be used for Timeline Zoom In/Out. Bug 65149
* Scene Settings now has an option to clamp images to \[0,1] before applying an inverse DRT. This can fix issues with display-referred media, for example caused by unpremultiply or Legal to Full scaling. A new option on the Sequence operator allows separate control of clamping when a DRT override is chosen. Bug 63701 Bug 66259
* Added category selection to the 'Prompt For Note And Category' dialog when adding Marks. Bug 59360
* Added `Win+Shift+M` (`Control+Shift+M` on Mac) keyboard shortcut to show/hide Marks And Client Events view. Bug 59360
* The "Zones" diagnostic now checks whether every system in the cloud has the same setting for its global preferences database, and that the 'filmlight' user has the same UID. Bug 65471
* Added a help window for Numbering Expressions in Render View. Bug 65498
* Submitting a render to a remote system now warns if there is nothing running on that system which will process the render (i.e. Baselight/Daylight/bl-render or, on a FLUX Store or Baselight RENDER system, the render service). Bug 65311
* Added tooltips to help buttons in Render View. Bug 65589
* Blend strips and Layer strips in composite mode now show the blend mode in the strip name. Bug 64457
* Added 180 degree Lat-Long support to the Panorama operator. Bug 65552
* In the Panorama operator's "Camera Control" mode, `Alt`+left mouse button can now used to pan the image, whilst `Ctrl+Alt`+left mouse (`Cmd+Alt`+left mouse on Mac) can be used to change the field of view. Bug 65552
* On macOS, several utility applications are now located in Utilities/Tools rather than alongside the Baselight application itself. Bug 61795
* In order to prevent accidental reduction of image quality due to upscaling, strip caching is now ignored when the Viewing Format or Rendering Format has a mapping from the Working Format which causes a scale-up. When this is detected, strip caching is ignored, and the cache button at the top of Parameter View and the cache icons on Timeline View are shown in orange. This behaviour can be disabled in Scene Settings View if necessary. Bug 53184
* "Texture Filename" metadata is now shown for ARRIRAW media. Bug 66628
* An NVMe raid based on Xinnor xiRAID is now supported. Bug 66049
* Reduced coloured artefacts in highlights of DNG media sequences. A new Highlight Filtering control on the DNG Params operator allows this filtering to be adjusted. Bug 66149
* Added "FilmLight: Linear / EGamut 2" and "FilmLight: TLog / EGamut 2" colour spaces. EGamut 2 is changed slightly to include modern camera colour spaces. There is no noticeable difference from a colour grading perspective. Bug 66101
* Added support for subrip (.srt) and Avid subcap (.txt) subtitle formats. Bug 62374
* Improved conversion from subtitle timecode to corresponding frame number. Bug 66729
* Gallery scene names now always have a suffix representing their version number (e.g. "\_v6") added to the end of the name. When a version 6.0 gallery scene was created by automatically copying a gallery scene from an earlier version of Baselight, that original gallery will remain, allowing easy switching between Baselight builds with different version numbers. Bug 66767
* OpenEXR renders from RED media now include `lens_cooke_i_dynamic` and `lens_cooke_i_static` metadata. Bug 66773
* Added support to conform using clip name in a CMX EDL, the EDL must contain `* FROM CLIP NAME:` or `*FROM CLIP NAME:` entries for events to enable the option in the Match Events By selection menu. Bug 64579
* The scene's working frame rate is now shown in the scene name drop-down menu. Bug 57284
* Apple ProRes and many other movie files are now read considerably faster than in previous builds. This can enable additional media to play at rate without caching. Bug 64439
* When conforming from the timeline add "Clip Name In Path Or Filename" to the Match Events By list if clip names are present. The `bl-conform --Filter` option now includes ClipName. Bug 57729
* Additional metadata is now read from PNG image files. Bug 65131
* Automatic white point adjustments made by Sequence operators when converting between the Input and Stack colour spaces are now shown on Colour Space Journey View. Bug 64683
* Added an option 'Apply Input Format Mapping' when conforming FCP/XMLs with Image Transforms. When set to yes, if the resolution and pixel aspect ratio of the working and input formats do not match, the transform is adjusted to compensate for the difference. Bug 64760
* Updated Photon to version 4.9.4. This can detect additional issues in rendered IMF packages. Bug 65555
* Added support for reading IPCM audio in QuickTime and MP4 files. Bug 65581
* Added command line tool for mapping the Blackboard Classic Wacom tablet. Bug 57119
* When performing an Update Avid AAF with Baselight grades a warning is now shown if no grades are exported. Bug 65686
* Added an option to export v5 Dolby Vision Metadata when rendering HDR IMF packages and Dolby Vision Mezzanine MXF files. Bug 60060
* Added `%u` or `%{ShotStartTimelineTimecode}` as a render filename template substitution which is the timeline (rec) timecode of the start of the current shot, as a number. Bug 65762
* The Working Format is now shown at the top of the list when creating a new format mapping. Bug 65896
* DRTs which are implemented using CLFs are now supported. Please contact `baselight-support@filmlight.ltd.uk` for more information. Bug 65098

### Bug Fixes Since Version 5

* Newly-inserted Blend operators using Linearised Colour Treatment now correctly use the colour space of their input, not the Working Colour Space. Bug 55995
* Fixed rare crash in Curve Grade where the working colourspace was indeterminate. Bug 56815
* Fixed issue preventing render of Dolby Atmos and Dolby Vision Mezzanine MXFs. This also fixes an issue where created movies could have the wrong permissions. Bug 64109
* Fixed rare crash with group grading inside a layer. Bug 64295
* Newly-inserted Blend operators using Linearised Colour Treatment now correctly use the colour space of their input, not the Working Colour Space. Bug 55995
* Fixed a potential scene loading error in DSpot and Switch Dust strips. Bug 64125
* Fixed crash pasting onto a Shader layer. Bug 64099
* Fixed crash on exit when cursor on image display. Bug 64030
* Fixed error messages for misconfigured Scratchpad. Bug 64131
* All strips with a missing reference input are now indicated by a red X on the strip. Bug 64600
* Fixed issue with pasting to a stack with protected mattes. Bug 63901
* Fixed an issue where applying a grade would sometimes shift strips upwards. Bug 63902
* Improved behaviour of sliders and desk controls in the (standalone) Blur and In/Out Blur tools. Bug 64628
* Improved trackball behaviour when adjusting parameters with non linear response curves. Bug 64679
* Viewing or scrubbing a thumbnail in the gallery will now always use the viewing colour space from the current cursor. Bug 62759
* Displaying a bypassed stack in Layer View no longer covers the scroll bar. Bug 64231
* Increased the size of the 'gang' icon and added a splitter bar to Hue Shift to separate Hue Controls from Saturation/Value controls. Bug 64229
* Fixed image issues seen with some Shader and OFX operators followed by a Transform. Bug 64386
* Fixed issue with Merge Apply with Protect Existing Destination Strips and Tracker strips causing a crash from overlapping strips. Bug 64505
* Improved trackball behaviour when adjusting parameters with non linear response curves. Bug 64679
* Fixed issue in Matte Tool where moving an encoder knob would enable the currently selected tool instead of the one linked to the encoder. Bug 64601
* Fixed sliders with non linear response curves not updating their position when extended range is toggled. Bug 64685
* Improved sensitivity of some controls in Matte Tool. Bug 64802
* Fixed crash when pressing Apply. Bug 64333
* Group grading now inserts strips in the correct track to maintain layer ordering. Bug 64672
* Improved mail queue diagnostic report for cases where there is exactly one mail message in the queue. Bug 64687
* Added reset buttons in the Blur and In/Out Blur tools. Bug 64716
* Fixed issue where renaming a stage in Matte Tool. Bug 64880
* Ensure 'New Shape' mode disabled/cancelled in a read only scene. Bug 64847
* Fixed bug where Matte Tool would not check for mismatched parameters
* before allowing its strips to be joined. Bug 64894
* Fixed a bug which could cause the keyframe bar to be empty for an operator containing keyframes. Bug 64843
* Fixed failure to render 8-bit Y'CbCrA images to JPEG 2000 Broadcast Contribution Profile YCC 422. Bug 65117
* Reduced fade in and fade out times of the Blackboard Classic. Bug 65356
* Ensure Avid (conform) categories are hidden on menus where appropriate. Bug 59360
* Fixed crash while tracking after switching scene. Bug 64864
* Added support for reading IRIDAS cubes written by the ARRI Reference Tool. Bug 66074
* Some dialogs which could become unusable if there were too many lines of text now use a scroll bar. Bug 65442
* Fixed non-standard positioning of reset and gang buttons in various tools including OFX, Matte Tool, and Blur. Bug 65449
* Made the bars between column headings more visible within tables and changed tables to always use horizontal scrolling when columns can be resized. Also fixed a regression causing column headers in the Manage Colour Spaces dialog to not be correctly aligned. Bug 65569
* Flipped bypass stripes in Layer View and Parameter View to match Timeline View's strip bypass. Bug 64557
* Fixed precision issues in the Timeline when fully zoomed-in and cursor was located several hours up the timeline. Bug 65726
* Fixed a hang caused by scrolling in Cuts View while editing the Comment (Editable) field of a thumbnail. Bug 64555
* Fixed clipped highlights in Cuts View when using BRAW media at a high ISO or exposure. Please use "bl-reset-cache -thumb" to remove incorrect thumbnails from the cache. Bug 65765
* Fixed inability to sort or reposition several columns in FLUX Manage View. Bug 65698
* When inserting the first Sequence into a scene from Conform or FLUX Manage, you are now prompted to change the scene's container and/or timeline timecode rate even when there are non-Sequence strips already in the scene. Bug 65755
* Added **Hue Safety** control in Curve Grade's customise menu for adjusting the built-in saturation modulation for adjustments based on hue. Bug 64626
* Fixed potential crash on scene close when Text operator selected. Bug 65605
* Fixed bug that prevented new layer insertion if a stack contained unresolved Reference strips. Bug 66056
* Added three additional buttons to the Tracker Desk Selection preference in Preferences -> Operators. This will allow users to map three additional trackers which will be accessible from the Blackboard/Slate. The old tracker controls will be visible on the panel when holding down Ctrl. Bug 65188
* Removed the option on macOS to use Apple ProRes compression with 10-bit Integer timeline caching. Bug 64264
* Fixed a rare issue whereby grabbing a composite grade to the Gallery could result in a render error if the media was taken offline. Bug 66063
* Fixed Multi-Paste bug which could occur when "Paste Groups" was on and the destination scene had no groups, resulting in one of the pasted groups occupying the "\\\<unsaved>" group slot and thus being liable to be overwritten. Bug 66116
* Fixed Multi-Paste bug which could occur when multiple source clips were judged as being equally likely to match a destination shot, resulting in the choice being essentially random and non-deterministic. Now, the source shot whose record time is closest to that of the destination shot is chosen. Bug 66125
* Fixed crash which could occur when closing the current scene whilst in the middle of a mouse-based editing operation. Fixed by blocking scene close in that situation. Bug 66177
* Fixed infinite scrolling which could occur when doing edit drags using the mouse on some Linux systems. This also fixed scrolling not being stopped appropriately early when scrolling to the left. Bug 65972
* Fixed scrolling in the timeline occurring when doing slip edits using the mouse. Bug 65972
* Fixed Timeline Sort to generate modern versions of Bars and Text. Bug 63936
* Fixed issue with cursor lag on SDI outputs. Bug 66241
* Fixed drag and drop from FLUX Manage to the Timeline View so that the drop zones always reflect the state of FLUX Manage's current insertion buttons. This allows it to offer "Replace", Audio and BLG insertion. Bug 63795
* Fixed an issue that caused a magenta image on the AJA Kona SDI or HDMI outputs when restarting Baselight, switching setups or running external tools such as bl-setups. Bug 66443
* Fixed crash when changing stream resolution in Client Sessions View. Bug 66170
* Fixed issues with data alignment when processing image files stored on an xfs disk with 4k logical sectors. Removed the FLIX\_AUTO\_FIX environment variable which is no longer required. Bug 4285
* Fixed missing UI in Dolby Vision Trim operator in Internal CMU (v2.9) mode. Bug 66488
* Tables now have a larger separation between columns and have better alignment. Also removed the 'Thumbnail' title text from Shots View and Gallery. Bug 65638
* Fixed background caching not triggering when changes to a strip's caching state were undone/redone. Bug 53320
* Fixed a diagnostic issue for Generation VIII systems that have a NVME boot disk. Bug 66529
* Added UI Saturation control in the Hue Angle Customise menu for adjusting the saturation of the wheel and histograms. Bug 66151
* Fixed a bug that could cause a crash exporting marks. Bug 66319
* Fixed an issue where Matte Tool panel interaction could become unresponsive when simultaneously adjusting encoders and trackballs. Bug 66360
* Fixed bug in Curve Grade where moving a single encoder quickly after another could result in 2 control points being edited simultaneously. Bug 66290
* Fixed issue with the Blackboard Classic not updating Shape Quickshape menu. Bug 65933
* Fixed potential crash when scrolling a long list by repeatedly clicking on a scrollbar. Bug 66491
* Fixed issue with keyboard focus in the Create and Edit Presets dialog. Bug 66397
* Improved conform of CMX EDLs with locator marks, allow case-insensitive colour names. Bug 66550
* Fixed memory leak when decoding ARRIRAW v7 images via CPU renderer. Bug 66420
* Fixed issue with over sensitive Wacom pen in FilmLightOS 8. Bug 66379
* Fixed crash that could occur from the Gallery when closing scenes. Bug 66499
* Fixed crash when movie decodes are continually failing. Bug 66566
* Fixed potential crash when deselecting a Curve Grade operator while simultaneously dragging a control point. Bug 20295
* Fixed crash which could sometimes occur when closing a scene whilst timeline scrolling is occurring. Bug 65663
* Fixed crash when attempting to modify some OFX parameters with explicit strip caching enabled. Bug 66600
* Fixed failure to generate FLUX Manage thumbnails for some DNxUncompressed media. Bug 66546
* Fixed crashes in Text Macros Panel. Bug 63190
* Fixed new-scene Timeline Caching setting, which has now moved from Preferences to Setups. Bug 65192
* Fixed audio error messages when using a frame increment of zero. Bug 60928
* Fixed crash in Client Sessions view when creating a new session without copying the existing stream settings to the new session. Bug 66132
* Fixed crash in Client Sessions view when creating a new session whilst an existing session is in progress. Bug 66000
* Fixed crash in Client Sessions view when the Stream Settings for a session have invalid values. Bug 64254
* The "Resend Invites" button in Client Sessions view is no longer displayed for local sessions. Bug 66160
* Fixed potential crash when removing a client from the Client Sessions View. Bug 66632
* Fixed an issue with zero-opacity shape matte. Bug 58022
* Fixed green value in chromaticities metadata when writing OpenEXR files using an EGamut colour space. Bug 65007
* Fixed a range of failures that could be caused by repeated application runs which never read any movie files, especially on a multi-GPU system. Bug 66629
* Fixed crash when resetting a Bars operator. Bug 66619
* Improved UI update speed when working with Dolby Vision. Bug 66681
* Prevented grabbing of stacks with (explicit) references to strips outside the stack to the gallery. Bug 64561
* Added a menu button to the layer list in Chromogen/Matte Tool (the older method of using right-click to bring up the menu still works as well). Bug 66620
* In Chromogen, Matte Tool and Flare, the Panel displays now show the user name for the stage rather than always showing the default stage name. Bug 66627
* Fixed an issue whereby the strip bypass button could be incorrectly disabled after inserting a matte. Bug 66425
* Fixed issue where trackers get unlinked after an Undo. Bug 66500
* Fixed missing cursor on NDI output, and improved responsiveness when picking or interacting with overlays on the NDI output. Bug 66576
* Fixed failures using Invizigrain OFX plugin at high resolution on some systems. Bug 66533
* The fragmentation diagnostic and overnight defragmentation service now ignore solid state devices. Bug 66710
* Fixed error where a CPU OFX operator could fail to render when it is in a stack beneath another CPU OFX operator which is cached. Bug 65730
* Fixed potential Blackboard 2 related crash on complex stacks. Bug 64703
* Fixed blank image when reading from some uncompressed OpenEXR files. Bug 65702
* Fixed per-frame metadata from ARRI and Sony MXF media, for example `%{Tilt}` and `%{Roll}`. Bug 65823
* Fixed an issue with the index service creating idle connections to the Postgres database. Bug 65886
* Fixed issue with XDCAM encoded MXF files rendered by the application not being readable in some third-party tools. Bug 65850
* Fixed issue where tracker keyframes could incorrectly be moved, and couldn't be deleted left/right. Bug 65993
* Fixed crash when overlapping strips were creating using Apply in merge mode. Bug 66008
* Fixed behaviour of keyframe buttons in OFX operators. Bug 66046
* Fixed a memory leak when reading XML files. Bug 63964
* Fixed "Stack output is too large" errors for example when using some OFX plugins. Bug 65681
* ARRIRAW media now uses the colour space metadata in the file to determine whether to use AWG3 or AWG4 for automatic decoding. This should reduce incidences of colour mismatches against decodes performed using other tools. Bug 66510
* Fixed behaviour of monochrome Lasergraphics DPX files. Bug 61013
* Fixed issue where trackers get unlinked after an Undo. Bug 66500
* Fixed issues with some OFX plugins in galleries. Bug 66526
* Removed edge repetition in Matchbox Shader for: CROK Beauty, CROK Fisheye, crok\_chroma\_warp, crok flicker, crok heathaze, crok kuwahara. Bug 64538
* Fixed AJA T-TAP Pro UHD RGB output. Bug 64432
* Fixed `SceneNameOnly` substitution to cope with multiple folders. Bug 64585
* Fixed crash when selecting operator in an inside outside from the desk. Bug 59151
* Fixed crash when selecting DCI 8K resolution output. Bug 59853
* Fixed crash in Paint. Bug 50465
* Improved application interactivity/performance when the Shots View is visible. Bug 64745
* Fixed crash reading 4:2:2 JPEG 2000 files with alpha. Bug 63673
* Fixed issue where DNxHD/DNxHR encoded QuickTime files rendered by the application could be incorrectly identified as interlaced instead of progressive in e.g. Clipster. Bug 65123
* Fixed crash in Frame.io package when downloading comments made by anonymous users. Bug 65351
* Fixed possible crash in Text operator loading a new font style for an existing font name. Bug 65557
* Fixed clipped highlights in Cuts View when using RED media at a high ISO or exposure. Please use `bl-reset-cache -thumb` to remove incorrect thumbnails from the cache. Bug 62978
* Fixed issue with `%{RandomUUID}` variable substitution when rendering with "Render Format: Use Input Format". Bug 65817
* Fixed naming of cropped input formats in FLUX Manage View when the crop is only in one dimension. Bug 65712
* Fixed issue with slow renders and the application becoming unresponsive when monitoring Dolby Atmos audio beyond the end of the source media. Bug 65815
* Improved speed of some renders with multiple deliverables, notably multiple audio files. Bug 65490
* Fixed clipping of OpenEXR media in gallery grab. Bug 64668
* Fixed hang when using "Prepare Noise Profile" in Neat Video when the OFX operator is in a cache strip. Bug 65752
* Fixed issue with GPU JPEG 2000 acceleration not working when decoding MXF files. Bug 65983
* Fixed issue with shot marks always applied to the bottom sequence when conforming AAFs. Bug 65975
* Fixed crash when reconfiguring NDI output device. Bug 65398
* Fixed issue that could generate corrupt files during unsuccessful MXF file trimming. Bug 66118
* Fixed crash caused by invalid Resolution setting for a stream in Client Sessions View. Bug 64254
* Fixed MXF UIDs appearing in the `bl-conform` output by default, only output with the `--verbose` option. Bug 65771
* Fixed crash when changing stream resolution in Client Sessions View. Bug 66170
* Fixed crash when applying a stack to itself when there are strips that are protected from being copied. Bug 66135
* The bitrate of DCI compliant JPEG 2000 essence has been reduced by 5% to avoid issues with older DCP players and third-party validation tools. Bug 66359
* Fixed display of custom column expression icon in Shots View. Bug 66075
* Fixed an issue that could affect Wacom pen sensitivity in FilmLightOS 8. Bug 66379
* Fixed issue when copying an input with additional operators. Bug 66684
* Fixed crash when using apply with auto selection off. Bug 58653
* Fixed a hotfix issue that could stop UI hosts from booting. Bug 66785



**버전 5 이후 버그 수정**

\


• 선형화된 컬러 처리(Linearised Colour Treatment)를 사용하는 새로 삽입된 블렌드 연산자가 이제 작업 컬러 공간이 아닌 입력의 컬러 공간을 올바르게 사용합니다. \[버그 55995]

• 작업 컬러 공간이 불확정적일 때 Curve Grade에서 발생하는 드문 충돌을 수정했습니다. \[버그 56815]

• 돌비 애트모스 및 돌비 비전 메자닌 MXF의 렌더링을 방해하는 문제를 수정했습니다. 이로 인해 생성된 영화가 잘못된 권한을 가질 수 있는 문제도 해결되었습니다. \[버그 64109]

• 레이어 내 그룹 그레이딩에서 발생하는 드문 충돌을 수정했습니다. \[버그 64295]

• 선형화된 컬러 처리(Linearised Colour Treatment)를 사용하는 새로 삽입된 블렌드 연산자가 이제 작업 컬러 공간이 아닌 입력의 컬러 공간을 올바르게 사용합니다. \[버그 55995]

• DSpot 및 Switch Dust 스트립에서 잠재적인 장면 로딩 오류를 수정했습니다. \[버그 64125]

• 쉐이더 레이어에 붙여넣기 시 발생하는 충돌을 수정했습니다. \[버그 64099]

• 이미지 디스플레이에서 커서가 있을 때 종료 시 발생하는 충돌을 수정했습니다. \[버그 64030]

• 잘못 구성된 Scratchpad에 대한 오류 메시지를 수정했습니다. \[버그 64131]

• 참조 입력이 누락된 모든 스트립은 이제 스트립에 빨간 X로 표시됩니다. \[버그 64600]

• 보호된 매트가 있는 스택에 붙여넣기 할 때 발생하는 문제를 수정했습니다. \[버그 63901]

• 그레이드를 적용할 때 스트립이 위로 이동하는 문제를 수정했습니다. \[버그 63902]

• 독립형 Blur 및 In/Out Blur 도구에서 슬라이더 및 데스크 컨트롤의 동작을 개선했습니다. \[버그 64628]

• 비선형 응답 곡선으로 매개변수를 조정할 때 트랙볼 동작을 개선했습니다. \[버그 64679]

• 갤러리에서 썸네일을 보거나 스크러빙할 때 항상 현재 커서의 뷰잉 컬러 스페이스를 사용하도록 수정했습니다. \[버그 62759]

• 레이어 뷰에서 우회된 스택을 표시할 때 스크롤 막대가 덮이는 문제를 수정했습니다. \[버그 64231]

• ‘갱’ 아이콘의 크기를 늘리고 Hue Shift에 스플리터 바를 추가하여 Hue Controls와 Saturation/Value controls를 분리했습니다. \[버그 64229]

• Shader 및 OFX 연산자 뒤에 Transform이 있는 경우 발생하는 이미지 문제를 수정했습니다. \[버그 64386]

• Merge Apply와 Protect Existing Destination Strips 및 Tracker strips를 사용할 때 중첩된 스트립으로 인해 발생하는 충돌을 수정했습니다. \[버그 64505]

• Matte Tool에서 인코더 노브를 이동할 때 현재 선택된 도구 대신 인코더에 연결된 도구가 활성화되는 문제를 수정했습니다. \[버그 64601]

• 확장된 범위를 전환할 때 위치가 업데이트되지 않는 비선형 응답 곡선을 가진 슬라이더를 수정했습니다. \[버그 64685]

• Matte Tool의 일부 컨트롤의 민감도를 개선했습니다. \[버그 64802]

• Apply를 누를 때 발생하는 충돌을 수정했습니다. \[버그 64333]

• 그룹 그레이딩이 이제 레이어 순서를 유지하기 위해 올바른 트랙에 스트립을 삽입합니다. \[버그 64672]

• 큐에 정확히 하나의 메일 메시지가 있을 때의 메일 큐 진단 보고서를 개선했습니다. \[버그 64687]

• Blur 및 In/Out Blur 도구에 재설정 버튼을 추가했습니다. \[버그 64716]

• Matte Tool에서 단계를 이름 변경할 때 발생하는 문제를 수정했습니다. \[버그 64880]

• 읽기 전용 장면에서 ‘New Shape’ 모드가 비활성화/취소되도록 보장했습니다. \[버그 64847]

• Matte Tool이 스트립을 결합하기 전에 불일치 매개변수를 확인하지 않는 버그를 수정했습니다. \[버그 64894]

• 키프레임이 포함된 연산자에서 키프레임 막대가 비어 있을 수 있는 버그를 수정했습니다. \[버그 64843]

• 8-bit Y’CbCrA 이미지를 JPEG 2000 Broadcast Contribution Profile YCC 422로 렌더링할 때 실패하는 문제를 수정했습니다. \[버그 65117]

• Blackboard Classic의 페이드 인 및 페이드 아웃 시간을 줄였습니다. \[버그 65356]

• 적절한 메뉴에서 Avid (conform) 카테고리를 숨기도록 보장했습니다. \[버그 59360]

• 장면을 전환한 후 추적 중에 발생하는 충돌을 수정했습니다. \[버그 64864]

• ARRI Reference Tool에서 작성된 IRIDAS 큐브를 읽는 지원을 추가했습니다. \[버그 66074]

• 텍스트 줄 수가 너무 많은 경우 사용할 수 없게 될 수 있는 일부 대화 상자가 이제 스크롤 막대를 사용하도록 수정했습니다. \[버그 65442]

• OFX, Matte Tool 및 Blur를 포함한 다양한 도구에서 재설정 및 갱 버튼의 비표준 위치를 수정했습니다. \[버그 65449]

• 표 내에서 열 머리글 간의 막대를 더 눈에 띄게 했고, 열을 항상 수평 스크롤링하도록 변경했습니다. 또한 컬러 스페이스 관리 대화 상자에서 열 머리글이 올바르게 정렬되지 않는 문제를 수정했습니다. \[버그 65569]

• 레이어 뷰 및 매개변수 뷰에서 타임라인 뷰의 스트립 우회와 일치하도록 우회 스트라이프를 뒤집었습니다. \[버그 64557]

• 타임라인을 완전히 확대하고 커서가 타임라인의 몇 시간 위에 위치할 때 타임라인의 정밀도 문제를 수정했습니다. \[버그 65726]

• 썸네일의 댓글 (편집 가능) 필드를 편집하는 동안 Cuts View에서 스크롤할 때 발생하는 중단 문제를 수정했습니다. \[버그 64555]

• 높은 ISO나 노출에서 BRAW 미디어를 사용할 때 Cuts View에서 하이라이트가 클립되는 문제를 수정했습니다. 캐시에서 잘못된 썸네일을 제거하려면 “bl-reset-cache -thumb”을 사용하십시오. \[버그 65765]

• FLUX Manage View에서 여러 열을 정렬하거나 재배치할 수 없는 문제를 수정했습니다. \[버그 65698]

• Conform 또는 FLUX Manage에서 장면에 첫 번째 시퀀스를 삽입할 때 장면에 이미 비시퀀스 스트립이 있는 경우에도 장면의 컨테이너 및/또는 타임라인 타임코드 비율을 변경하라는 메시지가 표시됩니다. \[버그 65755]

• Hue에 기반한 조정을 위한 내장 채도 변조를 조정하기 위해 Curve Grade의 사용자 지정 메뉴에 Hue Safety 컨트롤을 추가했습니다. \[버그 64626]

• 텍스트 연산자가 선택된 상태에서 장면을 닫을 때 발생할 수 있는 잠재적인 충돌을 수정했습니다. \[버그 65605]

• 해결되지 않은 참조 스트립이 포함된 스택에 새 레이어를 삽입할 수 없는 버그를 수정했습니다. \[버그 66056]

• Preferences -> Operators의 Tracker Desk Selection 기본 설정에 세 개의 추가 버튼을 추가했습니다. 이를 통해 사용자는 Blackboard/Slate에서 접근할 수 있는 세 개의 추가 트래커를 매핑할 수 있습니다. Ctrl 키를 누르고 있을 때 이전 트래커 컨트롤이 패널에 표시됩니다. \[버그 65188]

• macOS에서 10-bit Integer 타임라인 캐싱을 사용하는 Apple ProRes 압축 옵션을 제거했습니다. \[버그 64264]

• 컴포지트 그레이드를 갤러리에 저장할 때 미디어가 오프라인 상태일 경우 렌더링 오류가 발생할 수 있는 드문 문제를 수정했습니다. \[버그 66063]

• “Paste Groups”가 활성화되고 대상 장면에 그룹이 없을 때 발생할 수 있는 Multi-Paste 버그를 수정했습니다. 이로 인해 붙여넣어진 그룹 중 하나가 “\<unsaved>” 그룹 슬롯을 차지하게 되어 덮어쓰기 위험이 발생할 수 있었습니다. \[버그 66116]

• 여러 소스 클립이 대상 샷에 맞출 가능성이 동일하게 판단될 때 발생할 수 있는 Multi-Paste 버그를 수정했습니다. 이제 대상 샷의 기록 시간과 가장 가까운 소스 샷이 선택됩니다. \[버그 66125]

• 마우스 기반 편집 작업 중에 현재 장면을 닫을 때 발생할 수 있는 충돌을 수정했습니다. 해당 상황에서 장면 닫기를 차단하여 수정했습니다. \[버그 66177]

• 일부 Linux 시스템에서 마우스를 사용하여 편집 드래그를 할 때 발생할 수 있는 무한 스크롤 문제를 수정했습니다. 또한 왼쪽으로 스크롤할 때 적절히 일찍 스크롤이 중지되지 않는 문제를 수정했습니다. \[버그 65972]

• 마우스를 사용하여 슬립 편집을 할 때 타임라인에서 스크롤이 발생하는 문제를 수정했습니다. \[버그 65972]

• 타임라인 정렬이 Bars 및 Text의 최신 버전을 생성하도록 수정했습니다. \[버그 63936]

• SDI 출력에서 커서 지연 문제를 수정했습니다. \[버그 66241]

• FLUX Manage에서 타임라인 뷰로 드래그 앤 드롭할 때 드롭 존이 FLUX Manage의 현재 삽입 버튼 상태를 항상 반영하도록 수정했습니다. 이를 통해 “Replace”, 오디오 및 BLG 삽입을 제공할 수 있습니다. \[버그 63795]

• Baselight를 재시작하거나 설정을 전환하거나 bl-setups와 같은 외부 도구를 실행할 때 AJA Kona SDI 또는 HDMI 출력에서 마젠타 이미지가 발생하는 문제를 수정했습니다. \[버그 66443]

• 클라이언트 세션 보기에서 스트림 해상도를 변경할 때 발생하는 충돌을 수정했습니다. \[버그 66170]

• 4k 논리 섹터가 있는 xfs 디스크에 저장된 이미지 파일을 처리할 때 데이터 정렬 문제를 수정했습니다. 더 이상 필요하지 않은 FLIX\_AUTO\_FIX 환경 변수를 제거했습니다. \[버그 4285]

• Internal CMU (v2.9) 모드에서 Dolby Vision Trim 연산자의 UI 누락 문제를 수정했습니다. \[버그 66488]

• 표의 열 간격을 넓히고 정렬을 개선했습니다. 또한 샷 보기와 갤러리에서 ‘썸네일’ 제목 텍스트를 제거했습니다. \[버그 65638]

• 스트립의 캐싱 상태를 되돌리거나 다시 실행할 때 백그라운드 캐싱이 트리거되지 않는 문제를 수정했습니다. \[버그 53320]

• NVME 부팅 디스크를 사용하는 Generation VIII 시스템의 진단 문제를 수정했습니다. \[버그 66529]

• Hue Angle 사용자 정의 메뉴에 UI 채도 컨트롤을 추가하여 휠과 히스토그램의 채도를 조정할 수 있습니다. \[버그 66151]

• 마크를 내보낼 때 충돌을 일으킬 수 있는 버그를 수정했습니다. \[버그 66319]

• Matte Tool 패널 상호작용이 인코더와 트랙볼을 동시에 조정할 때 응답하지 않는 문제가 수정되었습니다. \[버그 66360]

• Curve Grade에서 하나의 인코더를 빠르게 이동한 후 다른 인코더를 이동할 때 두 개의 제어 포인트가 동시에 편집되는 문제를 수정했습니다. \[버그 66290]

• Blackboard Classic이 Shape Quickshape 메뉴를 업데이트하지 않는 문제를 수정했습니다. \[버그 65933]

• 스크롤 막대를 반복적으로 클릭하여 긴 목록을 스크롤할 때 발생할 수 있는 잠재적 충돌을 수정했습니다. \[버그 66491]

• 프리셋 만들기 및 편집 대화 상자에서 키보드 포커스 문제를 수정했습니다. \[버그 66397]

• 로케이터 마크가 있는 CMX EDL의 컨폼을 개선하고, 대소문자를 구분하지 않는 색상 이름을 허용했습니다. \[버그 66550]

• CPU 렌더러를 통해 ARRIRAW v7 이미지를 디코딩할 때 발생하는 메모리 누수를 수정했습니다. \[버그 66420]

• FilmLightOS 8에서 과민한 Wacom 펜 문제를 수정했습니다. \[버그 66379]

• 갤러리에서 장면을 닫을 때 발생할 수 있는 충돌을 수정했습니다. \[버그 66499]

• 영화 디코딩이 계속 실패할 때 발생하는 충돌을 수정했습니다. \[버그 66566]

• 제어 포인트를 드래그하면서 Curve Grade 연산자를 선택 해제할 때 발생할 수 있는 잠재적 충돌을 수정했습니다. \[버그 20295]

• 타임라인 스크롤 중 장면을 닫을 때 발생할 수 있는 충돌을 수정했습니다. \[버그 65663]

• 명시적 스트립 캐싱이 활성화된 상태에서 일부 OFX 매개변수를 수정하려고 할 때 발생하는 충돌을 수정했습니다. \[버그 66600]

• 일부 DNxUncompressed 미디어에 대한 FLUX Manage 썸네일 생성을 실패하는 문제를 수정했습니다. \[버그 66546]

• 텍스트 매크로 패널에서 발생하는 충돌을 수정했습니다. \[버그 63190]

• 새 장면 타임라인 캐싱 설정을 수정했으며, 이는 이제 기본 설정에서 설정으로 이동되었습니다. \[버그 65192]

• 프레임 증가가 0일 때 발생하는 오디오 오류 메시지를 수정했습니다. \[버그 60928]

• 새 세션을 만들 때 기존 스트림 설정을 새 세션으로 복사하지 않을 때 클라이언트 세션 보기에서 발생하는 충돌을 수정했습니다. \[버그 66132]

• 기존 세션이 진행 중일 때 새 세션을 만들 때 클라이언트 세션 보기에서 발생하는 충돌을 수정했습니다. \[버그 66000]

• 세션의 스트림 설정이 유효하지 않을 때 클라이언트 세션 보기에서 발생하는 충돌을 수정했습니다. \[버그 64254]

• 클라이언트 세션 보기에서 “초대 다시 보내기” 버튼이 로컬 세션에 대해 더 이상 표시되지 않습니다. \[버그 66160]

• 클라이언트 세션 보기에서 클라이언트를 제거할 때 발생할 수 있는 잠재적 충돌을 수정했습니다. \[버그 66632]

• 투명도가 0인 형태의 매트 문제를 수정했습니다. \[버그 58022]

• EGamut 색 공간을 사용하는 OpenEXR 파일을 작성할 때 색도 메타데이터의 녹색 값을 수정했습니다. \[버그 65007]

• 특히 다중 GPU 시스템에서 영화 파일을 전혀 읽지 않는 반복적인 응용 프로그램 실행으로 인해 발생할 수 있는 다양한 실패를 수정했습니다. \[버그 66629]

• Bars 연산자를 재설정할 때 발생하는 충돌을 수정했습니다. \[버그 66619]

• Dolby Vision 작업 시 UI 업데이트 속도를 개선했습니다. \[버그 66681]

• 스택 외부의 스트립에 대한 명시적 참조가 있는 스택을 갤러리에 가져오는 것을 방지했습니다. \[버그 64561]

• Chromogen/Matte Tool의 레이어 목록에 메뉴 버튼을 추가했습니다 (메뉴를 불러오기 위해 오른쪽 클릭을 사용하는 이전 방법도 계속 작동). \[버그 66620]

• Chromogen, Matte Tool 및 Flare에서 패널 디스플레이가 이제 기본 단계 이름 대신 단계의 사용자 이름을 표시하도록 수정되었습니다. \[버그 66627]

• 매트를 삽입한 후 스트립 우회 버튼이 잘못 비활성화될 수 있는 문제를 수정했습니다. \[버그 66425]

• Undo 후 트래커가 연결 해제되는 문제를 수정했습니다. \[버그 66500]

• NDI 출력에서 커서가 누락되는 문제를 수정하고, NDI 출력에서 오버레이를 선택하거나 상호작용할 때 응답성을 개선했습니다. \[버그 66576]

• 일부 시스템에서 고해상도로 Invizigrain OFX 플러그인을 사용할 때 발생하는 실패를 수정했습니다. \[버그 66533]

• 조각화 진단 및 야간 디프래그 서비스가 이제 SSD를 무시하도록 수정했습니다. \[버그 66710]

• CPU OFX 연산자가 캐시된 다른 CPU OFX 연산자 아래 스택에 있을 때 렌더링에 실패할 수 있는 오류를 수정했습니다. \[버그 65730]

• 복잡한 스택에서 발생할 수 있는 Blackboard 2 관련 충돌을 수정했습니다. \[버그 64703]

• 일부 압축되지 않은 OpenEXR 파일을 읽을 때 빈 이미지가 표시되는 문제를 수정했습니다. \[버그 65702]

• ARRI 및 Sony MXF 미디어에서 프레임별 메타데이터 예를 들어 %{Tilt} 및 %{Roll} 문제를 수정했습니다. \[버그 65823]

• 인덱스 서비스가 Postgres 데이터베이스에 유휴 연결을 생성하는 문제를 수정했습니다. \[버그 65886]

• 응용 프로그램에서 렌더링된 XDCAM 인코딩된 MXF 파일이 일부 타사 도구에서 읽을 수 없는 문제를 수정했습니다. \[버그 65850]

• 트래커 키프레임이 잘못 이동되거나 좌우로 삭제되지 않는 문제를 수정했습니다. \[버그 65993]

• 병합 모드에서 Apply를 사용하여 중첩된 스트립을 만들 때 발생하는 충돌을 수정했습니다. \[버그 66008]

• OFX 연산자에서 키프레임 버튼의 동작을 수정했습니다. \[버그 66046]

• XML 파일을 읽을 때 발생하는 메모리 누수를 수정했습니다. \[버그 63964]

• 일부 OFX 플러그인을 사용할 때 발생하는 “스택 출력이 너무 큼” 오류를 수정했습니다. \[버그 65681]

• ARRIRAW 미디어가 파일 내의 색상 공간 메타데이터를 사용하여 자동 디코딩 시 AWG3 또는 AWG4를 사용할지 여부를 결정하도록 수정했습니다. 이를 통해 다른 도구를 사용한 디코딩과의 색상 불일치 발생을 줄일 수 있습니다. \[버그 66510]

• 모노크롬 Lasergraphics DPX 파일의 동작을 수정했습니다. \[버그 61013]

• Undo 후 트래커가 연결 해제되는 문제를 수정했습니다. \[버그 66500]

• 갤러리에서 일부 OFX 플러그인과 관련된 문제를 수정했습니다. \[버그 66526]

• Matchbox Shader에서 CROK Beauty, CROK Fisheye, crok\_chroma\_warp, crok flicker, crok heathaze, crok kuwahara의 에지 반복을 제거했습니다. \[버그 64538]

• AJA T-TAP Pro UHD RGB 출력을 수정했습니다. \[버그 64432]

• 여러 폴더를 처리하기 위한 SceneNameOnly 치환을 수정했습니다. \[버그 64585]

• 데스크에서 인사이드 아웃사이드에서 연산자를 선택할 때 발생하는 충돌을 수정했습니다. \[버그 59151]

• DCI 8K 해상도 출력을 선택할 때 발생하는 충돌을 수정했습니다. \[버그 59853]

• 페인트에서 발생하는 충돌을 수정했습니다. \[버그 50465]

• 샷 뷰가 표시될 때 응용 프로그램의 상호작용성/성능을 개선했습니다. \[버그 64745]

• 알파와 함께 4:2:2 JPEG 2000 파일을 읽을 때 발생하는 충돌을 수정했습니다. \[버그 63673]

• 응용 프로그램에서 렌더링된 DNxHD/DNxHR 인코딩된 QuickTime 파일이 Clipster 등에서 프로그레시브 대신 인터레이스로 잘못 식별될 수 있는 문제를 수정했습니다. \[버그 65123]

• 익명 사용자가 작성한 댓글을 다운로드할 때 Frame.io 패키지에서 발생하는 충돌을 수정했습니다. \[버그 65351]

• 텍스트 연산자가 기존 글꼴 이름에 새 글꼴 스타일을 로드할 때 발생할 수 있는 잠재적 충돌을 수정했습니다. \[버그 65557]

• Cuts View에서 RED 미디어를 높은 ISO나 노출로 사용할 때 하이라이트가 클립되는 문제를 수정했습니다. 캐시에서 잘못된 썸네일을 제거하려면 bl-reset-cache -thumb을 사용하십시오. \[버그 62978]

• “Render Format: Use Input Format”으로 렌더링할 때 %{RandomUUID} 변수 치환 문제를 수정했습니다. \[버그 65817]

• FLUX Manage View에서 크롭이 한 차원에서만 이루어질 때 잘린 입력 포맷의 이름 지정 문제를 수정했습니다. \[버그 65712]

• 소스 미디어의 끝을 넘어서 돌비 애트모스 오디오를 모니터링할 때 발생하는 느린 렌더링 및 응용 프로그램이 응답하지 않는 문제를 수정했습니다. \[버그 65815]

• 여러 딜리버러블, 특히 여러 오디오 파일이 포함된 일부 렌더링의 속도를 개선했습니다. \[버그 65490]

• 갤러리에서 OpenEXR 미디어의 클립 문제를 수정했습니다. \[버그 64668]

• Neat Video에서 “Prepare Noise Profile”을 사용할 때 OFX 연산자가 캐시 스트립에 있을 때 발생하는 중단 문제를 수정했습니다. \[버그 65752]

• MXF 파일을 디코딩할 때 GPU JPEG 2000 가속이 작동하지 않는 문제를 수정했습니다. \[버그 65983]

• AAF를 컨폼할 때 샷 마크가 항상 하단 시퀀스에 적용되는 문제를 수정했습니다. \[버그 65975]

• NDI 출력 장치를 재구성할 때 발생하는 충돌을 수정했습니다. \[버그 65398]

• 실패한 MXF 파일 트리밍 중 손상된 파일이 생성될 수 있는 문제를 수정했습니다. \[버그 66118]

• 클라이언트 세션 보기에서 스트림의 잘못된 해상도 설정으로 인한 충돌을 수정했습니다. \[버그 64254]

• 기본적으로 bl-conform 출력에 나타나는 MXF UID를 –verbose 옵션을 사용할 때만 출력되도록 수정했습니다. \[버그 65771]

• 클라이언트 세션 보기에서 스트림 해상도를 변경할 때 발생하는 충돌을 수정했습니다. \[버그 66170]

• 보호된 스트립이 있을 때 스택을 자체에 적용할 때 발생하는 충돌을 수정했습니다. \[버그 66135]

• 오래된 DCP 플레이어와 타사 검증 도구에서 발생하는 문제를 피하기 위해 DCI 준수 JPEG 2000 에센스의 비트레이트를 5% 줄였습니다. \[버그 66359]

• 샷 보기에서 사용자 정의 열 표현 아이콘의 표시 문제를 수정했습니다. \[버그 66075]

• FilmLightOS 8에서 Wacom 펜 감도에 영향을 미칠 수 있는 문제를 수정했습니다. \[버그 66379]

• 추가 연산자와 함께 입력을 복사할 때 발생하는 문제를 수정했습니다. \[버그 66684]

• 자동 선택을 끈 상태에서 Apply를 사용할 때 발생하는 충돌을 수정했습니다. \[버그 58653]

• UI 호스트가 부팅되지 못하게 할 수 있는 긴급 수정 문제를 해결했습니다. \[버그 66785]
