# Baselight Release 4.4m1.8085 (2016-02-26)



Baselight Release 4.4m1.8085 (2016-02-26)

## New Features Since Baselight 4.4m1.7936

*   Added support for NVIDIA driver 352.63 on systems with GTX 580, GTX 680, GTX 780 and GTX 980.

    This driver is compatible with systems systems AJA Kona 4 or direct GPU display.

    This driver is NOT compatible with systems using FilmLight DVI2SDI or Framestore SDI display hardware \[bug 33008]
*   Added support for NVIDIA driver 340.96 on systems with GTX 680 and GTX 780 GPUs and DVI2SDI or Framestore SDI display hardware \[bug 35367]

    Note: When you install and run this version of Baselight, fl-diag may prompt you to upgrade your Nvidia driver. If this is the case, you must update your driver as the latest Baselight release contains software that has specific driver dependancies.

    Important: If you decide to roll back to a previous version of Baselight after you have upgraded your Nvidia driver, you will need to roll back the Nvidia driver as well. Contact Baselight Support to provide you with a custom driver installer for this purpose.

    To upgrade, see the support section of our website for the correct installer. This contains multiple versions of the driver that cover all supported Baselight hardware configurations, and will detect and install the correct version for your system.

## Bug Fixes Since Baselight 4.4m1.7936

* Improved cursor lag on image display when using AJA SDI output hardware \[bug 34357]
* In BLG Export and when updating AAFs for Avid, Sharpen operators created in 4.4m1 can now be converted into a form which can be read by Baselight 4.4 (plugins and full Baselight). The only caveat is that the "Anamorphic" setting is not supported in 4.4 and so if it is used in a 4.4m1 stack, that stack will not be exported \[bug 35203]
* Fixed issues with Dolby Vision Mastering Display \[bug 35268]
* Added aspect ratio information to Dolby EDR Metadata \[bug 32794]
* Fixed an issue that could cause decode failures, frame offsets and incorrect frame ordering in MXF files with start-position offsets. This issue affected XDCAM encoded MXF-files in particular \[bug 33591]
* Fixed a problem with Optical Flow retime, where Baselight FOUR and EIGHT systems would render incorrectly \[bug 35324]
* Fixed decode of ARRIRAW Open Gate (3414x2198 or 3424x2202) media using ARRI decode mode \[bug 34605]
* Fix new files being reported as zero size over /pfs (flood) interface when they were written using flux \[bug 28121]
* Don't attempt to stop Adaptec raid verification at Baselight startup because it may cause a kernel panic \[bug 35345]
* Fixed bug with fl-service xorg service running on IO node of cluster systems \[bug 35409]
* Fixed hang rendering R3D material \[bug 35426]
* Fixed render hang on BL4/BL8 \[bug 35453]
* Fixed playback errors at startup on clusters \[bug 35480]
