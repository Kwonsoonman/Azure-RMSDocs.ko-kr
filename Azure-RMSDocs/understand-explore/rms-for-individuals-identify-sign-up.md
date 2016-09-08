---
title: "사용자가 개인용 RMS에 등록했는지 확인하는 방법 | Azure RMS"
description: "관리자는 사용자가 개인용 RMS를 등록했는지 여부를 어떻게 알 수 있을까요? 다음과 같은 방법을 사용할 수 있습니다(한 가지 또는 여러 가지를 함께 사용)."
author: cabailey
manager: mbaldwin
ms.date: 08/24/2016
ms.topic: article
ms.prod: 
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: a36c3d99-a794-4f7a-aafb-64a950f1fcf9
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 024a29d7c7db2e4c0578a95c93e22f8e7a5b173e
ms.openlocfilehash: dc8c0a69078ffa3be87a5fb02bf86d9afe2dc27e


---


# 사용자가 개인용 RMS에 등록했는지 확인하는 방법

>*적용 대상: Azure 권한 관리*

관리자는 사용자가 개인용 RMS를 등록했는지 여부를 어떻게 알 수 있을까요? 다음과 같은 방법을 사용할 수 있습니다(한 가지 또는 여러 가지를 함께 사용).

-   사용자에게 중요한 기밀 파일을 어떻게 보호하는지 물어봅니다(특히, 조직 외부의 다른 사용자와 공동 작업할 때).

-   조직에 대한 Azure 구독이 있는 경우 [Get-MsolAccountSku](https://msdn.microsoft.com/library/azure/dn194118.aspx) cmdlet을 사용하여 **RIGHTSMANAGEMENT_ADHOC**이 구독 중 하나로 반환되는지 확인합니다. 구독 중 하나로 반환되는 경우 사용자가 셀프 서비스 등록 프로세스를 사용할 수 있도록 하는 활성 단위 풀과 함께 조직에 부여된 개인용 RMS 구독입니다.

-   시스템 관리 솔루션(예: System Center Configuration Manager)을 사용하여, 설치된 소프트웨어와 사용 중인 소프트웨어의 목록을 만듭니다. Rights Management 공유 응용 프로그램은 **ipviewer.exe** 프로그램을 통해 실행되며, 무료로 [응용 프로그램을 다운로드하고 설치](http://go.microsoft.com/fwlink/?LinkId=303970) 하여 소프트웨어 인벤토리에 사용할 이 응용 프로그램에 대한 다른 특성을 확인할 수 있습니다.

-   Rights Management 공유 응용 프로그램이 만든 파일 이름 확장명을 세심히 살펴봅니다. .pfile 및 .ppdf 파일 이름 확장명이 가장 명확한 예이지만, Rights Management에 의해 기본적으로 보호될 때 파일 이름 확장명이 변경되는 파일도 있습니다. 자세한 내용은 [Rights Management 공유 응용 프로그램 관리자 가이드](http://technet.microsoft.com/library/dn339003.aspx)에서 [지원되는 파일 형식 및 파일 이름 확장명](../rms-client/sharing-app-admin-guide-technical.md#supported-file-types-and-file-name-extensions) 섹션을 참조하세요.




<!--HONumber=Aug16_HO4-->


