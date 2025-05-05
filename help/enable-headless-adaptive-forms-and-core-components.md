---
title: AEM 6.5 Forms에서 Headless 적응형 Forms 활성화
seo-title: Step-by-Step Guide for enabling Headless Adaptive Forms on AEM 6.5 Forms
description: 단계별 안내서를 통해 AEM 6.5 Forms에서 Headless 적응형 양식을 활성화하는 방법을 알아보십시오. 튜토리얼에서는 이 강력한 기능을 웹 사이트에 쉽게 통합하고 사용자 경험을 개선할 수 있는 프로세스를 안내합니다.
seo-description: Learn how to enable headless adaptive forms on AEM 6.5 Forms with our step-by-step guide. Our tutorial walks you through the process, making it easy to integrate this powerful feature into your website and improve your user experience.
contentOwner: Khushwant Singh
role: Admin
exl-id: e1a5e7e0-d445-4cca-b8d7-693d9531f075
source-git-commit: 999c3d092d03d7a82363bc94ce79ceb33bf0df7e
workflow-type: tm+mt
source-wordcount: '743'
ht-degree: 13%

---

# AEM 6.5 Forms에서 Headless 적응형 Forms 활성화 {#enable-headless-adaptive-forms-on-aem-65-forms}

AEM 6.5 Forms 환경에서 Headless 적응형 Forms을 활성화하려면 AEM Archetype 41 이상 기반 프로젝트를 설정하고 모든 작성자 및 Publish 인스턴스에 배포합니다.

AEM Archetype 41 이상 기반 프로젝트를 AEM 6.5 Forms 인스턴스에 배포하면 [적응형 Forms 기반의 핵심 구성 요소를 만들 수 있습니다](create-a-headless-adaptive-form.md). 이러한 양식은 JSON 형식으로 표시되며 Headful과 Headless 적응형 Forms으로 사용되어 모바일, 웹 및 기본 앱을 비롯한 다양한 채널에서 보다 높은 유연성과 맞춤화를 가능하게 합니다.

## 사전 요구 사항 {#prerequisites}

AEM 6.5 Forms 환경에서 Headless 적응형 Forms을 활성화하기 전에

* [AEM 6.5 Forms 서비스 팩 16(6.5.16.0) 이상으로 업그레이드](https://experienceleague.adobe.com/docs/experience-manager-65/release-notes/aem-forms-current-service-pack-installation-instructions.html?lang=ko).

* [Apache Maven](https://maven.apache.org/download.cgi)의 최신 릴리스를 설치하십시오.

* 일반 텍스트 편집기를 설치합니다. 예를 들어 Microsoft Visual Studio Code입니다.

## 최신 AEM Archetype 기반 프로젝트 생성 및 배포

AEM Archetype 41 또는 [이후](https://github.com/adobe/aem-project-archetype) 기반 프로젝트를 만들고 모든 작성자 및 Publish 인스턴스에 배포하려면 다음을 수행하십시오.

1. 컴퓨터에 로그인하여 AEM 6.5 Forms 인스턴스를 호스팅 및 실행합니다.
1. 명령 프롬프트 또는 터미널을 엽니다.
1. 다음 명령을 실행하여 AEM Archetype 41 기반 프로젝트를 만듭니다.

   * Microsoft Windows

   ```Shell
      mvn -B org.apache.maven.plugins:maven-archetype-plugin:3.2.1:generate ^
      -D archetypeGroupId=com.adobe.aem ^
      -D archetypeArtifactId=aem-project-archetype ^
      -D archetypeVersion=41 ^
      -D appTitle="My Form" ^
      -D appId="myform" ^
      -D groupId="com.myform" ^
      -D includeFormsenrollment="y" ^
      -D aemVersion="6.5.15" 
   ```

   * Linux 또는 Apple macOS

   ```Shell
      mvn -B org.apache.maven.plugins:maven-archetype-plugin:3.2.1:generate \
      -D archetypeGroupId=com.adobe.aem \
      -D archetypeArtifactId=aem-project-archetype \
      -D archetypeVersion=41 \
      -D appTitle="My Form" \
      -D appId="myform" \
      -D groupId="com.myform" \
      -D includeFormsenrollment="y" \
      -D aemVersion="6.5.15" 
   ```

   위의 명령을 실행할 때는 다음 사항을 고려해야 합니다.

   * appTitle, appId 및 groupId를 포함하여 환경에 대한 특정 값을 반영하도록 명령을 업데이트합니다. 또한 includeFormsenrollment의 값을 &#39;y&#39;로 설정합니다. Forms 포털을 사용하는 경우 _includeExamples=y_ 옵션을 설정하여 프로젝트에 Forms 포털 핵심 구성 요소를 포함합니다.

   * &#39;aemVersion&#39;을 6.5.15.0에서 다른 버전으로 변경하지 마십시오.

1. (Archetype 버전 41 기반 프로젝트만 해당) AEM Archetype 프로젝트가 생성되면 적응형 Forms 기반의 핵심 구성 요소에 대해 테마를 활성화합니다. 테마를 활성화하려면 다음을 수행하십시오.

   1. 편집할 [AEM Archetype 프로젝트 폴더]/ui.apps/src/main/content/jcr_root/apps/__appId__/components/adaptiveForm/page/customheaderlibs.html을 엽니다.

   1. 21행에 다음 코드를 추가합니다.

      ```XML
      <sly data-sly-use.clientlib="core/wcm/components/commons/v1/templates/clientlib.html"
      data-sly-use.formstructparser="com.adobe.cq.forms.core.components.models.form.FormStructureParser"
      data-sly-test.themeClientLibRef="${formstructparser.themeClientLibRefFromFormContainer}">
      <sly data-sly-test="${themeClientLibRef}" data-sly-call="${clientlib.css @ categories=themeClientLibRef}"/>
      </sly>
      ```

      ![위에 언급된 코드를 21행에 추가](/help/assets/code-to-enable-themes.png)

   1. 파일을 저장하고 닫습니다.

1. 최신 버전의 Forms 핵심 구성 요소를 포함하도록 프로젝트 업데이트:

   1. 편집할 [AEM Archetype 프로젝트 폴더]/pom.xml을 엽니다.
   1. `core.forms.components.version` 및 `core.forms.components.af.version`의 버전을 [최신 Forms 핵심 구성 요소](https://github.com/adobe/aem-core-forms-components/tree/release/650) 버전으로 설정합니다.

      ![최신 버전의 양식 핵심 구성 요소 멘션](/help/assets/latest-forms-component-version.png)

   1. 파일을 저장하고 닫습니다.


1. AEM Archetype 프로젝트가 정상적으로 생성되면 환경에 대한 배포 패키지를 빌드합니다. 패키지를 빌드하려면:

   1. AEM Archetype 프로젝트의 루트 디렉토리로 이동합니다.


   1. 다음 명령을 실행하여 환경에 맞는 AEM Archetype 프로젝트를 빌드합니다.

      ```Shell
      mvn clean install
      ```

      ![archetypebuild-success](assets/corecomponent-build-successful.png)


   AEM Archetype 프로젝트가 성공적으로 빌드되면 AEM 패키지가 생성됩니다. 패키지는 [AEM Archetype 프로젝트 폴더]\all\target\[appid].all-[버전].zip에서 찾을 수 있습니다.

1. [패키지 관리자](https://experienceleague.adobe.com/docs/experience-manager-65/administering/contentmanagement/package-manager.html?lang=ko)를 사용하여 모든 작성자 및 Publish 인스턴스에 [AEM Archetype 프로젝트 폴더]\all\target\[appid].all-[버전].zip 패키지를 배포하십시오.

>[!NOTE]
>
>
>
>패키지 관리자를 통해 패키지를 설치하기 위해 게시 인스턴스의 로그인 대화 상자에 액세스하는 데 문제가 발생하는 경우 다음 URL을 통해 로그인해 보십시오. http://[Publish 서버 URL]:[포트]/시스템/콘솔. 이렇게 하면 Publish 인스턴스에 액세스할 수 있으므로 설치 프로세스를 진행할 수 있습니다.


사용자 환경에 대해 핵심 구성 요소가 활성화됩니다. 빈 적응형 양식 템플릿 기반 핵심 구성 요소와 Canvas 3.0 테마가 환경에 배포되어 [적응형 Forms 기반 핵심 구성 요소를 만들 수 있습니다](create-a-headless-adaptive-form.md).

## 자주 묻는 질문

### 핵심 구성 요소란 무엇입니까?

[핵심 구성 요소](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html?lang=ko-KR)는 AEM에서 개발 시간을 가속화고 웹 사이트의 유지 관리 비용을 절감할 수 있는 표준화된 웹 콘텐츠 관리(WCM) 구성 요소입니다.

### 핵심 구성 요소 활성화에 추가된 기능은 무엇입니까?


내 환경에 맞는 적응형 양식 핵심 구성 요소가 활성화되면 빈 핵심 구성 요소 기반 적응형 양식 템플릿 및 Canvas 3.0 테마가 해당 환경에 추가됩니다. 내 환경에 맞는 적응형 양식 핵심 구성 요소가 활성화되면 다음과 같은 작업을 수행할 수 있습니다.

* 적응형 Forms 기반의 핵심 구성 요소 만들기
* 적응형 양식 템플릿을 기반으로 핵심 구성 요소를 만듭니다.
* 적응형 양식 템플릿을 기반으로 핵심 구성 요소에 대한 사용자 지정 테마를 만듭니다.
* 모바일, 웹, 기본 앱 및 양식의 Headless 표시가 필요한 서비스와 같은 채널에 핵심 구성 요소 기반 적응형 양식의 JSON 표시를 제공합니다.
