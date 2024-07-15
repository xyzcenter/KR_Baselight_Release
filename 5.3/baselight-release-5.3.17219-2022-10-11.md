# Baselight Release 5.3.17219 (2022-10-11)



## New Features Since Baselight 5.3.17175

* Rendered WAV files now contain channel labels, project, scene, take and roll metadata copied from the audio source files. This behaviour can be disabled using Codec Params in Render View \[bug 61564]
* Restored the behaviour of the Tangent Bt panel so the B button changes between pages of controls \[bug 61893]

## Bug Fixes Since Baselight 5.3.17175

* Fixed hang caused by invalid UTF8 strings \[bug 61545]
* Fixed gestural switching from the image display to the UI display \[bug 61851]
* Fixed issue where trackers couldn't be assigned in stereo scenes \[bug 61728]
* Fixed hang when rendering sequences to a remote machine across dual 10G network interfaces \[bug 61903]
* Fixed crash when rendering from Sony RAW and X-OCN codecs using the CPU renderer \[bug 61918]
* The Codec Parameters dialog in Render View has been renamed to Metadata Settings for Audio Only deliverables \[bug 61899]
* Removed Python 3.10 from the macOS Software installer whilst we address conflicts with existing Python interpreters \[bug 61924]
* Fixed hangs during playback or rendering when using many source movies with embedded LUTs \[bug 61753]

***
