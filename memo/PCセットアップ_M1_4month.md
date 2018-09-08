#PCセットアップ(M1/４月)

OSインスコ後
株丹さんのmy_ubuntu_setupを参考に、ディレクトリの英語化とかemacs,git,etcインスコとか

NVIDIAドライバおよびCUDA7.5のインスコ
- runファイルで一気にドライバもCUDAも入れちゃった
- そのへんは全部CUIでX切ってやった

cuDNN
- ダウンロードしてきたあれを
https://daichiahl.wordpress.com/2016/01/15/ubuntu-14-04%E3%81%ABcudnn%E3%82%92%E3%82%A4%E3%83%B3%E3%82%B9%E3%83%88%E3%83%BC%E3%83%AB/

ハロパのインスコ

choromeのインスコ

gitの設定,shhの設定

pyenv
- [ここ](https://www.qoosky.net/techs/263)や[ここ](http://qiita.com/akito1986/items/be5dcd1a502aaf22010b)を参考にgithub経由でpyenvをインストール（pythonVerはpyenvで管理する）

プライベートIPの設定

virtualenv（python仮想環境はpyenv-virtualenvではなくvirtualenvおよびvirtualenvwrapperで管理する）
- pyenvでインスコしたpythonに`pyenv global VERSION`で忘れずに入りpipでvirtualenvとvirtualenvwrapperをインストール[｛参考｝](http://qiita.com/caad1229/items/325ca5c8ad198b0ebce7)
~~そのあと.bashrcに
`if [ -f /home/inoma-ubu/.pyenv/shims/virtualenvwrapper.sh ]; then
    export WORKON_HOME=$HOME/.virtualenvs
    source /home/inoma-ubu/.pyenv/shims/virtualenvwrapper.sh
fi`
Pathは`which virtualenvwrapper.sh`で調べて変える[｛参考｝](https://virtualenvwrapper-docs-ja.readthedocs.org/en/latest/install.html)~~なんかこれしちゃいかん？？

pycharmのインスコ

チームビューアのインスコ設定

[これ](http://n-nishida.hatenablog.com/entry/2015/04/19/053643)（n_nishidaのページ）にあるソフトをaptで入るものから先にいれといてpythonモジュールは仮想環境作ったあとにぶちこむ
- python3と2で入れ方が異なるもの
 - mecab
 →3の場合`pip install mecab-python3`

chainer
- 仮想上で、githubからクローンしたsetup.pyを
`python setup.py install`
もしくは`pip install chainer`



