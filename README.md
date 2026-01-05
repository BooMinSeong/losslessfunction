# Never Leave Ph.D

Hugo + Cloudflare Pages로 만든 개인 블로그입니다.

**Blog URL**: https://losslessfunction.pages.dev/

## 블로그 주제

- 논문 리뷰 (Machine Learning, Computer Vision)
- 생각 정리
- 음악 리뷰

## 기술 스택

- **Static Site Generator**: Hugo
- **Theme**: PaperMod
- **Hosting**: Cloudflare Pages
- **Version Control**: GitHub

## 로컬 실행

```bash
# 개발 서버 실행 (드래프트 포함)
hugo server -D

# 빌드
hugo
```

## 가이드 문서

**📝 [WRITING_GUIDE.md](WRITING_GUIDE.md)** - 글 작성 및 배포 가이드

**🔍 [SEO_GUIDE.md](SEO_GUIDE.md)** - 검색 엔진 최적화 및 노출 가이드

### 빠른 시작

```bash
# 논문 리뷰
hugo new content posts/papers/논문제목.md --kind papers

# 생각 정리
hugo new content posts/thoughts/제목.md --kind thoughts

# 음악 리뷰
hugo new content posts/music/앨범명.md --kind music
```

### 배포

1. 글 작성 후 `draft: false`로 설정
2. Git 커밋: `git add . && git commit -m "메시지"`
3. 푸시: `git push origin 브랜치명`
4. Cloudflare Pages가 자동으로 빌드 및 배포

## 프로젝트 구조

```
losslessfunction/
├── content/
│   ├── posts/
│   │   ├── papers/      # 논문 리뷰
│   │   ├── thoughts/    # 생각 정리
│   │   └── music/       # 음악 리뷰
│   └── about.md
├── archetypes/          # 글 템플릿
├── static/
│   └── images/
├── themes/
│   └── PaperMod/
└── hugo.yaml
```

## AI 친화적 특징

- 구조화된 Front Matter (논문 정보, 앨범 정보 등)
- JSON 출력 지원 (AI가 쉽게 파싱)
- 일관된 템플릿 구조
