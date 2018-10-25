---
title: 클래스 mip ExecutionState
description: 클래스 mip ExecutionState에 대한 참조
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: 976bca60f3f494a0fbf196e6512b00bdcdd63992
ms.sourcegitcommit: 1cf14852cd14ea91ac964fb03a901238455ffdff
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/28/2018
ms.locfileid: "47446314"
---
# <a name="class-mipexecutionstate"></a>클래스 mip::ExecutionState 
엔진을 실행하는 데 필요한 모든 상태에 대한 인터페이스입니다.
클라이언트는 필요한 상태를 얻기 위해 메서드만 호출해야 합니다. 또한 효율성을 위해 클라이언트는 해당 상태가 미리 계산되지 않고 동적으로 계산되도록 이 인터페이스를 구현할 수 있습니다.
  
## <a name="summary"></a>요약
 멤버                        | 설명                                
--------------------------------|---------------------------------------------
 public std::string GetNewLabelId() const  |  문서에 적용해야 하는 민감도 레이블 ID를 가져옵니다.
 public ActionSource GetNewLabelActionSource() const  |  새 레이블 작업의 원본을 가져옵니다.
 public std::string GetContentIdentifier() const  |  문서를 설명하는 콘텐츠 식별자를 가져옵니다. 파일의 예: [path] 메일의 예: [Subject:Sender].
 public ContentState GetContentState() const  |  응용 프로그램이 콘텐츠와 상호 작용하는 동안의 콘텐츠 상태를 가져옵니다.
public std::pair<bool, std::string> IsDowngradeJustified() const  |  구현은 기존 레이블을 다운그레이드할 근거가 제공되었는지 여부를 전달해야 합니다.
 public AssignmentMethod GetNewLabelAssignmentMethod() const  |  새 레이블의 할당 메서드를 가져옵니다.
public std::vector<std::pair<std::string, std::string>> GetNewLabelExtendedProperties() const  |  새 레이블의 확장 속성을 반환합니다.
public std::vector<std::pair<std::string, std::string>> GetContentMetadata(const std::vector<std::string>& names, const std::vector<std::string>& namePrefixes) const  |  콘텐츠에서 메타데이터 항목을 가져옵니다.
public std::shared_ptr<ProtectionDescriptor> GetProtectionDescriptor() const  |  보호 설명자를 가져옵니다.
 public ContentFormat GetContentFormat() const  |  콘텐츠 형식을 가져옵니다.
 public ActionType GetSupportedActions() const  |  지원되는 모든 동작 유형을 설명하는 마스킹된 열거형을 가져옵니다.
public virtual std::map<std::string, std::shared_ptr<ClassificationResult>> GetClassificationResults(const std::vector<std::string> &) const  |  분류 결과의 맵을 반환합니다.
  
## <a name="members"></a>멤버
  
### <a name="getnewlabelid"></a>GetNewLabelId
문서에 적용해야 하는 민감도 레이블 ID를 가져옵니다.

  
**반환**: 있는 경우 콘텐츠에 적용할 민감도 레이블 ID, 없는 경우 레이블을 제거하는 빈 값.
  
### <a name="getnewlabelactionsource"></a>GetNewLabelActionSource
새 레이블 작업의 원본을 가져옵니다.

  
**반환**: 작업 원본.
  
### <a name="getcontentidentifier"></a>GetContentIdentifier
문서를 설명하는 콘텐츠 식별자를 가져옵니다. 파일의 예: [path] 메일의 예: [Subject:Sender].

  
**반환**: 콘텐츠에 적용할 콘텐츠 식별자.
이 값은 감사에서 사람이 읽을 수 있는 콘텐츠 설명으로 사용됩니다.
  
### <a name="getcontentstate"></a>GetContentState
응용 프로그램이 콘텐츠와 상호 작용하는 동안의 콘텐츠 상태를 가져옵니다.

  
**반환**: 콘텐츠 데이터의 상태
  
### <a name="isdowngradejustified"></a>IsDowngradeJustified
구현은 기존 레이블을 다운그레이드할 근거가 제공되었는지 여부를 전달해야 합니다.

  
**반환**: 근거 메시지와 함께 다운그레이드 근거가 제공된 경우 true, 제공되지 않은 경우 false 
  
**참고 항목**: [mip::JustifyAction](class_mip_justifyaction.md)
  
### <a name="getnewlabelassignmentmethod"></a>GetNewLabelAssignmentMethod
새 레이블의 할당 메서드를 가져옵니다.

  
**반환**: 할당 메서드 STANDARD, PRIVILEGED, AUTO. 
  
**참고 항목**: mip::AssignmentMethod
  
### <a name="getnewlabelextendedproperties"></a>GetNewLabelExtendedProperties
새 레이블의 확장 속성을 반환합니다.

  
**반환**: 콘텐츠에 적용된 확장 속성.
  
### <a name="getcontentmetadata"></a>GetContentMetadata
콘텐츠에서 메타데이터 항목을 가져옵니다.

  
**반환**: 콘텐츠에 적용된 메타데이터. 각 메타데이터 항목은 이름/값 쌍입니다.
  
### <a name="protectiondescriptor"></a>ProtectionDescriptor
보호 설명자를 가져옵니다.

  
**반환**: 보호 설명자
  
### <a name="getcontentformat"></a>GetContentFormat
콘텐츠 형식을 가져옵니다.

  
**반환**: 기본값, EMAIL 
  
**참고 항목**: mip::ContentFormat
  
### <a name="actiontype"></a>ActionType
지원되는 모든 동작 유형을 설명하는 마스킹된 열거형을 가져옵니다.

  
**반환**: 지원되는 모든 동작 유형을 설명하는 마스킹된 열거형.
ActionType::Justify를 지원해야 합니다. 정책 및 레이블 변경에 근거가 필요한 경우 근거 작업이 항상 반환됩니다.
  
### <a name="classificationresult"></a>ClassificationResult
분류 결과의 맵을 반환합니다.

매개 변수:  
* **classificationId**: 분류 ID 목록 



  
**반환**: 분류 결과 목록