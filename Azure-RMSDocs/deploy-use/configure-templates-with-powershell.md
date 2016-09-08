---
title: "사용자 지정 템플릿에 대한 PowerShell 참조 | Azure RMS"
description: "템플릿을 만들고 관리하기 위해 Azure 클래식 포털에서 수행할 수 있는 모든 작업은 PowerShell을 사용하여 명령줄에서도 수행할 수 있습니다. 또한 테넌트 간에 템플릿을 복사하거나 다국어 이름/설명 등 템플릿의 복잡한 속성을 대량으로 편집할 수 있도록 템플릿을 내보내고 가져올 수도 있습니다."
author: cabailey
manager: mbaldwin
ms.date: 08/24/2016
ms.topic: article
ms.prod: 
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 30ee2f77-ce16-4113-bcda-6089131849ec
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 024a29d7c7db2e4c0578a95c93e22f8e7a5b173e
ms.openlocfilehash: 4874e6061bb9b8781fc2ad02c80dba38084f4747


---



# 사용자 지정 템플릿에 대한 PowerShell 참조

>*적용 대상: Azure 권한 관리, Office 365*

템플릿을 만들고 관리하기 위해 Azure 클래식 포털에서 수행할 수 있는 모든 작업은 PowerShell을 사용하여 명령줄에서도 수행할 수 있습니다. 또한 테넌트 간에 템플릿을 복사하거나 다국어 이름/설명 등 템플릿의 복잡한 속성을 대량으로 편집할 수 있도록 템플릿을 내보내고 가져올 수도 있습니다.

또한 내보내기 및 가져오기를 사용하여 사용자 지정 템플릿을 백업하고 복원할 수도 있습니다. 가장 좋은 방법은 사용자 지정 템플릿을 정기적으로 백업하는 것입니다. 이렇게 하면 의도하지 않은 변경을 수행한 경우 이전 버전으로 쉽게 되돌릴 수 있습니다.

> [!IMPORTANT]
> Windows PowerShell을 사용하여 Azure RMS 권한 정책 템플릿을 만들고 관리하려면 [Azure RMS용 Windows PowerShell 모듈](http://go.microsoft.com/fwlink/?LinkId=257721)버전 2.0.0.0 이상이 필요합니다.
> 
> 이전에 이 PowerShell 모듈을 설치한 경우 PowerShell 창에서 다음 명령을 실행하여 버전 번호를 확인합니다. `(Get-Module aadrm -ListAvailable).Version`

설치 지침은 [Azure 권한 관리용 Windows PowerShell 설치](install-powershell.md)를 참조하세요.

템플릿 만들기 및 관리를 지원하는 cmdlet

-   [Add-AadrmTemplate](https://msdn.microsoft.com/library/azure/dn727075.aspx)

-   [Export-AadrmTemplate](https://msdn.microsoft.com/library/azure/dn727078.aspx)

-   [Get-AadrmTemplate](https://msdn.microsoft.com/library/azure/dn727079.aspx)

-   [Get-AadrmTemplateProperty](https://msdn.microsoft.com/library/azure/dn727081.aspx)

-   [Import-AadrmTemplate](https://msdn.microsoft.com/library/azure/dn727077.aspx)

-   [New-AadrmRightsDefinition](https://msdn.microsoft.com/library/azure/dn727080.aspx)

-   [Remove-AadrmTemplate](https://msdn.microsoft.com/library/azure/dn727082.aspx)

-   [Set-AadrmTemplateProperty](https://msdn.microsoft.com/library/azure/dn727076.aspx)



## 참고 항목
[Azure 권한 관리용 사용자 지정 템플릿 구성](configure-custom-templates.md)


<!--HONumber=Aug16_HO4-->


