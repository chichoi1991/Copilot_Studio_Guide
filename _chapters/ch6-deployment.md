---
layout: chapter
title: "배포 및 사용 범위 설정"
short_title: "배포 및 범위 설정"
description: "Teams 배포, Web App 배포, 사용자/조직별 사용 범위 관리 방법을 다룹니다."
order: 6
icon: "🚀"
---

## Teams 배포

Microsoft Teams는 Copilot Studio Agent의 **가장 대표적인 배포 채널**입니다. 조직 내 대부분의 사용자가 이미 Teams를 사용하고 있기 때문에, 별도의 앱 설치 없이 Agent를 제공할 수 있습니다.

### 배포 절차

1. **Copilot Studio에서 Publish**
   - Agent 편집 화면 > **Publish** 버튼 클릭
   - 게시가 완료되면 **Channels** 메뉴에서 Teams를 선택

2. **Teams 채널 설정**
   - "Microsoft Teams" 채널 활성화
   - Agent 아이콘, 설명, 개인정보 처리방침 URL 등 메타데이터 입력

3. **Teams 앱 패키지 생성**
   - Copilot Studio가 자동으로 Teams 앱 매니페스트를 생성합니다.
   - "Open the bot" 링크로 즉시 테스트 가능

4. **Teams 관리센터 배포** (조직 전체 배포 시)
   - Teams Admin Center에서 앱을 업로드하여 조직 전체에 배포
   - 또는 특정 사용자/그룹에게만 선택적으로 배포

### Teams 배포 옵션

| 옵션 | 범위 | 설명 |
|---|---|---|
| **개인 링크 공유** | 개별 사용자 | 링크 클릭으로 Agent 추가 |
| **Teams 앱 카탈로그** | 조직 전체 | 관리자가 앱 카탈로그에 등록 |
| **정책 기반 배포** | 특정 그룹 | Teams 정책으로 자동 설치/핀 고정 |
| **사이드로딩** | 개발/테스트 | 개발 환경에서 직접 앱 패키지 업로드 |

<div class="info-box tip">
<strong>💡 실무 팁</strong>
조직 전체 배포 전에, 먼저 <strong>파일럿 그룹(10~50명)</strong>에게 배포하여 피드백을 수집하세요. Teams 관리센터의 <strong>앱 설정 정책</strong>을 활용하면 특정 부서/그룹에게만 선택적으로 배포할 수 있습니다.
</div>

---

## Web App 배포

Copilot Studio Agent는 **웹사이트에 임베드**하여 방문자에게 대화형 인터페이스를 제공할 수 있습니다.

### 웹 채널 배포 방식

#### 방식 1: iframe 임베드

Copilot Studio에서 제공하는 **임베드 코드(iframe)**를 웹사이트에 삽입합니다.

```html
<iframe
  src="https://copilotstudio.microsoft.com/environments/{env-id}/bots/{bot-id}/webchat"
  frameborder="0"
  style="width: 100%; min-height: 500px;">
</iframe>
```

#### 방식 2: Direct Line API

**Direct Line API**를 사용하면 완전히 커스텀된 웹 채팅 UI를 구현할 수 있습니다.

```javascript
// Direct Line 토큰 획득 후 WebChat 연동
const directLine = new DirectLine({
  token: '{direct-line-token}'
});
```

#### 방식 3: 커스텀 캔버스

Copilot Studio의 **커스텀 캔버스** 기능을 활용하면, 채팅 위젯의 디자인을 조직 브랜드에 맞게 커스터마이징할 수 있습니다.

### 웹 배포 시 고려사항

| 항목 | 설명 |
|---|---|
| **인증** | 웹사이트 방문자 인증 필요 여부 결정 |
| **도메인 제한** | 특정 도메인에서만 Agent 접근 허용 가능 |
| **반응형 디자인** | 모바일 브라우저 대응 |
| **CORS 설정** | 커스텀 캔버스 사용 시 CORS 정책 확인 |

<div class="info-box note">
<strong>📌 참고</strong>
웹 채널로 배포 시, <strong>인증되지 않은 익명 사용자</strong>도 Agent에 접근할 수 있습니다. 사내 민감 데이터를 다루는 Agent는 반드시 <strong>인증 필수</strong> 설정을 활성화하세요.
</div>

---

## 사용자/조직별 사용 범위 관리

Agent를 배포한 후에는 **누가, 어디에서, 어떤 기능을** 사용할 수 있는지 관리하는 것이 중요합니다.

### 접근 제어 계층

```
┌──────────────────────────────────────────┐
│        Power Platform 환경 (Environment) │
│  ┌────────────────────────────────────┐  │
│  │        보안 역할 (Security Role)    │  │
│  │  ┌──────────────────────────────┐  │  │
│  │  │    Agent 단위 공유 설정       │  │  │
│  │  │  ┌──────────────────────┐   │  │  │
│  │  │  │  Knowledge 접근 권한  │   │  │  │
│  │  │  └──────────────────────┘   │  │  │
│  │  └──────────────────────────────┘  │  │
│  └────────────────────────────────────┘  │
└──────────────────────────────────────────┘
```

### 환경(Environment) 기반 분리

| 환경 | 용도 | 접근 대상 |
|---|---|---|
| **개발 환경** | Agent 개발 및 테스트 | 개발팀 |
| **스테이징 환경** | UAT 및 검증 | 파일럿 사용자 |
| **운영 환경** | 실 서비스 운영 | 전체 사용자 |

### Agent 공유 설정

- **Agent 편집 권한**: 특정 사용자에게만 Agent 편집 권한 부여
- **Agent 사용 권한**: 특정 사용자/그룹에게만 Agent 사용 허용
- **Entra ID 보안 그룹 연동**: 조직의 보안 그룹 기반으로 접근 제어

### Knowledge 접근 제어

- Knowledge로 연결된 SharePoint 등의 데이터는 **사용자별 Entra ID 권한**에 따라 접근이 제어됩니다.
- 사용자 A가 접근 권한이 없는 문서의 내용은 Agent 응답에 포함되지 않습니다.
- 이를 **"사용자 수준 데이터 격리(User-level Data Isolation)"**라 합니다.

<div class="info-box warning">
<strong>⚠️ 주의</strong>
Agent 배포 전에 반드시 <strong>접근 권한 매트릭스</strong>를 작성하세요. 특히 Knowledge로 연결된 데이터 소스의 권한이 올바르게 설정되어 있는지 확인해야 합니다. 잘못된 권한 설정은 데이터 유출로 이어질 수 있습니다.
</div>
