# 베이스라이트 릴리즈 노트 5.2.11854 (2019-05-30)

## 최신기능 Baselight 5.2.11761이후&#x20;

### ARRI BLG Support 아리 BLG 지원&#x20;

*   Baselight and Daylight now support the reading of BLG data stored in ARRI media. This allows preliminary grades that are created on set using Prelight to be applied automatically when the media is imported into Daylight or Baselight, without the need for additional BLG files.

    This feature can be enabled in the Sequence Overrides tab of the Media Import Rules View. Settings in the Apply Embedded BLG dropdown allow embedded BLGs to be always applied, never applied, or for a dialog to give the option upon sequence insertion. The rule will be applied to BLGs inserted both from FLUX Manage, and during conform from an EDL. Compatible media types are ARRIRAW sequences, Quicktime movies and MXFs, shot on ARRI cameras \[bug 45943]\
    **이제 베이스라이트(Baselight)와 데이라이트(Daylight)에서 아리 미디어에 저장된 BLG 데이터를 읽을 수 있습니다. 미디어를 데이라이트(Daylight)나 베이스라이(Baselight)트에 넣을때 프리라이트(Prelight)로 미리 만들어온 룩(그레이드)를 자동으로 적용할 수 있으며, 추가적인 BLG 파일이 필요하지 않습니다.**\
    **이 기능은 미디어 임포트 규칙 보기(Media Import Rules Vie입)의 시퀀스 우선기능(Sequence Overrides)을 가능하게 합니다. 임베디드 BLG 드롭다운 적용에서의 설정은 임베디드 BLG를 항상 적용하거나, 적용하지 않거나, 시퀀스 입력시 옵션을 줄 수 있는 창을 만들수 있습니다. 이 규칙은 플럭스 매니지나 EDL 컨펌시 둘 다에서 BLG 입력을 적용할 수 있습니다. 호환가능한 미디어 유형은 ARRI 카메라들로 촬영된 ARRIRAW 시퀀스, 퀵타임 무비(Mov), MXF입니다.**

### Base Grade Bumps 베이스그레이드 범프&#x20;

*   Numeric keypad bumps, previously available for Film Grade, are now also available on Base Grade, with the following tweaks and changes: **숫자 키패드 범프, 이전에는 필름그레이드가 가능했는데, 이제는 베이스그레이드 또한 가능하게 되었습니다. 트윅과 변경은 다음과 같습니다.**

    To enable these bumps, set the numeric keypad mode to "Grading", under: **범프를 가능하게 할려면, 숫자키패드 모드를 '그레이딩(Grading)'으로 설정합니다.**

    ```
    "Edit" -> "Numeric Keypad Mode".
    ```

    Each zone can be bumped through a set of parameters called a Vector Bump. Unlike Film Grade, the individual channel bump keys, **각 영역은 벡터 범프라고 불리우는 변수값들의 세트를 통해서 값을 올릴 수 있습니다. **

    **필름그레이드와는 달리 각 채널별 범프키가 적용됩니다.**

    ```
    R|G|B Up & Down and C|M|Y Up & Down,
    ```

    **      R|G|B 업 앤 다운, C|M|Y 업 앤 다운,**have been generalised to a single set of keys:

    ```
    Left|Middle|Right Up & Down.
    ```

    The behaviour of each bump per channel can be customised. This can be done by editing the default Vector Bump values, under:

    ```
    "Customise" -> "Default Values and Bumps".
    ```

    By default, all groups with Vector Bumps have their bump values set to R|G|B, which have been fitted against the Munsel hues. Balance, has two additional Vector Bumps, one set to C|M|Y, and the other to Exposure|Flare|Saturation.

    The newly available keys which were reserved for C|M|Y bumps in Film Grade, have now been assigned as switches to different groups. These keypad mappings can also be customised, under:

    ```
    "Customise" -> "Configure Bump Keypad Keys".
    ```

    Switching between groups will show a yellow glow around the currently selected group as an indicator.

    The overall bump buttons and the keyframe toggle button retain the same functionality, based on currently selected group.

    The table below illustrates the new numeric keypad functions for Base Grade bumps.

    **Keypad         | Function**

    Num Lock, /, \* | Bump Left|Middle|Right Up 7, 8, 9 | Bump Left|Middle|Right Down 4, 5, 6 | Bump Keypad Mapping (4, 5, 6) 1, 2, 3 | Bump Keypad Mapping (1, 2, 3)

    * \| Keyframe Toggle
    *   \| Bump Overall Up Enter | Bump Overall Down 0, . | N/A

        Groups that can be bumped through the numeric keypad can also be used to bump on Blackboard and Slate \[bug 39320]\
        **   Keypad (키패드)        | Function (기능)**

        **   ------------------------------------------**

        **   Num Lock, /, \* | 범프 왼쪽|중간|오른쪽 업 **

        **   7, 8, 9        | 범프 왼쪽|중간|오른쪽 다운 **

        **   4, 5, 6        | 범프 키패드 매핑 (4, 5, 6)**

        **   1, 2, 3        | 범프 키패드 매핑 (1, 2, 3)**

        **   -              | 키프레임 토글**

        **   +              | 범프 전체 업**

        **   Enter          | 범프 전체 다운 **

        **   0, .           | N/A (적용없음)**

### Graticule Generator 격자 생성기&#x20;

*   Added a graticule generator to the Cursor view. When enabled, it starts by drawing a small box overlay at the centre of the screen. **커서보기(Cursor view)에 격자생성기를 추가했습니다. 사용하도록 설정하면, 화면 중앙에 작은 박스가 겹쳐서 보이게 됩니다.**

    The two sliders in the Cursor view adjust the width and the height of the box. The box is always centred during the horizontal and vertical adjustments. It is also possible to set the size of the graticule box manually using the corresponding edit boxes for each dimension. **커서뷰 격자생성기의 두개의 슬라이더는 박스의 가로와 세로를 조정합니다. 수평과 수직 조정중에 박스는 항상 중앙에 위치하여 있습니다. 격자 X, Y 박스 수치를 직접 넣어서 수동으로 격자 박스의 사이즈를 조절할 수 있습니다.**

    Blackboard controls: **블랙보드에서 조작**

    The graticule generator can also be controlled using a Blackboard. A new combo button named "Graticule" has been added to the "Cursor" button category in Chalk. Simply drag this onto a spare button to map it to the desk.

    The "Graticule" button works as follows: 1) Toggle graticule on/off A single press toggles the graticule state between enabled and disabled. 2) Show/Hide graticule panel If pressed and held, a graticule panel will be displayed allowing control of the graticule size using the corresponding encoders. When released, the graticule panel will disappear \[bug 16584]**블랙보드에서도 격자생성기를 제어할 수 있습니다.**

### Miscellaneous 기타기

* Added the ability to set categories on media to Media Import Rules View \[bug 49655]
* Added the ability to enable input strip caching with Media Import Rules \[bug 49323]
* Added the ability to control Stack Colour Space with Media Import Rules \[bug 49654]
* Added the ability to create new Galleries to the Gallery View \[bug 34128]
* Made 'Apply x Rules to y Shots' button obey shot selection \[bug 50231]
* Updated to DNxHD/DNxHR SDK version 2.4.2.31. This includes bug fixes \[bug 50846]
* Added support for RTX 2080 and RTX 6000 graphics cards, using the 418.56 driver \[bug 51104] **418.56 드라이버를 사용하여, RTX 2080 및 RTX 6000 그래픽 카드 추가 지원**
* Added a button to the Media Import Rules View to allow rules to be applied either to all shots in a scene or selected shots only \[bug 51203]

## 버그개선 Baselight 5.2.11761이후&#x20;

* Fix a crash while resetting the Zoom/Pan of a display image with panorama projection enabled \[bug 50662]
* Fix an issue where on changing the Zoom/Pan settings of a scene with multiple views at different shots, the image would disappear \[bug 50592]
* Improved the decode performance of temporally compressed movie files when navigating the timeline and creating thumbnails simultaneously \[bug 49528]
* Fixed an issue where resetting the Audio operator would have no effect \[bug 50731]
* Hide handles in Curve Grade when "Auto Handles" mode is enabled \[bug 50694]
* Most types of temporally compressed material in MXF or QuickTime containers will now use additional CPU resources to perform the decode. This improves the decode speed of e.g. XAVC Long and XDCAM encoded files \[bug 50010]
* Allowed access to File Metadata of the form abcd.efg \[bug 50536]
* Shots that are part of a dissolve are no longer considered graded \[bug 49068]
* Fixed issues with Truelight selection in Media Import Rules View \[bug 50230]
* Fixed crash in Gallery when closing a tab whereby another tab contains the same scene \[bug 50583]
* Fixed an issue that caused an invalid aspect ratio to be set in XDCAM essence when written to Sony MXF \[bug 50836] **Sony MXF에 기록할때, XDCAM 에센스에 잘못된 화면비를 설정하는 문제 해결**
* Retimes are removed from the input strip when updating an AAF with Baselight grades \[bug 50842]
* When importing .edl files we now accept a ':' following ASC\_SOP and ASC\_SAT specifiers \[bug 50792]
* Fixed an issue where DNG files from Panasonic V35LT cameras were not correctly identified as Panasonic CinemaDNG \[bug 50914]
* Fixed a crash when deleting a custom column that is being used for filtering \[bug 50981]
* Fixed issue whereby a colour pick for a colour well that is not currently displayed could lead to a hang \[bug 50775]
* Fixed issue with painting though a matte with multiple paint layers \[bug 50999]
* Fixed issue where some CDL groups would show incorrect text on Blackboard and Slate \[bug 50628]
* Fixed issue whereby updating an AAF with Baselight grades would sometimes fail \[bug 36213]
* The "Maximum hotspot grab range" preference setting is now in the "Display" tab. The setting is now aware of the display monitor resolution, in order to make it easier to work with control points with high resolution displays \[bug 48809]
* Fixed an issue where Media Import Rules were not being correctly applied to both inputs to a dissolve \[bug 50456]
* Removed the limit on the number of search directories in the EDL Import View and in bl-conform \[bug 50968]
* Fixed issue preventing multipaste from .ale files for which there are multiple possible timecode formats \[bug 50515]
* Fixed issue with variable retimes from Premiere XMLs in mixed framerate projects \[bug 50863]
* Changed the hotspot for scrolling through shots whilst performing a drag to be consistent with the size of the view \[bug 50758]
* Fixed issue with paint layer source mode not being passed to strips created by cutting stacks or copy and paste actions \[bug 51115]
* Improved speed of Shots View filtering \[bug 50250]
* Fixed Text issue where many keyframes would be dropped if keyframe striping was disabled and the transform was edited during playback \[bug 51131]
* Fixed an issue that could cause audio decode from movie files using frame-wrapped audio to be slow. This affected e.g. XAVC encoded MXF-files \[bug 50528]
* Fixed issue where the grade would 'jump' when the trackball was touched in Base Grade and Video Grade, for certain trackball positions \[bug 50872]
* Fixed crash when recalling from scratch pad to group grade selection \[bug 50366]
* Fixed an issue where MPEG-4 encoded QuickTime and MP4 movie files could decode frames in the wrong order. This fix can also slightly alter the look of this media in sequence strips inserted or refreshed after this fix \[bug 51294]
* Fixed an issue where Area Tracker and Area Tracker Perspective wouldn't track in low exposure contexts or with slight occlusions \[bug 50807]
* Fixed clamping applied in Shader operators which limited pixel values to +/- 10,000 \[bug 51114]
* Fix a crash when when conforming with some audio files \[bug 51293]
* Fixed clip alarm not indicating too-bright colours for some viewing colour spaces \[bug 51133]
* Improved handling of non-ASCII text pasted between Baselight and other Linux applications \[bug 50858]
* When writing OpenEXR files, "Tape" metadata is now stored as "reelName" to improve compatibility with other software \[bug 37445]
* Fixed a matte insertion issue. It was not possible to insert a matte on the second channel when a matte was selected \[bug 51195]
* Fixed a crash in Media Import Rules View when clicking on "Apply Rules to Shots" button \[bug 50643]
* Fixed incorrect "no conversion" message on Colour Space Journey View when the Sequence has a Video LUT and/or a Y'CbCr matrix \[bug 50740]
* Adaptec diagnostic now reports controller firmware version \[bug 50770]
* Changed behaviour when applying Media Import Rules during EDL import and FLUX Manage insert, to consider all new shots \[bug 51203]
* Fixed bug which could cause some FCP 7 XMLs generated via a "Modify XML" workflow to not load back into Baselight \[bug 50903]
