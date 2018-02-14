---
title: "Azure RMS - AIP에 대한 FAQ"
description: "Azure Information Protection의 데이터 보호 서비스인 Azure RMS(Azure Rights Management)에 대한 질문과 대답입니다."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 01/08/2018
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.custom: askipteam
ms.assetid: 90df11c5-355c-4ae6-a762-351b05d0fbed
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 776293c73b5ca63d0bfd409d8330bfe8295c792e
ms.sourcegitcommit: 972acdb468ac32a28e3e24c90694aff4b75206fc
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/29/2018
---
# <a name="frequently-asked-questions-about-data-protection-in-azure-information-protection"></a>Azure Information Protection의 데이터 보호에 대한 질문과 대답

>*적용 대상: Azure Information Protection, Office 365*

Azure Information Protection의 데이터 보호 서비스인 Azure Rights Management에 대해 궁금한 점이 있으신가요? 이 곳에 답변이 있는지 알아보시기 바랍니다. 

## <a name="do-files-have-to-be-in-the-cloud-to-be-protected-by-azure-rights-management"></a>Azure Rights Management로 보호받으려면 파일이 클라우드에 있어야 하나요?
아니요. 그것은 일반적인 오해입니다. Azure Rights Management 서비스(및 Microsoft)는 정보 보호 프로세스의 일환으로 사용자의 데이터를 보거나 저장하지 않습니다. 사용자가 보호하는 정보는 사용자가 Azure에 정보를 명시적으로 저장하거나 Azure에 정보를 저장하는 또 다른 클라우드 서비스를 사용하지 않는 한 절대 Azure에 전송되거나 보관되지 않습니다. 

자세한 내용은 [Azure RMS는 내부적으로 어떻게 작동하나요?](../understand-explore/how-does-it-work.md)를 참조하여, 온-프레미스에서 생성하고 저장한 비법이 Azure Rights Management 서비스를 통해 보호되면서도 온-프레미스에 유지될 수 있는지 방법이 무엇인지 알아보시기 바랍니다.

## <a name="whats-the-difference-between-azure-rights-management-encryption-and-encryption-in-other-microsoft-cloud-services"></a>Azure Rights Management 암호화와 다른 Microsoft 클라우드 서비스 암호화의 차이는 무엇인가요?

Microsoft는 서로 다르고 종종 상호 보완되는 시나리오의 데이터를 보호할 수 있는 여러 가지 암호화 기술을 제공합니다. 예를 들어 Office 365는 Office 365에 저장된 데이터에 대해 유휴 시 암호화를 제공하는 반면에 Azure Information Protection의 Azure Rights Management 서비스는 데이터의 위치나 전송 방식에 상관없이 데이터가 보호될 수 있도록 데이터를 독립적으로 암호화합니다.

이러한 암호화 기술은 상호 보완적이며 이러한 기술을 사용하려면 독립적인 사용 설정과 구성이 필요합니다. 이런 과정에서 암호화에 자신의 키를 사용할 수 있는 옵션(다른 이름: "BYOK")이 있기도 합니다. 이러한 기술 중 하나에 BYOK를 사용하도록 설정해도 다른 기술에는 영향을 미치지 않습니다. 예를 들어 BYOK를 Azure Information Protection에 사용하고 다른 암호화 기술에는 사용하지 않을 수 있으며 반대의 경우도 가능합니다. 서로 다른 기술에 사용되는 키는 각 서비스의 암호화 옵션을 구성하는 방식에 따라 같거나 다를 수 있습니다.

## <a name="whats-the-difference-between-byok-and-hyok-and-when-should-i-use-them"></a>BYOK와 HYOK의 차이는 무엇이며 언제 사용하는 것이 좋은가요?

Azure Information Protection 컨텍스트의 BYOK(**Bring your own key**)는 Azure Rights Management 보호를 위해 온-프레미스에 자체 키를 만드는 경우에 적합합니다. 그런 다음, 키를 계속 소유하고 관리하는 Azure Key Vault의 HSM(하드웨어 보안 모듈)에 해당 키를 전송합니다. 이렇게 하지 않으면, Azure Rights Management 보호는 Azure에서 자동으로 생성되고 관리되는 키를 사용합니다. 이러한 기본 구성을 "고객 관리"(BYOK 옵션)가 아닌 "Microsoft 관리"라고 합니다.

BYOK에 대한 자세한 내용 및 조직에 이 키 토폴로지를 선택해야 할지 여부는 [Azure Information Protection 테넌트 키 계획 및 구현](../plan-design/plan-implement-tenant-key.md)을 참조하세요. 

Azure Information Protection 컨텍스트의 HYOK(**Hold Your Own Key**)는 클라우드에 저장된 키로 보호할 수 없는 문서 또는 이메일 하위 집합이 있는 일부 조직에 적합합니다. 이러한 조직의 경우 BYOK를 사용하여 키를 만들고 관리하는 경우에도 이러한 제한이 적용됩니다. 제한은 규정 또는 준수를 목적으로 하는 경우가 종종 있으며 HYOK 구성은 조직 외부에 절대 공유하지 말고 내부 네트워크에서만 소비해야 하며 모바일 장치에서 액세스할 필요가 없는 "일급 비밀" 정보에만 적용해야 합니다. 

이런 예외(일반적으로 보호해야 하는 콘텐츠의 10% 미만) 사항에 대해, 조직은 Active Directory Rights Management Services라는 온-프레미스 솔루션을 사용하여 온-프레미스에 유지되는 키를 만들 수 있습니다. 이 솔루션을 사용하면, 컴퓨터는 클라우드에서 Azure Information Protection 정책을 가져오지만 식별된 콘텐츠는 온-프레미스 키를 사용하여 보호할 수 있습니다.

HYOK에 대한 자세한 내용을 참고하거나 제한 사항과 지침 및 이에 대한 적용 시기를 파악하려면 [AD RMS 보호에 대한 HYOK(Hold Your Own Key) 요구 사항 및 제한 사항](../deploy-use/configure-adrms-restrictions.md)을 참조하세요.

## <a name="can-i-now-use-byok-with-exchange-online"></a>이제 Exchange Online에 BYOK를 사용할 수 있나요?

네, 이제 [Azure Information Protection을 기반으로 구축된 새로운 Office 365 메시지 암호화 기능 설정](https://support.office.com/article/7ff0c040-b25c-4378-9904-b1b50210d00e)의 지침에 따라 Exchange Online에서 BYOK를 사용할 수 있습니다. 이 지침을 통해 새로운 Office 365 메시지 암호화는 물론 Azure Information Protection용 BYOK 사용을 지원하는 Exchange Online의 새 기능을 사용할 수 있습니다.

이러한 변화에 대한 자세한 내용은 [Office 365 메시지 암호화에서 사용할 수 있는 새로운 기능](https://techcommunity.microsoft.com/t5/Security-Privacy-and-Compliance/Email-Encryption-and-Rights-Protection/ba-p/110801) 블로그 공지를 참조하세요.

## <a name="where-can-i-find-information-about-third-party-solutions-that-integrate-with-azure-rms"></a>Azure RMS와 통합된 타사 솔루션에 대한 정보는 어디에서 찾을 수 있나요?

많은 소프트웨어 공급 업체가 이미 솔루션을 보유하고 있거나 Azure Rights Management와 통합된 솔루션을 구현하고 있으며 그 목록은 바르게 증가하고 있습니다. [RMS 지원 솔루션](requirements-applications.md#rms-enlightened-solutions) 목록을 확인하거나 Twitter의 [Microsoft Mobility@MSFTMobility](https://twitter.com/MSFTMobility)에서 최신 정보를 확인하는 것이 유용할 수 있습니다. [개발자 가이드](../develop/developers-guide.md)에서 통합 관련 질문을 확인할 수 있고 Azure Information Protection에 대한 통합 관련 질문은 [Yammer 사이트](https://www.yammer.com/AskIPTeam)에 게시할 수 있습니다.

## <a name="is-there-a-management-pack-or-similar-monitoring-mechanism-for-the-rms-connector"></a>RMS 커넥터와 유사한 모니터링 메커니즘이나 관리 팩이 있나요?

Rights Management 커넥터가 정보, 경고 및 오류 메시지를 이벤트 로그에 기록하지만 이러한 이벤트에 대한 모니터링이 포함된 관리 팩은 없습니다. 하지만 올바른 조치를 취하는 데 도움이 되는 자세한 정보가 포함된 이벤트 목록과 그에 대한 설명이 [Azure Rights Management 커넥터 모니터링](../deploy-use/monitor-rms-connector.md)에 문서화되어 있습니다.

## <a name="do-you-need-to-be-a-global-admin-to-configure-azure-rms-or-can-i-delegate-to-other-administrators"></a>Azure RMS를 구성하려면 전역 관리자여야 하나요? 다른 관리자에게 위임이 가능한가요?

Office 365 테넌트 또는 Azure AD 테넌트의 전역 관리자는 Azure Rights Management 서비스의 모든 관리 작업을 분명히 실행할 수 있습니다. 하지만 다른 사용자에게 관리 권한을 할당하려는 경우에는 Azure RMS PowerShell cmdlet인, [Add-AadrmRoleBasedAdministrator](/powershell/module/aadrm/add-aadrmrolebasedadministrator)를 사용해야 합니다. 관리자 역할은 사용자 계정 또는 그룹 단위로 할당할 수 있습니다. 두 가지 가능한 역할은 **전역 관리자** 및 **커넥터 관리자**입니다. 

역할 이름의 의미처럼 첫 번째 역할은 Azure Rights Management의 모든 관리 작업을 실행할 수 있는 권한을 부여하며(다른 클라우드 서비스의 전역 관리자로 만드는 것이 아님) 두 번째 역할은 RMS(Rights Management) 커넥터를 실행할 수 있는 권한만 부여합니다.

유의 사항:

- Office 365의 전역 관리자 및 Azure AD의 전역 관리자만 Office 365 관리 센터를 사용하여 Azure RMS를 구성할 수 있습니다. Azure Information Protection용 Azure Portal을 사용하면 전역 관리자 또는 보안 관리자로 로그인할 수 있습니다.

- Azure RMS에 대한 전역 관리자 역할을 할당 받은 사용자는 Azure RMS PowerShell 명령을 사용하여 Azure RMS를 구성해야 합니다. 특정 작업에 적합한 cmdlet을 찾으려면 [Windows PowerShell을 사용하여 Azure Rights Management 관리](../deploy-use/administer-powershell.md)를 참조하세요.

- [온보딩 컨트롤](../deploy-use/activate-service.md#configuring-onboarding-controls-for-a-phased-deployment)을 구성한 경우 이 구성은 Azure RMS(RMS 커넥터 제외)를 관리하는 권한에 영향을 미치지 않습니다. 콘텐츠를 보호할 수 있는 권한이 “IT 부서” 그룹으로 제한되도록 온보딩 컨트롤을 구성한 경우, RMS 커넥터를 설치하고 구성하는 데 사용하는 계정이 해당 그룹의 멤버여야 합니다. 

- Azure RMS의 관리자(예: 테넌트의 전역 관리자 또는 Azure RMS 전역 관리자)는 Azure RMS로 보호된 문서나 이메일의 보호를 자동으로 제거할 수 없습니다. Azure RMS의 슈퍼 사용자로 할당된 사용자만, 슈퍼 사용자 기능이 활성화 되어 있는 경우에 이 작업을 수행할 수 있습니다. 단, 테넌트의 전역 관리자 및 모든 Azure RMS 전역 관리자는 사용자(자신의 계정 포함)에게 슈퍼 사용자를 할당할 수 있습니다. 슈퍼 사용자 기능도 사용하도록 설정할 수 있습니다. 이러한 작업은 Azure RMS 관리자 로그에 기록됩니다. 자세한 내용은 [Azure Rights Management 및 검색 서비스 또는 데이터 복구를 위한 슈퍼 사용자 구성](../deploy-use/configure-super-users.md)의 모범 사례 섹션을 참조하세요. 

>[!NOTE]
> Azure Rights Management 보호를 구성할 수 있는 템플릿과 새 옵션이 Azure Portal로 이동했으며, 여기에서는 전역 관리자 액세스 외에 보안 관리자도 지원됩니다. 

## <a name="how-do-i-create-a-new-custom-template-in-the-azure-portal"></a>Azure Portal에서 새 사용자 지정 템플릿을 어떻게 만드나요?

사용자 지정 템플릿은 Azure Portal로 이동되었습니다. 이곳에서 템플릿으로 계속 관리하거나 템플릿을 레이블로 변환할 수 있습니다. 새 템플릿을 만들려면 새 레이블을 만들고 Azure RMS에 대한 데이터 보호 설정을 구성합니다. 이렇게 하면 Rights Management 템플릿과 통합되는 서비스 및 응용 프로그램을 통해 액세스할 수 있는 새 템플릿이 만들어집니다.

Azure Portal의 템플릿에 대한 자세한 내용은 [Azure Information Protection의 템플릿 구성 및 관리](../deploy-use/configure-policy-templates.md)를 참조하세요.

## <a name="ive-protected-a-document-and-now-want-to-change-the-usage-rights-or-add-usersdo-i-need-to-reprotect-the-document"></a>문서를 보호한 후 사용 권한을 변경하거나 사용자를 추가하려면 문서를 다시 보호해야 하나요?

레이블이나 템플릿을 사용하여 문서가 보호된 경우에는 문서를 다시 보호할 필요가 없습니다. 사용 권한을 변경하거나 새 그룹(또는 사용자)을 추가하여 레이블 또는 템플릿을 수정한 다음 변경 내용을 저장하고 게시합니다.

- 변경하기 전에 사용자가 문서에 액세스하지 않은 경우, 사용자가 문서를 열자마자 변경 내용이 적용됩니다. 

- 사용자가 이미 문서에 액세스한 경우, [사용 라이선스](../deploy-use/configure-usage-rights.md#rights-management-use-license)가 만료되면 변경 내용이 적용됩니다. 사용 라이선스가 만료될 때까지 기다릴 수 없는 경우에만 문서를 다시 보호합니다. 다시 보호하면 효과적으로 새 버전의 문서가 만들어지고 따라서 사용자를 위한 새 사용 라이선스가 만들어집니다.

또는, 필요한 권한에 대해 이미 그룹을 구성한 경우에는, 사용자를 포함하거나 제외하도록 그룹 멤버 자격을 변경할 수 있으며, 그러면 레이블이나 테이블을 변경할 필요가 없습니다. Azure Rights Management 서비스에서 그룹 멤버 자격이 [캐시되기](../plan-design/prepare.md#group-membership-caching-by-azure-information-protection) 때문에 변경 내용이 적용되기 까지 약간의 지연이 있을 수 있습니다.

사용자 지정 권한을 사용하여 문서를 보호한 경우 기존 문서에 대한 권한을 변경할 수 없습니다. 문서를 다시 보호하고 새 버전의 이 문서에 필요한 모든 사용자 및 모든 사용 권한을 지정해야 합니다. 보호된 문서를 다시 보호하려면 모든 권한 사용 권한이 있어야 합니다.

팁: 문서가 템플릿으로 보호되었는지 또는 사용자 지정 권한을 사용하여 보호되었는지 확인하려면 [Get-AIPFileStatus](/powershell/module/azureinformationprotection/get-aipfilestatus) PowerShell cmdlet을 사용합니다. 사용자 지정 권한의 **제한된 액세스**에 대한 템플릿 설명이 [Get-RMSTemplate](/powershell/module/azureinformationprotection/get-rmstemplate)을 실행하면 표시되지 않는 고유 템플릿 ID와 함께 항상 표시됩니다.

## <a name="i-have-a-hybrid-deployment-of-exchange-with-some-users-on-exchange-online-and-others-on-exchange-serveris-this-supported-by-azure-rms"></a>Exchange Online에 일부 사용자가 있고 Exchange Server에 다른 사용자가 있는 Exchange 혼합 배포가 있습니다. 이런 경우가 Azure RMS에서 지원되나요?
물론입니다. 그리고 좋은 점은 사용자가 두 가지 Exchange 배포에서 보호된 이메일 및 첨부 파일을 원활하게 보호하고 사용할 수 있습니다. 이렇게 구성하려면 [Azure RMS를 활성화](../deploy-use/activate-service.md)하고 [Exchange Online용 IRM을 사용하도록 설정](https://technet.microsoft.com/library/dn151475%28v=exchg.150%29.aspx)한 다음, Exchange Server용 [RMS 커넥터를 배포하고 구성](../deploy-use/deploy-rms-connector.md)합니다.

## <a name="if-i-use-this-protection-for-my-production-environment-is-my-company-then-locked-into-the-solution-or-risk-losing-access-to-content-that-we-protected-with-azure-rms"></a>내 프로덕션 환경에 이런 보호를 사용하면, 회사가 솔루션에 갇히거나 Azure RMS로 보호된 콘텐츠에 대한 액세스가 손실될 위험이 있나요?
아니요, Azure Rights Management 서비스를 더 이상 사용하지 않기로 결정하더라도 데이터를 항상 제어할 수 있고 계속 액세스할 수 있습니다. 자세한 내용은 [Azure Rights Management 서비스 해제 및 비활성화](../deploy-use/decommission-deactivate.md)를 참조하세요.

## <a name="can-i-control-which-of-my-users-can-use-azure-rms-to-protect-content"></a>Azure RMS를 사용하여 콘텐츠를 보호할 수 있는 사용자를 제어할 수 있나요?
네, Azure Rights Management 서비스에는 이런 시나리오를 위한 사용자 온보딩 제어 기능이 있습니다. 자세한 내용은 [Azure Rights Management 활성화](../deploy-use/activate-service.md) 문서의 [단계별 배포를 위한 온보딩 제어 구성](../deploy-use/activate-service.md#configuring-onboarding-controls-for-a-phased-deployment) 섹션을 참조하세요.

## <a name="can-i-prevent-users-from-sharing-protected-documents-with-specific-organizations"></a>사용자가 보호된 문서를 특정 조직과 공유하지 못하게 할 수 있습니까?
Azure Rights Management 서비스를 데이터 보호에 사용하는 가장 큰 장점 중 하나는 Azure AD에서 인증을 처리해 주기 때문에 각 파트너 조직에 대한 명시적 트러스트를 구성하지 않고도 B2B 공동 작업이 지원된다는 점입니다.

사용자가 특정 조직과 문서를 안전하게 공유하지 못하도록 관리하는 옵션은 없습니다. 예를 들어 신뢰하지 않는 조직이나 경쟁사의 조직을 차단하려고 합니다. Azure Rights Management 서비스가 보호된 문서를 이러한 조직의 사용자에게 보내지 못하도록 하는 것은 의미가 없습니다. 그러면 사용자가 보호되지 않은 문서를 공유할 수 있기 때문입니다. 이것은 이 시나리오에서 가장 원하지 않는 상황입니다. 예를 들어, 회사 기밀 문서를 누가 다른 조직의 어떤 사용자와 공유하는지 파악할 수 없지만 Azure Rights Management 서비스로 보호되는 문서(또는 이메일)에서는 이것이 가능합니다.

## <a name="when-i-share-a-protected-document-with-somebody-outside-my-company-how-does-that-user-get-authenticated"></a>보호되는 문서를 회사 외부의 누군가와 공유할 때 해당 사용자를 어떻게 인증하나요?

기본적으로 Azure Rights Management 서비스는 Azure Active Directory 계정 및 연결된 이메일 주소를 사용하여 사용자를 인증하며, 이로 인해 관리자의 B2B 공동 작업이 편리해집니다. 다른 조직에서 Azure 서비스를 사용하는 경우, 사용자는 Azure Active Directory에 계정이 이미 있으며, 이러한 계정이 온-프레미스에서 만들어지고 관리된 다음, Azure로 동기화된 경우에도 마찬가지입니다. 조직에 Office 365가 있는 경우, 이 서비스 역시 내부적으로 Azure Active Directory를 사용자 계정에 사용합니다. 사용자의 조직에 Azure에서 관리되는 계정이 없는 경우 사용자가 [개인용 RMS](../understand-explore/rms-for-individuals.md)에 등록하면, 사용자 계정이 있는 조직에 관리되지 않는 Azure 테넌트와 디렉터리가 만들어진 다음, 사용자(및 후속 사용자)가 Azure Rights Management 서비스에 인증될 수 있습니다.

이러한 계정에 대한 인증 방법은 조직의 관리자가 Azure Active Directory 계정을 어떻게 구성했는지에 따라 다양합니다. 예를 들어, 이러한 계정에 대해 만든 암호, MFA(다단계 인증), 페더레이션 또는 Active Directory Domain Services에서 만든 암호를 사용한 다음, Azure Active Directory에 동기화될 수 있습니다.

Office 문서 첨부 파일이 있는 이메일을 Azure AD에 계정이 없는 사용자로부터 보호하면 인증 방법이 변경됩니다. Azure Rights Management 서비스는 Gmail과 같이 많이 사용되는 소셜 ID 공급자와 페더레이션되어 있습니다. 사용자의 이메일 공급자가 지원되는 경우 사용자는 해당 서비스에 로그인할 수 있고 해당 이메일 공급자가 인증을 담당합니다. 사용자의 이메일 공급자가 지원되지 않는 경우, 또는 사용자가 원하는 경우, 사용자를 인증하고 보호된 문서가 포함된 이메일을 웹 브라우저에 표시하는 OTP(일회성 암호)를 신청할 수 있습니다.

## <a name="can-i-add-external-users-people-from-outside-my-company-to-custom-templates"></a>외부 사용자(회사 외부 사람)를 사용자 지정 템플릿에 추가할 수 있나요?

예 Azure Portal에서 구성할 수 있는 [보호 설정](../deploy-use/configure-policy-protection.md)을 통해 조직 외부의 사용자와 그룹 및 다른 조직의 모든 사용자에도 권한을 추가할 수 있습니다. [Office 365 메시지 암호화의 새로운 기능](https://support.office.com/article/7ff0c040-b25c-4378-9904-b1b50210d00e)을 사용한 이메일 발송에만 템플릿을 사용하려는 경우가 아니면 소셜 ID(예: Gmail 및 Microsoft)의 계정이나 Azure AD에 없는 다른 계정을 추가하지 마십시오.

Azure Information Protection 레이블이 있으면 먼저 사용자 지정 템플릿을 레이블로 변환해야 Azure Portal에서 이러한 보호 설정을 구성할 수 있습니다. 자세한 내용은 [Azure Information Protection의 템플릿 구성 및 관리](../deploy-use/configure-policy-templates.md)를 참조하세요.

아니면, PowerShell을 사용하여 외부 사용자를 사용자 지정 템플릿(및 레이블)에 추가할 수 있습니다. 이 구성을 위해서는 템플릿을 업데이트하는 데 사용하는 권한 정의 개체를 사용해야 합니다.

1. [New-AadrmRightsDefinition](/powershell/module/aadrm/new-aadrmrightsdefinition) cmdlet을 사용하여 변수를 만들어서 권한 정의 개체에 외부 이메일 주소와 권한을 지정합니다.

2. [Set-AadrmTemplateProperty](/powershell/module/aadrm/set-aadrmtemplateproperty) cmdlet을 사용하여 이 변수를 RightsDefinition 매개 변수에 제공합니다.
    
    기존 템플릿에 사용자를 추가할 때, 템플릿에 새 사용자 외에 기존 사용자에 대한 권한 정의 개체를 정의해야 합니다. 이 시나리오의 경우 cmdlet [예제](/powershell/module/aadrm/set-aadrmtemplateproperty#examples) 섹션의 **예제 3: 사용자 지정 템플릿에 새 사용자 및 권한 추가**가 유용할 수 있습니다. 

## <a name="what-type-of-groups-can-i-use-with-azure-rms"></a>Azure RMS에서 어떤 유형의 그룹을 사용할 수 있나요?
대부분의 시나리오는 Azure AD에서 이메일 주소가 있는 모든 그룹 유형을 사용할 수 있습니다. 이 규칙이 일반적으로 사용 권한을 할당할 때는 항상 적용되지만 Azure Rights Management 서비스 관리에는 몇 가지 예외가 있습니다. 자세한 내용은 [그룹 계정에 대한 Azure Information Protection 요구 사항](../plan-design/prepare.md#azure-information-protection-requirements-for-group-accounts)을 참조하세요.

## <a name="how-do-i-send-a-protected-email-to-a-gmail-or-hotmail-account"></a>보호된 이메일을 Gmail 또는 Hotmail 계정에 어떻게 보내나요?

Exchange Online 및 Azure Rights Management 서비스를 사용하는 경우에는 사용자에게 보호된 메시지로 이메일을 보냅니다. 예를 들어 웹용 Outlook의 명령 모음에서 새 **보호** 단추를 선택하고 Outlook **전달 금지** 단추나 메뉴 옵션을 사용할 수 있습니다. 또는 Azure Information Protection 레이블을 선택하면 전달 금지가 자동으로 적용되고 이메일이 분류됩니다. 

받는 사람에게 Gmail, Yahoo 또는 Microsoft 계정에 로그인 한 다음, 보호된 이메일을 읽을 수 있는 옵션이 표시됩니다. 또는 OTP(일회성 암호)로 브라우저에서 이메일을 읽을 수 있는 옵션을 선택할 수도 있습니다.

이런 시나리오를 지원하려면 Exchange Online에서 Azure Rights Management 서비스 및 Office 365 메시지 암호화의 새 기능을 사용하도록 설정해야 합니다. 이 구성에 대한 자세한 내용은 [Exchange Online: IRM 구성](../deploy-use/configure-office365.md#exchange-online-irm-configuration)을 참조하세요.

모든 장치의 모든 이메일 계정 지원을 포함하는 새로운 기능에 대한 자세한 내용은 [Office 365 메시지 암호화에 사용할 수 있는 새 기능 공지](https://techcommunity.microsoft.com/t5/Security-Privacy-and-Compliance/Email-Encryption-and-Rights-Protection/ba-p/110801)의 블로그 게시물을 참조하세요.

## <a name="what-devices-and-which-file-types-are-supported-by-azure-rms"></a>Azure RMS에서 어떤 장치와 어떤 파일 형식이 지원되나요?
Azure Rights Management 서비스를 지원하는 장치 목록은 [Azure Rights Management 데이터 보호를 지원하는 클라이언트 장치](../get-started/requirements-client-devices.md)를 참조하세요. 지원되는 모든 장치가 현재 모든 Rights Management 기능을 지원할 수 있는 것은 아니므로 [RMS 지원 응용 프로그램](../get-started/requirements-applications.md#rms-enlightened-applications)의 테이블을 반드시 확인하는 것이 좋습니다.

Azure Rights Management 서비스는 모든 파일 형식을 지원할 수 있습니다. 텍스트, 이미지, Microsoft Office(Word, Excel, PowerPoint) 파일, .pdf 파일 및 일부 다른 응용 프로그램 파일에 대해 Azure Rights Management는 암호화와 권한 적용이 모두 포함되는 기본 보호를 제공합니다. 다른 모든 응용 프로그램 및 파일 형식의 경우, 일반 보호가 파일 캡슐화 및 인증을 제공하여 사용자가 파일을 열도록 인증되었는지 확인합니다.

Azure Rights Management에서 기본적으로 지원되는 파일 이름 확장명 목록은 [Azure Information Protection 클라이언트로 보호되는 파일 형식](../rms-client/client-admin-guide-file-types.md)을 참조하세요. 목록에 없는 파일 이름 확장명은 파일에 일반 보호를 자동으로 적용하는 Azure Information Protection 클라이언트를 사용하여 지원됩니다.

## <a name="how-do-i-configure-a-mac-computer-to-protect-and-track-documents"></a>Mac 컴퓨터에서 문서를 보호하고 추적하도록 어떻게 구성하나요?

먼저, https://portal.office.com에서 소프트웨어 설치 링크를 사용하여 Mac용 Office를 설치했는지 확인합니다. 전체 지침은 [PC 또는 Mac에 Office 365 또는 Office 2016 다운로드, 설치 또는 다시 설치](https://support.office.com/en-us/article/Download-and-install-or-reinstall-Office-365-or-Office-2016-on-a-PC-or-Mac-4414EAAF-0478-48BE-9C42-23ADC4716658)를 참조하세요.

Outlook을 열고 Office 365 회사 또는 학교 계정을 사용하여 프로필을 만듭니다. 그런 다음, 새 메시지를 만들고 다음을 수행하여 Azure Rights Management 서비스를 사용하여 문서와 이메일을 보호할 수 있도록 Office를 구성합니다.

1. 새 메시지의 **옵션** 탭에서 **권한**을 클릭한 다음, **자격 증명 확인**을 클릭합니다.

2. 메시지가 표시되면 Office 365 회사 또는 학교 계정 세부 정보를 다시 입력하고 **로그인**을 선택합니다. 
    
    이제 Azure Rights Management 템플릿이 다운로드되고 **자격 증명 확인**이 **제한 없음**, **전달 금지** 및 테넌트용으로 게시된 Azure Rights Management 템플릿이 포함된 옵션으로 바뀝니다. 이제 새 메시지를 취소할 수 있습니다.

이메일 메시지나 문서를 보호하려면: **옵션** 탭에서 **권한**을 클릭하고 이메일이나 문서를 보호할 옵션이나 템플릿을 선택합니다.

문서를 보호한 후에 추적하려면: Azure Information Protection 클라이언트가 설치된 Windows 컴퓨터에서 Office 응용 프로그램이나 파일 탐색기를 사용하여 문서 추적 사이트에 문서를 등록합니다. 지침은 [문서 추적 및 해지](../rms-client/client-track-revoke.md)를 참조하세요. Mac 컴퓨터의 경우 이제 웹 브라우저를 사용하여 문서 추적 사이트(https://track.azurerms.com)로 이동하여 문서를 추적하고 해지할 수 있습니다.

## <a name="when-i-open-an-rms-protected-office-document-does-the-associated-temporary-file-become-rms-protected-as-well"></a>RMS 보호 Office 문서를 열면 연결된 임시 파일도 RMS 보호가 적용되나요?
아니요. 이 시나리오에서 연결된 임시 파일에는 원본 문서의 데이터가 포함되지 않고 그 대신 파일이 열려있는 동안 사용자가 입력한 내용만 포함됩니다. 원본 파일과 달리 임시 파일은 명백히 공유하도록 설계되지 않았고 장치에 유지되며 BitLocker 및 EFS와 같은 로컬 보안 컨트롤에 의해 보호됩니다.

## <a name="a-feature-i-am-looking-for-doesnt-seem-to-work-with-sharepoint-protected-librariesis-support-for-my-feature-planned"></a>내가 원하는 기능이 SharePoint 보호 라이브러리에서 작동하지 않는 것 같습니다. 기능에 대한 지원이 계획되어 있나요?
현재 SharePoint는 Rights Management 템플릿, 문서 보호 및 일부 기타 기능을 지원하지 않는 IRM 보호 라이브러리를 사용하여 RMS 보호 문서를 지원합니다. 자세한 내용은 [Office 응용 프로그램 및 서비스](../understand-explore/office-apps-services-support.md) 문서의 [SharePoint Online 및 SharePoint Server](../understand-explore/office-apps-services-support.md#sharepoint-online-and-sharepoint-server) 섹션을 참조하세요.

아직 지원되지 않는 특정 기능에 관심이 있는 경우 [Enterprise Mobility + Security 블로그](https://blogs.technet.microsoft.com/enterprisemobility/?product=azure-rights-management-services)의 공지에 주목해 주세요.

## <a name="how-do-i-configure-one-drive-for-business-in-sharepoint-online-so-that-users-can-safely-share-their-files-with-people-inside-and-outside-the-company"></a>사용자가 회사 내부와 외부의 사용자들과 파일을 안전하게 공유하도록 하려면 SharePoint Online에서 One Drive for Business를 어떻게 구성하나요?
기본적으로 Office 365 관리자는 구성할 필요가 없으며 사용자가 구성해야 합니다.

SharePoint 사이트 관리자가 자신이 소유하는 SharePoint 라이브러리에 대해 IRM을 사용하도록 설정하고 구성하듯이, OneDrive for Business는 사용자가 자신의 OneDrive for Business 라이브러리에 대해 IRM을 사용하도록 설정하고 구성하도록 설계되었습니다. 단, PowerShell을 사용하면 사용자를 위한 구성이 가능합니다. 지침은 [Office 365: 클라이언트 및 온라인 서비스를 위한 구성](../deploy-use/configure-office365.md) 문서의 [SharePoint Online 및 OneDrive for Business: IRM 구성](../deploy-use/configure-office365.md#sharepoint-online-and-onedrive-for-business-irm-configuration) 섹션을 참조하세요.

## <a name="do-you-have-any-tips-or-tricks-for-a-successful-deployment"></a>성공적인 배포를 위한 팁이나 요령이 있나요?

많은 배포를 감독하고 고객, 파트너, 컨설턴트 및 지원 엔지니어의 의견을 들어볼 때 경험을 기반으로 알려드릴 수 있는 가장 큰 팁은 **간단한 정책 디자인 및 배포**입니다.

Azure Information Protection은 누구와든 안전한 공유를 지원하기 때문에 데이터 보호 범위를 충분히 믿을 수 있습니다. 단, 권한 사용 제한을 구성할 때는 신중해야 합니다. 많은 조직에서 가장 큰 비즈니스 영향은 조직의 사람들에 대한 액세스를 제한하여 데이터 유출을 방지하는 데서 비롯됩니다. 물론 인쇄 편집 등을 막아야 하는 경우 훨씬 더 세분화할 수 있습니다. 보다 세분화된 제한은 높은 수준의 보안이 정말로 필요한 문서를 위한 예외로 두고, 제한적인 사용 권한을 처음부터 구현하지 말고 보다 단계적인 접근을 계획해야 합니다.

## <a name="how-do-we-regain-access-to-files-that-were-protected-by-an-employee-who-has-now-left-the-organization"></a>조직을 떠난 직원이 보호한 파일에 대한 액세스 권한을 다시 확보하려면 어떻게 해야 하나요?
[슈퍼 사용자 기능](../deploy-use/configure-super-users.md)을 사용합니다. 이 기능은 권한 있는 사용자에게 테넌트가 보호한 모든 문서와 이메일에 대한 모든 권한 사용 권한을 부여합니다. 슈퍼 사용자는 보호된 콘텐츠를 항상 읽을 수 있고 필요한 경우에는 보호를 제거하거나 다른 사용자를 위해 다시 보호할 수 있습니다. 동일한 기능을 통해 인증 서비스는 필요한 경우 파일을 인덱싱하고 검사할 수 있습니다.

## <a name="when-i-test-revocation-in-the-document-tracking-site-i-see-a-message-that-says-people-can-still-access-the-document-for-up-to-30-daysis-this-time-period-configurable"></a>문서 추적 사이트에서 해지를 테스트할 때 문서에 최대 30일까지 계속 액세스할 수 있다는 메시지가 표시됩니다. 이 기간을 구성할 수 있나요?

예 이 메시지에는 해당 파일에 대한 [사용 라이선스](../deploy-use/configure-usage-rights.md#rights-management-use-license)가 반영됩니다. 

파일을 해지하면 사용자가 Azure Rights Management 서비스에 인증하는 경우에만 해당 동작이 적용될 수 있습니다. 따라서 파일의 사용 라이선스 유효 기간이 30일이고 사용자가 해당 파일을 이미 열었으면, 사용자는 사용 라이선스 기간 동안 문서에 대한 액세스 권한을 계속 갖습니다. 사용 라이선스가 만료되면 문서가 해지되기 때문에 사용자의 액세스가 거부되는 시점에서 다시 인증해야 합니다.

문서를 보호한 사용자인 [Rights Management 발급자](../deploy-use/configure-usage-rights.md#rights-management-issuer-and-rights-management-owner)는 해지에서 제외되고 해당 문서에 항상 액세스할 수 있습니다. 

테넌트에 대한 사용 라이선스 유효 기간의 기본값은 30일이며 이 설정은 레이블이나 템플릿의 보다 제한적인 설정으로 재정의할 수 있습니다. 사용 라이선스에 대한 자세한 내용 및 구성 방법은 [Rights Management 사용 라이선스](../deploy-use/configure-usage-rights.md#rights-management-use-license) 문서를 참조하세요.

## <a name="can-rights-management-prevent-screen-captures"></a>Rights Management로 화면 캡처를 방지할 수 있나요?
**복사** [사용 권한](../deploy-use/configure-usage-rights.md)을 부여하지 않으면 Rights Management가 Windows 플랫폼(Windows 7, Windows 8.1, Windows 10, Windows Phone) 및 Android에서 일반적으로 사용되는 많은 화면 캡처 도구에서 화면 캡처를 막을 수 있습니다. 하지만, iOS 및 Mac 장치에서는 앱에서 화면 캡처를 막을 수 없으며 브라우저(예: Outlook Web App 및 Office Online에서 사용하는 경우)에서도 화면 캡처를 막을 수 없습니다.

화면 캡처를 막으면 기밀 또는 중요한 정보가 실수나 부주의로 노출되는 것을 방지하는 데 도움이 됩니다. 그러나 화면에 표시되는 데이터를 사용자가 공유할 수 있는 방법은 많으며 화면 캡처는 그 중 한 가지 방법일 뿐입니다. 예를 들어, 표시되는 정보를 공유하려는 사용자는 자신의 카메라 폰을 사용하여 사진을 찍거나, 데이터를 다시 입력하거나, 누군가에게 간단히 말로 전달할 수 있습니다.

이런 사례가 보여주듯이 모든 플랫폼과 소프트웨어가 Rights Management API를 지원하여 화면 캡처를 차단하더라도 공유하지 말아야 하는 데이터를 사용자가 공유하는 것을 기술만으로는 막을 수 없습니다. Rights Management는 권한 부여와 사용 정책을 사용하여 중요한 데이터를 보호하는 데 도움이 되지만 이 엔터프라이즈 권한 관리 솔루션은 다른 제어와 함께 사용되어야 합니다. 예를 들어, 물리적 보안을 구현하고, 조직의 데이터에 액세스 권한이 부여된 사람들을 주의 깊게 확인 및 모니터링하고, 공유하지 말아야 하는 데이터를 이해하도록 사용자 교육에 투자합니다.

## <a name="whats-the-difference-between-a-user-protecting-an-email-with-do-not-forward-and-a-template-that-doesnt-include-the-forward-right"></a>전달 금지가 포함된 이메일로 보호하는 것과 전달이 포함되지 않은 템플릿으로 보호하는 것의 차이가 무엇인가요?

이름과 모양에도 불구하고 **전달 금지**는 전달 권한이나 템플릿의 반대가 아닙니다. 실제로 이메일 전달 제한 외에 첨부 파일 복사, 인쇄 및 저장 제한이 포함된 일련의 권한입니다. 이러한 권한은 선택된 받는 사람을 통해 사용자에게 동적으로 적용되며 관리자에 의해 고정적으로 할당되지 않습니다. 자세한 내용은 [Azure Rights Management에 대한 사용 권한 구성](../deploy-use/configure-usage-rights.md)의 [이메일에 대한 전달 금지 옵션](../deploy-use/configure-usage-rights.md#do-not-forward-option-for-emails) 섹션을 참조하세요.

[!INCLUDE[Commenting house rules](../includes/houserules.md)]


