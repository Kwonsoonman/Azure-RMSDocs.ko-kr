# <a name="class-mipapplylabelaction"></a>class mip::ApplyLabelAction 
레이블 적용 동작에 따라 호출 응용 프로그램은 특정 레이블을 적용해야 합니다.
  
## <a name="summary"></a>요약
 멤버                        | 설명                                
--------------------------------|---------------------------------------------
 public const std::string& GetLabelId() const  |  필요한 레이블 ID를 가져옵니다.
 public ActionType GetType() const  |  [동작](class_mip_action.md) 유형을 가져옵니다.
  
## <a name="members"></a>멤버
  
### <a name="getlabelid"></a>GetLabelId
필요한 레이블 ID를 가져옵니다.

  
**반환**: 레이블 ID
  
### <a name="actiontype"></a>ActionType
[동작](class_mip_action.md) 유형을 가져옵니다.

  
**반환**: ActionType. 이 기본 클래스가 캐스트될 수 있는 파생 동작의 유형입니다.