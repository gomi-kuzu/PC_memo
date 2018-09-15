# ラズパイセットアップの自分用メモ 18/9/8

  + モデル　Rasberry Pi 3 B  
  + OS　ubuntu mate 16.04  

## 日本語入力のための設定
[参考](https://deviceplus.jp/hobby/raspberrypi_entry_049/)  
↑要約
基本的に上のバーからシステム＞＞設定＞＞ユーザ向け＞＞言語サポートと進んだ先であれこれやる  
注意点は２回ぐらい再起動しながらIMシステムにfctxを設定するとこ  

## ディレクトリ名を英語に  
1. このコマンド打つ  
`$ env LANGUAGE=C LC_MESSAGES=C xdg-user-dirs-gtk-update`

2. ログインし直して適用

3. Bluemanの設定変更  
`$ gsettings set org.blueman.transfer shared-path ~/Downloads`

## リモート関連
※ipは固定していおいたほうが無難  

### sshで入るための設定
[参考](https://s2jp.com/2014/01/raspberry-pi-ssh/)  
↑要約  
1. まず  
`$ sudo raspi-config`  
からsshを有効化からの  
```
$ sudo apt update
$ sudo apt upgrade
$ sudo apt install openssh-server
```
2. Windows側にSSHクライアントとしてTeraTermをインスコ  
3. TeraTermからはいる  
ラズパイ側のipを`ifconfig`コマンドで確認してTeraTermのホストのとこに入力して接続（ユーザ名とパスはラズパイのUbuntuのそれ）  

### リモートデスクトップから入るための設定
[参考1](https://qiita.com/sasayabaku/items/ff96f700d2b65fdf085e)
[参考2](https://qiita.com/t114/items/bfac508504b9a6b7570d)  
↑要約  
1. xrdpインスコと自動起動設定  
```
$ sudo apt install xrdp
$ sudo systemctl enable xrdp
```
2. 日本語キーボードの設定  
```
$ cd /etc/xrdp/
$ sudo wget http://w.vmeta.jp/temp/km-0411.ini
$ sudo ln -s km-0411.ini km-e0010411.ini
  ln -s km-0411.ini km-e0200411.ini
$ sudo ln -s km-0411.ini km-e0210411.ini
```
3. xrdp再起動  
`$ sudo service xrdp restart`  
4. winのリモートデスクトップにズパイのipぶち込んで入る  

## ROS(kinetic)インスコ
[参考](http://ai-coordinator.jp/ubuntu-mate-ros)  
↑要約  
1. 闇雲にこれ叩く（中身は公式wiki通り）  
```
$ sudo sh -c 'echo "deb http://packages.ros.org/ros/ubuntu $(lsb_release -sc) main" > /etc/apt/sources.list.d/ros-latest.list'  
$ sudo apt-key adv --keyserver hkp://ha.pool.sks-keyservers.net:80 --recv-key 421C365BD9FF1F717815A3895523BAEEB01FA116
$ sudo apt-get update
$ sudo apt-get upgrade
$ sudo apt-get install ros-kinetic-desktop-full
$ sudo rosdep init
$ rosdep update
$ echo "source /opt/ros/kinetic/setup.bash" >> ~/.bashrc
$ source ~/.bashrc
```
2. 確認  
`$ roscore`

## OpenCVインスコ(ROS経由)
[参考](https://gbiggs.github.io/ros_moveit_rsj_tutorial/image_processing_and_opencv.html)  

↑要約  
1. 以下のコマンドを叩く  
```
$ sudo apt install ros-kinetic-vision-opencv
$ sudo apt install python-opencv
$ sudo apt install libopencv-dev
```
2. これも一応  
`$ sudo apt-get install ros-kinetic-cv-camera`  
3. 確認  
USBカメラを挿して以下のようなpythonスクリプトを走らせる  
```python
#!/usr/bin/env python
# -*- coding: utf-8 -*-  
import cv2  
camera = cv2.VideoCapture(0)  
while True:  
    status, image = camera.read()  
    if not status:  
        break  
    cv2.imshow("window", image)  
    key = cv2.waitKey(30)  
    if key == 0x1b:  
        break  
camera.release()  
cv2.destroyAllWindows()  
```

## gitとgithubの設定
[参考](https://qiita.com/0ta2/items/25c27d447378b13a1ac3)  
0. インスコ  
`$ sudo apt install git`  
1. まずは初期設定  
```
$ git config --global user.name "ユーザーネーム"
$ git config --global user.email "メアド"
```
2. sshキーの登録  
 - キー生成  
`$ ssh-keygen -t rsa -b 4096`  
 - 公開鍵確認  
 `$ cat ~/.ssh/id_rsa.pub`  
 - 出てきた長い文字列をコピー  
 - githubにアクセスしてサインイン
 - Setting>>SSH key>>Add SSH key からさっきコピったやつを登録する

## ラズパイ起動で勝手にログインする設定に
1. システム>>システム管理>>ユーザとグループ>>パスワードからログイン時のパス要求を切っておく  
2. `/usr/share/lightdm/lightdm.conf.d/60-lightdm-gtk-greeter.conf`に以下を記載  
`autologin-user=pi　(<- ユーザ名)`  

## その他やったこと
aptでchromium入れたり  
emacsインスコしたり自分の設定ファイルコピってきたり  
etc...
