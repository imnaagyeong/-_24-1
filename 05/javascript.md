## 💡DOM

---

<aside>
💭 DOM

- 브라우저가 html코드를 분석해서 DOM트리로 만들어서 UI를 보여준다.
- DOM은 메모리에 웹 페이지 문서 구조를 트리구조로 표현해서 웹 브라우저가 HTML 페이지를 인식하게 해준다. 또한 위에서 보는 웹페이지를 이루는 요소들을 자바스크립트가 이용할 수 있게끔 브라우저가 트리구조로 만든 객체 모델을 의미한다.
- JavaScript 코드에서 DOM을 수정하는 것은 웹 브라우저의 DOM API를 사용하여 해당 문서의 노드를 변경하는 것이다. 이것은 자바스크립트 코드가 브라우저의 일부인 window 객체 안에 있기 때문에 가능하다.
- 웹페이지 빌드 과정(CRP)를 통해 DOM을 조작해서 화면을 변경시켜줄때 브라우저 내부에서는 어떠한 과정을 통해서 바뀐 화면을 변경시켜주는지 알수있다.
    
</aside>

## 💡Document Object

---

window 객체가 브라우저 창이라고 하면 document 객체는 브라우저 내에서 콘텐츠를 보여주는 웹페이지 자체라고 할 수 있다.

```jsx
let val;

val = document;
val = document.baseURI // 웹 페이지의 절대 URI를 반환
val = document.head; // <head> 태그 반환
val = document.body; // <body> 태그 반환
val = document.doctype; // 웹 페이지의 문서 형식을 반환
val = document.cookie // 웹 페이지의 쿠키를 반환

val = document.forms; // <form> 태그 반환
val = document.forms[0];
val = document.forms[0].id;
val = document.forms[0].action;
val = document.forms[0].method;

val = document.links; // href 속성이 있는 <a> 태그 반환
val = document.links[0];
val = document.links[0].id;
val = document.links[0].classList[0];
val = document.links[0].className;

val = document.images; // <img> 태그 반환

val = document.scripts; // <script> 태그 반환
val = document.scripts[0].getAttribute('src'); // 속성중 src를 가져옴

console.log(val);
```

### ☁️ Document 매서드들을 사용해 웹피이지 내의 태그들에 접근하기

1. 하나의 요소에 접근하는 경우
    
    ```jsx
    // 파라미터로 전달한 ID를 가진 태그를 반환
    document.getElementById(요소아이디)
    
    // 파라미터로 전달한 name 속성을 가진 태그를 반환
    document.getElementByName(name속성값)
    
    // 파라미터로 전달한 선택자에 맞는 첫 번째 태그를 반환
    /*id 라면 '.아이디이름' class라면 '#클래스이름'을 파라미터로 전달*/
    document.querySelector(선택자)
    ```
    
    ```jsx
    //document.getElementById()
    console.log(document.getElementById('header-container'));
    console.log(document.getElementById('header-heading').className);
    const headerContainer = document.getElementById('header-container');
    
    // styling 변경
    headerContainer.style.fontSize = '10px';
    headerContainer.style.display = 'none';
    
    // content 변경
    headerContainer.textContent = 'Text Content';
    headerContainer.innerText = 'Inner Text';
    headerContainer.innerHTML = '<span style="color:blue">Inner HTML</span>';
    
    // document.querySelector()
    console.log(document.querySelector('#form-first-div'));
    console.log(document.querySelector('.form-container'));
    console.log(document.querySelector('h5'));
    
    document.querySelector('li').style.color = 'blue';
    document.querySelector('ul li').style.color = 'red';
    
    document.querySelector('li:last-child').style.color = 'red';
    document.querySelector('li:nth-child(3)').style.color = 'orange';
    document.querySelector('li:nth-child(4)').textContent = 'Hello World';
    document.querySelector('li:nth-child(odd)').style.background = 'gray';
    document.querySelector('li:nth-child(even)').style.background = 'lightgray';
    ```
    
2. 여러 요소에 접근
    
    ```jsx
    // 파라미터로 전달한 태그이름을 가진 모든 태그들을 반환(배열)
    document.getElementsByTagName(태그이름)
    
    // 파라미터로 전달한 클래스 이름을 가진 모든 태그들을 반환(배열)
    document.getElementsByClassName(클래스이름)
    
    // 파라미터로 전달한 선택자에 맞는 모든 태그들을 반환(배열)
    document.querySelectorAll(선택자)
    ```
    
    ```jsx
    // document.getElementsByClassName
    const items = document.getElementsByClassName('list-group-item');
    console.log(items);
    console.log(items[0]);
    items[0].style.color = 'blue';
    items[3].textContent = 'Hi';
    
    // document.getElementsByTagName
    let list = document.getElementsByTagName('li');
    console.log(list);
    console.log(list[0]);
    list[0].style.color = 'red';
    list[3].textContent = 'Hello';
    
    // HTML 모음을 배열로 만들기
    list = Array.from(list);
    
    list.reverse();
    
    list.forEach(function(li, index){
         console.log(li.className);
         li.textContent = `${index}. List`;
     });
    
    console.log(list);
    
    // document.querySelectorAll
    const items = document.querySelectorAll('ul.list-group li.list-group-item');
    
    items.forEach(function (item, index) {
         item.textContent = `${index}. List`;
    });
    
    const liOdd = document.querySelectorAll('li:nth-child(odd)');
    const liEven = document.querySelectorAll('li:nth-child(even)');
    
    liOdd.forEach(function (li, index) {
        li.style.background = 'gray';
    });
    
    for (let i = 0; i < liEven.length; i++) {
        liEven[i].style.background = 'lightgray';
    }
    
    console.log(items);
    ```
    

### ☁️ innerHTML vs innerText vs textContent

1. innerHTML : html 까지 같이 보여준다.
2. innerText : 사용자에게 보여지는 텍스트 값을 읽어오며 여러 공백은 무시하고 하나의 공백만 처리한다.
3. textContent : display:none 스타일이 적용된 숨겨진 텍스트도 가져오는 노드가 가지고 있는 텍스트 값 그대로 보여준다.

### ☁️ DOM navigation(DOM 탐색하기)

- DOM을 이용하면 요소와 요소의 콘텐츠에 무엇이든 할 수 있다. 하지만 무언가를 하기전에 당연히 조작하고자 하는 DOM 객체에 접근하는 것이 선행되어야한다.
- DOM에 수행하는 모든 연산은 document 객체에서 시작한다. document 객체는 DOM에 접근하기 위한 진입점이다. 진입점을 통과하면 어떤 노드에도 접근할 수 있다.
