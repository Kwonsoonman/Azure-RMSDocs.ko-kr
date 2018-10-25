---
title: 개념 - PowerShell을 사용하여 액세스 토큰 획득.
description: 이 문서는 PowerShell을 사용하여 OAuth2 액세스 토큰을 획득하는 방법을 이해하는 데 도움이 됩니다. 이 작업은 인증 대리자 구현에 필요합니다.
author: BryanLa
ms.service: information-protection
ms.topic: conceptual
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: 3206fb99cd72c5d609375ec673e7798d33c735c3
ms.sourcegitcommit: 823a14784f4b34288f221e3b3cb41bbd1d5ef3a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/29/2018
ms.locfileid: "47453387"
---
# <a name="acquire-an-access-token-powershell"></a>액세스 토큰 획득(PowerShell)

이 예제에서는 외부 PowerShell 스크립트를 호출하여 OAuth2 토큰을 획득하는 방법을 보여 줍니다. 이 작업은 인증 대리자 구현에 필요합니다.

이 코드는 프로덕션용은 아니지만 개발 및 인증 개념을 이해하는 데 사용될 수 있습니다. 

## <a name="sampleauthacquiretoken"></a>sample::auth::AcquireToken()

### <a name="authh"></a>auth.h

AcquireToken이라는 단일 함수를 만듭니다. 이 자습서에서 반환 값은 하드 코드되므로 매개 변수가 수신되지 않고 단순히 문자열(토큰)만 반환됩니다.

```cpp
//auth.h
#include <string>

namespace sample {
  namespace auth {
    std::string AcquireToken();
  }
}
```

### <a name="authcpp"></a>auth.cpp

원본 파일은 이후 단계에서 하드 코드될 토큰 값을 반환합니다.

```cpp
//auth.cpp
#include <string>
#include "auth.h"

namespace sample {
  namespace auth {
    string AcquireToken() {
      std::string mToken = "your token here";
      return mToken;
    }
  }
}
```

## <a name="mint-a-token"></a>토큰 발급

마지막으로, mToken 변수에 넣을 토큰을 발급합니다. 아래 예에서는 Windows에서 ADAL 및 PowerShell을 통해 OAuth2 토큰을 신속하게 획득하는 데 사용할 수 있는 PowerShell 스크립트를 보여 줍니다. 이 토큰은 Office 365 보안 및 준수 센터 엔드포인트에만 부여됩니다. 따라서 리소스 URL이 업데이트되지 않는 경우 보호 작업이 실패합니다. 레이블 지정과 보호를 모두 테스트하려는 경우 이 시점에서 [다음 단계](#next-steps)로 건너뛰는 것이 좋습니다.

### <a name="install-adalpshttpswwwpowershellgallerycompackagesadalps31942-from-ps-gallery"></a>PS 갤러리에서 [ADAL.PS](https://www.powershellgallery.com/packages/ADAL.PS/3.19.4.2) 설치

```PowerShell
Install-Module -Name ADAL.PS
```

### <a name="use-get-adaltoken-to-obtain-the-access-token"></a>Get-ADALToken을 사용하여 액세스 토큰 획득

```PowerShell
#Install the ADAL.PS package if it's not installed.
if(!(Get-Package adal.ps)) { Install-Package -Name adal.ps }

$authority = "https://login.windows.net/common/oauth2/authorize" 
#this is the security and compliance center endpoint
$resourceUrl = "https://dataservice.o365filtering.com"
#clientId and redirectUri are from the RMS Sharing Application. 
#Once custom app registration is supported, a custom id and uri will be required. 
$clientId = "6b069eef-9dde-4a29-b402-8ce866edc897"
$redirectUri = "com.microsoft.rms-sharing-for-win://authorize"

$response = Get-ADALToken -Resource $resourceUrl -ClientId $clientId -RedirectUri $redirectUri -Authority $authority -PromptBehavior:Always
$response.AccessToken | clip
```

토큰을 `string mToken`의 값으로 클립보드에서 auth.cpp로 복사하여 위의 “your token here” 대신 넣습니다. 다음 단계에 얼마나 오래 걸리는지에 따라 스크립트를 다시 실행해야 할 수도 있습니다.


