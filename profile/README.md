<p align="center">
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="./assets/brand/qeploy/Qeploy-Logo-Dark.svg" />
    <img src="./assets/brand/qeploy/Qeploy-Logo-Primary.svg" alt="Qeploy" width="320" />
  </picture>
</p>

<p align="center">
  <strong>대화형 AI 웹서비스 빌드·배포 플랫폼</strong><br />
  자연어로 웹 프로젝트를 만들고, 실제 실행 환경에서 확인한 뒤, 내 GitHub·AWS에 배포하고 도메인까지 연결합니다.
</p>

<p align="center">
  <a href="https://qeploy.com">qeploy.com</a> ·
  <a href="https://www.youtube.com/watch?v=M1GR5Z2Jh-o">시연 영상</a> ·
  <a href="./docs/semester2-presentation.pdf">발표 자료 (PDF)</a> ·
  <a href="https://www.npmjs.com/package/@qeploy/cli">@qeploy/cli</a>
</p>

<br />

<p align="center">
  <img src="./assets/presentations/semester2/01-cover.png" alt="Qeploy — 대화형 AI 웹서비스 빌드·배포" width="100%" />
</p>

## Qeploy가 푸는 문제

AI로 웹 초안을 만드는 일은 쉬워졌습니다. 하지만 그 초안이 실제로 공개되어 운영되기까지는 여전히 개발 지식이 필요합니다.

- **코드 생성은 AI에 맡겨도, 배포·운영은 아직 사람이 합니다.** Stack Overflow Developer Survey 2026에서 익숙한 영역의 코드 생성에 AI를 쓰는 비율은 69.3%였고, 배포·운영·문제 해결에 쓰는 비율은 19.9%였습니다.
- **AI 결과를 믿는 조건은 검증입니다.** 같은 조사에서 응답자의 48.0%가 "쉽게 검증할 수 있을 때" AI를 신뢰한다고 답했습니다.
- **웹 초안 다음에 오는 일이 많습니다.** 코드 확인, 실행과 변경 비교, Git·빌드·호스팅, DNS·HTTPS, 상태 확인과 재배포까지 이어집니다.

Qeploy는 이 과정을 하나의 대화로 묶습니다. 사용자는 결과를 **미리보기 → 변경 내역 → 승인**의 순서로 검증하고, 배포는 **사용자 본인의 GitHub와 AWS 계정**에 합니다.

```text
자연어 요청 → AI Agent 작업 → Docker 미리보기 → 변경 확인·승인 → GitHub 커밋·PR → 배포 → 도메인 연결 → 운영
```

| | 관리형 환경 활용 | 사용자 자원 연결 |
| --- | --- | --- |
| **서비스 생성·공개 흐름 중심** | Lovable, Replit | **Qeploy** (내 GitHub · AWS) |
| **코드·저장소 작업 중심** | | Cursor |

---

## 시연 영상

<a href="https://www.youtube.com/watch?v=M1GR5Z2Jh-o">
  <img src="https://img.youtube.com/vi/M1GR5Z2Jh-o/maxresdefault.jpg" alt="Qeploy 시연 영상" width="720" />
</a>

- **2026 한이음 공모전 시연 (1분 26초)**: https://www.youtube.com/watch?v=M1GR5Z2Jh-o — 생성·수정 → 미리보기 → 승인·배포
- 1학기 시연 영상: https://youtu.be/40x44EsGruY

---

## 기능

✅ 구현됨 · 🟡 일부 구현 · ⬜ 계획

### 대화로 만들고 고치기

| 기능 | 상태 | 내용 |
| --- | :---: | --- |
| AI Workspace | ✅ | 자연어로 생성·수정·배포·도메인·인프라 작업 요청. 진행 상태와 로그를 실시간(SSE)으로 표시 |
| 작업 판단 Agent | ✅ | Decision Agent가 요청을 Code·Deploy·Domain·Infra Agent로 나눠 보냄. 정보가 부족하면 먼저 되묻고, 답을 받으면 작업을 이어감 |
| 개인 AI 키 (BYOK) | ✅ | 사용자 본인의 Anthropic·OpenAI 등 공식 API 키로 실행. Claude Code·Codex 실행 모드 지원. 서버 운영자 키로 대신 실행하지 않음 |
| 템플릿으로 시작 | ✅ | [qeploy-templates](https://github.com/Dvely/qeploy-templates) 카탈로그(랜딩·포트폴리오·쇼핑)에서 골라 시작 |
| GitHub 저장소 연동 | ✅ | GitHub App으로 저장소를 만들거나 연결. 요청 단위로 커밋하고 PR·merge·버전을 관리 |
| ZIP 업로드 가져오기 | ⬜ | 현재 제품 흐름에서 제외. 재설계 후 다시 검토 |

### 확인하고 승인하기

| 기능 | 상태 | 내용 |
| --- | :---: | --- |
| Docker 미리보기 | ✅ | 실제로 설치·빌드·실행한 결과를 확인. 정적 사이트와 백엔드·풀스택·DB를 포함한 앱 모두 지원 |
| 미리보기 격리 | ✅ | 비 root 실행, CPU·메모리·프로세스 수 제한, 호스트 포트 비노출, 소유권 확인 게이트웨이. 전용 내부 네트워크와 허용목록 프록시는 개발 서버에서 검증 중(기본 OFF) |
| 변경 내역 | ✅ | 요약과 상세 diff를 나눠 조회. 빌드 실패 시 원인 분석과 복구 |
| 승인 정책 | ✅ | 코드 변경·결과·배포·도메인·인프라 승인을 프로젝트마다 켜고 끔. 승인·거절 이력 보관 |

### 배포하고 운영하기

| 기능 | 상태 | 내용 |
| --- | :---: | --- |
| GitHub Pages 배포 | ✅ | 커스텀 도메인으로 다시 배포할 때도 경로를 맞춰 재빌드하고 기존 CNAME을 보존 |
| 사용자 AWS 배포 | ✅ | 정적 사이트는 S3 + CloudFront + ACM, 백엔드는 EC2, DB는 RDS 또는 Docker DB. 사용자 계정에 직접 프로비저닝 |
| 실패 복구 | ✅ | 배포가 실패하면 EC2·EIP 같은 자원을 먼저 회수하고 오류를 보고. 보고가 실패해도 상태 기록은 계속됨 |
| 도메인 연결 | ✅ | qeploy.com 무료 서브도메인과 커스텀 도메인, DNS 검증과 HTTPS |
| 환경변수·비밀값 | ✅ | 암호화해 저장하고 마스킹해 표시. 미리보기와 배포에 범위를 나눠 주입 |
| 서버 상태·비용 | 🟡 | 서버 상태 확인과 헬스 모니터링, 예상 비용·예산 상태 계산. 서버 사양 변경과 미사용 자원 정리 실행은 계획 |
| GCP 배포 | ⬜ | 계획 (현재는 AWS만 지원) |

### 내 코딩 에이전트에서 Qeploy 쓰기

| 기능 | 상태 | 내용 |
| --- | :---: | --- |
| MCP 서버 | ✅ | [`@qeploy/mcp`](https://www.npmjs.com/package/@qeploy/mcp) — Claude Code·Codex가 Qeploy를 도구로 호출 |
| CLI | ✅ | [`@qeploy/cli`](https://www.npmjs.com/package/@qeploy/cli) — `npx @qeploy/cli login` 후 터미널·CI에서 사용 |
| 개인 액세스 토큰 (PAT) | ✅ | 해시로 저장. 권한 범위와 만료를 지정하고, 쓰기 권한은 에이전트에 필요한 다섯 가지로 제한 |

---

## 시스템 구성

<p align="center">
  <img src="./assets/presentations/semester2/10-system-architecture.png" alt="시스템 구성" width="100%" />
</p>

<p align="center">
  <img src="./assets/presentations/semester2/11-agent-roles.png" alt="Agent 작업 분담" width="100%" />
</p>

| Agent | 역할 | 사용자 확인 |
| --- | --- | --- |
| Decision Agent | 요청과 프로젝트 상태를 보고 작업을 판단. 정보가 부족하면 추가 질문 | 답변 후 작업 재개 |
| Code | 생성·수정 | 실행 확인 · 결과 승인 |
| Deploy | GitHub Pages · AWS | 배포 승인 · 공개 |
| Domain | DNS · HTTPS | 레코드 · 인증서 |
| Infra | 서버 · DB | 생성 · 자원 정리 |

---

## 성능·안정성 개선

모두 같은 조건에서 개선 전과 후를 실측한 값입니다.

| 항목 | 개선 전 | 개선 후 | 방법 |
| --- | ---: | ---: | --- |
| 유휴 상태 DB 쿼리 | 1,904회/분 | 74회/분 (**−96.1%**) | 큐가 비면 조회 간격을 1초에서 최대 30초까지 늘림. 새 작업이 저장되면 워커를 깨워 1초 안에 처리 ([PR #350](https://github.com/Dvely/Dvely_springboot/pull/350)) |
| 변경 목록 조회 | 97.5 MB · 488 ms | 20.8 KB · 71 ms | 필요한 필드만 조회, 커서 페이지네이션 |
| 동시 SSE 스트림 | 2 / 5 | 5 / 5 | 이벤트 알림, 가상 스레드. 스트림당 SELECT 177 → 10회/분 |
| 초기 JavaScript (gzip) | 344.31 KB | 296.82 KB (**−13.8%**) | Markdown 지연 로딩, 목록 캐시 복원 |
| 실패 경로 검증 | | 테스트 1,808개 · 실패 0 | 실제 소켓 RST로 연결 종료를 재현하고, 복구 순서가 바뀌면 테스트가 실패하도록 함 |

---

## 성과

| 구분 | 내용 |
| --- | --- |
| 학술 | **ACK 2026 (한국정보처리학회 추계학술발표대회) 학부생 논문 게재** — 「공유 출구 프록시를 이용한 AI 생성 웹 애플리케이션 프리뷰의 세션별 네트워크 격리」. 2026.11 세종대학교 포스터 발표 |
| 공모전 | **2026 한이음 드림업 공모전** — 개설심의 선정, 중간평가 완료, 장려상 평가 대상 |
| 대외 공개 | **Wanted AI Championship 2026** 출품 — 「Qeploy: 대화로 완성하는 웹페이지 제작부터 배포까지 이어지는 서비스」 |
| 검색 노출 | qeploy.com SEO·GEO 최적화, Google Search Console·네이버 서치어드바이저 등록 |
| 배포 | MCP 서버·CLI npm 공개 배포 (`@qeploy/client` · `@qeploy/mcp` · `@qeploy/cli`) |

---

## 저장소

| 저장소 | 설명 |
| --- | --- |
| [Dvely_FE](https://github.com/Dvely/Dvely_FE) | 프론트엔드. React 19 · TypeScript · Vite · TanStack Query · Zustand · Tailwind CSS |
| [Dvely_springboot](https://github.com/Dvely/Dvely_springboot) | 백엔드. Java 25 · Spring Boot 4 · MySQL 8 · Flyway. Agent·미리보기·배포·도메인·인프라 처리, MCP 서버와 CLI(`agent-tools/`) 포함 |
| [qeploy-templates](https://github.com/Dvely/qeploy-templates) | 시작 템플릿 카탈로그. GitHub Pages로 카탈로그·데모·소스를 발행 |
| [.github](https://github.com/Dvely/.github) | 조직 프로필 README, 발표 자료, 브랜드 자산 |

## 기술 스택

| 영역 | 스택 |
| --- | --- |
| Frontend | React 19, TypeScript, Vite, TanStack Query, Zustand, Tailwind CSS |
| Backend | Java 25, Spring Boot 4, Spring Data JPA, MySQL 8, Flyway |
| 실행·미리보기 | Docker (docker-java), Nginx, PM2 |
| 외부 연동 | GitHub App · GitHub Pages, AWS (EC2 · S3 · CloudFront · ACM · RDS · SSM), Cloudflare DNS |
| AI | 사용자 본인 키(BYOK) — Anthropic · OpenAI 등, Claude Code · Codex 실행 모드 |
| 에이전트 연동 | MCP (stdio), Node.js CLI, 개인 액세스 토큰 |
| 운영 | AWS EC2, GitHub Actions (develop → 개발 서버, main → 운영 서버) |
| 협업 | GitHub, Figma, Notion |

---

## 팀 Dvely

<p>
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="./assets/brand/dvely/Dvely-Logo-Dark.svg" />
    <img src="./assets/brand/dvely/Dvely-Logo-Primary.svg" alt="Dvely" width="200" />
  </picture>
</p>

| 이름 | 역할 | 담당 |
| --- | --- | --- |
| 김인성 | 팀장 · PM · BE | 프로젝트 관리, 백엔드 — Project · Chat · DomainBinding · CloudConnection |
| 이운학 | BE · Infra | 백엔드, 인프라 — Auth · User · Deployment, Agentic Workflow 설계·개발 |
| 문채현 | FE · API | 프론트엔드, API 연동 — 미리보기·상태 화면 연동 |
| 김태우 | FE · Design | 프론트엔드, 디자인 — 화면 구조 설계, Figma 디자인, 퍼블리싱 |

---

## 다음 단계

| 시기 | 상태 | 내용 |
| --- | --- | --- |
| 2026.09 | 완료 | 미리보기 · GitHub Pages 배포, AWS 배포 · 도메인 연결 |
| 2026.10 | 완료 | 실패 복구, 오류 경로 검증 |
| 2026.10 | 구현·등록 | SEO·GEO 기반, Google·네이버 등록 |
| 다음 | 계획 | 검색·AI 노출(색인·검색 유입), 배포 검증(회귀 테스트·사용자 첫 배포 완주), 특허 검토(선행기술 비교) |

다음 사용자 검증에서는 **첫 URL 받기 → 메뉴 수정 → 재배포**를 끝까지 해 보게 합니다. 이때 소요 시간, 도움 요청 횟수, 중단한 단계, 재배포 성공 여부를 측정합니다.

---

## 발표 자료

| 발표 | 자료 |
| --- | --- |
| **2학기 발표** (31장) | [PDF](./docs/semester2-presentation.pdf) · 아래 슬라이드 이미지 |
| 1학기 최종발표 (15장) | 아래 슬라이드 이미지 |
| 1학기 중간발표 · 프로젝트 제안서 (10장) | 아래 슬라이드 이미지 |

<details>
<summary><strong>2학기 발표 슬라이드 보기 (31장)</strong></summary>

| | |
| --- | --- |
| <strong>01. 표지</strong><br><img src="./assets/presentations/semester2/01-cover.png" width="420"> | <strong>02. 목차</strong><br><img src="./assets/presentations/semester2/02-contents.png" width="420"> |
| <strong>03. 현상과 문제</strong><br><img src="./assets/presentations/semester2/03-section-problem.png" width="420"> | <strong>04. AI 활용 현황</strong><br><img src="./assets/presentations/semester2/04-ai-usage.png" width="420"> |
| <strong>05. 신뢰의 조건: 검증</strong><br><img src="./assets/presentations/semester2/05-trust-verification.png" width="420"> | <strong>06. 웹 초안 이후의 작업</strong><br><img src="./assets/presentations/semester2/06-after-web-draft.png" width="420"> |
| <strong>07. 서비스 포지셔닝</strong><br><img src="./assets/presentations/semester2/07-positioning.png" width="420"> | <strong>08. 서비스와 기술 구현</strong><br><img src="./assets/presentations/semester2/08-section-service.png" width="420"> |
| <strong>09. 서비스 시연</strong><br><a href="https://www.youtube.com/watch?v=M1GR5Z2Jh-o"><img src="./assets/presentations/semester2/09-demo-video.png" width="420"></a> | <strong>10. 시스템 구성</strong><br><img src="./assets/presentations/semester2/10-system-architecture.png" width="420"> |
| <strong>11. Agent 작업 분담</strong><br><img src="./assets/presentations/semester2/11-agent-roles.png" width="420"> | <strong>12. 미리보기 격리</strong><br><img src="./assets/presentations/semester2/12-preview-isolation.png" width="420"> |
| <strong>13. 인증정보의 실행 범위</strong><br><img src="./assets/presentations/semester2/13-credential-scope.png" width="420"> | <strong>14. 실패 복구 순서</strong><br><img src="./assets/presentations/semester2/14-failure-recovery.png" width="420"> |
| <strong>15. 사용 흐름에서 발견한 문제</strong><br><img src="./assets/presentations/semester2/15-usage-flow-issues.png" width="420"> | <strong>16. 유휴 DB 조회 감소</strong><br><img src="./assets/presentations/semester2/16-idle-db-query.png" width="420"> |
| <strong>17. 변경 목록 조회 경량화</strong><br><img src="./assets/presentations/semester2/17-change-list-query.png" width="420"> | <strong>18. 동시 스트림 개선</strong><br><img src="./assets/presentations/semester2/18-concurrent-streams.png" width="420"> |
| <strong>19. 초기 화면 경량화</strong><br><img src="./assets/presentations/semester2/19-initial-bundle.png" width="420"> | <strong>20. 실패 경로 검증</strong><br><img src="./assets/presentations/semester2/20-failure-path-tests.png" width="420"> |
| <strong>21. 특허 검토 아이디어</strong><br><img src="./assets/presentations/semester2/21-patent-idea.png" width="420"> | <strong>22. 검증과 실행 계획</strong><br><img src="./assets/presentations/semester2/22-section-validation.png" width="420"> |
| <strong>23. 첫 배포 완주 검증 계획</strong><br><img src="./assets/presentations/semester2/23-first-deploy-plan.png" width="420"> | <strong>24. 검색 등록과 문서 준비</strong><br><img src="./assets/presentations/semester2/24-seo-geo.png" width="420"> |
| <strong>25. 팀 Dvely</strong><br><img src="./assets/presentations/semester2/25-team.png" width="420"> | <strong>26. 협업 기록</strong><br><img src="./assets/presentations/semester2/26-collaboration.png" width="420"> |
| <strong>27. 논문 정리·투고</strong><br><img src="./assets/presentations/semester2/27-paper-ack2026.png" width="420"> | <strong>28. 한이음 제출 기록</strong><br><img src="./assets/presentations/semester2/28-hanium-dreamup.png" width="420"> |
| <strong>29. 서비스 대외 공개</strong><br><img src="./assets/presentations/semester2/29-wanted-ai-championship.png" width="420"> | <strong>30. 중간발표 이후와 다음 단계</strong><br><img src="./assets/presentations/semester2/30-next-steps.png" width="420"> |
| <strong>31. 마무리</strong><br><img src="./assets/presentations/semester2/31-closing.png" width="420"> | |

</details>

<details>
<summary>1학기 발표 슬라이드 보기 (중간발표 10장 · 최종발표 15장)</summary>

| 중간발표 (프로젝트 제안서) | 최종발표 |
| --- | --- |
| <strong>01. 표지</strong><br><img src="./assets/presentations/midterm/01-cover.png" width="420"> | <strong>01. 표지</strong><br><img src="./assets/presentations/final/01-cover.png" width="420"> |
| <strong>02. 개요</strong><br><img src="./assets/presentations/midterm/02-overview.png" width="420"> | <strong>02. 문제정의</strong><br><img src="./assets/presentations/final/02-problem-definition.png" width="420"> |
| <strong>03. 시스템 구성 및 동작</strong><br><img src="./assets/presentations/midterm/03-system-operation.png" width="420"> | <strong>03. 시장조사 · 경쟁사분석</strong><br><img src="./assets/presentations/final/03-market-competitor-analysis.png" width="420"> |
| <strong>04. 시스템 구성도</strong><br><img src="./assets/presentations/midterm/04-system-diagram.png" width="420"> | <strong>04. 기획의도 · 기대효과 · 최종목표</strong><br><img src="./assets/presentations/final/04-purpose-impact-goal.png" width="420"> |
| <strong>05. 개발환경</strong><br><img src="./assets/presentations/midterm/05-development-environment.png" width="420"> | <strong>05. 서비스소개 · 진행도</strong><br><img src="./assets/presentations/final/05-service-progress.png" width="420"> |
| <strong>06. 유사시스템 조사</strong><br><img src="./assets/presentations/midterm/06-competitor-research.png" width="420"> | <strong>06. System Architecture</strong><br><img src="./assets/presentations/final/06-system-architecture.png" width="420"> |
| <strong>07. 기술탐구</strong><br><img src="./assets/presentations/midterm/07-technical-study.png" width="420"> | <strong>07. Agentic Workflow</strong><br><img src="./assets/presentations/final/07-agentic-workflow.png" width="420"> |
| <strong>08. 화면 UI · 기능 목록</strong><br><img src="./assets/presentations/midterm/08-ui-feature-list.png" width="420"> | <strong>08. 시연영상</strong><br><img src="./assets/presentations/final/08-demo-video.png" width="420"> |
| <strong>09. 일정계획</strong><br><img src="./assets/presentations/midterm/09-schedule-plan.png" width="420"> | <strong>09. 트러블슈팅 · diff API 낭비</strong><br><img src="./assets/presentations/final/09-troubleshooting-diff-api.png" width="420"> |
| <strong>10. 기타</strong><br><img src="./assets/presentations/midterm/10-etc.png" width="420"> | <strong>10. 트러블슈팅 · chat 생성 방식</strong><br><img src="./assets/presentations/final/10-troubleshooting-chat-session.png" width="420"> |
| — | <strong>11. 트러블슈팅 · Agent 로그 스트리밍</strong><br><img src="./assets/presentations/final/11-troubleshooting-agent-log-streaming.png" width="420"> |
| — | <strong>12. 트러블슈팅 · base path / custom domain</strong><br><img src="./assets/presentations/final/12-troubleshooting-base-path-custom-domain.png" width="420"> |
| — | <strong>13. 트러블슈팅 · Human Error</strong><br><img src="./assets/presentations/final/13-troubleshooting-human-error.png" width="420"> |
| — | <strong>14. 팀 역할 및 소개</strong><br><img src="./assets/presentations/final/14-team-introduction.png" width="420"> |
| — | <strong>15. 일정 및 계획</strong><br><img src="./assets/presentations/final/15-roadmap-plan.png" width="420"> |

</details>
