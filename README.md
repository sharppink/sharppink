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
LangGraph | LangChain | Jupyter Notebook | Git

**Areas of Expertise**
AI/ML Applications | Multi-Agent Systems | Data Processing | Backend Development

## 🚀 Projects

### [워키포인트 (Kiki)](https://github.com/Kiki-The-Stock-Trader-Courier/kiki_with_lovable) — 걸음으로 만나는 근처 상장 기업

걷기로 포인트를 쌓고, 지도에서 내 주변 상장사를 확인하며, AI 챗봇 "키키"와 대화해 투자 정보를 얻는 웹/하이브리드 앱

- **AI**: 규칙 기반 1차 분류 → 애매한 요청만 소형 LLM 2차 보정하는 하이브리드 의도 라우터, 경량 RAG(네이버 뉴스 + 웹 스니펫 주입), 구조화 출력(JSON) 퀴즈 생성 후 서버 화이트리스트 검증, LangSmith로 전체 LLM 호출 트레이싱
- **아키텍처**: Vercel Hobby 함수 개수 제한을 단일 서버리스 게이트웨이(`api/gw.ts`) + `vercel.json` rewrites로 우회, 외부 시세/기업 API 실패 시 목업 폴백으로 무중단
- **Tech**: React 18 · TypeScript · Vite · Tailwind · shadcn/ui · Leaflet · TanStack Query · Supabase(Postgres·Auth) · OpenAI · Capacitor(Android/iOS) · Vitest · Playwright
