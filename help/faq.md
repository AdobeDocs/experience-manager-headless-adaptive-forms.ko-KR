---
title: 자주 묻는 질문
description: 자주 묻는 질문
solution: Experience Manager Forms
feature: Adaptive Forms
topic: Headless
role: Admin, Developer
level: Beginner, Intermediate
keywords: headless, 적응형 양식, FAQ
hide: false
exl-id: 5bfc307d-96a3-4007-b65f-32176ecdb710
source-git-commit: c46ac28e490a09d6f563c4b5673d30a53c277a69
workflow-type: tm+mt
source-wordcount: '423'
ht-degree: 1%

---

# 자주 묻는 질문(FAQ) {#headless-adaptive-forms-faq}

## Headless 적응형 양식을 사용하기 위해 React.js를 알아야 합니까?

프레임워크, 라이브러리 또는 언어를 사용하여 Headless 적응형 양식을 렌더링하고 REST API를 사용하여 양식을 검증하고 제출할 수 있습니다. OOTB가 제공된 AF-core 라이브러리는 프레임워크에 독립적입니다. OOTB에서 제공되는 React-Render 및 React-Component 라이브러리는 사용자의 편의를 위한 것입니다. 자신만의 구성 요소를 개발할 수 있으며 이러한 구성 요소를 사용하도록 제한되지 않습니다.

<!-- 
## Did Adobe release a new AEM Archetype for Headless adaptive forms?

You can use Archetype 37 with flag `includeFormsheadless` or later flag to create an AEM project with Headless adaptive forms functionality. 

-->

## Headless 적응형 양식을 사용하려면 Forms as a Cloud Service 샌드박스가 필요합니까?

스타터 앱을 사용하여 Headless 적응형 양식 개발 및 스타일링을 시작할 수 있습니다. Forms as a Cloud Service 적응형 호스트를 사용하려면 백엔드 기능과 함께 Headless 양식을 제공해야 합니다.

<!-- ## Do I need an archetype project to develop Headless adaptive forms?

You can use the starter app to start developing and styling your Headless adaptive forms. Later on, you can use the 
archetype project to deploy the finished Headless adaptive forms and corresponding custom code, created using starter app, to Forms as a Cloud Service environment. The Forms as a Cloud Service environment helps you test and productionize the forms. -->

## Headless 적응형 양식 미리 보기는 어디에서 얻을 수 있습니까? {#storybook-example}

스타터 앱을 사용하여 사용자 지정 Headless 적응형 양식을 렌더링하고 미리 볼 수 있습니다. [스토리북](https://opensource.adobe.com/aem-forms-af-runtime/storybook/?path=/story/reference-examples--introduction) 예제를 수정하여 Headless 적응형 양식을 미리 볼 수도 있습니다.

![](/help/assets/storybook-example.png)

## 사용자 정의 프레임워크에서 Headless 적응형 양식을 사용할 수 있습니까?

Headless 적응형 양식은 [표준 사양](/help/assets/headless-adaptive-forms-specification.pdf)을 기반으로 합니다. 사양을 확장하여 사용자 정의 구성 요소를 빌드하는 데 사용할 수 있습니다. 예를 들어, Chakra UI, Vue.js 등에 대한 구성 요소입니다.

## Headless 적응형 양식은 계단식 필드를 지원합니까?

계단식 필드에서 두 번째 필드의 내용은 첫 번째 필드에서 선택한 콘텐츠에 따라 다릅니다. [스토리북](https://opensource.adobe.com/aem-forms-af-runtime/storybook/?path=/story/adaptive-form-dynamic-behaviour--options&amp;args=formJson.items[0].fieldType:drop-down;formJson.items[0].minimum:!undefined;formJson.items[0].maximum:!undefined;formJson.items[0].label.value:Choose+number+of+options;formJson.items[0].enum[0]:1;formJson.items[0].enum[1]:2;formJson.items[0].enum[2]:3;formJson.items[1].fieldType:drop-down)은(는) 계단식 필드의 예제를 제공합니다.

## Headless 적응형 양식을 사용하여 양식에 개인화된 데이터를 미리 채울 수 있습니까?

Headless 적응형 양식을 사용하면 양식에 개인화된 데이터를 미리 채울 수 있습니다. [스토리북](https://opensource.adobe.com/aem-forms-af-runtime/storybook/?path=/story/reference-examples--prefill-form-with-personalised-data)은(는) Headless 적응형 양식을 미리 채우는 방법에 대한 예제를 제공합니다.

<!-- >
## Can I use existing Adaptive Forms editor to create a Headless adaptive form?

At this moment, you use the Adaptive Form Editor to specify the JSON structure and set submit action for the forms. Support for drag-and-drop components, applying rules using editor, and more editor-related options would be available later in the beta phase. Keep a watch on release notes.  -->

## Angular SPA에서 Headless 적응형 양식을 사용할 수 있습니까?

웹 SDK을 사용하여 Headless 적응형 양식을 Angular SPA과 통합할 수 있습니다. 모든 프레임워크와 독립적입니다. React SDK을 참조로 사용할 수 있습니다.

<!-- ## Should the `-r prerelease` switch be used every time to start the AEM SDK instance or only for the first time?

During the limited release program, use the `-r prerelease` switch every time you start the AEM SDK instance. 

## What is AEM Forms add-on (.far file) and how to install it?

Adobe Experience Manager Forms as a Cloud Service feature archive provides tools to create Headless adaptive forms on the local development environment. To install the feature archive, see [Setup development environment](setup-development-environment.md).

<!-- 
## Where do one get the license.properties file from?

You do not require a license.properties file to run AEM Cloud Service SDK. 

-->

## Headless AF를 위해 개발을 더 쉽게 할 플러그인이 있습니까?

예. Microsoft Visual Studio 코드에 대해 확장을 사용할 수 있습니다. Headless 적응형 양식 JSON을 수동으로 작성하는 편리한 방법을 제공합니다.

## Headless 적응형 양식을 CRM에 연결하여 데이터를 읽거나 쓸 수 있습니까?

Microsoft Dynamics 및 Salesforce을 사용하여 Headless 적응형 양식을 제출하거나 미리 채울 수 있습니다. CRM 외에도 Headless 적응형 양식은 REST 엔드포인트, 이메일 및 사용자 지정 제출 액션을 사용하여 제출 또는 미리 채우기를 지원합니다.
