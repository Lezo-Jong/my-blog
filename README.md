# my-blog 미니멀 테마 (게임 + AI 에이전트)

devlopr-jekyll 대신 쓸 수 있는, 미니멀하고 관리하기 쉬운 자체 제작 Jekyll 테마입니다.

## 적용 방법

1. 기존 `my-blog` 저장소를 백업해두세요 (브랜치를 하나 파두면 안전합니다).
2. 저장소의 기존 파일들 중 아래 항목을 이 폴더의 내용으로 교체하세요.
   - `_config.yml`
   - `_layouts/`
   - `_includes/`
   - `assets/css/style.css`
   - `index.html`
   - `game.html`, `ai-agent.html`, `about.md`
   - `Gemfile`
3. 기존 devlopr-jekyll 테마의 잔재(예: `assets/bower_components/`, 기존 테마 전용 `_data/`, `_sass/` 등)는 삭제해도 됩니다. 이 테마는 별도 의존성이 없습니다.
4. `_config.yml`의 `baseurl`이 실제 저장소 이름과 일치하는지 꼭 확인하세요 (지금은 `/my-blog`로 되어 있습니다).
5. 기존에 쓰던 글이 있다면 `_posts/` 폴더의 `.md` 파일들은 그대로 두고, front matter의 `categories`만 `[game]` 또는 `[ai-agent]`로 정리해주면 이 테마의 카테고리 페이지에 자동으로 걸립니다.
6. 커밋 후 푸시하면 GitHub Pages가 자동으로 다시 빌드합니다.

## 로컬에서 미리보기 (선택)

```
bundle install
bundle exec jekyll serve
```

`http://localhost:4000/my-blog/` 에서 확인할 수 있습니다.

## 새 글 쓰는 법

`_posts/` 폴더에 `YYYY-MM-DD-제목.md` 형식으로 파일을 추가하고, 맨 위에 아래처럼 front matter를 넣으면 됩니다.

```
---
layout: post
title: "글 제목"
categories: [game]   # 또는 [ai-agent]
---

내용 작성...
```

예시 글 2개(`_posts/2026-08-28-예시-*.md`)는 지우거나 실제 내용으로 바꿔서 쓰세요.
