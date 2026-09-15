# LaMI Lab 홈페이지

홈페이지 콘텐츠를 수정할 때 필요한 파일 위치와 작업 방법입니다. 각 섹션 제목을 클릭하면 내용이 펼쳐집니다.

<details>
<summary><h2>1. 디렉터리 구조</h2></summary>

```
lami-labs.github.io/
├── .github/workflows/deploy.yml   # GitHub Pages 자동 배포 워크플로
├── hugoblox.yaml                  # Hugo 버전 고정, 템플릿 ID
├── go.mod / go.sum                # Hugo 모듈(테마) 의존성
├── package.json                   # Tailwind, preact 의존성
│
├── config/_default/               # 사이트 전역 설정
│   ├── hugo.yaml                  #   사이트 제목, baseURL, security.exec 등
│   ├── params.yaml                #   테마 색상, 헤더/푸터, SEO, 분석 도구 등
│   └── menus.yaml                 #   상단 네비게이션 메뉴
│
├── content/                       # 페이지 뼈대 (각 페이지에 어떤 섹션을 넣을지)
│   ├── _index.md                  #   홈
│   ├── members/_index.md          #   Members (전체 목록, 메뉴에는 없음)
│   ├── members/professor/_index.md #  Members > Professor (교수 사진 + 소개/학력/경력)
│   ├── members/students/_index.md #   Members > Students (박사, 석박통합, 석사, 인턴)
│   ├── members/alumni/_index.md   #   Members > Alumni (졸업생)
│   ├── news/_index.md             #   News
│   ├── publications/_index.md     #   Publications
│   ├── gallery/_index.md          #   Gallery
│   ├── contact/_index.md          #   Contact (주소, 이메일, Office Hours)
│   ├── join/_index.md             #   Join LaMI (모집 안내, 지원 폼 링크)
│   ├── research/_index.md         #   Research (메뉴에는 없음, /research/ 직접 접속)
│   └── project/_index.md          #   Project (메뉴에는 없음)
│
├── data/                          # ★ 실제 콘텐츠 데이터 (가장 자주 수정)
│   ├── members/                   #   멤버 (과정별 폴더, 한 명당 YAML 하나)
│   │   ├── professor/  postdoc/  phd/  integrated/  master/  intern/  Alumni/
│   ├── research/                  #   연구 주제 (Research 페이지용, 현재 비어 있음)
│   ├── publications/publications.yaml
│   ├── project/projects.yaml
│   ├── news/news.yaml
│   ├── gallery/albums.yaml
│   ├── info/contact.yaml          #   Contact 페이지 주소/이메일/Office Hours
│   ├── info/resources.yaml        #   (장비 카드 데이터, 현재 미사용)
│   ├── info/contact_info.yaml     #   (구 연락처 카드 데이터, 현재 미사용)
│   └── application/notice.yaml    #   Join LaMI 페이지 안내문
│
├── docs/examples/                 # 멤버/연구 YAML 예시 파일 (.example)
│
├── layouts/                       # 커스텀 템플릿 (HTML + Hugo 템플릿 문법)
│   ├── shortcodes/                #   content/에서 {{< ... >}}로 호출하는 컴포넌트
│   │   ├── members-pi.html        #     교수 카드
│   │   ├── members-postdoc.html   #     포닥 카드
│   │   ├── members-phd.html       #     박사과정 카드
│   │   ├── members-integrated.html #    석박통합과정 카드
│   │   ├── members-master.html    #     석사과정 카드
│   │   ├── members-interns.html   #     학부생/인턴 카드
│   │   ├── members-alumni.html    #     졸업생 목록
│   │   ├── members-cards.html     #     (범용 멤버 카드, 현재 미사용)
│   │   ├── research-cards.html    #     연구 주제 카드 (Research 페이지)
│   │   ├── home-research-topic.html #   (홈용 연구 캐러셀, 현재 미사용)
│   │   ├── publication-cards.html #     논문 목록 + 검색/필터
│   │   ├── project-cards.html     #     과제 목록
│   │   ├── news-cards.html        #     뉴스 카드 (홈/뉴스 페이지 공용)
│   │   ├── gallery-albums.html    #     갤러리 앨범 + 라이트박스
│   │   ├── resource-cards.html    #     장비/서버 카드 (현재 미사용)
│   │   ├── contact-panel.html     #     연락처 2단 패널 (주소 / 이메일·Office Hours 카드)
│   │   ├── contact-info-cards.html #    (구 연락처 카드, 현재 미사용)
│   │   └── application-notice.html #    지원 안내
│   ├── partials/authors/
│   │   ├── author-image.html      #   멤버 사진 경로 결정 로직
│   │   └── author-hover-image.html #  멤버 hover 사진 경로 결정 로직
│   ├── partials/body_end.html     #   파비콘 강제 교체 스크립트
│   └── _partials/hooks/body-end/  #   페이지 하단에 삽입되는 JS
│       ├── favicon-static.html    #     파비콘 교체
│       ├── nav-underline.html     #     메뉴 밑줄 애니메이션
│       └── people-hover-image.html #    멤버 사진 hover 전환
│
├── assets/                        # Hugo 파이프라인으로 처리되는 자산
│   ├── css/custom.css             #   전역 커스텀 CSS (메뉴 간격, 컨테이너 폭 등)
│   ├── js/preact-built/hero.js    #   히어로 섹션 preact 번들 (빌드 결과물)
│   └── media/
│       ├── home.png               #   홈 히어로 배경 이미지
│       └── logo.png               #   헤더 로고
│
├── static/                        # 그대로 복사되는 정적 파일 (URL: /media/...)
│   ├── favicon.png
│   └── media/
│       ├── icon/*.svg             #   연락처/논문 링크용 아이콘
│       ├── members/               #   멤버 사진 (<slug>.jpg, hover용은 hidden/)
│       ├── research/              #   연구 주제 이미지
│       ├── news/                  #   뉴스 이미지
│       ├── gallery/<앨범폴더>/     #   갤러리 사진
│       └── resource/              #   장비 사진
│
└── blog/                          # 템플릿 잔여물. hugo.yaml에서 렌더링 비활성화됨
```

</details>

<details>
<summary><h2>2. 페이지별 수정 가이드</h2></summary>

페이지 구성은 `content/<페이지>/_index.md`에서 수정합니다. 목록형 콘텐츠는 shortcode(데이터를 화면에 표시하는 템플릿)가 `data/`에서 읽어오며, 홈 소개와 교수 소개처럼 페이지 파일 안에 직접 작성된 내용도 있습니다.

| 페이지 | URL | content 파일 | 데이터 소스 | 이미지 위치 |
|---|---|---|---|---|
| Home | `/` | `content/_index.md` | `data/news/news.yaml` | `assets/media/home.png` (배경) |
| Members > Professor | `/members/professor/` | `content/members/professor/_index.md` | 페이지 파일 안 HTML | `static/media/members/jisoo-mok.jpg` |
| Members > Students | `/members/students/` | `content/members/students/_index.md` | `data/members/**/*.yaml` (PhD, Integrated, Master, Interns) | `static/media/members/<slug>.jpg` |
| Members > Alumni | `/members/alumni/` | `content/members/alumni/_index.md` | `data/members/Alumni/*.yaml` | 없음 |
| Members (전체) | `/members/` | `content/members/_index.md` | 위 전체 | 메뉴에 노출되지 않음 |
| News | `/news/` | `content/news/_index.md` | `data/news/news.yaml` | `static/media/news/` |
| Publications | `/publications/` | `content/publications/_index.md` | `data/publications/publications.yaml` | 없음 (아이콘만) |
| Gallery | `/gallery/` | `content/gallery/_index.md` | `data/gallery/albums.yaml` | `static/media/gallery/<folder>/` |
| Contact | `/contact/` | `content/contact/_index.md` | `data/info/contact.yaml` | 없음 |
| Research (메뉴 없음) | `/research/` | `content/research/_index.md` | `data/research/*.yaml` | `static/media/research/` |
| Project (메뉴 없음) | `/project/` | `content/project/_index.md` | `data/project/projects.yaml` | 없음 |
| Join LaMI | `/join/` | `content/join/_index.md` | `data/application/notice.yaml` | 없음 |

### 홈 (`content/_index.md`)

- **히어로**: `sections[0]` (`block: hero`)의 `title`, `text`, `announcement`를 수정. 배경은 `assets/media/home.png`.
- **지원 링크**: 히어로의 Apply 버튼과 소개 문단의 `Join us →` 링크는 `/join/` (Join LaMI 페이지)로 갑니다. 구글 폼 주소는 `data/application/notice.yaml`의 `buttons`에만 있습니다.
- **연구실 소개 문단**: `id: intro` 블록의 HTML을 직접 수정.
- **Research Areas 3단 카드**: `id: research-areas` 블록의 HTML에 직접 작성되어 있음. 연구 분야 제목/설명을 바꾸려면 여기를 수정.
- **Latest News**: `{{< news-cards >}}` → `data/news/news.yaml`에서 최신 12개.

### Members > Professor (`content/members/professor/_index.md`)

- 이 페이지는 멤버 카드 shortcode를 쓰지 않고 `id: pi` 블록의 HTML로 직접 구성되어 있습니다. 왼쪽 사진, 오른쪽 소개글, 아래에 Education / Professional Experience / Academic Service / Invited Talks 4개 섹션입니다.
- 사진은 `static/media/members/jisoo-mok.jpg`를 읽습니다. 소개글, CV 링크, 경력이 바뀌면 이 파일의 HTML을 수정하세요.
- 교수 YAML(`data/members/professor/jisoo-mok.yaml`)은 전체 Members 페이지(`/members/`)에서만 쓰입니다.

### Contact (`content/contact/_index.md`)

- 2단 연락처 패널 한 블록으로 구성됩니다. (장비 카드 `resource-cards`는 제거했습니다. 다시 넣으려면 `data/info/resources.yaml`과 shortcode가 남아 있습니다.)
- 연락처 패널의 텍스트는 전부 `data/info/contact.yaml`에서 읽습니다. 페이지 파일은 건드릴 필요가 없습니다.
- 지도는 넣지 않았습니다. 주소 텍스트만 표시합니다.
- 데이터 파일은 페이지 이름과 달리 `data/info/`에 있습니다 (shortcode가 `site.Data.info`를 읽음).

</details>

<details>
<summary><h2>3. 자주 하는 작업</h2></summary>

**새 멤버 추가**

1. `data/members/<폴더>/<slug>.yaml` 생성. 아래 표의 `category` 값을 정확히 사용합니다.
2. `slug`(멤버를 구분하는 영문 이름)를 파일명과 맞추고, `name.display`, `role`을 입력합니다.
3. 사진을 `static/media/members/<slug>.jpg`로 저장합니다. 다른 파일을 사용하려면 `image: 파일명.png`로 지정합니다.
4. `order`가 작을수록 먼저 표시됩니다.

| 과정 | 데이터 폴더 | `category` 값 |
|---|---|---|
| 교수 | `professor/` | `PI` |
| 박사후연구원 | `postdoc/` | `Postdoc` |
| 박사과정 | `phd/` | `PhD Students` |
| 석박통합과정 | `integrated/` | `Integrated Students` |
| 석사과정 | `master/` | `Master Students` |
| 학부 인턴 | `intern/` | `Interns` |

`docs/examples/members/` 예시를 복사할 때는 YAML 항목의 앞쪽 `#`를 제거하고, 예시의 예전 카테고리 대신 위 표의 값을 사용합니다. 교수·박사후연구원 카드는 전체 Members 페이지에서 사용하며, 교수 소개 페이지는 별도로 수정합니다.

예: `data/members/intern/gildong-hong.yaml`

```yaml
schema: hugoblox/author/v1
slug: gildong-hong
category: Interns
order: 1
name:
  display: Gildong Hong
role: Undergraduate Intern
```

이 예시의 사진은 `static/media/members/gildong-hong.jpg`입니다. 마우스를 올렸을 때 다른 사진을 표시하려면 `static/media/members/hidden/`에 사진을 넣고 `hidden_image: 파일명.jpg`를 추가합니다.

**멤버 졸업 처리**

1. 기존 YAML을 `data/members/Alumni/`로 이동
2. `category: Alumni`로 바꾸고 `course`, `next`, `graduated` 추가
3. 불필요한 `links`, `tags` 등은 제거해도 됨 (Alumni 카드는 표시하지 않음)

**논문 추가**

1. `data/publications/publications.yaml` 맨 위에 항목 추가 (정렬은 자동)
2. `category`를 지정하면 해당 카테고리 필터가 자동으로 표시됨
3. 필요하면 `data/news/news.yaml`에 `type: Publication` 뉴스도 추가

**뉴스 추가**

1. `data/news/news.yaml`에 항목 추가
2. 이미지가 있으면 `static/media/news/`에 저장

**갤러리 앨범 추가**

1. `static/media/gallery/<folder>/`에 사진 저장 (`1.jpg`, `2.jpg`… 순번 권장)
2. `data/gallery/albums.yaml`에 항목 추가 (`folder`는 사진 폴더명, `category`는 카테고리 이름)
3. 등록된 카테고리만 필터로 표시되며, 앨범이 없으면 All만 표시됨. Load more는 현재 필터에서 아직 보여주지 않은 앨범이 있을 때 나타남 (처음 18개, 이후 18개씩 추가).

예: `static/media/gallery/workshop_2026/`에 사진을 넣은 뒤 아래 항목을 추가합니다. 빈 파일에 예시 주석만 있다면 그 아래에 작성하면 됩니다.

```yaml
- slug: workshop-2026
  title: Lab Workshop 2026
  folder: workshop_2026
  cover: 1.jpg
  category: Events
  date: "2026-09-15"
  location: Seoul
```

`folder`는 실제 사진 폴더명과 일치해야 합니다. `cover`는 해당 폴더 안의 파일명이며, 생략하면 숫자 순으로 정렬된 첫 번째 사진을 사용합니다.

**연락처 / Office Hours 변경**

1. `data/info/contact.yaml` 수정

**지원 폼 링크 변경**

1. `data/application/notice.yaml`의 `buttons[].url`

**새 페이지 추가**

1. `content/<이름>/_index.md` 생성 (기존 페이지 복사 권장)
2. 필요하면 `layouts/shortcodes/`에 컴포넌트 작성, `data/`에 데이터 파일 추가
3. `config/_default/menus.yaml`에 메뉴 항목 추가

</details>
