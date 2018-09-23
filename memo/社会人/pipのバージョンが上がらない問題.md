# pipのバージョンが最新にならなかったり　18/9/23
環境  
+ Rasberry Pi 3 B
+ Ubuntu mate 16.04

[参考](http://icchy.hatenablog.jp/entry/2018/04/17/064443)  

### 概要
aptで入れたpip(pip9以前)を`pip install --upgrade pip`で(pip10以降に)更新しようとするとよくないらしいよ

### 結局どうしたか  
`sudp apt-get purge python-pip`で一回pip消す  
[get-pip.py](https://pip.pypa.io/en/latest/installing/#installing-with-get-pip-py)落としてきてそれ経由でpip 入れ直し  
`python get-pip.py -vv`
