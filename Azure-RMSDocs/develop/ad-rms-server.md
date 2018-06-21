---
title: AD RMS 서버 | Azure RMS
description: RMS(권한 관리 서비스) 서버 구성 요소는 Microsoft 인터넷 정보 서비스에서 실행되는 웹 서비스 집합에 의해 구현됩니다.
keywords: ''
author: lleonard-msft
ms.author: alleonar
manager: mbaldwin
ms.date: 02/23/2017
ms.topic: article
ms.prod: ''
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 17B05780-B0EF-4805-8304-52DCDEB3AADB
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
ms.openlocfilehash: bb611b01129e1c79421621485606adc30fedfeae
ms.sourcegitcommit: 93124ef58e471277c7793130f1a82af33dabcea9
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/11/2018
ms.locfileid: "27765072"
---
# <a name="server"></a>서버

이 항목에서는 Azure 및 Windows Server용 RMS 서버의 용도와 기능에 대해 설명합니다.

**Azure RMS** - Azure 권한 관리 서비스를 사용하는 방법에 대한 자세한 내용은 [서비스 응용 프로그램이 클라우드 기반 RMS를 사용할 수 있도록 설정](how-to-use-file-api-with-aadrm-cloud.md) 항목을 참조하세요.

> [!IMPORTANT] 
> Azure RMS를 통해 응용 프로그램을 개발하고 테스트하는 것이 좋습니다.

**Windows Server** - Windows Server 2008 이상의 RMS 온-프레미스 서버에서는 RMS 서비스를 역할로 추가하여 설치하고 구성할 수 있습니다. 이전 운영 체제에 서비스를 설치하려면 Microsoft 다운로드 센터의 [Microsoft Windows Rights Management Services 서비스 팩 2](http://www.microsoft.com/download/en/details.aspx?id=4909)에서 다운로드합니다.

설치된 여러 웹 서비스 중, Windows Server에서 RMS 서버의 응용 프로그램 개발에 중요한 웹 서비스는 다음과 같습니다.

| 서비스 | 설명 |
|---------|-------------|
| 관리 | RMS를 관리할 수 있도록 하는 관리 웹 사이트를 호스트합니다. 루트 인증 서버 및 라이선스 서버에서 서비스가 실행됩니다. Active Directory Rights Management Services 스크립팅 API를 사용하여 관리 스크립트를 작성할 수 있습니다.|
| 계정 인증 |RMS 인증서 계층 구조에서 컴퓨터를 식별하는 컴퓨터 인증서와 사용자를 특정 컴퓨터와 연결하는 권한 계정 인증서를 만듭니다. 자세한 내용은 Activating a Computer and Activating a User(컴퓨터 활성화 및 사용자 활성화) 항목을 참조하세요.<p><p>이 서비스는 루트 인증 서버에서 실행됩니다. |
|라이선스 | *최종 사용자 라이선스*를 발급합니다. 루트 인증 서버 및 라이선스 서버에서 서비스가 실행됩니다.|
|게시 중 | 최종 사용자 라이선스에 열거할 수 있는 정책을 정의하는 *발급 라이선스*를 만듭니다. 자세한 내용은 [Creating an Issuance License](https://msdn.microsoft.com/library/Aa362355)(발급 라이선스 만들기) 항목을 참조하세요.<p><p>루트 인증 서버 및 라이선스 서버에서 서비스가 실행됩니다.|
|사전 인증 | 서버가 사용자를 대신하여 *권한 계정 인증서*를 요청할 수 있게 합니다. 루트 인증 서버 및 라이선스 서버에서 서비스가 실행됩니다.|
|서비스 로케이터 | RMS 클라이언트에서 계정 인증, 라이선스, 게시 서비스를 검색할 수 있도록 Active Directory에 이러한 서비스의 URL을 제공합니다. 루트 인증 서버 및 라이선스 서버에서 서비스가 실행됩니다.|

## <a name="related-topics"></a>관련 항목 ##
* [개요](ad-rms-overview.md)
* [Microsoft Internet Information Services](http://www.iis.net/overview)(Microsoft 인터넷 정보 서비스)
* [서비스 응용 프로그램이 클라우드 기반 RMS를 사용할 수 있도록 설정](how-to-use-file-api-with-aadrm-cloud.md)
* [Microsoft Windows Rights Management Services 서비스 팩 2](http://www.microsoft.com/download/en/details.aspx?id=4909)
* [Active Directory Rights Management Services Scripting API](https://msdn.microsoft.com/library/Bb968797)(Active Directory Rights Management Services 스크립팅 API)
* [Activating a Computer](https://msdn.microsoft.com/library/Cc530377)(컴퓨터 정품 인증)
* [Activating a User](https://msdn.microsoft.com/library/Cc530378)(사용자 활성화)
* [Creating an Issuance License](https://msdn.microsoft.com/library/Aa362355)(발급 라이선스 만들기)

[!INCLUDE[Commenting house rules](../includes/houserules.md)]