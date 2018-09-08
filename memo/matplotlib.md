#matplotlib使い方関連

- インポート
 `import matplotlib.pyplot as plt`
でインポート

- 基本
x軸要素y軸要素を数値や関数で与えplotメソッドに渡す
`x = np.arange(-3, 3, 0.1)`
`y = np.sin(x)`
`plt.plot(x, y)`
さらに
`plt.show`
でプロットしたものを見る

- すこし詳しい機能とか
plotの引数は
~~`plot(x軸要素,y軸要素,マーカー,ラベル)`~~
引数３個目より先は名前指定したほうがいい
例
`plot(x, y, color="k", marker="*", markersize=20, markerfacecolor="r")`
_
マーカーは"r-"のように文字列で与える
ラベルもも文字列で`label="X"`とか

	`plo.title("TITLE")`でタイトルを出せる

- オブジェクト指向的書き方？
`x = np.arange(-3, 3, 0.01)`
`y_sin = np.sin(x)`
`y_cos = np.cos(x)`
↑このへんは変わらん

1. Figureのインスタンスを生成
`fig = plt.figure(figsize=(16,6))`
引数は`figure(figsize:(横, 縦), 解像度:(dpi), facecolor:背景色)`
figsizeは描写する画面サイズのこと(16,6)は横1600px,縦600pxを表す
なにも入力しなければ(8,6)
_
(なんかとりあえず代入せんでも最初に`plt.figure(figsize=(16,6))`ってしとけばいいっぽい？）

2. Axesのインスタンスを生成
`ax1 = fig.add_subplot(2,1,1)
ax2 = fig.add_subplot(2,1,2)`
引数は2行１列分グラフマスを作ってその１個目ということを指定している
_
マスごとにサイズを変えたい場合は
`ax1 = plt.subplot2grid((1,20),(0,0),colspan=18)`
`ax2 = plt.subplot2grid((1,20),(0,19))`
subplot2gridの引数は((何行,何列)に分けるか,そのうち左から何番目,いくつ分まで占めるか)

3. データを渡してプロット
`ax1.plot(x, y_sin)`
`ax2.plot(x, y_cos)`

4. y軸の範囲を調節とグラフタイトル・ラベル付け
`ax1.set_ylim(-1.3, 1.3)`
`ax2.set_ylim(-1.3, 1.3)`

	`ax1.set_title("$\sin x$")`
	`ax2.set_title("$\cos x$")`

	`ax1.set_xlabel("x")`
	`ax2.set_xlabel("x")`

	`fig.tight_layout()`  ←タイトルとラベルが被るのを解消

	`plt.show()`
↑（）を忘れない！！


~~グラフの範囲
`ax1.xlim(0, 3)`
x軸は0から３までの範囲で表示~~

軸いくつづつ区切るか
`ax1.set_xticks(range(0,1000*(len(x_d)//1000)+1000,1000))`
引数(この配列に格納したかんじで,この数ずつ)

軸にラベル
`ax2.set_yticklabels(["stay","walk","jog","skip","stUp","stDown"])`

スタイル変更
`plt.style.use('seaborn-darkgrid')`

texで使うepsを出力するときは
`plt.rcParams['text.usetex'] = True`
をいれとくと崩れない

