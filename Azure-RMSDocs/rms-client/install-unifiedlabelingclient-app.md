---
title: Azure Information Protection 통합 레이블 지정 클라이언트 다운로드 및 설치(미리 보기)
description: 문서와 이메일을 분류하고 보호할 수 있도록 Windows용 Azure Information Protection 통합 레이블 지정 클라이언트의 미리 보기 버전을 설치하는 사용자에 대한 지침입니다.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 10/17/2018
ms.topic: conceptual
ms.service: information-protection
ms.assetid: 2bf09690-9dba-43b7-9e0a-0110915d4081
ms.reviewer: eymanor
ms.suite: ems
ms.openlocfilehash: 5d2f5c07ebc7f4844b0d35879ae00c7b9066cb6d
ms.sourcegitcommit: 6a732226a3c97fc06fcf815fbbb24a2e2faae209
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/16/2018
ms.locfileid: "49359003"
---
# <a name="download-and-install-the-azure-information-protection-unified-labeling-client-preview"></a>Azure Information Protection 통합 레이블 지정 클라이언트 다운로드 및 설치(미리 보기)

>*적용 대상: Active Directory Rights Management Services, [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), Windows 10, Windows 8.1, Windows 8, Windows 7 SP1*

> [!NOTE]
> 이 클라이언트는 미리 보기 상태이며 변경될 수 있습니다. Office 365 Security & Compliance Center에서 민감도 레이블을 사용하여 통합 레이블 지정 저장소를 사용하고 정책을 다운로드합니다. 이러한 레이블은 사용하려면 먼저 Security & Compliance Center에서 게시되어야 합니다. [추가 정보](https://techcommunity.microsoft.com/t5/Security-Privacy-and-Compliance/Announcing-the-availability-of-unified-labeling-management-in/ba-p/262492)

문서 및 이메일에 레이블을 지정하고 보호하도록 이 미리 보기 클라이언트를 설치하려면 PC의 로컬 관리자여야 합니다.

또한,

- Azure Information Protection 통합 레이블 지정 클라이언트에는 최소한 Microsoft .NET Framework 4.6.2 버전이 필요하며, 이 버전이 없으면 설치 관리자는 이 필수 구성 요소를 다운로드한 후 설치하려고 합니다. 이 필수 구성 요소가 클라이언트 설치의 일부로 설치된 경우 컴퓨터를 다시 시작해야 합니다.

- Windows 7 SP1이 설치되어 있는 경우 Azure Information Protection 통합 레이블 지정 클라이언트에는 특정 업데이트(KB 2533623)가 필요합니다. 사용 중인 PC에 이 업데이트가 필요하지만 설치되어 있지 않은 경우 설치는 완료되지만 Azure Information Protection 통합 레이블 지정 클라이언트에 이 업데이트가 필요하다는 메시지가 표시됩니다. 이 업데이트를 설치하지 않으면 Azure Information Protection 통합 레이블 지정 클라이언트의 일부 기능을 사용할 수 없습니다. 

## <a name="to-download-and-install-the-azure-information-protection-unified-labeling-client"></a>Azure Information Protection 통합 레이블 지정 클라이언트를 다운로드하고 설치하려면

Azure Information Protection 통합 레이블 지정 클라이언트를 설치하기 전에 사용자에 대해 게시된 Office 365 Security & Compliance Center에서 민감도 레이블이 있는지 확인합니다. 

Azure Portal에서 Azure Information Protection에 대해 현재 게시된 레이블이 있으면 Security & Compliance Center에 [이러한 레이블을 마이그레이션](../configure-policy-migrate-labels.md)할 수 있습니다.

1. [Microsoft 다운로드 센터](https://www.microsoft.com/en-us/download/details.aspx?id=57440)에서 미리 보기 클라이언트를 다운로드합니다.

2. 다운로드된 실행 파일 **AzInfoProtection_For_Unified_Labeling.exe**를 실행합니다. 계속하라는 메시지가 표시되면 **예**를 클릭합니다.    

3. **Azure Information Protection 클라이언트 설치** 페이지에서 다음을 수행합니다.     
    - 클라우드에 연결할 수 없지만 데모용으로 로컬 정책을 사용하여 Azure Information Protection의 클라이언트 쪽을 확인해 보려면 데모 정책을 설치하는 옵션을 선택합니다. 클라이언트가 Office 365 Security & Compliance Center에 연결되면 이 데모 정책이 조직의 레이블 정책으로 바뀝니다.

    - 사용 조건에 동의하면 **동의함**을 클릭합니다.    

4. 계속할지 묻는 메시지가 나타나면 **예**를 클릭하고 설치가 완료될 때까지 기다립니다.    

6. **닫기**를 클릭합니다. Azure Information Protection 통합 레이블 지정 클라이언트를 사용하기 전에 다음을 수행합니다.    

    - 컴퓨터에서 Office 2010를 실행하는 경우 컴퓨터를 다시 시작하고 마지막 단계에서 다음 섹션으로 이동합니다.    
        
    - 기타 버전의 Office에서는 모든 Office 애플리케이션 및 파일 탐색기의 모든 인스턴스를 다시 시작합니다. 이제 설치가 완료되었으며 클라이언트를 사용하여 문서와 메일에 레이블을 지정하고 보호할 수 있습니다.    

### <a name="installing-the-azure-information-protection-unified-labeling-client-with-office-2010"></a>Office 2010에서 Azure Information Protection 통합 레이블 지정 클라이언트 설치

앞의 지침에 따라 Azure Information Protection 통합 레이블 지정 클라이언트를 설치한 후에 다음을 수행합니다.

1. Microsoft Word를 엽니다. Azure Information Protection 클라이언트 설치 후 Office 2010 애플리케이션을 처음으로 실행하는 경우 **Microsoft Azure Information Protection** 대화 상자가 표시됩니다. 이 대화 상자에는 로그인 프로세스를 완료하려면 관리자 자격 증명이 필요하다고 나옵니다.

2. **Microsoft Azure Information Protection** 대화 상자에서 **확인**을 클릭합니다.

3. **사용자 액세스 제어** 대화 상자가 표시되면 Azure Information Protection 클라이언트가 레지스트리를 업데이트할 수 있도록 **예**를 클릭합니다.

이제 설치가 완료되었으며 Azure Information Protection 통합 레이블 지정 클라이언트를 사용하여 문서 및 이메일에 레이블을 지정하고 보호할 수 있습니다.

## <a name="next-steps"></a>다음 단계

Office 365 Security & Compliance Center에서 사용하는 통합 레이블 지정 저장소에 대한 자세한 내용은 [Security & Compliance Center에서 통합 레이블 지정 관리의 가용성 알림](https://techcommunity.microsoft.com/t5/Security-Privacy-and-Compliance/Announcing-the-availability-of-unified-labeling-management-in/ba-p/262492) 블로그 게시물을 참조하세요.

