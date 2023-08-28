---
title: Adobe Experience Manager 적응형 Forms을 사용하여 Headless 양식 만들기 및 게시 | 단계별 안내서
description: 이 단계별 안내서에서는 Adobe Experience Manager의 적응형 양식을 사용하여 Headless 양식을 만들고 게시하는 방법을 알아봅니다. Headless의 이점을 살펴보고 양식 작성 프로세스를 간소화할 수 있습니다. Adobe Experience Manager Headless 적응형 Forms을 사용하여 장치 간에 원활하게 작동하는 동적 반응형 양식 구축을 시작합니다.
solution: Experience Manager Forms
feature: Adaptive Forms
topic: Headless
role: Admin, Developer
level: Beginner, Intermediate
hide: false
exl-id: cd7c7972-376c-489f-a684-f479d92c37e7
source-git-commit: 47ac7d03c8c4fa18ac3bdcef04352fdd1cad1b16
workflow-type: tm+mt
source-wordcount: '1017'
ht-degree: 0%

---



# React 앱을 사용하여 Headless 양식 만들기 및 미리 보기 {#introduction}

시작 키트는 React 앱을 사용하여 빠르게 시작할 수 있도록 도와줍니다. angular, Vanilla JS 및 선택한 기타 개발 환경에서 Headless 적응형 양식을 자유롭게 개발하고 사용할 수 있습니다.

Headless 적응형 양식으로 시작하는 것은 매우 쉽고 빠릅니다. 준비된 React 프로젝트를 복제하고 종속성을 설치한 다음 프로젝트를 실행합니다. React 앱 실행 및 실행에 Headless 적응형 양식이 통합되었습니다. 샘플 React 프로젝트를 사용하여 Headless 적응형 양식을 프로덕션 환경에 배포하기 전에 빌드하고 테스트할 수 있습니다.

시작하겠습니다.

>[!NOTE]
>
>
> 이 시작 안내서는 React 앱을 사용합니다. Headless 적응형 양식을 사용하기 위해 선택한 기술 또는 프로그래밍 언어를 자유롭게 사용할 수 있습니다.

## 시작하기 전 {#pre-requisites}

React 앱을 만들고 실행하려면 컴퓨터에 다음 항목이 설치되어 있어야 합니다.

* 설치 [git 최신 릴리스](https://git-scm.com/downloads). Git을 처음 사용하는 경우 다음을 참조하십시오 [Git 설치](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git).

* 설치 [Node.js 16.13.0 이상](https://nodejs.org/en/download/). Node.js를 처음 사용하는 경우 [Node.js 설치 방법](https://nodejs.dev/en/learn/how-to-install-nodejs).

## 시작하기

요구 사항을 충족하면 다음 단계를 수행하여 시작하십시오.

1. [Headless 적응형 양식 시작 키트 설정](#setup)

1. [시작 키트에 포함된 Headless 적응형 양식 미리 보기](#preview)

1. [나만의 Headless 적응형 양식 만들기 및 렌더링](#custom)



## 1. Headless 적응형 양식 시작 키트 설정 {#install}

스타터 키트는 샘플 Headless 적응형 양식 및 해당 라이브러리가 있는 React 앱입니다. 이 키트를 사용하여 Headless 적응형 양식 및 관련 React 구성 요소를 개발하고 테스트하십시오. 다음 명령을 실행하여 Headless 적응형 양식 시작 키트를 설정합니다.

1. 명령 프롬프트를 열고 다음 명령을 실행합니다.

   ```shell
   git clone https://github.com/adobe/react-starter-kit-aem-headless-forms
   ```

   이 명령은 라는 디렉터리를 만듭니다. **react-starter-kit-aem-headless-forms** 현재 위치에서 Headless 적응형 양식 React 스타터 앱을 복제합니다. 양식을 렌더링하는 데 필요한 구성 및 종속성 목록과 함께 디렉터리에는 다음과 같은 중요한 콘텐츠가 포함되어 있습니다.

   * **샘플 양식**: 시작 키트에는 대출 신청 양식이 포함되어 있습니다. 앱에 포함된 양식(양식 정의)을 보려면 `/react-starter-kit-aem-headless-forms/form-definations/form-model.json` 파일.
   * **샘플 React 구성 요소**: 스타터 키트에는 리치 텍스트 및 슬라이더를 위한 샘플 React 구성 요소가 포함되어 있습니다. 이 안내서는 이러한 리치 텍스트 및 슬라이더 구성 요소를 사용하여 사용자 지정 구성 요소를 만드는 데 도움이 됩니다.
   * **Mappings.ts**: mappings.ts 파일은 사용자 지정 구성 요소를 양식 필드에 매핑하는 데 도움이 됩니다. 예를 들어 숫자 스텝퍼 필드를 등급 구성 요소에 매핑합니다.
   * **환경 구성**: 환경 구성을 사용하면 스타터 키트에 포함된 양식을 렌더링하거나 AEM Forms 서버에서 양식을 가져올 수 있습니다.

   ![](/help/assets/getting-started-starter-kit-content.png)

   >[!NOTE]
   >
   > 
   > 문서의 예제는 VSCode를 기반으로 합니다. 일반 텍스트 코드 편집기를 자유롭게 사용할 수 있습니다.


1. 다음 위치로 이동 **react-starter-kit-aem-headless-forms** 디렉터리를 만들고 다음 명령을 실행하여 종속성을 설치합니다.

   ```shell
   npm install
   ```

   이 명령은 Headless 적응형 양식 라이브러리(@aemforms/af-react-renderer, @aemforms/af-react-components, @adobe/react-spectrum)와 같이, 앱을 실행하고 빌드하는 데 필요한 모든 필수 패키지 및 라이브러리를 다운로드하고, 유효성 검사를 실행하고, 양식 인스턴스에 대한 데이터를 유지합니다.

   ![](/help/assets/install-react-app-starter-kit.png)


## 2. Headless 적응형 양식 미리 보기 {#preview}

시작 키트를 설정한 후 샘플 Headless 적응형 양식을 미리 보고 사용자 정의 양식으로 바꿀 수 있습니다. AEM Forms 서버에서 양식을 검색하도록 시작 키트를 구성할 수도 있습니다. 양식 미리 보기

1. 이름 바꾸기 `env_template` 파일 위치: `.env` 파일. 또한 USE_LOCAL_JSON 옵션이 true로 설정되어 있는지 확인합니다.

   ![](/help/assets/rename-env-file.png)

   <!-- The options in the .env file help you configure source of the forms definantion (.JSON):
    *  To source forms definantion (.JSON) from an AEM Server, set USE_LOCAL_JSON option to false, use the AEM_URL option to specify URL  of your AEM Server, and set the AEM_FORM_PATH option to path of your adaptive form.
    *  To source forms definantion (.JSON) form-model.json file included in the starter-kit, set USE_LOCAL_JSON option to false. -->

1. 다음 명령을 사용하여 앱을 실행합니다.

   ```shell
     npm start
   ```


   이 명령은 로컬 개발 서버를 시작하고 스타터 앱에 포함된 샘플 Headless 적응형 양식을 기본 웹 브라우저에서 엽니다.

   ![샘플 헤드리스 양식](assets/sample-headless-adaptive-form.png)

   짜잔! 사용자 정의 Headless 적응형 양식 개발을 시작하도록 모두 설정되었습니다.

   <!--  As you know, in a headless form the form data and logic are separate from the presentation layer and can be used by any client that can make HTTP requests, such as a mobile app, a static site, or a different web application. The form is often managed and stored on a server, which serves as the backend for the form. The client sends requests to the server to retrieve the form, submit data, and receive updated form data. This allows for greater flexibility and integration with different technologies. You can store and retrive a Headless adaptive form on an AEM Server  -->

## 3. Headless 적응형 양식 만들기 및 렌더링{#custom}

Headless 적응형 양식은 양식과 해당 구성 요소(예: 필드 및 버튼)를 JSON(JavaScript Object Notation) 형식으로 나타냅니다. JSON 포맷을 사용하면 다양한 프로그래밍 언어에서 쉽게 구문 분석하여 사용할 수 있어 시스템 간에 양식 데이터를 편리하게 교환할 수 있는 장점이 있습니다. 앱에 포함된 샘플 Headless 적응형 양식을 보려면 `/react-starter-kit-aem-headless-forms/form-definations/form-model.json` 파일.

&quot;이름&quot;, &quot;이메일&quot;, &quot;연락처 번호&quot; 및 &quot;메시지&quot; 네 개의 필드가 있는 연락처 양식을 만들어 보겠습니다. 필드는 JSON 내의 오브젝트(항목)로 정의되며, 각 오브젝트(항목)에는 유형, 레이블, 이름 및 필수 속성과 같은 속성이 있습니다. 양식에는 &quot;submit&quot; 유형의 단추도 있습니다. 다음은 양식에 대한 JSON입니다.


```JSON
{
  "afModelDefinition": {
    "adaptiveform": "0.10.0",
    "items": [
      {
        "fieldType": "text-input",
        "label": {
          "value": "Name"
        },
        "name": "name"
      },
      {
        "fieldType": "text-input",
        "format": "email",
        "label": {
          "value": "Email"
        },
        "name": "email"
      },
      {
        "fieldType": "text-input",
        "format": "phone",
        "pattern": "[0-9]{10}",
        "label": {
          "value": "Contact Number"
        },
        "name": "Phone"
      },
      {
        "fieldType": "multiline-input",
        "label": {
          "value":"Message"
        },
        "name": "message"
      },
      {
        "fieldType": "button",
        "label":{
          "value": "Submit"
        },
        "name":"submit",
        "events":{
          "click": "submitForm()"
        }
      }
    ],
    "action": "https://eozrmb1rwsmofct.m.pipedream.net",
    "description": "Contact Us",
    "title": "Contact Us",
    "metadata": {
      "grammar": "json-formula-1.0.0",
      "version": "1.0.0"
    }
  }
}
```

>[!NOTE]
>
> * &quot;afModelDefinition&quot; 속성은 React 애플리케이션에만 필요하며 양식 정의의 일부가 아닙니다.
> * 양식 JSON을 손으로 제작하거나 [AEM 적응형 양식 편집기(적응형 양식 WYSIWYG 편집기)](create-a-headless-adaptive-form.md) 을 클릭하여 양식 JSON을 만들고 게재합니다. 프로덕션 환경에서는 AEM Forms을 사용하여 나중에 양식 JSON을 비롯한 다양한 정보를 제공합니다.
> * 이 자습서에서는 https://pipedream.com/을 사용하여 양식 제출을 테스트합니다. 조직에서 승인한 자체 또는 타사 엔드포인트를 사용하여 Headless 적응형 양식에서 데이터를 수신합니다.


양식을 렌더링하려면 샘플 Headless 적응형 양식 JSON으로 바꿉니다 `/react-starter-kit-aem-headless-forms/form-definations/form-model.json` 위의 JSON을 사용하여 파일을 저장하고 starter-kit가 컴파일되고 양식을 새로 고칠 때까지 기다립니다.

![샘플 Headless 적응형 양식 JSON 바꾸기 `/react-starter-kit-aem-headless-forms/form-definations/form-model.json` 사용자 지정 Headless 적응형 양식 JSON 사용](assets/render-custom-headless-adaptive-form.png)

<!-- Your form is ready. Let's add some validations and make "Name", "Email", and "Message" fields mandatory. -->

Headless 적응형 양식을 성공적으로 렌더링했습니다.


## 보너스

양식을 호스팅하는 웹 페이지의 제목을 다음으로 설정해 보겠습니다. `Contact Us | WKND Adventures and Travel`. 제목을 변경하려면 _react-starter-kit-aem-headless-forms/public/index.html_ 편집할 파일 및 제목을 설정합니다.

![](assets/contact-us-headless-adaptive-forms-updated-title.png)


## 다음 단계

기본적으로 시작 키트는 [Adobe 스펙트럼](https://spectrum.adobe.com/) 양식을 렌더링할 구성 요소입니다. 를 사용하여 나만의 구성 요소나 서드파티 구성 요소를 만들어 사용할 수 있습니다. 예를 들어 Google Material UI 또는 Chakra UI를 사용합니다.

예: [Google 재질 UI 사용](use-google-material-ui-react-components-to-render-a-headless-form.md) 연락처 양식을 렌더링합니다.




