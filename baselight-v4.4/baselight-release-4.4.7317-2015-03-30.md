# Baselight Release 4.4.7317 (2015-03-30)



## Bug Fixes Since Baselight 4.4.7274

* Fixed failures when working with very long R3D clips using many run-on .R3D files \[bug 12724]
* Fixed bug which could cause view layouts to be recalled from the Slate's numeric keypad when 'View' mode wasn't selected \[bug 31349]
* Fixed bug which could cause tracked & keyframed shapes to move when their stack was split \[bug 31468]
* Fixed a bug which caused bl-browse to show directories as symbolic links when real symbolic links exist in the directory being browsed \[bug 31576]
* Fixed crash which could sometimes occur during tracking, especially at large resolutions \[bug 30618]
* Fixed display of images on a Gen V BL4/8 without a combiner when using 16 bit caching \[bug 31573]
* Fixed a bug that caused custom bitrates for DCP and DCI MXF codecs to be interpreted as bits per second rather than megabits per second \[bug 31606]
* Changing the Sequence Browser "List" option now updates the text on all items in the browser \[bug 31628]
* Fixed "sched\_setaffinity" warnings on console when running on a system with only 2 CPU cores \[bug 31566]
* Fixed bug introduced into fl-diag dpm SMART tests that showed as an incorrectly formated smartctl command line \[bug 31601]
* Fixed problems with LUT generation where errors were not correctly reported \[bug 31653]
* Fixed "Add Image" browser when editing a burnin \[bug 31669]
* Fixed hang on exit in the SDI display code \[bug 31471]
* Removed invalid "UltraHD 48p" setup \[bug 31678]
* Fixed incorrect default SDI resolution for "HD 24p (Dual)" setup \[bug 31688]
* Fixed diagnostic test for NVIDIA driver version on systems with FilmLight DVI2SDI or Framestore hardware \[bug 31776]
* Changed the default SDI output signal format to "Progressive" for the following built-in setups: "HD 23.98p (444)", "HD 24p (444)", "HD 25p (444)", "HD 29.97p (444)", "HD 30p (444)" \[bug 31770]
* Fixed HDMI output for high frame rate modes (48p, 50p, 59.94p, 60p) \[bug 31780]
* Fixed progress output from command-line bl-render \[bug 31786]
* Fix conform bug in subdirectory matching when using the pattern "%\*" to match any directory \[bug 31464]
* Fixed hang on startup when using 48p modes with the AJA Kona 4 SDI output \[bug 31818]
* Fixed AJA Kona 4 settings for PAL and NTSC setups \[bug 31786]
* Fixed compatibility issues reading and writing Avid DNxHR MXF files \[bug 31827]
