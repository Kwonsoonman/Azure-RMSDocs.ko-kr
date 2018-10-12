---
title: 개념 - MIP SDK의 보호 처리기입니다.
description: 이 문서는 보호 API 처리기가 만들어지고 작업 호출에 사용되는 방식을 이해하는 데 도움을 줍니다.
author: BryanLa
ms.service: information-protection
ms.topic: conceptual
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: a087f1bdef5a010718c67fbdca938ecbb62e5faa
ms.sourcegitcommit: 823a14784f4b34288f221e3b3cb41bbd1d5ef3a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/29/2018
ms.locfileid: "47453499"
---
# <a name="microsoft-information-protection-sdk---protection-handler-concepts"></a>Microsoft Information Protection SDK - 보호 처리기 개념

MIP SDK 보호 API에서 `mip::ProtectionHandler`는 보호된 스트림 및 버퍼를 암호화 및 암호 해독하고, 액세스 검사를 수행하고, 게시 라이선스를 가져오고, 보호된 정보에서 특성을 가져오기 위한 함수를 제공합니다. 

## <a name="requirements"></a>요구 사항

특정 파일에 사용할 `ProtectionHandler`를 만들려면 다음이 필요합니다.

- `ProtectionProfile`
- `ProtectionProfile`에 추가된 `ProtectionEngine`
- `mip::ProtectionHandler::Observer`를 상속하는 클래스([여기]()에 설명된 패턴과 유사함)
- `mip::ProtectionDescriptor` 또는 게시 라이선스

## <a name="create-a-protection-handler"></a>보호 처리기 만들기

`mip::ProtectionHandler` 개체는 `ProtectionDescriptor` 또는 직렬화된 게시 라이선스를 두 `ProtectionEngine` 함수 중 하나에 제공하여 생성됩니다. 게시 라이선스가 없는 일반 텍스트 정보를 보호하기 위해 보호 설명자를 생성해야 합니다. **게시 라이선스**는 이미 보호된 콘텐츠의 암호를 해독할 때 또는 라이선스가 이미 구성된 콘텐츠를 보호할 때 사용합니다. 연결된 게시 라이선스가 없으면 보호된 콘텐츠의 암호를 해독할 수 없습니다.

`mip::ProtectionEngine`은 `ProtectionHandler`를 만들기 위한 두 가지 함수를 제공합니다. 처리기 또는 게시 라이선스의 첫 번째 매개 변수를 제외하고 매개 변수는 동일합니다.

- `mip::ProtectionEngine::CreateProtectionHandlerFromDescriptorAsync`
  - 첫 번째 매개변수로 `ProtectionDescriptor`가 필요합니다.
- `mip::ProtectionEngine::CreateProtectionHandlerFromPublishingLicenseAsync`
  - `std::vector<unint8_t>`에 첫 번째 매개 변수로 저장된 직렬화된 게시 라이선스가 필요합니다.

### <a name="create-from-descriptor"></a>설명자에서 만들기

아직 보호되지 않은 콘텐츠를 보호하거나 콘텐츠에 새 보호를 적용하는 경우(암호 해독되었음을 의미함) `mip::ProtectionDescriptor`를 생성해야 합니다. 일단 생성되고 나면 `mip::ProtectionEngine::CreateProtectionHandlerFromDescriptorAsync()`에 전달되고 `mip::ProtectionHandler::Observer`를 통해 결과가 반환됩니다.

```cpp
auto handlerPromise = std::make_shared<std::promise<std::shared_ptr<ProtectionHandler>>>();
auto handlerFuture = handlerPromise->get_future();
auto observer = std::make_shared<ProtectionHandlerObserverImpl>();

//Refer to ProtectionDescriptor docs for details on creating the descriptor
auto descriptor = CreateProtectionDescriptor(); //Stub function

mEngine->CreateProtectionHandlerFromDescriptorAsync(
    descriptor,
    mip::ProtectionHandlerCreationOptions::None,
    observer,
    handlerPromise);

auto handler = handlerFuture.get();
```

`ProtectionHandler` 개체를 성공적으로 만든 후에 파일 작업(가져오기/설정/삭제/커밋)을 수행할 수 있습니다.

### <a name="create-from-publishing-license"></a>게시 라이선스에서 만들기

이 예제에서는 게시 라이선스를 일부 소스에서 이미 읽었으며 `std::vector<uint8_t> serializedPublishingLicense`에 저장되어 있다고 가정합니다.

```cpp

//TODO: Implement GetPublishingLicense()
//Snip implies that function reads PL from source file, database, stream, etc.
std::vector<uint8_t> serializedPublishingLicense = GetPublishingLicense(filePath);

auto handlerPromise = std::make_shared<std::promise<std::shared_ptr<ProtectionHandler>>>();
auto handlerFuture = handlerPromise->get_future();

shared_ptr<ProtectionHandlerObserverImpl> handleObserver =
    std::make_shared<ProtectionHandlerObserverImpl>();

mEngine->CreateProtectionHandlerFromPublishingLicenseAsync(
    serializedPublishingLicense,
    mip::ProtectionHandlerCreationOptions::None,
    handleObserver,
    handlerPromise);

auto handler = handlerFuture.get();
```

