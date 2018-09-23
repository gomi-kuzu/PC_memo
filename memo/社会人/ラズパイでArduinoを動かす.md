# ラズパイとArduino　連携めも
+ Models:Rasberry Pi 3 B & Arduino UNO R3 互換機
+ RasPi OS:Ubuntu mate 16.04

## PiへのArduinoIDEインスコ方法
1. [公式サイト](https://www.arduino.cc/en/Main/Software)からIDEのファイルダウンロード  
※落とすのは**Linux ARM用のやつ**
2. .shファイルから入れる  
`$ mkdir ~/tools`
このディレクトリにさっき落としたやつを解凍したもの(arduino-x.x.x)を配置したのち  
```
$ cd ~/tools/arduino-x.x.x
$ ./install.sh
```
3. .bashrcに以下を記述  
`export PATH=$PATH:$HOME/tools/aruino-x.x.x`  
4. 起動確認  
```
$ source ~/.bashrc
$ arduino
```
## ROS側の準備
パッケージの追加  
`$ sudo apt install ros-kinetic-rosserial-arduino  ros-kinetic-rosserial`  
## IDEへROSライブラリインストール
```
$ cd ~/tools/arduino-x.x.x/libraries
$ rosrun rosserial_arduino make_libraries.py .
```
※IDEのスケッチ＞ライブラリをインクルードにros_libが追加されていることを確認  (ファイル＞スケッチ例にもros_libが増える)

## 使用上の注意
USBアクセス兼権付与を行わないと通信できない  
`$ sudo chmod 666 /dev/ttyACM0`  

## 簡単なデモ
[Lチカ](https://qiita.com/nnn112358/items/059487952eb3f9a5489b)
