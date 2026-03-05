# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## 언어 및 커뮤니케이션 규칙
- **기본 응답 언어**: 한국어
- **코드 주석**: 한국어로 작성
- **커밋 메시지**: 한국어로 작성
- **문서화**: 한국어로 작성
- **변수명/함수명**: 영어 (코드 표준 준수)

## 프로젝트 개요
정적 HTML 포트폴리오 사이트로, 빌드 도구나 외부 의존성이 없는 순수 웹 기술(HTML5, CSS, Vanilla JavaScript)로 구성됨.

## 개발 환경 및 명령어

### 로컬 서버 실행
```bash
# Python 3를 사용한 간단한 HTTP 서버
python -m http.server 8000
# 또는
python3 -m http.server 8000

# Node.js가 설치되어 있다면
npx http-server
```
브라우저에서 `http://localhost:8000`으로 접속.

### 빌드/린트/테스트
이 프로젝트는 빌드 프로세스가 없습니다. 단일 `index.html` 파일이 배포 파일입니다.
- 브라우저 DevTools로 직접 테스트
- HTML/CSS 검증: W3C Validator 사용 권장

## 코드 구조

### 아키텍처 패턴
- **단일 페이지**: index.html 하나로 전체 사이트 구성
- **섹션 기반 설계**: Home, About, Projects, Contact 섹션으로 나눔
- **인라인 스타일**: HTML 내 `<style>` 태그에서 CSS 관리

### 주요 기술 스택

#### CSS
- **Tailwind CSS**: CDN으로 로드되는 유틸리티 기반 CSS 프레임워크
- **커스텀 애니메이션**: `<style>` 블록에서 정의 (typewriter, fade-in 등)
- **색상 스키마**: Tailwind 기본 색상 + 인디고(#818cf8)를 주요 강조색으로 사용

#### JavaScript
- **Vanilla JavaScript**: 프레임워크 없이 순수 JS 사용
- **주요 기능**:
  - 네비게이션 스크롤 효과 (nav.scrolled 클래스 토글)
  - 액티브 네비게이션 링크 업데이트 (Intersection Observer 패턴)
  - 섹션 fade-in 애니메이션 (Intersection Observer)
  - 타이핑 애니메이션 (Hero 텍스트)

### 주요 클래스 및 스타일
- `.typing-text`: Hero 섹션 타이핑 애니메이션
- `.fade-in / .fade-in.visible`: 스크롤 시 섹션 나타나는 애니메이션
- `.tech-card`: 기술 스택 카드 (hover 시 Y축 이동 + 아이콘 확대)
- `.project-card / .project-overlay`: 프로젝트 카드 (hover 시 오버레이 상향 슬라이드)
- `.btn-primary / .btn-secondary`: 버튼 스타일 (그라디언트, 테두리)

## 개발 시 유의사항
- CDN 리소스 사용: Tailwind CSS와 Google Fonts는 CDN으로 로드되므로, 개발 시 인터넷 연결 필요
- 반응형 디자인: `md:` 접두사 사용으로 태블릿/모바일 대응 (breakpoint 768px)
- 색상 통일: 주요 색상(#818cf8 인디고)이 여러 곳에서 사용되므로 변경 시 모든 위치 수정 필요
