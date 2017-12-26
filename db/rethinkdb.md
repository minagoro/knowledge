# RethinkDB

## 概要

- ドキュメント指向データベース。
- C++ でスクラッチされている。
- [RethinkDB 社が倒産して、オープンソースプロダクトになった。](https:// yakst.com/ja/posts/4416)。

## リソース

- [RethinkDB: the open-source database for the realtime web](https://www.rethinkdb.com/)

## 機能

- 管理 UI がデフォルトで実装されている。
- ReQL という独自のクエリ言語を使う。
- 数値型が double オンリー。

## インストール（サーバ）

- オフィシャルな Docker イメージがあるのでコマンド一発。
  ```
  docker run -d -P --name rethink1 rethinkdb
  ```
  - ポートがマッピングされて違う値になっているので注意。
- http://localhost:8080 を開くと管理 UI が確認できる。

## インストール（Node クライアント）

- こちらもコマンド一発。
  ```
  npm install rethinkdb
  ```
- チュートリアルのサンプルプログラムを実装する。  
  非常に直感的に書けるという印象。
  ```
  r = require('rethinkdb')
  r.connect({host: 'localhost', port: 32769}, function(err, conn) {
    if (err) throw err;
    r.db('test').tableCreate('tv_shows').run(conn, function(err, res) {
      if (err) throw err;
      console.log(res);
      r.table('tv_shows').insert({name: 'Star Trek TNG'}).run(conn, function(err, res) {
        if (err) throw err;
        console.log(res);
      });
    })
  });
  ```
- 実行する。
  ```
  # node main.js 
  { config_changes: [ { new_val: [Object], old_val: null } ],
    tables_created: 1 }
  { deleted: 0,
    errors: 0,
    generated_keys: [ '82396844-4924-460d-9c1e-edec77aa7ea6' ],
    inserted: 1,
    replaced: 0,
    skipped: 0,
    unchanged: 0 }
  ```
