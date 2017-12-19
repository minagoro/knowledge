# Milter

## 概要

- MTA で処理されるメールに外部プログラムがアクセスするためのコンセプト。
- Sendmail 由来だが、Postfix を始めとする複数の MTA でサポートされている。
- C のリファレンス実装として libmilter が提供されている。
  - libmilter は sendmail のパッケージに含まれている。

## コミュニティ

- milter.org が 2015 年に閉鎖。
  - Milter アプリケーションのレジストリ機能も含んでいた。

## 用語

- Milter
  - 広義の意味として Milter Application, Milter Protocol, Milter API のいずれの表現にも使われる。
- Milter Application
  - MTA で処理されるメールにアクセスするアプリのこと。
- Milter Protocol
  - Milter アプリが MTA との通信に使うプロトコルのこと。
- Milter API
  - Sendmail のドキュメント上で言及されていて、libmilter を指していると思われる。

## ドキュメント

- sendmail パッケージ内の libmilter/docs をブラウザで開く。
  - 公式にホスティングされているところはない。
  - 非公式かつ若干古いものであれば[ここ](http://www.elandsys.com/resources/sendmail/libmilter/)。
- ソースビルド方法、テスト手順などは libmilter/README にまとめられている。
- Milter を適用する MTA 側のドキュメントも参考にすべき。
  - （例）Postfix ドキュメントでの言及箇所: [Postfix before-queue Milter support](http://www.postfix.org/MILTER_README.html)
