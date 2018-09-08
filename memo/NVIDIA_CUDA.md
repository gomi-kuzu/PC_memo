#NVIDIAドライバーとCUDA導入（GPU換装につき二度目）
###OS:ubuntu14.04,グラボ:quadroK2200

0. あらかじめ公式サイトからCUDAインストローラのdebファイルを落としとく

1. 一応GUIを切って仮想コンソールに入る(CUI起動の設定にして再起動した)

2. 今入っているドライバーとCUDAを削除
`sudo apt-get --purge  remove  nvidia-*`
`sudo apt-get --purge remove cuda-*`

3. NVIDAドライバーのインスコ
`sudo add-apt-repository ppa:mamarley/nvidia`
`sudo apt-get update`
`apt-cache search 'nvidia-[0-9]+$'`
`sudo apt-get install nvidia-352`←公式サイトを参考に任意のバージョンを選ぶ

4. CUDAインスコ
`sudo dpkg -i cuda-repo-ubuntu1404-7-5-local_7.5-18_amd64.deb`
`sudo apt-get update`
`sudo apt-get install cuda`

5. 再起動
`sudo shutdown -r now`

6. .bashrcに次を記述
`export PATH=/usr/local/cuda-7.5/bin:$PATH`
`export LD_LIBRARY_PATH=/usr/local/cuda-7.5/lib64:$LD_LIBRARY_PATH`

7.　サンプル動かしてみる
`cuda-install-samples-7.5.sh ~`
`cd ~/NVIDIA_CUDA-Samples_7.5/5_Simulations/nbody`
`make`
`./nbody`
