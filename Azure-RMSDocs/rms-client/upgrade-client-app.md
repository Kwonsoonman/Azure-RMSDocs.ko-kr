---
title: "RMS 공유 응용 프로그램으로 수행해왔던 작업"
description: "RMS 공유 응용 프로그램에서 Azure Information Protection 클라이언트로 업그레이드한 사용자를 위한 지침입니다."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 02/08/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: d7bc2478-c22f-4e19-9992-012658362b25
ms.reviewer: eymanor
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: edc17f17d9668ed9c3dbaabab2b5000359fa410d
ms.openlocfilehash: 678f444d487f020c2806aef4479696f19b6263e6


---

# <a name="tasks-that-you-used-to-do-with-the-rms-sharing-application"></a>RMS 공유 응용 프로그램으로 수행해왔던 작업

최근에 Rights Management 공유 응용 프로그램("RMS 공유 앱"이라고도 함)에서 Azure Information Protection 클라이언트로 업그레이드했나요? 

다음 정보를 참조하여 빠르게 작업을 시작하는 방법을 배우세요.

|RMS 공유 앱|Azure Information Protection 클라이언트로 이 작업을 수행하는 방법
|-----------|--------------------|
|장치에서 파일 보호 <br /><br />"바로 보호"라고도 합니다.|Azure Information Protection 표시줄을 표시하는 Office 앱: 필요한 보호를 적용하는 레이블을 선택합니다.<br /><br />다른 파일의 경우 및 Azure Information Protection 클라이언트가 [보호 전용 모드](client-protection-only-mode.md)인 경우: 파일 탐색기 메뉴 옵션인 **분류 및 보호**를 사용하여 **분류 및 보호 - Azure Information Protection** 대화 상자를 엽니다. 그런 다음 필요한 보호를 적용하는 레이블을 선택하거나 자체 사용자 지정 권한을 지정합니다. <br /><br />자세한 내용은 [파일 또는 전자 메일 분류 및 보호](client-classify-protect.md)를 참조하세요.
|전자 메일을 통해 공유하는 파일 보호 <br /><br />"보호된 공유"라고도 합니다.|내부적으로 공유하는 경우: 필요한 보호를 제공하는 레이블을 문서 또는 전자 메일 메시지에 적용하거나 Outlook의 **전달 금지** 옵션을 선택합니다. <br /><br /> 외부에서 공유하는 경우: 파일 탐색기에서 파일 복사본을 사용하여 사용자 지정 권한으로 파일을 보호합니다. 그런 다음 전자 메일에 첨부 또는 SharePoint Online 문서에 초대 등의 표준 공유 메커니즘을 사용하여 파일을 공유합니다. 처음 사용하는 경우 https://aka.ms/rms-signup 링크를 지침으로 포함하는 것이 좋습니다. <br /><br />외부에서 공유하는 방법에 대한 자세한 내용은 사용자 가이드의 [조직 외부 사용자와 파일을 안전하게 공유](client-classify-protect.md#safely-share-a-file-with-people-outside-your-organization) 섹션을 참조하세요.
|보호된 파일에 대한 사용 권한 변경 <br /><br />"다시 보호"라고도 합니다.|Azure Information Protection 표시줄을 표시하는 Office 앱: 필요한 보호를 적용하는 레이블을 선택합니다.<br /><br />다른 파일의 경우 및 Azure Information Protection 클라이언트가 [보호 전용 모드](client-protection-only-mode.md)인 경우: 파일 탐색기 메뉴 옵션인 **분류 및 보호**를 사용하여 **분류 및 보호 - Azure Information Protection** 대화 상자를 엽니다. 그런 다음 필요한 보호를 적용하는 레이블을 선택하거나 자체 사용자 지정 권한을 지정합니다.<br /><br />자세한 내용은 [파일 또는 전자 메일 분류 및 보호](client-classify-protect.md)를 참조하세요.
|문서 추적 및 해지|Office 앱: 문서를 열고 **홈** 탭 > **보호** 그룹 > **보호** > **추적 및 해지**를 선택합니다.<br /><br />파일 탐색기: 파일 또는 폴더를 마우스 오른쪽 단추로 클릭하고 **분류 및 보호**를 선택합니다. 그런 후 **분류 및 보호 - Azure Information Protection** 대화 상자에서 **추적 및 해지**를 클릭합니다. <br /><br />자세한 내용은 [문서 추적 및 해지](client-track-revoke.md)를 참조하세요.
|보호된 파일 보기 및 사용|Azure Information Protection 뷰어에서는 보호된 파일을 열 수 있으므로 여기서 문서를 읽고, 해당 권한이 있는 경우에는 파일을 인쇄하고 저장할 수도 있습니다. 이 뷰어는 클라이언트와 함께 자동으로 설치되거나 별도로 설치할 수 있습니다.<br /><br />자세한 내용은 [보호된 파일 열기](client-view-use-files.md)를 참조하세요.
|파일에서 보호 제거|파일 탐색기 메뉴 옵션인 **분류 및 보호**를 사용하여 **분류 및 보호 - Azure Information Protection** 대화 상자를 엽니다. <br /><br />그런 후 단일 파일에 대해 **사용자 지정 권한으로 보호** 옵션을 선택 취소합니다. 여러 파일 또는 폴더에 대해서는 **사용자 지정 권한 제거**를 클릭합니다.<br /><br />자세한 내용은 [파일 및 전자 메일에서 레이블 및 보호 제거](client-remove-label-protection.md)를 참조하세요.|

## <a name="cant-find-the-option-youre-looking-for"></a>원하는 옵션을 찾을 수 없나요?

RMS 공유 응용 프로그램에서 선택하는 데 사용했던 특정 옵션을 찾고 있는 경우 다음 표를 확인하세요.

|RMS 공유 앱의 옵션|정보
|-----------|--------------------|
|**보호된 공유**|이 옵션은 Office 리본에서 더 이상 사용할 수 없습니다. Office 응용 프로그램 내에서 직접 공유하는 대신, 파일 탐색기의 오른쪽 클릭 옵션인 **분류 및 보호**를 사용하여 사용자 지정 권한으로 문서 사본을 보호하고 선택한 전자 메일 클라이언트 및 공유 위치를 사용하여 파일을 공유합니다. 처음 사용하는 경우 https://aka.ms/rms-signup 링크를 지침으로 포함하는 것이 좋습니다. <br /><br />외부에서 공유하는 방법에 대한 자세한 내용은 사용자 가이드의 [조직 외부 사용자와 파일을 안전하게 공유](#safely-share-a-file-with-people-outside-your-organization) 섹션을 참조하세요.
|**누군가가 이 문서를 열려고 하면 내게 메일을 보냅니다.**|문서 추적 사이트를 사용하여 기본 전자 메일 알림 설정 구성: 공유한 보호된 문서를 찾은 후 **설정** > **전자 메일 알림**을 클릭합니다.
|**이러한 문서에 대한 액세스를 즉시 취소할 수 있도록 허용합니다.**|이 옵션은 더 이상 사용할 수 없습니다. 오프라인 액세스를 허용하지 않는 템플릿을 구성합니다. 또한 [Set-AadrmMaxUseLicenseValidityTime](/powershell/aadrm/vlatest/set-aadrmmaxuselicensevaliditytime)을 실행하여 테넌트에 대한 라이선스 사용 유효 기간을 줄여야 하는지 여부를 고려합니다.







[!INCLUDE[Commenting house rules](../includes/houserules.md)]  



<!--HONumber=Feb17_HO2-->


