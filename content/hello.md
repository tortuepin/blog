+++
Description = ""
Tags = [
]
Categories = [
]
date = "2016-12-17T10:04:18+09:00"
title = "計算機室に行かずに卒業する"

+++

この記事は、mast Advent Calendar 2016 の20日目の記事です。


## 0. はじめに

私は機室が嫌いです。

嫌いなので機室には行かないことにして、機室のPCでやる課題は自分のPCでもできるように環境を整えました。  
それなりに苦労はありましたが、おかげでもうかれこれ二年くらい授業以外では機室に行っていませんし、授業もあんまり行っていません。  
基本的な部分だけですが、誰かの役にたつと嬉しい。

私の環境はmacですが、windowsでもできます。winの人はBush on Ubuntu on Windowsを使うと良いでしょう。[[ここ]](http://qiita.com/tortuepin/items/ce9e53fd85dd6b4cb6c5)を見ると良いです。

## 1. SSH

sshを使うと自分のPCから全額計算機システムの端末を利用することができます。[[この辺]](https://magazine.mast.tsukuba.ac.jp/archives/1793)を参照  
これさえあれば大抵の場合は機室に行かなくてもなんとかなるようになります。  
前はパスワードだけで使えたのですがいつの間にか公開鍵認証方式になってました。
詳しくは[[公開鍵認証によるUNIXシェルログイン]](https://www.u.tsukuba.ac.jp/icho13/publickey.html)とかを参照してください。

### sshの設定

さて、鍵の設定が終わったらターミナル上で

```
ssh -i id_rsa sXXXXXXX@hoge.tsukuba.ac.jp
```

とかやると接続できますが、いちいちこれを入力するのは面倒くさいので、.ssh/configを利用します。

.ssh/configとはsshの設定ファイルです。

詳しくはググってもらうとして([[この辺]](http://qiita.com/passol78/items/2ad123e39efeb1a5286b)が参考になります)  
~/.ssh/configに

```
Host 任意の名前(univ)
HostName ホスト名(ubuntu.tsukuba.ac.jp)
User ユーザー名(sXXXXXXX)
Port ポート番号(22)
IdentityFile 鍵へのパス(~/.ssh/hoge.keyとか)
```

と入力しておくと

```
ssh univ
```

とやるだけで接続できるようになります。


### 接続できたら

接続できたらあとは機室のubuntuの端末と同じように使えます。  

ただし、使えるのは端末だけなので、普段メモ帳とかを使っている人は端末内で使えるテキストエディタを使う必要があります。  
vimを使いましょう。


sshを抜ける時は

```
exit
```

です。


## 2. リモートデスクトップ

sshから利用できるのは端末だけですが、デスクトップ環境をリモートで利用する方法もあります。  
[[この辺]](https://www.u.tsukuba.ac.jp/icho13/remote.html)を見たりググると良いでしょう。

動作がモッサリなので私はあまり使いません。
学内からしかアクセスできないwebページを見るときには使えます。


## 3. Visual Studio

二年生まではsshとリモートデスクトップさえ使えれば問題なかったのですが、三年生になって突然Visual Studioの使用を(半ば)強制する授業が出てきました。

私はmacを使っているのですが、[[bootcamp]](https://www.apple.com/jp/support/bootcamp/)と[[Microsoft Imagine]](https://www.slis.tsukuba.ac.jp/ipc/resources/msdnaa.html)を駆使すればなんの問題もありません。

そう思ってmacにbootcampでwindows10を入れて、Microsoft Imagineで最新版のvisualstudioをインストールしたところ、死にました。

全額計算機システムに入っているのはVisual C++ 2010 一方Microsoft Imagineでインストールできるのは2015。

バージョン差のせいで授業で配られたプログラムが実行できないのです。

ならばと思ってMicrosoft Imagineから2010版をダウンロードしようとして死にました。

visual studio2010のダウンロードページはすでに削除されていました。

ここまでで、visualstudioのインストールがうまくいかなくて再インストールしたり、再インストールの途中で前回インストールした時のゴミが残っててなんかエラー出でそれを消してまたインストールしたり、なんとかvisualstudio2015で実行できないか試してみてダメだったり、なんだかんだと、諦めて機室でやっていれば課題なんてとっくに終わってるくらいの時間は経っていましたが、機室には絶対に行きたくないので、諦めずに頑張ったところ、

visual studio 2010のダウンロードページは残っていないが、直接のダウンロード先のリンクはまだ生きているということがわかり、そこからダウンロード、インストールに成功し、プログラムも実行できるようになりました。

[[Visual Studio 2010 Express 日本語版 (Microsoft.com)]](http://download.microsoft.com/download/4/E/6/4E61E454-1DE7-4B70-860B-13282DE65D6B/VS2010ExpressJPN.iso)

これがそのリンクです。一応貼っておきますが、いつまで生きているかはわかりません。

## 4. その他便利なもの

ここまで出来ればもう機室に行く必要は無くなりますが、課題をするのに便利なものをご紹介。

### DropBox
言わずと知れた。詳しくはgoogle先生に
課題に関連するファイルは全部ここに置いておくと、わざわざsshしなくてもローカルで課題ができます。

### Git/Github
ソースコードとかはDropBoxじゃなくてGitで管理してGithubに保存してます。詳しくはGoogle先生に  
ただ、配られたサンプルをそのままあげると著作権とかどうなんだろうって感じなので注意です。  
githubで課題名とか、特徴的な関数名とかで検索すると答えが出てきたりします。

### Microsoft Imagine
3.Visual Studioでも出てきましたが、情報学群にいるうちはタダでなんでも使えるので、使ったほうがいいです。
前はDreamSparkだった気がします。

### sftp
sshを使ってサーバーとローカルでファイルのやり取りができます。

### vim
テキストエディタです。使うとモテるらしいです。

### emacs
OSです。小指で懸垂ができる人は使うと良いです。

### google
先生はなんでも知っていますので、何かあったらまず聞いてみると良いです。
知恵袋で質問するときも、まずは先生にお伺いを立てて上位1000件くらいをしっかり読み込んでからでないと叱られてしまいます。

### 友達
これがあると何かと便利です。親切にしてもらったらきちんとお返ししましょう。


## 5. さいごに

Visual Studioの環境を整えるのがどれほど大変だったかを誰かに聞いて欲しくてAdvent Calendarに登録したのですが、さすがにそれだけだと申し訳ないので色々盛ってみました。

前述の通り基本的なところしか書いていないので、google先生と相談しながら改良していくと良いです。

ガンガン改良して引きこもり生活をさらに良いものにしていきましょう。
