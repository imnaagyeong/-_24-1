## Class Components

<aside>
<img src="/icons/suit-diamond_blue.svg" alt="/icons/suit-diamond_blue.svg" width="40px" /> Class Components

- `render`함수가 무조건 필요하고, 그 안에서 보여줘야할 JSX를 반환한다. 화면에 무엇을 표시할지 파악해야 할 때마다 메서드를 호출한다.
- `Component` 클래스를 상속받아 구현된다. 이 클래스는 렌더링에 필요한 `render` 함수와 다양한 라이프사이클 함수를 제공한다.
- `context` : 클래스 구성요소의 context는 .을 이용해서 사용할 수 있다. Class Components는 한번에 하나의 context만 읽을 수 있다.
- `constructor`(props) : 생성자는 클래스 구성 요소가 마운트되기 전에 실행된다. `super(props)`를 호출하여 부모 클래스의 생성자를 실행하고, 초기 상태를 설정한다.
    
    ```jsx
    constructor(props) {
        super(props);
        this.state = { counter: 0 };
      }
    ```
    
</aside>

- Class Components 정의하기
    
    ```jsx
    import { Component } from 'react';
    
    class Greeting extends Component {
      render() {
        return <h1>Hello, {this.props.name}!</h1>;
      }
    }
    ```
    

## Functional Components

<aside>
<img src="/icons/suit-diamond_blue.svg" alt="/icons/suit-diamond_blue.svg" width="40px" /> Functional Components

- 자바 스크립트 함수를 이용하여 리액트에 대한 기능적 구성요소를 만들 수 있다.
- 주로 상태 관리나 라이프사이클 메서드를 활용하지 않아도 되는 간단한 UI 표현에 사용된다.
- 이 함수의 반환값은 DOM 트리에 렌더링할 JSX코드이다.
    - hook을 사용하여 상태를 관리한다. hook이 도입된 이후로 클래스형 컴포넌트보다 함수형 컴포넌트를 더 많이 사용한다.
    - `props` 매개변수를 통해 부모 컴포넌트로부터 전달된 데이터를 받아 사용할 수 있다.
</aside>

- Functional Components 정의하기
    
    ```jsx
    import React from 'react';
    
    const Greeting = (props) => {
      return <h1>Hello, {props.name}!</h1>;
    }
    
    export default Greeting;
    ```
    

```jsx
// App.js
import React from 'react';
import Test from './test';

function App() {
  return <Test>Test에게 전달해줘</Test>;
}

export default App;

// test.js
import React, { Children } from 'react';

const Test = (props) => {
    return ( // 여러 요소를 반환할때는 ()을 이용해 감싸줘야한다.
        <div>
        <h1>I want to say {props.comment}</h1>;
        <br />
        <h2>I get message {props.children}</h2>
        </div>
    );
};

Test.defaultProps = {
    comment : 'hi'
};

export default Test;
```
<aside>
<img src="/icons/suit-diamond_blue.svg" alt="/icons/suit-diamond_blue.svg" width="40px" /> **JSX**

- JavaScript XML의 약자로, JavaScript 코드 안에서 XML 또는 HTML과 유사한 문법을 사용하여 UI를 정의할 수 있게한다.
- React는 사용자 인터페이스를 만들기 위한 JavaScript 라이브러리이며, JSX는 React에서 UI를 빌드하는 데 사용되는 특별한 문법이다.
- JSX도 표현식이므로 자바스크립트 객체로 인식된다.
</aside>

## JSX 문법

1. 모든 태그가 닫혀야한다. 그리고 태그는 자식을 포함할 수 있다. 만약 태그사이에 별 내용이 들어가지 않는다면 self-closing을 이용한다. <div />
2. 컴포넌트는 하나의 DOM 트리구조로 이루어져야하기 때문에 컴포넌트에 여러 요소가 있다면 반드시 부모요소 하나로 감싸야한다. 
    
    ```jsx
    import React from 'react';
    
    function App(){
    	return(
    	<div>
    		<h1>hello</h1>
    		<h1>hi</h1>
    	</div>
    	);
    }
    
    import React, {Fragment} from 'react';
    
    function App(){
    	return(
    	<Fragment>
    		<h1>hello</h1>
    		<h1>hi</h1>
    	</Fragment>
    	);
    }
    
    export default App;
    ```
    
3. JSX 내에서 중괄호 **`{}`**를 사용하여 JavaScript 표현식을 넣을 수 있다.
    
    ```jsx
    import React from 'react';
    
    let str = "hello";
    
    function App(){
    	return(
    	<div>
    		<h1>{str}</h1>
    		<h1>hi</h1>
    	</div>
    	);
    }
    ```
    
4. 조건부 연산자 : JSX내부의 자바스크립트 표현식에서 if문을 사용할 수 없다. 그래서 {}안에 조건부 연산자를 사용해서 조건문을 사용한다. &&를 사용할때 falsy한 값인 0은 예외적으로 화면에 나타나는것을 주의해야한다.
    
    ```jsx
    import React from 'react';
    
    function ExampleComponent({ isLoggedIn }) {
      return (
    		/* 삼항 연산자를 이용해 조건문을 작성했다. */
        <div>
          {isLoggedIn ? (
            <p>Welcome, User!</p>
          ) : (
            <p>Please log in to continue.</p>
          )}
        </div>
      );
    }
    
    export default ExampleComponent;
    ```
    
    ```jsx
    import React from 'react';
    
    function ExampleComponent({ isLoggedIn, username }) {
      return (
    	/* AND 연산자(&&)를 사용한 조건부 렌더링  */
        <div>
          {isLoggedIn && (
            <p>Welcome, {username}!</p>
          )}
        </div>
      );
    }
    
    export default ExampleComponent;
    ```
    
5. React에서는 **`undefined`**를 렌더링할 때 해당 부분을 무시하고 처리한다. 그래서 JSX 내부에서 **`undefined`**를 렌더링하는 것은 오류를 발생시키지 않는다. 하지만 컴포넌트의 **`render`** 메서드나 함수형 컴포넌트에서 **`undefined`**를 직접 반환하는 상황은 오류를 발생시키므로 조심해야한다.
6. 인라인 스타일링 : DOM 요소에 스타일을 적용할 때는 객체 형태로 넣어줘야한다. 인라인 스타일링을 사용하기 싫으면 `import './App.css';` 를 이용하는 방법도 있다.
    
    ```jsx
    import React from 'react';
    
    function ExampleComponent() {
    	const inlineStyle = {
      color: 'red',
      fontSize: '16px',
      margin: '10px',
    	};
    	
      return (
        <div style={inlineStyle}>
          This is a component with inline styling.
        </div>
      );
    }
    
    export default ExampleComponent;
    ```
    
7. CSS 클래스를 지정할 때는 **`className`**을 사용해야한다. 
    
    ```jsx
    import React from 'react';
    import './MyComponent.css';  // 외부 CSS 파일을 import
    
    function MyComponent() {
      return (
        <div className="my-container">
          <p className="my-text">Hello, React!</p>
        </div>
      );
    }
    
    export default MyComponent;
    ```
    
8. 주석은 {/*주석을 작성하기*/}를 이용해 작성한다.

   ## Hooks

<aside>
<img src="/icons/daisy_blue.svg" alt="/icons/daisy_blue.svg" width="40px" /> **Hooks**

이전에는 클래스 컴포넌트에서만 가능했던  상태와 생명주기 기능을 함수 컴포넌트에서도 사용할 수 있게한다. 

</aside>

## useState

[use**State**](https://www.notion.so/useState-a12be481ee5e4d3fbdf7716fa185b329?pvs=21)

- 함수 컴포넌트에서 상태를 추가하고 관리할 수 있게한다.
- 함수가 호출되면 배열을 반환하고 배열의 첫번째 요소는 현재 상태 값이고, 두번째 요소는 상태를 업데이트할 함수이다.
- 함수에 인자로 넘겨주는 값은 상태의 기본값이다.

## useEffect

[useEffect(Lifecycle)](https://www.notion.so/useEffect-Lifecycle-79f3ed96b772448ca00fc97f099b8807?pvs=21)

- 부수 효과를 수행하는데 사용되며, 컴포넌트의 마운트, 언마운트, 업데이트 시에 특정 작업을 수행할 수 있다.
- 예를들어 데이터 가져오기, 구독설정, 수동으로 DOM조작등이 있다.
- 두번째 매개변수로 전달된 배열에 의해 효과가 실행되는 조건이 제어된다.

```jsx
import React, { useEffect } from 'react';

function ExampleComponent() {
  useEffect(() => {
    // 이곳에 효과(Effect) 코드 작성
    return () => {
      // 효과를 정리하는 코드 (cleanup)
    };
  }, [dependencies]);
}
```

## **useContext**

[useContext](https://www.notion.so/useContext-38594f641e5c43ea9b786ef27b533479?pvs=21) 

- 컨텍스트를 활용하여 전역 상태를 함수 컴포넌트에서 사용할 수 있게 합니다.
- 컨텍스트(Context) 값을 사용할 때 사용된다

```jsx
import React, { useContext } from 'react';

const MyContext = React.createContext();

function ExampleComponent() {
  const contextValue = useContext(MyContext);
  // contextValue를 사용하여 작업 수행
}
```

## **useReducer**

[useReducer](https://www.notion.so/useReducer-197b2479274a4187ba8c53a681982045?pvs=21) 

- 복잡한 상태 로직을 관리할 수 있도록 해주는 리듀서 패턴을 도입합니다.
- 복잡한 상태 논리를 처리할 때 사용되며, 상태와 액션을 처리하는 리듀서 함수를 사용한다.

```jsx
import React, { useReducer } from 'react';

function reducer(state, action) {
  switch (action.type) {
    case 'INCREMENT':
      return { count: state.count + 1 };
    case 'DECREMENT':
      return { count: state.count - 1 };
    default:
      return state;
  }
}

function ExampleComponent() {
  const [state, dispatch] = useReducer(reducer, { count: 0 });

  return (
    <div>
      <p>Count: {state.count}</p>
      <button onClick={() => dispatch({ type: 'INCREMENT' })}>Increment</button>
      <button onClick={() => dispatch({ type: 'DECREMENT' })}>Decrement</button>
    </div>
  );
}
```

## **useCallback**

[useCallback](https://www.notion.so/useCallback-47af04f2582f4801b32350187338aa3d?pvs=21) 

- 함수를 메모이제이션하여 성능 최적화를 위해 사용됩니다.
- 콜백 함수를 메모이제이션하여 성능을 최적화할 때 사용된다.
- 두 번째 매개변수로 전달된 배열에 의해 함수가 재생성되는 조건이 제어된다

```jsx
import React, { useCallback } from 'react';

function ExampleComponent({ onClick }) {
  const handleClick = useCallback(() => {
    // Click 이벤트 처리 로직
  }, [dependencies]);
  
  return <button onClick={handleClick}>Click me</button>;
}
```

## **useMemo**

[useMemo](https://www.notion.so/useMemo-8a06388d84174a7fa8d4ec2ff66bea73?pvs=21) 

- 계산 비용이 많이 드는 연산의 결과를 메모이제이션하여 성능을 최적화할 수 있다.
- 두 번째 매개변수로 전달된 배열에 의해 메모이제이션을 갱신하는 조건이 제어된다.

```jsx
import React, { useMemo } from 'react';

function ExampleComponent({ data }) {
  const processedData = useMemo(() => {
    // data를 가공하는 작업
    return processedResult;
  }, [data]);

  return <div>{processedData}</div>;
}
```

## useRef

[useRef](https://www.notion.so/useRef-eb7ac68425024bdf874f2a938710780e?pvs=21)

- DOM 요소에 접근하거나 특정 값을 기억하기 위해 사용된다.
- 클래스 컴포넌트에서의 **`this`**와 유사하게, 컴포넌트 간의 상태를 변경하지 않고도 값을 기억하고 관리할 수 있게 한다.
- **`useRef`**는 기본적으로 **`.current`** 프로퍼티를 갖는 객체를 반환하며, 이 프로퍼티는 **`current`** 값을 변경하여 원하는 값을 저장할 수 있다.

```jsx
import React, { useRef, useEffect } from 'react';

function ExampleComponent() {
  const myRef = useRef();

  useEffect(() => {
    // myRef를 통해 DOM 요소에 접근할 수 있음
    myRef.current.focus();
  }, []);

  return <input ref={myRef} />;
}
```

## **Custom** Hook

- 여러 리액트 Hook을 조합하여 새로운 로직을 추상화한 함수이다. 이를 통해 컴포넌트 간의 로직을 재사용하고, 코드를 모듈화할 수 있다.

```jsx
// useCustomHook.js
import { useState, useEffect } from 'react';

function useCustomHook(initialValue) {
  const [value, setValue] = useState(initialValue);

  useEffect(() => {
    // 특정 로직 수행
    console.log('Custom Hook executed');
  }, [value]);

  const updateValue = (newValue) => {
    setValue(newValue);
  };

  return { value, updateValue };
}

//ExampleComponent.js
import React from 'react';
import useCustomHook from './useCustomHook';

function ExampleComponent() {
  const { value, updateValue } = useCustomHook(0);

  return (
    <div>
      <p>Value: {value}</p>
      <button onClick={() => updateValue(value + 1)}>Increment</button>
    </div>
  );
}
```

