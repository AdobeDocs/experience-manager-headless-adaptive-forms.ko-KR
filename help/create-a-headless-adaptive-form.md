---
title: 적응형 Forms 편집기를 사용하여 Headless 적응형 양식 만들기
description: 적응형 Forms 편집기를 사용하여 Headless 적응형 양식 만들기
solution: Experience Manager Forms
feature: Adaptive Forms
topic: Headless
role: Admin, Developer
level: Beginner, Intermediate
hide: false
exl-id: 0214dc2e-52ce-40e9-bef3-f4f4a7ff266f
source-git-commit: 47ac7d03c8c4fa18ac3bdcef04352fdd1cad1b16
workflow-type: tm+mt
source-wordcount: '1200'
ht-degree: 49%

---

# 적응형 Forms 편집기를 사용하여 Headless 적응형 양식 만들기 {#create-a-headless-adaptive-form-using-adaptive-forms-editor}

AEM Forms as a Cloud Service에서는 Headless 적응형 Forms을 만들 수 있는 사용자 친화적인 편집기를 제공합니다. 24개 이상의 핵심 구성 요소를 사용할 수 있으므로 편집기에서 구성 요소를 끌어다 놓아 양식을 쉽게 만들 수 있습니다. 또한 규칙 편집기를 사용하면 양식 필드에 유효성 검사를 추가할 수 있습니다.

>[!NOTE]
>
> 
>Headless 적응형 Forms을 처음 사용하는 경우 Adobe에서 다음을 수행하는 것을 권장합니다. [스타터 키트를 사용하여 Headless 양식 만들기 및 게시](create-and-publish-a-headless-form.md) Headless 양식용 적응형 Forms 편집기를 사용하기 전에 Headless 적응형 양식의 기본 사항을 알아보고 다듬는 튜토리얼입니다.

적응형 Forms 편집기를 사용하여 Headless 적응형 양식을 만들려면 다음 단계를 수행하십시오.

## 시작하기 전:

적응형 Forms 편집기를 사용하여 적응형 양식을 만들려면 다음 항목이 필요합니다.

**AEM 6.5 Forms의 경우:**

* AEM 6.5.16.0 이상의 Forms 작성자 인스턴스에 액세스합니다.

* 적응형 양식 핵심 구성 요소

* 적응형 Forms 핵심 구성 요소 템플릿

* 핵심 구성 요소 기반 템플릿을 위한 적응형 양식 테마

* 에 사용자 추가 [!DNL forms-users] 그룹입니다. [!DNL forms-users] 그룹의 멤버는 적응형 양식을 만들 수 있는 권한이 있습니다. 


**AEM Forms as a Cloud Service:**

* 다음에 대한 액세스 권한: [AEM Forms as a Cloud Service 작성자 인스턴스](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/setup-configure-migrate/setup-forms-cloud-service.html?lang=en) 또는 [로컬 AEM Forms as a Cloud Service SDK](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/setup-configure-migrate/setup-local-development-environment.html?lang=en) 환경.

* **적응형 양식 템플릿**: 템플릿은 기본 구조를 제공하고 적응형 양식의 모양(레이아웃 및 스타일)을 정의합니다. 특정 속성과 콘텐츠 구조를 포함하는 서식이 미리 지정된 구성 요소가 있습니다. 또한 테마와 제출 액션을 정의하는 옵션이 제공됩니다. 테마는 모양과 느낌을 정의하고 제출 액션은 적응형 양식 제출 시 수행할 작업을 정의합니다. 예: 수집된 데이터를 데이터 소스로 보내기. 클라우드 서비스는 blank라는 OOTB 템플릿을 제공합니다.

   * `blank Adaptive Forms (Core Components)` 템플릿은 새로운 모든 AEM Forms as a Cloud Service 프로그램에 포함됩니다.
   * 다음을 수행할 수도 있습니다. [새 적응형 Forms(핵심 구성 요소) 템플릿 만들기](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-foundation-components/create-an-adaptive-form-on-forms-cs/template-editor.html) 처음부터.

* **적응형 양식 테마**: 테마에 구성 요소 및 패널에 대한 스타일링 세부 정보가 포함됩니다. 스타일에는 배경색, 상태 색상, 투명도, 정렬과 크기와 같은 속성이 포함됩니다. 테마를 적용하면 지정된 스타일은 해당 구성 요소에 반영됩니다.  `Canvas` 템플릿은 새로운 모든 AEM Forms as a Cloud Service 프로그램에 포함됩니다.

* **권한**: 사용자를 [!DNL forms-users] 그룹에 추가합니다. [!DNL forms-users] 그룹의 멤버는 적응형 양식을 만들 수 있는 권한이 있습니다. 양식별 사용자 그룹의 자세한 목록은 다음을 참조하십시오. [그룹 및 권한](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/setup-configure-migrate/forms-groups-privileges-tasks.html).


## 적응형 양식 만들기  {#create-an-adaptive-form-components}

1. 에 로그인 [!DNL Experience Manager Forms] 작성자 인스턴스.

1. Experience Manager 로그인 페이지에서 자격 증명을 입력합니다. 로그인 후 왼쪽 상단 모서리에서 을 누릅니다 **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Forms]** > **[!UICONTROL Forms & Documents]**.

1. 탭 **[!UICONTROL Create]**  > **[!UICONTROL Adaptive Forms]**. 마법사가 열립니다. 소스 탭에서 템플릿을 선택합니다.

   ![템플릿](/help/assets/core-components-template.png)

   템플릿을 선택하면 템플릿에 지정된 테마 및 제출 액션이 자동으로 선택되고 **[!UICONTROL Create]** 버튼이 활성화되었습니다. 다음 페이지로 이동할 수 있습니다. **[!UICONTROL Style]** 또는 **[!UICONTROL Submission]** 탭을 사용하여 다른 테마를 선택하거나 작업을 제출할 수 있습니다. 선택한 템플릿이 테마를 지정하지 않으면 만들기 버튼은 비활성화된 상태로 유지됩니다. 다음 페이지로 이동할 수 있습니다. **[!UICONTROL Styles]** 탭을 사용하여 테마를 수동으로 선택할 수 있습니다.

1. 다음에서 **[!UICONTROL Style]** 탭에서 테마를 선택합니다.

   * 선택한 템플릿이 테마를 지정하면 테마가 마법사에서 자동으로 선택됩니다. 스타일 탭에서 다른 테마를 선택할 수도 있습니다.

   * 선택한 템플릿이 테마를 지정하지 않으면 스타일 탭을 사용하여 테마를 선택할 수 있습니다. 다음 **[!UICONTROL Create]** 테마를 선택한 후에만 버튼이 활성화됩니다.

1. (선택 사항) 데이터 탭에서 데이터 모델을 선택합니다.

   * **양식 데이터 모델**: [양식 데이터 모델](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/integrate/use-form-data-model/data-integration.html)을 통해 서로 다른 데이터 소스의 엔티티와 서비스를 적응형 양식으로 통합할 수 있습니다. 생성 중인 적응형 양식에 여러 데이터 소스에서의 데이터 가져오기 및 쓰기 작업이 포함된 경우 양식 데이터 모델을 선택합니다.

   * **JSON 스키마**: [JSON 스키마](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-foundation-components/create-an-adaptive-form-on-forms-cs/adaptive-form-json-schema-form-model.html?lang=en) 적응형 양식을 사용하면 생성 또는 소비되는 데이터 구조를 나타내는 JSON 스키마를 연결할 수 있으므로 조직의 백엔드 시스템과 원활하게 통합할 수 있습니다. 이 연결을 통해 작성자는 스키마 요소를 사용하여 콘텐츠를 적응형 양식에 동적으로 추가할 수 있습니다. 작성 프로세스 도중 콘텐츠 브라우저의 데이터 모델 오브젝트 탭을 통해 스키마 요소에 쉽게 액세스할 수 있고, 모든 필드는 새로 만든 적응형 양식에 자동으로 추가됩니다.

   기본적으로 연결된 JSON 스키마의 모든 필드는 자동으로 선택되고 해당 적응형 구성 요소로 변환되어 작성 프로세스를 간소화합니다. 편리성을 추가하기 위해 마법사는 확인란을 통해 적응형 양식에 포함되어야 하는 필드를 선택할 수 있습니다.

1. 다음에서 **[!UICONTROL Submission]** 탭에서 제출 액션을 선택합니다.

   * 템플릿을 선택하면 템플릿에 지정된 제출 액션이 자동으로 선택됩니다. 제출 탭에서 다른 제출 액션을 선택할 수 있습니다. 다음 **[!UICONTROL  Submission]** 탭에는 사용 가능한 모든 제출 작업이 표시됩니다.

   * 선택한 템플릿에서 제출 액션을 지정하지 않은 경우 **[!UICONTROL Submission]** 제출 액션을 선택할 수 있는 탭

1. (선택 사항) **[!UICONTROL Delivery]** 탭에서 적응형 양식의 게시 또는 게시 취소 날짜를 지정할 수 있습니다.

1. **[!UICONTROL Create]**&#x200B;을 누릅니다. 제목, 이름과 위치를 지정하여 적응형 양식을 저장할 대화 상자가 나타납니다.

   * **[!UICONTROL Title]** 양식의 표시 이름을 지정합니다. 제목은 [!DNL Experience Manager Forms] 사용자 인터페이스에서 형식을 식별하는 데 도움이 됩니다.
   * **[!UICONTROL Name:]** 양식 이름을 지정합니다. 이름이 지정된 노드가 저장소에서 만들어집니다. 제목 입력이 시작되면 이름 필드 값이 자동으로 생성됩니다. 제안 값을 변경할 수 있습니다. 이름 필드에는 영숫자 문자, 하이픈 및 밑줄만 포함될 수 있습니다. 잘못된 모든 입력은 하이픈으로 대체됩니다.
   * **[!UICONTROL Path:]** 적응형 양식을 저장할 위치를 지정합니다. 적응형 양식을 `/content/dam/formsanddocuments`에서 바로 저장하거나 `/content/dam/formsanddocuments/adaptiveforms`와 같은 폴더를 만들어 적응형 양식을 저장할 수 있습니다. 경로에서 사용하기 전에 폴더를 만들어야 합니다. 다음 **[!UICONTROL Path]** 필드는 폴더를 자동으로 만들지 않습니다.

1. **[!UICONTROL Create]**&#x200B;을 누릅니다. 적응형 양식을 만들고 적응형 양식 편집기에서 엽니다. 편집기에 템플릿에서 사용 가능한 콘텐츠가 표시됩니다.  적응형 양식 유형에 따라 연관된 양식 요소에 있는 양식 요소 <!--XFA form template, XML schema or --> JSON 스키마 또는 양식 데이터 모델은 **[!UICONTROL Data Model Objects]** 의 탭 **[!UICONTROL Content Browser]** 를 클릭합니다. 이러한 요소를 드래그 앤 드롭하여 적응형 양식을 작성할 수도 있습니다.

이제 적응형 Forms 구성 요소를 적응형 Forms 컨테이너로 끌어다 놓아 양식을 디자인하고 만들 수 있습니다.


## 적응형 양식의 JSON 렌디션 보기 {#preview-form}

적응형 양식을 선택하고 을 누릅니다 **미리 보기**. 양식의 미리보기가 나타납니다. 양식의 양식 정의(JSON)를 보려면 URL에서 .html 확장자를 .model.json으로 바꾸십시오

예: http://[author-server]:[포트]/editor.html/content/forms/af/contact-us.model.json

Headless 적응형 Forms을 사용할 수 있습니다 [getForm](https://opensource.adobe.com/aem-forms-af-runtime/api/#tag/Get-Form-Definition) 양식 정의(JSON)를 가져와서 애플리케이션에서 사용하기 위한 API입니다.

![양식 정의 보기(JSOI)](assets/json-definantion.png)

