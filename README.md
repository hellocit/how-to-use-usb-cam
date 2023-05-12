# how-to-use-usb-cam

# ROS1環境でusbカメラを使用するための情報を収集したリポジトリ
# installation 
カメラを使うためのROSパッケージ
```
sudo apt install ros-noetic-usb-cam
sudo apt install ros-noetic-image-view
```
# 準備

以下のコマンドを打ち込むことでusbカメラとその他のカメラを区別
```
v4l2-ctl --list-devices
```
自分の環境での結果
```
v4l2-ctl --list-devices
HD Webcam: HD Webcam (usb-0000:00:14.0-13):
	/dev/video0
	/dev/video1
	/dev/video2
	/dev/video3

C270 HD WEBCAM (usb-0000:00:14.0-2):
	/dev/video4
	/dev/video5
```
上記の結果からvideo4と5がusbである．(理由は不明だが4か5のどちらかがハズレ)
# 起動
ノードの起動コマンド
```
rosrun usb_cam usb_cam_node _video_device:=/dev/video4
rosrun image_view image_view image:=/usb_cam/image_raw
```
# まとめ
私の環境では上記のコマンドをターミナルに打ち込むことでusbカメラを使用できた．
# 参考文献
* http://ishi.main.jp/ros/ros_uvccam.html
* https://ma38su.hatenablog.com/entry/2021/06/23/121926
* https://qiita.com/Yuya-Shimizu/items/10804c9ac44a3568d116