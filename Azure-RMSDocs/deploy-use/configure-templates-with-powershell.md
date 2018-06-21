---
title: 보호 템플릿의 PowerShell - Azure Information Protection
description: 보호 템플릿을 만들고 관리하기 위해 Azure Portal에서 수행할 수 있는 모든 작업은 PowerShell을 사용하여 명령줄에서도 수행할 수 있습니다. 또한 테넌트 간에 템플릿을 복사하거나 다국어 이름/설명 등 템플릿의 복잡한 속성을 대량으로 편집할 수 있도록 템플릿을 내보내고 가져올 수도 있습니다.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 02/23/2018
ms.topic: article
ms.prod: ''
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 30ee2f77-ce16-4113-bcda-6089131849ec
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 30dbfbe2cd9ef7d8acd89a9a76cd1108d7c03ab2
ms.sourcegitcommit: dbbfadc72f4005f81c9f28c515119bc3098201ce
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/28/2018
ms.locfileid: "30205723"
---
# <a name="powershell-reference-for-protection-templates"></a>보호 템플릿의 PowerShell 참조

>*적용 대상:[ Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [Office 365](http://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*

Azure Information Protection에 대한 보호 설정은 보호 템플릿에 저장됩니다. 보호 설정을 만들고 관리하기 위해 Azure Portal에서 수행할 수 있는 모든 작업은 PowerShell을 사용하여 명령줄에서도 수행할 수 있습니다. 

또한 보호 템플릿을 내보내고 가져올 수 있습니다. 이러한 두 작업을 통해 테넌트 간에 보호 템플릿을 복사하거나 다국어 이름 및 설명과 같은 복잡한 속성의 대량 편집을 수행할 수 있습니다.

내보내기 및 가져오기를 사용하여 보호 템플릿을 백업하고 복원할 수도 있습니다. 모범 사례로 정기적으로 템플릿을 백업합니다. 그런 다음, 의도하지 않게 보호 설정을 변경하는 경우 이전 버전으로 쉽게 되돌릴 수 있습니다.

설치 지침은 [AADRM PowerShell 모듈 설치](install-powershell.md)를 참조하세요.

보호 템플릿 만들기 및 관리를 지원하는 cmdlet:

- [Add-AadrmTemplate](/powershell/module/aadrm/add-aadrmtemplate)

- [Export-AadrmTemplate](/powershell/module/aadrm/export-aadrmtemplate)

- [Get-AadrmTemplate](/powershell/module/aadrm/get-aadrmtemplate)

- [Get-AadrmTemplateProperty](/powershell/module/aadrm/get-aadrmtemplateproperty)

- [Import-AadrmTemplate](/powershell/module/aadrm/import-aadrmtemplate)

- [New-AadrmRightsDefinition](/powershell/module/aadrm/new-aadrmrightsdefinition)

- [Remove-AadrmTemplate](/powershell/module/aadrm/remove-aadrmtemplate)

- [Set-AadrmTemplateProperty](/powershell/module/aadrm/set-aadrmtemplateproperty)



## <a name="see-also"></a>참고 항목
[Azure Information Protection의 템플릿 구성 및 관리](configure-policy-templates.md)

[!INCLUDE[Commenting house rules](../includes/houserules.md)]
