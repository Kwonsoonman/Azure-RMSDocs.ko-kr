---
title: 개념 - Python을 사용하여 액세스 토큰 획득.
description: 이 문서는 Python을 사용하여 OAuth2 액세스 토큰을 획득하는 방법을 이해하는 데 도움이 됩니다. 이 작업은 인증 대리자 구현에 필요합니다.
author: BryanLa
ms.service: information-protection
ms.topic: conceptual
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: 4d6db3d2bd2e2b980770027e07104f7528264e66
ms.sourcegitcommit: fa0be701b85b1fba5e75428714bb4525dd739a93
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/07/2018
ms.locfileid: "51223888"
---
# <a name="acquire-an-access-token-python"></a>액세스 토큰 획득(Python)

이 예제에서는 외부 Python 스크립트를 호출하여 OAuth2 토큰을 획득하는 방법을 보여 줍니다. 이 작업은 인증 대리자 구현에 필요합니다.

이 코드는 프로덕션용은 아니지만 개발 및 인증 개념을 이해하는 데 사용될 수 있습니다. 샘플은 여러 플랫폼에서 사용할 수 있습니다.

## <a name="prerequisites"></a>전제 조건

아래 샘플을 실행하려면 다음을 완료해야 합니다.

- Python 2.7 설치
- 프로젝트에 utils.h/cpp를 구현합니다. 
- auth.py를 프로젝트에 추가해야 하며, 빌드 시 이진과 동일한 디렉터리에 있어야 합니다.

## <a name="sampleauthacquiretoken"></a>sample::auth::AcquireToken()

단순 인증 예제에서는 매개 변수를 사용하지 않고 하드 코드된 토큰 값을 반환하는 단순 `AcquireToken()` 함수를 보여 주었습니다. 이 예제에서는 인증 매개 변수를 허용하고 외부 Python 스크립트를 호출하여 토큰을 반환하도록 AcquireToken()을 오버로드합니다.

### <a name="authh"></a>auth.h

auth.h에서 `AcquireToken()`이 재정의되며, 재정의된 함수 및 업데이트된 매개 변수는 다음과 같습니다.

```cpp
//auth.h
#include <string>

namespace sample {
  namespace auth {
    std::string AcquireToken();

    std::string AcquireToken(
        const std::string& userName, //A string value containing the user's UPN.
        const std::string& password, //The user's password in plaintext
        const std::string& clientId, //The AAD client ID of your application.
        const std::string& resource, //The resource URL for which an OAuth2 token is required. Provided by challenge object.
        const std::string& authority); //The authentication authority endpoint. Provided by challenge object.
    }
}
```

처음 세 개의 매개 변수는 사용자 입력에 의해 제공되거나 애플리케이션에 하드 코드됩니다. 마지막 두 개의 매개 변수는 SDK에서 인증 대리자에 제공합니다. 


### <a name="authcpp"></a>auth.cpp

auth.cpp에서 재정의된 함수 정의를 추가한 다음, Python 스크립트를 호출하는 데 필요한 코드를 정의합니다. 이 함수는 제공된 모든 매개 변수를 허용하고 Python 스크립트에 전달합니다. 스크립트는 토큰을 실행하고 문자열 형식으로 반환합니다.

```cpp
#include "auth.h"
#include "utils.h"

#include <fstream>
#include <functional>
#include <memory>
#include <string>

using std::string;
using std::runtime_error;

namespace sample {
    namespace auth {

    string AcquireToken() { //ignore in this sample
    }

    //This function implements token acquisition in the application by calling an external Python script.
    //The Python script requires username, password, clientId, resource, and authority.
    //Username, Password, and ClientId are provided by the user/developer
    //Resource and Authority are provided as part of the OAuth2Challenge object that is passed in by the SDK to the AuthDelegate.
    string AcquireToken(
        const string& userName,
        const string& password,
        const string& clientId,
        const string& resource,
        const string& authority) {

    string cmd = "python";
    if (sample::FileExists("auth.py"))
        cmd += " auth.py -u ";

    else
        throw runtime_error("Unable to find auth script.");

    cmd += userName;
    cmd += " -p ";
    cmd += password;
    cmd += " -a ";
    cmd += authority;
    cmd += " -r ";
    cmd += resource;
    cmd += " -c ";
    cmd += (!clientId.empty() ? clientId : "0edbblll-8773-44de-b87c-b8c6276d41eb");

    string result = sample::Execute(cmd.c_str());
    if (result.empty())
        throw runtime_error("Failed to acquire token. Ensure Python is installed correctly.");

    return result;
    }
    }
}

```

## <a name="python-script"></a>Python 스크립트

이 스크립트는 단순 http 요청을 통해 직접 인증 토큰을 획득합니다. 이 스크립트는 샘플 앱에서 사용할 인증 토큰을 획득하는 수단으로만 포함되었으며 프로덕션 코드에서 사용하기 위한 것이 아닙니다. 스크립트는 이전의 일반 사용자 이름/암호 http 인증을 지원하는 테넌트에 대해서만 작동합니다. MFA 또는 인증서 기반 인증은 실패합니다.

```python
import getopt
import sys
import json
import urllib
import urllib2
import re

def printUsage():
  print('auth.py -u <username> -p <password> -a <authority> -r <resource> -c <clientId>')

def main(argv):
  try:
    options, args = getopt.getopt(argv, 'hu:p:a:r:c:')
  except getopt.GetoptError:
    printUsage()
    sys.exit(-1)

  username = ''
  password = ''
  authority = ''
  resource = ''
  clientId = ''

  for option, arg in options:
    if option == '-h':
      printUsage()
      sys.exit()
    elif option == '-u':
      username = arg
    elif option == '-p':
      password = arg
    elif option == '-a':
      authority = arg
    elif option == '-r':
      resource = arg
    elif option == '-c':
      clientId = arg

  if username == '' or password == '' or authority == '' or resource == '' or clientId == '':
    printUsage()
    sys.exit(-1)

  # Find everything after the last '/' and replace it with 'token'
  if not authority.endswith('token'):
    regex = re.compile('^(.*[\/])')
    match = regex.match(authority)
    authority = match.group()
    authority = authority + 'token'

  # Build REST call
  headers = {
    'Content-Type': 'application/x-www-form-urlencoded',
    'Accept': 'application/json'
  }

  params = {
    'resource': resource,
    'client_id': clientId,
    'grant_type': 'password',
    'username': username,
    'password': password
  }

  req = urllib2.Request(
    url = authority,
    headers = headers,
    data = urllib.urlencode(params))

  f = urllib2.urlopen(req)
  response = f.read()
  f.close()
  sys.stdout.write(json.loads(response)['access_token'])

if __name__ == '__main__':
  main(sys.argv[1:])
```

## <a name="update-acquireoauth2token"></a>AcquireOAuth2Token 업데이트

마지막으로, `AuthDelegateImpl`의 `AcquireOAuth2Token` 함수를 업데이트하여 재정의된 `AcquireToken` 함수를 호출합니다. 리소스 및 권한 URL은 `challenge.GetResource()` 및 `challenge.GetAuthority()`를 읽어 얻습니다. `OAuth2Challenge`는 엔진을 추가할 때 인증 대리자에게 전달됩니다. 이 작업은 SDK에서 수행되며 개발자 쪽의 추가 작업이 필요하지 않습니다. 

```cpp
bool AuthDelegateImpl::AcquireOAuth2Token(
    const mip::Identity& /*identity*/,
    const OAuth2Challenge& challenge,
    OAuth2Token& token) {

    //call our AcquireToken function, passing in username, password, clientId, and getting the resource/authority from the OAuth2Challenge object
    string accessToken = sample::auth::AcquireToken(mUserName, mPassword, mClientId, challenge.GetResource(), challenge.GetAuthority());
    token.SetAccessToken(accessToken);
    return true;
}
```

`engine`이 추가되면 SDK에서는 AcquireOAuth2Token 함수를 호출하고, 챌린지를 전달하고, Python 스크립트를 실행하고, 토큰을 수신한 다음, 토큰을 서비스에 제공합니다.


