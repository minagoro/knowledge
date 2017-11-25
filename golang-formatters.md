# Go 言語のコード整形ツール

## コード整形とは ?

- コードの中のスタイル違反（もしくはシンタックス違反）の部分を機械的に修正する機能。
- コード整形するツールは、一般にフォーマッタと呼ばれる。
  - linter はスタイル違反を指摘してくれるだけ、フォーマッタはスタイル違反を直してくれる。
  - 指摘の内容によっては自動整形が難しいこともあるので、一般に linter ツールと比べてバリエーションは少ない。

## Go 言語のフォーマッタ事情

- gofmt, goimports, goreturns の3つがメジャー。
  - Atom, VSCode の Go 言語機能でもネイティブでサポートされている。
- goimports, goreturns は開発作業を効率化するためのツール。
  - エディタのフック機能を利用して編集中に自動実行されることを想定している。

### gofmt

- [gofmt - The Go Programming Language](https://golang.org/cmd/gofmt/)
- go コマンドにバンドルされているツール。
- Go 言語で推奨されるコーディングスタイルに合わせて、コードを自動整形する。

### goimports

- [goimports - GoDoc](https://godoc.org/golang.org/x/tools/cmd/goimports)
- Go の開発チームによって拡張ツールという位置付けで提供されている。
- gofmt を拡張したもの。
- スタイルチェックに加えて import の整理機能を実装したもの。
  - 足りない import を検出して、機械的に追加する。  
    このために GOPATH 以下にインストールされているライブラリを探索する。
  - 不要な import を見つけて、機械的に削除する。

### goreturns

- [sqs/goreturns: A gofmt/goimports-like tool for Go programmers that fills in Go return statements with zero values to match the func return types](https://github.com/sqs/goreturns)
- Source Graph 社の [Quinn Slack さん](https://github.com/sqs)による開発。
  - Source Graph は Go の Language Server の実装に Contribute している会社。
- goimports を拡張したもの。
- スタイルチェックと import の整理に加えて、return 文の補完機能を実装したもの。
  - 関数の宣言から戻り値に足りていない値を検出して、return 文の修正を行う。
  - 値としては nil と 0 が追加される。
  -（挙動を見ると）return 文自体が実装されていない時点では何も行わない。

## どのフォーマッタを採用すべきか

- プロジェクトとしては gofmt を採用しておけば良い。
  - スタイルの統一は gofmt の機能までで実現される。
- goimports, goreturns は個人レベルで採用するもの。
  - 開発作業が捗るので、エディタへの導入を推奨する。
  - goreturns の機能はやや too much か。
