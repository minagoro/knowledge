# DMARC

## 概要

### DMARC とは？

- RFC 7489 で規定されているプロトコル。
  - Domain-based Message Authentication,Reporting and Conformance の略。
- **送信元ドメイン認証に失敗したときのハンドリング方法を公開する**ための取り決め。
  - SPF と DKIM を認証方式として想定。
  - ドメインオーナが**ポリシー**として DNS 上で公開する。
- これに加え、**認証結果のフィードバック**に関しても取り決められている。
  - メール受信サーバが**レポート**としてドメインオーナにメール送信する。
  - レポートは詐称メールに対する防衛状況の観察と向上に利用される。
- *DMARKと typo しないこと。* 👻

### 参考になるサイト

- [dmarc.org – Domain Message Authentication Reporting & Conformance](https://dmarc.org/)
  - DMARC のポータルサイト。
  - *DMARC の概要に関してわかりやすく説明されていてる。（とりまココ読め*
- [RFC 7489 - Domain-based Message Authentication, Reporting, and Conformance (DMARC)](https://tools.ietf.org/html/rfc7489)
  - DMARC の RFC。
- [Domain-based Message Authentication, Reporting & Conformance (dmarc)](https://datatracker.ietf.org/wg/dmarc/about/)
  - DMARC のワーキンググループ。
  - ML や Issue Tracker も運営。

## ポリシーの公開

### ポリシーとは？

- **メール受信サーバが送信ドメイン認証できないメールをどう扱うかを示したもの。**
- ドメインオーナによって公開され、メール受信サーバによって適用される。
- ドメインオーナはポリシー（とそれに付随する情報）を **DNS 上で公開する**。
- *ドメインオーナが認証に失敗したときのハンドリング方法を推奨できる。*
- *ドメインとしてメールセキュリティに対する意識レベルをアピールできる。

### DMARC レコード

#### 概要

- **`_dmarc` サブドメインの DNS TXT レコードとして公開する。**

  - 公開状況の確認：```dig txt _dmarc.<ドメイン名>```

- ポリシー情報をフォーマットに従ってテキスト化する。 

  ```
  "v=DMARC1;p=reject;pct=100;rua=mailto:postmaster@dmarcdomain.com"
  ```

  - key と value を = で区切ってセミコロンでつなげる。
  - 参考： [6.3 General Record Format (RFC 7489)](https://tools.ietf.org/html/rfc7489#section-6.3)

- *"none" から始めて、状況を観察しつつ徐々に制限をきつくしていくと良い。*

- *現状、"none" で様子を見ているメール事業者が多い。*

#### レコード内容

- **ドメイン／サブドメインのポリシー**
  - **指定しない（none）、隔離（quarantine）、拒否（reject）のいずれかを指定。**
- ポリシーを適用するメールの率
  - デフォルトは 100
- **失敗／集計レポートの送信先（URL）**
  - 複数指定も可能。
- 失敗レポートの形式／オプション
- 集計レポートの送信間隔

## 認証結果のフィードバック

### DMARC フィードバック

- 認証結果や受信時に実施された処理はドメインオーナに通知される。

- DMARC レコードに基づいて**メール受信サーバが送信する。**

- **集計レポート(aggregate report)**と**失敗レポート (failure report) **との2種類がある。

- *ドメインオーナは送信メールの認証状況を把握できる。*

- *（ポリシーを none でもいいので）DMARC レコードを書いておけば、*

  *DMARC 対応の受信サーバからレポートが届く。*

### 集計レポート

#### 概要

- **一定期間の**認証結果や実施したメッセージ処理をまとめたもの。
- **（少なくとも）1日1回送信する。**
  - レポート本体は XML 形式で記述する。
  - GZIP 圧縮して添付ファイルとして送信する。
  - 参考：[Appendix C.  DMARC XML Schema (RFC 7489)](https://tools.ietf.org/html/rfc7489#appendix-C)
- 送信に失敗する場合、エラーレポートを送信する。
  - DSN 形式のテキストメール。
  - 参考：[7.2.2 Error Reports (RFC 7489)](https://tools.ietf.org/html/rfc7489#section-7.2.2)

#### レポート内容

- **DMARC レコードから得られたポリシー**
- **実施したメッセージ処理**
- **SPF および DKIM の判定結果**
- 成功したメッセージ数
- 全メッセージ数

### 失敗レポート

#### 概要

- フォレンジックレポートとも呼ばれる。
  - forensic [fərénsik]：法医学の, 鑑識の
- **認証に失敗した場合に即時送信する。**
  - どの検証 (SPF / DKIM) を対象とするかは DMARC レコードで指定する。
- 集計レポートより詳しい情報を掲載する。
  - AFRF (Abuse Failure Reporting Format) を一部拡張した形式。
  - AFRF は [RFC 6591](https://tools.ietf.org/html/rfc6591) で定められている。
- 認証の失敗が**異常終了な場合にも送信される**。
  - *SPF / DKIM レコードの記述や署名方法に問題があるかも。*😎

#### レポート内容

- **失敗した認証方式（SPF / DKIM）**
- **SPF / DKIM の認証情報**
- 配送結果

## 付録

### A. iij.ad.jp の DMARC レコード問い合わせ結果

```
$ dig txt _dmarc.iij.ad.jp

; <<>> DiG 9.9.7-P3 <<>> txt _dmarc.iij.ad.jp
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 55552
;; flags: qr rd ra ad; QUERY: 1, ANSWER: 1, AUTHORITY: 2, ADDITIONAL: 5

;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 4096
;; QUESTION SECTION:
;_dmarc.iij.ad.jp.		IN	TXT

;; ANSWER SECTION:
_dmarc.iij.ad.jp.	3600	IN	TXT	"v=DMARC1; p=none; adkim=s; aspf=s; rua=mailto:dmarc-rua@iij.ad.jp; ruf=mailto:dmarc-ruf@iij.ad.jp"

;; AUTHORITY SECTION:
iij.ad.jp.		2448	IN	NS	dns0.iij.ad.jp.
iij.ad.jp.		2448	IN	NS	dns1.iij.ad.jp.

;; ADDITIONAL SECTION:
dns0.iij.ad.jp.		507	IN	A	210.130.0.5
dns0.iij.ad.jp.		507	IN	AAAA	2001:240::105
dns1.iij.ad.jp.		3442	IN	A	210.130.1.5
dns1.iij.ad.jp.		3442	IN	AAAA	2001:240::115

;; Query time: 12 msec
;; SERVER: 10.131.16.20#53(10.131.16.20)
;; WHEN: Sun Jan 28 14:39:07 JST 2018
;; MSG SIZE  rcvd: 281
```

<!--（テキスト装飾について）強調：重要そうなところ、斜体：個人的な意見と注釈-->

<!--（未調査項目）DMARC の実装、DMARC の運用事例、DMARC レポートの解析サービス-->

