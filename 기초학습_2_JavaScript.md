# 📗 JavaScript 기초 - 태양계 프로젝트 필수 개념

태양계 프로젝트를 이해하기 위해 꼭 알아야 할 JavaScript 기초입니다.

---

## 📋 목차
1. [JavaScript란?](#1-javascript란)
2. [변수와 데이터 타입](#2-변수와-데이터-타입)
3. [함수](#3-함수)
4. [객체와 배열](#4-객체와-배열)
5. [조건문과 반복문](#5-조건문과-반복문)
6. [프로젝트에서 사용되는 JavaScript](#6-프로젝트에서-사용되는-javascript)
7. [연습 문제](#7-연습-문제)

---

## 1. JavaScript란?

### 1-1. JavaScript의 역할

**JavaScript (JS)**
- 웹 페이지에 **동작**을 추가하는 언어
- 사용자와 **상호작용** 가능
- **계산**, **애니메이션**, **데이터 처리**

**비유:**
- HTML = 집의 골조
- CSS = 인테리어
- **JavaScript = 전기, 수도, 엘리베이터 (기능)**

---

### 1-2. JavaScript 실행 방법

#### 브라우저 콘솔
1. 웹 브라우저 열기
2. `F12` 키 누르기
3. **Console** 탭 선택
4. 코드 입력하고 엔터!

```javascript
console.log("안녕하세요!");  // 콘솔에 출력
```

---

## 2. 변수와 데이터 타입

### 2-1. 변수 선언

변수 = 값을 담는 상자

#### const - 변경 불가능한 변수 (상수)
```javascript
const name = "지구";
console.log(name);  // "지구"

// name = "화성";  // ❌ 오류! const는 변경 불가
```

#### let - 변경 가능한 변수
```javascript
let count = 0;
console.log(count);  // 0

count = 5;
console.log(count);  // 5 ✅ 변경 가능!
```

#### var - 예전 방식 (사용 X)
```javascript
var age = 20;  // 사용하지 마세요!
```

**💡 규칙:**
- 변하지 않는 값 → `const`
- 변할 수 있는 값 → `let`
- **절대 `var` 사용하지 않기!**

---

### 2-2. 데이터 타입

#### 숫자 (Number)
```javascript
const age = 20;
const pi = 3.14159;
const negative = -5;
```

**프로젝트에서:**
```javascript
const earthOrbitRadius = 20;     // 지구 궤도 반지름
let earthAngle = 0;               // 지구 공전 각도
earthAngle += 0.01;               // 각도 증가
```

---

#### 문자열 (String)
```javascript
const name = "지구";
const greeting = '안녕하세요';
const message = `반갑습니다, ${name}!`;  // 템플릿 리터럴
```

**따옴표 종류:**
- `"큰 따옴표"`
- `'작은 따옴표'`
- `` `백틱` `` - 변수 포함 가능 (`${변수}`)

---

#### 불린 (Boolean)
```javascript
const isRunning = true;
const isFinished = false;
```

---

#### null과 undefined
```javascript
let value = null;        // 의도적으로 비어있음
let notDefined;          // undefined (값을 아직 안 넣음)
```

---

### 2-3. 연산자

#### 산술 연산자
```javascript
const a = 10;
const b = 3;

console.log(a + b);  // 13 (더하기)
console.log(a - b);  // 7  (빼기)
console.log(a * b);  // 30 (곱하기)
console.log(a / b);  // 3.333... (나누기)
```

**프로젝트에서:**
```javascript
earthAngle += 0.01;  // earthAngle = earthAngle + 0.01
```

---

#### 비교 연산자
```javascript
console.log(5 > 3);   // true (크다)
console.log(5 < 3);   // false (작다)
console.log(5 === 5); // true (같다)
console.log(5 !== 3); // true (다르다)
```

**주의:** `===` 사용 (= 두 개 아님!)
- `=` : 대입 (값을 넣기)
- `===` : 비교 (같은지 확인)

---

## 3. 함수

### 3-1. 함수란?

**함수 (Function)**
- 코드 묶음
- 필요할 때 호출해서 실행
- **재사용** 가능

**비유:** 
- 함수 = 레시피
- 호출 = 요리하기

---

### 3-2. 함수 선언 방법

#### 일반 함수
```javascript
function greet(name) {
  console.log(`안녕하세요, ${name}님!`);
}

// 함수 호출
greet("지구");  // "안녕하세요, 지구님!"
```

---

#### 화살표 함수 (Arrow Function) ⭐
```javascript
const greet = (name) => {
  console.log(`안녕하세요, ${name}님!`);
};

greet("화성");  // "안녕하세요, 화성님!"
```

**화살표 함수 = 일반 함수의 짧은 표현**

**더 짧게:**
```javascript
// 한 줄이면 중괄호 생략 가능
const add = (a, b) => a + b;

console.log(add(2, 3));  // 5
```

---

#### 함수 예시

**프로젝트에서:**
```javascript
// 애니메이션 함수
function animate() {
  requestAnimationFrame(animate);  // 계속 반복
  
  // 태양 자전
  sun.rotation.y += 0.001;
  
  // 지구 공전
  earthAngle += 0.01;
  earth.position.x = Math.cos(earthAngle) * earthOrbitRadius;
  
  // 화면에 그리기
  renderer.render(scene, camera);
}

// 함수 실행
animate();
```

---

### 3-3. 매개변수와 반환값

#### 매개변수 (Parameter)
```javascript
function multiply(a, b) {  // a, b = 매개변수
  return a * b;            // 반환값
}

const result = multiply(5, 3);  // 5, 3 = 인수
console.log(result);  // 15
```

---

#### 반환값 없는 함수
```javascript
function sayHello() {
  console.log("안녕!");
  // return이 없으면 undefined 반환
}
```

---

## 4. 객체와 배열

### 4-1. 객체 (Object)

**객체 = 관련된 데이터를 묶어놓은 것**

```javascript
const planet = {
  name: "지구",
  radius: 2,
  color: 0x2233ff,
  hasLife: true
};

// 접근 방법 1: 점 표기법
console.log(planet.name);    // "지구"
console.log(planet.radius);  // 2

// 접근 방법 2: 대괄호 표기법
console.log(planet["color"]);  // 0x2233ff
```

---

#### 객체 수정
```javascript
planet.radius = 3;           // 값 변경
planet.distance = 150;       // 새 속성 추가
```

---

#### 프로젝트에서
```javascript
// Three.js 재질 객체
const earthMaterial = new THREE.MeshStandardMaterial({ 
  color: 0x2233ff,     // 속성: 색상
  roughness: 0.7       // 속성: 거칠기
});
```

---

### 4-2. 배열 (Array)

**배열 = 순서가 있는 목록**

```javascript
const planets = ["수성", "금성", "지구", "화성"];

// 인덱스는 0부터 시작!
console.log(planets[0]);  // "수성"
console.log(planets[2]);  // "지구"
console.log(planets.length);  // 4 (길이)
```

---

#### 배열 메서드
```javascript
const numbers = [1, 2, 3];

numbers.push(4);      // 끝에 추가 [1, 2, 3, 4]
numbers.pop();        // 끝에서 제거 [1, 2, 3]
```

---

#### 프로젝트에서
```javascript
// 별 좌표 배열
const starVertices = [];

for (let i = 0; i < 1000; i++) {
  starVertices.push(x, y, z);  // 좌표 추가
}
```

---

## 5. 조건문과 반복문

### 5-1. 조건문 (if)

```javascript
const score = 85;

if (score >= 90) {
  console.log("A등급");
} else if (score >= 80) {
  console.log("B등급");
} else {
  console.log("C등급");
}
```

---

### 5-2. 반복문 (for)

```javascript
// 0부터 4까지 반복
for (let i = 0; i < 5; i++) {
  console.log(i);  // 0, 1, 2, 3, 4
}
```

**프로젝트에서:**
```javascript
// 별 1000개 만들기
for (let i = 0; i < 1000; i++) {
  const x = (Math.random() - 0.5) * 200;
  const y = (Math.random() - 0.5) * 200;
  const z = (Math.random() - 0.5) * 200;
  starVertices.push(x, y, z);
}
```

---

#### 반복문 구조
```javascript
for (초기값; 조건; 증가) {
  // 실행할 코드
}

for (let i = 0; i < 5; i++) {
  //   ↑        ↑      ↑
  //   시작     종료    1씩 증가
}
```

---

## 6. 프로젝트에서 사용되는 JavaScript

### 6-1. import - 모듈 가져오기

```javascript
import { ref, onMounted } from 'vue';
import * as THREE from 'three';
```

**의미:**
- Vue에서 `ref`, `onMounted` 함수 가져오기
- Three.js의 모든 것(`*`)을 `THREE`라는 이름으로 가져오기

---

### 6-2. const로 Three.js 객체 만들기

```javascript
// Scene (무대) 만들기
const scene = new THREE.Scene();
scene.background = new THREE.Color(0x000011);

// 태양 만들기
const sunGeometry = new THREE.SphereGeometry(5, 32, 32);
const sunMaterial = new THREE.MeshBasicMaterial({ 
  color: 0xffff00 
});
const sun = new THREE.Mesh(sunGeometry, sunMaterial);
scene.add(sun);  // 무대에 추가
```

**패턴:**
1. Geometry (형태) 만들기
2. Material (재질) 만들기
3. Mesh (객체) = Geometry + Material
4. Scene에 추가

---

### 6-3. 애니메이션 변수

```javascript
let earthAngle = 0;  // 지구 공전 각도 (변경됨 → let)
let moonAngle = 0;   // 달 공전 각도

function animate() {
  requestAnimationFrame(animate);  // 계속 반복
  
  // 각도 증가
  earthAngle += 0.01;
  moonAngle += 0.05;
  
  // 위치 계산 (원 그리기)
  earth.position.x = Math.cos(earthAngle) * 20;
  earth.position.z = Math.sin(earthAngle) * 20;
}
```

---

### 6-4. Math 객체 (수학 함수)

```javascript
// 삼각함수 (원 그리기)
Math.cos(angle)  // 코사인
Math.sin(angle)  // 사인

// 상수
Math.PI          // 3.14159... (파이)

// 랜덤
Math.random()    // 0~1 사이 랜덤 숫자
```

**프로젝트에서:**
```javascript
// 원 위의 점 계산 (공전 궤도)
const x = Math.cos(angle) * radius;
const z = Math.sin(angle) * radius;
```

**시각적 이해:**
```
        y (위)
        |
        |
--------+-------- x (오른쪽)
       /|
      / |
     /  |
    z   |
  (앞)  |
```

---

### 6-5. 객체 속성 접근

```javascript
// 점 표기법
sun.rotation.y += 0.001;
earth.position.x = 10;
earth.position.z = 20;

// 체인 접근
scene.background = new THREE.Color(0x000011);
//    ↑            ↑
//    객체         속성
```

---

### 6-6. 함수 호출과 메서드

```javascript
// 함수 호출
scene.add(sun);           // scene에 sun 추가
renderer.render(scene, camera);  // 화면에 그리기

// 메서드 체인
camera.lookAt(0, 0, 0);   // 카메라가 (0,0,0) 바라보기
```

---

## 7. 연습 문제

### 기초 연습

#### 연습 1: 변수 선언
다음을 JavaScript 변수로 선언하세요:
- 행성 이름: "화성" (변경 불가)
- 행성 크기: 1.5 (변경 가능)

<details>
<summary>정답 보기</summary>

```javascript
const planetName = "화성";
let planetSize = 1.5;
```
</details>

---

#### 연습 2: 함수 만들기
두 숫자를 더하는 함수를 만드세요.

<details>
<summary>정답 보기</summary>

```javascript
// 방법 1: 일반 함수
function add(a, b) {
  return a + b;
}

// 방법 2: 화살표 함수
const add = (a, b) => a + b;

console.log(add(5, 3));  // 8
```
</details>

---

#### 연습 3: 객체 만들기
다음 정보를 가진 행성 객체를 만드세요:
- 이름: "목성"
- 크기: 11
- 색상: 0xff8800

<details>
<summary>정답 보기</summary>

```javascript
const jupiter = {
  name: "목성",
  size: 11,
  color: 0xff8800
};

console.log(jupiter.name);  // "목성"
```
</details>

---

#### 연습 4: 배열과 반복문
1부터 10까지의 숫자를 배열에 넣고 출력하세요.

<details>
<summary>정답 보기</summary>

```javascript
const numbers = [];

for (let i = 1; i <= 10; i++) {
  numbers.push(i);
}

console.log(numbers);  // [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
```
</details>

---

### 프로젝트 관련 연습

#### 연습 5: 공전 속도 이해하기
다음 코드에서 지구가 더 빠르게 공전하려면?

```javascript
let earthAngle = 0;

function animate() {
  earthAngle += 0.01;  // 이 값을 변경하세요!
  earth.position.x = Math.cos(earthAngle) * 20;
}
```

<details>
<summary>정답 보기</summary>

```javascript
earthAngle += 0.02;  // 0.01 → 0.02 (2배 빠름)
// 또는
earthAngle += 0.05;  // 5배 빠름
```
</details>

---

#### 연습 6: 새로운 행성 추가
화성을 추가하는 코드를 완성하세요:

```javascript
const marsGeometry = new THREE.SphereGeometry(?, ?, ?);
const marsMaterial = new THREE.MeshStandardMaterial({ 
  color: ?  // 빨간색
});
const mars = new THREE.Mesh(?, ?);
scene.add(?);
```

<details>
<summary>정답 보기</summary>

```javascript
const marsGeometry = new THREE.SphereGeometry(1.5, 32, 32);
const marsMaterial = new THREE.MeshStandardMaterial({ 
  color: 0xff0000  // 빨간색
});
const mars = new THREE.Mesh(marsGeometry, marsMaterial);
scene.add(mars);
```
</details>

---

#### 연습 7: 조건문 활용
행성 크기에 따라 메시지 출력하기

```javascript
const planetSize = 5;

// 코드를 작성하세요
// 크기 10 이상: "거대한 행성"
// 크기 5 이상: "중간 크기 행성"
// 그 외: "작은 행성"
```

<details>
<summary>정답 보기</summary>

```javascript
const planetSize = 5;

if (planetSize >= 10) {
  console.log("거대한 행성");
} else if (planetSize >= 5) {
  console.log("중간 크기 행성");
} else {
  console.log("작은 행성");
}
```
</details>

---

## 8. JavaScript 디버깅

### 8-1. console.log 활용

```javascript
const earthAngle = 0.5;
console.log("earthAngle:", earthAngle);  // 값 확인

const earth = { x: 10, y: 0, z: 20 };
console.log("earth position:", earth);  // 객체 확인
```

---

### 8-2. 브라우저 개발자 도구

1. `F12` 키 누르기
2. **Console** 탭
   - 오류 메시지 확인
   - console.log 출력 보기
3. **Sources** 탭
   - 중단점(breakpoint) 설정
   - 한 줄씩 실행

---

### 8-3. 흔한 오류

#### 오류 1: 변수를 찾을 수 없음
```javascript
console.log(myVariable);  
// ReferenceError: myVariable is not defined

// 해결: 변수를 먼저 선언
const myVariable = 10;
console.log(myVariable);
```

---

#### 오류 2: 함수를 찾을 수 없음
```javascript
myFunction();  
// TypeError: myFunction is not a function

// 해결: 함수를 먼저 정의
function myFunction() {
  console.log("실행!");
}
myFunction();
```

---

#### 오류 3: 속성을 읽을 수 없음
```javascript
const obj = null;
console.log(obj.property);  
// TypeError: Cannot read property of null

// 해결: 객체가 존재하는지 확인
if (obj) {
  console.log(obj.property);
}
```

---

## 9. ES6+ 문법 (현대 JavaScript)

### 9-1. 구조 분해 할당

```javascript
// 배열 구조 분해
const [a, b, c] = [1, 2, 3];
console.log(a);  // 1

// 객체 구조 분해
const planet = { name: "지구", size: 2 };
const { name, size } = planet;
console.log(name);  // "지구"
```

**프로젝트에서:**
```javascript
import { ref, onMounted } from 'vue';
//       ↑ 구조 분해로 가져오기
```

---

### 9-2. 템플릿 리터럴

```javascript
const name = "지구";
const size = 2;

// 기존 방식
console.log("행성 이름: " + name + ", 크기: " + size);

// 템플릿 리터럴 (백틱 사용)
console.log(`행성 이름: ${name}, 크기: ${size}`);
```

---

### 9-3. 스프레드 연산자

```javascript
const arr1 = [1, 2, 3];
const arr2 = [...arr1, 4, 5];  // [1, 2, 3, 4, 5]

const obj1 = { a: 1, b: 2 };
const obj2 = { ...obj1, c: 3 };  // { a: 1, b: 2, c: 3 }
```

---

## 10. 다음 단계

JavaScript 기초를 익혔다면:

1. ✅ **Vue.js 기초 학습**
   - ref()와 반응형
   - onMounted() 생명주기
   - 템플릿 문법

2. ✅ **Three.js 기초 학습**
   - 3D 그래픽 기본 개념
   - Scene, Camera, Renderer
   - Geometry와 Material

3. ✅ **통합 학습 가이드**
   - 전체 로드맵
   - 실전 프로젝트 시작

4. ✅ **실전 프로젝트**
   - 태양계 시뮬레이션 만들기
   - 코드 이해하고 수정하기

---

## 📚 추가 학습 자료

### 온라인 강의
- 생활코딩 JavaScript: https://opentutorials.org/course/743
- MDN JavaScript Guide: https://developer.mozilla.org/ko/docs/Web/JavaScript/Guide
- JavaScript.info: https://ko.javascript.info/

### 연습 사이트
- CodeWars: https://www.codewars.com
- Programmers: https://programmers.co.kr
- LeetCode: https://leetcode.com

---

## ✅ 체크리스트

JavaScript를 이해했는지 체크해보세요:

### 기초 개념
- [ ] const와 let의 차이를 안다
- [ ] 함수를 만들고 호출할 수 있다
- [ ] 화살표 함수를 이해한다
- [ ] 객체와 배열을 만들 수 있다
- [ ] for 반복문을 사용할 수 있다

### 프로젝트 이해
- [ ] import 문이 무엇인지 안다
- [ ] Math.cos, Math.sin이 무엇인지 안다
- [ ] 객체 속성 접근(점 표기법)을 이해한다
- [ ] animate 함수의 역할을 이해한다
- [ ] earthAngle += 0.01의 의미를 안다

### 실전 능력
- [ ] console.log로 디버깅할 수 있다
- [ ] 오류 메시지를 읽을 수 있다
- [ ] 코드를 보고 이해할 수 있다
- [ ] 간단한 수정을 할 수 있다

---

**다음 문서:** Vue.js 기초로 넘어가세요! 🚀