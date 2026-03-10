---
title: Headless 적응형 Forms에 대한 FAQ
description: 자주 묻는 질문
solution: Experience Manager Forms
feature: Adaptive Forms
topic: Headless
role: Admin, Developer
level: Beginner, Intermediate
keywords: headless, 적응형 양식, FAQ
hide: false
exl-id: 5bfc307d-96a3-4007-b65f-32176ecdb710
source-git-commit: 780f06a39c75dbf8795ac7a971150410ed7981e9
workflow-type: tm+mt
source-wordcount: '837'
ht-degree: 0%

---

# 자주 묻는 질문 (FAQ) {#headless-adaptive-forms-faq}

## Headless 적응형 양식을 사용하기 위해 React.js를 알아야 합니까?

프레임워크, 라이브러리 또는 언어를 사용하여 Headless 적응형 양식을 렌더링하고 Adobe의 REST API를 사용하여 양식을 유효성 검사하고 제출할 수 있습니다. 기본 제공되는 AF 코어 라이브러리는 프레임워크에 독립적입니다. React-Render 및 React-Component 라이브러리는 즉시 사용할 수 있는 편리한 기능입니다. 고유한 구성 요소를 빌드할 수 있습니다. 제공된 구성 요소에 국한되지 않습니다.


<!-- 
## Did Adobe release a new AEM Archetype for Headless adaptive forms?

You can use Archetype 37 with flag `includeFormsheadless` or later flag to create an AEM project with Headless adaptive forms functionality. 

-->

## Headless 적응형 양식을 사용하려면 Forms as a Cloud Service 샌드박스가 필요합니까?

스타터 앱을 사용하여 Headless 적응형 양식 개발 및 스타일링을 시작할 수 있습니다. 백엔드 양식 기능과 함께 Headless 적응형 양식을 호스팅하고 제공하는 Forms as a Cloud Service이 필요합니다.

<!-- ## Do I need an archetype project to develop Headless adaptive forms?

You can use the starter app to start developing and styling your Headless adaptive forms. Later on, you can use the 
archetype project to deploy the finished Headless adaptive forms and corresponding custom code, created using starter app, to Forms as a Cloud Service environment. The Forms as a Cloud Service environment helps you test and productionize the forms. -->

## Headless 적응형 양식의 미리 보기는 어디에서 확인할 수 있습니까? {#storybook-example}

스타터 앱을 사용하여 사용자 지정 Headless 적응형 양식을 렌더링하고 미리 볼 수 있습니다. [스토리북](https://opensource.adobe.com/aem-forms-af-runtime/storybook/?path=/story/reference-examples--introduction) 예제를 수정하여 Headless 적응형 양식을 미리 볼 수도 있습니다.

![](/help/assets/storybook-example.png)

## 사용자 정의 프레임워크에서 Headless 적응형 양식을 사용할 수 있습니까?

Headless 적응형 양식은 [표준 사양](/help/assets/headless-adaptive-forms-specification.pdf)을 기반으로 합니다. 사양을 확장하여 사용자 정의 구성 요소를 빌드하는 데 사용할 수 있습니다. 예를 들어, Chakra UI, Vue.js 등에 대한 구성 요소입니다.

## Headless 적응형 양식은 계단식 필드를 지원합니까?

계단식 필드에서, 두 번째 필드의 내용은 첫 번째 필드에서 선택한 내용에 따라 달라집니다. [스토리북](https://opensource.adobe.com/aem-forms-af-runtime/storybook/?path=/story/adaptive-form-dynamic-behaviour--options&args=formJson.items[0].fieldType:drop-down;formJson.items[0].minimum:!undefined;formJson.items[0].maximum:!undefined;formJson.items[0].label.value:Choose+number+of+options;formJson.items[0].enum[0]:1;formJson.items[0].enum[1]:2;formJson.items[0].enum[2]:3;formJson.items[1].fieldType:drop-down)은(는) 계단식 필드의 예제를 제공합니다.

## Headless 적응형 양식을 사용하여 양식에 개인화된 데이터를 미리 채울 수 있습니까?

Headless 적응형 양식을 사용하면 양식에 개인화된 데이터를 미리 채울 수 있습니다. [스토리북](https://opensource.adobe.com/aem-forms-af-runtime/storybook/?path=/story/reference-examples--prefill-form-with-personalised-data)은(는) Headless 적응형 양식을 미리 채우는 방법에 대한 예제를 제공합니다.

<!-- >
## Can I use existing Adaptive Forms editor to create a Headless adaptive form?

At this moment, you use the Adaptive Form Editor to specify the JSON structure and set submit action for the forms. Support for drag-and-drop components, applying rules using editor, and more editor-related options would be available later in the beta phase. Keep a watch on release notes.  -->

## Angular SPA에서 Headless 적응형 양식을 사용할 수 있습니까?

웹 SDK을 사용하여 Headless 적응형 양식을 Angular SPA와 통합할 수 있습니다. 모든 프레임워크와 독립적입니다. React SDK을 참조로 사용할 수 있습니다.

<!-- ## Should the `-r prerelease` switch be used every time to start the AEM SDK instance or only for the first time?

During the limited release program, use the `-r prerelease` switch every time you start the AEM SDK instance. 

## What is AEM Forms add-on (.far file) and how to install it?

Adobe Experience Manager Forms as a Cloud Service feature archive provides tools to create Headless adaptive forms on the local development environment. To install the feature archive, see [Setup development environment](setup-development-environment.md).

<!-- 
## Where do one get the license.properties file from?

You do not require a license.properties file to run AEM Cloud Service SDK. 

-->

## Headless AF를 위해 개발을 더 쉽게 할 플러그인이 있습니까?

예 — Visual Studio 코드 확장을 사용하면 JSON에서 Headless 적응형 양식을 수동으로 작성할 수 있습니다.

## 모바일 또는 오프라인 양식에 대해 권장되는 접근 방식은 무엇입니까? {#mobile-offline-forms}

Headless 적응형 Forms API를 통해 나만의 네이티브 앱을 빌드하고 양식 정의를 가져오십시오. 오프라인 지원(예: 로컬 저장소 및 동기화)을 선택적으로 구현할 수 있습니다. 권장 접근 방식 및 API에 대한 링크는 [모바일 양식 모범 사례](mobile-forms-best-practices.md)를 참조하십시오.

## AEM Forms에서 GraphQL 또는 Headless API를 어떻게 사용합니까?

AEM Headless 적응형 Forms은 GraphQL이 아닌 **HTTP/REST API**&#x200B;를 사용합니다. 앱에서 이러한 API를 호출하여 양식을 나열하고, 양식 정의(JSON)를 가져오고, 제출 상태를 확인 및 추적합니다. 전체 참조를 위해 [Headless 적응형 양식 HTTP API](https://opensource.adobe.com/aem-forms-af-runtime/api/)를 사용하십시오. 양식을 가져오고 렌더링하는 방법은 [아키텍처](architecture.md) 및 [Headless 양식 이해](understanding-headless-forms.md)를 참조하십시오.

## Adobe AEM Forms에서 React 구성 요소를 사용하여 Headless 양식을 구현하고 스타일을 지정하려면 어떻게 해야 합니까?

React 구성 요소 및 CSS(또는 Material UI와 같은 UI 라이브러리)를 사용하여 Headless 양식을 구현하고 스타일을 지정할 수 있습니다. 양식 논리(상태, 유효성 검사 및 규칙)는 Forms Web SDK 및 양식 JSON에서 제공되며, 앱이 이를 렌더링하는 UI를 제공합니다.

* React UI 라이브러리로 Headless 양식의 스타일을 지정하려면 [사용자 지정 React 라이브러리를 사용하여 Headless 양식 렌더링](use-google-material-ui-react-components-to-render-a-headless-form.md)을 참조하십시오.
* 사용자 지정 React 구성 요소를 빌드하고 양식 필드에 매핑하려면 [사용자 지정 구성 요소를 사용하여 Headless 양식 렌더링](developing-for-headless-forms-using-your-own-components.md)을 참조하십시오.

Headless 양식 사용 시기, 상태 관리 및 유효성 검사와 같은 개념에 대해서는 [Headless 양식 이해](understanding-headless-forms.md)를 참조하십시오.

## 사용자 지정 CSS, 테마, 규칙 편집기 및 Headless 양식을 사용하여 AEM Forms을 구현하고 맞춤화하려면 어떻게 해야 합니까?

**헤드리스 양식:** 스타일 및 디자인을 완전히 제어할 수 있습니다. 자체 React(또는 기타) 구성 요소와 자체 CSS를 사용하며, 기본 제공 테마는 없습니다. [사용자 지정 React 라이브러리를 사용하여 Headless 양식을 렌더링하고](use-google-material-ui-react-components-to-render-a-headless-form.md) [사용자 지정 구성 요소를 사용하여 Headless 양식을 렌더링하고](developing-for-headless-forms-using-your-own-components.md)Headless 양식을 구현하고 스타일링할 수 있습니다.

**클래식 AEM Forms(테마, 규칙 편집기, 시각적 편집기):** 사용자 지정 CSS, 테마 편집기 및 규칙 편집기는 Headless가 아닌 클래식 적응형 Forms 작성 환경에 적용됩니다. 이러한 항목은 Experience League에서 [AEM Forms 설명서](https://experienceleague.adobe.com/docs/experience-manager-forms.html)를 참조하십시오.

## Headless 적응형 양식을 CRM에 연결하여 데이터를 읽거나 쓸 수 있습니까?

Microsoft Dynamics 및 Salesforce을 사용하여 Headless 적응형 양식을 제출하거나 미리 채울 수 있습니다. CRM 외에도 Headless 적응형 양식은 REST 엔드포인트, 이메일 및 사용자 지정 제출 액션을 사용하여 제출 또는 미리 채우기를 지원합니다.
