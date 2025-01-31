# 基本的なコマンド

## ■ コマンド

コマンドには、コマンド名と同じファイル名の外部コマンドと、シェルに内臓されている内部コマンドが存在する。  
入力したコマンドが存在しない場合や、スペルミスをしている場合はエラーメッセージが出力される。  
なお、Linuxでは、コマンドやファイル名などは大文字と小文字は区別される。

### ● 構文

コマンドにはオプションや引数を指定できます。  
コマンドによってオプションが必須のもの、引数が必須なもの、また、引数やオプションが存在しないものがあります。  
ほとんどの場合は引数よりもオプションを先に指定します。

- 書式  
    `コマンド [オプション] [引数]`  
    [ ]は省略可能

## ■ シェルの便利な機能

コマンドライン操作を効率よく行う為に、シェルには便利な機能が備わっています。

### ● 補完機能

コマンドやファイル名など、入力中の文字列を自動的に補完する機能です。  
入力中に`Tabキー`を押すと、残りの部分が自動的に補完されます。

``` shell
$ his
# Tabキーを押す
```

``` shell
$ history
```

入力時点での候補が複数ある場合は、Tabキーを押しても何も反応しません。  
Tabキーを２回押すことで、その時点での候補がすべて表示されます。

``` shell
$ h
# Tabキーを２回押す
```

``` shell
$ h
h2load               hb-view              hexdump              htcacheclean
h2ph                 hdid                 hidutil              htdbm
h2ph5.18             hdik                 history              htdigest
```

### ● コマンド履歴

実行したコマンドは保存されていて、後から呼び出すことで再入力の手間が省けます。  
`カーソルキーの「↑」(またはCtrl+P)`を押すと、最近実行したコマンドから遡って表示されます。  
また、`カーソルキーの「↓」(またはCtrl+N)`を押すと、古いコマンドから遡って表示されます。  
目的のコマンドが表示された時点で`Enterキー`を押すとコマンドが再実行されます。  
効率よくコマンド履歴を検索するには、**インクリメント検索**を利用します。  
`Ctrl+R`を押すと状態が変化します。  
１文字入力するごとにコマンドの候補が表示されます。入力するごとに候補が絞られていきます。  
終了するには`Ctrl+C`を押すと終了します。

## ■ パイプとリダイレクト

Linuxでは、コマンドの出力先を画面上にからファイルに切り替えたり、別のコマンドへと繋いだりすることができます。

### ● パイプ

コマンドをいくつも連携させ、複雑な操作が可能になります。  

- 書式  
    `コマンド１ | コマンド２`

`パイプ「|」`を使うと、コマンドの出力を別のコマンドに渡して処理することができます。  
例えば`ls`コマンド(ファイル一覧表示)と`wc`コマンド(行数・単語数・バイト数)を連携させてみます。

``` shell
$ ls
hoge    hoge1   hoge2

$ ls | wc -l
    3
```

このようにファイル数を数えることができます。  
パイプが使われるケースとしては、行数が多くスクロールアウトしてしまう表示を、`less`コマンドで１ページずつ表示するようなケースがあります。  

``` shell
$ ls -la | less
```

### ● リダイレクト

コマンドの実行結果をファイルに保存したいとに使うのがリダイレクトです。  
様々な書き方がありますが、とりあえず「`>`」「`>>`」を覚えとけば大丈夫です。

- 書式  
    `コマンド > 出力先ファイル名`  
    `コマンド >> 出力先ファイル名`

例えば下記の例ではlsの実行結果をfilelistに保存しています。

``` shell
$ ls > filelist
```

通常画面上に出力される結果をfilelistというファイルに書き込まれます。  
ファイルがない場合には新規にファイルが作成されます。  
ちなみに「`>`」はファイルに上書きされ、「`>>`」は末尾に追記します。

## ■ メタキャラクタの利用

シェルでは特殊な意味をもつ記号を**メタキャラクタ**という。  
その中でもファイル名のパターンを表す特殊な記号を**ワイルドカード**いう。  
シェルのメタキャラクタを使うと、パターンに一致する複数ファイルを扱うことができます。  
例えば/etcディレクトリ以下からファイル末尾が「.conf」のファイルだけを表示したいのであれば、

``` shell
$ ls /etc/*.conf
```

のようにします。  
`*` は「０文字以上の任意の文字列」を表すメタキャラクタです。  
文字数を限定したい場合は、「任意の１文字」を表すメタキャラクタの`?` を使います。

``` shell
# /etcディレクトリ以下のhで始まるファイルを表示
$ ls /etc/h*
# /etcディレクトリ以下のhで始まるファイル名の長さが5文字のファイルを表示
$ ls /etc/h????
```

<a href="../../README.md/#ttl3-3">戻る➡︎</a>
