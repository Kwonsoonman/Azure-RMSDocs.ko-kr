# <a name="class-mipaddwatermarkaction"></a>클래스 mip::AddWatermarkAction 
워터마크를 추가하도록 지정하는 동작 클래스입니다.
  
## <a name="summary"></a>요약
 멤버                        | 설명                                
--------------------------------|---------------------------------------------
 public const std::string& GetUIElementName()  |  워터마크 요소를 표시하는 데 사용되는 API입니다.
 public WatermarkLayout GetLayout() const  |  워터마크 레이아웃을 가져오는 데 사용되는 API입니다.
 public const std::string& GetText() const  |  콘텐츠 헤더로 이동하려는 텍스트를 가져옵니다.
 public const std::string& GetFontName() const  |  콘텐츠 헤더를 표시하는 데 사용되는 글꼴 이름을 가져옵니다.
 public int GetFontSize() const  |  콘텐츠 헤더를 표시하는 데 사용되는 글꼴 크기를 가져옵니다.
 public const std::string& GetFontColor() const  |  콘텐츠 헤더를 표시하는 데 사용되는 글꼴 색을 가져옵니다.
 public ActionType GetType() const  |  [동작](class_mip_action.md) 유형을 가져옵니다.
  
## <a name="members"></a>멤버
  
### <a name="getuielementname"></a>GetUIElementName
워터마크 요소를 표시하는 데 사용되는 API입니다.

  
**반환**: 워터마크를 포함하는 UI 요소에 사용해야 하는 이름. 워터마크를 제거해야 하는 경우 동일한 이름이 RemoveWatermarkingAction에 반환됩니다.
  
### <a name="getlayout"></a>GetLayout
워터마크 레이아웃을 가져오는 데 사용되는 API입니다.

  
**반환**: WatermarkLayout. 열거형 HORIZONTAL|DIAGONAL 형식의 워터마크 레이아웃입니다. ,
  
### <a name="gettext"></a>GetText
콘텐츠 헤더로 이동하려는 텍스트를 가져옵니다.

  
**반환**: 콘텐츠 헤더 텍스트
  
### <a name="getfontname"></a>GetFontName
콘텐츠 헤더를 표시하는 데 사용되는 글꼴 이름을 가져옵니다.

  
**반환**: 글꼴 이름, 정책 Calibri에 의해 설정되지 않은 경우 기본값
  
### <a name="getfontsize"></a>GetFontSize
콘텐츠 헤더를 표시하는 데 사용되는 글꼴 크기를 가져옵니다.

  
**반환**: 정수 글꼴 크기
  
### <a name="getfontcolor"></a>GetFontColor
콘텐츠 헤더를 표시하는 데 사용되는 글꼴 색을 가져옵니다.

  
**반환**: 문자열 글꼴 색(예: “#000000”)
  
### <a name="actiontype"></a>ActionType
[동작](class_mip_action.md) 유형을 가져옵니다.

  
**반환**: ActionType. 이 기본 클래스가 캐스트될 수 있는 파생 동작의 유형입니다.