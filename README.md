# Perception Layer Debug
## 前面准备
### mavros源码下载编译并链接


### 下载终端模拟器方便调试
```
sudo apt install terminator
```

## Intel D435i 调试
### 步骤
1. 深度相机Intel D435i在ROS2中有专门的驱动，具体请看网上教程。

2. 打开ROS2节点，发布深度相机话题。 
```
ros2 launch realsense2_camera rs_launch.py
```
打开rqt_image_view可以看到```/camera/camera/color/image_row```和```/camera/camera/depth/image_rect_raw```发布的图像。

<p align="center">
  <img src="media/RGB图.jpg" alt="RGB图" width="49%" />
  <img src="media/深度图.jpg" alt="深度图" width="49%" />
</p>

### 相关问题
1. Intel D435i 需要USB3.0的数据线，若不是，无法收到图像。

2. Intel NUC 不能将飞控和激光雷达接在同一侧的USB，否则会占用传输内存。

## onborad-detector 调试
### 步骤
1. [onboard-detector](https://github.com/Zhefan-Xu/onboard_detector)下载源码并编译。
2. 配置修改
 - 相机内参
 - 图像分辨率
3. 先source再启动。
```
source /to/your/path/dectector_ws/install/setup.bash
ros2 launch onboard_detector dynamic_detector.launch.py
ros2 launch onboard_detector rviz.launch.py
```
### 相关问题
1. 需修改QoS配置