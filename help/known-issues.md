---
title: Headless 적응형 양식의 알려진 문제
description: Headless 적응형 양식의 알려진 문제
keywords: 헤드리스, 적응형 양식, 알려진 문제
hide: true
source-git-commit: 0127f8ddede38083f0932b0e8d7efdd0dd77c3a6
workflow-type: tm+mt
source-wordcount: '111'
ht-degree: 1%

---


# 알려진 문제 {#known-issues}

* 편집, 표시 및 데이터 패턴은 지원되지 않습니다. (CQ-4327047)
* minItems 제약 조건은 동적으로 변경할 수 없습니다. (CQ-4342499)
* 위반하는 경우 패널 레벨 유효성 검사에서 오류가 발생하지 않습니다. (CQ-4342373)
* 위반한 경우 파일 유효성 검사에서 오류가 발생하지 않습니다. (CQ-4342372)
* 사용자 지정 속성은 동적이지 않습니다. (CQ-4342376)
* 표현식을 사용하여 변경 이벤트 시 파일 데이터를 동적으로 변경하면 무한 루프가 발생합니다. (CQ-4342377)
* 첨부 파일이 도움말 텍스트를 지원하지 않습니다. (CQ-4342370)
* 필수 확인란은 선택하지 않은 경우 제출 시 오류가 표시되지 않습니다. (CQ-4342371)
* aria-label이 첨부 파일에 추가되지 않았습니다. (CQ-4341494)
