---
title: Headless 적응형 양식용 Visual Studio 코드 확장
description: Headless 적응형 양식용 Visual Studio 코드 확장
solution: Experience Manager Forms
feature: Adaptive Forms
topic: Headless
role: Admin, Developer
level: Beginner, Intermediate
keywords: headless, 적응형 양식, Visual Studio 코드 확장
hide: false
exl-id: 11960e91-6c09-48d4-9d57-37537f808cd4
source-git-commit: 47ac7d03c8c4fa18ac3bdcef04352fdd1cad1b16
workflow-type: tm+mt
source-wordcount: '206'
ht-degree: 0%

---

# Headless 적응형 양식용 Microsoft Visual Studio 코드 확장

Microsoft® Visual Studio 코드를 IDE로 사용하는 경우 Microsoft Visual Studio 코드용 응용 Forms 확장을 사용할 수 있습니다. 확장:

* Visual Studio 코드에 적응형 Forms에 대한 IntelliSense 기능을 추가합니다.
* Headless 적응형 양식 구성 요소에 대한 JSON 구문의 유효성 검사 및 자동 완성을 지원합니다.
* Headless 적응형 양식에 대한 구조를 쉽게 탐색할 수 있는 패널을 제공합니다
* Headless 적응형 양식 번역 지원

<!-- 

The extension o easily navigate the structure 

Adobe provides an extension for Microsoft&reg; Visual Studio Code to make it easier for you to navigate structure and develop Headless adaptive forms in Visual Studio Code. The extension adds Adaptive Forms related IntelliSense capabilities and helps auto-complete Headless adaptive forms JSON syntax. It also adds a panel, titled Forms Tree, to help navigate structure of Headless adaptive form. 

-->

## 사전 요구 사항

* 다운로드 및 설치 [Microsoft Visual Studio Code 1.62.0 이상](https://code.visualstudio.com/docs/supporting/FAQ#_how-do-i-find-the-version). 이전 버전이 있거나 설치된 버전이 없는 경우에서 최신 버전을 다운로드하십시오. [Microsoft 웹 사이트](https://code.visualstudio.com/docs/setup/setup-overview). Apple macOS의 명령줄에서 Visual Studio를 사용하려면 [명령줄에서 실행](https://code.visualstudio.com/docs/setup/mac#_launching-from-the-command-line).
* 다운로드 [적응형 양식 빌더 확장](/help/assets/adaptive-form-builder-0.12.0.vsix).

## 확장 설치

1. 명령 프롬프트를 열고 다운로드한 확장 파일이 포함된 디렉토리로 이동합니다. *적응형 양식 빌더-[버전].v6*.

1. 다음 명령을 실행하여 확장을 설치합니다.

   `code -–install-extension adaptive-form-builder-0.12.0.vsix`

   <br>

   ![확장 설치 중](/help/assets/install-extension.png)


   .vsix 파일에 대한 자세한 내용은 [Microsoft Visual Studio 코드 도움말](https://code.visualstudio.com/docs/editor/extension-marketplace#_install-from-a-vsix).
