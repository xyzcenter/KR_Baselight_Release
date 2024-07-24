# 😀 Baselight Release 5.3.18523 (2023-09-04)



## New Features Since Baselight 5.3.18465

* Added preference to fl-diag for the NVIDIA GPUs test, to check the number of installed render GPUs matches the expected number \[bug 65466]

## Baselight 5.3.18465 이후의 새로운 기능

* 설치된 렌더 GPU의 수가 예상된 수와 일치하는지 확인하기 위해 NVIDIA GPU 테스트를 위한 fl-diag 환경 설정이 추가되었습니다 \[버그 65466]



## Bug Fixes Since Baselight 5.3.18465

* Fixed issue where IMF package metadata configured in Render View was not applied to the created package. Notably this affected CPL and PKL filenames, OPL file creation and other metadata such as "Title" and "Issuer" \[bug 65450]
* Fixed errors reading CLF files containing 1D or 3D LUTs \[bug 65446]
* Fixed memory leak which could occur when closing scenes \[bug 65467]
* Fixed failure to start some applications e.g. fl-queue \[bug 65489]
* Fixed possible crash conforming CMX EDLs with locator marks containing an empty comment \[bug 65438]
* Fixed errors rendering using a queue on a remote system when the user ID of the user submitting the render does not exist on the remote system \[bug 65469]

## Baselight 5.3.18465 이후의 버그 수정

* Render View에서 구성된 IMF 패키지 메타데이터가 생성된 패키지에 적용되지 않는 문제를 수정했습니다. 특히 CPL 및 PKL 파일명, OPL 파일 생성 및 “Title”과 “Issuer” 같은 기타 메타데이터에 영향을 미쳤습니다 \[버그 65450].
* 1D 또는 3D LUTs를 포함하는 CLF 파일을 읽을 때 발생하는 오류를 수정했습니다 \[버그 65446].
* 장면을 닫을 때 발생할 수 있는 메모리 누수를 수정했습니다 \[버그 65467].
* 일부 애플리케이션(예: fl-queue)을 시작하지 못하는 문제를 수정했습니다 \[버그 65489].
* 빈 코멘트를 포함한 로케이터 마크가 있는 CMX EDL을 맞출 때 발생할 수 있는 충돌을 수정했습니다 \[버그 65438].
* 렌더를 제출한 사용자의 사용자 ID가 원격 시스템에 존재하지 않을 때 원격 시스템에서 큐를 사용하여 렌더링할 때 발생하는 오류를 수정했습니다 \[버그 65469].

***
