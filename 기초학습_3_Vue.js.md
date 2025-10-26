# 💚 Vue.js 기초 - 태양계 프로젝트 필수 개념

태양계 프로젝트를 이해하기 위해 꼭 알아야 할 Vue.js 기초입니다.

---

## 📋 목차
1. [Vue.js란?](#1-vuejs란)
2. [Single File Component (SFC)](#2-single-file-component-sfc)
3. [반응형 데이터 - ref()](#3-반응형-데이터---ref)
4. [생명주기 - onMounted, onUnmounted](#4-생명주기---onmounted-onunmounted)
5. [템플릿 문법](#5-템플릿-문법)
6. [프로젝트 코드 완전 분석](#6-프로젝트-코드-완전-분석)
7. [연습 문제](#7-연습-문제)

---

## 1. Vue.js란?

### 1-1. Vue.js 소개

**Vue.js (뷰)**
- 사용자 인터페이스를 만들기 위한 **JavaScript 프레임워크**
- "프로그레시브 프레임워크" - 필요한 만큼만 사용 가능
- **쉽고 직관적**

**프레임워크란?**
- 건축으로 치면 "프리패브(조립식 주택)"
- 기본 구조가 있어서 빠르게 만들 수 있음

---

### 1-2. Vue의 특징

#### ✅ 배우기 쉬움
- HTML과 비슷한 템플릿 문법
- 직관적인 구조

#### ✅ 반응형
- 데이터가 변하면 화면이 **자동으로** 업데이트
- 개발자가 직접 DOM 조작 X

#### ✅ 컴포넌트 기반
- UI를 재사용 가능한 조각으로 나눔
- 유지보수 쉬움

---

### 1-3. Composition API vs Options API

Vue는 두 가지 작성 방법이 있습니다:

#### Options API (예전 방식)
```vue
<script>
export default {
  data() {
    return {
      count: 0
    }
  },
  mounted() {
    console.log('마운트됨')
  }
}
</script>
```

#### Composition API (현대적, 우리가 사용하는 방식) ⭐
```vue
<script setup>
import { ref, onMounted } from 'vue'

const count = ref(0)

onMounted(() => {
  console.log('마운트됨')
})
</script>
```

**우리 프로젝트는 Composition API 사용!**
- 더 간결함
- React Hooks와 비슷
- TypeScript와 잘 맞음

---

## 2. Single File Component (SFC)

### 2-1. .vue 파일 구조

Vue는 하나의 파일에 모든 것을 담습니다:

```vue
<template>
  <!-- 1️⃣ HTML 구조 (화면) -->
  <div>태양계</div>
</template>

<script setup>
// 2️⃣ JavaScript 로직 (동작)
import { ref } from 'vue'
const count = ref(0)
</script>

<style scoped>
/* 3️⃣ CSS 스타일 (꾸미기) */
div {
  color: white;
}
</style>
```

**3개 섹션:**
1. `<template>` - 무엇을 보여줄지
2. `<script setup>` - 어떻게 동작할지
3. `<style scoped>` - 어떻게 보일지

---

### 2-2. 섹션별 상세 설명

#### 📄 `<template>` 섹션
```vue
<template>
  <div class="container">
    <h1>{{ title }}</h1>
    <p>카운트: {{ count }}</p>
  </div>
</template>
```

**특징:**
- HTML처럼 보임
- `{{ }}` 안에 JavaScript 변수 사용 가능
- 하나의 루트 요소 필요 (div로 감싸기)

---

#### 🔧 `<script setup>` 섹션
```vue
<script setup>
import { ref, onMounted } from 'vue'
import * as THREE from 'three'

const title = ref("태양계")
const count = ref(0)

onMounted(() => {
  console.log("시작!")
})
</script>
```

**특징:**
- `setup`을 쓰면 자동으로 Composition API 사용
- import 한 것들이 template에서 바로 사용 가능
- 변수, 함수를 정의하면 template에서 접근 가능

---

#### 🎨 `<style scoped>` 섹션
```vue
<style scoped>
.container {
  width: 100%;
  height: 100vh;
}

h1 {
  color: white;
}
</style>
```

**scoped의 의미:**
- 이 스타일이 **이 컴포넌트에만** 적용
- 다른 컴포넌트에 영향 X
- 스타일 충돌 방지

---

## 3. 반응형 데이터 - ref()

### 3-1. ref()란?

**ref() = 반응형 참조 (Reactive Reference)**
- 값을 **추적** 가능한 상자에 담기
- 값이 변하면 화면이 **자동** 업데이트

**비유:**
- 일반 변수 = 그냥 종이에 쓴 숫자
- ref() = 전광판에 표시된 숫자 (바뀌면 즉시 반영)

---

### 3-2. ref() 사용법

#### 기본 사용
```vue
<script setup>
import { ref } from 'vue'

// ref 만들기
const count = ref(0)

// 값 읽기
console.log(count.value)  // 0

// 값 변경
count.value = 5
count.value++  // 6
</script>
```

**⚠️ 중요: `.value` 꼭 붙이기!**
- `<script>` 안에서는 `.value` 필요
- `<template>` 안에서는 `.value` 불필요 (자동)

---

#### 템플릿에서 사용
```vue
<template>
  <!-- .value 없이 사용! -->
  <p>카운트: {{ count }}</p>
  <button @click="count++">증가</button>
</template>

<script setup>
import { ref } from 'vue'
const count = ref(0)
</script>
```

---

### 3-3. ref()의 종류

#### 숫자
```javascript
const age = ref(20)
age.value = 21
```

#### 문자열
```javascript
const name = ref("지구")
name.value = "화성"
```

#### 불린
```javascript
const isActive = ref(true)
isActive.value = false
```

#### null (DOM 참조용) ⭐
```javascript
const containerRef = ref(null)
// 나중에 HTML 요소가 여기에 담김
```

---

### 3-4. 프로젝트에서 ref() 사용

```vue
<template>
  <div ref="containerRef"></div>
  <!--    ↑ 이 요소를 참조 -->
</template>

<script setup>
import { ref } from 'vue'

// 1. ref 생성 (처음엔 null)
const containerRef = ref(null)

onMounted(() => {
  // 2. 이제 containerRef.value에 실제 HTML 요소가 담김
  console.log(containerRef.value)  // <div>...</div>
  
  // 3. Three.js 캔버스를 여기에 추가
  containerRef.value.appendChild(renderer.domElement)
})
</script>
```

---

## 4. 생명주기 - onMounted, onUnmounted

### 4-1. 생명주기란?

**생명주기 (Lifecycle)**
- 컴포넌트가 생성되고 사라지는 과정
- 각 단계에서 코드 실행 가능

```
생성 → 마운트 → 업데이트 → 언마운트
       ↑                  ↑
   onMounted()      onUnmounted()
```

---

### 4-2. onMounted()

**onMounted() = 컴포넌트가 화면에 나타났을 때**

```vue
<script setup>
import { onMounted } from 'vue'

onMounted(() => {
  console.log("컴포넌트가 화면에 나타났어요!")
  // 여기서 초기화 작업
})
</script>
```

**언제 사용?**
- DOM 요소에 접근해야 할 때
- API 호출
- **Three.js 초기화** ⭐

---

### 4-3. onUnmounted()

**onUnmounted() = 컴포넌트가 사라질 때**

```vue
<script setup>
import { onUnmounted } from 'vue'

onUnmounted(() => {
  console.log("컴포넌트가 사라져요!")
  // 여기서 정리 작업
})
</script>
```

**언제 사용?**
- 이벤트 리스너 제거
- 타이머 정리
- **Three.js 리소스 정리** ⭐

---

### 4-4. 프로젝트에서 생명주기 사용

```vue
<script setup>
import { ref, onMounted, onUnmounted } from 'vue'
import * as THREE from 'three'

const containerRef = ref(null)

onMounted(() => {
  // 1. Three.js 초기화
  const scene = new THREE.Scene()
  const camera = new THREE.PerspectiveCamera(...)
  const renderer = new THREE.WebGLRenderer()
  
  // 2. DOM에 추가
  containerRef.value.appendChild(renderer.domElement)
  
  // 3. 애니메이션 시작
  animate()
  
  // 4. 창 크기 변경 이벤트
  window.addEventListener('resize', handleResize)
})

onUnmounted(() => {
  // 정리: 이벤트 리스너 제거
  window.removeEventListener('resize', handleResize)
  
  // 정리: Three.js 리소스
  renderer.dispose()
})
</script>
```

---

## 5. 템플릿 문법

### 5-1. 텍스트 보간 (Interpolation)

```vue
<template>
  <p>{{ message }}</p>
  <p>{{ count + 1 }}</p>
  <p>{{ isActive ? '활성' : '비활성' }}</p>
</template>

<script setup>
const message = ref("안녕하세요")
const count = ref(5)
const isActive = ref(true)
</script>
```

**`{{ }}` 안에 사용 가능:**
- 변수
- 간단한 JavaScript 표현식
- 삼항 연산자

---

### 5-2. 속성 바인딩

#### v-bind (또는 :)
```vue
<template>
  <!-- 일반 방법 -->
  <div v-bind:class="className"></div>
  
  <!-- 축약 -->
  <div :class="className"></div>
  <img :src="imageUrl" :alt="altText">
</template>

<script setup>
const className = ref("my-class")
const imageUrl = ref("/logo.png")
const altText = ref("로고")
</script>
```

---

### 5-3. 이벤트 처리

#### v-on (또는 @)
```vue
<template>
  <!-- 일반 방법 -->
  <button v-on:click="increment">증가</button>
  
  <!-- 축약 (더 많이 사용) -->
  <button @click="increment">증가</button>
  <button @click="count++">직접 증가</button>
</template>

<script setup>
import { ref } from 'vue'

const count = ref(0)

const increment = () => {
  count.value++
}
</script>
```

---

### 5-4. 조건부 렌더링

#### v-if, v-else
```vue
<template>
  <div v-if="isVisible">보여요!</div>
  <div v-else>안 보여요!</div>
  
  <p v-if="score >= 90">A등급</p>
  <p v-else-if="score >= 80">B등급</p>
  <p v-else>C등급</p>
</template>

<script setup>
const isVisible = ref(true)
const score = ref(85)
</script>
```

---

### 5-5. 리스트 렌더링

#### v-for
```vue
<template>
  <ul>
    <li v-for="planet in planets" :key="planet">
      {{ planet }}
    </li>
  </ul>
</template>

<script setup>
const planets = ref(["수성", "금성", "지구", "화성"])
</script>
```

**⚠️ :key 필수!**
- 각 항목을 구별하기 위한 고유값
- 성능 최적화

---

## 6. 프로젝트 코드 완전 분석

우리 태양계 프로젝트를 한 줄씩 분석해봅시다!

### 6-1. 템플릿 부분

```vue
<template>
  <!-- 1. 최상위 컨테이너 -->
  <div class="solar-system">
    
    <!-- 2. Three.js 캔버스를 담을 곳 -->
    <!--    ref="containerRef" - JavaScript에서 이 요소에 접근 -->
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

### 6-2. 스크립트 부분 (초기 설정)

```vue
<script setup>
// 1️⃣ Vue 함수 가져오기
import { ref, onMounted, onUnmounted } from 'vue';

// 2️⃣ Three.js 전체 가져오기 (THREE라는 이름으로)
import * as THREE from 'three';

// 3️⃣ DOM 요소를 참조할 ref 만들기
// 처음엔 null, onMounted에서 실제 요소가 담김
const containerRef = ref(null);
```

---

### 6-3. onMounted - Three.js 초기화

```vue
onMounted(() => {
  // ========== 1. 기본 설정 ==========
  
  // Scene: 3D 세계 (무대)
  const scene = new THREE.Scene();
  scene.background = new THREE.Color(0x000011);  // 우주색
  
  // Camera: 카메라 (관객의 눈)
  const camera = new THREE.PerspectiveCamera(
    75,                                  // 시야각
    window.innerWidth / window.innerHeight,  // 화면 비율
    0.1,                                // 가까운 거리
    1000                                // 먼 거리
  );
  camera.position.z = 50;  // 뒤로
  camera.position.y = 20;  // 위로
  camera.lookAt(0, 0, 0);  // 중심을 바라봄
  
  // Renderer: 렌더러 (그리는 도구)
  const renderer = new THREE.WebGLRenderer({ antialias: true });
  renderer.setSize(window.innerWidth, window.innerHeight);
  
  // 렌더러를 HTML에 추가
  containerRef.value.appendChild(renderer.domElement);
```

---

### 6-4. 태양 만들기

```vue
  // ========== 2. 태양 만들기 ==========
  
  // Geometry: 형태 (구)
  const sunGeometry = new THREE.SphereGeometry(
    5,    // 반지름 5
    32,   // 가로 세밀도
    32    // 세로 세밀도
  );
  
  // Material: 재질
  const sunMaterial = new THREE.MeshBasicMaterial({ 
    color: 0xffff00,           // 노란색
    emissive: 0xffff00,        // 스스로 빛남
    emissiveIntensity: 0.5     // 빛의 강도
  });
  
  // Mesh: Geometry + Material = 완성된 객체
  const sun = new THREE.Mesh(sunGeometry, sunMaterial);
  
  // Scene에 추가 (무대에 올리기)
  scene.add(sun);
  
  // 태양의 빛 추가
  const sunLight = new THREE.PointLight(0xffffff, 2, 100);
  scene.add(sunLight);
```

---

### 6-5. 지구와 달 만들기

```vue
  // ========== 3. 지구 만들기 ==========
  const earthGeometry = new THREE.SphereGeometry(2, 32, 32);
  const earthMaterial = new THREE.MeshStandardMaterial({ 
    color: 0x2233ff,     // 파란색
    roughness: 0.7       // 거친 정도
  });
  const earth = new THREE.Mesh(earthGeometry, earthMaterial);
  scene.add(earth);
  
  // ========== 4. 달 만들기 ==========
  const moonGeometry = new THREE.SphereGeometry(0.5, 32, 32);
  const moonMaterial = new THREE.MeshStandardMaterial({ 
    color: 0xaaaaaa,     // 회색
    roughness: 0.9
  });
  const moon = new THREE.Mesh(moonGeometry, moonMaterial);
  scene.add(moon);
```

---

### 6-6. 지구 궤도선 그리기

```vue
  // ========== 5. 지구 궤도 선 ==========
  const earthOrbitRadius = 20;  // 궤도 반지름
  
  // 점들을 담을 배열
  const earthOrbitPoints = [];
  
  // 원 그리기 (64개 점으로)
  for (let i = 0; i <= 64; i++) {
    const angle = (i / 64) * Math.PI * 2;  // 각도 계산
    earthOrbitPoints.push(
      Math.cos(angle) * earthOrbitRadius,  // x 좌표
      0,                                    // y 좌표 (평면)
      Math.sin(angle) * earthOrbitRadius   // z 좌표
    );
  }
  
  // Geometry 만들고 점 추가
  const earthOrbitGeometry = new THREE.BufferGeometry();
  earthOrbitGeometry.setAttribute(
    'position', 
    new THREE.Float32BufferAttribute(earthOrbitPoints, 3)
  );
  
  // 선 재질
  const earthOrbitMaterial = new THREE.LineBasicMaterial({ 
    color: 0x444444,      // 회색
    transparent: true,    // 투명 가능
    opacity: 0.3          // 30% 불투명
  });
  
  // 선 만들기
  const earthOrbit = new THREE.Line(
    earthOrbitGeometry, 
    earthOrbitMaterial
  );
  scene.add(earthOrbit);
```

---

### 6-7. 별 만들기

```vue
  // ========== 6. 별 배경 ==========
  const starsGeometry = new THREE.BufferGeometry();
  const starVertices = [];
  
  // 1000개의 별 생성
  for (let i = 0; i < 1000; i++) {
    // 랜덤 위치 (-100 ~ 100)
    const x = (Math.random() - 0.5) * 200;
    const y = (Math.random() - 0.5) * 200;
    const z = (Math.random() - 0.5) * 200;
    starVertices.push(x, y, z);
  }
  
  starsGeometry.setAttribute(
    'position', 
    new THREE.Float32BufferAttribute(starVertices, 3)
  );
  
  const starsMaterial = new THREE.PointsMaterial({ 
    color: 0xffffff,  // 흰색
    size: 0.5         // 크기
  });
  
  const stars = new THREE.Points(starsGeometry, starsMaterial);
  scene.add(stars);
```

---

### 6-8. 애니메이션

```vue
  // ========== 7. 애니메이션 변수 ==========
  let earthAngle = 0;  // 지구 공전 각도
  let moonAngle = 0;   // 달 공전 각도
  
  // ========== 8. 애니메이션 함수 ==========
  function animate() {
    // 다음 프레임 요청 (계속 반복)
    requestAnimationFrame(animate);
    
    // 태양 자전
    sun.rotation.y += 0.001;
    
    // 지구 공전
    earthAngle += 0.01;  // 각도 증가
    earth.position.x = Math.cos(earthAngle) * earthOrbitRadius;
    earth.position.z = Math.sin(earthAngle) * earthOrbitRadius;
    
    // 지구 자전
    earth.rotation.y += 0.02;
    
    // 달 공전 (지구 주위)
    moonAngle += 0.05;
    const moonOrbitRadius = 5;
    moon.position.x = earth.position.x + Math.cos(moonAngle) * moonOrbitRadius;
    moon.position.z = earth.position.z + Math.sin(moonAngle) * moonOrbitRadius;
    
    // 화면에 그리기
    renderer.render(scene, camera);
  }
  
  // 애니메이션 시작!
  animate();
```

---

### 6-9. 창 크기 변경 대응

```vue
  // ========== 9. 창 크기 변경 이벤트 ==========
  function handleResize() {
    // 카메라 비율 업데이트
    camera.aspect = window.innerWidth / window.innerHeight;
    camera.updateProjectionMatrix();
    
    // 렌더러 크기 업데이트
    renderer.setSize(window.innerWidth, window.innerHeight);
  }
  
  // 이벤트 리스너 등록
  window.addEventListener('resize', handleResize);
});  // onMounted 끝
```

---

### 6-10. 정리 (onUnmounted)

```vue
// ========== 10. 정리 ==========
onUnmounted(() => {
  // 이벤트 리스너 제거
  window.removeEventListener('resize', handleResize);
  
  // DOM에서 제거
  if (containerRef.value) {
    containerRef.value.removeChild(renderer.domElement);
  }
  
  // Three.js 리소스 정리
  renderer.dispose();
});
</script>
```

---

### 6-11. 스타일 부분

```vue
<style scoped>
/* 전체 컨테이너 */
.solar-system {
  width: 100%;         /* 가로 전체 */
  height: 100vh;       /* 세로 전체 */
  overflow: hidden;    /* 넘치는 부분 숨김 */
}

/* 캔버스 컨테이너 */
.canvas-container {
  width: 100%;
  height: 100%;
}

/* 정보 패널 */
.info-panel {
  position: absolute;              /* 절대 위치 */
  top: 20px;
  left: 20px;
  color: white;
  font-family: Arial, sans-serif;
  background: rgba(0, 0, 0, 0.7); /* 반투명 검은색 */
  padding: 15px;
  border-radius: 8px;
  font-size: 14px;
}

/* 제목 */
.info-panel h2 {
  margin: 0 0 10px 0;
}

/* 문단 */
.info-panel p {
  margin: 5px 0;
}

/* 궤도 설명 */
.orbit-info {
  margin-top: 10px;
  font-size: 12px;
  opacity: 0.8;
}
</style>
```

---

## 7. 연습 문제

### 기초 연습

#### 연습 1: ref 만들기
카운터를 만드세요:
- count ref (초기값 0)
- 증가 버튼
- 감소 버튼
- 화면에 count 표시

<details>
<summary>정답 보기</summary>

```vue
<template>
  <div>
    <p>카운트: {{ count }}</p>
    <button @click="count++">증가</button>
    <button @click="count--">감소</button>
  </div>
</template>

<script setup>
import { ref } from 'vue'
const count = ref(0)
</script>
```
</details>

---

#### 연습 2: onMounted 사용
컴포넌트가 마운트되면 "안녕하세요!"를 콘솔에 출력하세요.

<details>
<summary>정답 보기</summary>

```vue
<script setup>
import { onMounted } from 'vue'

onMounted(() => {
  console.log("안녕하세요!")
})
</script>
```
</details>

---

### 프로젝트 관련 연습

#### 연습 3: 지구 속도 2배로
프로젝트 코드에서 지구의 공전 속도를 2배로 만드세요.

<details>
<summary>힌트</summary>

`earthAngle +=` 부분을 찾으세요.
</details>

<details>
<summary>정답 보기</summary>

```javascript
// 기존
earthAngle += 0.01;

// 변경
earthAngle += 0.02;  // 2배
```
</details>

---

#### 연습 4: 정보 패널 토글
버튼을 누르면 정보 패널이 보이고/숨기게 만드세요.

<details>
<summary>힌트</summary>

1. `showInfo` ref 만들기 (true/false)
2. `v-if="showInfo"` 사용
3. 버튼의 `@click`에서 `showInfo.value = !showInfo.value`
</details>

<details>
<summary>정답 보기</summary>

```vue
<template>
  <div class="solar-system">
    <div ref="containerRef"></div>
    
    <!-- v-if로 조건부 렌더링 -->
    <div v-if="showInfo" class="info-panel">
      정보...
    </div>
    
    <!-- 토글 버튼 -->
    <button @click="showInfo = !showInfo">
      정보 {{ showInfo ? '숨기기' : '보기' }}
    </button>
  </div>
</template>

<script setup>
import { ref } from 'vue'
const showInfo = ref(true)
</script>
```
</details>

---

#### 연습 5: 행성 개수 표시
정보 패널에 현재 행성 개수를 표시하세요.

<details>
<summary>힌트</summary>

1. `planetCount` ref 만들기
2. template에서 `{{ planetCount }}` 표시
</details>

<details>
<summary>정답 보기</summary>

```vue
<template>
  <div class="info-panel">
    <h2>🌟 간단한 태양계 시뮬레이션</h2>
    <p>현재 행성 개수: {{ planetCount }}개</p>
    <p>☀️ 노란색 = 태양 (자전)</p>
    <!-- ... -->
  </div>
</template>

<script setup>
import { ref } from 'vue'
const planetCount = ref(3)  // 태양, 지구, 달
</script>
```
</details>

---

## 8. 다음 단계

Vue.js 기초를 익혔다면:

1. ✅ **Three.js 기초 학습**
   - 3D 좌표계와 회전
   - Scene, Camera, Renderer
   - Geometry와 Material
   - 애니메이션과 원운동

2. ✅ **프로젝트 실습**
   - 태양계 프로젝트 만들기
   - 코드 수정하며 익히기

3. ✅ **Vue 심화**
   - computed (계산된 속성)
   - watch (감시자)
   - provide/inject

4. ✅ **Three.js 더 배우기**
   - 다른 Geometry
   - 더 복잡한 애니메이션
   - 텍스처와 라이팅

---

## 📚 추가 학습 자료

### 공식 문서
- Vue.js 공식: https://ko.vuejs.org
- Vue 튜토리얼: https://ko.vuejs.org/tutorial/
- Composition API: https://ko.vuejs.org/guide/extras/composition-api-faq.html

### 추천 강의
- Vue Mastery: https://www.vuemastery.com
- Captain Pangyo 블로그
- 생활코딩 Vue.js

---

## ✅ 체크리스트

Vue.js를 이해했는지 체크해보세요:

### SFC 구조
- [ ] template, script, style의 역할을 안다
- [ ] scoped의 의미를 이해한다
- [ ] `<script setup>` 사용법을 안다

### 반응형 데이터
- [ ] ref()가 무엇인지 안다
- [ ] .value를 언제 사용하는지 안다
- [ ] template에서 ref 사용법을 안다
- [ ] DOM 참조용 ref를 만들 수 있다

### 생명주기
- [ ] onMounted()의 역할을 안다
- [ ] onUnmounted()의 역할을 안다
- [ ] 언제 각각을 사용하는지 안다

### 템플릿 문법
- [ ] {{ }} 보간법을 사용할 수 있다
- [ ] v-bind(:) 사용법을 안다
- [ ] v-on(@) 사용법을 안다
- [ ] v-if, v-for를 이해한다

### 프로젝트 이해
- [ ] 프로젝트 코드 전체를 이해한다
- [ ] 각 부분의 역할을 설명할 수 있다
- [ ] 코드를 수정할 수 있다

---

**다음 단계:** 실제 프로젝트를 만들어보세요! 🚀