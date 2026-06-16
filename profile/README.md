# Qeploy

> 대화형 AI 웹서비스 빌드·배포 자동화 플랫폼

<p align="center">
  <img src="./assets/presentations/final/01-cover.png" alt="Qeploy Cover" width="100%" />
</p>

Qeploy는 사용자가 자연어로 웹서비스를 생성·수정하고, GitHub 기반 버전관리와 Preview, 배포, 도메인 연결, 클라우드 운영 흐름까지 하나로 연결하는 AI Agent 기반 웹서비스 운영 자동화 플랫폼입니다.

생성형 AI로 웹 초안을 만드는 일은 쉬워졌지만, 실제 서비스 URL로 공개하기까지의 수정·검증·배포·도메인·인프라 운영 과정은 여전히 복잡합니다. Qeploy는 이 과정을 대화형 Agent 흐름으로 단순화하여 비개발자, 입문 개발자, 학생 팀, 예비 창업팀이 아이디어를 빠르게 실제 서비스로 연결할 수 있도록 돕습니다.

---

## Demo Video

[![Qeploy Demo Video](https://img.youtube.com/vi/40x44EsGruY/maxresdefault.jpg)](https://youtu.be/40x44EsGruY?si=SnJmcpMu_P3-9r0E)

- YouTube: https://youtu.be/40x44EsGruY?si=SnJmcpMu_P3-9r0E

---

## Repositories

| Repository | Description |
|---|---|
| [Dvely_FE](https://github.com/Dvely/Dvely_FE) | React 기반 프론트엔드 |
| [Dvely_springboot](https://github.com/Dvely/Dvely_springboot) | Spring Boot 기반 백엔드 API 서버 |
| [.github](https://github.com/Dvely/.github) | Dvely 조직 프로필 README 및 발표자료 이미지 관리 |

---

## Problem Definition

| 구분 | 내용 |
|---|---|
| 현상 | 생성형 AI로 웹 초안 제작은 쉬워졌지만, 실제 서비스로 운영하기 위한 과정은 여전히 복잡합니다. |
| 문제인식 | 배포, 도메인, GitHub, 클라우드 인프라 설정은 비개발자와 입문 개발자에게 높은 진입장벽으로 남아 있습니다. |
| 문제정의 | AI로 만든 웹 결과물이 실제 서비스 URL로 연결되기까지의 생성·수정·검증·배포·운영 흐름을 단순화해야 합니다. |

---

## Goal

Qeploy의 목표는 단순 코드 생성이 아니라, 서비스가 실제 운영 가능한 상태에 도달하도록 돕는 것입니다.

```text
Idea → AI Edit → Diff Review → Preview → Deploy → Domain → Operation
```

최종적으로는 자연어 요청만으로 웹서비스를 생성·수정하고, GitHub 기반 버전관리와 배포를 거쳐 도메인 연결 및 AWS/GCP 등 클라우드 인프라 운영까지 지원하는 AI Agent 기반 웹서비스 운영 자동화 플랫폼을 지향합니다.

---

## Core Features

### 1. 자연어 기반 웹서비스 생성·수정

사용자는 복잡한 코드 수정 없이 자연어로 원하는 웹서비스 또는 수정사항을 요청할 수 있습니다.

```text
TODO 서비스를 만들어줘.
메인 화면의 버튼 색상을 보라색으로 바꿔줘.
GitHub Pages에 배포하고 URL을 알려줘.
도메인 연결도 진행해줘.
```

### 2. Agentic Workflow

사용자 요청은 의사결정 Agent를 거쳐 Code Agent, Deploy Agent, Domain Agent 등으로 분류됩니다. 각 Agent는 담당 작업을 수행하고, 실행 전 승인과 로그 확인 과정을 거쳐 안정적으로 반영됩니다.

<p align="center">
  <img src="./assets/presentations/final/07-agentic-workflow.png" alt="Agentic Workflow" width="100%" />
</p>

### 3. 코드 생성·수정·Diff 확인

Code Agent는 사용자의 자연어 요청을 코드 변경 작업으로 변환합니다. 변경사항은 Diff 형태로 확인하고 승인 후 반영할 수 있어, 예기치 않은 변경을 줄일 수 있습니다.

### 4. GitHub 기반 버전관리·배포

GitHub API를 활용해 저장소 생성, 코드 커밋, GitHub Pages 배포, CI/CD 연동 흐름을 지원합니다.

### 5. Preview 및 Production Deploy

배포 전 결과를 확인할 수 있는 Preview 환경을 제공하고, 이후 Production 배포까지 연결합니다. 이를 통해 사용자는 수정 결과를 검증한 뒤 실제 URL로 공개할 수 있습니다.

### 6. Domain Agent

Cloudflare API를 활용해 CNAME, DNS, HTTPS 등 도메인 연결 흐름을 자동화합니다.

### 7. Agent 로그 스트리밍

SSE 기반 로그 스트리밍으로 Agent의 진행 상태를 실시간으로 확인할 수 있습니다. 사용자는 생성, 커밋, 배포, 도메인 연결 과정을 대화 화면에서 추적할 수 있습니다.

### 8. 인프라 운영 확장

향후 AWS/GCP 등 클라우드 인프라 상태 확인, 운영 수정, 장애 복구, 배포 실패 원인 분석까지 확장하는 것을 목표로 합니다.

---

## System Architecture

<p align="center">
  <img src="./assets/presentations/final/06-system-architecture.png" alt="System Architecture" width="100%" />
</p>

Qeploy는 AWS EC2 환경에서 Nginx, React Frontend, Spring Boot Backend, PM2를 중심으로 구성됩니다. 외부 연동으로는 MySQL, Docker Preview Runtime, Anthropic/OpenAI LLM, GitHub API, Cloudflare API를 활용합니다.

```text
User Browser
  ↓
Nginx Reverse Proxy
  ↓
React Frontend / Spring Boot Backend
  ↓
AI Agent + GitHub API + Cloudflare API
  ↓
Preview / Deploy / Domain Connection
```

---

## Tech Stack

| Area | Stack |
|---|---|
| Frontend | React, Vite, Axios |
| Backend | Spring Boot, JPA, REST API |
| Database | MySQL |
| Runtime / Infra | AWS EC2, Nginx, PM2, Docker |
| AI | Anthropic API, OpenAI API |
| DevOps | GitHub API, GitHub Pages, GitHub Actions, Cloudflare API |
| Collaboration | Figma, Notion, GitHub |

---

## Service Progress

<p align="center">
  <img src="./assets/presentations/final/05-service-progress.png" alt="Service Progress" width="100%" />
</p>

현재 프로젝트는 PRD 정리, Figma 디자인 시스템, Swagger 기반 백엔드 API, AWS 서버 환경 구성까지 진행되었습니다.

| Area | Progress |
|---|---|
| 기획 | 95% |
| 디자인 | 70% |
| 프론트엔드 | 60% |
| 백엔드 | 80% |
| 인프라 | 90% |

---

## Troubleshooting

| Issue | Problem | Solution | Effect |
|---|---|---|---|
| Diff API 낭비 | 동일한 변경사항을 반복 조회하며 불필요한 API 호출 발생 | diff 조회 필요 여부를 state로 관리 | 변경 가능성이 있을 때만 diff를 다시 조회 |
| Chat 생성 방식 | 메시지 없이 빈 대화 세션이 계속 생성됨 | 첫 메시지 전송 시 세션 생성 API와 메시지 생성 API를 순차 호출 | 실제 대화가 있는 경우에만 세션 생성 |
| Agent 로그 스트리밍 | WebSocket은 양방향 통신에 적합하지만 로그 전달은 단방향 구조 | SSE 기반 로그 스트리밍 적용 | 구현 비용을 줄이고 실시간 진행 상태 확인 |
| Base Path / Custom Domain | GitHub Pages 재배포 시 assets 404 또는 CNAME 연결 끊김 | 루트 경로 기준 재빌드 및 CNAME 복원 | 커스텀 도메인 환경에서도 안정적 유지 |
| Human Error | PR/merge 누락 상태에서 서로 다른 화면 기준으로 논의 | PR/merge 상태 기준 통일 | 협업 기준 정리 및 검증 흐름 개선 |

---

## Presentations

> 이미지 경로는 `.github/profile/README.md` 기준입니다.

### 1학기 중간 프로젝트 제안서 발표

- 발표명: 프로젝트 계획서
- 주제: 대화형 AI 웹서비스 빌드·배포 자동화 플랫폼
- 주요 내용: 개요, 시스템 구성 및 동작, 개발환경, 유사시스템 조사, 기술탐구, 일정계획
- 권장 PPT 경로: `./docs/2026-1-midterm-presentation.pptx`
- 권장 PDF 경로: `./docs/2026-1-midterm-presentation.pdf`

<p align="center">
  <img src="./assets/presentations/midterm/01-cover.png" alt="중간발표 표지" width="100%" />
</p>

<details>
<summary>중간 발표자료 이미지 전체 보기</summary>

<img src="./assets/presentations/midterm/01-cover.png" alt="중간발표 01" width="100%" />

<img src="./assets/presentations/midterm/02-overview.png" alt="중간발표 02" width="100%" />

<img src="./assets/presentations/midterm/03-system-operation.png" alt="중간발표 03" width="100%" />

<img src="./assets/presentations/midterm/04-system-diagram.png" alt="중간발표 04" width="100%" />

<img src="./assets/presentations/midterm/05-development-environment.png" alt="중간발표 05" width="100%" />

<img src="./assets/presentations/midterm/06-competitor-research.png" alt="중간발표 06" width="100%" />

<img src="./assets/presentations/midterm/07-technical-study.png" alt="중간발표 07" width="100%" />

<img src="./assets/presentations/midterm/08-ui-feature-list.png" alt="중간발표 08" width="100%" />

<img src="./assets/presentations/midterm/09-schedule-plan.png" alt="중간발표 09" width="100%" />

<img src="./assets/presentations/midterm/10-etc.png" alt="중간발표 10" width="100%" />

</details>

### 1학기 기말 프로젝트 최종 발표

- 발표명: Graduation Project Midterm Presentation / 최종 발표자료
- 주제: Qeploy 대화형 AI 웹서비스 빌드·배포 자동화 플랫폼
- 주요 내용: 문제정의, 시장조사, 최종목표, 서비스 진행도, 시스템 아키텍처, Agentic Workflow, 시연영상, 트러블슈팅, 팀 소개, 향후 계획
- 권장 PPT 경로: `./docs/2026-1-final-presentation.pptx`
- 권장 PDF 경로: `./docs/2026-1-final-presentation.pdf`

<p align="center">
  <img src="./assets/presentations/final/01-cover.png" alt="최종발표 표지" width="100%" />
</p>

<details>
<summary>최종 발표자료 이미지 전체 보기</summary>

<img src="./assets/presentations/final/01-cover.png" alt="최종발표 01" width="100%" />

<img src="./assets/presentations/final/02-problem-definition.png" alt="최종발표 02" width="100%" />

<img src="./assets/presentations/final/03-market-competitor-analysis.png" alt="최종발표 03" width="100%" />

<img src="./assets/presentations/final/04-purpose-impact-goal.png" alt="최종발표 04" width="100%" />

<img src="./assets/presentations/final/05-service-progress.png" alt="최종발표 05" width="100%" />

<img src="./assets/presentations/final/06-system-architecture.png" alt="최종발표 06" width="100%" />

<img src="./assets/presentations/final/07-agentic-workflow.png" alt="최종발표 07" width="100%" />

<img src="./assets/presentations/final/08-demo-video.png" alt="최종발표 08" width="100%" />

<img src="./assets/presentations/final/09-troubleshooting-diff-api.png" alt="최종발표 09" width="100%" />

<img src="./assets/presentations/final/10-troubleshooting-chat-session.png" alt="최종발표 10" width="100%" />

<img src="./assets/presentations/final/11-troubleshooting-agent-log-streaming.png" alt="최종발표 11" width="100%" />

<img src="./assets/presentations/final/12-troubleshooting-base-path-custom-domain.png" alt="최종발표 12" width="100%" />

<img src="./assets/presentations/final/13-troubleshooting-human-error.png" alt="최종발표 13" width="100%" />

<img src="./assets/presentations/final/14-team-introduction.png" alt="최종발표 14" width="100%" />

<img src="./assets/presentations/final/15-roadmap-plan.png" alt="최종발표 15" width="100%" />

</details>

---

## Folder Structure

`.github` 레포지토리에 아래 구조로 업로드하면 조직 프로필 README에서 이미지가 바로 표시됩니다.

```text
.github/
└── profile/
    ├── README.md
    ├── docs/
    │   ├── README.md
    │   ├── 2026-1-midterm-presentation.pptx
    │   ├── 2026-1-midterm-presentation.pdf
    │   ├── 2026-1-final-presentation.pptx
    │   └── 2026-1-final-presentation.pdf
    └── assets/
        └── presentations/
            ├── midterm/
            │   ├── 01-cover.png
            │   ├── 02-overview.png
            │   ├── 03-system-operation.png
            │   ├── 04-system-diagram.png
            │   ├── 05-development-environment.png
            │   ├── 06-competitor-research.png
            │   ├── 07-technical-study.png
            │   ├── 08-ui-feature-list.png
            │   ├── 09-schedule-plan.png
            │   └── 10-etc.png
            └── final/
                ├── 01-cover.png
                ├── 02-problem-definition.png
                ├── 03-market-competitor-analysis.png
                ├── 04-purpose-impact-goal.png
                ├── 05-service-progress.png
                ├── 06-system-architecture.png
                ├── 07-agentic-workflow.png
                ├── 08-demo-video.png
                ├── 09-troubleshooting-diff-api.png
                ├── 10-troubleshooting-chat-session.png
                ├── 11-troubleshooting-agent-log-streaming.png
                ├── 12-troubleshooting-base-path-custom-domain.png
                ├── 13-troubleshooting-human-error.png
                ├── 14-team-introduction.png
                └── 15-roadmap-plan.png
```

---

## Image Path Guide

README에서 이미지를 보여줄 때는 아래처럼 작성하면 됩니다.

```md
![중간발표 표지](./assets/presentations/midterm/01-cover.png)
![최종발표 표지](./assets/presentations/final/01-cover.png)
![시스템 아키텍처](./assets/presentations/final/06-system-architecture.png)
![Agentic Workflow](./assets/presentations/final/07-agentic-workflow.png)
```

---

## Team

| Name | Role | Responsibility |
|---|---|---|
| 김인성 | PM / BE | 서비스 기획, 요구사항 정리, 기능 우선순위 관리, Project·Chat·DomainBinding·CloudConnection 모듈 개발 |
| 이운학 | Infra / BE | 인프라 세팅, Auth·User·Deployment 모듈 개발, Agentic Workflow 설계 및 개발 |
| 문채현 | FE | 프론트 정책 설정, 각종 API 연동, 미리보기 및 상태 화면 연동 |
| 김태우 | Design / FE | 서비스 화면 구조 설계, Figma 디자인, 퍼블리싱 |

<p align="center">
  <img src="./assets/presentations/final/14-team-introduction.png" alt="Team Introduction" width="100%" />
</p>

---

## Roadmap

<p align="center">
  <img src="./assets/presentations/final/15-roadmap-plan.png" alt="Roadmap" width="100%" />
</p>

### 여름방학 집중 개발

- 프론트 핵심 화면 고도화
- Agentic Workflow 안정화
- GitHub Pages 배포 흐름 보완
- Custom Domain 처리 안정화

### 2학기 개발 계획

- AWS/GCP 등 클라우드 인프라 관리 기능 구체화
- 서버 상태 확인 및 운영 수정 기능 확장
- 사용자 테스트 및 피드백 반영
- 예외 처리 및 보안 검증

---

## Vision

Qeploy는 누구나 아이디어를 실제 서비스 URL로 빠르게 연결할 수 있는 개발·배포 환경을 제공합니다.

```text
말로 설명하면, 서비스가 완성되고 배포된다.
```

Qeploy의 최종 방향은 자연어 기반 Agent가 웹서비스의 생성, 수정, 검증, 배포, 도메인 연결, 클라우드 운영까지 함께 처리하는 것입니다.
