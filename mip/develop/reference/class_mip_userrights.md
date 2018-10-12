---
title: 클래스 UserRights
description: 클래스 mip UserRights에 대한 참조
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: c1ef7aaba00bf595d80f07f318aa5808f3a56409
ms.sourcegitcommit: 1cf14852cd14ea91ac964fb03a901238455ffdff
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/28/2018
ms.locfileid: "47445124"
---
# <a name="class-mipuserrights"></a>클래스 mip::UserRights 
사용자 그룹 및 이들과 연결된 권한입니다.
  
## <a name="summary"></a>요약
 멤버                        | 설명                                
--------------------------------|---------------------------------------------
public UserRights(const std::vector<std::string>& users, const std::vector<std::string>& rights)  |  [UserRights](class_mip_userrights.md) 생성자입니다.
public const std::vector<std::string>& Users() const  |  권한 집합과 연결된 사용자를 가져옵니다.
public const std::vector<std::string>& Rights() const  |  사용자 그룹과 연결된 권한을 가져옵니다.
  
## <a name="members"></a>멤버
  
### <a name="userrights"></a>UserRights
[UserRights](class_mip_userrights.md) 생성자입니다.

매개 변수:  
* **users**: 동일한 권한을 공유하는 사용자 그룹 


* **rights**: 사용자 그룹에서 공유되는 권한


  
### <a name="users"></a>사용자
권한 집합과 연결된 사용자를 가져옵니다.

  
**반환**: 권한 집합과 연결된 사용자
  
### <a name="rights"></a>권한
사용자 그룹과 연결된 권한을 가져옵니다.

  
**반환**: 사용자 그룹과 연결된 권한