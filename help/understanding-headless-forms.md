---
title: 헤드리스 양식 이해 - 개념 및 FAQ
description: Headless 양식의 정의, 기존 양식 라이브러리와 차이점, 구현 세부 정보, UI 제어, 성능 및 프레임워크 및 백엔드와의 통합에 대한 일반적인 질문에 대한 답변입니다.
solution: Experience Manager Forms
feature: Adaptive Forms
topic: Headless
role: Admin, Developer
level: Beginner, Intermediate
keywords: headless forms, headless 양식 라이브러리, 적응형 양식, 상태 관리, 유효성 검사, 디자인 시스템, SSR, CMS
hide: false
exl-id: a1b2c3d4-e5f6-7890-abcd-ef1234567890
source-git-commit: 780f06a39c75dbf8795ac7a971150410ed7981e9
workflow-type: tm+mt
source-wordcount: '2605'
ht-degree: 0%

---


# 헤드리스 양식 이해 - 개념 및 FAQ {#understanding-headless-forms}

이 안내서는 Headless 양식에 대한 일반적인 질문과 AEM Headless 적응형 Forms에 어떻게 적용되는지 답변합니다. 이 패널을 통해 Headless 접근 방식을 사용할 시점과 스택에서 양식을 구현하고 스타일을 지정하고 통합하는 방법을 결정할 수 있습니다.

## 기본 사항 및 이해 {#basics-understanding}

### Headless 양식 라이브러리란 정확히 무엇입니까?

**Headless 양식 라이브러리**&#x200B;는 **양식 논리**(상태, 유효성 검사, 규칙, 제출)와 **프레젠테이션**(UI 구성 요소 및 스타일)을 구분하는 양식 솔루션입니다. &quot;head&quot;는 표시되는 양식 UI이고, &quot;headless&quot;는 라이브러리가 고정 UI를 지시하거나 전달하지 않음을 의미합니다. 대신 다음이 노출됩니다.

* **양식 모델**(대개 JSON): 구조, 필드, 제약 조건 및 규칙입니다.
* 양식 상태를 읽고 업데이트하며, 유효성 검사를 실행하고, 제출을 처리하기 위한 **API 또는 후크**.
* UI가 변경 사항에 반응할 수 있도록 **이벤트 및 라이프사이클**.

AEM Headless 적응형 Forms에서 양식은 Adobe Experience Manager에서 호스팅되는 [JSON 구조](architecture.md)입니다. [Forms Web SDK](architecture.md#developer-tools)(클라이언트측 런타임)은 논리 레이어(비즈니스 규칙 프로세서, 상태 관리, 유효성 검사)를 제공하는 반면, 앱에서는 해당 구조를 렌더링하는 UI를 제공합니다.

### Headless 양식은 기존 양식 라이브러리와 어떻게 다릅니까?

| 측면 | 기존 양식 라이브러리 | Headless 양식 라이브러리 |
|--------|---------------------------|------------------------|
| **UI** | 기본 제공 구성 요소 및 스타일과 함께 제공 | 규정된 UI가 없습니다. 고유한 구성 요소를 가져올 수 있습니다. |
| **스타일링** | 라이브러리 구성 요소의 테마 지정 또는 무시 | 전체 제어, 디자인 시스템 그대로 사용 |
| **양식 정의** | 종종 코드 전용(JSX/HTML의 구성 요소) | 종종 데이터 기반(CMS 또는 API의 JSON/스키마) |
| **상태 및 유효성 검사** | 라이브러리 구성 요소에 연결됨 | API/후크를 통해 노출됨. 모든 UI가 바인딩될 수 있음 |
| **채널** | 일반적으로 웹(경우에 따라 하나의 프레임워크) | 동일한 양식 정의로 웹, 모바일, 채팅 등을 구동할 수 있습니다. |

AEM Headless 적응형 Forms을 사용하면 AEM에서 [양식을 만들고 게시](create-and-publish-a-headless-form.md)할 수 있습니다. 모든 클라이언트(React, Angular, 기본 모바일, 챗봇)는 [양식 JSON을 가져오기](architecture.md)하고 해당 채널에 적절한 UI로 렌더링할 수 있습니다.

### UI 기반 양식 솔루션 대신 Headless 양식을 사용해야 하는 이유는 무엇입니까?

헤드리스 양식은 다음과 같은 경우에 적합합니다.

* **시스템 일관성 디자인** - 라이브러리 기본값에 영향을 주지 않고 기존 구성 요소와 브랜드를 사용하십시오.
* **다중 채널** - 웹, 모바일 및 기타 터치포인트에 대한 하나의 양식 정의([개요](overview.md) 참조).
* **CMS 또는 백엔드 기반 양식** - 작성자가 코드 배포 없이 양식 구조 및 규칙을 변경합니다. 앱은 JSON만 사용합니다.
* **프레임워크 유연성** - [AF-core](https://www.npmjs.com/package/@aemforms/af-core) 라이브러리는 프레임워크에 독립적입니다. 편의를 위해 React 바인딩이 제공되지만 다른 프레임워크에 대한 바인딩을 빌드할 수 있습니다.
* **백엔드 기능** - 특정 UI 스택에 잠그지 않고 미리 채우기, 유효성 검사, 제출, 워크플로 및 Forms 데이터 모델에 AEM Forms을 활용합니다.

### Headless 접근 방식을 사용하는 것이 언제 타당합니까?

다음과 같은 경우 Headless 양식 사용:

* 강력한 디자인 시스템 또는 구성 요소 라이브러리가 있거나 있어야 합니다.
* Forms은 비개발자가 작성(예: CMS에서 작성)하므로 여러 앱 또는 채널에서 작업해야 합니다.
* 웹, 모바일 또는 다른 클라이언트에서 동일한 양식 논리(유효성 검사, 규칙)가 필요합니다.
* 다시 렌더링하는 것을 최소화하고 UI와 독립적으로 양식 논리를 테스트 가능하도록 유지하려고 합니다.

다음과 같은 경우 UI가 포함된 기존 양식 라이브러리를 고려하십시오.

* 단일 웹 앱의 작업 양식이 신속하게 필요하며 사용자 지정 UI 또는 다중 채널에 대해서는 신경 쓰지 않습니다.
* 팀은 하나의 프레임워크에서 코드로만 양식을 정의하는 것을 선호합니다.

### &#39;헤드리스&#39;는 유행어일까 아니면 진짜 문제를 해결할까.

실제 아키텍처 문제를 해결합니다.

* **문제 분리** - 양식 구조, 규칙 및 유효성 검사가 데이터 및 논리 레이어에서 라이브됩니다. UI 레이어는 사용자 작업만 렌더링하고 발송합니다. 이렇게 하면 테스트 안정성과 재사용이 향상됩니다.
* **채널 독립성** - 하나의 양식 정의로 서로 다른 UI를 구현할 수 있습니다(예: React 웹, React Native, Angular 또는 음성). AEM Headless 적응형 Forms은 [한 번 빌드하고 React, SPA, 웹, 모바일 등을 통해 제공](overview.md)할 수 있도록 빌드되었습니다.
* **코드 없이 작성** - 비즈니스 사용자는 [적응형 양식 편집기](create-a-headless-adaptive-form.md)에서 필드 및 규칙을 변경할 수 있습니다. 개발자는 콘텐츠 변경을 위해 다시 배포할 필요가 없습니다.
* **기존 스택과 통합** - 디자인 시스템, 상태 관리 및 라우팅을 유지합니다. Headless 레이어는 양식 상태, 유효성 검사 및 제출만 처리합니다.

## 구현 및 기술 관련 질문 {#implementation-technical}

### Headless 양식은 상태를 어떻게 관리합니까?

AEM Headless 적응형 Forms에서 상태는 **Forms 웹 SDK**&#x200B;에 의해 관리됩니다.

* **비즈니스 규칙 프로세서** - JSON 형식을 수락하고 필드 상태를 관리하며 JSON에 정의된 규칙 및 이벤트 처리기를 실행합니다.
* **React 바인더** - React 구성 요소가 현재 상태 및 핸들러를 받도록 컨트롤러에 후크(예: `useRuleEngine`)를 제공합니다. 코어 API를 통해 비 React UI에서 동일한 상태를 사용할 수 있습니다.
* **상태**&#x200B;에는 필드 값, 가시성, 유효성 및 양식 모델에 정의된 사용자 지정 속성이 포함됩니다.

UI 구성 요소가 상태 및 처리기(예: `[state, handlers] = useRuleEngine(props)`)를 받습니다. 사용자가 상호 작용할 때 `state`에서 렌더링하고 `handlers`을(를) 호출합니다. 런타임은 양식 정의 및 규칙과 동기화된 상태를 유지합니다. [아키텍처](architecture.md) 및 [Headless 양식을 렌더링하려면 사용자 지정 구성 요소를 사용](developing-for-headless-forms-using-your-own-components.md)을 참조하십시오.

### Headless 양식 설정에서 유효성 검사는 어떻게 작동합니까?

유효성 검사는 양식 논리 계층의 일부입니다.

* **제약 조건**&#x200B;은(는) JSON 형식(예: 필수, 최소/최대, 패턴)에 정의되어 있습니다. Forms Web SDK은 이러한 제약 조건을 적용하고 유효성 검사 상태(예: 유효/무효, 오류 메시지)를 구성 요소에 표시합니다.
* **클라이언트측 유효성 검사**&#x200B;은(는) 양식 구조를 기반으로 SDK에서 적용됩니다. UI에 상태의 오류가 표시됩니다.
* **서버측 유효성 검사**&#x200B;는 AEM API(예: 끝점 유효성 검사)를 통해 사용할 수 있습니다. 제출 전이나 제출 중에 유효성 검사를 수행할 수 있습니다.

UI에서 유효성 검사 논리를 구현하지 않고, 런타임에서 제공한 유효성 검사 상태와 메시지만 표시합니다.

### Headless 양식을 스키마 유효성 검사와 통합할 수 있습니까(Yup, Zod, Joi)?

기본 제공 유효성 검사는 양식 JSON 제한에 의해 구동됩니다. Yup, Zod, Joi 또는 이와 유사한 기능을 사용하려면

* 진실의 한 소스가 스키마 유효성 검사와 양식 구조를 모두 유도하도록 스키마에서 Headless 적응형 양식 JSON을 **유도 또는 생성**&#x200B;할 수 있습니다(예: JSON 스키마를 양식 JSON으로 변환).
* 양식 JSON 이상의 **사용자 지정 유효성 검사**&#x200B;의 경우 이벤트 핸들러 또는 제출 전에 고유한 유효성 검사기(Yup/Zod/Joi)를 실행하고 결과를 양식 상태 또는 전송 차단으로 푸시할 수 있습니다. 통합 지점은 상태 및 제출에 사용하는 것과 동일한 후크/API입니다.

[적응형 Forms 사양](/help/assets/headless-adaptive-forms-specification.pdf) 및 [JSON 수식](architecture.md)은 런타임에 사용되는 규칙 및 제약 조건 모델을 정의합니다.

### 비동기 유효성 검사(예: 사용자 이름 가용성)를 처리하려면 어떻게 해야 합니까?

비동기 유효성 검사는 애플리케이션 계층에서 구현할 수 있습니다.

* 필드가 변경될 때 논리를 트리거하려면 JSON 형식(지원되는 경우)의 **규칙 또는 이벤트 핸들러**&#x200B;를 사용하십시오.
* **사용자 지정 구성 요소**&#x200B;에서 동일한 상태/처리기 후크를 사용하여 백 엔드(예: 사용자 이름 가용성 API)를 호출한 다음 런타임 API 또는 UI에 표시되는 로컬 상태를 통해 필드의 유효성을 업데이트하거나 오류를 표시합니다.
* 또는 흐림 효과 검사 **on blur 또는 submit** 전에 검사를 수행하고 비동기 검사에 실패한 경우 사용자 지정 메시지를 사용하여 필드 상태를 invalid로 설정합니다.

정확한 패턴은 앱이 [비즈니스 규칙 프로세서](architecture.md) 및 사용자 지정 구성 요소와 어떻게 통합되는지에 따라 다릅니다.

### Headless 양식을 사용하여 API에 데이터를 제출하려면 어떻게 해야 합니까?

제출이 UI에서 분리됩니다.

* **AEM 제출 액션** - REST 끝점, 이메일 또는 통합(예: Microsoft Dynamics, Salesforce)에 제출하도록 AEM에서 양식을 구성합니다. 양식이 실제 HTTP/백엔드 호출을 처리하는 AEM을 통해 제출됩니다. [이벤트를 사용하여 양식 데이터 처리 및 제출](use-events-to-handle-and-submit-form-data.md)을 참조하십시오.
* **클라이언트측 제출** - 앱이 런타임 상태에서 제출을 수신 대기하거나 양식 데이터를 수집하여 사용자의 API로 전송할 수 있습니다. [HTTP API](https://opensource.adobe.com/aem-forms-af-runtime/api/) 문서 목록, 가져오기, 유효성 검사, 제출 및 제출 상태 추적.
* **미리 채우기** - 폼이 로드될 때 상태가 이미 채워지도록 REST 끝점 또는 서버측을 통해 데이터를 미리 채울 수 있습니다. [스토리북 - 미리 채우기 예](https://opensource.adobe.com/aem-forms-af-runtime/storybook/?path=/story/reference-examples--prefill-form-with-personalised-data)를 참조하세요.

## UI 및 디자인 제어 {#ui-design-control}

### Headless 양식으로 나만의 디자인 시스템 또는 구성 요소 라이브러리를 사용할 수 있습니까?

예. 이는 Headless 양식의 주요 이점입니다. AEM Headless 적응형 Forms 사용:

* 고유한 구성 요소를 양식 모델에 **매핑**&#x200B;합니다(필드 유형 또는 리소스 유형별). [사용자 지정 구성 요소를 사용하여 Headless 양식을 렌더링](developing-for-headless-forms-using-your-own-components.md) 및 [Google Material UI React 구성 요소를 사용하여 Headless 양식을 렌더링](use-google-material-ui-react-components-to-render-a-headless-form.md)을 참조하십시오.
* 런타임에서 **상태 및 처리기**&#x200B;를 제공합니다. 구성 요소는 디자인 시스템을 사용하여 렌더링하고 형식 논리가 동기화 상태를 유지하도록 처리기를 호출합니다.
* **React Spectrum**, Material UI, Chakra UI 또는 사용자 지정 구성 요소 라이브러리를 사용할 수 있습니다. [specification](/help/assets/headless-adaptive-forms-specification.pdf)은(는) 사용자 지정 구성 요소(예: Chakra UI, Vue.js)에 대해 확장할 수 있습니다. [FAQ - 사용자 지정 프레임워크](faq.md#is-it-possible-to-use-headless-adaptive-forms-with-custom-frameworks)를 참조하십시오.

### Headless 양식에서 접근성 지원(ARIA, 키보드 처리)을 제공합니까?

사용자가 제공한 **UI 계층**&#x200B;에서 액세스 가능성이 구현되었습니다. Headless 레이어는 DOM을 렌더링하지 않으므로 ARIA 또는 키보드 동작을 자체적으로 추가하지 않습니다. 다음과 같은 방법으로 액세스 권한을 얻을 수 있습니다.

* 디자인 시스템 또는 라이브러리에서 **액세스 가능한 구성 요소**&#x200B;를 사용합니다(대부분 ARIA 및 키보드 지원 포함).
* 사용자 지정 필드 구성 요소(레이블, 오류 메시지, 포커스 관리, 키보드 탐색)의 **접근성 모범 사례**&#x200B;를 따릅니다.
* 받은 양식 구조 및 상태(예: 필수, 유효하지 않음, 표시)가 구성 요소의 ARIA 속성 및 동작에 반영되도록 합니다.

즉시 사용 가능한 React Spectrum 기반 구성 요소를 사용하는 경우 내장된 액세스 가능성이 제공됩니다.

### 복잡한 UI 구성 요소(날짜 선택기, 사용자 정의 드롭다운)를 어떻게 처리합니까?

JSON 형식의 해당 필드 형식 또는 사용자 지정 리소스 형식에 매핑된 **사용자 지정 구성 요소**(으)로 처리합니다.

* 다른 필드 구성 요소와 동일한 **props/state/handlers**&#x200B;을(를) 허용하도록 구성 요소를 구현합니다(예: `useRuleEngine`을(를) 통해).
* 값, 가시성 및 유효성에 **상태**&#x200B;를 사용하고, 값을 업데이트하고 유효성 검사를 트리거하려면 **처리기**&#x200B;를 사용하십시오.
* 선택한 UI 라이브러리로 날짜 선택기 또는 사용자 지정 드롭다운을 렌더링합니다. 변경 시 양식 상태가 올바르게 유지되도록 새 값으로 핸들러를 호출합니다.

필드 유형 및 리소스 유형별 매핑은 [사용자 지정 구성 요소를 사용하여 Headless 양식을 렌더링합니다](developing-for-headless-forms-using-your-own-components.md)를 참조하십시오.

### 필드(동적 양식)를 동적으로 추가하거나 제거할 수 있습니까?

양식 구조는 서버에서 반환된 **양식 JSON**&#x200B;에 의해 정의됩니다. 동적 동작은 다음을 통해 수행됩니다.

* **JSON 형식의 규칙** - 표현식을 기반으로 값을 표시/숨기기, 활성화/비활성화 또는 설정합니다. [비즈니스 규칙 프로세서](architecture.md)에서 이러한 규칙을 실행합니다. 구성 요소는 `state.visible` 등에 반응합니다.
* **서버 기반 구조** - 서로 다른 사용자 또는 컨텍스트가 서로 다른 양식 JSON(예: 다른 단계 또는 섹션)을 받을 수 있으므로 &quot;동적&quot;은 &quot;요청마다 다른 양식 정의&quot;를 의미할 수 있습니다.
* **클라이언트측 변경** - 앱에서 양식 모델을 수정할 수 있는 경우(예: 반복 가능한 구조의 항목 추가/제거) 런타임에서 이를 반영할 수 있습니다. 정확한 기능은 양식 스키마와 런타임 API에 따라 다릅니다.

[스토리북](https://opensource.adobe.com/aem-forms-af-runtime/storybook/)에는 동적 동작의 예제가 포함되어 있습니다.

### 조건부 필드(입력을 기반으로 표시/숨기기)를 어떻게 처리합니까?

조건부 가시성은 비즈니스 규칙 프로세서에서 평가한 JSON 양식의 **규칙**&#x200B;에 의해 결정됩니다. 조건(예: &quot;필드 A가 X인 경우 필드 B 표시&quot;), 런타임 업데이트 상태(예: `state.visible`)를 정의합니다. 구성 요소는 **상태 준수**(예: `if (!state.visible) return null;`)만 하면 됩니다. 상태에서 렌더링하지 않고 표시/숨기기에는 추가 UI 논리가 필요하지 않습니다. 연속 및 조건부 동작은 [적응형 Forms 사양](/help/assets/headless-adaptive-forms-specification.pdf)에 문서화되어 있으며 [스토리북 - 연속 필드](https://opensource.adobe.com/aem-forms-af-runtime/storybook/?path=/story/adaptive-form-dynamic-behaviour--options&args=formJson.items[0].fieldType:drop-down;formJson.items[0].minimum:!undefined;formJson.items[0].maximum:!undefined;formJson.items[0].label.value:Choose+number+of+options;formJson.items[0].enum[0]:1;formJson.items[0].enum[1]:2;formJson.items[0].enum[2]:3;formJson.items[1].fieldType:drop-down)에 나와 있습니다. [FAQ - 계단식 필드](faq.md#do-headless-adaptive-forms-support-cascading-fields)도 참조하세요.

## 성능 및 확장성 {#performance-scalability}

### Headless 양식이 기존 양식 라이브러리보다 성능이 향상되었습니까?

그럴 수 있지만 구현에 따라 다릅니다.

* **대상 업데이트** - 잘 설계된 Headless 런타임은 변경된 상태만 업데이트하고 이를 사용하는 구성 요소만 알려주므로 단일 양식 구성 요소에 비해 불필요한 재렌더링을 줄일 수 있습니다.
* **더 작은 UI 번들** - 전체 라이브러리 구성 요소 집합이 아닌 사용 중인 디자인 시스템의 UI 구성 요소만 제공됩니다.
* **지연 로드** - 필요한 경우 양식 JSON을 가져올 수 있습니다. 초기 번들은 더 작게 유지될 수 있습니다.

또한 성능은 구성 요소 구현 방식에 따라 다릅니다(예: 불필요한 재렌더링, 회고화 방지).

### 재렌더링은 어떻게 최소화합니까?

* **상태 셰이프** - 런타임은 세분화된 업데이트를 허용하는 구조로 형식 상태를 유지하므로 트리의 영향을 받는 부분만 다시 렌더링해야 합니다.
* **후크 디자인** - `useRuleEngine`과(와) 같은 후크를 구현하여 구성 요소가 사용하는 상태로만 구성 요소를 구독할 수 있으므로 부모 또는 형제 변경 내용이 모든 필드를 다시 렌더링하도록 강제하지는 않습니다.
* **책임** - 사용자 지정 구성 요소에서 React 모범 사례(예: `React.memo`, 안정적인 콜백)를 사용하여 다시 렌더링을 최소화할 수 있습니다.

### Headless 양식은 큰 여러 단계 양식에 적합합니까?

예, 적절히 설계된 경우:

* **양식 정의** - 큰 양식은 JSON에서 단계 또는 섹션으로 분할할 수 있습니다. 표시되는 단계/섹션만 UI에서 완전히 활성화되어야 하며, 지원되는 경우 숨겨진 섹션에 대한 규칙을 소극적으로 평가해야 할 수 있습니다.
* **상태** - 런타임에 일관된 양식 상태가 하나 있습니다. 단계 탐색에서 섹션을 표시/숨기거나 데이터를 복제하지 않고 &quot;현재 단계&quot;를 업데이트하는 중입니다.
* **청킹 및 지연 로드** - 초기 페이로드 및 구문 분석 비용을 낮게 유지하기 위해 청크로 양식 JSON을 가져오거나 단계 진행 시 추가 섹션을 로드할 수 있습니다.

규모가 매우 큰 양식의 경우 구조(예: 마법사 단계), 서버 기반 양식 변형, 실제 페이로드를 사용하여 렌더링 및 규칙 실행 측정 등을 고려하십시오.

## 통합 및 에코시스템 {#integration-ecosystem}

### Headless 양식이 Next.js/SSR/서버 작업에서 작동할 수 있습니까?

* **Next.js / React** - 예. React 렌더러 및 후크는 React 환경에서 작동합니다. 클라이언트 구성 요소에서 Forms Web SDK을 사용합니다. 필요에 따라 서버 또는 클라이언트에서 양식 JSON을 가져옵니다.
* **SSR** - 서버에서 양식 JSON을 가져와서 클라이언트에 전달하여 양식이 데이터를 포함하도록 할 수 있습니다. 양식 상호 작용(상태, 유효성 검사, 규칙)은 SDK이 로드된 클라이언트에서 실행됩니다. SSR 중에 클라이언트 전용 상태에 의존하는 양식 필드를 렌더링하지 않거나 클라이언트에서 하이드레이트하는 자리 표시자를 사용합니다.
* **서버 작업(Next.js)** - 제출 처리기에서 서버 작업을 호출할 수 있습니다. 사용자가 제출하면 클라이언트 코드는 Headless 상태에서 양식 데이터를 수집하고 AEM 제출 엔드포인트 대신 또는 그 외에 서버 작업을 호출합니다.

### Headless Forms는 CMS, Headless Commerce 또는 백엔드 시스템과 어떻게 통합됩니까?

* **CMS** - AEM은 양식 정의에 대한 CMS입니다. 작성자는 양식 JSON을 만들고 게시합니다. 다른 CMS는 양식 URL/API를 참조하거나 연결할 수 있습니다. 앱은 AEM(또는 CDN)에서 양식을 가져오고 선택적으로 다른 CMS에서 복사 또는 레이아웃을 가져옵니다.
* **미리 채우기 및 제출** - [미리 채우기](https://opensource.adobe.com/aem-forms-af-runtime/storybook/?path=/story/reference-examples--prefill-form-with-personalised-data) 및 제출은 REST 끝점에 도달할 수 있으므로 CRM, DAM 또는 상거래 백엔드에서 미리 채우고 동일하거나 다른 시스템에 제출할 수 있습니다. AEM Forms은 [Microsoft Dynamics 및 Salesforce](faq.md), REST, 이메일 및 사용자 지정 제출 액션도 지원합니다.
* **Forms 데이터 모델** - AEM Forms은 서로 다른 데이터 소스에 연결할 수 있는 Forms 데이터 모델을 제공합니다. headless forms에서는 모든 통합을 직접 빌드하지 않고 이러한 기능을 미리 채우기, 유효성 검사 및 제출에 사용할 수 있습니다.

모바일 및 오프라인 시나리오의 경우, 권장되는 접근 방법은 [Headless 적응형 Forms API를 통해 나만의 앱을 빌드하고 양식 정의를 가져오는](mobile-forms-best-practices.md)입니다.

## 추가 참조 {#see-also}

* [개요](overview.md)
* [아키텍처](architecture.md)
* [자주 묻는 질문](faq.md)
* [Headless 양식 만들기 및 게시](create-and-publish-a-headless-form.md)
* [Headless 적응형 양식 API](https://opensource.adobe.com/aem-forms-af-runtime/api/)
* [코드 플레이그라운드](https://experienceleague.adobe.com/landing/aem-headless-forms/developer/code.html?lang=ko)
* [스토리북](https://opensource.adobe.com/aem-forms-af-runtime/storybook/)
