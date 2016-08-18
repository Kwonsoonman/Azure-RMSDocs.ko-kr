---
title: "2단계&colon; HSM 보호된 키-HSM 보호된 키 마이그레이션 | Azure RMS"
description: 
keywords: 
author: cabailey
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: c5bbf37e-f1bf-4010-a60f-37177c9e9b39
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 7a9c8b531ec342e7d5daf0cbcacd6597a79e6a55
ms.openlocfilehash: 7b531ebba1923653cb37c70a02fa888a40e96528


---

# 2단계: HSM 보호된 키-HSM 보호된 키 마이그레이션

*적용 대상: Active Directory Rights Management Services, Azure 권한 관리*


이 지침은 [AD RMS에서 Azure 권한 관리로의 마이그레이션 경로](migrate-from-ad-rms-to-azure-rms.md)에 포함되며, AD RMS 키가 HSM으로 보호되고 HSM 보호된 테넌트 키를 사용하여 Azure 권한 관리로 마이그레이션하려는 경우에만 적용됩니다. 

선택한 구성 시나리오가 아닌 경우 [2단계. AD RMS에서 구성 데이터를 내보낸 후 Azure RMS로 가져오기](migrate-from-ad-rms-phase1.md#step-2-export-configuration-data-from-ad-rms-and-import-it-to-azure-rms)로 돌아가서 다른 구성을 선택합니다.

> [!NOTE]
> 이러한 지침에서는 AD RMS 키가 모듈로 보호되어 있다고 가정합니다. 이것은 일반적인 경우입니다. AD RMS 키가 OCS로 보호되어 있는 경우 이러한 지침을 수행하기 전에 [AskIPTeam@microsoft.com](mailto: askipteam@microsoft.com?subject=AD%20RMS%20migration%20with%20OCS-protected%20key)에 문의하세요.

HSM 키와 AD RMS 구성을 Azure RMS로 가져오는 두 부분으로 된 절차이며, 결과적으로 직접 관리하는 Azure RMS 테넌트 키가 생성됩니다(BYOK).

먼저 Azure RMS로 전송할 수 있도록 HSM 키를 패키지한 다음에 구성 데이터와 함께 가져와야 합니다.

## 1부: HSM 키를 Azure RMS로 전송할 수 있도록 패키지

1.  [Azure 권한 관리 테넌트 키 계획 및 구현](plan-implement-tenant-key.md)의 [BYOK(Bring Your Own Key) 구현](plan-implement-tenant-key.md#implementing-your-azure-rights-management-tenant-key) 섹션에 있는 단계를 수행합니다. 다음 경우를 제외하고 **인터넷을 통해 테넌트 키 생성 및 전송** 절차를 따릅니다.

    -   AD RMS 배포에서 생성된 동일한 키가 이미 있으므로 **테넌트 키 생성**단계는 따르지 마세요. Thales 설치의 AD RMS 서버에서 사용되는 키를 식별하고, 마이그레이션 중에 이 키를 사용해야 합니다. Thales 암호화된 키 파일 이름은 일반적으로 서버에서 로컬로 **key_(keyAppName)_(keyIdentifier)**입니다.

    -   Add-AadrmKey 명령을 사용하는 **Azure RMS로 테넌트 키 전송** 단계는 따르지 마세요.  대신 내보낸 트러스트된 게시 도메인을 업로드할 때 Import-AadrmTpd 명령을 사용하여 준비된 HSM 키를 전송합니다.

2.  인터넷에 연결된 워크스테이션의 Windows PowerShell 세션에서 Azure RMS 서비스에 다시 연결합니다.

이제 Azure RMS용 HSM 키를 준비했으므로 HSM 키 파일과 AD RMS 구성 데이터를 가져올 수 있습니다.

## 2부: Azure RMS로 HSM 키 및 구성 데이터 가져오기

1.  인터넷에 연결된 워크스테이션의 Windows PowerShell 세션에서 처음에 내보낸 트러스트된 게시 도메인(.xml) 파일을 업로드합니다. 트러스트된 게시 도메인이 여러 개 있어 .xml 파일이 두 개 이상 있는 경우, 마이그레이션 후 Azure RMS에서 콘텐츠를 보호하는 데 사용할 HSM 키에 해당하는 내보낸 트러스트된 게시 도메인이 포함되어 있는 파일을 선택하세요. 다음 명령을 사용합니다.

    ```
    Import-AadrmTpd -TpdFile <PathToTpdPackageFile> -ProtectionPassword -HsmKeyFile <PathToBYOKPackage> -Active $True -Verbose
    ```
    예: **Import -TpdFile E:\no_key_tpd_contosokey1.xml  -HsmKeyFile E:\KeyTransferPackage-contosokey.byok -ProtectionPassword -Active $true -Verbose**

    이전에 지정한 암호를 입력하라는 메시지가 표시되면 입력한 후 이 작업을 수행할 것임을 확인합니다.

2.  명령이 완료되면 트러스트된 게시 도메인을 내보내 만든 나머지 각 .xml 파일에 대해 1단계를 반복합니다. 하지만 이러한 파일의 경우 Import 명령을 실행할 때 **-Active**를 **false**로 설정합니다.  예: **Import -TpdFile E:\contosokey2.xml -HsmKeyFile E:\KeyTransferPackage-contosokey.byok -ProtectionPassword -Active $false -Verbose**

3.  [Disconnect-AadrmService](http://msdn.microsoft.com/library/windowsazure/dn629416.aspx) cmdlet를 사용하여 Azure RMS 서비스에서 연결을 끊습니다.

    ```
    Disconnect-AadrmService
    ```

이제 [3단계. RMS 테넌트 활성화](migrate-from-ad-rms-phase1.md#step-3-activate-your-rms-tenant)로 이동할 준비가 되었습니다.




<!--HONumber=Jul16_HO3-->


