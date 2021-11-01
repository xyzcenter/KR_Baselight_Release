# 베이스라이트 릴리즈 노트 5.2.12238 (2019-08-22)

## 최신 기능 Baselight 5.2.12057이

### FilmLight Image Transfer **필름라이트 이미지 전송**

*   The new FilmLight Image Transfer (FLIT) service accelerates copying of media using FLUX Manage or fl-cp.

    FLIT automatically uses the fastest network link (or pair of links) connecting the source and destination systems, and will use almost all the network capacity, if the storage is fast enough.

    When writing image sequences to FilmLight storage, FLIT uses the most efficient layout for fast playback.

    Files copied using FLIT are unmodified by the copy (unlike image files in certain formats copied using older FilmLight tools).

    FLIT can copy files with restrictive permissions which can only be read or written as a result of extended group membership (unlike older FilmLight tools).

    FLIT can copy files between locations that are not both accessible to one single machine, for example from a removable drive on one system to a removable drive on another system \[bug 49593]

**     **  새로운 필름라이트 이미지전(FLIT, 플릿) 서비스는 플럭스 매지니또는 fl-cp 복사 프로그램르 사용하여 미디어를 복사하는데 가속화시킵니다. 플릿(FLIT)는 소스와 대상 시스템을 연결하는 가장 빠른 네트워크 링크(또는 쌍으로 된 링크)를 자동으로 사용하며, 스토리지가 충분히 빠른 경우 거의 모든 네트워크 용량을 사용합니다. 이미지 시퀀스(소스)를 필름라이트 스토리지에 쓸 경우 플릿는 빠른 재생을 위한 가장 효율적인 레이아웃을 사용합니다. 플릿을 (이전의 필름라이트 툴을 사용하여 특정 포맷의 이미지 파일과는 달리) 사용하여 복사한 파일은 복사로 인해서 수정되지 않습니다. 플릿는(이전 필름라이트 툴과 달리) 확장된 그룹 멤버쉽결과로 제한적은 권을 가지고 읽거나 쓸수 있습니다. 플릿은 하나의 단일 시스템에서 둘다 액세스할 수 있는 위치간의 파일을 복사할 수 있습니다. 예. 한시스템의 이동식 드라이브에서 다른 시스템의 이동식 드라이브로 이동

### Sequence Versioning **시퀀스 버전닝**

*   Added support for Sequence Versioning, which allows a Sequence operator to switch between different versions of the input media. It also allows the Sequence operator to scan for new versions of the input media and, optionally, switch to a new current version. This means that the user can quickly update a scene to reflect new versions of the input media with needing to conform or manually load media using FLUX Manage.

    Sequence Versioning comes in two forms:

    * Open Clip Versioning: Open Clip files are XML files (the format was developed by Autodesk) which refer to multiple versions of the media representing a clip. A separate Open Clip file is generated for each shot which requires sequence versioning and is then modified as new versions arrive. Baselight detects changes in Open Clip files and then scans for any new media referenced by the Open Clip. The simple file format makes them very easy to generate and update by 3rd-party tools, meaning that updating Baselight scenes to reflect new versions can be completely automated by using Open Clip files to reflect, say, the contents of a post house's asset database.
    * Filename Versioning: In this type of versioning, Baselight looks for sub-strings in file names which look like version numbers (e.g "\_v1" or ".V34") and replaces them with the new %V substitution. Then, when scanning for new versions, it detects all media which matches this template. The simplicity of this scheme makes it very easy to integrate in pipelines between VFX and finishing - the rendered VFX media simply need to be produced with a consistent naming scheme in which versioned filenames diffe only in version numbers \[bug 27173]
* Reflecting the fact that there are two types of Sequence Versioning, there are two sets of versioning-related settings in the EDL Import panel:
  *   Open Clip versioning: To conform using Open Clip files, switch on the "Use Open Clip" toggle in the "Media" section. Then, in the drop-down to the right of the button, select the directory containing the Open Clip files which refer to the media being conformed. Finally, if you're confident that _all_ the media to be conformed should be referenced by an Open Clip file, switch on the "Restrict" toggle, which ensures that media not referenced by Open Clip will ignored when scanning for media.

      It is still necessary to set one or more search directories to be scanned for media. At the very least, the search directories should contain the media representing the current version of each shot.

      Then, conform as normal. If any of the filenames of media in the search directory match filenames in Open Clip files, any Sequence operators generated will be sequence-versioned and pointed at the matching Open Clip file.
  * Filename versioning: If "Use Open Clip" is switched off, then the "Sequence Versioning" option becomes available. In it, select "Detect Versions in Paths and/or Filenames" to enable filename versioning. With it enabled, Baselight will look for version numbers in matching media and if they are found, any Sequence operators generated will be sequence-versioned, with the appropriate %V substitutions.
*   It is also possible to add sequence versioned media from FLUX Manage. Simply inserting media which contains version numbers will produce the "Sequence Versioning" dialog which allows the user to decide whether or not to use sequence versioning in the Sequence operators inserted.

    Known issues:

    *   It isn't currently possible to insert Open Clip files using FLUX

        Manage, other than via the "Browse for New Sequence" button in

        the Sequence operator UI.
    *   The FLUX Manage UI is not currently sequence versioning aware -

        it doesn't treat Open Clip (.clip) files as image files and only

        detects version numbers in the filenames when inserted into the

        timeline.
* If a Sequence operator is versioned, the Sequence UI changes to reflect this:
  *   If the sequence is Open Clip-versioned, the "File Name" edit

      field will contain the path to an Open Clip (.clip) file, rather

      than a path to image media.
  *   If the sequence is filename-versioned, the "File Name" edit field

      will contain a template with one or more %V substitutions.
  * A "Version" drop-down appears containing the versions of the input media detected so far. The current version's version name will be drawn in green. For Open Clip versioning, if a version couldn't be found, the filename of the version will be shown in grey, rather than blue.
  *   In the "Actions" menu, two additional options appear:

      *   Change to Current Sequence Version: If selected, then the

          Sequence's version is changed to be the current version in the

          Open Clip or the filename version with the highest number.
      *   Check for New Sequence Versions: Pops up a dialog which scans

          for new versions of the input media.

      Both of these actions work with grouped grading switched on, making it easy to update versions of multiple Sequence operators in one go.
* To scan for updated versions of _all_ the shots in the scene, the "Check for New Sequence Versions" action has been added to the "Baselight" menu. Selecting it pops up a dialog which will scan for new media and will also provide the following options:
  *   Add Category to Updated Shots: If "Yes", then the user can add a

      category to those shots which have new versions.
  *   Create Tab in Shots View: If the previous setting is "Yes", then

      the user has the option of creating a Shots view tab which will

      show those shots which have new versions.
  *   Set Current Version in Updated Sequence: If "Yes", all Sequence

      operators with new versions will be modified to point to the

      current version. Without this, the current version of all

      sequences will be left alone.
* To force a check for new sequence versions when the scene is opened, a new "Check for Sequence Version Changes" option has been added to the "General" tab in the Scene Settings view.
* To assist in creating and updating Open Clip files, the bl-openclip command line tool has been added. Usage information is available by running the tool with no arguments.

### IMF Packages **IMF패키지**

*   Added support for writing IMF packages of type Application 2e. The The DCP tab in the render panel has changed name from 'DCP' to 'DCP / IMF'. The type selector in this tab now contains the following IMF package options: **어플리케이션 2e 유형의 IMF패키지 생성지원이 추가되었습니다. 랜더 패널안의 DCP탭이 ‘DCP’에서 ‘DCP/IMF’로 변경되었습니다. IMF 패캐지 옵션에는 다음과 같은 선택이 가능합니다. **

    *   IMF: Application 2e: This option will create a package compliant with SMPTE 2067-21. **IMF: 어플리케이션 2e: 이 옵션은 SMPTE 2067-1을 준수하는 패키지를 만듭니다. **

        The video encoding is selectable between IMF profile or Broadcast Contribution profile JPEG 2000 with or without subsampling. The same set of video codec parameters that are available when rendering these profiles to the 'J2C' or 'IMF MXF' filetypes are available for this package type. **비디오 엔코딩은 서브샘플링이 있거나 없는 IMF 프로파일이나 브로드캐스트 컨트리뷰션 프로파일 JPEG2000을 선택할 수 있습니다. J2C나 IMF MXF 파일유형과 같은 랜더링이 가능한 패키지를 사용할때 같은 비디오 코덱 변수 세트를 선택할 수 있습니다. **

        Audio is optional and can be either 48kHz or 96kHz 24-bit PCM. Audio codec parameters can be used to set the language tag and the applied Multi Component Audio (MCA) tags are fully configurable using the audio codec parameters dialog in the render panel. The same set of audio codec parameters that are available when rendering the 'IMF Audio' filetype is available for this package type.

        The render panel will show an entry for 'IMF Colour Tag' in the 'Video' selector when selecting this package type. The IMF Colour Tag entry contains a text field which shows which tag will be applied, if any. It also has a 'Change...' button to assist in setting up output for the different colorimetry systems.

        MaxCLL/MaxFALL metadata can be added by enabling the analysis of these values in the render panel. **랜더패널에 이러한 분석을 활성화하면 MaxCLL/MaxFALL 메타데이터를 추가할 수 있습니다. **
    *   IMF: Application 2e with Dolby Vision Mezzanine: As above but the video file will be a Dolby Vision Mezzanine MXF with embedded Dolby Vision metadata. This option only appears if a Dolby Vision mastering display has been set in the scene settings. This package type will not display the 'IMF Colour Tag' entry in the 'Video' selector. The available colour spaces are restricted to the relevant Dolby mastering spaces and the bitdepth is locked to 12-bit.

        Analysis of MaxCLL/MaxFALL is always performed for this package type and metadata will be added to the created CPL.
    * IMF: Netflix SDR: This option is a subset of the "IMF: Application 2e" package type, with the available resolutions and codec options locked to match the SDR packages defined in Netflix Originals Delivery Specification version OC-3-2. The colour space must be Rec.1886: 2.4 Gamma / Rec.709, and the frame rate must be one of 23.976 / 24 / 25 / 29.97 / 30 / 50 / 59.94 / 60 for packages to be compliant.
    * IMF: Netflix HDR: This option is a subset of the "IMF: Application 2e with Dolby Vision Mezzanine" package type, with the available resolutions and codec options locked to match the HDR packages defined in Netflix Originals Delivery Specification version OC-3-2. The colour space must be ST 2084 PQ / P3 D65, and the frame rate must be one of 23.976 / 24 / 25 / 29.97 / 30 / 50 / 59.94 / 60 for packages to be compliant.

    All IMF package types will present an 'IMF' selector in the render panel that allows configuration of the package title, content kind, content version, issuer, originator and created file names. The package title will be copied to the annotation field in the created ASSETMAP, CPL, PKL and OPL files.

    The available DCP packages types are 'DCP: Interop' and 'DCP: SMPTE'. Wether to include audio was previously part of the DCP package type selection, but is now configured using the 'Enable Audio' toggle in the render panel \[bug 26866]
*   Added a new filetype called "IMF Audio". It allows 48kHz and 98kHz 24-bit PCM audio to be written to AS-02 MXF containers. MCA audio channel labels and soundfield group labels can be configured using the codec parameters dialog in the render panel. By default, the audio channel layout tags will be used to label individual channels where possible. Soundfield groups for stereo (ST), 5.1 (51) and 7.1 (71) channel audio will be applied if the output tags L+R, L+R+C+LFE+Ls+Rs or L+R+C+LFE+Ls+Rs+Lrs+Rrs are present. E.g. 'ST(L+R)' will be used for 2ch audio with output tags Left + Right.

    The 'MCA Configuration' entry in the codec parameters for this file type accepts the following audio channel labels: L : Left R : Right C : Center LFE : Low Frequency Effects Ls : Left Surround Rs : Right Surround Lss : Left Side Surround Rss : Right Side Surround Lrs : Left Rear Surround Rrs : Right Rear Surround Lc : Left Center Rc : Right Center Cs : Center Surround HI : Hearing Impaired VIN : Visually Impaired-Narrative M1 : Mono One M2 : Mono Two Lt : Left Total Rt : Right Total Lst : Left Surround Total Rst : Right Surround Total S : Surround

    *   : No label

        NSC001 - NSC128 : Numbered Source Channel

    The available soundfield group labels are: 51 : 5.1 71 : 7.1DS SDS : 7.1SDS 61 : 6.1 M : 1.0 Monaural ST : Standard Stereo DM : Dual Mono DNS : Discrete Numbered Sources 30 : 3.0 40 : 4.0 50 : 5.0 60 : 6.0 70 : 7.0DS LtRt : Lt-Rt 51Ex : 5.1EX HA : Hearing Accessibility VA : Visual Accessibility

    MCA configuration is specified using a comma separated list of audio channel labels and soundfield group labels. Soundfield group labels define the audio channels that belong to the group by a comma separated list of audio channel labels within parentheses.

    Labels are applied in the order they occur in the configuration string. For example, to explicitly tag a L+R stereo configuration, set the MCA configuration entry to 'ST(L+R)'. This will add the audio channel label 'L' to the first channel, and 'R' to the second. Both are then wrapped in the soundfield group label 'ST'.

    A more complex MCA configuration example could look like 'ST(L,R),DNS(NSC001,NSC002),-,VIN'. This will label channels 1-2 as being the left and right channel of a stereo configuration. Channel 3-4 will be labeled as numbered source channels 1 & 2 and wrapped in a soundfield group label of the "Discrete Numbered Sources" type. Channel 5-6 will be untagged and tagged "Visually Impaired-Narrative" respectively. Neither channel 5 nor 6 will be part of a soundfield group label.

    If there are more channels than tags, remaining channels will be untagged. This means that a single '-' can be used to disable MCA tagging completely.

    The codec parameters for language, title, title version, content kind and element kind will set the corresponding MCA tags for spoken language, title, title version, etc, in each defined soundfield group label \[bug 26866]

### Miscellaneous 기타기

* The command-line copying tool fl-cp has been rewritten to use the fluxc command to enqueue copies in the Operations Queue and then to monitor their progress \[bug 50601]
* Updated the Sony RAW SDK to version 3.3.0, which adds support for reading X-OCN 4K 2.39:1 bitstreams \[bug 51227] **소니 RAW(로우) SDK 버전 3.3.0 지원 : 이를 통해서 X-OCN(소니 고유 로우 포맷)의  4K 해상도 2.39:1 비율(4096x1716)을 지원**
* Added support for reading additional metadata from Sony MXF-files, including Cooke protocol lens metadata \[bug 51855] **소니 MXF파일에서 쿠크 렌즈 메타데이터기록되어 있을 경우 읽을 수 있어서 편리하게 표준/와이드/광각을 사용했는지 확인이 가능**
* Improved metadata-based input colour space selection for EXR files which were written by Baselight/Daylight \[bug 51808]
* QuickTime colour space tags ('nclc' and 'gama') are now used to assist metadata-based input colour space selection \[bug 51981]
* The interpretation of QuickTime colour space tags ('nclc' and 'gama') are now shown as metadata in FLUX Manage \[bug 51987]
* Added support for reading Avid DNxUncompressed MXF files \[bug 51554]
* In Render View, when using a Render Frame Rate which is different from the scene's Working Frame Rate, "Frames To Render" now always shows frame numbers at the Working Frame Rate, and text alongside "Render Frame Rate" now indicates the frames that will be rendered at the Render Frame Rate \[bug 38602]
* Added options in Setup editor for choosing 48, 50 and 60fps timeline timecodes \[bug 52015]
* Updated to ARRIRAW SDK v5.5. This adds support for the ALEXA Mini LF camera \[bug 52385]
* Added "Document Library" to the Help menu, which opens the Document Library page of the FilmLight website \[bug 52145]
* Updated to DNxHD/DNxHR SDK version 2.5.2. This includes bug fixes \[bug 52326]
* Added support for RTX 2080 Ti graphics card, using the 418.56 driver \[bug 51764]
* Fixed an issue that affects the browsing of movies with frame rates that are greater than 255 \[bug 52039]

## 버그 개선 Baselight 5.2.12057 이

* Improved Texture Highlight help text \[bug 50241]
* Fixed an issue with Sony MXF-files where the format frame rate would be used instead of the capture frame rate \[bug 51373]
* Added a note about Looks to FilmLight's scene template tooltip \[bug 51752]
* Added a customise option in the Shape operator to set a default intershape operation \[bug 51528]
* Increased the default exposure of Photo RAW files with one stop when blending highlights. This makes exposure match better when switching between the two highlight handling modes 'Blend' and 'Clip' in the Photo RAW Parameters operator \[bug 51753]
* Fixed hang in Shots View when trying to substitute a column value into itself \[bug 51710]
* Fixed incorrect display and behaviour of selected shots button in Media Import Rules View \[bug 51766]
* Fixed issue where bypassing all wasn't correctly updating in Layer View \[bug 51926]
* Fixed indication of gamma curve EOTF in Render View Colour Space Tagging menu \[bug 51956]
* Fixed Smart Paste pasting onto source stack creating strange gaps in stack \[bug 52026]
* Fixed crash when conforming using 'static text' in a Media Import Rule with 'Setup for tape ingest' \[bug 51311]
* Fixed sorting of some Shots View columns not working after editing them after a conform \[bug 51800]
* Fixed Media Import Rules View not enabling/disabling correctly \[bug 52019]
* Fixed crash in Layer View when updating selections \[bug 51892]
* In the Text operator shortened escape strings, such as '%F' for %{TimelineFrame}, now update correctly \[bug 52072]
* Fixed failures on some Baselight FOUR/EIGHT systems, typically seen when accessing a file system mounted on the io node \[bug 52066]
* Fixed a crash when loading a font file that doesn't specify a style name \[bug 52108]
* Fixed 50fps timecode calculation in some edge case sequences \[bug 51836]
* Fixed issue in layer number selector whereby the thumbnails were too large \[bug 51805]
* Layer names shown in the Layer View are now clipped correctly when resizing and the name doesn't fit the thumbnail \[bug 51763]
* Fixed issue in Gallery causing comments to disappear when they become too long \[bug 51525]
* Fixed issue where Layer View controls would be disabled when Cuts View was not shown \[bug 52276]
* Fixed delays caused where a badly-configured DNS takes a long time to give a negative response \[bug 52064]
* Fixed crash in bl-conform when source directories were not expressed using volume names \[Bug 51934]
* Allow selection of timecode framerate format when conforming 50fps AAFs \[bug 52007]
* Fixed bug where explicit layer paste on Slate could leave the paste operation in progress \[bug 52339]
* Fixed missing SignalRange entry in Dolby Vision XML \[bug 52361]
* Fixed crash when changing keyer type in a layer \[bug 52394]
* Fixed error on Dolby Vision View if it is opened before a scene is open \[bug 52424]
