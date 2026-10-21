# Antigravity Dashboard Starter

Google Antigravity 2.0 & CLI 핸즈온 워크샵을 위한 스타터 리포지토리입니다.
비즈니스 운영 데이터(`business_operations.csv`)를 기반으로 자율 AI 에이전트를 활용해 실시간 경영 모니터링 웹 대시보드를 구축하고 브라우저 E2E 무결성을 검증합니다.

---

## 📂 프로젝트 구조

```text
antigravity-dashboard-starter/
├── data/
│   └── business_operations.csv       # 6개월치(2026-03 ~ 2026-08) 5개 부서 운영 데이터 (920행)
├── .agents/
│   ├── rules/
│   │   └── design_guidelines.md       # 구글 클라우드 테마 색상 팔레트 및 대시보드 UI 가이드라인
│   └── mcp_config.json                # 로컬 파일시스템 MCP 설정
└── README.md                          # 실습 안내서
```

---

## 🚀 메인 핸즈온 5단계 진행 순서

### [실습 1단계] 스타터 리포지토리 로드 및 데이터 탐색 (Explore)
Antigravity 데스크톱 앱에서 이 폴더를 열고, 에이전트에게 데이터셋의 구조와 잠재적 이슈를 파악시킵니다.
```text
@business_operations.csv 이 데이터가 어떤 구조이고, 눈에 띄는 문제가 있는지 먼저 알려줘.
아직 코드는 만들지 마.
```

### [실습 2단계] 요구사항 정리 및 구현 계획서 (/grill-me → /plan → 승인)
에이전트에게 역인터뷰를 진행시키고, 대시보드 구현 계획서를 요청합니다.
```text
[1. 요구사항 역인터뷰]
/grill-me @business_operations.csv 로 경영진 보고용 대시보드를 만들고 싶어

[2. 구현 계획서 요청 (/plan)]
/plan 위 요구사항대로 구현 계획서(Implementation Plan)를 세워줘. 최소한 아래는 포함해줘.
1. 상단 KPI 카드: 총 매출, 총 지출, 순이익, 평균 CS 해결률
2. 월별/부서별 매출 및 지출 추이 차트
3. 부서별 비용 지출 비중 도넛 차트
4. CS 티켓 처리 현황 테이블 (해결률 80% 미만 경고 배지)
5. 상단 부서별 드롭다운 필터

[3. 계획서 인라인 코멘트 & 승인]
- 예: "Engineering은 매출이 0이니 0 나눗셈을 방어해줘"
- 반영된 계획 확인 후 Proceed 클릭

[4. 감사 Hook 생성]
대시보드 코드 파일이 수정될 때마다 audit_changes.log에 기록하는 Hook을 .agents/hooks.json으로 만들어줘. PostToolUse 이벤트와 matcher를 사용해줘.
```

### [실습 3단계] 디자인 룰 적용 및 로컬 서버 실행 (Execute)
`.agents/rules/design_guidelines.md`에 정의된 구글 클라우드 색상 팔레트(`Google Blue #1a73e8` 등)가 적용되었는지 확인하고 로컬 서버를 구동합니다.
```text
방금 작성한 대시보드 웹 앱을 실행해서 로컬 포트로 열어줘.
```
*(기본 로컬 주소: `http://localhost:8000`)*

### [실습 4단계] 브라우저 서브에이전트 E2E 검증 & 녹화본 확인 (Verify)
격리된 브라우저 서브에이전트를 호출하여 UI 정상 표시 여부와 인터랙션을 자율 테스트합니다.
```text
/browser 로컬 대시보드 웹 서버에 접속해서 다음을 테스트해줘.
1. 페이지 타이틀 및 KPI 카드 4종이 정상 표시되는지 확인.
2. 부서 필터에서 'Engineering'을 선택했을 때 차트가 갱신되는지 검증.
3. 브라우저 콘솔 에러가 없는지 점검.
4. 최종 스크린샷과 조작 전 과정을 담은 녹화 영상(Recording)을 첨부해줘.
```

### [실습 5단계] Antigravity CLI 조작 & Session Resume (Handoff)
터미널에서 CLI(`agy`)로 테스트 코드를 작성하고, 개선 사항을 팀 룰로 영구 저장합니다.
```bash
# 1. 터미널 원샷 명령
agy "data/business_operations.csv의 데이터 포맷을 검증하는 pytest 코드를 작성하고 실행해줘"

# 2. 대화형 TUI 모드 진입
agy

# 3. 노하우 룰 생성
/learn 오늘 대시보드 작업에서 반복해서 고쳤던 부분을 정리해서 .agents/rules/dashboard_best_practices.md 규칙 파일로 만들어줘.
```
