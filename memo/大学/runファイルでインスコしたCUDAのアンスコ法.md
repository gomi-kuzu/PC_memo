#runファイルで入れたCUDAはこうやって消せ！

CUI入ってログイン後
`sudo service lightdm stop`

`sudo /usr/local/cuda-7.5/bin/uninstall_cuda_X.X.pl`
`sudo /usr/bin/nvidia-uninstall`

`sudo apt-get --purge remove nvidia-*`
`sudo apt-get --purge remove cuda-*`



`sudo service lightdm start`

/usr/localのCUDAのディレクトリが残ってる場合はrmコマンド（-r付き）で消そう

[参考]
http://it.senatus.jp/page-337/
http://qiita.com/conta_/items/d639ef0068c9b7a0cd12