 ![](https://i.imgur.com/vkF51nI.png)
 ###### tags: `kreis` `github` `ssh`
# GitHub ssh接続メモ


---
## はじめに

* GitHubにSSH接続をするにsshの鍵登録をします。すでにGiuhubのユーザ登録済の状態とする。まだの場合は下記よりGitHubのホームページより登録を行って下さい。※沢山分かりやすい手順がググればありますのでここでは割愛。
https://github.com
![](https://i.imgur.com/ulHSDe4.png)


* Windowsでは`Git for Windows`をインストール。Mac,LinuxはデフォルトでGitが入っている。※Docker等を利用するのであればWSL2がお勧め。Gitはデフォルトで入っている。
* 個人的に本よりもGithubから出ているドキュメントが一番わかりやすいと思う。![](https://i.imgur.com/xkhqIZp.png)
---
## 自分のパソコンで秘密鍵・公開鍵の生成を行う


#自分のホームディレクトリに .sshがない場合は作成。
$cd ~/.ssh

#下記コマンドを投入
$ssh-keygen -t rsa

* 例） ここではkreis-rsaという名前で作成している、デフォルト（空Enter）はid_rsa。
はじめて登録（.ssh/下にid.rasが存在しない）の場合はデフォルト（空Enter）で作成したほうがよい。※id.ras意外の場合は下記Configの設定が必要となる。
![](https://i.imgur.com/Xl8oKBi.png)

## 公開鍵をGitHubにアップする 

* 先ほど作った xxxx.pub（公開鍵）の中身をコピー。
![](https://i.imgur.com/8wO6IEf.png)
* https://github.com/settings/ssh　から公開鍵登録。![](https://i.imgur.com/C94t2HO.png)


* titleに公開鍵名、コピーした公開鍵の中身（key)をkeyにコピー![](https://i.imgur.com/8ECZeP9.png)
* 登録後![](https://i.imgur.com/h24Hg6R.png)
## ターミナルに戻り接続確認を行う 
* $ssh -T git@github.com で下記メッセージがでれば登録OK！！![](https://i.imgur.com/deEil01.png)


## gitHub 複数アカウントを作成した場合
* githubアカウントを複数もっている場合はconfigの記載が必要。![](https://i.imgur.com/3YcoGc5.png)
* host名で接続確認。![](https://i.imgur.com/RHIuRl6.png)

## 結論 
複数のGitHubIDを切り替えて作成するには別途バッチファイルが必要。よってプロジェクト毎にDockerを利用してDockerリポジトリ内でgitを利用するのがよいのではと。


