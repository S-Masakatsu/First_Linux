# zshのインストールと設定

## １. zshがインストールされているか確認

``` shell
$ zsh --version
```

## ２. yumでzshをインストール

``` shell
sudo yum -y install zsh
```

## ■ zshの起動とログイン・シェルの設定

### １. 現在使用しているshellの確認

``` shell
$ echo $SHELL
```

### ２. 使用可能なshellの確認

``` shell
$ cat /etc/shells
```

### ３. ログイン・シェルに設定

``` shell
chsh -s /bin/zsh
```

<a href="../../README.md#ttl3-2">戻る</a>
