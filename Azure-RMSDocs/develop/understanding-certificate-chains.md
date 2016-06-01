---
# required metadata

title: 인증서 체인 이해 | Azure RMS
description: 권한 사용 응용 프로그램에는 공개 키 쌍과 Microsoft 인증서가 신뢰할 수 있는 루트에 있는 인증서 체인이 필요합니다.
keywords:
author: bruceperlerms
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 6AEA2162-82BF-4867-9285-111CD3FCD2F6
# optional metadata

#ROBOTS:
audience: developer
#ms.devlang:
ms.reviewer: shubhamp
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# 인증서 체인 이해

권한 사용 응용 프로그램을 개발하려면 공개 키 쌍과 Microsoft 인증서가 신뢰할 수 있는 루트에 있는 인증서 체인이 필요합니다.

## 인증서 종류

RMS(권한 관리 서비스) 환경에서 사용되는 각 라이선스 및 인증서는 Microsoft CA(인증 기관) 인증서로 돌아가는 인증서 체인으로 구성되어 있습니다. Microsoft는 라이선스 또는 인증서를 중첩할 수 있는 두 개의 체인인 사전 프로덕션 인증서 체인과 프로덕션 체인을 제공합니다. Microsoft와 *프로덕션 사용권 계약*에 서명하지 않고 작업할 수 있도록 응용 프로그램을 개발하는 경우 사전 프로덕션 계층 구조를 사용하는 것이 좋습니다. RMS 서버도 사전 프로덕션용으로 구성해야 합니다.

응용 프로그램을 릴리스하기 전에 프로덕션 체인으로 전환해야 합니다. 사전 프로덕션 인증서로 보호된 콘텐츠는 프로덕션 인증서보다 덜 안전합니다.

공개 및 개인 키와 사전 프로덕션 인증서는 SDK의 `%MsipcSDKDir%\Bin` 폴더에 있는 다음 파일에 포함되어 있습니다.

- **ISVTier5AppSigningPrivKey.dat**에는 응용 프로그램 개발 중에 사용할 매니페스트에 서명하는 데 사용되는 개인 키가 들어 있습니다.
- **ISVTier5AppSigningPubKey.dat**에는 사전 프로덕션 인증서 계층 구조에 서명된 공개 키가 들어 있습니다.
- **ISVTier5AppSignSDK_Client.xml**에는 응용 프로그램 개발 중에 사용할 매니페스트를 생성하는 데 사용되는 사전 프로덕션 인증서가 들어 있습니다.

 

인증서와 개인 키를 사용하여 응용 프로그램의 프로세스 공간에 로드될 수 있거나 로드되어야 하는 파일과 로드되지 않아야 하는 파일을 식별하는 매니페스트를 만들고 서명합니다. 그런 다음 매니페스트가 플랫폼에 의해 로드됩니다.

응용 프로그램 개발 중에 사전 프로덕션 인증서를 사용했는지 여부에 관계없이 응용 프로그램을 릴리스할 준비가 되면 새로운 키 쌍을 생성하고, Microsoft에서 발급한 프로덕션 인증서를 받고, 새 개인 키와 인증서를 사용하여 응용 프로그램 매니페스트를 만들고 서명해야 합니다.

인증서 체인 및 응용 프로그램 서명 작업에 대한 자세한 내용은 [프로덕션 환경으로 전환](switching-to-the-production-environment.md)을 참조하세요.

## 관련 항목

* [개발자 개념](ad-rms-concepts-nav.md)
* [프로덕션 환경으로 전환](switching-to-the-production-environment.md)
 

 


<!--HONumber=May16_HO2-->


