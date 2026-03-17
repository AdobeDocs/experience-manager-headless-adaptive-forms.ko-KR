---
title: 맞춤형 구성 요소를 사용하여 Headless 양식 렌더링
description: 사용자 지정 구성 요소를 만들고 이를 Headless 적응형 Forms 필드에 매핑하는 방법을 알아봅니다. 이 안내서에서는 사용자 지정 렌더링 및 동작을 수행하기 위해 필드 유형 및 리소스 유형별로 구성 요소를 매핑하는 방법을 설명합니다.
solution: Experience Manager Forms
feature: Adaptive Forms
topic: Headless
role: Admin, Developer
level: Beginner, Intermediate
index: true
exl-id: 5aba1821-35dc-4da4-b188-d4853d64d5ee
source-git-commit: 86129488bec7faed87600a237ac034ca1b601187
workflow-type: tm+mt
source-wordcount: '471'
ht-degree: 0%

---


# 맞춤형 구성 요소를 사용하여 Headless 양식 렌더링 {#developing-for-headless-forms-using-your-own-components}

Headless 적응형 Forms에서 사용자 지정 구성 요소를 만들고 구현하여 양식의 모양과 기능을 정의할 수 있습니다. 기본 구성 요소는 표준 동작을 제공하지만 사용자 지정 &quot;공지&quot; 구성 요소 또는 특수 &quot;스크리블 서명&quot; 필드와 같은 특정 UI 요소 또는 상호 작용이 필요할 수 있습니다.

이 문서에서는 사용자 지정 React 구성 요소를 만들고 이를 Headless 적응형 양식에 매핑하는 과정을 안내합니다.

## &#x200B;1. 사용자 지정 React 구성 요소 만들기

먼저 양식 필드를 렌더링할 React 구성 요소를 만듭니다. 이 구성 요소는 모든 React 라이브러리(예: 재질 UI, Ant 디자인 또는 사용자 지정 스타일)를 사용할 수 있습니다.

예를 들어 특정 스타일을 사용하여 읽기 전용 메시지를 렌더링하는 사용자 지정 **공지** 구성 요소를 만들어 보겠습니다.

1. React 프로젝트의 구성 요소 디렉터리(예: `src/components`)로 이동합니다.
2. 구성 요소에 대한 새 폴더 및 파일(예: `Announcement/index.tsx`)을 만듭니다.
3. 구성 요소 구현 Headless Forms 런타임과 호환되는 `props`을(를) 허용해야 합니다(일반적으로 필드의 상태를 수신).

```tsx
import React from 'react';
import { useRuleEngine } from '@aemforms/af-react-renderer';
import { FieldJson, State } from '@aemforms/af-core';

const Announcement = function (props: State<FieldJson>) {
    // The useRuleEngine hook connects the component to the form logic
    const [state, handlers] = useRuleEngine(props);

    if (!state.visible) {
        return null;
    }

    return (
        <div className="custom-announcement" style={{ border: '1px solid #ccc', padding: '10px', backgroundColor: '#f9f9f9' }}>
            <h3>{state?.label?.value}</h3>
            <p>{state?.default}</p>
        </div>
    );
}

export default Announcement;
```

## &#x200B;2. 사용자 지정 구성 요소 매핑

사용자 지정 구성 요소를 사용하려면 `mappings.ts` 파일에 매핑해야 합니다. Headless Forms 런타임은 이 매핑을 사용하여 JSON 양식의 각 필드에 대해 렌더링할 React 구성 요소를 결정합니다.

구성 요소를 매핑하는 기본 방법에는 **필드 형식** 또는 **리소스 형식**&#x200B;의 두 가지가 있습니다.

### 필드 유형별 매핑

표준 매핑은 양식 JSON의 `fieldType` 속성(예: `text-input`, `checkbox`, `button`)을 기반으로 합니다. 표준 구성 요소의 *모두* 인스턴스를 사용자 지정 버전으로 바꾸려는 경우에 유용합니다.

1. `src/utils/mappings.ts`(또는 매핑이 정의된 위치)을 엽니다.
2. 사용자 지정 구성 요소를 가져옵니다.
3. `fieldType`을(를) 키로 사용하여 매핑 개체에 추가합니다.

```typescript
import { mappings } from "@aemforms/af-react-components";
import Announcement from "../components/Announcement";

const customMappings: any = {
  ...mappings,
  "text-input": Announcement // This would replace ALL text-input fields (use with caution)
};

export default customMappings;
```

### 리소스 유형별 매핑(사용자 정의 구성 요소)

AEM에서 사용자 지정 구성 요소를 만든 경우(예: 표준 텍스트 구성 요소를 확장하는 &quot;공지&quot; 구성 요소) React 앱에서 해당 특정 구성 요소를 *만*&#x200B;다르게 렌더링하려면 해당 **리소스 유형** 또는 고유 식별자로 매핑해야 합니다.

이 접근 방식을 사용하면 표준 텍스트 구성 요소를 정상적으로 렌더링하고 사용자 지정 &quot;공지&quot; 구성 요소에서는 특수화된 React 구현을 사용할 수 있습니다.

1. 구성 요소에 대한 고유 식별자를 식별합니다. Headless 양식 JSON에서는 구성된 경우 `:type` 속성 또는 사용자 지정 `fieldType`에서 종종 발견됩니다.
2. 이 식별자를 사용하여 매핑을 추가합니다.

```typescript
import { mappings } from "@aemforms/af-react-components";
import Announcement from "../components/Announcement";

const customMappings: any = {
  ...mappings,
  // Map by resource type or custom identifier
  "my-project/components/announcement": Announcement
};

export default customMappings;
```

> **참고:** AEM 양식 모델이 올바른 `:type` 또는 `mappings.ts`에서 사용하는 키와 일치하는 식별자를 내보내는지 확인하십시오.

## &#x200B;3. 매핑 적용

마지막으로 Headless 양식 인스턴스가 이러한 사용자 정의 매핑을 사용하는지 확인하십시오.

```tsx
import React from 'react';
import { AdaptiveForm } from '@aemforms/af-react-renderer';
import customMappings from './utils/mappings';
import formJSON from './form-def.json';

function App() {
  return (
    <AdaptiveForm
      formJson={formJSON}
      mappings={customMappings}
    />
  );
}

export default App;
```

이러한 단계를 따라 특정 디자인 및 기능 요구 사항과 일치하는 구성 요소를 사용하여 Headless 적응형 Forms의 기능을 확장할 수 있습니다.
