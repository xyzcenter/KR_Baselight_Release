# Baselight Release 4.4m1.7448 (2015-06-11)



## New Features Since Baselight 4.4m1.7383

* Added support for reading newer Avid MXF files using ProRes codecs \[bug 32333]
* Added Blackboard and Slate support for bumping values in the CDL grade \[bug 32239]
* Added a "Fuzzy" option to the "Match By" section of the Multi-Paste View. When used instead of "Exact" for Tape Name, Clip Name or BLG Name options, the matching process changes:
  *   The match is case insensitive (this replaces the former "ignore

      case" variations in the drop-down.
  *   If it can't find an exact match, it will try to find a common

      prefix and match using that instead. For example, with "Fuzzy"

      selected, "shot\_abcd\_v1" would match against "shot\_abcd",

      "shot\_abcd\_v2" etc. The common prefix must comprise at least

      half of the original tape name, clip name or BLG name to

      prevent too many false matches \[bug 20760]
* The number of audio channels in the Render view can be set to "Auto (from source)". This makes the output movie have the same number of audio channels as the source audio file. This is useful for rendering dailies, where each shot may have a differing number of source audio channels and the output movie or audio file should have the matching number of audio channels \[bug 32190]
* When rendering with Audio Channels set to "Auto (from source)", clips with no audio will result in movie files with no audio track \[bug 32525]
* You can now remap the audio channels in Render view, on a per-deliverable basis. This allows you to generate, for example, stereo h.264 movies for dailies where the left and right channels in the h.264 movie are mapped to the mono mix channel from the source audio files \[bug 4508]
* Added option on Colour Space operator to convert to the Input Colour Space of the Sequence operator at the top of the stack \[bug 31795]
* CDL Grade can now be added as an Input Layer operator \[bug 32448]
* Several changes relating to merging events around dissolves when loading CMX EDLs:
  *   Due to feedback from customers that Baselight was too aggressive

      in merging events at the out-point of dissolves, the "Merge

      events around CMX3600 dissolves" preferences has now become a

      drop-down with three options:

      &#x20; "Don't Merge" - Don't merge any events.

      &#x20; "Merge only zero-length incoming clips" - Baselight only merges

      &#x20;  events at the in-point of dissolves and only if the incoming

      &#x20;  event of the dissolve is zero length. This is the new default.

      &#x20; "Merge incoming and outgoing clips" - Baselight will attempt to

      &#x20;  merge clips on both in the input and output of dissolves. This

      &#x20;  is the old default \[bug 30088]
  *   Baselight is now able to merge events where there was a speed

      change applied to both events.
  *   Baselight is now able to merge if the first mergeable event's

      tape name differs from the following event's tape name only by

      having the letter B on the end (eg "100B") \[bug 29070]
* Updated to ARRIRAW SDK v5.1. This improves colour reproduction for ALEXA 65 material. The Baselight ARRIRAW decoder has been updated to use the same colour science. Note that this only affects ALEXA 65 material added to a scene; older scenes are unaffected.
* Added choice of full-resolution decode method for Sony F65 material in Sony RAW Params operator \[bug 32664]
* Added preference for background caching shots before the current cursor position first \[bug 32594]
* Added an extra decimal place of precision to film grade exposure value & bump \[bug 32592]
* Added a new trackball mode to curve grade operator: "Control Point Per Trackball" (available from the 'Customise' menu). Once enabled the 3 trackballs map to control points at the bottom, middle and top end of the currently selected curve \[bug 32584]

## Bug Fixes Since Baselight 4.4m1.7383

* Added DPM (Disk Performance Monitoring) support for Adaptec RAID controllers as used on Gen VI hardware. Including adding a 3ware style presentation of drive latency figures. Also amended the DPM tool so that Hitachi Deskstar P7K500 drives which don't always return a SMART value for rotational speed aren't flagged as SSDs \[bug 31638, 32616, 32684]
* Fixed DPX and OpenEXR being copied in the wrong format (e.g. copying 16-bit DPX resulted in a 10-bit output sequence) \[bug 32326]
* Badly-formatted timecodes no longer cause an EDL crash \[bug 32357]
* Fixed crash importing a EDL with "Generate Film and Video Grades" selected when one of the events has no CDL values \[bug 32283]
* Fixed bl-conform --template not applying values from the Scene Template \[bug 32323]
* Fixed gallery grab failure when the grabbed stack uses a Job Format \[bug 32277]
* Fixed the launching of Baselight on a display that is not ":0.0" \[bug 27501]
* Fixed the stopping of an in-progress conform reporting incorrect results when re-started \[bug 25814]
* Fixed the netperf diagnostic for single 10Gb link kompressors in environments that have a wildcard dns \[bug 30563]
* Added default values to ALE CDL exports \[bug 32398]
* The default Truelight profiles directory in the preferences is now used as the default location for the Truelight strip as well as for the cursor. If a profile or cube is selected from another directory, the list for that strip will now be populated from the same directory \[bug 26688]
* The reload button on the Truelight strip now also reloads the contents of the list of profiles and cubes \[bug 31612]
* Changed the ordering of cube format options in the Export LUTs dialog, to show Truelight formats then others in alphabetical order \[bug 31923]
* Added scroll bar to OFX plugins that only have one tab of controls \[bug 32432]
* Fixed display of mattes while interactively grading with interlaced scene \[bug 32293]
* Fixed missing Sony: S-Log2 / S-Gamut colour space \[bug 32407]
* Fixed crash when unable to load formats during application startup \[bug 31582]
* Fixed render failure using "Prefer Source Codec" when first input shot is not a movie \[bug 32500]
* Fixed rendering with pulldown \[bug 32496]
* Fixed pulldown removal in Sequence operator \[bug 32459]
* Fixed field order options in rendering (-interlace/-progressive in bl-render) \[bug 32503]
* Fixed bl-conform to create a crash report if it fails \[bug 32502]
* Fixed failure to read RAW image sequences (ARRIRAW, RMF etc) stored in resolution directories when the Input Format is set to a crop/full-gate resolution \[bug 32507]
* Format editor Copy button no longer retains previously copied formats \[bug 32508]
* Improved scope performance during playback on some nvidia video cards \[bug 32501]
* Fixed bug where dragging a gallery thumbnail which had fallen back to using its grabbed still (rather than the original media) into another gallery would show an "X" rather than the image \[bug 32504]
* Fixed clipping to 1.0 when rendering OpenEXR from a scene set to 32-bit floating-point cache \[bug 32247]
* Fixed an issue which caused very many index table segments to be created when rendering XDCAM MXF. This in turn caused these files to be slow to open \[bug 32527]
* Fixed crash changing the Audio Codec setting in the Render view when Audio Channels was set to "Auto (from source)" \[bug 32533]
* When formats are chosen during conform, scene formats and job formats are now chosen ahead of global formats \[bug 32529]
* Fixed failure in Verify render \[bug 32620]
* Added workaround for incorrect firmware in some ARRI B+W cameras \[bug 32622]
* Fixed occasional issues with loss of metadata from BLG files, causing problems with multi-paste \[bug 32662]
* Fixed potential "too many open files" and "bad file descriptor" error messages \[bug 32636]
* Fixed slow write speeds for some image formats e.g. DPX \[bug 32567]
* For compatibility with other software, DPX files are now written with both frame rate metadata fields set to the frame rate of the render; the timecode frame rate is no longer stored \[bug 32251]
* Improved speed of fl-cp copies \[bug 32666]
* Fixed renders failing when a disabled deliverable has an error in its configuration \[bug 32235]
* Fixed crash when changing the displayed columns in a table (e.g. on the Queue Monitor View) \[bug 32732]
* On completion, LUT generation now removes the temporary test chart files it has created \[bug 32530]
* Crash when saving Denoise preferences fixed \[bug 32749]
*   Fixed issues with image corruption which could occur while or after working with RED material decoded using the GPU, and related "Unable to obtain GPU memory for RED decode" failures. Both of these issues were caused by a bug in the Nvidia graphics driver \[bug 32729]

    PLEASE NOTE: since corrupted images may have been stored in the cache, cached images written by earlier releases are not used by this release; this means that scenes opened in this release will not retain any previously-cached frames.
* Fixed an issue which caused decode failures and hangs reading constant-rate MXFs with empty variable-rate indexes \[bug 32388]
* Fixed slow replay of 3X16 files from remote machines \[bug 32666]
