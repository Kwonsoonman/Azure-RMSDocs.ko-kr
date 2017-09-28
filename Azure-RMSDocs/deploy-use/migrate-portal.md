---
title: "Azure 클래식 포털에서 마이그레이션 - AIP"
description: "Azure 클래식 포털에서 수행했던 관리 작업을 Azure Portal에서 한눈에 볼 수 있습니다."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 09/19/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 57a1073c-02e0-441b-bf49-c6b72fdba24f
ms.reviewer: demizets
ms.suite: ems
ms.openlocfilehash: 8462a0c351ef8a75a7cd31bae923fd5ec3b8999f
ms.sourcegitcommit: f7ef0f040ae4af4bf1283ebcb0750b65b6939313
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/20/2017
---
# <a name="tasks-that-you-used-to-do-with-the-azure-classic-portal"></a>Azure 클래식 포털과 관련된 작업

>*적용 대상: Azure Information Protection, Office 365*

Azure Rights Management 서비스를 관리하기 위한 Azure 클래식 포털에 사용되며 Azure Portal로 전환하는 데 도움이 필요합니까? 

> [!NOTE]
> Azure 클래식 포털은 **2017년 11월 30일**에 사용 중지됩니다. 자세한 내용은 [미래로의 Azure AD 관리자 환경: Azure 클래식 포털 사용 중지(영문)](https://blogs.technet.microsoft.com/enterprisemobility/2017/09/18/marching-into-the-future-of-the-azure-ad-admin-experience-retiring-the-azure-classic-portal/) 블로그 게시물 공지 사항을 참조하세요.

## <a name="how-to-do-your-familiar-admin-tasks"></a>친숙한 관리 작업을 수행하는 방법

다음 정보는 새로운 포털로 신속하게 전환하는 데 도움이 됩니다.

|Azure 클래식 포털|Azure Portal에서 이 작업을 수행하는 방법
|-----------|--------------------|
|처음으로 구성 설정 액세스|1. 테넌트에 대한 전역 관리자 또는 보안 관리자로 Azure Portal에 로그인합니다.<br /><br />2. 허브 메뉴에서 **새로 만들기**를 클릭한 다음 **MARKETPLACE** 목록에서 **보안 + ID**를 클릭합니다.<br /><br />3. **보안 + ID** 블레이드의 **추천 앱** 목록에서 **Azure Information Protection**을 선택합니다. 그런 다음 **Azure Information Protection** 블레이드에서 **만들기**를 클릭합니다.<br /><br />이 작업으로 **Azure Information Protection** 블레이드가 만들어지며, 다음에 포털에 로그인할 때 허브 **추가 서비스** 목록에서 서비스를 선택할 수 있습니다.
|새 템플릿 만들기|보호를 적용하는 레이블을 만들고, **권한 설정**을 사용하여 권한, 만료 및 오프라인 액세스를 정의합니다. <br /><br />내부적으로 이 구성에서는 Rights Management 템플릿과 통합되는 서비스 및 응용 프로그램을 통해 액세스할 수 있는 새 사용자 지정 템플릿을 만듭니다.<br /><br />자세한 내용은 [새 템플릿 만들기](configure-policy-templates.md#to-create-a-new-template)를 참조하세요.
|템플릿 속성 편집: <br /><br />- 템플릿 이름 및 설명<br /><br />- 사용 권한, 콘텐츠 만료 및 오프라인 액세스 설정|아직 수행하지 않은 경우 [템플릿을 레이블로 변환](configure-policy-templates.md#to-convert-templates-to-labels)한 후 다음을 수행합니다<br /><br />1. 레이블 이름 및 설명을 변경합니다.<br /><br />2. 레이블의 보호 설정을 변경하여 권한, 만료 및 오프라인 액세스 설정을 업데이트합니다.<br /><br />자세한 내용은 [Rights Management 보호에 대한 레이블 구성](configure-policy-protection.md#to-configure-a-label-for-rights-management-protection)을 참조하세요.
|템플릿 보관|레이블 상태를 **사용 안 함**으로 설정합니다.
|범위 지정 템플릿 만들기|범위 지정 정책을 만들고 이 범위에서 보호를 적용하는 레이블을 만듭니다. <br /><br />자세한 내용은 [범위 지정 정책을 사용하여 특정 사용자용 Azure Information Protection 정책을 구성하는 방법](configure-policy-scope.md)을 참조하세요.
|템플릿 복사|Azure Portal에서는 템플릿을 복사할 수 없습니다. 두 레이블에서 동일한 보호 설정을 유지하려면 각 레이블에 대한 권한을 설정해야 합니다. <br /><br />자세한 내용은 [Rights Management 보호에 대한 레이블 구성](configure-policy-protection.md#to-configure-a-label-for-rights-management-protection)을 참조하세요.
|템플릿 삭제|템플릿을 삭제하면 액세스할 수 없는 데이터가 될 수 있으므로 Azure Portal에서는 이 작업을 지원하지 않습니다. 그러나 레이블을 삭제한 다음 [Remove-AadrmTemplate](/powershell/module/aadrm/remove-aadrmtemplate) PowerShell cmdlet을 사용하여 템플릿을 제거할 수 있습니다. <br /><br />자세한 내용은 [Azure Information Protection에 대한 레이블을 삭제하거나 순서를 변경하는 방법](configure-policy-delete-reorder.md)을 참조하세요.
|다중 언어 지원|**관리** 메뉴 선택에서 **언어(미리 보기)**를 선택하여 템플릿 이름과 설명을 포함하는 사용자 지정 가능한 필드를 내보냅니다. 문자열을 번역한 다음 이러한 문자열을 포털로 가져옵니다. <br /><br />자세한 내용은 [Azure Information Protection에서 다른 언어에 대한 레이블 및 템플릿을 구성하는 방법](configure-policy-languages.md)을 참조하세요.
|Rights Management 웹 보고서|[Get-AadrmUsageLog](/powershell/module/aadrm/Get-AadrmUsageLog) PowerShell cmdlet을 사용하여 Azure Rights Management 서비스에 대한 사용 현황 로그를 다운로드합니다. 그런 다음 이 데이터를 사용하여 사용자 지정 보고서를 만들 수 있습니다. <br /><br />자세한 내용은 [Azure Rights Management Service의 사용 현황 로깅 및 분석](log-analyze-usage.md)을 참조하세요.<br /><br />팁: 새로운 Azure Information Protection용 중앙 집중식 보고 솔루션에 대한 [Enterprise Mobility and Security 블로그(영문)](https://blogs.technet.microsoft.com/enterprisemobility/?product=azure-information-protection)의 공지 사항을 확인하세요. 
|Rights Management 서비스 활성화 및 비활성화|**관리** 메뉴 옵션에서 **RMS 설정** 또는 **보호 활성화**를 선택합니다. 이 옵션의 이름을 바꾸는 중입니다.<br /><br />자세한 내용은 [Azure 포털에서 Azure Rights Management 활성화하는 방법](activate-azure.md)을 참조하세요.

Azure Portal에서 템플릿을 편집하거나 레이블로 변환하기 전에 [Azure Portal의 템플릿 고려 사항](configure-policy-templates.md#considerations-for-templates-in-the-azure-portal)을 참조하세요.


## <a name="what-else-has-changed"></a>기타 변경 사항

새로운 Azure Portal 기능:

- 조직에 대해 자동으로 만들어지는 [기본 템플릿](configure-policy-templates.md#default-templates)을 편집할 수 있습니다.

- 템플릿을 레이블로 변환하여 템플릿과 레이블을 독립적으로 관리하는 대신 단일 개체를 관리할 수 있습니다. 지침은 [템플릿을 레이블로 변환](configure-policy-templates.md#to-convert-templates-to-labels)을 참조하세요.

보안 관리자 역할 지원: Azure 클래식 포털에 전역 관리자로 로그인하여 Azure Rights Management를 구성해야 했지만, Azure Portal에 전역 관리자 또는 보안 관리자 역할이 있는 계정으로 로그인하여 Azure Information Protection를 구성할 수 있습니다. 

템플릿을 만들고 관리하고 서비스를 활성화하거나 비활성화하는 PowerShell cmdlet은 변경 없이 계속 지원됩니다.


## <a name="see-also"></a>참고 항목
자세한 내용은 [Azure Information Protection의 템플릿 구성 및 관리](../deploy-use/configure-policy-templates.md)를 참조하세요.

[!INCLUDE[Commenting house rules](../includes/houserules.md)]