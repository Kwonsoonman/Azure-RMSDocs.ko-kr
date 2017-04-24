---
title: "소프트웨어 보호된 키-소프트웨어 보호된 키 마이그레이션 - AIP"
description: "AD RMS에서 Azure Information Protection으로 마이그레이션 경로에 포함되며, AD RMS 키가 소프트웨어로 보호되고 소프트웨어 보호된 테넌트 키를 사용하여 Azure Information Protection으로 마이그레이션하려는 경우에만 적용되는 지침에 대해 설명합니다."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 04/06/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 81a5cf4f-c1f3-44a9-ad42-66e95f33ed27
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 60370cc34184b28f5cdecf6ad51f9ba58dd4816a
ms.sourcegitcommit: 77b0936bea2700eb12b580e5738e077d447d5686
translationtype: HT
---
# <a name="step-2-software-protected-key-to-software-protected-key-migration"></a>2단계: 소프트웨어 보호된 키-소프트웨어 보호된 키 마이그레이션

>*적용 대상: Active Directory Rights Management Services, Azure Information Protection, Office 365*


[AD RMS에서 Azure Information Protection으로 마이그레이션 경로](migrate-from-ad-rms-to-azure-rms.md)에 포함되며, AD RMS 키가 소프트웨어로 보호되고 소프트웨어 보호된 테넌트 키를 사용하여 Azure Information Protection으로 마이그레이션하려는 경우에만 적용되는 지침에 대해 설명합니다. 

선택한 구성 시나리오가 아닌 경우 [4단계. AD RMS에서 구성 데이터를 내보낸 후 Azure RMS로 가져오기](migrate-from-ad-rms-phase2.md#step-4-export-configuration-data-from-ad-rms-and-import-it-to-azure-information-protection)로 돌아가서 다른 구성을 선택합니다.

다음 절차에 따라 AD RMS 구성을 Azure Information Protection으로 가져옵니다. 그러면 Microsoft에서 관리하는 Azure Information Protection 테넌트 키가 생성됩니다.

## <a name="to-import-the-configuration-data-to-azure-information-protection"></a>구성 데이터를 Azure Information Protection으로 가져오려면

1. 인터넷에 연결된 워크스테이션에서 [Connect-AadrmService](/powershell/aadrm/vlatest/connect-aadrmservice) cmdlet을 사용하여 Azure Rights Management 서비스에 연결합니다.

    ```
    Connect-AadrmService
    ```
    메시지가 표시되면 [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)] 테넌트 관리자 자격 증명을 입력합니다(일반적으로 Azure Active Directory 또는 Office 365에 대한 전역 관리자 계정 사용).

2. [Import-AadrmTpd](/powershell/aadrm/vlatest/import-aadrmtpd) cmdlet을 사용하여 처음에 내보낸 트러스트된 게시 도메인(.xml) 파일을 업로드합니다. 트러스트된 게시 도메인이 여러 개 있어 .xml 파일이 두 개 이상 있는 경우, 마이그레이션 후 Azure Information Protection에서 콘텐츠를 보호하는 데 사용할 내보낸 트러스트된 게시 도메인이 포함되어 있는 파일을 선택하세요. 다음 명령을 사용합니다.

    ```
    Import-AadrmTpd -TpdFile <PathToTpdPackageFile> -ProtectionPassword <secure string> -Active $True -Verbose
    ```
    [ConvertTo-SecureString -AsPlaintext](https://technet.microsoft.com/library/hh849818.aspx) 또는 [Read-Host](https://technet.microsoft.com/library/hh849945.aspx)를 사용하여 암호를 보안 문자열로 지정할 수 있습니다. ConvertTo-SecureString을 사용하고 암호에 특수 문자가 있는 경우 작은따옴표 안에 암호를 입력하거나 특수 문자를 이스케이프합니다.
    
    예를 들어 먼저 **$TPD_Password = Read-Host -AsSecureString**을 실행하고 이전에 지정한 암호를 입력합니다. 그런 다음 **Import-AadrmTpd -TpdFile E:\contosokey1.xml -ProtectionPassword $TPD_Password -Active $true -Verbose**를 실행합니다. 메시지가 표시되면 이 작업을 수행할 것인지 확인합니다.
    
3.  명령이 완료되면 트러스트된 게시 도메인을 내보내 만든 나머지 각 .xml 파일에 대해 3단계를 반복합니다. 예를 들어 AD RMS 클러스터를 암호화 모드 2로 업그레이드한 경우 추가 파일을 하나 이상 가져와야 합니다. 하지만 이러한 파일의 경우 Import 명령을 실행할 때 **-Active**를 **false**로 설정합니다. 예: **Import-AadrmTpd -TpdFile E:\contosokey2.xml -ProtectionPassword $TPD_Password -Active $false -Verbose**

4.  [Disconnect-AadrmService](/powershell/aadrm/vlatest/disconnect-aadrmservice) cmdlet을 사용하여 Azure Rights Management 서비스에서 연결을 끊습니다.

    ```
    Disconnect-AadrmService
    ```


이제 [5단계. Azure Information Protection 테넌트 활성화](migrate-from-ad-rms-phase2.md#step-5-activate-the-azure-rights-management-service)로 이동할 준비가 되었습니다.

[!INCLUDE[Commenting house rules](../includes/houserules.md)]

