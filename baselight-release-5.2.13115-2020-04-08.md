# 베이스라이트 릴리즈 노트 5.2.13115 (2020-04-08)

## 버그 개선 ( Baselight 5.2.13060 이후 )

* Updated the flos-tools package to 6.4.13039. New features include:
  * Support for the 'rendernode' flag in cloud.cfg
  *   Support for Adaptec 3154-24i & 3154-8i16e controllers in BLX

      configuration
  *   A new '-check-connectivity' option to fl-verify-network that

      tests MTU settings to other hosts in the cloud \[bug 54506]
* Fixed corrupted NodeJS flapi module \[bug 54560]
* Fixed crash on startup when attached to a Blackboard ONE \[bug 54563]
* Fixed crash when stopping playback on macOS \[54558]
* Improved compatiblity of fl-service startup on systemd-based systems \[bug 54415]
* Improved compatibility of the nodemon service on non-FilmLightOS systems \[bug 54413]
* Fixed spurious error with xorg service when Plymouth is not installed \[bug 54361]
* Improved compatibility of the Automounter diagnostic \[bug 54349]
* The CPU diagnostic no longer runs on non-flos machines \[bug 54246]
* The filesystem mounts diagnostic no longer runs on non-flos machines \[bug 54208]
* Fixed an issue that could prevent AAC audio in QuickTime movies from being decoded \[bug 54177]
* Fixed issue with CDL grade not working with the Tangent panels \[bug 54587]
* Fixed problem with selecting non-default audio output device in Setups editor (related to using HP Remote Graphics) \[bug 54592]
* Fixed issue which caused the Render View control to choose the queue into which renders are submitted not to appear on macOS \[bug 54588]
* Fixed problem with FilmLight xorg service preventing use of local keyboard or mouse on RENDER nodes \[bug 54313]
