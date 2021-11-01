# 베이스라이트 릴리즈 노트 5.2.11913 (2019-06-13)

## 최신 기능 Baselight 5.2.11854이후&#x20;

*   Added option to the Metadata section on Render View to allow control

    over the frame rate metadata stored in DPX, OpenEXR and JPEG 2000

    files \[bug 51164]

## 버그 개선 Baselight 5.2.11854이후&#x20;

* Fixed loading of control surface button layouts \[bug 51338]
* Fixed issue that caused some per-frame metadata from movie files to be ignored \[bug 51506]
* Improved behaviour when attempting to start Baselight on a system using the 418.56 nvidia driver when there is insufficient free GPU memory \[bug 51396]
* Fixed crash when using ARRIRAW media with other RAW media on a system with limited GPU memory \[bug 51556]
* Fixed database warning from 'index' service on the first install of Baselight \[bug 51651]
* Fixed crash when working with dissolves in stereo scenes \[bug 51655]
* Fixed crash in Multi-Paste \[bug 51578]
