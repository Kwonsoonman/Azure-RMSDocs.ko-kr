---
title: 빠른 시작 - C++ MIP SDK를 사용하여 MIP(Microsoft Information Protection) 테넌트의 민감도 레이블 나열
description: Microsoft Information Protection C++ SDK를 사용하여 테넌트의 민감도 레이블을 나열하는 방법을 보여 주는 빠른 시작입니다.
author: BryanLa
ms.service: information-protection
ms.topic: quickstart
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: fc8d4b43bae9a7b74edef10947ef5aa22e5d1267
ms.sourcegitcommit: d677088db8588fb2cc4a5d7dd296e76d0d9a2e9c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/03/2018
ms.locfileid: "48251780"
---
# <a name="quickstart-list-sensitivity-labels-c"></a>빠른 시작: 민감도 레이블(C++)

이 빠른 시작은 MIP 파일 API를 사용하여 조직에 대해 구성된 민감도 레이블을 나열하는 방법을 보여 줍니다.

## <a name="prerequisites"></a>전제 조건

다음 필수 구성 요소를 아직 완료하지 않은 경우 먼저 완료합니다.

- 전체 [빠른 시작: 먼저, 클라이언트 응용 프로그램 초기화(C++)](quick-app-initialization-cpp.md)를 수행합니다. 그러면 스타터 Visual Studio 솔루션이 빌드됩니다. 이 “민감도 레이블 나열” 빠른 시작은 적절한 스타터 솔루션을 생성하기 위해 이전 빠른 시작을 기반으로 합니다.
- 옵션: [분류 레이블](concept-classification-labels.md) 개념을 검토합니다.

## <a name="add-logic-to-list-the-sensitivity-labels"></a>민감도 레이블을 나열하는 논리 추가

파일 엔진 개체를 사용하여 조직의 민감도 레이블을 나열하는 논리를 추가합니다. 

1. 이전 “빠른 시작: 클라이언트 응용 프로그램 초기화(C++)” 기사에서 만든 Visual Studio 솔루션을 엽니다.

2. **솔루션 탐색기**를 사용하여 프로젝트에서 `main()` 메서드의 구현이 포함된 .cpp 파일을 엽니다. 파일 이름은 프로젝트를 만드는 동안 지정한 프로젝트 이름과 같습니다. 

3. 파일 맨 위에서 다음 `using` 지시문을 `using mip::FileEngine;` 뒤에 추가합니다.

   ```cpp
   using std::endl;
   ```

4. `main()` 본문이 끝나가는 위치에서 `catch` 블록의 닫는 괄호 `}` 아래와 `return 0;` 위(여기서 이전 빠른 시작에서 벗어남)에 다음 코드를 삽입합니다.

   ```cpp
   // List sensitivity labels
   cout << "\nSensitivity labels for your organization:\n";
   auto labels = engine->ListSensitivityLabels();
   for (const auto& label : labels)
   {
      cout << label->GetName() << " : " << label->GetId() << endl;

      for (const auto& child : label->GetChildren())
      {
        cout << "->  " << child->GetName() << " : " << child->GetId() << endl;
      }
   }
   system("pause");
   ``` 

## <a name="create-a-powershell-script-to-generate-access-tokens"></a>액세스 토큰을 생성하는 PowerShell 스크립트를 만듭니다.

다음 PowerShell 스크립트를 사용하여 SDK에서 요청한 대로 액세스 토큰을 생성합니다. 이 스크립트는 이전에 “MIP SDK 설정 및 구성”에서 설치한 ADAL.PS 모듈의 `Get-ADALToken` cmdlet을 사용합니다. 

1. PowerShell 스크립트 파일(확장명: .ps1)을 만들고 다음 스크립트를 복사해 이 파일에 붙여넣습니다.

   - Azure AD 앱 등록에 지정된 값과 일치하도록 `$appId` 및 `$redirectUri` 변수를 업데이트합니다. 
   - `$authority` 및 `$resourceUrl`는 다음 섹션에서 업데이트됩니다.

   ```powershell
   $authority = '<authority-url>'                   # Enforced by MIP SDK
   $resourceUrl = '<resource-url>'                  # Enforced by MIP SDK; matches a resource/API URL requested in the app registration
   $appId = '0edbblll-8773-44de-b87c-b8c6276d41eb'  # App ID of the Azure AD app registration
   $redirectUri = 'bltest://authorize'              # Must match the redirect URI of the Azure AD app registration
   $response = Get-ADALToken -Resource $resourceUrl -ClientId $appId -RedirectUri $redirectUri -Authority $authority -PromptBehavior:RefreshSession 
   $response.AccessToken | clip                     # Copy the access token text to the clipboard
   ```

2. 클라이언트 응용 프로그램에서 요청한 대로 나중에 실행할 수 있도록 스크립트 파일을 저장하세요.

## <a name="build-and-test-the-application"></a>응용 프로그램 빌드 및 테스트

최종적으로, 클라이언트 응용 프로그램을 빌드하고 테스트합니다. 

1. F6 키(**솔루션 빌드**)를 사용하여 클라이언트 응용 프로그램을 빌드합니다. 빌드 오류가 없으면 F5 키(**디버깅 시작**)를 사용하여 응용 프로그램을 실행합니다.

2. 프로젝트가 성공적으로 빌드 및 실행되면 응용 프로그램은 SDK가 `AcquireOAuth2Token()` 메서드를 호출할 때마다 액세스 토큰을 묻는 메시지를 표시합니다. 메시지가 여러 번 나타나는데, 요청된 값이 동일한 경우에는 이전에 생성한 토큰을 재사용할 수 있습니다.

   ```console
   Run the PowerShell script to generate an access token using the following values, then copy/paste it below:
   Set $authority to: https://login.windows.net/common/oauth2/authorize
   Set $resourceUrl to: https://syncservice.o365syncservice.com/
   Be sure to sign in with user account: user1@tenant.onmicrosoft.com
   Enter access token:
   ```

3. 위의 프롬프트에 응답을 제공하려면 다시 PowerShell 스크립트로 돌아가 다음과 같이 수행합니다.

   - `$authority` 및 `$resourceUrl` 변수를 업데이트합니다. 이 변수 2개는 2단계의 콘솔 출력에서 지정한 값과 일치해야 합니다. 이러한 값은 `AcquireOAuth2Token()`의 `challenge` 매개 변수로 다음과 같이 MIP SDK에서 제공합니다.
     - `$authority`는 `https://login.windows.net/common/oauth2/authorize`여야 합니다.
     - `$resourceUrl`은 `https://syncservice.o365syncservice.com/` 또는 `https://aadrm.com`이어야 합니다.
   - PowerShell 스크립트를 실행합니다. `Get-ADALToken` cmdlet은 다음 예제와 유사한 Azure AD 인증 프롬프트를 트리거합니다. 2단계의 콘솔 출력에서 제공된 것과 동일한 계정을 지정합니다. 로그인에 성공하면 액세스 토큰이 클립보드에 배치됩니다.

     [![Visual Studio에서 토큰 로그인 획득](media/quick-file-list-labels-cpp/acquire-token-sign-in.png)](media/quick-file-list-labels-cpp/acquire-token-sign-in.png#lightbox)

   - 또한 로그인 계정으로 실행 중인 경우 응용 프로그램이 MIP API에 액세스하도록 허용하려면 동의해야 할 수 있습니다. 이 문제는 (“MIP SDK 설정 및 구성”의 설명대로) Azure AD 응용 프로그램 등록에 사전 동의하지 않았거나 (응용 프로그램이 등록된 테넌트와) 다른 테넌트의 계정으로 로그인한 경우 발생합니다. **동의**를 클릭하기만 하면 동의가 기록됩니다.

     [![Visual Studio 동의](media/quick-file-list-labels-cpp/acquire-token-sign-in-consent.png)](media/quick-file-list-labels-cpp/acquire-token-sign-in-consent.png#lightbox)

4. 액세스 토큰을 제공한 후에는 콘솔 출력에 다음 예제와 유사한 민감도 레이블이 표시되어야 합니다.

   ```console
   Non-Business : 87ba5c36-17cf-14793-bbc2-bd5b3a9f95cz
   Public : 83867195-f2b8-2ac2-b0b6-6bb73cb33afz
   General : f42a3342-8706-4288-bd31-ebb85995028z
   Confidential : 074e457c-5848-4542-9a6f-34a182080e7z
   Highly Confidential : f55c2dea-db0f-47cd-8520-a52e1590fb6z

   Press any key to continue . . .
   ```

   > [!NOTE]
   > 다음 빠른 시작에서 사용할 것이므로 하나 이상의 민감도 레이블의 ID(예: `f42a3342-8706-4288-bd31-ebb85995028z`)를 복사해 저장해 두세요.

## <a name="troubleshooting"></a>문제 해결

### <a name="problems-during-execution-of-powershell-script"></a>PowerShell 스크립트 실행 중 발생한 문제 

| 요약 | 오류 메시지 | 해결 방법 |
|---------|---------------|----------|
| 응용 프로그램 등록 또는 PowerShell 스크립트(AADSTS50011)에서 리디렉션 URI가 잘못됨 |AADSTS50011: 요청에 지정된 응답 URL이 응용 프로그램에 대해 구성된 응답 URL과 일치하지 않음: ‘ac6348d6-0d2f-4786-af33-07ad46e69bfc’. | 다음 단계 중 하나를 수행하여 사용된 재지정 URI를 확인합니다.<br><br><li>PowerShell 스크립트와 일치하도록 Azure AD 응용 프로그램 구성의 리디렉션 URI를 업데이트하세요. [MIP SDK 설정 및 구성](setup-configure-mip.md#register-a-client-application-with-azure-active-directory)을 참조해 리디렉션 URI 속성을 올바르게 구성했는지 확인하세요.<br><li>응용 프로그램 등록과 일치하도록 PowerShell 스크립트에서 `redirectUri` 변수를 업데이트하세요. |
| 로그인 계정이 잘못됨(AADSTS50020) | AADSTS50020: ID 공급자 ‘ https://sts.windows.net/72f988bl-86f1-41af-91ab-2d7cd011db47/’의 사용자 계정 ‘user@domain.com’이 테넌트의 ‘조직 이름’에 없고 해당 테넌트에 응용 프로그램 ‘0edbblll-8773-44de-b87c-b8c6276d41eb’에 액세스할 수 없습니다. | 다음 단계 중 하나를 수행합니다.<br><br><li>PowerShell 스크립트를 다시 실행합니다. 하지만 Azure AD 응용 프로그램이 등록된 것과 동일한 테넌트의 계정을 사용해야 합니다.<br><li>로그인 계정이 올바른 경우에는 PowerShell 호스트 세션이 다른 계정으로 이미 인증되어 있을 수 있습니다. 이 경우 스크립트 호스트를 종료한 다음, 다시 열어 다시 실행해 보세요.<br><li>이 빠른 시작을 웹앱(네이티브 앱 대신)에서 사용하는데, 다른 테넌트의 계정을 사용해 로그인해야 하는 경우 다중 테넌트를 사용하도록 Azure AD 응용 프로그램 등록이 활성화되어 있는지 확인하세요. 응용 프로그램 등록에서 “매니페스트 편집” 기능을 사용하여 확인하고 `"availableToOtherTenants": true,`를 지정하는지 확인할 수 있습니다. |
| 응용 프로그램 등록에서 권한이 잘못됨(AADSTS65005) | AADSTS65005: 리소스가 잘못되었습니다. 클라이언트가 클라이언트 응용 프로그램 등록에서 요청된 권한에 나열되지 않은 리소스에 대한 액세스 권한을 요청했습니다. 클라이언트 앱 ID: 0edbblll-8773-44de-b87c-b8c6276d41eb. 요청의 리소스 값: https://syncservice.o365syncservice.com/. 리소스 앱 ID: 870c4f2e-85b6-4d43-bdda-6ed9a579b725. 앱 등록의 유효한 리소스 목록: 00000002-0000-0000-c000-000000000000. | Azure AD 응용 프로그램 구성에서 사용 권한 요청을 업데이트하세요. 응용 프로그램 등록에서 사용 권한 요청을 올바르게 구성했는지 확인하려면 [MIP SDK 설정 및 구성](setup-configure-mip.md#register-a-client-application-with-azure-active-directory)을 참조하세요. |

### <a name="problems-during-execution-of-c-application"></a>C++ 응용 프로그램 실행 중 발생한 문제

| 요약 | 오류 메시지 | 해결 방법 |
|---------|---------------|----------|
| 액세스 토큰이 잘못됨 | *An exception occurred... is the access token incorrect/expired?<br><br>Failed API call: profile_add_engine_async Failed with: [class mip::PolicySyncException] Failed acquiring policy, Request failed with http status code: 401, x-ms-diagnostics: [2000001;reason="OAuth token submitted with the request cannot be parsed.";error_category="invalid_token"], correlationId:[35bc0023-3727-4eff-8062-000006d5d672]'<br><br>C:\VSProjects\MipDev\Quickstarts\AppInitialization\x64\Debug\AppInitialization.exe (process 29924) exited with code 0.<br><br>Press any key to close this window . . .* | 프로젝트가 성공적으로 빌드되었지만 왼쪽과 유사하게 출력되는 경우 `AcquireOAuth2Token()` 메서드에 유효하지 않거나 만료된 토큰이 있을 수 있습니다. [토큰 획득 논리 업데이트](#update-the-token-acquisition-logic-with-a-valid-access-token)로 돌아가 액세스 토큰을 다시 생성한 다음, `AcquireOAuth2Token()`을 다시 업데이트하고 다시 빌드/테스트해 보세요. 또한 [jwt.ms](https://jwt.ms/) 단일 페이지 웹 응용 프로그램을 사용하여 토큰 및 해당 클레임을 검사하고 확인할 수도 있습니다. |
| 민감도 레이블이 구성되지 않음 | 해당 없음 | 프로젝트가 성공적으로 빌드되었으나 콘솔 창에 출력되지 않은 경우, 조직의 민감도 레이블이 올바르게 구성되어 있는지 확인하세요. 자세한 내용은 “레이블 분류 체계 및 보호 설정 정의”에서 [MIP SDK 설정 및 구성](setup-configure-mip.md)을 참조하세요.  |

## <a name="next-steps"></a>다음 단계

조직에 대한 민감도 레이블을 나열하는 방법을 배웠으므로 다음 빠른 시작을 수행해 보세요.

> [!div class="nextstepaction"]
> [민감도 레이블 설정 및 가져오기](quick-file-set-get-label-cpp.md)
