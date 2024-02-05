---
title: 핵심 구성 요소 및 Headless를 사용하여 매력적인 양식 작성
seo-title: Build Engaging Forms Using Core Components and Headless
description: 핵심 구성 요소 및 Headless를 사용하여 매력적인 양식 작성
seo-description: Build Engaging Forms Using Core Components and Headless
topic-tags: develop
exl-id: ef99ffe9-4a37-4f0a-a4d3-78976c92220f
source-git-commit: bcc51bcae3b26cf20e7c0b5b75935bf69a991731
workflow-type: tm+mt
source-wordcount: '2452'
ht-degree: 85%

---

# AEM Forms as a Cloud Service에서 핵심 구성 요소 및 Headless 적응형 Forms을 사용하여 매력적인 Forms 구축 {#build-engaging-forms-using-core-components-and-headless}

## 랩 개요 {#lab-overview}

이 실습 랩에서는 다음과 같은 사항을 알아봅니다.

AEM Forms를 사용하여 AEM Sites와 일치하는 최신 핵심 구성 요소를 사용해 적응형 양식을 쉽게 만드는 방법, 적응형 양식을 웹, 모바일 및 채팅에 헤드리스 양식으로 제공하여 옴니채널 데이터 캡처 경험을 가능하게 하는 방법. 또한 스타일링, 사용자 정의 및 프론트엔드 개발에 대한 모범 사례를 살펴봅니다.

## 핵심 사항 {#key-takeaways}

* **비즈니스 민첩성**: 비즈니스 사용자로서 여러 채널의 양식 경험을 쉽게 작성할 수 있습니다.

* **프론트엔드 개발자의 능력**: 프론트엔드 개발자로서 Headless 양식을 사용하여 최종 사용자 경험을 제어할 수 있습니다.

* **개발자 속도**: 개발자로서 Sites 및 Forms 구성 요소를 쉽고 일관되게 사용자 정의할 수 있습니다.

## 사전 요구 사항 {#prerequisites}

랩에서 이 핸즈를 사용하려면:

* 설치 [git 최신 릴리스](https://git-scm.com/downloads). Git을 처음 사용하는 경우 다음을 참조하십시오 [Git 설치](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git).

* 설치 [Node.js 16.13.0 이상](https://nodejs.org/en/download/). Node.js를 처음 사용하는 경우 [Node.js 설치 방법](https://nodejs.org/en/learn/getting-started/how-to-install-nodejs).

* [적응형 Forms 핵심 구성 요소 활성화](enable-headless-adaptive-forms-and-core-components-on-forms-cloud-service.md) AEM Forms as a Cloud Service 환경용입니다.

* 설치 [Microsoft Visual Studio 코드](https://code.visualstudio.com/download) 또는 일반 텍스트 편집기입니다. 문서의 예제에서는 Microsoft Visual Studio 코드를 사용합니다.



## 수업 1 {#lesson-1}

### 목표 {#lesson-1-objectives}

AEM Forms as a Cloud Service 환경을 숙지합니다.

### 수업 컨텍스트 {#lesson-1-context}

이 수업에서는 사용자 인터페이스를 탐색하며 AEM Forms as a Cloud Service 환경을 숙지합니다.

### 연습 {#lesson-1-excercise}

1. 브라우저를 열고 Cloud Service 작성자 환경의 URL을 입력합니다. 예:
   [https://author-p105303-e986623.adobeaemcloud.com/ui#/aem/aem/start.html](https://author-p105303-e986623.adobeaemcloud.com/ui%23/aem/aem/start.html)

1. Cloud Service 작성자 환경에 로그인합니다.
   ![](/help/assets/screenshot2028113829.png){width="50%" align="left"}

1. AEM Forms UI로 이동하려면 **Forms > Forms 및 문서**.



   ![](/help/assets/screenshot2028113929.png){width="50%" align="left"}

   환경 설정 또는 정보와 관련된 팝업을 모두 닫습니다. 사용 가능한 모든 양식이 표시됩니다.


## 수업 2

### 목표

최신 핵심 구성 요소를 사용하여 적응형 양식을 작성하고 양식을 구성 및 제출합니다.

### 수업 컨텍스트

이 수업에서는 비즈니스 사용자로서 데이터 캡처를 위한 표준화된 OOTB 핵심 구성 요소로 적응형 양식 작성을 사용하여 웹, 모바일 및 채팅과 같은 여러 채널의 적응형 양식을 작성합니다.

### 연습

1. 양식의 제출 엔드포인트를 만듭니다.

   1. 새 브라우저 탭에서 <https://requestbin.com/>을 엽니다.
   1. **공개 bin 만들기**를 클릭하고 엔드포인트 URL을 복사합니다.
      ![](/help/assets/screenshot2028114329.png){width="50%" align="left"}

      ![](/help/assets/screenshot202023-03-0120at206.10.0020pm.png){width="50%" align="left"}

1. 마법사 인터페이스를 사용하여 적응형 양식 작성:

   1. 수업 1에 사용된 브라우저 탭에서 AEM Forms as Cloud Service 웹 인터페이스로 이동한 후 양식 및 문서로 이동합니다.
      ![](/help/assets/screenshot2028114029.png)

   1. **만들기**를 클릭하고 적응형 양식을 선택합니다.
      ![](/help/assets/screenshot2028114629.png)

   1. 아래와 같이 템플릿 선택 화면에서 **핵심 구성 요소가 있는 빈 내용** 템플릿을 선택합니다.
      ![](/help/assets/screenshot202023-03-0120at206.09.1520pm.png)

   1. **스타일** 탭을 클릭하고 아래와 같이 **wknd-theme** 테마를 선택합니다.
      ![](/help/assets/screenshot202023-03-0120at206.09.2320pm.png)

   1. 다음을 클릭합니다. **제출** 탭을 클릭하고 다음을 선택합니다. **REST 끝점에 제출** 카드 및 의 공용 저장소를 지정합니다. **POST 요청용 URL** 아래에 표시된 필드:
      ![](/help/assets/screenshot202023-03-0120at206.09.5320pm.png)

   1. **만들기**&#x200B;를 클릭합니다. 양식에 이름 및 제목을 지정합니다. 예를 들어, **등록**. **만들기**&#x200B;를 클릭합니다.

   1. 적응형 양식 편집기가 열립니다. 환경 설정 또는 정보와 관련된 모든 팝업이나 대화 상자를 닫습니다. 왼쪽 레일에서 구성 요소 브라우저를 클릭하고 **머리글** 및 **바닥글** 구성 요소를 추가합니다.
      ![](/help/assets/screenshot2028121929.png)

   1. 구성 요소 브라우저에서 구성 요소를 드래그 앤 드롭하여 다음과 같이 양식을 만듭니다.

      ![](/help/assets/screenshot2028115129.png){width="50%" align="left"}

1. 양식에 유효성 검사 추가:

   1. **전화번호** 구성 요소를 클릭하여 팝업 메뉴가 표시되도록 합니다. 메뉴의 **공구 모양 아이콘**&#x200B;을 클릭하여 필드를 구성합니다.

   1. **유효성 검사 탭**&#x200B;을 열고 **필수** 필드에 표시한 후 **완료**를 클릭합니다. 성공 메시지가 표시됩니다.
      ![](/help/assets/screenshot2028123529.png){width="50%" align="left"}

      ![](/help/assets/screenshot2028123629.png){width="50%" align="left"}

1. 양식을 미리 보고 제출합니다.

   1. 최종 사용자 관점에서 양식을 미리 보려면 **미리보기**&#x200B;를 클릭합니다.

   1. 더미 데이터로 양식을 채우십시오.

   1. 양식을 제출합니다.
      ![](/help/assets/screenshot2028125729.png)

   1. bin 요청 탭에서 제출된 데이터를 확인합니다.
      ![](/help/assets/screenshot2028125829.png)

1. 규칙이 있는 양식에 대화형 작업 추가:

   1. 다음을 클릭합니다. **5% 할인을 받으려면 상자를 선택합니다.** 구성 요소. 옵션 도구 모음에서 규칙 아이콘을 클릭합니다. 규칙 편집기 옵션이 열립니다.

   1. 다음과 같은 경우 규칙을 만듭니다. **5% 할인을 받으려면 상자를 선택합니다.** 옵션을 선택하면 신용 카드 적용 옵션이 비활성화됩니다.

1. 양식을 게시합니다.

   1. AEM Forms 관리 인터페이스(예: ) 열기 `https://author-p105303-e986623.adobeaemcloud.com/ui%23/aem/aem/forms.html/content/dam/formsanddocuments`을 누르고 양식을 선택합니다.

   1. **게시**&#x200B;를 클릭합니다.

      ![](/help/assets/screenshot2028115629.png)

      성공 메시지가 표시됩니다.

      ![](/help/assets/screenshot2028115729.png)

      양식의 게시 URL은 `https://publish-p105303-e986623.adobeaemcloud.com/content/forms/af/registration.html`과 유사합니다.

   1. 게시된 양식을 보려면 위 URL의 프로그램 ID(pXXXXXX) 및 환경 ID(eXXXXXX)를 환경의 ID로 바꿉니다.

## 수업 3

### 목표

프론트엔드 개발 모범 사례를 사용하여 스타일을 업데이트합니다.

### 수업 컨텍스트

이 수업에서는 프론트엔드 개발자로서 이전에 만든 적응형 양식의 스타일을 쉽게 업데이트하는 방법을 알아봅니다.

### 연습

테마의 로컬 저장소 설정:

1. 관리자 권한으로 명령 프롬프트 또는 셸 열기.

   ![](/help/assets/screenshot2028115829.png){width="50%" align="left"}

1. 명령 프롬프트에서 다음 명령을 사용하여 **c:\git** 폴더로 이동합니다

   ```Shell
   cd c:\git
   ```

1. 다음 명령을 사용하여 테마 프론트엔드 코드를 복제합니다.

   ```Shell
   git clone -b WKND https://github.com/adobe/aem-forms-theme-canvas
   ```


1. 나열된 순서대로 다음 명령을 사용하여 **aem-forms-theme-canvas** 디렉터리로 이동하고 Visual Studio Code를 엽니다.

   ```Shell
   cd aem-forms-theme-canvas
   code .
   ```

   ![](/help/assets/screenshot2028126029.png)

1. **상위 폴더에 있는 모든 파일의 작성자 신뢰**&#x200B;를 선택하고 **예, 작성자를 신뢰함**&#x200B;을 클릭합니다.

   ![](/help/assets/screenshot2028116229.png){width="50%" align="left"}

1. 클라우드 서비스 게시 환경에서 호스팅되는 양식을 렌더링하려면 `env_template` 파일의 이름을 바꿉니다.  파일 이름을 바꾸려면 **env_template** 파일을 마우스 오른쪽 버튼으로 클릭하고 **이름 바꾸기** 옵션을 선택합니다.

   ![](/help/assets/screenshot2028116429.png){width="50%" align="left"}

   </br>

   ![](/help/assets/screenshot2028116529.png){width="50%" align="left"}

1. .env 파일의 변수에 대해 다음 값을 설정하고 파일을 저장합니다.

   * **AEM_URL**: 클라우드 서비스 게시 환경을 지정합니다. 예, `https://publish-p105303-e986623.adobeaemcloud.com/`

   * **AEM_ADAPTIVE_FORM**: 양식의 경로를 지정합니다. 예를 들어 양식 경로가 `/content/forms/af/registration`인 경우 이 변수의 값은 `registration`이 됩니다.

     ![](/help/assets/screenshot2028116429.png){width="50%" align="left"}

1. AEM 환경에서 로컬 사용자를 만듭니다.

   >[!NOTE]
   > 로컬 사용자를 만들려면 다음 작업을 수행하십시오.
   > 다음으로 이동 `AEM Home` > `Tools` > `Security` > `Users`
   > 사용자가 forms-users 그룹의 멤버인지 확인합니다.


1. 명령 프롬프트 창에서 다음 명령을 실행합니다.

   ```Shell
   npm install
   ```

   ![](/help/assets/screenshot2028117029.png)

   >[!NOTE]
   >
   > * 를 통해 npm을 업데이트하라는 메시지가 표시되는 경우 `npm notice Run npm nstall -g npm@9.6.0` 명령, 메시지를 무시합니다.
   > * 통합 문서에서 지시하지 않는 한 다른 npm 명령은 실행하지 않습니다.

1. 이제 다음 명령을 실행하여 양식을 미리 봅니다.

   ```Shell
   npm run live
   ```

   ![](/help/assets/screenshot2028117229.png)

   위의 명령이 실행되면 다음을 기다립니다. `webpack compiled` 메시지와 함께 AEM 로그인 페이지로 리디렉션됩니다.

1. 클릭 **로컬로 로그인(관리 작업만 해당)** AEM 로그인 페이지에서 참조할 수 있습니다.
1. 생성된 로컬 사용자의 자격 증명을 입력하면 양식이 브라우저 탭에 표시됩니다.

   >[!NOTE]
   >
   >`npm run live` 명령을 실행한 후 3~4분 이상 브라우저에 빈 화면이 표시되는 경우 브라우저 URL의 `localhost`를 127.0.0.1로 변경하고 **Enter**&#x200B;를 누릅니다.


   ![](/help/assets/screenshot2028115129.png){width="50%" align="left"}


1. Visual Studio Code에서 `PROJECT\src\site\_variables.scss` 파일을 엽니다. `$error` 색상은 빨간색입니다.

   ![](/help/assets/screenshot2028120729.png){width="50%" align="left"}

1. 브라우저에서 양식을 제출하면 **이름** 필드에 빨간색이 표시됩니다.

   ![](/help/assets/screenshot2028120829.png)

1. **$error** 색상을 **#5736eb**&#x200B;로 설정하고 파일을 저장합니다.

   ![](/help/assets/screenshot2028120729.png){width="50%" align="left"}

1. 브라우저를 새로 고치고 양식을 제출합니다. 이에 따라 이름 필드의 오류 색상이 변경됩니다.

   ![](/help/assets/screenshot2028121129.png)

1. 명령 프롬프트에서 **CTRL+C**&#x200B;를 누르고 **Y**&#x200B;를 입력한 다음 **Enter** 키를 눌러 npm 프로세스를 종료합니다. 다음 연습 세트와 충돌하지 않도록 npm 서버를 정지하는 것이 중요합니다.
1. Visual Studio Code 및 명령 프롬프트 창을 닫습니다.

## 수업 4

### 목표

양식을 웹/모바일 및 기타 인터페이스에 Headless 양식으로 렌더링합니다.

### 수업 컨텍스트

이 수업에서는 프론트엔드 개발자로서 React 스펙트럼 디자인 프레임워크를 사용하여 이전에 Headless 양식으로 만든 적응형 양식을 렌더링하는 방법을 알아봅니다.

### 연습

React 스타터 프로젝트를 사용하여 로컬 저장소 설정:

1. 관리자 권한을 사용해 명령 프롬프트를 엽니다.

   ![](/help/assets/screenshot2028115829.png){width="50%" align="left"}

1. 명령 프롬프트에서 다음 명령을 사용하여 **c:\git** 폴더로 이동합니다

   ```Shell
   cd c:\git
   ```

1. 다음 명령을 사용하여 적응형 양식 React 스타터 프로젝트를 복제합니다.

   ```Shell
   git clone https://github.com/adobe/react-starter-kit-aem-headless-forms
   ```

   ![](/help/assets/screenshot2028117329.png)

1. 나열된 순서대로 다음 명령을 사용하여 **react-starter-kit-aem-headless-forms** 디렉터리로 이동하고 Visual Studio Code를 엽니다.

   ```Shell
   cd react-starter-kit-aem-headless-forms
   
   code .
   ```

   ![](/help/assets/screenshot2028117529.png)


   Visual Studio Code 창이 열립니다.

   ![](/help/assets/screenshot2028117429.png){width="50%" align="left"}

클라우드 서비스 게시 환경에서 호스팅되는 양식을 렌더링하려면 다음과 같이 합니다.

1. env_template 파일의 이름을 .env 파일로 바꿉니다. 이름을 바꾸려면 **env_template** 파일을 마우스 오른쪽 버튼으로 클릭하고 **이름 바꾸기** 옵션을 선택합니다.

   ![](/help/assets/screenshot2028117629.png){width="50%" align="left"}

   ![](/help/assets/screenshot2028117729.png)

1. .env 파일의 변수에 대해 다음 값을 설정합니다. 변수를 업데이트한 후 파일을 저장합니다.

   * **AEM_URL**: 클라우드 서비스 게시 환경의 URL을 지정합니다. 예, `https://publish-p105303-e986623.adobeaemcloud.com`

   * **AEM_FORM_PATH**: 이전 수업에서 만든 적응형 양식의 경로를 지정합니다. 예, `/content/forms/af/registration/`

     ![](/help/assets/screenshot202023-03-0820at202.49.1820pm.png)

1. 명령 창을 열고 현재 위치가 react-starter-kit-aem-headless-forms 디렉터리인지 확인한 후 다음 명령을 실행합니다.

   ```Shell
   npm install
   ```

   ![](/help/assets/screenshot2028118029.png)


1. 명령 프롬프트 창에서 다음 명령을 실행합니다.

   ```Shell
   npm start
   ```

   ![](/help/assets/screenshot2028118129.png)

   위 명령은 React 스펙트럼 프론트엔드 라이브러리를 사용하여 Headless 방식으로 AEM에서 가져온 양식 정의를 렌더링하는 로컬 개발 서버를 시작합니다.

   >[!NOTE]
   >
   > 
   > `npm start` 명령을 실행한 후 3~4분 이상 브라우저에 빈 화면이 표시되는 경우 브라우저 URL의 `localhost`를 127.0.0.1로 변경하고 **Enter**&#x200B;를 누릅니다.

   ![](/help/assets/screenshot2028118229.png)

이 Headless 형식의 규칙 실행을 확인해 보겠습니다.

1. **5% 할인을 받으려면 확인란 선택** 옵션을 선택합니다. 신용 카드 신청을 위한 후속 옵션이 비활성화됩니다.

   ![](/help/assets/screenshot2028126229.png)

1. 신용 카드 옵션을 활성화하려면 **5% 할인을 받으려면 확인란 선택**&#x200B;을 선택 취소합니다.

   ![](/help/assets/screenshot2028126329.png)

비즈니스 사용자로서 서버의 양식을 변경하고 자동으로 Headless 양식에 반영된 변경 사항을 확인해 보겠습니다.

1. 브라우저에서 AEM Forms 관리 인터페이스를 엽니다. 예: [https://author-p105303-e986623.adobeaemcloud.com/ui#/aem/aem/forms.html/content/dam/formsanddocuments](https://author-p105303-e986623.adobeaemcloud.com/ui%23/aem/aem/forms.html/content/dam/formsanddocuments).

1. 다음 항목 선택 **접촉선** 양식 및 클릭 **편집.** 적응형 양식 편집기에서 양식이 열립니다.


1. **전화번호** 필드를 선택하고 도구 모음에서 **편집 아이콘(연필 아이콘)**&#x200B;을 클릭합니다. 팝업 도구 모음이 보이지 않으면 오른쪽 상단에서 **미리보기** 버튼 왼쪽에 있는 **편집** 버튼을 클릭하여 편집 모드로 전환합니다.

   ![](/help/assets/screenshot2028119629.png)

1. 레이블을 휴대폰 번호로 변경합니다. 양식의 빈 공간을 클릭하면 양식의 변경 사항이 저장됩니다.

   ![](/help/assets/screenshot2028119729.png)

변경 사항을 게시 환경에 전파하기 위해 업데이트된 양식을 게시해 보겠습니다.

1. AEM Forms 관리 인터페이스 탭에서 등록 양식을 선택하고 **게시 취소**&#x200B;를 클릭합니다. **게시 취소** 버튼이 표시되지 않으면 3단계로 건너뛰어 변경 사항을 직접 게시합니다.

1. **게시 취소**&#x200B;를 클릭합니다. 각 대화 상자에서 **닫기**&#x200B;를 클릭합니다.

1. 브라우저를 새로 고친 후 등록 양식을 선택하고 **게시**&#x200B;를 클릭합니다.

1. **게시**&#x200B;를 클릭합니다. 각 대화 상자에서 **닫기**&#x200B;를 클릭합니다.

1. Headless 양식이 표시된 브라우저 탭을 새로 고칩니다. 전화번호 레이블이 휴대폰 번호로 변경됩니다.

   ![](/help/assets/screenshot2028120529.png)

1. **react-starter-kit-aem-headless-forms** 프로젝트를 시작하는 데 사용된 명령 프롬프트 창을 열고 **CTRL+C**&#x200B;를 누른 후 **Y**&#x200B;를 입력하고 Enter 키를 눌러 npm 프로세스를 종료합니다. 다음 연습 세트와 충돌하지 않도록 npm 서버를 정지하는 것이 중요합니다.

1. Visual Studio Code 및 명령 프롬프트 창을 닫습니다.


## 수업 5

### 목표

Google Material UI를 사용하여 양식을 Headless 양식으로 렌더링

### 수업 컨텍스트

이 수업에서는 프론트엔드 개발자로서 Google Material UI를 사용하여 이전에 Headless 양식으로 만든 적응형 양식을 렌더링하는 방법을 알아봅니다.

### 연습

Material UI 스타터 프로젝트를 사용하여 로컬 저장소 설정:

1. 관리자 권한을 사용해 명령 프롬프트를 엽니다.

   ![](/help/assets/screenshot2028115829.png){width="50%" align="left"}


1. 명령 프롬프트에서 다음 명령을 사용하여 **c:\git** 폴더로 이동합니다.

   ```Shell
   cd c:\git
   ```

1. 나열된 순서대로 다음 명령을 실행하여 mui라는 폴더를 만들고 다음 명령을 사용하여 mui 폴더로 이동합니다.

   ```Shell
   mkdir mui
   
   cd mui
   ```

1. 다음 명령을 사용하여 적응형 양식 React 스타터 프로젝트를 복제합니다.

   ```Shell
   git clone -b mui-lab https://github.com/adobe/react-starter-kit-aem-headless-forms
   ```

   ![](/help/assets/screenshot2028126529.png)

1. 나열된 순서대로 다음 명령을 사용하여 **react-starter-kit-aem-headless-forms** 폴더로 이동하고 Visual Studio Code에서 코드를 엽니다.

   ```Shell
   cd react-starter-kit-aem-headless-forms
   
   code .
   ```

   ![](/help/assets/screenshot2028126829.png)

클라우드 서비스 게시 환경에서 호스팅되는 양식을 렌더링하려면 다음과 같이 합니다.

1. **env_template** 파일의 이름을 **.env** 파일로 바꿉니다. 이름을 바꾸려면 **env_template** 파일을 마우스 오른쪽 버튼으로 클릭하고 **이름 바꾸기**&#x200B;를 선택합니다.

   ![](/help/assets/screenshot2028126629.png){width="50%" align="left"}

1. .env 파일의 변수에 대해 다음 값을 설정합니다. 변수를 업데이트한 후 파일을 저장합니다. **CTRL + S** 스위치 조합을 사용하여 파일을 저장합니다.

   * **AEM_URL**: 클라우드 서비스 게시 환경의 URL을 지정합니다. 예: [https://publish-p105303-e986623.adobeaemcloud.com](https://publish-p105303-e986623.adobeaemcloud.com/)

   * **AEM_FORM_PATH**: 이전 수업에서 만든 적응형 양식의 경로를 지정합니다. 예: /content/forms/af/registration/

     ![](/help/assets/screenshot2028126929.png)

1. 명령 창을 열고 현재 위치가 **react-starter-kit-aem-headless-forms** 디렉터리인지 확인한 후 다음 명령을 실행합니다.

   ```Shell
   npm install
   ```

   ![](/help/assets/screenshot2028127029.png)

1. 명령 프롬프트 창에서 다음 명령을 실행합니다.

   ```Shell
   npm start
   ```

   ![](/help/assets/screenshot2028127129.png)

   위 명령은 로컬 개발 서버를 시작하고 Google Material UI 프론트엔드 라이브러리를 사용하여 Headless 방식으로 AEM에서 가져온 양식 정의를 렌더링합니다.

   >[!NOTE]
   >
   >`npm start` 명령을 실행한 후 3~4분 이상 브라우저에 빈 화면이 표시되는 경우 브라우저 URL의 `localhost`를 127.0.0.1로 변경하고 **Enter**&#x200B;를 누릅니다.

   ![](/help/assets/screenshot2028127229.png)

1. 이 양식 렌디션에서 동일한 비즈니스 로직의 실행을 평가하려면 다음 작업을 수행하십시오.

   **5% 할인을 받으려면 확인란 선택**&#x200B;을 선택합니다. 후속 옵션인 **We Finance 기업 신용 카드 양식을 신청하시겠습니까?**&#x200B;가 비활성화됩니다.

   ![](/help/assets/screenshot2028127329.png){width="50%" align="left"}

## 수업 6

### 목표

Material UI 구성 요소 변형을 사용하여 Headless 형태의 대체 디자인 만들기

### 수업 컨텍스트

이 수업에서는 프론트엔드 개발자로서 이전에 비즈니스 사용자가 만든 적응형 양식에 대해 Material UI를 사용하여 다양한 구성 요소의 대체 표시를 만드는 방법을 알아봅니다.

### 연습

Headless 프로젝트의 구성 요소 변형을 업데이트합니다. Material UI 텍스트 입력 구성 요소의 변형을 `OutlinedInput`으로 변경하려면 다음과 같이 합니다.

1. Visual Code에서 `src/components/textinput/index.tsx`에 있는 `index.tsx` 파일을 열어 텍스트 입력 구성 요소로 이동합니다.

1. 코드 103행의 시작 부분에 `//`를 추가합니다. 이렇게 하면 줄이 주석으로 변환됩니다.

   ```Shell
   //const Cmp = \'outlined\' === appliedCssClassNames ? OutlinedInput: Input;
   ```

1. 구성 요소의 다른 변형을 사용하고 파일을 저장하려면 104행에 다음을 추가합니다. **CTRL + S** 스위치 조합을 사용하여 파일을 저장합니다.

   ```Shell
   const Cmp = OutlinedInput;
   ```

   ![](/help/assets/screenshot2028127629.png)

   &#39;OutlinedInput&#39; 변형에 올바른 대소문자를 사용하는 것이 필수적입니다. 그렇게 하지 않으면 컴파일이 실패합니다. 로컬 개발 환경 컴파일은 명령 프롬프트에서 자동으로 시작됩니다. 다음 메시지가 나타날 때까지 기다립니다

   `webpack 5.75.0 compiled with 3 warnings in 6659 ms`
   `inside proxy req`
   `setting new origin header`

1. 브라우저가 자동으로 새로 고쳐지지 않으면 브라우저를 새로 고쳐 텍스트 입력 구성 요소가 다른 변형을 사용하는지 확인합니다.

   ![](/help/assets/screenshot2028127729.png)


   이 변경 사항은 AEM Forms Server의 양식 정의를 변경하지 않고 최종 사용자에게 발생하며, 고려 중인 Headless 채널에만 적용됩니다. 예: 이 랩의 웹 채널.

   ![](/help/assets/screenshot2028127529.png){width="50%" align="left"}


1. Visual Studio Code 및 명령 프롬프트 창을 닫습니다.

## 자주 묻는 질문 (FAQ)

+++ 적응형 양식 마법사를 공개적으로 사용할 수 있습니까?

예, AEM Forms as Cloud Service에서 사용할 수 있습니다.

+++


+++ 핵심 구성 요소를 공개적으로 사용할 수 있습니까?

예, AEM Forms as Cloud Service에서 적응형 양식 핵심 구성 요소를 사용할 수 있습니다.

+++

+++ Headless 양식을 공개적으로 사용할 수 있습니까?

예, AEM Forms as Cloud Service에서 Headless 양식을 사용할 수 있습니다.

+++

+++ Headless 양식에 별도의 라이선스가 필요합니까?

아니요, Headless 양식은 동일한 라이선스 값 지표(양식 제출 수)를 사용합니다.

+++

+++ AEM 6.5 Forms에서 핵심 구성 요소 및 Headless 양식을 사용할 수 있습니까?

예, 적응형 양식 핵심 구성 요소와 Headless 양식 모두 AEM Forms 6.5 서비스 팩 16 이상에서 사용할 수 있습니다.

+++


## 다음 단계

적응형 양식을 작성하고 Headless 양식을 사용하여 여러 채널에 전달하는 방법을 학습했으므로 이제 새로운 기술을 실무에 접목할 차례입니다. 학습한 내용을 유용하게 활용하여 최종 사용자가 있는 곳에서 대규모로 뛰어난 데이터 캡처 경험을 만들고 제공해 보십시오!

## 리소스

* [적응형 양식 핵심 구성 요소 소개](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html)

* [핵심 구성 요소를 사용하여 적응형 양식 만들기](https://experienceleague.corp.adobe.com/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-core-components/create-an-adaptive-form-on-forms-cs/creating-adaptive-form-core-components.html)

* [핵심 구성 요소 기반 AF의 스타일링 업데이트](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-core-components/create-an-adaptive-form-on-forms-cs/using-themes-in-core-components.html?lang=en)

* [Headless 적응형 양식](https://experienceleague.adobe.com/docs/experience-manager-headless-adaptive-forms/using/overview.html?lang=en)

* [Headless React 스타터 키트 사용](https://experienceleague.adobe.com/docs/experience-manager-headless-adaptive-forms/using/get-started/create-and-publish-a-headless-form.html?lang=en)
