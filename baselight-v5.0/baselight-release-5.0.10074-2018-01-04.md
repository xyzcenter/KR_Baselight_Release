# 베이스라이트 릴리즈 노트 5.0.10074 (2018-01-04)



## New Features Since Baselight 5.0.10007

* Added support for NVIDIA Quadro M620 UI GPU \[bug 45506]
* Updated to RED SDK v7.0.5. This includes:
  * Option to use new IPP2 colour science
  * New tone curves (Hybrid Log Gamma, Gamma 2.2 & 2.6, REDlog Film)
  * New primaries (DCI P3, DCI P3 D64, ProPhoto RGB)
  * Support for Helium 8K S35 Monochrome sensor
  * Support for Weapon Monstro 8K VV sensor \[bug 45542]
* Files can now be renamed in FLUX Manage \[bug 46214]

## Bug Fixes Since Baselight 5.0.10007

* Fixed bug with Audio Sync when syncing by Timecode \[bug 44937]
* Fixed crash in format auto-update when job/global format has been deleted \[bug 45881]
* Fixed an issue preventing PhotoRAW from working on multi-GPU systems \[bug 45401]
* Fixed issues when dragging a scene from Job Manager to a Copy Destination on FLUX Manage View \[bug 44992]
* Muxed stereo renders (anaglyphic, interlaced, side by side and over/under) now render burnins into each eye separately \[bug 18446]
* Audio files can now be inserted onto the timeline from FLUX Manage \[bug 45834]
* Fixed licence issue with Baselight TRANSFER \[bug 46097]
* Fixed issue which prevented using NVIDIA Driver 375.66 with GTX 980, Quadro NVS 810, Quadro K6000, M4000, M5000 and M6000 GPUs \[bug 46135]
* Fixed range and default value of Dolby Vision Tone Detail Weight control \[bug 46204]
* Fixed bug with Audio Sync settings not being saved when the scene is closed \[bug 46178]
* Fixed bug with Audio Sync failing to correctly sync audio when the Audio TC frame rate does not match the scene's working frame rate \[bug 46208]
* Fixed handling of media with 48 and 48@24 fps timecodes \[bug 46231]
* Fixed incorrect Shot Timecode for media whose timecode has a doubled frame rate (60@30, 48@24 etc) and its first frame is the second of a timecode pair \[bug 46231]
* Fixed Log section of Queue Monitor not updating correctly when selecting a new operation \[bug 45188]
