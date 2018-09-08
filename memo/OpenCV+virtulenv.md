#virtualenv環境内でOpenCVを使うために
仮想環境のパイソンのsite-packagesに移動して
`cd ~/.virtualenv/環境名/lib/python2.7/site-packages` 
システム環境のOpenCVモジュールファイルへのシンボリックリンクをはってやる！
ちなみにシンボリックリンクの作り方`ln -s リンク元のファイルorフォルダ リンクを置くフォルダ`

`ln -s /usr/local/Cellar/opencv/2.4.9/lib/python2.7/site-packages/cv.py cv.py`
`ln -s /usr/local/Cellar/opencv/2.4.9/lib/python2.7/site-packages/cv2.so cv2.so`