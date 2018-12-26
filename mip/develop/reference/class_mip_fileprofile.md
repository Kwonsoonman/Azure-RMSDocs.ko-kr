---
title: 클래스 mip FileProfile
description: 클래스 mip FileProfile에 대한 참조
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: f317f1eff0266db1da211e164ec5e427ba7ce17d
ms.sourcegitcommit: 1cf14852cd14ea91ac964fb03a901238455ffdff
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/28/2018
ms.locfileid: "47445889"
---
# <a name="class-mipfileprofile"></a>클래스 mip::FileProfile 
[FileProfile](class_mip_fileprofile.md) 클래스는 Microsoft Information Protection 작업을 사용하기 위한 루트 클래스입니다.
일반적인 애플리케이션에는 프로필이 하나만 필요합니다.
  
## <a name="summary"></a>요약
 멤버                        | 설명                                
--------------------------------|---------------------------------------------
 public const Settings& GetSettings() const  |  프로필 설정을 반환합니다.
public void ListEnginesAsync(const std::shared_ptr<void>& context)  |  엔진 나열 작업을 시작합니다.
public void UnloadEngineAsync(const std::string& id, const std::shared_ptr<void>& context)  |  지정된 ID를 사용하여 파일 엔진 언로드를 시작합니다.
public void AddEngineAsync(const FileEngine::Settings& settings, const std::shared_ptr<void>& context)  |  프로필에 대한 새 파일 엔진 추가를 시작합니다.
public void DeleteEngineAsync(const std::string& id, const std::shared_ptr<void>& context)  |  지정된 ID를 사용하여 파일 엔진 삭제를 시작합니다. 지정된 프로필에 대한 모든 데이터가 삭제됩니다.
  
## <a name="members"></a>멤버
  
### <a name="settings"></a>설정
프로필 설정을 반환합니다.
  
### <a name="listenginesasync"></a>ListEnginesAsync
엔진 나열 작업을 시작합니다.
[FileProfile::Observer](class_mip_fileprofile_observer.md)는 성공 또는 실패 시 호출됩니다.
  
### <a name="unloadengineasync"></a>UnloadEngineAsync
지정된 ID를 사용하여 파일 엔진 언로드를 시작합니다.
[FileProfile::Observer](class_mip_fileprofile_observer.md)는 성공 또는 실패 시 호출됩니다.
  
### <a name="addengineasync"></a>AddEngineAsync
프로필에 대한 새 파일 엔진 추가를 시작합니다.
[FileProfile::Observer](class_mip_fileprofile_observer.md)는 성공 또는 실패 시 호출됩니다.
  
### <a name="deleteengineasync"></a>DeleteEngineAsync
지정된 ID를 사용하여 파일 엔진 삭제를 시작합니다. 지정된 프로필에 대한 모든 데이터가 삭제됩니다.
[FileProfile::Observer](class_mip_fileprofile_observer.md)는 성공 또는 실패 시 호출됩니다.