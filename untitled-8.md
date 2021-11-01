# 베이스라이트 릴리즈 노트 5.2.11483 (2019-02-27)



## New Features Since Baselight 5.2.11383

### Baselight CONFORM

Installing and running on macOS 10.14 Mojave is now supported. macOS 10.9, 10.10 or 10.11 are no longer supported \[bug 50131]

### Three-Point Insertion

*   Insertion of a single sequence from FLUX Manage View can now use "three-point insertion", taking account of In and Out marks and gaps on the timeline to control where the strip is placed on the timeline.

    *   If there are In and Out marks on the timeline, then the

        sequence is inserted between the marks.
    *   If there is an In mark on the timeline, then the sequence is

        inserted starting at the mark.
    *   If there is an Out mark on the timeline, then the sequence is

        inserted to the left of the mark.
    *   If there are no In/Out marks on the timeline but the cursor is in

        a gap between two stacks, then the sequence is inserted into the

        gap.
    * Otherwise the sequence is inserted at the cursor's location.

    The FLUX Manage View Mark In/Out controls continue to determine the length of the sequence which is inserted.

    Four-point insertion (where there are In and Out marks or a gap, and also the sequence has been marked both In and Out) is not supported.

    This behaviour applies when the Insert button is pressed or a sequence thumbnail is double-clicked.

    The old behaviour (where insertion always occurs at the cursor) can be restored using the Options button above the Insert button on FLUX Manage View.

    In and Out marks can be added to the timeline from the Marks menu, the keyboard shift+\[ and shift+], Blackboard 1 Mark In/Out buttons, or Blackboard 2 and Slate ctrl+Prev/Next Frame buttons \[bug 48421]

    New commands to navigate to the In/Out marks on the timeline have been added to the Marks menu \[bug 50322]
*   Similarly, strip insertion from the Insert menu now also takes account of In and Out marks and gaps on the timeline.

    *   If there is a selected strip, then the strip is inserted below (or

        above) it, as before.
    * If there are In or Out marks on the timeline, then the strip is inserted at or between the mark(s).
    * If the cursor is in a gap between two stacks, then the strip is inserted into the gap.
    * Otherwise the strip is inserted at the cursor, with a default length of 100 frames.

    An option on the Insert menu controls whether insertion at marks or gaps happens regardless of whether a strip is selected \[bug 48421]

### Miscellaneous

* The EDL Import window now gives the option to apply a set of categories to all imported sequences \[bug 46449]
* An OpenEXR sequence will now default to using a track named 'rgba' rather than the first track in the file \[bug 50024]
* An OpenEXR sequence whose first frame has different tracks or channels from the remaining frames is now treated as if every frame has the tracks and channels of the remaining frames \[bug 45964]
* When not in "Ripple" or "Rolling" edit modes, Paste Strips at Cursor now bounces existing strips overlapping the paste location out of the way, rather than failing \[bug 50014]
* There is now an option in Multi Paste to copy the source layer 0 strip categories. These can be appended to or replace the destination layer 0 categories. Also categories can be excluded from the copy \[bug 28968, bug 50147]
* To allow more flexibility in how the scene's start timecode is set/used in EDL Import, the following changes have been made:
  *   The "Overwrite Start Timecode" EDL Import setting has now been

      renamed "Scene Timecode".
  * The "No" option has been renamed "Leave Unchanged".
  * The "Yes" option has been renamed "Overwrite Start Timecode".
  *   The "Position Events Using Existing Scene Timecode" has been

      added. When this option is selected, rather than simply placing

      the new events at the current cursor location, they will be

      placed in the scene using their record timecode and The existing

      timecode of the scene. This is useful for conforming EDLs

      representing a partial update of an existing edit - e.g an EDL

      representing updated VFX shots \[bug 49886]
* Client View can now be set to start automatically when Baselight starts \[bug 50129]
* In 1x1 stereo display mode, when a shape strip is selected the overlays for both that shape strip & the matching other eye's shape strip are drawn in the appropriate output. In this mode interactions with the overlays (eg. dragging control points) are disabled on the image itself, however shape positions can still be adjusted from the desk/trackballs \[bug 46385]
* Added control modifier support to middle trackball when moving shapes horizontally in a stereo scene (with grouped grading enabled). When activated, rather than moving the other eye's shape in the opposite direction (adjusting convergence), both eye's shapes will move in the same direction (adjusting position) \[bug 46385]
*   Media Import Rules now support Metadata mapping of arbitrary text. An additional submenu "Text" has been added to the "From" column of the Media Import Rules Metadata Mapping tab. This menu allows text to be created, edited and deleted for use in rules. Substitution codes supported in these text entries are as follows:

    %L Clip Name %O Comment %E Event Number %D Sequence Filename %N Tape Name %Z Insert Name - name as if inserted from FLUXmanage.

    Using these options in conjunction with setting the "To" column to "Name" allows the name of the input strip to be controlled \[bug 49675, bug 49656]
* Creating (and deleting) shapes in an existing shape strip now obeys grouped grading in a stereo scene (creating/deleting matching shapes in the other eye) \[bug 50300]
* A click in the timecode display area of the timeline now moves the current cursor to the click position \[bug 33142]
*   Added new grouped grading option to the "Edit" menu: "Grouped Grade All Keyframes". This controls how the currently selected operator behaves with grouped grading enabled when that operator contains keyframes.

    If enabled (together with grouped grading), when a change is made to one of the operator's keyframes, the same relative change is applied to all the other keyframes. If disabled, only the keyframe at the current time will be modified.

    In a stereo scene, if the current operator has a matching operator for the other eye (and "Grouped Grade Both Eyes" is enabled), then this also applies to keyframes on the other eye's operator.

    Note: The new "Grouped Grade All Keyframes" option replaces the shape specific "Apply Transform Modifications To All Keyframes" option \[bug 50406]
* Added "Group Grade Both Eyes" to Chalk actions under the stereo section. This will toggle the group grade both eyes setting \[bug 50387]
* When choosing an EXR channel or track in the Reference operator or Layer setup dialog, a thumbnail of each channel/track is now shown \[bug 50257]
* Added ARRI Look Library Scene Looks to FilmLight's website, as an additional download package \[bug 46007]
* Added "Apple: \~2.2 Gamma / P3 D65" colour space to be used with newer Apple displays \[bug 49961]
* Added -left, -right and -both flags to bl-shots to select which stereo track(s) to include in the XML output generated when the -xml option is selected \[bug 50270]
* Updated the Sony RAW SDK to version 3.2.0, which adds support for reading X-OCN XT as well as 6K 16:9 and 6K 2.39:1 bitstreams \[bug 50232]
* Added v5 User Guide \[bug 50375]

## Bug Fixes Since Baselight 5.2.11383

* Fixed FLUX Manage thumbnail failures for some multi-channel OpenEXR sequences \[bug 50024]
* In shape strips, the "Lock Y Positions" toggle setting is now obeyed when dragging/moving control points (as well as transform boxes) \[bug 49956]
* Fixed bug in "Overwrite Start Timecode" in EDL Import view where it didn't offset the start timecode properly if the conform wasn't done at the beginning of the timeline \[bug 49866]
* Fixed failure when grabbing stacks using multi-channel and/or multi-view OpenEXR files to a gallery \[bug 50076]
* Fixed filtering UI being shown in 1x1 Shots Layout \[bug 50078]
* Fixed Shots View filtering not saving or updating correctly \[bug 50103]
* Fixed multi-pasting metadata to include both eyes in stereo scenes \[bug 50199]
* Fixed issues with overlays sometimes drawing incorrectly when playing across strips of different types \[bug 46385]
* Fixed bug which could result in the "Grouped Grade Both Eyes" menu option from being incorrectly (automatically) disabled after using the Stereo Grade operator \[bug 50323]
* Fixed bug where transform overlays were being incorrectly displayed during playback when disabled \[bug 50337]
* Ensure layer strips with no grade changes that have explicit caching enabled are actually cached \[bug 50354]
* Fixed stereo bug where the matte mode (Overlay/Inverse Overlay) would sometimes only be applied to the current eye, rather than both eyes \[bug 50262]
* Fixed inverted custom curve matte un-inverting when opacity is set to zero \[bug 50185]
* Fixed changing the colour of a stereo-split strip \[bug 50383]
* Fixed stereo bug where creating a new tracker from a stereo split strip would not insert the tracker inside the existing split tracker strip, where it should \[bug 50423]
* Fixed an issue where 3X10 DPX files written by Scanity software could be misinterpreted as 1X10 \[bug 49926]
* Fixed reading of 10-bit DPX files that uses packing value 2 (type B) \[bug 50018]
* AES3 emphasis metadata is now written correctly when rendering to Sony MXF. This fixes an issue where these files could be flagged as having metadata errors in the Sony format verification tools \[bug 49957]
* Fixed an issue where the audio waveform view did not work with audio from encrypted DCPs where the KDM was set in the DCP Params strip \[bug 49763]
* Fixed an issue decoding some large RAW files on specific hardware configurations \[bug 50023]
* Fixed an issue where Baselight would fail to start up and report 'No comms from host' \[bug 34409]
* Fixed an issue where timecodes with rate larger than 30fps in MXF containers would always be interpreted as double-frame timecode. This also solves a problem where these timecodes could be flagged as drop-frame when they were not \[bug 50081]
* Fixed an issue where inserting media from local volumes gave the option to change the scene container \[bug 42204]
* Fixed an issue where the incorrect coding equations label could be written to IMF MXFs, along with various minor improvements:
  *   Avaliable colour primaries and transfer function tags are now

      written, even when none of the IMF-specified colorimetry systems

      are used.
  *   Coding equations tags are no longer written when rendering RGB

      essence.
  *   The dialog available to assist configuring the render panel to

      produce IMF-spec colorimetry systems now also shows an option for

      the Y'CbCr matrix to use \[bug 49337]
* Fixed issue where source file was deleted if source and destination were the same while copying in FLUX Manage View via symlinks \[bug 49795]
* Improved UI for Stereo Geometry Fix \[bug 49379]
* Reduced the number of warnings about Grouped Grading when making adjustments to Stereo Geometry Fix \[bug 49378]
* Fixed failure to create a per-job gallery when the opened scene uses a basic Working Format \[bug 50002]
* Improved warning on Render View when using Full to Legal Video LUT with a legacy ProRes deliverable \[bug 49919]
* Fixed crash when attempting to copy an unreadable folder by dropping it on a folder in FLUX Manage \[bug 49756]
* Fixed crash when using Source Alpha on an OFX operator \[bug 49781]
* Fixed crash in Smart Paste when pasting input strip and there is copy protection on \[bug 49776]
* Fixed an issue whereby certain Slate buttons were resetting strips unexpectedly \[bug 49702]
* File and Folder patterns now supported for index and non-index use \[bug 49846]
* Fixed an issue with printing the SDI temperature to the terminal \[bug 49147]
* Fixed issue with Relight3D overlay interfering with certain stereo display setups \[bug 49829]
* Fixed interaction problem in Relight3D with material that has camera matrices stored in a certain format \[bug 49666]
* Improved interaction with Light Intensity and Light Target Distance slider in Relight3D \[bug 49844]
* Improved slate/blackboard button interaction to indicate what current interaction mode is active for Relight3D \[bug 49840]
* Improved desk encoder precision for Target Distance, Cone and Hot spot angle for Relight3D \[bug 49833]
* Fixed an issue that could cause the File System Index to fail to update metadata for sequences \[bug 50118]
* Consolidate now accounts for temporal and time-remapping operators under each Sequence, to ensure that every frame which is needed by the scene is copied \[bug 49662]
* Fixed issue that meant burnin metadata could be incorrect in a stack using a temporal OFX effect (e.g. NeatVideo) \[bug 50009]
* Fixed an issue that could cause the File System Index to be updated more frequently than it should \[bug 50114]
* Fixed an issue with missing symlinks when using the File System Index \[bug 49949]
* Fixed issue with switching paint strips losing the erase brush settings \[bug 49864]
* Fixed a low-level metadata inconsistency when rendering Avid OP-Atom MXFs. These files can now be AMA linked in Avid \[bug 49478]
* Fixed issue in Paint with desk encoders leaving a delta open when switch to a different strip \[bug 49989]
* Improved display of active Media Import Rules to only report rules that do something as being active \[bug 50145]
* Fixed font-specific outline text rendering errors \[bug 50210]
* Network diagnostic now accepts interfaces which are faster than expected \[bug 50237]
* Fixed issue where pop-up showing the active grades in a strip were not displaying correctly \[bug 50266]
* Fixed a crash when user colour space cannot be parsed \[bug 50312]
* Added support for Pro Tools audio stem naming and fixed issue with deleting audio stems when performing another search, with a new option to reset all stems \[bug 43545]
* Fixed crash in EDL Import when finalizing a conform with a gap in the timeline \[bug 50186]
* Added "Display Pixel Offset" customise option for Grid Warp and new options to reset control points to the default grid or to the 'other' grid \[bug 48732]
* Turning on "Display Pixel Offset" in Grid Warp will highlight any displaced control points with an outer ring, in order to quickly see which control points have been modified \[bug 48655]
* Improved the efficiency of data transfers to the Slate control panel. This fixes issues seen when the panel is connected via a USB extender. The change requires updated Slate firmware; please contact FilmLight support for further information \[bug 50090]
* Fixed an issue that prevented MXF-files with multiple partitions of CBE essence from being read correctly \[bug 50360]
* Fixed bug which could cause a crash when adjusting a transform from the trackballs during playback \[bug 13552]
* Fixed bug causing a crash during Timeline Sort \[bug 50398]
* Fixed an issue that prevented some MXF-files with missing essence descriptor metadata from being opened \[bug 50395]
* Fixed an issue where incorrect image metadata in MXF-headers could cause broken decode of thumbnails and images in the affected files \[bug 50400]
* Fixed an issue where UUIDs generated by different processes started at nearly the same time were insufficiently randomised. This affected the IDs generated by fl-kdmtool in particular \[bug 50377]
* Improved spacing of text drawn on macOS Retina displays \[bug 43230]
* Fixed failure when copying sequences from remote media \[bug 49777]
* Fixed warning when compiling some Matchbox Shaders \[bug 49807]
* Fixed UHD setups to default to use Rec.2020 matrix \[bug 49914]
* Timecodes from ARRIRAW files now have a fixed frame rate \[bug 50082]
* Fixed crash in bl-conform when setting containers \[bug 50214]
* Fixed crash in Colour Panel \[bug 50275]
* Fixed crash when loading a scene with a Text strip referencing a non-existant font \[bug 50247]
* Fixed performance issues related to colour space menus \[bug 49369]
* Made re-selection of the current param strip from a multi-selection consistent \[bug 49624]
* Fixed issue causing keyframes of audio sequences to be loaded incorrectly \[bug 49141]
* Fixed potential crash on scene load after using cloned curves in shapes \[bug 50439]
* Adaptec RAID disk diagnostics now report disk serial numbers and locations \[bug 31830]
* Fixed various issues with MaxCLL/MacFALL analysis, including when rendering to a local path and when rendering movies with audio. The per-frame analysis data is now written as floating-point, for greater clarity when the analysis numbers are very small \[bug 50479]
* Paint and Text now deal with missing and renamed colour spaces correctly \[bug 49938]
* Corrected the Timeline offset for Grid Warps undergoing a Timeline Sort \[bug 50481]
* Fixed "too many open files" errors when using a floating licence server \[bug 49958]
* Improved performance issues when browsing folders containing movie files, particularly on 3rd-party storage \[bug 50198]
* Fixed crash when changing the Y'CbCr matrix on some varieties of Sequence \[bug 50518]
