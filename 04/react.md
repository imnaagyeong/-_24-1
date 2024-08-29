### 모듈 내보내기(export) & 모듈 불러오기(import)

- 모듈 내보내기(export) : 모듈을 다른 파일에서 사용하려면 해당 모듈에서 내보내기를 해야한다.
    
    ```jsx
    // MyModule.js
    const myFunction = () => {
      // ...
    };
    
    export default myFunction;
    ```
    
- 모듈 불러오기(import): 다른 파일에서 모듈을 사용하려면 **`import`** 키워드를 사용한다.
    
    ```jsx
    // AnotherFile.js
    import myFunction from './MyModule';
    
    // myFunction을 사용할 수 있음
    ```
    

### 마운트(Mounting) & 업데이트 & 언마운트(Unmounting) : 컴포넌트의 생명주기와 연관이 있다.

- 마운트(Mounting) : 컴포넌트가 처음으로 생성되어 브라우저에 나타나는 것이다. 이때 호출되는 함수는 아래와 같다.
    1. **`constructor`:** 컴포넌트의 생성자 메서드로, 컴포넌트를 만들 때 처음으로 호출된다. state의 값을 초기기화 할때 사용한다.
    2. **`render`:** 컴포넌트가 렌더링되는 메서드로, UI를 구성한다.
    3. **`componentDidMount`:** 컴포넌트가 DOM에 마운트된 후에 호출되는 메서드로, 초기 데이터 로딩 및 외부 라이브러리 초기화 등을 수행한다. 
- 업데이트 : 컴포넌트가 업데이트 될 때 실행되는 함수들이다.
    1. **`getDerivedStateFromProps`**  : 새로운 props와 현재 state를 비교하여 새로운 state를 반환하거나 **`null`**을 반환할 수 있다. 주로 state를 props에 따라 동적으로 업데이트할 때 사용된다.
    2. **`shouldComponentUpdate`** : 컴포넌트를 리렌더링 할지 말지를 결정하는 메서드이다. 성능 최적화를 위해 사용되며, 변경된 props 또는 state를 비교하여 리렌더링이 필요한지 결정한다.
    3. **`render`** : 컴포넌트를 새로운 값으로 업데이트하고 새로운 UI를 렌더링한다. 
    4. **`getSnapshotBeforeUpdate`**: 변경된 요소에 대하여 DOM 객체에 반영되기 직전에 호출되는 메서드이다. 이 메서드의 반환 값은 **`componentDidUpdate`** 메서드의 세 번째 인자로 전달되며, 주로 DOM 조작이나 애니메이션 등의 작업을 수행하기 위해 사용된다.
    5. **`componentDidUpdate`** : 컴포넌트 업데이트 작업이 끝난 후에 호출되는 메서드로, 리렌더링이 완료된 후에 추가적인 작업을 수행할 때 사용된다. 
- 언마운트(Unmounting) : 컴포넌트가 DOM에서 제거되는 과정을 의미한다.
    1. **`componentWillUnmount`:** 컴포넌트가 DOM에서 제거되기 전에 호출되는 메서드로, 리소스 해제나 이벤트 리스너 등의 정리 작업을 수행한다.

### ARROW함수(람다함수)

- 기존의 함수 선언문과 함수 표현식보다 간결한 문법을 제공하고, 함수 내부에서 **`this`**의 동작을 더 일관성 있게 다룬다.
- 단일 표현식을 반환할 때 중괄호 **`{}`** 및 **`return`** 키워드를 생략할 수 있다.
    
    ```jsx
    // 일반 함수 표현식
    const add = function(a, b) {
      return a + b;
    };
    
    // Arrow 함수
    const add = (a, b) => a + b;
    ```
    
- 일반 함수는 호출될 때 자신이 종속된 객체를 `this`로 가리킨다. 이는 함수가 어디서 호출된 위치에 따라 `this`가 동적으로 결정되는 것을 의미한다. 람다 함수는 함수가 정의된 위치에서 가까운 범위의 함수의 this를 참조한다. 람다함수를 사용하면 항상 동일한 `this` 를 가리킨다.
- 매개변수가 하나뿐이라면 괄호 **`()`**를 생략할 수 있다.
    
    ```jsx
    // 일반 함수 표현식
    const square = function(x) {
      return x * x;
    };
    
    // Arrow 함수
    const square = x => x * x;
    ```
    
- Arrow 함수는 콜백 함수로 많이 사용된다.
    
    ```jsx
    const numbers = [1, 2, 3, 4, 5];
    // 일반 함수 표현식
    const squared = numbers.map(function(number) {
      return number * number;
    });
    
    // Arrow 함수
    const squared = numbers.map(number => number * number);
    ```
    

### 배열 비구조화 할당

JavaScript에서 배열의 값을 추출하여 변수에 할당하는 문법이다. 이를 통해 배열의 각 요소를 개별 변수로 쉽게 추출할 수 있다.

```jsx
const num = [1, 2, 3];
const one = numbers[0];
const two = numbers[1];
const three = numbers[2];

// 비구조화 할당
const num = [1, 2, 3];
const [one, two, three] = numbers; 
```
