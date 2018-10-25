---
title: 개념 - 분류 레이블
description: 이 문서는 데이터 분류에 레이블을 사용하는 방법을 이해하는 데 도움이 됩니다.
author: BryanLa
ms.service: information-protection
ms.topic: conceptual
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: a32193194b9806dbab5066db27192265566ca44f
ms.sourcegitcommit: 1cf14852cd14ea91ac964fb03a901238455ffdff
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/28/2018
ms.locfileid: "47446654"
---
# <a name="microsoft-information-protection-sdk---classification-label-concepts"></a>Microsoft Information Protection SDK - 분류 레이블 개념

조직은 포괄적인 데이터 보호 전략의 일부로 조직 내 데이터의 민감도 수준을 설명하는 데이터 분류 시스템을 구현한 후 이러한 분류와 문서 특성을 매핑해야 합니다.

분류 관련 특성은 일반적으로 의도하지 않은 주체가 해당 문서나 데이터를 보거나 분실하는 경우 조직에 미치는 **위험**과 연관이 있습니다. 익숙한 미국 정부 분류 시스템에는 세 가지 분류 수준이 있습니다. 각 수준에는 해당 분류를 적용해야 하는 경우를 설명하는 정의가 있습니다.

* **일급비밀**: 합당한 수준에서 판단할 때, 무단으로 공개되는 경우 원래 분류 기관이 확인하거나 설명할 수 있는 국가 보안에 특별히 심각한 손해를 미칠 것으로 예상되는 정보에 적용합니다.
* **비밀**: 합당한 수준에서 판단할 때, 무단으로 공개되는 경우 원래 분류 기관이 확인하거나 설명할 수 있는 국가 보안에 심각한 손해를 미칠 것으로 예상되는 정보에 적용합니다.
* **기밀**: 합당한 수준에서 판단할 때, 무단으로 공개되는 경우 원래 분류 기관이 확인하거나 설명할 수 있는 국가 보안에 손해를 미칠 것으로 예상되는 정보에 적용합니다.
* **분류 안 됨**: 실제로 분류가 아니라 위의 세 가지 중 하나에 해당하지 않는 경우입니다.

상업용 또는 민간 부문 응용 프로그램에서는 Azure Information Protection 서비스의 기본값과 비슷한 목록을 화폐 가치와 연결하여 정의할 수 있습니다.

* **극비**: 합당한 수준에서 판단할 때, 무단으로 공개되는 경우 미화 1백만 달러가 넘는 손해를 미칠 것으로 예상되는 정보에 적용합니다.
* **기밀**: 합당한 수준에서 판단할 때, 무단으로 공개되는 경우 미화 10만 달러가 넘는 손해를 미칠 것으로 예상되는 정보에 적용합니다.
* **일반**: 합당한 수준에서 판단할 때, 무단으로 공개되는 경우 측정 가능한 손해를 거의 미치지 않을 것으로 예상되는 정보에 적용합니다.
* **공개**: 공용으로 이용하도록 외부에 공개되는 정보에 적용합니다. 
* **비즈니스 무관**: 회사 비즈니스와 직접 또는 간접적으로 관련이 없는 정보에 적용합니다.

각 분류는 정보가 무단으로 공개되는 경우에 비즈니스에 미치는 위험을 설명합니다. 이러한 분류 및 조건을 식별한 후에는 데이터 소유자가 적용할 분류를 이해하는 데 도움이 되는 특성을 식별해야 합니다.

## <a name="labeling"></a>레이블 지정

데이터 분류를 정보 집합과 연관시키는 작업을 **레이블 지정**이라고 합니다. MIP SDK가 문서에 분류 **레이블**을 적용하는 것과 관련이 있으므로, 분류를 참조하지 않고 레이블을 참조합니다. 사용자 또는 프로세스가 정보에 대한 지식을 기반으로 이미 데이터를 **분류**했다면 MIP SDK는 정보에 **레이블을 지정**합니다.

## <a name="labels-in-the-mip-sdk"></a>MIP SDK의 레이블

레이블은 MIP SDK의 기본 구성 요소입니다. 레이블은 SDK가 다루는 모든 문서의 태그 지정, 보호 및 콘텐츠 표시를 유도합니다. SDK는 다음을 수행할 수 있습니다.

* 문서에 레이블 적용
* 문서의 기존 레이블 읽기
* 정책에서 요구하는 경우 기존 레이블 및 위임 근거 변경
* 문서에서 레이블 제거

레이블은 레이블 관리가 보안 및 준수 센터에서 정의한 구성에 따라 보호 및 콘텐츠 표시를 적용합니다. 

## <a name="miplabel-vs-mipcontentlabel"></a>mip::Label 및 mip::ContentLabel

MIP SDK에 두 가지 유형의 레이블, 즉 `Label` 및 `ContentLabel`이 있습니다.

* Label: 사용자 또는 프로세스가 조직 정책에 정의된 대로 적용할 수 있는 레이블입니다.
* ContentLabel: 문서 또는 정보에 이미 있는 레이블입니다. 읽거나 업데이트하거나 제거할 수 있습니다. 

다시 말해서, `ContentLabel`은 정보에 적용되는 `Label`입니다.

## <a name="metadata"></a>메타데이터

또한 SDK는 키/값 쌍으로 추가 메타데이터를 문서에 추가하는 것을 지원합니다. 조직에 더 구체적인 방식으로 정보를 설명하는 하위 분류나 태그가 있는 경우 SDK를 사용하여 해당 메타데이터를 적용할 수 있습니다.

## <a name="next-steps"></a>다음 단계

미국 정부 분류 시스템에 대한 자세한 내용은 https://www.gpo.gov/fdsys/pkg/FR-2010-01-05/html/E9-31418.htm을 참조하세요.