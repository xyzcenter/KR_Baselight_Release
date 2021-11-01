# Baselight Release 4.3.5769 (2012-12-20)



## New Features Since Baselight 4.3.5720

*   Added support for Tangent Element and Tangent Wave desks.

    Element Bt

    * Has two 12 button layouts \[General] and \[DBS] toggled with&#x20;
    *   \[General] contains Copy/Paste, Undo/Redo, Keyframe and Mark

        manipulation controls
    *   \[DBS] provides buttons for selecting and applying looks from the Gallery and Cutview

        Element Tk
    *   3 trackballs & rings with reset buttons map to colour wheel and master values in active strip

        Element Kb
    *   12 push button encoders map to values in active strip

        Element Mf
    * Transport controls
      * Hold  button and tap  and  for frame skip
    * Ring of trackball acts as shuttle control
    *   Keypad can be latched to select Scratchpad slots, Cursors and Timecode values

        Wave
    * Transport & Shuttle Controls
    * 9 push button encoders map to values in active strip
    * 3 trackballs and master dials map to 2D values in active strip
    * Up/Down buttons move position of render row
    * Function buttons:
      * F1 Undo
      * F2 Redo
      * F3 UI/Image Screen Toggle
      * F4 Copy
      * F5 Paste
      * F6 Move Keyframes
      * F7 Previous Keyframe
      * F8 Next Keyframe
      * F9 Set/Unset KeyFrame
*   Added selection of higher layers through double, triple, quadruple, etc. taps of desk Layer buttons.

    The number of layers skipped depends on the number of buttons active in the layout. E.g.

    Blackboard 1 desks (6 Layer buttons)

    * Double tap Layer 6 to get Layer 12
    * Triple tap Layer 6 to get Layer 18

    Blackboard 2 desks (standard Chalk layout - 10 Layer buttons)

    * Double tap Layer 6 to get Layer 16
    * Triple tap Layer 6 to get Layer 26

    Note: This feature is disabled by default. Enable and alter sensitivity of the tap behaviour with Blackboard Setup -> Layer Selection \[bug 21421]
*   Blackboard 2 Display View buttons (1x1, 2x1, etc.) now show the current mode they are in e.g. "2x2 Butterfly". The various modes are iterated through by using  + ,  + , etc.

    The  button is now also used to swap between the various stereo modes (line interlace, checkerbox, etc.) when in a stereo scene. Stereo modes are unavailable in non-stereo scenes \[bug 18824]
* Blackboard 1 & 2 - Extended "Shots" button to toggle between various Play Range modes and the full scene.
  * No Modifier      - Current Shot
  * &#x20;         \- Between Marks
  * &#x20;          \- Selected Shots
  * &#x20;\+  - Review Range \[Bugs 19680 & 22184]
* Added support for rendering to MPEG-2 XDCAM HD 4:2:2 50Mbps using the "Sony MXF" filetype.
* Render View now has a button to copy the "First File" path to the clipboard.
* Added "Set Keyframe Toggle" action to Chalk \[bug 22387]
* Added support for reading 4-channel ADX files (please note that the fourth channel is ignored) \[bug 22431]
* Improved Mac OS 10.7 Kompressor performance when rendering to Baselight volume \[bug 21751]
* Improved performance of Curve Grade & Video Grade when using custom curves \[bug 22327]
* Cursor View now allows the current cursor's viewing format, resolution, mask, guide and Truelight profile to be set as the initial settings for the current scene and/or job \[bug 17382]
*   Added "Review Range" to Blackboard desks. Activate by pressing

    &#x20;\+  + . Also available as an action in Chalk \[bug 19680]
* Improved debugging of image server processes. If the file "/usr/fl/etc/is\_log" exists on a machine then details of the last 2500 image server requests will be logged. If an image server process crashes this information will be sent back to FilmLight with the crash report \[bug 22140]

## Bug Fixes Since Baselight 4.3.5720

* bl-delete now works with scenes in folders \[bug 22207]
* The rendering spinner on the Baselight menu bar no longer continues spinning after an aborted flip to the other eye \[bug 22430]
* Image Transform Settings are now applied under an explicity-cached strip (from the Scene Settings or from an Image Transform Settings strip placed beneath the cached strip), to control the transform from the Working Format to the Viewing Format. Note that Image Transform Settings set above an explicitly-cached strip have no effect when the Input Format matches the resolution of the Working Format \[bug 22433]
* Controls under the mouse now correctly react when they are moved, typically by the scroll wheel \[bug 22105]
* Fix for crash when adding a custom button in Chalk after moving a workspace view while holding Windows key \[bug 22403]
* Fixed bug which could cause a crash when switching between shape strips during playback \[bug 16592]
* Fixed scene corruption bug when applying from gallery with blur in input strip \[bug 22470]
* Fixed bug where it was possible to export Chalk layouts to non- existent USB sticks \[bug 22254]
* "Switch Eyes" button on Blackboard 2 keypad when in Cursor mode is now disabled when in a non-stereo scene \[bug 21890]
* Improved formatting of numbers on Blackboard 2 encoder readouts \[bug 22434]
* Fixed some buttons being incorrectly labeled on Blackboard 2 ONE desks \[bug 22479]
* Fixed bug where pressing and holding the directional keys on Blackboard desks didn't scroll the DBS \[bug 22488]
* Fixed bug on Blackboard 2 where  toggle can disappear when in latched mode \[bug 22535]
* Fixed colour of Phantom cine files from Miro cameras \[bug 22562]
* Fix for slow clockwise encoder movements on Blackboard 2 & ONE desks not being reported. Run "bl-update-bb2" or "bl-update-bb2one" to upgrade desk firmware to latest version \[bug 22564]
* Fix for  + \<Layer Up/Down> to change between stacks on Blackboard desks not working \[bug 22496]
* Fixed OFX plugin progress dialogs \[bug 22573]
* Fixed bug with .exr copy to PFS which created an invalid image if its height was not a multiple of the node count \[bug 22070]
* Fixed crash rendering complex scene to EXR files \[bug 20589]
* Fixed 100% CPU usage in image server processes \[bug 22375]
* Fixed 'xinetd flood reader is not responding' errors caused by a too-short timeout in the pfs2 diagnostic \[bug 21553]
* This release will disable NVIDIA PAT on Supermicro H8DAi-2/H8DA3-2 motherboards running Flos 2.1. PAT could trigger occasional node freezes with this combination of hardware & software \[bug 21644]
* Fixed failure to get licences from a licence server under heavy load; added additional debugging to report licence server errors \[bug 22555]
* Optimised MXF multi-track audio reading \[bug 22458]
* Prevented R3D thumbnails from being rendered using a RED Rocket, which will improve performance when playing and also addresses some thumbnail corruption issues \[bug 21514]
* Fixed hang when using fl-cp to copy folders containing sequences with '%' in their names \[bug 22617]
* Fixed hang when rendering some long scenes to movies \[bug 21951]
* Fixed OFX plugin path on Mac OS X \[bug 22556]
* Fixed conforming new Avid flip/flop effects \[bug 20362]
* Blackboard 2 Button Demo now works again \[bug 22574]
* Fixed behaviour of JL Cooper MCS3 and Spectrum panels \[bug 22471]
* Improved Blackboard 2 Jog Shuttle timeline navigation. Frame Step mode has no notch resistance by default and is more responsive at low speeds \[bug 22478]
