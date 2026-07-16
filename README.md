Sentitype: 비언어적 단서의 실시간 파라미터화를 통한 화용론적 거대언어모델(LLM) 상담 시스템 연구
A Study on Pragmatic LLM Counseling System through Real-time Parameterization of Non-verbal Cues

-프로젝트 개요 (Abstract)

 본 연구는 텍스트 정보에만 의존하는 기존 상담용 AI의 한계를 극복하기 위해, 입력 환경에서의 수정 패턴, 발화 사이의 침묵 및 망설임 등 비언어적 단서를 실시간 파라미터로 추출하고 이를 거대언어모델의 답변 생성 로직에 동적으로 주입하는 적응형 상담 프레임워크 'Sentitype'를 제안합니다.
 인문학적 소양과 컴퓨터공학의 데이터 엔지니어링 기술을 융합하여, 인공지능이 인간의 텍스트 이면에 숨겨진 실시간 정서 상태를 완벽히 이해하고 최적의 공감 솔루션을 제공하는 시스템을 공학적으로 구현하였습니다.

 -시스템 아키텍처 및 데이터 흐름
 
[클라이언트: 웹 브라우저] 
(JavaScript Bridge: Keydown / Keyup 이벤트 실시간 캡처)
[백엔드: Python 분석 엔진]
(Z-score 기반 개인 편차 제거 및 3대 심리 가중치 산출)
[상담 최적화 엔진] 
(동적 프롬프트 주입 - 지침형 Instructional 바인딩)
[LLM 추론 엔진: GPT-4o] ➔ [실시간 맞춤형 상담 발화 출력 (스트리밍)]

-핵심 구현 코드

def get_instructional_prompt(hesitation_z, correction_rate, dwell_z):
    """
    KSD 실시간 정규화 지표를 입력받아 지침형(Instructional) 프롬프트를 동적 튜닝합니다.
    """
    base_instructions = [
        "System: 당신은 경청과 따뜻한 정서적 지지를 전문으로 하는 심리 상담사 페르소나입니다."
    ]
    
    # 1. 망설임 지표 분석을 통한 대화 템포 제어
    if hesitation_z > 1.5:
        base_instructions.append(
            "- [지침] 사용자의 생각 정리에 인지적 망설임이 감지되었습니다. 답변을 재촉하지 말고, "
            "천천히 마음을 털어놓을 수 있도록 여유로운 템포와 열린 질문으로 대화를 리드하세요."
        )
    
    # 2. 초조함/자기검열 감지 시 대처 가이드 바인딩
    if correction_rate > 0.2:
        base_instructions.append(
            "- [지침] 사용자가 문장을 수차례 지우며 강한 자기검열 혹은 초조함을 보이고 있습니다. "
            "완벽한 문장을 쓰지 않아도 괜찮음을 자연스럽게 상기시키며, 정서적 방어벽을 낮추어 주십시오."
        )
        
    # 3. 피로도 지표 반영
    if dwell_z > 1.2:
        base_instructions.append(
            "- [지침] 사용자의 물리적 반응 속도가 떨어져 고인지적 피로 상태가 감지되었습니다. "
            "이해하기 쉬운 명료하고 짧은 호흡의 어조를 사용하고, 충분한 휴식을 권유하십시오."
        )
        
    if len(base_instructions) == 1:
        base_instructions.append("- [지침] 일상적인 상담 어조와 공감을 유지하며 대화를 진행하십시오.")
        
    return "\n".join(base_instructions)

-성능 및 평가

수치형 전략(Numeric): 3.12\5.0
서술형 전략(Descriptive): 3.84\5.0
지침형 전략(Instructional): 4.68\5.0

-연구의 가치 및 향후 연구 방향

미디어 및 테크 저널리즘 연계: 인간과 AI의 인터랙션 메커니즘을 데이터로 정량화하여 해석하는 수준 높은 'AI 리터러시' 역량을 확립함.

향후 대학생 피험자 범위를 다변화하여 대규모 임상 통계 검증을 거칠 예정이며, 슬라이더 기반의 수동 피드백 루프를 강화학습 기반의 완전히 자동화된 '자기 진화형 정서 제어 아키텍처'로 고도화할 계획입니다.
    
