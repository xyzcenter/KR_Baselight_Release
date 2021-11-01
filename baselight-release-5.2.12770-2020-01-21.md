# 베이스라이트 릴리즈 노트 5.2.12770 (2020-01-21)

## 최신 기능 (Baselight 5.2.12692이후)

### FilmLight API (FLAPI)

*   FilmLight API is a new client-server API (application programming interface) which allows 3rd-party software to interface with Baselight and Daylight.\
    **  **필름라이트 API(에이피아이)는 새로운 클라이언트-서버 API (응용 프로그램 인터페이스)로 베이스라이트와 데이라이트 프로그램에 써드파티 소프트웨어를 허락할 수 있는 인터페이스를 말합니다.

    FLAPI currently supports writing client software in the following languages:\
    **FL에이피아이는 현재 아래의 언어들로 작성된 클라이언트 소프트웨어를 지원합니다. **\


    * Python 2.7
    * Python 3.4 or later
    * JavaScript
    * NodeJS
    * Java 8+ (JDK 1.8+)

    Documentation for FLAPI can be found in the following locations:

    Linux: /usr/fl/baselight/doc/flapi /usr/fl/daylight/doc/flapi

    macOS: /Applications/Baselight/Current/Documents/flapi /Applications/Daylight/Current/Documents/flapi

    Example FLAPI scripts can be found in the following locations:

    Linux: /usr/fl/baselight/share/flapi/examples /usr/fl/daylight/share/flapi/examples

    macOS: /Applications/Baselight/Current/Utilities/Resources/ Share/flapi/examples /Applications/Daylight/Current/Utilities/Resources/ Share/flapi/examples

    Please note that FLAPI is currently in beta. FilmLight will be frequently adding new functionality and features to the interfaces exposed via FLAPI. FilmLight reserves the right to change aspects of the interfaces exposed by FLAPI, although we will do our best to minimise changes which will affect client software \[bug 53725]

### Client View

*   Added a rewritten (FLAPI based) version of Client View. Client View is a web based interface that allows clients to interact with the colourist during a grading session from a laptop or tablet. Once connected, clients can:

    *   Scroll through a (live) thumbnail gallery of all the shots in the

        scene currently being graded.
    * View metadata for the shots in that scene.
    *   Flag shots for the attention of the colourist (during a review

        session, for example).
    *   Annotate shots with comments for the colourist (or other clients

        in the room).

    To open the Client View from a web browser, use the URL displayed in Baselight's Client View menu (accessed from the "Phone" icon in the menu bar). This menu also allows you to start/stop the Client View, set an access passcode etc.

    On successful connection, the client will be prompted to login with a user/client name and passcode (Note: If one has been set, all users will share the same passcode).

    Once logged in, the Client View main page will be displayed. The page header displays the name of the currently open scene (if any). The body of the page contains a scrollable gallery of thumbnails for all the shots in the currently open scene. The page footer contains a "Home" button that jumps to the shot currently being graded and a follow toggle button to keep the current shot in view.

    Clicking on a thumbnail image will display the metadata associated with that shot.

    Each thumbnail has "Flag" and "Pen" icon buttons. The flag button is used for toggling a flag on the shot (which marks a shot for the attention of the Baselight colourist). The pen button pops up a dialog box for editing the shot's notes. Each shot's notes are presented as a chat stream, allowing multiple clients (and the colourist) to comment on/discuss each shot independently.

    The flag & pen buttons are drawn bright blue if the client has already flagged, or added a note to a shot respectively.

    In Baselight itself, the Shots View has a new metadata panel tab: "Client Data". This tab shows any notes/flags for the currently selected shot. The colourist may also add notes to the current shot via the text box at the bottom of the tab.

    An additional Shots View filtering option has also been added: "Client Data". This allows the colourist to quickly find shots that have client notes and/or flags \[bug 52551]

### Miscellaneous

*   Added support for navigating through the first & last frames of consecutive strips on repeated presses of the Home & End keys (rather than only jumping to the start/end the currently selected strip).

    This can be enabled/disabled via the "Legacy Home/End Behaviour" option on the Navigate menu \[bug 53208]
* Added Export Still button to Chalk \[bug 52616]
* Category flags in Counters now obey the Counter Intensity setting in Setups \[bug 53188]
* Updated to DNxHD/DNxHR/DNxUncompressed SDK version 2.5.4. There should be no visible effects \[bug 53197]
* Updated to Blackmagic RAW SDK version 1.6. This addresses a bug with macOS 10.15.1 Catalina, adds support for the URSA Broadcast and addresses an issue with AMD 5700-series GPUs on macOS \[bug 53497]
* Updated to Sony SMDK Toolkit version 4.18. This enables additional metadata to be read from Sony camera MXF files \[bug 50233]
* Added support for trimming MXF files from the Sony VENICE camera \[bug 47512]
* Added Tint control to Sony RAW Params and improved behaviour of Colour Temperature control \[bug 47548]
* Added the option to import marks when conforming from AAF files \[bug 39743]
* Updated the Canon RAW SDK to version 2.3. This adds support for RMF and CRM files from newer Canon cameras. On Linux, nvidia driver version 375.66 or later is now required to decode these files \[bug 53068]
* The default behaviour of Select Operators Of Specific Type is now to select only modified operators in Layers. This can be changed using the toggle in the submenu to select all (modified and unmodified) operators in Layers \[bug 53499]
* ARRIRAW metadata embedded in ProRes QuickTime media written by ARRI cameras is now carried through to OpenEXR rendered files, and can be seen in 'fl-imageinfo -raw' \[bug 35143]
* Sequences with missing timecode on their final frame, or for which a consistent timecode frame rate cannot be established, are now indicated correctly in FLUX Manage using '#' instead of '-' between the start and end timecodes, and can be filtered using the "Bad timecode" tile \[bug 53108]
* Updated to ARRI Metadata Bridge version 1.3. This improves ARRI camera metadata transfer to OpenEXR renders \[bug 47173]
* Added -cmd option to fl-cp which shows the fluxc command that it runs \[bug 53399]
* Added "Don't ask again" buttons to the single-frame analysis commands in Dolby Vision Analysis strips \[bug 53085]
* FLUX Manage now allows filtering and sorting by colour space tags (Primaries, EOTF and Matrix) \[bug 52657]
* Added a filter option to the New Mapping dialog in the Formats editor \[bug 53430]
* Consolidate can now trim ARRIRAW MXF files, by creating a sequence of .ari files. Note that any audio tracks in the source media are not preserved in the trimmed output \[bug 45309]
* Consolidate can now trim Apple ProRes QuickTime files. Note that any audio tracks in the source media are not preserved in the trimmed output \[bug 45546]
* Added support for HP Z2 Mini Gen 4 UI hosts \[bug 49463]
* Added current paste mode to the Cuts View and Gallery View menu \[bug 53009]
* Results Blending keyframes are now movable and the keyframe dropdown menu has been improved. The chosen keyframe option from the dropdown menu will now also persist across the same operator types. Additionally, keyframes to the left and right of the cursor can now be selected via the right-click menu \[bug 41190]
* Added Dustbusting duration control to paint layers. This sets the duration of the keyframes set for dustbusting mode \[bug 53013]

## 버그 개선 (Baselight 5.2.12692이후)

* Fixed white point mismatch when generating LUTs between display-referred spaces \[bug 51994]
* Prevented removal of Sequence operator from Layer 0 \[bug 51943]
* Fixed crash in ArriLook on undo \[bug 52950]
* Fixed reading of Scanity 10-bit DPX files that do not use packing value 2 (type B) \[bug 53056]
* Fixed an issue that would cause updated Linux kernel modules to be inactive \[bug 52914]
* Fixed issue where Gallery offline media from composite stacks would not render \[bug 52770]
* The size of thumbnails in the Gallery View and Cuts View are now retained upon restarting \[bug 28898]
* Fixed issue where Drag and Drop via Layer View would always paste keyframes regardless of the Paste Keyframes preference \[bug 53268]
* Fixed filename shown in FLUX Manage when previewing an image sequence \[bug 53255]
* Fixed error when copying to / in FLUX Manage \[bug 53306]
* Fixed error creating a scene with its Working Format set from the FLUX Manage format, when that format is not a global format \[bug 53092]
* Fixed inefficient behaviour when copying a folder which contains sidecar (e.g. .RMD) files \[bug 52961]
* Fixed error importing FCPXML files with formats of zero width/height \[bug 53194]
* BLGs can now be inserted directly to the Gallery from FLUX Manage \[bug 53082]
* Fixed bug which could result in a chequerboard image when using a composite layer with a foreground (leaf) reference and a foreground stack containing a matte \[bug 52630]
* Fix divide by zero when importing Premiere XMLs with clip fps values of zero \[bug 53344]
* Fixed potential crash when using optical flow to retime sequence operators in conjunction with (large) downstream transforms \[bug 52786]
* Fixed failures and crashes when using a scene set to 12-bit Integer RGB caching, for example when tracking, or when rendering to PNG \[bug 52317]
* Fixed "Could not find track" error when updating and AAF containing a mixdown track
* Fixed potential crash when deleting layers from the Blackboard or Slate \[bug 53394]
* Fixed "Delta in progress" caused by X and Y reset buttons in the Text operator \[bug 53446]
* Fixed failures from fl-cp and FLUX Manage when converting a sequence to a different image format \[bug 53453]
* Fixed failures dragging from the file browser in FLUX Manage View with a multiple selection including both folders and sequences/files \[bug 53250]
* Fixed display of stored counter brightness value \[bug 53414]
* Fixed problems with Galleries containing different frame rate grabs \[bug 48974]
* Fixed crash when copying grabs between Galleries \[bug 53177]
* Fixed issue where Try and Apply would cause the cursor to jump back to the first frame when on the final clip \[bug 51810]
* Fixed extended character encoding in PDF reports \[bug 53496]
* Updated non-ProRes Deliverables in Scene Templates to avoid warnings when switching them to use ProRes \[bug 53505]
* Fixed usage text for bl-reset-cache \[bug 53040]
* Fixed failures when there are unexpected files or directories in the /usr/fl folder \[bug 51523]
* Fixed fl-cp incorrectly sending a crash report when it takes no action \[bug 53371]
* Fixed "attempt to use closed socket" errors when copying media \[bug 52957]
* Fixed crash when grabbing large stacks to the scratchpad \[bug 50161]
* Fixed bug which could result in incorrect/missing burnins on the first frame of rendered out shots \[bug 53035]
* Fixed incorrect text clipping in PDF reports \[bug 52971]
* Improved behaviour on macOS when inserting new removable media or attaching a new external drive \[bug 53064]
* Fixed failure in Dolby Vision v4.0 EDR XML export \[bug 53588]
* Fixed an issue that prevented some OpAtom MXF files from being read \[bug 53540]
* Fixed issue when exporting an ALE whereby "None" was not always displayed as an option for clip name \[bug 51670]
* Fixed flit copy being slow to start on macOS \[bug 53601]
* Improved the index indicator on the volumes menu so it more accurately reflects when a volume index is active \[bug 53372]
* Fixed hang when picking a colour for a selected colour well, particularly in a Shader operator \[bug 51984]
* Fixed an error with wrong paths when dragging multiple source directories in FLUX Manage \[bug 53494]
* Fixed errors with MatteXYZ and Relight3D when using the 418 nvidia driver \[bug 53629]
* Fixed gallery failure after grabbing a sequence that uses its media's Full Sensor resolution \[bug 53364]
* Fixed incorrect input into text fields on macOS when pressing function keys \[bug 53367]
* Fixed issue with Apply or copying when the target is an incomplete stack \[bug 53026]
* Fixed crash when picking outside of the image \[bug 52372]
* Fixed behaviour of Dolby Vision action in Chalk \[bug 53653]
* Fixed Dual Output Layout mouse behaviour \[bug 52674]
* Fixed occasional crash in Media Import Rules View \[bug 53021]
* Fixed crash in ARRI Look operator \[bug 53678]
* Improved flit service file error reporting \[bug 53206, bug 53350]
* Fixed flit service crash if source file changes size \[bug 53033]
* Fixed error reading a multi-part OpenEXR file where the default RGBA (or RGB) channels are not all in the same part \[bug 53688]
* Fixed an issue that could cause various apps and services to consume 100% CPU if there is no configured swap \[bug 53182]
* Fixed a crash during application of Media Import Rules \[bug 52258]
* Fixed Shots View filtering on "Mode" and "Type" columns \[bug 50206]
* Fixed application hang when dragging and dropping onto a scroll bar \[bug 46415]
* Fixed issues with /vol on macOS 10.15 Catalina \[bug 53752]
* Fixed incorrect details in "Fatal error updating EDL" queued render error \[bug 53656]
* Fixed crash in Gallery when exiting which also rarely occurred when switching Gallery tabs \[bug 47966]
* Improved behaviour if the macOS display profile is changed while the application is running \[bug 52070]
* Fixed invalid Dolby Vision analysis on some flat-colour shots \[bug 53766]
* Fixed incorrect changes to offset and timecode when changing a Sequence to use different media, by browsing or switching versions \[bug 53619]
* Fixed an issue that could cause a crash when the application exits \[bug 52060]
* Fixed an issue that could cause conform to fail when a sequence has missing keycode \[bug 52233]
* Fixed crash that could occur when a tooltip was displayed and its text was changed due to keyboard input \[bug 53775]
* Fixed failure to decode Sony media on a MacBook with Intel Iris graphics \[bug 44311]
* Fixed a rare case in Conform that could fail to complete a media scan \[bug 53410]
* Fixed Adaptec RAID controller diagnostic on Baselight X systems with Adaptec 3154-24i and Adaptec 3154-8i16e controllers \[bug 53824]
* Fixed missing Blackboard 2 & Slate action for Export Still \[bug 53844]
* Fixed issue with Disk Performance Monitoring (DPM) showing blank columns on some Gen VII configurations that use MSCC 31XX RAID controllers \[bug 53591]
* Fixed crash which could occur when loading AAF file containing some oddly-formed BLG data and "Apply Baselight Grades" being on \[bug 52880]
* Fixed crash which could occur when loading a gallery containing an undefined format \[bug 52864]
