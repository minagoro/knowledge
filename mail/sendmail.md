# Sendmail

## 概要

- UNIX で伝統的なオープンソースの MTA ソフトウェア。
- Eric Allman によって 30 年以上前に開発された。
  - [[Preface] History](https://www.cs.ait.ac.th/~on/O/oreilly/tcpip/sendmail/prf1_02.htm)
- Sendmail 社は 2013年に Proofpoint に買収された。
  - [Proofpoint, Inc. Acquires Sendmail, Inc. (NASDAQ:PFPT)](https://github.com/avar/sendmail-pmilter/blob/master/doc/milter-protocol.txt)
- [Sendmail Consortium のサイト](www.sendmail.org) も既に閉鎖されている。
- ftp.sendmail.org に何も置かれていないような。
  - ミラーサイトには tarball 等ぞろぞろあるので、そちらにアクセスすべし。

## 機能

### sm-client

- ホスト内からのメール送信を処理するためのもの。

## 設定ファイル

### 基本情報

- mc ファイルと cf ファイルがある。
  - mc: macro config の略。
  - cf: config の略。
- mc ファイルを make すると cf ファイルが生成される。
  ```
  $ cd /etc/mail
  $ sudo make
  // まだ sendmail サーバには適用されていない。
  ```
- 変更は mc ファイルに対して行う、cf ファイルは編集するべからず。
- ```make restart``` で現在の設定をサーバに適用する。
  ```
  $ sudo make restart
  ```

### よくある設定変更

- ループバックアドレス以外からの送信を受け付けるには、  
  ```/etc/mail/sendmail.mc``` で指定されている接続 IP アドレスの制限を外せばよい。
  ```
  dnl DAEMON_OPTIONS(`Port=smtp,Addr=127.0.0.1, Name=MTA')dnl
  DAEMON_OPTIONS(`Port=smtp, Name=MTA')dnl
  ```
- メールを受け取るホスト名（基本的には自ホストの名前のはず）を指定するには、  
  ```/etc/mail/local-host-names``` に受け取るホスト名を記入すればよい。
