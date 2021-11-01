# 베이스라이트 릴리즈 노트 5.3.14986 (2021-07-01)

## 중요 알림

Baselight 5.3 no longer supports the following legacy hardware and OS plaforms:

* Baselight FOUR and Baselight EIGHT systems
* DVI-to-SDI Convertors or Combiners performing that function
* RME Hammerfall audio cards
*   Tape deck control within Baselight (the standalone VTRE application

    remains available)
* Spirit telecine control
* NVIDIA Quadro NVS 450 GPU (as a User Interface display card)
* macOS 10.13 and earlier

Generation V systems using DVI-to-SDI Convertors or Combiners need to either be upgraded to the Baselight Ultra High Definition option (see data sheet) which includes an AJA Kona 4 PCIe card or revert to GPU DVI output. Earlier generation systems are now constrained to a GPU DVI output only.

Please contact Baselight support to discuss upgrading from a NVS 450 if required.

FLOS 8 or later is required to use GPU JPEG 2000 acceleration with Nvidia Ampere GPUs

## 최신 기능 Baselight 5.3.14861 이후&#x20;

### 기타 기능&#x20;

*   On a Linux system with a GPU that has sufficient VRAM, and an Nvidia

    driver version 418 or newer, RED media decompression is now

    accelerated using Cuda. This is indicated on the menu bar with a

    blue (rather than green) "G" icon \[bug 57573]

## 버그 개선 (Baselight 5.3.14861 이후)

* Fixed install script platform detection of CentOS 8 \[bug 58014]
* Fixed fl-service platform detection of some RHEL 8 variants \[bug 58027]
* Fixed crashes on macOS when OFX plugins crash when Baselight tries to load them \[bug 54568]
* Fixed image corruption when using some 10-bit QuickTime or MP4 media which was recorded with the camera rotated \[bug 55127]
*   레드 SDK 버전 8이후 리눅스에서 가끔식 잘못 디코딩되는 문제 수정, 본 수정패치는 엔비디아 418드라이버 이후 버전이 필요함. 예전 드라이버 버전의 경우 레드 카메라 미디어는 CPU에서 가능함. 느려질 수 있음. \
    Fixed occasional incorrect decode of RED media on Linux since the update to RED SDK version 8.

    PLEASE NOTE: The fix for this issue requires an Nvidia driver version 418 or newer; systems with an older driver will decode all RED media using the CPU, which will be very slow. Please contact baselight-support@filmlight.ltd.uk if you are affected by this \[bug 57993]
* Fixed an issue with RAID formatting when no NVMe devices are present \[bug 58112]

## Known Issues

* When running Baselight CONFORM or Daylight on macOS 10.15 Catalina, local volumes which are defined in volume.cfg within /Volumes can result in "Stale NFS file handle" errors. This is due to a bug in macOS. To work around this issue:
  * open System Preferences from the Dock or the Apple menu
  * choose "Security & Privacy"
  *   click the padlock icon and use your password or Touch ID to allow

      changes to be made
  * select "Full Disk Access" in the list on the left
  * click the "+" button on the right to open a file browser
  * on your keyboard, press "/" to open the "Go to the folder" dialog
  * enter "/sbin" and click "Go"
  *   select the file called "nfsd" and click "Open"

      After restarting your Mac, the volume(s) should now work correctly

      \[bug 53073]
* Saturated areas in Photo RAW files can acquire a colour tint when adjusting the exposure slider in the Photo RAW Parameters operator while blending highlights \[bug 44769]
* Baselight 5 enables GPU acceleration in OFX plugins. This improves performance but may introduce new issues depending on the 3rd-party plugin implementation \[bug 47224]
* Canon RAW media added to scenes in Baselight 5.1.10836 or earlier using the tone curve setting "Canon Log" may now fail to decode with an error message stating "Invalid function parameter". Changing the tone curve will allow images to decode, but will change their look \[bug 50371]
