# 베이스라이트 릴리즈 노트 5.2.13060 (2020-03-23)

## 최신 기능 (Baselight 5.2.13010이후)

*   Added support for reading compressed DNG files from Kinefinity MAVO

    and other cameras \[bug 53487]

## 버그 개선 ( Baselight 5.2.13010이후)

* Fixed an issue on macOS so that a check is carried out to ensure that the currently running FilmLight services match the Application being run \[bug 53452]
* Fixed crash in CDL Grade when Tangent Element panels are connected \[bug 54460]
* Fixed additional issues with invalid Dolby Vision analysis on some flat-colour shots \[bug 53766]
*   Fixed behaviour of Sony RAW media when the Colour Temperature control had been adjusted. In order to maintain the appearance of such media in older scenes, all Sony RAW sequences added in earlier builds now render as closely as possible to how they did prior to Baselight 5.2.12770, and only newly-added sequences will use the new correct White Balance and Tint behaviour.

    PLEASE NOTE: If you have used Colour Temperature controls with Sony RAW media in Baselight 5.2.12770 or later, you will need to reinsert the media in order to restore the behaviour you had been seeing \[bug 54332]
* Changed the background image of the Blackboard Classic, to remove the lens flare \[bug 54241]
* Fixed issue with the Grid Warp, Text, Perspective and Tracker operators not displaying the correct buttons on a Blackboard Classic \[bug 54325]
* Fixed Shots View Expressions using "Name" not working after column was renamed to "Strip Name". Both options now work \[bug 53395]
* Fixed problem where the application would fail to start with an "Underlying Transport Error" message \[bug 53740]
* Fixed issue with Euphonix desk preventing grading operators from being inserted \[bug 54489]
* Fixed UI problems with Decode Parameters in Media Import Rules View \[bug 54481]
* Fixed issue where the application would prevent the display going to sleep on macOS \[bug 54515]
* Fixed AJA T-Tap support \[bug 54537]
