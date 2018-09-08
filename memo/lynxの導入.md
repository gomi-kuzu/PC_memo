# lynxで快適テキストブラウジング

- インスコはアプリセンターからlynxで検索＆ポチポチ

- `/usr/bin/`にggrksという名前で以下のシェルスクリプトを配置


	for x in "$@"  
	do  
  	query=$query$x+  
	done  
	lynx https://google.co.jp/search?q=$query

- `sudo chmod a+x /usr/bin/ggrks`で実行権限付与
- `/etc/lynx-cur/lynx.cfg`にある設定ファイルを開き
ファイル中の
`#SET_COOKIES:TRUE`と`#ACCEPT_ALL_COOKIES:FALSE`のコメントを外し
`SET_COOKIES:TRUE`
`ACCEPT_ALL_COOKIES:TRUE`
と両方TRUEにしてクッキーを常に許可するようにする

 
これでターミナルで`ggrks hogehogeunko` とかすればテキストブラウザでグーグル検索ができる！！！！！！！