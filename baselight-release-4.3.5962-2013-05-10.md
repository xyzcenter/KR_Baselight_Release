# Baselight Release 4.3.5962 (2013-05-10)



## New Features Since Baselight 4.3.5900

### Baselight Grade Files (BLGs)

* This releases marks the introduction of the Baselight Grade (BLG) format. BLG files are a new mechanism for storing Baselight grades, allowing them to be easily loaded and exported to/from full Baselight, the various Baselight Editions and FLIP.
  *   BLG files are essentially OpenEXR files. They contain 3 image

      layers:

      &#x20; Default: An image displaying a wipe between the graded and

      ```
      ungraded versions of the image. This makes it easy to see
      in a glace the effect of a grade.
      ```

      &#x20; Source: The ungraded input image, in its native colour space.

      &#x20; Graded: The graded image, in its native colour space.

      Having both the input and the result available in a single images

      is very useful, as it make it easy to construct a LUT which

      represents simple grades on non-Baselight systems.
  *   BLG files also contain all the metadata required for Baselight

      to reconstruct the grade stack in its entirety, including

      spacial operations like blurs and shapes, which cannot be

      represented by simple LUTs.
  *   BLG files also (optionally) contain all the keyframes of the

      exported grade, allow them to contain the intent of a complex,

      dynamic colour correction.
  *   If a grade requires external resources to achieve its look, then

      the external files are compressed and included within the BLG -

      typical examples would be LUTs and Truelight profile, looks etc.
  *   Each BLG has the "BLGName" attribute, which is simply the name of

      the BLG file without the ".blg.exr" suffix.
  *   Each BLG also contains the "BLGID" attribute, which is a 32-digit

      string derived from the contents of the source image and the

      Baselighr grade applied to it. This make it an excellent piece

      of metadata to use to match grades to shots, as BLGIDs are

      _extremely_ likely to be unique within a project.
*   To generate BLG files, select the shots you what BLG equivalents of and select the new "Export BLGs..." option in the "Actions" menu at the bottom-right of the Shots View. This launches a dialog with the following settings:

    * Directory: The directory into which the BLGs are to be exported.
    *   Template: A template defining how the exported BLG files are to

        be named. Most of the standard Baselight text substitutions (eg

        %N for tape name etc) can be used. To see all the possible

        substitutiosn, click the "?" button to the right of the template

        edit field.
    *   Scale: Resolution of OpenEXR files you wish to generate: Full,

        Half, Quarter etc. This option is used to make BLG files smaller,

        but whatever the resolution they are exported at, they will

        still behaviour like full resolution images when imported back

        into Baselight.
    *   Frame: Whether to use the first frame or the poster frame as the

        representative frame of the shot.
    *   Keyframes: Whether or not you wish the BLG file to contain

        keyframes. If "No" is selected, then the grade will be sampled

        at the "Frame" position and will contain no keyframes. If "Yes",

        then the BLG will contain all keyframes and they will be imported

        when the BLG is loaded by Baselight.
    *   Preview Image Transform: The color space of the "Default" (wipe)

        layer of the OpenEXR file. "Linear" means that the preview will

        be expressed in a true linear colour space - this option is good

        if you wish to import BLG files into something like NUKE.

        "Linear (Mac OS X compatible)" means that an additional correction

        factor is applied to the preview to make it look correct when

        viewed in the Finder or Preview on Mac OS X - this is required

        because Mac OS X doesn't appear to treat true linear images

        properly.

    Once, you're happy with the settings, simply click "Export".
* A single BLG file can also be quicky exported via the "BLG Quick Export" command, which is mapped to the Alt+e accelerator. The BLG file will be written to the directory specified by the "BLG Quick Export Directory" preference (located in the "BLG" section of the "System" tab). The filename of the BLG will take the form of: YYYYMMDD\_HHHMM\_SS.blg.exr
* The Sequence Browser has been updated to include BLG file support:
  *   BLG files found within a directory listing have a coloured icon

      beside them to make them easy to spot.
  *   A selected BLG file will display the timecode/keycode ranges

      the BLG file represents, even though the OpenEXR file contains

      a single image. The ranges shown are the ranges of the original

      shot the BLG was exported from. Also displayed are the BLGName

      and BLGID attributes which every BLG file contains.
  *   The "Default" (wipe), "Source" and "Graded" layers can be viewed

      by selecting the appropriate layer in the dropdown beneath the

      metadata section.
  *   Like any other type of image, BLG files can be inserted/multi-

      inserted into a timeline, by clicking "Insert at Cursor" (this

      button was previously called "Insert Below") or "Multi-Insert".

      BLG files inserted onto the timeline will have exactly the same

      shot lengths, metadata and keyframes as the shots they were

      originally exported from, simply applied to the "Source" layer.
  *   When other strips in the Timeline View are selected, then the

      button changes to "Insert BLG Grade Below". Clicking it will

      result in the grading stack represented by the BLG being inserted

      below the bottom-most selected strip in each selected shot.

      The "Include Layer 0 Operations" paste option is obeyed, allowing

      any Layer 0 operations present in the BLG (debayering operators

      for example) to be applied to the selected stack.
  *   If a resource contained within the BLG (eg a Truelight profile)

      has the same name as an existing resource, then a dialog will

      pop up, asking the user how they wish to resolve the conflict.

      There are three possible resolutions:

      &#x20;  Rename: Import new version under a new, non-conflicting name.

      &#x20;  Replace: Replace the version on this machine with the version

      ```
       from the BLG file.
      ```

      &#x20;  Original: Use the version on this machine instead of the

      ```
       version from the BLG file.
      ```
* The new Multi-Paste View includes BLG support, allowing the user to quickly paste grades from a directory of BLGs onto shots with matching metadata. See below for details.
*   The EDL Import View is now able to read BLGName and BLGID metadata out of the comment field of any EDL type. Syntax examples:

    BLGNAME=my\_example\_blg BLGID=7e07c10ac51b276ef35875941f53cfbc BLGNAME=my\_example\_blg, BLGID=7e07c10ac51b276ef35875941f53cfbc

    This functionality is very useful in associating a look with a shot, as after an EDL is imported, the new Multi-Paste view can be used to apply the appropriate grade, simply by matching against BLGName or BLGId.
* BLGName and BLGID columns have been added to the Shots View, allowing the user to see what looks have been associated with each shot.
* The fl-imageinfo now supports BLG files and will emit BLG-specific metadata in addition to the normal OpenEXR data.
* Added bl-applyblg utility to apply a BLG to a sequence or movie. Run "bl-applyblg -i" for usage information.

### Strip Categories

*   Paste Protection Category:

    A new category type has been added which allows the protect of strip from being changed during a paste action. Layers containing strips that have a no paste category will not be modified during any paste action. They will not be removed, written over or have their mattes changed. This category is labelled "Don't paste over strips of category".

    Note: This use of categories replaces the "NO\_PASTE"-in-strip-name hack available in previous releases. It has now been removed.
*   Copy Inhibit Category:

    A new category type has been added which allows a strip to be inhibited from being included in a copy action. Layers containing strips that have a copy inhibit category will not be included in any paste action when they are present in the source stack and protected by the copy inhibit category. This category is labelled "Don't copy strips of category".
*   Both are used in Apply actions, Blackboard copy and paste, and keyboard or Edit Menu copy and paste. Copy inhibit and paste protect will only work for strip categories - using a mark on a strip will have no effect on copy and paste.

    Existing categories can be added and removed to the new types via the preference or scene settings. The category groups found in Scene setting "Category Group" tab allow the categories types to be set on a per scene basis. Existing categories can be added and removed to the new types. Category groups can also be set up via the preferences panel, under the "Timeline" tab, to work across scenes.

### Multi-Paste View

* Baselight's Multi-Paste functionality has been extended and is now accessed from the Multi-Paste View (View menu). This new view contains the following settings:
  * Source: Specifies where the source grades are to be obtained: Current Copy Buffer: The current contents of the copy buffer. This is the equivalent to the multi-paste source in previous versions of Baselight. Multiple Scenes: Allows the user to select multiple scenes by clicking "Select Scenes", which will launch a job browser. This brower allows the user to add/remove scenes to/from a list via the "Add Selected Scenes" and "Remove Selected Scenes" buttons. All the scenes in a job can be added by selecting a job and clicking "Add All Selected Scenes In Job". BLG Files: Allows the user to paste the grade stacks contained within a directory of BLG files. This is an excellent way of restoring the grade pre-visualised on set using FLIP at the start of the final grade.
  * BLG Directory: When pasting BLG files, specifies the directory where they are to be found.
  * Resolve BLG Resource Conflicts By: Specifies how Baselight is to resolve file naming conflicts caused by inporting resources containing within a BLG file (Truelight profiles, cubes, looks etc). There are three possible strategies: Replace Existing Resources with BLG Versions: If there is already an existing resource with the same name as the resource contained within the BLG file, then the existing resource will be overwritten by the BLG's version. Use Existing Resources with the Same Name: If there is already an existing resource with the same name as the resource contained within the BLG file, the existing resource is used in the grade stack. In this case, the BLG's resource will not be imported. Import BLG Resources Under a New Name: If there is a naming conflict, then the BLG's resource will be imported using a name which doesn't conflict and the grade stack updated to reflect this.
  * Match Shots By: Allows the user to specify the metadata by which shots are matched with one another.
  *   Paste: Specifies whether or not operators from layer 0 (the top of stack) in the source shot are copied to layer 0 in the destination shot: Stack Only (exclude Layer 0): Copy the source stack, but do not copy layer 0 operations - this matches the behaviour of multi-paste in previous versions of Baselight. Layer 0 and Stack: Paste _both_ the source stack and the source layer 0 operators. Layer 0 Only: Paste _only_ the layer 0 operators.

      When pasting of layer 0 operators is enabled, a dropdown appears allow the user to specify what happens to the existing operators in layer 0: Overwrite Layer 0 Operators: All destination layer 0 operators are overwritten, other than "Sequence" and "Audio" operators. Append To Existing Layer 0 Operators: All destination layer 0 operators are retained and the copied operators are appended at the bottom, unless an operator occurs in both source and destination and the destination operator is in its default state - in that situation, the source operator will overwrite the destination operator in its existing location.
  * Source Stacks: Specifies what strips are to be copied from the source shots: Copy All Strips: All strips will be copied from the source stack. Copy All Strips Except Of Category..: All strips will be copied, except those tagged with one or more of the categories specified by selecting options in the "Choose" dropdown menu. Note that tagging a grade strip with an excluding category will result its matte also being excluded and vice versa. Copy Only Strips Of Category..: Only those strips tagged with one or more of the specified categories will be copies.
  * Destination Stacks: Specifies what strips in the destination shot, if any, are to be retained: Overwrite All Strips: All strips in the destination stack are to be removed prior to the paste. Overwrite All Strips, Except Strips Of Category..: All strips are to be removed, except those tagged with one or more of the categories specified. Retain All Strips: All strips will be retained. Retain All Strips, Except Strips of Category..: All strips will be retained, except those tagged with one or more of the categories specified.
  *   When there is a chance of strips being retained in the destination stack, a dropdown appears allowing the user to specify where the new strips should be pasted, relative to the existing stack: Paste Above Existing Strips Paste Below Existing Strips

      KNOWN ISSUE: It is not currently possible to merge the layers of the source and retained destination stacks, the copied strips will all lie either above or below the retained strips. This merge functionality will be added in a future release.
  * Shred Composites Into Separate Shots: A single-stack composite is a composite where the timeline extent of the top side of the composite completely matches or overlaps the bottom. A standard foreground/background chroma-key would be a good example, whereas a dissolve transition would not. This setting specifies how these should be treated: No: The entire compositing stack will be treated as a single shot, with the metadata coming from layer 0 (top of stack). Yes, Except For Composites Of Category..: Each individual element of the composite will be treated as a separate shot and will be pasted separately, unless the compositing operator has been tagged with one or more of the categories specified. If a composite is shredded, the compositing operator which combines the shot will _not_ be pasted. This is useful if the destination scene has an existing compositing structure and you simply wish to paste the grades.
  * Treat External Mattes As Individual Shots: Specifies whether or not external matte sequences (eg rotoscopes) are to be treated as separate shots, rather than being included as part of their top strip's shot. This is useful when the destination scene has an existing external matte structure (eg automatically generated scenes for CG animated movies) and you simply wish the copy the grades.
* Pressing "Multi-Paste" in this view will perform the multi-paste according to the settings specifies, with feedback being provided in the progress area. If multiple source scenes are specified, each source will be opened in order, a multi-paste performed and the scene closed. Once a shot has received a grade from a source scene, it will _not_ accept a grade from any other subsequent scene.
* The Multi-Paste View now provides detailed feedback as to which destination shots had grades successfully pasted onto them and where those grades came from. Simply clicking on individual lines in the progress area will wrap the current cursor to the appropriate source/destination location. In the case of BLG file sources, then the Sequence Browser will be opened to display the BLG file in question. Pastes where there was no ambiguity will be marked in green. Pastes where multiple source shots matched a destination shot will be marked in orange, encouraging the user to check them carefully. If the source shot lies in a closed scene, the scene will be opened into a new cursor.
* Much like Timeline Sort, multiple tabs of different Multi-Paste settings can be stored in tabs of the Multi-Paste view.
* The Ctrl+m shortcut (Cmd+m on Mac) now simply applies the current Multi-Paste Views's settings without needing the view to be visible. The "Multi-Paste Mode" sub-menu in the "Edit" menu from previous versions of Baselight has been removed - all multi-paste settings are to be edited using the Multi-Paste View.
* The Multi-Paste View can be popped up/popped down using the Win+m accelerator (Ctrl+m accelerator on the Mac).
* Added a number additional filter types to Multi-Paste:
  * BLGName
  * BLGID
  * Clip Name
  *   Avid UID: Very useful when multi-pasting between two

      &#x20; different AAF conforms. Avid's media management

      &#x20; is based around the concept of tagging media with unique

      &#x20; identifiers (the UID), so the same media referenced by two

      &#x20; different AAFs will typically have the same UID.

      * Case-invariant variations of a number of existing filters.

### Timeline Sort

* Changed the appearance of the "Remove Strips Of Category" option to match the appearance of other category-related settings in other views.
* Renamed the "Composites" setting to "Shred Composites Into Separate Shots", and changed its options to match those in Multi-Paste View. Just like Multi-Paste View, it is possible to prevent a composite being shredded by specifying one or more categories from the "Choose" menu.

### EDL Import

*   The "Copy Grades" setting has always used multi-paste internally to do the copy, and this is still the case. However, its behaviour has been changed slightly in light of the possibilities offered by the new multi-paste. When active, it now behaves like a multi-paste with the following settings: Layer 0: Paste Layer 0 and Stack.

    Source Shots: Copy All Strips

    Destination Shots: Overwrite All Strips

    Shred Composites Into Separate Shots: No

    Treat External Mattes As Individual Shots: No.
* Copying grades using different settings will need to be done as an explicit multi-paste using the Multi-Paste View.

### Audio

* Added support for AAC audio decoding from QuickTime files. This requires an additional license option, which is available at no extra charge. Please contact Baselight support for an updated license \[bug 15471]
* Added support for AAC audio encoding when rendering to QuickTime or MP4 on Linux. This requires a additional license option, which is available at no extra charge. Please contact Baselight Support for an updated licence \[bug 15471]
* Added support for discrete audio tracks when rendering to QuickTime or MP4 movies. In this mode, each audio channel is placed into a separate track in the movie file \[bug 22018]
* Added support for specifying surround-sound channel layout when rendering to QuickTime movies with discrete audio tracks.
* Added constant offset parameter to Audio Sync view. This is a value in frames (accurate to one tenth of a frame) which is added to the audio offset when synchronising based on timecode. It allows for a constant delay between the audio and video to be compensated for during the automated Audio Sync process.
* Improved Shot Timecode, File Timecode and File Timecode 2 audio sync modes where audio file starts after the start of the image sequence.
* Added support for adjusting the Audio Offset for multiple selected shots via the Waveform View when Grouped Grading is enabled. This works for sliding the offset offset by dragging in the Audio Waveform view, and also when using the Nudge Audio Left/Right keyboard shortcuts.

### Rendering

* Rendering of H264 movies will now default to using multiple threads on machines with multiple cores \[bug 22425]
* Added option to use Clip name from Shots View as the Tape name when rendering.
* Added %n and %{FrameCount} to render filename template; this is a counter which starts at 0 and increments regardless of the frame range(s) being rendered \[bug 18642]
*   Added support for file numbering expressions in Render View and bl-render. This extends the existing numbering options: %F - timeline frame number - %{TimelineFrame} %T - timeline timecode - %{TimelineTimecode} %G - shot frame number - %{ImageFrame} %H - shot timecode - %{ShotTimecode} %E - timeline frame number at shot start - %{ShotStartFrame} %U - shot timcode at shot start - %{ShotStartTimecode} %n - rendered frame count - %{FrameCount} by allowing a mathematical expression to be used instead.

    Examples: %.6{F+2000} - first frame on timeline renders to 002000 %.7{F-E} - each new shot starts numbering at 0000000 %{F-E+1} - each new shot starts numbering at 1 %.5{F\*2+100} - 00100, 00102, 00104 etc %.6{10001+n} - 010001, 010002 etc, regardless of frame range

### File Formats and Codecs

* Added support for concatenating Canon C300 and Panasonic P2 clips that are spread across several MXF files \[bug 23307, bug 22513]
* Sony F65RAW MXF files can now be decoded at 8192x4320, 7680x4320, 8192x2160 and 6144x3240 resolutions, by setting an appropriate input format (note that this will be slow) \[bug 22701]

### Miscellaneous

* Added support for controlling which Baselight Kompressor (if any) to use when decoding QuickTime movies for images and audio:
  *   Scene Settings View allows the Kompressor used by a scene to be

      changed.
  *   Setups controls the setting for new scenes, and this setting is

      also used in the Sequence Browser and bl-browse \[bug 15160]
* It is now possible to slide away the operator selection section of the Grade and Matte tabs to get more screen real estate on smaller displays. Simply click the small triangle to the left of the operator section.
* Added the ability to "Remove Strips Of Category" to the "Update FCP XML with Baselight Grades" Export panel. This is useful to remove Transform strips added as part of EDL Import, which we don't include when updating an XML, as it would result in the transform being applied twice (once by FCP itself and once by the Baselight plugin).
* The Machine Control view is now toggled up/down using the Win+v shortcut (Ctrl+v on the Mac).
* Added Circle Take column to Shots view. Circle Take data is read from ALEs when imported into Baselight, and can be written into ALEs. The value of the Circle Take column is also available in the burn-in editor using the %{SrcCircleTake} variable.
* Added support to Burn-Ins for original conform CDL values and current CDL values when using CDL-compatible video grades. The variables %{ConfASCSOP} and %{ConfASCSAT} can be used to burn-in the original CDL values taken from a CDL or ALE. The variables %{ASCSOP} and %{ASCSAT} contain the current CDL grade values being applied.
* Sony F65RAW MXF files now show the filename as both Clip and Tape metadata.
* Added support for using %U and %.#U when naming movie files to allow the shot start timecode, converted to frame number, to be used to generate a name for a movie file.
* Fixed "Add All Scenes in Folder" button in Multi-Paste source scene selection dialog so that scenes in all subfolders are also add to the list of source scenes.
* Added "Remove All" button to Multi-Paste source scene selection dialog.
* Added DVI 1920x1080 24p and DVI 1920x1080 25p video modes for DVI-only operation.
* The Sequence Browser "Insert Below" button has now been relabeled "Insert At Cursor" to better reflect its actual behaviour.
* The fl-ls tool has a new option -M, which displays all metadata from the listed sequences. The existing option -m is unchanged.
* "Raw Image Alpha Channel" is now an option in Preferences for the Reference default mode \[bug 23477]
* Added support for Tangent panel trackball controls to Transform \[bug 22688]
* Added "RGB Overlay" mode to the RGB Parade. This overlays the three waveforms over one another rather than side by side. This mode cannot be used simultaneously with the Luma Waveform or YCC Parade.
* Added "Overlay Intensity" to the Luma Waveform, RGB Parade, YCC Parade and Vectorscope. This allows you to change the brightness/intensity of the overlay.
* View layouts accessible through Blackboard numeric keypad "Views" mode are now available as individual Actions in Chalk \[bug 22751]
* fl-rm now allows deletion of individual frames of a sequence, using the form fl-rm /vol/images/.../%.7F.dpx:100 \[bug 23602]
* The Baselight version used to create and save scenes (where this is known) is now shown on the Job Manager.
* Added Chalk actions for Save, Save As and Close \[bug 23803]
* Added new bl-timecode utility to report a scene's timeline start timecode \[bug 23915]

## Bug Fixes Since Baselight 4.3.5900

* If you cannot open a scene because all 9 cursors are active, Baselight now warns you before opening the scene \[bug 23039]
* Fixed crash exporting FCP XML from a scene with a scene-local working format \[bug 22278]
* Added names for several previously unrecognised decks, including XDCAM BluRay \[bug 23250]
* Fixed memory leak with OFX plugin on-demand renders \[bug 23313]
* Fixed bug in Timeline Sort where it wasn't possible to construct a "Sort By" order of "Directory", "Filename", "Frame Number".
* Removing strips from within a stack now deals much better with gaps between strips. Previously, gaps were never removed, leaving spurious space below remaining strips in the stack.
* Grabbing to the gallery no longer incorrectly grabs only the input layer if "Layer 0 Ops" is selected.
* "Include Input Strip" has been renamed to "Include Layer 0 Operations" to match cutview.
* fl-ls now gives the same results when invoked on a single image or movie as on a directory containing that file \[bug 23372]
* Fixed crash in video grade when set to CDL mode and hitting reset on the Blackboard \[bug 21533]
* Fixed compressor name for QuickTime movies written from Linux as shown in QuickTime Player's "Format" field \[bug 21836]
* Fixed problem conforming against image sequences \[bug 22202]
* Fixed behaviour of Decode operators (e.g. Sony RAW Decode) when copied and pasted into other shots \[bug 23383]
* Fixed memory leaks that could occur in the DKey, Matte Tool and Tracker rops \[bug 23423]
* Fixed crash in multi-paste which could occur if the copy data contained strips which had been deleted after the copy was done \[bug 23426]
* Audio file types are no longer listed in the "File Types" dropdown in the EDL Import View.
* The "48@24fps" and "50@25fps" frame rate options no longer appear in the EDL Import panel when importing 24 and 25 fps ALE edls.
* fl-cp now reports the filename causing a "too many levels of symbolic links" error \[bug 23425]
* Removed display of Tangent-specific desk layouts from Chalk tool, selecting them would cause unexpected behaviour on Blackboard 2 \[bug 23424]
* Fixed crash when a filename template contains a very large field padding \[bug 22516]
* Baselight now rejects filename templates with field padding more than 99 \[bug 22516]
* Fixed crash when turning on mask and burnin, when gallery scene format doesn't have a mask of the same name \[bug 23458]
* Updated firmware for 3ware cards 9650se and 9750 \[bug 15234]
* Baselight ONE systems now run the raid3wareconfig diagnostic
* Diagnostics on Kompressors now warn if the myricom driver is older than version 1.3.3 \[bug 23449]
* Fixed render failure in Sharpen through a matte when gain is zero \[bug 23532]
* Fixed diagnostic hang on Mountain Lion kompressors. Note that Mountain Lion is not yet a fully supported platform \[bug 23565]
* Update 3ware toolset to 3w-9xxx.9.5.5.1 \[bug 22557]
* The colour of some RAW-format files, such as Canon CR2, was previously occasionally stretched to fill the 16-bits available. This could cause flickering between frames. New scenes with these files now decode the images without scaling \[bug 23443]
* Fixed crash reading some QuickTime files on Mac \[bug 23574]
* Fixed caching of first frame of scene after deletion of source material \[bug 23503]
* Fixed bug where taking finger off Ctrl first when splitting a strip with Ctrl+I(Toggle Mark) on Blackboard desks would also incorrectly drop a mark \[bug 22940]
* Fixed incorrect interpretation of quicktime edit lists on Linux causing incorrect calculation of movie length, offset and frame rate \[bug 22458]
* Fixed "Invalid audio channel layout index" error when rendering to a movie with audio.
* Fixed SSDs not having a SMART seek error count \[bug 23296]
* Made flioinfo figures more consistent by replacing the fixed file count with one relating to the measured IO performance \[bug 6449]
* Fixed issue where opening certain quicktime files would take a long time and produce lots of "skipping corrupted frame" errors in the console \[bug 23680]
* Fixed crash when using %f in a sequence template \[bug 23654]
* Added the profile or cube name to the error reported when loading the profile failed \[bug 23720]
* Improved memory usage when an OFX plugin uses many images in an analysis pass \[bug 23313]
* Fixed kOfxImagePropUniqueIdentifier in OFX plugins \[bug 22475]
* Fixed crash on quit when multiple shots are selected in Cuts View and an overlay is active \[bug 23679]
* Fixed shearing in Sony F5/F55 thumbnails in flux \[bug 23463]
* Fixed initial selection in file panels, e.g. when browsing to replace stem audio files from Scene Settings \[bug 23737]
* Fixed issue where the last frame in some MXF files would fail to decode \[bug 23742]
* Fixed issue where Chalk-remapped left trackball bottom-left and bottom-right buttons stop working when a Shape strip is active \[bug 23142]
* Fixes issues with scene creation (and Save As) in an imported job \[bug 20762]
* Fixed crash opening System Monitor on Baselight PORTABLE \[bug 23766]
* Fixed cancel button on OFX progress dialogs \[bug 23767]
* Critical syslog errors are displayed in the Baselight alert panel \[bug 13327]
* Fixed crash viewing gallery shots that were dragged from Cuts View \[bug 23368]
* Fixed meta data of cached strips on clusters \[bug 23818]
* Fixed UI issues preventing changing the channel list using the Channels popup in the Audio Waveform view.
* Fix memory leak when rendering an audio file to a remote Baselight system \[bug 22652]
* Fixed crash which could occur when scrubbing a thumbnail after grabbing to the Gallery via a drag \[bug 23368]
* When user attempts to insert or appy a BLG created by a newer, incompatible version of Baselight via the Sequence Browser, Baselight will present a dialog box explaining that the BLG grade data cannot be loaded. The EXR image sequence will still be inserted into the timeline however \[bug 23865]
* Fixed System Information diagnostic which was not including all required information \[bug 23866]
* XFS diagnostic checks the syslog for filesystem warnings which have appeared since xfs\_repair was last run \[bug 13327]
* Improve reliability of purr automatic wake-up of UI host \[bug 22649]
* Added scrollbar to the Mark/Strip Categories preferences editor, to fix issues when there are many categories defined \[bug 23894]
* Fixed transport controls on Avid Transport panels \[bug 23872]
* Fixed crash in Audio Waveform view when the user attempted to adjust the audio offset by Ctrl-dragging in the audio waveform view with no active audio sequence in the timeline \[bug 23902]
* Fixed "movie is not open" errors when rendering from a Baselight ONE to a global "mount" volume which is mounted on the same Baselight ONE \[bug 23492]
* Fixed incorrect colours on some (e.g. yuv2 codec) QuickTime movies read by a Baselight Kompressor from a volume not hosted via a Baselight Kompressor \[bug 23906]
* Fixed occasional failures to import scenes \[bug 23974]
* Fixed memory leak when reconnecting to Blackboard 2 \[bug 23123]
* Fixed Telecine Grade trackball reset buttons not being labeled on Blackboard 2 desks \[bug 22669]
* Fix for incorrect trackball reset button behaviour on Tangent Element/Wave desks when editing parameters in triple slider mode \[bug 23222]
* Fixed crash when holding the Mark key on Blackboard 1 \[bug 22772]
* Reduced time taken to update Blackboard 2 ONE screens \[bug 23262]
* Fixed error with Truelight profiles using lutLength{2} with outputDisplay \[bug 22699]
* Updated Truelight library for improved handling of LUT files in non-Truelight formats \[bug 23358]
* Fixed bug in StereoGrade which prevented picking to set the zero-convergence point when in Anaglyph, Interviewed, Checkerboard or Difference display modes \[bug 22948]
* Fixed minor bug in bl-shots' "-replace" mode where it would incorrectly report the number of mappings it had read from stdin.
* Increased timeout checking licences at startup \[bug 22555]
* Fixed broken behaviour of "+" and "-" buttons on Blackboard 2 soft keyboard numeric keypad \[bug 22976]
* Fixed crash when pressing  on Blackboard desks in Truelight Player application \[bug 22771]
* Fixed CtrlLock on Blackboard 2 desks, now modifies encoder behaviour for fine-tuning values \[bug 22849]
* Free space on pfs is now calculated as (number of nodes x minimum space on any node) to better reflect the usable space \[bug 23069]
* Busy services can now be stopped more reliably, especially at shutdown \[bug 23302]
* 3ware statuses of 'SMART-FAILURE' will now be reported in the appropriate diagnostic module \[bug 23297]
* Fixed cache rechecking after an OFX plugin button press \[bug 23270]
* Fixed some keyboard shortcuts on Baselight PORTABLE, notably anything using shifted number keys \[bug 23021]
* Added support for OfxParamPropStringFilePathExists in OFX plugins \[bug 22395]
* Changes to Render View presets are now saved immediately \[bug 22990]
* The "Grouped Grade Stacks Above/Below" setting is now persistent \[bug 22364]
* Fixed crash if the Gallery "Display UI Controls" preference was turned off \[bug 22321]
