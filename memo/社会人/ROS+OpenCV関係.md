# ROSでOpenCV活用するときのめも

## Appで色々簡単に試せる
[参考1](https://qiita.com/nnn112358/items/c8119857a85077de41db)[参考2](http://wiki.ros.org/opencv_apps)   
例）
```
$ roscore
$ rosrun usb_cam usb_cam_node
$ rosrun image_view image_view image:=/usb_cam/image_raw debug_view:=-1
$ roslaunch opencv_apps face_detection.launch image:=/usb_cam/image_raw
```
### topic名を指定して　顔部分のみ見たり  
上の状態で  
`$ rosrun image_view image_view image:=/face_detection/face_image`
## キャリブレーションのやり方
[参考](https://qiita.com/proton_lattice/items/aa805b28700575ba5ed3)
