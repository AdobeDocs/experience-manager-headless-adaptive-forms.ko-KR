---
title: Headless 적응형 양식 아키텍처
description: AEM Forms Headless 적응형 Forms의 아키텍처와 이를 통해 다양한 플랫폼용 양식을 신속하게 구축할 수 있는 방법에 대해 알아봅니다. 이 문서에서는 Headless 적응형 Forms의 작동 방식과 양식 작성 프로세스를 단순화하기 위해 다양한 애플리케이션과 통합할 수 있는 방법에 대한 통찰력을 제공합니다.
solution: Experience Manager Forms
feature: Adaptive Forms
topic: Headless
role: Admin, Developer
level: Beginner, Intermediate
keywords: 헤드리스, 적응형 양식, 아키텍처
hide: false
exl-id: ee7096d8-89e2-41e0-85e7-b26457df96fb
source-git-commit: 56ad9d8fefc4933847061ba6007ad367984bd2e0
workflow-type: tm+mt
source-wordcount: '893'
ht-degree: 0%

---


# Headless 적응형 양식은 어떻게 작동합니까?

Headless 적응형 양식은 기본적으로 양식 필드(텍스트 상자, 선택 사항 및 기타 필드)와 양식에 대화형 동작을 추가하기 위한 해당 규칙(조건부 논리)으로 구성된 JSON 구조(스키마)입니다. 애플리케이션 또는 웹 사이트에서 REST API를 사용하여 호스팅된 JSON 구조를 요청하고 JSON 구조를 기본적으로 앱 또는 웹 사이트의 양식으로 렌더링할 수 있습니다. 단일 Headless 적응형 양식은 앱이나 웹 사이트별 변경 없이 여러 웹 페이지 및 애플리케이션을 제공할 수 있습니다.

![Headless 적응형 양식 작동 방식](/help/assets/how-headless-adaprive-forms-work.png)

## 아키텍처 {#architecture}

일반적인 Headless 적응형 양식 아키텍처는 Adobe Experience Manager Forms 서버, Adobe Experience Manager Forms 서버에서 호스팅되는 Headless 적응형 양식 및 채널별 양식 표현물을 위한 프론트엔드 앱(웹 사이트, 모바일 애플리케이션, JavaScript 앱, 채팅 애플리케이션 등)을 구성합니다.

Headless 적응형 양식 배포의 일반적인 아키텍처는 다음과 같습니다.

![아키텍처](/help/assets/headless-af-architecture.png)

<!-- 

You can use the React renderer component shipped with Headless adaptive forms to render an Adaptive Form or build your own custom component to natively render a Headless Form in a website or an application or use any UI framework or programming language to build your own components to render your forms.

A typical Headless adaptive forms architecture constitutes an Adobe Experience Manager Server, JSON structure of forms, various frontend apps for channel-specific form renditions.

![Architecture](/help/assets/headless-af-architecture.png) -->

### Headless 적응형 양식 구현의 구성 요소

**Adobe Experience Manager 서버**: Adobe Experience Manager은 Headless 적응형 양식의 호스트 역할과 함께 다음과 같은 백엔드 기능을 제공합니다.

* Headless 양식의 목록, 가져오기, 미리 채우기, 유효성 검사, 제출, 제출 상태를 추적할 RESTful API입니다.
* Headless 적응형 양식을 쉽게 개발할 수 있는 시각적 편집기.
* 서로 다른 데이터 소스로 데이터를 전송하거나 수신하는 Forms 데이터 모델.
* 복잡한 작업을 자동화하는 워크플로우 엔진입니다.

**Headless 적응형 양식**: Headless 적응형 양식은 .json 파일로 표시됩니다. JSON 구조는 양식의 구성 요소, 제한 및 구조를 정의합니다.

**프론트엔드 앱**: SPA(단일 페이지 애플리케이션), 모바일 앱, JavaScript 앱과 같은 프론트엔드 앱은 Headless 적응형 양식(JSON 양식 표현)을 사용하고 클라이언트에서 양식을 렌더링합니다. Headless 적응형 양식과 함께 제공되는 React 렌더러 구성 요소를 사용하여 적응형 양식을 렌더링하거나 사용자 지정 구성 요소를 빌드하여 Headless 적응형 양식을 기본적으로 렌더링할 수 있습니다.

<!-- ### Understanding Headless adaptive forms definition -->



### 개발자 도구

일반적인 개발 사이클에서는 Adobe Experience Manager Forms 서버에서 Headless 적응형 양식을 만들고 호스팅하는 것부터 시작합니다. 두 번째 단계에서는 UI 구성 요소를 매핑하거나 Google Material UI 또는 Chakra UI와 같은 공개 UI 구성 요소 라이브러리를 사용하여 양식의 스타일을 지정합니다. 마지막 단계에서는 애플리케이션(웹 사이트, 모바일 애플리케이션, JavaScript 앱, 채팅 애플리케이션 또는 기타 다양한 표면)에서 Headless 적응형 양식을 가져와 표시합니다.

다음 도구는 Headless 적응형 양식을 만들고 애플리케이션에 통합하는 데 도움이 됩니다.

**Forms Web SDK(클라이언트측 런타임)**: Forms Web SDK는 클라이언트측 JavaScript 라이브러리입니다. 양식 필드에 클라이언트측 유효성 검사를 적용하고, 양식의 상태를 유지하고, 양식을 UI 레이어 또는 적응형 양식 렌더링 구성 요소와 연결하는 후크를 제공할 수 있습니다. 고객이 양식의 다양한 필드에 적용된 제한을 확인하고 양식의 JSON 구조를 UI 프레임워크에 연결할 수 있도록 후크를 제공합니다. Forms Web SDK에는 다음 구성 요소가 있습니다.

* **비즈니스 규칙 프로세서**: 비즈니스 규칙 프로세서는 양식 JSON 구조를 입력으로 수락하고 양식 필드의 상태를 관리하며 규칙을 실행하고 JSON에 있는 이벤트 핸들러를 처리합니다.
* **React 바인더**: 양식 구성 요소에 상태를 추가하기 위한 후크를 컨트롤러에 제공합니다. 또한 양식을 미리 채우는 데에도 유용합니다.
* **구성 요소 라이브러리**: React Spectrum 구성 요소를 제공하고 React Binder 모듈의 후크를 사용하여 해당 구성 요소에 상태를 추가합니다.

Forms Web SDK는 양식의 다양한 필드에 적용된 제한을 확인하는 API를 제공할 뿐만 아니라 Headless 적응형 양식을 UI 프레임워크에 연결하는 후크를 제공합니다. 또한 Headless 적응형 양식&#x200B;을 애플리케이션에 통합하는 데 도움이 되는 Headless 적응형 양식용 React Renderer를 제공합니다. Web SDK의 다음 구성 요소를 사용할 수 있습니다.

* **[@aemforms/af-react-components](https://www.npmjs.com/package/@aemforms/af-react-components)**
* **[@aemforms/af-react-renderer](https://www.npmjs.com/package/@aemforms/af-react-renderer)**
* **[@aemforms/af-core](https://www.npmjs.com/package/@aemforms/af-core)**

이러한 모든 구성 요소는 AEM Archetype에 포함됩니다. Headless 적응형 양식용 AEM Archetype 37 이상 프로젝트를 만들면 위에 나열된 라이브러리의 최신 버전이 프로젝트에 포함됩니다.

**시작된 애플리케이션**: Adobe은 Headless 적응형 양식을 빠르게 시작할 수 있도록 돕기 위해 시작한 애플리케이션도 출시했습니다.

<!-- **View Library (UI Layer)**: A custom form application built in a front-end language. You can use react, Angular, Flutter, NPM, Vue.js, Ionic, BootStrap, or any other language to built front end. You can also use the Headless adaptive forms Super Component, provided out-of-the-box, inside a react application to render a Headless adaptive form. Headless adaptive forms super component makes use of OOTB react spectrum -based form components to render the Headless adaptive form. 

Core-Components: It enables use to render an Adaptive Form using JSON structure. It uses rule grammar to help create dynamic field interactions. The rule grammar is based on [JSON formula](http://github.com/adobe/json-formula/). You can develop your own renderer or embed the React based Adaptive Forms renderer, provided OOTB, in your front-end app to render the form. -->

**스토리북**: [스토리북](https://opensource.adobe.com/aem-forms-af-runtime/storybook/) 는 Headless 적응형 양식의 다양한 구성 요소에 대한 개요를 제공합니다. 또한 지원되는 모든 구성 요소, 해당 속성 및 제약 조건의 목록을 제공합니다.

**Visual Studio 코드 확장**: [Visual Studio 코드 확장](visual-studio-code-extension-for-headless-adaptive-forms.md) 을 참조하십시오. JSON 구조의 구성 요소 추가, 삭제 또는 이름 바꾸기와 같은 일반적인 함수와 함께 양식의 JSON 구조에 대한 IntelliSense 지원 및 유효성 검사를 제공합니다.

**적응형 Forms 버전 2.0 사양**: 적응형 Forms 버전 2.0 사양은 Headless 적응형 양식을 정의하는 데 사용할 수 있는 모든 구성 요소, 제한 및 방법에 대한 자세한 정보를 제공합니다. 사양은 다음 위치에서 사용할 수 있습니다. [PDF](/help/assets/Headless-Adaptive-Form-Specification.pdf) 포맷.

**HTTP 및 JavaScript API**: [HTTP API](https://opensource.adobe.com/aem-forms-af-runtime/api/) headless 양식의 제출 상태를 나열, 가져오기, 유효성 검사, 제출 및 추적할 수 있습니다. [JS API](https://opensource.adobe.com/aem-forms-af-runtime/jsdocs/) 는 모든 JavaScript 기반 UI 프레임워크에서 Headless 적응형 양식을 사용할 수 있도록 지원합니다.

**JSON 공식**: JSON 구조를 쿼리하고 Headless 적응형 양식에 대한 규칙을 만드는 데 도움이 되는 양식 표현식 문법 구현입니다. 이 문법은 스프레드시트 같은 함수와 연산자로 구성된 매쉬업이며 [JMESPath](https://jmespath.org/) json 쿼리 언어. 다음을 사용할 수 있습니다. [운동장](https://opensource.adobe.com/json-formula/dist/index.html) json 공식 구문 및 기능을 살펴봅니다.
