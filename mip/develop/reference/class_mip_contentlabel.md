---
title: 클래스 mip ContentLabel
description: 클래스 mip ContentLabel에 대한 참조
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: c105f620ed2cd3d6f1427f2543784ea66ce2c4d7
ms.sourcegitcommit: 1cf14852cd14ea91ac964fb03a901238455ffdff
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/28/2018
ms.locfileid: "47446025"
---
# <a name="class-mipcontentlabel"></a>클래스 mip::ContentLabel 
콘텐츠 조각, 일반적으로 문서에 적용되는 Microsoft Information Protection 레이블의 추상화입니다.
적용된 특정 레이블 인스턴스에 대한 속성도 포함합니다.
  
## <a name="summary"></a>요약
 멤버                        | 설명                                
--------------------------------|---------------------------------------------
 public const std::string& GetCreationTime() const  |  레이블을 만든 시간을 가져옵니다.
 public AssignmentMethod GetAssignmentMethod() const  |  레이블의 할당 메서드를 가져옵니다.
public const std::vector<std::pair<std::string, std::string>>& GetExtendedProperties() const  |  확장 속성을 가져옵니다.
 public bool IsProtectionAppliedFromLabel() const  |  레이블에 의해 보호가 적용되었는지 여부를 가져옵니다.
public std::shared_ptr<Label> GetLabel() const  |  콘텐츠에 적용된 실제 레이블 개체를 가져옵니다.
  
## <a name="members"></a>멤버
  
### <a name="getcreationtime"></a>GetCreationTime
레이블을 만든 시간을 가져옵니다.

  
**반환**: 만든 시간 GMT 문자열.
  
### <a name="getassignmentmethod"></a>GetAssignmentMethod
레이블의 할당 메서드를 가져옵니다.

  
**반환**: AssignmentMethod STANDARD | PRIVILEGED | AUTO. 
  
**참고 항목**: mip::AssignmentMethod
  
### <a name="getextendedproperties"></a>GetExtendedProperties
확장 속성을 가져옵니다.

  
**반환**: 확장 속성.
  
### <a name="isprotectionappliedfromlabel"></a>IsProtectionAppliedFromLabel
레이블에 의해 보호가 적용되었는지 여부를 가져옵니다.

  
**반환**: 템플릿 보호가 있고 이 레이블에 의해 보호된 경우 True, 그렇지 않으면 false.
  
### <a name="label"></a>Label
콘텐츠에 적용된 실제 레이블 개체를 가져옵니다.

  
**반환**: 콘텐츠에 적용된 레이블 개체. 
  
**참고 항목**: [mip::Label](class_mip_label.md)