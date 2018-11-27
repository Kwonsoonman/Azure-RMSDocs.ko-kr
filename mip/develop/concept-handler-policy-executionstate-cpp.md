---
title: 개념 - Microsoft Information Protection SDK의 ExecutionState 구현
description: 이 문서는 Microsoft Information Protection SDK의 ExecutionState를 사용하여 작업을 계산하고 감사 로깅에 대한 세부 정보를 제공하는 방법을 이해하는 데 도움이 됩니다.
services: information-protection
author: tommoser
ms.service: information-protection
ms.topic: conceptual
ms.date: 11/01/2018
ms.author: tommos
ms.openlocfilehash: 71cc6f08e130fe4a97604924643d13fd341a5625
ms.sourcegitcommit: ef70dab87478084fca853f389dab2408b95d1df1
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/26/2018
ms.locfileid: "52304166"
---
# <a name="implement-executionstate"></a>ExecutionState 구현

현재 상태 및 원하는 상태에 따라 수행해야 하는 작업을 계산하기 위해 MIP SDK에 정보를 전달하면 `mip::ExecutionState` 클래스를 통해 구현됩니다. SDK의 다른 클래스와 마찬가지로 `ExecutionState`는 추상 클래스이며 개발자가 구현해야 합니다.

> `ExecutionState` 구현의 전체 예를 보려면 다음 샘플 원본을 검토하세요.
>
> * [execution_state_impl.h](https://github.com/Azure-Samples/mipsdk-policyapi-cpp-sample-basic/blob/master/mipsdk-policyapi-cpp-sample-basic/execution_state_impl.h)
> * [execution_state_impl.cpp](https://github.com/Azure-Samples/mipsdk-policyapi-cpp-sample-basic/blob/master/mipsdk-policyapi-cpp-sample-basic/execution_state_impl.cpp)

## <a name="mipexecutionstate-members"></a>mip::ExecutionState 멤버

`ExecutionState`는 다음 가상 멤버를 표시합니다. 각 작업은 정책 엔진에 일부 컨텍스트를 제공하여 응용 프로그램에서 수행해야 하는 작업에 대한 정보를 반환합니다. 또한 이 정보를 사용하여 Azure Information Protection 보고 기능에 감사 정보를 제공할 수 있습니다.


| 멤버                                                                           | 반환                                                                                                              |
|----------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------|
| `std::string GetNewLabelId()`                                                      | 개체에 적용할 레이블 ID를 반환합니다.                                                                    |
| `mip::ContentState GetContentState()`                                              | 개체의 mip::ContentState를 반환합니다.                                                                         |
| `std::pair<bool, std::string> IsDowngradeJustified()`                              | 다운그레이드가 양쪽 맞춤이 맞춰지는지 여부를 나타내는 std:: pair를 반환합니다.                                 |
| `std::string GetContentIdentifier()`                                               | 콘텐츠 식별자를 반환합니다. 사람이 읽을 수 있는 식별자로, 개체의 위치를 나타냅니다.   |
| `mip::ActionSource GetNewLabelActionSource()`                                      | 레이블의 mip::ActionSource를 반환합니다.                                                                          |
| `mip::AssignmentMethod GetNewLabelAssignmentMethod()`                              | 레이블의 mip::AssignmentMethod를 반환합니다.                                                                        |
| `std::vector<std::pair<std::string, std::string>> GetNewLabelExtendedProperties()` | 문서에 적용할 사용자 지정 메타데이터가 포함된 std::vector of std::pairs 문자열을 반환합니다. |
| `std::vector<std::pair<std::string, std::string>> GetContentMetadata()`            | 현재 콘텐츠 메타데이터가 포함된 std::pairs of std:: vector 문자열을 반환합니다.                               |
| `std::shared_ptr<mip::ProtectionDescriptor> GetProtectionDescriptor()`           | 포인터를 mip::ProtectionDescriptor에 반환                                                                     |
| `mip::ContentFormat GetContentFormat()`                                            | mip::ContentFormat 반환                                                                                           |
| `mip::ActionType GetSupportedActions()`                                           | 레이블에 대한 mip::ActionTypes를 반환합니다.                                                                              |

`mip::ExecutionState`에서 파생된 클래스의 구현에서 각 항목을 재정의해야 합니다. 위에 링크된 샘플 응용 프로그램에서 이 프로세스는 `ExecutionStateOptions`이라는 구조체를 구현하고 파생 클래스의 생성자에 전달함으로써 수행됩니다.

[예제](https://github.com/Azure-Samples/mipsdk-policyapi-cpp-sample-basic/blob/master/mipsdk-policyapi-cpp-sample-basic/execution_state_impl.h)에서 `ExecutionStateOptions`이라는 구조체는 다음과 같이 정의됩니다.

```cpp
struct ExecutionStateOptions {
    std::unordered_map<std::string, std::string> metadata;
    std::string newLabelId;
    std::string contentIdentifier;
    mip::ActionSource actionSource = mip::ActionSource::MANUAL;
    mip::ContentState contentState = mip::ContentState::REST;
    mip::AssignmentMethod assignmentMethod = mip::AssignmentMethod::STANDARD;
    bool isDowngradeJustified = false;
    std::string downgradeJustification;
    std::string templateId;
    mip::ContentFormat contentFormat = mip::ContentFormat::DEFAULT;
};
```

각 속성은 응용 프로그램에 의해 설정되고 `ExecutionStateOptions`는 `mip::ExecutionState`에서 파생된 클래스의 생성자로 전달됩니다. 이 정보는 수행할 작업을 결정하는 데 사용됩니다. `mip::ExecutionState`에 제공된 테이터도 Azure Information Protection Analytics에 표시됩니다.

### <a name="next-steps"></a>다음 단계

- 확인 하는 방법을 알아봅니다 [기존 또는 새 레이블에 대 한 작업 계산](concept-handler-policy-computeactions-cpp.md), 현재 및 원하는 상태를 기반으로 합니다.
- 다운로드는 [정책 api 시도 GitHub에서 정책 API 샘플](https://azure.microsoft.com/resources/samples/?sort=0&term=mipsdk+policyapi)
