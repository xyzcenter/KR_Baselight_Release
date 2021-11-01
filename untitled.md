# 베이스라이트 릴리즈 노트 5.2.12393 (2019-10-03)

## 최신기능 (Baselight 5.2.12381이후)

*   Added support for reading ProRes encoded MXFs from the ALEXA Mini LF

    camera \[bug 52776]\
    **알렉사 미니 LF 카메라로부터 프로레스로 엔코딩된 MXF 파일 읽기를 지원합니다.**

## 버그 개선 ( Baselight 5.2.12381이후)&#x20;

* Fixed a failure in the bl-render commandline when omitting the "-filetype" parameter \[bug 52795]
* Fixed ARRIRAW MXF failures in thumbnails and on systems with limited GPU memory \[bug 52833]\
  **  제한된 GPU 메모리로 인해서 썸네일과 시스템에서 ARRIRAW MXF 실패되는 부분 수정**
