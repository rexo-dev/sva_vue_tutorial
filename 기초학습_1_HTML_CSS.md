# 📘 HTML/CSS 기초 - 태양계 프로젝트 필수 개념

태양계 프로젝트를 이해하기 위해 꼭 알아야 할 HTML과 CSS 기초입니다.

---

## 📋 목차
1. [HTML 기초](#1-html-기초)
2. [CSS 기초](#2-css-기초)
3. [프로젝트에서 사용되는 HTML/CSS](#3-프로젝트에서-사용되는-htmlcss)
4. [연습 문제](#4-연습-문제)

---

## 1. HTML 기초

### 1-1. HTML이란?

**HTML (HyperText Markup Language)**
- 웹 페이지의 **구조**를 만드는 언어
- "마크업 언어" = 태그로 내용을 표시

**비유:**
- HTML = 집의 골조 (벽, 문, 창문)
- CSS = 집의 인테리어 (색깔, 가구)
- JavaScript = 집의 기능 (조명 스위치, 문 자동 열림)

---

### 1-2. 기본 태그

#### `<div>` - 컨테이너 (가장 많이 사용!)

```html
<div>
  여기에 내용을 담습니다
</div>
```

**용도:** 
- 다른 요소들을 그룹화
- 레이아웃 구성
- 스타일 적용을 위한 컨테이너

**프로젝트에서:**
```vue
<template>
  <div class="solar-system">  ← 전체를 감싸는 컨테이너
    <div ref="containerRef"></div>  ← Three.js 캔버스용
    <div class="info-panel">  ← 정보 패널용
      정보 내용
    </div>
  </div>
</template>
```

---

#### `<h1>`, `<h2>` - 제목

```html
<h1>큰 제목</h1>
<h2>중간 제목</h2>
<h3>작은 제목</h3>
```

**프로젝트에서:**
```vue
<h2>🌟 간단한 태양계 시뮬레이션</h2>
```

---

#### `<p>` - 문단 (paragraph)

```html
<p>이것은 문단입니다.</p>
```

**프로젝트에서:**
```vue
<p>☀️ 노란색 = 태양 (자전)</p>
<p>🌍 파란색 = 지구 (공전 + 자전)</p>
```

---

### 1-3. 속성 (Attributes)

태그에 추가 정보를 붙이는 방법

#### class - CSS 스타일을 적용하기 위한 이름

```html
<div class="my-box">내용</div>
<div class="red-text big-size">내용</div>  ← 여러 개 가능
```

**프로젝트에서:**
```vue
<div class="solar-system">  ← 'solar-system' 클래스
<div class="info-panel">    ← 'info-panel' 클래스
```

---

#### ref - Vue에서 요소를 참조하기 위한 이름

```vue
<div ref="myElement"></div>
```

**프로젝트에서:**
```vue
<div ref="containerRef"></div>  ← JavaScript에서 이 요소를 찾을 수 있음
```

---

### 1-4. HTML 구조 규칙

#### 1. 태그는 항상 열고 닫기
```html
<!-- ✅ 올바른 예 -->
<div>내용</div>

<!-- ❌ 잘못된 예 -->
<div>내용
```

#### 2. 태그는 중첩 가능
```html
<div>
  <div>
    <p>깊이 중첩된 문단</p>
  </div>
</div>
```

#### 3. 태그 이름은 소문자 사용
```html
<!-- ✅ 올바른 예 -->
<div></div>

<!-- ❌ 잘못된 예 (작동은 하지만 비권장) -->
<DIV></DIV>
```

---

## 2. CSS 기초

### 2-1. CSS란?

**CSS (Cascading Style Sheets)**
- 웹 페이지의 **스타일**을 꾸미는 언어
- 색상, 크기, 위치 등을 지정

---

### 2-2. CSS 작성 방법

#### 방법 1: 인라인 스타일 (HTML 태그에 직접)
```html
<div style="color: red; font-size: 20px;">
  빨간 글씨
</div>
```

**프로젝트에서 (React 버전):**
```jsx
<div style={{ 
  color: 'white',
  fontSize: '14px'
}}>
```

---

#### 방법 2: 내부 스타일 (Vue의 `<style>` 태그)
```vue
<template>
  <div class="my-box">내용</div>
</template>

<style scoped>
.my-box {
  color: red;
  font-size: 20px;
}
</style>
```

---

### 2-3. CSS 선택자

#### 클래스 선택자 (가장 많이 사용)
```css
.info-panel {
  color: white;
}
```
- `.`으로 시작
- HTML의 `class="info-panel"`과 연결

#### 태그 선택자
```css
div {
  color: blue;
}
```
- 모든 `<div>` 태그에 적용

#### 자식 선택자
```css
.info-panel h2 {
  margin: 0;
}
```
- `.info-panel` 안의 `<h2>`에만 적용

---

### 2-4. 주요 CSS 속성

#### 색상
```css
.my-box {
  color: white;              /* 글자 색 */
  background: black;         /* 배경 색 */
  background: rgba(0,0,0,0.7); /* 반투명 배경 */
}
```

**색상 표현 방법:**
- 이름: `red`, `blue`, `white`
- HEX: `#ff0000` (빨강)
- RGB: `rgb(255, 0, 0)` (빨강)
- RGBA: `rgba(255, 0, 0, 0.5)` (반투명 빨강)

**프로젝트에서:**
```css
.info-panel {
  color: white;                      /* 흰색 글자 */
  background: rgba(0, 0, 0, 0.7);   /* 반투명 검은 배경 */
}
```

---

#### 크기
```css
.my-box {
  width: 100px;      /* 너비 */
  height: 50px;      /* 높이 */
  width: 100%;       /* 부모의 100% */
  height: 100vh;     /* 화면 높이의 100% */
}
```

**프로젝트에서:**
```css
.solar-system {
  width: 100%;       /* 전체 너비 */
  height: 100vh;     /* 전체 화면 높이 */
}
```

---

#### 여백
```css
.my-box {
  margin: 10px;      /* 바깥 여백 */
  padding: 15px;     /* 안쪽 여백 */
  
  /* 개별 지정 */
  margin-top: 10px;
  margin-right: 20px;
  margin-bottom: 10px;
  margin-left: 20px;
  
  /* 축약 */
  margin: 10px 20px 10px 20px;  /* 위 오른쪽 아래 왼쪽 */
  margin: 10px 20px;             /* 상하 좌우 */
}
```

**시각적 이해:**
```
┌─────────────────────────┐
│   margin (바깥 여백)     │
│  ┌──────────────────┐   │
│  │ padding (안쪽)    │   │
│  │  ┌───────────┐   │   │
│  │  │  내용     │   │   │
│  │  └───────────┘   │   │
│  └──────────────────┘   │
└─────────────────────────┘
```

**프로젝트에서:**
```css
.info-panel {
  padding: 15px;     /* 안쪽 여백 */
}

.info-panel p {
  margin: 5px 0;     /* 상하 5px, 좌우 0 */
}
```

---

#### 위치
```css
.my-box {
  position: absolute;    /* 절대 위치 */
  top: 20px;            /* 위에서 20px */
  left: 20px;           /* 왼쪽에서 20px */
  right: 20px;          /* 오른쪽에서 20px */
  bottom: 20px;         /* 아래에서 20px */
}
```

**position 종류:**
- `static`: 기본값 (일반 흐름)
- `relative`: 원래 위치 기준
- `absolute`: 부모 요소 기준
- `fixed`: 화면 기준 (스크롤해도 고정)

**프로젝트에서:**
```css
.info-panel {
  position: absolute;  /* 절대 위치 */
  top: 20px;          /* 위에서 20px */
  left: 20px;         /* 왼쪽에서 20px */
}
```

---

#### 글자 스타일
```css
.my-text {
  font-size: 14px;              /* 글자 크기 */
  font-family: Arial;           /* 글꼴 */
  font-weight: bold;            /* 굵기 */
  text-align: center;           /* 정렬 */
  line-height: 1.5;             /* 줄 간격 */
}
```

**프로젝트에서:**
```css
.info-panel {
  font-family: Arial, sans-serif;
  font-size: 14px;
}
```

---

#### 테두리와 모서리
```css
.my-box {
  border: 1px solid black;    /* 테두리 */
  border-radius: 8px;         /* 둥근 모서리 */
}
```

**프로젝트에서:**
```css
.info-panel {
  border-radius: 8px;   /* 둥근 모서리 */
}
```

---

#### 투명도
```css
.my-box {
  opacity: 0.5;        /* 전체 투명도 (0~1) */
}
```

**프로젝트에서:**
```css
.orbit-info {
  opacity: 0.8;        /* 80% 불투명 */
}
```

---

### 2-5. Flexbox (레이아웃)

요소를 쉽게 정렬하는 방법

```css
.container {
  display: flex;              /* Flexbox 활성화 */
  justify-content: center;    /* 가로 중앙 */
  align-items: center;        /* 세로 중앙 */
  flex-direction: row;        /* 가로 방향 (기본값) */
  flex-direction: column;     /* 세로 방향 */
}
```

**예시:**
```html
<div style="display: flex; justify-content: center; align-items: center;">
  <div>가운데 정렬됨</div>
</div>
```

---

## 3. 프로젝트에서 사용되는 HTML/CSS

### 3-1. 전체 구조 (Vue 버전)

```vue
<template>
  <!-- 1. 최상위 컨테이너 -->
  <div class="solar-system">
    
    <!-- 2. Three.js 캔버스가 들어갈 곳 -->
    <div ref="containerRef" class="canvas-container"></div>
    
    <!-- 3. 정보 패널 -->
    <div class="info-panel">
      <h2>🌟 간단한 태양계 시뮬레이션</h2>
      <p>☀️ 노란색 = 태양 (자전)</p>
      <p>🌍 파란색 = 지구 (공전 + 자전)</p>
      <p>🌙 회색 = 달 (지구 주위 공전)</p>
      <p class="orbit-info">회색 선은 지구의 궤도를 나타냅니다</p>
    </div>
    
  </div>
</template>
```

---

### 3-2. 스타일 설명

```css
/* 1. 전체 컨테이너 */
.solar-system {
  width: 100%;        /* 가로 전체 */
  height: 100vh;      /* 세로 전체 (vh = viewport height) */
  overflow: hidden;   /* 넘치는 부분 숨김 */
}

/* 2. 캔버스 컨테이너 */
.canvas-container {
  width: 100%;
  height: 100%;
}

/* 3. 정보 패널 */
.info-panel {
  position: absolute;              /* 절대 위치 */
  top: 20px;                       /* 위에서 20px */
  left: 20px;                      /* 왼쪽에서 20px */
  color: white;                    /* 흰색 글자 */
  font-family: Arial, sans-serif;  /* Arial 폰트 */
  background: rgba(0, 0, 0, 0.7); /* 반투명 검은 배경 */
  padding: 15px;                   /* 안쪽 여백 */
  border-radius: 8px;              /* 둥근 모서리 */
  font-size: 14px;                 /* 글자 크기 */
}

/* 4. 제목 스타일 */
.info-panel h2 {
  margin: 0 0 10px 0;  /* 아래만 10px 여백 */
}

/* 5. 문단 스타일 */
.info-panel p {
  margin: 5px 0;       /* 상하 5px 여백 */
}

/* 6. 궤도 설명 스타일 */
.orbit-info {
  margin-top: 10px;    /* 위쪽 여백 */
  font-size: 12px;     /* 작은 글자 */
  opacity: 0.8;        /* 약간 투명 */
}
```

---

### 3-3. scoped의 의미

```vue
<style scoped>
/* scoped = 이 컴포넌트에만 적용 */
.info-panel {
  color: white;
}
</style>
```

**scoped가 있으면:**
- 이 스타일이 이 컴포넌트에만 적용
- 다른 컴포넌트에 영향 없음

**scoped가 없으면:**
- 전체 앱에 적용
- 다른 컴포넌트에도 영향

---

## 4. 연습 문제

### 기초 연습

#### 연습 1: HTML 구조 만들기
다음 구조를 HTML로 작성하세요:
```
- 컨테이너 (class="box")
  - 제목 (h1): "안녕하세요"
  - 문단 (p): "HTML을 배우고 있어요"
```

<details>
<summary>정답 보기</summary>

```html
<div class="box">
  <h1>안녕하세요</h1>
  <p>HTML을 배우고 있어요</p>
</div>
```
</details>

---

#### 연습 2: CSS 스타일 적용
위의 `.box`에 다음 스타일을 적용하세요:
- 배경색: 파란색
- 글자색: 흰색
- 안쪽 여백: 20px
- 둥근 모서리: 10px

<details>
<summary>정답 보기</summary>

```css
.box {
  background: blue;
  color: white;
  padding: 20px;
  border-radius: 10px;
}
```
</details>

---

### 프로젝트 관련 연습

#### 연습 3: 정보 패널 위치 변경
정보 패널을 오른쪽 위로 옮기세요.

<details>
<summary>힌트</summary>

`left` 대신 `right`를 사용하세요.
</details>

<details>
<summary>정답 보기</summary>

```css
.info-panel {
  position: absolute;
  top: 20px;
  right: 20px;    /* left 대신 right */
  /* 나머지 스타일... */
}
```
</details>

---

#### 연습 4: 정보 패널 색상 변경
정보 패널 배경을 파란색 반투명으로 바꾸세요.

<details>
<summary>힌트</summary>

`rgba(빨강, 초록, 파랑, 투명도)`
파란색은 `rgba(0, 0, 255, 투명도)`
</details>

<details>
<summary>정답 보기</summary>

```css
.info-panel {
  background: rgba(0, 0, 255, 0.7);  /* 반투명 파란색 */
  /* 나머지 스타일... */
}
```
</details>

---

#### 연습 5: 글자 크기 조절
제목을 더 크게, 문단을 더 작게 만드세요.

<details>
<summary>정답 보기</summary>

```css
.info-panel h2 {
  font-size: 20px;   /* 제목 크게 */
}

.info-panel p {
  font-size: 12px;   /* 문단 작게 */
}
```
</details>

---

## 5. 다음 단계

HTML/CSS 기초를 익혔다면:

1. ✅ **JavaScript 기초 학습**
   - 변수, 함수, 조건문
   - 배열, 객체
   - 프로젝트에 필요한 개념

2. ✅ **Vue.js 기초 학습**
   - 컴포넌트 구조
   - ref(), onMounted()
   - 템플릿 문법

3. ✅ **Three.js 기초 학습**
   - 3D 그래픽 기초
   - Scene, Camera, Renderer
   - Geometry와 Material

4. ✅ **통합 학습 가이드**
   - 전체 로드맵
   - 단계별 프로젝트 진행

---

## 📚 추가 학습 자료

### 온라인 튜토리얼
- MDN Web Docs: https://developer.mozilla.org/ko/docs/Web/HTML
- W3Schools: https://www.w3schools.com/html/
- 생활코딩: https://opentutorials.org/course/1

### 연습 사이트
- CodePen: https://codepen.io (실시간 코드 실습)
- JSFiddle: https://jsfiddle.net

---

## 💡 학습 팁

### HTML/CSS 학습 방법
1. **따라 치기**
   - 예제 코드를 직접 타이핑
   - 복사-붙여넣기 X

2. **변형해보기**
   - 색상을 바꿔보기
   - 크기를 조절해보기
   - 위치를 옮겨보기

3. **작은 것부터**
   - 간단한 박스 만들기
   - 점점 복잡하게
   - 프로젝트는 나중에!

4. **브라우저 개발자 도구 활용**
   - F12 키
   - Elements 탭에서 실시간 수정
   - 바로 결과 확인

---

## ✅ 체크리스트

HTML/CSS를 이해했는지 체크해보세요:

### HTML
- [ ] `<div>`, `<h2>`, `<p>` 태그를 사용할 수 있다
- [ ] `class` 속성을 이해한다
- [ ] `ref` 속성이 무엇인지 안다
- [ ] 태그를 중첩할 수 있다

### CSS
- [ ] 클래스 선택자(`.class`)를 사용할 수 있다
- [ ] 색상을 지정할 수 있다 (color, background)
- [ ] 크기를 조절할 수 있다 (width, height)
- [ ] 여백을 조절할 수 있다 (margin, padding)
- [ ] 위치를 지정할 수 있다 (position, top, left)

### 프로젝트 이해
- [ ] 프로젝트의 HTML 구조를 이해한다
- [ ] 정보 패널이 왜 위에 떠있는지 안다 (position: absolute)
- [ ] 스타일을 수정해서 색상/위치를 바꿀 수 있다

---

**다음 문서:** JavaScript 기초로 넘어가세요! 🚀