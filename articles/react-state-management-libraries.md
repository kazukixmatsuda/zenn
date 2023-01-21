---
title: 'React の状態管理ライブラリ9選'
emoji: '😎'
type: 'tech'
topics: ['react']
published: true
---

## はじめに

次から次へと登場する状態管理ライブラリですが、それだけ React (に限った話ではないが) において状態管理というのは大きなテーマであり、最も実装難易度の高いトピックの一つでしょう。適切な設計ができないとアプリケーションの規模が大きくなるにつれ負債は増え続けます。

状態管理の難しさをよく表した文章が [Redux の公式サイト](https://redux.js.org/understanding/thinking-in-redux/motivation)にあるためお借りしたいと思います。(Redux の公式サイトは読み物としても面白いです)

> JavaScript のシングルページアプリケーションの要件がますます複雑になるにつれて、コードはこれまで以上に多くの状態を管理する必要があります。この状態には、サーバーのレスポンスやキャッシュされたデータ、まだサーバーに永続化されていないローカルに作成されたデータなどが含まれます。UI の状態も複雑化しており、アクティブなルート、選択されたタブ、スピナー、ページネーションコントロールなどを管理する必要があります。
>
> この常に変化する状態を管理するのは大変なことです。モデルが別のモデルを更新できるなら、ビューはモデルを更新でき、そのモデルが別のモデルを更新し、さらにそれが別のビューを更新させるかもしれません。ある時点で、アプリで何が起こるかわからなくなり、**いつ、なぜ、どのように状態を制御するのかがわからなくなります**。システムが不透明で非決定的であると、バグの再現や新機能の追加が難しくなります。

筆者もこのような状況に直面しました。状態が 5 個程度であれば何の問題もないかもしれません。ただそれが 10、20..と増えていった場合、**いつ、なぜ、どのように状態を制御するのかがわからなくなります**。このような複雑さを少しでも楽に管理し、デグレすることを恐れずに自信を持って開発できるよう日々ベストプラクティスが模索され、ライブラリが開発されているというわけです。

という、the 技術記事 のような書き出しをしましたが、今回は設計論的なお堅い話をするわけではなく、主要な React の状態管理ライブラリを 9 個筆者が触ってみて感じたことや、それぞれの特徴、基本的な使い方について書きたいと思います。比較表などを使用して優劣をつけるわけではありません。基本的に公式サイトを参考にしています。

登場するライブラリはこちら。

- Redux
- Recoil
- Zustand
- Jotai
- Valtio
- Nano stores
- Hookstate
- Elf
- Rematch

:::message
タイトルに「React の」状態管理ライブラリとありますが React 以外で使用できるものも含まれます。
:::

余談ですが [npm trends](https://npmtrends.com/@hookstate/core-vs-@ngneat/elf-vs-jotai-vs-mobx-vs-nanostores-vs-recoil-vs-redux-vs-valtio-vs-zustand) のデータを見てみます。

![](https://storage.googleapis.com/zenn-user-upload/6a293266ee9b-20230121.png)

Redux の圧勝ですね。Redux を批判するような記事を時々見かけますが、新規プロジェクトでの採用率が気になります。既に Redux で書かれたものを移行するコストが大きすぎることなども影響してそうです。

## Redux

https://redux.js.org/

- Flux アーキテクチャ
- 大規模なアプリケーションでは特に力を発揮
- 成熟したエコシステム
- [1.6kB](https://bundlephobia.com/package/redux@4.2.0) + [4.7kB](https://bundlephobia.com/package/react-redux@8.0.5) (redux + react-redux)
- [13.5kB](https://bundlephobia.com/package/@reduxjs/toolkit@1.9.1) (Redux Toolkit)

:::message
本記事に記載のサイズは　 minified + gzipped されたものです。
:::

※ この記事では Action や Reducer、Dispatch など Redux の基本的な概念の説明は行いません。もし Redux に触れたことがない方は、公式サイトの[チュートリアル](https://redux.js.org/tutorials/essentials/part-1-overview-concepts)がとてもわかりやすいためそちらをご参考にしてください。

React の状態管理ライブラリではもっとも使用され有名である Redux ですが、React が Hooks の世界に突入後、一気に人気が落ちた気がします。ローカルステートは `useState` で手軽に制御できる反面、グルーバルステートは起こりうるすべての状態変化パターンの Action を書き、さらにそれらの Action を処理するために Reducer を書くと、多くのコードが必要になり、すぐにメンテナンスコストが肥大化してしまうことが問題点の一つでしょう。

そのような問題を解決するために公式が Redux Toolkit (RTK) を作成しました。ボイラープレートを減らし、デフォルトでベストプラクティスが組み込まれ、Redux アプリケーションをより簡単に書くことができるようにしたツールセットです。

> If you are writing any Redux logic today, you should be using Redux Toolkit to write that code!

公式も RTK を使いな！と言っています。

具体的な書き方を見ていく前に Redux の 3 つの原則をおさらいしておきます。

### Single source of truth

アプリケーションのグローバルステートは、1 つのストア内のオブジェクトツリーに保存されます。複数ストアを作成することはできません。

### State is read-only

ステートは読み取り専用です。ステートを変更する唯一の方法は、何が起こったかを記述したプレーンオブジェクトである Action を発行することです。アプリケーションで何が起こったかを記述するイベントと考えることができます。ストアを直接書き換えることはできず、UI イベント、ネットワークコールバック、あるいは WebSocket のような他のソースからのデータであろうと、最終的には Action を発行する必要があります。

### Changes are made with pure functions

Action によってステートがどのように更新されるかを指定するために Reducer を書きます。Reducer は前のステートと Action の内容をもとに新しいステートを計算する純粋な関数です。既存のステートを変更することは許されません。その代わり、既存のステートをコピーし、コピーされた値に変更を加えることで不変の更新を行います。Action がイベントなのであれば、Reducer はイベントリスナーと考えることができるでしょう。`(state, action) => newState`

ステートの更新フローを簡素化した公式サイトの図をお借りします。矢印に注目すると一方通行になっていることがわかります。このようにすることで複雑なデータ管理に秩序を持たせ、予測可能な状態管理を実現しています。

![](https://storage.googleapis.com/zenn-user-upload/b47d4ad813d9-20230115.png)

より具体的な図を見てみます。なんやら難しいことをやっているように見えますが、Action を ストアに送り、Action の内容をもとに Reducer が ステート更新し、更新したことが UI へ通知され、新しいステートをもとに再レンダリングしているだけです。

![](https://storage.googleapis.com/zenn-user-upload/37638d33b12d-20230118.gif)

前置きが長くなりましたが RTK のコードを見ていきます。まずは `configureStore` で空のストアを作成します。

```js:app/store.js
import { configureStore } from '@reduxjs/toolkit';

export default configureStore({
  reducer: {}
});
```

コンポーネントからストアにアクセスできるようにするため `Provider` でラップします。

```jsx:index.js
import { Provider } from 'react-redux'
import store from './app/store'

ReactDOM.render(
  <Provider store={store}>
    <App />
  </Provider>,
  document.getElementById('root')
)
```

`createSlice` で Slice を作成していきます。Slice とは RTK の概念で、ストアを分割して管理しやすくしたものです。分割はあくまで見かけ上の話であり実際のストアは 1 つです。

```js:src/features/counter/counterSlice.js
import { createSlice } from '@reduxjs/toolkit'

export const counterSlice = createSlice({
  name: 'counter', // Slice名
  initialState: { // 初期値
    value: 0
  },
  reducers: {
    increment: state => {
      // Redux のルール違反である「現在のステートを変更」しているように見えますが
      // 内部で Immer を使用しているため、実際には現在のステートを変更していません。
      // 変更を検知し内部的に新しいステートを作成しています。
      state.value += 1
    },
    decrement: state => {
      state.value -= 1
    },
    incrementByAmount: (state, action) => {
      state.value += action.payload
    }
  }
})

// Action creator が Reducer ごとに自動生成されます
export const { increment, decrement, incrementByAmount } = counterSlice.actions

export default counterSlice.reducer
```

作成した Slice をストアへ追加します。

```js:app/store.js
import { configureStore } from '@reduxjs/toolkit'
import counterReducer from '../features/counter/counterSlice'

export default configureStore({
  reducer: {
    counter: counterReducer // 追加
  }
})
```

コンポーネントからストアの読み書きを行います。読み込みには `useSelector` を使用し、必要なステートのみ選択します。そうすることで取得したステート以外が更新された場合でもコンポーネントは再レンダリングされません。書き込みは Action creator を実行し、dispatch するだけです。

```js:features/counter/Counter.js
import { useSelector, useDispatch } from 'react-redux'
import { decrement, increment } from './counterSlice'

export function Counter() {
  const count = useSelector(state => state.counter.value) // ストアからデータを読み込む
  const dispatch = useDispatch()

  return (
    <div>
      <div>
        <button
          onClick={() => dispatch(increment())} // アクションをディスパッチ
        >
          Increment
        </button>
        <span>{count}</span>
        <button
          onClick={() => dispatch(decrement())} // アクションをディスパッチ
        >
          Decrement
        </button>
      </div>
    </div>
  )
}
```

基本的な Redux の書き方を見てきました。確かにこの後紹介するライブラリ達と比べると冗長に感じることもありますが、ルールが厳密である分アプリケーションが大規模になり開発者が増えるほど力を発揮すると思います。また、Redux を使用しない場合でも、Redux の誕生背景や設計仕様を学ぶことは開発者として成長するいい機会になるはずです。

最後に Redux に関する良記事もご紹介しておきます。

https://zenn.dev/suzuesa/articles/35ace7a7cd127f9a1d08

https://zenn.dev/kazuma1989/articles/68c2339e056530

## Recoil

https://recoiljs.org/

- Meta 社が開発
- Atom, Selector という基本概念
- Redux のように特定のアーキテクチャを強制されない
- Hooks のような API
- 状態定義は分散型であるためコード分割が可能
- [23.4kB](https://bundlephobia.com/package/recoil@0.7.6) (結構大きいな...)

Recoil は Redux の一強を打ち砕く筆頭候補だと思っています。Meta 社が開発していることもあり React との相性もいいです。React 開発者であればすぐに使うことができるでしょう。早速見ていきます。

Recoil のステートを使用するコンポーネントは、`RecoilRoot` で囲む必要があります。Redux や Context の Provider 相当です。

```js
import { RecoilRoot } from 'recoil';

function App() {
  return (
    <RecoilRoot>
      <Component />
    </RecoilRoot>
  );
}
```

基本概念の Atom を見ていきます。Recoil では Atom が データストアの役割を担っており、Atom は複数作成可能です。Atom を作成する際は `key` を指定する必要があります。これはグローバルでユニークにする必要があるのですが、どのように管理するのがベストなのでしょか。今回の例のように意味を持つ文字列で管理するべきなのか、UUID のようなものを使用するのか...。

```js
// Atom を作成
const fontSizeState = atom({
  key: 'fontSizeState',
  default: 14, // 初期値
});
```

コンポーネントから Atom のデータを読み取ってみます。

```jsx
function FontButton() {
  const [fontSize, setFontSize] = useRecoilState(fontSizeState);
  return (
    <button
      onClick={() => setFontSize((size) => size + 1)}
      style={{ fontSize }}
    >
      Click to Enlarge
    </button>
  );
}
```

`useRecoilState` の引数に Atom を渡すといった形ですね。返り値は Atom の値と、その値を更新するための関数です。まさに `useState` のグローバル版といった感じでとても使いやすい API になっています。Atom が更新されると、その Atom をサブスクライブしているコンポーネントが再レンダリングされます。

値の取得だけしたい場合は `useRecoilValue`、更新だけしたい場合は `useSetRecoilState` を使用します。

```js
const fontSize = useRecoilValue(fontSizeState);
const setFontSize = useSetRecoilState(fontSizeState);
```

続いてもう一つの基本概念である Selector を見ていきます。Selector は Atom や他の Selector を受け取り派生データを計算する純粋関数です。依存関係が変更されると再計算されます。Atom と同じくユニークな `key` が必要です。

```js
// Selector を作成
const fontSizeLabelState = selector({
  key: 'fontSizeLabelState',
  get: ({ get }) => {
    const fontSize = get(fontSizeState);
    const unit = 'px';

    return `${fontSize}${unit}`;
  },
});
```

初見でも何をしているか分かりやすいですね。Atom から値を取得し `px` という文字列を付け加えた値を返しています。今回は値を読み取っていますが書き込むことも可能です。

コンポーネントから Selector を使用してみます。`fontSizeLabelState` Selector は値を更新しないため、`useRecoilValue` を使用します。

```jsx
function FontButton() {
  const [fontSize, setFontSize] = useRecoilState(fontSizeState);
  const fontSizeLabel = useRecoilValue(fontSizeLabelState);

  return (
    <>
      <div>Current font size: {fontSizeLabel}</div>

      <button onClick={() => setFontSize(fontSize + 1)} style={{ fontSize }}>
        Click to Enlarge
      </button>
    </>
  );
}
```

Redux の中央集権制とすると Recoil は地方分権制とでも言えるでしょうか。つまり Redux ではステートが一箇所に集中するのに対し、Recoil は複数に分割することができます。「ある 2 つのコンポーネントでステートを共有したいけど位置関係的に Props のバケツリレーはつらい。でも Redux のストアに入れるほどでもない...。」といった場合でも、Recoil なら 2 つのコンポーネントでのみ使用される Atom を作成するだけなので、気軽にグローバルステートを作成することができます。また、Redux のように特定のアーキテクチャが決まっていません。１つの Atom にステートを詰め込めば Redux のようにも使えます。開発者にステートの分割方法やフォルダ構成、ロジックの置き場所などの決定権が大きく委ねられられているため実力の見せ所でしょう。

Redux と Recoil の詳しい違いについては [うひょさん](https://twitter.com/uhyo_) のブログが非常にわかりやすかったためご紹介させていただきます。

https://blog.uhy.ooo/entry/2021-07-24/react-state-management/

この記事を執筆中にうひょさんが Recoil に関するスライドを出されたのでそちらも紹介。

https://speakerdeck.com/uhyo/sutetoguan-li-wochao-erurecoilyun-yong-nokao-efang

## Zustand

https://github.com/pmndrs/zustand

- ドイツ語で「状態」という意味
- 公式マスコットのくまさんが可愛い 🧸
- Redux に近い
- Hooks のような API
- 日本人の [Daishi Kato さん](https://twitter.com/dai_shi)が開発している
- 超軽量
- [1.1kB](https://bundlephobia.com/package/zustand@4.3.1)

Zustand は [JavaScript Rising Stars](https://risingstars.js.org/2022/en#section-statemanagement) の状態管理部門で 2 年連続 1 位に輝いています。今回紹介するするライブラリの中で最も勢いがあると言っても過言ではないでしょう。

まずストアを作成します。`create` 関数を使用してストアを定義し、戻り値の Hook でステートの操作をおこないます。Redux と同じくステートは不変に更新する必要があります。ストアにはステートと、ステートを変更する Action が含まれます。RTK の Slice を簡素化した印象です。

```js
import { create } from 'zustand';

const useBearStore = create((set) => ({
  bears: 0, // ステート
  increasePopulation: () => set((state) => ({ bears: state.bears + 1 })), // Action
}));
```

注目すべき点は `set` 関数です。ステートは不変に更新する必要があるため、本来ならこのように記載する必要があるはずです。

```js
set((state) => ({ ...state, bears: state.bears + 1 }));
```

しかしこれは頻出パターンのため、実際には `set` は `state` をマージしており、`...state` の部分は省略できるようになっています。

```js
set((state) => ({ bears: state.bears + 1 }));
```

ただし、ネストされたオブジェクト場合は明治的にマージする必要があります。( [Immer](https://github.com/immerjs/immer) などを使用することでそのような問題にも対応できます。)

```js
import { create } from 'zustand';

const useCountStore = create((set) => ({
  nested: { count: 0 },
  inc: () =>
    set((state) => ({
      nested: {
        ...state.nested,
        count: state.nested.count + 1,
      },
    })),
}));
```

非同期 Action も簡単に書けます。

```js
const useFishStore = create((set) => ({
  fishies: {},
  fetch: async (pond) => {
    const response = await fetch(pond);
    set({ fishies: await response.json() });
  },
}));
```

コンポーネントからストアの値を読み書きしてみます。フックはどもからでも使用できるため、プロバイダーのようなものでラップする必要はありません。

```js
function BearCounter() {
  const bears = useBearStore((state) => state.bears);
  return <h1>{bears} around here ...</h1>;
}

function Controls() {
  const increasePopulation = useBearStore((state) => state.increasePopulation);
  return <button onClick={increasePopulation}>one up</button>;
}
```

今回は `create` 関数で定義したステートや 関数 (Action) を個別に取得していますが、全て取得することもできます。ただし無駄な再レンダリングが発生する可能性があるため、基本的にはコンポーネント内で使用しているステートのみ取得するようにします。考え方は Redux の Selector と同じですね。

```js
// 全て取得
const state = useBearStore();
```

基本的な部分しか触れてませんが、Redux と Recoil の中間のような印象を受けました。ストアは Redux に近いですが、ストアを読み書きする側は Recoil に近い気がします。Redux 思想のいいとこ取りをしつつ Hooks を使用して状態管理できる超軽量ライブラリということで注目を集めているのだと思います。脱 Redux の第一候補であることは間違いありません。まだ公式サイトがないため Github の [docs](https://github.com/pmndrs/zustand/tree/main/docs) を参考にすると良いでしょう。

## Jotai

https://jotai.org/

- Recoil インスパイア
- またまた [Daishi Kato さん](https://twitter.com/dai_shi)が開発
- [4.7kB](https://bundlephobia.com/package/jotai@1.13.0)

公式ドキュメントにはこのような記載があります。

> Jotai は Recoil にインスパイアされたアトムモデルで React の状態管理に **ボトムアップ** のアプローチをとっています。アトムを組み合わせることで状態を構築でき、アトムの依存関係に基づいてレンダリングが最適化されます。これにより、React Context の余分な再レンダリングの問題を解決し、メモ化技術の必要性を排除しています。

よく問題になる余分な再レンダリング問題を解決することが主目的のようです。`ボトムアップ` というの言葉が何を意味しているのかあまり理解できなかったのですが、こちらの記事が大変参考になりました。

https://zenn.dev/tell_y/articles/d714f9c16c1d3a

Github に記載されている Recoil との違いはこちらです。

- ミニマルな API
- Atom にユニークなキーを設定する必要がない
- TypeScript 指向 (Recoil の基本は Flow 指向？)

キーを設定する必要がないのは Recoil に対してかなり大きいアドバンテージだと思います。

まず Atom を作成します。`atom` の引数に初期値を渡します。複数作成可能です。

```js
import { atom } from 'jotai';

const countAtom = atom(0);
const countryAtom = atom('Japan');
const citiesAtom = atom(['Tokyo', 'Kyoto', 'Osaka']);
const mangaAtom = atom({
  'Dragon Ball': 1984,
  'One Piece': 1997,
  Naruto: 1999,
});
```

コンポーネントで Atom を使用します。プロバイダーのようなものでラップする必要はありません。Recoil 同様 `useState` と同じような API です。

```js
import { useAtom } from 'jotai';

function Counter() {
  const [count, setCount] = useAtom(countAtom);
  return (
    <>
      <p>{count}</p>
      <button onClick={() => setCount((c) => c + 1)}>one up</button>
    </>
  );
}
```

`atom()` は下記 3 種類の引数を取れます。1 は既に紹介したため、2 と 3 を見ていきます。

1. 初期値
2. read 関数
3. read 関数 + write 関数

read 関数を引数に渡す場合 Atom から新しい**読み取り専用の Atom** を作成することができます。Recoil の値を取得する Selector の役割に似ていますね。

```js
const countAtom = atom(1);
const doubledCountAtom = atom((get) => get(countAtom) * 2);

function DoubleCounter() {
  const [doubledCount] = useAtom(doubledCountAtom);
  return <h2>{doubledCount}</h2>;
}
```

複数の Atom から Atom を作成することもできます。

```js
const count1 = atom(1);
const count2 = atom(2);
const count3 = atom(3);

const sum = atom((get) => get(count1) + get(count2) + get(count3));
```

非同期 Atom

```js
const urlAtom = atom('https://json.host.com')
const fetchUrlAtom = atom(async (get) => {
  const response = await fetch(get(urlAtom))
  return await response.json()
})

function Status() {
  // 非同期処理が完了後再レンダリングされる
  const [json] = useAtom(fetchUrlAtom)
  ...
```

read 関数 + write 関数 を見ていきます。Atom から新しい**読み書き可能な Atom** を作成することができます。もし書き込み専用にしたい場合は read 関数に null を渡せば OK です。

```js
const countAtom = atom(0);
const addingCountAtom = atom(
  (get) => get(countAtom), // read 関数
  (get, set, num) => {
    // write 関数
    set(countAtom, get(countAtom) + num);
  }
);

function Counter() {
  const [count, add] = useAtom(addingCountAtom);
  return (
    <div>
      <div>{count}</div>
      <button onClick={() => add(Math.random())}>Add random number</button>
    </div>
  );
}
```

全てを Atom で完結させることができ、複雑なデータ構造も Atom を組み合わせることで柔軟に表現できそうだと感じました。既に記載しましたが、Recoil と異なり Atom にキーを設定する必要がないだけでも採用するメリットはありそうです。アプリケーションの規模が大きくなるにつれキーの管理が煩雑になるのは目に見えています。サイズの小ささを見ても Recoil を大きくリードしています。API も直感的で React 開発者あれば学習に必要な時間はほとんどないでしょう。

開発現場で「Jotai の状態どうなっている？」という会話がありそうななさそうな...笑

## Valtio

https://valtio.pmnd.rs/

- Proxy ベース
- JavaScript のオブジェクトをそのまま React の状態として使える
- Redux や Zustand とは異なり Mutable State Model
- またまたまた [Daishi Kato さん](https://twitter.com/dai_shi)が開発している
- [2.9kB](https://bundlephobia.com/package/valtio@1.8.2)

まず `proxy` を使用してストア(プロキシ)を作成します。

```js
import { proxy } from 'valtio';

const state = proxy({ count: 0, text: 'hello' });
```

プロキシは通常の JavaScript オブジェクトでありどこからでも変更可能です。これは Redux や Zustand と根本的に異なる点です。

```js
setInterval(() => {
  ++state.count;
}, 1000);
```

プロキシの変更をサブスクライブには `useSnapshot` を使用します。コンポーネントはアクセスしたステートが変更されたときのみ再レンダリングされるため、レンダリングが最適化されます。

```jsx
// `state.count` の変更時に再レンダリングされるが `state.text` の変更時にはされない
function Counter() {
  const snap = useSnapshot(state);
  return (
    <div>
      {snap.count}
      <button onClick={() => ++state.count}>+1</button>
    </div>
  );
}
```

コンポーネントの外側でもプロキシの変更をサブスクライブできます。

```js
import { subscribe } from 'valtio';

const state = proxy({
  obj: { foo: 'bar' },
  arr: ['hello'],
});

subscribe(state, () => console.log('state has changed to', state));

// 一部のステートのみサブスクライブも可能
subscribe(state.obj, () => console.log('state.obj has changed to', state.obj));
```

他のライブラリとは違ったアプローチで面白いですね。Mutable State と Immutable State の違いやプロキシを使用した状態管理の仕組みについては Daishi Kato さんが書かれた記事に詳しく書かれているためご紹介させていただきます。

https://blog.axlight.com/posts/how-valtio-proxy-state-works-vanilla-part/

https://blog.axlight.com/posts/how-valtio-proxy-state-works-react-part/

## Nano stores

https://github.com/nanostores/nanostores

- PostCSS や Autoprefixer のコアコントリビューターである [Andrey Sitnik さん](https://github.com/ai)が開発
- 依存性ゼロ
- React、React Native、Preact、Vue、Svelte、Vanilla JS に対応
- チャンクには、チャンク内のコンポーネントによって使用されるストアのみが含まれる
- ロジックをコンポーネントからストアに移動するように設計された
- [1.6kB](https://bundlephobia.com/package/nanostores@0.7.1)

Recoil、Jotai と同じく Atom 単位でステートを管理します。作成した Atom の `get()` `set()` メソッドを使用して読み書きを行います。

```js:store/users.ts
import { atom } from 'nanostores'

export const users = atom<User[]>([])

export function addUser(user: User) {
  users.set([...users.get(), user]);
}
```

`computed` で派生データを表現します。

```js:store/admins.ts
import { computed } from 'nanostores'

export const admins = computed(users, list =>
  list.filter(user => user.isAdmin)
)
```

複数のストアを組み合わせることも可能です。

```js
import { lastVisit } from './lastVisit.js';
import { posts } from './posts.js';

export const newPosts = computed([lastVisit, posts], (when, allPosts) => {
  return allPosts.filter((post) => post.publishedAt > when);
});
```

コンポーネントでは `useStore` を使用してストアから値を読み取ります。ストアの値が変更されると、コンポーネントは再レンダリングされます。

```js:components/admins.tsx
import { useStore } from '@nanostores/react'
import { admins } from '../stores/admins.js'

export const Admins = () => {
  const list = useStore(admins)
  return (
    <ul>
      {list.map(user => <UserItem user={user} />)}
    </ul>
  )
}
```

オブジェクトを管理したい場合は `map` を使用します。`atom` は使用できません。

```js
import { map } from 'nanostores';

export const profile = map({
  name: 'anonymous',
});

// 変更
profile.set({ name: 'Kazimir Malevich' });
profile.setKey('name', 'Kazimir Malevich');
```

map 関数の実装を見てみます。

```js:map/index.js
import { atom } from '../atom/index.js'

export let map = (value = {}) => {
  let store = atom(value)

  store.setKey = function (key, newValue) {
    if (typeof newValue === 'undefined') {
      if (key in store.value) {
        store.value = { ...store.value }
        delete store.value[key]
        store.notify(key)
      }
    } else if (store.value[key] !== newValue) {
      store.value = {
        ...store.value,
        [key]: newValue
      }
      store.notify(key)
    }
  }

  return store
}
```

とてもシンプルですね。状態管理ライブラリの内部実装を勉強する第一歩として適しているかもしれません。

`action` 関数を使用してストアを変更することもできます。バリデーションやネットワーク操作などのビジネスロジックを動かすのに適しています。

```js
import { action } from 'nanostores';

export const increase = action(
  counter, // ストア
  'increase', // action 名
  (store, add) => {
    if (validateMax(store.get() + add)) {
      store.set(store.get() + add);
    }
    return store.get();
  }
);

increase(1); //=> 1
increase(5); //=> 6
```

基本的には Recoil や Jotai と同じような印象を受けました。今回は紹介しきれませんが、LocalStorage の操作、SPA ルーター、翻訳を可能にする I18n ライブラリなど公式が提供しているツールもあります。

## Hookstate

https://hookstate.js.org/

- Hooks をベースにした状態管理
- プラグインシステム
- [6.1kB](https://bundlephobia.com/package/@hookstate/core@4.0.0)

ステートは `hookstate` 関数を使用して作成します。コンポーネントの外部でステートの値を取得、更新できます。コンポーネント内部でステートを使用する場合は `useHookstate` を使用します。ステートの値には `get` `set` メソッドを通してアクセスします。

```jsx
import { hookstate, useHookstate } from '@hookstate/core';

// ステートの作成
const globalState = hookstate(0);

// コンポーネントの外部
setInterval(() => globalState.set((p) => p + 1), 3000);

const ExampleComponent = () => {
  // コンポーネントの内部
  const state = useHookstate(globalState);
  return (
    <>
      <p>Counter value: {state.get()}</p>
      <button onClick={() => state.set((p) => p + 1)}>Increment</button>
    </>
  );
};
```

React 組み込みの `useState` の代わりに `useHookstate` を使用することもできます。

```jsx
import { useHookstate } from '@hookstate/core';

export const ExampleComponent = () => {
  const state = useHookstate(0);
  return (
    <>
      <b>Counter value: {state.get()} </b>
      <button onClick={() => state.set((p) => p + 1)}>Increment</button>
    </>
  );
};
```

`useHookstate` の使い方を詳しく見ていきます。

```ts
const state = useHookstate({ a: 1, b: 2 });

// 更新
state.set({ a: 2, b: 3 });
state.set((p) => ({ a: p.a + 1, b: p.b - 1 }));

// 一部のみ更新 (プロパティ a が使用されている全てのコンポーネントを再レンダリング)
state.a.set((p) => p + 1);
state['a'].set((p) => p + 1);
state.merge((p) => ({ a: p.a + 1 }));

// プロパティ名を取得
const keys = state.keys; //  ['a', 'b']

// プロパティを追加
const state = useHookstate<{ a: number; b?: number }>({
  a: 1,
});
state.b.set(2);
state['b'].set(2);
state.merge({ b: 2 });

// プロパティを削除
import { none } from '@hookstate/core';
state.b.set(none);
state['b'].set(none);
state.merge({ b: none });
```

Hookstate の公式サイトにはこのように書かれています。

> Incredible performance based on unique method for tracking of used/rendered and updated state segments. Ideal solution for huge states and very frequent updates.

ドキュメントにも [パフォーマンス専用のセクション](https://hookstate.js.org/docs/performance-intro)があったりと、スピードにかなり自信を持っていることがわかります。[このページ](https://hookstate.js.org/docs/performance-large-state)には Hookstate で管理された 5000 個のフォームがありますが、確かにチラつきを感じることはありません。今回パフォーマンスの計測までは行いませんが、他のライブラリと比較してみるのも面白そうです。

## Elf

https://ngneat.github.io/elf/

- RxJS 上に構築
- 複数ストアを作成可能で、必要なものだけバンドルされる
- ページネーションをビルトインサポート
- [2kB](https://bundlephobia.com/package/@ngneat/elf@2.3.0)

[Akita](https://opensource.salesforce.com/akita/) という状態管理ライブラリが前身のようです。

RxJS やリアクティブプログラミングという言葉の意味については、[奥野 賢太郎](https://twitter.com/okunokentaro?s=20&t=Jsp0QAMuu_DMo6QJ36g54Q) さんが書かれた記事がわかりやすいためおすすめです。

https://www.codegrid.net/articles/2017-rxjs-1/

`createStore` 関数でストアを作成します。

```ts
import { createStore, withProps } from '@ngneat/elf';

interface AuthProps {
  user: { id: string } | null;
}

const authStore = createStore(
  { name: 'auth' }, // ストア名
  withProps < AuthProps > { user: null }
);
```

`select` 関数を使用してストアからスライスを選択できます。

```js
import { select } from '@ngneat/elf';

const user$ = authStore.pipe(select((state) => state.user));
```

`updade` 関数を使用してストアを更新します。

```js
authStore.update((state) => ({
  ...state,
  user: { id: 'foo' },
}));
```

Elf の重要な機能の一つである Entities を簡単に紹介します。この機能により、ストアはエンティティストアとして動作するようになります。

エンティティストアを作成します。

```ts
import { createStore } from '@ngneat/elf';
import { withEntities } from '@ngneat/elf-entities';

interface Todo {
  id: number;
  label: string;
}

const todosStore = createStore({ name: 'todos' }, withEntities<Todo>());
```

これにより、ミューテーションとクエリを使用できるようになります。いくつかみていきましょう。

```js
// ストアのエンティティコレクション全体を選択
import { selectAllEntities } from '@ngneat/elf-entities';
const todos$ = todosStore.pipe(selectAllEntities());

// ストアから複数のエンティティを選択
import { selectMany } from '@ngneat/elf-entities';
const todos$ = todosStore.pipe(selectMany([id, id]));
const titles$ = todosStore.pipe(selectMany(id, { pluck: 'title' }));

// ストアから最初のエンティティを選択
import { selectFirst } from '@ngneat/elf-entities';
const first$ = todosStore.pipe(selectFirst());

// ストアのエンティティコレクションのサイズを選択
import { selectEntitiesCount } from '@ngneat/elf-entities';
const count$ = todosStore.pipe(selectEntitiesCount());
```

今回は Query 系を紹介しましたが、Mutation もライブラリが用意している便利は関数が多くあります。ORM を使用しているようで面白いです。公式ドキュメントにも紹介がありますが、リポジトリパターンと相性が良さそうですね。

## Rematch

https://rematchjs.org/

- 軽量 Redux
- Redux のボイラープレートを削減
- プラグインシステム
- [1.7kB](https://bundlephobia.com/package/@rematch/core@2.2.0)

まずモデルを定義します。モデルはステート、Reducer、非同期 Action を一つにまとめたものです。

```js
export const count = {
  state: 0, // 初期値
  reducers: {
    // 純粋関数での処理
    increment(state, payload) {
      return state + payload;
    },
  },
  effects: (dispatch) => ({
    // 純粋関数でない場合の処理
    async incrementAsync(payload, rootState) {
      await new Promise((resolve) => setTimeout(resolve, 1000));
      dispatch.count.increment(payload);
    },
  }),
};
```

ただの JavaScript オブジェクトですね。これだと型がつかなそうですが、TypeScript も 100% サポートされています。ヘルパーメソッド `createModel` を使用してモデルを作成します。

```ts:./models/count.ts
import { createModel } from '@rematch/core';
import { RootModel } from '.';

export const count = createModel<RootModel>()({
  state: 0,
  reducers: {
    increment(state, payload: number) {
      return state + payload;
    },
  },
  effects: (dispatch) => ({
    async incrementAsync(payload: number, state) {
      await new Promise((resolve) =>
        setTimeout(resolve, 1000)
      );
      dispatch.count.increment(payload);
    },
  }),
});
```

```ts:./models/index.ts
import { Models } from "@rematch/core";
import { count } from "./count";

export interface RootModel extends Models<RootModel> {
  count: typeof count;
}

export const models: RootModel = { count };
```

ストアの初期化をします。

```js
import { init } from '@rematch/core';
import * as models from './models';

const store = init({ models });

export default store;
```

Action を Dispatch してモデル内の Reducer や Effect をトリガーします。`dispatch[model][action](payload)` というショートハンドを使うこともできます。

```js
const { dispatch } = store;
// state = { count: 0 }
// reducers
dispatch({ type: 'count/increment', payload: 1 }); // state = { count: 1 }
dispatch.count.increment(1); // state = { count: 2 }

// effects
dispatch({ type: 'count/incrementAsync', payload: 1 }); // state = { count: 3 } after delay
dispatch.count.incrementAsync(1); // state = { count: 4 } after delay
```

`react-redux` を使用し、コンポーネントからモデルを操作してみます。

```jsx
import { Provider, connect } from 'react-redux';
import store from './store';

const Count = (props) => (
  <div>
    The count is {props.count}
    <button onClick={props.increment}>increment</button>
    <button onClick={props.incrementAsync}>incrementAsync</button>
  </div>
);

const mapState = (state) => ({
  count: state.count,
});

const mapDispatch = (dispatch) => ({
  increment: () => dispatch.count.increment(1),
  incrementAsync: () => dispatch.count.incrementAsync(1),
});

const CountContainer = connect(mapState, mapDispatch)(Count);

ReactDOM.render(
  <Provider store={store}>
    <CountContainer />
  </Provider>,
  document.getElementById('root')
);
```

公式が提供しているプラグインがいくつかあるため、今回は Immer プラグインを見てみます。Redux Toolkit と同じような使われ方で、Reducer をラップしステートの更新処理を書きやすくします。プラグインの設定はストア作成時に行います。

```ts
import immerPlugin from '@rematch/immer';
import { init } from '@rematch/core';
import { models, RootModel } from './models';

export const store = init<RootModel>({
  models,
  plugins: [immerPlugin()], // 追加
});
```

```ts
import { createModel } from '@rematch/core';
import { RootModel } from './models';

export const todo = createModel<RootModel>()({
  state: [
    {
      todo: 'Learn typescript',
      done: true,
    },
  ],
  reducers: {
    done(state) {
      // 見た目上はミュータブル更新ができる
      state.push({ todo: 'Tweet about it', done: false });
      state[1].done = true;
    },
  },
});
```

Redux Toolkit も Rematch も実務で使用した経験はないため何とも言えませんが、Redux を使用したい場合 Redux Toolkit で充分なのでは？と感じました。Rematch の最も大きいアドバンテージはサイズの小ささでしょう。Rematch の 1.7kB に対して、Redux Toolkit は 13.5kB あります。最近はバンドルサイズを小さくすることに焦点が当てられる機会が多いので、Rematch でも要件を満たせる場合は積極的に採用してもいいかもしれません。

## まとめ

甲乙つけがたいですが個人的には Jotai が優勝でした。とてもシンプル・軽量であり、設計は開発者の実力に大きく委ねられているところが好きです。(何より日本人の方が開発しているので応援したくなります)

ただ全ての要件に対応できるライブラリというのは基本的に存在しません。アプリケーションの規模や、メンバーの状況によって採用すべきものは変わってきます。それぞれの特徴を把握した上で適切に技術選定できる力が必要です。

普段は React 標準の Context や Apollo を使用する機会が多いため、今後は今回記載したライブラリも積極的に使用していきたいです。また、SWR や React Query と組み合わせた場合についても深ぼっていけたらなと思います。

最後までお読みいただきありがとうございました 🙇‍♂️
