# 베이스라이트 릴리즈 노트 5.2.12692 (2019-12-13)

## 최신 기능 ( Baselight 5.2.12568 이후)

*   Improved error message to report memory information on out-of-memory

    exit and on start-up \[bug 53516]\
    **   메모리 부족 종료 및 시작할 때  개선된 에러메시지로 메모리 정보를 리포트함.**

## 버그 개선 (Baselight 5.2.12568 이후)

* Addressed an issue which could lead to rectangular areas of corrupted images in some scenes when using the 418 nvidia driver on Linux \[bug 52607]\
  **리눅스 운영체제에서 418 엔비디아 드라이버 사용시 일부 씬에서 사각형 깨진 이미지가 나오는 문제 해결**
* Fixed bug where the perspective trackers wouldn't get linked after copying or selecting already existing ones \[bug 53459]
* Fixed crash in flit service when a copy is cancelled \[bug 53390]
* Fixed crash when grabbing large stacks to the scratchpad \[bug 50161]
* Fixed presentation of some cloud volumes on macOS \[bug 53310]
* Fixed crash when opening Render View \[bug 53400]
* Fixed image artefacts and out-of-order frames in long-GOP MXF movies. This affected AVC-LongGOP and XDCAM encoded movies in particular \[bug 53441]
