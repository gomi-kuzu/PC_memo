#Rのインストール時の問題とか

2016/10/14

ubuntu14.04

##手順
1. まず、Ubuntuのバージョンを確認
`cat /etc/lsb-release`
で出てくる、「DISTRIB_CODENAME=hogehoge」を確認

2. ダウンロード元のミラーサイトを登録
`sudo emacs /etc/apt/sources.list`

3. 一番下の行に一文追加
DISTRIB_CODENAME=hogehogeの場合
`deb https://cran.ism.ac.jp/bin/linux/ubuntu hogehoge/`
を追加

4. 公開鍵登録
`gpg --keyserver keyserver.ubuntu.com --recv-key E084DAB9`
`gpg -a --export E084DAB9 | sudo apt-key add -`

##ここ(4.)で問題発生
サーバーへのアクセスが何回やってもタイムアウトする

##そこで
 `gpg --keyserver hkp://keyserver.ubuntu.com:80 --recv-key E084DAB9`
 `gpg -a --export E084DAB9 | sudo apt-key add -`
 としたらできた
 参考サイト（https://forums.ubuntulinux.jp/viewtopic.php?pid=102945）にはproxyがどうのこうのかいてあったが詳しくは知らん
 
 ##手順に戻って
 
 /5. インスコ
`sudo apt-get update`
`sudo apt-get install r-base`

終わり
