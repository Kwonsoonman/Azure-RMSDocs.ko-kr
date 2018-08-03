---
title: Azure RMS에 대한 FAQ - AIP
description: 데이터 보호 서비스인 Azure Information Protection의 Azure Rights Management 서비스(Azure RMS)의 몇 가지 질문과 대답입니다.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 05/21/2018
ms.topic: article
ms.prod: ''
ms.service: information-protection
ms.technology: techgroup-identity
ms.custom: askipteam
ms.assetid: 90df11c5-355c-4ae6-a762-351b05d0fbed
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: ee408c47572bcdfcbfccc6d193ed432b92c6f4a1
ms.sourcegitcommit: 949bf02d5d12bef8e26d89ad5d6a0d5cc7826135
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/02/2018
ms.locfileid: "39474770"
---
# <a name="frequently-asked-questions-about-data-protection-in-azure-information-protection"></a>Azure Information Protection에서 데이터 보호에 대한 질문과 대답

>*적용 대상: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [Office 365](http://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*

데이터 보호 서비스인 Azure Information Protection의 Azure Rights Management 서비스에 대해 질문이 있나요? 여기에 해당 질문에 대한 대답이 있는지 확인하세요.

## <a name="do-files-have-to-be-in-the-cloud-to-be-protected-by-azure-rights-management"></a>파일을 Azure Rights Management에서 보호하려면 해당 파일이 클라우드에 있어야 하나요?
아니요. 이것은 일반적인 오해입니다. Azure Rights Management 서비스(및 Microsoft)가 데이터를 정보 보호 프로세스의 일부로 보거나 저장하지 않는다는 것입니다. 보호하는 정보는 Azure에 명시적으로 저장하거나 Azure에 정보를 저장하는 다른 클라우드 서비스를 사용하지 않는 한, Azure로 전송되거나 Azure에 저장되지 않습니다.

[Azure RMS는 어떤 방식으로 작동하나요? 기본적인 이해](./how-does-it-work.md)를 참조하여 온-프레미스에서 생성 및 저장된 콜라 비밀 제조법이 Azure Rights Management 서비스를 통해 어떻게 보호되고 온-프레미스에 유지되는지를 확인할 수 있습니다.

## <a name="whats-the-difference-between-azure-rights-management-encryption-and-encryption-in-other-microsoft-cloud-services"></a>Azure Rights Management 암호화와 다른 Microsoft Cloud Services의 암호화 간의 차이점은 무엇인가요?

Microsoft는 다르거나 종종 상호 보완적인 시나리오에서 데이터를 보호할 수 있는 여러 암호화 기술을 제공합니다. 예를 들어 Office 365는 Office 365에 저장된 데이터에 대해 유휴 시 암호화를 제공하는 반면에 Azure Information Protection의 Azure Rights Management 서비스는 데이터의 위치나 전송 방식에 상관없이 데이터가 보호될 수 있도록 데이터를 독립적으로 암호화합니다.

이러한 암호화 기술은 상호 보완적이며 사용하려면 개별적으로 사용 설정 및 구성해야 합니다. 이때 암호화를 위해 고유한 키를 가져올 수도 있습니다("BYOK" 시나리오라고도 함). 이러한 기술 중 하나에 대해 BYOK를 사용하도록 설정해도 다른 기술에는 영향을 주지 않습니다. 예를 들어 Azure Information Protection에는 BYOK를 사용하고 다른 암호화 기술에는 BYOK를 사용하지 않을 수 있습니다. 이러한 다른 기술에서 사용하는 키는 같거나 다를 수 있는데, 각 서비스의 암호화 옵션 구성 방법에 달려 있습니다.

## <a name="whats-the-difference-between-byok-and-hyok-and-when-should-i-use-them"></a>BYOK와 HYOK를 사용해야 하는 경우 이 둘의 차이는 무엇인가요?

Azure Information Protection의 컨텍스트에서 **BYOK**(Bring Your Own Key)는 Azure Rights Management 보호에 대해 온-프레미스에 고유한 키를 만드는 경우에 사용합니다. 그런 다음 키를 계속 소유하고 관리하는 Azure Key Vault의 HSM(하드웨어 보안 모듈)으로 해당 키를 전송합니다. 이렇게 하지 않으면 Azure Rights Management 보호는 Azure에서 자동으로 생성되고 관리되는 키를 사용합니다. 이 기본 구성을 “사용자가 관리”(BYOK 옵션)가 아니라 "Microsoft가 관리"라고 합니다.

BYOK에 대한 자세한 내용과 조직에 대해 이 키 토폴로지를 선택해야 하는지 여부는 [Azure Information Protection 테넌트 키 계획 및 구현](./plan-design/plan-implement-tenant-key.md)을 참조하세요.

Azure Information Protection의 컨텍스트에서 **HYOK**(Hold Your Own Key)는 클라우드에 저장되는 키로 보호할 수 없는 일부 문서 또는 메일이 있는 적은 수의 조직에서 사용합니다. 이러한 조직에서는 BYOK를 사용하여 키를 만들고 관리하는 경우에도 이 제한이 적용됩니다. 제한은 종종 규정 또는 규정 준수 사유가 될 수 있으며, HYOK 구성은 조직 외부에서 공유해서는 안되며 내부 네트워크에서만 사용되고 모바일 장치에서 액세스해서는 안 되는 "일급 비밀" 정보에만 적용되어야 합니다.

이러한 예외(일반적으로 보호되어야 하는 모든 콘텐츠의 10% 미만)의 경우, 조직은 온-프레미스 솔루션인 Active Directory Rights Management Services를 사용하여 온-프레미스에 유지하는 키를 만들 수 있습니다. 이 솔루션을 사용하면 컴퓨터는 클라우드에서 Azure Information Protection 정책을 가져오지만 이 확인된 콘텐츠는 온-프레미스 키를 사용하여 보호될 수 있습니다.

HYOK에 대한 자세한 내용을 보고 제한 사항을 이해했음을 확인하고 HYOK 사용 시 지침을 보려면 [AD RMS 보호에 대한 HYOK(Hold Your Own Key) 요구 사항 및 제한](./deploy-use/configure-adrms-restrictions.md)을 참조하세요.

## <a name="can-i-now-use-byok-with-exchange-online"></a>이제 Exchange Online에서 BYOK를 사용할 수 있습니까?

예, 이제 [Azure Information Protection을 기반으로 구축된 새로운 Office 365 메시지 암호화 기능 설정](https://support.office.com/article/7ff0c040-b25c-4378-9904-b1b50210d00e)의 지침을 따르면 Exchange Online에서 BYOK를 사용할 수 있습니다. 이러한 지침을 통해 새로운 Office 365 메시지 암호화는 물론 Azure Information Protection에 대해 BYOK를 지원하는 Exchange Online의 새로운 기능을 사용할 수 있습니다.

변경 내용에 대한 자세한 내용은 블로그 공지 [새로운 기능을 갖춘 Office 365 메시지 암호화](https://techcommunity.microsoft.com/t5/Security-Privacy-and-Compliance/Email-Encryption-and-Rights-Protection/ba-p/110801)를 참조하세요.

## <a name="where-can-i-find-information-about-third-party-solutions-that-integrate-with-azure-rms"></a>Azure RMS와 통합되는 타사 솔루션에 대한 정보는 어디서 찾을 수 있나요?

많은 소프트웨어 공급 업체들은 이미 Azure Rights Management와 통합하는 솔루션을 보유하고 있거나 이러한 솔루션을 구현하고 있으며, 그 목록은 빠르게 증가되고 있습니다. [RMS 지원 솔루션](requirements-applications.md#rms-enlightened-solutions) 목록을 확인하고 Twitter에서 [Microsoft Mobility@MSFTMobility](https://twitter.com/MSFTMobility)의 최신 업데이트를 확인하는 것도 유용합니다. 또한 [개발자 가이드](./develop/developers-guide.md)를 확인하고 Azure Information Protection [Yammer 사이트](https://www.yammer.com/AskIPTeam)에서 특정 통합 질문을 게시하세요.

## <a name="is-there-a-management-pack-or-similar-monitoring-mechanism-for-the-rms-connector"></a>RMS 커넥터에 대한 관리 팩이나 유사한 모니터링 메커니즘이 있나요?

Rights Management 커넥터에서 정보, 경고 및 오류 메시지를 이벤트 로그에 기록하긴 하지만, 이러한 이벤트에 대한 모니터링을 포함하는 관리 팩은 없습니다. 그러나 이벤트 목록과 해당 설명이 정정 작업을 할 수 있도록 돕는 자세한 정보와 함께 [Azure Rights Management 커넥터 모니터링](./deploy-use/monitor-rms-connector.md)에 정리되어 있습니다.

## <a name="do-you-need-to-be-a-global-admin-to-configure-azure-rms-or-can-i-delegate-to-other-administrators"></a>Azure RMS를 구성하려면 전역 관리자여야 하나요? 또는, 다른 관리자에게 위임할 수 있나요?

새로 도입된 Information Protection 관리자 역할을 통해 이제 이 질문(및 답변)은 기본 FAQ 페이지로 이동됩니다. [Azure Information Protection을 구성하려면 전역 관리자여야 하나요? 또는 다른 관리자에게 위임할 수 있나요?](faqs.md#do-you-need-to-be-a-global-admin-to-configure-azure-information-protection-or-can-i-delegate-to-other-administrators)

## <a name="how-do-i-create-a-new-custom-template-in-the-azure-portal"></a>Azure Portal에서 새 사용자 지정 템플릿을 만들려면 어떻게 해야 하나요?

사용자 지정 템플릿은 Azure Portal로 이동되고 있으며 여기에서 계속 템플릿으로 관리하거나 레이블로 변환할 수 있습니다. 새 템플릿을 만들려면 새 레이블을 만들고 Azure RMS에 대한 데이터 보호 설정을 구성합니다. 내부적으로 새 템플릿이 만들어진 다음 권한 관리 템플릿과 통합되는 서비스 및 응용 프로그램에서 액세스될 수 있습니다.

Azure Portal의 템플릿에 대한 자세한 내용은 [Azure Information Protection의 템플릿 구성 및 관리](./deploy-use/configure-policy-templates.md)를 참조하세요.

## <a name="ive-protected-a-document-and-now-want-to-change-the-usage-rights-or-add-usersdo-i-need-to-reprotect-the-document"></a>문서를 보호한 상태에서 이제 사용 권한을 변경하거나 사용자를 추가하려면 문서를 다시 보호해야 합니까?

레이블 또는 템플릿을 사용하여 문서를 보호하는 경우 문서를 다시 보호할 필요는 없습니다. 사용 권한을 변경하거나 새 그룹(또는 사용자)을 추가하여 레이블 또는 템플릿을 수정한 다음, 이러한 변경 내용을 저장하고 게시합니다.

- 사용자가 변경하기 전에 문서에 액세스하지 않은 경우 변경 내용은 사용자가 문서를 여는 즉시 적용됩니다.

- 사용자가 이미 문서에 액세스한 경우에는 해당 [사용 라이선스](./deploy-use/configure-usage-rights.md#rights-management-use-license) 기간이 만료된 후에 변경 내용이 적용됩니다. 사용 라이선스가 만료될 때까지 기다릴 수 없는 경우에만 문서를 다시 보호합니다. 효과적으로 다시 보호하는 방법은 문서의 새 버전, 그에 따른 사용자에 대한 새 사용 라이선스를 만드는 것입니다.

또는 필요한 사용 권한에 대한 그룹을 이미 구성했다면 사용자를 포함하거나 제외하도록 그룹 구성원을 변경할 수 있으며, 레이블 또는 템플릿을 변경할 필요는 없습니다. 그룹 구성원은 Azure Rights Management 서비스에 의해 [캐시](./plan-design/prepare.md#group-membership-caching-by-azure-information-protection)되므로 변경 내용이 적용되기 전에 약간 지연이 있을 수 있습니다.

사용자 지정 권한을 사용하여 문서를 보호한 경우 기존 문서에 대한 권한을 변경할 수 없습니다. 문서를 다시 보호하고 문서의 이 새 버전이 필요한 모든 사용자 및 모든 사용 권한을 지정해야 합니다. 보호된 문서를 다시 보호하려면 모든 권한 사용 권한이 있어야 합니다.

문서가 템플릿 또는 사용자 지정 권한을 사용하여 보호되었는지 확인하려면 [Get-AIPFileStatus](/powershell/module/azureinformationprotection/get-aipfilestatus) PowerShell cmdlet을 사용합니다. [Get-RMSTemplate](/powershell/module/azureinformationprotection/get-rmstemplate)을 실행할 때 표시되지 않는 고유한 템플릿 ID와 함께 사용자 지정 권한에 대한 **제한된 액세스**의 템플릿 설명이 항상 표시됩니다.

## <a name="i-have-a-hybrid-deployment-of-exchange-with-some-users-on-exchange-online-and-others-on-exchange-serveris-this-supported-by-azure-rms"></a>Exchange Online의 사용자와 Exchange Server 서버의 다른 사용자로 구성된 Exchange의 하이브리드 배포입니다. Azure RMS에서 지원되나요?
물론입니다. 사용자가 두 Exchange 배포에서 보호되는 메일과 첨부 파일을 원활하게 보호하고 소비할 수 있습니다. 이 구성을 사용하려면 [Azure RMS를 활성화](./deploy-use/activate-service.md)하고 [Exchange Online에 IRM을 사용하도록 설정](https://technet.microsoft.com/library/dn151475%28v=exchg.150%29.aspx)한 다음 Exchange Server용 [RMS 커넥터를 배포 및 구성](./deploy-use/deploy-rms-connector.md)합니다.

## <a name="if-i-use-this-protection-for-my-production-environment-is-my-company-then-locked-into-the-solution-or-risk-losing-access-to-content-that-we-protected-with-azure-rms"></a>이 보호를 프로덕션 환경에서 사용할 경우 회사가 솔루션에 갇히거나, Azure RMS로 보호한 콘텐츠를 액세스할 수 없게 되나요?
아니요. 항상 데이터를 제어하고 지속적으로 액세스할 수 있습니다. 더 이상 Azure Rights Management 서비스를 사용하지 않아도 마찬가지입니다. 자세한 내용은 [Azure 권한 관리 서비스 해제 및 비활성화](./deploy-use/decommission-deactivate.md)를 참조하세요.

## <a name="can-i-control-which-of-my-users-can-use-azure-rms-to-protect-content"></a>Azure RMS를 사용하여 콘텐츠를 보호할 수 있는 사용자를 제어할 수 있나요?
예. Azure Rights Management 서비스에는 이 시나리오에 대한 사용자 온보딩 컨트롤이 있습니다. 자세한 내용은 [Azure 권한 관리 활성화](./deploy-use/activate-service.md) 문서에서 [단계별 배포에 대한 온보딩 컨트롤 구성](./deploy-use/activate-service.md#configuring-onboarding-controls-for-a-phased-deployment) 섹션을 참조하세요.

## <a name="can-i-prevent-users-from-sharing-protected-documents-with-specific-organizations"></a>사용자가 보호된 문서를 특정 조직과 공유하지 못하게 할 수 있나요?
데이터 보호용 Azure Rights Management 서비스의 가장 큰 이점 중 하나는 Azure AD가 인증을 처리하기 때문에 각 파트너 조직에 대한 명시적 트러스트를 구성할 필요 없이 비즈니스 간 공동 작업을 지원한다는 점입니다.

사용자가 특정 조직과 안전하게 문서를 공유하지 못하게 하는 관리 옵션은 없습니다. 신뢰하지 않거나 경쟁 사업을 진행하는 조직을 차단하고 싶은 경우를 예로 들 수 있습니다. Azure Rights Management 서비스에서 이러한 조직의 사용자에게 보호된 문서를 보내지 못하게 하면 사용자가 보호되지 않은 상태로 문서를 공유하게 되므로 원치 않는 결과가 나타날 수 있습니다. 따라서 이 방법은 적절하지 않습니다. 예를 들어 누가 이러한 조직의 어떤 사용자와 회사 기밀 문서를 공유하는지, 문서(또는 메일)가 Azure Rights Management 서비스를 통해 보호될 때 어떤 작업을 수행할 수 있는지를 알 수 없게 됩니다.

## <a name="when-i-share-a-protected-document-with-somebody-outside-my-company-how-does-that-user-get-authenticated"></a>보호되는 문서를 회사 외부의 누군가와 공유할 때 해당 사용자를 어떻게 인증하나요?

기본적으로 Azure Rights Management 서비스는 기업 간 공동 작업에서의 관리자 편의를 위해 Azure Active Directory 계정과, 연결된 전자 메일 주소를 사용자 인증에 사용합니다. 다른 조직에서 Azure 서비스를 사용한다면 온-프레미스에서 만들어져 관리되며 Azure에 동기화되는 계정이더라도 사용자에게 이미 Azure Active Directory 계정이 있을 것입니다. 해당 조직에 Office 365가 있다면 바탕에서는 사용자 계정에 Azure Active Directory를 사용하고 있습니다. 사용자 조직이 Azure에서 계정을 관리하지 않은 경우 [개인용 RMS](./rms-for-individuals.md)에 등록할 수 있습니다. 그러면 해당 사용자의 계정이 있는 조직에 대해 관리되지 않는 Azure 테넌트와 디렉터리가 생성되어 해당 사용자(및 후속 사용자)를 Azure Rights Management 서비스에 인증할 수 있게 됩니다.

이러한 계정에 대한 인증 방법은 다른 조직의 관리자가 Azure Active Directory 계정을 어떻게 구성했느냐에 따라 달라질 수 있습니다. 예를 들어, 이 계정에 대해 만든 암호, 다단계 인증(MFA), 페더레이션 또는 Active Directory 도메인 서비스에서 생성된 후 Azure Active Directory에 동기화된 암호 등을 사용할 수 있습니다.

기타 인증 방법:

- Azure AD에 계정이 없는 사용자에게 보내는 Office 문서 첨부 파일이 포함된 전자 메일을 보호하는 경우 인증 방법이 변경됩니다. Azure Rights Management 서비스는 Gmail과 같이 많이 사용되는 일부 소셜 ID 공급자와 페더레이션되어 있습니다. 사용자의 전자 메일 공급자가 지원되는 경우 사용자는 해당 서비스에 로그인 할 수 있으며 사용자의 전자 메일 공급자가 인증을 담당합니다. 사용자의 전자 메일 공급자가 지원되지 않거나 기본 설정인 경우 사용자는 인증을 위해 일회성 암호를 신청할 수 있으며 보호된 문서가 있는 전자 메일을 웹 브라우저에 표시할 수 있습니다.

- Azure Information Protection은 지원되는 응용 프로그램에 Microsoft 계정을 사용할 수 있습니다. 현재 인증에 Microsoft 계정을 사용할 경우, 일부 응용 프로그램이 보호된 콘텐츠를 열 수 없습니다. [추가 정보](secure-collaboration-documents.md#supported-scenarios-for-opening-protected-documents)

## <a name="can-i-add-external-users-people-from-outside-my-company-to-custom-templates"></a>외부 사용자(회사 외부의 사용자)를 사용자 지정 템플릿에 추가할 수 있나요?

예. Azure Portal에서 구성한 [보호 설정](./deploy-use/configure-policy-protection.md)을 통해 조직 외부의 사용자 및 그룹과 심지어 다른 조직의 모든 사용자에게 권한을 추가할 수 있습니다. [Azure Information Protection을 사용하여 보안 문서 공동 작업](secure-collaboration-documents.md) 단계별 예제를 참조하는 것이 좋습니다. 

Azure Information Protection 레이블이 설치된 경우 Azure Portal에서 이러한 보호 설정을 구성하기 전에 먼저 사용자 지정 템플릿을 레이블로 변환해야 합니다. 자세한 내용은 [Azure Information Protection 템플릿 구성 및 관리](./deploy-use/configure-policy-templates.md)를 참조하세요.

또는 PowerShell을 사용하여 사용자 지정 템플릿(및 레이블)에 외부 사용자를 추가할 수 있습니다. 이 구성에서는 템플릿을 업데이트하는 데 사용하는 권한 정의 개체를 사용하도록 해야 합니다.

1. 변수를 만드는 [New-AadrmRightsDefinition](/powershell/module/aadrm/new-aadrmrightsdefinition) cmdlet을 사용하여 권한 정의 개체에서 외부 메일 주소 및 해당 권한을 지정합니다.

2. [Set-AadrmTemplateProperty](/powershell/module/aadrm/set-aadrmtemplateproperty) cmdlet을 사용하여 이 변수를 RightsDefinition 매개 변수에 제공합니다.

    기존 템플릿에 사용자를 추가하는 경우 새 사용자 외에도 템플릿의 기존 사용자를 위한 권한 정의 개체를 정의해야 합니다. 이 시나리오에서는 cmdlet의 [예제](/powershell/module/aadrm/set-aadrmtemplateproperty#examples) 섹션에서 유용한 **예제 3: 사용자 지정 템플릿에 새 사용자 및 권한 추가**를 찾을 수 있습닌다.

## <a name="what-type-of-groups-can-i-use-with-azure-rms"></a>Azure RMS에서 사용할 수있는 그룹 유형은 무엇입니까?
대부분의 시나리오에서 전자 메일 주소가 있는 Azure AD의 그룹 유형을 사용할 수 있습니다. 이 방법은 사용 권한을 할당할 때 항상 적용되지만 Azure Rights Management 서비스를 관리하기 위한 몇 가지 예외가 있습니다. 자세한 내용은 [그룹 계정에 대한 Azure Information Protection 요구 사항](./plan-design/prepare.md#azure-information-protection-requirements-for-group-accounts)을 참조하세요.

## <a name="how-do-i-send-a-protected-email-to-a-gmail-or-hotmail-account"></a>보호된 메일을 Gmail 또는 Hotmail 계정으로 보내려면 어떻게 해야 하나요?

Exchange Online과 Azure Rights Management 서비스를 사용할 때는 전자 메일을 사용자에게 보호된 메시지로 보냅니다. 예를 들어 웹의 Outlook의 명령 모음에서 새 **보호** 단추를 선택하고 Outlook **전달 금지** 단추 또는 메뉴 옵션을 사용할 수 있습니다. 또는 자동으로 전달 금지를 적용하고 전자 메일을 분류하는 Azure Information Protection 레이블을 선택할 수 있습니다.

받는 사람에게 Gmail, Yahoo 또는 Microsoft 계정에 로그인하는 옵션이 표시되고 받는 사람은 보호된 이메일을 읽을 수 있습니다. 또는 일회성 암호로 브라우저에서 전자 메일을 읽는 옵션을 선택할 수도 있습니다.

이 시나리오를 지원하려면 Azure Rights Management 서비스 및 Office 365 메시지 암호화의 새로운 기능에서 Exchange Online을 사용할 수 있어야 합니다. 이 구성에 대한 자세한 내용은 [Exchange Online: IRM 구성](./deploy-use/configure-office365.md#exchange-online-irm-configuration)을 참조하세요.

모든 장치에서 모든 전자 메일 계정 지원을 포함하는 새로운 기능에 대한 자세한 내용은 블로그 게시물 [Office 365 메시지 암호화에서 사용할 수 있는 새로운 기능](https://techcommunity.microsoft.com/t5/Security-Privacy-and-Compliance/Email-Encryption-and-Rights-Protection/ba-p/110801)을 참조하세요.

## <a name="what-devices-and-which-file-types-are-supported-by-azure-rms"></a>Azure RMS에서는 어떤 장치 및 파일 형식을 지원하나요?
Azure Rights Management 서비스를 지원하는 장치 목록은 [Azure Rights Management 데이터 보호를 지원하는 클라이언트 장치](./requirements-client-devices.md)를 참조하세요. 현재는 지원 장치 중 일부만 모든 Rights Management 기능을 지원하기 때문에 [RMS 기반 응용 프로그램](./requirements-applications.md#rms-enlightened-applications) 표도 확인해야 합니다.

Azure Rights Management 서비스는 모든 형식의 파일을 지원할 수 있습니다. 텍스트, 이미지, Microsoft Office(Word, Excel, PowerPoint) 파일, .pdf 파일 및 일부 기타 응용 프로그램 파일 형식의 경우 Azure Rights Management는 권한 적용 및 암호화를 모두 포함하는 기본 보호 기능을 제공합니다. 기타 모든 응용 프로그램 및 파일 형식의 경우 일반적인 보호를 통해 사용자가 파일을 열 권한이 있는지 확인하는 인증 및 파일 캡슐화 기능을 제공합니다.

Azure Rights Management에 의해 고유하게 지원되는 파일 이름 확장명 목록을 보려면 [Azure Information Protection 클라이언트에서 지원하는 파일 형식](./rms-client/client-admin-guide-file-types.md)을 참조하세요. 여기에 나열되지 않은 파일 이름 확장명은 해당 파일에 일반 보호를 자동 적용하는 Azure Information Protection 클라이언트를 통해 지원됩니다.

## <a name="how-do-i-configure-a-mac-computer-to-protect-and-track-documents"></a>문서를 보호하고 추적하도록 Mac 컴퓨터를 구성하려면 어떻게 해야 하나요?

먼저 https://portal.office.com의 소프트웨어 설치 링크를 사용하여 Mac용 Office를 설치해야 합니다. 전체 지침은 [PC 또는 Mac에서 Office 365 또는 Office 2016 다운로드 및 설치 또는 다시 설치](https://support.office.com/en-us/article/Download-and-install-or-reinstall-Office-365-or-Office-2016-on-a-PC-or-Mac-4414EAAF-0478-48BE-9C42-23ADC4716658)를 참조하세요.

Outlook을 열고 Office 365 회사 또는 학교 계정을 사용하여 프로필을 만듭니다. 그런 다음 새 메시지를 만들고 Azure 권한 관리 서비스를 사용하여 문서와 메일을 보호할 수 있도록 다음과 같이 Office를 구성합니다.

1. 새 메시지에서 **옵션** 탭을 클릭하고 **사용 권한**을 클릭한 후 **자격 증명 확인**을 클릭합니다.

2. 로그인하라는 메시지가 표시되면 Office 365 회사 또는 학교 계정 세부 정보를 다시 지정한 후 **로그인**을 선택합니다.

    그러면 Azure 권한 관리 템플릿이 다운로드되고 **자격 증명 확인**은 **제한 없음**, **전달 금지** 및 테넌트에 대해 게시된 Azure 권한 관리 템플릿을 포함하는 옵션으로 바뀝니다. 이제 이 새 메시지를 취소할 수 있습니다.

전자 메일 메시지 또는 문서를 보호하려면 **옵션** 탭에서 **사용 권한**을 클릭하고 전자 메일이나 문서를 보호하는 옵션 또는 템플릿을 선택합니다.

문서를 호환 후 추적하려면 Azure Information Protection 클라이언트가 설치된 Windows 컴퓨터에서 Office 응용 프로그램 또는 파일 탐색기를 사용하여 해당 문서를 문서 추적 사이트에 등록합니다. 자세한 내용은 [문서 추적 및 취소](./rms-client/client-track-revoke.md)를 참조하세요. Mac 컴퓨터에서는 웹 브라우저를 사용하여 문서 추적 사이트 (https://track.azurerms.com) 로 이동한 후 이 문서를 추적 및 취소할 수 있습니다.

## <a name="when-i-open-an-rms-protected-office-document-does-the-associated-temporary-file-become-rms-protected-as-well"></a>RMS로 보호된 Office 문서를 열면 연결된 임시 파일도 RMS로 보호되나요?
아니요. 이 시나리오에서는 연결된 임시 파일에 원래 문서의 데이터가 포함되지 않고 대신 파일이 열려 있는 동안 사용자가 입력하는 내용만 포함됩니다. 원본 파일과 달리 임시 파일은 명시적으로 공유를 위해 설계되지 않았으며 로컬 보안 컨트롤(예: BitLocker 및 EFS)로 보호되는 장치에 있습니다.

## <a name="a-feature-i-am-looking-for-doesnt-seem-to-work-with-sharepoint-protected-librariesis-support-for-my-feature-planned"></a>SharePoint 보호 라이브러리에서 작동하지 않는 것 같은 기능이 있습니다. 이 기능에 대한 지원이 예정되어 있나요?
현재, SharePoint는 Rights Management 템플릿, 문서 추적 및 일부 다른 기능을 지원하지 않는 IRM 보호 라이브러리를 사용하여 RMS 보호 문서를 지원합니다. 자세한 내용은 [Office 응용 프로그램 및 서비스](./office-apps-services-support.md) 문서에서 [SharePoint Online 및 SharePoint Server](./office-apps-services-support.md#sharepoint-online-and-sharepoint-server) 섹션을 참조하세요.

아직 지원되지 않는 특정 기능에 관심이 있는 경우 [Enterprise Mobility and Security Blog](https://cloudblogs.microsoft.com/enterprisemobility/?product=azure-rights-management-services)(Enterprise Mobility 및 보안 블로그)의 공지에 관심을 기울이시기 바랍니다.

## <a name="how-do-i-configure-one-drive-for-business-in-sharepoint-online-so-that-users-can-safely-share-their-files-with-people-inside-and-outside-the-company"></a>사용자가 회사 내부와 외부의 사람들과 파일을 안전하게 공유할 수 있게, SharePoint Online에서 One Drive for Business를 어떻게 구성하나요?
기본적으로 이것은 Office 365 관리자가 구성하는 것이 아니라 사용자가 구성합니다.

SharePoint 사이트 관리자가 자신이 소유한 SharePoint 라이브러리에 IRM을 활성화 및 구성하듯이 비즈니스용 OneDrive는 사용자가 본인이 보유한 비즈니스용 OneDrive 라이브러리를 활성화 및 구성할 수 있게 디자인되었습니다. 그러나 이러한 사용자를 위해 PowerShell을 사용하여 이 작업을 수행할 수 있습니다. 지침은 [Office 365: 클라이언트 및 온라인 서비스 구성](./deploy-use/configure-office365.md) 문서에서 [SharePoint Online 및 비즈니스용 OneDrive: IRM 구성](./deploy-use/configure-office365.md#sharepoint-online-and-onedrive-for-business-irm-configuration) 섹션을 참조하세요.

## <a name="do-you-have-any-tips-or-tricks-for-a-successful-deployment"></a>배포 성공을 위한 팁이나 요령이 있나요?

많은 배포를 감독하고 고객, 파트너, 컨설턴트와 지원 엔지니어의 이야기를 들어본 결과, 경험을 바탕으로 전달할 수 있는 가장 중요한 팁 중 하나는 **단순한 정책을 디자인 및 배포**하라는 것입니다.

Azure Information Protection는 모든 사용자와 안전하게 공유할 수 있도록 하므로 데이터 보호 범위에 욕심을 부려도 좋습니다. 하지만 권한 사용 제한을 구성할 때는 신중해야합니다. 많은 조직에서 비즈니스에 대한 영향력이 가장 큰 것은 조직의 사람들에 대한 액세스를 제한하여 데이터 누출을 방지하는 것입니다. 물론, 사용자의 인쇄나 편집 등을 방지해야 하는 경우 훨씬 더 세분화할 수도 있습니다.  그러나 더 세분화된 제한은 정말로 높은 수준의 보안이 필요한 문서에 대한 예외로 유지하고, 처음부터 이러한 더 제한적인 사용 권한을 구현하지는 말고 보다 단계적으로 접근하도록 계획하십시오.

## <a name="how-do-we-regain-access-to-files-that-were-protected-by-an-employee-who-has-now-left-the-organization"></a>이제 조직을 떠난 직원이 보호하던 파일에 대한 액세스는 어떻게 확보하나요?
[슈퍼 사용자 기능](./deploy-use/configure-super-users.md)을 사용하십시오. 이 기능은 테넌트가 보호하는 모든 문서 및 전자 메일에 대한 권한이 있는 사용자에게 모든 권한 사용권을 부여합니다. 수퍼 사용자는 보호된 콘텐츠를 언제나 읽을 수 있고 필요한 경우 다른 사용자를 위해 보호를 제거하거나 다시 적용할 수 있습니다. 이 기능은 권한이 있는 서비스가 필요에 따라 파일을 인덱스 및 검사할 수 있도록 합니다.

## <a name="when-i-test-revocation-in-the-document-tracking-site-i-see-a-message-that-says-people-can-still-access-the-document-for-up-to-30-daysis-this-time-period-configurable"></a>문서 추적 사이트에서 해지를 테스트할 때 다른 사용자가 최대 30일 동안 문서에 계속 액세스할 수 있다는 메시지가 표시되는데, 이 기간을 구성할 수 있나요?

예. 이 메시지는 해당 특정 파일에 대한 [사용 라이선스](./deploy-use/configure-usage-rights.md#rights-management-use-license)를 나타냅니다.

파일을 해지하는 경우 해당 작업은 사용자가 Azure Rights Management 서비스에 인증하는 경우에만 적용될 수 있습니다. 따라서 파일의 사용권 유효 기간이 30일이고 사용자가 이미 문서를 연 경우 해당 사용자는 사용권 기간 동안 문서에 계속 액세스할 수 있습니다. 사용권이 만료되는 경우 사용자는 문서가 해지되어 액세스가 거부되는 시점에 다시 인증해야 합니다.

문서를 보호한 사용자인 [Rights Management 발급자](./deploy-use/configure-usage-rights.md#rights-management-issuer-and-rights-management-owner)는 이 해지에서 제외되며 문서에 항상 액세스할 수 있습니다.

테넌트에 대한 사용 라이선스 유효 기간에 대한 기본값은 30일이며, 이 설정은 레이블 또는 템플릿의 더 제한적인 설정에 따라 재정의할 수 있습니다. 사용 라이선스 및 구성하는 방법에 대한 자세한 내용은 [Rights Management 사용 라이선스](./deploy-use/configure-usage-rights.md#rights-management-use-license) 설명서를 참조하세요.

## <a name="can-rights-management-prevent-screen-captures"></a>Rights Management 기능을 사용하면 화면을 캡처할 수 없나요?
Rights Management는 **복사** [사용 권한](./deploy-use/configure-usage-rights.md)을 부여하지 않음으로써 화면 캡처가 Windows 플랫폼(Windows 7, Windows 8.1, Windows 10, Windows Phone) 및 Android에서 일반적으로 사용되는 화면 캡처 도구가 되지 않도록 할 수 있습니다. 그러나 iOS 및 Mac 장치에서 화면 캡처를 보호하도록 모든 앱을 허용하지 않으므로 브라우저(예: Outlook Web App 및 Office Online과 함께 사용하는 경우)에서도 화면 캡처를 막을 수 없습니다.

화면 캡처를 차단하면 실수나 부주의로 인한 기밀 또는 중요한 정보 공개를 방지할 수 있습니다. 그러나 사용자가 화면에 표시되는 데이터를 공유할 수 있는 방법은 여러 가지가 있으며 스크린 샷을 만드는 것은 한 가지 방법에 불과합니다. 예를 들어 표시되는 정보를 공유하려는 사용자가 휴대폰 카메라로 사진을 찍거나 데이터를 다시 입력하거나, 누군가에게 구두로 전달할 수도 있습니다.

이 예제에서 보여주듯이 모든 플랫폼과 모든 소프트웨어에서 화면 캡처를 차단하기 위해 Rights Management API를 지원했더라도 기술만으로 사용자가 하지 않아야 하는 데이터 공유를 항상 방지할 수 있는 것은 아닙니다. Rights Management는 권한 부여 및 사용 정책을 사용하여 중요한 데이터를 보호하는 데 도움이 될 수 있지만 이러한 엔터프라이즈 권한 관리 솔루션을 다른 제어 기능과 함께 사용해야 합니다. 예를 들어 물리적 보안을 구현하고, 조직 데이터에 액세스할 수 있도록 허가된 사람들을 신중하게 모니터링하고, 공유해서는 안 되는 데이터를 이해하도록 사용자를 교육하는 데 투자해야 합니다.

## <a name="whats-the-difference-between-a-user-protecting-an-email-with-do-not-forward-and-a-template-that-doesnt-include-the-forward-right"></a>전달 금지로 메일을 보호하는 사용자와 전달 권한이 없는 템플릿 간의 차이점은 무엇입니까?

이름 및 모양에도 불구하고 **전달 금지**는 전달 권한의 반대도 아니고 템플릿도 아닙니다. 실제로 메일 전달 제한 외에도, 첨부 파일 복사, 인쇄 및 저장 제한이 포함된 권한 집합입니다. 권한은 선택한 수신자를 통해 사용자에게 동적으로 적용되며, 관리자가 권한을 정적으로 할당하지 않습니다. 자세한 내용은 [Azure 권한 관리에 대한 사용 권한 구성](./deploy-use/configure-usage-rights.md) 항목의 [메일에 대한 전달 금지 옵션](./deploy-use/configure-usage-rights.md#do-not-forward-option-for-emails) 섹션을 참조하세요.

