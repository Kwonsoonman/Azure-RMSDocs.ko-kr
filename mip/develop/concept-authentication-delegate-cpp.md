---
title: 개념 - 인증 대리자 구현(C++)
description: 이 문서는 C++에서 인증 대리자를 구현하는 방법을 이해하는 데 도움이 됩니다.
author: BryanLa
ms.service: information-protection
ms.topic: conceptual
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: f80eb1f7ade5e024bd6d7d68775624b51f3f1809
ms.sourcegitcommit: fa0be701b85b1fba5e75428714bb4525dd739a93
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/07/2018
ms.locfileid: "51223911"
---
# <a name="microsoft-information-protection-sdk---implementing-an-authentication-delegate-c"></a>Microsoft Information Protection SDK - 인증 대리자 구현(C++)

MIP SDK는 인증 챌린지를 처리하고 토큰으로 응답하기 위한 인증 대리자를 구현합니다. MIP SDK 자체는 토큰 획득을 구현하지 않습니다. 토큰 획득 프로세스는 개발자의 책임이며 `mip::AuthDelegate` 클래스, 구체적으로 `AcquireOAuth2Token` 멤버 함수를 확장하여 수행됩니다.

## <a name="building-authdelegateimpl"></a>AuthDelegateImpl 빌드

기본 클래스 `mip::AuthDelegate`를 확장하기 위해 `sample::auth::AuthDelegateImpl`이라는 새 클래스를 만듭니다. 이 클래스는 `AcquireOAuth2Token` 기능을 구현하고 인증 매개 변수에서 사용할 생성자를 설정합니다.

### <a name="authdelegateimplh"></a>auth_delegate_impl.h

이 예제에서는 기본 생성자가 사용자 이름, 암호 및 응용 프로그램의 [응용 프로그램 ID](/azure/active-directory/develop/developer-glossary#application-id-client-id)만 허용합니다. 이는 private 변수 `mUserName`, `mPassword` 및 `mClientId`에 저장됩니다.

ID 공급자나 리소스 URI와 같은 정보는 적어도 `AuthDelegateImpl` 생성자에서 구현할 필요가 없다는 점에 유의해야 합니다. 이 정보는 `OAuth2Challenge` 개체에 `AcquireOAuth2Token`의 일부로 전달됩니다. 대신, 해당 세부 정보를 `AcquireOAuth2Token`의 `AcquireToken` 호출에 전달하겠습니다.

```cpp
//auth_delegate_impl.h
#include <string.h>
#include "mip/common_types.h"

namespace sample {
namespace auth {
class AuthDelegateImpl final : public mip::AuthDelegate { //extend mip::AuthDelegate base class
public:
  AuthDelegateImpl() = delete;

  //constructor accepts username, password, and clientId, all plain strings.
  AuthDelegateImpl(
    const std::string& userName,
    const std::string& password,
    const std::string& clientId
  );

  bool AcquireOAuth2Token(const mip::Identity& identity, const OAuth2Challenge& challenge, OAuth2Token& token) override;

private:
  std::string mUserName;
  std::string mPassword;
  std::string mClientId;
};

}
}
```

### <a name="authdelegateimplcpp"></a>auth_delegate_impl.cpp

`AcquireOAuth2Token`은 OAuth2 공급자 호출이 수행될 위치입니다. 아래 예제에서는 두 개의 `AcquireToken()` 호출이 있습니다. 실제로는 하나의 호출만 수행됩니다. 이러한 구현은 [다음 단계](#next-steps) 아래에 제공된 섹션에서 설명합니다.

```cpp
//auth_delegate_impl.cpp
#include "auth_delegate_impl.h"
#include <stdexcept>
#include "auth.h" //contains the auth class used later for token acquisition

using std::runtime_error;
using std::string;

namespace sample {
namespace auth {

AuthDelegateImpl::AuthDelegateImpl(
    const string& userName,
    const string& password,
    const string& clientId)
    : mUserName(userName),
    mPassword(password),
    mClientId(clientId) {
}

//Here we could simply add our token acquisition code to AcquireOAuth2Token
//Instead, that code is implemented in auth.h/cpp to demonstrate calling an external library
bool AuthDelegateImpl::AcquireOAuth2Token(
    const mip::Identity& /*identity*/, //This won't be used
    const OAuth2Challenge& challenge,
    const OAuth2Token& token) {

      //sample::auth::AcquireToken is the code where the token acquisition routine is implemented.
      //AcquireToken() returns a string that contains the OAuth2 token.

      //Simple example for getting hard coded token. Comment out if not used.
      string accessToken = sample::auth::AcquireToken();

      //Practical example for calling external OAuth2 library with provided authentication details.
      string accessToken = sample::auth::AcquireToken(mUserName, mPassword, mClientId, challenge.GetAuthority(), challenge.GetResource());  

      //set the passed in OAuth2Token value to the access token acquired by our provider
      token.SetAccessToken(accessToken);
      return true;
    }
}
}
```

## <a name="next-steps"></a>다음 단계

인증 구현을 완료하려면 `AcquireToken()` 함수의 코드 숨김을 빌드해야 합니다. 아래 예제에서는 토큰을 획득하는 몇 가지 방법에 대해 설명합니다.

- [단순/PowerShell 토큰 획득 예제](concept-authentication-acquire-token-ps.md)
- [Python 토큰 획득 예제](concept-authentication-acquire-token-py.md)
