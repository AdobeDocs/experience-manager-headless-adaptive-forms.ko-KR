---
title: 모바일 양식 우수 사례
description: 모바일 및 오프라인 양식 사용 사례의 경우, Headless 적응형 Forms API를 통해 고유한 기본 앱을 빌드하고 양식 정의를 가져오십시오. 기본 모바일 애플리케이션에 대해 권장되는 접근 방식입니다.
solution: Experience Manager Forms
feature: Adaptive Forms
topic: Headless
role: Admin, Developer
level: Beginner, Intermediate
keywords: 모바일 양식, 기본 앱, 오프라인 양식, Headless API
hide: false
exl-id: b8e2f1a4-5c6d-4e2a-9f3b-1d4e5a6c7b8d
source-git-commit: 780f06a39c75dbf8795ac7a971150410ed7981e9
workflow-type: tm+mt
source-wordcount: '330'
ht-degree: 0%

---

# 모바일 양식 우수 사례 {#mobile-forms-best-practices}

모바일 및 오프라인 양식 사용 사례의 경우, Headless 적응형 Forms API를 통해 고유한 기본 앱을 빌드하고 양식 정의를 가져오는 것이 좋습니다. 이를 통해 모바일 경험을 완벽하게 제어하고 모바일 플랫폼이 발전함에 따라 지속적인 지원을 받을 수 있습니다.

## 권장 접근 방식 {#recommended-approach}

다음과 같은 기본 모바일 애플리케이션(iOS 또는 Android)을 빌드합니다.

1. **Headless 양식 정의를 가져옵니다** - [Headless 적응형 Forms API를 사용](https://opensource.adobe.com/aem-forms-af-runtime/api/)하여 요청 시 양식 JSON을 검색합니다(예: 사용자가 양식을 열거나 앱에서 해당 양식으로 이동할 때). 사용 가능한 양식을 나열한 다음 ID별로 양식 정의를 가져올 수 있습니다.

2. **앱에서 양식을 렌더링합니다** - 기본 설정 UI 프레임워크(예: React Native 또는 기본 보기)를 사용하여 JSON에서 양식을 렌더링합니다. 스택에 맞는 Forms Web SDK 및 기존 Headless 적응형 양식 React 구성 요소를 사용하거나 동일한 JSON 구조를 사용하는 고유한 렌더러를 빌드할 수 있습니다.

3. **선택적으로 오프라인 지원** - 앱에서 로컬 저장소 및 동기화를 구현합니다. 예를 들어 온라인 상태일 때 양식 정의를 캐시하고, 로컬로 초안을 저장하고, 디바이스가 다시 온라인 상태일 때 데이터를 제출하거나 동기화합니다.

이 접근 방식은 Android 및 iOS이 변경될 때 앱을 유지 관리할 수 있도록 하며 양식 작성, 유효성 검사 및 제출에 지원되는 Headless 적응형 Forms 플랫폼을 사용합니다.

## 시작하기 {#getting-started}

* [AEM Headless 적응형 양식 개요](overview.md) - 기능 및 개념
* [Headless 적응형 양식 API](https://opensource.adobe.com/aem-forms-af-runtime/api/) - 양식을 프로그래밍 방식으로 나열, 가져오기, 유효성 검사 및 제출합니다.
* [아키텍처](architecture.md) - Headless 적응형 양식의 작동 방식과 프론트엔드 앱에서 이를 사용하는 방식.

단계별 통합은 [Headless 양식 만들기 및 게시](create-and-publish-a-headless-form.md) 및 [개발자 포털](https://experienceleague.adobe.com/landing/aem-headless-forms/developer.html?lang=en)을 참조하십시오.
