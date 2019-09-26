# ソフトウェアのインストールとアップデート

ここではLinuxでのソフトウェアのインストールとアップデートについて紹介します。

## ■ ソフトウェアのインストール

Linuxではパッケージ単位でソフトウェアを管理します。パッケージには種類がありますがLinuxではRPMというパッケージを採用している。  
RPMを採用しているディストリビューションにはcentOSのほか、Red Hat Enterprise、Fedora、openSUSEなどがあるが、基本的には他のディストリビューションのRPMパッケージは利用できないと考えて良い。(依存関係の問題)  
RPMを管理するには`rpm` コマンドを使うのだが、管理するには骨が折れるので、centOSでは`yum` コマンドを使う。(centOS8では`dnf`)  
`yum` を使うことによりインターネット経由でソフトウェアをインストールしたりアップデートしたりすることができる。

## ■ ソフトウェアのアップデート

ソフトウェアは日々更新されます。機能追加、バグ修正、重要なセキュリティアップデートもある。  
YUMをつかってインストールしたソフトウェアは、`yum` を使って一括してアップデートができる。

- 書式  
    `yum [-y] update`

詳しくは下記、外部ページを参照してください。

- [yumコマンドの使い方](https://www.atmarkit.co.jp/ait/articles/1608/29/news019.html)

## ■ OSの自動アップデート

`yum` コマンドを使ったアップデートは手動による操作が必要です。アップデートは日々ある中、その度`yum` を実行するのは面倒くさいです。  
Linuxでは、crontabという仕組みを使って、タスクを定期的・自動的に実行させる事ができます。YUMを使ったシステムアップデートを自動で処理するには、**yum-cron**パッケージをインストールします。

1. yum-cronパッケージのインストール

    ``` shell
    $ sudo yum -y install yum-cron
    ```

1. 設定ファイルの編集

    ``` shell
    $ sudo vi /etc/yum/yum-cron.conf
    ```

    20行目の設定が「no」になっているのでそこを「yes」にする。

    ``` shell
    apply_updates = yes
    ```

1. 起動し、自動的に起動するようにする

    ``` shell
    $ sudo systemctl start yum-cron.service
    $ sudo systemctl enable yum-cron.service
    ```

アップデートするパッケージによっては、今まで動いていたアプリケーションが動かなくなる場合もあるのでアップデートをセキュリティアップデートに限定したい場合は、yum-cron.confファイル内で、「update_cmd = default」を「security」もしくは「minimal-security」にする。

``` shell
update_cmd = securty
# もしくは
update_cmd = minimal-security
```

<a href="../../README.md">戻る➡︎</a>
