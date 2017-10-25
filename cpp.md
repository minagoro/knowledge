# C++ のナレッジ

## 言語の概要

- C にクラスを始めとした多くの機能を追加した言語。
- Standard C++ Foundation によって規格化が進められている。
  - https://isocpp.org/

## ドキュメント

- 仕様は購入しないと見れない。
  - 研究者やコンパイラ実装者を対象としたものなので、一般技術者はみる必要ないとされている。  
    https://isocpp.org/std/the-standard
  - ドラフトは無償公開されている。
- C++11/14 の仕様については、江添さんの書かれた書籍が詳しい。
  - http://ezoeryou.github.io/cpp-book/C++11-Syntax-and-Feature.xhtml
- メジャーなリファレンスサイトを利用するのが現実的。
  - http://en.cppreference.com/w/
- Effective C++ は必読とされていて、言語を使う上での落とし穴がまとめられている。

## Tips など
- 文字でない文字を使うなど、コードポイントで文字を指定した場合は、[ユニバーサル文字名](http://ezoeryou.github.io/cpp-book/C++11-Syntax-and-Feature.xhtml#universal-character-name) を使うとよい。
  ```
  "\u007f" // DELETE 制御文字
  ```
