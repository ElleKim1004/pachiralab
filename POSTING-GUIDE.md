# 파키라랩 홈페이지 — 글 쓰는 방법

## 한 줄 요약

`_posts` 폴더에 **파일 하나**를 만들면 목록·상세페이지·RSS가 자동으로 생깁니다.

---

## 1. 글 올리기

GitHub 저장소(`ElleKim1004/pachiralab`)에서:

1. `_posts` 폴더 열기
2. 우측 상단 **Add file → Create new file**
3. 파일 이름을 아래 규칙으로 입력
4. 내용 작성 후 맨 아래 **Commit changes**
5. 1~2분 뒤 pachira.kr에 반영됩니다

### 파일 이름 규칙 (꼭 지켜야 함)

```
연도-월-일-영문제목.md
```

예: `2026-09-01-tips-application-guide.md`

- 날짜는 반드시 `2026-09-01` 형식 (한 자리 수도 `09`처럼 두 자리)
- 영문 제목은 띄어쓰기 대신 하이픈(`-`), 한글 쓰지 않기 — 주소에 그대로 들어갑니다
- 확장자는 `.md`

---

## 2. 글 내용 형식

파일 맨 위에 `---` 로 감싼 블록이 있어야 합니다. 이게 없으면 글로 인식되지 않습니다.

```markdown
---
layout: post
title: "여기에 한글 제목을 씁니다"
categories: [open-innovation]
summary: "목록에 보일 한 줄 소개입니다."
---

여기부터 본문입니다.

## 소제목

문단은 빈 줄로 나눕니다.

- 목록은 이렇게
- 하이픈으로 씁니다

**굵게** 쓰고 싶으면 별표 두 개로 감쌉니다.

> 인용문은 꺾쇠로 시작합니다.
```

### categories 에 쓸 수 있는 값

| 쓰는 값 | 게시판 | 주소 |
|---|---|---|
| `open-innovation` | 오픈이노베이션 | pachira.kr/open-innovation/ |
| `accelerator` | 액셀러레이터 | pachira.kr/accelerator/ |
| `investment-ir` | 투자유치·IR | pachira.kr/investment-ir/ |
| `certification-support` | 인증·정부지원사업 | pachira.kr/certification-support/ |
| `management-brand` | 경영·브랜드 | pachira.kr/management-brand/ |
| `notice` | 공지사항 | pachira.kr/notice/ |
| `news` | 뉴스 | pachira.kr/news/ |

**하나만** 씁니다. 여러 개 쓰면 주소가 이상해집니다.

---

## 3. 이미지 넣기

1. `assets` 폴더에 이미지 업로드 (Add file → Upload files)
2. 본문에서 이렇게 씁니다

```markdown
![설명글](/assets/파일이름.jpg)
```

파일 이름은 영문·숫자로 하는 편이 안전합니다.

---

## 4. 자주 하는 실수

| 증상 | 원인 |
|---|---|
| 글이 안 보임 | 파일 이름 날짜 형식이 틀림 / `---` 블록 없음 |
| 제목이 깨져 보임 | `title:` 값에 큰따옴표를 안 감쌈 (`:` `"` 가 들어가면 필수) |
| 엉뚱한 게시판에 들어감 | `categories` 철자 오류 — 위 표에서 복사해 쓰기 |
| 반영이 안 됨 | 배포에 1~2분 걸립니다. 그래도 안 되면 저장소 Actions 탭에서 실패 여부 확인 |

---

## 5. 연재(시리즈)로 글 올리기

같은 시리즈로 묶고 싶은 글은 앞부분에 두 줄만 더 넣으면 됩니다.

```markdown
---
layout: post
title: "핵심 제목만 씁니다"
categories: [open-innovation]
series: column
episode: 11
summary: "목록에 보일 한 줄 소개입니다."
---
```

- `series` — `column`(시사 칼럼) 또는 `basics`(기초편)
- `episode` — 회차 번호. 숫자만 씁니다

이 두 줄이 들어가면 자동으로 생기는 것들:

- 글 맨 위에 **연재 배지 + N화 / 전체 M화 진행 막대**
- 글 맨 아래에 **← 이전 화 / 다음 화 →** 버튼
- 글 맨 아래에 **전체 목차** 접기 상자
- `/open-innovation/` 목록 페이지의 **시리즈 블록**에 회차 순으로 자동 정렬

### 시리즈를 새로 만들 때

`_config.yml` 의 네 곳에 한 줄씩 추가합니다.

```yaml
series_order:   - 새이름
series_names:   새이름: "화면에 보일 시리즈 이름"
series_desc:    새이름: "한 줄 설명"
series_total:   새이름: 30      # 총 몇 화 예정인지
```

---

## 6. 본문 중간에 이미지 넣기 (네이버 블로그처럼)

이미지와 캡션을 같이 넣으려면 본문 중간에 이렇게 씁니다.

```html
<figure>
  <img src="/assets/파일이름.jpg" alt="이미지 설명">
  <figcaption>사진 아래 들어갈 캡션입니다</figcaption>
</figure>
```

이미지는 먼저 `assets` 폴더에 올려야 합니다 (Add file → Upload files). 파일 이름은 영문·숫자로 하는 편이 안전합니다.

### 이미지 자리만 미리 잡아두기

아직 이미지가 없으면 자리만 표시해둘 수 있습니다.

```html
<div class="img-slot"><span>이미지 자리 ① — 어떤 그림이 들어갈지</span><span>캡션: 들어갈 캡션</span></div>
```

점선 상자로 표시되고, 나중에 위의 `<figure>` 블록으로 바꾸면 됩니다. 칼럼 1~10편에는 이 자리표시자가 각각 두 개씩 들어가 있고, 바로 위에 바꿔 쓸 코드가 주석으로 적혀 있습니다.

---

## 7. 게시판을 새로 만들고 싶을 때

파일 두 곳을 고쳐야 합니다.

1. `_config.yml` 의 `category_names` 에 한 줄 추가
2. 같은 이름의 폴더를 만들고 그 안에 `index.html` 생성 (기존 `notice/index.html` 복사해서 값만 바꾸면 됩니다)

복잡하면 저한테 "○○ 게시판 만들어줘" 하고 말씀하시면 됩니다.

---

## 참고: 파일 구조

```
index.html              ← 랜딩페이지 (건드리지 않아도 됨)
_config.yml             ← 사이트 설정
_layouts/               ← 페이지 틀
_includes/              ← 공통 조각
assets/                 ← 이미지·CSS
_posts/                 ← 여기에 글을 씁니다
insight/ notice/ news/ … ← 게시판 목록 페이지
```
