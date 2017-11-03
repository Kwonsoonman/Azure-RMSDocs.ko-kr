---
title: "AD RMS-Azure Information Protection 마이그레이션 - 3단계"
description: "AD RMS에서 Azure Information Protection으로 마이그레이션하는 과정의 세 번째 단계로, AD RMS에서 Azure Information Protection으로 마이그레이션 7단계가 포함됩니다."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 10/11/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: e3fd9bd9-3638-444a-a773-e1d5101b1793
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: ca2c8156489b55911ee340fd52f85e68b5280915
ms.sourcegitcommit: 3952fc01c6182c143df7f0d2e748594e49bf1da8
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/01/2017
---
# <a name="migration-phase-3---client-side-configuration"></a>마이그레이션 3단계 - 클라이언트 쪽 구성

>*적용 대상: Active Directory Rights Management Services, Azure Information Protection, Office 365*

AD RMS에서 Azure Information Protection으로 마이그레이션 3단계에는 다음 정보를 사용합니다. 이러한 절차는 [AD RMS에서 Azure Information Protection으로 마이그레이션](migrate-from-ad-rms-to-azure-rms.md)의 7단계를 설명합니다.

## <a name="step-7-reconfigure-windows-computers-to-use-azure-information-protection"></a>7단계. Azure Information Protection을 사용하도록 Windows 컴퓨터 다시 구성

Windows 컴퓨터의 경우 두 개의 마이그레이션 스크립트를 사용하여 AD RMS 클라이언트를 다시 구성합니다.

- Migrate-Client.cmd

- Migrate-User.cmd

클라이언트 구성 스크립트(Migrate-Client.cmd)는 레지스트리에 컴퓨터 수준 설정을 구성합니다. 즉, 그러한 변경 내용을 만들 수 있는 보안 컨텍스트에서 실행해야 함을 의미합니다. 일반적으로 다음 메서드 중 하나를 의미합니다.

- 그룹 정책을 사용하여 컴퓨터 시작 스크립트로 스크립트를 실행합니다.

- 그룹 정책 소프트웨어 설치를 사용하여 컴퓨터에 스크립트를 할당합니다.

- 소프트웨어 배포 솔루션을 사용하여 컴퓨터에 스크립트를 배포합니다. 예를 들어, System Center Configuration Manager의 [패키지 및 프로그램](/sccm/apps/deploy-use/packages-and-programs)을 사용합니다. **실행 모드**에 있는 패키지 및 프로그램의 속성에서 스크립트가 장치에서 관리자 권한으로 실행되도록 지정합니다. 

- 사용자에 로컬 관리자 권한이 있는 경우에 로그온 스크립트를 사용합니다.

사용자 구성 스크립트(Migrate-User.cmd)는 사용자 수준 설정을 구성하고 클라이언트 라이선스 저장소를 정리합니다. 즉, 이 스크립트는 실제 사용자의 컨텍스트에서 실행해야 합니다. 예를 들면 다음과 같습니다.

- 로그온 스크립트를 사용합니다.

- 그룹 정책 소프트웨어 설치를 사용하여 실행할 사용자에 대한 스크립트를 게시합니다.

- 소프트웨어 배포 솔루션을 사용하여 사용자에 스크립트를 배포합니다. 예를 들어, System Center Configuration Manager의 [패키지 및 프로그램](/sccm/apps/deploy-use/packages-and-programs)을 사용합니다. **실행 모드**에 있는 패키지 및 프로그램의 속성에서 스크립트가 사용자의 권한으로 실행되도록 지정합니다. 

- 사용자에게 자신의 컴퓨터에 로그인할 때 스크립트를 실행할 것인지 묻는 메시지가 표시됩니다.

두 개의 스크립트에는 버전 번호가 포함되어 있으며, 이 버전 번호가 변경될 때까지 다시 실행하지 마세요. 즉, 마이그레이션이 완료될 때까지 스크립트를 그대로 둘 수 있음을 의미합니다. 그러나 컴퓨터 및 사용자가 자신의 Windows 컴퓨터에서 다시 실행하길 원하는 스크립트를 변경하는 경우 두 스크립트에 다음 줄을 더 큰 값으로 업데이트합니다.

    SET Version=20170427

사용자 구성 스크립트는 클라이언트구성 스크립트 이후에 실행되도록 설계되었으며 이 검사의 버전 번호를 사용합니다. 같은 버전을 사용하는 클라이언트 구성 스크립트가 실행되지 않은 경우 중지됩니다. 이 검사는 두 스크립트가 올바른 시퀀스에서 실행되는지 확인합니다. 

모든 Windows 클라이언트를 한 번에 마이그레이션할 수 없는 경우 클라이언트 배치에 대해 다음 절차를 실행합니다. 배치에서 마이그레이션할 Windows 컴퓨터가 있는 각 사용자의 경우 앞에서 만든 **AIPMigrated** 그룹에 사용자를 추가합니다.

### <a name="windows-client-reconfiguration-by-using-registry-edits"></a>레지스트리 편집을 사용하여 Windows 클라이언트 재구성

1. [준비 단계](migrate-from-ad-rms-phase1.md#step-2-prepare-for-client-migration)에서 이러한 스크립트를 다운로드할 때 이전에 추출한 마이그레이션 스크립트, **Migrate-Client.cmd** 및 **Migrate-User.cmd**로 반환합니다.

2.  **Migrate-Client.cmd**의 지침에 따라 테넌트의 Azure Rights Management 서비스 URL과 AD RMS 클러스터 엑스트라넷 라이선스 URL 및 인트라넷 라이선스 URL의 서버 이름을 포함하도록 스크립트를 수정합니다. 그런 다음 이전에 설명된 스크립트 버전을 증가시킵니다. 스크립트 버전을 추적하기 위해서는 YYYYMMDD와 같은 형식의 현재 날짜를 사용하는 것이 좋습니다.

    > [!IMPORTANT]
    > 앞서와 같이 주소 앞 또는 뒤에 추가 공백이 생기지 않도록 주의하세요.
    > 
    > 또한 AD RMS 서버에서 SSL/TLS 서버 인증서를 사용하는 경우 라이선스 URL 값의 문자열에 포트 번호 **443**이 포함되어 있는지 확인하세요. 예: https:// rms.treyresearch.net:443/_wmcs/licensing 이 정보는 Active Directory Rights Management Services 콘솔에서 클러스터 이름을 클릭하고 **클러스터 세부 정보** 정보에서 확인할 수 있습니다. URL에 포함된 포트 번호 443이 포함된 경우 스크립트를 수정할 때 이 값을 포함하세요. 예: https://rms.treyresearch.net:**443**. 

    *&lt;테넌트 URL&gt;*의 Azure Rights Management 서비스 URL을 검색해야 할 경우 다시 [Azure Rights Management 서비스 URL을 식별하려면](migrate-from-ad-rms-phase1.md#to-identify-your-azure-rights-management-service-url)을 참조하세요.

3. 이 단계의 맨 앞에 나온 지침을 사용하여, AIPMigrated 그룹의 구성원이 사용하는 Windows 클라이언트 컴퓨터에서 **Migrate-Client.cmd** 및 **Migrate-User.cmd**를 실행하도록 스크립트 배포 메서드를 구성합니다. 

## <a name="next-steps"></a>다음 단계
마이그레이션을 계속하려면 [4단계 - 지원 서비스 구성](migrate-from-ad-rms-phase4.md)으로 이동합니다.

[!INCLUDE[Commenting house rules](../includes/houserules.md)]