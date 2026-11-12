# HANDOFF — OT Calculator

> 작업 이어갈 때 **이 파일 먼저** 읽기. (상세 운영 내용은 루트 `CLAUDE.md`)

## 한 줄 요약
Redbank Transport 기사용 OT 계산기 PWA. 단일 `index.html` + 서비스워커. GitHub Pages 배포.

## 지금 상태 (2026-11-13)
- 위치: `~/OT-Calculator` (홈 루트로 옮김. 예전 위치 `Work Space/OT-Calculator`)
- 브랜치 `main`, 마지막 커밋 `345b256`, 작업물 깨끗
- 배포: `https://ustarman.github.io/OT-Calculator/` (main push → 자동)
- git 인증: keychain (URL에 토큰 없음)

## 다음에 손대면 좋을 것 (아이디어, 미확정)
- (없음 — 안정 버전. Brendon이 요청할 때 진행)

## 빠뜨리기 쉬운 것 ⚠️
- 코드 수정 시 `sw.js`의 캐시 버전 번호(`ot-calculator-vNN`) **반드시 +1** (현재 v15)
- commit/push/배포는 **Brendon OK 받고** 진행

## 백업
- `~/app-backups/OT-Calculator-live-2026-06-27-f001984.zip`
