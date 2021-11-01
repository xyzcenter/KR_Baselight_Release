# 베이스라이트 릴리즈 노트 5.2.14009 (2020-12-01)



Baselight Release 5.2.14009 (2020-12-01)

## New Features Since Baselight 5.2.13892

*   Added support for using the UI GPU in conjunction with the render GPU on Baselight ONE systems when the current Setup is configured to use 'No external output - Display in UI' for the Primary Video Output.

    The image display in the UI can now be rendered using the render GPU, instead of the UI GPU. This can be beneficial for situations where a Baselight ONE system is being used remotely via remote desktop software.

    To enable this functionality you must run bl-config-xorg from this updated version of Baselight to update your GPU configuration and restart your system \[bug 52890]
* On Linux, applications have new icons and are compatible with GNOME 3 desktops. Note that you may have to log out and back in to activate them the first time. The fl-setup-desktop command can be used to add icons to the desktop, but keep in mind that under GNOME 3 desktop icons are only displayed using "Classic" desktop mode \[bug 54735]
* On Linux, there is now an application icon for launching the Queue Monitor \[bug 55066]

### Blackboard Classic for macOS

*   Blackboard Classic is now supported on macOS.

    On installation the Blackboard Classic device name needs to be selected in the Preferences (under "System:External Devices:Input devices - Blackboard Classic Device"). Once the device has been selected and the Wacom is used, the Blackboard Classic will ask permission to access the macOS Accessibility. fl-bbclassic.app should already have been added to the "Security and Privacy:Privacy:Accessibility" options in the System Preferences and sometimes needs to be ticked before the Wacom will work. After set-up the Wacom should function all the time.

    To use the Blackboard Classic inside Baselight, the Blackboard Classic option needs to be selected in "System:External Devices:Input Devices" in the preferences.

    All other functionality should match the FLOS version of Blackboard Classic \[bug 55439]

## Bug Fixes Since Baselight 5.2.13892

* Fixed issue where trackers couldn't be unlinked just after deleting the tracker strip \[bug 55842]
* Fixed failures when a large consolidate operation includes both image sequences and movies being trimmed \[bug 54643]
* fl-fsr no longer attempts to defragment archive files (gz, tar, zip) stored on image volume \[bug 56143]
* Fixed "Unexpected compression ID" error when reading DNx QuickTime movies that have missing compression metadata \[bug 56089]
* Fixed issue causing some retimed shots in FCPXML conform to have an incorrect length \[bug 55104]
* Added support for FCPXML version 1.9 \[bug 55929]
* Fixed parsing of keyframed transforms in FCPXML \[bug 56021]
* Fixed inefficient use of GPU memory on macOS systems with GPUs with more than 8GB VRAM \[bug 37855]
* Fixed failure to read badly-formed OpenEXR files which have duplicated channel names \[bug 56299]
* Fixed issue where updating the Poster Frame on a shot would not update Layer View thumbnails correctly \[bug 56208]
* Fixed flapi service crash on startup on macOS \[bug 55941]
* Fixed deliverable preset apply not setting field ordering when the frame rate of the preset matched the frame rate of the scene from which it was defined \[bug 55775]
* Fixed issue where exporting Blackmagic LUTs would show invalid resolution options, leading to a hang \[bug 55685]
* fl-setup-desktop now correctly creates application icons on Baselight TWO/X UI hosts \[bug 56439]
