---
layout: chapter
title: "외부(사내/대외) 시스템 연동 방식"
short_title: "외부 시스템 연동"
description: "Power Automate 연계, 표준 커넥터, HTTP API 연동, 인증 방식 등 Copilot Studio의 외부 시스템 통합 전략을 안내합니다."
order: 4
icon: "🔗"
---

## Power Automate 연계

**Power Automate**는 Copilot Studio와 가장 긴밀하게 연동되는 자동화 플랫폼입니다. Agent의 대화 흐름 중 복잡한 비즈니스 로직이나 다단계 처리를 Power Automate 플로우로 위임할 수 있습니다.

### 연계 방식

1. **Copilot Studio에서 직접 호출**
   - Topic 내 Action 노드에서 Power Automate 플로우를 직접 선택·호출합니다.
   - 입력 파라미터를 전달하고, 플로우 실행 결과를 변수로 받아 대화에 활용합니다.

2. **Copilot Studio 전용 트리거 사용**
   - Power Automate에서 "Copilot Studio에서 플로우 실행" 트리거를 사용하면, Copilot Studio에서 해당 플로우를 Action으로 인식합니다.

### Power Automate 연계 시 고려사항

| 항목 | 설명 |
|---|---|
| **실행 시간 제한** | Copilot Studio에서 호출하는 플로우는 **100초 이내** 완료 권장 |
| **입출력 크기** | 전달 가능한 데이터 크기에 제한이 있으므로 대용량 데이터 전달은 지양 |
| **에러 핸들링** | 플로우 실패 시 Copilot Studio로 에러 정보를 반환하여 사용자에게 안내 |
| **라이선스** | Power Automate 프리미엄 커넥터 사용 시 별도 라이선스 필요 |

<div class="info-box tip">
<strong>💡 실무 팁</strong>
Power Automate 플로우를 만들 때, <strong>"Copilot Studio에서만 호출되는 전용 플로우"</strong>와 <strong>"범용 자동화 플로우"</strong>를 분리해서 관리하면 유지보수가 편리합니다.
</div>

---

## 표준 커넥터 활용

Copilot Studio는 Power Platform의 **표준 커넥터(Standard Connector)**를 통해 다양한 Microsoft 및 써드파티 서비스에 직접 연결할 수 있습니다.

### 자주 사용되는 표준 커넥터

| 커넥터 | 용도 | 예시 |
|---|---|---|
| **SharePoint** | 문서/목록 조회·관리 | 사내 게시판 데이터 조회 |
| **Outlook (Office 365)** | 메일 발송 | 결과 알림 메일 전송 |
| **Microsoft Teams** | 메시지/채널 관리 | 특정 채널에 알림 전송 |
| **Dataverse** | 데이터 CRUD | 고객 정보 조회/등록 |
| **Excel Online** | 스프레드시트 조작 | 엑셀 기반 데이터 조회/기록 |
| **Planner** | 작업 관리 | 할 일 생성/조회 |

### 프리미엄 커넥터

표준 커넥터 외에도 **프리미엄 커넥터**를 사용할 수 있습니다. 프리미엄 커넥터는 별도 라이선스가 필요합니다.

- SQL Server, Azure SQL
- HTTP with Microsoft Entra ID
- SAP, Salesforce 등 외부 SaaS

---

## HTTP 기반 API 연동

표준 커넥터로 제공되지 않는 **사내 REST API**나 **외부 서비스 API**와 연동할 때는 HTTP 요청을 직접 사용합니다.

### 연동 방식

#### 방식 1: Power Automate HTTP 액션

Power Automate 플로우 내에서 HTTP 액션을 사용하여 API를 호출하고, 결과를 Copilot Studio로 반환합니다.

```
Copilot Studio → Power Automate 플로우 → HTTP 액션 → 외부 API
                                         ← 응답 결과 ←
```

#### 방식 2: 커스텀 커넥터

사내 API를 OpenAPI(Swagger) 스펙으로 정의하여 **커스텀 커넥터**를 만들면, 표준 커넥터처럼 Copilot Studio에서 직접 사용할 수 있습니다.

```
1. API의 OpenAPI 스펙 준비 (JSON/YAML)
2. Power Platform 관리센터에서 커스텀 커넥터 생성
3. 커넥터에 인증 정보 설정
4. Copilot Studio에서 Action으로 연결
```

#### 방식 3: MCP (Model Context Protocol) 커넥터

최근 지원되기 시작한 MCP 커넥터를 활용하면, MCP 서버를 통해 외부 도구 및 데이터에 접근할 수 있습니다.

### API 연동 시 체크리스트

- [ ] API 엔드포인트 URL 및 HTTP 메서드 확인
- [ ] 요청/응답 형식 (JSON 스키마) 문서화
- [ ] 인증 방식 확인 (API Key / OAuth / Entra ID)
- [ ] 타임아웃 및 에러 응답 처리 로직
- [ ] 네트워크 접근성 (사내망 vs 인터넷)

<div class="info-box warning">
<strong>⚠️ 주의</strong>
사내 방화벽 뒤에 있는 API는 <strong>On-premises Data Gateway</strong>를 설치하거나, <strong>Azure API Management</strong>를 통해 외부 노출해야 Copilot Studio에서 접근할 수 있습니다.
</div>

---

## 인증 방식 개요 (API Key / OAuth / Entra ID)

외부 시스템 연동 시 가장 중요한 요소 중 하나가 **인증(Authentication)**입니다. 데이터 보안과 직결되므로 적절한 인증 방식을 선택해야 합니다.

### 인증 방식 비교

| 방식 | 설명 | 적합한 경우 |
|---|---|---|
| **API Key** | 고정된 키 값을 헤더/파라미터에 포함 | 단순 API, PoC, 내부 전용 API |
| **OAuth 2.0** | 토큰 기반 인증. 사용자 대신 액세스 토큰 획득 | 써드파티 서비스 (Google, Salesforce 등) |
| **Microsoft Entra ID** | Microsoft 통합 인증. SSO 가능 | Microsoft 365, Azure, 사내 시스템 |

### API Key 방식

```
HTTP Header: x-api-key: {your-api-key}
```

- 간단하지만, 키가 노출되면 보안 위험이 있습니다.
- Power Automate의 HTTP 액션에서 헤더로 전달합니다.
- 키는 반드시 **환경 변수** 또는 **Azure Key Vault**에 저장하여 관리하세요.

### OAuth 2.0 방식

```
1. 사용자 인증 요청 (Authorization Code Flow)
2. 인가 서버에서 Authorization Code 발급
3. Access Token 교환
4. API 호출 시 Bearer Token 포함
```

- 커스텀 커넥터에서 OAuth 2.0 설정을 지원합니다.
- Client ID, Client Secret, Authorization URL, Token URL 등을 설정합니다.

### Microsoft Entra ID 방식

- Copilot Studio의 기본 인증 체계입니다.
- 사용자가 Agent에 로그인하면 **Entra ID 토큰**을 자동으로 활용합니다.
- Microsoft Graph API, SharePoint, Dataverse 등에 **SSO(Single Sign-On)** 접근이 가능합니다.

<div class="info-box note">
<strong>📌 권장 사항</strong>
가능하면 <strong>Microsoft Entra ID 기반 인증</strong>을 우선적으로 사용하세요. SSO가 가능하고, 조직의 보안 정책(조건부 액세스, MFA 등)과 통합됩니다. API Key는 PoC나 내부 전용 API에만 제한적으로 사용하세요.
</div>
