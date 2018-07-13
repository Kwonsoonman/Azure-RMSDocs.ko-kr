---
title: 소프트웨어 보호된 키-소프트웨어 보호된 키 마이그레이션 - AIP
description: AD RMS에서 Azure Information Protection으로 마이그레이션 경로에 포함되며, AD RMS 키가 소프트웨어로 보호되고 소프트웨어 보호된 테넌트 키를 사용하여 Azure Information Protection으로 마이그레이션하려는 경우에만 적용되는 지침에 대해 설명합니다.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 07/11/2018
ms.topic: article
ms.prod: ''
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 81a5cf4f-c1f3-44a9-ad42-66e95f33ed27
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: d9c35a175d32a53060c2876910df1608455814cf
ms.sourcegitcommit: 0fda9ea4a7b91d4bb3a9e4f9d5cc4106ce1e2d43
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/12/2018
ms.locfileid: "38973310"
---
# <a name="step-2-software-protected-key-to-software-protected-key-migration"></a>2단계: 소프트웨어 보호된 키-소프트웨어 보호된 키 마이그레이션

>*적용 대상: Active Directory Rights Management Services, [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [Office 365](http://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*


[AD RMS에서 Azure Information Protection으로 마이그레이션 경로](migrate-from-ad-rms-to-azure-rms.md)에 포함되며, AD RMS 키가 소프트웨어로 보호되고 소프트웨어 보호된 테넌트 키를 사용하여 Azure Information Protection으로 마이그레이션하려는 경우에만 적용되는 지침에 대해 설명합니다. 

선택한 구성 시나리오가 아닌 경우 [4단계. AD RMS에서 구성 데이터를 내보낸 후 Azure RMS로 가져오기](migrate-from-ad-rms-phase2.md#step-4-export-configuration-data-from-ad-rms-and-import-it-to-azure-information-protection)로 돌아가서 다른 구성을 선택합니다.

다음 절차에 따라 AD RMS 구성을 Azure Information Protection으로 가져옵니다. 그러면 Microsoft에서 관리하는 Azure Information Protection 테넌트 키가 생성됩니다.

## <a name="to-import-the-configuration-data-to-azure-information-protection"></a>구성 데이터를 Azure Information Protection으로 가져오려면

1. 인터넷에 연결된 워크스테이션에서 [Connect-AadrmService](/powershell/aadrm/vlatest/connect-aadrmservice) cmdlet을 사용하여 Azure Rights Management 서비스에 연결합니다.

    ```
    Connect-AadrmService
    ```
    메시지가 표시되면 [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)] 테넌트 관리자 자격 증명을 입력합니다(일반적으로 Azure Active Directory 또는 Office 365에 대한 전역 관리자 계정 사용).

2. [Import-AadrmTpd](/powershell/aadrm/vlatest/import-aadrmtpd) cmdlet을 사용하여 내보낸 각 트러스트된 게시 도메인(.xml) 파일을 업로드합니다. 예를 들어 AD RMS 클러스터를 암호화 모드 2로 업그레이드한 경우 추가 파일을 하나 이상 가져와야 합니다. 
    
    이 cmdlet을 실행하려면 각 구성 데이터 파일에 대해 이전에 지정한 암호가 필요합니다. 
    
    예를 들어 암호를 저장하려면 다음을 먼저 실행 합니다.
    
        $TPD_Password = Read-Host -AsSecureString
    
    지정한 암호를 입력하여 첫 번째 구성 데이터 파일을 내보냅니다. 그런 다음 E:\contosokey1.xml 등을 구성 파일에 사용하고 다음 명령을 실행한 후 이 작업을 수행하려는 것을 확인합니다.
    ```
    Import-AadrmTpd -TpdFile E:\contosokey1.xml -ProtectionPassword $TPD_Password -Verbose
    ```
    
3. 각 파일을 업로드한 경우 [Set-AadrmKeyProperties](/powershell/module/aadrm/set-aadrmkeyproperties)를 실행하여 AD RMS에서 현재 활성 SLC 키와 일치하는 가져온 키를 식별할 수 있습니다. 이 키는 Azure Rights Management 서비스의 활성 테넌트 키가 됩니다.

4.  [Disconnect-AadrmService](/powershell/aadrm/vlatest/disconnect-aadrmservice) cmdlet을 사용하여 Azure Rights Management 서비스에서 연결을 끊습니다.

    ```
    Disconnect-AadrmService
    ```

이제 [5단계. Azure Rights Management 서비스 활성화](migrate-from-ad-rms-phase2.md#step-5-activate-the-azure-rights-management-service)로 이동할 수 있습니다.

[!INCLUDE[Commenting house rules](../includes/houserules.md)]

