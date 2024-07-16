# Baselight 릴리즈 6.0.20515 (2024-06-06)

### New Features Since Baselight 6.0.20380

* Added NVIDIA 470.223.02 as a supported NVIDIA driver. Bug 68314
* Added support for decoding XF-AVC 4:2:2 10-bit (xfia) in QuickTime and MP4 files. Bug 68368
* Updated to use AJA SDK 16.2.6 and latest Kona 5 firmware. Bug 67183
* Added diagnostic support for Broadcom MR9580 RAID controller. Bug 67610

### Baselight 6.0.20380 이후 새로운 기능

• NVIDIA 470.223.02 드라이버가 지원되는 NVIDIA 드라이버로 추가되었습니다. (버그 68314)

• QuickTime 및 MP4 파일에서 XF-AVC 4:2:2 10-bit (xfia) 디코딩 지원이 추가되었습니다. (버그 68368)

• AJA SDK 16.2.6 및 최신 Kona 5 펌웨어를 사용하도록 업데이트되었습니다. (버그 67183)

• Broadcom MR9580 RAID 컨트롤러에 대한 진단 지원이 추가되었습니다. (버그 67610)

### Bug Fixes Since Baselight 6.0.20380

* Fixed bug when exporting a cube from scenes that use a DRT with black offset. Bug 68332
* Fixed a crash after repeatedly switching the cursor to the SDI with the X Grade operator selected. Bug 65410
* Fixed UI slowdown which could occur when playing back or when background caching in scenes with strips overlapping multiple shots, especially when zoomed out a long way. Bug 68411
* Improved performance of Blackboard 2 Timeline View in situations where some strips spanned across multiple shots (e.g. an offline strip above the grading conform). Bug 68414
* Fixed a memory leak in the Baselight UI process when background caching in some scenes. Bug 67852
* Improved UI interactivity when working with galleries in "Current Cursor" mode. Bug 68020
* Fixed an issue with the gallery that could cause slow updates. Bug 68434
* Fixed issue causing Chromogen/Flare update to become sluggish over time. Bug 68452
* Greatly improved performance when inserting/removing layers with a large Cuts View present in the UI. Bug 68419
* Removed 'Gallery' and 'Gallery 2' Shots View filters that would appear after adding the Current Cursor to Gallery View. This prevents crashes that could occur after removing these tabs. Bug 68475
* Slightly improved responsiveness when a Layer View is present in the UI and the timeline contains complex stacks. Bug 68478
* Fixed issue causing a crash in the Presets View for certain layer stacks. Bug 67802
* Performance improvements for X Grade operator. Bug 68497

### Baselight 6.0.20380 이후 버그 수정 사항

• 블랙 오프셋이 있는 DRT를 사용하는 씬에서 큐브를 내보낼 때 발생하던 버그를 수정했습니다. (버그 68332)

• X Grade 연산자가 선택된 상태에서 SDI로 커서를 반복해서 전환할 때 발생하던 크래시를 수정했습니다. (버그 65410)

• 여러 샷을 겹치는 스트립이 있는 씬에서 재생하거나 백그라운드 캐싱할 때 발생할 수 있는 UI 느려짐 문제를 수정했습니다. 특히, 크게 축소된 상태에서 문제가 더 두드러졌습니다. (버그 68411)

• 일부 스트립이 여러 샷에 걸쳐 있는 경우(예: 그레이딩 적합 위의 오프라인 스트립) Blackboard 2 타임라인 뷰의 성능을 개선했습니다. (버그 68414)

• 일부 씬에서 백그라운드 캐싱할 때 Baselight UI 프로세스의 메모리 누수를 수정했습니다. (버그 67852)

• “현재 커서” 모드에서 갤러리 작업 시 UI 상호작용성을 개선했습니다. (버그 68020)

• 갤러리에서 업데이트 속도가 느려질 수 있는 문제를 수정했습니다. (버그 68434)

• Chromogen/Flare 업데이트가 시간이 지남에 따라 느려지는 문제를 수정했습니다. (버그 68452)

• UI에 큰 컷 뷰가 있을 때 레이어를 삽입/제거할 때의 성능을 크게 개선했습니다. (버그 68419)

• ‘갤러리’ 및 ‘갤러리 2’ 샷 뷰 필터를 제거했습니다. 이는 갤러리 뷰에 현재 커서를 추가한 후 이러한 탭을 제거하면 발생할 수 있는 크래시를 방지합니다. (버그 68475)

• UI에 레이어 뷰가 있고 타임라인에 복잡한 스택이 포함된 경우 반응성을 약간 개선했습니다. (버그 68478)

• 특정 레이어 스택에서 프리셋 뷰가 크래시를 일으키는 문제를 수정했습니다. (버그 67802)

• X Grade 연산자의 성능을 개선했습니다. (버그 68497)

\
