# Variable
## 💡 변수란 무엇인가?

---

<aside>
📍 Variable : 변수는 하나의 값을 저장하기 위해 확보한 메모리 공간 자체 또는 그 메모리 공간을 식별하기 위해 붙인 이름을 말한다.

- 변수이름(식별자) : 메모리 공간에 저장된 값을 식별할 수 있는 고유이름, 식별자는 메모리 주소를 기억하고 있어 주소를 통해 값에 접근할 수 있다.
- 변수값 : 변수에 저장된 값
- 할당(Assignment) : 변수에 값을 저장하는 것
- 참조(Reference) : 변수에 저장된 값을 읽어들이는 것
</aside>

<aside>
📍 var, let const 선언,초기화,할당 순서

- var는 1. 선언 & 초기화, 2. 할당 순으로 변수를 생성한다.
- let은 1. 선언단계, 2. 초기화단계, 3. 할당 단계 순으로 변수를 생성한다.
- const는 선언+초기화+할당이 한번에 일어난다.
</aside>

## 💡 변수 선언

---

<aside>
📍 변수 선언 : 값을 저장하기위한 메모리 공간을 확보하는 것이다.

- var, let, const를 사용하여 변수를 선언한다.
- var는 한번 선언된 변수를 다시 선언할 수 있다. 반면에 let은 불가능하다. 그리고 둘다 업데이트가 가능하다.
- 자바 스크립트는 변수 선언시 초기화를 하지 않으면 undefined으로 암묵적으로 초기화되어있다.
- 변수를 선언하지 않고 사용할려고 하면 Reference Error가 발생한다.
- 변수이름을 비롯한 모든 식별자는 execution context에 등록된다. execution context는 자바스크립트 엔진이 소스코드를 평가하고 실행하기 위해 필요한 환경을 제공하고 코드의 실행 결과를 실제로 관리하는 영역이다.
</aside>

## 💡 변수 선언의 실행 시점과 변수 호이스팅

---

1. var : 호이스팅(hoisting)이 발생하여 선언부가 스코프의 맨 위로 끌어올려지기 때문에 선언 전에 변수에 접근할 수 있다. 이때 변수는 undefined로 초기화 된다. 그래서 함수선언이 뒤에 있어도 참조 에러가 발생하지 않는다. var는 함수 스코프이다.
    
    ```jsx
    console.log(greeting); // undefined
    
    var greeting = 'hello';
    
    console.log(greeting); // hello
    ```
    
    
2. const & let : 블록 범위(block scope)를 가지고 있으며, 호이스팅은 발생하지만 초기화는 호이스팅되지 않는다. 따라서 TDZ(Temporal Dead Zone)에 해당 변수가 들어가게 되고, 선언 이전에 변수에 접근하면 ReferenceError가 발생한다. var와 달리 초기에 초기화되지 않는다. 
    
    ```jsx
    console.log(score); // [TDZ] , ReferenceError 
    
    let score;
    
    console.log(score); // undefined
    
    score = 'hello'
    console.log(score); // hello
    ```

## 💡 값의 할당

---

1. var : 변수 선언은 소스평가 과정에서 실행되지만 값의 할당은 런타임에 실행되므로 주의해야한다. 변수는 선언당시 undefined로 할당이 되고 초기화를 할때 재할당이 이루어진다.
    
    ```jsx
    // 예제 04-08
    console.log(score); // undefined
    
    var score;  // ① 변수 선언
    score = 80; // ② 값의 할당
    
    console.log(score); // 80
    
    //예제 04-10 : 변수선언만 호이스팅이 발생하기 때문이다.
    console.log(score); // undefined
    
    score = 80; // 값의 할당
    var score = 50;  // 변수 선언
    
    console.log(score); // 50
    ```
    
2. const : 변수에 저장된 값을 상수로 여겨 재할당할 수 없다. 선언과 동시에 값을 할당해야하며, 이후에는 재할당이 불가능하다..


# Primitive types

<aside>
💬 type

- 원시 타입(변경불가능한 값)으로는 number, string, boolean, undefined, null, symbol가 있다. 이 이외의 값들은 객체타입이다.
- 원시타입은 고정된 크기로 call stack에 저장이 되고 실제 데이터가 변수에 할당된다. 참조타입은 데이터 크기가 정해지지 않고 데이터 실제값은 heap에 저장이되고 call stack에 heap의 주소가 저장된다.
    
    
- 타입 구분할 수 있는 방법 연산자로 typeof을 사용하거나 메서드로 Object.is(a, b)를 사용한다.
- 데이터 타입이 필요한이유
    1. 값을 저장할 때 확보해야하는 메모리 공간의 크기를 결정하기 위해
    2. 값을 참조할때 한번에 읽어 들여야할 메모리 공간의 크기를 결정하기 위해
    3. 메모리에서 읽어 들인 2진수를 어떻게 해석할지 결정하기 위해
- 자바스크립트는 타입을 동적으로 바뀔수있는 동적 타입 언어이다. 즉 자바스크립트의 변수는 선언이 아닌 할당에 의해 타입이 결정된다. 그리고 재할당에 의해 변수의 타입은 언제든지 동적으로 변할 수 있다. 즉 같은 변수가 여러개의 타입을 가질 수 있고 타입을 명시하지 않아도 된다.
</aside>

## 💡 1. number

---

<aside>
💭 **number**

1. 정수와 실수 구분 없이 하나의 숫자 타입만 존재한다. 숫자 타입의 값은 64부동소수점 형식을 따르므로 모든 수를 실수로 처리한다. 그러므로 1과 1.0은 같다고 판단한다.
2. 숫자 타입은 주로 연산을 수행하는게 사용된다.
3. 2진수, 8진수, 16진수를 표현하기 위한 데이터 타입을 제공하지 않으므로 이들 값을 참조하면 모두 10진수로 해석된다.
    
    ```jsx
    var binary = 0b01000001; // 2진수
    var octal = 0o101;       // 8진수
    var hex = 0x41;          // 16진수
    
    // 표기법만 다를 뿐 모두 같은 값이다.
    console.log(binary); // 65
    console.log(octal);  // 65
    console.log(hex);    // 65
    console.log(binary === octal); // true
    console.log(octal === hex);    // true
    ```
    
4. 특별한 값 3가지 : Infinity(양의 무한대),  -Infinity(음의 무한대), NaN(산술 연산 불가)
5. 0이 `0`과 `-0`으로 2개가 존재한다. 이는 비트 표현의 부호 비트가 다르기 때문에 발생한다. 
</aside>

### ☁️ 숫자형 형변환

- `+`을 변수명앞에 사용하면 바꿀려고하는 값이 전부 숫자일 경우 숫자로 변환한다.
    
    ```jsx
    let strNum = "123";
    let num = +strNum; // 문자열 "123"을 숫자로 변환
    console.log(num); // 출력: 123
    
    let strNums = ["1", "2", "3"];
    let nums = strNums.map(+); // 배열의 각 요소를 숫자로 변환
    console.log(nums); // 출력: [1, 2, 3]
    ```
    
- `Number()`를 사용하면 바꿀려고하는 값이 전부 숫자일 경우 숫자로 변환한다.
    
    ```jsx
    console.log(Number("10px")); // NaN
    ```
    
- `parseInt()` : 문자열을 처음부터 읽어서 숫자로 시작하는 부분을 정수로 변환한다. 그리고 두번째 매개변수로 진법을 전달해서 원하는 진수로 변환할 수 있다
    
    ```jsx
    console.log(parseInt("10", 2)); // 출력: 2 (이진수로 변환)
    console.log(parseInt("10px")); // 10
    console.log(parseInt("f3")); // NaN
    ```
    
- `parseFloat()` : 문자열을 읽어서 부동소수점으로 변환한다.
- `toString()` : 10진수를 → 2진수 /16진수로 바꿀때 사용한다.
    
    ```jsx
    let num = 10;
    
    num.toString(); // 10
    num.toString(2); // 1010
    
    let num2 = 255;
    num2.toString(16); // ff
    ```
    

### ☁️ 숫자형인지 판단하는 함수

- `isNaN(value)` : value가 숫자가 아니라면 true, 숫자라면 false를 반환한다.
- `isFinite(value)` : value가 유한한 숫자인지 확인한다. Infinity,  -Infinity, NaN인경우엔 false를 반환한다.

### ☁️ 반올림 함수

| 함수 | Math.floor(내림) | Math.ceil(올림) | Math.round(반올림) |
| --- | --- | --- | --- |
| 3.1 | 3 | 4 | 3 |
| 3.6 | 3 | 4 | 4 |
| -1.1 | -2 | -1 | -1 |
| -1.6 | -2 | -1 | -2 |

🧐 소수점 n번째에서 반올림을 하고 싶다면 num.toFixed(n)을 이용하자

### ☁️ 기타 수학 함수

- `Math.random()` : 0에서 1사이의 난수를 반환한다.
    
    ```jsx
    Math.floor(Math.random() * 100) + 1); // 1~100
    Math.floor(Math.random() * 20) + 1); // 1~20
    ```
    
- `Math.max(a,b,c,,)` & `Math.min(a,b,c,,,)` : 임의 개수의 인수에서 가장 큰것과 가장 작은 것을 반환하다.
- `Math.pow(n, power)` : n^power를 반환한다.

## 💡 2. string

---

<aside>
💭 **string**

1. 문자열은 큰따옴표, 작은 따옴표, 백틱으로 텍스트를 감싼다. 
2. 템플릿 리터럴 : 멀티라인 문자열, 표현식 삽입, 태그드 템플릿등 편리한 문자열 처리 기능을 제공한다. 백틱을 사용해 표현한다.
    - 멀티라인 문자열 : 일반 문자열 내에서 줄바꿈 등의 공백을 표현하기위해 \으로 시작하는 이스케이프 시퀀스를 사용한다.
        
        
        | 이스케이프 시퀀스 | 의미 | 이스케이프 시퀀스 | 의미 |
        | --- | --- | --- | --- |
        | \n  | 다음행으로 이동 | \’ |  작은 따옴표 |
        | \t | 수평 탭 | \”  | 큰따옴표 |
        | \uXXXX  | 유니코드 | \\  | 백 슬래시 |
    - 표현식 삽입 : 문자열은 + 연산자를 이용해 연결할 수 있다. 표현식은 ${}을 이용하 삽입한다.
3. 문자열은 불변이므로 새로운 문자열을 만들어 이전 문자열 대신 할당한다.
</aside>

### ☁️ character 접근하기

- str[index] : index번째 있는 문자에 접근할 수 있다. []는 음수인덱스에 대해서는 undefined를 반환한다.
- str.at(pos) : 음의 위치를 허용한다. 음수이면 pos문자열 끝부터 계산한다. str.at(-1)은 마지막 문자이다.

### ☁️ 문자열관련 함수

- `str.length` : 문자열의 길이를 알 수 있다.
- `str.toLowerCase()` & `str.toUpperCase()` : 각각 문자열의 문자를 소문자로 변환하거나 대문자로 변환하는 함수이다.
- `str.indexOf(substr, pos)` : 주어진 pos에서 시작해서 substr을 찾고 위치를 반환한다. 만약 substr을 찾기 못했다면 -1을 반환한다. str.lastIndexOf(substr, pos)는 문자열 끝부터 찾기 시작한다.
    
    ```jsx
    let srt "Hi guys. Nice to meet you.";
    
    str.indexOf('to'); // 14 - 0부터 시작한다.
    
    if(str.indexOf("Hi") > -1 ){
    	console.log("Hi가 포함된 문장입니다.");
    }
    ```
    
- `str.includes(substr, pos)` 함수는 문자열이 지정된 부분 문자열(substring)을 포함하고 있는지 여부를 확인하고 있으면 true없으면 false를 반환한다.
- `str.startsWith()` 및 `str.endsWith()` 메서드는 각각 주어진 부분 문자열이 문자열의 시작 혹은 끝에 있는지 여부를 확인하는 데 사용된다.
- `str.slice(start, end)` : 문자열에서 부분 문자열을 추출하는 데 사용된다. end가 없으면 문자열 끝까지 양수면 그 end는 포함하지않고 그 전까지이다. 음수이면 끝에서부터 센다.
- `str.substring(start, end)` 메서드는 문자열에서 부분 문자열을 추출하는 데 사용된다.  start와 end위치를 바꿔도 동작한다. 음수는 0으로 인식한다.
- `str.substr(start, count)` : 메서드는 문자열에서 부분 문자열을 추출하는 데 사용된다. start부터 count수만큼 가져온다.
    
    ```jsx
    let str = "abcdefg";
    
    str.slice(2) // 2~끝 cdefg
    str.slice(0,5) // 0~4 abcde
    str.slice(2, -2) // 끝(0)에서 ~ 2 efg
    
    str.substring(2, 5); //cde
    str.substring(5, 2); //cde
    // 두 메서드의 차이점은 slice()는 음수 값을 허용하고, 
    //substring()은 음수 값을 0으로 간주하는 것이다. 
    
    str.substr(2,4); // cdef
    str.substr(-4,2); // de
    ```
    
- `str.trim()` : 문자열의 시작과 끝에서 공백을 제거합니다.
- `str.repeat(n)` : 문자열을 n번 반복한다.

### ☁️ 문자열 비교

- 문자열은 알파벳 순서로 비교된다. 소문자는 대문자보다 크다.

## 💡 3. boolean

---

<aside>
💭 **boolean**

- 논리적 참, 거짓을 나타내는 true와 false뿐이다.
- 보통 프로그램의 흐름을 제어하는 조건문에서 자주 사용한다.
</aside>

## 💡 4. undefined

---

<aside>
💭 **undefined**

- 값이 할당되지 않은 변수의 기본값이다.
- 변수가 선언되었지만 초기화되지 않았거나 값이 할당되지 않았을 때 자동으로 할당된다.
- 함수에서 반환하지 않는 경우나 존재하지 않는 객체 속성에 접근할 때도 반환될 수 있다.
</aside>

## 💡 5. null

---

<aside>
💭 **null**

- 값이 없다는 것을 의도적으로 명시할 때 사용하는 값이다.
- 변수를 초기화할때 사용되거나, 프로그래머가 의도적으로 변수에 값이 없음을 할당할 때 사용된다.
- null은 객체를 나타내는데 사용될 수 있으며, 객체가 없음을 나타내기 위해 사용된다.
- 함수가 유효한 값을 반환할 수 없는 경우 에러대신 null을 반환한다.
- 객체가 아니지만 typeof를 사용하면 object로 나온다.
</aside>

## 💡 6. symbol

---

<aside>
💭 **symbol**

- 다른 값과 중복되지 않는 유일무이한 값이다. 주로 이름이 충돌할 위험이 없는 객체의 유일한 속성키를 만들기 위해 사용한다. 즉 유일한 식별자를 만들때 사용된다.
- Symbol 함수를 호출해 생성한다. 생성한 심벌값은 외부에 노출되지 않는다.
- 컴파일러 또는 인터프리터는 심벌 테이블이라고 부르는 자료구조를 통해 식별자를 키로 바인딩 된 값의 메모리 주소, 데이터 타입, 스코프등을 관리한다.
</aside>
