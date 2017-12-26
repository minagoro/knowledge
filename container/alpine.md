# Alpine

## Alpine とは

- [index | Alpine Linux](https://alpinelinux.org/)
- Linux ディストリビューションの一つ。
  - 読み方は「アルパイン」。
- セキュリティ面の重視とサイズの小ささを特徴としている。
  - Alpine の Docker イメージは 4.5 MB !
  - Docker のオフィシャルイメージとして採用されつつある !
    - [Docker 社の CTO が非公式ながら Hacker News で名言した。](https://news.ycombinator.com/item?id=11000827)

## Alpine の詳細

- [musl libc](http://www.musl-libc.org/) を採用。
- [BusyBox](https://busybox.net/) と呼ばれるユーティリティツールセットを採用。
  - 機能的には GNU coreutils に相対するもの。
- APK と呼ばれるパッケージ管理システムを採用。

## 参考

- [Dockerやる前のAlpine Linux - YoshinoriN's Memento](https://yoshinorin.net/2016/10/01/alpine-linux/)
