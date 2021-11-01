# 베이스라이트 릴리즈 노트 5.2.13010 (2020-03-10)

## 최신 기능 (Baselight 5.2.12809이후)

### Blackboard Classic 블랙보드 클래식

*   Blackboard Classic is a new control surface. It's connected via a

    single Ethernet cable directly to the Baselight system. Once

    switched on the Blackboard will boot and then display  its host

    name and IP address on the leftmost screen. Baselight preference

    needs to have the external control section set to Blackboard

    Classic, and the IP address (or machine name) set in the

    "Input Devices - Blackboard Classic IP" addresses section. The Wacom

    tablet will not work until the IP address has been set in

    preference. Once set, run bl-config-xorg and bl-config-tablet to

    setup the Wacom and restart X. Once the Blackboard Classic is

    configured you can start Baselight. Once the Blackboard Classic is

    configured you can start Baselight and it'll act just like the

    original Blackboard \[bug 53975]

블랙보드 클래씩(Blackboard Classic)은 새로운 컨트롤 판넬입니다. 베이스라이트 시스템과 단일 이더넷 케이블로 직접 연결할 수 있습니다. 블랙보드의 뒷면 스위치를 끼면 부팅될 것이며 그후 왼쪽 스크린에 호스트네임(hostname)과 아이피 주소가 나올 것입니다. 베이스라이트 설정창에서 외부 컨트롤섹션에서 블랙보드 클래씩을 선택하고 아이이주소 (또는 이름)을 "입력 디바이스- 블랙보드 클래씩 아이피" 영역에 입력합니다. 설정창에서 아이피 주소를 설정하기 전까지 와콤 타블렛은 작동하지 않을 것입니다.&#x20;

설정시, bl-config-xorg 와 bl-config-tablet을 실행하고 그래픽모드를 재시작합니다.(Ctrl+alt+backspace 또는 재부팅) 블랙보드 클래씩의 구성이 완료후 베이스라이트를 실행할 수 있습니다. 베이스라이트에서 오리니절 블랙보드와 같이 블랙보드 클래씩을 사용할 수 있습니다.

### AJA Hardware Support AJA하드웨어 지

* 맥OS에서 AJA15.0이상의 드라이버 추가 지원
* AJA Kona5, Kona1, Io4K plus 추가 지원
* AJA Kona5에서 4K 스테레오 비디오 모드 추가 지원
* AJA Kona5에서 4K 120p및 4K Stereo 120p 비디오 모드 추가 지원
* AJA Kona5에서 8K UHD 및 DCI 비디오 모드 추가 지원
* AJA Kona5 및 Io4K Plus에서 6G 및 12G-SDI 4K 비디오 모드 추가 지원
* AJA Kona4, Kona5, io4k, io4k plus에서 듀얼링크 3G-SDI 4K 비디오 모드 추가지원
* AJA Kona4, Kona5, io4k, io4k plus에서 TWO SI 추가지원

****

### Blackmagic Hardware Support 블랙매직 하드웨어 지원&#x20;

*   Added support for Blackmagic SDI hardware on macOS. 맥OS에서 블랙매직 SDI하드웨어를 추가지원

    This has been tested using the following devices, but other Blackmagic SDI devices should also be supported:**  아래의 디바이스를 테스트했지만 추후 다른 블랙매직 SDI 디바이스도 지원할 예정**

    * UltraStudio Mini Monitor
    * UltraStudio HD Mini
    * UltraStudio 4K
    * UltraStudio 4K Mini
    * DeckLink 8K Pro

### Video Output 비디오 출력

*   Improved video playback on SDI hardware \
    SDI 하드웨어의 개선된 비디오재

    Baselight will now use all the available frame buffer memory on SDI display hardware to improve the reliability of video playback \[bug 34828]&#x20;

&#x20;      베이스라이트는 비디오 재생의 안정성을 향상시키기 위해서 SDI 디스플레이 하드웨어에서 사용 가능한 모든 프레임 버퍼 메모리를 사용합니다.

* Dynamic Setup Switching \
  다이나믹 셋업 스위칭

You can now change the current SDI video output mode without restarting the application.\
Changing the selected video setup, or changing parameters of the current setup, will result in the video mode changing immediately \[bug 44089] \
\
베이스라이트 프로그램의 재시작없이 현재의 SDI 비디오 출력 모드를 변경할 수 있습니다.   선택된 비디오 설정을 변경하거나 현재 설정의 변수값을 변경하면 비디오 모드의 즉시 변경된 결과가 나옵니다.

* &#x20;Release SDI Hardware in Background \
  백그라운드상태일때 SDI 하드웨어 릴리즈

Baselight and Daylight can now release the SDI video hardware when the application moves into the background.   \
To enable this, go into Preferences->Display->Output and set "Release SDI Hardware When in Background" to "Yes".  \
베이스라이트나 데이라이트가 백그라운드로 움직일때 SDI 비디오 하드웨어는 놔줄 수 있습니다.\
가능하게 할려면, 설정창에서 (설정->디스플레이->출력)으로 가서 "Release SDI Hardware When in Background"를 Yes로 설정하면 됩니다.

### bl-grep **bl-grep (베이스라이트 그랩)**

*   Added a command-line tool called 'bl-grep', which allows you to search through scenes for shots with matching metadata.&#x20;

    See `bl-grep -h` for a list of options \[bug 54136]\


    베이스라이트 그랩이라 불리우는 커맨드라인 툴이 추가되어 씬에서 매칭되는 메타데이터의 샷을 검색하는데 사용할 수 있습니다.

### Single-Channel Matte Caching **단일 채널 매트 캐싱**

*   Strip caching of strips that are known to output single-channel

    images (input layers reading a matte channel from a Sequence,

    References to single channels, keyers etc) now uses a compressed

    single-channel cache. This uses far less disk space and can

    considerably improve performance, for example in scenes where many

    cached Reference strips are used to read channels from

    PIZ-compressed OpenEXR source media \[bug 53898] \
    예를 들면 PIZ 압축된 OpenEXR미디어에서 읽은 채널들을 캐쉬된 레퍼런스 스트립트에서 사용할때 좀 더 적은 디스크 공간과 성능을 크게 향상 시킬 수 있습니다.

### Miscellaneous 기타기능

* Model ID metadata as well as additional gamma curve and look settings are now shown for AVC-encoded Canon MXF movies \[bug 53730] ** AVC인코딩된 캐논 MXF 무비파일에서 추가적인 감마 커브와 룩설정 뿐만 아니라 모델 ID 메타데이터가 표시됩니다.**
* Additional metadata is now shown for HEVC-encoded Canon MXF movies \[bug 53731]\
  **HEVC엔코딩된 캐논 MXF 무비파일의 추가된 메타데이터가 표시됩니다.**
* Added ring and trackball controls for the transforms on paint layers \[bug 50485]
* Added 'Legal To Full Range' Override to Media Import Rules View \[bug 50091]
* Added support for reading 12-bit 4:4:4 XF-AVC encoded QuickTime movies \[bug 53787]\
  **12비트 444 XF-AVC인코딩 퀵타임 무비파일 읽기를 추가지원**
* Updated to Sony SMDK Toolkit version 4.18. This enables recognition of additional colour space tags in Sony camera MXF files \[bug 53729]\
  **소니 SMDK 툴킷 버전 4.18 업데이트. 소니 카메라 MXF파일에서 추가된 컬러스페이스 태그를 인식합니다.**
* Added option to Cursor View to allow the Software CMU to show how a v2.9 Dolby Vision device will render when presented with the v4.0 Dolby Vision XML generated by Baselight \[bug 53947]\
  **소프트웨어 CMU에 커서뷰 옵션이 추가되어 베이스라이트에서 생성된 v4.0 돌비비젼 XML이 v2.9 돌비비젼 디바이스에서 어떻게 랜더 될 것인지 볼 수 있습니다.**
* Updated to DNxHD/DNxHR/DNxUncompressed SDK version 2.6.0.10. There should be no visible effects \[bug 54101]
* Added support for modifiers to allow Pan+Zoom in graphs on systems without a middle mouse button (similarly to the way Pan+Zoom works in the image viewer on those systems). \[bug 54191]
* "Did you know?" images are now shown during application startup to inform you about recently-added new features \[bug 53530]\
  **Did you know 이미지를 보여주어 베이스라이트 프로그램이 시작될때 최근에 추가된 새로운 기능에 대해서 알려드립니다.**
* Added option to Multi-Paste to include Audio when pasting Layer O Operators. This allows you to paste the Audio Sync from one scene into another \[bug 53993]
* On all Linux-based systems, the installer will write a configuration to /etc/sudoers.d that enumerates required commands. When secure mode is enabled (via fl-make-secure on FilmLightOS, or by default on other operating systems), this removes the need for having a global passwordless sudo setup \[bug 54146]
*   Added new CDL arithmetic actions to CDL Grade's Customise menu \[bug 53585]:

    *   Subtract CDL Grade Above: Searches up the stack, finds the next CDL Grade operator, obtains its values, inverts them and then merges them with the current CDL Grade values. This makes it easy to take a "look" grade, precede it with a neutralising grade which colour-balances the images and then subtract the neutralising grade from the "look" grade, ending up with same image.

        Useful in dailies workflows where one needs to provide CDL values which neutralise the image and separate "look" CDLs applied on top of that.
    * Merge CDL Grade Above: Searches up the stack, finds the next CDL Grade operator, obtains its values and merges them with the current CDL Grade values. It then resets the values of the CDL Grade operator it found and, if the strip no longer has an effect on the image, removes it. Useful to combine separate CDL Grade operators into one.
    * Merge CDL Grade Below: Like "Merge CDL Grade Above" except it searches down the stack.

    Merging of CDL Grades is only possible if the upper CDL Grade has Power values of (1, 1, 1) and a Saturation value of 1.

    Keyboard accelerators for these actions are available when the numeric keypad is in "Grading" mode: Subtract CDL Grade Above: Shift+numeric keypad "-" Merge CDL Grade Below: Shift+numeric keypad "+"
*   Values from Number custom columns can now be used in frame number expressions in the render panel.

    For example, if you define a new Number custom column called "EXRStartFrame", you can specify a unique render start frame for each shot, and integrate it into the frame number calculation like so:

    F-E+EXRStartFrame

    Where F is the frame number of the current frame being rendered, E is the frame number at the start of the shot, and EXRStartFrame is the value in the EXRStartFrame column in Shots view for that shot \[bug 53804]
* Added Client View keyboard shortcuts for toggling the "Flagged" status of the currently selected shot ("f") and for popping up the note edit dialog ("n") \[bug 54354]

## 버그 개선 (Baselight 5.2.12809이후)

* Changed location of Motion Blur operator in the Insert menu group; it can be found now in the Temporal category \[bug 53655]
* Fixed clipping of thumbnails in Reports View and in exported reports \[bug 53495]
* Fixed rare crash in Layer View when updating its thumbnails \[bug 53168]
* Fixed issue causing Gallery to be laid out incorrectly when UI controls are not displayed and moved Display UI controls preference to the general section of Cuts View, Gallery & Scratchpad \[bug 53492]
* Fixed issue preventing some DPX files with orientation change from being read \[bug 53418]
* Fixed crash when right clicking on an operator in a layer with 10 or more operators \[bug 53708]
* Fixed issue where some operators didn't show extended range values correctly after extended range is turned off \[bug 53769]
* Fixed issue whereby Layers could not be selected in Gallery via the Layer View when the Scene did not originate from the Gallery \[bug 53675]
* Renamed 'Name' column in Shots View to 'Strip Name' \[bug 53395]
* CMX3600 EDLs with spaces in the Tape field are now accepted \[bug 53265]
* Fixed behaviour of 'Delete Layers' button on control surfaces \[bug 53488]
* Fixed crash drawing paint strokes when there are no paint layers \[bug 53753]
* Fixed crash when trying to edit a perspective overlay with no paint layers present \[bug 53754]
* Fixed issue whereby when removing strips of a specific category in AAF Update, strips without that category could also be removed \[bug 53703]
* Fixed crash in AAF Update when a clip has been duplicated in the timeline \[bug 53714]
* Fixed failures after scanning large amounts of Canon MXF media with sidecar .MIF files \[bug 53823]
* Fixed issue preventing some AVC-Intra MXF files from being read \[bug 53317]
* Fixed distorted audio on AJA hardware output at startup \[bug 43544]
* Fixed crash when picking colours from the image display, in a scene using 32-bit floating-point RGB display setting, on a system using the 418 nvidia driver \[bug 53847]
* Added Legal to Full, Field Order and the Treatment to the paste layer 0 operators copied during a paste / apply action \[bug 51662]
* Fixed cache being disabled when the cache is located on a volume having a large block size and fewer than 1M free blocks \[bug 53948]
* Fixed issue with the button text in Grid Warp and Tracker controls on a Blackboard 1 or Blackboard 1 Classic \[bug 53929]
* Fixed issue with the mouse cursor disappearing when controlling the transform overlay from the blackboard \[bug 49799]
* Fixed fill on empty in Paint being reset during a copy \[bug 53994]
* Fixed raw metadata contained in arrays from MXF files \[bug 54023]
* Fixed an issue with System Monitor View that could cause Baselight to encounter "too many open files" errors \[bug 54008]
* Fixed an issue that could prevent renders from being verified or submitted with an error message about "rs\_movietype\_map" \[bug 54028]
* Baselight now detects when a PostgreSQL server is almost out of available connection slots, and drops cached connections to avoid exhausting them all \[bug 53541]
* Fixed occasional crash when inserting sequence media whose path matches the Ingest Filename Template \[bug 54044]
* Fixed crash when using the "Create Format" option on the New Scene panel in Job Manager \[bug 54034]
* Fixed issue causing some CRM files from newer Canon cameras to be decoded with a strong pink cast on macOS \[bug 54066]
* Fixed problem with FLAPI server holding on to a floating license \[bug 54086]
* The 'sudo' diagnostic now works correctly in "secure" OS mode \[bug 51988]
* The 'mailq' diagnostic now also works on systems that use Postfix instead of sendmail \[bug 22691]
* Removed obsolete "security level" diagnostic \[bug 54170]
* Improved speed of some initialisation tasks. In some environments this can make a significant speed improvement on operations such as file browsing \[bug 54082]
* Increased the default number of threads used to encode H.264 written to QuickTime movies. This improves the render speed of this codec on newer systems. Note that the compressed output may change slightly depending on the number of threads being used \[bug 54015]
* Fixed expansion of %R and other substitutions when editing the filename of a Sequence \[bug 53969]
* Fixed failure to decode full-gate ARX media \[bug 54103]
* Fixed spurious "Updating cloud media" console messages \[bug 54112]
* Fixed Play Between Marks not playing all frames \[bug 54115]
* Fixed Switch configuration diagnostic to warn if switch cannot be contacted \[bug 53335]
* Fixed an issue with FLUX Manage volume menu behaviour \[bug 53368]
* Fixed error decoding RED HDRx clips \[bug 53538]
* Fixed several crashes on exit \[bug 53733]
* Legal to Full scaling is now applied to Apple ProRes encoded MXF files by default \[bug 53587]
* Fixed an issue where 16-bit Apple ProRes encoded MXF files only used 10-bit precision \[bug 54138]
* Changed Shots View @if function to consider an empty string, '0', 'n', 'no' and 'false' as false values (case-insensitive) and anything else as true \[bug 53047]
* Fixed incorrect "Insufficient permission to write new XML" error from a Modify XML render \[bug 53809]
* Fixed various issues that arose when Dolby Vision Trim strips were pasted into a scene using a different Dolby Vision version \[bug 54161]
* Fixed occasional crash on exit, more common at sites with many systems \[bug 53324]
* Fixed rare crash in Layer View when updating its thumbnails \[bug 53168]
* Fixed issue whereby Layers could not be selected in Gallery via the Layer View when the Scene did not originate from the Gallery \[bug 53675]
* Fixed issue causing Gallery to be laid out incorrectly when UI controls are not displayed and moved Display UI control preference to the general section of Cuts View, Gallery & Scratchpad \[bug 53492]
* Improved positioning of keyframes for certain effects in AAFs \[bug 53941]
* Fixed issue with the tracker failing to copy when protect layer 0 was on \[bug 51596]
* Fixed issue on macOS where the 'macsetup' service would override the value for 'kern.ipc.maxsockbuf' in /etc/sysctl.conf, leading to poor networking performance on macOS 10.15 Catalina \[bug 54189]
* Long-GOP MXF movies are no longer trimmable. This prevents an issue where a trimmed movie could start on the wrong frame \[bug 53329]
* Fixed issue causing LUTs not to apply during conform \[bug 53843]
* Fixed issue with incorrect handling of timecode crossing midnight for RED, ARRIRAW and MXF material \[bug 54207]
* Fixed issue with application crashing when exporting a report that used a filter tab from Shots view which sorted on a custom column which had been subsequently deleted \[bug 50029]
* /pfs1 link is no longer created during installation \[bug 54097]
* Fixed hang related to Shots View filtering \[bug 45470]
* Fixed crash on shutdown in flapid service \[bug 54255]
* Fixed crash on startup \[bug 54213]
* Fixed issue on macOS when some network cards do not return their network speed, causing connectivity issues with FLUX Manage and related networking services \[bug 54279]
* Fixed crash which could occur when multi-pasting some BLGs \[bug 53529]
* Prevent a repeated error message from flooding console log files \[bug 52986]
* Fixed issues with Relight3D and MatteXYZ operators \[bug 54254]
* Fixed bind failure when transforming cached strip \[bug 52128]
* Fixed bug in filename sequence versioning when the full path to a file contained the version number multiple times, but only a single version existed \[bug 53592]
* Fixed incorrect offset change if Sequence media is replaced with media with a different timecode frame rate \[bug 53619]
* Fixed issue where Audio Timecode was not carried across when using Multi-Paste with Include Audio option \[bug 54373]
* Fixed bl-reset-video error message when exiting the application on a Baselight ONE \[bug 54095]
* Fixed behaviour of Media Import Rules decode parameter override toggle buttons \[bug 54410]
