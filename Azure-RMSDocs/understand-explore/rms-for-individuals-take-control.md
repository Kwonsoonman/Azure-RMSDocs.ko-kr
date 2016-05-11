---
# required metadata

title: 관리자가 개인용 RMS에 대해 생성된 계정을 제어하는 방법 | Azure RMS
description:
keywords:
author: cabailey
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: a83880d0-f0f9-4a32-9e00-2f6635d7cc8d

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: esaggese
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---



# 관리자가 개인용 RMS용으로 만들어진 계정을 제어하는 방법

조직의 개인용 RMS 구독을 유료 구독으로 전환하지 않으려는 경우 다음과 같은 방법으로 조직용으로 만들어진 Azure 디렉터리에서 계속해서 사용자 계정을 제어할 수 있습니다.

-   Azure Active Directory 및 Active Directory 도메인 서비스 인프라를 위한 디렉터리 통합 솔루션을 구현합니다. 사용자가 권한 관리를 사용하기 위한 새 계정을 만들지 않아도 되도록 계정과 암호를 동기화할 수 있습니다. 그러면 온-프레미스 암호 정책이 새 Azure 사용자 계정에 적용됩니다. 사용자가 권한 관리를 사용하기 위한 다른 암호를 기억하지 않아도 되도록 암호도 동기화할 수 있습니다.

-   사용자가 개인용 RMS 구독을 위해 Azure 권한 관리에 사용 등록하는 것을 방지할 수 있습니다. 대부분의 경우 이렇게 하는 데에는 이점이 별로 없습니다. 왜냐하면 사용자가 보호 메커니즘 없이 파일을 공유하거나(회사를 위험에 빠뜨릴 수 있음) IT 부서에서 해당 데이터에 액세스할 수 있는 옵션이 제공되지 않는 다른 파일 보호 메커니즘을 사용할 수 있기 때문입니다. 그럼에도 불구하고 사용자가 개인용 RMS를 사용하기 위해 등록하는 것을 방지하려면 조직의 Azure 디렉터리 소유권을 가진 후에 다음 중 하나를 수행합니다.

    -   모든 사용자가 개인용 RMS를 포함한 셀프서비스 구독에 등록하지 못하게 차단합니다.  현재 서비스에서는 이를 설정할 수 없으며 이 설정은 셀프서비스 프로세스를 사용하는 모든 Azure 구독에 적용됩니다. 이 작업을 수행하려면 Azure Active Directory용 Windows PowerShell 모듈의 [Set-MsolCompanySettings](http://technet.microsoft.com/library/dn194127.aspx) cmdlet에서 **AllowAdHocSubscriptions** 매개 변수를 false로 설정합니다. 예: **Set-MsolCompanySettings -AllowAdHocSubscriptions $false**

    -   사용자가 Azure에서 새 계정을 만들지 못하도록 합니다. 이렇게 하면 Azure에 계정이 이미 있는 사용자만 개인용 RMS를 포함한 셀프서비스 구독에 등록할 수 있습니다.  이 작업을 수행하려면 Azure Active Directory용 Windows PowerShell 모듈의 [Set-MsolCompanySettings](http://technet.microsoft.com/library/dn194127.aspx) cmdlet에서 **AllowEmailVerifiedUsers** 매개 변수를 false로 설정합니다. 예: **Set-MsolCompanySettings -AllowEmailVerifiedUsers $false -AllowAdHocSubscriptions $true**

    -   Active Directory 도메인 서비스 인프라를 Azure Active Directory와 동기화합니다. 이렇게 하면 사용자가 개인용 RMS 등의 셀프서비스 구독에 등록할 때 새 계정이 만들어지지 않으며, 이전에 Azure 디렉터리에서 만들어진 계정을 삭제하거나 사용하지 않을 수 있습니다.

Azure 디렉터리에서 사용자 계정을 제어하거나, 사용자가 개인용 RMS에 등록하지 못하도록 하려면 Azure 구독을 얻은 후 디렉터리를 소유해야 합니다. Azure 구독이 없는 경우 무료로 얻을 수 있습니다. 디렉터리가 셀프 서비스 프로세스 중에 자동으로 만들어진 경우에는 해당 디렉터리를 만드는 데 사용한 도메인을 소유해야 합니다. Azure에 이미 디렉터리가 있지만 사용자가 조직에서 사용하는 새 도메인을 지정한 경우 해당 도메인을 기존 디렉터리에 병합합니다. 자세한 내용은 [Azure 셀프서비스 등록이란?](https://azure.microsoft.com/documentation/articles/active-directory-self-service-signup/)을 참조하세요.


## 다음 단계

관리자 대신 사용자가 Azure Active Directory에 개인용 RMS에 대한 자신의 계정을 만들 수 있다면 이 작업을 수행했는지 어떻게 확인할 수 있을까요?  [사용자가 개인용 RMS에 등록했는지 확인하는 방법](rms-for-individuals-identify-sign-up.md)을 참조하세요.


<!--HONumber=Apr16_HO3-->


