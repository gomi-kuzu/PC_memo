#PIL(pillow)の使い方

インポート系
`from PIL import Image`
`from PIL import ImageOps`
画像を読み込む
`im = Image.open("ファイルパス",モード)
↑モードは何も入力しなければ"r"(リード)`
グレースケールに変換(下の""内をRGBにしたらカラースケール)
`img = im.convert("L")`
保存
`img.save("sample.jpg","JPEG",quality=100)`
表示
`img.show()`
画素データ取得
`px = img.getdata()`
画像データをリストに渡す
`l = list(px)`
画像データを配列に渡す(numpy使用)
`numpy.array(px)`
色反転（ネガ⇔ポジ、白⇔黒）
`im2 = ImageOps.invert(im,)`

リサイズその１
`img = im.resize((100,200), Image.ANTIALIAS)`
↑第1引数でサイズ指定(横,縦),第2引数でフィルタ加工指定？（ここではアンチエイリアス）
リサイズその２
`img　=　im.thumbnail((100, 100), Image.ANTIALIAS)`

各種情報の取得
`im.size`
↑（横,縦）で返ってくる

