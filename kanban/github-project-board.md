# GitHub の Project Board 機能

## Project Board 機能とは？

- GitHub の提供するカンバン方式のタスク管理機能。
- 各カンバンボードはプロジェクト単位もしくは Organization 単位で管理する。
- Issue 機能と統合されていて、各カードはひとつの Issue と対応する。
  - タスクの詳細やメンバとのコミュニケーションは Issue の Description や Comment を利用する。
- キャパシティに基づく制限の機能は、いまのところ実装されていない。
- 隠し機能として（？）TODO 管理機能は実装されている。
  - Issue の Description に Task List 記法を記入すると、カードに n/m という表示と進捗バー的な表示が現れる。
    これらの表示は Task List のチェック率にあわせて更新される。

## 使ってみた感想

- 使い慣れた Issue 機能との統合が使いやすい。
- 一方で、Issues がタスクの登録で占有されてしまい不具合報告の場としては使えなくなるので、
  カンバン用に独立したプロジェクトを用意した方が良いかもしれない。
- GitHub 通巻のシンプルな UI は Projct Board 機能でも健在、使いやすく気の利いたデザイン。
- 忠実なカンバンではなく、シンプルにタスクの可視化を実現するための機能であると推測できる。
  - 細かい機能やモバイル未対応な点など、作り込みの点では専業の他社サービスに劣る。

