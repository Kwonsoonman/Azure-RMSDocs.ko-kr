---
title: 개념 - MIP SDK의 관찰자.
description: MIP SDK는 거의 완전히 비동기로 설계되었습니다. 이 문서는 관찰자가 구현되고 비동기에 사용되는 방법을 이해하는 데 도움이 됩니다.
author: BryanLa
ms.service: information-protection
ms.topic: conceptual
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: 99f68383a4e697f4f8f04c19523ccb0fb50fa3c0
ms.sourcegitcommit: 1cf14852cd14ea91ac964fb03a901238455ffdff
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/28/2018
ms.locfileid: "47445564"
---
# <a name="microsoft-information-protection-sdk---observer-concepts"></a>Microsoft Information Protection SDK - 관찰자 개념

MIP SDK는 거의 완전히 비동기로 설계되었습니다. 예를 들어 네트워크 또는 파일 IO를 발생시키는 작업은 비동기적으로 수행됩니다. 이러한 비동기 이벤트에 대한 이벤트 알림을 처리하기 위해 SDK는 [관찰자 패턴](https://wikipedia.org/wiki/Observer_pattern)을 사용합니다. 

## <a name="implementation-overview"></a>구현 개요

비동기 작업을 수행할 개체를 생성하는 경우 `Observer` 클래스를 구현해야 합니다. 관찰자는 MIP SDK의 다양한 비동기 작업과 관련된 알림 이벤트를 수신하고 호출자에게 결과를 제공합니다.

각 `Observer` 클래스의 함수는 가상이며 선호하는 비동기 패턴에 대해 재정의됩니다. SDK는 `std::promise` 및 `std::future`를 통해 이벤트 알림 관찰자 패턴을 구현합니다.

각 클래스별 관찰자는 비동기 작업의 결과를 위해 성공 및 오류/실패 함수 집합을 포함합니다. ‘성공’ 함수는 작업과 연결된 개체를 반환합니다. ‘오류’/‘실패’ 함수는 작업이 실패한 원인에 대한 세부 정보를 포함하는 예외를 반환합니다.

예를 들어 `FileProfile`은 다음 두 가지 작업을 지원합니다. 

- `FileProfile::AddEngineAsync`를 통해 프로필에 새 엔진을 추가할 수 있습니다. 
- `FileProfile::UnloadEngineAsync`를 통해 프로필에서 엔진을 언로드할 수 있습니다.

비동기 작업마다 두 개의 `Observer` 함수가 구현되므로 `FileProfile`과 연결된 **네 개**의 `Observer` 메서드가 있다고 가정할 수 있습니다. 

- `FileProfileObserver::OnAddEngineSuccess()`
- `FileProfileObserver::OnAddEngineError()`
- `FileProfileObserver::OnUnloadEngineSuccess`
- `FileProfileObserver::OnUnloadEngineError()`과 같은 URL을 사용합니다. 

## <a name="mip-sdk-observer-classes"></a>MIP SDK 관찰자 클래스

MIP SDK 파일 API에는 다음 두 개의 관찰자가 있습니다.

* `mip::FileProfile::Observer`
* `mip::FileHandler::Observer`

MIP SDK 정책 API에는 단일 관찰자만 있습니다.

* `mip::Profile::Observer`

MIP SDK 보호 API에는 다음 세 개의 관찰자가 있습니다.

* `mip::ProtectionProfile::Observer`
* `mip::ProtectionEngine::Observer`
* `mip::ProtectionHandler::Observer`

## <a name="next-steps"></a>다음 단계

다양한 API에서 관찰자를 구현하고 사용하는 방법을 자세히 알아봅니다.

* [파일 API 관찰자(C++)](concept-async-observers-file-cpp.md)
* [정책 API 관찰자(C++)](concept-async-observers-policy-cpp.md)
* [보호 API 관찰자(C++)](concept-async-observers-protection-cpp.md)
