# Baselight Release 5.3.17175 (2022-09-28)



## New Features Since Baselight 5.3.17079

### Client View Improvements/Streaming

*   The Client View (a web browser based app that allows clients to monitor/interact with the colourist during a grading session) has received several improvements, most notably support for playback streaming.

    ### Client/Stream and Session Configuration

    Client View stream, client and session settings are configured from the new "Client Sessions View", which can be accessed directly from the Client View (phone icon) menu (or from the "Views" menu). This view has a dropdown (in the top left) for selecting the current session and session management (creating a new session etc).

    The "Access Code" text box can be used to set an access code for the currently selected session. If set, clients must enter this code at the Client View's login page to access the session.

    There are also 2 sections for configuring stream and client settings in the current session.

    ### Stream Settings

    The "Stream Settings" section is used to configure the 2 video streams Baselight outputs simultaneously: "Stream A" and "Stream B". These 2 streams mirror the current video output, but each can be configured with its own resolution, bitrate etc.

    Stream A is encoded using HEVC/H.265 (if supported by GPU hardware encoders), whereas stream B uses H.264. Given the same bitrate, an H.265 stream offers better quality than a H.264 stream.

    Stream A using HEVC also offers a "HDR" colour space option, which corresponds to the "Rec.2100: ST 2084 PQ / Rec.2020 / 1000 nits" colour space, whereas stream B is limited to "sRGB", which corresponds to the "sRGB Display: 2.2 Gamma / Rec.709" colour space.

    A typical use for Stream B would to offer a more compressed, lower quality stream to specific clients when outgoing bandwidth from the host system is limited.

    Note: Changes made in the "Stream Settings" section are not applied to the streams/connected clients until the "Save/Apply Stream Settings" button is pressed.

    ### Client Settings

    The "Client Settings" section is used to select which (if any) stream each client receives, as well as what options/features are available to that client in the Client View itself.

    It is organised into 2 pages/tabs. The "Connected Client Settings" tab shows only settings for clients currently connected. Each connected client will appear as a row of toggle/tick buttons.

    These include "Stream A" and "Stream B" toggles for selecting which stream that client will receive (if any). By default, new clients will be allocated "Stream A" until the available outgoing bandwidth value (see below) has been reached. Additional connections will then not be automatically allocated a stream (and will only receive still images).

    Modifications to the connected client settings are not applied until the "Save/Apply All Client Settings" (or "Selected Client Settings") button is pressed. This also saves the settings to the current session.

    The "Saved Session Client Settings" page shows the saved client settings in the current session. Clients on this page may or may not be currently connected. This page can be used to setup a session before clients have arrived/connected by using the "Create Client Entry" button to add them in advance.

    Both pages contain a "Lock Client List" toggle, which can be used to prevent clients not in the saved session settings from connecting to that session at all.

    At the bottom of the Client Sessions View is an "Outgoing Bandwidth" section. This contains a text box for setting an "available bandwidth" value. This should be set to the maximum outgoing/upload bandwidth available to the host system for streaming.

    When clients connect, the "Allocated" indicator bar will fill (based on the client's stream selection/settings) until the available bandwidth value is reached, at which point additional (streaming) client connections will appear in red at the end of the bar (to indicate the available bandwidth has been exceeded).

    ### Client View Web App

    The Client View web app has also been significantly improved to support streaming. It is now arranged into 2 pages: "Grid" and "Stream".

    The "Grid" page presents a grid of (thumbnail or high res) still images (similar to previous versions of the Client View).

    The "Stream" page is completely new and is itself divided into 2 sections. The top section/image typically displays the live stream from the host. The bottom section displays a scrollable strip of thumbnail images representing the shots in the scene.

    By default, client streams mirror what the colourist sees on their primary display output. However, clients can be switched to a 'clean' output stream. When enabled, client streams will always show the final graded image from the bottom of the current stack. Additionally, streams will hide selected operator overlays, ignore bypass/zoom state etc.

    Clean output can be enabled from the Client View 'Phone' icon menu. There is also a desk action available in the 'Display View' section of Chalk ("Toggle Clean Stream Output"). On the Blackboard Classic, holding "Ctrl" and pressing "Cursor Output" also toggles clean output mode.

    Clicking on a thumbnail will switch the main image to a still frame from that shot (and the thumbnail will glow yellow to indicate the explicitly selected shot). The main image can be scrubbed to a different frame in that shot using the scrub/control bar at the bottom of the image.

    Clients can also flag and/or add notes to a frame from a shot using the flag and note icon buttons in the scrub/control bar. Frames with client notes or flags appear in the Baselight timeline as marks with a 'C' icon at the top. Additionally the colourist can navigate to, view and edit client flags/notes in the Marks View.

    When viewing a still frame, clients can wipe between the graded and ungraded images by dragging the '<>' button on the left edge of the image.

    The main image can be returned to following the stream using either the "Follow" toggle button, or by clicking on the selected/glowing thumbnail again (to deselect it).

    When viewing the stream, if a client hovers over the main image they will enable a "laser pointer", which is also visible to the colourist (and other clients). This can be disabled on a per-client basis from the Client Connections View described above.

    The colourist also has a laser pointer which is displayed on all connected Client Views. This laser pointer is only visible/active while the '-' (minus) key is held down (and the mouse/pen is on the image display).

    There is also a Chalk desk button (in the "Display" category) to activate the laser pointer ("Show Baselight Laser Pointer"). This button also only activates the laser pointer while it is held down.

    On a Blackboard Classic, the laser pointer is activated by holding down the UI/Image toggle button.

    The colour and name associated with this laser pointer can be customised from the Client View "phone" icon menu (via the "Configure Baselight Laser Pointer" option).

    If a client is viewing a HDR stream, the Client View will also display a HDR toggle button. This can be used by clients to switch between the HDR stream ("Stream A") and the SDR one ("Stream B").

    ### Notes

    When viewing an HDR stream, the thumbnail strip at the bottom of the Stream page will be hidden/unavailable.

    If a client has been configured without streaming ("Stream A" and "Stream B" unchecked in the Client Sessions View), The "Stream" page will be renamed to "Fullscreen" and only still frames will be displayed in the main image.

    Currently, streaming does not include encryption or cloud-based reflection of the video stream. All clients connect directly to the Baselight system, so it is important that sufficient outgoing bandwidth is available to support the desired bitrate and number of clients.

    It is strongly recommended that a VPN is used when streaming to prevent unauthorised viewing of client images.

    We are working on implementing a cloud-based authentication and reflection platform which will greatly simplify client access to Client View, as well as optionally reflecting the stream, greatly reducing outgoing bandwidth requirements \[bug 56627]

### Dolby Atmos

*   Dolby Atmos audio is now supported in Scene Audio and for export in IMF packages.

    IMF IAB and ADM BWF are supported for the Dolby Atmos master.

    A Dolby Atmos section has been added to the Scene Audio tab in Scene Settings. The Dolby Atmos master file should be selected here. In order to monitor the Dolby Atmos master, use the Type dropdown menu in the Audio section below and set it to Dolby Atmos.

    Use the 'Output Format' dropdown menu to select the monitoring format you prefer. The following layouts are supported: 2.0, 5.1, 5.1.4, 7.1 and 7.1.4.

    When a Dolby Atmos master is configured in Scene Settings, a 'Dolby Atmos' audio codec becomes available in the audio export setting for IMF packages and IMF Audio files.

    When creating a supplemental IMF package, Dolby Atmos tracks present in the Master CPL can either be preserved, removed or replaced. Updating only part of a Dolby Atmos track is not supported.

    Dolby Atmos sources can also be used as regular audio by adding them in the Audio section of the Scene Audio tab. Supported file types are IMF IAB, DCP IAB and ADM BWF. The CPL files of IMF packages containing Dolby Atmos can also be used.

    Please note, Dolby Atmos audio files cannot be used with Sequence Audio at this time \[bug 33556]

### Frame.io Integration

*   Integrated support for the Frame.io cloud-based collaboration platform is now available in Baselight and Daylight. Videos and comments can be uploaded to Frame.io, and comments made in Frame.io can be downloaded into scenes.

    The Frame.io integration is implemented in Python entirely using the FilmLight API (FLAPI) and its scripts can be used for reference.

    ### Installation

    The Frame.io scripts are installed from the Packages tab in the new Scripts View. After installation, a "Login to Frame.io" option is shown in the Baselight/Daylight menu, choose this to login to Frame.io and allow access to the account.

    ### Uploading videos and comments to Frame.io

    Select "Upload Video and Comments" from "Frame.io Actions" on the Scene menu, and follow the prompts to select the account, team, and project.

    Choose a deliverable preset - the list shows all presets from Render View which output movie files. Ensure the deliverable uses a file format and codec that is supported by Frame.io.

    Choose the Marks to include in the upload. Shot, Timeline and Client Marks are supported.

    A queued render and upload will be placed in the Operations Queue, progress can be monitored in Queue Monitor View. Any failed uploads will automatically retry the upload.

    Please note:

    * The movie files are rendered to disk and then uploaded. The name and location of the files is set in the deliverable preset in Render View
    * All frames in the scene will be rendered and sent to Frame.io, regardless of the Frames to Render setting
    * Ensure that the desired timecode is used for the output, using the Metadata setting in the Video section of Render View

    ### Downloading comments from Frame.io

    Supported comments from Frame.io include client comments, spanned comments (indicating a duration), comments with no timecode, and team comments. Annotation graphics and emojis will not be displayed, but any associated comments will be shown. Comments downloaded from Frame.io are added to the scene as Client Marks.

    Comments for the current scene can be downloaded by choosing "Download New Comments" from "Frame.io Actions" on the Scene menu. There are two download options:

    *   "From this Scene" lists all available videos that were uploaded from the current scene. Videos with new comments are listed first. Select the video to add its comments to the scene.

        If any previously-uploaded videos were removed from Frame.io, they will be listed as unavailable. They can be removed from the scene and will no longer be listed as a comment source.
    *   "From External Source" allows a search of any accessible Frame.io project, listing video files that were not submitted from the current scene. The length of each video (in frames) and how that compares to the current scene is displayed, as well as any available comments.

        Choosing an external source may of course mean that the comments do not match your current scene \[bug 61077]

### Miscellaneous

* Python 3.6 is now included with the Linux software installer and is automatically installed on FilmLightOS 6.4. Python 3.6 is pre-installed on FilmLightOS 8 \[bug 61021]
* Python 3.10 is now included with the macOS software installer and is automatically installed when installing Baselight if no existing Python interpreter is found \[bug 58520]
* Updated to RED SDK 8.3.0. This includes:
  * Support for the upcoming V-RAPTOR XL camera
  * Improved decode performance on Apple Silicon for DSMC/DSMC2 clips
  * Significantly improved per-frame metadata API performance
  * Fix for possible corrupt frames with DSMC clips on Apple Silicon
  * Fix for rare crash with renamed long R3D filenames \[bug 61076]
* Updated to RED SDK 8.3.1. This fixes a potential crash \[bug 61288]
* Dolby Vision XML export now adds an .xml extension to the output file if needed \[bug 60627]
* Baselight CONFORM can now export BLGs and LUTs \[bug 57319]
* ARRI Look Library now uses tetrahedral LUT interpolation. If you use the ARRI Look Library, consider redownloading it from our website. \[Bug 54235]
* Added 'Numbered Discrete' audio channel label option to Render View. This labels QuickTime audio channels as 'Discrete-0', 'Discrete-1' etc \[bug 61261]
* Custom environment variables can now be set in the /vol/.support/etc/environment file. This can be used for example to add an OFX plugin search path allowing plugins to be stored in a shared network location \[bug 61286]
* Updated to FFmpeg version 4.4.1. Please note that this can introduce minor differences when decoding heavily-compressed codecs, notably 8-bit 4:2:0 H.264 \[bug 61808]

## Bug Fixes Since Baselight 5.3.17079

* Fixed a bug which would cause the timeline's caching bar to be flushed/emptied for a shot if a note/flag was added to that shot from a connected Client View \[bug 60364]
* Audio channel mapping editors in Render View, Audio Monitoring View, Scene Settings View and Sequence Audio now have improved labels to make source and destination clearer \[bug 60431]
* Archives of 4.4m1 jobs can now be imported into systems that are running PostgreSQL 12 database servers \[bug 60181]
* Fixed potential crashes that could occur when importing old 4.4m1 archives \[bug 60467, bug 60807]
* Cloud Media device detection now works correctly on FilmLightOS 8.4 systems running graphical desktop sessions \[bug 59506]
* The fltp fl-service and corresponding fl-diag module now correctly read /usr/fl/etc/fltp.conf on FilmLightOS 8 systems \[bug 59866]
* The fl-setupssh program can now be run under sudo, and the macssh diagnostic has been updated to use this program when checking ssh- based volumes \[bug 60570]
* Tidied Marks View to make button labeling consistent, add tool tips etc \[bug 60402]
* Fixed issue reading LTC timecode from logical tracks in Audio Sync \[bug 60497]
* Fixed incorrect behaviour of Dolby Vision 2.9 content mapping when the image does not cover the whole frame \[bug 60488]
* Fixed incorrect behaviour of the New Scene dialog after cancelling the Create Format dialog \[bug 60027]
* Removed extraneous text from Offset Frames setting in the Audio Sync View \[bug 69461]
* Changed SDI temperature diag to only report one temperature when run on Kona 5 cards with fast firmware switching \[bug 60509]
* Fixed crash when hiding Shots View when the thumbnail column isn't shown \[bug 59927]
* Fixed issue with timecode written into Avid OpAtom MXF when the timecode used a rate different from the movie frame rate. Also fixed an issue reading such timecode from some MXF files \[bug 57694]
* Fixed missing thumbnails and crash reading 10-bit 4:2:2 IMF packages \[bug 60694]
* Fixed a crash that occurs when the application is exited, caused by a memory handling error during filesystem scanning \[bug 60540]
* Fixed incorrect behaviour when combining sequences of images with the same filename format that have a different number of digits in their frame numbers \[bug 54758]
* Fixed crash exporting a BLG when a LUT operator cannot extract an embedded LUT from input media \[bug 60722]
* Improved layout of Transform parameters \[bug 60695]
* Fixed an issue that caused some XDCAM encoded MXF files to be unsupported \[bug 60738]
* Added text in Edge Crop to display the current aspect ratio \[bug 60225]
* Fixed GPU usage warning messages on Apple Silicon \[bug 60759]
* Fixed unreadable jobs after importing a database dumped from a older (<9.2) PostgreSQL server into a newer (>=9.2) server \[bug 60796]
* Fixed crash when releasing and reacquiring SDI hardware \[bug 55141]
* Fixed a rare bug in the flici interpreter that could potentially cause a crash when parsing very long expressions \[bug 855]
* Fixed an occasional crash on exit \[bug 54538]
* Fixed crash when editing trackers using trackball \[bug 59804]
* Added keyboard bindings for selecting shots before and after the cursor. These bindings can be seen within the Select menu. The behaviour of Control + Shift + Enter used to toggle shot selection has also changed to be consistent with the Sel/Des. All button on a Blackboard or Slate. Notably, with the DBS unlocked, it will now select between the DBS and current cursor position. It can also be used to select all Gallery grabs when the DBS is within the Gallery \[bug 58668]
* Fixed potential FLUX Manage View preview related crash \[bug 26341]
* Fixed bug in fl-cp that could cause a directory copy to fail \[bug 61031]
* Fixed crash selecting strip-marked frames in Render View in an empty scene \[bug 61028]
* Fixed crash that could be triggered by renders using an ambiguous filename extension \[bug 61046]
* Improved help text for the selection of stream type when using the H.264 / HEVC hardware encoder \[bug 61004]
* Media copies and Consolidate now always use the flit service to copy all image files, which fixes issues with the loss of some metadata \[bug 46765]
* Dolby Vision Trim strips can no longer be set to have no target display \[bug 60567]
* Fixed issues with setting a Dolby Vision Render Colour Space in an older scene \[bug 60485]
* Fixed crash that could occur in Dolby Vision Trim when working under a Dissolve \[bug 60708]
* Fixed crash that could occur in Dolby Vision Trim when changing the Analysis Area to "Sequence Input Area" \[bug 60783]
* Text, subtitle and burnin operators now combine Korean Jamo letterform input into Hangul characters \[bug 59130]
* Fixed crash in export when queue database cannot be contacted \[bug 61184]
* Fixed an issue whereby an incorrect file structure is produced when using Consolidate with the option 'Copy Files and Trim Sections From Movies' \[bug 61065]
* Fixed a bug which would require multiple 'undo's to revert a single change to a Base Grade master/trackball ring value \[bug 61214]
* Fixed a bug when conforming from an indexed volume and using filtering by movie type \[bug 60294]
* The "Range" field on the Sequence parameters now scales correctly when using a large font size preference \[bug 61212]
* Fixed crash when editing the "Contrast Pivot" value in the Default Values and Bumps dialog in Base Grade. Also fixed a bug where changing the default value of Flare or Saturation mostly wouldn't work \[bug 60520]
* Fixed crash in Multi-Paste from ALE file when there was a keycode column present \[bug 60292]
* Fixed a crash during a scratchpad grab or layer 0 paste which included a param operator \[bug 61262]
* Fixed poor playback performance when using many LUTs \[bug 59433]
* Fixed issue with bl-config-xorg selecting the wrong GPU connector for Blackboard ONE or TWO on FilmLightOS 8 \[bug 61348]
* Fixed crash in Python interpreter if a FLAPI plugin from a Python package failed to load \[bug 61339]
* Moved the option to 'Goto This Shot' out of the 'Navigate' submenu within the right-click menu of Cuts View \[bug 61407]
* Fixed hang on startup on some macOS systems caused by BorisFX Continuum OFX plugin \[bug 60987]
* Fixed an issue where supplemental IMF packages with audio tracks using the 'New' mode could fail to render with an error message about 'No frames to render' \[bug 61441]
* Fixed issue where "Clear Poster Frame" would cause large scenes to slow down \[bug 61416]
* Fixed poor performance when using the same LUTs in separate shots that use a different set of colour spaces \[bug 61515]
* Fixed creation of supplemental IMF packages with Dolby Vision where the Master Scene starts with a gap \[bug 61523]
* Fixed lifted blacks in outside-L5 (letterbox) areas when using Dolby Vision Content Mapping to Rec.1886 \[bug 60436]
* Fixed issue that could cause invalid supplemental IMF CPLs to be created when using a Master CPL written by another application \[bug 61517]
* Fixed issue with Master Scene remaining open after rendering or viewing differences for a supplemental IMF deliverable \[bug 61590]
* Audio tracks in supplemental IMF packages now have separate entries in the Scene Differences dialog shown when comparing a master scene to the current scene \[bug 61442]
* Generic IMF package deliverables once again write the timecode configured in the Render View 'Metadata' setting \[bug 61542]
* Fixed diagnostics to fail if there are no rendering GPUs present in a Baselight ONE (in case of hardware failure) \[bug 39811]
* Fixed issue conforming AAFs with transforms if any of the values are not changed from default in Avid \[bug 61361]
* Improved the visibility of cursor lines in Cuts View and Gallery by increasing their width \[bug 61562]
* Fixed crash in some situations where a blur operator is used \[bug 40043]
* Fixed failures reading ARRI QuickTime media trimmed by some third-party tools \[bug 61757]
* Fixed issue with use of the UI GPU on Baselight ONE systems when primary output is set to "No external output" \[bug 60589]
* Fixed crashes when working with some camera media, notably ARRIRAW \[bug 61601]
* Fixed excessive amount of 'etmetadata' fields in OpenEXR renders from RED camera files containing ET Metadata \[bug 61731]
* Fixed issue during application quit that caused a warning the next time the application is started \[bug 60661]

***
