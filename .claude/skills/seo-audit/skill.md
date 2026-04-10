---
name: seo-audit
description: 리치인터뷰 사이트 전체의 SEO 상태를 감사하고 개선하는 스킬
user_invocable: true
---

# SEO Audit Skill

사이트 전체의 SEO 상태를 점검하고 문제를 수정한다.

## 점검 항목

### 1. 메타데이터 완전성
- 모든 HTML 파일에서 `<title>`, `<meta description>`, OG 태그, canonical 확인
- 중복 title/description 탐지
- description 길이 검증 (50-160자)

### 2. 사이트맵 정합성
- `sitemap.xml`의 URL 목록과 실제 파일 1:1 매핑 확인
- 누락된 페이지 탐지 및 추가
- `lastmod` 날짜 정확성 확인

### 3. 구조화 데이터
- 모든 포스트의 Article LD+JSON 검증
- 모든 인물의 Person LD+JSON 검증
- 필수 필드 누락 확인

### 4. 내부 링크
- 깨진 링크 탐지 (존재하지 않는 파일 참조)
- BASE_PATH (`/richinterview/`) 누락 확인
- 인물 ↔ 포스트 양방향 링크 확인

### 5. 기술 SEO
- robots.txt 설정 검증
- 모바일 viewport 태그 확인
- 이미지 alt 텍스트 존재 여부

## 출력
점검 결과를 요약 리포트로 생성:
- 총 페이지 수 / 정상 / 문제 있는 페이지
- 카테고리별 이슈 목록
- 자동 수정한 항목 / 수동 확인 필요 항목
