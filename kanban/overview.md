# カンバンの概要

## カンバンとは？

- アジャイルソフトウェア開発手法のひとつ。
- David J. Anderson によってまとめられた手法で、原典は「[カンバン:　ソフトウェア開発の変革](https://www.amazon.co.jp/dp/B00O8GIJ1E)」。
- 英語でも "Kanban" 。
- 作業中のタスクを可視化することで、開発チームがタスクを受け入れすぎないようにするための手法。
  - ただし一般的には、単にチーム内のタスクを可視化するための手法として知られている。
  - 可視化には「カンバンボード」が用いられる。

## カンバンボードとは？

- カードウォール、タスクボードなどとも呼ばれる。
- 各カードはチーム内のタスクに対応する。
  - タスクの詳細まで小さいカードに書きれないので、細かい内容は別で管理する必要がある。
- 各カードはいずれかのステージに配置される。
  - どのようなステージを用意するかは、管理者がチームの開発フローにあわせて決める。
  - 各カードには見込み工数、各ステージにはキャパシティを設定する。
  - ステージ内のカードの合計工数が、そのステージのキャパシティを超えてはいけない。

## カンバンボードのシンプルな運用例

1. プロジェクトの作業フェイズ単位で新しいボードを用意する。

2. Icebox, Backlog, In Progress, Done の4つのステージを用意する。

3. 新規タスクはすべて Icebox に配置する。

4. 管理者は Icebox 内のカードに担当者とマイルストーンを割り当てて、カードを Backlog に移動する。

5. 開発者は作業の着手とともに、カードを In Progress に移動する。

6. 開発者は作業の完了とともに、カードを Done に移動する。

7. フェイズの終わりに振り返りを行い、ベロシティの算定とキャパシティの見直しを行う。  

   ちなみに、ベロシティとは時間あたりの平均処理工数のこと。

## カンバン方式を採用したチーム開発ツール

| サービス名                                    | 運営会社      | 所感                                       |
| ---------------------------------------- | --------- | ---------------------------------------- |
| [ZenHub](https://www.zenhub.com/)        | ZenHub    | ブラウザのアドオンとして機能する異色なサービス。GitHub との連携を打ち出してる。 |
| [Pivotal Tracker](https://www.pivotaltracker.com/) | Pivotal   | 非常に多機能で、カンバンに忠実なタスク管理が実現可能。              |
| [Jira](https://www.atlassian.com/software/jira) | Atlassian | エンタープライズ向け。BTS に統合されている。                 |
| [Trello](www.trello.com/)                | Atlassian | カジュアルな Jira。シンプルで使いやすい。Todo アプリとして取り上げられることも多い。類似サービスの中ではかなり人気が高い。 |
| GitHub の Project Board                   | GitHub    | 一番シンプルで良いが、若干機能が足りない。使い慣れた Issues 機能との連携は非常に使いやすい。モバイルに未対応。 |

