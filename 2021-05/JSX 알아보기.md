# JSX

## What is JSX?
> ๐ก JSX๋? ์๋ฐ์คํฌ๋ฆฝํธ ํ์ฅ ๋ฌธ๋ฒ์ผ๋ก XML๊ณผ ์ ์ฌํ๋ฉฐ ๋์ ๊ฐ๋์ฑ์ผ๋ก ๋ฆฌ์กํธ์์ ๋ง์ด ์ฌ์ฉ๋๋ค.

JSX๋ ๊ฐ์ฒด ์์ฑ๊ณผ ํจ์ ํธ์ถ์ ์ํ ๋ฌธ๋ฒ์  ํธ์๋ฅผ ์ ๊ณตํ๊ธฐ ์ํด์ ๋ง๋ค์ด์ง ํ์ฅ ๊ธฐ๋ฅ์ด๋ค.

### JSX์ ์ฅ์ 
- ๋์ ๊ฐ๋์ฑ
- ์์ฑํ๊ธฐ ํธ๋ฆฌํจ
- XML๊ณผ ์ ์ฌ

์์ ์ฅ์ ์ ํ ๋๋ก
- ์ค์ฒฉ๋ ๊ตฌ์กฐ๋ฅผ ์ ๋ํ๋ผ ์ ์๋ค.

๋ผ๋ ํฐ ์ฅ์ ์ด ์๋ค.

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

๋๊ฐ์ง ์๋ฅผ ๋ณด๋ฉด JSX ์ฝ๋์ ๋ฐ์ด๋ ๊ฐ๋์ฑ์ ํ ๋์ ์์๋ณผ ์ ์๋ค.

๋ํ JSX๋ ๋ฐ๋ฒจ์ด ์ฝ๋๋ฅผ ๋ณํํ๋ ๊ณผ์ ์์ ์๋ฌ ๋ถ๋ถ์ ๊ฐ์งํ๊ณ  ์๋ ค์ฃผ๊ธฐ ๋๋ฌธ์ ์๋ฌ ๊ด๋ฆฌํ๊ธฐ์๋ ๋ ํธ๋ฆฌํ๋ค.

---

## JSX์ ๋ํ์ ์ธ ๋ฌธ๋ฒ

### 1. ํ๋์ ๋ถ๋ชจ
JSX์์๋ ์ฌ๋ฌ๊ฐ์ ์์๋ฅผ ํํํ  ๊ฒฝ์ฐ ๋ฐ๋์ ํ๋์ ๋ถ๋ชจ๋ก ๊ฐ์ธ์ผํ๋ค.

```javascript

export default function App() {
    return(
        <>
            Hello World!
        </>
    )
}

```

### 2. ์๋ฐ์คํฌ๋ฆฝํธ ๋ณ์
JSX๋ ๋ด๋ถ์์ ์๋ฐ์คํฌ๋ฆฝํธ์ ๋ณ์๋ฅผ ์ ๋ฌํ์ฌ ์ด์ฉํ๋ค.

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

### 2. ์กฐ๊ฑด๋ฌธ
JSX๋ ์๋ฐ์คํฌ๋ฆฝํธ์ ์กฐ๊ฑด๋ฌธ์ ์ด์ฉํ์ฌ ์ํฉ์ ๋ฐ๋ผ ๋ค๋ฅธ ์์๋ฅผ ์ถ๋ ฅํ  ์ ์์ต๋๋ค.

> ๐ก ๋ณต์กํ ์กฐ๊ฑด๋ฌธ์ ๊ฒฝ์ฐ JSX๋ฐ์์ ์กฐ๊ฑด์ ๋ฐ๋ฅธ ๊ฐ์ ์ค์ ํ๊ณ  JSX๋ด์ ์กฐ๊ฑด๋ฌธ์์๋ ์ต๋ํ ๊ฐ๋จํ๊ฒ ์์ฑํ๋ ๊ฒ์ด ์ข๋ค.

#### ์๋ฐ์คํฌ๋ฆฝํธ์ ์กฐ๊ฑด๋ฌธ
ํผ์ก ๊ทธ์์ฒด

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

#### JSX์ IF ์กฐ๊ฑด๋ฌธ
JSX๋ ๋ด๋ถ์์ if ์กฐ๊ฑด๋ฌธ ์ธ์๋ ์ผํญ ์ฐ์ฐ์๋ฅผ ์ฌ์ฉํ  ์ ์๋ค.
JavaScript ๋ณด๋ค ๊ฐ๋์ฑ์ด ์ข๊ณ  ์ฆ์ ์คํํจ์ ํํ๋ฅผ ๋๋ค.

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

### 3. ๋ผ๋ฆฌ ์ฐ์ฐ์

#### AND ์ฐ์ฐ์์ OR ์ฐ์ฐ์

JSX์์๋ AND, OR ์ฐ์ฐ์๋ฅผ ํ์ฉํด์ ํน์  ์กฐ๊ฑด์ ๋ฐ๋ผ ์ปดํฌ๋ํธ์ ๋ ๋๋ง ์ฌ๋ถ๋ฅผ ๊ฒฐ์ ํ๋ ์ฝ๋๋ฅผ ๊ตฌ์ฑ ํ  ์ ์์ต๋๋ค.

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

- **AND ์ฐ์ฐ์**

`JSX`์์๋ `false`๋ ๋ ๋๋ง๋์ง ์๊ธฐ ๋๋ฌธ์ `AND` ์ฐ์ฐ์์ ์์ ์กฐ๊ฑด์ด `true`์ผ ๊ฒฝ์ฐ๋ ๋ํ๋๊ณ , ๊ฑฐ์ง์ธ ๊ฒฝ์ฐ๋ ๋ํ๋์ง ์์ต๋๋ค.

-**OR ์ฐ์ฐ์**

`OR`์ ๊ฒฝ์ฐ๋ ๋ฐ๋๋ก ์์ ์กฐ๊ฑด์ด `false`์ธ ๊ฒฝ์ฐ ๋ด์ฉ์ด ๋ํ๋๊ณ , ์กฐ๊ฑด์ด `true`์ธ ๊ฒฝ์ฐ์๋ ๋ํ๋์ง ์์ต๋๋ค.

```javascript
function sayHello(name) {
  return name || "Noname";
}

sayHello("Ji Yeon") // "Ji Yeon"
sayHello()         // "Noname"
```

### 4. null & undefined
์กฐ๊ฑด์ ๋ฐ๋ผ ์ถ๋ ฅ๋๋ ๊ฐ์ ๋ณ๊ฒฝํ๋ค ๋ณด๋ฉด ์ปดํฌ๋ํธ๊ฐ null ์ด๋ undefined๋ฅผ ๋ฐํํ๋ ๊ฒฝ์ฐ๊ฐ ์๋ค.
JSX์ ๊ฒฝ์ฐ null์ ํ์ฉํ์ง๋ง undefined๋ ์ค๋ฅ๊ฐ ๋ฐ์ํ๊ธฐ ๋๋ฌธ์ ์ฃผ์ํด์ผํ๋ค.

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

### 5. ์ฃผ์
JSX์์์ ์ฃผ์์ ์๋ฐ์คํฌ๋ฆฝํธ์์์ ์ฃผ์๊ณผ ์ฐจ์ด๊ฐ ์๋ค.

- JSX ์ฃผ์ : `{/* ์ฃผ์ */}`

๋จ, ํ๊ทธ ์์์ ์ฃผ์์ ์ฌ์ฉํ  ๊ฒฝ์ฐ ์๋ฐ์คํฌ๋ฆฝํธ์ฒ๋ผ `//์ฃผ์` ๋๋ `/* ์ฃผ์ */`์ ์ฌ์ฉํ  ์ ์๋ค.

### 6. ์คํ์ผ๋ง
JSX๋ HTML๊ณผ ๋ฌ๋ฆฌ style์ ๋ฌธ์์ด๋ก ์๋ ฅํ๋ ๊ฒ์ด ์๋๋ผ ๊ฐ์ฒด ํํ๋ก ์๋ ฅํด์ผํฉ๋๋ค.
๋ํ `font-size`์ฒ๋ผ `-` ํ์ดํ์ผ๋ก ์ฐ๊ฒฐ๋ ์ด๋ฆ์ ํ์ดํ์ ์ ๊ฑฐํ๊ณ  ์นด๋ฉ ํ๊ธฐ๋ฒ์ธ `fontSize`๋ก ์์ฑํด์ผํฉ๋๋ค.

```javascript
<h2 style={{fontSize='24px', fontWeight='bold'}}>
    JSX Style
</h2>
```
