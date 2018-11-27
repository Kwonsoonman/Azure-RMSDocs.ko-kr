---
title: 개념 - MIP SDK의 정책 처리기입니다.
description: 이 문서는 정잭 API 처리기가 만들어지고 작업 호출에 사용되는 방식을 이해하는 데 도움을 줍니다.
author: tommoser
ms.service: information-protection
ms.topic: conceptual
ms.date: 11/16/2018
ms.author: tommos
ms.openlocfilehash: 02198f7762e2952f946757d14c13a41b22d73c7a
ms.sourcegitcommit: ef70dab87478084fca853f389dab2408b95d1df1
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/26/2018
ms.locfileid: "52303994"
---
# <a name="microsoft-information-protection-sdk---policy-handler-concepts"></a>Microsoft Information Protection SDK - 정책 처리기 개념

정책은 API의 `mip::PolicyHandler` 정책 동작을 계산 하 여 감사 이벤트를 전송 하는 데 사용 되는 작업을 노출 합니다.

## <a name="policy-handler-functions"></a>정책 처리기 함수

`mip::PolicyHandler`는 레이블과 보호 정보를 모두 읽고 쓰고 제거하는 메서드를 노출합니다. 전체 목록은 [API 참조](reference/class_mip_PolicyHandler.md)를 참조하세요.

이 문서에서는 다음 메서드에 대해 다룹니다.

- `ComputeActions`
- `NotifyCommittedActions`

## <a name="requirements"></a>요구 사항

`PolicyHandler` 만들기는 다음이 필요합니다.

- `PolicyProfile`
- `PolicyProfile`에 추가된 `PolicyEngine`
- `mip::PolicyHandler::Observer`를 상속하는 클래스

## <a name="create-a-policy-handler"></a>정책 처리기 만들기

정책 작업을 가져오는 데 필요한 첫 번째 단계는 `PolicyHandler` 개체를 만드는 것입니다. 이 클래스는 특정 레이블이 수행 해야 하는 작업의 목록을 가져오려면 하는 데 필요한 기능을 구현 합니다. 또한 감사 이벤트를 트리거할 함수를 구현 합니다.

`PolicyHandler` 만들기는 promise/future 패턴을 사용하여 `PolicyEngine`의 `CreatePolicyHandlerAsync` 함수를 호출하는 것만큼 쉽습니다.

`CreatePolicyHandlerAsync`는 단일 매개 변수(**isAuditDiscoveryEnabled**)를 허용합니다. 응용 프로그램이 감사 로깅에서 하트비트 이벤트를 나타내야 할 경우 이 값을 **true**로 설정합니다.

> [!NOTE]
> `CreatePolicyHandler`에 `Observer` 개체가 필요하므로 파생 클래스에서 `mip::PolicyHandler::Observer` 클래스를 구현해야 합니다. 

```cpp
auto createPolicyHandlerPromise = std::make_shared<std::promise<std::shared_ptr<mip::PolicyHandler>>>();
auto createPolicyHandlerFuture = createPolicyHandlerPromise->get_future();
PolicyEngine->CreatePolicyHandlerAsync(true);
auto handler = createPolicyHandlerFuture.get();
```

`PolicyHandler` 개체를 성공적으로 만든 후 작업을 계산하고 감사 이벤트를 제출할 수 있습니다.

## <a name="next-steps"></a>다음 단계

이제는 정책 처리기를 만드는 방법을 배웠습니다.

- 에 대해 알아봅니다 하는 방법 [실행 상태 클래스를 만들고](concept-handler-policy-executionstate-cpp.md), 계산 작업을 결정 하는 데 사용 됩니다.
- 다운로드는 [정책 api 시도 GitHub에서 정책 API 샘플](https://azure.microsoft.com/resources/samples/?sort=0&term=mipsdk+policyapi)
