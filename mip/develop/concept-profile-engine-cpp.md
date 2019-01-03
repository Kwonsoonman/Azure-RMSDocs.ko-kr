---
title: 개념 - MIP SDK의 핵심 개념 - 프로필 및 엔진
description: 이 문서는 애플리케이션 초기화 중에 작성되는 프로필 및 엔진이라는 핵심 SDK 개념을 이해하는 데 도움이 됩니다.
author: BryanLa
ms.service: information-protection
ms.topic: conceptual
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: 6f11944e7cceed39423af2a8104ce044d1f6eec6
ms.sourcegitcommit: 823a14784f4b34288f221e3b3cb41bbd1d5ef3a6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/29/2018
ms.locfileid: "47453421"
---
# <a name="microsoft-information-protection-sdk---profile-and-engine-object-concepts"></a>Microsoft Information Protection SDK - 프로필 및 엔진 개체 개념

## <a name="profiles"></a>프로필

프로필은 MIP SDK의 모든 작업에 대한 루트 클래스입니다. 세 개의 API 중 하나를 사용하기 전에 클라이언트 애플리케이션에서 프로필을 만들어야 합니다. 이후 모든 작업은 프로필에 의해 또는 프로필에 ‘추가된’ 다른 개체에 의해 수행됩니다.

MIP SDK에 세 가지 유형의 프로필이 있습니다.

- [`PolicyProfile`](reference/class_mip_policyprofile.md): MIP 정책 API용 프로필 클래스입니다.
- [`ProtectionProfile`](reference/class_mip_protectionprofile.md): MIP 보호 API용 프로필 클래스입니다.
- [`FileProfile`](reference/class_mip_fileprofile.md): MIP 파일 API용 프로필 클래스입니다.

소비 애플리케이션에서 사용되는 API에 따라 사용해야 할 프로필 클래스가 결정됩니다.

프로필 자체는 다음 기능을 제공합니다.

- SDK 상태의 저장소 위치를 정의합니다. 상태 데이터에는 사용자 세부 정보, 다운로드한 사용자 정책, 로그 및 원격 분석 데이터가 포함됩니다.
- 상태를 메모리에 로드할지 아니면 디스크에 유지할지 정의합니다.
- `mip::AuthDelegate`를 적용하여 인증을 처리합니다.
- SDK를 사용하는 앱의 애플리케이션 ID 및 식별 이름을 설정합니다.

### <a name="profile-settings"></a>프로필 설정

- `Path`: 로깅, 원격 분석 및 기타 영구 상태가 저장되는 파일 경로입니다.
- `useInMemoryStorage`: 주의 상태를 메모리에 저장할지 아니면 디스크에 저장할지 정의하는 부울입니다.
- `authDelegate`: `mip::AuthDelegate` 클래스의 공유 포인터입니다. 
- `consentDelegate`: `mip::ConsentDelegate` 클래스의 공유 포인터입니다. 
- `observer`: 프로필 `Observer` 구현에 대한 공유 포인터입니다(`PolicyProfile`, `ProtectionProfile`, `EngineProfile`).
- `applicationInfo`: `mip::ApplicationInfo` 개체입니다. SDK를 사용 중인 애플리케이션에 대한 정보입니다.

## <a name="engines"></a>엔진

파일, 프로필 및 보호 API에서 엔진은 특정 ID를 대신하여 수행되는 작업을 위한 인터페이스를 제공합니다. 애플리케이션에 로그인하는 사용자별로 하나의 엔진이 프로필 개체에 추가됩니다. 엔진에서 수행하는 모든 작업은 해당 ID의 컨텍스트에서 이루어집니다.

SDK에는 API마다 하나씩 총 세 개의 엔진 클래스가 있습니다. 다음 목록은 엔진 클래스 및 각 엔진 클래스와 연관된 몇 개의 함수를 보여 줍니다.

- [`mip::ProtectionEngine`]
- [`mip::PolicyEngine`](reference/class_mip_policyengine.md)
  - `ListSensitivityLabels()`: 로드된 엔진의 레이블 목록을 가져옵니다.
  - `GetSensitivityLabel()`: 기존 콘텐츠에서 레이블을 가져옵니다.
  - `ComputeActions()`: 레이블 ID 및 선택적인 메타데이터가 제공되면 특정 항목에 대해 발생해야 하는 작업의 목록을 반환합니다.
- [`mip::FileEngine`](reference/class_mip_fileengine.md)
  - `ListSensitivityLabels()`: 로드된 엔진의 레이블 목록을 가져옵니다.
  - `CreateFileHandler()`: 특정 파일 또는 스트림의 `mip::FileHandler`를 만듭니다.

### <a name="engine-states"></a>엔진 상태

엔진에는 다음 두 상태 중 하나가 있을 수 있습니다.

- `CREATED`: 작성됨은 필수 백 엔드 서비스를 호출한 후 SDK에 로컬 상태 정보가 충분하다는 것을 나타냅니다.
- `LOADED`: SDK에서 엔진이 작동 가능한 데 필요한 데이터 구조를 빌드했습니다.

임의의 작업을 수행하려면 엔진이 작성 및 로드되어야 합니다. `Profile` 클래스는 `AddEngineAsync`, `RemoveEngineAsync`, `UnloadEngineAsync` 등의 엔진 관리 메서드를 노출합니다.

다음 표는 가능한 엔진 상태 및 상태를 변경할 수 있는 메서드를 설명합니다.

|         | NONE              | CREATED           | LOADED         |
|---------|-------------------|-------------------|----------------|
| NONE    |                   |                   | AddEngineAsync |
| CREATED | DeleteEngineAsync |                   | AddEngineAsync |
| LOADED  | DeleteEngineAsync | UnloadEngineAsync |                |

### <a name="engine-id"></a>엔진 ID

각 엔진에는 모든 엔진 관리 작업에 사용되는 고유 식별자인 `id`가 있습니다. 애플리케이션이 `id`를 제공할 수 있거나, 애플리케이션에서 제공되지 않은 경우 SDK가 새 고유 식별자를 생성합니다. 기타 모든 엔진 속성(예: ID 정보의 메일 주소)은 SDK에 대한 불투명 페이로드입니다. SDK는 다른 속성을 고유하게 유지하기 위한 논리를 수행하거나 다른 제한 조건을 적용하지 않습니다.

### <a name="engine-management-methods"></a>엔진 관리 메서드

위에서 언급한 대로 SDK에는 `AddEngineAsync`, `DeleteEngineAsync`, `UnloadEngineAsync`라는 세 개의 엔진 관리 메서드가 있습니다.

#### <a name="addengineasync"></a>AddEngineAsync

이 메서드는 기존 엔진을 로드하거나 아직 로컬 상태에 없는 경우 새 엔진을 만듭니다.

애플리케이션에서 `id`를 제공하지 않으면 `AddEngineAsync`가 `id`를 새로 생성합니다. 그런 다음, 해당 `id`의 엔진이 로컬 상태에 이미 있는지 확인하고 있는 경우 해당 엔진을 로드합니다. 엔진이 로컬 상태에 ‘없는’ 경우에는 필요한 API 및 백 엔드 서비스를 호출하여 새 엔진이 만들어집니다.

두 경우 모두, 메서드가 성공하면 엔진이 로드되어 사용할 준비가 됩니다.

#### <a name="deleteengineasync"></a>DeleteEngineAsync

지정된 `id`를 가진 엔진을 삭제합니다. 엔진의 모든 추적은 로컬 상태에서 제거됩니다.

#### <a name="unloadengineasync"></a>UnloadEngineAsync

지정된 `id`를 가진 엔진에 대한 메모리 내 데이터 구조를 언로드합니다. 이 엔진의 로컬 상태는 그대로 유지되며 `AddEngineAsync`로 다시 로드할 수 있습니다.

이 메서드를 사용하면 곧 사용될 것으로 예상되지 않는 엔진을 언로드하는 등 애플리케이션이 주의하여 메모리를 사용합니다.

## <a name="next-steps"></a>다음 단계

- 다음으로, [인증 개념](concept-authentication-cpp.md) 및 [관찰자](concept-async-observers.md)에 대해 자세히 알아보겠습니다. MIP는 확장 가능한 인증 모델을 제공하고, 관찰자는 비동기 이벤트에 대해 이벤트 알림을 제공하는 데 사용됩니다. 두 가지 모두 기본적이며 모든 MIP API 집합에 적용됩니다.
- 이번에는 파일, 정책 및 보호 API에 대한 프로필 및 엔진 개념을 살펴보겠습니다.
  - [파일 API 프로필 개념](concept-profile-engine-file-profile-cpp.md)
  - [파일 API 엔진 개념](concept-profile-engine-file-engine-cpp.md)
  - [정책 API 프로필 개념](concept-profile-engine-file-profile-cpp.md)
  - [정책 API 엔진 개념](concept-profile-engine-file-engine-cpp.md)
  - [보호 API 프로필 개념](concept-profile-engine-file-profile-cpp.md)
  - [보호 API 엔진 개념](concept-profile-engine-file-engine-cpp.md)  
