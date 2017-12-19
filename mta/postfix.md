# Postfix

## Postfix とは

- メールサーバ。
- 現 Google の [Wietse Venema さん](http://www.porcupine.org/wietse/) が IBM 研究所時代に開発。
- Sendmail の代替として開発された。
- スループットと管理のしやすさに重点が置かれている。

## 資料

- [The Postfix Home Page](http://www.postfix.org)
- リポジトリは公開されてなさそう。

## インストール

- ソースビルドの方法はドキュメントが用意されている。
  - [Postfix Installation From Source Code](http://www.postfix.org/INSTALL.html)
  - 必須なので、postfix ユーザ／グループ と postdrop グループ を作っておく。
- sendmail との競合に気をつける。
  - alternative --config mta で切り替えればいいだけ？
  - sendmail をアンインストールしてしまえれば何も考えなくて済むが、
    sendmail に依存する他のアプリがあるので簡単にはできないはず。

## 機能（Milter のサポート）

- Postfix 2.3 以降で対応している。
- MTA はメールをキューに積む前に Milter アプリを呼び出す。
  - Milter アプリが通したもののみキューに積まれる。
- 2種類のフィルタリストを持つ。
  - SMTP-only と non-SMTP の2つ。
- SMTP-only は smtpd 経由で受け取ったものを処理する。
  - 迷惑メールのフィルタリングや認証に使われる。
  - SMTP-only Milter アプリは smtpd_milters というキーワードを用いて指定する。
- non-SMTP は sendmail コマンド経由、もしくは qmqpd 経由で受け取ったものを処理する。
  - smtpd_milters というキーワードを用いて指定する。

## 機能（ポリシーの定義）

### ポリシーとは

- 受け取ったメールを許可するかブロックするかを決めるルールを指している。

### 定義する手段

- アクセスポリシーデリゲート機能を利用すべし。
  - [Postfix SMTP Access Policy Delegation](http://www.postfix.org/SMTPD_POLICY_README.html)
  - ポリシーの実装を外部サーバ（ポリシーサーバ）に移譲する機能。
  - Postfix 2.1 以降で対応している。
  - ルールの定義をポリシーサーバとして実装すればよい。
    - サーバには各メールのメタ情報が渡される。
    - 各メールのメタ情報を元にした判定処理を実装する。

### ポリシーサーバの実装

- 実装の簡便さから、スクリプト言語での実装が推奨されている。
  - プログラムは複数の SMTP コネクションで使い回されるため、  
    スクリプト言語特有の起動時のオーバーヘッドはボトルネックになりづらい。
  - 使い回される最大回数は $max_use の定義値に基づく。
- サーバに渡されるメールのメタ情報を元に、判定処理を実装する。
- どういったメタ情報が渡されるかは、プロトコルの規定を参照する。

## アーキテクチャ

- TODO
