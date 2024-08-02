# Operator
## 💡 1. 산술연산자

---

### ☁️ 이항 산술 연산자

2개의 피연산자를 산술 연산하여 숫자 값을 만든다.

| 연산자 | 의미 | 연산자 | 의미 |
| --- | --- | --- | --- |
| + | 덧셈 | * | 곱셈 |
| - | 뺄셈 | / | 나눗셈 |
| ** | 지수화 | % | 나머지 |

### ☁️ 단항 산술 연산자

| 연산자 | 의미 | 연산자 | 의미 |
| --- | --- | --- | --- |
| ++ | 증가 | — | 감소 |
| - | 숫자의 부호를 반대로 바꾼다. |  |  |
- 전위 연산자는 먼저 피연산의 값을 증가/감소 시킨후, 다른 연산을 수행한다.
- 후위 연산자는 먼저 다른 연산을 수행한 후, 피연산자의 값을 증가/감소 시킨다.

```jsx
let x = 5;
let y = 5;

// 전위 연산자
console.log(++x); // 출력: 6
console.log(x);   // 출력: 6

// 후위 연산자
console.log(y++); // 출력: 5
console.log(y);   // 출력: 6
```

### ☁️ +

- 숫자 타입이 아닌 피연산자에 +단항 연산자를 사용하면 피연산자를 숫자 타입으로 변환하여 반환한다.
- 피연산자 중 하나 이상이 문자열인 경우 문자열 연결 연산자로 동작한다.

```jsx
// 숫자 타입이 아닌 피연산자에 단항 연산자로 사용
let str = "123";
console.log(+str); // 출력: 123 (문자열 "123"이 숫자로 변환됨)

// 피연산자 중 하나 이상이 문자열인 경우 문자열 연결 연산자로 동작
let num1 = 10;
let str1 = "20";
console.log(num1 + str1); // 출력: "1020" (숫자 10과 문자열 "20"이 문자열로 연결됨)

// true는 1로 타입 변환된다.
1 + true; // -> 2

// false는 0으로 타입 변환된다.
1 + false; // -> 1

// null은 0으로 타입 변환된다.
1 + null; // -> 1

// undefined는 숫자로 타입 변환되지 않는다.
+undefined;    // -> NaN
1 + undefined; // -> NaN
```

## 💡 2. 비교 연산자

---

| 연산자 | 설명 | 연산자 | 설명 |
| --- | --- | --- | --- |
| ==(동등비교) | 값이 같음 | ===(일치비교) | 값과 타입이 같음 |
| != | 값이 같음 | !== | 값과 타입이 같음 |
- 동등비교 연산자는 좌항과 우항의 피연산자를 비교할 때 암묵적 타입 변환을 통해 타입을 일치시킨 후 같은 값인지 비교한다.
- 일치비교에서 주의할 점은 NaN는 항상 값지 않으므로 NaN인지 판단하고 싶다면 Number.isNaN()함수를 이용해야한다. 그리고 양의 0과 음의 0을 일치비교로 하면 true가 나오므로 Object.is()를 사용해서 비교한다.

```jsx
// NaN
let x = NaN;
console.log(Number.isNaN(x)); // 출력: true

let y = "문자열";
console.log(Number.isNaN(y)); // 출력: false

// 0 & -0
let a = 0;
let b = -0;
console.log(Object.is(a, b)); // 출력: false
```

## 💡 3. 삼항 연산자

---

<aside>
💭 조건식 ? 조건식이 true일때 반환할 값 : 조건식이 false일때 반환할 값

</aside>

```jsx
// 조건 ? 참일 때의 값 : 거짓일 때의 값
let x = 10;
let y = (x > 5) ? "크다" : "작거나 같다";
console.log(y); // 출력: "크다"

// 변수 a가 짝수인지 홀수인지 판별하여 결과를 출력
let a = 7;
let result = (a % 2 === 0) ? "짝수" : "홀수";
console.log(result); // 출력: "홀수"

let a = 10;
let b = 20;
let result = (a > b) ? "a가 크다" : (a < b) ? "b가 크다" : "a와 b는 같다";
console.log(result); // 출력: "b가 크다"
```

## 💡 4. 논리 연산자

---

### ☁️ 드모르간의 법칙

- !(P && Q) === (!P || !Q)
- // !(P || Q) === (!P && !Q)

```jsx
// !(P && Q) === (!P || !Q)
let P = true;
let Q = false;
let result1 = !(P && Q);
let result2 = (!P || !Q);
console.log(result1 === result2); // 출력: true

// !(P || Q) === (!P && !Q)
let P = true;
let Q = false;
let result1 = !(P || Q);
let result2 = (!P && !Q);
console.log(result1 === result2); // 출력: true
```

# Type Casting

## 💡 0.Type Casting

---

기존 원시 값을 직접 변경하는 것이 아니라 기존 원시값을 사용해 다른 타입의 새로운 원시 값을 생성하는것이다.

## 💡 1. implicit coercion(암묵적 타입 변환)

---

- 기존 변수 값을 재할당하여 변경하는 것이 아니라 자바스크립트 엔진은 표현식을 에러 없이 평가하기 위해 피연산자의 값을 암묵적 타입 변환해 새로운 타입의 값을 만들어 한 번 사용하고 버린다.
- 암묵적 타입변환이 발생하면 문자열, 숫자 , 불리언과 같은 원시 타입중 하나로 타입을 자동변환하다.

```jsx
// 피연산자가 모두 문자열 타입이어야 하는 문맥
'10' + 2 // -> '102'

// 피연산자가 모두 숫자 타입이어야 하는 문맥
5 * '10' // -> 50

// 피연산자 또는 표현식이 불리언 타입이어야 하는 문맥
!0 // -> true
if (1) { }
```

### ☁️ 문자열 타입변환

```jsx
// 숫자 타입
0 + ''         // -> "0"
-0 + ''        // -> "0"
1 + ''         // -> "1"
-1 + ''        // -> "-1"
NaN + ''       // -> "NaN"
Infinity + ''  // -> "Infinity"
-Infinity + '' // -> "-Infinity"

// 불리언 타입
true + ''  // -> "true"
false + '' // -> "false"

// null 타입
null + '' // -> "null"

// undefined 타입
undefined + '' // -> "undefined"

// 심벌 타입
(Symbol()) + '' // -> TypeError: Cannot convert a Symbol value to a string

// 객체 타입
({}) + ''           // -> "[object Object]"
Math + ''           // -> "[object Math]"
[] + ''             // -> ""
[10, 20] + ''       // -> "10,20"
(function(){}) + '' // -> "function(){}"
Array + ''          // -> "function Array() { [native code] }"
```

### ☁️ 문자열 타입변환

*, -, / 는 숫자로 변환한다. 그래서 산술 연산자의 모든 피연산자는 코드 문맥상 숫자 타입이어야한다.

```jsx
// 문자열 타입
+''       // -> 0
+'0'      // -> 0
+'1'      // -> 1
+'string' // -> NaN

// 불리언 타입
+true     // -> 1
+false    // -> 0

// null 타입
+null     // -> 0

// undefined 타입
+undefined // -> NaN

// 심벌 타입
+Symbol() // -> TypeError: Cannot convert a Symbol value to a number

// 객체 타입
+{}             // -> NaN
+[]             // -> 0
+[10, 20]       // -> NaN
+(function(){}) // -> NaN
```

### ☁️ 불리언 타입으로 변환

자바스크립트 엔진은 불리언 타입이 아니값을 Truthy & Falsy로 구분한다.

- Truthy : 불리언 컨텍스트에서 `true`로 평가되는값이다
    1. 모든 비어있지 않은 문자열 (예: `'hello'`)
    2. 모든 숫자, 0을 포함한 (예: `42`, `1`, `3.14`)
    3. 모든 객체 (예: `{}`, `[]`, `function() {}`)
    4. `true` (불리언 값 자체)
- Falsy : Falsy 값은 불리언 컨텍스트에서 `false`로 평가되는 값이다.
    1. 빈 문자열 (`''`)
    2. 숫자 0 (`0`)
    3. `null`
    4. `undefined`
    5. `NaN` (Not a Number)
    6.  `false` (불리언 값 자체)

## 💡 2. type coercion(타입 강제 변환)

---

명시적 타입 변환은 타입을 변경하겠다는 개발자의 의지가 코드에 명백히 드러난다. 이는 코드의 가독성을 높이고 예상치 못한 동작을 방지하기 위해 사용된다. 주로 내장 함수를 사용하여 타입을 변환한다.

### ☁️ 문자열 타입으로 변환

1. String 생성자 함수를 new 없이 호출한다.
2. Object.prototype.toString() 매서드를 사용한다.
3. 문자열 연결 연산자를 사용한다.

```jsx
// 1. String 생성자 함수를 new 연산자 없이 호출하는 방법
// 숫자 타입 => 문자열 타입
String(1);        // -> "1"
String(NaN);      // -> "NaN"
String(Infinity); // -> "Infinity"
// 불리언 타입 => 문자열 타입
String(true);     // -> "true"
String(false);    // -> "false"

// 2. Object.prototype.toString 메서드를 사용하는 방법
// 숫자 타입 => 문자열 타입
(1).toString();        // -> "1"
(NaN).toString();      // -> "NaN"
(Infinity).toString(); // -> "Infinity"
// 불리언 타입 => 문자열 타입
(true).toString();     // -> "true"
(false).toString();    // -> "false"

// 3. 문자열 연결 연산자를 이용하는 방법
// 숫자 타입 => 문자열 타입
1 + '';        // -> "1"
NaN + '';      // -> "NaN"
Infinity + ''; // -> "Infinity"
// 불리언 타입 => 문자열 타입
true + '';     // -> "true"
false + '';    // -> "false"
```

### ☁️ 숫자 타입으로 변환

1. Number 생성자 함수를 new 없이 호출한다.
2. parseInt(), parseFloat() 메서드를 사용한다.
3. + 단항 연산자를 사용한다.
4. * 산술 연산자를 사용한다.

```jsx
// 1. Number 생성자 함수를 new 연산자 없이 호출하는 방법
// 문자열 타입 => 숫자 타입
Number('0');     // -> 0
Number('-1');    // -> -1
Number('10.53'); // -> 10.53
// 불리언 타입 => 숫자 타입
Number(true);    // -> 1
Number(false);   // -> 0

// 2. parseInt, parseFloat 함수를 사용하는 방법(문자열만 변환 가능)
// 문자열 타입 => 숫자 타입
parseInt('0');       // -> 0
parseInt('-1');      // -> -1
parseFloat('10.53'); // -> 10.53

// 3. + 단항 산술 연산자를 이용하는 방법
// 문자열 타입 => 숫자 타입
+'0';     // -> 0
+'-1';    // -> -1
+'10.53'; // -> 10.53
// 불리언 타입 => 숫자 타입
+true;    // -> 1
+false;   // -> 0

// 4. * 산술 연산자를 이용하는 방법
// 문자열 타입 => 숫자 타입
'0' * 1;     // -> 0
'-1' * 1;    // -> -1
'10.53' * 1; // -> 10.53
// 불리언 타입 => 숫자 타입
true * 1;    // -> 1
false * 1;   // -> 0
```

### ☁️ 불리언 타입으로 변환

1. Boolean 생성자 함수를 new 없이 호출한다.
2. !부정 논리 연산자를 두번 사용한다.
```jsx
// 1. Boolean 생성자 함수를 new 연산자 없이 호출하는 방법
// 문자열 타입 => 불리언 타입
Boolean('x');       // -> true
Boolean('');        // -> false
Boolean('false');   // -> true
// 숫자 타입 => 불리언 타입
Boolean(0);         // -> false
Boolean(1);         // -> true
Boolean(NaN);       // -> false
Boolean(Infinity);  // -> true
// null 타입 => 불리언 타입
Boolean(null);      // -> false
// undefined 타입 => 불리언 타입
Boolean(undefined); // -> false
// 객체 타입 => 불리언 타입
Boolean({});        // -> true
Boolean([]);        // -> true

// 2. ! 부정 논리 연산자를 두번 사용하는 방법
// 문자열 타입 => 불리언 타입
!!'x';       // -> true
!!'';        // -> false
!!'false';   // -> true
// 숫자 타입 => 불리언 타입
!!0;         // -> false
!!1;         // -> true
!!NaN;       // -> false
!!Infinity;  // -> true
// null 타입 => 불리언 타입
!!null;      // -> false
// undefined 타입 => 불리언 타입
!!undefined; // -> false
// 객체 타입 => 불리언 타입
!!{};        // -> true
!![];        // -> true
```
