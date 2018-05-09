# <a name="class-mipremovecontentfooteraction"></a>클래스 mip::RemoveContentFooterAction 
문서에서 콘텐츠 바닥글을 제거하도록 지정하는 동작 클래스입니다.
  
## <a name="summary"></a>요약
 멤버                        | 설명                                
--------------------------------|---------------------------------------------
public const std::vector<std::string>& GetUIElementNames()  |  제거할 UI 요소를 찾는 데 사용되어야 하는 이름 목록을 가져옵니다.
public ActionType GetType() const  |  [동작](#classmip_1_1_action) 유형을 가져옵니다.
  
## <a name="members"></a>멤버
  
### <a name="getuielementnames"></a>GetUIElementNames
제거할 UI 요소를 찾는 데 사용되어야 하는 이름 목록을 가져옵니다.
  
#### <a name="returns"></a>Returns
UI 요소 이름의 목록
  
### <a name="actiontype"></a>ActionType
[동작](#classmip_1_1_action) 유형을 가져옵니다.
  
#### <a name="returns"></a>Returns
ActionType 이 기본 클래스가 캐스트될 수 있는 파생 동작의 유형입니다.