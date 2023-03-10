---
title: 'React Developer Roadmap 2023'
emoji: 'ð¦'
type: 'tech' # tech: æè¡è¨äº / idea: ã¢ã¤ãã¢
topics: ['react']
published: false
---

## ã¯ããã«

https://roadmap.sh/react

React Developer Roadmap ã® 2023 å¹´çãå¬éããã¦ããã®ã§ä¸éã (æµãã) è¦ã¦ææ³ãªã©ãã ãã ãæ¸ãã¾ããåé ç®ã«ã¤ãã¦ã®è©³ããåå®¹ã¯å¬å¼ãµã¤ãããåç§ãã ããã

ã­ã¼ããããã®é çªã¯ãã¡ãã§ãã

- Visit JavaScript Roadmap
- CLI Tools
- Components
- Rendering
- Hooks
- Routers
- State Management
- Styling
- API Calls
- Testing
- Frameworks
- Forms
- Mobile
- Frontend Roadmap

## Visit JavaScript Roadmap

https://roadmap.sh/javascript

React ã®ã­ã¼ããããã¯ JavaScript ã®åå¼·ãæåã«ãã¾ããJavaScript ã®ã©ã¤ãã©ãªãªã®ã§å½ç¶ã§ãã­ããµãããå°éã«é å¼µãã¾ããããæè¿ãéåæå¦çã¨ã¤ãã³ãã«ã¼ãå¨ãã®ç¥è­ãè¶³ããªããã¨ãçæããããããã®ã§åå¼·ãç´ãã¦ãã¾ããè©°ã¾ãæã£ã¦ React ã¨ãããã JavaScript ãçè§£ã§ãã¦ããªããã¨ãå¤ããã§ããã­...ã

## CLI Tools

ç¾å¨ React ãä½¿ç¨ããã¢ããªã±ã¼ã·ã§ã³ãä½æããæ¹æ³ã¯ç¡æ°ã«ããããè¿·ãç¹ã®ä¸ã¤ã§ããReact ã®ã³ã¢ã³ã³ããªãã¥ã¼ã¿ã¼ã§ãããæè¿ Vercel ã¸å¥ããã [Andrew Clark ãã](https://twitter.com/acdlite)ããã®ãããªãã¤ã¼ããããã¦ãã¾ãããç¢ºãã« Next.js ãªã©ãä½¿ç¨ããæ©ä¼ãå¤ããªããç´ ã® React ã§ã¢ããªã±ã¼ã·ã§ã³ãä½æããæ©ä¼ãæ¸ã£ã¦ãã¦ããã®ããããã¾ããã

https://twitter.com/acdlite/status/1617611126514266112

### Create React App

https://create-react-app.dev/

ãã¡ãã«é¢ãã¦èª¬æã¯ä¸è¦ã§ããã...ãReact ãæãæ¯ãã¦ãããã¼ã«ãªã®ã§ã¯ãªãã§ããããã

ããããå¨ãã­ã³ãã¨ã³ãã¨ã³ã¸ãã¢ãä¸åº¦ã¯å®è¡ããã§ãããã³ãã³ãã

```bash
npx create-react-app my-app
cd my-app
npm run start
```

Create React App ã«ã¤ãã¦æè¿è©±é¡ã«ãªã£ã¦ãã PR ãããã¾ããT3 Stack ã®æå±èã§ãã [Theo ãã](https://twitter.com/t3dotgg)ãä½æãã¾ããã

https://github.com/reactjs/reactjs.org/pull/5487

React ã¯ç¾å¨[æ°ããå¬å¼ãµã¤ã](https://beta.reactjs.org/)ãä½ã£ã¦ããã®ã§ãããããã«ãã®ãããªè¨è¿°ãããã¾ãã

> React ãå­¦ã¶ãªããCreate React App ããå§ããã¾ããããã¯ãReact ãè©¦ããæ°ããã·ã³ã°ã«ãã¼ã¸ãã¯ã©ã¤ã¢ã³ããµã¤ãã¢ããªã±ã¼ã·ã§ã³ãæ§ç¯ããæãä¸è¬çãªæ¹æ³ã§ããReact ã®ããã«ä½ããã¦ãã¾ãããã«ã¼ãã£ã³ã°ããã¼ã¿ãã§ããã«ã¤ãã¦ã¯æè¦ãåããã¦ãã¾ããã

ããã§ Create React App ã§ã¯ãªããVite ãå§ããããæç« ãä¿®æ­£ãã PR ã§ããããªãè­°è«ãçãä¸ãã£ã¦ãã¦ãReact ã®ã³ã¢ã³ã³ããªãã¥ã¼ã¿ã¼ã§ãã [Dan ãã](https://twitter.com/dan_abramov)ã[ã³ã¡ã³ã](https://github.com/reactjs/reactjs.org/pull/5487#issuecomment-1409720741)ããã¦ãã¾ãããªã Create React App ããã¤ããéãã¦ããããããããããä¸èª­ããããã¨ããå§ããã¾ãã

### Vite

https://vitejs.dev/

Vue.js ã®éçºèã§ãã [Evan You ãã](https://github.com/yyx990803)ãéçºãã¦ãã¾ãã

```bash
npm create vite@latest my-app -- --template react
cd my-app
npm install
npm run dev
```

Create React App ã®ä»£ããã«ä½¿ç¨ããã¦ããæ©ä¼ãå¢ããã§ãããã

## Components

### Class Components vs Functional Components

ç¾å¨ã® React ã®ä¸çã¯ Hooks ã«ããæãç«ã£ã¦ããã®ã§ ? åºæ¬çã«ã¯ Functional Components ãä½¿ç¨ãã¾ããããç­èã¯ Functional Components ãã¤ãã£ãä¸ä»£ãªã®ã§ãClass Components ã¯ `componentDidMount` ã `componentWillUnmount` ãªã©ãReact ã®ã©ã¤ããµã¤ã¯ã«ãåå¼·ããéã«å°ãè§¦ããç¨åº¦ã§ãããå®åã§æ¸ããçµé¨ã¯ããã¾ããã

Class Components ã®ä¾

```jsx
import React, { Component } from 'react';

class ClassComponent extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      count: 0,
    };
  }

  render() {
    return (
      <div>
        <p>Count: {this.state.count}</p>
        <button onClick={() => this.setState({ count: this.state.count + 1 })}>
          Click me
        </button>
      </div>
    );
  }
}

export default ClassComponent;
```

Functional Components ã®ä¾

```jsx
import React, { useState } from 'react';

function FunctionalComponent() {
  const [count, setCount] = useState(0);

  return (
    <div>
      <p>Count: {count}</p>
      <button onClick={() => setCount(count + 1)}>Click me</button>
    </div>
  );
}

export default FunctionalComponent;
```

### JSX

2 å¹´å React ãåå¼·ããã¦ã®é ãJSX ã¨ Google ã§æ¤ç´¢ããã¨ ãJSX æ°æã¡æªãããªã©ã¨ãµã¸ã§ã¹ãããã¦ããã®ãæãããã§ãã ã¾ã JSX ãæ¹å¤ãããããªè¨äºãããªãè¦ããã¾ãããåäººçã«ã¯ VSCode ã TypeScript ãªã©ã®ããããããéçºèä½é¨ã¯æé«ã§ããDjango ã PHP ãªã©ã®ãã³ãã¬ã¼ãã¨ã³ã¸ã³ã«ã¯æ­£ç´æ»ããããªã...ããã¶ã¤ãã¼ã¨ã®åæ¥­åé¡ãªã©ãããã¾ããããJSX ãå½ããåã«ãªãããã¦ãã®åé¡ãã»ã¨ãã©è§£æ¶ãããã®ã§ã¯ãªãã§ããããï¼ Vue ãªã©ã¨éã£ã¦ React ã¯ç¬èªã®ææ³ãããããã§ã¯ãªããç´ ã® JavaScript ã§æ¸ããç¹ãå¥½ããªãã¤ã³ãã§ãã

### Props vs State

ä½ãã©ã®ã³ã³ãã¼ãã³ãã§ç®¡çãã¹ããªã®ãããã­ã¸ã§ã¯ãã®ã«ã¼ã«ãã¢ã¼ã­ãã¯ãã£ã«ãã£ã¦é©åã«å¤æ­ããå¿è¦ãããã¾ããç¡é§ãª State ãä½æããªããã¨ããProps ã¨ãã¦æä½éå¿è¦ãªç©ãæ¸¡ãããã«ãããã¨ã§ãåã¬ã³ããªã³ã°ãæå¶ãããã¨ã«ã¤ãªãããã¢ããªã±ã¼ã·ã§ã³ã®ããã©ã¼ãã³ã¹åä¸ã«ç´çµãã¾ããPresntational/Container Components vs Colocation/Lifting State Up ã®è©±ã¯ã¨ã¦ãåå¼·ã«ãªãã¾ããã

https://medium.com/@dan_abramov/smart-and-dumb-components-7ca2f9a7c7d0

https://kentcdodds.com/blog/state-colocation-will-make-your-react-app-faster

### Conditional Rendering

https://reactjs.org/docs/conditional-rendering.html

æ¥æ¬èªã«ããã¨ãæ¡ä»¶ä»ãã¬ã³ããªã³ã°ãã§ããã­ã°ã¤ã³ãã¦ããããã¦ããªããã§è¡¨ç¤ºãåãæ¿ãããæãªã©ã«ä½¿ç¨ãã¾ããä¸é æ¼ç®å­ã && æ¼ç®å­ãä½¿ç¨ãããã¨ãã»ã¨ãã©ã§ãã

### Composition

https://reactjs.org/docs/composition-vs-inheritance.html

ã³ã³ãã¼ãã³ãã Props ã¨ãã¦ä»ã®ã³ã³ãã¼ãã³ãã«æ¸¡ããã¨ã§ããReact.children ãä¸»ãªä¾ã§ãã

## Rendering

### Component Life Cycle

ã³ã³ãã¼ãã³ãåã®ã©ã®ã³ã¼ããã©ã®ã¿ã¤ãã³ã°ã§å®è¡ããããã®çµæããã¤åæ ãããã®ããçè§£ããå¿è¦ãããã¾ãã`useState` ã¨ `useEffect` ãä½¿ç¨ããæ§ããªç®æã« `console.log` ãããå®éã«ç¢ºããã¦ã¿ãã¨ãã¨ã¦ãåå¼·ã«ãªããããå§ãã§ãã

### Lists and Keys

ã­ã¼ã¯ãReact ãã©ã®é ç®ãå¤æ´ã»è¿½å ã»åé¤ãããããè­å¥ããã®ã«ä½¿ããã¾ãããã¼ã¿ã® ID ãªã©ãã­ã¼ã¨ãã¦ä½¿ç¨ãããã¨ãå¤ãã§ãã

```jsx
const numbers = [1, 2, 3, 4, 5];
const listItems = numbers.map((number) => (
  <li key={number.toString()}>{number}</li>
));
```

ã¤ã³ããã¯ã¹ãã­ã¼ã¨ãã¦è¨­å®ããã®ã¯ã¢ã³ããã¿ã¼ã³ã«ãªã£ã¦ãã¾ãã

```jsx
todos.map((todo, index) => <Todo {...todo} key={index} />);
```

çç±ã¯ãã¡ã

https://robinpokorny.com/blog/index-as-a-key-is-an-anti-pattern/

### Render Props

props ã éãã¦ JSX è¦ç´ ãã³ã³ãã¼ãã³ãã«æ¸¡ããã¨ã§ãã

https://www.patterns.dev/posts/render-props-pattern/

### Refs

ããæ¯è¼ããã State / ç¶æ (useState) ã¨ Ref / åç§ (useRef) ã§ãããéãã¯å¤§ããäºã¤ããã¾ãã

- åç§ãæ´æ°ãã¦ãåã¬ã³ããªã³ã°ã¯çºçããªãããç¶æãæ´æ°ããã¨ã³ã³ãã¼ãã³ãã¯åã¬ã³ããªã³ã°ããã
- åç§ã®æ´æ°ã¯åæ (æ´æ°ãããåç§å¤ãããã«å©ç¨ã§ãã)ãç¶æã®æ´æ°ã¯éåæ (åæç»å¾ã«ç¶æå¤æ°ãæ´æ°ããã)

ã¾ã useRef ã¯ DOM è¦ç´ ã«ã¢ã¯ã»ã¹ãããã¨ãã§ãããããã¤ã³ããããã£ã¼ã«ãã«ãã¡ã¼ã«ã¹ãå½ã¦ãããããã¨ãã§ãã¾ãã

```jsx
import { useRef, useEffect } from 'react';

function InputFocus() {
  const inputRef = useRef();
  useEffect(() => {
    inputRef.current.focus();
  }, []);

  return <input ref={inputRef} type='text' />;
}
```

ãã ãDom ãæä½ãããã¨ã¯ãReact ãç®¡çãã¦ããä»®æ³ DOM ã¨ å® DOM ã®éã§ä¸æ´åãçºçããå¯è½æ§ãããããæ³¨æãã¦ä½¿ç¨ãããã¨ãå¿è¦ã§ãã

### Events

https://beta.reactjs.org/learn/responding-to-events

ã¿ãªãããæ®æ®µããããæ¸ãã¦ããã ããããã§ãã

```jsx
export default function Button() {
  function handleClick() {
    alert('You clicked me!');
  }

  return <button onClick={handleClick}>Click me</button>;
}
```

ã¤ãã³ããã³ãã©ã®ååã¯ãæ£ç¿ä¸ handle ã®å¾ã«ã¤ãã³ãåãä»ããã®ãä¸è¬çã§ãã`onClick={handleClick}`ã `onMouseEnter={handleMouseEnter}` ãªã©ã®ããã«ãªãã¾ããæåã¯ `<button onClick={handleClick}>` ã¨ã`<button onClick={handleClick()}>` ã®éããåãããªãã£ãã®ãæãããã§ã...ãé¢æ°ã¯å¼ã³åºãã®ã§ã¯ãªããæ¸¡ããã¨ã«æ³¨æãã¾ããããå¾èã¯ã¬ã³ããªã³ã°ä¸­ã«å®è¡ããã¦ãã¾ãã¾ãã

### High Order Components

High Order Components (HOC) ã¯ãããã£ãååã®æ©è½ãããããã§ã¯ãªããReact ã§ç¨ããããèãæ¹ã»ãã¿ã¼ã³ã®ä¸ã¤ã§ããå·ä½çã«ã¯ãHOC ã¯ã³ã³ãã¼ãã³ããåãåããæ°ããã³ã³ãã¼ãã³ããè¿ãé¢æ°ã§ãã

```jsx
const withError = (Component) => (props) => {
  if (props.error) {
    return <div>Something went wrong ...</div>;
  }

  return <Component {...props} />;
};

export default withError;
```

> React Hooks ãåé¨ããå®è£ã®è©³ç´°ï¼ä¾ï¼ã¹ãã¼ããå¯ä½ç¨ï¼ã§é¢æ°ã³ã³ãã¼ãã³ãã«å³ä»ãããããã®ç¾ç¶ã§ããã®ã«å¯¾ããReact Higher-Order Components ã¯å¤é¨ããé¢æ°ï¼ããã³ã¯ã©ã¹ã³ã³ãã¼ãã³ãï¼ã«å³ä»ãããããã®ã§ãããHOC ã¯ãå®éã®ã³ã³ãã¼ãã³ãããã®å®è£ã®è©³ç´°ï¼React Hooks ãªã©ï¼ãåé¨ã§å®è¡ããåã«ã³ã³ãã¼ãã³ããä¿è­·ããããã®å®ç§ãªç¾ã¨ãªãã

ä¸è¨è¨äºããå¼ç¨

https://www.robinwieruch.de/react-higher-order-components/

## Hooks

### useState

set é¢æ°ã§å¤ãæ´æ°ãããã®ã¯é¢æ°ãå¼ã³åºãããå¾ãã¨ãããã¨ãç¥ããªãã¦è©°ã¾ã£ããã¨ãããã¾ããã

```jsx
const Component = () => {
  const [count, setCount] = useState(0);

  const handleClick = () => {
    setCount((prevCount) => prevCount + 1);
    console.log(count); // ãã®æç¹ã§ã¯ã¾ã  0
  };
};
```

### useEffect

ç¬¬äºå¼æ°ã¨ã¯ãªã¼ã³ã¢ããã®ä½¿ãæ¹ã«ã¤ãã¦æåã¯æã«èºãã¾ãããå¦çãå®è¡ãããã¿ã¤ãã³ã°ãçè§£ããå¿è¦ãããã¾ããClass Components ã® `componentDidMount` ã `componentWillUnmount` ãªã©ã®ã©ã¤ããµã¤ã¯ã«ã¡ã½ããã useEffect ã§ã©ã®ããã«è¡¨ç¾ã§ããã®ããçè§£ãã¦ããã¨ããããããã¾ããã[ãã²ããã](https://twitter.com/uhyo_)ã®ãã¡ãã®è¨äºã«ã¯å¤§å¤ãä¸è©±ã«ãªãã¾ããã

https://zenn.dev/uhyo/articles/react17-useeffect

### Writing Custom Hooks

use~ ã¨å½åãããé¢æ°ãä½æãã¾ããè¤æ°ã®ã³ã³ãã¼ãã³ãã«å­å¨ããå±éå¦çãåãåºãã¦ä½æããé¢æ°ã§ããã©ã¤ãã©ãªã®é¢æ°ãç´æ¥å¼ã³åºãããä¸å±¤ã©ãããã¦å¶ç´ãå ããå ´åã«ãªã©ã«ãä½¿ç¨ããã¾ãã

### useCallback

props ã¸æ¸¡ãé¢æ°ãã­ã£ãã·ã¥ãã¾ããæ­£ç´ãã¾ãç©æ¥µçã«ä½¿ãã¦ããªãã®ã§æè­ãã¦ãããã...ã

### useRef

### useMemo

props ã¸æ¸¡ããªãã¸ã§ã¯ããã­ã£ãã·ã¥ãã¾ãã

### useReducer

### useContext

ã°ã­ã¼ãã«ã¹ãã¼ããä½æã§ãã¾ããç­èãä½¿ãæ©ä¼ãå¤ãã§ãããã¹ãã¼ããå¢ããã«ã¤ã Context éã®ä¾å­é¢ä¿ãè¤éã«ãªããã³ã¼ããªã¼ãã£ã³ã°ãå¤§å¤ã«ãªãå°è±¡ã§ããã¾ããä½åãªéã¬ã³ããªã³ã°ãçºçãããªãããã«æ°ãä½¿ãå¿è¦ãããã¾ãã

## Routers

Next.js ãªã©æè¿ã®ãã¬ã¼ã ã¯ã¼ã¯ã¯ã«ã¼ãã£ã³ã°ãèªåã§è¡ãªã£ã¦ãããããèªåã§æ¸ããçµé¨ãã»ã¨ãã©ããã¾ãããä»å¾ä½¿ããã¦ããã ãããã¬ã¼ã ã¯ã¼ã¯ããããããã¡ã¤ã«ãã¼ã¹ã«ã¼ãã£ã³ã°ãæ¡ç¨ãã¦ãããã¨ã§ãããã

### React Router

https://reactrouter.com/en/main

ããããã«ã¼ãã£ã³ã°ç³»ã®ã©ã¤ãã©ãªã¯ããä¸æãªã®ã§ã¯ãªãã§ããããã

```jsx
import React from 'react';
import { createRoot } from 'react-dom/client';
import { createBrowserRouter, RouterProvider, Link } from 'react-router-dom';

const router = createBrowserRouter([
  {
    path: '/',
    element: (
      <div>
        <h1>Hello World</h1>
        <Link to='about'>About Us</Link>
      </div>
    ),
  },
  {
    path: 'about',
    element: <div>About</div>,
  },
]);

createRoot(document.getElementById('root')).render(
  <RouterProvider router={router} />
);
```

### Reach Router

https://reach.tech/router/

[ãªãã¸ããª](https://github.com/reach/router)ãè¦ã¦ã¿ã¾ããããæçµæ´æ°ã 3 å¹´åã¨ãªã£ã¦ããç¾å¨ã¯ã¡ã³ããã³ã¹ããã¦ããªããã§ããã

```jsx
import React from 'react';
import { render } from 'react-dom';
import { Router, Link } from '@reach/router';

let Home = () => <div>Home</div>;
let Dash = () => <div>Dash</div>;

render(
  <Router>
    <Home path='/' />
    <Dash path='dashboard' />
  </Router>
);
```

## State Management

React ã¨ç¶æç®¡çã¯åã£ã¦ãåããªãé¢ä¿ã§ããåæ¥ç¶æç®¡çã©ã¤ãã©ãªã«ã¤ãã¦ã¾ã¨ããè¨äºãæ¸ããã®ã§èª­ãã§ããã ããã¨å¬ããã§ãã

https://zenn.dev/kazukix/articles/react-state-management-libraries

React Developer Roadmap ã§ç´¹ä»ããã¦ãããã®ã¯ãã®è¨äºã§ãç°¡åã«åãä¸ãã¾ãã

### Recoil

https://recoiljs.org/

Meta ç¤¾ãéçºãã¦ãã¾ããRedux ã¨ã¯çéã®ãããªè¨­è¨ææ³ã§ããã¹ãã¼ãã Atom ã¨ããåä½ã§ç®¡çããAtom ã¯è¤æ°ä½æãããã¨ãã§ãã¾ãã

```jsx
const textState = atom({
  key: 'textState', // ã°ã­ã¼ãã«ã§ä¸æãªã­ã¼
  default: '', // åæå¤
});

function TextInput() {
  const [text, setText] = useRecoilState(textState);

  const onChange = (event) => {
    setText(event.target.value);
  };

  return (
    <div>
      <input type='text' value={text} onChange={onChange} />
      <br />
      Echo: {text}
    </div>
  );
}
```

### MobX

https://mobx.js.org/README.html

ç­èã¯ä½¿ç¨ãããã¨ãããã¾ãããä¸»ã«ã¯ã©ã¹ã³ã³ãã¼ãã³ãã§ä½¿ç¨ããã¦ããã¨åæã«æ³åãã¦ãã¾ãã

```jsx
import React from 'react';
import ReactDOM from 'react-dom';
import { makeAutoObservable } from 'mobx';
import { observer } from 'mobx-react-lite';

class Timer {
  secondsPassed = 0;

  constructor() {
    makeAutoObservable(this);
  }

  increaseTimer() {
    this.secondsPassed += 1;
  }
}

const myTimer = new Timer();

const TimerView = observer(({ timer }) => (
  <span>Seconds passed: {timer.secondsPassed}</span>
));

ReactDOM.render(<TimerView timer={myTimer} />, document.body);

setInterval(() => {
  myTimer.increaseTimer();
}, 1000);
```

### Redux Toolkit

Redux ã®ãã¤ã©ã¼ãã¬ã¼ããæ¸ãããããã©ã«ãã§ãã¹ããã©ã¯ãã£ã¹ãçµã¿è¾¼ã¾ããRedux ã¢ããªã±ã¼ã·ã§ã³ãããç°¡åã«æ¸ããã¨ãã§ããããã«ãããã¼ã«ã»ããã§ããRedux å¬å¼ãæä¾ãã¦ãã¾ããæ¢å­ã®ç´ ã® Redux ã¢ããªã±ã¼ã·ã§ã³ã Redux Toolkit ã«ç½®ãæããã®ã¯çµæ§å´åãããããã§ãããæ°è¦ã« Redux ãæ¡ç¨ãããªãåºæ¬çã«ä½¿ç¨ããã¹ãã§ãããã

```jsx
import { createSlice } from '@reduxjs/toolkit';

// Slice ãä½æ (Slice ã¨ã¯ã¹ãã¢ãåå²ãããããªã¤ã¡ã¼ã¸)
export const counterSlice = createSlice({
  name: 'counter', // Sliceå
  initialState: {
    value: 0,
  },
  reducers: {
    increment: (state) => {
      state.value += 1;
    },
    decrement: (state) => {
      state.value -= 1;
    },
  },
});

// Action creator ã Reducer ãã¨ã«èªåçæããã¾ã
export const { increment, decrement } = counterSlice.actions;

export default counterSlice.reducer;
```

ã³ã³ãã¼ãã³ãããã¹ãã¢ã®ãã¼ã¿ãèª­ã¿æ¸ãã

```jsx
import { useSelector, useDispatch } from 'react-redux';
import { decrement, increment } from './counterSlice';

export function Counter() {
  // useSelector ã§ã¹ãã¢ãããã¼ã¿ãèª­ã¿è¾¼ã
  const count = useSelector((state) => state.counter.value);
  const dispatch = useDispatch();

  return (
    <div>
      <div>
        <button
          // ã¢ã¯ã·ã§ã³ããã£ã¹ããããã¹ãã¢ãæ´æ°
          onClick={() => dispatch(increment())}
        >
          Increment
        </button>
        <span>{count}</span>
        <button
          // ã¢ã¯ã·ã§ã³ããã£ã¹ããããã¹ãã¢ãæ´æ°
          onClick={() => dispatch(decrement())}
        >
          Decrement
        </button>
      </div>
    </div>
  );
}
```

### Zustand

https://github.com/pmndrs/zustand

è¶è»½é Redux ã®ãããªç«ã¡ä½ç½®ã§ãããã  Redux ããã·ã³ãã«ã«è¨è¿°ãããã¨ãã§ããHook ãä½¿ç¨ãã¦ã¹ãã¢ã®èª­ã¿æ¸ããè¡ãã¾ãã

```jsx
import { create } from 'zustand';

// ã¹ãã¢ã®ä½æ
const useBearStore = create((set) => ({
  bears: 0,
  increasePopulation: () => set((state) => ({ bears: state.bears + 1 })),
  removeAllBears: () => set({ bears: 0 }),
}));

// ã³ã³ãã¼ãã³ãã¨ãã¹ãã¢ãèª­ã¿æ¸ã
function BearCounter() {
  const bears = useBearStore((state) => state.bears);
  return <h1>{bears} around here ...</h1>;
}

function Controls() {
  const increasePopulation = useBearStore((state) => state.increasePopulation);
  return <button onClick={increasePopulation}>one up</button>;
}
```

### Context

https://beta.reactjs.org/reference/react/useContext

React æ¨æºã® API ã§ããç­èãä½¿ç¨ããæ©ä¼ãå¤ãã®ã§ããããã¤ã©ã¼ãã¬ã¼ãã®å¤ãã¨ãã¹ãã¼ããè¤éã«ãªã£ã¦ããã¨ãåã¬ã³ããªã³ã°ã®ç®¡çããContext éã®ä¾å­é¢ä¿ãå¢ãã³ã¼ããªã¼ãã£ã³ã°ã®æéãå¢ãããªã©ã®è¾ããæãã¦ãã¾ããã°ã­ã¼ãã«ã¹ãã¼ããåç´ãªæ§æã§ãããå¤é¨ã©ã¤ãã©ãªãå°å¥ããã¾ã§ããªãå ´åã«é©ãã¦ããã§ãããã

```jsx
import { createContext, useContext } from 'react';

const ThemeContext = createContext(null);

export default function MyApp() {
  return (
    <ThemeContext.Provider value='dark'>
      <Form />
    </ThemeContext.Provider>
  );
}

function Form() {
  return (
    <Panel title='Welcome'>
      <Button>Sign up</Button>
      <Button>Log in</Button>
    </Panel>
  );
}

function Panel({ title, children }) {
  // Context ãããã¼ã¿ãåå¾
  const theme = useContext(ThemeContext);
  const className = 'panel-' + theme;
  return (
    <section className={className}>
      <h1>{title}</h1>
      {children}
    </section>
  );
}
```

## Styling

ã¹ã¿ã¤ãªã³ã°ã©ã¤ãã©ãªã® npm trends ãã¼ã¿ãè¦ã¦ã¿ã¾ãã

![](https://storage.googleapis.com/zenn-user-upload/63dcc3315b1f-20230205.png)

Styled Components ã¯ã¾ã ã¾ã å¼·ãã§ãã­ãTailwind ã®ä¼¸ã³çããããã§ãã

### Emotion

https://emotion.sh/docs/introduction

```jsx
import { css } from '@emotion/react';

const color = 'white';

return (
  <div
    css={css`
      padding: 32px;
      background-color: hotpink;
      font-size: 24px;
      border-radius: 4px;
      &:hover {
        color: ${color};
      }
    `}
  >
    Hover to change color.
  </div>
);
```

`@emotion/styled` ããã±ã¼ã¸ãä½¿ç¨ãããã¨ã§ Styled Components ã£ã½ãæ¸ããã¨ãã§ãã¾ãã

```jsx
import styled from '@emotion/styled';

const Button = styled.button`
  padding: 32px;
  background-color: hotpink;
  font-size: 24px;
  border-radius: 4px;
  color: black;
  font-weight: bold;
  &:hover {
    color: white;
  }
`;

return <Button>This my button component.</Button>;
```

### Styled Components

https://styled-components.com/

å«ãã§ã¯ãªãã§ããã`@emotion/styled` ã¨åãã§ã¿ã°ãå¤æ°åããã¨ããã«è¥å¹²éåæãããã¾ãã

```jsx
const Button = styled.button`
  background: ${(props) => (props.primary ? 'palevioletred' : 'white')};
  color: ${(props) => (props.primary ? 'white' : 'palevioletred')};
  font-size: 1em;
  margin: 1em;
  padding: 0.25em 1em;
  border: 2px solid palevioletred;
  border-radius: 3px;
`;

return (
  <div>
    <Button>Normal</Button>
    <Button primary>Primary</Button>
  </div>
);
```

### Tailwind

https://tailwindcss.com/

className ãåé·ã«ãªãã¾ããããã¡ãã¡ã¹ã¿ã¤ã«ã®å®ç¾©åãè¦ã«è¡ããªãã¦ããã®ã¯å¥½ãã§ããæ£ããã¾ã§ã¯[ãã¼ãã·ã¼ã](https://tailwindcomponents.com/cheatsheet/)ãå¸¸ã«ã¿ãã§éãã¦ããã¾ãããã

```html
<figure class="md:flex bg-slate-100 rounded-xl p-8 md:p-0 dark:bg-slate-800">
  <img
    class="w-24 h-24 md:w-48 md:h-auto md:rounded-none rounded-full mx-auto"
    src="/sarah-dayan.jpg"
    alt=""
    width="384"
    height="512"
  />
  <div class="pt-6 md:p-8 text-center md:text-left space-y-4">
    <blockquote>
      <p class="text-lg font-medium">
        âTailwind CSS is the only framework that I've seen scale on large teams.
        Itâs easy to customize, adapts to any design, and the build size is
        tiny.â
      </p>
    </blockquote>
    <figcaption class="font-medium">
      <div class="text-sky-500 dark:text-sky-400">Sarah Dayan</div>
      <div class="text-slate-700 dark:text-slate-500">
        Staff Engineer, Algolia
      </div>
    </figcaption>
  </div>
</figure>
```

### Material UI

https://mui.com/

åé¨ã§ã¹ã¿ã¤ãªã³ã°ã¨ã³ã¸ã³ã¨ãã¦ Emotion ãä½¿ç¨ãã¦ãã¾ããStyled Components ãä½¿ç¨ãããã¨ãã§ãã¾ããå¬å¼ãç¨æãã¦ãããã³ãã¬ã¼ããæ²¢å±±ããã®ã§ã¹ã¿ã¤ã«ãä¸åæ¸ããã«ããããªãã¼ã¸ãä½æãããã¨ãã§ãã¾ãã

ã»ã¬ã¯ãããã¯ã¹ã®å®è£ä¾

```jsx
<FormControl fullWidth>
  <InputLabel id='demo-simple-select-label'>Age</InputLabel>
  <Select
    labelId='demo-simple-select-label'
    id='demo-simple-select'
    value={age}
    label='Age'
    onChange={handleChange}
  >
    <MenuItem value={10}>Ten</MenuItem>
    <MenuItem value={20}>Twenty</MenuItem>
    <MenuItem value={30}>Thirty</MenuItem>
  </Select>
</FormControl>
```

### Mantine

https://mantine.dev/

[2022 JavaScript Rising Stars](https://risingstars.js.org/2022/en#section-all) ã®å¨é¨éã§ 13 ä½ã«è¼ãã¦ãã¾ããããããããæ³¨ç®ãããã©ã¤ãã©ãªã§ããããåé¨ã§ã¹ã¿ã¤ãªã³ã°ã¨ã³ã¸ã³ã¨ãã¦ Emotion ãä½¿ç¨ãã¦ãã¾ãã

ã¯ãªãããã¼ãã¸ã³ãã¼ãã¿ã³ã®å®è£ä¾

```jsx
import { Button, Tooltip } from '@mantine/core';
import { useClipboard } from '@mantine/hooks';
import { IconCopy, IconCheck } from '@tabler/icons';

export function ButtonCopy() {
  const clipboard = useClipboard();
  return (
    <Tooltip
      label='Link copied!'
      offset={5}
      position='bottom'
      radius='xl'
      transition='slide-down'
      transitionDuration={100}
      opened={clipboard.copied}
    >
      <Button
        variant='light'
        rightIcon={
          clipboard.copied ? (
            <IconCheck size={20} stroke={1.5} />
          ) : (
            <IconCopy size={20} stroke={1.5} />
          )
        }
        radius='xl'
        size='md'
        styles={{
          root: { paddingRight: 14, height: 48 },
          rightIcon: { marginLeft: 22 },
        }}
        onClick={() =>
          clipboard.copy('https://www.youtube.com/watch?v=dQw4w9WgXcQ')
        }
      >
        Copy link to clipboard
      </Button>
    </Tooltip>
  );
}
```

### Chakra UI

https://chakra-ui.com/

```jsx
import * as React from 'react';
import { Box, Center, Image, Flex, Badge, Text } from '@chakra-ui/react';
import { MdStar } from 'react-icons/md';

export default function Example() {
  return (
    <Center h='100vh'>
      <Box p='5' maxW='320px' borderWidth='1px'>
        <Image borderRadius='md' src='https://bit.ly/2k1H1t6' />
        <Flex align='baseline' mt={2}>
          <Badge colorScheme='pink'>Plus</Badge>
          <Text
            ml={2}
            textTransform='uppercase'
            fontSize='sm'
            fontWeight='bold'
            color='pink.800'
          >
            Verified &bull; Cape Town
          </Text>
        </Flex>
        <Text mt={2} fontSize='xl' fontWeight='semibold' lineHeight='short'>
          Modern, Chic Penthouse with Mountain, City & Sea Views
        </Text>
        <Text mt={2}>$119/night</Text>
        <Flex mt={2} align='center'>
          <Box as={MdStar} color='orange.400' />
          <Text ml={1} fontSize='sm'>
            <b>4.84</b> (190)
          </Text>
        </Flex>
      </Box>
    </Center>
  );
}
```

Material UI vs Mantine vs Chakra UI ã®åè² ã®è¡æ¹ã¯ãã³ãã«ãµã¤ãºã®éããªã®ã§ã¯ï¼ã¨ãã£ãå°è±¡ãæ­£ç´ã¹ã¿ã¤ãªã³ã°ã«å¼·ãèå³ã¯ãªããä½¿ãã¥ãããªããã°ã©ãã§ãããã¨ããã®ãæ¬é³...ããã ãUI ã®å°è±¡ãä½¿ããããããµã¼ãã¹ã«ä¸ããå½±é¿ã¯ã¨ã¦ãå¤§ãããã¨ã¯çè§£ãã¦ããã®ã§ãä¸æãªãã¶ã¤ã³ãå®è£ããããããªããã³ãã¬ã¼ããä½¿ã£ãæ¹ãè¯ããããã¾ãããã¶ã¤ã³ç³»ã®ã©ã¤ãã©ãªã¯åºæ¬çã«å¥ããã¥ããã®ã§ãæ¬¡ã«ç´¹ä»ãã CSS Modules ãæ¡ç¨ããäºä¾ãããè¦ããã¾ãã

### CSS Modules

https://github.com/css-modules/css-modules

Pure ãª CSS ãæ¸ãã¾ããããããã°ã­ã¼ãã«æ±æãããªãã§ï¼ã¨ãããã¤ãCSS Modules èªä½ã¯ä»æ§ã§ãããwebpack ã vite ãªã©ã®ãã³ãã©ã¼ã«å®è£ããããæå¾ã«ä½¿ç¨ããã®ã¯çµæ§åã ããã¯ã©ã¹åã®è£å®ãå¹ããªãã¦ã¤ãã¤ãã ã£ãã(ç¥ããªãã ãã§è£å®ãããæ¹æ³ããããããããªã)

```css
.className {
  color: green;
}
```

```jsx
import styles from './style.css';

element.innerHTML = '<div class="' + styles.className + '">';
```

## API Calls

æè¿æãé²åãã¦ããé ç®ã§ã¯ãªãã§ããããããã¼ã¿åå¾ã ãã§ã¯ãªãç¶æç®¡çã¾ã§è¡ãããã®ãåºã¦ãã¾ããã

### SWR

https://swr.vercel.app/

Vercel ãéçºãã¦ãããã¼ã¿ãã§ããã³ã°ã©ã¤ãã©ãªã§ãã

```jsx
import useSWR from 'swr';

const fetcher = (...args) => fetch(...args).then((res) => res.json());

function Profile() {
  const { data, error, isLoading } = useSWR('/api/user/123', fetcher);

  if (error) return <div>failed to load</div>;
  if (isLoading) return <div>loading...</div>;

  return <div>hello {data.name}!</div>;
}
```

â ãããªã¹ãã¼ããä½ãå¿è¦ããªãã§ãã­ï¼

```js
const [isLoading, setIsLoading] = useState(false);
const [error, setError] = useState('');
```

ä»ã«ãä¾¿å©ãªãªãã·ã§ã³ãæ²¢å±±ãããã¦ã¼ã¶ã¼ããã¼ã¸ã«æ»ã£ã¦ãã¦ãã¡ã¼ã«ã¹ããæããä¸å®ééãã¨ã«ãã¼ã¿ãã§ããããããã¨ãã§ãã¾ããééããªãä»å¾ããã«ä½¿ããã¦ããã§ãããã

### react-query

https://tanstack.com/

ç¾å¨ã¯ TanStack Query ã«çµ±åããã¾ãããã­ã£ãã·ã¥ã®ç¶æãªã©ãç¢ºèªã§ãã DevTool ãããã¾ããSWR ã¨åãã§è±å¯ãªãªãã·ã§ã³ãããã¾ãã

```jsx
function Example() {
  const { isLoading, error, data } = useQuery({
    queryKey: ['repoData'],
    queryFn: () =>
      fetch('https://api.github.com/repos/tannerlinsley/react-query').then(
        (res) => res.json()
      ),
  });

  if (isLoading) return 'Loading...';

  if (error) return 'An error has occurred: ' + error.message;

  return (
    <div>
      <h1>{data.name}</h1>
      <p>{data.description}</p>
      <strong>ð {data.subscribers_count}</strong>{' '}
      <strong>â¨ {data.stargazers_count}</strong>{' '}
      <strong>ð´ {data.forks_count}</strong>
    </div>
  );
}
```

npm trends ãè¦ãã¨ãã¾ã  React Query ãã TanStack Query ã¸ã®ç§»è¡ããã¾ãé²ãã§ããªããã§ããä»ã¯ã»ã¨ãã©å·®ããªãã®ã§ãSWR vs TanStack Query ã®è¡æ¹ãæ°ã«ãªãã¾ãã­ã

![](https://storage.googleapis.com/zenn-user-upload/fd00565afb39-20230205.png)

### Axios

https://axios-http.com/

HTTP ã¯ã©ã¤ã¢ã³ãã¨ãã£ããããã§ããã­ããã¦ã³ã­ã¼ãæ°ãæ¡ãéãã¾ãããã  Axios vs SWR ãªã®ãã¨ããã¨ããã§ã¯ãªããSWR ã TanStack Query ã®ã¡ã¤ã³ã¯ ã­ã£ãã·ã¥æ©æ§ã¨ Hooks API ãªã®ã§ fetcher é¢æ°ãèªä½ããå¿è¦ããããããã§ Axios ãä½¿ç¨ãããã¨ãã§ãã¾ãã

![](https://storage.googleapis.com/zenn-user-upload/51688d609b0b-20230205.png)

```jsx
async function getUser() {
  try {
    const response = await axios.get('/user?ID=12345');
    console.log(response);
  } catch (error) {
    console.error(error);
  }
}
```

### suprtagent

https://ladjs.github.io/superagent/

ä½¿ç¨ãããã¨ã¯ãªãã§ãã

```js
import request from 'superagent';

request
  .post('/api/pet')
  .send({ name: 'Manny', species: 'cat' })
  .set('X-API-Key', 'foobar')
  .set('Accept', 'application/json')
  .then((res) => {
    alert('yay got ' + JSON.stringify(res.body));
  });
```

### rtk-query

https://redux-toolkit.js.org/rtk-query/overview

RTK Query ã¯ Redux Toolkit ã®ããã±ã¼ã¸ã«å«ã¾ãããªãã·ã§ã³ã®ã¢ããªã³ã§ãã

ãµã¼ãã¼ã®ãã¼ã¹ URL ã¨å¯¾è©±ãããã¨ã³ããã¤ã³ããåæãããAPI ã¹ã©ã¤ã¹ããå®ç¾©ãã¾ãã

```jsx
import { createApi, fetchBaseQuery } from '@reduxjs/toolkit/query/react'
import type { Pokemon } from './types'

export const pokemonApi = createApi({
  reducerPath: 'pokemonApi',
  baseQuery: fetchBaseQuery({ baseUrl: 'https://pokeapi.co/api/v2/' }),
  endpoints: (builder) => ({
    getPokemonByName: builder.query<Pokemon, string>({
      query: (name) => `pokemon/${name}`,
    }),
  }),
})

// å®ç¾©ãããã¨ã³ããã¤ã³ãã«åºã¥ãã¦ããã¯ãèªåçæããã¾ã
export const { useGetPokemonByNameQuery } = pokemonApi
```

API ã¹ã©ã¤ã¹ã«ã¯ãèªåçæããã Redux ã¹ã©ã¤ã¹ãªãã¥ã¼ãµã¨ãè³¼èª­ã®ã©ã¤ãã¿ã¤ã ãç®¡çããã«ã¹ã¿ã ããã«ã¦ã§ã¢ãå«ã¾ãã¦ãã¾ãããããã¯ä¸¡æ¹ã¨ã Redux ã¹ãã¢ã«è¿½å ããå¿è¦ãããã¾ãã

```jsx
import { configureStore } from '@reduxjs/toolkit';
import { setupListeners } from '@reduxjs/toolkit/query';
import { pokemonApi } from './services/pokemon';

export const store = configureStore({
  reducer: {
    [pokemonApi.reducerPath]: pokemonApi.reducer,
  },
  middleware: (getDefaultMiddleware) =>
    getDefaultMiddleware().concat(pokemonApi.middleware),
});

setupListeners(store.dispatch);
```

ã³ã³ãã¼ãã³ãããèªåçæãããããã¯ãä½¿ç¨ãã¾ãã

```jsx
import { useGetPokemonByNameQuery } from './services/pokemon';

export default function App() {
  const { data, error, isLoading } = useGetPokemonByNameQuery('bulbasaur');
}
```

ãã¯ã Redux ã¯ æè¿ã®ãã¼ã«ã¨æ¯ã¹ãã¨ãã¤ã©ã¼ãã¬ã¼ããå¤ããªãåé·ã«æããé¨åãããã¾ãã

### Apollo

https://www.apollographql.com/docs/react

GraphQL ã¯ã©ã¤ã¢ã³ãã¨ãã£ããã¾ã Apollo Client ãé¸æè¢ã«ä¸ããã¾ããã¨ããããä¸å¼·ã§ããããã³ãã¥ããã£ãéå¸¸ã«å¤§ããããã­ã¥ã¡ã³ããåå®ãã¦ãã¾ããã¯ã¨ãªã®ãªãã·ã§ã³ãã­ã£ãã·ã¥ãæè»ã«è¨­å®ã§ãã¾ãã

```jsx
import { useQuery, gql } from '@apollo/client';

const GET_LOCATIONS = gql`
  query GetLocations {
    locations {
      id
      name
      description
      photo
    }
  }
`;

function DisplayLocations() {
  const { loading, error, data } = useQuery(GET_LOCATIONS);

  if (loading) return <p>Loading...</p>;
  if (error) return <p>Error : {error.message}</p>;

  return data.locations.map(({ id, name, description, photo }) => (
    <div key={id}>
      <h3>{name}</h3>
      <p>{description}</p>
    </div>
  ));
}
```

Apollo Client ã®å¼·åãªæ©è½ã®ä¸ã¤ã§ãããã§ããããªã·ã¼ã«ã¤ãã¦ãç´¹ä»ãã¾ãã(æè¿ã®ã©ã¤ãã©ãªã¯åæ§ãªæ©è½ãããã¾ãã...) ãã§ããããªã·ã¼ã¯ `useQuery` ã®ãªãã·ã§ã³ã§æå®ã§ãã¾ãã`nextFetchPolicy` ãè¨­å®ããã¨ã`fetchPolicy` ã¯ã¯ã¨ãªã®æåã®å®è¡ã«ä½¿ç¨ããã`nextFetchPolicy` ã¯ 2 åç®ä»¥éã«ä½¿ç¨ããã¾ãã

```jsx
const { loading, error, data } = useQuery(GET_DOGS, {
  // æåã¯ãããã¯ã¼ã¯ãªã¯ã¨ã¹ããéããããã®å¾ã¯ã­ã£ãã·ã¥ãä½¿ç¨ããä¾
  fetchPolicy: 'network-only',
  nextFetchPolicy: 'cache-first',
});
```

- cache-first

ããã©ã«ãã®ãã§ããããªã·ã¼ãã¾ãã­ã£ãã·ã¥ã«å¯¾ãã¦ã¯ã¨ãªã¼ãå®è¡ããè¦æ±ããããã¼ã¿ããã¹ã¦ã­ã£ãã·ã¥ã«å­å¨ããå ´åããã®ãã¼ã¿ãè¿ããã¾ããããã§ãªãå ´åã¯ãGraphQL ãµã¼ãã¼ã«å¯¾ãã¦ã¯ã¨ãªãå®è¡ãããã®ãã¼ã¿ãã­ã£ãã·ã¥ããå¾ã«è¿ãã¾ãã

- cache-only

ã­ã£ãã·ã¥ã«å¯¾ãã¦ã®ã¿ã¯ã¨ãªã¼ãå®è¡ãã¾ãããµã¼ãã¼ã«åãåããããã¨ã¯ããã¾ãããè¦æ±ããããã¹ã¦ã®ãã£ã¼ã«ãã®ãã¼ã¿ãã­ã£ãã·ã¥ã«å«ã¾ãã¦ããªãå ´åãã¨ã©ã¼ãã¹ã­ã¼ããã¾ãã

- cache-and-network

ã­ã£ãã·ã¥ã¨ GraphQL ãµã¼ãã¼ã®ä¸¡æ¹ã«å¯¾ãã¦ã¯ã¨ãªãå®è¡ãã¾ãããµã¼ãã¼å´ã®ã¯ã¨ãªçµæãã­ã£ãã·ã¥ããããã£ã¼ã«ããå¤æ´ããå ´åãã¯ã¨ãªã¯èªåçã«æ´æ°ããã¾ãã

- network-only

æåã«ã­ã£ãã·ã¥ãç¢ºèªãããã¨ãªããGraphQL ãµã¼ãã¼ã«å¯¾ãã¦ã¯ã¨ãªãå®è¡ãã¾ããã¯ã¨ãªã®çµæã¯ã­ã£ãã·ã¥ã«ä¿å­ããã¾ãã

- no-cache

network-only ã¨ä¼¼ã¦ãã¾ãããã¯ã¨ãªã¼ã®çµæãã­ã£ãã·ã¥ã«ä¿å­ãããªãç¹ãç°ãªãã¾ãã

- standby

cache-first ã¨åãã­ã¸ãã¯ãä½¿ç¨ãã¾ãããã ãããã®ã¯ã¨ãªã¯ãåºç¤ã¨ãªããã£ã¼ã«ãã®å¤ãå¤æ´ããã¦ãèªåçã«ã¯æ´æ°ããã¾ããããã®ã¯ã¨ãªã¯ãrefetch ã¨ updateQueries ãä½¿ç¨ãã¦æåã§æ´æ°ãããã¨ãã§ãã¾ãã

### Relay

https://relay.dev/

Meta ç¤¾ãéçºãã¦ãã GraphQL ã¯ã©ã¤ã¢ã³ãã©ã¤ãã©ãªã§ãã

### Urql

https://formidable.com/open-source/urql/

Formidable Labs ç¤¾ã«ãã£ã¦éçºã»ä¿å®ããã¦ãã GraphQL ã¯ã©ã¤ã¢ã³ãã©ã¤ãã©ãªã§ããUniversal React Query Library ã®ç¥ã ããã§ããReact ã¨ããã¤ã¤ãPreactãVueãSvelte ãªã©ããµãã¼ããã¦ãã¾ãã

```jsx
import { useQuery } from 'urql';

const TodosQuery = `
  query {
    todos {
      id
      title
    }
  }
`;

const Todos = () => {
  // useQuery ã¯ã¿ãã«ãè¿ãã¾ãã
  // è¿ãããã¿ãã«ã¯ãçµæãªãã¸ã§ã¯ãã¨åå®è¡é¢æ°ãå«ãéåã§ãã
  const [result, reexecuteQuery] = useQuery({
    query: TodosQuery,
    // ãªã¯ã¨ã¹ãããªã·ã¼ãè¨­å®ã§ãã¾ããApollo ã§ãããã§ããããªã·ã¼ã§ãã
    // cache-first / cache-only / cache-and-network / network-only
    requestPolicy: 'cache-and-network',
  });

  const refresh = () => {
    reexecuteQuery({ requestPolicy: 'network-only' });
  };

  const { data, fetching, error } = result;

  if (fetching) return <p>Loading...</p>;
  if (error) return <p>Oh no... {error.message}</p>;

  return (
    <ul>
      {data.todos.map((todo) => (
        <li key={todo.id}>{todo.title}</li>
      ))}
    </ul>
  );
};
```

## Testing

![](https://storage.googleapis.com/zenn-user-upload/20d420214365-20230219.png)

### Jest

https://jestjs.io/

### Vitest

### React Testing Library

### Cypress

### Playwright

## Frameworks

### Next.js

https://nextjs.org/

Next.js ã«é¢ãã¦ã¯ä»æ´åãä¸ããå¿è¦ããªãæ°ããã¾ããVercel ç¤¾ã«åªç§ãªäººæãéä¸­ãã¦ããã®ã§ä»å¾ããã«æå¾ã§ãã¾ãã

ãã¹ããã©ã¯ãã£ã¹ã®è©°ãåããããã¯ã®ããã«æ©è½ãåå®ãã¦ãã¾ãã

- ãã¼ã¸ãã¼ã¹ã®ã«ã¼ãã£ã³ã°ã·ã¹ãã 
- ããªã¬ã³ããªã³ã°ã¯ãéççæï¼SSGï¼ã¨ãµã¼ãã¼ãµã¤ãã¬ã³ããªã³ã°ï¼SSRï¼ã®ä¸¡æ¹ããã¼ã¸åä½ã§ãµãã¼ã
- èªåã³ã¼ãåå²ã«ãããã¼ã¸ã­ã¼ãã®é«éå
- æé©åãããããªãã§ããã«ããã¯ã©ã¤ã¢ã³ããµã¤ãã«ã¼ãã³ã°
- åèµã® CSS ã¨ Sass ã®ãµãã¼ããããã³ä»»æã® CSS-in-JS ã©ã¤ãã©ãªã®ãµãã¼ã
- Fast Refresh ã«å¯¾å¿ããéçºç°å¢
- Serverless Functions ã§ API ã¨ã³ããã¤ã³ããæ§ç¯ããããã® API ã«ã¼ã
- ãã«ã¨ã¯ã¹ãã³ããã«

### Remix

## Forms

ãã©ã¼ã ã®è³ªãä½ãã¨ã¦ã¼ã¶ã¼ã«å¤§ããªã¹ãã¬ã¹ãããã¾ãã

- ã©ããå¥åã¨ã©ã¼ã«ãªã£ã¦ããã®ãåããããã
- éä¿¡ãã¦å¥åã¨ã©ã¼ãããã¨å¥åãã¦ããåå®¹ãæ¶ãã
- å¥åä¾ãåããããã (placeholder ã«å¥åä¾ããããååº¦ç¢ºèªãããããå¥åããæå­ãæ¶ãå¿è¦ããããªã©)

ãã®ãããã©ã¼ã ã«ã¯ãã ããããã¨ããæ°æã¡ãå¼·ãã§ããèªåã§ãã©ã¼ã ãä½ããã¨ãã§ãã¾ãããä¾¿å©ãªã©ã¤ãã©ãªãå¢ãã¦ãã¦ããã®ã§ãåãåããã¨ããã®ãé¸æè¢ã®ä¸ã¤ã§ãã

ã¾ãã¯æ¯è¼ããã

![](https://storage.googleapis.com/zenn-user-upload/b0db09cdbee1-20230212.png)

React Hook Form ã®ä¼¸ã³çãå¤§ããã§ãã­ãFormik ãããªãä½¿ç¨ããã¦ãã¾ãããã¡ã³ããã³ã¹ã®æ´»çºãããµã¤ãºãªã©ãæ¯è¼ããã¨ React Hook Form ã®æ¡ç¨ãç¡é£ããªã¨æãã¾ãã(React Hook Form ã¯[9.1kB](https://bundlephobia.com/package/react-hook-form@7.43.1)ãFormik ã¯[13kB](https://bundlephobia.com/package/formik@2.2.9)ã) React Developer Roadmap ã«ã¯åºã¦ãã¾ããããZod ã Yup ãªã©ããªãã¼ã·ã§ã³ã©ã¤ãã©ãªã¨ã®ç¸æ§ãªã©ãè©ä¾¡å¯¾è±¡ã«ãªãããã§ããææ³ã¨ããé¢ã§ã React Hook Form ãåäººçã«ã¯å¥½ã¿ã§ãã

### React Hook Form

https://react-hook-form.com/

[å¬å¼ãµã¤ã](https://react-hook-form.com/faqs#ReactHookFormFormikorReduxForm)ã«ããä»ã®ã©ã¤ãã©ãªã¨ã®æ¯è¼è¡¨ããåããã¾ãã

![](https://storage.googleapis.com/zenn-user-upload/5f67271fe287-20230212.png)

æ³¨ç®ãã¹ãã¯ React Hook Form ãéå¶å¾¡ã³ã³ãã¼ãã³ããä½¿ç¨ãã¦ããç¹ã§ãã[å¬å¼ãµã¤ã](https://react-hook-form.com/faqs#PerformanceofReactHookForm)ã«ãä¸è¨ã®ããã«æ¸ããã¦ãããããã©ã¼ãã³ã¹ã®ãããã®ãããªå®è£ã«ãªã£ã¦ãã¾ãã

> ããã©ã¼ãã³ã¹ã¯ãã®ã©ã¤ãã©ãªãä½ãããä¸»ãªçç±ã®ä¸ã¤ã§ãããReact Hook Form ã¯å¶å¾¡ãããªããã©ã¼ã ã«ä¾å­ãã¦ãããregister é¢æ°ã ref ãã­ã£ããã£ããå¶å¾¡ãããã³ã³ãã¼ãã³ãã Controller ã useController ã§ãã®åã¬ã³ããªã³ã°ã¹ã³ã¼ããæã£ã¦ããã®ã¯ãã®ããã§ãããã®ã¢ãã­ã¼ãã«ãããã¦ã¼ã¶ã¼ãå¥åããåå®¹ããã®ä»ã®ãã©ã¼ã ã®å¤ããã©ã¼ã ãã¢ããªã±ã¼ã·ã§ã³ã®ã«ã¼ãã§å¤æ´ããããã¨ã«ããåã¬ã³ããªã³ã°ã®éãæ¸ãããã¨ãã§ãã¾ããã³ã³ãã¼ãã³ãã¯ãå¶å¾¡ãããã³ã³ãã¼ãã³ãããããªã¼ãã¼ããããå°ãªãããããã¼ã¸ã¸ã®å®è£ãéããªãã¾ãã

ã¡ãªã¿ã« React å¬å¼ã¯ãã©ã¼ã ã®å®è£ã«å¶å¾¡ãããã³ã³ãã¼ãã³ããä½¿ç¨ãããã¨ãæ¨å¥¨ãã¦ãã¾ãã

https://ja.reactjs.org/docs/uncontrolled-components.html

> ã»ã¨ãã©ã®å ´åã§ã¯ããã©ã¼ã ã®å®è£ã«ã¯å¶å¾¡ãããã³ã³ãã¼ãã³ã (controlled component) ãä½¿ç¨ãããã¨ããå§ããã¦ãã¾ããå¶å¾¡ãããã³ã³ãã¼ãã³ãã§ã¯ããã©ã¼ã ã®ãã¼ã¿ã¯ React ã³ã³ãã¼ãã³ããæ±ãã¾ããéå¶å¾¡ã³ã³ãã¼ãã³ã (uncontrolled component) ã¯ãã®ä»£æ¿ã¨ãªããã®ã§ããããã©ã¼ã ãã¼ã¿ã DOM èªèº«ãæ±ãã¾ãã
>
> éå¶å¾¡ã³ã³ãã¼ãã³ããè¨è¿°ããã«ã¯ãå state ã®æ´æ°ã«å¯¾ãã¦ã¤ãã³ããã³ãã©ãæ¸ãä»£ããã«ãref ãä½¿ç¨ãã¦ DOM ãããã©ã¼ã ã®å¤ãåå¾ãã¾ãã
>
> éå¶å¾¡ã³ã³ãã¼ãã³ãã§ã¯ DOM ã«ä¿¡é ¼ã§ããæå ±æº (source of truth) ãä¿æãããããä½¿ç¨ããã° React ã¨é React ã®ã³ã¼ãã®çµ±åãç°¡åã«ãªããã¨ãããã¾ããæ±ãã¦ãæ§ããªãã®ã§éãè¨è¿°ãããã¨æããªãå°ãã ãã³ã¼ãéãæ¸ããã¾ããããã§ãªããã°ãéå¸¸ã®å¶å¾¡ãããã³ã³ãã¼ãã³ããä½¿ç¨ããã¹ãã§ãã

åºæ¬çãªæ¸ãæ¹ãè¦ã¦ããã¾ãã

```tsx
import { useForm } from 'react-hook-form';

type FormData = {
  firstName: string;
  lastName: string;
};

export default function App() {
  const {
    register,
    setValue,
    handleSubmit,
    formState: { errors },
  } = useForm<FormData>();
  const onSubmit = handleSubmit((data) => console.log(data));
  // firstName and lastName will have correct type

  return (
    <form onSubmit={onSubmit}>
      <label>First Name</label>
      <input {...register('firstName')} />
      <label>Last Name</label>
      <input {...register('lastName')} />
      <button
        type='button'
        onClick={() => {
          setValue('lastName', 'luo'); // â
          setValue('firstName', true); // â: true is not string
          errors.bill; // â: property bill does not exist
        }}
      >
        SetValue
      </button>
    </form>
  );
}
```

Yup, Zod ãªã©ãå¬å¼ã§ãµãã¼ããã¦ãã¾ããYup ã®ä¾ â

```tsx
import { useForm } from 'react-hook-form';
import { yupResolver } from '@hookform/resolvers/yup';
import * as yup from 'yup';

const schema = yup
  .object({
    firstName: yup.string().required(),
    age: yup.number().positive().integer().required(),
  })
  .required();
type FormData = yup.InferType<typeof schema>;

export default function App() {
  const {
    register,
    handleSubmit,
    formState: { errors },
  } = useForm<FormData>({
    resolver: yupResolver(schema),
  });
  const onSubmit = (data: FormData) => console.log(data);

  return (
    <form onSubmit={handleSubmit(onSubmit)}>
      <input {...register('firstName')} />
      <p>{errors.firstName?.message}</p>

      <input {...register('age')} />
      <p>{errors.age?.message}</p>

      <input type='submit' />
    </form>
  );
}
```

### Formik

https://formik.org/

Formik ã¯ä¸è¨é ç®ã 1 ã¤ã®å ´æã«ã¾ã¨ãããã¨ã§ããã¹ãããªãã¡ã¯ã¿ãªã³ã°ããã©ã¼ã ã®æ¨è«ãå®¹æã«ããç©äºãæ´çãããã¨ããããã¨ãç®çã«éçºãããã©ã¤ãã©ãªã¨å¬å¼ãµã¤ãã«æ¸ããã¦ãã¾ãã

- ãã©ã¼ã ã¹ãã¼ãã¸ã®å¤ã®åºãå¥ã
- ããªãã¼ã·ã§ã³ã¨ã¨ã©ã¼ã¡ãã»ã¼ã¸
- ãã©ã¼ã éä¿¡ã®å¦ç

```tsx
import 'react-app-polyfill/ie11';
import { Formik, Field, Form, FormikHelpers } from 'formik';

interface Values {
  firstName: string;
  lastName: string;
  email: string;
}

const App = () => {
  return (
    <div>
      <h1>Signup</h1>
      <Formik
        initialValues={{
          firstName: '',
          lastName: '',
          email: '',
        }}
        onSubmit={(
          values: Values,
          { setSubmitting }: FormikHelpers<Values>
        ) => {
          setTimeout(() => {
            alert(JSON.stringify(values, null, 2));
            setSubmitting(false);
          }, 500);
        }}
      >
        <Form>
          <label htmlFor='firstName'>First Name</label>
          <Field id='firstName' name='firstName' placeholder='John' />

          <label htmlFor='lastName'>Last Name</label>
          <Field id='lastName' name='lastName' placeholder='Doe' />

          <label htmlFor='email'>Email</label>
          <Field
            id='email'
            name='email'
            placeholder='john@acme.com'
            type='email'
          />

          <button type='submit'>Submit</button>
        </Form>
      </Formik>
    </div>
  );
};
```

å¬å¼ãµã¤ãã§ã¯ããªãã¼ã·ã§ã³ã©ã¤ãã©ãªã« Yup ãä½¿ç¨ãããã¨ãæ¨ããã¦ãã¾ãã

```jsx
import { Formik, Form, Field } from 'formik';
import * as Yup from 'yup';

const SignupSchema = Yup.object().shape({
  firstName: Yup.string()
    .min(2, 'Too Short!')
    .max(50, 'Too Long!')
    .required('Required'),
  lastName: Yup.string()
    .min(2, 'Too Short!')
    .max(50, 'Too Long!')
    .required('Required'),
  email: Yup.string().email('Invalid email').required('Required'),
});

export const ValidationSchemaExample = () => (
  <div>
    <h1>Signup</h1>
    <Formik
      initialValues={{
        firstName: '',
        lastName: '',
        email: '',
      }}
      validationSchema={SignupSchema}
      onSubmit={(values) => {
        console.log(values);
      }}
    >
      {({ errors, touched }) => (
        <Form>
          <Field name='firstName' />
          {errors.firstName && touched.firstName ? (
            <div>{errors.firstName}</div>
          ) : null}
          <Field name='lastName' />
          {errors.lastName && touched.lastName ? (
            <div>{errors.lastName}</div>
          ) : null}
          <Field name='email' type='email' />
          {errors.email && touched.email ? <div>{errors.email}</div> : null}
          <button type='submit'>Submit</button>
        </Form>
      )}
    </Formik>
  </div>
);
```

### Final Form

https://final-form.org/react

[@erikras ãã](https://twitter.com/erikras)ã [Redux Form](https://redux-form.com/8.3.0/) ã§ã®éçºçµé¨ããã¨ã«éçºããã©ã¤ãã©ãªã§ãã

```jsx
import { Form, Field } from 'react-final-form';

const MyForm = () => (
  <Form
    onSubmit={onSubmit}
    validate={validate}
    render={({ handleSubmit }) => (
      <form onSubmit={handleSubmit}>
        <h2>Simple Default Input</h2>
        <div>
          <label>First Name</label>
          <Field name='firstName' component='input' placeholder='First Name' />
        </div>

        <h2>An Arbitrary Reusable Input Component</h2>
        <div>
          <label>Interests</label>
          <Field name='interests' component={InterestPicker} />
        </div>

        <h2>Render Function</h2>
        <Field
          name='bio'
          render={({ input, meta }) => (
            <div>
              <label>Bio</label>
              <textarea {...input} />
              {meta.touched && meta.error && <span>{meta.error}</span>}
            </div>
          )}
        />

        <h2>Render Function as Children</h2>
        <Field name='phone'>
          {({ input, meta }) => (
            <div>
              <label>Phone</label>
              <input type='text' {...input} placeholder='Phone' />
              {meta.touched && meta.error && <span>{meta.error}</span>}
            </div>
          )}
        </Field>

        <button type='submit'>Submit</button>
      </form>
    )}
  />
);
```

## Mobile

### React Native

https://reactnative.dev/

React ã¨åãæ§æã§ ã¢ãã¤ã«ã¢ããªéçºãã§ããã©ã¤ãã©ãªã§ããReact Native ãåå¹´éã»ã©ä½¿ç¨ãã¾ãããããã«ãå¨ãã¨ã¹ã¿ã¤ãªã³ã°ã«æ£ããã°ããªãå¿å°ããéçºãè¡ãã¾ãã(Expo ãä½¿ç¨ããã°ãã«ãå¨ãã¯å¤å°æ¥½ã«ãªãã®ããããã¾ãããç­èã¯ React Native CLI ãä½¿ç¨ãã¦ãã¾ãã) React Native ã®ã³ã³ãã¼ãã³ãã¯æçµçã« ãã¤ãã£ãã® View ã¸å¤æãããã¨ãã£ããã¨ããããå¤ãã¯ããã¾ããããã¤ãã£ãéçºã®ç¥è­ãæ±ãããããã¨ãããã¾ããã¾ã React ã¨æ¯ã¹ã¦ãã¾ãã¨ã³ãã¥ããã£ã®å¤§ãããããªãå°ããæãã¾ããã«ã¼ãã£ã³ã°ãã¢ãã¡ã¼ã·ã§ã³ã¨ãã£ãåºæ¬çãªãã¨ã¯ã©ã¤ãã©ãªãåå®ãã¦ãã¾ãããå°ãããããªè¦ä»¶ã«ãªãã¨ã©ã¤ãã©ãªãåä¾ã®æ°ãæ¥æ¸ãã¾ããã¡ã³ããã³ã¹ãã»ã¨ãã©ããã¦ããªãã£ãããGithub ã® ã¹ã¿ã¼æ°ãæ°ç¾ãã®ãä½¿ç¨ããæ©ä¼ããªãã¨ã¯è¨ãã¾ãããã©ã¤ãã©ãªã«ãã°ãããå ´åãJava ã Objective-C ãèª­ã¿æ¸ãããå¿è¦ããããããçµå± JavaScript ã ãã§ã¯ç°¡æ½ããããªãé¨åãããã¾ãã

ãã¤ãã¹é¢ï¼ã°ããæ¸ãã¦ãã¾ãã¾ããããWeb ç³»ã®ãã¼ã ã§ã¢ãã¤ã«ã¢ããªãéçºãããå ´åã¨ã¦ãéå®ãã¾ããæ°ããè¨èªãå­¦ç¿ããå¿è¦ããªãæç¹ã§éçºã³ã¹ããä¸ããã¾ãããä¸é¨ã§ã¯ Web ã®è³ç£ãä½¿ãã¾ããã¾ããFlutter ã«å¢ããå¥ªããã¦ããæãå¦ããªãã®ã§é å¼µã£ã¦ã»ããã§ãã

```jsx
import React from 'react';
import { Text, View } from 'react-native';

const HelloWorldApp = () => {
  return (
    <View
      style={{
        flex: 1,
        justifyContent: 'center',
        alignItems: 'center',
      }}
    >
      <Text>Hello, world!</Text>
    </View>
  );
};

export default HelloWorldApp;
```

## Frontend Roadmap

https://roadmap.sh/frontend

å½ç¶ React ä»¥å¤ã«ãã¢ããªã±ã¼ã·ã§ã³ãéçºããä¸ã§å¿è¦ã«ãªã£ã¦ããç¥è­ã¯ããããããã¾ããHTTP ã ãã©ã¦ã¶ã®ä»çµã¿ã¯ãã¡ããã®ãã¨ãTypeScript ã¯ä»ãå¿é ã§ããéã®ãã¯é·ãã§ãããä¸ããä¸ã¤ãã¤å®ç§ã«ããªãã¦ããå¿è¦ã¯ãªããå®åã§å¿è¦ã«ãªã£ãæãèå³ãæ¹§ããæã«ã³ãã³ãé²ãã¦è¡ãã°ããã¨æã£ã¦ãã¾ãã

## ã¾ã¨ã

React ã¨ããã©ã¤ãã©ãªã²ã¨ã¤ã¨ã£ã¦ãããªãé·ãã­ã¼ããããã«ãªã£ã¦ãã¦ãããã»ã©æ¨ä»ã®ãã­ã³ãã¨ã³ãé åã¯è¤éåãã¦ãã¾ãããµã¼ãã¼ãµã¤ããã¨ãã¸ã«ã¾ã§å½±é¿ãåã¼ãæ©è½ãå¤ãããã¯ããã­ã³ãã¨ã³ãã¨ããè¨èèªä½ææ§ãªãã®ã¨ãªãã¤ã¤ããã¾ãã

React å¨ãã®ã¨ã³ã·ã¹ãã ã¯æãæè¡ã®é²åãæ©ããæµè¡ã®ç§»ãå¤ãããæ¿ããé åã ã¨æã£ã¦ãã¾ããã ãããããããããã®ã©ã¤ãã©ãªã¯ãªã¯ã³ã³ãã ã¨ãããçµå±ãã§ååããéçºèã®èªå·±æºè¶³ãã¨ãã£ãã³ã¡ã³ããè¦ããã¾ããããããåºæ¬çã«æ°ããæè¡ã¨ããã®ã¯ç¾ç¶ã®åé¡ç¹ãè§£æ±ºããããã«çã¾ãã¾ãããã¨ãä½¿ãããªããªã£ãã¨ãã¦ããããã§å­¦ãã ææ³ã¯å¿ãæ¬¡ã®ã¹ãããã«ç¹ããã¨æã£ã¦ãã¾ããæ°ããã©ã¤ãã©ãªããã¬ã¼ã ã¯ã¼ã¯ãåºã¦ããéã«ããããé©åã«è©ä¾¡ã§ããããæ¥ãæãåããã¦æ¤è¨¼ãããã¨ãç¶ãã¦ããããã§ãã

æå¾ã¾ã§ãèª­ã¿ããã ããããã¨ããããã¾ãã ðââï¸
