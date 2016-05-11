---
# required metadata

title: 개요 | Azure RMS
description: RMS(권한 관리 서비스)는 디지털 정보가 무단으로 사용되지 않도록 보호하는 정보 보호 기술입니다.
keywords:
author: bruceperlerms
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: a58894d5-3271-46d7-bb1c-fbd22eae8530

# optional metadata

#ROBOTS:
audience: developer
#ms.devlang:
ms.reviewer: shubhamp
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

﻿
# 개요

RMS(권한 관리 서비스)는 디지털 정보가 무단으로 사용되지 않도록 보호하는 정보 보호 기술입니다. 권한 사용 응용 프로그램을 통해 콘텐츠 소유자는 콘텐츠를 열거나 수정, 인쇄, 전달하거나 다른 작업을 수행할 수 있는 사람을 정의할 수 있습니다.

## 개요

AD RMS는 [서버](ad-rms-server.md) 및 [클라이언트](ad-rms-client.md) 구성 요소 둘 다로 이루어져 있습니다. 서버 구성 요소는 Windows Server 2008 R2와 같은 Windows Server에서 실행되거나 Azure의 RMS 웹 서비스를 통해 클라우드에서 실행되는 여러 웹 서비스를 포함합니다. 클라이언트 구성 요소는 클라이언트 또는 서버 운영 체제에서 실행할 수 있으며, 응용 프로그램이 콘텐츠를 암호화 및 암호 해독하고, 템플릿 및 해지 목록을 검색하고, 서버에서 라이선스 및 인증서를 획득하고, 기타 관련된 권한 관리 작업을 수행할 수 있도록 하는 기능을 포함합니다.

자세한 내용은 [응용 프로그램 종류](application-types.md)를 참조하세요.

권한 관리 서비스 SDK 2.1을 기반으로 빌드된 응용 프로그램을 적용할 수 있는 몇 가지 시나리오는 다음과 같습니다.

-   법률 회사가 중요한 메일 메시지를 인쇄하거나 전달하지 못하게 하려고 합니다.
-   컴퓨터 보조 디자인 및 제조 소프트웨어 개발자가 암호 사용을 요구하지 않고 도면 액세스 권한을 연구 부서 내의 소규모 사용자 그룹으로 제한하려고 합니다.
-   그래픽 디자인 웹 사이트의 소유자가 이미지의 저해상도 복사본에 대해서는 무료 보기를 허용하지만 고해상도 버전에 액세스할 때는 요금을 지불해야 하는 단일 라이선스를 사용하려고 합니다.
-   온라인 문서 라이브러리의 소유자가 사용자의 ID에 따라 문서를 보거나 인쇄 또는 편집할 수 있는 권한을 설정하려고 합니다.
-   회사에서 보기 및 편집 권한을 특정 사용자로 제한하는 내부 웹 사이트에 중요한 직원 정보를 게시하려고 합니다.

AD RMS 서버, AD RMS 클라이언트 및 해당 기능에 대한 자세한 내용은 [AD RMS에 대한 IT 전문가 설명서](https://TechNet.Microsoft.Com/en-us/library/cc771234.aspx)의 TechNet 콘텐츠를 참조하세요.

시작하려면 [시작](getting-started-with-ad-rms-2-0.md)을 참조하세요.

## 관련 항목

* [AD RMS 개념](application-types.md)
* [AD RMS와 AD RMS 2.1의 차이점](differences-between-ad-rms-and-ad-rms-2-0.md)
* [시작](getting-started-with-ad-rms-2-0.md)
* [AD RMS에 대한 IT 전문가 설명서](https://TechNet.Microsoft.Com/en-us/library/cc771234.aspx)
* [서버](ad-rms-server.md)
* [client](ad-rms-client.md)
 

 





<!--HONumber=Apr16_HO3-->

