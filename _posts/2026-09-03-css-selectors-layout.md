---
layout: post
title: "CSS 완전 정복: 선택자부터 레이아웃까지"
date: 2026-09-03 15:00:00 +0900
categories: [git]
tags: [css, selectors, layout, flexbox, grid, beginner]
---

## 들어가며

이전 포스트에서 HTML은 웹페이지의 "뼈대"라고 했습니다. 그렇다면 **CSS는 화장품입니다** — 페이지를 아름답게 만들고, 배치하고, 애니메이션을 추가합니다.

CSS를 다루는 핵심은 두 가지입니다:
1. **올바른 요소를 선택하기** (선택자)
2. **선택된 요소를 배치하기** (레이아웃)

이 포스트에서는 이 두 가지를 마스터해봅시다.

## 1단계: CSS 선택자 — 올바른 요소를 찾기

CSS에서 스타일을 적용하려면 먼저 "어떤 요소에 적용할 건지" 명확히 해야 합니다. 이것이 **선택자(selector)**의 역할입니다.

### 전체 선택자 (*)

```css
* {
  color: red;
}
```

페이지의 **모든 요소**를 선택합니다. 거의 사용하지 않으며, 사용해도 매우 일반적인 스타일만 적용합니다.

### 태그 선택자

```css
li {
  color: blue;
}
```

**특정 태그의 모든 요소**를 선택합니다. 위 예제는 모든 `<li>` 요소를 파란색으로 만듭니다.

**장점**: 같은 종류의 요소에 일괄 적용
**단점**: 같은 태그의 일부만 다르게 꾸밀 수 없음

### ID 선택자 (#)

```css
#special-header {
  color: purple;
  background-color: yellow;
}
```

```html
<h1 id="special-header">이 제목만 특별해</h1>
```

ID는 **페이지 내에서 유일**해야 합니다. 특정 하나의 요소를 선택할 때 사용합니다.

**규칙**: 한 페이지 내에서 같은 ID를 여러 번 사용하면 안 됩니다.

### 클래스 선택자 (.)

```css
.highlight {
  color: aquamarine;
  background-color: black;
}
```

```html
<p class="highlight">강조된 문단 1</p>
<p class="highlight">강조된 문단 2</p>
<p class="highlight">강조된 문단 3</p>
```

클래스는 **여러 요소에 같은 스타일**을 적용할 때 사용합니다. ID와 달리 재사용이 자유롭습니다.

### 선택자 우선순위 — 충돌이 생기면?

여러 선택자가 같은 요소를 지정하면 어느 것이 적용될까요?

```css
* { color: red; }           /* 우선순위: 가장 낮음 */
li { color: blue; }         /* 우선순위: 중간 */
.highlight { color: green; }  /* 우선순위: 높음 */
#important { color: purple; }   /* 우선순위: 가장 높음 */
```

**우선순위 순서** (낮음 → 높음):
1. 전체 선택자 (`*`)
2. 태그 선택자 (`li`, `p`, `div` 등)
3. 클래스 선택자 (`.class`)
4. ID 선택자 (`#id`)
5. 인라인 스타일 (`style="..."`) — 가장 높음

**비유하자면:**
- **전체 선택자**: 학교 전체에 공지
- **태그 선택자**: 특정 학년 전체에 공지
- **클래스 선택자**: 특정 반(여러 반 가능)에 공지
- **ID 선택자**: 특정 학생 한 명에게만 공지

같은 우선순위를 가진 선택자가 충돌하면, **나중에 정의된 것**이 적용됩니다.

## 2단계: 박스 모델 — 요소의 크기와 간격

모든 HTML 요소는 상자(box) 형태로 생각할 수 있습니다.

```
┌─────────────────────────────────────┐
│ margin (바깥 여백)                   │
│ ┌───────────────────────────────┐   │
│ │ border (테두리)                 │   │
│ │ ┌───────────────────────────┐ │   │
│ │ │ padding (안쪽 여백)        │ │   │
│ │ │ ┌───────────────────────┐ │ │   │
│ │ │ │ content (콘텐츠)      │ │ │   │
│ │ │ └───────────────────────┘ │ │   │
│ │ └───────────────────────────┘ │   │
│ └───────────────────────────────┘   │
└─────────────────────────────────────┘
```

```css
.card {
  width: 300px;           /* 콘텐츠 너비 */
  padding: 20px;          /* 내부 여백 */
  border: 2px solid #333; /* 테두리 */
  margin: 10px;           /* 외부 여백 */
}
```

**각 부분의 역할:**
- **content**: 텍스트나 이미지 같은 실제 내용
- **padding**: 콘텐츠와 테두리 사이의 공간
- **border**: 상자의 테두리
- **margin**: 다른 요소와의 거리

## 3단계: 디스플레이 속성 — 요소의 배치 방식

HTML 요소는 기본적으로 두 가지 방식으로 배치됩니다.

### Block 요소 (블록)

```css
div {
  display: block;
}
```

**특징:**
- 항상 새 줄에서 시작
- 가로 폭을 전부 차지
- width와 height 설정 가능
- **예**: `<div>`, `<p>`, `<h1>`, `<header>`

시각적으로는 상자가 세로로 쌓입니다:
```
┌─────────────┐
│ Block 1     │
└─────────────┘
┌─────────────┐
│ Block 2     │
└─────────────┘
```

### Inline 요소 (인라인)

```css
span {
  display: inline;
}
```

**특징:**
- 텍스트처럼 옆으로 붙음
- 필요한 너비만 차지
- width와 height 설정 불가
- **예**: `<span>`, `<a>`, `<strong>`, `<em>`

```
This is [inline 1][inline 2][inline 3] text.
```

### Inline-Block 요소 (하이브리드)

```css
button {
  display: inline-block;
}
```

**특징:**
- 텍스트처럼 옆으로 붙음 (inline)
- 동시에 width와 height 설정 가능 (block)
- **예**: `<button>`, `<img>`, `<input>`

## 4단계: Flexbox — 현대적인 행/렬 배치

웹페이지에서 요소들을 "정렬"해야 하는 경우가 매우 많습니다. Flexbox는 이를 매우 쉽게 만들어줍니다.

### 부모와 자식의 개념

```html
<div class="container">     <!-- 부모 (Flex Container) -->
  <div class="item">Item 1</div>    <!-- 자식 -->
  <div class="item">Item 2</div>    <!-- 자식 -->
  <div class="item">Item 3</div>    <!-- 자식 -->
</div>
```

```css
.container {
  display: flex;
  gap: 10px;  /* 자식 요소들 사이의 간격 */
}
```

**기본 동작:**
- 자식 요소들이 **왼쪽에서 오른쪽**으로 정렬됩니다
- 화면 크기에 따라 **자동으로 조정**됩니다

### 주요 Flex 속성

#### 1. justify-content — 가로 정렬

```css
.container {
  display: flex;
  justify-content: space-between;  /* 양쪽 끝에 배치 */
}
```

옵션:
- `flex-start`: 왼쪽 정렬 (기본값)
- `flex-end`: 오른쪽 정렬
- `center`: 가운데 정렬
- `space-between`: 양쪽 끝, 중간은 균등
- `space-around`: 모두 균등 간격

#### 2. align-items — 세로 정렬

```css
.container {
  display: flex;
  align-items: center;  /* 세로 가운데 정렬 */
  height: 200px;
}
```

#### 3. flex-direction — 방향 변경

```css
.container {
  display: flex;
  flex-direction: column;  /* 아래로 쌓기 (세로 배치) */
}
```

옵션:
- `row`: 왼쪽에서 오른쪽 (기본값)
- `column`: 위에서 아래
- `row-reverse`: 오른쪽에서 왼쪽
- `column-reverse`: 아래에서 위

### 실제 예제: 상품 카드 나열

```html
<main class="product-list">
  <div class="card">
    <img src="product1.jpg">
    <h3>노트북 거치대</h3>
    <p class="price">17,000원</p>
  </div>
  
  <div class="card">
    <img src="product2.jpg">
    <h3>마우스</h3>
    <p class="price">25,000원</p>
  </div>
</main>
```

```css
.product-list {
  display: flex;
  gap: 20px;
  flex-wrap: wrap;  /* 화면이 좁으면 다음 줄로 */
}

.card {
  flex: 1;  /* 각 카드가 균등한 너비 */
  min-width: 250px;
  padding: 20px;
  border: 1px solid #ddd;
}
```

## 5단계: Grid — 2차원 레이아웃

Flexbox는 주로 **1차원**(행 또는 열)을 다루지만, Grid는 **2차원**(행과 열 동시)을 다룹니다.

```html
<main class="grid-list">
  <div class="card">카드 1</div>
  <div class="card">카드 2</div>
  <div class="card">카드 3</div>
  <div class="card">카드 4</div>
  <div class="card">카드 5</div>
  <div class="card">카드 6</div>
</main>
```

```css
.grid-list {
  display: grid;
  grid-template-columns: repeat(3, 1fr);  /* 3개 열, 균등 너비 */
  gap: 20px;
}
```

**동작:**
- 자동으로 3개씩 행으로 정렬
- 화면이 좁아지면 `grid-template-columns` 값을 수정

### Flexbox vs Grid

| 특징 | Flexbox | Grid |
|------|---------|------|
| 차원 | 1차원 (주로) | 2차원 |
| 사용 예 | 네비게이션, 카드 나열 | 페이지 레이아웃, 대시보드 |
| 학습 난도 | 쉬움 | 중간 |

## 6단계: Tailwind CSS — 클래스명으로 스타일링

기존 CSS 방식:
```css
.button {
  padding: 10px 20px;
  background-color: blue;
  color: white;
  border-radius: 5px;
  cursor: pointer;
}
```

```html
<button class="button">클릭</button>
```

Tailwind 방식:
```html
<button class="px-5 py-2 bg-blue-500 text-white rounded cursor-pointer">
  클릭
</button>
```

### Tailwind의 장점

1. **빠른 프로토타이핑** — CSS 파일을 왔다갔다할 필요 없음
2. **일관성** — 미리 정의된 색상, 크기 등 사용
3. **반응형 설계가 쉬움** — `md:`, `lg:` 같은 프리픽스 사용

### Tailwind의 단점

1. **HTML이 길어짐** — 클래스명이 많아짐
2. **학습곡선** — 클래스명을 외워야 함
3. **CSS 파일 크기** — 최적화 필요

### 일반 CSS vs Tailwind

**일반 CSS를 사용할 때:**
```css
/* style.css */
.card {
  padding: 20px;
  border: 1px solid #ddd;
  border-radius: 8px;
}

.card:hover {
  box-shadow: 0 4px 8px rgba(0,0,0,0.1);
}
```

**Tailwind를 사용할 때:**
```html
<div class="p-5 border border-gray-300 rounded-lg hover:shadow-lg">
  콘텐츠
</div>
```

## 핵심 정리

| 개념 | 언제 사용 | 예 |
|------|----------|-----|
| 선택자 | 스타일을 적용할 요소 선택 | `.highlight`, `#header` |
| 우선순위 | 여러 CSS 규칙의 충돌 해결 | ID > 클래스 > 태그 |
| Flexbox | 1차원 배치 (행 또는 열) | 네비게이션 바, 아이템 나열 |
| Grid | 2차원 배치 (행과 열) | 페이지 레이아웃, 갤러리 |
| Tailwind | 빠른 스타일링 | 프로토타입, 소규모 프로젝트 |

## 실전 예제: 완성된 카드 레이아웃

```html
<main class="product-grid">
  <article class="product-card">
    <div class="product-image"></div>
    <h3 class="product-title">노트북 거치대</h3>
    <p class="product-price">17,000원</p>
    <p class="product-description">
      각도를 6단계로 조절할 수 있습니다.
    </p>
  </article>
  <!-- 더 많은 카드... -->
</main>
```

```css
.product-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
  gap: 20px;
  padding: 20px;
}

.product-card {
  border: 1px solid #e0e0e0;
  border-radius: 8px;
  padding: 16px;
  transition: box-shadow 0.3s ease;
}

.product-card:hover {
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.1);
}

.product-image {
  width: 100%;
  height: 200px;
  background-color: #f0f0f0;
  border-radius: 6px;
  margin-bottom: 12px;
}

.product-title {
  font-size: 18px;
  font-weight: bold;
  margin: 10px 0;
}

.product-price {
  color: #e74c3c;
  font-size: 16px;
  font-weight: bold;
}

.product-description {
  font-size: 14px;
  color: #666;
  line-height: 1.5;
}
```

## 다음 단계

HTML로 구조를 만들고, CSS로 스타일을 적용했습니다. 이제 **JavaScript로 상호작용**을 추가할 수 있습니다. 사용자가 버튼을 클릭할 때, 마우스를 올릴 때 등의 이벤트를 처리할 수 있죠.

---

**더 학습하면 좋은 개념:**
- [MDN: CSS 선택자](https://developer.mozilla.org/ko/docs/Web/CSS/CSS_Selectors)
- [MDN: Flexbox](https://developer.mozilla.org/ko/docs/Web/CSS/CSS_Flexible_Box_Layout)
- [MDN: Grid](https://developer.mozilla.org/ko/docs/Web/CSS/CSS_Grid_Layout)
- [Tailwind CSS 공식 문서](https://tailwindcss.com/docs)
- [CSS Tricks: Flexbox 완벽 가이드](https://css-tricks.com/snippets/css/a-guide-to-flexbox/)
