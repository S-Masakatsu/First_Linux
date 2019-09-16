# 初めてのLinux

## ■ 環境

- Mac
    - MacOS Mojave Ver.10.14.6

## ■ VirtualBoxの利用

### ● VirtualBoxのダウンロード

[Download Virtualbox](https://www.virtualbox.org/wiki/Downloads)  
こちらから最新版のダウンロードを行う。

### ● CentOSのダウンロード

下記からダウンロードを行う。  
よくわからなければ`最新版`(一番上)をダウンロードする。  
[公式：Download CentOS 7](http://isoredirect.centos.org/centos/7/isos/x86_64/CentOS-7-x86_64-Minimal-1810.iso)

<h2 id="ttl2"> ■ CentOS 7をVisualBoxでインストールする</h2>

インストール方法は下記を参照

- <a href="./Install/centos/README.md">CentOS 7のインストール</a>

## ■ シェルとコマンド

Linuxではコマンド操作基本です。コマンドの実態はプログラムです。  
コマンドを実行するソフトウェアを**シェル**という。  
もっとも広く使われているのがbashである。  
centOSでもbashが標準シェルで使われている。

<img src="./images/index/index01.png">

### ● シェルの種類

|シェル|説明|
|---|---|
|sh|Bourneシェル。UNIX系OSで古くから使われているシンプルなシェル。機能は少ない。|
|bash|Bourneシェルを大幅に改良したシェル。多くのディストリビューションで標準となっている。|
|csh|BSD系UNIXで使われてきたシェル。sh系とはスクリプトが異なっている。|
|tcsh|cshを改良したシェル。|
|ksh|Bourneシェルを拡張したシェル。|
|ash|shの代替となる、小型かつ高速なシェル。|
|dash|Debian版のash。スクリプトの実行が高速な軽量シェル。|
|zsh|kshにbashやtcshの機能を取り入れた非常に強力なシェル。|

<h3 id="ttl3-2"> ● zshのインストール・設定</h3>

インストール方法は下記から

- <a href="/Install/zsh/README.md">zshのインストールと設定</a>

<h3 id="ttl3-3"> ● 基本的なコマンド</h3>

下記ページでは基本的なコマンド操作を紹介。  
詳しくは下記から。

- <a href="/BasicCommands/README.md">基本的なコマンド</a>
