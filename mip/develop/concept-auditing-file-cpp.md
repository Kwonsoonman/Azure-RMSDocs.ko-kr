---
title: 개념 - Microsoft Information Protection SDK 파일 API 프로필의 감사
description: 이 문서는 Microsoft Information Protection SDK를 사용하여 파일 API 감사 이벤트를 Azure Information Protection Analytics에 제출하는 방법을 이해하는 데 도움이 됩니다.
services: information-protection
author: tommoser
ms.service: information-protection
ms.topic: conceptual
ms.date: 11/01/2018
ms.author: tommos
ms.openlocfilehash: bd04d9aa2edd6be01ae9e912d7ddbf936d6dd4df
ms.sourcegitcommit: 05fdaf43f74013eecb5886b95b09dd5e00670753
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/09/2018
ms.locfileid: "51297836"
---
# <a name="auditing-in-the-mip-sdk-file-api"></a>MIP SDK 파일 API의 감사

Azure Information Protection 관리 포털은 관리자 보고서에 대한 액세스 권한을 제공합니다. 이러한 보고서는 사용자가 MIP SDK를 통합한 모든 응용 프로그램에서 수동 또는 자동으로 적용하는 레이블에 대한 가시성을 제공합니다. SDK를 사용하는 개발 파트너는 응용 프로그램의 정보가 고객 보고서에 표시되도록 이 기능을 쉽게 지원할 수 있습니다.

## <a name="event-types"></a>이벤트 유형

SDK를 통해 Azure Information Protection Analytics에 제출할 수 있는 세 가지 유형의 이벤트가 있습니다. **하트비트 이벤트**, **검색 이벤트** 및 **변경 이벤트**

### <a name="heartbeat-events"></a>하트비트 이벤트

하트비트 이벤트는 파일 API를 통합한 모든 응용 프로그램에 대해 자동으로 생성됩니다. 하트비트 이벤트에는 다음이 포함됩니다.

* TenantId
* 생성 시간
* 사용자 계정 이름
* 감사가 생성된 머신의 이름
* 프로세스 이름
* 플랫폼
* 응용 프로그램 ID - Azure AD 응용 프로그램 ID에 해당합니다.

이러한 이벤트는 Microsoft Information Protection SDK를 사용하는 엔터프라이즈 전체의 응용 프로그램을 검색하는 데 유용합니다.

### <a name="discovery-events"></a>검색 이벤트

검색 이벤트는 파일 API에서 읽거나 사용하는 레이블이 지정된 정보에 대한 정보를 제공합니다. 이러한 이벤트는 조직 전체의 정보에 액세스하는 장치, 위치 및 사용자를 나타낼 때 유용합니다.

이러한 이벤트는 새 `mip::FileHandler`를 만들 때 `AuditDiscoveryEnabled` 매개 변수를 true로 설정하여 Azure Information Protection Analytics에 제출됩니다. 또한 사람이 읽을 수 있는 몇 가지 형식의 파일을 식별하는 콘텐츠 식별자가 제공됩니다. 이 식별자에 대한 파일 경로를 사용하는 것이 좋습니다.

아래 예제에서는 감사 검색을 사용하도록 설정된 새 `mip::FileHandler`를 만듭니다. `mip::FileEngine`에서 `CreateFileHandler()` 메서드가 호출되고 `AuditDiscoveryEnabled`가 true로 설정됩니다. `FileHanlder`에서 레이블을 읽으면 검색 감사가 생성됩니다.

```cpp
// Create FileHandler with discovery enabled
auto handlerPromise = std::make_shared<std::promise<std::shared_ptr<FileHandler>>>();
auto handlerFuture = handlerPromise->get_future();
fileEngine->CreateFileHandlerAsync(filePath, contentId, mip::ContentState::REST, true /*AuditDiscoveryEnabled*/, make_shared<FileHandlerObserver>(), createFileHandlerPromise);
auto handler = handlerFuture.get();

// Read label. This generates the discovery audit.
auto label = handler->GetLabel();
```

### <a name="change-events"></a>변경 이벤트

변경 이벤트는 파일, 적용되거나 변경된 레이블 및 사용자가 제공한 모든 근거에 대한 정보를 제공합니다. 변경 내용이 파일에 성공적으로 커밋된 후 `mip::FileHandler`에서 `NotifyCommitSuccessful()`을 호출하여 변경 이벤트가 생성됩니다.

```cpp
// Create labeling options, set label
string contentId = "C:\users\myuser\Documents\MyPlan.docx";
mip::LabelingOptions labelingOptions(mip::AssignmentMethod::PRIVILEGED, mip::ActionSource::MANUAL);
handler->SetLabel(labelId, labelingOptions);
auto commitPromise = std::make_shared<std::promise<bool>>();
auto commitFuture = commitPromise->get_future();

// CommitAsync() returns a bool. If the change was successful, call NotifyCommitSuccessful().
fileHandler->CommitAsync(outputFile, commitPromise);
if(commitFuture.get()) {

    // Submit audit event.
    handler->NotifyCommitSuccessful(contentId);
}
```

## <a name="audit-dashboard"></a>감사 대시보드

Azure Information Protection 감사 파이프라인에 제출된 이벤트에는 https://portal.azure.com의 보고서에 표시됩니다. Azure Information Protection Analytics는 공개 미리 보기로 제공되며 기능은 변경될 수 있습니다.

## <a name="next-steps"></a>다음 단계

Azure Information Protection의 감사 환경에 대한 자세한 내용은 [Tech Community의 미리 보기 공지 블로그](https://techcommunity.microsoft.com/t5/Azure-Information-Protection/Data-discovery-reporting-and-analytics-for-all-your-data-with/ba-p/253854)를 살펴보세요.
