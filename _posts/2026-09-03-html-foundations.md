---
layout: post
title: "HTML 기초: 웹페이지의 뼈대 이해하기"
date: 2026-09-03 14:30:00 +0900
categories: [Web, HTML]
tags: [html, beginner, web-fundamentals]
---

## 들어가며

웹페이지를 만드는 것은 집을 짓는 것과 비슷합니다. **HTML은 집의 뼈대와 벽**입니다. 집을 아무리 예쁘게 칠하고 꾸며도(CSS, 디자인) 뼈대가 튼튼하지 않으면 의미가 없죠. 

HTML은 **HyperText Markup Language**의 약자입니다. 여러 개의 문서를 링크로 연결(HyperText)한다는 의미이며, 태그(Markup)로 내용의 의미를 전달합니다.

## 1단계: 글자 관련 태그 — 텍스트에 의미 부여하기

### 제목과 문단 구조

웹페이지의 가장 기본이 되는 것은 텍스트입니다. 하지만 모든 글자가 같은 크기일 필요는 없습니다.

```
<h1>가장 큰 제목</h1>
<h2>부 제목</h2>
<h3>더 작은 제목</h3>
...
<h6>가장 작은 제목</h6>
```

**왜 h1부터 h6까지 있을까요?** 
- **h1**: 페이지의 주제 (보통 한 번만 사용)
- **h2-h3**: 섹션 구분
- **h4-h6**: 세부 항목

이렇게 계층 구조를 만들면 독자와 검색 엔진 모두 페이지 구조를 이해하기 쉬워집니다.

### 문단 태그

```
<p>이것은 문단입니다.</p>
```

HTML에서 아무리 많은 공백이나 줄바꿈을 입력해도 **한 칸의 공백으로만 표현**됩니다. 정확한 공백을 표현하려면 `<pre>` 태그를 사용합니다.

```
<pre>
  여러 칸 띄어쓰기            혹은
  줄 바꿈 등을 포함해서      화면에 표현합니다.
</pre>
```

### 텍스트 강조

같은 "굵은 글씨"도 두 가지 방법이 있습니다:

```
<strong>강한 강조</strong>  <!-- 의미적으로 중요함을 표현 -->
<b>시각적으로만 굵음</b>     <!-- 단지 굵은 스타일만 적용 -->
```

비유하자면, **strong은 선생님이 빨간펜으로 동그라미 친 부분**(의미 있음), **b는 단순히 형광펜으로 칠한 부분**(시각적만)입니다.

마찬가지로:
- `<em>` vs `<i>`: 기울임꼴 (em이 의미적 강조)
- `<mark>`: 형광펜 효과
- `<u>`: 밑줄
- `<small>`: 작은 글씨 (주석, 부가정보용)
- `<sub>`, `<sup>`: 아래첨자, 윗첨자
- `<s>`: 취소선

## 2단계: 목록 만들기 — 정보를 체계적으로 구성하기

웹에서 정보를 깔끔하게 보여주려면 목록 구조가 필수입니다.

### 순서가 있는 목록 (Ordered List)

```html
<ol>
  <li>첫 번째 단계</li>
  <li>두 번째 단계</li>
  <li>세 번째 단계</li>
</ol>
```

### 순서가 없는 목록 (Unordered List)

```html
<ul>
  <li>항목 1</li>
  <li>항목 2</li>
  <li>항목 3</li>
</ul>
```

**언제 어떤 목록을 쓸까요?**
- 요리 레시피, 설치 단계 → `<ol>` (순서가 중요)
- 장점 나열, 기능 목록 → `<ul>` (순서가 없음)

## 3단계: 표 만들기 — 데이터를 정렬하기

숫자나 통계 같은 구조화된 데이터는 표로 보여주는 것이 가장 효과적입니다.

```html
<table>
  <tr>              <!-- Table Row: 행 -->
    <th>이름</th>   <!-- Table Header: 헤더 -->
    <th>가격</th>
  </tr>
  <tr>
    <td>노트북</td> <!-- Table Data: 셀 -->
    <td>1,500,000원</td>
  </tr>
</table>
```

표 구조를 이해하는 팁: 엑셀 스프레드시트를 생각하면 됩니다. 각 `<tr>`은 행, 각 `<td>`는 셀입니다.

## 4단계: 영역 나누기 — 레이아웃 구조 만들기

웹페이지는 여러 섹션으로 나뉩니다. 이를 표현하는 태그들:

```html
<header>사이트 헤더 (로고, 네비게이션)</header>
<main>페이지의 주요 콘텐츠</main>
<section>주제별 섹션</section>
<article>독립적인 기사나 포스트</article>
<aside>옆에 있는 정보 (사이드바)</aside>
<footer>푸터 (저작권, 링크)</footer>
```

이 태그들은 시각적으로는 별 차이가 없지만, **컴퓨터에게 구조를 알려줍니다**. 검색 엔진이나 스크린 리더(시각장애인용)도 이 정보를 활용합니다.

## 5단계: 이미지와 미디어 — 시각적 요소 추가

### 이미지 삽입

```html
<img src="image.jpg" alt="이미지 설명">
```

**alt 속성이 중요한 이유:**
- 이미지가 로드되지 않으면 이 텍스트가 표시됩니다
- 시각장애인을 위한 스크린 리더가 읽어줍니다
- 검색 엔진이 이미지 내용을 이해합니다

### 동영상과 음성

```html
<audio controls>
  <source src="audio.mp3" type="audio/mpeg">
</audio>

<video width="640" height="480" controls>
  <source src="video.mp4" type="video/mp4">
</video>
```

`controls` 속성을 추가하면 재생/일시정지 버튼이 생깁니다.

## 6단계: 링크 — 웹을 "웹"으로 만들기

```html
<a href="https://example.com">클릭하세요</a>
<a href="about.html">같은 폴더의 다른 페이지</a>
<a href="#section2">페이지 내 특정 위치로 이동</a>
```

## 7단계: 폼 — 사용자 입력 받기

폼은 웹의 가장 강력한 기능입니다. 사용자가 정보를 입력하고 서버로 보낼 수 있게 합니다.

### 기본 폼 구조

```html
<form action="process.php" method="post">
  <label for="username">사용자명:</label>
  <input type="text" id="username" name="username" required>
  
  <button type="submit">제출</button>
</form>
```

**form 속성:**
- `action`: 폼 데이터를 받을 서버 주소
- `method`: 데이터 전송 방식
  - `GET`: URL에 데이터가 보임 (공개 정보용)
  - `POST`: URL에 데이터가 숨겨짐 (비밀번호 등)

### input 태그의 다양한 타입

```html
<!-- 텍스트 입력 -->
<input type="text" placeholder="이름을 입력하세요">
<input type="password" placeholder="비밀번호">
<input type="email" placeholder="이메일">
<input type="search" placeholder="검색">

<!-- 숫자 입력 -->
<input type="number" min="0" max="10">
<input type="range" min="0" max="100">  <!-- 슬라이더 -->

<!-- 날짜/시간 -->
<input type="date">
<input type="time">
<input type="month">

<!-- 선택 입력 -->
<input type="checkbox">  <!-- 여러 개 선택 가능 -->
<input type="radio">     <!-- 하나만 선택 가능 -->
<input type="color">     <!-- 색상 선택 -->
<input type="file">      <!-- 파일 업로드 -->
```

### 라디오 버튼과 체크박스

**라디오 버튼** (하나만 선택):
```html
<input type="radio" name="gender" value="male"> 남성
<input type="radio" name="gender" value="female"> 여성
```

**체크박스** (여러 개 선택):
```html
<input type="checkbox" name="hobby" value="reading"> 독서
<input type="checkbox" name="hobby" value="sports"> 운동
```

### 드롭다운 목록

```html
<select name="country">
  <option value="kr">한국</option>
  <option value="jp">일본</option>
  <option value="cn">중국</option>
</select>
```

### 여러 줄 입력

```html
<textarea rows="10" cols="50"></textarea>
```

`input type="text"`는 한 줄만 입력 가능하지만, `textarea`는 여러 줄을 입력할 수 있습니다.

## 핵심 원칙 정리

1. **의미가 중요하다** — 시각적 표현보다 의미 있는 태그 선택하기
2. **계층 구조를 만든다** — h1→h2→h3로 명확한 구조 제시하기
3. **접근성을 고려한다** — alt, label, required 등으로 모든 사용자 배려하기
4. **시멘틱 태그를 사용한다** — `<div>`보다 `<article>`, `<section>` 선택하기

## 다음 단계

HTML만으로는 디자인이 없습니다. 다음 포스트에서는 **CSS로 이 뼈대를 아름답게 꾸미는 방법**을 배워보겠습니다.

---

**더 학습하면 좋은 개념:**
- [MDN: HTML 요소 참조](https://developer.mozilla.org/ko/docs/Web/HTML/Element)
- [W3C: HTML 표준](https://html.spec.whatwg.org/)
- [HTML Validator](https://validator.w3.org/)
