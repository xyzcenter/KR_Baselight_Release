# Baselight Release 4.4.6234 (2013-09-20)



## New Features Since Baselight 4.4.6201

*   Added support for the new Slate control surface. Slate uses the same technology as the Blackboard 2 but in a smaller, more portable form.

    The soft-mappable buttons are used to allow Slate access to the breadth of Baselight features. The left and right panels, each consisting of 24 buttons, can be quickly switched between a selection of with Slate Layouts. The initial set of Slate Layouts consists of:

    * Keypad
    * Layers
    * DBS
    * Display
    * Stack
    * Transport

    Buttons relating to the current strip are displayed when no Slate Layout is active.

    Undo/Redo, Copy/Paste, UI/Image, Layer Up/Down, Keyframe Toggle and playback controls are present above the trackballs, along with the trackball/ring reset operators.

    The Slate encoder push buttons function as reset buttons.
* Added a new "Merge events around CMX3600 dissolves" option in the "Timeline"->"Conform" tab in the Baselight preferences. CMX3600 EDLs often have the incoming or outgoing events in a dissolve split into two. If the option is on (the default, matching the previous behaviour), Baselight will attempt to merge events with matching tape name and timecode, so that the user doesn't need to merge manually. However, this is not always appropriate, especially in situations where the source timecode is monotonically increasing. Switching off this option disables the merging behaviour.
* Blackboard 2 encoder push buttons now reset the associated values instead of toggling the "gang" state.
* Add Grain can now be added as a layer operator.
* If you have set a Grade Result Colour Space, this is now used as the initial Render Colour Space in the Render View \[bug 25369]
*   Updated to RED SDK v4.5. This addresses some issues in earlier SDK releases, and adds:

    *   Support for the RED Rocket-X accelerator board (note that RED ONE

        clips are not supported on RED Rocket-X) - please note this has

        not yet been tested by FilmLight; if you have a Rocket-X please

        contact baselight-support@filmlight.ltd.uk to report any issues
    *   Support for the RED 6K Dragon sensor (not supported on RED Rocket;

        note that DRX has no effect for Dragon)
    * Support for the RED Motion Mount

    Users of RED Rocket cards installed in Baselight Kompressor systems will need to:

    1. update the Rocket driver using the installer package REDrocket\_Driver\_OSX\_v1.4.36.0.pkg that can be found in the /Applications/Baselight/Current/Utilities/Resources/etc folder.
    2. update the RED Rocket card's firmware using the rocketup\_1.1.17.3 utility included with Baselight.

    Ensure the Kompressor is shut down and restarted after updating the firmware.
* Added display of Capture Rate and Playback Rate metadata for Canon RMF files \[bug 25528]

## Bug Fixes Since Baselight 4.4.6201

* Fixed crash when applying Baselight Grades which had been exported from a Baselight Edition in CPU rendering mode \[bug 25444]
* Fixed crash in Render View when switching to use QuickTime Movie rendering via a Baselight Kompressor \[bug 25446]
* Fixed Northlight Alpha issues on multinode systems, and Baselight TWO systems with dual network interfaces \[bug 25438]
* The colour space of OpenEXR files is now automatically set to Rec.709 Linear \[bug 25427]
* Fixed crash due to overlapping strips caused by switching eyes during a second conform \[bug 25448]
* Renamed the "Gallery" keypad mode to "Recall" on the Blackboard 2 \[bug 25304]
* Fixed crash when switching to the matte selector after deleting a matte operator \[bug 25275]
* Fixed crash after closing scene and pressing 3D button \[bug 25181]
* Fixed Layer view and layer selector showing only matte channels \[bug 25330]
* Added support for Telecine Grade on MC Color and Tangent desks \[bug 25177]
* Blackboard 2 and Slate keypad now display correct Scratchpad slot number when "Next Page" is active \[bug 25243]
* Improved Tangent Element support for Film Grade and Curve Grade \[bugs 22536, 22719]
* Fixed problem where Blackboard 2 desks could lose their brightness setting \[bug 24514]
* Fixed crash applying a deliverable preset with Output Format: Use Input Format \[bug 25473]
* Fixed problem with the display mode when switching between a stereo and mono scene. This was also causing the cursor not to move in the mono scene on playback \[bug 24916]
* Fixed bug where tracks were not being added to a tracker strip when a tracked shape/transform strip was stereo split \[bug 23640]
* Fixed bug on a Blackboard One which could cause the blend encoder to be enabled even when the Inside/Outside key was not held down \[bug 25499]
* Fixed suprious 3ware diagnostic failure on Baselight ONE Deskside systems \[bug 25492]
* Fixed Prepare for Review \[bug 25519]
* Fixed problem where combine stereo stacks was going into an infinite loop \[bug 25550]
* Added warning dialog when attempting to reset a Chalk layout \[bug 25526]
