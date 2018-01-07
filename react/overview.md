# React

## React とは？

- [React - A JavaScript library for building user interfaces](https://reactjs.org/)
- Facebook 製のフロントエンド開発ライブラリ。
- コンポーネントベース。（Vue.js と同じ）
- JSX が推されていて、JavaScript と比べて見通しよく実装できる。

## React のコンセプト

- コンポーネントと呼ばれる単位で、ステート毎にビューを設計する。
- コンポーネントを組み合わせることで、サイト全体の UI を構成する。
- ステートに変更があったコンポーネントだけを再描画することで、効率的に動作する。

## ライブラリのインタフェイス

- コンポーネントは React.Component の派生クラスとして実装する。
- 派生クラスには render メソッドを実装し、構成した HTML を戻り値として返す。
- ステートは React.Component クラスの state 変数として表される。
- state 変数の値が変更するごとに render メソッドが呼ばれてページが書き換わる。

## アプリの開発フロー

- ツールを使ってプロジェクトを作成する。
  - [facebookincubator/create-react-app: Create React apps with no build configuration.](https://github.com/facebookincubator/create-react-app)
  - webpack や Babel といったレイヤは隠蔽されている。
- ホットリロードに対応しているので、ファイルを変更すると自動でリロードされる。

## スタイルガイド

- [Airbnb React/JSX Style Guide](https://github.com/airbnb/javascript/tree/master/react)

