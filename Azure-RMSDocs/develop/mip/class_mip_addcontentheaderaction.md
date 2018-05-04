# <a name="class-mipaddcontentheaderaction"></a>클래스 mip::AddContentHeaderAction 
콘텐츠 헤더를 추가하도록 지정하는 동작 클래스입니다.
## <a name="summary"></a>요약
 멤버                        | 설명                                
--------------------------------|---------------------------------------------
public const std::string & GetUIElementName | 콘텐츠 헤더 요소를 표시하는 데 사용되는 API입니다.
public const std::string & GetText | 콘텐츠 헤더로 이동하려는 텍스트를 가져옵니다.
public const std::string & GetFontName | 콘텐츠 헤더를 표시하는 데 사용되는 글꼴 이름을 가져옵니다.
public int GetFontSize | 콘텐츠 헤더를 표시하는 데 사용되는 글꼴 크기를 가져옵니다.
public const std::string & GetFontColor | 콘텐츠 헤더를 표시하는 데 사용되는 글꼴 색을 가져옵니다.
public ContentMarkAlignment GetAlignment | 헤더의 맞춤을 가져옵니다.
public int GetMargin | 아래쪽의 헤더 여백을 가져옵니다.
public ActionType GetType
## <a name="members"></a>멤버
### <a name="getuielementname"></a>GetUIElementName
콘텐츠 헤더 요소를 표시하는 데 사용되는 API입니다.
#### <a name="returns"></a>Returns
콘텐츠 헤더를 포함하는 UI 요소에 사용해야 하는 이름입니다. 콘텐츠 헤더를 제거해야 하는 경우 동일한 이름이 [RemoveContentHeaderAction](#classmip_1_1_remove_content_header_action)에 반환됩니다.
### <a name="gettext"></a>GetText
콘텐츠 헤더로 이동하려는 텍스트를 가져옵니다.
#### <a name="returns"></a>Returns
콘텐츠 헤더 텍스트.
### <a name="getfontname"></a>GetFontName
콘텐츠 헤더를 표시하는 데 사용되는 글꼴 이름을 가져옵니다.
#### <a name="returns"></a>Returns
글꼴 이름, 정책 Calibri에 의해 설정되지 않은 경우 기본값.
### <a name="getfontsize"></a>GetFontSize
콘텐츠 헤더를 표시하는 데 사용되는 글꼴 크기를 가져옵니다.
#### <a name="returns"></a>Returns
정수 글꼴 크기.
### <a name="getfontcolor"></a>GetFontColor
콘텐츠 헤더를 표시하는 데 사용되는 글꼴 색을 가져옵니다.
#### <a name="returns"></a>Returns
문자열 글꼴 색(예: “#000000”).
### <a name="getalignment"></a>GetAlignment
헤더의 맞춤을 가져옵니다.
#### <a name="returns"></a>Returns
ContentMarkAlignment 열거자, LEFT|RIGHT|CENTER. 
**참고 항목**: ContentMarkAlignment
### <a name="getmargin"></a>GetMargin
아래쪽의 헤더 여백을 가져옵니다.
#### <a name="returns"></a>Returns
문서 아래쪽의 여백을 나타내는 정수(예: 10mm).
### <a name="actiontype"></a>ActionType
[동작](#classmip_1_1_action) 유형을 가져옵니다.
#### <a name="returns"></a>Returns
ActionType 이 기본 클래스가 캐스트될 수 있는 파생 동작의 유형입니다.