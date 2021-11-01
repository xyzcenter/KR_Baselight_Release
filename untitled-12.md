# Baselight Release 4.3.6187 (2013-08-20)



## New Features Since Baselight 4.3.6117

*   Added the ability to load/save Baselight grades from/to Avid AAF files. This enables an easy, render-free round-tripping workflow with Baselight for Avid within Media Composer/Symphony.

    To load Baselight for Avid grades from an AAF, simply set "Apply Baselight Grades" to "Yes" in the EDL Import panel and conform as normal.

    To save Baselight grades into an AAF file, simply select "Update Avid AAF with Baselight Grades" in the "Export Format" dropdown in the EDL Export panel. This export option has the following options:

    Input Filename: The AAF file originally used to conform the timeline. Output Filename: The name of the AAF file to be generated. The generated AAF will be identical to the input AAF in structure, other than containing Baselight for Avid metadata in every shot. Remove Avid CCs: Used to remove Avid colour corrections. Remove Strips of Category: Used to remove strips tagged with a given category. This is typically used to remove Transforms applied during EDL Import so that the transformn doesn't get applied twice back in Avid. Continue on Error: Whether or no the EDL Export should abort if any shot can't be exported.

    The only Baselight grades which can't be exported to Avid are those stacks which include temporal effects (eg Temporal Degrain, Motion Blur, DSpot etc) or those stacks with split strips.
* Improved the "Modify AAF" workflow in several ways:
  *   Failures to relink a single clip no longer cause a hard

      failure to generate a modified AAF. Instead, as many clips

      as possible are relinked with detailed error reporting

      for any clips which failed.
  *   The actual AAF modification is now done in a separate

      process, meaning that crashes in the Avid AAF library

      no longer crash Baselight and prevent a modified AAF

      being written. Instead, Baselight detects a crash in the

      sub-process and redoes the modification, simply omitting

      the problem clip.
  *   AAFs in which clips failed to relink are now automatically

      sent to FilmLight for analysis, along with sufficient&#x20;

      metadata to reproduce the issue.
  *   Improved AAF speed change conform handling to only show

      warnings when variable speed change encountered plus better

      handling of Avid MC timewarps.
* Changed filename conform to initially try conforming using a common base directory, then if that fails to find anything, it assumes all media is in a single directory.
* Changed AAF conform to handle MXFs slightly differently. Previously if a clip spanned two MXFs, the conform split this into two clips. Now the conform handles this as a single clip.
* Added FCP Flip/Flop support.
* Add the ability to set the keyframe interpolation mode for Transforms added by EDL Import \[bug 25054]
* Added support for NVIDIA Quadro NVS 510 graphics card for UI hosts \[bug 23507]
* Added support for reading AVC-Intra MXF files written by Avid products \[bug 14622]
*   Updated to RED SDK v4.4, RED Rocket driver v1.4.33.0 and RED Rocket firmware v1.1.17.3.

    This adds:

    *   Support for the Mysterium-X Monochrome sensor in the Epic-M

        Monochrome and Epic-X Monochrome cameras (only with RED Rocket

        disabled at this time)
    * DRX is now available on the RED Rocket
    * Additional metadata support, including user-defined metadata

    Users of RED Rocket cards installed in Baselight Linux systems will need to update the RED Rocket card's firmware using the rocketup\_1.1.17.3 utility included with Baselight. Ensure that all systems hosting the RED Rocket cards are shut down and restarted after updating the firmware.

    Users of RED Rocket cards installed in Baselight Kompressor systems will need to:

    1. update the Rocket driver using the installer package REDrocket\_Driver\_OSX\_v1.4.32.0.pkg that can be found in the /Applications/Baselight/Current/Utilities/Resources/etc folder.
    2. update the RED Rocket card's firmware using the rocketup\_1.1.16.11 utility included with Baselight (be aware that a bug in this utility causes it to report the wrong version number while it is running; do not be alarmed by this).

    Ensure the Kompressor is shut down and restarted after updating the firmware.
* Modified AAF relinking after render to check that the AAF file didn't change since conform. Baselight will no longer relink to a changed AAF file \[bug 25212]
* Made improvements to the "Overwrite Tape Name" EDL Import setting:
  *   Added the "With Filename" option, which allows you to overwrite

      the tapename with the first  characters of the event's

      filename.&#x20;
  *   Removed the "" option, as it generated a lot

      of spurious conform tabs which very rarely helped, as the

      default number of leading characters (16) was usually wrong

      \[bug 25313]

## Bug Fixes Since Baselight 4.3.6117

* Fixed crash handling very large shapes \[Bug 20799]
* Fixed render hang on rendering movies on BL8 \[Bug 24605]
* Allow yfs filesystems for /mnt/disk1 on some systems \[bug 22694]
* Fix crash on startup in Baselight \[bug 23131]
* Ensured custom film grade page configurations setup in Baselight version 4.4 don't crash version 4.3 \[bug 25056]
* Ensured formats using new Baselight 4.4 colour spaces are unavailable and do not cause issues \[bug 25067]
* Fixed crash when exporting BLGs from a scene whose Working Format is not defined in global preferences \[bug 25063]
* Playback monitor improvement, pending reads replaced with completed reads. The read monitoring now takes into account the position in the playback queue of the read request \[bug 24674]
* Fixed the 'Zones' diagnostic to be less likely to hang when systems in the cloud are unreliable \[bug 23970]
* Fixed mix and transitions not working together when doing an AAF conform \[bug 16108]
* Fixed issue with AAF reading crashing - patch to AAF library \[bug 19953]
* Fixed issue with XF305 MXF files containing subclips \[bug 22968]
* Modified AAF conform to conform filenames correctly \[bug 20970]
* Fixed a problem with the SMPTE-352 payload identifier packet that upset Panasonic plasma displays \[bug 24991]
* Baselight would occasionally freeze on older Supermicro H8QM3 systems. This release adjusts the MTRR register on such systems to avoid the freeze \[bug 24723]
* Fixed issue conforming MXF files containing subclips \[bug 25049]
* Fixed crash when applying to stack in replace mode with copy protected categories \[bug 25161]
* Fixed issue with timeline rippling when inserting Baselight grades into AAF files \[bug 25217]
* Fixed issue with incorrect xfs attributes \[bug 25220]
* Modified AAF relinking to add a version number so that future relinking can be compatible with conforming in earlier versions. Anything without a version number is assumed to be prior to this release \[bug 25212]
* Fixed issue where views would turn white after switching workspaces \[bug 24218]
* Fixed failure to recognise Sony RAW MXF files with a zero-sized marker rectangle \[bug 25269]
* Multi-Insert of movies which span multiple MXF files now inserts only one copy of the movie \[bug 25261]
