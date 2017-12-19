# Visual Studio Code に関するナレッジ

作成: 2017年10月10日 最終更新: 2017年10月10日

_最近はもっぱら Atom を常用しているが、環境構築がいつまで経っても落ち着かない。
今後のトレンドは Atom IDE かと思って Laguage Server の検証に取り組んでいたこともあって、
その起源である Visual Studio Code の検証に着手した。
結果的には食わず嫌いではもったいなほどよく出来たエディタで、
もともと乗り換えを検討していたという程のモチベーションさえない状態で検証を始めたが、
今後 Visual Studio Code は私にとってファーストチョイスのエディタになるだろう。_

## VSCode の概要

[Visual Studio Code - Code Editing. Redefined](https://code.visualstudio.com/)

- Microsoft 製のエディタ
- 略して VSCode と記載されることが多い
- Electron を GUI バックエンドとしているところから Atom と比較されることが多い
- Windows, Linux, MacOS をサポート
  - Windows ユーザにとってはファーストチョイスか
- デフォルトのサポート言語は JavaScript, TypeScript, Node.js
  - Web 開発を意識したエディタであることを感じる
  - Visual Studio との差別化?
- マーケットプレースから任意のエクステンションを追加することで機能を追加できる
- ナイトリービルド版は VS Code Insiders と呼ばれる
  - https://code.visualstudio.com/insiders

## VSCode の使用感

- Visual Studio　っぽさから、一瞬ながら禁断症状を感じた
  - 結論からいうとデザインだけなので大した問題ではない
- Atom より軽快
  - もっさり感がない、検索も速い
- Atom と違って機能が揃っていてすぐ使える
  - デバッガ、ミニマップ、アプリ内端末エミュレータもデフォルト
  - より IDE を意識した作り、フリーソフトウェアに見えない
  - Linux デスクトップでもフォントのレンダリングに問題なし
- アプリ設定の変更の仕方がおもしろい
  - 愚直な 設定ファイル書き換えと GUI によるポチポチのハイブリッド

## 設定のポイント

- 使用状況、クラッシュレポートの送信をオフにする
  - 必要に応じて自動更新も
- プロキシ設定を忘れない
- 戻ると進むのキーバインドがわかりにくいので、再設定したほうがいい気がする

## 付録A. settings.json の例

```json
{
    "telemetry.enableTelemetry": false,
    "telemetry.enableCrashReporter": false,
    "window.restoreWindows": "all",
    "editor.renderWhitespace": "all",
    "editor.wordWrap": "bounded",
    "editor.rulers": [
        80
    ],
    "editor.smoothScrolling": true,
    "editor.minimap.showSlider": "always",
    "workbench.startupEditor": "none",
    "editor.minimap.renderCharacters": false,
    "editor.cursorBlinking": "blink",
    "editor.mouseWheelZoom": true,
    "editor.renderControlCharacters": true,
    "editor.renderLineHighlight": "line",
    "editor.folding": false,
    "workbench.editor.labelFormat": "medium",
    "workbench.fontAliasing": "default",
    "workbench.editor.swipeToNavigate": true,
    "workbench.tips.enabled": false,
    "workbench.colorTheme": "Default Light+",
    "files.autoGuessEncoding": true,
    "files.trimTrailingWhitespace": true,
    "files.trimFinalNewlines": true
}
```
