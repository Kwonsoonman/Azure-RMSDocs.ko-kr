---
# required metadata

title: Azure Rights Management 커넥터 모니터링 | Azure RMS
description:
keywords:
author: cabailey
manager: mbaldwin
ms.date: 06/09/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 8a1b3e54-f788-4f84-b9d7-5d5079e50b4e

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: esaggese
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Azure Rights Management 커넥터 모니터링

*적용 대상: Azure 권한 관리, Windows Server 2012, Windows Server 2012 R2*

RMS 커넥터를 설치하고 구성한 후에 다음과 같은 방법과 정보를 사용하여 커넥터와 조직의 Azure RMS 사용을 모니터링할 수 있습니다.

## 응용 프로그램 이벤트 로그 항목

RMS 커넥터에서는 응용 프로그램 이벤트 로그를 사용하여 **Microsoft RMS 커넥터**의 항목을 기록합니다. 

예를 들어, 커넥터 서비스가 시작된 것을 확인하는 ID 1000, 서버가 RMS 커넥터에 연결된 것을 나타내는 ID 1002, 권한이 있는 계정의 목록(각 계정 나열)이 커넥터에 다운로드된 것을 나타내는 ID 1004와 같은 정보 이벤트가 있습니다. 

커넥터에서 HTTPS를 사용하도록 구성하지 않은 경우에는 클라이언트에서 비보안(HTTP) 연결을 사용하고 있음을 나타내는 경고 ID 2002가 표시될 수 있습니다.

커넥터에서 Azure RMS에 연결하지 못하면 오류 3001이 표시될 가능성이 큽니다. 예를 들어, 이러한 표시는 RMS 커넥터를 실행하는 하나 이상의 서버에 DNS 문제가 있거나 인터넷에 액세스할 수 없는 경우에 나타날 수 있습니다. 

> [!TIP] RMS 커넥터 서버에서 Azure RMS에 연결할 수 없는 경우는 웹 프록시 구성에 원인이 있을 가능성이 큽니다.

모든 이벤트 로그 항목이 그렇듯이, 자세한 내용을 보려면 메시지를 상세히 검색합니다.

커넥터를 처음 배포할 때 이벤트 로그를 확인하는 것 외에도, 지속적으로 경고와 오류를 확인합니다. 예를 들어, 처음에는 커넥터가 정상적으로 작동했는데 다른 관리자가 종속 구성을 변경할 수도 있습니다. 예를 들어, 다른 관리자가 RMS 커넥터 서버에서 더 이상 인터넷에 연결할 수 없도록 웹 프록시 서버 구성을 변경하거나(오류 3001) 커넥터 사용이 승인된 것으로 지정한 그룹에서 컴퓨터 계정을 제거할 수도 있습니다(경고 2001).

## 성능 카운터

RMS 커넥터를 설치하면 **Microsoft Rights Management 커넥터** 성능 카운터가 자동으로 생성되며, 이 카운터는 커넥터를 통해 Azure RMS의 사용 성능을 모니터링하는 데 유용합니다. 

예를 들어, 문서나 메일을 보호하거나 보호된 문서 또는 메일을 열 때 정기적으로 지연이 발생하는 경우는 성능 카운터를 사용하여 지연의 원인이 커넥터의 처리 시간, Azure RMS의 처리 시간, 네트워크 지연 중 어느 것에 있는지 확인할 수 있습니다. 지연이 발생하는 위치를 쉽게 찾을 수 있도록 **커넥터 처리 시간**, **서비스 응답 시간**, **커넥터 응답 시간**의 평균 수를 포함하는 카운터를 확인합니다. 예: **라이선싱 성공 일괄 처리 요청 평균 커넥터 응답 시간**.

최근에 커넥터를 사용할 새 서버 계정을 추가한 경우에 **마지막 권한 부여 정책 업데이트 이후 시간** 카운터를 확인하여 커넥터를 업데이트한 후 목록을 다운로드했는지, 아니면 조금 더 기다려야 하는지(최대 15분) 확인할 수 있습니다.

## RMS 분석기

Rights Management 서비스 분석기 도구를 사용하면 커넥터의 상태를 모니터링하고 구성 문제를 식별하는 데 유용합니다.

이 도구를 아직 다운로드하지 않은 경우에는 [다운로드 센터](https://www.microsoft.com/en-us/download/details.aspx?id=46437)에서 다운로드한 다음 인터넷에 연결할 수 있으며 RMS 커넥터에 연결된 컴퓨터에 설치할 수 있습니다. 도구를 실행하고 **시작** 페이지에서 **Azure RMS 커넥터** 옵션을 선택합니다.

추가 정보 및 지침은 다운로드 페이지의 **세부 정보** 및 **설치 지침**을 참조하세요.

## 로깅

사용 현황 로깅은 메일과 문서가 보호되고 사용되는 경우를 식별할 때 유용합니다. 여기에 RMS 커넥터를 사용하는 경우, 로그의 사용자 ID 필드에는 RMS 커넥터를 설치할 때 자동으로 생성되는 서비스 주체 이름이 포함됩니다.

자세한 내용은 [Azure 권한 관리 사용 현황 로깅 및 분석](log-analyze-usage.md)을 참조하세요.

진단을 위해 더 자세한 로깅이 필요한 경우는 Windows Sysinternals에서 [Debugview](http://go.microsoft.com/fwlink/?LinkID=309277)를 사용하고 IIS의 기본 사이트에서 web.config 파일을 구성하여 RMS 커넥터에 대한 추적을 사용하도록 설정할 수 있습니다. 이렇게 하려면 다음을 수행합니다.

1. **%programfiles%\Microsoft Rights Management connector\Web Service**에서 web.config 파일을 찾습니다.

2. 다음 줄을 찾습니다.

        <trace enabled="false" requestLimit="10" pageOutput="false" traceMode="SortByTime" localOnly="true"/>

3. 이 줄을 다음으로 바꿉니다.

        <trace enabled="true" requestLimit="10" pageOutput="false" traceMode="SortByTime" localOnly="true"/>

4.  IIS를 중지했다가 시작하여 추적을 활성화합니다. 

5.  필요한 추적을 캡처한 경우에는 3단계에서 해당 줄을 되돌리고 IIS를 중지했다가 다시 시작합니다.



<!--HONumber=Jun16_HO2-->


