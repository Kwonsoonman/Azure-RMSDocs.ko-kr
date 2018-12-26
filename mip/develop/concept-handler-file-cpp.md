---
title: 개념 - MIP SDK의 파일 처리기
description: 이 문서는 파일 API 처리기가 만들어지고 작업 호출에 사용되는 방식을 이해하는 데 도움을 줍니다.
author: BryanLa
ms.service: information-protection
ms.topic: conceptual
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: 6b2916a3937892353f4389a59b5e48356deda603
ms.sourcegitcommit: 823a14784f4b34288f221e3b3cb41bbd1d5ef3a6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/29/2018
ms.locfileid: "47453370"
---
# <a name="microsoft-information-protection-sdk---file-handler-concepts"></a>Microsoft Information Protection SDK - 파일 처리기 개념

MIP SDK 파일 API에서 `mip::FileHandler`는 지원이 기본으로 제공되는 파일 형식 집합에 대해 레이블 읽기/쓰기 또는 보호에 사용할 수 있는 다양한 모든 작업을 노출합니다. 

## <a name="supported-file-types"></a>지원되는 파일 형식

- OCP(Office 2010 이상)를 기반으로 하는 Office 파일 형식
- 레거시 Office 파일 형식(Office 2007)
- PDF
- 일반적인 PFILE 지원
- Adobe XMP를 지원하는 파일

## <a name="file-handler-functions"></a>파일 처리기 함수

`mip::FileHandler`는 레이블과 보호 정보를 모두 읽고 쓰고 제거하는 메서드를 노출합니다. 전체 목록은 [API 참조](reference/class_mip_filehandler.md)를 참조하세요.

이 문서에서는 다음 메서드에 대해 다룹니다.

- `GetLabelAsync()`
- `SetLabel()`
- `DeleteLabel()`
- `CommitAsync()`

## <a name="requirements"></a>요구 사항

특정 파일에 사용할 `FileHandler`를 만들려면 다음이 필요합니다.

- `FileProfile`
- `FileProfile`에 추가된 `FileEngine`
- `mip::FileHandler::Observer`를 상속하는 클래스

## <a name="create-a-file-handler"></a>파일 처리기 만들기

파일 API에서 파일을 관리하는 데 필요한 첫 번째 단계는 `FileHandler` 개체를 만드는 것입니다. 이 클래스는 파일에 대한 레이블 변경 내용을 가져오고, 설정하고, 업데이트하고, 삭제하고, 커밋하는 데 필요한 모든 기능을 구현합니다.

`FileHandler` 만들기는 promise/future 패턴을 사용하여 `FileEngine`의 `CreateFileHandlerAsync` 함수를 호출하는 것만큼 쉽습니다.

`CreateFileHandlerAsync`는 읽거나 수정해야 하는 파일의 경로, 비동기 이벤트 알림용 `mip::FileHandler::Observer`, `FileHandler`의 promise 등의 세 가지 매개 변수를 수용합니다.

**참고**: `CreateFileHandler`에 `Observer` 개체가 필요하므로 파생 클래스에서 `mip::FileHandler::Observer` 클래스를 구현해야 합니다. 

```cpp
auto createFileHandlerPromise = std::make_shared<std::promise<std::shared_ptr<mip::FileHandler>>>();
auto createFileHandlerFuture = createFileHandlerPromise->get_future();
fileEngine->CreateFileHandlerAsync(filePath, std::make_shared<FileHandlerObserver>(), createFileHandlerPromise);
auto handler = createFileHandlerFuture.get();
```

`FileHandler` 개체를 성공적으로 만든 후에 파일 작업(가져오기/설정/삭제/커밋)을 수행할 수 있습니다.

## <a name="read-a-label"></a>레이블 읽기

### <a name="metadata-requirements"></a>메타데이터 요구 사항

파일에서 메타데이터를 읽고 애플리케이션에서 사용할 수 있는 항목으로 변환하기 위한 몇 가지 요구 사항이 있습니다.

- 읽을 레이블이 O365 서비스에 여전히 존재해야 합니다. 완전히 삭제된 경우 SDK는 해당 레이블에 대한 정보를 얻지 못하고 오류를 반환합니다.
- 파일 메타데이터가 그대로 유지되어야 합니다. 이 메타데이터에는 다음이 포함됩니다.
  - Attribute1
  - Attribute2

### <a name="getlabelasync"></a>GetLabelAsync()

특정 파일을 가리키도록 처리기를 만들었으면 promise/future 패턴으로 돌아가 레이블을 비동기적으로 읽습니다. 이 promise는 적용된 레이블에 대한 모든 정보가 포함된 `mip::ContentLabel` 개체에 해당합니다.

`promise` 및 `future` 개체를 인스턴스화한 후에 `handler->GetLabelAsync()`를 호출하고 `promise`를 단독 매개 변수로 제공하여 레이블을 읽습니다. 마지막으로, 레이블은 `future`에서 가져오는 `mip::ContentLabel` 개체에 저장할 수 있습니다.

```cpp
auto loadPromise = std::make_shared<std::promise<std::shared_ptr<mip::ContentLabel>>>();
auto loadFuture = loadPromise->get_future();
handler->GetLabelAsync(loadPromise);
auto label = loadFuture.get();
```

레이블 데이터는 `label` 개체에서 읽고 애플리케이션의 다른 구성 요소 또는 기능에 전달할 수 있습니다.

***

## <a name="set-a-label"></a>레이블 설정

레이블 설정은 두 부분으로 구성된 프로세스입니다. 먼저, 해당 파일을 가리키는 처리기를 만들었으면 몇 개의 매개 변수를 사용해 `FileHandler->SetLabel()`을 호출하여 레이블을 설정할 수 있습니다.

```cpp
handler->SetLabel(label->GetId(), mip::LabelingOptions{ mip::AssignmentMethod::PRIVILEGED, "" });
```

첫 번째 매개 변수는 단순히 `ListLabelsAsync()`의 레이블 식별자입니다. 이 값은 전용 변수에 저장하거나 `mip::Label->GetId()`에서 읽어 올 수 있습니다.

위의 예에서는 `label`이라는 개체에 원하는 `mip::Label`을 저장했다고 가정합니다.

### <a name="labeling-options"></a>레이블 지정 옵션

레이블을 설정하는 데 필요한 두 번째 매개 변수는 `SetLabel()` 함수를 호출하는 동안 인라인으로 만드는 `mip::LabelingOptions` 개체입니다. 이 개체를 미리 만들 수도 있습니다.

`LabelingOptions`는 작업의 `AssignmentMethod` 및 근거와 같은 레이블 관련 추가 정보를 지정합니다.

- `mip::AssignmentMethod`는 `STANDARD`, `PRIVILEGED` 또는 `AUTO`의 세 가지 값이 있는 열거자입니다. 자세한 내용은 `mip::AssignmentMethod` 참조를 검토하세요.
- 근거는 서비스 정책에 필요한 경우 *그리고* 파일의 *기존* 민감도를 낮추는 경우에만 필요합니다.

```cpp
auto labelingOptions = mip::LabelingOptions();
labelingOptions.SetMethod(mip::AssignmentMethod::STANDARD);
labelingOptions.SetJustificationMessage("Because I made an educated decision based upon the contents of this file.");
```

이제 레이블 지정 옵션을 인라인으로 만드는 대신 `SetLabel()` 함수에 전달할 수 있습니다.

```cpp
handler->SetLabel(label->GetId(), labelingOptions);
```

처리기가 참조하는 파일에 레이블을 지정했으며 이제 변경 내용을 커밋하고 파일을 디스크에 쓰거나 출력 스트림을 만드는 단계가 하나 더 있습니다.

### <a name="commit-changes"></a>변경 내용 커밋

MIP SDK에서 파일 변경 내용을 커밋하는 마지막 단계는 변경 내용을 **커밋**하는 것입니다. 이는 `FileHandler->CommitAsync()` 함수를 사용하여 수행됩니다. 

커밋 함수를 구현하기 위해 promise/future로 돌아가서 `bool`의 promise를 만듭니다. `CommitAsync()` 함수는 작업이 성공하면 true를 반환하고 어떤 이유로든 작업이 실패하면 false를 반환합니다. 

`promise` 및 `future`를 만든 후 `CommitAsync()`가 호출되고 출력 파일 경로(`std::string`)와 promise 등 두 개의 매개 변수가 제공됩니다. 마지막으로, `future` 개체의 값을 가져와 결과를 얻습니다.

```cpp
auto commitPromise = std::make_shared<std::promise<bool>>();
auto commitFuture = commitPromise->get_future();
handler->CommitAsync(outputFile, commitPromise);
auto wasCommitted = commitFuture.get();
```

**중요**: `FileHandler`는 기존 파일을 업데이트하거나 덮어쓰지 않습니다. 레이블이 지정되는 파일을 **바꾸는** 것은 개발자가 결정합니다. 

**FileA.docx**에 레이블을 쓰는 경우 이 레이블이 적용된 파일 사본 **FileB.docx**가 만들어집니다. **FileA.docx** 제거/이름 바꾸기 및 **FileB.docx** 이름 바꾸기를 위한 코드를 써야 합니다.

***

## <a name="delete-a-label"></a>레이블 삭제

```cpp
auto handler = mEngine->CreateFileHandler(filePath, std::make_shared<FileHandlerObserverImpl>());
handler->DeleteLabel(mip::AssignmentMethod::PRIVILEGED, "Label unnecessary.");
auto commitPromise = std::make_shared<std::promise<bool>>();
auto commitFuture = commitPromise->get_future();
handler->CommitAsync(outputFile, commitPromise);
```
