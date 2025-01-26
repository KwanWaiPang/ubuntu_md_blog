---
layout: post
title: "Fast-LIVO2测试及论文解读"
date:   2025-01-26
tags: [SLAM, LiDAR]
comments: true
author: kwanwaipang
toc: true
---


<!-- * 目录
{:toc} -->

# 代码配置
按照官方给出的[Github仓库](https://github.com/hku-mars/FAST-LIVO2) step by step配置
1. Ubuntu, ROS, Sophus都是原本系统安装好的，直接跳过。
2. Mimalloc是可选项，也跳过
3. Vikit
~~~
cd catkin_ws/src
git clone https://github.com/xuankuzcr/rpg_vikit.git
~~~
4. livox_ros_driver。
Follow [livox_ros_driver Installation](https://github.com/Livox-SDK/livox_ros_driver).
5. 下载源码
~~~
cd ~/catkin_ws/src
git clone https://github.com/hku-mars/FAST-LIVO2

#直接cm
cd ../
catkin_make
source ~/catkin_ws/devel/setup.bash
~~~
6. 出现Sophus相关的报错.在“/home/kwanwaipang/catkin_ws/src/rpg_vikit/vikit_common/CMakeLists.txt”中添加下面代码即可
~~~
#添加Sophus_LIBRARIES
SET(Sophus_LIBRARIES "/usr/local/lib/libSophus.so")
~~~

<div align="center">
  <img src="./2025-01-26 12-19-37 的屏幕截图.png" width="60%" />
<figcaption>  
编译成功
</figcaption>
</div>


# 实验测试
~~~
roslaunch fast_livo mapping_avia.launch
rosbag play YOUR_DOWNLOADED.bag
~~~


# 论文解读


# 参考资料
* [FAST-LIVO2 Github](https://github.com/hku-mars/FAST-LIVO2)
* [paper link](https://arxiv.org/pdf/2408.14035)