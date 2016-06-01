---
# required metadata

title: 방법&#58; Azure 응용 프로그램 ID 가져오기 | Azure RMS
description: Microsoft Rights Management SDK 4.2를 사용하여 RMS 사용 응용 프로그램을 만들려면 RMS 팀과 계약을 작성해야 합니다.
keywords:
author: bruceperlerms
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 0fe9dc-bc91-4018-b28d-2db293a3eaa2
# optional metadata

#ROBOTS:
audience: developer
#ms.devlang:
ms.reviewer: shubhamp
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# 방법: Azure 응용 프로그램 ID 가져오기

Microsoft Rights Management SDK 4.2를 사용하여 RMS 사용 응용 프로그램을 만들려면 RMS 팀과 계약을 작성해야 합니다.

## 개요

MS RMS SDK 4.2를 사용하여 RMS 사용 앱을 만들고 릴리스하려면 RMS 팀과 서비스 사용 계약도 작성해야 합니다. RMLA(권한 관리 사용권 계약)라고도 하는 이 계약에서는 앱의 동작(비즈니스 규칙 준수)을 통해 사용자 및/또는 콘텐츠 소유자를 대신해서 확인할 콘텐츠 보호 계약을 준수하는 방법을 안내합니다. RMS 사용 앱의 작성자로 RMS 팀과 작성한 계약은 이 계약을 나타내고 앱이 Azure AD 인증 서비스에 연결할 수 있도록 하는 "Azure 응용 프로그램 ID"의 현재 상태에 따라 적용됩니다.

## 처리

앱 ID를 만들고 RMS 팀과의 사용 계약에 서명하려면 다음 단계를 따르세요.

-   [Azure에서 앱 ID를 만드는 방법](https://msdn.microsoft.com/en-us/library/azure/dn132599.aspx) 항목의 지침에 따라 앱 ID를 만듭니다.
-   RMS 팀에 RMLA 프로세스를 시작하도록 요청하고 "앱 ID"를 <askipteam@microsoft.com>으로 보냅니다..
-   RMLA에 서명하여 RMS 팀에 다시 보냅니다.
-   이제 서명된 RMLA가 있으므로 *clientID* 매개 변수를 통해 인증 라이브러리를 호출할 때 응용 프로그램 ID를 전달해야 합니다.

    [iOS/OS X 코드 예제](ios-os-x-code-examples.md) 항목에서 인증 호출은 이런 방식으로 수행됩니다.


    // ADAL을 사용하여 검색 토큰
        [context acquireTokenWithResource:authenticationParameters.resource
                                 clientId:appClientId
                              redirectUri:redirectURI
                                   userId:authenticationParameters.userId
                          completionBlock:^(ADAuthenticationResult *result)



**참고** RMS 팀이 60일 내에 서명된 RMLA를 받지 못할 경우 앱이 Azure 인증 시스템에 인증할 수 없습니다.

 

 

 


<!--HONumber=Apr16_HO4-->


