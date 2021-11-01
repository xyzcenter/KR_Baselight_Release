# 베이스라이트 릴리즈 노트 5.1.10830 (2018-07-27)



## New Features Since Baselight 5.1.10720

### Dolby Vision Software CMU

*   Dolby Vision content mapping is Dolby's technology for mapping HDR images for SDR displays. Until now grading with Dolby Vision has required the use of a Dolby Vision Content Mapping Unit (CMU) connected to the SDI stream, and rendering SDR deliverables using Dolby Vision has required command-line tools.

    Now, the content mapping can be applied inside Baselight during grading, playback and rendering. This functionality is known as "Software CMU".

    An additional licence must by purchased from Dolby in order to allow the trim controls in the Dolby Vision Trim strip to be adjusted when using the Software CMU.

    Scene Settings View (on the Format & Colour tab, Dolby Vision section) allows a scene to be set to use the Software CMU. Once this is done, the Cursor View's Viewing Colour Space menu shows (at the top) the colour space of the Dolby Vision Mastering Display and of each Dolby Vision Target Display. Choosing a Target Display will cause the Software CMU to be used to convert to the SDR colour space instead of Baselight's normal colour pipeline. The Colour Space Journey View updates to show what is being done.

    The Render Colour Space menu on Render View shows the same new colour space options.

    If a Mask is selected on Cursor or Render View, the Software CMU is only applied within the masked area \[bug 44614]

### Other Dolby Vision Changes

* The Dolby Vision strip has been replaced by separate Dolby Vision Analysis and Dolby Vision Trim strips, for clarity and to prevent issues caused by copying and pasting strips \[bug 48199]
* Dolby Vision analysis is now always automatically performed in the appropriate colour space; there is no longer any need to change the cursor's viewing colour space before analysis.
* Changing a scene's Dolby Vision Mastering Display to one with a different brightness invalidates all analysis data stored in its Dolby Vision Analysis strips, requiring them to be re-analysed.
* Analysis numbers ("L1") are now shown on the Dolby Vision Analysis operator UI, to assist troubleshooting.

### Dual Colour Spaces Layout

*   When using dual outputs from an AJA card or combiner, the Display menu now offers Dual Colour Spaces Layout. In this layout, the two video outputs each show the current cursor, but using two separate viewing colour spaces. The viewing colour space for the secondary output is chosen on Cursor View.

    When using this layout, Cursor View also allows you to select which video output is used for Histogram View, the various Scopes Views and Colour Space Journey View.

    This layout is particularly useful when combined with the Dolby Vision Software CMU, as it allows you to:

    * connect the HDR mastering display to one output and an SDR target display to the other output, and view both the HDR and SDR versions at the same time
    * connect two different target SDR displays so you can refer to one SDR trim while adjusting the trim for the other target display
    * connect two identical target SDR displays so you can compare Baselight's DRT-based SDR version of an HDR scene with the Dolby Vision Software CMU version

    This layout could also be used with a hardware CMU, sending the mastering HDR image to the CMU and showing another colour space on the other output.

    In this layout, the timeline is cached for both colour spaces.

### Miscellaneous

* Added Audio Codec Parameters to Render view. These codec parameters can be modified in the same way as Codec Parameters for movie codecs, and are presented for any audio file types & codecs that support parameters \[bug 46438]
*   Added support for writing Broadcast WAVE header information into rendered WAV audio files.

    The Broadcast WAVE header is populated with:

    * origination date & time
    *   origination reference containing FilmLight software version used

        to render the audio file
    * timecode that matches the record timecode of the source scene
    *   description field, that can be specified via the Audio Codec

        Parameters in the Render View. The "BWAV Description" codec

        parameter is a string that can include standard variable names

        like %{Scene} or %{Job}.

    Any variables in the BWAV Description parameter will be substituted when the audio file is rendered \[bug 46438]
*   Added support for selecting which timecode to embed when rendering audio files. This option is available when rendering "Audio Only" or "Sequence + Audio".

    You can select from the following options for the timecode embedded in the audio file:

    * Record Timecode : Timeline timecode
    * Shot Timecode : Source Timecode of the shot
    * Audio Timecode : Audio Tiemcode of the shot
    * File Timecode : Audio Timecode from source audio file

    The audio timecode can be specified via the bl-render command line using -atc option \[bug 46438]
*   Added %{Host} and %{Zone} as variables which can be used in Text operators, burnins, render filenames and audio metadata.

    %{Host} : the database server that contains the scene being rendered %{Zone} : the machine that is performing the rendering of the scene

    NOTE: If you submit a render to a remote render queue, the remote system's zone name will be used for the Zone variable \[bug 46438]
* Updated the Sony RAW SDK to version 3.1.0, which adds support for reading X-OCN 4K 6:5, 6K 17:9 and 6K 1.85:1 bitstreams \[bug 47819]
* Added option to apply stereo grade data to both eyes simultaneously during conform \[bug 47694]
* Added support for reading HDE-compressed ARRIRAW files (.arx) \[bug 47699]
* Updated to RED SDK 7.0.7. This contains some bug fixes and improves load times for R3D clips recorded on newer sensors and camera firmware \[bug 47797]
* Reduced snap size of ARRIRAW Params White Balance parameter from 100 to 25 to allow more precise White Balance adjustments \[bug 48287]
*   Added support for reading Input Format from ALE during EDL Import. If an "Input Format" column is present in the ALE, the option to "Use Input Format from EDL" will be shown in the EDL Import window.

    When this option is set to "Yes", EDL Import will attempt to use the named format as the Input Format when conforming the event against source media. If the named format is not one of the possible formats that can be used for the matching source material, a warning will be added to the EDL Import window for the event \[bug 48241]
* Added ability to import keycode from an ALE \[bug 48141]
* Changed the EDL Import view's container handling to match FLUX Manage. Now, if the search directory for a conform lies outside the current container, a dialog will pop up offering a range of possible containers based on the search directory. This will occur even if the search directory isn't on a filesystem mounted under /vol \[bug 46364]
* Files rendered by Baselight or copied by FLUX Manage now respect the umask of the user who submitted the render/copy \[bug 44569]
* Added "Apply Exposure Index" option to Sony RAW Params, to allow the exposure to match files rendered from Sony's RAW Viewer application which doesn't apply the Exposure Index \[bug 48383]
* Added "Has Speed Change" column in Shots view. This will show any shots that have an Increment value other 1.0, where the frame rate of the shot does not match the scene, or any shot that has a Retime operator. It can be used as a filter in Shots view to identify shots which do or do not have any speed change \[bug 48420]

## Bug Fixes Since Baselight 5.1.10720

* Fixed image corruption with OFX plugins, especially when using a transform after the OFX operator \[bug 46111]
* Fixed image corruption with Shader operators, especially when using a transform after the Shader operator \[bug 41601]
* Fixed an issue where AVC-Intra MXF files using the Panasonic V-Log colour space incorrectly set the 'Legal to Full Scale' option by default \[bug 48177]
* Added View, Try and Apply hotkeys to the keyboard. View is ';' Try is '/' and Apply is '@'. Note that Align Timeline has been moved to 'ctrl + ;' now \[bug 31910]
* Fixed issue with pasting layer 0 not taking all the correct colour space parameters \[bug 35459]
* Fix a "Object Id 0 is out of range" error when upgrading 4.4m1 scenes \[bug 48197]
* Fixed a rare crash that could occur when recovering a scene that was upgraded from 4.4m1 \[bug 48428]
* Enabled drag and drop from the gallery layer view \[bug 46315]
* Added option in copy and paste menu to turn off pasting of colour space information in the layer 0 paste \[bug 47129]
* Fixed an issue with sudoers configuration \[bug 48201]
* Fixed crash exporting a LUT from a stack containing spatial operators \[bug 48095]
* Fixed render service on a FLUX Store not using all available GPUs \[bug 48121]
* Prepare For Review now correctly uses the colour space and proxy resolution settings of the currently-open cursors \[bug 43435]
* Fixed crash writing stereo ALE with no clip name metadata \[bug 48111]
* Greater accuracy in variable retimes from Premiere XMLs, particularly when velocity ramps are used \[bug 47962]
* Fixed crash when clips that are ignored during EDL import have effects applied to them \[bug 44350]
* Fixed keyframing issues when applying SDL events from .edl files during conform \[bug 47697]
* SDL data in .edl files with no valid events no longer causes a crash \[bug 48217]
* Increased the responsiveness of the Tangent Element MF trackball ring \[bug 48280]
* Improved reporting of errors in fl-service \[bug 44643]
* Fixed flux and render service processes continuing to run after installing a new Baselight/Daylight build or using fl-vers to switch the current build \[bug 48155]
* Fixed bug in BLG export/Update Avid AAF with Baselight Grades which caused the behaviour of a ColourSpace operator to change if it was set to convert to the scene's Working Colour Space \[bug 47919]
* Fixed issue on multi-GPU systems with JPEG 2000 where too much GPU memory was set aside for rendering \[bug 48050]
* Fix bug parsing frame offset in keycode from ALE \[bug 48297]
* The tracker strip will display and track all trackers by default. This behaviour can be changed to track and display only the selected tracker using the (persistent) "Selected Tracker Only" button/setting \[bug 48114]
* Fixed appearance of the Frame Rate menu in Sequence \[bug 48356]
* Fixed an issue that could cause decode failure of Sony RAW MXF files on upgraded scenes \[bug 48369]
* Sony RAW media now shows ISO metadata \[bug 48383]
* Fixed issue that prevented USB audio devices from being used at 44.1kHz sample rate \[bug 47663]
* Fixed reading RGB and greyscale Phantom cine files \[bug 48390]
* Fixed failures when copying MXF movies with linked audio and video files \[bug 48406]
* Fixed filtering based on floating-point value columns in Shots view \[bug 48429]
* Fixed failure in "bl-render -set" \[bug 48450]
* Errors in /vol automounting are now logged \[bug 48459]
* The first diagnostic run after installing a new build will now run the "daily" diagnostic tests, and will not ignore any warnings that were previously ignored \[bug 48476]
* Fixed bug to pass through audio track names when track number is larger than number of channels in audio file \[bug 48489]
* Fixed timecode metadata read from OpenEXR files having an incorrect "Timecode" metadata string \[bug 48501]
* Diag "GPU texture test" is now multi-gpu aware \[bug 47235]
* Fixed failure to decode ARRIRAW media between 4321 and 5120 pixels wide on a Linux system with a 3GB GPU (e.g. GTX 780). This media is now decoded on the CPU \[bug 48462]
* fl-make-secure script creates ssh configuration files if necessary \[bug 48530]
* Fixed ssh connection diagnostic \[bug 48198]
* Fixed fl-make-secure syntax error expanding hosts/\* directory names \[bug 48529]
* Fixed pre-render hanging in some queued renders \[bug 48460]
* Fixed crash when the user's group list has many group IDs longer than 7 digits \[bug 48541]
* Updated flos-tools package to add support for 6.4TB nvme. Also includes minor fixes to fl-config master and fl-setup-raid to require a reboot if nvme sector size is changed, and to connect to other hosts in the local zone using ssh instead of rsh \[bug 48411]
* Added nvme support to dpm command \[bug 47142]
