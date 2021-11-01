# 베이스라이트 릴리즈 노트 5.2.11675 (2019-04-09)

## 최신 기능 Baselight 5.2.11644 이후&#x20;

* Added support for reading Apple ProRes RAW camera media \[bug 47832]
* Added support for reading Blackmagic RAW camera media. Note that this functionality is not available on Linux systems using older NVIDIA drivers (versions 290, 304 or 319) \[bug 49057]

## 버그 개선 Baselight 5.2.11644 이후&#x20;

* Fixed issues with Truelight selection in Truelight strip \[bug 50195]
* Fixed colour space conversion applied to OFX input images used in the UI \[bug 50847]
* Fixed a potential crash when pressing the filter button on a media row in EDL Import View \[bug 51067]
* Fixed issue that caused Consolidate not to trim the head of movies \[bug 51063]
* Fixed behaviour of the Sequence Input Colour Space menu during playback, and when Grouped Grading is enabled while Shots View is open \[bug 50788]
* Fixed "Scene Timecode" not appearing among the conform settings in the EDL Import View \[bug 51102]
