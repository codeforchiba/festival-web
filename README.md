# festival-web

[Code for Chiba](http://code4chiba.org) のお祭りデータセンターの Web フロントエンドです。

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

ローカル環境にnode.jsをインストールして開発環境を作ります。

### 開発ツールのインストール

- [node](https://nodejs.org/en/)のインストール

**（nodeが既にインストールされている場合はスキップ可）**

※注　macの場合nodeが/usr/local下にインストールされると権限の問題でnpmコマンドが失敗します。
インストール先を変更するか、権限を与えるようにしてください。

- [AWS CLI のインストールと設定](http://docs.aws.amazon.com/ja_jp/streams/latest/dev/kinesis-tutorial-cli-installation.html)
**（デプロイ時に必要な設定）**

### 開発環境準備

- npmとgruntをアップデートする。

```
$ npm install -g npm
$ npm install -g grunt-cli
```

- ソースをチェックアウトし、プロジェクトのディレクトリに移動します。

```
$ git clone https://github.com/codeforchiba/feschibal.git
$ cd feschibal
```

### 開発環境で実行する
#### 1. 必要なモジュールのセットアップ

プロジェクトのディレクトリ直下で実行してください。
```
$ npm install
```

#### 2. ビルド

サーバに設置するためのファイルをdist配下に生成します。

オプションを指定しないと`config/default.yml`を使ってbuildします。

##### ステージング

`config/staging.yml`を使ってbuildします。
```
$ grunt build:staging
```

##### 本番

`config/production.yml`を使ってbuildします。
```
$ grunt build:production
```

#### 3. 環境変数

nodeの環境変数を、process.env.<環境変数>で取得しています。  
必要な環境変数を開発環境に設定してください。

#### 4. デプロイ

grunt-aws-s3プラグインにより、AWSへデプロイされます。  
AWS Access Key ID,AWS Secret Access Keyは、  
[AWS CLI のインストールと設定](http://docs.aws.amazon.com/ja_jp/streams/latest/dev/kinesis-tutorial-cli-installation.html)で設定したCredentialを参照します。
```
$ grunt upload-s3
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
