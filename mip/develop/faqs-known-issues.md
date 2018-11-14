---
title: FAQ 및 알려진 문제 - Microsoft Information Projection SDK.
description: MIP(Microsoft Information Protection) SDK FAQ 및 문제와 오류 해결 지침
author: BryanLa
ms.service: information-protection
ms.topic: troubleshooting
ms.date: 10/19/2018
ms.author: bryanla
ms.openlocfilehash: f213b31d9b0e41ea9c1e076055a90e9f62b31b3a
ms.sourcegitcommit: fa0be701b85b1fba5e75428714bb4525dd739a93
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/07/2018
ms.locfileid: "51223928"
---
# <a name="microsoft-information-protection-mip-sdk-faqs-and-issues"></a>MIP(Microsoft Information Protection) SDK FAQ 및 문제

이 문서는 FAQ(질문과 대답) 및 알려진 문제와 일반적인 오류에 대한 문제 해결 지침을 제공합니다.

## <a name="frequently-asked-questions"></a>질문과 대답 

### <a name="question-which-platforms-are-supported-by-the-mip-sdk"></a>질문: MIP SDK에서 지원하는 플랫폼은 무엇인가요?

MIP SDK는 다음 플랫폼에서 지원됩니다.

[!INCLUDE [MIP SDK platform support](../include/mip-sdk-platform-support.md)]

### <a name="question-how-does-the-sdk-handle-strings-and-what-string-type-should-i-be-using-in-my-code"></a>질문: SDK에서는 문자열을 어떻게 처리하며, 내 코드에서 어떤 문자열 유형을 사용해야 하나요?

SDK는 플랫폼 간에 사용하도록 설계되었고 문자열 처리에 [UTF-8(유니코드 변환 형식-8비트)](https://wikipedia.org/wiki/UTF-8)을 사용합니다. 구체적인 지침은 사용 중인 플랫폼에 따라 다릅니다.

| 플랫폼 | 지침 |
|-|-|
| Windows 원형 | C++ SDK 클라이언트의 경우 API 함수로/에서 문자열을 전달하는 데 C++ 표준 라이브러리 유형 [`std::string`](https://wikipedia.org/wiki/C%2B%2B_string_handling)이 사용됩니다. UTF-8로/에서 변환은 MIP SDK에서 내부적으로 관리합니다. API에서 `std::string`이 반환되면 UTF-8 인코딩을 예상해 해당 문자열 변환 시 이에 따라 관리해야 합니다. 경우에 따라 문자열이 `uint8_t` 벡터(예: 게시 라이선스(PL))의 일부로 반환되지만 불투명 blob으로 처리해야 합니다.<br><br>자세한 내용 및 예제는 다음을 참조하세요.<ul><li>[WideCharToMultiByte function](/windows/desktop/api/stringapiset/nf-stringapiset-widechartomultibyte)(UTF-8과 같은 멀티바이트로 와이드 문자 변환과 관련해 도움이 필요한 경우)<li>[SDK 다운로드](setup-configure-mip.md#configure-your-client-workstation)에 포함된 다음 샘플 파일:<ul><li>`file\samples\common\string_utils.cpp`의 샘플 문자열 유틸리티 함수(와이드 UTF-8 문자열로/에서 변환하는 경우)<li>`file\samples\file\main.cpp`에서 `wmain(int argc, wchar_t *argv[])` 구현(이전 문자열 변환 함수 사용)</li></ul></ul>|
| .NET | .NET SDK 클라이언트의 경우 모든 문자열은 기본 UTF-16 인코딩을 사용하고 특수 변환이 필요 없습니다. UTF-16으로/에서 변환은 MIP SDK가 내부적으로 관리합니다. |
| 기타 플랫폼 | MIP SDK에서 지원하는 기타 모든 플랫폼은 UTF-8에 대한 기본 지원을 제공합니다. |

## <a name="issues-and-errors-reference"></a>문제 및 오류 참조

### <a name="error-file-format-not-supported"></a>오류: "파일 형식이 지원되지 않음"  

| 오류 | 해결 방법 |
|-|-|
|*파일 형식이 지원되지 않음*| 이 예외는 디지털로 서명되었거나 암호로 보호된 PDF 파일을 보호하거나 레이블을 지정하려고 할 때 발생합니다. PDF 파일 보호 및 레이블 지정에 대한 자세한 내용은 [New support for PDF encryption with Microsoft Information Protection](https://techcommunity.microsoft.com/t5/Azure-Information-Protection/New-support-for-PDF-encryption-with-Microsoft-Information/ba-p/262757)(Microsoft Information Protection을 사용하여 PDF 암호화 새로 지원)을 참조하세요.|

### <a name="error-failed-to-parse-the-acquired-compliance-policy"></a>오류: "획득된 준수 정책을 구문 분석하지 못했습니다."  

MIP SDK를 다운로드했으며 샘플 응용 프로그램을 실행했습니다. 파일 샘플을 사용하여 모든 레이블을 나열하려고 했으나 다음과 같은 오류가 발생합니다.

| 오류 | 해결 방법 |
|-|-|
|*Something bad happened: Failed to parse the acquired Compliance Policy. Failed with: [class mip::CompliancePolicyParserException] Tag not found: policy, NodeType: 15, Name: No Name Found, Value: , Ancestors: <SyncFile><Content>, correlationId:[34668a40-blll-4ef8-b2af-00005aa674z9]*| 이 오류는 Azure Information Protection에서 통합 레이블 지정 환경으로 레이블을 마이그레이션하지 않았음을 나타냅니다. [Azure Information Protection 레이블을 Office 365 보안 및 준수 센터로 마이그레이션하는 방법](/azure/information-protection/configure-policy-migrate-labels)에 따라 레이블을 마이그레이션한 다음 Office 365 보안 및 준수 센터에서 레이블 정책을 생성합니다. 완료되면 샘플이 성공적으로 실행됩니다.|
