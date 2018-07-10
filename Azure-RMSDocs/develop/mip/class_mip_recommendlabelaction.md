# <a name="class-miprecommendlabelaction"></a>class mip::RecommendLabelAction 
레이블 권장 동작은 사용자에게 레이블을 제안하기 위한 것입니다. 사용자가 권장 레이블을 무시한 후 이 호출을 표시하지 않는 것은 실행 상태에서 지원되는 작업을 통해 수행되어야 합니다.
  
## <a name="summary"></a>요약
 멤버                        | 설명                                
--------------------------------|---------------------------------------------
 public const std::string& GetLabelId() const  |  제안된 레이블 ID를 가져옵니다.
 public ActionType GetType() const  |  [동작](class_mip_action.md) 유형을 가져옵니다.
  
## <a name="members"></a>멤버
  
### <a name="getlabelid"></a>GetLabelId
제안된 레이블 ID를 가져옵니다.

  
**반환**: 레이블 ID
  
### <a name="actiontype"></a>ActionType
[동작](class_mip_action.md) 유형을 가져옵니다.

  
**반환**: ActionType. 이 기본 클래스가 캐스트될 수 있는 파생 동작의 유형입니다.