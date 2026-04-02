---
layout: chapter
title: "Copilot Studio 개요 및 접속"
short_title: "개요 및 접속"
description: "Copilot Studio에 접속하는 방법, 필요한 라이선스와 과금 구조, 그리고 유사 서비스와의 차이를 실무 관점에서 설명합니다."
order: 1
icon: "🌐"
---

## Copilot Studio란?

Microsoft Copilot Studio는 **로우코드(Low-Code) 기반의 AI Agent 빌더**입니다. 코드를 작성하지 않고도 자연어 대화형 Agent를 만들고, 사내 데이터와 연결하며, 외부 시스템과 통합할 수 있습니다.

### 핵심 특징

- **그래픽 기반 편집기**: 드래그 앤 드롭 방식의 대화 흐름 디자이너
- **AI 기반 자연어 이해(NLU)**: 사용자 의도를 자동 파악하여 적절한 Topic으로 라우팅
- **Generative AI 내장**: Azure OpenAI GPT 모델 기반의 생성형 응답 기능 기본 탑재
- **다중 채널 배포**: Teams, 웹사이트, 모바일 앱, Facebook 등 다양한 채널 동시 지원
- **Power Platform 통합**: Power Automate, Dataverse, 표준/프리미엄 커넥터와 네이티브 연동
- **Microsoft 365 Copilot 확장**: 선언형 Agent를 통해 M365 Copilot의 기능을 확장 가능

### Agent vs Agent Flow

Copilot Studio에서는 두 가지 핵심 단위를 만들 수 있습니다.

| 구분 | Agent | Agent Flow |
|---|---|---|
| **역할** | 사용자와 대화하며 업무를 처리 | 반복 작업을 자동화하는 워크플로우 |
| **트리거** | 사용자 메시지 입력 | 수동 실행, 스케줄, 이벤트, 다른 Agent 호출 |
| **인터페이스** | 대화형 (채팅) | 비대화형 (백그라운드 실행) |
| **활용 예시** | FAQ 봇, IT 헬프데스크, 고객 응대 | 주문 처리, 데이터 동기화, 보고서 생성 |

<div class="info-box note">
<strong>📌 참고</strong>
Agent Flow는 Copilot Studio 내에서 네이티브로 생성되며, Power Automate 플로우와 유사하지만 <strong>Agent와의 통합에 최적화</strong>되어 있습니다. Agent가 대화 중 Agent Flow를 도구(tool)로 호출하고, 그 결과를 다시 대화에 활용할 수 있습니다.
</div>

---

## Copilot Studio 접속 방법

### 웹 앱 (기본)

| 항목 | 내용 |
|---|---|
| **접속 URL** | [https://copilotstudio.microsoft.com](https://copilotstudio.microsoft.com) |
| **데모 체험** | [https://copilotstudio.microsoft.com/tryit](https://copilotstudio.microsoft.com/tryit) |
| **지원 브라우저** | Chrome 91+, Firefox 89+, Safari 16.4+, Edge (최신 Chromium 기반) |
| **로그인 계정** | 조직의 Microsoft Entra ID(구 Azure AD) 계정 |

### Teams 앱

Copilot Studio는 **Teams 앱**으로도 사용할 수 있습니다. Teams 내에서 바로 Agent를 만들고 팀 내부에 배포할 수 있어 빠른 프로토타이핑에 유리합니다.

- Teams 앱 열기: [aka.ms/PVATeamsApp](https://aka.ms/PVATeamsApp)
- Teams 앱으로 만든 Agent는 **Teams 채널에만 배포 가능** (웹, 외부 채널 불가)
- Teams 앱은 **클래식 챗봇만 지원**하며, 최신 Agent 기능(Generative Orchestration 등)은 웹 앱에서만 사용 가능

<div class="info-box warning">
<strong>⚠️ 실무에서 자주 하는 실수</strong>
<ul>
<li><strong>개인 Microsoft 계정 (@outlook.com, @hotmail.com)</strong>으로는 접속할 수 없습니다. 반드시 <strong>조직 계정</strong>으로 로그인하세요.</li>
<li><strong>게스트 사용자(Guest User)</strong>는 Copilot Studio에 접근할 수 없습니다. 외부 협력업체 직원에게 Agent 편집 권한을 주려면 해당 사용자를 조직의 <strong>정규 멤버</strong>로 등록해야 합니다.</li>
<li>처음 접속 시 <strong>환경(Environment) 선택 화면</strong>이 나옵니다. 운영 환경과 개발 환경을 구분하여 사용하세요. 잘못된 환경에서 Agent를 만들면 나중에 이동이 어렵습니다.</li>
</ul>
</div>

---

## 접근 권한 및 라이선스 개요

Copilot Studio를 사용하려면 적절한 라이선스가 필요합니다. 라이선스 구조가 다소 복잡하므로 정확히 이해하는 것이 중요합니다.

### 라이선스 유형

| 라이선스 | 설명 | Agent 게시 가능 | 주요 대상 |
|---|---|---|---|
| **Microsoft 365 Copilot** | M365 Copilot 라이선스에 Copilot Studio 사용 권한 포함. M365 Copilot 내에서 Agent를 사용하면 Copilot Credit 소비 없음 | ✅ | Copilot 도입 조직 |
| **Copilot Studio 독립 라이선스** | Copilot Studio 전용. **테넌트 라이선스 + 사용자 라이선스** 모두 필요 | ✅ | Agent 전용 구축 조직 |
| **Teams 포함 플랜** | 일부 M365 구독에 포함. Teams 채널 전용, 제한된 기능 | ✅ (Teams만) | 내부 소규모 봇 |
| **평가판 (Trial)** | 무료 체험. Agent 생성 및 테스트 가능 | ❌ (게시 불가) | PoC / 테스트 용도 |

<div class="info-box warning">
<strong>⚠️ 반드시 알아야 할 포인트: 테넌트 라이선스 vs 사용자 라이선스</strong>
독립 라이선스는 <strong>두 가지를 모두 구매</strong>해야 합니다.
<ul>
<li><strong>Copilot Studio (테넌트 라이선스)</strong>: 조직 단위로 구매. 개별 사용자에게 할당하지 않음.</li>
<li><strong>Copilot Studio User License (사용자 라이선스)</strong>: Agent를 만들고 편집하는 각 사용자에게 할당.</li>
</ul>
M365 관리센터 > 청구 > 구독에서 이 두 라이선스가 모두 표시되는지 확인하세요. 하나만 있으면 동작하지 않습니다.
</div>

### 평가판(Trial) 상세

| 항목 | 내용 |
|---|---|
| **신청 방법** | [https://go.microsoft.com/fwlink/?LinkId=2107702](https://go.microsoft.com/fwlink/?LinkId=2107702) 에서 회사 이메일로 신청 |
| **사용 기간** | 최초 60일 → 만료 시 30일 연장 가능 |
| **Agent 유지** | 평가판 만료 후에도 Agent가 **90일간 유지** (편집·게시 불가, 기존 대화만 동작) |
| **게시(Publish)** | ❌ **불가** — 테스트 채팅 패널에서만 테스트 가능 |
| **Self-service 차단** | 조직의 IT 관리자가 `AllowAdHocSubscriptions` 설정으로 셀프 사인업을 차단할 수 있음 |

<div class="info-box tip">
<strong>💡 실무 팁: 평가판으로 PoC 진행 시</strong>
<ul>
<li>평가판에서는 Agent를 <strong>게시할 수 없으므로</strong>, 이해관계자에게 시연할 때는 <strong>테스트 채팅 패널을 화면 공유</strong>하거나 녹화하여 보여주세요.</li>
<li>평가판 개인 이메일(@outlook.com 등) 신청 시 "가입을 완료할 수 없습니다" 오류가 발생합니다. 반드시 <strong>회사/학교 계정</strong>을 사용하세요.</li>
<li>"Self-service 차단" 오류가 나오면 IT 관리자에게 평가판 사인업 허용을 요청해야 합니다.</li>
</ul>
</div>

### 권한 구조

Copilot Studio는 **Power Platform 환경(Environment)** 위에서 동작합니다.

```
테넌트 (Tenant)
  └── 환경 (Environment)  ← Agent가 여기에 속함
       ├── 보안 역할 (Security Role)
       ├── Agent 1
       ├── Agent 2
       └── ...
```

| 역할 | 할 수 있는 것 | 할 수 없는 것 |
|---|---|---|
| **테넌트 관리자** | 환경 생성/삭제, 라이선스 할당, DLP 정책 | - |
| **환경 관리자** | 사용자 관리, Agent 배포, 보안 설정 | 환경 생성/삭제 |
| **Maker (작성자)** | Agent 생성, Topics/Knowledge/Actions 편집 | 환경 설정, 사용자 관리 |
| **사용자 (End User)** | 배포된 Agent 이용 | Agent 편집 (별도 라이선스 불필요) |

<div class="info-box note">
<strong>📌 중요</strong>
Agent를 <strong>사용하는 최종 사용자</strong>에게는 별도 라이선스가 필요 없습니다. 게시된 Agent에 접근할 수 있는 사람이면 누구나 이용 가능합니다.
</div>

---

## 과금 구조: Copilot Credits

2025년 9월 1일부터 Copilot Studio의 과금 단위가 **"메시지(Messages)"에서 "Copilot Credits"**로 변경되었습니다. Agent가 수행하는 작업의 종류와 복잡도에 따라 소비되는 Credit이 다릅니다.

### Copilot Credit 소비 단가

| 기능 | 소비량 | M365 Copilot 사용자 |
|---|---|---|
| **Classic Answer** (사전 정의된 응답) | 1 Credit | 무료 |
| **Generative Answer** (생성형 응답) | 2 Credits | 무료 |
| **Agent Action** (트리거, 추론, 토픽 전환) | 5 Credits | 무료 |
| **Tenant Graph Grounding** (M365 Graph 기반 응답) | 10 Credits | 무료 |
| **Agent Flow Actions** (100 action 당) | 13 Credits | 무료 |
| **AI Tools (Basic)** (10 응답 당) | 1 Credit | 무료 |
| **AI Tools (Standard)** (10 응답 당) | 15 Credits | 무료 |
| **AI Tools (Premium, 추론 모델)** (10 응답 당) | 100 Credits | 무료 |

<div class="info-box warning">
<strong>⚠️ 과금 함정: 복합 Credit 소비</strong>
하나의 사용자 질문에 <strong>여러 기능이 동시에 소비</strong>될 수 있습니다. 예를 들어, Tenant Graph Grounding이 활성화된 Agent에서 Generative Answer를 생성하면 한 번의 응답에 <strong>10 + 2 = 12 Credits</strong>가 소비됩니다. 이를 모르고 배포하면 예상보다 빠르게 크레딧이 소진됩니다.
</div>

### 과금 방식

| 방식 | 설명 | 적합한 경우 |
|---|---|---|
| **선불 팩 (Prepaid Pack)** | 월 정액으로 Copilot Credit 구매. 미사용분은 이월 불가 | 사용량 예측 가능한 운영 환경 |
| **종량제 (Pay-as-you-go)** | Azure 구독 연결 후 실제 사용량만큼 청구 | PoC, 사용량 불규칙한 환경 |
| **사전 구매 (Pre-Purchase Plan)** | 1년 단위 선불 Credit 구매. Azure 포털에서 구매 | 대규모 운영, 비용 최적화 |

### 초과 사용(Overage) 정책

| 상황 | 동작 |
|---|---|
| 선불 팩 100% 소진 | 경고 알림. 아직 동작함. |
| 선불 팩 **125% 초과** | **Agent 비활성화**. 새 대화 불가. "This agent has reached its usage limit." 메시지 표시 |
| 복구 방법 | 추가 Credit 구매, 환경 간 Credit 재할당, 또는 Pay-as-you-go 연결 |

<div class="info-box tip">
<strong>💡 실무 팁: 비용 관리 전략</strong>
<ul>
<li>초과 사용 시 Agent가 <strong>자동으로 비활성화</strong>되므로, Power Platform 관리센터에서 <strong>월별 소비량을 정기적으로 모니터링</strong>하세요.</li>
<li><a href="https://microsoft.github.io/copilot-studio-estimator/" target="_blank">Microsoft Copilot Studio Agent Usage Estimator</a>를 활용하면 Agent 유형, 트래픽, Knowledge 소스 등을 기반으로 예상 Credit 소비량을 미리 산출할 수 있습니다.</li>
<li><strong>M365 Copilot 라이선스 사용자</strong>는 Teams/SharePoint/Copilot Chat에서 Agent를 사용할 때 Credit이 차감되지 않습니다. M365 Copilot이 이미 도입된 조직이라면 이 점을 적극 활용하세요.</li>
<li>개별 Agent 단위로 <strong>월별 Credit 사용 한도</strong>를 설정할 수 있습니다. Power Platform 관리센터 > 라이선싱 > Copilot Studio > Manage Agents에서 설정하세요.</li>
</ul>
</div>

### 과금 시뮬레이션 예시

**시나리오: 고객 지원 Agent (웹사이트 배포)**

| 항목 | 설정 |
|---|---|
| 하루 평균 이용자 | 900명 |
| 이용자당 Classic Answer | 4건 |
| 이용자당 Generative Answer | 2건 |

```
일일 소비량 = [(4 × 1) + (2 × 2)] × 900 = 7,200 Credits/일
월간 소비량 ≈ 7,200 × 30 = 216,000 Credits/월
```

**시나리오: 사내 영업 성과 Agent (M365 Copilot Chat 내 배포)**

| 항목 | 설정 |
|---|---|
| M365 Copilot 라이선스 사용자 | 50명 (무료) |
| 비라이선스 사용자 | 100명 |
| 이용자당 Generative Answer | 4건 |
| 이용자당 Tenant Graph Grounding | 4건 |

```
일일 소비량 = [(4 × 2) + (4 × 10)] × 100명(비라이선스만) = 4,800 Credits/일
※ M365 Copilot 라이선스 50명은 무료이므로 계산에서 제외
```

---

## Quotas & Limits (사용 한도)

공식 문서에서 잘 드러나지 않지만, 실제 운영에 큰 영향을 미치는 제한사항들입니다.

### 요청 속도 제한 (Rate Limits)

| 환경 유형 | 분당 요청(RPM) | 시간당 요청(RPH) |
|---|---|---|
| 선불 팩 1~10개 | 50 | 1,000 |
| 선불 팩 11~50개 | 80 | 1,600 |
| 선불 팩 51~150개 | 100 | 2,000 |
| **평가판 / 개발자 환경** | **10** | **200** |
| Pay-as-you-go | 100 | 2,000 |
| M365 Copilot 사용자 | 100 | 2,000 |

<div class="info-box warning">
<strong>⚠️ 평가판 환경의 속도 제한</strong>
평가판/개발자 환경은 <strong>분당 10건, 시간당 200건</strong>으로 매우 제한적입니다. PoC에서 여러 사람이 동시 테스트하면 <strong>"failure notice"</strong> 메시지가 나타나면서 응답이 차단될 수 있습니다. 데모 시연 전 반드시 확인하세요.
</div>

### 주요 제한사항 정리

| 항목 | 제한 |
|---|---|
| Agent Instructions (지침) | 8,000자 |
| Topic 수 | 환경당 Agent별 1,000개 |
| 트리거 문구 | Topic당 200개 |
| Skill 수 | Agent당 100개 |
| 파일 업로드 크기 | 512 MB/파일 |
| 파일 업로드 수 | 500개 (SharePoint 제외) |
| 세션 수 | 무제한 (단, 사용자당 24시간 내 10세션 제한) |
| SharePoint 파일 크기 (M365 Copilot 없을 때) | **7 MB** 이하만 Generative Answers에 사용 가능 |
| SharePoint 파일 크기 (M365 Copilot 있을 때) | 200 MB까지 지원 |
| SharePoint 목록 조회 | 첫 2,048행까지만 반환 |

<div class="info-box tip">
<strong>💡 실무에서 자주 겪는 함정들</strong>
<ul>
<li><strong>SharePoint 7MB 제한</strong>: M365 Copilot 라이선스가 없는 테넌트에서 SharePoint Knowledge를 연결하면, 7MB 이상 파일은 <strong>조용히 무시</strong>됩니다. 에러 없이 "응답을 찾을 수 없다"고 나오므로 원인 파악이 어렵습니다.</li>
<li><strong>클래식 ASPX 페이지</strong>: SharePoint의 모던 페이지만 지원됩니다. 클래식 ASPX 페이지 콘텐츠는 Knowledge 검색 대상에서 제외됩니다.</li>
<li><strong>SharePoint 파일명 &amp; 기호</strong>: 문서나 폴더 이름에 <strong>"&amp;" 기호</strong>가 포함되면 Knowledge 인덱싱이 실패합니다.</li>
<li><strong>민감도 레이블</strong>: "기밀(Confidential)" 또는 "극비(Highly Confidential)" 민감도 레이블이 적용되었거나 암호 보호된 문서는 인덱싱 <strong>자체가 불가</strong>합니다. 상태는 "Ready"로 표시되지만 실제로는 응답 생성에 사용되지 않습니다.</li>
<li><strong>동기화 주기</strong>: SharePoint/OneDrive Knowledge 소스의 동기화 주기가 4~6시간입니다. 문서를 업데이트해도 즉시 반영되지 않습니다.</li>
</ul>
</div>

---

## Copilot Chat / App Builder / Copilot Studio 차이

Microsoft는 다양한 AI/자동화 도구를 제공하고 있어, 각 도구의 역할과 차이를 이해하는 것이 중요합니다.

| 구분 | Copilot Chat (BizChat) | App Builder | Copilot Studio |
|---|---|---|---|
| **핵심 목적** | 일상 업무 보조 (검색, 요약, 작성) | 데이터 기반 업무 앱 빌드 | 대화형 AI Agent 구축 |
| **사용 대상** | 최종 사용자 (직원) | 시민 개발자 / 현업 | 시민 개발자 / 개발자 |
| **인터페이스** | 채팅 (M365 앱 내 통합) | 앱 화면 (폼, 테이블, 갤러리) | 대화 흐름 디자이너 + 채팅 |
| **주요 기능** | 문서 요약, 이메일 작성, 질의응답 | CRUD 앱 빌드, 데이터 시각화 | 토픽 설계, Knowledge, Action, Agent Flow |
| **데이터 연결** | M365 Graph 기반 (자동) | Dataverse, SharePoint 등 | 다양한 커넥터 + REST API + MCP |
| **커스터마이징** | 제한적 (프롬프트 수준, 선언형 Agent) | 앱 레벨 커스터마이징 | Agent 로직 전체 제어 (Topics, Actions, Instructions) |
| **배포 대상** | M365 앱 내 자동 통합 | Teams, 웹 | Teams, 웹, 커스텀 채널, Direct Line |
| **과금** | M365 Copilot 라이선스에 포함 | Power Apps 라이선스 | Copilot Credits 기반 |

### 자주 혼동되는 포인트

#### "Copilot Chat에서도 Agent를 만들 수 있다던데?"

맞습니다. M365 Copilot Chat에서 **선언형 에이전트(Declarative Agent)**를 만들 수 있습니다. 하지만 이것은 Copilot Studio의 Agent와 다릅니다.

| | 선언형 Agent (Copilot Chat) | Custom Agent (Copilot Studio) |
|---|---|---|
| **편집 도구** | Agent Builder (간단 UI) | Copilot Studio (전체 편집기) |
| **로직 제어** | Instructions + Knowledge | Topics + Actions + Knowledge + Agent Flow |
| **외부 연동** | 제한적 (Graph 커넥터 수준) | 전체 Power Platform 커넥터 + HTTP + MCP |
| **배포** | M365 Copilot 내부만 | Teams, 웹, 외부 채널 |
| **복잡한 분기 처리** | 불가 | 가능 (조건 노드, Topic 리다이렉트) |

#### 판단 기준: 언제 어떤 도구를 선택할까?

```
사내 직원이 문서를 빠르게 찾고 요약?     → Copilot Chat
현업에서 간단한 데이터 관리 앱 필요?      → App Builder
자연어 대화로 업무를 처리하는 Agent?      → Copilot Studio
M365 Copilot 확장 (간단한 추가 지침)?    → 선언형 Agent (Agent Builder)
M365 Copilot 확장 (복잡한 로직 + 외부 API)? → Copilot Studio
```

<div class="info-box tip">
<strong>💡 실무 팁</strong>
이 도구들은 경쟁 관계가 아니라 <strong>보완 관계</strong>입니다. 실제로 많은 조직에서 다음과 같은 조합으로 사용합니다:
<ul>
<li><strong>Copilot Chat (기본)</strong> → 모든 직원이 일상적 질의에 사용</li>
<li><strong>선언형 Agent</strong> → 특정 업무 도메인(HR, 법무 등)에 특화된 Copilot 확장</li>
<li><strong>Copilot Studio Agent</strong> → 외부 시스템 연동이 필요한 복잡한 업무 자동화</li>
<li><strong>App Builder</strong> → 데이터 입력/조회가 필요한 구조화된 업무용 앱</li>
</ul>
</div>

---

## 접속 후 첫 화면: 환경(Environment) 이해

Copilot Studio에 처음 접속하면 **환경(Environment)**을 선택해야 합니다. 이 개념을 이해하지 못하면 나중에 Agent를 잘못된 환경에 만들어 이동이 어려운 상황에 처할 수 있습니다.

### 환경이란?

Power Platform 환경은 Agent, 데이터, 커넥터 등이 저장되는 **격리된 컨테이너**입니다.

| 환경 유형 | 용도 | 특징 |
|---|---|---|
| **기본 환경 (Default)** | 테넌트 최초 생성 시 자동 생성 | 모든 사용자 접근 가능. 프로덕션에 부적합 |
| **개발자 환경 (Developer)** | 개인 개발/테스트 | 무료. 제한된 Quota (RPM 10) |
| **샌드박스 환경 (Sandbox)** | 검증/테스트 | 리셋 가능. 프로덕션 복사본 생성 가능 |
| **프로덕션 환경 (Production)** | 실 서비스 운영 | 백업, 복구, DLP 정책 적용 |

<div class="info-box warning">
<strong>⚠️ 흔한 실수: 기본 환경에 Agent 생성</strong>
처음 접속하면 자동으로 <strong>"기본 환경(Default)"</strong>이 선택됩니다. 여기에 Agent를 만들면:
<ul>
<li>조직의 모든 사용자가 해당 Agent를 볼 수 있습니다 (격리 불가)</li>
<li>DLP(데이터 손실 방지) 정책이 갑자기 적용되면 Agent가 동작을 멈출 수 있습니다</li>
<li>다른 환경으로 이동이 <strong>간단하지 않습니다</strong> (솔루션 내보내기/가져오기 필요)</li>
</ul>
운영용 Agent는 반드시 <strong>별도 프로덕션 환경</strong>을 만들어서 사용하세요.
</div>
