# 😀 Baselight 릴리스 6.0.19915 (2024-03-27)

### New Features Since Baselight 6.0.19881

* Updated to R3D SDK 8.5.1. This fixes several bugs, and adds support for V-RAPTOR \[X] media. Note that Extended Highlights is beta functionality and is not yet available. Bug 67193

### Baselight 6.0.19881 이후 새로운 기능

**• R3D SDK 8.5.1 업데이트**

• 여러 버그가 수정되었고 V-RAPTOR \[X] 미디어 지원이 추가되었습니다. 단, Extended Highlights는 베타 기능으로 아직 사용할 수 없습니다. (버그 67193)

### Bug Fixes Since Baselight 6.0.19881

* Fixed memory leak in Timeline drawing, which could occur if a shot overlapped other shots' horizontal extents (a common example would be an offline located above the grading strips). Bug 67522
* Fixed extremely slow reading of some BLG files, in particular those using the "ACES RRT 1.1+" DRT. Bug 33064
* Fixed editing of mark note text via clicking on the note text bubble in the timeline. Bug 67684

### Baselight 6.0.19881 이후 버그 수정 사항

• 타임라인 그리기에서 샷이 다른 샷의 수평 범위와 겹칠 때 발생하던 메모리 누수를 수정했습니다. (예: 그레이딩 스트립 위에 있는 오프라인 샷). (버그 67522)

• 특히 “ACES RRT 1.1+” DRT를 사용하는 일부 BLG 파일의 읽기 속도가 매우 느린 문제를 수정했습니다. (버그 33064)

• 타임라인에서 노트 텍스트 버블을 클릭하여 마크 노트 텍스트를 편집할 수 없던 문제를 수정했습니다. (버그 67684)

### Known Issues

* Significant image corruption is seen on Intel macOS systems running macOS 13 Ventura, especially when using RED and ARRIRAW media. This appears to be fixed in macOS 14 Sonoma. Bug 62237
*   Volumes shared from macOS systems may fail when accessed from remote systems due to a bug in macOS. To work around this issue:

    * Open System Preferences from the Dock or the Apple menu
    * Choose "Security & Privacy"
    * Click the padlock icon and use your password or Touch ID to allow changes to be made
    * Select "Full Disk Access" in the list on the left
    * Click the `+` button on the right to open a file browser
    * On your keyboard, press `/` to open the "Go to the folder" dialog
    * Enter `/sbin` and click `Go`
    * Select the file called `nfsd` and click `Open`

    After restarting your Mac, the volume(s) should now work correctly. Bug 62601
* Saturated areas in Photo RAW files can acquire a colour tint when adjusting the exposure slider in the Photo RAW Parameters operator while blending highlights. Bug 44769
* The Relight operator currently has unexpected behaviour when dragging to set global scale. Bug 63798
* Blackboard Classic control surfaces exhibit occasional flickering when switching between operators. This will be fixed in a future beta release. Bug 62406
* On some Intel Macs, adding or removing Luma Waveform, RGB Parade, or YCbCr Parade views can result in image corruption and missing scopes. However, if one restarts Baselight with these views present, the scopes will behave properly. Bug 65932
* Shots using RIFE ML Retime (either in a Sequence or a Retime operator) behave as if Process in Working Format is selected. This can result in lower-quality output if the Render Format is larger than the Working Format. These shots also crop the image to the Working Format. Bug 66016
