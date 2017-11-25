# Bats

## Bats とは

- [sstephenson/bats: Bash Automated Testing System](https://github.com/sstephenson/bats)
- Bash ベースのテストフレームワーク。
- Basecamp 社の [Sam Stephenson さん](https://github.com/sstephenson)による開発。
- 2011 年に初回リリース。

## Bats の特徴

- _Bash スクリプトとしてテストが書ける。_
- _[TAP](tap.md) 互換の標準出力に対応している。_

## インストール方法

- README ではソースインストールが案内されている。
  ```
  $ git clone https://github.com/sstephenson/bats.git
  $ cd bats
  $ ./install.sh /usr/local
  ```
- オフィシャルな方法かはわからないが、YUM や Homebrew でもパッケージ管理されている。

## テストの書き方

- テストを実装したファイルを Bats テストファイルと呼ぶ。
- テストファイルには ```bats``` という拡張子を用いる。
- テストファイルには、一つのテストを一つの関数として実装する。
  ```
  @test "addition using bc" {
    result="$(echo 2+2 | bc)"
    [ "$result" -eq 4 ]
  }
  ```
- テストファイルの実体は Bash スクリプト。
  - ```set -e``` で実行してるだけ。
  - アサーションは Bash の条件判定式を使って行う。
- setup 関数、teardown 関数を定義していると、Bats が各テストの実行前後で呼び出す。
  - 一般にこれらの関数はテストの準備と後片付けに利用される。
- Bats はいくつかのユーティリティ関数を提供している。
  - ```run``` 関数: コマンドを実行して、終了ステータスと標準出力をそれぞれ既定の変数（$status と $output もしくは $lines）に受け取る。

## テストフレームワークとしての機能

- テストの実行には ```bats``` コマンドを用いる。
- ```bats``` コマンドは、テストファイルのパスを指定して実行する。
  - 実行するとテストファイルに定義されているテストが（全て）実行される。
  ```
  $ bats addition.bats
  ✓ addition using bc
  ✓ addition using dc

  2 tests, 0 failures
  ```
  - テストファイルのshebang に ```#!/user/bin/env bats``` と書いておいても良い。
  - 複数のテストファイルや、テストファイルを含むディレクトリのパスを指定しても良い。

## 所感

- フレームワークとしてのレイヤが薄く Bash の透過性が高いため、Bash の知見だけでテストの作成がすぐに始められるし、Bats を知らないメンバーもテストの内容を理解できる。
- シェルプログラミングのデメリットとして大規模な開発が苦手という点が挙げられるが、テストなのでそもそもコードサイズが大きくなることがない（はず）。
- テストファイルの拡張子が .bats であることから、エディタ（というか VSCode）がデフォルトの設定では Bash スクリプトとして認識できず、コード補完やシンタックスハイライトがなされない。
