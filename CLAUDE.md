# Rich Interview (리치인터뷰)

AI 더빙 인터뷰를 큐레이션하는 정적 HTML 블로그 사이트.
글로벌 리더(Jensen Huang, Sam Altman, Warren Buffett 등)의 유튜브 인터뷰를 한국어 AI 더빙으로 제공.

## Design System
- `DESIGN.md` 참조: Supabase 스타일 (다크 모드 네이티브, 에메랄드 그린 액센트, Circular 폰트)
- HTML/CSS 작성 시 반드시 DESIGN.md의 색상 팔레트, 타이포그래피, 컴포넌트 스타일을 따를 것
- 전체 디자인 컬렉션: `~/awesome-design-md/design-md/` (55개 브랜드 참조 가능)

## 기술 스택

- **프론트엔드:** 순수 HTML5 + CSS3 (프레임워크/빌드 도구 없음)
- **호스팅:** GitHub Pages (`fractalreason-coder.github.io/richinterview`)
- **외부 의존성:** YouTube iframe 임베드
- **SEO:** sitemap.xml, robots.txt, Schema.org LD+JSON, OG 태그

## 프로젝트 구조

```
richinterview/
├── index.html          # 홈페이지 (포스트 그리드 + 인물 목록)
├── people.html         # 인물 디렉토리 페이지
├── style.css           # 글로벌 스타일 (다크 테마, #e63946 액센트)
├── robots.txt          # SEO 로봇 설정
├── sitemap.xml         # XML 사이트맵 (86개 URL)
├── posts/              # 57개 포스트 HTML 파일
│   └── {제목}.html     # 각 포스트: 메타데이터 + 유튜브 임베드 + LLM 분석 + 트랜스크립트
└── people/             # 26명 인물 프로필 HTML
    └── {이름}.html     # 각 인물: 프로필 + 에피소드 목록
```

## HTML 템플릿 규칙

### 포스트 구조
- `<meta>` 태그: title, description, og:*, twitter:*, canonical
- Schema.org LD+JSON (Article 타입)
- 헤더/네비게이션
- `.post-meta`: 인물 태그, 날짜, 영상 길이
- `.shorts-embed`: YouTube iframe (16:9)
- `.article`: LLM 생성 분석 (h2, p, ul, blockquote)
- `.transcript`: 전체 자막
- `.cta`: 유튜브 구독 버튼

### 인물 프로필 구조
- Schema.org LD+JSON (Person 타입)
- 프로필 헤더 (이름, 직함, 키워드)
- 바이오 섹션
- 에피소드 섹션 (썸네일 + 포스트 링크)

### 스타일 규칙
- 다크 테마, 폰트: 'Apple SD Gothic Neo'
- 액센트 컬러: #e63946
- 모바일 반응형: max-width 768px 브레이크포인트
- BASE_PATH: `/richinterview` (GitHub Pages 서브디렉토리)

## 개발 컨벤션

- 새 포스트/인물 추가 시 반드시 `sitemap.xml` 업데이트
- `index.html`의 포스트 그리드와 `people.html`의 인물 목록도 동기화
- 모든 내부 링크는 `/richinterview/` 프리픽스 사용
- 유튜브 썸네일: `https://img.youtube.com/vi/{VIDEO_ID}/maxresdefault.jpg`
- 날짜 형식: YYYY-MM-DD
