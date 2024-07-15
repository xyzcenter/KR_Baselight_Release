# Baselight Release 5.3.17366 (2022-11-21)



## New Features Since Baselight 5.3.17219

* macOS 13 Ventura is now supported on Apple Silicon hardware, please see Known Issues \[bug 62018]
*   Added "Increment" option for custom Integer metadata columns.

    This allows values in an Integer column to auto-increment per frame across a sequence. These values can be used in burn-ins and in filename expressions for renders.

    To enable the Increment option, right-click on a custom Integer column heading in Shots View and select the "Set Increment" option. Setting the value to 1 will increment the value by 1 for each frame in the sequence \[bug 62327]

## Bug Fixes Since Baselight 5.3.17219

* Improved shot selection behaviour using keyboard shortcuts. Notably, Ctrl+Shift+Enter will now always toggle selecting all shots regardless of the DBS lock state and Ctrl+Alt+Enter can now be used to toggle selection between the DBS and current cursor position \[bug 61931]
* Fixed issue causing some ALEXA 35 MXF files to be unsupported \[bug 61996]
* Fixed hang when retrieving long project lists from Frame.io. Please update to version 1.0.26 of the filmlight-frameio package from Scripts View \[bug 61989]
* Fixed issue with images on SDI output being displayed out-of-order on some NVIDIA GPUs when decoding ARRIRAW source material \[bug 62044]
* Fixed image corruption on Linux, for example when using retime with ARRIRAW media \[bug 61850]
* Fixed issue with GPU offload process usage when running command line render utility bl-render \[bug 61955]
* Fixed an issue in indexed XFS volumes that could prevent new directories from being added to the index \[bug 61929]
* Fixed issues decoding Canon RAW on systems with no SDI output and multiple GPUs \[bug 62238]
* Fixed potential crash when dragging and dropping grades onto the Cuts View \[bug 52838]

***
