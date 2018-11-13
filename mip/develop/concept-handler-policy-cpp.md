---
title: 개념 - MIP SDK의 정책 처리기입니다.
description: 이 문서는 정잭 API 처리기가 만들어지고 작업 호출에 사용되는 방식을 이해하는 데 도움을 줍니다.
author: tommoser
ms.service: information-protection
ms.topic: conceptual
ms.date: 11/01/2018
ms.author: tommos
ms.openlocfilehash: c1e150de6096e070f46232e77a4749081fe0bb9f
ms.sourcegitcommit: 05fdaf43f74013eecb5886b95b09dd5e00670753
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/09/2018
ms.locfileid: "51297850"
---
# <a name="microsoft-information-protection-sdk---policy-handler-concepts"></a>Microsoft Information Protection SDK - 정책 처리기 개념

정책 API에서 `mip::PolicyHandler`은 정책 작업을 계산하고 감사 이벤트를 제출하는 데 사용할 수 있는 다양한 작업을 표시합니다.

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

정책 작업을 가져오는 데 필요한 첫 번째 단계는 `PolicyHandler` 개체를 만드는 것입니다. 이 클래스는 특정 레이블이 수행해야 하는 작업 목록과 감사 이벤트를 트리거하는 함수에 필요한 기능을 구현합니다.

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

# <a name="compute-an-action"></a>작업 계산

이전에 설명한 대로 정책 API의 주요 기능은 다음과 같습니다.

- 사용 가능한 레이블을 나열합니다.
- 현재 및 원하는 상태에 따라 수행해야 하는 특정 작업 집합을 반환합니다. 

이 프로세스의 마지막 단계는 레이블 식별자와 필요에 따라 기존 레이블에 대한 메타데이터를 `ComputeActions()` 함수에 제공하는 것입니다.

이 문서의 샘플 코드는 GitHub에서 찾을 수 있습니다.

* [mipsdk-policyapi-cpp-sample-basic](https://github.com/Azure-Samples/mipsdk-policyapi-cpp-sample-basic)

## <a name="compute-an-action-for-a-new-label"></a>새 레이블에 대한 작업 계산

새 레이블에 대한 `mip::Actions` 계산은 [ExecutionState](concept-auditing-policy-executionstate-cpp.md) 섹션에 정의된 `ExecutionStateImpl`을 사용하여 수행할 수 있습니다.

```cpp
// Replace with valid label ID.
string newLabelId = "d7b93a40-4df3-47e4-b2fd-7862fc6b095c"; 
sample::policy::ExecutionStateOptions options;

// Set desired newLabelId in ExecutionStateOptions.
options.newLabelId = newLabelId;

// Initialize ExecutionStateImpl with options, create handler, call ComputeActions.
std::unique_ptr<ExecutionStateImpl> state(new ExecutionStateImpl(options));
auto handler = mEngine->CreatePolicyHandler(false); // Don't generate audit event.
auto actions = handler->ComputeActions(*state);
```

`actions`의 일부로 반환된 `mip::MetadataActions`만 기록하면 다음과 같이 표시됩니다.

```cpp
Add: MSIP_Label_d7b93a40-4df3-47e4-b2fd-7862fc6b095c_Enabled : true
Add: MSIP_Label_d7b93a40-4df3-47e4-b2fd-7862fc6b095c_SetDate : 2018-10-23T20:39:06-0800
Add: MSIP_Label_d7b93a40-4df3-47e4-b2fd-7862fc6b095c_Method : Standard
Add: MSIP_Label_d7b93a40-4df3-47e4-b2fd-7862fc6b095c_Name : Contoso FTEs (C)
Add: MSIP_Label_d7b93a40-4df3-47e4-b2fd-7862fc6b095c_SiteId : 94f6984e-8d31-4794-bdeb-3ac89ad2b660
Add: MSIP_Label_d7b93a40-4df3-47e4-b2fd-7862fc6b095c_ActionId : 2266fbe8-a0d9-44e8-bad8-00008f2a0915
Add: MSIP_Label_d7b93a40-4df3-47e4-b2fd-7862fc6b095c_ContentBits : 3
```

`PolicyHandler`가 작업을 계산하고 `mip::Action` 중 `std::vector`를 반환합니다. 이 메타데이터를 파일이나 데이터에 적용하는 것은 응용 프로그램 개발자의 몫입니다.

> [!NOTE]
> 위의 예에서는 `mip::MetadataAction` 출력만 표시됩니다. 추가 작업 유형을 표시하는 예를 보려면 [정책 API 다운로드](https://aka.ms/mipsdkbins)를 사용하여 샘플 번들을 검토하세요.

## <a name="compute-actions-with-an-existing-label"></a>기존 레이블로 작업 계산

정책 API를 사용하는 경우 콘텐츠에서 메타데이터를 읽는 것은 응용 프로그램에 달려 있습니다. 이 메타데이터는 `mip::ExecutionState`의 일부로 API에 제공됩니다. `ComputeActions()`은 레이블이 지정되지 않은 문서에 새 레이블을 적용하는 것보다 더 복잡한 작업을 처리할 수 있습니다. 아래 예제에서는 레이블이 이미 존재하는 경우 보다 중요한 레이블에서 덜 중요한 레이블로 레이블을 다운그레이드하는 방법을 보여줍니다. 이 프로세스는 쉼표로 구분된 메타데이터 문자열을 읽고 `mip::ExecutionState`를 통해 API에 제공함으로써 시뮬레이션됩니다.

> [!NOTE]
> 이 샘플에서는 `SplitString()`이라는 유틸리티 함수를 사용합니다. 예제는 [여기에서](https://github.com/Azure-Samples/mipsdk-policyapi-cpp-sample-advanced/blob/master/mipsdk-policyapi-cpp-sample-advanced/utils.cpp) 찾을 수 있습니다.

```cpp
// Replace with valid label ID.
string newLabelId = "d7b93a40-4df3-47e4-b2fd-7862fc6b095c";

// Comma and Pipe Delimited Metadata.
string metadata = "MSIP_Label_d7b93a40-4df3-47e4-b2fd-7862fc6b095c_Enabled|true,MSIP_Label_d7b93a40-4df3-47e4-b2fd-7862fc6b095c_SetDate|2018-10-23T21:53:31-0800,MSIP_Label_d7b93a40-4df3-47e4-b2fd-7862fc6b095c_Method|Standard,MSIP_Label_d7b93a40-4df3-47e4-b2fd-7862fc6b095c_Name|Contoso FTEs (C),MSIP_Label_d7b93a40-4df3-47e4-b2fd-7862fc6b095c_SiteId|94f6984e-8d31-4794-bdeb-3ac89ad2b660,MSIP_Label_d7b93a40-4df3-47e4-b2fd-7862fc6b095c_ActionId|b56491d9-155f-40ff-866f-0000acd85c31,MSIP_Label_d7b93a40-4df3-47e4-b2fd-7862fc6b095c_ContentBits|7";

// Create ExecutionStateOptions and set newLabelId.
sample::policy::ExecutionStateOptions options;
options.newLabelId = newLabelId;

// Split metadata string by commas, store in vector.
vector<string> metadataPairs = sample::utils::SplitString(metadata, ','); 

// Iterate through each string, splitting by the pipe.
// Add each key/value pair to ExecutionStateOptions metadata.
for (const string& metadataPair : metadataPairs) {
    vector<string> keyValue = sample::utils::SplitString(metadataPair, '|');
    options.metadata[keyValue[0]] = keyValue[1];
}

// Initialize ExecutionStateImpl with options, create handler, call ComputeActions
std::unique_ptr<ExecutionStateImpl> state(new ExecutionStateImpl(options));
auto handler = mEngine->CreatePolicyHandler(false); // Don't generate audit event.
auto actions = handler->ComputeActions(*state);
```

위의 예제에서는 몇 가지 작업을 수행할 수 있습니다. 이러한 작업은 입력 및 레이블 구성으로 제공된 레이블에 따라 달라집니다. 최소한 결과는 `GetMetadataToRemove()`를 통해 제거할 데이터와 `GetMetadataToAdd()`를 통해 추가할 데이터가 포함된 단일 `mip::MetadataAction`이 됩니다.

```
Add: MSIP_Label_d48d0e60-c766-40d6-96d3-53b2857fe775_Enabled : true
Add: MSIP_Label_d48d0e60-c766-40d6-96d3-53b2857fe775_SetDate : 2018-10-23T23:59:41-0800
Add: MSIP_Label_d48d0e60-c766-40d6-96d3-53b2857fe775_Method : Standard
Add: MSIP_Label_d48d0e60-c766-40d6-96d3-53b2857fe775_Name : General
Add: MSIP_Label_d48d0e60-c766-40d6-96d3-53b2857fe775_SiteId : 94f6984e-8d31-4794-bdeb-3ac89ad2b660
Add: MSIP_Label_d48d0e60-c766-40d6-96d3-53b2857fe775_ActionId : 447a996b-28ea-482c-b0b5-000075bd4bb3
Add: MSIP_Label_d48d0e60-c766-40d6-96d3-53b2857fe775_ContentBits : 7
Remove: MSIP_Label_d7b93a40-4df3-47e4-b2fd-7862fc6b095c_Name
Remove: MSIP_Label_d7b93a40-4df3-47e4-b2fd-7862fc6b095c_Enabled
Remove: MSIP_Label_d7b93a40-4df3-47e4-b2fd-7862fc6b095c_SiteId
Remove: MSIP_Label_d7b93a40-4df3-47e4-b2fd-7862fc6b095c_SetDate
Remove: MSIP_Label_d7b93a40-4df3-47e4-b2fd-7862fc6b095c_Method
Remove: MSIP_Label_d7b93a40-4df3-47e4-b2fd-7862fc6b095c_ContentBits
Remove: MSIP_Label_d7b93a40-4df3-47e4-b2fd-7862fc6b095c_ActionId
```

## <a name="next-steps"></a>다음 단계

* 그런 다음, [GitHub의 정책 API 샘플 및 정책 API 테스트](https://azure.microsoft.com/resources/samples/?sort=0&term=mipsdk+policyapi) 다운로드
* [Azure Information Protection analytics에 감사 이벤트를 전달](concept-auditing-policy-cpp.md)하는 방법에 대해 읽기