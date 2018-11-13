---
title: 개념 - Microsoft Information Protection SDK 정책 API 프로필의 감사
description: 이 문서는 Microsoft Information Protection SDK를 사용하여 정책 API 감사 이벤트를 Azure Information Protection Analytics에 제출하는 방법을 이해하는 데 도움이 됩니다.
services: information-protection
author: tommoser
ms.service: information-protection
ms.topic: conceptual
ms.date: 11/07/2018
ms.author: tommos
ms.openlocfilehash: c660a5f58acd87ff9047a21fea26cc2732667493
ms.sourcegitcommit: 05fdaf43f74013eecb5886b95b09dd5e00670753
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/09/2018
ms.locfileid: "51297849"
---
# <a name="auditing-in-the-mip-sdk"></a>MIP SDK의 감사

Azure Information Protection 관리 포털은 관리자 보고서에 대한 액세스 권한을 제공합니다. 이러한 보고서는 MIP SDK를 통합한 모든 응용 프로그램에서 사용자가 수동 또는 자동으로 적용하는 레이블에 대한 가시성을 제공합니다. SDK를 활용하는 개발 파트너는 고객 보고서에 표시되도록 응용 프로그램의 정보를 제공할 수 있으므로 이러한 기능을 쉽게 지원할 수 있습니다.

## <a name="event-types"></a>이벤트 유형

SDK를 통해 Azure Information Protection Analytics에 제출할 수 있는 세 가지 유형의 이벤트가 있습니다. **하트비트 이벤트**, **검색 이벤트** 및 **변경 이벤트**

### <a name="heartbeat-events"></a>하트비트 이벤트

하트비트 이벤트는 정책 API를 통합한 모든 응용 프로그램에 대해 자동으로 생성됩니다. 하트비트 이벤트에는 다음이 포함됩니다.

* TenantId
* 생성 시간
* 사용자 계정 이름
* 감사가 생성된 머신의 이름
* 프로세스 이름
* 플랫폼
* 응용 프로그램 ID - Azure AD 응용 프로그램 ID에 해당합니다.

이러한 이벤트는 Microsoft Information Protection SDK를 사용하는 엔터프라이즈 전체의 응용 프로그램을 검색하는 데 유용합니다.

### <a name="discovery-events"></a>검색 이벤트

검색 이벤트는 정책 API에서 읽거나 사용하는 레이블이 지정된 정보에 대한 정보를 제공합니다. 이러한 이벤트는 조직 전체의 정보에 액세스하는 장치, 위치 및 사용자를 나타낼 때 유용합니다.

`mip::PolicyEngine`을 통해 `mip::PolicyHandler` 개체를 만들 때 부울 플래그를 설정하여 정책 API에 검색 이벤트가 생성됩니다. 아래 예에서는 **isAuditDiscoveryEnabled**의 값이 true로 설정됩니다. `mip::ExecutionState`가 `ComputeActions()` 또는 `GetSensitivityLabel()`(기존 메타데이터 정보 및 콘텐츠 식별자 포함)로 전달되면 해당 검색 정보가 Azure Information Protection Analytics에 제출됩니다.

검색 감사는 응용 프로그램이 `ComputeActions()` 또는 `GetSensitivityLabel()`을 호출하고 `mip::ExecutionState`를 제공하면 생성됩니다. 이 이벤트는 처리기당 한 번만 생성됩니다.

실행 상태에 대한 자세한 내용은 `mip::ExecutionState` 개념 설명서를 검토하세요.

```cpp
// Create PolicyHandler, passing in true for isAuditDiscoveryEnabled
auto handler = mEngine->CreatePolicyHandler(true);

// Returns vector of mip::Action and generates discovery event.
auto actions = handler->ComputeActions(*state);

//Or, get the label for a given state
auto label = handler->GetSensitivityLabel(*state);
```

실제로 Azure Information Protection Analytics로 파일 액세스 정보를 전달할 수 있도록 하려면 **isAuditDiscoveryEnabled**가 `mip::PolicyHandler` 구축 중 `true`이어야 합니다.

## <a name="change-event"></a>변경 이벤트

변경 이벤트는 파일, 적용되거나 변경된 레이블 및 사용자가 제공한 모든 근거에 대한 정보를 제공합니다. 변경 이벤트는 `mip::PolicyHandler`에서 `NotifyCommittedActions()`을 호출하여 생성됩니다. 변경 내용이 성공적으로 커밋된 후 호출이 수행되고 작업을 계산하는 데 사용된 `mip::ExecutionState`가 전달됩니다.

> 이 함수를 응용 프로그램이 호출하지 못하면 Azure Information Protection Analytics에 랜딩하는 이벤트가 없습니다.

```cpp
handler->NotifyCommittedActions(*state);
```

## <a name="audit-dashboard"></a>감사 대시보드

Azure Information Protection 감사 파이프라인에 제출된 이벤트에는 https://portal.azure.com의 보고서에 표시됩니다. Azure Information Protection Analytics는 공개 미리 보기로 제공되며 기능은 변경될 수 있습니다.

## <a name="next-steps"></a>다음 단계

Azure Information Protection의 감사 환경에 대한 자세한 내용은 [Tech Community의 미리 보기 공지 블로그](https://techcommunity.microsoft.com/t5/Azure-Information-Protection/Data-discovery-reporting-and-analytics-for-all-your-data-with/ba-p/253854)를 참조하세요.

