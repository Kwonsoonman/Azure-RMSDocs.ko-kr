---
title: "개발 환경 파일 | Azure RMS"
description: "이 항목에서는 개발 환경 파일과 컴퓨터의 상대 설치 위치를 보여 줍니다."
keywords: 
author: bruceperlerms
manager: mbaldwin
ms.date: 09/25/2016
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: B57AC6F3-733C-42A8-AF83-0E15FBF27C99
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: b4abffcbe6e49ea25f3cf493a1e68fcd6ea25b26
ms.openlocfilehash: fa85dde3f578f51efa57af78e211d3e712378b61


---

# 개발 환경 파일

이 항목에서는 개발 환경 파일과 컴퓨터의 상대 설치 위치를 보여 줍니다.

권한 관리 서비스 SDK 2.1에는 컴퓨터의 기본 위치나 지정한 위치(%MsipcSDKDir%)에 설치된 다음 파일이 포함되어 있습니다.

|파일|경로|설명|
|----|----|-----------|
|ReadMe.htm| \ | RMS 도움말 및 [릴리스 정보](release-notes-rtm.md)에 대한 링크를 포함합니다.|
|Isvtier5appsigningprivkey.dat|\bin|RMS 사용 응용 프로그램을 개발하는 동안 사용할 매니페스트를 생성하는 데 사용되는 개인 키를 포함합니다.|
|Isvtier5appsigningpubkey.dat|\bin|RMS 사용 응용 프로그램을 개발하는 동안 사용할 매니페스트를 생성하는 데 사용되는 공개 키를 포함합니다.|
|Isvtier5appsignsdk_client.xml|\bin|RMS 사용 응용 프로그램을 개발하는 동안 사용할 매니페스트를 생성하는 데 사용됩니다.|
|YourAppName.isv.mcf|\bin|RMS 사용 응용 프로그램을 개발하는 동안 매니페스트를 생성하는 데 사용할 수 있는 상용구 매니페스트 구성 파일입니다.|
|Ipcsecproc_isv.dll|\bin\x86|ISV 계층 구조에서 작동할 때 Active Directory Rights Management Services 클라이언트 2.1에서 x86 응용 프로그램에 대해 내부적으로 사용되는 DLL입니다.|
|Ipcsecproc_ssp_isv.dll|\bin\x86|ISV 계층 구조에서 작동할 때 AD RMS 2.1에서 x86 응용 프로그램에 대해 내부적으로 사용되는 DLL입니다.|
|Ipcsecproc_isv.dll|\bin\x64|ISV 계층 구조에서 작동할 때 AD RMS 클라이언트 2.1에서 x64 응용 프로그램에 대해 내부적으로 사용되는 DLL입니다.|
|Ipcsecproc_ssp_isv.dll|\bin\x64|ISV 계층 구조에서 작동할 때 AD RMS 클라이언트 2.1에서 x64 응용 프로그램에 대해 내부적으로 사용되는 DLL입니다.|
|Msipc.h|\inc|RMS SDK 2.1에 대한 주 포함 파일입니다.|
|Ipcprot.h|\inc|RMS SDK 2.1에서 내보낸 공용 인터페이스를 포함합니다.|
|Ipcbase.h|\inc|RMS SDK 2.1에서 내보낸 기본 형식 및 도우미 함수를 포함합니다.|
|Ipcerror.h|\inc|RMS SDK 2.1에서 내보낸 공개 오류 코드를 포함합니다.|
|Ipcfile.h|\inc|RMS SDK 2.1에서 내보낸 파일 API 인터페이스를 포함합니다.|
|Msipc.lib|\lib|RMS SDK 2.1을 사용하여 x86 응용 프로그램을 빌드할 때 연결할 라이브러리입니다.|
|Msipc_s.lib|\lib|x86 응용 프로그램의 [<strong>IpcInitialize</strong>](/information-protection/sdk/2.1/api/win/functions#msipc_ipcinitialize)에 대한 진입점을 제공합니다.|
|Msipc.lib|\lib\x64|RMS SDK 2.1을 사용하여 x64 응용 프로그램을 빌드할 때 연결할 라이브러리입니다.|
|Msipc_s.lib|\lib\x64|x64 응용 프로그램의 [<strong>IpcInitialize</strong>](/information-protection/sdk/2.1/api/win/functions#msipc_ipcinitialize)에 대한 진입점을 제공합니다.|
|Genmanifest.exe|\tools|RMS 사용 응용 프로그램을 개발하는 동안 사용할 매니페스트를 생성합니다.|
 

 

 



<!--HONumber=Sep16_HO5-->


