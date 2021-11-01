# 베이스라이트 릴리즈 노트 5.2.12568 (2019-11-08)

## 최신 기능 (Baselight 5.2.12424이후)

### Volume Indexing  **볼륨 인덱싱**

*   Baselight and Daylight now support using volume indexes. A volume index is a database of the files on a volume, along with all the metadata that is known about image files (e.g. file resolutions, timecodes etc).\
    **  베이스라이트와 데이라이트는 볼륨 인덱싱을 지원합니다. 볼륨인덱싱은 볼륨의 파일을 데이터베이트화 합니다. 예를 들면 파일 해상도, 타임코드등의 메타데이터를 포함한 정보 등이 있습니다.**

    A volume index can significantly improve the speed of operations including EDL conform and browsing for media, and it can enable otherwise impractical operations such as using a FLUX Manage filter to query all the media on an entire multi-terabyte volume to find all the shots using a particular codec, or with a particular tape name, or over a certain length etc. The Descend option in FLUX Manage View is greatly enhanced through the use of indexed volumes.

    A new button on the file browser to the left of the Bookmark button (with a star icon) indicates whether a volume index is available and has been used, and can be clicked to choose whether to use the index or not. The same star icon is shown on the volume drop-down on file browsers to indicate when the volume is indexed.

    Volume indexes are maintained by a FilmLight service named "index", which also caches thumbnails for all the media to further accelerate FLUX Manage. As the volume content is modified, the index service will automatically update its database with the new content.

    Volume indexes will be enabled in a future Baselight release for local /vol/images RAID volumes on Linux.

    If you wish to enable the index now, edit /usr/fl/etc/volume.cfg and add a "limit images index=1" line below the "dir images" line for the local zone, then run "sudo fl-service index restart".

    Other mounted volumes cannot be indexed - this includes media drives and PFS volumes on Baselight FOUR/EIGHT systems. Third-party storage (e.g. SANs) can be indexed through the purchase of a FLUX Index product; please contact your local FilmLight sales agent for more information \[bug 49472]

### Gallery Import and Export **갤러리 임포트와 익스포트**

*   Galleries can now be exported with reference frames to a .blgallery archive file. These Gallery archive files can then be imported directly into Gallery View on a different system. Importing a Gallery archive file will add its scene to your Gallery Job and add offline reference frames to be found by the scene.

    The Gallery '+' button has been replaced by an action menu to better represent its new actions \[bug 37125] \
    갤러리의 레퍼런스 이미지를 .blgallery 아카이브 파일로 추출할 수 있습니다.&#x20;

    &#x20; 이 갤러리 아카이브파일을 다른 시스템의 갤러리뷰 안에 직접 임포트 할 수 있습니다. 불러와진 갤러리 아카이브 파일은 잡:갤러리안에 추가되어 오프라인 레퍼런스 프레임으로 추가되어 집니다.   갤러리의 '+' 버튼은 새로운 액션을 더 잘 표현하기 위한 액션메뉴로 대체되었습니다.   갤러리의 '+' 버튼은 새로운 액션을 더 잘 표현하기 위한 액션메뉴로 대체되었습니다.
* Sequences and stills can now be inserted directly into Gallery scenes using either drag & drop from FLUX Manage or from the right-click menu \[bug 43970]\
  **  **시퀀스나 스틸이미지는 플럭스 툴에서 드래그앤 드롭이나 마우스 우클릭메뉴를 통해서 갤러리씬을 직접 입력할 수 있습니다.

### Miscellaneous **기타기능 **

* Added "Toggle Marks for Selected Strips" to the Marks menu. This adds a mark of a chosen type/category to a selection of strips. The mark is applied only on the strips relevant to the type (e.g. Timeline mark) and will be placed at the start of each strip. When applied to a selection of partially marked strips, the relevant mark will be applied to unmarked strips, while already-marked strips will be left unchanged. Multiple categories are supported for Grade and Shot marks, while Timeline marks support only one category. Optional default/custom notes are applied to the whole selection \[bug 52588]
* Updated the IMF package types 'IMF: Netflix SDR' and 'IMF: Netflix HDR' to conform with Netflix Originals Delivery Specifications OC-3-3. This update only involved a change to the available language codes \[bug 52599]\
  ** IMF 패키지 타입이 'IMF: Netflix SDR', 'IMF: Netflix HDR' 에서 넷플릭스 오리지널 딜리버리 규격 OC-3-3이 업데이트 되었습니다. 이 업데이트는 가능한 언어 코드 변경에 유효합니다.**
* Added support for reading Grass Valley HQX encoded MXFs \[bug 52753]
* Added -queue option to fl-cp which prevents it from waiting while a copy operation completes \[bug 52805]
* Added -raw option to fl-imageinfo which causes it to output unnormalised ("raw") metadata in JSON format \[bug 49537]
* Updated to DNxHD/DNxHR SDK version 2.5.3. This includes bug fixes \[bug 52743]
* Added "has metadata" tile to FLUX Manage, to allow filtering based on whether sequences have a value for a given metadata key \[bug 52771]
* Added "image aspect ratio" tile to FLUX Manage, to allow filtering and sorting based on the overall sequence aspect ratio \[bug 52845]
* Added support for reading additional audio codecs in AVI files \[bug 52754]
* Added split function to Shots View Column Expression. The function allows splitting of an expression based on a delimiter. For example @split{%{Tape},_, 0} will return the first matching instance of the result of separating the Tape column with character '_' \[bug 52671]
* Copies submitted as root result in files being read and written as user 'nobody' by FLIT. This is now logged as a warning in the queue \[bug 53001]
* "Select All Strips Of Type", renamed as "Select All Operators of Type" and now includes operators within Layers as well as dedicated strips. The submenu includes two options: "Only Include Modified Operators In Layers", which constrains the selection of Layers to those which have a modified instance of the operator in question, and "Change Selected Operators In Layers", which causes the current selection of relevant Layers to be changed to the specified operator type. "Select All  Operator" also follows the rules specified by these two options \[bug 47320]
* Updated flos-tools package, improving fl-setup-raid support for 315x RAID controllers \[bug 52526]
* Added dpm diagnostic support for MSCC 315x controllers \[bug 49810]

## 버그 개선 (Baselight 5.2.12424이후)

* Fixed an issue that prevented directly editing mark note text when "Display All Note Text" was selected \[bug 52405]
* Fixed a crash triggered by using long paths for the KDM in the DCP Params strip \[bug 52574]
* Disabled the "Include Colour Space in Layer 0" menu option when the "Include Layer 0 Operations" is off \[bug 52652]
* Fixed issue with Layer View where stacks would appear blank after changing workspaces \[bug 52611]
* Fixed occasional crash when attempting to select a layer number for results blending \[bug 52681]
* Audio Sync View now syncs audio with selected sequence strips as well as selected shots \[bug 51903]
* Fixed rare crash caused when closing scenes with an active Layer View \[bug 52816]
* Fixed rare crash when finishing a drag and drop via Layer View \[bug 52647]
* The Area Track Perspective button is now mapped onto the desks where required \[Bug 47469]
* Improved reliability of the disk controller performance diagnostic test \[bug 52948]
* Fixed issues with Layer View automatic scrolling when holding layers to paste. Scrolling now works correctly and increases in speed when hovering closer to the top or bottom of the current stack \[bug 52802]
* Fixed fl-cp no longer creating the destination directory \[bug 52855]
* Fixed a crash when GPU JPEG 2000 accelerated decode failed while reading MXF files \[bug 52871]
* Render View now shows a warning if a Netflix IMF deliverable is configured using legal range data \[bug 52764]
* Fixed failure to render a scene whose name starts with a space \[bug 52539]
* Fixed a decode issue affecting Sony AVC-LongGOP encoded MXF files with dynamic metadata \[bug 52881]
* Fixed crash when updating an AAF containing a Motion Strobe retime \[bug 39256]
* Fixed crash when opening Render View \[bug 52882]
* Fixed occasional crash related to colour space menus \[bug 52800]
* The Working Format on the New Scene dialog no longer resets when choosing a built-in scene template \[bug 52783]
* Fixed crash in flux service \[bug 52540]
* Fixed crash in Shots View \[bug 52502]
* Fixed a crash when rendering IMF packages on macOS \[bug 52762]
* Fixed FCPXML import of projects with references between nested sequences \[bug 52810]
* Fixed an issue where the presented duration of audio files in FLUX Manage was rounded to the nearest second \[bug 52359]
* Fixed potential input versioning crashes when:
  *   detecting sequence versioning in the EDL Import View and FLUX

      Manage View
  * synchronising/loading input versions \[bug 52867]
* Fixed issue where the frame rate and field order were included in the layer 0 operators paste action. These are now no longer included \[bug 52652]
* Fixed crashes when many strips are set to cache in a single stack \[bug 26411]
* Fixed error when parsing a generator with a transition in FCPXML files \[bug 52796]
* Fixed Blackboard Select and Arrow key to only select up to the nearest selected shot to match the manual explanation \[bug 51955]
* Fixed a crash reading 4:2:0 and 4:2:2 JPEG 2000 encoded MXF files. Sequence operators affected by this will now produce an error message about missing blob metadata, and need to be refreshed to decode correctly \[bug 52944]
* Improved support for older FCPXMLs \[bug 52803]
* Fixed crash in flit service when several copies are running simultaneously \[bug 52962]
* Fixed incorrect errors reported when attempting to read truncated QuickTime files \[bug 21581]
* Legal to Full scaling is applied in EDL Import in the same manner as when inserting a sequence via FLUX Manage \[bug 52527]
* Changed automatic scrolling when dragging shots over the Gallery and Cuts View to be more smooth \[bug 52849]
* Fixed database errors being misreported as "Waiting for another process" \[bug 52992]
* Fixed issues when working with large numbers of Blackmagic RAW files \[bug 53011]
* Fixed errors in copying media with '%' in its filename or folder path, and when attempting to copy media which is no longer present when the copy runs \[bug 53008]
* Fixed errors in renaming media with '%' in its filename or folder path \[bug 53100]
* Fixed crash pressing / key to filter a menu \[bug 52894]
* Fixed crash when inserting or removing a local media drive \[bug 52921]
* Fixed occasional crash in flux service \[bug 52540]
* Fixed crash in formats editor \[bug 45892]
* Fixed audio offset when conforming media with OP-Atom audio \[bug 52613]
* Do a better job of importing Premiere XMLs with bad record in/out data in dissolves \[bug 52388]
* Fixed crash in flit service when a copy is cancelled \[bug 53016]
* Fixed missing ARRI metadata from ProRes MXF files written by ARRI cameras \[bug 53054]
* Fixed Transform Alarm Overlay to deal with stacks containing explicitly cached strips \[bug 50738]
* Fixed ICC colour profile being copied from TIFF input media to rendered TIFF files \[bug 52393]
* Reverted a change to the decode of MXF and QuickTime files with Y'CbCr data that was introduced in build 5.2.12381 and later. This fixes a number of decode errors and crashes related to reading these files. In particular, this caused Sony SStP MXF files to fail with an error message about failing to decode macro-blocks. Affected Sequence operators may need to be refreshed to decode correctly \[bug 52960]
* Provided a means to address errors when interacting with non-UTF-8 filenames in FLUX Manage, by re-initialising the operations queue database \[bug 52024]
* Improved the performance of the command line 'fsdb-ls' command when using an index \[bug 52295]
* Fixed tracker crash after entering an invalid tracker name in the tracking section \[bug 40526]
* Fixed a crash in FLUX Manage file scanning when using an index \[bug 52844]
* Fixed a potential crash when browsing for a new sequence in the Sequence operator UI \[Bug 52791]
* Fixed potential crash when selecting 'Dual Output Layout' display mode when working with stereo scenes \[bug 51579]
* In the Sequence operator UI, when selecting a given version, ensured its path is on the right volume when the image container has changed \[bug 52749]
* Fixed potential Sequence operator out of strip range offset issues after :
  *   browsing for a new sequence (The in/out points were also not

      considered)
  *   selecting a new input version

      \[bug 52587]
* Fixed slate-update-firmware version detection \[bug 52038]
* Fixed conform failing when using "" and a "%D" (file name) substitution, when an event in the EDL didn't include a filename \[bug 52807]
* Fixed crash encountered when using the version 418 nvidia driver \[bug 52562]
* Fixed OFX memory allocation error on systems with GPUs with more than 8GB VRAM \[bug 53062]
* Fixed a bug when editing the file name field in the Sequence operator UI. It was not applied on the grouped grading selection anymore \[bug 52937]
* Fixed a bug when editing the file name field in the Sequence operator UI. It was not working for a sequence of image matching several frame ranges \[bug 52427]
* Fixed an issue with FLIT network negotiation which could fail if two machines had interfaces on the same subnet but they were unable to communicate over that subnet \[bug 52918]
* Fixed an issue that could cause a crash when similarly named sequences are browsed in FLUX Manage \[bug 53059]
* Fixed a crash in FLUX Manage when copying multiple folders between panes \[bug 50240]
* Fixed a crash when rendering using XAVC codecs \[bug 53218]
* Fixed an occasional hang in flit service \[bug 53210]
