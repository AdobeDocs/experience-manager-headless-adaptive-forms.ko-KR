---
title: AEM Forms as a Cloud Service에서 Headless 적응형 Forms 활성화
description: AEM Forms as a Cloud Service에서 Headless 적응형 양식을 활성화하는 단계별 안내서로, 환경에서 설정 및 활성화를 단순화합니다.
solution: Experience Manager Forms
feature: Adaptive Forms
topic: Headless
role: Admin
level: Beginner, Intermediate
contentOwner: Khushwant Singh
docset: CloudService
hide: true
exl-id: 7afff771-1296-4162-84c5-c8266b94af2f
source-git-commit: 3af67fd41cdd1e63a460e56ef1d273c90b3954d7
workflow-type: tm+mt
source-wordcount: '943'
ht-degree: 51%

---

# AEM Forms as a Cloud Service에서 Headless 적응형 Forms 활성화 {#enable-headless-adaptive-forms-on-aem-forms-cloud-service}

AEM Forms as a Cloud Service에서 Headless 적응형 Forms을 활성화하면 AEM Forms Cloud Service 인스턴스를 사용하여 Headless Forms을 만들고, 게시하고, 여러 채널에 전달할 수 있습니다. Headless Adaptive Forms를 사용하려면 적응형 양식 핵심 구성 요소 활성화 환경이 필요합니다.

## 고려 사항

* 새로운 AEM Forms as a Cloud Service 프로그램을 만들 때 [Headless 적응형 Forms이 이미 환경에 대해 활성화되어 있습니다](#are-adaptive-forms-core-components-enabled-for-my-environment).

* 핵심 구성 요소가 [활성화되지 않음](#enable-components)인 이전 Forms as a Cloud Service 프로그램을 실행 중인 경우 먼저 [적응형 Forms 핵심 구성 요소 종속성 추가](#enable-headless-adaptive-forms-for-an-aem-forms-as-a-cloud-service-environment)를 Cloud Service 저장소에 하십시오. 업데이트된 저장소를 각 환경에 배포하여 Headless 적응형 양식을 활성화합니다.

* Cloud Service 환경에서 [핵심 구성 요소 기반 적응형 양식을 만들 수](create-a-headless-adaptive-form.md)을(를) 이미 허용하고 있는 경우 Headless 적응형 양식이 자동으로 활성화됩니다. 그런 다음 이러한 양식을 모바일, 웹, 기본 앱 또는 이를 필요로 하는 모든 서비스에 Headless 환경으로 제공할 수 있습니다.

>[!NOTE]
>
>
> Adobe은 AEM Forms as a Cloud Service 환경에서 Headless Adaptive Forms을 활성화하지 않고도 개발자가 Headless Adaptive Forms 개발을 빠르게 시작할 수 있도록 적응형 Forms [스타터 키트(React 앱)](create-and-publish-a-headless-form.md)을 제공합니다. [Headless 양식 개발을 통한 빠른 실습](create-and-publish-a-headless-form.md) 후에 Forms as a Cloud Service 환경에서 Headless 적응형 Forms을 활성화할 수 있습니다.

## AEM Forms as a Cloud Service 환경을 위한 Headless 적응형 Forms 활성화

AEM Forms as a Cloud Service 환경을 위한 Headless 적응형 Forms을 활성화하려면 나열된 순서로 다음 단계를 수행하십시오

<!-- Missing image ALT tag -->
![](/help/assets/enable-headless-adaptive-forms-on-aem-forms-cloud-service.png)


## &#x200B;1. AEM Forms as a Cloud Service Git 저장소 복제 {#clone-git-repository}

1. [Cloud Manager](https://my.cloudmanager.adobe.com/)에 로그인하고 조직과 프로그램을 선택합니다.

1. **프로그램 개요** 페이지에서 **파이프라인** 카드로 이동합니다.

1. Git 저장소에 액세스하고 관리하려면 **저장소 정보 액세스** 단추를 클릭하십시오. 페이지에는 다음 정보가 포함됩니다.

   * Cloud Manager Git 저장소의 URL.
   * Git 저장소(사용자 이름 및 암호) 및 Git 사용자 이름의 자격 증명입니다.

   **암호 생성**&#x200B;을 클릭하여 암호를 보거나 생성합니다.

1. 로컬 컴퓨터에서 터미널 또는 명령 프롬프트를 열고 다음 명령을 실행합니다.

   ```Shell
   git clone [Git Repository URL]
   ```

   메시지가 표시되면 자격 증명을 제공합니다. 저장소를 로컬 컴퓨터에 복제합니다.


## &#x200B;2. Git 저장소에 적응형 Forms 핵심 구성 요소 종속성 추가 {#add-adaptive-forms-core-components-dependencies}

1. 일반 텍스트 코드 편집기에서 Git 저장소 폴더를 엽니다. 예: VS 코드.
1. 편집할 `[AEM Repository Folder]\pom.xml` 페이지를 엽니다.
1. `core.forms.components.version`, `core.forms.components.af.version` 및 `core.wcm.components.version` 구성 요소의 버전을 [핵심 구성 요소 설명서](https://github.com/adobe/aem-core-forms-components)에 지정된 버전으로 바꿉니다. 구성 요소가 없으면 이러한 구성 요소를 추가합니다.

   ```XML
   <!-- Replace the version with the latest released version at https://github.com/adobe/aem-core-forms-components/tags -->
   
   <properties>
       <core.forms.components.version>2.0.14</core.formscomponents.version>
       <core.forms.components.af.version>2.0.14</core.forms.components.af.version>  
       <core.wcm.components.version>2.21.2</core.wcmcomponents.version>
   </properties>
   ```

   ![최신 버전의 양식 핵심 구성 요소 멘션](/help/assets/latest-forms-component-version.png)

1. `[AEM Repository Folder]\pom.xml` 파일의 종속성 섹션에서 다음 종속성을 추가하고 파일을 저장합니다.

   ```XML
       <!-- WCM Core Component Examples Dependencies -->
           <dependency>
               <groupId>com.adobe.cq</groupId>
               <artifactId>core.wcm.components.examples.ui.apps</artifactId>
               <type>zip</type>
               <version>${core.wcm.components.version}</version>
           </dependency>
           <dependency>
               <groupId>com.adobe.cq</groupId>
               <artifactId>core.wcm.components.examples.ui.content</artifactId>
               <type>zip</type>
               <version>${core.wcm.components.version}</version>
           </dependency>
           <dependency>
               <groupId>com.adobe.cq</groupId>
               <artifactId>core.wcm.components.examples.ui.config</artifactId>
               <version>${core.wcm.components.version}</version>
               <type>zip</type>
           </dependency>    
           <!-- End of WCM Core Component Examples Dependencies -->
           <!-- Forms Core Component Dependencies -->
           <dependency>
               <groupId>com.adobe.aem</groupId>
               <artifactId>core-forms-components-core</artifactId>
               <version>${core.forms.components.version}</version>
           </dependency>
           <dependency>
               <groupId>com.adobe.aem</groupId>
               <artifactId>core-forms-components-apps</artifactId>
               <version>${core.forms.components.version}</version>
               <type>zip</type>
           </dependency>
           <dependency>
               <groupId>com.adobe.aem</groupId>
               <artifactId>core-forms-components-af-core</artifactId>
               <version>${core.forms.components.version}</version>
           </dependency>
           <dependency>
               <groupId>com.adobe.aem</groupId>
               <artifactId>core-forms-components-af-apps</artifactId>
               <version>${core.forms.components.version}</version>
               <type>zip</type>
           </dependency>
           <dependency>
               <groupId>com.adobe.aem</groupId>
               <artifactId>core-forms-components-examples-apps</artifactId>
               <type>zip</type>
               <version>${core.forms.components.version}</version>
           </dependency>
           <dependency>
               <groupId>com.adobe.aem</groupId>
               <artifactId>core-forms-components-examples-content</artifactId>
               <type>zip</type>
               <version>${core.forms.components.version}</version>
           </dependency>
   <!-- End of AEM Forms Core Component Dependencies -->
   ```

1. 편집할 `[AEM Repository Folder]/all/pom.xml` 페이지를 엽니다. `<embeddeds>` 섹션에서 다음 종속성을 추가하고 파일을 저장합니다.

   ```XML
   <!-- WCM Core Component Examples Dependencies -->
   
   <!-- inside plugin config of filevault-package-maven-plugin -->  
   <!-- embed wcm core components examples artifacts -->
   
   <embedded>
       <groupId>com.adobe.cq</groupId>
       <artifactId>core.wcm.components.examples.ui.apps</artifactId>
       <type>zip</type>
       <target>/apps/${appId}-vendor-packages/content/install</target>
   </embedded>
   <embedded>
       <groupId>com.adobe.cq</groupId>
       <artifactId>core.wcm.components.examples.ui.content</artifactId>
       <type>zip</type>
       <target>/apps/${appId}-vendor-packages/content/install</target>
   </embedded>
   <embedded>
       <groupId>com.adobe.cq</groupId>
       <artifactId>core.wcm.components.examples.ui.config</artifactId>
       <type>zip</type>
       <target>/apps/${appId}-vendor-packages/content/install</target>
   </embedded>
   <!-- embed forms core components artifacts -->
   <embedded>
       <groupId>com.adobe.aem</groupId>
       <artifactId>core-forms-components-af-apps</artifactId>
       <type>zip</type>
       <target>/apps/${appId}-vendor-packages/application/install</target>
   </embedded>
   <embedded>
       <groupId>com.adobe.aem</groupId>
       <artifactId>core-forms-components-af-core</artifactId>
       <target>/apps/${appId}-vendor-packages/application/install</target>
   </embedded>
   <embedded>
       <groupId>com.adobe.aem</groupId>
       <artifactId>core-forms-components-examples-apps</artifactId>
       <type>zip</type>
       <target>/apps/${appId}-vendor-packages/content/install</target>
   </embedded>
   <embedded>
       <groupId>com.adobe.aem</groupId>
       <artifactId>core-forms-components-examples-content</artifactId>
       <type>zip</type>
       <target>/apps/${appId}-vendor-packages/content/install</target>
   </embedded>
   ```

   >[!NOTE]
   >
   >
   >  `${appId}`를 appId로 바꿉니다.
   >
   >  `[AEM Repository Folder]/all/pom.xml` 파일에서 `${appId}`를 찾으려면 `-packages/application/install` 용어를 검색합니다. `-packages/application/install` 용어 앞의 텍스트는 `${appId}`입니다. 예: 다음 코드 `myheadlessform`은 `${appId}`입니다.
   >
   >   ```
   >             <embedded>
   >                     <groupId>com.myheadlessform</groupId>
   >                     <artifactId>myheadlessform.ui.apps<artifactId>
   >                     <type>zip</type>
   >                   <target>/apps/myheadlessform-packages/application install</target>
   >             </embedded>
   >   ```

1. `[AEM Repository Folder]/all/pom.xml` 파일의 `<dependencies>` 섹션에서 다음 종속성을 추가하고 파일을 저장합니다.

   ```XML
           <!-- Other existing dependencies -->
           <!-- wcm core components examples dependencies -->
           <dependency>
               <groupId>com.adobe.cq</groupId>
               <artifactId>core.wcm.components.examples.ui.apps</artifactId>
               <type>zip</type>
           </dependency>
           <dependency>
               <groupId>com.adobe.cq</groupId>
               <artifactId>core.wcm.components.examples.ui.config</artifactId>
               <type>zip</type>
               </dependency>
           <dependency>
               <groupId>com.adobe.cq</groupId>
               <artifactId>core.wcm.components.examples.ui.content</artifactId>
               <type>zip</type>
           </dependency>
               <!-- forms core components dependencies -->
           <dependency>
               <groupId>com.adobe.aem</groupId>
               <artifactId>core-forms-components-af-apps</artifactId>
               <type>zip</type>
           </dependency>
           <dependency>
               <groupId>com.adobe.aem</groupId>
               <artifactId>core-forms-components-examples-apps</artifactId>
               <type>zip</type>
           </dependency>
               <dependency>
               <groupId>com.adobe.aem</groupId>
               <artifactId>core-forms-components-examples-content</artifactId>
               <type>zip</type>
           </dependency>
   ```

1. 편집할 `[AEM Repository Folder]/ui.apps/pom.xml`을 엽니다. `af-core bundle` 종속성을 추가하고 파일을 저장합니다.

   ```XML
       <dependency>
       <groupId>com.adobe.aem</groupId>
       <artifactId>core-forms-components-af-core</artifactId>
       </dependency>
   ```

   >[!NOTE]
   >
   >다음 적응형 양식 핵심 구성 요소 아티팩트가 프로젝트에 포함되지 않았는지 확인합니다.
   >
   > `<dependency>`
   >
   >   `<groupId>com.adobe.aem</groupId>`
   >   `<artifactId>core-forms-components-apps</artifactId>`
   >
   > `</dependency>`
   >
   > 및
   >
   > `<dependency>`
   >
   >   `<groupId>com.adobe.aem</groupId>`
   >   `<artifactId>core-forms-components-core</artifactId>`
   >
   > `</dependency>`


1. 파일을 저장하고 닫습니다.

## &#x200B;3.  최신 버전의 Forms 핵심 구성 요소를 포함하도록 프로젝트를 업데이트합니다.

1. 편집할 [AEM Archetype 프로젝트 폴더]/pom.xml을 엽니다.


1. 파일을 저장하고 닫습니다.

## &#x200B;4. Git 저장소에 업데이트를 커밋하고 파이프라인을 실행하여 저장소를 배포합니다 {#Commit-the-updates-to-your-git-repository}

1. Git 저장소에 코드를 커밋하려면 다음을 수행하십시오.
   1. 터미널 또는 명령 프롬프트를 엽니다.
   1. `[AEM Repository Folder]`로 이동하고 나열된 순서대로 다음 명령을 실행합니다.

      ```Shell
      git add pom.xml
      git add all/pom.xml
      git add ui.apps/pom.xml
      git commit -m "Added dependencies for Adaptive Forms Core Components"
      git push origin
      ```

1. 파일이 Git 저장소에 커밋되면 [파이프라인을 실행합니다](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-manager/content/using/code-deployment).

   파이프라인 실행이 성공하면 해당 환경에 대해 적응형 Forms 핵심 구성 요소가 활성화됩니다. 또한 적응형 양식(핵심 구성 요소) 템플릿 및 Canvas 3.0 테마가 Forms as a Cloud Service 환경에 추가되면 핵심 구성 요소 기반 적응형 양식을 사용자 정의하고 만들 수 있는 옵션이 제공됩니다.


## 자주 묻는 질문 {#faq}

### 핵심 구성 요소란 무엇입니까? {#core-components}

[핵심 구성 요소](https://experienceleague.adobe.com/ko/docs/experience-manager-core-components/using/introduction)는 AEM에서 개발 시간을 단축하고 웹 사이트의 유지 관리 비용을 절감할 수 있는 표준화된 웹 콘텐츠 관리(WCM) 구성 요소입니다.

### 핵심 구성 요소를 활성화하는 경우 추가되는 모든 기능은 무엇입니까? {#core-components-capabilities}

내 환경에 맞는 적응형 양식 핵심 구성 요소가 활성화되면 빈 핵심 구성 요소 기반 적응형 양식 템플릿 및 Canvas 3.0 테마가 해당 환경에 추가됩니다. 내 환경에 맞는 적응형 양식 핵심 구성 요소가 활성화되면 다음과 같은 작업을 수행할 수 있습니다.

* 적응형 Forms 기반의 핵심 구성 요소 만들기
* 적응형 양식 템플릿을 기반으로 핵심 구성 요소를 만듭니다.
* 적응형 양식 템플릿을 기반으로 핵심 구성 요소에 대한 사용자 지정 테마를 만듭니다.
* 모바일, 웹, 기본 앱 및 양식의 Headless 표시가 필요한 서비스와 같은 채널에 핵심 구성 요소 기반 적응형 양식의 JSON 표시를 제공합니다.

### 내 환경에 맞는 적응형 양식 핵심 구성 요소가 활성화되어 있습니까? {#enable-components}

내 환경에 맞는 적응형 양식 핵심 구성 요소가 활성화되어 있는지 확인하려면:

1. [AEM Forms as a Cloud Service 저장소 복제](#1-clone-your-aem-forms-as-a-cloud-service-git-repository).

1. `[AEM Repository Folder]/all/pom.xml` AEM Forms Cloud Service Git 저장소 파일을 엽니다.

1. 다음 종속성을 검색합니다.

   * core-forms-components-af-core
   * core-forms-components-core
   * core-forms-components-apps
   * core-forms-components-af-apps
   * core-forms-components-examples-apps
   * core-forms-components-examples-content


   ![all/pom.xml에서 core-forms-components-af-core 아티팩트 찾기](/help/assets/enable-headless-adaptive-forms-on-aem-forms-cloud-service-locate-core-af-artifact.png)

   종속성이 있는 경우 내 환경에 맞는 적응형 양식 핵심 구성 요소가 활성화됩니다.
