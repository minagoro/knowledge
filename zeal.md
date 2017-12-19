# Zeal

## 概要

- Dash ライクなドキュメントブラウザ。
- Dash の docset リポジトリを利用する。
- 対応 OS は Linux, Windows。
- オープンソースで無償提供されている。

## Dash との違い

- Dash は MacOS に対応しているが、Zeal は Linux, Windows に対応。
- Zeal はオープンソース開発されている。
- Zeal は無償提供されていて、ライセンス購入による機能追加等もない。
- Zeal は主要パッケージマネージャに登録されていてインストールが簡単。
- Dash と違って、複数バージョンの docset 管理に対応していない。(※1)
- Dash と違って、スニペット管理機能がない。
- 地味に docset の追加が UI 的に不便。
- サードパーティのドキュメントソースに対応していない。(※2)
  - ※1: フィード URL 直打ちで過去のバージョンの追加は可能。複数バージョンの共存ができるかは不明。
  - ※2: フィード URL 直打ちで個別の docset 追加は可能。

## ソースビルド手順 (CentOS 7)

Zeal は YUM の主要リポジトリに登録されていないので、CentOS 環境ではソースビルドが必要。

1. 依存パッケージをインストールする。
   ```
   yum install -y epel-release
   yum install -y cmake3 extra-cmake-modules qt5-qtwebkit-devel libarchive-devel xcb-util-keysyms-devel
   ```
2. cmake で Makefile を生成して、make でビルドする。
   ```
   $ mkdir build
   $ cd build
   $ cmake ..
   // 依存パッケージがなくてエラーになることが大半なので、
   // その場合はパッケージ名をエスパーして yum install する。
   $ make
   ```
3. 実行すると、GUI が立ち上がる。
   ```
   $ bin/zeal
   ```


## 資料

- [Zeal - Offline Documentation Browser](https://zealdocs.org/)
