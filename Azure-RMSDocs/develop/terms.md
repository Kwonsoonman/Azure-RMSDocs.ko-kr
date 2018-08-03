---
title: AIP 개발자 용어 | Microsoft Docs
description: 권한 관리 서비스와 관련된 개발자 용어 정의 컬렉션입니다.
keywords: ''
author: lleonard-msft
ms.author: alleonar
manager: mbaldwin
ms.date: 01/23/2017
ms.topic: article
ms.prod: ''
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: adb1f868-0da7-431b-83d1-86f41c2da4ae
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
ms.openlocfilehash: a0b63f08041c7cf57dd079136bd55a95b1659fd3
ms.sourcegitcommit: 44ff610dec678604c449d42cc0b0863ca8224009
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/31/2018
ms.locfileid: "39375371"
---
# <a name="terms"></a>용어

Azure Information Protection과 관련된 개발자 용어 정의 컬렉션입니다.

**사용되지 않는 알고리즘**  
이전 콘텐츠 보호 체계를 구현하는 모달 설정으로, 특히 ECB(Electronic Codebook Cipher Mode)를 가리킵니다. 이 SDK에서는 이 설정을 통해 [AD 권한 관리 서비스 SDK](https://msdn.microsoft.com/library/windows/desktop/cc530379.aspx)에서 사용하는 MSDRM 라이브러리와 호환되는 라이선스를 생성할 수 있습니다.

이 설정으로 인해 응용 프로그램이 콘텐츠 보호에 대한 고객의 표준에 맞지 않는 방식으로 콘텐츠를 보호할 수도 있습니다.

이 설정은 응용 프로그램이 Microsoft Rights Management SDK 3.0 이상에 추가된 암호화 향상 기능을 사용할 수 없게 합니다.

**Microsoft 보호된 파일 형식**

PFile 형식이라고도 하며, AD RMS의 기본 파일 형식이고 RMS 사용 응용 프로그램 전체에서 표준으로 사용됩니다.

PFile 형식은 Microsoft Rights Management SDK 4.2가 설계된 방식에 포함되므로 응용 프로그램 개발자에게 투명합니다.

