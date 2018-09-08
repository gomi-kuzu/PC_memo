#Tensorflow＋Kerasインスコ
2016/9/15
Ubuntu14.04

###※まずpyenvが若干古くなってたので更新したよ
~/.pyenv上で
`git pull`
`pyenv rehash`
###pyenvでアナコンダをインスコ
`pyenv install anaconda3-4.0.0`
`pyenv shell anaconda3-4.0.0`
###TensorFlowのインストール
`conda create -n tensorflow python=3.5`
`source activate tensorflow`
`export TF_BINARY_URL=https://storage.googleapis.com/tensorflow/linux/gpu/tensorflow-0.10.0-cp35-cp35m-linux_x86_64.whl`
`pip install --ignore-installed --upgrade $TF_BINARY_URL`

###Kerasインスコ
ソースをgit cloneしてきてから
`python setup.py install`

参考http://qiita.com/yukiB/items/5d5b202af86e3c587843