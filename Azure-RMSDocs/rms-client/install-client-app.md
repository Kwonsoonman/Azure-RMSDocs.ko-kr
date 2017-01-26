---
title: "Azure Information Protection 클라이언트 다운로드 및 설치 | Azure Information Protection"
description: "문서와 전자 메일을 분류하고 보호할 수 있도록 Windows용 Azure Information Protection 클라이언트를 설치하는 사용자용 지침을 제공합니다."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 01/13/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 2bf09690-9dba-43b7-9e0a-0110915d4081
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 22af60687ad030e686ba843ced6d450487353a0e
ms.openlocfilehash: 72266181c5334ed7e03b2022df61c4065f1c3ac7


---

# <a name="download-and-install-the-azure-information-protection-client"></a>Azure Information Protection 클라이언트 다운로드 및 설치

>*적용 대상: Active Directory Rights Management 서비스, Azure Information Protection, Windows 10, Windows 8.1, Windows 8, Windows 7 SP1*

**[ 이 클라이언트 버전은 미리 보기 상태이며 변경될 수 있습니다. ]**

관리자가 Azure Information Protection 클라이언트를 설치하지 않는 경우 직접 설치할 수 있습니다. PC의 로컬 관리자여야만 이 클라이언트를 설치할 수 있습니다. 

### <a name="office-2010-only"></a>Office 2010에만 해당

이 버전의 Office를 사용하는 경우 Azure Information Protection 클라이언트는 관리자 권한이 필요한 레지스트리 키를 설정해야 합니다. 

지침에 따라 클라이언트를 다운로드하여 설치하고 Office 2010에 대한 다음 섹션의 지침을 따르세요.

## <a name="to-download-and-install-the-azure-information-protection-client"></a>Azure Information Protection 클라이언트를 다운로드 및 설치하려면

1.  [Microsoft 다운로드 사이트](https://www.microsoft.com/en-us/download/details.aspx?id=53018)로 이동한 다음 Azure Information Protection 클라이언트의 **미리 보기** 버전을 다운로드합니다.

2. 다운로드된 실행 파일을 두 번 클릭합니다. 

3. **Azure Information Protection 클라이언트 설치** 페이지에서 다음을 수행합니다. 
    
    - 클라우드에 연결할 수 없지만 데모용으로 로컬 정책을 사용하여 Azure Information Protection의 클라이언트 쪽을 확인해 보려면 데모 정책을 설치하는 옵션을 선택합니다. 클라이언트에서 Azure Information Protection 서비스에 연결하면 이 데모 정책이 조직의 Azure Information Protection 정책으로 바뀝니다.
    
    - 사용 조건에 동의하면 **동의함**을 클릭합니다.

4. 계속할지 묻는 메시지가 나타나면 **예**를 클릭하고 설치가 완료될 때까지 기다립니다.

3. **닫기**를 클릭합니다. Azure Information Protection 클라이언트 사용을 시작하기 전에 다음을 수행합니다.

    - 컴퓨터에서 Office 2010를 실행하는 경우 컴퓨터를 다시 시작하고 마지막 단계에서 다음 섹션으로 이동합니다.
    
    - 기타 버전의 Office에서는 모든 Office 응용 프로그램 및 파일 탐색기의 모든 인스턴스를 다시 시작합니다. 이제 설치가 완료되었으며 클라이언트를 사용하여 문서와 메일에 레이블을 지정하고 보호할 수 있습니다.

> [!NOTE]
> Windows 7 SP1이 설치되어 있는 경우 Azure Information Protection 클라이언트를 사용하려면 특정 업데이트([KB 2533623](https://support.microsoft.com/en-us/kb/2533623))가 필요합니다. 사용 중인 PC에 이 업데이트가 필요한데 설치되어 있지 않은 경우 클라이언트를 사용하려고 할 때 Azure Information Protection 클라이언트의 모든 기능을 사용하려면 이 업데이트를 설치해야 한다는 메시지가 표시됩니다.

### <a name="installing-the-azure-information-protection-client-with-office-2010"></a>Office 2010과 함께 Azure Information Protection 클라이언트 설치

앞의 지침에 따라 Azure Information Protection 클라이언트를 설치한 후 다음을 수행합니다.

1. Microsoft Word를 엽니다. Azure Information Protection 클라이언트 설치 후 Office 2010 응용 프로그램을 처음으로 실행하는 경우 **Microsoft Azure Information Protection** 대화 상자가 표시됩니다. 이 대화 상자에는 로그인 프로세스를 완료하려면 관리자 자격 증명이 필요하다고 나옵니다.

2. **Microsoft Azure Information Protection** 대화 상자에서 **확인**을 클릭합니다.

2. **사용자 액세스 제어** 대화 상자가 표시되면 Azure Information Protection 클라이언트가 레지스트리를 업데이트할 수 있도록 **예**를 클릭합니다.

이제 설치가 완료되었으며 Azure Information Protection을 사용하여 문서와 메일에 레이블을 지정하고 보호할 수 있습니다.

## <a name="other-instructions"></a>기타 지침
사용 방법 지침은 Azure Information Protection 사용자 가이드의 다음 섹션을 참조하세요.

-   [원하는 옵션을 선택하](client-user-guide.md#what-do-you-want-to-do)세요.

## <a name="additional-information-for-administrators"></a>관리자용 추가 정보
[Azure Information Protection 클라이언트 설치](info-protect-client.md)

[!INCLUDE[Commenting house rules](../includes/houserules.md)]



<!--HONumber=Jan17_HO4-->


