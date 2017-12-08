# git-worktree

## 概要

- 同じローカルリポジトリ紐づいた複数の作業ディレクトリを管理するツール。
  - 通常、一つのローカルリポジトリ (.git) に対応する作業ディレクトリは一つだけ。
  - 二つ目（以降）の作業ディレクトリの作成および管理を行うためのコマンドを提供する。
- 作業ツリー ≒ 作業ディレクトリ。
  - 作業ツリーというのは、git-worktree が作業ディレクトリを扱う単位。
  - 実際に作業ディレクトリが消えていても作業ツリーは残っている。

## ユースケース

- ひとつの作業ディレクトリをひとつのブランチに対応づけて管理できる。

## メリット／デメリット

- C/C++ のプロジェクトでブランチを変えるたびに再コンパイルが走らなくて楽。
- git-stash よりシンプルに作業中の状態を残せる。
- git-worktree を使っていることを忘れて作業するなどした結果、作業ツリーの状態がよくわからなくなってくる。
- IDE の中間情報など git 管理されていないファイルは共有されないので、作業ディレクトリごとに再生成が必要になる。

## ベストプラクティス

### ディレクトリ構成

- ひとつの作業ディレクトリをひとつのブランチに対応づけて考える。

### 始め方

1. git clone する。
   ```
   git clone https://github.com/msh5/knowledge
   ```
2. （checkout されているのは master ブランチなので）master というサブディレクトリに移動する。
   ```
   mkdir knowledge.tmp
   mv knowledge knowledge.tmp/master
   mv knowledge.tmp knowledge
   ```

### 使い方

- 新しい作業ディレクトリを作成する。
  ```
  rootdir="$(git worktree list | grep master | awk '{print $1}')/.."
  branch="develop"
  git worktree add "${rootdir}/${branch}" ${branch}
  ```
  - origin/* を指定した場合に自動でブランチを作成するといったことはやってくれないので、
    git branch で作成してから実行すること。

## 資料

- [Git - git-worktree Documentation](https://git-scm.com/docs/git-worktree)


