# 베이스라이트 릴리즈 노트 5.0.10254 (2018-02-22)



## New Features Since Baselight 5.0.10184

* Updated to ARRIRAW SDK v5.4. This adds support for the ALEXA LF camera \[bug 46621]
* Dolby Vision EDR export now has the option to use frame numbers derived from the Record (Timeline) Timecode \[bug 45916]
* Added support for NVIDIA Quadro P1000 UI GPU \[bug 46664]
* Added keyboard shortcut for "Combine/Separate Stereo Stacks" command
  * Ctrl-Shift-\` on Linux
  * Cmd-Shift-PlusMinus on macOS \[bug 24869]
*   Added support for conforming audio from ALE during EDL Import.

    Currently only full, container-relative paths to audio files are supported.

    The ALE must contain the following columns to conform the audio file:

    * "Audio Path" : a container-relative path to the audio file
    * "Audio Offset" : an offset in seconds within the audio file

    Audio metadata will also be carried over if the ALE contains the following columns:

    * "Audio TC" : audio timecode at the start of the shot
    * "Audio Fps" : audio timecode framerate
    * "Audio Roll" or "Soundroll"
    * "Audio Channels" : number of audio channels in audio file
    *   "Audio Track Names" : a comma-separated list of audio track

        names \[bug 46691]

## Bug Fixes Since Baselight 5.0.10184

* Dolby Vision EDR export now fails if there is not a Dolby Vision strip at every frame of the scene \[bug 46613]
* Dolby Vision EDR export now includes valid UniqueID data \[bug 46311]
* Fixed Shots View tab configuration not saving properly on scenes created from template \[bug 46587]
* Fixed crash when trying to paste a stack that had been deleted after it had been copied \[bug 44161]
* Fixed crash renaming custom columns \[bug 46596]
* Increased resolutions of R3D and ARRI media that can be decoded on macOS with a 3GB GPU \[bug 45226]
* Enabled left/right eye source timecode columns when exporting a stereo ALE with "Use Shot (Src) Timecode" option enabled \[bug 46665]
* Fixed incorrect negative Sequence frame numbers, notably at the first frame of the shot when the Offset is -1 \[bug 43357]
* Fixed bug which could result in the metadata for the wrong eye being written to stereo ALE columns \[bug 46689]
* Fixed missing Audio Timecode for Right eye in Single Stack Stereo scenes after using Audio Sync operation \[bug 46686]
* Fix floating-point number precision in Shots View (read-only columns), EDL export and Report export \[bug 46690]
* Fixed locking issues when clearing undo/redo history \[bug 46207]
* Fixed ambiguity in volume lists, for example when there are several systems each mounting the same SAN \[bug 46669]
* Fixed reading 60fps and 120fps ALEs \[bug 56770]
* Added 120p to the list of default frame rates in the New Scene dialog \[bug 46771]
* Fixed issue where applying a BLG to a sequence from FLUX Manage would reset the flip/flop parameter of the Sequence operator when the "Include Layer 0 Operations" copy/paste option was disabled \[bug 46809]
* Fixed the right eye filename sometimes being incorrectly used for the rendered filename (e.g. with %W) when rendering a stereo scene as anaglyphic or muxed \[bug 46810]
* Changed Gen VII BL2 current\_clocksource to tsc to reduce read\_hpet overhead on large system with many CPUs \[bug 46792]
* Fixed filename issue in adaptec\_fwflash script \[bug 46818]
* Fixed temperature / hours not appearing in 8TB drive dpm statistics \[bug 46814]
* Changed fl-setupssh to generate rsa keys (instead of dsa) to allow connection to MacOS 10.12 \[bug 40385]
* Stop prompting to save if you try and close a scene immediately after opening it \[bug 46838]
