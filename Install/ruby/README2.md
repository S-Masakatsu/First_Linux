# centOSでRubyの最新版をインストールする

- 実行環境
    - CentOS Linux release 7.6.1810 (Core)

## ■ 既存のrubyをアンインストールする

``` shell
$ sudo yum -y remove ruby
```

## ■ Rubyのインストール

### １. gitのインストール

gitがインストールされていない場合はインストールしてください。
インストール方法は下記から。

- <a src="../git/README.md">gitのインストール</a>

インストールされている場合は次に進んでください。

### ２. rbenvのインストール

#### ２-１. rbenvを取得

rbenv をクローンします。

``` shell
$ git clone https://github.com/rbenv/rbenv.git ~/.rbenv
```

``` shell
$ cd ~/.rbenv && src/configure && make -C src
```

#### ２-２. パスを通す

rbenvのパスを通して有効化します。

``` shell
$ echo 'export PATH="$HOME/.rbenv/bin:$PATH"' >> ~/.bash_profile
$ ~/.rbenv/bin/rbenv init
$ source ~/.bash_profile
```

#### ２-３. 確認

rbenvがインストールされたことを確認します。

``` shell
$ rbenv -v
rbenv 1.1.1-2-g615f844
```

### ３. ruby-buildのインストール

#### ４-１. ruby-buildを取得

ruby-buildをクローンします。

``` shell
$ git clone https://github.com/rbenv/ruby-build.git ~/.rbenv/plugins/ruby-build
```

#### ４-２. ruby-buildをインストール

ruby-buildをインストールします。

``` shell
$ sudo ~/.rbenv/plugins/ruby-build/install.sh
```

ruby-buildがインストールできるとrbenvのpluginであるrbenv installコマンドが使用できるようになります。

#### ４-３. インストール可能なバージョン確認

``` shell
$ rbenv install -l
```

インストール可能なRubyのバージョンが一覧で表示されます。

### ５. Rubyのインストール

今回は2.5.6をインストールします。

#### ５-１. パッケージのインストール

Rubyをインストールするのに必要なパッケージを先にインストールします。

``` shell
$ sudo yum install -y openssl-devel readline-devel zlib-devel
```

#### ５-２. Rubyのインストール

Rubyのインストールをします。

``` shell
$ rbenv install 2.5.6
```

#### ５-３. パスを通す

Rubyへのパスを通して有効化します。

``` shell
$ echo 'eval "$(rbenv init -)"' >> ~/.bash_profile
$ source ~/.bash_profile
```

#### ５-４. rbenvの設定

rbenvで2.5.6を使用するように設定します。

``` shell
$ rbenv global 2.5.6
```

#### ５-５. 確認

``` shell
$ ruby -v
ruby 2.5.6p201 (2019-08-28 revision 67796) [x86_64-linux]
```

Rubyのバージョンが表示されればインストール完了です。
