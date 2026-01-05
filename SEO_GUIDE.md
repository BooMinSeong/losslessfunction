# Never Leave Ph.D 블로그 SEO 가이드

이 문서는 블로그를 검색 엔진에 노출시키고 최적화하는 방법을 설명합니다.

## 목차

1. [현재 SEO 설정](#현재-seo-설정)
2. [Google Search Console 등록](#google-search-console-등록)
3. [Naver 검색 등록](#naver-검색-등록)
4. [검색 노출 확인](#검색-노출-확인)
5. [SEO 최적화 팁](#seo-최적화-팁)

---

## 현재 SEO 설정

블로그에 이미 적용된 SEO 설정:

- ✅ **sitemap.xml**: 자동 생성 (https://losslessfunction.pages.dev/sitemap.xml)
- ✅ **robots.txt**: 검색 엔진 크롤러 허용 설정
- ✅ **RSS 피드**: 자동 생성 (https://losslessfunction.pages.dev/index.xml)
- ✅ **구조화된 메타데이터**: Front Matter에 논문 정보, 앨범 정보 등 포함
- ✅ **깨끗한 URL**: 한글 제목도 URL-safe하게 변환
- ✅ **모바일 최적화**: 반응형 디자인

---

## Google Search Console 등록

### 1. Google Search Console 접속

https://search.google.com/search-console 접속 후 Google 계정으로 로그인

### 2. 속성 추가

1. 좌측 상단 드롭다운 메뉴 클릭
2. "속성 추가" 선택
3. **URL 접두어** 선택
4. `https://losslessfunction.pages.dev/` 입력
5. "계속" 클릭

### 3. 소유권 확인

#### 방법 1: HTML 파일 업로드 (권장)

1. Google이 제공하는 HTML 파일 다운로드 (예: `google1234567890abcdef.html`)
2. 블로그 저장소의 `static/` 폴더에 파일 복사:
   ```bash
   cp ~/Downloads/google1234567890abcdef.html static/
   ```
3. Git 커밋 및 푸시:
   ```bash
   git add static/google*.html
   git commit -m "Add Google Search Console verification file"
   git push origin 브랜치명
   ```
4. Cloudflare Pages 배포 완료 대기 (1-2분)
5. Google Search Console에서 "확인" 버튼 클릭

#### 방법 2: HTML 태그 (대안)

1. Google이 제공하는 메타 태그 복사
2. `layouts/partials/extend_head.html` 파일 생성:
   ```bash
   mkdir -p layouts/partials
   ```
3. 파일에 메타 태그 추가:
   ```html
   <meta name="google-site-verification" content="여기에_코드_입력" />
   ```
4. 커밋 및 푸시

### 4. Sitemap 제출

소유권 확인 후:

1. 좌측 메뉴에서 "Sitemaps" 선택
2. "새 사이트맵 추가" 입력란에 `sitemap.xml` 입력
3. "제출" 클릭

### 5. 색인 요청

1. 좌측 메뉴에서 "URL 검사" 선택
2. 블로그 URL 입력 (예: `https://losslessfunction.pages.dev/`)
3. "색인 생성 요청" 클릭
4. 주요 페이지들도 개별적으로 색인 요청:
   - 홈페이지
   - About 페이지
   - 주요 포스트 몇 개

---

## Naver 검색 등록

### 1. Naver Search Advisor 접속

https://searchadvisor.naver.com/ 접속 후 Naver 계정으로 로그인

### 2. 웹마스터 도구 사이트 등록

1. "웹마스터 도구" 메뉴 선택
2. "사이트 추가" 클릭
3. `https://losslessfunction.pages.dev/` 입력

### 3. 소유권 확인

#### HTML 파일 업로드 방식:

1. Naver가 제공하는 HTML 파일 다운로드
2. `static/` 폴더에 복사
3. Git 커밋 및 푸시
4. "소유확인" 클릭

### 4. 사이트맵 제출

1. "요청" → "사이트맵 제출" 선택
2. `https://losslessfunction.pages.dev/sitemap.xml` 입력
3. "확인" 클릭

### 5. RSS 제출 (선택)

1. "요청" → "RSS 제출" 선택
2. `https://losslessfunction.pages.dev/index.xml` 입력

---

## 검색 노출 확인

### Google 검색

**사이트 전체 검색:**
```
site:losslessfunction.pages.dev
```

**특정 페이지 검색:**
```
site:losslessfunction.pages.dev "Never Leave Ph.D"
```

### Naver 검색

```
site:losslessfunction.pages.dev
```

### 주의사항

- **초기 색인 시간**: 보통 1-7일 소요
- **완전한 노출**: 2-4주 소요 가능
- **정기적인 콘텐츠 업데이트**가 검색 순위에 도움

---

## SEO 최적화 팁

### 1. 제목 최적화

**좋은 제목:**
- 명확하고 구체적
- 30-60자 사이
- 키워드 포함

**예시:**
```markdown
title: "YOLOv8 논문 리뷰: 실시간 객체 탐지의 최신 기술"
```

### 2. Summary 활용

모든 포스트에 `summary` 작성:

```yaml
summary: "YOLOv8의 주요 개선사항과 성능 평가를 자세히 분석합니다."
```

- 검색 결과 스니펫으로 표시됨
- 150-160자 권장

### 3. 태그와 카테고리

**일관성 있는 태그 사용:**
```yaml
categories: ["papers"]
tags: ["computer vision", "object detection", "YOLO", "deep learning"]
```

- 소문자 사용
- 단어는 하이픈(-) 또는 공백으로 구분
- 3-7개 태그 권장

### 4. 내부 링크

관련 포스트 간 링크 추가:

```markdown
[이전 YOLO 리뷰](/posts/papers/yolov5-review/)도 참고하세요.
```

### 5. 이미지 최적화

이미지 사용 시:

```markdown
![YOLOv8 아키텍처](/images/yolov8-architecture.png)
```

- 이미지에 설명적인 alt 텍스트 사용
- 파일명도 의미 있게 작성 (`image1.png` → `yolov8-architecture.png`)
- 이미지 용량 최적화 (500KB 이하 권장)

### 6. 정기적인 업데이트

- **주 1-2회** 새 글 발행
- 기존 글도 주기적으로 업데이트
- 날짜가 변경되면 검색 엔진이 재크롤링

### 7. 외부 링크

- 권위 있는 사이트 (논문, 공식 문서) 링크
- 너무 많은 외부 링크는 피하기

### 8. 모바일 최적화

- 이미 반응형 디자인 적용됨 ✅
- 긴 문장보다 짧은 단락 선호
- 코드 블록은 스크롤 가능하도록

### 9. 페이지 속도

현재 설정:
- Cloudflare Pages CDN 사용 ✅
- 정적 사이트로 빠른 로딩 ✅

추가 최적화:
- 이미지 압축 (TinyPNG, ImageOptim 등)
- 불필요한 JavaScript 최소화

### 10. 소셜 미디어 공유

포스트를 작성하면:
- Twitter/X에 공유
- LinkedIn에 공유 (논문 리뷰)
- 관련 커뮤니티에 공유

소셜 신호(Social signals)가 SEO에 간접적으로 도움

---

## 검색 순위 모니터링

### Google Search Console 활용

1. **실적** 메뉴:
   - 노출수, 클릭수, CTR, 평균 순위 확인
   - 어떤 검색어로 유입되는지 분석

2. **커버리지**:
   - 색인 생성된 페이지 수 확인
   - 오류 확인 및 수정

3. **개선 사항**:
   - 모바일 사용성 점검
   - 페이지 경험 확인

### 주요 지표

- **CTR (클릭률)**: 검색 결과에서 클릭된 비율
  - 제목과 설명 최적화로 개선
- **노출수**: 검색 결과에 표시된 횟수
  - 꾸준한 콘텐츠 발행으로 증가
- **평균 순위**: 검색 결과 순위
  - 품질 높은 콘텐츠로 개선

---

## 체크리스트

### 초기 설정 (1회)
- [ ] Google Search Console 등록
- [ ] Google에 sitemap 제출
- [ ] Naver Search Advisor 등록
- [ ] Naver에 sitemap 제출
- [ ] 소유권 확인 파일 업로드

### 글 작성 시마다
- [ ] 명확한 제목 작성 (30-60자)
- [ ] summary 작성 (150-160자)
- [ ] 적절한 태그 3-7개 추가
- [ ] 이미지에 alt 텍스트 추가
- [ ] 내부 링크 1-3개 포함
- [ ] 외부 링크 (출처) 추가

### 정기적으로 (월 1회)
- [ ] Google Search Console 실적 확인
- [ ] 인기 검색어 분석
- [ ] 오래된 글 업데이트
- [ ] 깨진 링크 확인

---

## 유용한 도구

### SEO 분석
- [Google Search Console](https://search.google.com/search-console)
- [Naver Search Advisor](https://searchadvisor.naver.com/)
- [PageSpeed Insights](https://pagespeed.web.dev/) - 페이지 속도 측정

### 키워드 리서치
- [Google Trends](https://trends.google.com/)
- [Naver 키워드 도구](https://searchad.naver.com/)

### 이미지 최적화
- [TinyPNG](https://tinypng.com/)
- [ImageOptim](https://imageoptim.com/)

### 구조화된 데이터 테스트
- [Schema Markup Validator](https://validator.schema.org/)

---

## FAQ

### Q: 언제 검색에 노출되나요?
A: Google/Naver에 등록 후 1-7일 내 색인 생성, 완전한 노출까지 2-4주 소요

### Q: 검색 순위를 빠르게 올리는 방법은?
A:
1. 품질 높은 콘텐츠 지속적으로 발행
2. 타겟 키워드 최적화
3. 외부에서 링크 유도 (소셜 미디어, 커뮤니티)
4. 기존 글 업데이트

### Q: 한글 URL이 문제가 되나요?
A: Hugo가 자동으로 URL-safe하게 변환하므로 문제없습니다.

### Q: 얼마나 자주 글을 써야 하나요?
A: 주 1-2회 권장. 꾸준함이 중요합니다.

### Q: 검색 유입이 없어요
A:
1. Google Search Console에서 색인 상태 확인
2. 경쟁 키워드 피하고 롱테일 키워드 공략
3. 최소 10-20개 글 발행 후 효과 나타남

---

## 추가 참고 자료

- [Google SEO 초보자 가이드](https://developers.google.com/search/docs/beginner/seo-starter-guide)
- [Naver 검색 등록 가이드](https://searchadvisor.naver.com/guide)
- [Hugo SEO Best Practices](https://gohugo.io/templates/internal#open-graph)

---

**검색 엔진 최적화는 장기전입니다. 꾸준히 양질의 콘텐츠를 발행하는 것이 가장 중요합니다!**
