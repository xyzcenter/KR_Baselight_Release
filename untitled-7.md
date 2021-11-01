# 베이스라이트 릴리즈 노트 5.2.11383 (2019-01-30)



## Bug Fixes Since Baselight 5.2.11313

* Fixed Dolby Vision Software CMU behaviour when using a Dolby Vision Viewing/Rendering Colour Space with a maximum brightness higher than any Dolby Vision Trim set for the shot (e.g. rendering a 1000-nit deliverable when there is only a 100-nit trim) \[bug 50035]
* Fixed failure to recognise movie and/or audio files when browsing a large directory in FLUX Manage \[bug 50039]
* Fixed problem where opening the Media Import Rules View after opening a scene would remove any rules from the scene \[bug 50087]
* Fixed crash in EXR writing, encountered for example when grabbing certain resolutions of EXR files to a gallery \[bug 50085]
* Fixed crash when using Input Format in a Media Import Rules filter \[bug 50088]
* Fixed problem where importing an EDL caused Media Import Rules to be applied to all shots in the scene \[bug 50108]
* Fixed an issue where HD resolution DNxHR 444 written to Quicktime would display black or green frames when viewed in Avid or on MacOS \[bug 49771]
* Fixed issue with scratchpad not storing keyframes \[bug 50184]
* Fixed issue which would prevent undo/redo/scene close etc. from working after deselecting a panorama operator \[bug 50124]
* Fixed crash rendering scenes with denoise and burnins \[bug 50192]
* Fixed crash on startup on macOS when using SDI output hardware \[bug 50144]
* Fixed crash on macOS when disconnecting a removable drive \[bug 49708]
* Fixed a failure to import jobs with a very large number of tags \[bug 50157]
* Fixed crash clicking on a colour well in the Preferences window when no scene is open \[bug 50263]
