---
title: "Azure Information Protection에서 대칭 키를 갱신하는 방법"
description: "이 문서에서는 Azure Information Protection에서 대칭 키를 갱신하는 프로세스를 설명합니다."
keywords: 
author: lleonard-msft
manager: mbaldwin
ms.author: alleonar
ms.date: 03/27/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: a0b8c8f0-6ed5-48bb-8155-ac4f319ec178
ms.openlocfilehash: 159e5b58883490e4417ecbdb9815340c9ccaa66d
ms.sourcegitcommit: dca4534a0aa7f63c0c525c9a3ce445088d1362bb
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-renew-the-symmetric-key-in-azure-information-protection"></a>방법: Azure Information Protection에서 대칭 키 갱신

**대칭 키**는 대칭 키 암호화에서 메시지를 암호화하고 암호 해독하는 암호입니다.  

Azure AD(Azure Active Directory)에서 응용 프로그램을 나타내는 서비스 주체 개체를 만들 때 이 프로세스에서는 응용 프로그램을 확인하기 위한 256비트 대칭 키도 생성합니다. 이 대칭 키는 기본적으로 1년 동안 유효합니다. 

다음 단계는 대칭 키를 갱신하는 방법을 보여줍니다. 

## <a name="prerequisites"></a>전제 조건

* [Azure AD PowerShell 참조](https://docs.microsoft.com/powershell/msonline/)에 설명된 대로 Azure AD(Azure Active Directory) PowerShell 모듈을 설치해야 합니다.


## <a name="renewing-the-symmetric-key-after-expiry"></a>만료 후 대칭 키 갱신

응용 프로그램과 연결된 대칭 키가 만료되었을 때 새 서비스 주체를 만들 필요는 없습니다. 대신 Microsoft Online Services(MSol)에서 제공하는 [PowerShell commandlet](https://docs.microsoft.com/powershell/module/msonline)을 사용하여 기존 서비스 주체에 대한 새 대칭 키를 발급하면 됩니다.

이 프로세스를 보여 주기 위해 이미 [`New-MsolServicePrincipal`](https://docs.microsoft.com/powershell/msonline/v1/new-msolserviceprincipalcredential) 명령을 사용하여 새 서비스 주체를 만들었다고 가정합니다.

```
New-MsolServicePrincipalCredential -ServicePrincipalName "SupportExampleApp"
```

만들기 프로세스에서는 표시된 것처럼 대칭 키 및 **AppPrincipalId**를 만듭니다.

```
The following symmetric key was created as one was not supplied
ZYbF/lTtwE28qplQofCpi2syWd11D83+A3DRlb2Jnv8=

DisplayName : SupportExampleApp
ServicePrincipalNames : {7d9c1f38-600c-4b4d-8249-22427f016963}
ObjectId : 0ee53770-ec86-409e-8939-6d8239880518
AppPrincipalId : 7d9c1f38-600c-4b4d-8249-22427f016963
TrustedForDelegation : False
AccountEnabled : True
Addresses : []
KeyType : Symmetric
KeyId : acb9ad1b-36ce-4a7d-956c-40e5ac29dcbe
StartDate : 3/22/2017 3:27:53 PM
EndDate : 3/22/2018 3:27:53 PM
Usage : Verify
```

이 대칭 키는 2018/3/22, 오후 3:27:53에 만료됩니다. 현재 서비스 주체를 사용하려면 대칭 키를 갱신해야 합니다. 이렇게 하려면 [`New-MsolServicePrincipalCredential`](https://docs.microsoft.com/powershell/msonline/v1/new-msolserviceprincipalcredential) 명령을 사용합니다. 

```
New-MsolServicePrincipalCredential -AppPrincipalId 7d9c1f38-600c-4b4d-8249-22427f016963
```

그러면 지정된 **AppPrincipalId**에 대한 새 대칭 키가 만들어집니다.

```
The following symmetric key was created as one was not supplied ON8YYaMYNmwSfMX625Ei4eC6N1zaeCxbc219W090v28-
```
[`GetMsolServicePrincipalCredential`](https://docs.microsoft.com/powershell/msonline/v1/get-msolserviceprincipalcredential) 명령을 사용하여 표시된 것처럼 새 대칭 키가 올바른 서비스 주체와 연결되었는지 확인할 수 있습니다. 이 명령은 현재 서비스 주체와 연결된 모든 키를 나열합니다.

```
Get-MsolServicePrincipalCredential -AppPrincipalId 7d9c1f38-600c-4b4d-8249-22427f016963 -ReturnKeyValues $true

Type : Symmetric
Value :
KeyId : c1ac145f-e899-4c90-8a02-2cef40054fc5
StartDate : 3/24/2017 10:11:07 PM
EndDate : 3/24/2018 10:11:07 PM
Usage : Verify

Type : Symmetric
Value :
KeyId : acb9ad1b-36ce-4a7d-956c-40e5ac29dcbe
StartDate : 3/22/2017 3:27:53 PM
EndDate : 3/22/2018 3:27:53 PM
Usage : Verify
```

대칭 키가 실제로 올바른 서비스 주체와 연결되었는지 확인한 후 새 키로 서비스 주체의 인증 매개 변수를 업데이트할 수 있습니다. 

그런 다음 [`Remove-MsolServicePrincipalCredential`](https://docs.microsoft.com/powershell/msonline/v1/remove-msolserviceprincipalcredential) 명령을 사용하여 이전 대칭 키를 제거하고 `Get-MsolServicePrincipalCredential` 명령을 사용하여 키가 제거되었는지 확인할 수 있습니다.

```
Remove-MsolServicePrincipalCredential -KeyId acb9ad1b-36ce-4a7d-956c-40e5ac29dcbe -ObjectId 0ee53770-ec86-409e-8939-6d8239880518
```

## <a name="related-topics"></a>관련 항목

* [방법: 서비스 응용 프로그램이 클라우드 기반 RMS를 사용할 수 있도록 설정](how-to-use-file-api-with-aadrm-cloud.md)
* [Azure Active Directory MSOnline PowerShell 참조](https://docs.microsoft.com/powershell/msonline/)
