# JSX

## What is JSX?
    💡 JSX란? 자바스크립트 확장 문법으로 XML과 유사하며 높은 가독성으로 리액트에서 많이 사용된다.

JSX는 객체 생성과 함수 호출을 위한 문법적 편의를 제공하기 위해서 만들어진 확장 기능이다.

### JSX의 장점
- 높은 가독성
- 작성하기 편리함
- XML과 유사

위의 장점을 토대로
- 중첩된 구조를 잘 나타낼 수 있다.

라는 큰 장점이 있다.

## JavaScript vs JSX

- **JavaScript**

```javascript

'use strict';

function formatName(user) {
    return user.firstName + ' ' + user.lastName;
};

const user = {
    firstName: 'Ji Yeon',
    lastName: 'Park'
};

const element = /*#___PURE___*/ React.createElement(
    'h1',
    null,
    'Hello, ',
    formatName(user),
    '!'
)

```

- **JSX**

```jsx

function formatName(user) {
    return user.firstName + ' ' + user.lastName;
};

const user = {
    firstName: 'Ji Yeon',
    lastName: 'Park'
};

const element = <h1>Hello, {formatName(user)}!</h1>

```

두가지 예를 보면 JSX 코드의 뛰어난 가독성을 한 눈에 알아볼 수 있다.

또한 JSX는 바벨이 코드를 변환하는 과정에서 에러 부분을 감지하고 알려주기 때문에 에러 관리하기에도 더 편리하다.

---

## JSX의 대표적인 문법

### 1. 하나의 부모
JSX에서는 여러개의 요소를 표현할 경우 반드시 하나의 부모로 감싸야한다.

```javascript

export default function App() {
    return(
        <>
            Hello World!
        </>
    )
}

```

### 2. 자바스크립트 변수
JSX는 내부에서 자바스크립트의 변수를 전달하여 이용한다.

```javascript

export default function App() {

    const name = 'JiYeon';

    return(
        <>
            Hello {name}!
        </>
    )
}

```

### 2. 조건문
JSX는 자바스크립트의 조건문을 이용하여 상황에 따라 다른 요소를 출력할 수 있습니다.

    💡 복잡한 조건문의 경우 JSX밖에서 조건에 따른 값을 설정하고 JSX내의 조건문에서는 최대한 간단하게 작성하는 것이 좋다.

#### 자바스크립트의 조건문
혼잡 그자체

```javascript

## JavaScript

export default function App() {

    const name = 'JiYeon';

    return(
        <>
            Hello {name}!
            {(() => {
                if(name === 'GPARKKII') return 'My Name is GPARKKII';
                else if (name === 'JiYeon') return 'My Name is JiYeon';
                else return 'My Name is React Native';
            })()}
        </>
    )
}

```

#### JSX의 IF 조건문
JSX는 내부에서 if 조건문 외에도 삼항 연산자를 사용할 수 있다.
JavaScript 보다 가독성이 좋고 즉시 실행함수 형태를 띈다.

```jsx

## JSX

export default function App() {

    const name = 'JiYeon';

    return(
        <>
            Hello {name}!
            {name === 'GPARKKII' ? 'My name is Gparkkii' : 'My name is React Native'}
        </>
    )
}

```

### 3. 논리 연산자

#### AND 연산자와 OR 연산자

JSX에서는 AND, OR 연산자를 활용해서 특정 조건에 따라 컴포넌트의 렌더링 여부를 결정하는 코드를 구성 할 수 있습니다.

```javascript
export default function App() {

    const name = 'JiYeon';
    const age = 20;

    return(
        <>
            Hello {name}!
            {name === 'GPARKKII' && (
                <strong> I am GPARKKII</strong>
            ))}
            {age < 30 && (
                <strong> I am young~ </strong>
            )}
        </>
    )
}
```

- **AND 연산자**

`JSX`에서는 `false`는 렌더링되지 않기 때문에 `AND` 연산자의 앞의 조건이 `true`일 경우는 나타나고, 거짓인 경우는 나타나지 않습니다.

-**OR 연산자**

`OR`의 경우는 반대로 앞의 조건이 `false`인 경우 내용이 나타나고, 조건이 `true`인 경우에는 나타나지 않습니다.

```javascript
function sayHello(name) {
  return name || "Noname";
}

sayHello("Ji Yeon") // "Ji Yeon"
sayHello()         // "Noname"
```

### 4. null & undefined
조건에 따라 출력되는 값을 변경하다 보면 컴포넌트가 null 이나 undefined를 반환하는 경우가 있다.
JSX의 경우 null은 허용하지만 undefined는 오류가 발생하기 때문에 주의해야한다.

```javascript
/* No Error */
export default function App() {
    return null;
}

/* Error */
export default function App() {
    return undefined;
}
```

### 5. 주석
JSX에서의 주석은 자바스크립트에서의 주석과 차이가 있다.

- JSX 주석 : `{/* 주석 */}`

단, 태그 안에서 주석을 사용할 경우 자바스크립트처럼 `//주석` 또는 `/* 주석 */`을 사용할 수 있다.

### 6. 스타일링
JSX는 HTML과 달리 style에 문자열로 입력하는 것이 아니라 객체 형태로 입력해야합니다.
또한 `font-size`처럼 `-` 하이픈으로 연결된 이름은 하이픈을 제거하고 카멜 표기법인 `fontSize`로 작성해야합니다.

```javascript
<h2 style={{fontSize='24px', fontWeight='bold'}}>
    JSX Style
</h2>
```
