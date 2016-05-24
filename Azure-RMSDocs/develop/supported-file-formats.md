---
# required metadata

title: 지원되는 파일 형식 | Azure RMS
description: 현재 버전의 파일 API는 MS Office 파일, PDF 및 다른 모든 파일 형식의 PFile 보호에 대한 기본 보호를 지원합니다.
keywords:
author: bruceperlerms
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: EC831494-7F2C-4C70-9063-B02CDDEA14EE
# optional metadata

#ROBOTS:
audience: developer
#ms.devlang:
ms.reviewer: shubhamp
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# 지원되는 파일 형식

파일 API는 네이티브 형식과 Pfile 형식을 지원합니다.

## 지원되는 파일 형식

현재 버전의 파일 API는 Microsoft Office 파일, PDF(Portable Document Files) 및 다른 모든 파일 형식의 PFile 보호에 대한 기본 보호를 지원합니다. 선택적으로 PDF 파일에 PFile 보호를 적용할 수 있습니다.

-   **기본 보호**. 기본 보호에서는 파일이 MIME 형식(파일 이름 확장명)을 기반으로 하는 AD RMS 파일 형식으로 암호화됩니다. 파일 API를 사용하여 기본적으로 보호되는 파일은 기본 보호를 사용하는 AD RMS 사용 응용 프로그램(예: Office 2013, Office 2010 및 FoxIt PDF Reader)에 필요한 형식과 일치합니다. 기본 보호는 Office 파일, PDF 파일 및 다른 일부 파일 형식에서만 지원됩니다. 기본 보호가 지원되는 파일 형식에 대한 자세한 내용은 [파일 API 구성](file-api-configuration.md)을 참조하세요.
-   **PFile 보호**. PFile 보호에서 파일은 AD RMS PFile(보호된 파일) 형식을 사용하여 암호화됩니다. 파일은 확장명이 .pfile인 파일로 암호화됩니다. PFile 보호는 Office 파일을 제외한 모든 파일 형식에 대해 지원됩니다.

관리자는 레지스트리 키를 설정하여 파일 이름 확장명에 따라 파일을 보호할지 여부와 방법을 구성할 수 있습니다. 파일 API를 사용하는 경우 파일 보호를 구성하는 방법에 대한 자세한 내용은 [파일 API 구성](file-api-configuration.md)을 참조하세요.

## 관련 항목

* [개발자 노트](developer-notes.md)
* [파일 API 구성](file-api-configuration.md)
 

 





<!--HONumber=Apr16_HO4-->


