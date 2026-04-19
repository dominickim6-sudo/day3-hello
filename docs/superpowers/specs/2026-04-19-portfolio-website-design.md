---
name: Portfolio Static Website
date: 2026-04-19
status: approved
---

# Portfolio Static Website Design

## Overview

다크 테마 기반 개인 포트폴리오 정적 웹사이트. 사이드바 네비게이션으로 섹션을 전환하는 SPA 방식. 단일 HTML 파일 + Tailwind CSS CDN.

## Tech Stack

- **HTML5** - 단일 `index.html` 파일
- **Tailwind CSS** - CDN (빌드 없음)
- **Vanilla JavaScript** - 사이드바 네비게이션, 섹션 전환
- **Hosting** - GitHub Pages

## Layout

```
┌──────────┬─────────────────────────────┐
│ Sidebar  │        Main Content         │
│ (220px)  │                             │
│          │                             │
│ [Avatar] │   Active Section Content    │
│ [Name]   │                             │
│ [Title]  │                             │
│          │                             │
│ ──────── │                             │
│ [Nav]    │                             │
│  About   │                             │
│  Projects│                             │
│  Resume  │                             │
│  Blog    │                             │
│  Contact │                             │
│          │                             │
│ [Social] │                             │
└──────────┴─────────────────────────────┘
```

- **Sidebar**: 고정 위치 (`position: fixed`), 좌측 220px
- **Main**: `margin-left: 220px`, 스크롤 가능
- **모바일**: 사이드바 숨김 + 햄버거 메뉴 토글

## Color Scheme (Dark Theme)

| Role        | Color     | Usage                 |
|-------------|-----------|-----------------------|
| Background  | `#0d1117` | 메인 배경             |
| Sidebar     | `#161b22` | 사이드바 배경         |
| Surface     | `#21262d` | 카드, 입력창 배경     |
| Border      | `#30363d` | 테두리, 구분선        |
| Text        | `#e6edf3` | 주 텍스트             |
| Text Muted  | `#8b949e` | 보조 텍스트           |
| Accent      | `#e94560` | 활성 메뉴, 링크, CTA  |
| Accent Hover| `#ff6b81` | 호버 상태             |

## Sections

### 1. About
- 프로필 사진 (원형, 120px)
- 이름 (h1)
- 직업 타이틀
- 한줄 소개 (2-3문장)
- 기술 스택 태그 (pill 형태)

### 2. Projects
- 프로젝트 카드 그리드 (2 columns)
- 각 카드: 썸네일 이미지, 제목, 설명, 기술 태그, 링크 (GitHub/Live)
- 호버 시 살짝 올라가는 애니메이션

### 3. Resume
- 타임라인 형태 (세로 라인 + 점)
- Experience 섹션: 회사명, 직책, 기간, 설명
- Education 섹션: 학교, 전공, 기간
- Skills 섹션: 카테고리별 기술 태그

### 4. Blog (콘텐츠 게시)
- 글 목록 카드 리스트
- 각 항목: 제목, 날짜, 요약, 카테고리 태그
- 추후 실제 글 추가를 위한 플레이스홀더 3개

### 5. Contact
- 이메일, GitHub, LinkedIn 아이콘 + 링크
- **카카오톡 상담 버튼** (카카오톡 채널 1:1 채팅 연결)
- 심플한 연락 폼 (이름, 이메일, 메시지) - JS로 메일to 링크 생성

## Interactions

- **사이드바 네비게이션**: 클릭 시 해당 섹션으로 스크롤 (smooth scroll)
- **활성 메뉴 표시**: Intersection Observer로 현재 섹션 감지
- **카드 호버**: `transform: translateY(-4px)` + 그림자
- **모바일 반응형**: 768px 이하에서 사이드바 숨김, 햄버거 메뉴

## KakaoTalk Integration

카카오톡 채널 상담 버튼:
- Contact 섹션에 노란색 카카오톡 버튼 배치
- 클릭 시 카카오톡 채널 1:1 채팅 페이지로 이동
- 채널 ID는 플레이스홀더로 두고 실제 ID는 나중에 교체

## File Structure

```
index.html          # 전체 웹사이트 (단일 파일)
├── <head>          # Tailwind CDN, 커스텀 스타일
├── <aside>         # 사이드바 네비게이션
└── <main>          # 5개 섹션 (about, projects, resume, blog, contact)
    └── <script>    # 네비게이션 로직, Intersection Observer
```

## Out of Scope

- 백엔드 / 데이터베이스
- 폼 제출 서버 처리 (mailto 대체)
- SEO 최적화
- 다국어 지원
