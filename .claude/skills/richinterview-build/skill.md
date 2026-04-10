---
name: richinterview-build
description: 리치인터뷰 프로젝트의 콘텐츠 생성, SEO 개선, 사이트 관리를 에이전트 팀으로 수행하는 오케스트레이터
user_invocable: true
---

# Rich Interview Build Orchestrator

콘텐츠 생성과 SEO 최적화를 조율하는 오케스트레이터 스킬.

## 트리거 조건
- '포스트 추가해줘', '인물 추가해줘', '콘텐츠 만들어줘'
- 'SEO 개선해줘', '사이트맵 업데이트해줘'
- '전체 점검해줘', '빌드', 'build'

## 워크플로우

### Phase 1: 분석
1. 요청 내용 파악 (신규 콘텐츠 vs 개선 vs 점검)
2. 현재 사이트 상태 확인 (포스트 수, 인물 수, 최근 변경)
3. 작업 범위 결정

### Phase 2: 팀 구성
- **소규모 작업** (포스트 1-2개 추가): content-creator 단독
- **중규모 작업** (인물 추가 + 다수 포스트): content-creator + seo-optimizer
- **대규모 작업** (사이트 전체 개선): 두 에이전트 풀 가동 + 교차 검증

### Phase 3: 실행
1. `TeamCreate`로 에이전트 팀 구성
2. content-creator에게 콘텐츠 생성/수정 작업 할당
3. seo-optimizer에게 메타데이터/사이트맵 검증 할당
4. 결과 취합 및 크로스 체크

### Phase 4: 검증 및 완료
1. 생성된 HTML의 구조 검증
2. 내부 링크 정합성 확인
3. sitemap.xml 동기화 확인
4. index.html / people.html 업데이트 확인
5. Git 커밋 준비 (변경 파일 목록 + 커밋 메시지 제안)

## 품질 기준
- 새 포스트는 기존 포스트와 동일한 HTML 구조를 따를 것
- 모든 메타데이터(OG, Schema.org) 누락 없을 것
- sitemap.xml과 실제 파일이 1:1 매핑될 것
