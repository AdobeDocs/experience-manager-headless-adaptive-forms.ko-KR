---
title: AEM Headless 적응형 양식 개요
description: AEM Headless 적응형 양식 개요.
hide: true
exl-id: cd7c7972-376c-489f-a684-f479d92c37e7
source-git-commit: 0127f8ddede38083f0932b0e8d7efdd0dd77c3a6
workflow-type: tm+mt
source-wordcount: '510'
ht-degree: 3%

---


# 릴리스 정보

Experience Manager 헤드리스 적응형 양식 얼리 어답터 릴리스를 시작합니다. 를 시작하고 릴리스를 최대한 활용하려면 리소스와 지침을 계속 읽어 보십시오.

Adobe Experience Manager Headless 적응형 양식을 사용하여 React, Angular 등과 같은 프론트엔드 UI 프레임워크를 사용하여 양식 애플리케이션을 빌드하고 적응형 Forms Web SDK를 사용하여 상태 관리, 유효성 검사 및 다양한 다른 터치포인트와의 통합과 같은 기능을 사용할 수 있습니다.

얼리어답터 릴리스에서는 의 Headless 적응형 양식을 사용할 수 있는 액세스 권한을 제공합니다. [로컬 개발 환경](setup-development-environment.md). 로컬 개발 환경을 사용하여 Headless 적응형 양식을 작성하고 테스트할 수 있습니다.

Headless 적응형 양식은 지속적으로 개선됩니다. 최신 개선 사항을 확인하려면 이 페이지를 정기적으로 방문하십시오. 이 페이지에서는 조기 액세스, 최신 릴리스, 새로운 기능, 개선 사항, 버그 수정, 더 이상 사용되지 않는 기능, 특별 지침 및 향후 변경 계획에 대한 정보를 제공합니다.

<!-- 

## July 2022 (v0.22.1)

### New features

* Introduced the `validateFormData` API. It validates all the components against the rules and constraints an returns the list of errors. The validation takes place on the server.
* Introduced the `FormLoad` event.
* Introduced the `importData` and `exportData`.
* You can now dynamically add or remove items, that expect unqiue values, from a repeatable panel. You can use the `minItems` and `maxitems` constraint to set limit of item.
* You can now use constraint to set maximum file upload size, accepted file types, minimum files, and maximum files to upload.

### Improvements and bug fixes

* The service was executing some event handlers twice. The issue is fixed.
* Fixing Data Generation with different values of dataRef, name and type.

<!-- ### React Renderer component -->

## 얼리어답터 릴리스에서 사용 가능한 아티팩트

Adobe Experience Manager Headless 적응형 양식을 귀하에게 제공하기 위한 여정에서 다음 아티팩트를 얼리어답터 릴리스에서 사용할 수 있습니다.

### AEM FORMS AS A CLOUD SERVICE SDK

Headless 적응형 양식을 만들고 저장하고 가져올 수 있는 AEM Forms as a Cloud Service SDK입니다. 또한 Headless 적응형 양식에 대한 미리 채우기, 서버측 규칙 유효성 검사 및 제출 서비스를 제공하는 데 도움이 됩니다.

### Forms 웹 SDK

Forms Web SDK는 양식의 다양한 필드에 적용된 제한 사항의 유효성을 검사하기 위한 API와 양식의 JSON 구조를 UI 프레임워크에 연결하기 위한 후크를 제공합니다. 또한 Headless 적응형 양식&#x200B;을 애플리케이션에 통합하는 데 도움이 되는 Headless 적응형 양식용 React Renderer를 제공합니다. Web SDK의 다음 구성 요소를 사용할 수 있습니다.

* **[@aemforms/af-react-components](https://www.npmjs.com/package/@aemforms/af-react-components)**
* **[@aemforms/af-react-renderer](https://www.npmjs.com/package/@aemforms/af-react-renderer)**
* **[@aemforms/af-core](https://www.npmjs.com/package/@aemforms/af-core)**

<!-- npm i --save @aemforms/af-react-components @aemforms/af-react-renderer @aemforms/af-core -->

#### 스토리북

[스토리북](https://opensource.adobe.com/aem-forms-af-runtime/storybook/) 는 Headless 적응형 양식의 다양한 구성 요소에 대한 개요를 제공합니다. 또한 지원되는 모든 구성 요소, 해당 속성 및 제약 조건의 목록을 제공합니다.

### Forms 핵심 구성 요소

<!-- Forms components are the structural elements that constitute the content of the form being authored. These components provide various form fields and ability to customize those fields. -->

핵심 구성 요소는 표준화된 웹 콘텐츠 관리(WCM) 구성 요소 세트로서, 개발 시간을 단축하고 양식 유지 관리 비용을 절감하는 데 도움이 됩니다. Forms 컨테이너 구성 요소는 핵심 구성 요소입니다. Forms as a Cloud Service SDK의 적응형 Forms 편집기에서 Headless 적응형 양식의 JSON 구조를 임베드하고 렌더링하는 데 도움이 됩니다.

### 적응형 Forms V2 사양

Headless 적응형 양식 사양은 Headless 적응형 양식을 정의하는 데 사용할 수 있는 모든 구성 요소, 제한 및 방법에 대한 자세한 정보를 제공합니다. 사양은 다음 위치에서 사용할 수 있습니다. [PDF](/help/assets/Headless-Adaptive-Form-Specification.pdf) 포맷.

### HTTP 및 JS API

[HTTP API](https://opensource.adobe.com/aem-forms-af-runtime/api/) headless 양식의 제출 상태를 나열, 가져오기, 유효성 검사, 제출 및 추적할 수 있습니다. [JS API](https://opensource.adobe.com/aem-forms-af-runtime/jsdocs/) 는 모든 JavaScript 기반 UI 프레임워크에서 Headless 적응형 양식을 사용할 수 있도록 지원합니다.

### Visual Studio 코드 확장

[Visual Studio 코드 확장](visual-studio-code-extension-for-headless-adaptive-forms.md) 을 참조하십시오. JSON 구조의 구성 요소 추가, 삭제 또는 이름 바꾸기와 같은 일반적인 기능과 함께 양식의 JSON 구조에 대한 IntelliSense 지원 및 유효성 검사를 제공합니다.

<!-- ## What's next

The following features would be available in upcoming releases:

* HTTP APIs to invoke a business logic.
* Server-side capabilities (Prefill, server-side validation, generating Document of Record (DoR), Submitting to a Form Data Model or using Form Data Models for creating rules, and more).
* Continuous improvements to specifications and Headless adaptive form runtime.
* Use  Adaptive Forms editor for easier management and authoring Headless adaptive forms.
-->