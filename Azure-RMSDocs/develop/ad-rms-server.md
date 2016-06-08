---
# required metadata

title: AD RMS 서버 | Azure RMS
description: RMS(권한 관리 서비스) 서버 구성 요소는 Microsoft 인터넷 정보 서비스에서 실행되는 웹 서비스 집합에 의해 구현됩니다.
keywords:
author: bruceperlerms
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 17B05780-B0EF-4805-8304-52DCDEB3AADB
# optional metadata

#ROBOTS:
audience: developer
#ms.devlang:
ms.reviewer: shubhamp
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---
** 이 SDK 콘텐츠는 현재 버전이 아닙니다. 잠시 MSDN에서 [현재 버전](https://msdn.microsoft.com/library/windows/desktop/hh535290(v=vs.85).aspx)의 설명서를 확인해 주세요. **

# AD RMS 서버
이 항목에서는 RMS 서버의 용도와 기능에 대해 설명합니다.

RMS(권한 관리 서비스) 서버 구성 요소는 [Microsoft IIS(인터넷 정보 서비스)](http://www.iis.net/overview)에서 실행되는 웹 서비스 집합에 의해 구현됩니다. Azure의 RMS를 통해 클라우드 기반 구현을 사용할 수도 있습니다. Azure 권한 관리 서비스를 사용하는 방법에 대한 자세한 내용은 [서비스 응용 프로그램이 클라우드 기반 RMS를 사용할 수 있도록 설정](how-to-use-file-api-with-aadrm-cloud.md)을 참조하세요.

Windows Server 2008 이상의 온-프레미스 서버에서는 RMS 서비스를 역할로 추가하여 설치 및 구성할 수 있습니다. 이전 운영 체제에 서비스를 설치하려면 Microsoft 다운로드 센터의 [Microsoft Windows Rights Management Services 서비스 팩 2](http://www.microsoft.com/download/en/details.aspx?id=4909)에서 다운로드합니다.

설치된 여러 웹 서비스 중 응용 프로그램 개발에 중요한 웹 서비스는 다음과 같습니다.

**관리** - RMS를 관리할 수 있도록 하는 관리 웹 사이트를 호스트합니다. 루트 인증 서버 및 라이선스 서버에서 서비스가 실행됩니다. [Active Directory Rights Management Services 스크립팅 API](https://msdn.microsoft.com/library/Bb968797)를 사용하여 관리 스크립트를 작성할 수 있습니다.

**계정 인증** - RMS 인증서 계층 구조에서 컴퓨터를 식별하는 컴퓨터 인증서와 사용자를 특정 컴퓨터와 연결하는 권한 계정 인증서를 만듭니다. 자세한 내용은 [사용자 활성화](https://msdn.microsoft.com/library/Cc530378)를 참조하세요.

이 서비스는 루트 인증 서버에서 실행됩니다.

**라이선스** - 최종 사용자가 보호된 콘텐츠를 사용할 수 있도록 하는 최종 사용자 라이선스를 발급합니다. 루트 인증 서버 및 라이선스 서버에서 서비스가 실행됩니다.

**게시** - [발급 라이선스](https://msdn.microsoft.com/library/Aa362355)를 만듭니다. 루트 인증 서버 및 라이선스 서버에서 서비스가 실행됩니다.

**사전 인증** - 서버가 사용자를 대신하여 RAC(권한 계정 인증서)를 요청할 수 있게 합니다. RAC는 RMS 정품 인증을 통해 얻은 컴퓨터 인증서를 사용하여 사용자 계정을 특정 컴퓨터나 컴퓨터 그룹에 바인딩하며 소비자가 보호된 콘텐츠를 사용할 수 있도록 합니다. 루트 인증 서버 및 라이선스 서버에서 서비스가 실행됩니다.

**서비스 로케이터** - RMS 클라이언트에서 계정 인증, 라이선스, 게시 서비스를 검색할 수 있도록 Active Directory에 이러한 서비스의 URL을 제공합니다. 루트 인증 서버 및 라이선스 서버에서 서비스가 실행됩니다.

 

## 관련 항목 ##
* [개요](ad-rms-overview.md)
* [Microsoft 인터넷 정보 서비스](http://www.iis.net/overview)
* [서비스 응용 프로그램이 클라우드 기반 RMS를 사용할 수 있도록 설정](how-to-use-file-api-with-aadrm-cloud.md)
* [Microsoft Windows Rights Management Services 서비스 팩 2](http://www.microsoft.com/download/en/details.aspx?id=4909)
* [Active Directory Rights Management Services 스크립팅 API](https://msdn.microsoft.com/library/Bb968797)
* [컴퓨터 정품 인증](https://msdn.microsoft.com/library/Cc530377)
* [사용자 활성화](https://msdn.microsoft.com/library/Cc530378)
* [발급 라이선스 만들기](https://msdn.microsoft.com/library/Aa362355)

 

 


<!--HONumber=Jun16_HO1-->


