# Vagrant のオペレーション

## ホストの構築

### 基本コマンド

```shell
ls .Vagrantfile # カレントディレクトリに Vagrantfile が存在することを確認
vagrant up [ホスト名]
```

### Provider を指定する

```shell
vagrant up [ホスト名] --provider=libvirt	# Vagrantfile の中で指定した方が安全。
```

### デバッグ出力を確認する

```shell
vagrant up [ホスト名] --debug
```

## 構築状況を確認

### 基本コマンド

```shell
ls .Vagrantfile
vagrant status 		# ホストの作成状況と動作状況がわかる。
virsh list --all	# ちなみに、プラットフォームのコマンドをみても同じ。（むしろわかりやすかったりする。）
```

### ユーザグローバルに確認

```shell
vagrant global-status
```

## ホストへのリモートアクセス

### SSH でアクセス

```shell
vagrant ssh [ホスト名]
```

### SSH のアクセス情報を確認

```shell
vagrant ssh-config [ホスト名]
```

### RDP でアクセス

```shell
vagrant rdp [ホスト名]
```

### PowerShell でアクセス

```shell
vagrant powershell [ホスト名]
```

## ホストを止める

### ホストを一時停止する

```shell
vagrant suspend [ホスト名]	# ホストの再開は `vagrant resume [ホスト名]`。
```

### ホストを安全に停止する

```shell
vagrant halt [ホスト名]
```

### ホストを強制停止する

```shell
vagrant halt --force [ホスト名]
```

### ホストを強制停止&削除する

```
vagrant destroy [ホスト名]
```

## ベストプラクティス

### コマンド名を短縮する

```shell
alias vag=vagrant
```

### サブコマンドを短縮する

```shell
alias vagrant=_vagrant
_vagrant() {
		...
        if test "x$1" = "xbox"; then
                if test "x$2" = "xls"; then
                        \vagrant box list
                else
                        \vagrant $@
                fi
        elif test "x$1" = "xst"; then
                \vagrant status
        elif test "x$1" = "xprov"; then
                \vagrant provision $2
        else
                \vagrant $@
        fi
		...
}
```

### 停止用サブコマンドを定義する

```shell
alias vagrant=_vagrant
_vagrant() {
		...
		if test "x$1" = "xshutdown"; then
                \vagrant halt $2
        elif test "x$1" = "xstop"; then
                \vagrant halt --force $2
        else
                \vagrant $@
        fi
		...
}
```

