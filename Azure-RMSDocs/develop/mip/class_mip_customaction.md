# <a name="class-mipcustomaction"></a>클래스 mip::CustomAction 
[CustomAction](class_mip_customaction.md)은 동작의 모든 하위 속성을 속성 모음으로 캡처하는 일반 동작 클래스입니다. 호출자는 동작의 의미를 이해해야 합니다.
  
## <a name="summary"></a>요약
 멤버                        | 설명                                
--------------------------------|---------------------------------------------
public const std::vector<std::pair<std::string, std::string>>& GetProperties() const  |  속성 키 값 쌍 목록을 가져옵니다.
 public ActionType GetType() const  |  [동작](class_mip_action.md) 유형을 가져옵니다.
  
## <a name="members"></a>멤버
  
### <a name="getproperties"></a>GetProperties
속성 키 값 쌍 목록을 가져옵니다.

  
**반환**: 키 값 쌍 목록.
  
### <a name="actiontype"></a>ActionType
[동작](class_mip_action.md) 유형을 가져옵니다.

  
**반환**: ActionType. 이 기본 클래스가 캐스트될 수 있는 파생 동작의 유형입니다.