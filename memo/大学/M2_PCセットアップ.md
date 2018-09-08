#PCセットアップ(M2/４月)

#####OSインスコ後
株丹さんのmy_ubuntu_setupを参考に、ディレクトリの英語化とかemacs,git,etcインスコとかrosのインスコ

#####プライベートIPの設定

#####choromeのインスコ


#####NVIDIAドライバおよびCUDA8.0のインスコ(このへんは全部CUIでX切ってやった)
`sudo apt-get install freeglut3-dev build-essential libx11-dev libxmu-dev  libxi-dev libgl1-mesa-glx libglu1-mesa libglu1-mesa-dev linux-headers-`uname -r``

`mkdir cuda`
`cd cuda`

ドライバのとcudaのrunファイルを落としてきてcudaディレクトリに入れとる
`chmod +x NVIDIA-Linux-x86_64-xxx.x.run`
`chmod +x cuda_7.0.28_linux.run`

`sudo emacs /etc/modprobe.d/blacklist-nouveau.conf`

↓これ書く

blacklist nouveau
blacklist lbm-nouveau
options nouvaeu modeset=0
alias nouveau off
alias lbm-nouveau off

`echo options nouveau modeset=0 | sudo tee -a /etc/modprobe.d/nouveau-kms.conf`
`update-initramfs -u`

再起動後
CUIに入って
`sudo service lightdm stop`
`cd ~/cuda`
`sudo ./NVIDIA-Linux-X86_64-xxx.xxx.run`

でドライバ入れ
`sudo ./cuda_7xxx.run`
でcuda入れる

`sudo service lightdm start`
でGUIに帰ってくる


######cuDNN
- 公式からダウンロードしてきたやつを展開後
`sudo cp -a cuda/lib64/* /usr/local/cuda-8.0/lib64/`
`sudo cp -a cuda/include/* /usr/local/cuda-8.0/include/`
`sudo ldconfig`

.bashrcに以下を記述

export CUDA_PATH=/usr/local/cuda-8.0
export PATH=$CUDA_PATH/bin:$PATH
export LD_LIBRARY_PATH=$CUDA_PATH/lib64:$LD_LIBRARY_PATH

export CPATH=$CUDA_PATH/include:$CPATH
export LIBRARY_PATH=$CUDA_PATH/lib64:$LD_LIBRARY_PATH
export LD_LIBRARY_PATH=$CUDA_PATH/lib64:$LD_LIBRARY_PATH

export CFLAGS=-I/usr/local/cuda-8.0/include
export LDFLAGS=-L/usr/local/cuda-8.0/lib64



pycharmのインスコ(インストールホームに気をつけるべき；；間違ってダウンロードディレクトリに入れちゃったけどまあうごくからいいや)

ハロパのインスコ


gitの設定,shhの設定

TexおよびYatexのインスこ
http://cirkitrwrc.blogspot.jp/2014/07/ubuntu1404ltsemacstex.html
を参考に
.emacs.dおよび.latexmkrcは今後使いまわしていこう(ぐーぐるドライブに保存)


#####pyenv
- [ここ](https://www.qoosky.net/techs/263)や[ここ](http://qiita.com/akito1986/items/be5dcd1a502aaf22010b)を参考にgithub経由でpyenvをインストール
→詳細
`sudo apt-get install git gcc make openssl libssl-dev libbz2-dev libreadline-dev libsqlite3-dev`

`git clone git@github.com:pyenv/pyenv.git ./.pyenv`
.pyenv内のpluginsディレクトリに移動後

`git clone git@github.com:pyenv/pyenv-virtualenv.git`

そして.bachrcに以下を記述

export PYENV_ROOT="${HOME}/.pyenv"
if [ -d "${PYENV_ROOT}" ]; then
   export PATH=${PYENV_ROOT}/bin:$PATH
   eval "$(pyenv init -)"
   eval "$(pyenv virtualenv-init -)"
fi

んで
`source .bashrc`
からの
`pyenv install anaconda2-4.3.1`
`pyenv rehash`

OpenCVいれるには
`conda install --channel https://conda.anaconda.org/menpo opencv`

#####チームビューアのインスコ設定


[これ](http://n-nishida.hatenablog.com/entry/2015/04/19/053643)（n_nishidaのページ）にあるソフトをaptで入るものから先にいれといてpythonモジュールは仮想環境作ったあとにぶちこむ(mecabぐらいしか入れてない)
- python3と2で入れ方が異なるもの
 - mecab
 →3の場合`pip install mecab-python3`

chainer
- 仮想上で、githubからクローンしたsetup.pyを
`python setup.py install`
もしくは`pip install chainer`

#####プリンターの設定