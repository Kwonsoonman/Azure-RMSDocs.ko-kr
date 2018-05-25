# <a name="class-mipexecutionstate"></a>클래스 mip::ExecutionState 
엔진을 실행하는 데 필요한 모든 상태에 대한 인터페이스입니다.
클라이언트는 필요한 상태를 얻기 위해 메서드만 호출해야 합니다. 또한 효율성을 위해 클라이언트는 해당 상태가 미리 계산되지 않고 동적으로 계산되도록 이 인터페이스를 구현할 수 있습니다.
  
## <a name="summary"></a>요약
 멤버                        | 설명                                
--------------------------------|---------------------------------------------
 public std::string GetNewLabelId() const  |  문서에 적용해야 하는 민감도 레이블 ID를 가져옵니다.
 public bool IsDowngradeJustified() const  |  구현은 기존 레이블을 다운그레이드할 근거가 제공되었는지 여부를 전달해야 합니다.
 public AssignmentMethod GetNewLabelAssignmentMethod() const  |  새 레이블의 할당 메서드를 가져옵니다.
public std::vector<std::pair<std::string, std::string>> GetContentMetadata(const std::vector<std::string>& names, const std::vector<std::string>& namePrefixes) const  |  콘텐츠에서 메타데이터 항목을 가져옵니다.
 public std::string GetTemplateId() const  |  권한 관리 서비스 보호 템플릿 ID를 가져옵니다.
 public ContentFormat GetContentFormat() const  |  콘텐츠 형식을 가져옵니다.
 public const ActionType GetSupportedActions() const  |  응용 프로그램이 지원하는 작업 목록을 반환합니다. 모든 동작 유형은 [mip/upe/action.h](#action)에 나열됩니다.
  
## <a name="members"></a>멤버
  
### <a name="getnewlabelid"></a>GetNewLabelId
문서에 적용해야 하는 민감도 레이블 ID를 가져옵니다.

  
**반환**: 있는 경우 콘텐츠에 적용할 민감도 레이블 ID, 없는 경우 공란이 되어 레이블을 제거합니다.
  
### <a name="isdowngradejustified"></a>IsDowngradeJustified
구현은 기존 레이블을 다운그레이드할 근거가 제공되었는지 여부를 전달해야 합니다.

  
**반환**: 이미 다운그레이드 근거가 제공된 경우 true, 근거가 제공되지 않은 경우 false. 
**참고 항목**: [mip::JustifyAction](class_mip_justifyaction.md)
  
### <a name="getnewlabelassignmentmethod"></a>GetNewLabelAssignmentMethod
새 레이블의 할당 메서드를 가져옵니다.

  
**반환**: 할당 메서드 STANDARD, PRIVILEGED, AUTO. 
**참고 항목**: mip::AssignmentMethod
  
### <a name="getcontentmetadata"></a>GetContentMetadata
콘텐츠에서 메타데이터 항목을 가져옵니다.

  
**반환**: 콘텐츠에 적용된 메타데이터를 나타내는 키 값 쌍의 벡터. 각 메타데이터 항목은 이름 및 값 쌍입니다.
  
### <a name="gettemplateid"></a>GetTemplateId
권한 관리 서비스 보호 템플릿 ID를 가져옵니다.

  
**반환**: 있는 경우 권한 관리 서비스 보호 템플릿 ID, 없는 경우 중괄호 없이 GUID 형식으로 빈 문자열을 반환합니다.
  
### <a name="getcontentformat"></a>GetContentFormat
콘텐츠 형식을 가져옵니다.

  
**반환**: DEFAULT, EMAIL **참고 항목**: mip::ContentFormat
  
### <a name="actiontype"></a>ActionType
응용 프로그램이 지원하는 작업 목록을 반환합니다. 모든 동작 유형은 [mip/upe/action.h](#action)에 나열됩니다.