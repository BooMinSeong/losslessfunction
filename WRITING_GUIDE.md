# Never Leave Ph.D 블로그 글 작성 가이드

이 문서는 Hugo 블로그에서 글을 작성하고 배포하는 방법을 설명합니다.

## 목차

1. [새 글 작성하기](#새-글-작성하기)
2. [카테고리별 작성 가이드](#카테고리별-작성-가이드)
3. [글 수정하기](#글-수정하기)
4. [로컬에서 미리보기](#로컬에서-미리보기)
5. [배포하기](#배포하기)

---

## 새 글 작성하기

### 1. 논문 리뷰 작성

```bash
hugo new content posts/papers/제목.md --kind papers
```

**예시:**
```bash
hugo new content posts/papers/yolov8-review.md --kind papers
```

생성된 파일을 열고 다음 내용을 채웁니다:

```markdown
---
title: "YOLOv8 리뷰"
date: 2025-12-16T10:00:00Z
draft: false  # true → false로 변경해야 배포됨
categories: ["papers"]
tags: ["computer vision", "object detection", "YOLO"]

# 논문 정보
paper:
  title: "YOLOv8: Real-time Object Detection"
  authors: ["Ultralytics Team"]
  venue: "GitHub"
  year: 2023
  arxiv_id: ""
  url: "https://github.com/ultralytics/ultralytics"

# AI 친화적 메타데이터
difficulty: "intermediate"
summary: "YOLO 시리즈의 최신 버전으로, 정확도와 속도를 모두 개선"
keywords: ["YOLOv8", "object detection", "real-time"]
---

## 논문 정보

- **Title**: YOLOv8: Real-time Object Detection
- **Authors**: Ultralytics Team
- **Venue**: GitHub
- **Year**: 2023
- **Link**: https://github.com/ultralytics/ultralytics

## 핵심 요약

YOLOv8은 YOLO 시리즈의 최신 버전으로...

(이하 내용 작성)
```

### 2. 생각 정리 작성

```bash
hugo new content posts/thoughts/제목.md --kind thoughts
```

**예시:**
```bash
hugo new content posts/thoughts/효율적인-연구-방법.md --kind thoughts
```

```markdown
---
title: "효율적인 연구 방법"
date: 2025-12-16T10:00:00Z
draft: false
categories: ["thoughts"]
tags: ["연구", "방법론"]

summary: "연구를 효율적으로 진행하기 위한 개인적인 전략"
---

## 서론

최근 연구를 진행하면서...

(자유롭게 내용 작성)
```

### 3. 음악 리뷰 작성

```bash
hugo new content posts/music/앨범명.md --kind music
```

**예시:**
```bash
hugo new content posts/music/kid-a-review.md --kind music
```

```markdown
---
title: "Kid A 리뷰"
date: 2025-12-16T10:00:00Z
draft: false
categories: ["music"]
tags: ["radiohead", "electronic", "alternative"]

# 앨범 정보
album:
  title: "Kid A"
  artist: "Radiohead"
  year: 2000
  genre: ["Electronic", "Art Rock", "Experimental"]
  label: "Parlophone"

summary: "Radiohead의 실험적 걸작"
cover_image: ""
rating: 10
---

## 앨범 정보

- **Artist**: Radiohead
- **Album**: Kid A
- **Year**: 2000
- **Genre**: Electronic, Art Rock, Experimental
- **Label**: Parlophone

## 트랙리스트

1. Everything in Its Right Place
2. Kid A
3. The National Anthem
4. How to Disappear Completely
5. Treefingers
...

(이하 내용 작성)
```

---

## 카테고리별 작성 가이드

### 논문 리뷰 (Papers)

**필수 항목:**
- Front Matter의 `paper` 섹션 채우기 (title, authors, venue, year, url)
- `difficulty` 설정: beginner, intermediate, advanced 중 선택
- `summary`: 한 줄 요약
- `keywords`: 핵심 키워드 배열

**본문 구조:**
1. 논문 정보
2. 핵심 요약
3. 주요 내용 (문제 정의, 제안 방법, 실험 결과)
4. 개인 평가 (장점, 한계, 적용 가능성)
5. 관련 자료

### 생각 정리 (Thoughts)

**자유 형식**
- 연구, 개발, 학습 과정에서의 인사이트
- 특별한 구조 없이 자유롭게 작성
- tags를 적절히 활용하여 분류

### 음악 리뷰 (Music)

**필수 항목:**
- Front Matter의 `album` 섹션 채우기
- `rating`: 0-10 점수 설정

**본문 구조:**
1. 앨범 정보
2. 트랙리스트
3. 감상평 (전체적인 인상, 인상 깊은 트랙, 추천 대상)
4. 평점

---

## 글 수정하기

### 기존 글 찾기

```bash
# 모든 포스트 목록 보기
ls -R content/posts/

# 특정 카테고리 글 보기
ls content/posts/papers/
ls content/posts/thoughts/
ls content/posts/music/
```

### 수정 방법

1. 원하는 `.md` 파일을 에디터로 열기
2. 내용 수정
3. 저장
4. [배포하기](#배포하기) 섹션 참고하여 푸시

---

## 로컬에서 미리보기

글을 작성한 후 배포 전에 로컬에서 확인할 수 있습니다.

### Hugo 개발 서버 실행

```bash
# 드래프트 포함하여 미리보기
hugo server -D

# 또는 드래프트 제외
hugo server
```

실행 후 브라우저에서 `http://localhost:1313` 접속

### 서버 종료

`Ctrl + C`

---

## 배포하기

### 1. draft 상태 확인

**중요**: 배포하려면 Front Matter의 `draft`를 `false`로 설정해야 합니다.

```markdown
---
title: "제목"
date: 2025-12-16T10:00:00Z
draft: false  # ← 이 부분을 false로!
---
```

### 2. Git으로 변경사항 커밋

```bash
# 현재 상태 확인
git status

# 변경된 파일 추가
git add .

# 커밋 (의미 있는 메시지 작성)
git commit -m "Add: YOLOv8 논문 리뷰 추가"
```

**커밋 메시지 예시:**
- `Add: 새 논문 리뷰 - Transformer 아키텍처`
- `Update: 학습 방법론 글 수정`
- `Fix: 음악 리뷰 오타 수정`

### 3. GitHub에 푸시

```bash
# 현재 브랜치 확인
git branch

# 푸시
git push origin <브랜치명>

# 예시:
git push origin claude/setup-hugo-blog-u0Ial
```

### 4. Pull Request 생성 (메인 브랜치 사용 시)

1. GitHub 저장소 페이지 접속
2. "Compare & pull request" 버튼 클릭
3. PR 제목과 설명 작성
4. "Create pull request" 클릭
5. "Merge pull request" 클릭하여 main 브랜치에 병합

### 5. 배포 확인

- Cloudflare Pages가 자동으로 빌드 시작 (1-2분 소요)
- https://losslessfunction.pages.dev/ 에서 변경사항 확인
- Cloudflare Pages 대시보드에서 배포 로그 확인 가능

---

## 팁과 트릭

### 1. 마크다운 문법

```markdown
# 제목 1
## 제목 2
### 제목 3

**볼드체**
*이탤릭체*

- 리스트 항목 1
- 리스트 항목 2

1. 번호 리스트 1
2. 번호 리스트 2

[링크 텍스트](https://example.com)

![이미지 설명](/images/example.jpg)

`인라인 코드`

​```python
# 코드 블록
def hello():
    print("Hello, World!")
​```
```

### 2. 이미지 추가하기

이미지는 `static/images/` 폴더에 저장:

```bash
# 이미지 복사
cp ~/Downloads/image.jpg static/images/

# 마크다운에서 참조
![설명](/images/image.jpg)
```

### 3. 태그 활용

태그를 일관성 있게 사용하면 나중에 검색이 쉽습니다:

```yaml
tags: ["machine learning", "computer vision", "transformer"]
```

### 4. draft 관리

작성 중인 글은 `draft: true`로 설정:
- 로컬 미리보기: `hugo server -D`
- 배포 시 자동으로 제외됨

### 5. 날짜 형식

Front Matter의 date는 ISO 8601 형식 사용:
```yaml
date: 2025-12-16T14:30:00+09:00
```

---

## 문제 해결

### Q: 글이 배포되지 않아요

**확인사항:**
1. `draft: false`로 설정했는지 확인
2. Git에 커밋하고 푸시했는지 확인
3. Cloudflare Pages에서 빌드 에러가 없는지 확인

### Q: 한글이 깨져요

- 파일을 UTF-8 인코딩으로 저장했는지 확인

### Q: 이미지가 표시되지 않아요

- 이미지 경로가 `/images/파일명.jpg` 형식인지 확인
- 이미지 파일이 `static/images/` 폴더에 있는지 확인
- 파일명에 공백이나 특수문자가 없는지 확인

### Q: 로컬 Hugo 서버가 실행되지 않아요

```bash
# Hugo 버전 확인
hugo version

# 최신 버전 설치 필요 시 (0.146.0 이상 권장)
```

---

## 워크플로우 요약

```
1. 새 글 작성
   ↓
   hugo new content posts/[category]/제목.md --kind [category]

2. 내용 작성
   ↓
   에디터에서 .md 파일 편집

3. 로컬 확인 (선택)
   ↓
   hugo server -D

4. draft: false 설정
   ↓
   Front Matter 수정

5. Git 커밋
   ↓
   git add . && git commit -m "메시지"

6. 푸시
   ↓
   git push origin 브랜치명

7. PR 생성 및 병합 (main 브랜치 사용 시)
   ↓
   GitHub에서 PR 생성 및 병합

8. 배포 확인
   ↓
   https://losslessfunction.pages.dev/
```

---

## 추가 참고 자료

- Hugo 공식 문서: https://gohugo.io/documentation/
- PaperMod 테마 문서: https://github.com/adityatelange/hugo-PaperMod/wiki
- 마크다운 가이드: https://www.markdownguide.org/

---

**Happy Writing! 🚀**
