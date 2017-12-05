# festival-web

[Code for Chiba](http://www.code4chiba.org) のお祭りデータセンターの Web フロントエンドです。

## 使用ライブラリ

主に以下のライブラリを使用して作られています。

- jquery
- bootstrap
- leaflet
- riotjs

## 開発ツール

本プロジェクトでは開発ツールとしてGruntを使用しています。
Gruntが担うタスクは以下の機能になります。

- scssのコンパイル
- tagファイルのコンパイル
- 開発用httpサーバの起動
- リリース用モジュール（ソース圧縮、結合等）の生成

## ローカル環境で開発する

ローカル環境にNode.jsをインストールして開発環境を作ります。

### 開発ツールのインストール

* [Node.js](https://nodejs.org/en/)

**（Node.jsが既にインストールされている場合はスキップ可）**

※注　macの場合nodeが/usr/local下にインストールされると権限の問題でnpmコマンドが失敗します。
インストール先を変更するか、権限を与えるようにしてください。

### 開発環境準備

- npmとgruntをアップデートする。

```
$ npm install -g npm
$ npm install -g grunt-cli
```

- ソースをチェックアウトし、プロジェクトのディレクトリに移動します。

```
$ git clone https://github.com/codeforchiba/festival-web.git
$ cd festival-web
```

### 開発環境で実行する
#### 必要なモジュールのセットアップ

プロジェクトのディレクトリ直下で実行してください。
```
$ npm install
```

その後、Gruntタスクを実行すると、開発環境で実行することができます。

```
$ grunt serve
```

### ビルドする

サーバに設置するためのファイルを `dist` 配下に生成します。

`target` オプションを指定しないと`config/default.yml`を使ってビルドします。

#### ステージング環境向け

`config/staging.yml`を使ってbuildします。

```
$ grunt build --target=staging
```

#### 本番環境向け

`config/production.yml`を使ってbuildします。

```
$ grunt build --target=production
```

### デプロイ

AWS S3へのデプロイを想定した作りとなっています。必要な環境変数を設定して、実行します。

* AWS_ACCESS_KEY_ID
* AWS_SECRET_ACCESS_KEY
* AWS_BUCKET
* AWS_REGION(Optional)

```
$ grunt deploy
```

## ディレクトリ構造

### app

アプリケーションソースの配置場所

### .tmp

Gruntによって自動生成されたファイル（css, js）が配置される場所。
scssから生成されたcssファイル。tagファイルから生成されたjsファイルが配置されています。
ソースのコミット対象外としています。

### dist

"grunt build" で生成された本番用モジュールが配置されます。
ソースのコミット対象外としています。

### node_modules

開発ツールであるGruntに関連するファイルが配置されています。
"npm install" をすることで必要なモジュールがこのディレクトリの下に配置されます。
ソースのコミット対象外としています。

## ライセンス

MIT
