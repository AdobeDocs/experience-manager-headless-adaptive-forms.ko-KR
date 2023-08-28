---
title: 핵심 구성 요소 및 Headless를 사용하여 매력적인 양식 작성
seo-title: Build Engaging Forms Using Core Components and Headless
description: 핵심 구성 요소 및 Headless를 사용하여 매력적인 양식 작성
seo-description: Build Engaging Forms Using Core Components and Headless
solution: Experience Manager Forms
feature: Adaptive Forms
topic: Headless
role: Admin, Developer
level: Beginner, Intermediate
topic-tags: develop
hide: true
exl-id: 46df943c-0622-4b3b-a802-85c39ac6a734
source-git-commit: 47ac7d03c8c4fa18ac3bdcef04352fdd1cad1b16
workflow-type: tm+mt
source-wordcount: '2189'
ht-degree: 62%

---

# 핵심 구성 요소 및 Headless를 사용하여 매력적인 양식 작성 AEM 6.5 Forms의 적응형 Forms {#build-engaging-forms-using-core-components-and-headless}

## 랩 개요 {#lab-overview}

이 실습 랩에서는 다음과 같은 사항을 알아봅니다.

AEM Forms을 사용하여 AEM Sites과 일치하는 최신 핵심 구성 요소를 사용하여 적응형 Forms을 손쉽게 만들고, 적응형 Forms을 headless 양식으로 웹, 모바일 및 채팅에 전달하여 옴니채널 데이터 캡처 경험을 활성화하는 방법. 또한 스타일링, 사용자 정의 및 프론트엔드 개발에 대한 모범 사례를 살펴봅니다.

## 핵심 사항 {#key-takeaways}

* **비즈니스 민첩성**: 비즈니스 사용자로서 여러 채널의 양식 경험을 쉽게 작성할 수 있습니다.

* **프론트엔드 개발자의 능력**: 프론트엔드 개발자로서 Headless 양식을 사용하여 최종 사용자 경험을 제어할 수 있습니다.

* **개발자 속도**: 개발자로서 Sites 및 Forms 구성 요소를 쉽고 일관되게 사용자 정의할 수 있습니다.

## 시작하기 전 {#pre-requisites}

랩에서 이 핸즈를 사용하려면:

* 설치 [git 최신 릴리스](https://git-scm.com/downloads). Git을 처음 사용하는 경우 다음을 참조하십시오 [Git 설치](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git).

* 설치 [Node.js 16.13.0 이상](https://nodejs.org/en/download/). Node.js를 처음 사용하는 경우 [Node.js 설치 방법](https://nodejs.dev/en/learn/how-to-install-nodejs).

* [Headless 적응형 Forms 활성화](enable-headless-adaptive-forms-and-core-components.md) AEM 6.5 Forms 환경에서.

* 설치 [Microsoft Visual Studio 코드](https://code.visualstudio.com/download) 또는 일반 텍스트 편집기입니다. 문서의 예제에서는 Microsoft Visual Studio 코드를 사용합니다.

## 수업 1 {#lesson-1}

### 목표 {#lesson-1-objectives}

AEM 6.5 Forms 환경에 대해 숙지하십시오.

### 수업 컨텍스트 {#lesson-1-context}

이 단원에서는 사용자 인터페이스를 탐색하여 AEM 6.5 Forms에 대해 숙지합니다.

### 연습 {#lesson-1-excercise}

1. 브라우저를 열고 작성자 환경의 URL을 입력합니다. 예:
   [https://localhost:4502](https://localhost:4502).

1. 로그인한 후 AEM Forms UI로 이동합니다. **Forms**&#x200B;를 클릭합니다.

   ![](/help/assets/screenshot2028113829.png){width="50%" align="left"}

1. **양식 및 문서**&#x200B;를 클릭합니다. 환경 설정 또는 정보와 관련된 모든 팝업을 닫습니다.

   ![](/help/assets/screenshot2028113929.png){width="50%" align="left"}

   사용 가능한 모든 양식이 표시됩니다.

   ![](/help/assets/screenshot2028114029.png){width="50%" align="left"}

## 수업 2

### 목표

최신 핵심 구성 요소를 사용하여 적응형 양식을 작성하고 양식을 구성하고 제출합니다.

### 수업 컨텍스트

이 단원에서 비즈니스 사용자는 표준화된 기본 핵심 구성 요소와 함께 적응형 Forms 편집기를 사용하여 웹, 모바일 및 채팅과 같은 여러 채널에 대한 적응형 양식을 작성하고 데이터를 캡처합니다.

### 연습

1. 양식의 제출 엔드포인트를 만듭니다.

   1. 새 브라우저 탭에서 <https://requestbin.com/>을 엽니다.
      ![](/help/assets/screenshot2028114329.png){width="50%" align="left"}

   1. **공개 bin 만들기**를 클릭하고 엔드포인트 URL을 복사합니다.
      ![](/help/assets/screenshot202023-03-0120at206.10.0020pm.png){width="50%" align="left"}

   이 특정 끝점은 데이터를 제출하고 볼 수 있는 예제입니다. 실제 프로덕션에서는 자체 엔드포인트 또는 데이터 소스를 사용하여 캡처된 데이터를 저장합니다.

1. 적응형 양식 작성:

   1. 단원 1에 사용된 브라우저 탭에서 AEM Forms 웹 인터페이스로 이동하여 로 이동합니다. **Forms** > **Forms 및 문서**.

   1. **만들기**를 클릭하고 적응형 양식을 선택합니다.
      ![](/help/assets/creating-adaptive-form-6-5.png){width="50%" align="left"}

   1. 다음 항목 선택 **핵심 구성 요소가 포함된 빈 항목** 아래 표시된 템플릿 선택 화면에서 템플릿을 선택하고 **다음**.
      ![](/help/assets/creating-adaptive-form-6-5-select-blank-template.png){width="50%" align="left"}

   1. 지정 `Contact us` (으)로 **제목** 형식. 다음을 확인합니다. **이름** 이(가) `contact-us`.
      ![](/help/assets/creating-adaptive-form-65-specify-title.png){width="50%" align="left"}

   1. **만들기**&#x200B;를 클릭합니다. 대화 상자가 표시됩니다.

   1. 대화 상자에서 **편집**. 양식이 적응형 양식 편집기에서 열립니다. 환경 설정 또는 정보와 관련된 모든 팝업이나 대화 상자를 닫습니다.

   1. 구성 요소 브라우저를 열고 패널 구성 요소를 화면 가운데로 끌어서 놓습니다.

      ![](/help/assets/lab65-add-panel.png){width="50%" align="left"}

   1. 구성 요소 브라우저에서 구성 요소를 드래그 앤 드롭하여 다음과 같이 양식을 만듭니다.

      ![](/help/assets/contact-us-headless-adaptive-form.png){width="50%" align="left"}


   1. 컨텐츠 브라우저를 열고 가이드 컨테이너 속성 아이콘을 클릭한 다음 **제출** 탭. 다음 항목 선택 **REST 끝점에 제출** 작업 제출, 다음 항목 선택 **POST 요청 활성화** 옵션을 선택하고 의 2단원에서 만든 REST 끝점을 지정합니다. **POST 요청용 URL** 텍스트 상자를 클릭하고 **완료** 아이콘.

      ![](/help/assets/configure-submit-action.png){width="50%" align="left"}

1. 적응형 양식 게시:

   1. AEM UI를 열고 다음으로 이동 **Forms** > **Forms 및 문서**. 이전 단계에서 만든 양식을 선택하고 **게시**.

   1. 에셋 게시 대화 상자에서 **게시**. 성공 메시지가 표시됩니다.

## 수업 3

### 목표

프론트엔드 개발 모범 사례를 사용하여 스타일을 업데이트합니다.

### 수업 컨텍스트

이 단원에서는 프론트엔드 개발자로서 이전에 만든 적응형 양식의 스타일을 쉽게 업데이트할 수 있는 방법에 대해 알아봅니다.

### 연습

테마의 로컬 저장소 설정:

1. 관리자 권한으로 명령 프롬프트 또는 셸 열기.

   ![](/help/assets/screenshot2028115829.png){width="50%" align="left"}

1. 명령 프롬프트에서 다음 명령을 사용하여 `c:\git` 폴더로 이동합니다.

   ```Shell
   cd git
   ```

   폴더가 없으면 `md git` 생성 명령입니다.

1. 다음 명령을 사용하여 테마 프론트엔드 코드를 복제합니다.

   ```Shell
   git clone -b WKND https://github.com/adobe/aem-forms-theme-canvas
   ```

1. 나열된 순서대로 다음 명령을 사용하여 **aem-forms-theme-canvas** 디렉터리로 이동하고 Visual Studio Code를 엽니다.

   ```Shell
   cd aem-forms-theme-canvas
   code .
   ```

   ![](/help/assets/screenshot2028126029.png){width="50%" align="left"}

1. **상위 폴더에 있는 모든 파일의 작성자 신뢰**&#x200B;를 선택하고 **예, 작성자를 신뢰함**&#x200B;을 클릭합니다.

   ![](/help/assets/screenshot2028116229.png){width="50%" align="left"}

1. 이름 바꾸기 `env_template` 파일을 .env로 변환  파일 이름을 바꾸려면 **env_template** 파일을 마우스 오른쪽 버튼으로 클릭하고 **이름 바꾸기** 옵션을 선택합니다.

   ![](/help/assets/screenshot2028116429.png){width="30%" align="left"}

   </br>

   ![](/help/assets/screenshot2028116529.png){width="50%" align="left"}

1. .env 파일의 변수에 대해 다음 값을 설정하고 파일을 저장합니다.

   * **AEM_URL**: 의 URL 지정 **게시** 인스턴스. 예, `https://localhost:4502/`

   * **AEM_ADAPTIVE_FORM**: 양식 이름을 지정합니다. (예: `contact-us`)

   </br>

   ![](/help/assets/lab65-theme-environment-variable.png)


1. 명령 프롬프트 창에서 다음 명령을 실행합니다.

   ```Shell
   npm install
   ```

   ![](/help/assets/screenshot2028117029.png)

   >[!NOTE]
   >
   > * `npm notice Run npm nstall -g npm@9.6.0` 명령을 통해 npm을 업데이트하라는 메시지가 표시되면 메시지를 무시합니다.
   > * 통합 문서에서 지시하지 않는 한 다른 npm 명령은 실행하지 않습니다.

1. 이제 다음 명령을 실행하여 양식을 미리 봅니다.

   ```Shell
   npm run live
   ```

   ![](/help/assets/screenshot2028117229.png)

   위 명령이 실행되면 `webpack compiled` 메시지를 기다립니다. 양식이 브라우저 탭에 표시됩니다.

   >[!NOTE]
   >
   >`npm run live` 명령을 실행한 후 3~4분 이상 브라우저에 빈 화면이 표시되는 경우 브라우저 URL의 `localhost`를 127.0.0.1로 변경하고 **Enter**&#x200B;를 누릅니다.


   ![](/help/assets/contact-us-headless-adaptive-form-with-canvas-theme.png){width="50%" align="left"}


1. Visual Studio Code에서 `PROJECT\src\site\_variables.scss` 파일을 엽니다. `$error` 색상은 빨간색입니다.

   ![](/help/assets/screenshot2028120729.png){width="50%" align="left"}

1. 브라우저에서 양식을 제출하면 **이름** 필드에 빨간색이 표시됩니다.

   ![](/help/assets/error-color-before.png)

1. **$error** 색상을 **#5736eb**&#x200B;로 설정하고 파일을 저장합니다.

1. 브라우저를 새로 고치고 양식을 제출합니다. 이에 따라 이름 필드의 오류 색상이 변경됩니다.

   ![](/help/assets/error-color-after.png)

1. 명령 프롬프트에서 **CTRL+C**&#x200B;를 누르고 **Y**&#x200B;를 입력한 다음 **Enter** 키를 눌러 npm 프로세스를 종료합니다. 다음 연습 세트와 충돌하지 않도록 npm 서버를 정지하는 것이 중요합니다.
1. Visual Studio Code 및 명령 프롬프트 창을 닫습니다.

## 수업 4

### 목표

양식을 웹/모바일 및 기타 인터페이스에 Headless 양식으로 렌더링합니다.

### 수업 컨텍스트

이 단원에서는 프론트엔드 개발자로서 React 스펙트럼 디자인 프레임워크를 사용하여 이전에 만든 적응형 양식을 Headless 양식으로 렌더링할 수 있는 방법에 대해 알아봅니다.

### 연습

React 스타터 프로젝트를 사용하여 로컬 저장소 설정:

1. 관리자 권한을 사용해 명령 프롬프트를 엽니다.

   ![](/help/assets/screenshot2028115829.png){width="30%" align="left"}

1. 명령 프롬프트에서 다음 명령을 사용하여 `c:\git` 폴더로 이동합니다.

   ```Shell
   cd git
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

게시 환경에서 호스팅된 양식을 렌더링하려면 다음을 수행하십시오.

1. env_template 파일의 이름을 .env 파일로 바꿉니다. 이름을 바꾸려면 **env_template** 파일을 마우스 오른쪽 버튼으로 클릭하고 **이름 바꾸기** 옵션을 선택합니다.

   ![](/help/assets/screenshot2028117629.png){width="30%" align="left"}

   ![](/help/assets/screenshot2028117729.png)

1. .env 파일의 변수에 대해 다음 값을 설정합니다. 변수를 업데이트한 후 파일을 저장합니다.

   * **AEM_URL**: 게시 환경의 URL을 지정합니다. 예, `https://localhost:4503/`

   * **AEM_FORM_PATH**: 이전 단원에서 만든 적응형 양식의 경로를 지정합니다. 예, `/content/forms/af/contact-us/`

   </br>

   ![](/help/assets/lab65-starter-kit-environment-variable.png)

1. 명령 창을 열고 현재 위치가 **react-starter-kit-aem-headless-forms** 디렉터리인지 확인한 후 다음 명령을 실행합니다.

   ```Shell
   npm install
   ```

   ![](/help/assets/screenshot2028118029.png)


1. 명령 프롬프트 창에서 다음 명령을 실행합니다.

   ```Shell
   npm start
   ```

   ![](/help/assets/lab65-starter-kit-start.png)

   위 명령은 React 스펙트럼 프론트엔드 라이브러리를 사용하여 Headless 방식으로 AEM에서 가져온 양식 정의를 렌더링하는 로컬 개발 서버를 시작합니다.

   >[!NOTE]
   >
   > 
   > `npm start` 명령을 실행한 후 3~4분 이상 브라우저에 빈 화면이 표시되는 경우 브라우저 URL의 `localhost`를 127.0.0.1로 변경하고 **Enter**&#x200B;를 누릅니다.

   ![](/help/assets/headless-adaptive-form-lab.png)

비즈니스 사용자로서 서버의 양식을 변경하고 자동으로 Headless 양식에 반영된 변경 사항을 확인해 보겠습니다.

1. 브라우저에서 AEM Forms 관리 인터페이스를 엽니다. 예를 들어, [http://localhost:4502/aem/forms.html/content/dam/formsanddocuments](http://localhost:4502/aem/forms.html/content/dam/formsanddocuments).

1. 다음 항목 선택 **연락처** 양식 및 클릭 **편집.** 적응형 Forms 편집기에서 양식이 열립니다.


1. 다음 항목 선택 **연락처 번호** 필드를 클릭하고 **편집 아이콘(연필 아이콘)** 을 클릭합니다. 팝업 도구 모음이 보이지 않으면 오른쪽 상단에서 **미리보기** 버튼 왼쪽에 있는 **편집** 버튼을 클릭하여 편집 모드로 전환합니다.

   ![](/help/assets/change-field-title.png){width="50%" align="left"}

1. 레이블을 다음으로 변경 **모바일 번호**. 양식의 빈 공간을 클릭하면 양식의 변경 사항이 저장됩니다.

변경 사항을 게시 환경에 전파하기 위해 업데이트된 양식을 게시해 보겠습니다.

1. AEM Forms 관리 인터페이스 탭에서 연락처 양식을 선택하고 **게시 취소**. **게시 취소** 버튼이 표시되지 않으면 3단계로 건너뛰어 변경 사항을 직접 게시합니다.


1. **게시 취소**&#x200B;를 클릭합니다. 각 대화 상자에서 **닫기**&#x200B;를 클릭합니다.

1. 브라우저를 새로 고친 후 연락처 양식을 선택하고 을(를) 클릭합니다. **게시**.


1. **게시**&#x200B;를 클릭합니다. 각 대화 상자에서 **닫기**&#x200B;를 클릭합니다.

1. Headless 양식이 표시된 브라우저 탭을 새로 고칩니다. 연락처 번호 레이블이 모바일 번호로 변경되었습니다.

   ![](/help/assets/headless-adaptive-form.png)

1. **react-starter-kit-aem-headless-forms** 프로젝트를 시작하는 데 사용된 명령 프롬프트 창을 열고 **CTRL+C**&#x200B;를 누른 후 **Y**&#x200B;를 입력하고 Enter 키를 눌러 npm 프로세스를 종료합니다. 다음 연습 세트와 충돌하지 않도록 npm 서버를 정지하는 것이 중요합니다.

1. Visual Studio Code 및 명령 프롬프트 창을 닫습니다.


## 수업 5

### 목표

Google Material UI를 사용하여 양식을 Headless 양식으로 렌더링

### 수업 컨텍스트

이 단원에서는 프론트엔드 개발자로서 Google Material UI를 사용하여 이전에 headless 양식으로 만든 적응형 양식을 렌더링하는 방법을 알아봅니다.

### 연습

Material UI 스타터 프로젝트를 사용하여 로컬 저장소 설정:

1. 관리자 권한을 사용해 명령 프롬프트를 엽니다.

   ![](/help/assets/screenshot2028115829.png){width="30%" align="left"}

1. 명령 프롬프트에서 다음 명령을 사용하여 `c:\git` 폴더로 이동합니다.

   ```Shell
   cd git
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

게시 환경에서 호스팅된 양식을 렌더링하려면 다음을 수행하십시오.

1. **env_template** 파일의 이름을 **.env** 파일로 바꿉니다. 이름을 바꾸려면 **env_template** 파일을 마우스 오른쪽 버튼으로 클릭하고 **이름 바꾸기**&#x200B;를 선택합니다.

   ![](/help/assets/screenshot2028126629.png){width="30%" align="left"}

1. .env 파일의 변수에 대해 다음 값을 설정합니다. 변수를 업데이트한 후 파일을 저장합니다. **CTRL + S** 스위치 조합을 사용하여 파일을 저장합니다.

   * **AEM_URL**: 게시 환경의 URL을 지정합니다. 예를 들어, [https://localhost:4503](https://localhost:4503)

   * **AEM_FORM_PATH**: 이전 단원에서 만든 적응형 양식의 경로를 지정합니다. 예: /content/forms/af/contact-us/


1. 명령 창을 열고 현재 위치가 **react-starter-kit-aem-headless-forms** 디렉터리인지 확인한 후 다음 명령을 실행합니다.

   ```Shell
   npm install
   ```

   ![](/help/assets/screenshot2028127029.png)

1. 명령 프롬프트 창에서 다음 명령을 실행합니다.

   ```Shell
   npm start
   ```

   ![](/help/assets/lab65-mui-starter-kit-start.png)

   위 명령은 로컬 개발 서버를 시작하고 Google Material UI 프론트엔드 라이브러리를 사용하여 Headless 방식으로 AEM에서 가져온 양식 정의를 렌더링합니다.

   >[!NOTE]
   >
   >`npm start` 명령을 실행한 후 3~4분 이상 브라우저에 빈 화면이 표시되는 경우 브라우저 URL의 `localhost`를 127.0.0.1로 변경하고 **Enter**&#x200B;를 누릅니다.

   ![](/help/assets/google-mui-form.png)

## 수업 6

### 목표

Material UI 구성 요소 변형을 사용하여 Headless 형태의 대체 디자인 만들기

### 수업 컨텍스트

이 단원에서는 프론트엔드 개발자로서 비즈니스 사용자가 이전에 만든 적응형 양식에 대해 재료 UI를 사용하여 다양한 구성 요소의 대체 표현을 만드는 방법을 알아봅니다.

### 연습

Headless 프로젝트의 구성 요소 변형을 업데이트합니다. Material UI 텍스트 입력 구성 요소의 변형을 `OutlinedInput`으로 변경하려면 다음과 같이 합니다.

1. Visual Code에서 `src/components/textinput/index.tsx`에 있는 `index.tsx` 파일을 열어 텍스트 입력 구성 요소로 이동합니다.

1. 코드 104행의 시작 부분에 `//`를 추가합니다. 이렇게 하면 줄이 주석으로 변환됩니다.

   ```Shell
   //const Cmp = \'outlined\' === appliedCssClassNames ? OutlinedInput: Input;
   ```

1. 구성 요소의 다른 변형을 사용하고 파일을 저장하려면 105행에 다음을 추가합니다. **CTRL + S** 스위치 조합을 사용하여 파일을 저장합니다.

   ```Shell
   const Cmp = OutlinedInput;
   ```

   ![](/help/assets/aem65-lab-code-update.png)

   &#39;OutlinedInput&#39; 변형에 올바른 대소문자를 사용하는 것이 필수적입니다. 그렇게 하지 않으면 컴파일이 실패합니다. 로컬 개발 환경 컴파일은 명령 프롬프트에서 자동으로 시작됩니다. 다음 메시지가 나타날 때까지 기다립니다

   `webpack 5.75.0 compiled with 3 warnings in 6659 ms`
   `inside proxy req`
   `setting new origin header`

1. 브라우저가 자동으로 새로 고쳐지지 않으면 브라우저를 새로 고쳐 텍스트 입력 구성 요소가 다른 변형을 사용하는지 확인합니다.

   ![](/help/assets/screenshot2028127729.png){width="50%" align="left"}


   이 변경 사항은 AEM Forms Server의 양식 정의를 변경하지 않고 최종 사용자에게 발생하며, 고려 중인 Headless 채널에만 적용됩니다. 예: 이 랩의 웹 채널.

   ![](/help/assets/aem65-lab-mui-style-update.png)


1. Visual Studio Code 및 명령 프롬프트 창을 닫습니다.

## 자주 묻는 질문 (FAQ)

+++ 핵심 구성 요소를 공개적으로 사용할 수 있습니까?

예. 적응형 Forms 핵심 구성 요소는 AEM 6.5 Forms 및 Forms as Cloud Service에서 사용할 수 있습니다. 적응형 Forms 핵심 구성 요소를 사용하려면 AEM Forms 6.5 서비스 팩 16 이상이 필요합니다.

+++

+++ Headless 양식에 별도의 라이선스가 필요합니까?

아니요, Headless 양식은 동일한 라이선스 값 지표(양식 제출 수)를 사용합니다.

+++




## 다음 단계

Headless 양식을 사용하여 적응형 Forms을 구축하고 여러 채널에 전달하는 방법을 배웠으므로 이제 새로운 기술을 사용할 수 있습니다. 학습한 내용을 유용하게 활용하여 최종 사용자가 있는 곳에서 대규모로 뛰어난 데이터 캡처 경험을 만들고 제공해 보십시오!

## 리소스

* [적응형 양식 핵심 구성 요소 소개](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html)

* [핵심 구성 요소를 사용하여 적응형 양식 만들기](https://experienceleague.corp.adobe.com/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-core-components/create-an-adaptive-form-on-forms-cs/creating-adaptive-form-core-components.html)

* [핵심 구성 요소 기반 AF의 스타일링 업데이트](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-core-components/create-an-adaptive-form-on-forms-cs/using-themes-in-core-components.html?lang=en)

* [헤드리스 적응형 Forms](https://experienceleague.adobe.com/docs/experience-manager-headless-adaptive-forms/using/overview.html?lang=en)

* [Headless React 스타터 키트 사용](https://experienceleague.adobe.com/docs/experience-manager-headless-adaptive-forms/using/get-started/create-and-publish-a-headless-form.html?lang=en)
