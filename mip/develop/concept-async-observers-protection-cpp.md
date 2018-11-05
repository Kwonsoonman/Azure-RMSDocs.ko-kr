---
title: 개념 - MIP SDK의 보호 API 관찰자입니다.
description: MIP SDK는 거의 완전히 비동기로 설계되었습니다. 이 문서에서는 보호 API 관찰자를 구현해 비동기 상태에 사용하는 방법을 설명합니다.
author: BryanLa
ms.service: information-protection
ms.topic: conceptual
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: 35c0fb8eb358c5872ab378755d303425cc8e80a4
ms.sourcegitcommit: 2c4e72120213407516a49286368f9b2860505f56
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/30/2018
ms.locfileid: "50236818"
---
# <a name="microsoft-information-protection-sdk---protection-api-observers"></a>Microsoft Information Protection SDK - 보호 API 관찰자

보호 API에는 세 개의 관찰자 클래스가 있습니다. 관찰자 멤버는 가상이며 비동기 작업의 콜백을 처리하기 위해 재정의할 수 있습니다.

- [보호 프로필: `mip::ProtectionProfile::Observer`](reference/class_mip_ProtectionProfile_observer.md)
- [보호 엔진: `mip::ProtectionEngine::Observer`](reference/class_mip_ProtectionEngine_observer.md)
- [보호 처리기: `mip::ProtectionHandler::Observer`](reference/class_mip_Protectionhandler_observer.md)

비동기 작업이 완료되면 결과에 해당하는 `OnXxx()` 멤버 함수가 호출됩니다. `mip::ProtectionProfile::Observer`의 경우 `OnLoadSuccess()`, `OnLoadFailure()` 및 `OnAddEngineSuccess()`를 예로 들 수 있습니다.

아래 예제에서는 SDK 샘플에서도 사용되는 promise/future 패턴을 보여 주며, 원하는 콜백 동작을 구현하기 위해 확장할 수 있습니다. 

## <a name="protectionprofile-observer-implementation"></a>ProtectionProfile 관찰자 구현

다음 예제에서는 `mip::ProtectionProfile::Observer`에서 파생된 `ProtectionProfileObserverImpl` 클래스를 만들었습니다. 멤버 함수는 샘플 전체에서 사용되는 promise/future 패턴을 사용하도록 재정의되었습니다.

### <a name="protectionprofileobserverimpl-class-declaration"></a>ProtectionProfileObserverImpl 클래스 선언

헤더에서 `mip::ProtectionProfile::Observer`에서 파생하여 `ProtectionProfileObserverImpl`를 정의한 다음, 각 멤버 함수를 재정의합니다.

```cpp
//ProtectionProfileObserverImpl.h
class ProtectionProfileObserverImpl final : public mip::ProtectionProfile::Observer {
public:
  ProtectionProfileObserverImpl() { }
  void OnLoadSuccess(const shared_ptr<mip::ProtectionProfile>& profile, const shared_ptr<void>& context) override;
  void OnLoadFailure(const exception_ptr& error, const shared_ptr<void>& context) override;
  void OnAddEngineSuccess(const shared_ptr<mip::ProtectionEngine>& engine, const shared_ptr<void>& context) override;
  void OnAddEngineError(const exception_ptr& error, const shared_ptr<void>& context) override;
};
```

### <a name="protectionprofileobserverimpl-implementation"></a>ProtectionProfileObserverImpl 구현

구현 자체에서 각 관찰자 멤버 함수에 대해 수행할 작업을 간단하게 정의합니다.

각 멤버는 두 개의 매개 변수를 허용합니다. 첫 번째는 함수에서 처리 중인 클래스에 대한 공유 포인터입니다. `ProtectionObserver::OnLoadSuccess`는 `mip::ProtectionProtection`을 받을 것으로 예상하고, `ProtectionObserver::OnAddEngineSuccess`는 `mip::ProtectionEngine`을 받을 것으로 예상합니다.

두 번째는 *context*에 대한 공유 포인터입니다. 이 구현에서 컨텍스트는 `shared_ptr<void>`로 전달된 `std::promise`에 대한 참조입니다. 함수의 첫째 줄에서 이 컨텍스트를 `std::promise`로 캐스트한 다음, `promise`라는 개체에 저장합니다.

마지막으로, `promise->set_value()`를 설정하고 `mip::ProtectionProtection` 개체를 전달하여 future를 준비합니다.

```cpp
//protection_observers.cpp

void ProtectionProfileObserverImpl::OnLoadSuccess(
  const shared_ptr<mip::ProtectionProfile>& profile,
  const shared_ptr<void>& context) {
  auto loadPromise = static_cast<promise<shared_ptr<mip::ProtectionProfile>>*>(context.get());
  loadPromise->set_value(profile);
};

void ProtectionProfileObserverImpl::OnLoadFailure(const exception_ptr& error, const shared_ptr<void>& context) {
  auto loadPromise = static_cast<promise<shared_ptr<mip::ProtectionProfile>>*>(context.get());
  loadPromise->set_exception(error);
};

void ProtectionProfileObserverImpl::OnAddEngineSuccess(
  const shared_ptr<mip::ProtectionEngine>& engine,
  const shared_ptr<void>& context) {
  auto addEnginePromise = static_cast<promise<shared_ptr<mip::ProtectionEngine>>*>(context.get());
  addEnginePromise->set_value(engine);
};

void ProtectionProfileObserverImpl::OnAddEngineError(
  const exception_ptr& error,
  const shared_ptr<void>& context) {
  auto addEnginePromise = static_cast<promise<shared_ptr<mip::ProtectionEngine>>*>(context.get());
  addEnginePromise->set_exception(error);
};
```

SDK 클래스를 인스턴스화하거나 비동기 작업을 수행하는 함수를 사용하는 경우 관찰자 구현을 설정 생성자 또는 비동기 함수 자체에 전달합니다. `mip::ProtectionProfile::Settings` 개체를 인스턴스화할 때 생성자는 `mip::ProtectionProfile::Observer`를 매개 변수 중 하나로 사용합니다. 아래 예제에서는 `mip::ProtectionProfile::Settings` 생성자에서 사용되는 사용자 지정 `ProtectionProfileObserverImpl`를 보여 줍니다.

## <a name="protectionhandler-observer-implementation"></a>ProtectionHandler 관찰자 구현

보호 관찰자와 유사하게, `mip::ProtectionHandler`는 보호 작업 중 비동기 이벤트 알림을 처리하기 위한 `mip::ProtectionHandler::Observer` 클래스를 구현합니다. 이러한 구현은 위에 자세히 설명된 구현과 유사합니다. `ProtectionHandlerObserverImpl`는 부분적으로 아래에 정의되어 있습니다. 전체 구현은 [GitHub 샘플 리포지토리](https://azure.microsoft.com/resources/samples/?sort=0&term=mip+sdk)에서 찾을 수 있습니다.

### <a name="protectionhandlerobserverimpl-class-declaration"></a>ProtectionHandlerObserverImpl 클래스 선언

```cpp
//protection_observers.h

class ProtectionHandlerObserverImpl final : public mip::ProtectionHandler::Observer {
public:
  ProtectionHandlerObserverImpl() { }
  void OnCreateProtectionHandlerSuccess(const shared_ptr<mip::ProtectionHandler>& protectionHandler, const shared_ptr<void>& context) override;
  void OnCreateProtectionHandlerError(const exception_ptr& error, const shared_ptr<void>& context) override;
};
```

### <a name="protectionhandlerobserverimpl-partial-implementation"></a>ProtectionHandlerObserverImpl 부분 구현

이 샘플은 처음 두 함수만 제공하지만, 나머지 함수도 두 함수 및 `ProtectionObserver`와 유사한 패턴을 사용합니다.

```cpp
//protection_observers.cpp

void ProtectionHandlerObserverImpl::OnCreateProtectionHandlerSuccess(
  const shared_ptr<mip::ProtectionHandler>& protectionHandler,
  const shared_ptr<void>& context) {
  auto createProtectionHandlerPromise = static_cast<promise<shared_ptr<mip::ProtectionHandler>>*>(context.get());
  createProtectionHandlerPromise->set_value(protectionHandler);
};

void ProtectionHandlerObserverImpl::OnCreateProtectionHandlerError(
  const exception_ptr& error,
  const shared_ptr<void>& context) {
  auto createProtectionHandlerPromise = static_cast<promise<shared_ptr<mip::ProtectionHandler>>*>(context.get());
  createProtectionHandlerPromise->set_exception(error);
};
```

