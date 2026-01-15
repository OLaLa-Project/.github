# OLaLA — Operational LLM & Logic Architecture

**OLaLA**는 조직이 **Large Language Models(LLMs)** 를  
**검증·통제·승인·배포** 가능한 형태로 운영하기 위한  
**AI 운영 아키텍처(Operational Architecture)** 입니다.

> OLaLA는 챗봇 프레임워크가 아닙니다.  
> OLaLA는 **LLM을 프로덕션 시스템으로 다루기 위한 구조와 규칙**입니다.

---

## Why OLaLA?

조직에서 LLM을 실제 업무에 투입할 때, 문제는 모델 성능이 아니라 **운영**입니다.

- ❌ 프롬프트 변경 이력 없음
- ❌ 검증되지 않은 답변의 배포
- ❌ 환각·허위 정보·정책 위반에 대한 책임 불명확
- ❌ 보안/법무/데이터 오너 승인 없이 릴리즈

OLaLA는 다음 질문에 **시스템 차원에서** 답합니다.

- 이 답변은 **검증되었는가?**
- 이 버전은 **누가 승인했는가?**
- 정책을 **위반하지 않았는가?**
- 문제가 생기면 **즉시 롤백 가능한가?**

---

## What is OLaLA?

**OLaLA = Operational LLM & Logic Architecture**

| Letter | Meaning | Technical Focus |
|------|--------|----------------|
| **O** | Operational | 배포·운영·감사 가능한 구조 |
| **L** | LLM | 모델 교체 가능, 규격 고정 |
| **a** | and | RAG·Policy·Eval·Human-in-the-loop |
| **L** | Logic | 검증·판단·리스크 스코어링 |
| **A** | Architecture | 레이어드·확장 가능한 구조 |

---

## Core Philosophy

### 1. LLM Output is an Artifact
- 답변은 **즉흥 결과**가 아니라
- **버전·정책·평가 결과에 귀속된 아티팩트**

### 2. No Evaluation, No Deployment
- 평가(Eval) 미통과 → 승인 불가 → 배포 불가
- **CI/CD 개념을 LLM에 적용**

### 3. Governance is Built-in
- RBAC
- Approval Workflow
- Audit Log
- Immutable Versions

---

## Architecture Overview

OLaLA는 단일 서비스가 아니라 **레이어드 아키텍처**입니다.

[ UI / Console ]
↓
[ API Gateway + Auth ]
↓
[ Assistant / Policy / Eval Services ]
↓
[ Logic Layer (FakeNewsGuard 등) ]
↓
[ LLM Gateway (Provider Abstraction) ]
↓
[ Model Providers ]

yaml
코드 복사

### Key Layers

- **Assistant Layer**
  - Prompt, Policy, Tool, Knowledge 조합
- **Logic Layer**
  - Fact consistency
  - Fake news / hallucination detection
  - Risk scoring
- **Evaluation Layer**
  - Testset 기반 자동 평가
  - 회귀 테스트
- **Approval & Deploy Layer**
  - Role-based approval
  - Environment 분리
  - Rollback
- **Observability**
  - Cost / Latency / Failure / Feedback
  - Audit logs (append-only)

---

## Key Projects in This Organization

### 🧠 OLaLA Foundry
**AI Assistant Design · Evaluation · Approval · Deployment Platform**

- Assistant Versioning
- Policy-as-Config
- Evaluation Gate
- Approval Workflow
- Multi-channel Deployment

> CI/CD for AI Assistants

---

### 🛡️ FakeNewsGuard
**Logic Layer for Truth & Consistency Verification**

- Claim extraction
- Evidence grounding
- Cross-source consistency check
- Risk / confidence scoring

> FakeNewsGuard는 OLaLA의 **Logic Layer** 핵심 엔진입니다.

---

## Tech Stack (Reference)

> 실제 구현은 프로젝트별로 다를 수 있으나, 구조는 동일합니다.

### Frontend
- Next.js (App Router)
- TypeScript
- Tailwind CSS
- TanStack Query

### Backend
- FastAPI / NestJS
- PostgreSQL (+ pgvector)
- Redis (Queue)
- Object Storage (S3 compatible)

### AI / ML
- LLM Gateway (Provider abstraction)
- Embedding + Vector Search
- LLM-as-a-Judge (Eval)
- Rule-based + Model-based Logic

### Ops
- Docker
- CI/CD (GitHub Actions)
- OpenTelemetry
- Audit Logging

---

## What OLaLA Is NOT

- ❌ 단순 챗봇 빌더
- ❌ 프롬프트 관리 툴
- ❌ 모델 성능만 강조하는 AI 데모

OLaLA는 **“조직이 AI 출력에 책임질 수 있게 만드는 구조”**입니다.

---

## Who Is This For?

- AI 제품 오너 / PM
- 보안·컴플라이언스 팀
- 플랫폼 엔지니어 / MLOps
- 조직 단위 AI 도입을 고민하는 팀

---

## Vision

> **LLMs should be governed like production systems, not experiments.**

OLaLA는  
**LLM 운영의 표준 아키텍처**를 만드는 것을 목표로 합니다.

---

## License & Contribution

- License: TBD
- Contribution: Architecture-first, PRD-driven development
- Discussions & RFCs are welcome

---

**OLaLA — Architecture before intelligence.**
