---
title: 클래스 mip PolicyEngine
description: 클래스 mip PolicyEngine에 대한 참조
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: 57dd325e9c00a3cb2a4056f7ef0b522efef5d0c4
ms.sourcegitcommit: 1cf14852cd14ea91ac964fb03a901238455ffdff
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/28/2018
ms.locfileid: "47446042"
---
# <a name="class-mippolicyengine"></a>클래스 mip::PolicyEngine 
이 클래스는 모든 엔진 함수에 대한 인터페이스를 제공합니다.
  
## <a name="summary"></a>요약
 멤버                        | 설명                                
--------------------------------|---------------------------------------------
 public const Settings& GetSettings() const  |  정책 엔진 [Settings](class_mip_policyengine_settings.md)를 가져옵니다.
public const std::vector<std::shared_ptr<Label>>& ListSensitivityLabels()  |  정책 엔진과 연결된 민감도 레이블을 나열합니다.
 public const std::string& GetMoreInfoUrl() const  |  정책/레이블에 대한 자세한 정보를 조회하기 위한 URL을 제공합니다.
 public bool IsLabelingRequired() const  |  정책이 문서에 레이블을 지정하도록 요구하는지 여부를 확인합니다.
public std::shared_ptr<Label> GetDefaultSensitivityLabel()  |  기본 민감도 레이블을 가져옵니다.
public std::shared_ptr<PolicyHandler> CreatePolicyHandler(const std::string& contentIdentifier)  |  파일의 실행 상태에 대해 정책 관련 함수를 실행할 정책 처리기를 만듭니다.
 public void SendApplicationAuditEvent(const std::string& level, const std::string& eventType, const std::string& eventData)  |  애플리케이션 특정 이벤트를 감사 파이프라인에 기록합니다.
  
## <a name="members"></a>멤버
  
### <a name="settings"></a>설정
정책 엔진 [Settings](class_mip_policyengine_settings.md)를 가져옵니다.

  
**반환**: 정책 엔진 설정. 
  
**참고 항목**: [mip::PolicyEngine::Settings](class_mip_policyengine_settings.md)
  
### <a name="label"></a>Label
정책 엔진과 연결된 민감도 레이블을 나열합니다.

  
**반환**: 민감도 레이블 목록.
  
### <a name="getmoreinfourl"></a>GetMoreInfoUrl
정책/레이블에 대한 자세한 정보를 조회하기 위한 URL을 제공합니다.

  
**반환**: 문자열 형식의 URL입니다.
  
### <a name="islabelingrequired"></a>IsLabelingRequired
정책이 문서에 레이블을 지정하도록 요구하는지 여부를 확인합니다.

  
**반환**: 레이블 지정이 필수이면 True, 그렇지 않으면 false.
  
### <a name="label"></a>Label
기본 민감도 레이블을 가져옵니다.

  
**반환**: 있는 경우 기본 민감도 레이블, 설정된 기본 레이블이 없는 경우 nullptr.
  
### <a name="policyhandler"></a>PolicyHandler
파일의 실행 상태에 대해 정책 관련 함수를 실행할 정책 처리기를 만듭니다.

매개 변수:  
* **contentIdentifier**: 사람이 읽을 수 있는 콘텐츠 식별자. 파일의 예: "C:\mip-sdk-for-cpp\files\audit.docx" [path] 메일의 예: "RE: Audit design:user1@contoso.com" [Subject:Sender]



  
**반환**: 정책 처리기
  
### <a name="sendapplicationauditevent"></a>SendApplicationAuditEvent
애플리케이션 특정 이벤트를 감사 파이프라인에 기록합니다.

매개 변수:  
* **description**: 정보/오류/경고 로그 수준 


* **eventType**: 이벤트 유형에 대한 설명 


* **eventData**: 이벤트와 연결된 데이터

