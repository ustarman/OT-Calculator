# OT Calculator — 운영 가이드 (CLAUDE.md)

Redbank Transport 운전기사용 **초과근무(OT) 계산기** PWA.
설치형(홈화면 추가) + 오프라인 동작하는 단일 HTML 앱.

## 무엇을 하는 앱인가
- 로스터 근무시간(Rostered Hours)과 실제 근무시간(Actual Hours)을 입력하면
  - **Extra OT**(추가 초과), **Rostered OT**(로스터상 초과)를 계산
- **캘린더(History)** 로 날짜별 기록 저장·조회
- **격주 급여기간(fortnightly pay period)** 요약 — 기준: 2026-06-14(일) 앵커
- **Export / Import 백업** (파일로 내보내고 다시 불러오기)
- 다크모드, iOS 줌 방지 처리

## 기술 스택
- 순수 HTML/CSS/JS **단일 파일** (`index.html`, 약 930줄) — 빌드 단계 없음
- **서비스워커**(`sw.js`) — HTML은 network-first(업데이트 자동 반영), 아이콘 등은 cache-first
- **PWA**: `manifest.json`, `icon-192.png`, `icon-512.png`
- 데이터는 브라우저 로컬(localStorage)에 저장 — 서버/DB 없음

## 로컬 실행
```bash
npx serve -p 3456 .
```
(`.claude/launch.json`에 `ot-calculator` 설정 등록됨 → 포트 3456)

## 배포 (GitHub Pages)
- 원격: `github.com/ustarman/OT-Calculator` (브랜치 `main`)
- 공개 주소: `https://ustarman.github.io/OT-Calculator/`
- **main에 push 하면 Pages가 자동 반영**. gh-pages 브랜치 없음(main에서 바로 서빙).
- 인증: macOS keychain (`ustarman@github.com`). 원격 URL에 토큰 박지 말 것.

## ⚠️ 코드 바꿀 때 반드시
- **`sw.js`의 `const CACHE = 'ot-calculator-vNN'` 숫자를 올릴 것.**
  안 올리면 기존 사용자가 캐시된 옛 버전을 계속 봄. (현재 v15)
- `start_url`/SW fallback 경로가 `/OT-Calculator/` 로 하드코딩돼 있음 — 배포 경로 바꾸면 같이 수정.

## 배포 규칙
- git commit / push / 배포는 **Brendon의 명시적 OK 뒤에만**. 작은 수정도 먼저 물어볼 것.

## 현재 상태 (2026-11-13)
- 마지막 커밋 `345b256` (SW network-first for HTML)
- 위치: `~/OT-Calculator` (이전엔 `Work Space/OT-Calculator`에 있어서 세션에 안 떴음 → 홈 루트로 이동함)
- git 깨끗 (작업물 변경 없음)
