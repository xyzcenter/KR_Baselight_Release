# Baselight Release 6.0.20380 (2024-05-09)

##

### New Features Since Baselight 6.0.20256

* Added support for the NVIDIA RTX 5000 Ada Lovelace GPU. Bug 68211

### Baselight 6.0.20256 이후 새로운 기능

• NVIDIA RTX 5000 Ada Lovelace GPU 지원이 추가되었습니다. (버그 68211)

### Bug Fixes Since Baselight 6.0.20256

* Improved compatibility of metadata written to QuickTime files; other tools should now be able to read it. Bug 68174
* Fixed image errors in some situations when working on a multiple-GPU system with an input sequence stored on a remote system which is connected by dual-link networking. Bug 68001
* Fixed crash when selecting a Paint operator in some scenes. Bug 67090
* Fixed issue where opening non-gallery scenes in the gallery would require the '\_v6' suffix. Bug 67893
* Fixed incorrect drawing of dimmed filtered-out ranges in the Timeline View, especially when changing the zoom level. Bug 67057

### Baselight 6.0.20256 이후 버그 수정 사항

• QuickTime 파일에 작성된 메타데이터의 호환성이 개선되었습니다. 이제 다른 도구에서도 이를 읽을 수 있습니다. (버그 68174)

• 듀얼 링크 네트워킹으로 연결된 원격 시스템에 입력 시퀀스가 저장된 상태에서 다중 GPU 시스템에서 작업할 때 발생하던 이미지 오류를 수정했습니다. (버그 68001)

• 일부 씬에서 페인트 연산자를 선택할 때 발생하던 크래시를 수정했습니다. (버그 67090)

• 갤러리에서 비갤러리 씬을 열 때 ‘\_v6’ 접미사를 요구하던 문제를 수정했습니다. (버그 67893)

• 타임라인 뷰에서 줌 레벨을 변경할 때 특히 필터링된 범위가 흐리게 그려지던 문제를 수정했습니다. (버그 67057)
