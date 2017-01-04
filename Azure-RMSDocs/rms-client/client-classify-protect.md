---
title: "Azure Information Protection을 사용하여 파일이나 전자 메일 분류 및 보호 | Azure Information Protection"
description: "문서와 전자 메일을 분류하고 보호하는 방법에 대한 지침을 제공합니다."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 12/07/2016
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 75268245-6f14-4218-b904-202f63fb3ce6
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: e6d4cc50259b9d9bb73a75c648f9e6915562accf
ms.openlocfilehash: e1d61fbe1d74a4a57d9a1fdf518aeb0242d0f7ad


---

# <a name="classify-and-protect-a-file-or-email-by-using-azure-information-protection"></a>Azure Information Protection을 사용하여 파일이나 전자 메일 분류 및 보호

>*적용 대상: Active Directory Rights Management 서비스, Azure Information Protection, Windows 10, Windows 8.1, Windows 8, Windows 7 SP1*

**[ 이 클라이언트 버전은 미리 보기 상태이며 변경될 수 있습니다. ]**

문서와 전자 메일을 분류 및 보호하는 가장 쉬운 방법은 Office 데스크톱 앱(**Word**, **Excel**, **PowerPoint**, **Outlook**) 내에서 해당 문서 및 전자 메일을 만들거나 편집하는 것입니다. 

그러나 **파일 탐색기**를 사용하여 파일을 분류하고 보호할 수도 있습니다. 파일 탐색기는 추가적인 파일 형식을 지원하며, 여러 파일을 한 번에 편리하게 분류 및 보호할 수 있습니다.

## <a name="using-office-apps-to-classify-and-protect-your-documents-and-emails"></a>Office 앱을 사용하여 문서와 전자 메일 분류 및 보호

Azure Information Protection 표시줄에서 자동으로 구성된 레이블 중 하나를 선택합니다. 예를 들면 다음과 같습니다.

![Azure Information Protection 표시줄 예제](../media/info-protect-bar-not-set-callout.png)


## <a name="using-file-explorer-to-classify-and-protect-files"></a>파일 탐색기를 사용하여 파일 분류 및 보호

파일 탐색기를 사용할 때는 파일 하나/여러 개 또는 폴더를 빠르게 분류하고 보호할 수 있습니다. 

폴더를 선택하면 해당 폴더의 모든 파일 및 하위 폴더가 설정된 분류 및 보호 옵션을 사용하도록 자동으로 선택됩니다. 그러나 해당 폴더 또는 하위 폴더에서 새로 만드는 파일의 경우 이러한 옵션으로 자동 구성되지 않습니다.

파일 탐색기를 사용하여 파일을 분류하고 보호할 때는 레이블이 제공되지 않는 경우도 있습니다. 선택한 파일이 분류를 지원하지 않으면 레이블이 제공되지 않습니다. 관리자가 보호를 적용하도록 레이블을 구성한 경우에만 이러한 파일에 대해 레이블을 선택할 수 있습니다. 또는 보호 설정을 직접 지정할 수 있습니다. 

파일 탐색기에서 지원되는 파일 형식의 목록은 이 페이지의 [분류 및 보호가 지원되는 파일 형식](#file-types-supported-for-classification-and-protection) 섹션을 참조하세요.


### <a name="to-classify-and-protect-a-file-by-using-file-explorer"></a>파일 탐색기를 사용하여 파일을 분류 및 보호하려면

1.  파일 탐색기에서 파일 하나/여러 개 또는 폴더를 선택합니다. 마우스 오른쪽 단추를 클릭하고 **분류 및 보호(미리 보기)**를 선택합니다. 

2. **분류 및 보호 - Azure Information Protection** 대화 상자에서 Office 응용 프로그램에서와 같이 레이블을 사용합니다. 그러면 관리자가 정의한 분류와 보호가 설정됩니다. 레이블이 제공되지 않아 선택할 수 없다면 선택한 파일은 분류를 지원하지 않는 것입니다. 그래도 해당 파일을 보호할 수는 있습니다.

3. 이러한 파일을 보호하려면 관리자가 선택한 레이블에 대해 정의한 보호 설정(**자동(선택한 분류 레이블 기준)**)을 선택하거나 설정을 직접 지정(**사용자 지정 권한으로 재정의**)합니다.
    
    재정의 옵션을 사용하는 경우 관리자가 선택한 레이블에 대해 정의했을 수 있는 보호 설정이 사용되지 않습니다. 대신 보호 설정을 직접 지정해야 합니다. 

4. 재정의 옵션을 선택한 경우 다음 항목을 지정합니다.

    - **권한 선택**: 선택한 하나 이상의 파일을 보호할 때 사용자에게 제공할 액세스 권한 수준을 선택합니다.
    
    - **사용자 선택**: 하나 이상의 파일에 대해 선택한 권한을 소유해야 하는 사용자를 지정합니다. 주소록을 사용하여 조직 내 사용자와 그룹을 검색한 다음 선택할 수 있습니다. 다른 조직 사용자의 경우에는 전체 전자 메일 주소를 지정해야 합니다. 개인 전자 메일 주소는 현재 지원되지 않으므로 업무용 전자 메일 주소를 사용해야 합니다.
        
    - **액세스 만료**: 특정 기간에만 제공해야 하는 파일에 한해 이 옵션을 선택합니다. 그러면 지정한 사용자가 지정된 날짜 이후로는 선택한 하나 이상의 파일을 열 수 없습니다. 원본 파일은 계속 열 수 있지만 현재 표준 시간대로 선택한 날짜의 자정이 지나면 지정된 사용자는 파일을 열 수 없습니다.

5. **적용**을 클릭한 다음 **닫기**를 클릭합니다.

이제 선택한 하나 이상의 파일이 선택한 옵션에 따라 분류 및 보호됩니다. 경우에 따라(보호를 추가하면 파일 이름 확장명이 바뀌는 경우) 파일 탐색기의 원본 파일이 Azure Information Protection 잠금 아이콘이 있는 새 파일로 대체됩니다. 예를 들면 다음과 같습니다.

![Azure Information Protection 잠금 아이콘이 있는 보호된 파일](../media/Pfile.png)

분류 및 보호 설정을 변경하려는 경우 또는 나중에 설정을 수정해야 하는 경우 새 설정을 사용하여 이 프로세스를 반복하면 됩니다.

지정한 분류 및 보호 설정은 파일을 전자 메일로 보내거나 다른 위치에 저장하더라도 계속 적용된 상태로 유지됩니다. 파일을 보호한 경우에는 사용자가 해당 파일을 사용하는 방식을 추적할 수 있으며 필요에 따라 파일 액세스 권한을 해지할 수 있습니다. 자세한 내용은 [Azure Information Protection 사용 시 보호된 문서 추적 및 액세스 권한 해지](client-track-revoke.md)를 참조하세요. 

#### <a name="file-types-supported-for-classification-and-protection"></a>분류 및 보호가 지원되는 파일 형식

다음 파일 형식의 경우 분류만 지원됩니다. 다른 파일 형식은 보호도 수행해야 분류가 지원됩니다.

- **Microsoft Visio**: .vsdx, .vsdm, .vssx, .vssm, .vsd, .vdw, .vst

- **Microsoft Project**: .mpp, .mpt

- **Microsoft Publisher**: .pub

- **Microsoft Office 97, Office 2010, Office 2003**: .xls, .xlt, .doc, .dot, .ppt, .pps, .pot

- **Microsoft XPS**: .xps .oxps

- **이미지**: .jpg, .jpe, .jpeg, .jif, .jfif, .jfi.png, .tif, .tiff

- **SolidWorks**: .sldprt, .slddrw, .sldasm

- **Autodesk Design Review 2013**: .dwfx

- **Adobe Photoshop**: .psd

- **디지털 네거티브**: .dng


[파일 API 구성](../develop/file-api-configuration.md)에 설명되어 있는 파일 형식의 경우에는 Rights Management 서비스를 사용하여 보호할 수 있습니다. 관리자가 구성한 레이블을 선택할 때 이 보호를 자동으로 적용할 수도 있고, [권한 수준](../deploy-use/configure-usage-rights.md#rights-included-in-permissions-levels)을 사용하여 보호 설정을 직접 지정할 수도 있습니다. 


## <a name="other-instructions"></a>기타 지침
사용 방법 지침은 Azure Information Protection 사용자 가이드의 다음 섹션을 참조하세요.

-   [원하는 옵션을 선택하](client-user-guide.md#what-do-you-want-to-do)세요.




<!--HONumber=Dec16_HO1-->


