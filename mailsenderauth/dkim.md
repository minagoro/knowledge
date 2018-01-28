# DKIM

## 概要

- 送信元ドメイン認証の方式のひとつ。
- Domainkeys Identified Mail の略。
- 送信元ドメインの検証に加えてメール本文の改竄検知にも対応する。
- SPF と違ってメールが途中で異なる MTA を中継されても検証が可能。

## 仕組み

- 送信者は秘密鍵と公開鍵を用意し、公開鍵はDNS サーバ上で公開する。

- 送信者はメール送信時に、署名を作成し秘密鍵で暗号化する。

- 暗号化した署名は、DKIM-Signature ヘッダとして当該メールに追記する。

  ```
  DKIM-Signature: v=1; a=rsa-sha256; c=simple/simple; d=example.jp;
                    s=dkimjp20101115; t=1308471652;
                    bh=KF7zwHMa9ToPtsGy8urMTpCLCfTnzrcJ6mxHnrWCffQ=;
                    h=To:Sender:MIME-Version:Subject:From:Content-Type:
                     Content-Transfer-Encoding:Message-Id:Date;
                    b=xdIeG4cUHIBhU0nix2V5tK9ZN7QwnKd+qYuFamqtZpon2EfsKfSwdGhSHvU6fRj3z
                    dp6tVjGpT64hx4eayxKcnjHTYMq8yRVgEPp9naNrCD7SIX70P6LvrbFpMZc85Exxpx
                    FZdETOXsumsY7pt6tpP9puwjN3/5EsYuwWM63AUY=
  ```

- 受信者はメール受信時に、公開鍵を使って署名を検証する。

- 検証結果は、Authentication-Results ヘッダとして当該メールに追記する。

  ```
  Authentication-Results: example.com;
      sender-id=pass header.from=example.jp;
      dkim=pass (good signature) header.i=@example.jp
  ```

  ​

