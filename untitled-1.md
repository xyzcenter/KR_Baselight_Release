# 베이스라이트 릴리즈 노트 5.2.12381 (2019-09-26)

## 최신기능 (Baselight 5.2.12356이후)

### Dolby Vision **돌비비젼**

*   Added support for Dolby Vision v4.0 in Analysis, Trim, Software CMU and XML export.

    v4.0 Analysis adds an "L3 Mid Offset" option. v4.0 Trim adds additional advanced trim controls and six-vector secondary controls.

    v4.0 behaviour is enabled from Scene Settings View. Note that switching a scene between different CMU versions will delete all existing Dolby Vision Analysis and Trim strips \[bug 50761]\
    **  분석, 트림, 소프트웨어 CMU, XML추출 등의 돌비비젼 버전4.0 지원 기능을 추가했습니다.   버전 4.0의 분석(Analysis)기능에는 L3 미들 오프셋 옵션이 추가되었습니다. 트림에서는 추가적인 향상된 트림 컨털과 6벡터 세컨더리 컨트롤이 가능합니다.   4.0 방식에서는 씬설정뷰가 가능합니다. 참고로 다른 CMU버전으로 씬을 스위칭할 경우 모든 돌비비젼 분석 및 트림스트립이 삭제됩니다.**

### Toggle Previous Operator 토글(**이전 오퍼레이터로 스위칭)**

*   Added the ability to toggle between the current and the previous operator for quick and easy adjustment of two operators. \
    **  현재와 이전 오퍼레이터사이에서 빠르고 쉽게 두 오퍼레이터 적용이 가능하도록 토글(스위칭)이 가능하게 되었습니다.**

    'Toggle Previous Operator' is available on the Select menu, the "=" key, Chalk and on the Blackboard 2 and Slate default layouts.\
    **  선택 메뉴에서 '이전 오퍼레이터로 스위칭'을 가능하게 할 경우 "=" 키나 블랙보드2/슬레이트 기본 레이아웃에서 선택가능합니다.**

    For Blackboard 1 and Blackboard Classic, operators can be toggled by holding Inside/Outside followed by any operator to the right of the Inside/Outside button \[bug 51940] \
    **  블랙보드1이나 블랙보드 클래식에서는 인사이드/아웃사이드 버튼을 누른 상태에서 인사이드/아웃사이드 버전의 오른쪽의 어떤 오퍼레이터로 스위칭할 수 있습니다.**

### Final Cut Pro X XML Conform and Modify

*   Added support for conforming Final Cut Pro X .fcpxml files, and modifying them to reference new media rendered from Baselight.

    Conform is supported from FCPXML files in the same manner as AAFs, XMLs, etc. Supported effects include dissolves, transforms and retimes.

    To update an FCPXML with rendered graded media:

    * Perform a Timeline Sort using the "FCP XML Rendering" tab
    *   Select the "Movies, Video+Audio" tab in the Render View, choose

        File Type as a Quicktime Movie, and check the "Modify FCPXML"

        button
    *   The updated FCPXML file will be written to the specified location

        once the render is finished \[bug 18628]

### Input Methods **입력방식**

*   On Linux, X11 Input Methods (see the desktop System->Preferences-> Input Method menu) can now be used to enter non-ASCII characters into text fields in the application.

    For example this permits using the AltGr modifier key for European characters like "ß", or by using a more complex input method for CJK characters.

    This can be used for Burnins or Text strips when a suitable font is chosen for the text, or when entering filenames - but note that the characters may not be shown in the user interface \[bug 51875]\
    **  리눅스에서 X11 입력방식(데스크탑의 시스템->설정->입력방식메뉴(Input Method menu)에서) **

    **  어플리케이션의 텍스트 영역에서 비 ASCII 캐릭터를 사용할 수 있게 되었습니다.   예를 들면, "ß" 유럽캐릭터를 위해서 AltGr(오른쪽Alt) 수정키를 사용하여 작성할 수 있거나 CJK(중국일본한국)캐릭터를 위한 복잡한 입력방식을 사용을 허용합니다.   이는 적절한 폰트가 텍스트 또는 파일이름 입력을 우해서 선택된 경우, 번인 또는 텍스트 스트립을 **

    **  사용할 수 있게 합니다. 그렇지만 유저 인터페이스에서는 캐릭터가 보이지 않습니다.**

### Miscellaneous **기타기능**

* Updated to Blackmagic RAW SDK 1.4. This adds support for the Blackmagic Pocket Cinema Camera 6K \[bug 51786] **  블랙매직 로우 SDK 1.4가 업데이트 되었습니다. 블래매직 포켓 시네마 카메라 6K위한 기능 지원입니다.**
* Added option to disable active grade tooltips on the timeline. Right-click on the timeline to toggle "Display Active Grade Tooltip" \[bug 52255] **  타임라인에서 활성화된 색보정 툴팁을 비활성화 할 수 있는 옵션을 추가했습니다. 타임라인에서 마우스 우클릭하여 "Display Active Grade Tooltip(활성화된 색보정 툴팁 보기)"를 스위치하여 비활성화 할 수 있습니다.**
* Updated the Sony XAVC Encoder to version 1.1.11. This improves parallel processing \[bug 52305]**  소니 XAVC 엔코더의 1.1.11 버전으로 업데이트 했습니다. 이는 병렬 프로레싱을 개선시킵니다.**
*   Movie formats that do not have integrated audio, e.g. 'DCI MXF' and 'IMF MXF', are now available under the 'Movies Video+Audio' tab in the render panel. Renders for these filetypes can now be setup to output audio to a separate file \[bug 39852]**  무비포맷에서 오디오가 포함되지 않은 예를 들면 DCI MXF와 IMF MXF의 경우 랜더 패널에서 **

    **  Movie (Video+Audio)에서 랜더가 됩니다. 이와 같은 파일 타입의 랜더에서는 출력된 오디오의 분리된 파일형태의 설정을 할수 있습니다.**
* Modify AAF now allows clips to be split in the Baselight timeline before updating an AAF with Baselight grades; these splits are reflected in the updated AAF \[bug 26315]
* Updated bl-openclip to support Open Clip files expressed with relative paths \[bug 52373]
* Improved the detection of sequence versioning patterns during a conform to avoid as much as possible any ambiguity \[bug 52102]
* FLUX Manage now shows "Grade Data" information when media has embedded BLG, CDL or LUT grades, and new filter tiles allow filtering based on this information \[bug 52049]**  플럭스매니지(Flux Manage)에서는 미디어에 임베디드된 BLG, CDL, LUT 색보정 데이터에서 색보정 데이터 정보를 보여주며, 새로운 필터 타일에서는 이 정보기반으로 필터링을 가능하게 합니다. **
* Additional metadata, including per-frame metadata, is now shown for non-HEVC Canon MXF movies \[bug 51755]**  프레임별 메타데이터를 포함한 추가 메타데이터가 있는 비 HEVC 캐논 MXF 무비 파이르 볼 수 있게 지원합니다.**
* Added Transform operator Customise menu option for enabling & disabling 'Show Input' on tracker strips created for stabilisation \[bug 52715]
* Allowed a sequence of images or a movie to be potentially part of several Open Clip files during a conform \[bug 52603]

## 버그 개선 (Baselight 5.2.12356이후)

* The sequence of Panorama encoders has been reordered to match the GUI layout. Each encoder has a reset button added underneath in order to be used on a Blackboard \[bug 52217]
* The controls for Grid Warp control points have been moved to the left-hand side of the Blackboard layout in order to be more clear \[bug 52165]
* In the Colour Temperature operator, the default minimum and maximum values of Old Temp have been changed to 3200K and 9800K respectively \[bug 51529]
* Fixed crash in Base Grade graph pop-up menu \[bug 52107]
* Fixed incorrect undo text in the edit menu, after an edit that didn't actually change anything \[bug 52288]
* Fixed 50fps timecode calculation in some edge case sequences \[bug 51836]
* Fixed crash when updating certain Premiere XML files \[bug 50286]
* Fixed occasional crash in Layer View when toggling large matte view when a scene is closed \[bug 52085]
* Correct timecode is now added to IMF Audio MXFs. This applies both to audio files rendered as part of IMF packages and audio files rendered using the "IMF Audio" filetype \[bug 52348]
* Fixed the reported resolution and decoded image area of Nikon D4 NEF-files to match the decode of other software such as Finder and Photoshop. Previously, the image was shifted to the right with loss of image data on the right hand side. This change affects any existing scenes using Nikon D4 NEF-files \[bug 52310]
* Fixed an issue where audio OpAtom MXF files could fail to read a few audio samples at the end of the file. This could cause audible clicks at strip boundaries at some frame rates \[bug 52284]
* Fixed potential crash when clicking on/selecting existing Despot operator rectangles after a Despot strip had been split/temporally offset \[bug 17238]
* Fixed issue where not all Color Correction effects would be removed from clips when updating an AAF with Baselight grades \[bug 50844]
* Fixed an issue where highlights in DNG and Photo RAW files could change colour when changing the 'Always Decode At Max Quality' toggle button. The 'Always Decode At Max Quality' option is no longer shown for these files, as they're always decoded at max quality to avoid this issue. Existing sequence strips will retain the old behaviour \[bug 52236]
* Fixed an issue where switching Chalk layouts would cause buttons to disappear \[bug 52430]
* Fixed an issue that prevented 'Sequence + Audio File' renders from scenes with a Dolby Vision mastering display set in the scene settings \[bug 52435]
* Fixed an issue that could cause renders of the filetype 'DCI Audio' to fail with an internal error when the scene working rate was not 24fps \[bug 52442]
* The default highlight reconstruction threshold in the DNG Params operator has been improved, which fixes issues with magenta or washed out highlights for some DNG-files \[bug 52336]
* Layer View now remembers which stacks were shown when restarting \[bug 52037]
* Fixed an issue that caused volumes to be temporarily unavailable \[bug 52513]
* Fixed rare crash when attempting to view the stack of a current shot within the Gallery \[bug 52538]
* Associate OP-Atom audio files with the appropriate video sequences during conform \[bug 49986]
* Fixed occasional crash in Text operator \[bug 51180]
* Fixed an issue when an Open Clip file had relative path versions in its own directory \[bug 52389]
* Fixed a bug in the Sequence Operation UI with the version drop down displaying incorrectly "Not a known version" \[bug 52371]
* Fixed a potential bug when scanning the versions of a sequence versioning pattern and not being able to disambiguate a given version Id \[bug 52417]
* Fixed an issue with "Strip Auto Select On" when moving to a new shot and not selecting a strip in an equivalent substack as the previous selected strip when it was possible \[bug 51762]
* Fixed an issue that could prevent some crash reports from being sent to FilmLight \[bug 52093]
* Fixed issue whereby some AAFs would fail to load \[bug 52203]
* Fixed issue with Media Import Rules View and read only scenes \[bug 52580]
* Fixed an issue with IMF CPLs where the IntrinsicDuration and SourceDuration entries for the video track in HDR IMF-packages was incorrectly set to 0 \[bug 52589]
* Added additional metadata in the picture essence descriptor of IMF MXFs. This fixes XML-schema validation issues for IMF-package CPLs \[bug 52590]
* Fixed issue where database backup diagnostic would fail on systems set with a non-English default language \[bug 52605]
* Changed colour space assigned to Rec.709 QuickTime movies based on metadata; previously it used "Rec.709 Camera: \~1.95 Gamma / Rec.709", now it uses "Rec.1886: 2.4 Gamma / Rec.709" \[bug 52604]
* Fixed tooltip text for "Rec.2020: ST 2084 PQ / Rec.2020 / 108 nits" and "Dolby: ST 2084 PQ / P3 D65 / 4000 nits" colour spaces \[bug 52005]
* Fixed problems with Media Import Rules View and read-only scenes \[bug 52580]
* Fixed an issue where audio could fail to render with a warning about source data not containing the required samples \[bug 52124]
* Fixed issue where numeric keypad bumps would lag in Film Grade \[bug 52619]
* Fixed an issue where attempting to submit a render with duplicate filenames would produce an incorrect error message \[bug 51884]
* Fixed network connection issues when a 'share' volume was defined within a zone in volume.cfg \[bug 52650]
* Fixed thumbnail issues with RMF media \[bug 52666]
* Fixed errors when pasting a Dolby Vision Trim strip into a scene that has no Dolby Vision Mastering Display set \[bug 52663]
* Fixed some Matchbox shaders not appearing in the Shader dialog \[bug 52628]
* Improved appearance of Paint strokes while drawing additional strokes \[bug 52488]
* The extraviewingconditions file is no longer used \[bug 52221]
* Improved error message when using unsupported timecode rates when exporting CMX EDLs \[bug 52012]
* Some GPU errors, notably out-of-memory, are now reported rather than causing a crash \[bug 51208]
* Fixed errors caused by changing workspace while dragging \[bug 50171]
* Improved the decode speed of some codecs using planar Y'CbCr in QuickTime and MXF containers. This improves the performance of Grass Valley HQX in particular \[bug 24375]
* Fixed crash after changing the preference database during application startup \[bug 52437]
* Improved error messages from database connection errors \[bug 52542]
* Fixed multi-paste not applying the colourspace when pasting from BLGs \[bug 51473]
* Fixed a bug after a conform with Open Clip, where missing versions in the Sequence operator's versions drop down could potentially have a wrong name \[bug 52582]
* Fixed a bug in the manual selection of movies/sequences per event in EDL-import view \[bug 52601]
* Fixed crash in some uses of the Paint operator \[bug 51075]
* Fixed a potential crash while detecting sequence versioning after inserting media from FLUX Manage \[bug 52560]
* Fixed %C being lost from Sequence filenames after manual edits are made \[bug 52748]
* Fixed a rendering artefact when metadata-driven burnin text is empty \[bug 52402]
* Fixed a potential crash when upgrading 4.4m1 jobs where every scene in the job is unable to be upgraded \[bug 51820]
* Fixed an occasional crash in flit service when local-to-local copy is cancelled \[bug 52683]
* Fixed crash when dynamically generated burnin text is empty \[bug 52761]
* Fixed OFX GPU memory errors \[bug 52759]
* Fixed error changing a Sequence to use new media, when there was no original media, for example due to conforming with "Setup for Tape Ingest" \[bug 52757]
* Fix crash where Scene Detect is running in one scene and swapping to another cursor in a different scene \[bug 52740]
