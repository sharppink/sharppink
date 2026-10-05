## 🎯 About Me
AI/LLM 애플리케이션과 백엔드 시스템 개발에 관심이 많은 개발자입니다. **LangGraph**를 활용한 멀티 에이전트 워크플로우 구축과 데이터 처리 파이프라인 설계에 집중하고 있습니다.

- 🤖 **관심 분야**: LLM 애플리케이션, 멀티 에이전트 시스템, 백엔드 개발
- 📚 **현재 학습 중**: 고급 LLM 아키텍처, 에이전트 오케스트레이션, API 설계
- 🎯 **목표**: AI 기술을 실무에 적용할 수 있는 백엔드/AI 엔지니어로 성장하는 것

## 🎓 Education

**안양대학교** | 통계데이터사이언스학과 학사
- 2020.03 - 2026.02

**키움 디지털 아카데미(KDA) 3기 수료**
- 키움증권 주관 실무형 금융 데이터 인재 양성 프로그램
- 2025.12 ~ 2026.04

## 💻 Tech Stack

**Languages**
Python | TypeScript | JavaScript

**Frameworks & Tools**
LangGraph | LangChain | FastAPI | Streamlit | Supabase | Docker | Ollama | n8n | ComfyUI | Jupyter Notebook | Git

**Areas of Expertise**
AI/ML Applications | Multi-Agent Systems | Data Processing | Backend Development

## 🚀 Projects

### [GoodJob](https://github.com/sharppink/goodjob) — 채용공고 맞춤 이력서 생성 AI 에이전트

채용공고와 내 경력을 비교해 적합도를 점수로 매기고, 충분히 맞으면 그 공고에 맞춘 이력서·면접 예상 질문·자소서를 써 주는 AI 서비스

🔗 **Live Demo**: [goodjob-ai.streamlit.app](https://goodjob-ai.streamlit.app) (Google 계정으로 로그인, 계정당 하루 사용 횟수 제한)

- **AI**: LangGraph 6단계 에이전트(공고 구조화 → RAG 경력 검색 → 적합도 판정 → 이력서 초안 → 사실성 검토 → 면접 질문), 적합도가 낮으면 조기 종료. 검토 단계에서 원본 경력과 대조해 근거 없는 경력 업무를 같은 입력 5회 생성 기준 14건 → 0건으로 제거
- **측정 기반 결정**: RAGAS로 재 보니 리랭커가 검색 recall을 0.90 → 0.65로 떨어뜨려 기본값에서 제외, gpt-4o 응답으로 증류한 데이터로 Qwen2.5-7B를 QLoRA 파인튜닝해 공고 파서 우대기술 F1 0.59 → 0.73
- **개인정보 보호 모드**: 프로필이 PC 밖으로 나가지 않도록 LLM·임베딩을 전부 로컬(Ollama)로 처리
- **서비스 기능**: 프로필에서 검색어를 만들어 맞는 공고를 찾는 공고 추천(목록·비공고 페이지 자동 제외), 생성한 이력서가 자동으로 들어가고 드래그로 지원 단계를 옮기는 지원 현황 보드
- **운영**: Google 로그인 + 계정별 데이터 분리(Supabase pgvector, RLS), 공개 배포 비용 상한을 위한 계정별·전체 하루 사용량 제한, pytest 180여 개 + GitHub Actions CI(pgvector 통합 테스트·Docker 동작 확인), Streamlit Cloud 배포
- **Tech**: Python · LangGraph · OpenAI · Ollama · Chroma · Supabase(pgvector) · RAGAS · Unsloth · FastAPI · Streamlit · Docker · GitHub Actions

### [워키포인트 (Kiki)](https://github.com/Kiki-The-Stock-Trader-Courier/kiki_with_lovable) — 걸음으로 만나는 근처 상장 기업

걷기로 포인트를 쌓고, 지도에서 내 주변 상장사를 확인하며, AI 챗봇 "키키"와 대화해 투자 정보를 얻는 웹/하이브리드 앱

- **AI**: 규칙 기반 1차 분류 → 애매한 요청만 소형 LLM 2차 보정하는 하이브리드 의도 라우터, 경량 RAG(네이버 뉴스 + 웹 스니펫 주입), 구조화 출력(JSON) 퀴즈 생성 후 서버 화이트리스트 검증, LangSmith로 전체 LLM 호출 트레이싱
- **아키텍처**: Vercel Hobby 함수 개수 제한을 단일 서버리스 게이트웨이(`api/gw.ts`) + `vercel.json` rewrites로 우회, 외부 시세/기업 API 실패 시 목업 폴백으로 무중단
- **Tech**: React 18 · TypeScript · Vite · Tailwind · shadcn/ui · Leaflet · TanStack Query · Supabase(Postgres·Auth) · OpenAI · Capacitor(Android/iOS) · Vitest · Playwright


### [KITCH](https://github.com/YeouidoRocketTeam/Project_Rocket_Team) — 주식 정보 신뢰도 AI 분석 앱

SNS·유튜브·뉴스의 주식 정보 링크를 입력하면 AI가 ROC 가중치법으로 신뢰도를 자동 채점해, 개인 투자자가 찌라시·선동성 콘텐츠를 걸러낼 수 있게 돕는 모바일 앱

- **신뢰도 알고리즘**: 출처 권위도(40.8%) · 시점 유효성(24.2%) · 논리적 완결성(15.8%) · 이해관계 투명성(10.3%) · 데이터 구체성(6.1%) · 교차검증 일치도(2.8%) 6개 지표를 ROC 가중치법으로 합산, 체크리스트 기반 감점 방식으로 0~100점 산출
- - **AI**: 멀티 에이전트 + RAG로 교차검증(교차검증 불일치 시 "경고 상태" 자동 발동), 섹터 키워드 기반 관련 뉴스 자동 페치, 감성 분석(Sentiment) 병행
  - - **아키텍처**: pnpm 모노레포(api-server · mobile · lib) — OpenAPI 스펙에서 Orval로 React Query 훅·Zod 스키마 코드젠, Express 5 라우트는 api-zod로 요청·응답 검증, 키움증권 연동 바텀바
    - - **Tech**: React Native · Expo · TypeScript · Express 5 · PostgreSQL · Drizzle ORM · OpenAI · Zod · Orval · pnpm Workspaces
