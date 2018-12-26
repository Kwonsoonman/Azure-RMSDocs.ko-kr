---
title: 클래스 mip ProtectionProfile
description: 클래스 mip ProtectionProfile에 대한 참조
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: a7dffb4a6b1490ef185eb9a5062f394f4509f00a
ms.sourcegitcommit: 1cf14852cd14ea91ac964fb03a901238455ffdff
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/28/2018
ms.locfileid: "47446688"
---
# <a name="class-mipprotectionprofile"></a>클래스 mip::ProtectionProfile 
[ProtectionProfile](class_mip_protectionprofile.md)은 보호 작업을 수행하기 위한 루트 클래스입니다.
보호 작업을 수행하기 전에 애플리케이션이 [ProtectionProfile](class_mip_protectionprofile.md)을 만들어야 합니다.
  
## <a name="summary"></a>요약
 멤버                        | 설명                                
--------------------------------|---------------------------------------------
 public const Settings& GetSettings() const  |  초기화하는 동안, 그리고 수명 내내 [ProtectionProfile](class_mip_protectionprofile.md)에서 사용되는 설정을 가져옵니다.
public void ListEnginesAsync(const std::shared_ptr<void>& context)  |  엔진 나열 작업을 시작합니다.
public std::vector<std::string> ListEngines()  |  엔진을 나열합니다.
public void AddEngineAsync(const ProtectionEngine::Settings& settings, const std::shared_ptr<void>& context)  |  프로필에 새 보호 엔진 추가를 시작합니다.
public std::shared_ptr<ProtectionEngine> AddEngine(const ProtectionEngine::Settings& settings)  |  프로필에 새 보호 엔진을 추가합니다.
public void DeleteEngineAsync(const std::string& engineId, const std::shared_ptr<void>& context)  |  지정된 ID를 사용하여 보호 엔진 삭제를 시작합니다. 지정된 엔진에 대한 모든 데이터가 삭제됩니다.
 public void DeleteEngine(const std::string& engineId)  |  지정된 ID를 사용하여 보호 엔진을 삭제합니다. 지정된 엔진에 대한 모든 데이터가 삭제됩니다.
  
## <a name="members"></a>멤버
  
### <a name="settings"></a>설정
초기화하는 동안, 그리고 수명 내내 [ProtectionProfile](class_mip_protectionprofile.md)에서 사용되는 설정을 가져옵니다.

  
**반환**: 초기화하는 동안, 그리고 수명 내내 [ProtectionProfile](class_mip_protectionprofile.md)에서 사용되는 [설정](class_mip_protectionprofile_settings.md)
  
### <a name="listenginesasync"></a>ListEnginesAsync
엔진 나열 작업을 시작합니다.

매개 변수:  
* **context**: 관찰자에 다시 불투명하게 전달될 클라이언트 컨텍스트


[ProtectionProfile::Observer](class_mip_protectionprofile_observer.md)는 성공 또는 실패 시 호출됩니다.
  
### <a name="listengines"></a>ListEngines
엔진을 나열합니다.

  
**반환**: 캐시된 엔진 ID
  
### <a name="addengineasync"></a>AddEngineAsync
프로필에 새 보호 엔진 추가를 시작합니다.

매개 변수:  
* **settings**: 엔진의 설정을 지정하는 [mip::ProtectionEngine::Settings](class_mip_protectionengine_settings.md) 개체 


* **context**: 관찰자에 다시 불투명하게 전달될 클라이언트 컨텍스트


[ProtectionProfile::Observer](class_mip_protectionprofile_observer.md)는 성공 또는 실패 시 호출됩니다.
  
### <a name="protectionengine"></a>ProtectionEngine
프로필에 새 보호 엔진을 추가합니다.

매개 변수:  
* **settings**: 엔진의 설정을 지정하는 [mip::ProtectionEngine::Settings](class_mip_protectionengine_settings.md) 개체



  
**반환**: 새로 만든 [ProtectionEngine](class_mip_protectionengine.md)
  
### <a name="deleteengineasync"></a>DeleteEngineAsync
지정된 ID를 사용하여 보호 엔진 삭제를 시작합니다. 지정된 엔진에 대한 모든 데이터가 삭제됩니다.

매개 변수:  
* **id**: 고유 엔진 ID입니다. 


* **context**: 관찰자에 다시 불투명하게 전달될 클라이언트 컨텍스트


[ProtectionProfile::Observer](class_mip_protectionprofile_observer.md)는 성공 또는 실패 시 호출됩니다.
  
### <a name="deleteengine"></a>DeleteEngine
지정된 ID를 사용하여 보호 엔진을 삭제합니다. 지정된 엔진에 대한 모든 데이터가 삭제됩니다.

매개 변수:  
* **id**: 고유 엔진 ID입니다.

