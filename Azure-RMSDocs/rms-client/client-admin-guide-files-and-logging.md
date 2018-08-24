---
title: Azure Information Protection 클라이언트 파일 및 사용 현황 로깅
description: Windows용 Azure Information Protection 클라이언트의 클라이언트 파일 및 사용 현황 로깅에 대한 정보
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 08/06/2018
ms.topic: article
ms.service: information-protection
ms.assetid: 5a34ab85-773f-4782-ba09-c321cddf5bc0
ms.reviewer: eymanor
ms.suite: ems
ms.openlocfilehash: 2354ba5f084adb4139dc72dfd8f69d33bd6a9743
ms.sourcegitcommit: 7ba9850e5bb07b14741bb90ebbe98f1ebe057b10
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/23/2018
ms.locfileid: "42808333"
---
# <a name="admin-guide-azure-information-protection-client-files-and-client-usage-logging"></a>관리자 가이드: Azure Information Protection 클라이언트 파일 및 클라이언트 사용 현황 로깅

>*적용 대상: Active Directory Rights Management Services, [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), Windows 10, Windows 8.1, Windows 8, Windows 7 with SP1, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2*

Azure Information Protection 클라이언트를 설치한 후에 파일의 위치를 파악하고 클라이언트가 사용되는 방식을 모니터링해야 합니다.

## <a name="file-locations-for-the-azure-information-protection-client"></a>Azure Information Protection 클라이언트에 대한 파일 위치

클라이언트 파일:   

- 64비트 운영 체제: **\ProgramFiles (x86)\Microsoft Azure Information Protection**

- 32비트 운영 체제: **\Program Files\Microsoft Azure Information Protection**

클라이언트 로그 파일 및 현재 설치된 정책 파일:

- 64비트 및 32비트 운영 체제: **%localappdata%\Microsoft\MSIP**

## <a name="usage-logging-for-the-azure-information-protection-client"></a>Azure Information Protection 클라이언트에 대한 사용 현황 로깅

클라이언트는 사용자 활동을 로컬 Windows 이벤트 로그 **응용 프로그램 및 서비스 로그** > **Azure Information Protection**에 기록합니다. 이벤트에는 다음과 같은 정보가 포함됩니다.

- 클라이언트 버전, 정책 ID

- 로그인한 사용자의 IP 주소

- 파일 이름 및 위치

- 작업:

    - 레이블 설정: 정보 ID 101
    
    - 레이블 설정(하위 수준): 정보 ID 101
    
    - 레이블 설정(상위 수준): 정보 ID 101
    
    - 레이블 제거: 정보 ID 104
   
    - 권장 팁: 정보 105
    
    - 사용자 지정 보호 적용: 정보 ID 201
    
    - 사용자 지정 보호 제거: 정보 ID 202
    
    - 로그인(운영): 정보 ID 902
    
    - 정책 다운로드(운영): 정보 ID 901
    
- 작업 소스:
    
    - 수동 
    
    - 권장
    
    - 자동  
    
    - 시스템(로그인 및 다운로드 정책용)
    
    - Default
    
- 작업 전/후의 레이블 
    
- 작업 전/후의 보호
    
- 사용자 근거(해당하는 경우)

- 지정된 사용자, 그룹 또는 조직에 대한 [인코딩 이름별 사용 권한](../configure-usage-rights.md#usage-rights-and-descriptions)을 포함하는 사용자 지정 사용 권한(해당하는 경우)
    
보호 서비스의 사용 현황 로깅에 대한 자세한 내용은 [Azure Rights Management Service 사용 현황 로깅 및 분석](../log-analyze-usage.md)을 참조하세요.



## <a name="next-steps"></a>다음 단계
Azure Information Protection 클라이언트와 연결된 모든 로그 파일을 파악했으므로 다음에서 이 클라이언트를 지원하는 데 필요할 수 있는 추가 정보를 참조하세요.

- [사용자 지정](client-admin-guide-customizations.md)

- [문서 추적](client-admin-guide-document-tracking.md)

- [지원되는 파일 유형](client-admin-guide-file-types.md)

- [PowerShell 명령](client-admin-guide-powershell.md)

