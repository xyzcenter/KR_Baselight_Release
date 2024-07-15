# Baselight Release 6.0.20256 (2024-04-25)

##

### New Features Since Baselight 6.0.19915

#### Shape Control Point Transforms

*   It's now possible to transform (scale, rotate and translate) explicitly selected shape control points. To do this, first sweep select multiple (shape) control points. Holding down the `Win` modifier (or `Ctrl` on a Mac) will then popup a yellow transform box which can be used to transform those control points.

    Additionally, holding down `Ctrl` (`Cmd` on a Mac) and dragging the box centre can be used to adjust the centre of rotation/scale.

    On a Blackboard 1/Classic the `Ctrl Lock` key can be used to popup the yellow transform box. On any FilmLight desk, while the yellow transform box is visible/active the following trackball mappings apply:

    * Middle Trackball : Translate the selected control points.
    * Middle Trackball Ring : Rotate the selected control points.
    * Right Trackball : Translate the pivot/centre of rotation.
    * Right Trackball Ring : Scale the selected control points. Bug 67681

#### DRT Black Offset Compensation

*   Some DRTs map a negative linear light value to 0.0 in display-referred values. When a DRT defines this offset in its `BlackOffset` parameter, a new "Compensate For DRT Black Offset" control is shown below the DRT selection in Scene Settings View. When enabled, Baselight adds a compensatory flare before and after several modern grading operators. These operators are:

    * Base Grade (compensation was already present in Baselight 5)
    * Boost Detail
    * Boost Shadow
    * Chromogen
    * Colour Crosstalk in "Calculate In Linear" mode
    * Compress Gamut
    * Curve Grade
    * Hue Angle
    * Look (with looks using formulae or triangles)
    * X Grade

    This change should improve the colour grading behaviour of all of these operators when used in combination with such DRTs. Bug 67883

#### Miscellaneous

* Added support for the NVIDIA 550.76 driver. Bug 68044
* Added support for new FilmLight CONNECT traffic routing scheme. Bug 68056
* QuickTime metadata with reverse-DNS naming (e.g. `com.apple.quicktime.model`) is now copied from QuickTime source media to QuickTime rendered output media. Bug 68112

### Bug Fixes Since Baselight 6.0.19915

* Fixed rendering of web admin UI. Bug 67006
* The hotfix service no longer unmounts NFS volumes. Bug 66517
* Fixed issues on Intel macOS systems with empty or incorrect scopes, and related issues in Display View. Bug 65932
* Fixed error message when creating a new FilmLight CONNECT session via the Client Sessions view. Bug 66626
