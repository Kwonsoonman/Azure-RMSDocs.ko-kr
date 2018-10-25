---
title: 개념 - MIP SDK의 인증.
description: 이 문서는 MIP SDK가 인증을 구현하는 방식과 클라이언트 응용 프로그램이 OAuth2 액세스 토큰 획득 로직을 제공하기 위한 요구 사항을 이해하는 데 도움이 될 것입니다.
author: BryanLa
ms.service: information-protection
ms.topic: conceptual
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: 288342c467574cf84c60e1211238b65a9e716b6c
ms.sourcegitcommit: 860955fb2c292b3ca5910cd41095363f58caf553
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48230525"
---
# <a name="microsoft-information-protection-sdk---authentication-concepts"></a>Microsoft Information Protection SDK - 인증 개념

MIP SDK의 인증은 `mip::AuthDelegate` 클래스를 확장해 선호하는 인증 방법을 구현함으로써 수행됩니다. `mip::AuthDelegate` 클래스에 포함된 정보는 다음과 같습니다.

- `mip::AuthDelegate::OAuth2Challenge` - OAuth2 기관 정보를 관리하고 이 정보를 클라이언트 응용 프로그램에 제공하는 클래스입니다.
- `mip::AuthDelegate::OAuth2Token` - (클라이언트 응용 프로그램에서) OAuth2 액세스 토큰 획득 및 토큰 저장소를 관리하는 클래스입니다.
- `mip::AuthDelegate::AcquireOAuth2Token()` - 순수 가상 함수로, 이 함수의 구현이 액세스 토큰 획득 방법을 결정합니다. SDK에서 호출하면 이 함수는 액세스 토큰을 획득한 다음, SDK의 인증 논리에 해당 토큰을 제공합니다.

`mip::AuthDelegate::AcquireOAuth2Token`은 다음 매개 변수를 수락해 토큰 획득 성공 여부를 나타내는 부울을 반환합니다.

- `mip::Identity`: 인증된 사용자 또는 서비스의 ID입니다(알려진 경우).
- `mip::AuthDelegate::OAuth2Challenge`: 두 개의 매개 변수 즉, **authority** 및 **resource**를 수락합니다. **Authority**는 토큰이 생성되는 서비스입니다. **리소스**는 액세스하려는 서비스입니다. SDK는 호출 시 이러한 매개 변수를 대리자에게 전달합니다.
- `mip::AuthDelegate::OAuth2Token`: 토큰 결과가 이 개체에 기록됩니다. 이 개체는 엔진이 로드될 때 SDK에서 사용합니다. 인증을 구현하는 경우가 아니라면 그 어디에서도 이 값을 가져오거나 설정하면 안 됩니다.

**중요:** 응용 프로그램에서는 `AcquireOAuth2Token`을 직접 호출하지 않습니다. SDK는 필요할 때 이 함수를 호출합니다.

## <a name="consent"></a>Consent

계정의 ID로 로그인해 보호되는 리소스/API에 액세스할 수 있는 권한을 부여하기 전에 Azure AD는 응용 프로그램에 동의를 요구합니다. 동의는 계정의 테넌트에서 특정 계정(사용자 동의) 또는 모든 계정(관리자 동의)에 대한 권한의 영구 확인으로 기록됩니다. 액세스하는 API, 응용 프로그램에서 요청하는 권한 및 로그인에 사용된 계정에 따라 다양한 시나리오에서 동의가 발생합니다. 

- 응용 프로그램이 등록된 테넌트와 ‘동일한 테넌트’의 계정(여러분 또는 관리자가 “권한 부여” 기능을 통해 명시적으로 사전 동의 후 액세스하지 않은 경우)
- ‘다른 테넌트’의 계정(응용 프로그램이 다중 테넌트로 등록되어 있고, 테넌트 관리자가 모든 사용자에 대해 사전에 동의하지 않은 경우)

`mip::Consent` 열거형 클래스는 응용 프로그램 개발자가 SDK에서 액세스하는 엔드포인트를 기반으로 사용자 정의 동의 환경을 제공할 수 있도록 하는 사용하기 쉬운 접근 방식을 구현합니다. 알림은 사용자에게 수집할 데이터, 데이터 제거 방법 또는 법률 또는 준수 정책에서 요구하는 기타 모든 정보에 대해 알립니다. 사용자가 동의하면 응용 프로그램은 계속 진행할 수 있습니다. 

### <a name="implementation"></a>구현

`mip::Consent` 기본 클래스를 확장하고 `mip::Consent` 열거 값 중 하나를 반환하도록 `GetUserConsent`를 구현하여 동의를 구현합니다. 

`mip::Consent`에서 파생된 개체는 `mip::FileProfile::Settings` 또는 `mip::ProtectionProfile::Settings` 생성자로 전달됩니다.

사용자가 동의를 제공해야 하는 작업을 수행하면 SDK는 `GetUserConsent` 메서드를 호출해 대상 URL을 매개 변수로 전달합니다. 이 매개 변수는 필수 정보를 사용자에게 표시하도록 구현하는 이 메서드 내에 있습니다. 사용자는 이러한 정보를 보고 서비스 사용에 동의할지 여부를 결정합니다. 

### <a name="consent-options"></a>동의 옵션

- **AcceptAlways**: 동의하고 결정 사항을 기억합니다.
- **Accept**:한 번 동의합니다.
- **Reject**: 동의하지 않습니다.

SDK에서 이 메서드로 사용자 동의를 요청하면 클라이언트 응용 프로그램이 사용자에게 URL을 표시해야 합니다. 클라이언트 응용 프로그램은 사용자 동의를 얻는 수단을 몇 가지 제공하고 사용자의 결정에 해당하는 적절한 동의 열거형을 반환해야 합니다.

### <a name="sample-implementation"></a>샘플 구현

#### <a name="consentdelegateimplh"></a>consent_delegate_impl.h

```cpp
class ConsentDelegateImpl final : public mip::ConsentDelegate {
public:
  ConsentDelegateImpl() = default;
  
  virtual mip::Consent GetUserConsent(const std::string& url) override;

};
```

#### <a name="consentdelegateimplcpp"></a>consent_delegate_impl.cpp

SDK에서 동의를 요구하면 *SDK*에서 `GetUserConsent` 메서드를 호출하고 URL이 매개 변수로 전달됩니다. 아래 샘플에서는 SDK가 제공된 URL에 연결되었다고 사용자에게 알리고, `Consent::AcceptAlways`를 반환합니다. 사용자에게 실제 선택 항목이 제공되지 않았기 때문에 이는 좋은 예는 아닙니다.

```cpp
Consent ConsentDelegateImpl::GetUserConsent(const string& url) {
  //Print the consent URL, ask user to choose
  std::cout << "SDK will connect to: " << url << std::endl;

  std::cout << "1) Accept Always" << std::endl;
  std::cout << "2) Accept" << std::endl;
  std::cout << "3) Reject" << std::endl;
  std::cout << "Select an option: ";
  char input;
  std::cin >> input;

  switch (input)
  {
  case '1':
    return Consent::AcceptAlways;
    break;
  case '2':
    return Consent::Accept;
    break;
  case '3':
    return Consent::Reject;
    break;
  default:
    return Consent::Reject;
  }  
}
```

## <a name="next-steps"></a>다음 단계

간단하게 설명하기 위해 대리자를 나타내는 샘플이 외부 스크립트를 호출해 토큰 획득을 구현합니다. 이 스크립트는 다른 유형의 스크립트, 오픈 소스 OAuth2 라이브러리 또는 사용자 지정 OAuth2 라이브러리로 바꿀 수 있습니다.

- [PowerShell을 사용하여 액세스 토큰 획득](concept-authentication-acquire-token-ps.md)
- [Python을 사용하여 액세스 토큰 획득](concept-authentication-acquire-token-py.md)
