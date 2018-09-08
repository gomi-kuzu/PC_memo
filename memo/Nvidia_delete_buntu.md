#ubuntu14.04 NVIDIAドライバー削除
1. CUIモードで再起動
まず`sudo emacs /etc/init/lightdm.override`
さらにこのファイルに１行`manual`と記す
これで`sudo shutdown -r now`として再起動する
最初のロード画面でGUIに入らず待機しているのでそこで
`Ctrl+Alt+F1`でCUIに入れる
その後GUIを起動したければ`sudo lightdm`
また、CUIログインをやめたければlightdm.overrideファイルを消すか
manual⇛#manualと内容をコメントアウトするかすれば良い

2. CUIで入ったら
`sudo apt-get purge nvidia*`

これで再起動して、システム設定⇛ソフトウェアとアップデート⇛追加のドライバーを確認して
プロプライエタリドライバーではなく、X.Orgのドライバが適用されていればOK