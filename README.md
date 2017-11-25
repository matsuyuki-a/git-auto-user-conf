git-auto-user-conf
==================

コンピュータの同じユーザで, リポジトリごとに異なる `.gitconfig` のuser設定を使用したい場合に便利なシェルスクリプトです. ホームディレクトリに配置した設定ファイルの通りの `[user]` 設定を 1コマンドでリポジトリに適用できます.

## 準備
1. 何らかの方法で `git-auto-user-conf` に PATH を通します.
2. ホームディレクトリに ファイル `お好きな名前.gitconfig` を作成します. 複数作成することもできます.
3. ファイルの内容は, 下記の内容とします. `.gitconfig` の`[user]` の部分だけ. `=` の右側は設定したい値に変更してください.

```
[user]
  name = Example Name
  email = example@example.com
```

## 使用方法
1. 端末上で, gitリポジトリの一番上のディレクトリ (直下に `.git` ディレクトリがあるところ)に移動します.
2. `git-auto-user-conf お好きな名前` で ホームディレクトリ下にある `お好きな名前.gitconfig` の設定を使用します.
3. 完了

例えば, ホームディレクトリ下の `example.gitconfig` に書かれているユーザ設定をリポジトリで使用したい場合には, gitリポジトリの一番上のディレクトリで

``` sh
$ git-auto-user-conf example
``` 
を実行します.

リポジトリ内の設定で既に `[user]` による設定があったり, コマンドを実行したディレクトリの直下に `.git` ディレクトリが無かったりすると失敗します.

## 便利な使い方
`git config --global user.useConfigOnly true` により, グローバルのユーザ設定がない場合にコミットを失敗させることができます. この設定がない場合, 環境変数の値を使用してコミットしてしまうのですが, この設定をすることにより `git-auto-user-conf` を実行し忘れた時に, 環境変数の値でコミットされる事故を防ぐことができます.

## ライセンス
CC0

