# <a name="class-mippolicyengine"></a>클래스 mip::PolicyEngine 
이 클래스는 모든 엔진 함수에 대한 인터페이스를 제공합니다.
  
## <a name="summary"></a>요약
 멤버                        | 설명                                
--------------------------------|---------------------------------------------
public const Settings& GetSettings() const  |  정책 엔진 [Settings](#classmip_1_1_policy_engine_1_1_settings)를 가져옵니다.
public const std::vector<std::shared_ptr<Label>>& ListSensitivityLabels()  |  정책 엔진과 연결된 민감도 레이블을 나열합니다.
public std::shared_ptr<ContentLabel> GetSensitivityLabel(const ExecutionState& state)  |  기존 콘텐츠에서 민감도 레이블을 가져옵니다.
public std::shared_ptr<Label> GetDefaultSensitivityLabel()  |  기본 민감도 레이블을 가져옵니다.
public std::vector<std::shared_ptr<Action>> ComputeActions(const ExecutionState& state)  |  제공된 상태에 따라 엔진에서 규칙을 실행하고 실행할 동작 목록을 반환합니다.
  
## <a name="members"></a>멤버
  
### <a name="settings"></a>설정
정책 엔진 [Settings](#classmip_1_1_policy_engine_1_1_settings)를 가져옵니다.
  
#### <a name="returns"></a>Returns
정책 엔진 설정. 
**참고 항목**: [mip::PolicyEngine::Settings](#classmip_1_1_policy_engine_1_1_settings)
  
### <a name="label"></a>Label
정책 엔진과 연결된 민감도 레이블을 나열합니다.
  
#### <a name="returns"></a>Returns
민감도 레이블 목록.
  
### <a name="contentlabel"></a>ContentLabel
기존 콘텐츠에서 민감도 레이블을 가져옵니다.
레이블을 검색하는 데 필요한 정보는 제공된 실행 상태를 사용하여 얻습니다. 
  
#### <a name="parameters"></a>매개 변수
* state 
  
#### <a name="returns"></a>Returns
민감도 레이블과 추가 정보를 포함하는 콘텐츠 레이블 개체. 없는 경우 빈 결과를 반환합니다. 
**참고 항목**: [mip::ContentLabel](#classmip_1_1_content_label).
  
### <a name="label"></a>Label
기본 민감도 레이블을 가져옵니다.
  
#### <a name="returns"></a>Returns
있는 경우 기본 민감도 레이블, 설정된 기본 레이블이 없는 경우 nullptr.
  
### <a name="action"></a>작업
제공된 상태에 따라 엔진에서 규칙을 실행하고 실행할 동작 목록을 반환합니다.
  
#### <a name="parameters"></a>매개 변수
* state 규칙이 실행 중인 콘텐츠의 현재 실행 상태입니다. 
  
#### <a name="returns"></a>Returns
콘텐츠에 적용되어야 하는 동작 목록.