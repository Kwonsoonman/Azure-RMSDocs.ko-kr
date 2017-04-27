---
title: "AD RMS-Azure Information Protection 마이그레이션 - 3단계"
description: "AD RMS에서 Azure Information Protection으로 마이그레이션하는 과정의 세 번째 단계로, AD RMS에서 Azure Information Protection으로 마이그레이션 7단계가 포함됩니다."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 04/18/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: e3fd9bd9-3638-444a-a773-e1d5101b1793
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 55dfd0ef99e1b220c65c9a8be994de161e98d8ec
ms.sourcegitcommit: 237ce3a0cc4921da5a08ed5753e6491403298194
translationtype: HT
---
# <a name="migration-phase-3---client-side-configuration"></a>마이그레이션 3단계 - 클라이언트 쪽 구성

>*적용 대상: Active Directory Rights Management Services, Azure Information Protection, Office 365*

AD RMS에서 Azure Information Protection으로 마이그레이션 3단계에는 다음 정보를 사용합니다. 이러한 절차는 [AD RMS에서 Azure Information Protection으로 마이그레이션](migrate-from-ad-rms-to-azure-rms.md)의 7단계를 설명합니다.

모든 클라이언트를 한 번에 마이그레이션할 수 없는 경우 클라이언트 배치에 대해 이러한 절차를 실행합니다. 배치에서 마이그레이션할 Windows 컴퓨터가 있는 각 사용자의 경우 앞에서 만든 **AIPMigrated** 그룹에 사용자를 추가합니다.

## <a name="step-7-reconfigure-clients-to-use-azure-information-protection"></a>7단계. Azure Information Protection을 사용하도록 클라이언트 다시 구성

이 단계에서는 마이그레이션 스크립트를 사용하여 AD RMS 클라이언트를 다시 구성합니다. 스크립트는 AD RMS 대신 Azure Rights Management 서비스를 사용하도록 Windows 컴퓨터에서 구성을 다시 설정합니다. 

**CleanUpRMS.cmd**:

- AD RMS 클라이언트에서 해당 구성을 저장하는 데 사용하는 모든 폴더와 레지스트리 키의 내용을 삭제합니다. 이 정보는 클라이언트의 AD RMS 클러스터 위치를 포함합니다.

**MigrateClient.cmd**:

- Azure Rights Management 서비스에 대한 사용자 환경(부트스트랩)을 초기화하도록 클라이언트를 구성합니다.

-  Azure Rights Management 서비스에 연결하여 AD RMS 클러스터로 보호되는 콘텐츠에 대한 사용권을 가져오도록 클라이언트를 구성합니다. 


### <a name="client-reconfiguration-by-using-registry-edits"></a>레지스트리 편집을 사용하여 클라이언트 재구성

1. 앞에서 추출한 마이그레이션 스크립트 **CleanUpRMS.cmd** 및 **MigrateClient.cmd**로 돌아갑니다.

2.  **MigrateClient.cmd**의 지침에 따라 테넌트의 Azure Rights Management 서비스 URL과 AD RMS 클러스터 엑스트라넷 라이선스 URL 및 인트라넷 라이선스 URL의 서버 이름을 포함하도록 스크립트를 수정합니다.

    > [!IMPORTANT]
    > 앞서와 같이 주소 앞 또는 뒤에 추가 공백이 생기지 않도록 주의하세요.
    > 
    > 또한 AD RMS 서버에서 SSL/TLS 서버 인증서를 사용하는 경우 라이선스 URL 값의 문자열에 포트 번호 **443**이 포함되어 있는지 확인하세요. 예: https:// rms.treyresearch.net:443/_wmcs/licensing 이 정보는 Active Directory Rights Management Services 콘솔에서 클러스터 이름을 클릭하고 **클러스터 세부 정보** 정보에서 확인할 수 있습니다. URL에 포함된 포트 번호 443이 포함된 경우 스크립트를 수정할 때 이 값을 포함하세요. 예: https://rms.treyresearch.net:**443**. 

    *&lt;테넌트 URL&gt;*의 Azure Rights Management 서비스 URL을 검색해야 할 경우 다시 [Azure Rights Management 서비스 URL을 식별하려면](migrate-from-ad-rms-phase1.md#to-identify-your-azure-rights-management-service-url)을 참조하세요.

3.  **AIPMigrated** 그룹의 멤버에서 사용되는 클라이언트 컴퓨터에서 **CleanUpRMS.cmd**를 실행한 다음 **MigrateClient.cmd**를 실행합니다. 예를 들어 이러한 스크립트를 실행하는 그룹 정책 개체를 만들어 이 사용자 그룹에 할당합니다.


## <a name="next-steps"></a>다음 단계
마이그레이션을 계속하려면 [4단계 - 지원 서비스 구성](migrate-from-ad-rms-phase3.md)으로 이동합니다.

[!INCLUDE[Commenting house rules](../includes/houserules.md)]