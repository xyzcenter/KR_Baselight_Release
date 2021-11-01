# 베이스라이트 릴리즈 노트 5.1.10917 (2018-09-03)



## New Features Since Baselight 5.1.10836

* Added option to Scene Settings and Setups to control the Stack Colour Space of newly-inserted Sequence operators \[bug 48555]
* Added options to export and import Global Formats from the formats editor \[bug 43895]
* Basic cursor synchronisation is now available to remote grading sessions. The cursor position and render layer are mirrored, as well as play state, play speed, loop mode and shot filtering settings. Nothing is required to enable this feature, it is automatic when a scene is opened in follow-mode \[bug 41583]
* Updated to Canon RAW SDK 2.2. This adds support for Canon C700 FF media \[bug 46472]

## Bug Fixes Since Baselight 5.1.10836

* Fixed Dolby Vision Software CMU not being applied when rendering more than 500 frames \[bug 48612]
* Fixed poor quality of ProRes 4:4:4 media when decoded at optimised half-resolution (note that existing Sequence operators in scenes will not change behaviour) \[bug 48581]
* Fixed unpredictable crash in FLUX Manage \[bug 48418]
* Fixed Shader operators losing optional inputs when split or pasted \[bug 48407]
* Fixed crash when using a bad BLG that refers to an unknown colour space \[bug 45693]
* Fixed crash when updating the tracker controls in shapes \[bug 48043]
* Prevent shapes from setting up the state of the 'selected track only' button during navigation to the tracker strip \[bug 48613]
* Fixed behaviour of Shader operators that distort or blur the image, when using a viewing format whose mapping uses an area smaller than the entire input image \[bug 48788]
* Fixed an issue where some XDCAM encoded MXF files written by Avid software were decoded with blocky artefacts \[bug 48796]
* Fixed crash within paint when switching to All Strokes tab after a reset \[bug 48558]
* Fixed crash when conforming for Tape Ingest \[bug 48594]
* Added a diagnostic preference to override the number of nvme cards expected \[bug 48527]
* Fixed errors in dissolves in Dolby Vision XML export when using Record Timecode numbering \[bug 48811]
* Fixed incorrect use of P3 D65 colour space in Dolby Vision XML when using a Rec.2020 Dolby Vision Mastering Display \[bug 48791]
* Fixed issue that caused keyboard and mouse input to be ignored during playback in some situations \[bug 48587]
