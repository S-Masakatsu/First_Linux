# CentOS 7のインストール

## ■ 事前準備

- VirtualBoxのダウンロード
- CentOSのダウンロード

## １. VM作成

1. 新規作成をする  
    名前を`CentOS`にするとタイプとバージョンを自動設定してくれる。

    <img src="../images/install/install01.png">

1. メモリーサイズの指定  

    <img src="../images/install/install02.png">

1. 仮想ハードディスクを作成するを選択する

    <img src="../images/install/install03.png">

1. VDIを選択する

    <img src="../images/install/install04.png">

1. 固定サイズを選択する

    <img src="../images/install/install05.png">

1. ファイルの場所とサイズはそのままにする

    <img src="../images/install/install06.png">

1. 作成すれば終了

## ２. ホストオンリーネットワークの設定

macからssh接続できるように、ホストオンリーネットワークというのを指定する必要がある。

1. VirtualBoxのメニューバー → ファイル → ホストネットワークマネージャーを選択

    <img src="../images/install/install07.png">

1. アダプターを手動で設定にチェックを付け、IPv4アドレスを`192.168.56.1`にする

    <img src="../images/install/install08.png">

1. VMの設定 → ネットワーク → アダプター1にブリッジアダプターを設定する

    <img src="../images/install/install09.png">

1. VMの設定 → ネットワーク → アダプター2にホストオンリーアダプターを設定する

    <img src="../images/install/install10.png">


## ３. CentOSのインストール

1. VMを起動して、CentOSをインストールする

    <img src="../images/install/install11.png">

1. Install CentOS 7を選択してEnterを押す

1. 日本語を選択する

    <img src="../images/install/install12.png">

1. インストール先を選択し、何も変更せず完了をする

    <img src="../images/install/install13.png">

    <img src="../images/install/install14.png">

1. インストールを開始する

1. rootパスワードせ設定し放置する

## 4. ネットワーク設定

1. rootユーザーでログインする

    <img src="../images/install/install15.png">

1. nmtuiコマンドを実行して、Edit a connectionを選択

    ``` shell
    $ nmtui
    ```

    <img src="../images/install/install16.png">

1. enp0s3を選択

    <img src="../images/install/install17.png">

1. IPv６をIgnoreに変更、Automatically connectにチェックを付ける

    <img src="../images/install/install18.png">

1. enp0s8を選択

    <img src="../images/install/install19.png">

1. Ipv4 CONFIGURATIONをManualに変更し、Addressesを192.168.56.101/24にする(101は任意の数字でOK)  
    同じようにIpv6をIgnoreに変更、Automatically connectにチェックを付ける

    <img src="../images/install/install20.png">

1. 戻ってQuit

    <img src="../images/install/install21.png">

1. 変更を反映させる

    ``` shell
    [root@localhost ~]# service NetworkManager restart
    # または
    [root@localhost ~]# service network restart
    ```

## ５. SSH接続

1. SSH接続確認

    ``` shell
    $ ssh root@192.168.56.1000
    # パスワード入力
    ```

1. `~/.ssh/config`に追記

    ``` shell
    [root@localhost ~]# exit
    $ vi ~/.ssh/config
    ```

    `~/.ssh/config`

    ``` shell
    # CnetOS
    Host centOS
        User root
        Hostname 192.168.56.100
    ```

    Hostの名前は任意

1. 接続確認

    ``` shell
    $ ssh centOS
    ```

    設定したHost名をいれる

1. 完了

    ``` shell
    [root@localhost ~]#
    ```
