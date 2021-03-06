---
title: Microsoft Information Protection에 대해 보호된 PDF reader
description: ''
keywords: ''
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 12/04/2018
ms.topic: article
ms.prod: azure
ms.service: information-protection
ms.assetid: aab59e02-930b-4a17-8442-2d5d081fe1a6
ms.reviewer: kartikka
ms.suite: ems
ms.openlocfilehash: d4421caa4ec6846456c12aa831644e957c5b4fd9
ms.sourcegitcommit: 8e7b135bf48ced7e53d91f45d62b7bbd0f37634e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/04/2018
ms.locfileid: "52861203"
---
# <a name="supported-pdf-readers-for-microsoft-information-protection"></a>Microsoft Information Protection에 대해 지원되는 PDF reader

다음 정보를 사용하여 분류 및 보호를 위해 레이블이 지정된 PDF 문서 및 이러한 문서를 보는 방법에 대해 자세히 알아봅니다.

Microsoft와 Adobe 간의 공동 작업을 통해 분류되고 필요에 따라 보호된 PDF 문서에 대해 더 간소화되고 일관된 환경을 제공합니다. 이 공동 작업에서는 [Azure Information Protection](../what-is-information-protection.md)과 같은 Microsoft Information Protection 솔루션을 사용하여 Adobe Acrobat 네이티브 통합을 지원합니다. 

이 네이티브 통합에는 다음과 같은 혜택이 있습니다.

- 중요한 정보를 포함하기 때문에 보호된 PDF 문서를 볼 수 있습니다.

- 문서에 적용된 조직의 레이블에 대한 분류 값을 볼 수 있습니다.

- PDF 암호화에 대해 ISO 표준을 지원합니다.
    
    [관리자가 이 기능을 사용 안 함으로 설정](client-admin-guide-customizations.md#dont-protect-pdf-files-by-using-the-iso-standard-for-pdf-encryption)하지 않은 이상, 이 보호된 PDF 파일 형식은 이제 최신 버전의 Azure Information Protection 클라이언트에서 기본적으로 사용하도록 설정됩니다.

자세한 정보는 [10월부터 Microsoft Information Protection으로 보호되는 PDF에 Adobe Acrobat Reader 사용](https://techcommunity.microsoft.com/t5/Azure-Information-Protection/Starting-October-use-Adobe-Acrobat-Reader-for-PDFs-protected-by/ba-p/262738) 블로그 게시물을 참조하세요.

## <a name="supported-pdf-readers"></a>지원되는 PDF reader

다음과 같은 PDF reader는 PDF 암호화에 대해 표준 ISO를 준수하는 보호된 PDF 파일을 열 수 있습니다.

|운영 체제|지원되는 reader 및 다운로드 링크|
|----------------|-----------------------------------|
|Windows 10 이전 버전<br />Windows 7 서비스 팩 1을 통해|Adobe Acrobat Reader(기본 설정):<br />-  [Adobe 일반 사용 약관 참고](https://www.adobe.com/legal/terms.html) <br />- [미리 보기 다운로드](https://ardownload2.adobe.com/pub/adobe/reader/win/AcrobatDC/misc/MIP_Preview/1900820120/Adobe_MIP_Preview_1900820120.zip) <br /><br /> Azure Information Protection 뷰어: [미리 보기](https://go.microsoft.com/fwlink/?linkid=838993)<br /><br />Foxit reader: [다운로드](https://www.foxitsoftware.com/pdf-reader/)|
|Android|Azure Information Protection 앱: [다운로드](https://go.microsoft.com/fwlink/?LinkId=325340)|
|iOS|Azure Information Protection 앱: [다운로드](https://go.microsoft.com/fwlink/?LinkId=325338)|

### <a name="support-for-previous-formats"></a>이전 서식 지원

다음 표에 안내된 PDF 리더는 .ppdf 파일 이름 확장명을 갖는 보호된 PDF 문서와 .pdf 파일 이름 확장명을 갖는 오래된 형식을 지원합니다.

현재 SharePoint Online 및 SharePoint 온-프레미스에서는 IRM 보호 라이브러리에서 PDF 문서에 대해 이전 서식을 사용합니다.


|운영 체제|지원되는 reader|
|----------------|-----------------------------------|
|Windows 10 이전 버전<br />Windows 7 서비스 팩 1을 통해|Azure Information Protection 뷰어<br /><br />Gaaiho 문서<br /><br />GigaTrust Desktop PDF Client for Adobe<br /><br />Foxit Reader<br /><br />Nitro PDF Reader<br /><br />RMS 공유 앱|
|Android|Azure Information Protection 앱<br /><br />RMS를 사용한 Foxit MobilePDF<br /><br />GigaTrust App for Android|
|iOS|Azure Information Protection 앱<br /><br />RMS를 사용한 Foxit MobilePDF<br /><br />TITUS Docs|
