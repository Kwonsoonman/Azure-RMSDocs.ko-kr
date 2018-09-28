# <a name="class-miplabel"></a>클래스 mip::Label 
단일 Microsoft Information Protection 레이블에 대한 추상화입니다.
  
## <a name="summary"></a>요약
 멤버                        | 설명                                
--------------------------------|---------------------------------------------
 public const std::string& GetId() const  |  레이블 ID를 가져옵니다.
 public const std::string& GetName() const  |  레이블 이름을 가져옵니다.
 public const std::string& GetDescription() const  |  레이블 설명을 가져옵니다.
 public const std::string& GetColor() const  |  레이블을 표시할 색을 가져옵니다.
 public int GetSensitivity() const  |  레이블의 민감도를 가져옵니다.
 public const std::string& GetTooltip() const  |  레이블의 도구 설명을 가져옵니다.
 public bool IsActive() const  |  레이블이 활성 상태인 경우 부울 신호를 가져옵니다.
public std::weak_ptr<Label> GetParent() const  |  부모 레이블을 가져옵니다.
public const std::vector<std::shared_ptr<Label>>& GetChildren() const  |  현재 레이블의 자식 레이블을 가져옵니다.
  
## <a name="members"></a>멤버
  
### <a name="getid"></a>GetId
레이블 ID를 가져옵니다.

  
**반환**: 레이블 ID
  
### <a name="getname"></a>GetName
레이블 이름을 가져옵니다.

  
**반환**: 레이블 이름
  
### <a name="getdescription"></a>GetDescription
레이블 설명을 가져옵니다.

  
**반환**: 레이블 설명
  
### <a name="getcolor"></a>GetColor
레이블을 표시할 색을 가져옵니다.

  
**반환**: 문자열 형식의 색상값. 각 RR, GG, BB가 16진수 0-f인 “#RRGGBB”.
  
### <a name="getsensitivity"></a>GetSensitivity
레이블의 민감도를 가져옵니다.

  
**반환**: 숫자 값. 값이 클수록 더 높은 민감도를 정의합니다.
  
### <a name="gettooltip"></a>GetTooltip
레이블의 도구 설명을 가져옵니다.

  
**반환**: 도구 설명 문자열
  
### <a name="isactive"></a>IsActive
레이블이 활성 상태인 경우 부울 신호를 가져옵니다.
활성 레이블만 적용할 수 있습니다. 비활성 레이블은 적용할 수 없고 표시 목적으로만 사용됩니다. 

  
**반환**: 레이블이 활성 상태이면 true, 그렇지 않으면 false
  
### <a name="label"></a>Label
부모 레이블을 가져옵니다.

  
**반환**: 있는 경우 부모 레이블에 대한 약한 포인터, 그렇지 않으면 빈 포인터
  
### <a name="label"></a>Label
현재 레이블의 자식 레이블을 가져옵니다.

  
**반환**: 레이블에 대한 공유 포인터의 벡터