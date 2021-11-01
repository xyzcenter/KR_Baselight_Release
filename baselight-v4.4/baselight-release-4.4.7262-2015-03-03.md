# Baselight Release 4.4.7262 (2015-03-03)



## New Features Since Baselight 4.4.7218

* Added -u option to "fl-queuetool list" to make the queue list update continuously \[bug 31036]
*   Added option to set "Input Video LUT" in the "Update Avid AAF with Baselight Grades" EDL Export panel. This option allows you to specify a Legal-to-Full scale to be applied in Baselight for Avid, to counteract Avid's application of a Full-to-Legal scale to some RGB444 formats linked via AMA.

    To see the effect in Avid, you will need to install a recent version of the Baselight for Avid 4.4 beta (post 4.4.7217).
* The Input layer of Baselight for Avid effects written by the EDL Export View's "Update Avid AAF with Baselight Grades" option now contain the name of the shot from the Baselight timeline.
* Added support for reading embedded 2-bit dirt matte in 10-bit DPX images from Scanity \[bug 22879]
* Added 50MB UHD sized file pass to flioinfo which is used by the fl-diag disk\_performance test \[bug 30984]

## Bug Fixes Since Baselight 4.4.7218

* Fixed errors that arise when "Default container directory (high res)" is made empty in Setups editor \[bug 31051]
* Fixed incorrect Reference Timecode frame rate when inserting material with discontinuous timecode, or with an ambiguous timecode frame rate \[bug 31039]
* Fixed behaviour of "fl-queuetool tasks" when tasks lists is non-contiguous \[bug 31121]
* Fixed incorrect behaviour when using Ctrl + Right Trackball Ring as Jog Wheel control on Slate desks \[bug 30182]
* Improved the performance of sequence browsing and conform on slower filesystems such as SANs and external drives \[bug 30972]
* Fixed errors loading the DNxHD library on some systems \[bug 31179]
* Fixed instability when using RED decoding on GPU or RED Rocket, particularly on Baselight FOUR/EIGHT systems \[bug 31137]
* Fixed crash which could occur on grabbing a new scratchpad entry after having closed another scene \[bug 31064]
* Fixed Film Grade Balance Exposure behaviour when exposure is keyframed \[bug 31294]
* Fixed a bug in the file/sequence browser that could cause directories to be given the wrong permissions or modes, and special files such as a FIFO might cause the browser to hang \[bug 31303]
* Fixed support for 1920x1080 and 2048x1080 video modes at 47.95, 48.00, 50.00, 59.94 and 60.00 Hz when using 1.5G-SDI and 3G-SDI Level B signalling on the AJA Kona 4 \[bug 31333]
* Fixed 4K HDMI routing on the AJA Kona 4 \[bug 31344]
* Fixed incorrect pixels on the left side of ProRes images when the image width is not a multiple of 16 pixels \[bug 31309]
* Improved error message when attempting to use HDRx blending with GPU decoding; this is not supported by the RED SDK \[bug 31340]
* Fixed start timecode written to QuickTime movies when timecode frame rate is 50@25 or 48@24 \[bug 31378]
* DNxHR QuickTime movies tagged as "AVdh" are now correctly recognised by Baselight; DNxHR QuickTime movies written by Baselight are now correctly tagged as "AVdh" \[bug 31423]
* Ensured that tcpmux-server has no connection limit \[bug 29311]
* Fixed DNxHD failures on Baselight Kompressor \[bug 31290]
