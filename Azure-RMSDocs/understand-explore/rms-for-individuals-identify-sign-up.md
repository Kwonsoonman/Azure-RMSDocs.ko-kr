---
title: "사용자가 개인용 RMS에 등록했는지 확인 - AIP"
description: "관리자는 사용자가 개인용 RMS를 등록했는지 여부를 어떻게 알 수 있을까요? 이 문서에서 설명하는 방법 중 하나를 사용하거나 여러 방법을 조합하여 사용할 수 있습니다."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 02/08/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: a36c3d99-a794-4f7a-aafb-64a950f1fcf9
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 10dfa64146587fe816df6a555e0a3b43c1290c45
ms.sourcegitcommit: 31e128cc1b917bf767987f0b2144b7f3b6288f2e
translationtype: HT
---
# <a name="how-to-find-out-if-your-users-have-signed-up-for-rms-for-individuals"></a>사용자가 개인용 RMS에 등록했는지 확인하는 방법

>*적용 대상: Azure Information Protection*

관리자는 사용자가 개인용 RMS를 등록했는지 여부를 어떻게 알 수 있을까요? 다음과 같은 방법을 사용할 수 있습니다(한 가지 또는 여러 가지를 함께 사용).

-   사용자에게 중요한 기밀 파일을 어떻게 보호하는지 물어봅니다(특히, 조직 외부의 다른 사용자와 공동 작업할 때).

-   조직에 대한 Azure 구독이 있는 경우 [Get-MsolAccountSku](https://msdn.microsoft.com/library/azure/dn194118.aspx) cmdlet을 사용하여 사용자에게 **RIGHTSMANAGEMENT_ADHOC**가 할당되었는지 확인합니다. 이 라이선스는 사용자가 셀프 서비스 등록 프로세스를 사용할 수 있도록 하는 활성 단위 풀과 함께 조직에 부여된 개인용 RMS 구독이 있으면 제공됩니다.

-   시스템 관리 솔루션(예: System Center Configuration Manager)을 사용하여, 설치된 소프트웨어와 사용 중인 소프트웨어의 목록을 만듭니다. 예를 들어 Azure Information Protection 클라이언트에서 사용되는 **MSIP.App.exe**와 Rights management 공유 응용 프로그램용 **ipviewer.exe**입니다. 이 클라이언트와 응용 프로그램을 무료로 다운로드한 후 설치하여 소프트웨어 인벤토리에 사용하는 다른 특성을 식별할 수 있습니다.

-   Azure Information Protection 클라이언트 또는 Rights Management 공유 응용 프로그램이 만든 파일 이름 확장명을 세심히 살펴봅니다. .pfile 및 .ppdf 파일 이름 확장명이 가장 명확한 예이지만, Rights Management Service에 의해 기본적으로 보호될 때 파일 이름 확장명이 변경되는 파일도 있습니다. 자세한 내용은 Azure Information Protection 클라이언트 관리자 가이드에서 [보호에 지원되는 파일 형식](../rms-client/client-admin-guide-file-types.md#file-types-supported-for-protection)을 참조하세요.

[!INCLUDE[Commenting house rules](../includes/houserules.md)]