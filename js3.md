## 3장

### 변수

이름이 붙은 값으로, 값이 언제든 바뀔 수 있음

- 변수선언 - var, let

    `let currentTempC = 22; // 섭씨온도`

- 초기값을 설정하지 않으면 특별한 값 `undefined`가 할당됨

    `let currentTempC;  // let currentTempC = undefined; 와 같음`

- 하나의 let문에서 여러 개의 변수 선언 가능

    `let targetTempC, room1 = "conference_room_a", room2 = "lobby";`

### 상수

변수와 마찬가지로 값을 할당받을 수 있지만, 한번 할당한 값을 바꿀 수 없음

`const ROOM_TEMP_C = 21.5, MAX_TEMP_C = 30;`

### 식별자

식별자는 변수, 상수, 함수의 이름

- 글자, $, 밑줄(_)로 시작
- 글자, 숫자, $, 밑줄 사용
- 유니코드 문자 사용 가능
- 예약어X (ex: let)
- 대문자 시작X

#### 카멜 케이스

`currentTempC, anIdentifierName`

#### 스네이크 케이스

`current_temp_c, an_identifier_name`

### 리터럴

리터럴은 값을 만드는 방법

```js
let room1 = "conference_room_a";    // 따옴표 안은 리터럴

let currentRoom = room1;            // 이제 currentRoom의 값은 room1의 값과 같다.

currentRoom = conference_room_a;    // 에러발생
                                    // conference_room_a란 식별자는 존재하지 않는다.
```

### 원시 타입과 객체

자바스크립트의 값은 원시 값(primitive) 또는 객체(object)

#### 원시 타입

원시 타입은 불변(immutable)

```js
let str = "hello";
str = "world";
```

str은 불변 값 "hello"로 초기화 후 새로운 불변 값 "world"를 할당받음

"hello"와 "world"는 서로 다른 문자열

- 숫자
- 문자열
- 불리언
- null
- undefined
- 심볼

#### 객체

객체는 여러 가지 형태와 값을 가질 수 있음

- Array
- Date
- RegExp
- Map과 Weakmap
- Set과 WeakSet

원시타입|객체타입
-|-
숫자   | Number
문자열 | String
불리언 | Boolean

### 숫자

자바스크립트에는 10진수, 2진수, 8진수, 16진수의 네 가지 숫자형 리터럴을 인식

10진 리터럴에는 소수점 없는 정수, 소수점 있는 10진수(12.34 등), 과학에서 사용하는 지수 표기법을 쓸 수 있음

```js
let count = 10;         // 숫자 리터럴. count는 더블형
const blue = 0x0000ff;  // 16진수
const umask = 0o0022;   // 8진수
const roomTemp = 21.5;  // 10진수
const c = 3.0e6;        // 지수 (3.0 x 10^6 = 3,000,000)
const e = -1.6e-19;     // 지수 (-1.6 x 10^-19 = 0.00000000000000000016)
const inf = Infinity;
const ninf = -Infinity;
const nan = NaN;        // "숫자가 아님"
```

`10진수, 16진수, 지수 등 어떤 리터럴 형식을 사용하더라도 결국 숫자는 더블 형식으로 저장됨`

```js
const small = Number.EPSILON;               // 1에 더했을 때 1과 구분되는 결과를 만들 수 있는
                                            // 가장 작은 값. 근사치는 2.2e-16
const bigInt = Number.MAX_SAFE_INTEGER;     // 표현할 수 있는 가장 큰 정수
const max = Number.MAX_VALUE;               // 표현할 수 있는 가장 큰 숫자
const minInt = Number.MIN_SAFE_INTEGER;     // 표현할 수 있는 가장 작은 정수
const min = Number.MIN_VALUE;               // 표현할 수 있는 가장 작은 숫자
const nInf = Number.NEGATIVE_INFINITY;      // -Infinity
const nan = Number.NaN;                     // NaN
const inf = Number.POSITIVE_INFINITY;       // Infinity
```

### 문자열

자바스크립트 문자열은 유니코드 텍스트(이모티콘 포함)

문자열 리터럴에는 작은따옴표, 큰따옴표, 백틱을 사용

#### 이스케이프

```js
const dialog = 'Sam looked up, and said "hello, old friend!", as Max walked in.';
const imperative = "Don't do that!";
```

```js
// 에러 발생
const dialog = "Sam looked up and said "don't do that!" to Max.";
```

```js
const dialog1 = "He looked up and said \"don't do that!\" to Max.";
const dialog2 = 'He looked up and said "don\'t do that!" to Max.';
```

### 특수문자

코드|설명
-|-
\n|
\r|
\t|
\'|
\"|
\`|
\$|
\|
\uXXXX|
\xXX|
\0|
\v|
\b|
\f|

#### 템플릿 문자열

문자열 안에 값을 쓸 수 있음

- ES6 이전에는 문자열 병합을 사용

```js
let currentTemp = 19.5;
// 00b0는 온도를 나타내는 유니코드 코드 포인트
const message = "The current temperature is " + currentTemp + "\u00b0C";
```

- ES6에서는 문자열 템플릿(백틱 사용)

```js
let currentTemp = 19.5;
const message = `The current temperature is ${currentTemp}\u00b0C`;
```

#### 여러 줄 문자열

```js
const multiline = "line1\n" +
    "line2\n" + 
    "line3";
```

따옴표와 백탁 섞어 쓸 수 있음

```js
const multiline = `Current temperature:\n` +
    `\t${currentTemp}\u00b0C\n` +
    "Don't worry... the heat is on!";
```

#### 숫자와 문자열

숫자를 따옴표 안에 넣으면 문자열

하지만, 자바스크립트는 숫자가 들어있는 문자열을 자동으로 숫자로 바꿈

```js
const result1 = 3 + '30';   // 3이 문자열로 바뀌어 '330'이 된다.
const result2 = 3 * '30';   // 30이 숫자로 바뀌어 숫자 90이 된다.
```

#### 심볼

심볼은 항상 유일하며, 다른 어떤 심볼과도 일치하지 않음

심볼은 Symbol() 생성자로 만듬

```js
const RED = Symbol("The color of a sunset!");
const ORANGE = Symbol("The color of a sunset!");
RED === ORANGE  // false: 심볼은 모두 서로 다름
```

#### null 과 undefined

```js
let currentTemp;            // 암시적으로 undefined
const targetTemp = null;    // null
currentTemp = 19.5;         // currentTemp에는 이제 값이 있다.
currentTemp = undefined;    // 권장X
```

#### 객체

객체의 본질은 컨테이너

컨테이너의 내용물은 시간이 지나면서 바뀔 수 있지만, 내용물이 바뀐다고 컨테이너가 바뀌지는 않는다.

객체는 중괄호를 사용

객체의 콘텐츠는 프로퍼티 또는 멤버라고 부른다.

프로퍼티는 이름(키)와 값으로 구성

프로퍼티 이름은 문자열 또는 심볼이어야 함

```js
const obj = {};                 // 빈 객체 선언
obj.color = "yellow";           // obj에 color 프로퍼티 추가
obj["not an identifier"] = 3;
obj["not an identifire"];       // 3
obj["color"];                   // "yellow"
```

```js
const SIZE = Symbol();
obj[SIZE] = 8;
obj[SIZE];              // 8
```

```js
const sam1 = {
    name: 'Sam',
    age: 4,
};

const sam2 = { name: 'Sam', age: 4 };   // 한줄로 선언

const sam3 = {      // 프로퍼티 값도 객체가 될 수 있음
    name: 'Sam',
    Classification: {
        kingdom: 'Anamalia',
        phylum: 'Chordata',
        class: 'Mamalia',
        order: 'Carnivoria',
        family: 'Felidae',
        subfamily: 'Felinae',
        genus: 'Felis',
        species: 'catus',
    },
};
```

```js
sam3.classification.family;
sam3["classification"].family;
sam3.classification["family"];
sam3["classification"]["family"];
```

```js
// 함수 추가
sam3.speak = function() { return "Meow!"; };
sam3.speak();               // "Meow!"
```

```js
// 객체에서 프로퍼티 제거
delete sam3.classification; // classification 트리 전체 삭제
delete sam3.speak;          // speak 함수 삭제
```

#### Number, String, Boolean 객체

```js
const s = "hello";
s.toUpperCase();        // "HELLO"
```

s는 마치 객체처럼, 함수 프로퍼티를 가진 것 처럼 보인다.

s는 원시 문자열 타입이다.

자바스크립트는 일시적인 String 객체를 만든 것

이 임시 객체에 toUpperCase 함수가 들어있음

`자바스크립트는 함수를 호출하는 즉시 임시 객체를 파괴`

```js
const s = "hello";
s.rating = 3;       // 에러가 없음
s.rating            // undefined
```

#### 배열

- 배열 크기는 고정되지 않고, 언제든 요소를 추가, 제거 가능
- 요소의 데이터 타입을 가리지 않음
- 배열 요소는 0으로 시작

```js
const a1 = [1, 2, 3, 4];
const a2 = [1, 'two', 3, null];
const a3 = [
    "What the hammer? What the chain?",
    "In what furnace was thy brain?",
    "What the anvil? What dread grasp",
    "Dare its deadly terrors clasp?",
];
const a4 = [
    { name: "Ruby", hardness: 9 },
    { name: "Diamond", hardness: 10 },
    { name: "Topaz", hardness: 8 },
];
const a5 = [
    [1, 3, 5],
    [2, 4, 6],
];

const arr = ['a', 'b', 'c'];
arr.length;         // 3
arr[0];             // 'a'
arr[arr.length-1];  // 'c'
```

#### 객체와 배열 마지막 쉼표

마지막 쉼표는 사용하든 안하든 상관없다.

JSON에는 마지막 쉼표를 허용하지 않는다.

#### 날짜

```js
const now = new Date();
now;

const halloween = new Date(2016, 9, 31);    // 월은 0에서 시작. 즉, 9는 10월
const halloweenParty = new Date(2016, 9, 31, 19, 0);    // 19:00 = 7:00 pm

halloweenParty.getFullYear();       // 2016
halloweenParty.getMonth();          // 9
halloweenParty.getDate();           // 31
halloweenParty.getDay();            // 1 (월요일, 0은 일요일)
halloweenParty.getHours();          // 19
halloweenParty.getMinutes();        // 0
halloweenParty.getSeconds();        // 0
halloweenParty.getMilliseconds();   // 0
```

#### 정규 표현식

#### 맵과 셋

#### 데이터 타입 변환

- 숫자로 변환

```js
const numStr = "33.3";
const num = Number(numStr);
// Number 객체의 인스턴스가 아니다.
```

숫자로 바꿀 수 없는 문자열은 NaN이 반환

```js
const a = parseInt("16 volts", 10); // "volts" 는 무시. 16은 10진수
const b = parseInt("3a", 16);       // 16진수 3a를 10진수로 바꿈. 결과는 58
const c = parseFloat("15.5 kph");   // "kph" 는 무시. parseFloat는 항상 기수가 10이라고 가정
```

```js
const d = new Date();   // 현재 날짜
const ts = d.valueOf(); // UTC 1970년 1월 1일 자정으로부터 몇 밀리초가 지났는지 나타내는 숫자
```

- 문자열로 변환

```js
const n = 33.5;
n;              // 33.5 - 숫자
const s = n.toString();
s;              // "33.5" - 문자열

const arr = [1, true, "hello"];
arr.toString();     // "1,true,hello" - 쉼표로 연결된 문자열
```

- 불리언으로 변환

```js
const n = 0;            // 거짓 같은 값
const b1 = !!n;         // false
const b2 = Boolean(n);  // false
```

### 요약

- 자바스크립트에는 여섯 가지 원시 타입과 객체 타입이 있다.
- 자바스크립트의 모든 숫자는 배정도 부동소수점 숫자(더블)이다.
- 배열은 특수한 객체이며, 객체와 마찬가지로 매우 강력하고 유연한 데이터 타입이다.
- 날짜, 맵, 셋, 정규표현식 등 자주 사용할 다른 데이터 타입은 특수한 객체이다.

***원시형과 참조형***

원시 값은 불변이고, 원시 값을 복사/전달할 때는 값 자체를 복사/전달

```js
let a = 1;      // 원본
let b = a;      // 사본. b는 1. a가 아님
a = 2;          // 원본 값 변경
console.log(b)  // 1. 사본의 값은 바뀌지 않음
```

객체는 가변이고, 객체를 복사/전달할 때는 객체가 아니라, 그 객체를 가리키고 있다는 사실(참조)을 복사/전달

```js
let o = { a: 1 };
let p = o;          // p는 o가 '가리키고 있는 것'을 가리킴
o.a = 2
console.log(p)      // {a: 2}
```

!주의!

```js
let o = { a: 1 };
let p = o;          // p는 o가 '가리키고 있는 것'을 가리킴
    p === o         // true
o = { a: 2 };       // 이제 o는 다른 것을 가리킴. {a: 1}을 수정한 것이 아님
    p === o         // false
console.log(p)      // {a: 1}
```

객체를 가리키는 변수는 그 객체를 가리키고 있을 뿐, 객체 자체는 아니다. 따라서 변수와 객체는 결코 같지 않다.

```js
let q = {a: 1};
q === {a: 1};       // false
```