---
layout: chapter
title: "참고 자료 및 확장 방향"
short_title: "참고 자료"
description: "Copilot Studio 공식 문서, Power Automate 연계 문서, 외부 연동 참고 자료, 향후 확장 아키텍처 방향을 정리합니다."
order: 8
---

## Copilot Studio 공식 문서

Microsoft가 제공하는 공식 문서 및 학습 리소스입니다.

### 핵심 공식 문서

| 리소스 | 설명 | 링크 |
|---|---|---|
| **Copilot Studio 공식 문서** | 제품 전체 문서 | [learn.microsoft.com/microsoft-copilot-studio](https://learn.microsoft.com/microsoft-copilot-studio/) |
| **Copilot Studio 시작 가이드** | 처음 사용자를 위한 퀵스타트 | [Get started](https://learn.microsoft.com/microsoft-copilot-studio/fundamentals-get-started) |
| **Agent 만들기** | Agent 생성 및 설정 가이드 | [Create agents](https://learn.microsoft.com/microsoft-copilot-studio/authoring-first-bot) |
| **Topics 작성** | Topic 설계 방법 상세 안내 | [Create topics](https://learn.microsoft.com/microsoft-copilot-studio/authoring-create-edit-topics) |
| **Knowledge 설정** | Knowledge 소스 연결 가이드 | [Knowledge sources](https://learn.microsoft.com/microsoft-copilot-studio/knowledge-copilot-studio) |
| **Actions 설정** | Action 연동 방법 | [Use actions](https://learn.microsoft.com/microsoft-copilot-studio/advanced-plugin-actions) |

### 학습 리소스

| 리소스 | 설명 |
|---|---|
| **Microsoft Learn 학습 경로** | Copilot Studio 관련 무료 온라인 교육 모듈 |
| **YouTube - Microsoft Mechanics** | 제품 데모 및 신기능 소개 영상 |
| **Copilot Studio 커뮤니티** | [Power Platform Community](https://powerusers.microsoft.com/) |
| **GitHub 샘플** | 공식 샘플 코드 및 템플릿 |

---

## Power Automate 연계 문서

Copilot Studio와 Power Automate를 연계할 때 참고할 문서입니다.

### 공식 문서

| 리소스 | 설명 | 링크 |
|---|---|---|
| **Power Automate 공식 문서** | 전체 제품 문서 | [learn.microsoft.com/power-automate](https://learn.microsoft.com/power-automate/) |
| **Copilot Studio에서 플로우 호출** | Studio ↔ Power Automate 연계 가이드 | [Call Power Automate flows](https://learn.microsoft.com/microsoft-copilot-studio/advanced-flow) |
| **커넥터 레퍼런스** | 모든 커넥터 목록 및 사용법 | [Connector reference](https://learn.microsoft.com/connectors/connector-reference/) |
| **커스텀 커넥터 만들기** | 자체 API를 커넥터로 등록하는 방법 | [Custom connectors](https://learn.microsoft.com/connectors/custom-connectors/) |

### 자주 사용되는 Power Automate 패턴

| 패턴 | 설명 | 활용 예 |
|---|---|---|
| **데이터 조회 후 반환** | 외부 시스템에서 데이터를 조회하여 Agent에 반환 | ERP 재고 조회, CRM 고객 조회 |
| **데이터 생성/수정** | 사용자 입력을 받아 외부 시스템에 기록 | 티켓 생성, 주문 등록 |
| **알림 발송** | 특정 이벤트 발생 시 알림 전송 | 승인 요청, 장애 알림 |
| **승인 워크플로우** | 다단계 승인 프로세스 | 구매 결재, 휴가 승인 |
| **파일 처리** | 파일 생성, 변환, 저장 | 보고서 PDF 생성, 문서 변환 |

---

## 외부 시스템 연동 참고 자료

사내 및 대외 시스템과의 연동에 참고할 수 있는 자료입니다.

### Microsoft 관련 연동

| 시스템 | 연동 방식 | 참고 문서 |
|---|---|---|
| **Microsoft Graph API** | 표준 커넥터 / HTTP | [Graph API 문서](https://learn.microsoft.com/graph/) |
| **SharePoint REST API** | SharePoint 커넥터 | [SharePoint API](https://learn.microsoft.com/sharepoint/dev/) |
| **Dataverse Web API** | Dataverse 커넥터 | [Dataverse API](https://learn.microsoft.com/power-apps/developer/data-platform/webapi/overview) |
| **Azure AI Services** | HTTP / 커스텀 커넥터 | [Azure AI 문서](https://learn.microsoft.com/azure/ai-services/) |

### 외부 SaaS 연동

| 시스템 | 연동 방식 | 비고 |
|---|---|---|
| **ServiceNow** | 표준 커넥터 (프리미엄) | IT 헬프데스크 티켓 관리 |
| **Salesforce** | 표준 커넥터 (프리미엄) | CRM 데이터 연동 |
| **SAP** | 커스텀 커넥터 / SAP 커넥터 | ERP 연동 |
| **Slack** | 표준 커넥터 | 알림 연동 (Teams 병행 시) |
| **Google Workspace** | 커스텀 커넥터 | 캘린더, 드라이브 연동 |

### API 연동 개발 도구

| 도구 | 용도 |
|---|---|
| **Postman** | API 테스트 및 디버깅 |
| **Swagger Editor** | OpenAPI 스펙 작성 및 검증 |
| **Azure API Management** | API 게이트웨이, 인증, 모니터링 |
| **On-premises Data Gateway** | 사내 온프레미스 시스템 연결 |

---

## 향후 확장 시 아키텍처 방향

Copilot Studio 기반 Agent를 시작점으로, 향후 조직의 AI 인프라를 확장할 때 고려할 수 있는 아키텍처 방향입니다.

### 확장 단계

```
Phase 1                Phase 2                Phase 3
┌──────────────┐      ┌──────────────┐      ┌──────────────┐
│ Copilot Studio│      │  Studio +    │      │  AI Platform │
│ 단독 운영     │  →   │  Azure 연동   │  →   │  통합 운영    │
│              │      │              │      │              │
│ • FAQ Agent  │      │ • 커스텀 RAG  │      │ • 멀티 Agent │
│ • 간단 조회   │      │ • Azure Fn   │      │ • AI 오케스트 │
│ • PA 연계    │      │ • AI Search  │      │ • 분석 파이프  │
└──────────────┘      └──────────────┘      └──────────────┘
```

### Phase 1: Copilot Studio 단독 운영

- Copilot Studio만으로 구현 가능한 Agent 배포
- Knowledge + Topics + Power Automate 기본 활용
- 사용자 피드백 수집 및 개선 사이클 구축

### Phase 2: Studio + Azure 연동

- **Azure AI Search**: 대규모 문서 검색을 위한 고급 RAG 파이프라인
- **Azure OpenAI Service**: GPT 모델을 직접 호출하는 고급 생성 시나리오
- **Azure Functions**: 복잡한 비즈니스 로직을 서버리스 함수로 분리
- **Azure Cosmos DB**: 대화 이력, 사용자 컨텍스트 영속 저장

### Phase 3: AI Platform 통합 운영

- **멀티 에이전트 오케스트레이션**: Semantic Kernel, AutoGen 등을 활용한 다중 Agent 협업
- **통합 AI 게이트웨이**: Azure API Management를 통한 AI 서비스 중앙 관리
- **MLOps 파이프라인**: 모델 성능 모니터링, A/B 테스트, 자동 재학습
- **데이터 분석 통합**: Agent 대화 데이터를 분석하여 비즈니스 인사이트 도출

### 확장 시 기술 스택 매핑

| 요구사항 | 기술 스택 |
|---|---|
| 대화 인터페이스 | Copilot Studio / Bot Framework |
| 생성형 AI | Azure OpenAI Service |
| 문서 검색 (RAG) | Azure AI Search + Embedding |
| 백엔드 로직 | Azure Functions / App Service |
| 데이터 저장 | Cosmos DB / SQL Database |
| 인증/보안 | Microsoft Entra ID / API Management |
| 모니터링 | Application Insights / Azure Monitor |
| CI/CD | Azure DevOps / GitHub Actions |

<div class="info-box tip">
<strong>💡 실무 팁</strong>
확장은 <strong>필요에 의해 점진적으로</strong> 진행하세요. "혹시 나중에 필요할까 봐" 미리 복잡한 아키텍처를 구축하면 오히려 운영 비용과 복잡도만 증가합니다. <strong>Phase 1에서 충분한 사용자 피드백</strong>을 수집한 후, 실제 한계에 부딪혔을 때 Phase 2로 확장하는 것이 가장 효율적입니다.
</div>

<div class="info-box note">
<strong>📌 최신 동향 체크</strong>
Microsoft는 Copilot Studio를 지속적으로 업데이트하고 있습니다. <a href="https://learn.microsoft.com/microsoft-copilot-studio/whats-new" target="_blank">What's new in Copilot Studio</a> 페이지에서 최신 기능과 변경사항을 주기적으로 확인하세요.
</div>
