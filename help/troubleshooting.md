---
title: Headless 적응형 Forms 문제 해결
description: Headless 적응형 Forms 문제 해결
keywords: 헤드리스, 적응형 양식, 문제 해결
solution: Experience Manager Forms
feature: Adaptive Forms
topic: Headless
role: Admin, Developer
level: Beginner, Intermediate
hide: false
exl-id: bfb7e688-d2be-4aaa-ac9b-147cbd74b516
source-git-commit: 47ac7d03c8c4fa18ac3bdcef04352fdd1cad1b16
workflow-type: tm+mt
source-wordcount: '133'
ht-degree: 5%

---

# 문제 해결

## 로컬 개발 환경에 Archetype 프로젝트를 배포할 수 없음

### 문제

`mvn -PautoInstallPackage clean install` 또는 유사한 명령을 사용하여 AEM Archetype 프로젝트를 배포하는 경우 프로젝트가 배포되지 않습니다.

### 이유

지원되지 않는 버전 또는 node.js 또는 NPM의 손상된 설치 때문에 발생할 수 있습니다.

### 솔루션

1. 환경에서 [현재 Node.JS 설치를 제거](https://khushwantsehgal.wordpress.com/2022/06/28/how-to-remove-node-js-completely-from-windows-10/)합니다.

1. NPM으로 Node.JS 16.13.0 이상을 설치합니다.

1. 시스템을 다시 부팅합니다.


## `mvn clean install` 명령이 실행되지 않습니다.

### 문제

`mvn clean install` 또는 유사한 명령을 사용하여 AEM Archetype 프로젝트를 배포하는 경우 명령이 실행되지 않습니다.

### 이유

Git이 설치되지 않은 경우 발생할 수 있습니다.

### 솔루션

[Git 최신 릴리스](https://git-scm.com/downloads)를 다운로드하여 설치하십시오. Git을 처음 사용하는 경우 [Git 설치](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git)를 참조하십시오.
