---
title: "AD RMS-Azure Information Protection 마이그레이션 - 5단계"
description: "AD RMS에서 Azure Information Protection으로 마이그레이션하는 과정의 다섯 번째 단계로, AD RMS에서 Azure Information Protection으로 마이그레이션 10~12단계가 포함됩니다."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 11/16/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: d51e7bdd-2e5c-4304-98cc-cf2e7858557d
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 2cf486a5319d6addcd150351054d44db62c250b0
ms.sourcegitcommit: 9b975e66b12a3836003c6c4de139ded4bbf370bf
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/21/2017
---
# <a name="migration-phase-5---post-migration-tasks"></a>마이그레이션 5단계 - 마이그레이션 후 작업

>*적용 대상: Active Directory Rights Management Services, Azure Information Protection, Office 365*


AD RMS에서 Azure Information Protection으로 마이그레이션 5단계에는 다음 정보를 사용합니다. 이러한 절차는 [AD RMS에서 Azure Information Protection으로 마이그레이션](migrate-from-ad-rms-to-azure-rms.md)의 10~12단계를 설명합니다.

## <a name="step-10-deprovision-ad-rms"></a>10단계. AD RMS 프로비전 해제

온-프레미스 권한 관리 인프라에서 컴퓨터를 검색하지 못하게 하려면 Active Directory에서 SCP(서비스 연결 지점)를 제거합니다. 이는 레지스트리에서 마이그레이션 스크립트를 실행하는 등의 방법으로 구성한 리디렉션 때문에 마이그레이션한 기존 클라이언트에 대한 선택 사항입니다. 그러나 SCP를 제거하면 마이그레이션이 완료될 때 새 클라이언트 및 잠재적으로 RMS 관련 서비스 및 도구가 SCP를 찾지 못합니다. 이때 모든 컴퓨터 연결은 Azure Rights Management Service로 이동해야 합니다. 

SCP를 제거하려면 도메인 엔터프라이즈 관리자로 로그인하고 다음 절차를 사용합니다.

1. Active Directory Rights Management Services 콘솔에서 AD RMS 클러스터를 마우스 오른쪽 단추로 클릭하고 **속성**을 클릭합니다.

2. **SCP** 탭을 클릭합니다.

3. **SCP 변경** 확인란을 선택합니다.

4. **현재 SCP 제거**를 클릭하고 **확인**을 클릭합니다.

이제 AD RMS 서버의 활동을 모니터링합니다. 예를 들어 [시스템 상태 보고서의 요청](https://technet.microsoft.com/library/ee221012%28v=ws.10%29.aspx), [ServiceRequest 테이블](http://technet.microsoft.com/library/dd772686%28v=ws.10%29.aspx) 또는 [보호된 콘텐츠에 대한 사용자 액세스 감사](http://social.technet.microsoft.com/wiki/contents/articles/3440.ad-rms-frequently-asked-questions-faq.aspx)를 확인합니다. 

RMS 클라이언트가 이러한 서버와 더 이상 통신하지 않으며 클라이언트가 Azure Information Protection을 성공적으로 사용하고 있는지 확인한 다음, 이러한 서버에서 AD RMS 서버 역할을 제거할 수 있습니다. 전용 서버를 사용하는 경우 일정 기간 먼저 서버를 종료하는 준비 단계를 거칠 수 있습니다. 이렇게 하면 클라이언트가 Azure Information Protection을 사용하지 않는 이유를 조사하는 동안 서비스 연속성을 위해 이러한 서버를 다시 시작해야 할 수 있는 문제가 보고되지 않았는지 확인하는 시간을 가질 수 있습니다.

AD RMS 서버 프로비전을 해제한 후 Azure Portal에서 템플릿을 검토할 수 있습니다. 예를 들어 템플릿을 레이블로 변환하고 통합하여 사용자의 선택의 폭을 줄여주거나 템플릿을 다시 구성합니다. 이때 기본 템플릿을 게시하는 것도 좋습니다. 자세한 내용은 [Azure Information Protection 템플릿 구성 및 관리](../deploy-use/configure-policy-templates.md)를 참조하세요.

>[!IMPORTANT]
> 이 마이그레이션이 끝나면 AD RMS 클러스터를 Azure Information Protection 및 HYOK(Hold Your Own Key) 옵션에 사용할 수 없습니다. 현재 구현된 리디렉션 때문에 Azure Information Protection 레이블에 HYOK를 사용하기로 한 경우 사용하는 AD RMS 클러스터의 라이선스 URL은 마이그레이션한 클러스터의 라이선스 URL과 달라야 합니다.

## <a name="step-11-complete-client-migration-tasks"></a>11단계. 전체 클라이언트 마이그레이션 작업

모바일 장치 클라이언트 및 Mac 컴퓨터의 경우: [AD RMS 모바일 장치 확장](http://technet.microsoft.com/library/dn673574.aspx)을 배포할 때 만든 DNS SRV 레코드를 제거합니다.

이러한 DNS 변경 내용이 전파되면 이러한 클라이언트는 자동으로 검색하고 Azure Rights Management 서비스를 사용하기 시작합니다. 그러나 Office Mac을 실행하는 Mac 컴퓨터는 AD RMS에서 정보를 캐시합니다. 이러한 컴퓨터에서 이 프로세스는 최대 30일이 걸릴 수 있습니다. 

Mac 컴퓨터가 키 집합에서 검색 프로세스를 즉시 실행하도록 하려면 “adal”을 검색하고 ADAL 항목을 모두 삭제합니다. 그러고 나서 다음 명령을 해당 컴퓨터에서 실행합니다.

````

rm -r ~/Library/Cache/MSRightsManagement

rm -r ~/Library/Caches/com.microsoft.RMS-XPCService

rm -r ~/Library/Caches/Microsoft\ Rights\ Management\ Services

rm -r ~/Library/Containers/com.microsoft.RMS-XPCService

rm -r ~/Library/Containers/com.microsoft.RMSTestApp

rm ~/Library/Group\ Containers/UBF8T346G9.Office/DRM.plist

killall cfprefsd

````

모든 기존 Windows 컴퓨터를 Azure Information Protection으로 마이그레이션했으면 계속 온보딩 컨트롤을 사용하거나 마이그레이션 프로세스를 위해 만든 **AIPMigrated** 그룹을 유지할 이유가 없습니다. 

먼저 온보딩 컨트롤을 제거한 다음 **AIPMigrated** 그룹과 마이그레이션 스크립트를 배포하기 위해 만든 모든 소프트웨어 배포 메서드를 삭제할 수 있습니다.

온보딩 컨트롤을 제거하려면:

1. PowerShell 세션에서 Azure Rights Management 서비스에 연결하고 메시지가 표시되면 전역 관리자 자격 증명을 지정합니다.

        Connect-Aadrmservice

2. 다음 명령을 실행하고 **Y**를 입력하여 확인합니다.

        Set-AadrmOnboardingControlPolicy -UseRmsUserLicense $False
    
    이 명령은 모든 컴퓨터가 문서 및 전자 메일을 보호할 수 있도록 Azure Rights Management 보호 서비스에 대한 모든 라이선스 적용을 제거합니다.

3. 더 이상 온보딩 컨트롤이 설정되어 있지 않은지 확인합니다.

        Get-AadrmOnboardingControlPolicy

    출력에서 **License**가 **False**를 표시해야 하고, **SecurityGroupOjbectId**에 대해 표시되는 GUID가 없습니다.

마지막으로, Office 2010을 사용 중이며, Windows 작업 스케줄러 라이브러리에서 **AD RMS Rights Policy Template Management(자동)** 작업을 활성화한 경우 Azure Information Protection 클라이언트에서는 이 작업이 사용되지 않으므로 비활성화하세요. 이 작업은 일반적으로 그룹 정책을 사용하여 활성화되며 AD RMS 배포를 지원합니다. 이 작업은 **Microsoft** > **Windows** > **Active Directory Rights Management Services 클라이언트**에 있습니다.

## <a name="step-12-rekey-your-azure-information-protection-tenant-key"></a>12단계. Azure Information Protection 테넌트 키 다시 생성

이 단계는 AD RMS 배포에서 RMS 암호화 모드 1을 사용 중이던 경우 마이그레이션이 완료될 때 권장됩니다. 키를 다시 생성하면 RMS 암호화 모드 2를 사용하는 보호가 적용됩니다. 

AD RMS 배포에서 암호화 모드 2를 사용한 경우에도 새 키는 AD RMS 키에 대한 잠재적인 보안 위반으로부터 테넌트를 보호하는 데 도움이 되므로 이 단계가 여전히 권장됩니다.

그러나 AD RMS와 함께 Exchange Online을 사용한 경우 키를 다시 생성하지 마세요. Exchange Online은 암호화 모드 변경을 지원하지 않습니다. 

Azure Information Protection 테넌트 키를 다시 생성하면(“키 롤링”이라고도 함) 현재 활성 키가 보관되고 Azure Information Protection이 지정하는 다른 키를 사용하기 시작합니다. 이 다른 키는 Azure Key Vault에서 생성하는 새 키이거나, 테넌트에 대해 자동으로 생성된 기본 키일 수 있습니다.

한 키에서 다른 키로 이동하는 작업은 즉시 수행되는 것이 아니라 몇 주에 걸쳐서 수행됩니다. 즉시 수행되지 않으므로 원래 키에 대해 의심스러운 위반이 발생할 때까지 기다리지 말고, 마이그레이션이 완료되는 즉시 이 단계를 수행하세요.

Azure Information Protection 테넌트 키를 다시 입력하려면 다음과 같이 합니다.

- **테넌트가 Microsoft에서 관리되는 경우**: PowerShell cmdlet [Set-AadrmKeyProperties](/powershell/module/aadrm/set-aadrmkeyproperties)를 실행하고 테넌트에 대해 자동으로 생성된 키의 키 식별자를 지정합니다. [Get-AadrmKeys](/powershell/module/aadrm/get-aadrmkeys) cmdlet을 실행하여 지정할 값을 식별할 수 있습니다. 테넌트에 대해 자동으로 생성된 키에는 가장 오래된 생성 날짜가 있으므로, 다음 명령을 사용하여 식별할 수 있습니다.
    
        (Get-AadrmKeys) | Sort-Object CreationTime | Select-Object -First 1

- **사용자가 관리하는 테넌트 키인 경우(BYOK)**: Azure Key Vault에서 Azure Information Protection 테넌트에 대해 키 생성 프로세스를 반복한 다음 [Use-AadrmKeyVaultKey](/powershell/aadrm/vlatest/use-aadrmkeyvaultkey) cmdlet을 다시 실행하여 이 새 키에 대한 URI를 지정합니다. 

Azure Information Protection 테넌트 키 관리에 대한 자세한 내용은 [Azure Rights Management 테넌트 키에 대한 작업](../deploy-use/operations-tenant-key.md)을 참조하세요.


## <a name="next-steps"></a>다음 단계

이제는 마이그레이션을 완료했으므로 [배포 로드맵](deployment-roadmap.md)을 검토하여 필요할 수 있는 다른 배포 작업을 확인합니다.

[!INCLUDE[Commenting house rules](../includes/houserules.md)]
