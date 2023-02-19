---
title: 'React Developer Roadmap 2023'
emoji: '🦁'
type: 'tech' # tech: 技術記事 / idea: アイデア
topics: ['react']
published: false
---

## はじめに

https://roadmap.sh/react

React Developer Roadmap の 2023 年版が公開されているので一通り (浅〜く) 見て感想などをだらだら書きます。各項目についての詳しい内容は公式サイトをご参照ください。

ロードマップの順番はこちらです。

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

React のロードマップは JavaScript の勉強が最初にきます。JavaScript のライブラリなので当然ですね。サボらず地道に頑張りましょう。最近、非同期処理とイベントループ周りの知識が足りないことを痛感させれられたので勉強し直しています。詰まる時って React というより JavaScript を理解できていないことが多いんですよね...。

## CLI Tools

現在 React を使用したアプリケーションを作成する方法は無数にあるため迷う点の一つです。React のコアコントリビューターであり、最近 Vercel へ入られた [Andrew Clark さん](https://twitter.com/acdlite)がこのようなツイートをされていました。確かに Next.js などを使用する機会が多くなり、素の React でアプリケーションを作成する機会が減ってきているのかもしれません。

https://twitter.com/acdlite/status/1617611126514266112

### Create React App

https://create-react-app.dev/

こちらに関して説明は不要でしょう...。React を最も支えてきたツールなのではないでしょうか。

おそらく全フロントエンドエンジニアが一度は実行したであろうコマンド。

```bash
npx create-react-app my-app
cd my-app
npm run start
```

Create React App について最近話題になっている PR があります。T3 Stack の提唱者である [Theo さん](https://twitter.com/t3dotgg)が作成しました。

https://github.com/reactjs/reactjs.org/pull/5487

React は現在[新しい公式サイト](https://beta.reactjs.org/)を作っているのですが、そこにこのような記述があります。

> React を学ぶなら、Create React App をお勧めします。これは、React を試し、新しいシングルページ、クライアントサイドアプリケーションを構築する最も一般的な方法です。React のために作られていますが、ルーティングやデータフェッチについては意見が分かれていません。

ここで Create React App ではなく、Vite を勧めるよう文章を修正した PR です。かなり議論が盛り上がっていて、React のコアコントリビューターである [Dan さん](https://twitter.com/dan_abramov)も[コメント](https://github.com/reactjs/reactjs.org/pull/5487#issuecomment-1409720741)されています。なぜ Create React App がヘイトを集めているかよくわかるため一読されることをお勧めします。

### Vite

https://vitejs.dev/

Vue.js の開発者である [Evan You さん](https://github.com/yyx990803)が開発しています。

```bash
npm create vite@latest my-app -- --template react
cd my-app
npm install
npm run dev
```

Create React App の代わりに使用されていく機会が増えるでしょう。

## Components

### Class Components vs Functional Components

現在の React の世界は Hooks により成り立っているので ? 基本的には Functional Components を使用しましょう。筆者は Functional Components ネイティブ世代なので、Class Components は `componentDidMount` や `componentWillUnmount` など、React のライフサイクルを勉強した際に少し触れた程度であり、実務で書いた経験はありません。

Class Components の例

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

Functional Components の例

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

2 年前 React を勉強したての頃、JSX と Google で検索すると 「JSX 気持ち悪い」などとサジェストされていたのが懐かしいです。 また JSX を批判するような記事もかなり見かけました。個人的には VSCode や TypeScript などのおかげもあり開発者体験は最高です。Django や PHP などのテンプレートエンジンには正直戻りたくない...。デザイナーとの分業問題などもありましたが、JSX が当たり前になりすぎてその問題もほとんど解消されたのではないでしょうか？ Vue などと違って React は独自の文法があるわけではなく、素の JavaScript で書ける点も好きなポイントです。

### Props vs State

何をどのコンポーネントで管理すべきなのか、プロジェクトのルールやアーキテクチャによって適切に判断する必要があります。無駄な State を作成しないことや、Props として最低限必要な物を渡すようにすることで、再レンダリングを抑制することにつながり、アプリケーションのパフォーマンス向上に直結します。Presntational/Container Components vs Colocation/Lifting State Up の話はとても勉強になりました。

https://medium.com/@dan_abramov/smart-and-dumb-components-7ca2f9a7c7d0

https://kentcdodds.com/blog/state-colocation-will-make-your-react-app-faster

### Conditional Rendering

https://reactjs.org/docs/conditional-rendering.html

日本語にすると「条件付きレンダリング」です。ログインしているかしていないかで表示を切り替えたい時などに使用します。三項演算子か && 演算子を使用することがほとんどです。

### Composition

https://reactjs.org/docs/composition-vs-inheritance.html

コンポーネントを Props として他のコンポーネントに渡すことです。React.children が主な例です。

## Rendering

### Component Life Cycle

コンポーネント内のどのコードがどのタイミングで実行され、その結果がいつ反映されるのかを理解する必要があります。`useState` と `useEffect` を使用し、様々な箇所に `console.log` をいれ実際に確かめてみると、とても勉強になるためお勧めです。

### Lists and Keys

キーは、React がどの項目が変更・追加・削除されたかを識別するのに使われます。データの ID などをキーとして使用することが多いです。

```jsx
const numbers = [1, 2, 3, 4, 5];
const listItems = numbers.map((number) => (
  <li key={number.toString()}>{number}</li>
));
```

インデックスをキーとして設定するのはアンチパターンになっています。

```jsx
todos.map((todo, index) => <Todo {...todo} key={index} />);
```

理由はこちら

https://robinpokorny.com/blog/index-as-a-key-is-an-anti-pattern/

### Render Props

props を 通じて JSX 要素をコンポーネントに渡すことです。

https://www.patterns.dev/posts/render-props-pattern/

### Refs

よく比較される State / 状態 (useState) と Ref / 参照 (useRef) ですが、違いは大きく二つあります。

- 参照を更新しても再レンダリングは発生しないが、状態を更新するとコンポーネントは再レンダリングされる
- 参照の更新は同期 (更新された参照値がすぐに利用できる)、状態の更新は非同期 (再描画後に状態変数が更新される)

また useRef は DOM 要素にアクセスすることができるため、インプットフィールドにファーカスを当てたりすることができます。

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

ただ、Dom を操作することは、React が管理している仮想 DOM と 実 DOM の間で不整合が発生する可能性があるため注意して使用することが必要です。

### Events

https://beta.reactjs.org/learn/responding-to-events

みなさんが普段たくさん書いているだろうこれです。

```jsx
export default function Button() {
  function handleClick() {
    alert('You clicked me!');
  }

  return <button onClick={handleClick}>Click me</button>;
}
```

イベントハンドラの名前は、慣習上 handle の後にイベント名を付けるのが一般的です。`onClick={handleClick}`、 `onMouseEnter={handleMouseEnter}` などのようになります。最初は `<button onClick={handleClick}>` と、`<button onClick={handleClick()}>` の違いが分からなかったのも懐かしいです...。関数は呼び出すのではなく、渡すことに注意しましょう。後者はレンダリング中に実行されてしまいます。

### High Order Components

High Order Components (HOC) はそういった名前の機能があるわけではなく、React で用いられる考え方・パターンの一つです。具体的には、HOC はコンポーネントを受け取り、新しいコンポーネントを返す関数です。

```jsx
const withError = (Component) => (props) => {
  if (props.error) {
    return <div>Something went wrong ...</div>;
  }

  return <Component {...props} />;
};

export default withError;
```

> React Hooks が内部から実装の詳細（例：ステート、副作用）で関数コンポーネントに味付けするための現状であるのに対し、React Higher-Order Components は外部から関数（およびクラスコンポーネント）に味付けをするものである。HOC は、実際のコンポーネントがその実装の詳細（React Hooks など）を内部で実行する前にコンポーネントを保護するための完璧な盾となる。

下記記事より引用

https://www.robinwieruch.de/react-higher-order-components/

## Hooks

### useState

set 関数で値が更新されるのは関数が呼び出された後、ということを知らなくて詰まったことがありました。

```jsx
const Component = () => {
  const [count, setCount] = useState(0);

  const handleClick = () => {
    setCount((prevCount) => prevCount + 1);
    console.log(count); // この時点ではまだ 0
  };
};
```

### useEffect

第二引数とクリーンアップの使い方について最初は時に躓きました。処理が実行されるタイミングを理解する必要があります。Class Components の `componentDidMount` や `componentWillUnmount` などのライフサイクルメソッドが useEffect でどのように表現できるのかも理解しておくといいかもしれません。[うひょさん](https://twitter.com/uhyo_)のこちらの記事には大変お世話になりました。

https://zenn.dev/uhyo/articles/react17-useeffect

### Writing Custom Hooks

use~ と命名された関数を作成します。複数のコンポーネントに存在する共通処理を取り出して作成した関数です。ライブラリの関数を直接呼び出さず、一層ラップして制約を加える場合になどにも使用されます。

### useCallback

props へ渡す関数をキャッシュします。正直あまり積極的に使えていないので意識していきたい...。

### useRef

### useMemo

props へ渡すオブジェクトをキャッシュします。

### useReducer

### useContext

グローバルステートを作成できます。筆者も使う機会が多いですが、ステートが増えるにつれ Context 間の依存関係が複雑になり、コードリーディングが大変になる印象です。また、余分な際レンダリングを発生させないように気を使う必要があります。

## Routers

Next.js など最近のフレームワークはルーティングを自動で行なってくれるため自前で書いた経験がほとんどありません。今後使われていくだろうフレームワークもおそらくファイルベースルーティングを採用していることでしょう。

### React Router

https://reactrouter.com/en/main

おそらくルーティング系のライブラリはこれ一択なのではないでしょうか。

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

[リポジトリ](https://github.com/reach/router)を見てみましたが、最終更新が 3 年前となっており現在はメンテナンスされていなそうでした。

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

React と状態管理は切っても切れない関係です。先日状態管理ライブラリについてまとめた記事を書いたので読んできただけると嬉しいです。

https://zenn.dev/kazukix/articles/react-state-management-libraries

React Developer Roadmap で紹介されているものはこの記事でも簡単に取り上げます。

### Recoil

https://recoiljs.org/

Meta 社が開発しています。Redux とは真逆のような設計思想です。ステートを Atom という単位で管理し、Atom は複数作成することができます。

```jsx
const textState = atom({
  key: 'textState', // グローバルで一意なキー
  default: '', // 初期値
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

筆者は使用したことがありません。主にクラスコンポーネントで使用されていると勝手に想像しています。

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

Redux のボイラープレートを減らし、デフォルトでベストプラクティスが組み込まれ、Redux アプリケーションをより簡単に書くことができるようにしたツールセットです。Redux 公式が提供しています。既存の素の Redux アプリケーションを Redux Toolkit に置き換えるのは結構労力がいりそうですが、新規に Redux を採用するなら基本的に使用するべきでしょう。

```jsx
import { createSlice } from '@reduxjs/toolkit';

// Slice を作成 (Slice とはストアを分割したようなイメージ)
export const counterSlice = createSlice({
  name: 'counter', // Slice名
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

// Action creator が Reducer ごとに自動生成されます
export const { increment, decrement } = counterSlice.actions;

export default counterSlice.reducer;
```

コンポーネントからストアのデータを読み書き。

```jsx
import { useSelector, useDispatch } from 'react-redux';
import { decrement, increment } from './counterSlice';

export function Counter() {
  // useSelector でストアからデータを読み込む
  const count = useSelector((state) => state.counter.value);
  const dispatch = useDispatch();

  return (
    <div>
      <div>
        <button
          // アクションをディスパッチしストアを更新
          onClick={() => dispatch(increment())}
        >
          Increment
        </button>
        <span>{count}</span>
        <button
          // アクションをディスパッチしストアを更新
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

超軽量 Redux のような立ち位置です。ただ Redux よりシンプルに記述することができ、Hook を使用してストアの読み書きを行えます。

```jsx
import { create } from 'zustand';

// ストアの作成
const useBearStore = create((set) => ({
  bears: 0,
  increasePopulation: () => set((state) => ({ bears: state.bears + 1 })),
  removeAllBears: () => set({ bears: 0 }),
}));

// コンポーネントとかストアを読み書き
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

React 標準の API です。筆者も使用する機会が多いのですが、ボイラープレートの多さと、ステートが複雑になってくると、再レンダリングの管理や、Context 間の依存関係が増えコードリーディングの時間が増えるなどの辛さを感じています。グローバルステートが単純な構成であり、外部ライブラリを導入するまでもない場合に適しているでしょう。

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
  // Context からデータを取得
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

スタイリングライブラリの npm trends データを見てみます。

![](https://storage.googleapis.com/zenn-user-upload/63dcc3315b1f-20230205.png)

Styled Components はまだまだ強いですね。Tailwind の伸び率もすごいです。

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

`@emotion/styled` パッケージを使用することで Styled Components っぽく書くこともできます。

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

嫌いではないですが、`@emotion/styled` と同じでタグを変数化するところに若干違和感があります。

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

className が冗長になりますが、いちいちスタイルの定義元を見に行かなくていいのは好きです。慣れるまでは[チートシート](https://tailwindcomponents.com/cheatsheet/)を常にタブで開いておきましょう。

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
        “Tailwind CSS is the only framework that I've seen scale on large teams.
        It’s easy to customize, adapts to any design, and the build size is
        tiny.”
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

内部でスタイリングエンジンとして Emotion を使用しています。Styled Components を使用することもできます。公式が用意しているテンプレートも沢山あるのでスタイルを一切書かずにきれいなページを作成することもできます。

セレクトボックスの実装例

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

[2022 JavaScript Rising Stars](https://risingstars.js.org/2022/en#section-all) の全部門で 13 位に輝いています。これからより注目されるライブラリでしょう。内部でスタイリングエンジンとして Emotion を使用しています。

クリップボードへコピーボタンの実装例

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

Material UI vs Mantine vs Chakra UI の勝負の行方はバンドルサイズの違いなのでは？といった印象。正直スタイリングに強い興味はなく、使いづらくなければどれでもいいというのが本音...。ただ、UI の印象や使いやすさがサービスに与える影響はとても大きいことは理解しているので、下手なデザインを実装するくらいならテンプレートを使った方が良さそう。また、デザイン系のライブラリは基本的に剥がしづらいので、次に紹介する CSS Modules を採用する事例もよく見かけます。

### CSS Modules

https://github.com/css-modules/css-modules

Pure な CSS が書けますよ、しかもグローバル汚染をしないで！というやつ。CSS Modules 自体は仕様であり、webpack や vite などのバンドラーに実装がある。最後に使用したのは結構前だが、クラス名の補完が効かなくてイマイチだった。(知らないだけで補完させる方法があるかもしれない)

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

最近最も進化している項目ではないでしょうか。データ取得だけではなく状態管理まで行えるものも出てきました。

### SWR

https://swr.vercel.app/

Vercel が開発しているデータフェッチングライブラリです。

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

↓ こんなステートを作る必要もないですね！

```js
const [isLoading, setIsLoading] = useState(false);
const [error, setError] = useState('');
```

他にも便利なオプションが沢山あり、ユーザーがページに戻ってきてファーカスした時や、一定間隔ごとにデータフェッチをすることができます。間違いなく今後さらに使われていくでしょう。

### react-query

https://tanstack.com/

現在は TanStack Query に統合されました。キャッシュの状態などを確認できる DevTool があります。SWR と同じで豊富なオプションがあります。

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
      <strong>👀 {data.subscribers_count}</strong>{' '}
      <strong>✨ {data.stargazers_count}</strong>{' '}
      <strong>🍴 {data.forks_count}</strong>
    </div>
  );
}
```

npm trends を見ると、まだ React Query から TanStack Query への移行があまり進んでいなそうです。今はほとんど差がないので、SWR vs TanStack Query の行方が気になりますね。

![](https://storage.googleapis.com/zenn-user-upload/fd00565afb39-20230205.png)

### Axios

https://axios-http.com/

HTTP クライアントといったらこれですよね。ダウンロード数も桁が違います。ただ Axios vs SWR なのかというとそうではなく、SWR や TanStack Query のメインは キャッシュ機構と Hooks API なので fetcher 関数を自作する必要があり、そこで Axios を使用することもできます。

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

使用したことはないです。

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

RTK Query は Redux Toolkit のパッケージに含まれるオプションのアドオンです。

サーバーのベース URL と対話したいエンドポイントを列挙した「API スライス」を定義します。

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

// 定義されたエンドポイントに基づいてフックが自動生成されます
export const { useGetPokemonByNameQuery } = pokemonApi
```

API スライスには、自動生成された Redux スライスリデューサと、購読のライフタイムを管理するカスタムミドルウェアも含まれています。これらは両方とも Redux ストアに追加する必要があります。

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

コンポーネントから自動生成されたフックを使用します。

```jsx
import { useGetPokemonByNameQuery } from './services/pokemon';

export default function App() {
  const { data, error, isLoading } = useGetPokemonByNameQuery('bulbasaur');
}
```

やはり Redux は 最近のツールと比べるとボイラープレートが多くなり冗長に感じる部分があります。

### Apollo

https://www.apollographql.com/docs/react

GraphQL クライアントといったらまず Apollo Client が選択肢に上がります。というより一強でしょう。コミュニティも非常に大きく、ドキュメントも充実しています。クエリのオプションやキャッシュも柔軟に設定できます。

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

Apollo Client の強力な機能の一つであるフェッチポリシーについてご紹介します。(最近のライブラリは同様な機能がありますが...) フェッチポリシーは `useQuery` のオプションで指定できます。`nextFetchPolicy` を設定すると、`fetchPolicy` はクエリの最初の実行に使用され、`nextFetchPolicy` は 2 回目以降に使用されます。

```jsx
const { loading, error, data } = useQuery(GET_DOGS, {
  // 最初はネットワークリクエストを送るが、その後はキャッシュを使用する例
  fetchPolicy: 'network-only',
  nextFetchPolicy: 'cache-first',
});
```

- cache-first

デフォルトのフェッチポリシー。まずキャッシュに対してクエリーを実行し、要求されたデータがすべてキャッシュに存在する場合、そのデータが返されます。そうでない場合は、GraphQL サーバーに対してクエリを実行し、そのデータをキャッシュした後に返します。

- cache-only

キャッシュに対してのみクエリーを実行します。サーバーに問い合わせることはありません。要求されたすべてのフィールドのデータがキャッシュに含まれていない場合、エラーがスローされます。

- cache-and-network

キャッシュと GraphQL サーバーの両方に対してクエリを実行します。サーバー側のクエリ結果がキャッシュされたフィールドを変更した場合、クエリは自動的に更新されます。

- network-only

最初にキャッシュを確認することなく、GraphQL サーバーに対してクエリを実行します。クエリの結果はキャッシュに保存されます。

- no-cache

network-only と似ていますが、クエリーの結果がキャッシュに保存されない点が異なります。

- standby

cache-first と同じロジックを使用します。ただし、このクエリは、基礎となるフィールドの値が変更されても自動的には更新されません。このクエリは、refetch と updateQueries を使用して手動で更新することができます。

### Relay

https://relay.dev/

Meta 社が開発している GraphQL クライアントライブラリです。

### Urql

https://formidable.com/open-source/urql/

Formidable Labs 社によって開発・保守されている GraphQL クライアントライブラリです。Universal React Query Library の略だそうです。React といいつつ、Preact、Vue、Svelte などをサポートしています。

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
  // useQuery はタプルを返します。
  // 返されるタプルは、結果オブジェクトと再実行関数を含む配列です。
  const [result, reexecuteQuery] = useQuery({
    query: TodosQuery,
    // リクエストポリシーも設定できます。Apollo でいうフェッチポリシーです。
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

Next.js に関しては今更取り上げる必要もない気がします。Vercel 社に優秀な人材が集中しているので今後さらに期待できます。

ベストプラクティスの詰め合わせパックのように機能が充実しています。

- ページベースのルーティングシステム
- プリレンダリングは、静的生成（SSG）とサーバーサイドレンダリング（SSR）の両方をページ単位でサポート
- 自動コード分割によるページロードの高速化
- 最適化されたプリフェッチによるクライアントサイドルーチング
- 内蔵の CSS と Sass のサポート、および任意の CSS-in-JS ライブラリのサポート
- Fast Refresh に対応した開発環境
- Serverless Functions で API エンドポイントを構築するための API ルート
- フルエクステンダブル

### Remix

## Forms

フォームの質が低いとユーザーに大きなストレスをかけます。

- どこが入力エラーになっているのか分かりずらい
- 送信して入力エラーがあると入力していた内容が消える
- 入力例が分かりずらい (placeholder に入力例があり、再度確認したいため入力した文字を消す必要があるなど)

そのためフォームにはこだわりたいという気持ちが強いです。自前でフォームを作ることもできますが、便利なライブラリが増えてきているので、力を借りるというのも選択肢の一つです。

まずは比較から。

![](https://storage.googleapis.com/zenn-user-upload/b0db09cdbee1-20230212.png)

React Hook Form の伸び率が大きいですね。Formik もかなり使用されていますが、メンテナンスの活発さやサイズなどを比較すると React Hook Form の採用が無難かなと思います。(React Hook Form は[9.1kB](https://bundlephobia.com/package/react-hook-form@7.43.1)。Formik は[13kB](https://bundlephobia.com/package/formik@2.2.9)。) React Developer Roadmap には出てきませんが、Zod や Yup などバリデーションライブラリとの相性なども評価対象になりそうです。文法という面でも React Hook Form が個人的には好みです。

### React Hook Form

https://react-hook-form.com/

[公式サイト](https://react-hook-form.com/faqs#ReactHookFormFormikorReduxForm)にある他のライブラリとの比較表をお借りします。

![](https://storage.googleapis.com/zenn-user-upload/5f67271fe287-20230212.png)

注目すべきは React Hook Form が非制御コンポーネントを使用している点です。[公式サイト](https://react-hook-form.com/faqs#PerformanceofReactHookForm)にも下記のように書かれており、パフォーマンスのためそのような実装になっています。

> パフォーマンスはこのライブラリが作られた主な理由の一つである。React Hook Form は制御されないフォームに依存しており、register 関数が ref をキャプチャし、制御されるコンポーネントが Controller や useController でその再レンダリングスコープを持っているのはそのためです。このアプローチにより、ユーザーが入力した内容やその他のフォームの値がフォームやアプリケーションのルートで変更されることによる再レンダリングの量を減らすことができます。コンポーネントは、制御されたコンポーネントよりもオーバーヘッドが少ないため、ページへの実装が速くなります。

ちなみに React 公式はフォームの実装に制御されたコンポーネントを使用することを推奨しています。

https://ja.reactjs.org/docs/uncontrolled-components.html

> ほとんどの場合では、フォームの実装には制御されたコンポーネント (controlled component) を使用することをお勧めしています。制御されたコンポーネントでは、フォームのデータは React コンポーネントが扱います。非制御コンポーネント (uncontrolled component) はその代替となるものであり、フォームデータを DOM 自身が扱います。
>
> 非制御コンポーネントを記述するには、各 state の更新に対してイベントハンドラを書く代わりに、ref を使用して DOM からフォームの値を取得します。
>
> 非制御コンポーネントでは DOM に信頼できる情報源 (source of truth) を保持するため、使用すれば React と非 React のコードの統合が簡単になることがあります。汚くても構わないので速く記述したいと思うなら少しだけコード量も減らせます。そうでなければ、通常の制御されたコンポーネントを使用するべきです。

基本的な書き方を見ていきます。

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
          setValue('lastName', 'luo'); // ✅
          setValue('firstName', true); // ❌: true is not string
          errors.bill; // ❌: property bill does not exist
        }}
      >
        SetValue
      </button>
    </form>
  );
}
```

Yup, Zod などを公式でサポートしています。Yup の例 ↓

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

Formik は下記項目を 1 つの場所にまとめることで、テストやリファクタリング、フォームの推論を容易にし、物事を整理することをすることを目的に開発されたライブラリと公式サイトに書かれています。

- フォームステートへの値の出し入れ
- バリデーションとエラーメッセージ
- フォーム送信の処理

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

公式サイトではバリデーションライブラリに Yup を使用することが推されています。

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

[@erikras さん](https://twitter.com/erikras)が [Redux Form](https://redux-form.com/8.3.0/) での開発経験をもとに開発したライブラリです。

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

React と同じ構文で モバイルアプリ開発ができるライブラリです。React Native を半年間ほど使用しましたが、ビルド周りとスタイリングに慣れればかなり心地よく開発を行えます。(Expo を使用すればビルド周りは多少楽になるのかもしれません。筆者は React Native CLI を使用しています。) React Native のコンポーネントは最終的に ネイティブの View へ変換されるといったこともあり、多くはありませんがネイティブ開発の知識が求められることがあります。また React と比べてしまうとコミュニティの大きさがかなり小さく感じます。ルーティングやアニメーションといった基本的なことはライブラリが充実していますが、少しニッチな要件になるとライブラリや前例の数が急減します。メンテナンスがほとんどされていなかったり、Github の スター数が数百ものを使用する機会もないとは言えません。ライブラリにバグがある場合、Java や Objective-C を読み書きする必要があるため、結局 JavaScript だけでは簡潔しきれない部分もあります。

マイナス面？ばかり書いてしまいましたが、Web 系のチームでモバイルアプリを開発したい場合とても重宝します。新しく言語を学習する必要がない時点で開発コストが下がりますし、一部では Web の資産を使いまわせます。Flutter に勢いを奪われている感が否めないので頑張ってほしいです。

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

当然 React 以外にもアプリケーションを開発する上で必要になってくる知識はたくさんあります。HTTP や ブラウザの仕組みはもちろんのこと、TypeScript は今や必須です。道のりは長いですが、上から一つずつ完璧にこなしていく必要はなく、実務で必要になった時や興味が湧いた時にコツコツ進めて行けばいいと思っています。

## まとめ

React というライブラリひとつとってもかなり長いロードマップになっていて、それほど昨今のフロントエンド領域は複雑化しています。サーバーサイドやエッジにまで影響を及ぼす機能も多く、もはやフロントエンドという言葉自体曖昧なものとなりつつあります。

React 周りのエコシステムは最も技術の進化が早く、流行の移り変わりが激しい領域だと思っています。だからこそ、よく「あのライブラリはオワコン」だとか、「結局〜で十分」「開発者の自己満足」といったコメントを見かけます。しかし、基本的に新しい技術というのは現状の問題点を解決するために生まれます。たとえ使われなくなったとしても、そこで学んだ思想は必ず次のステップに繋がると思っています。新しいライブラリやフレームワークが出てきた際に、それを適切に評価できるよう日々手を動かして検証することを続けていきたいです。

最後までお読みいただきありがとうございました 🙇‍♂️
