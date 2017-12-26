# VPN

## VPN とは

- Virtual Private Network の略。
- （物理的にではなく）論理的に構成した閉域網のこと。
- 一般に企業が通信の秘匿性を確保するために利用する。

## VPN の歴史

### 専用線（1900年頃〜）

- インターネットとは別の専用端末／回線を利用したイーサネット接続。
- 閉域イーサネットとも呼ばれる。
- これによって構成されたネットワークを閉域網とよぶ。
- メリット：秘匿性が完全に保証される。
- デメリット：高価な上、距離に依存して費用は高くなる。
- デメリット：ハブ＆スポーク型の構成により、耐障害性が低い。

### IP-VPN（2000年頃〜）

- 1つの回線を共用することで低価格化を実現する。
- 各通信事業者がそれぞれ共用の専用線を管理する。
- L3 レベルで VPN を構成するので、サポートするのは IP のみ。
- メリット：距離に依存しない料金体系で提供される。
- メリット：フラットなネットワーク構成が実現可能で、耐障害性が高い。
- デメリット：帯域は保証されない。（ただし、一般に安定している。）
- デメリット：IP 以外の通信に利用できない。

### 広域イーサネット（2000年頃〜）

- L2 レベルで VPN を構成することで、マルチプロトコルを実現する。
- メリット：IP-VPN と比べて高速で安価。（スイッチだけで構築できるため）
- メリット：IP 以外の通信も利用できる。

### インターネット VPN（2010年頃〜）

- インターネット網を利用して VPN を構築する技術。
- インターネット網に接続した VPN 機器を利用して、VPN トンネルを構成する。
- 技術自体ははるか昔からあったが、ブロードバンド回線の普及により実用レベルとなった。
- 小規模拠点はインターネット VPN で済ませる、バックアップ回線としての利用も増えている。
- メリット：圧倒的に安価。
- デメリット：秘匿性は利用する暗号化の強度に依存する。
- デメリット：帯域は利用するインターネット網に依存する。

## 資料

- [企業ネットワーク（VPN）基礎講座 | フリービット法人向けICTサービス](http://biz.freebit.com/service/column/vpnbasic00.html)
  - VPN 技術の変遷を追う形式をとっていて、説明がわかりやすい。