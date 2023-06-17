# reactjs-and-nextjs-bigenner

> 書籍「React.js & Next.js 超入門」を読んだときのメモです

### Reactとは
* Webの開発にJavaScriptが注目されるようになったのは、フロントエンドの実装が複雑になりReactなどのJavaScriptフレームワークが普及したことが理由である。またバックエンドでもNode.jsというJavaScriptの実行環境が使用され始めたというのも理由のひとつかもしれない。
* ReactはFacebookによって開発されたオープンソースのフロントエンドフレームワークです。
* Reactの特徴は「リアクティブ・プログラミング」。リアクティブとは、何かの値の変更がすぐに反映される仕組みのこと。値がどのように伝わっていくかを重視している。
* Reactを使用するときに、全部手作業でファイルを作るというのは非効率なので、一般的に必要なものが一式揃っているプロジェクトを使用することが多い。
* JavaScriptのパッケージを管理するときは「npm」というプログラムを使用します。（「JavaScriptのパッケージ」というのは、既に準備されているオブジェクトのコードという認識で大丈夫。オブジェクトというのは何かしらの機能を持っているソースコードだと思ってください。）
* npmというプログラムはNode.jsというプログラムに取り込まれている。そのため、JavaScriptでプログラミングするなら、とりあえずNode.jsを入れておけと考えてもいい。
* Reactの基本的な考え方は「表示を更新したければ、またエレメントを作ってレンダリングし直せばいい」ということ

<br>

### Node.jsとは
* 上記でも軽く説明したように、JavaScriptでサーバープログラムの開発を行うのに多様されているJavaScriptの実行環境を「Node.js」という。
* Node.jsに利用されているパッケージ管理ソフト「npm」を使い、さまざまなJavaScriptのソフトウェアのインストールなどを行っている。Reactの開発を行うためのソフトウェアも、これを利用して用意するようになっている。
*

<br>

### Reactの開発
* Reactのアプリケーションを作成するには以下のプログラムを使う
```sh
npx create-react-app project-name

# 例
npx create-react-app react-app

# npmを使っても同じことができますが書き方が異なる
npm init react-app project-name
```
* `creact-react-app`コマンドを実行すると以下のテキストが表示される。これはプロジェクトを操作するときのコマンドである。
```sh
npx create-react-app react_app
#一部省略
  npm start
    Starts the development server.

  npm run build
    Bundles the app into static files for production.

  npm test
    Starts the test runner.

  npm run eject
    Removes this tool and copies build dependencies, configuration files
    and scripts into the app directory. If you do this, you can’t go back!

We suggest that you begin by typing:

  cd react_app
  npm start

Happy hacking!
```
上記のテキストでは、`npm`コマンドの表記しかないが`yarn`コマンドでの実行コマンドについても以下に記載する。`yarn`については次項で説明する。
>`npm start` または `yarn start`
> * 開発用のサーバープログラムを使用してプロジェクトを実行する。
> * ローカルでWebブラウザでアクセスし、動作を確認できる。

>`npm run build` または `yarn build`
>   * プロジェクトのビルド（プロジェクトのファイル群から実装にWebサーバーにアップロードして利用するファイル類を生成）を行う

>`npm test` または `yarn test`
>   * テストプログラムを実行し、アプリケーションのテストを行う。

>`npm run eject` または `yarn eject`
>   * プロジェクトのイジェクトを行う。
>   * イジェクトとは、プロジェクトのさまざまな依存関係をすべてプロジェクト内に移動し、完全に独立した形で扱えるようにする作業。
>   * 初心者のうちは使わないかも...。

<br>

### ちょろっと登場した npx ってなに？
`yarn`については次で説明するとして、ちょろっと登場した `npx` ってなに？と思うかもしれないが、これも `npm` と同じパッケージ管理ツールである。パッケージのダウンロードと実行を一括して行う「より便利になったnpm」という認識で大丈夫。

<br>

### yarnとは？
* `yarn` は `npm` と同じパッケージ管理ツール
* `npm` は `Node.js` をインストールすると一緒にインストールされるプログラムであるが、 `yarn` は、`npm`、`homebrew`、`MacPorts`でインストールする必要がある
* `yarn` はFacebookが開発するソフト（ReactもFacebookが開発したフレームワーク...）
>`yarn` の強み
>   * `npm` と比べてパッケージのインストールが速い
>   * `npm` と比べてセキュリティが高い。インストール時にパッケージが不正に変更されていないかなどをチェックサムを用いて検証することができるため、安全なパッケージのインストールが可能である
>   * パッケージ管理も優れている。インストール後に `yarn.lock` というファイルが作成される。これはインストールしたプログラムが使用している別のプログラムのバージョンが明記されている。つまりパッケージ間の依存関係について明記された `yarn.lock` というファイルが生成される。

<br>

### プロジェクトの中身
create-react-appで作成されたプロジェクトの中身を確認すると以下の通りです。
```sh
~/reactjs_and_nextjs/react_app
$ tree -L 1
.
├── README.md
├── build
├── node_modules
├── package-lock.json
├── package.json
├── public
└── src
```
それぞれざっくり役割を確認します
* `node_modules`：npmで管理されるモジュール類がまとめたある。直接編集することはまずない。
* `public`：公開フォルダ。HTMLやCSSなど公開されるファルイ類が保管される。
* `src`：Reactで作成したファイルなどがまとめられる。編集したファイルが置くのはここ。
* `.gitignore`：Gitで使うgitで管理したくないディレクトリやファイルを設定するファイル。
* `package.json`；npmでパッケージ管理するための設定情報ファイル。
* `README.md`：言わずもがなのREADMEファイルです。ドキュメント管理は大切ですのでプロジェクトについてしっかり書きましょう。
* （`yarn.lock`：yarnでパッケージ管理している場合に作成される。yarnに関する設定情報を記述したファイル。）





