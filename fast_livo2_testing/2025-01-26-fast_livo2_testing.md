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
修改launch文件直接开启的时候播包会方便些，修改代码请见[link](https://github.com/KwanWaiPang/Fast-LIVO2_comment/blob/main/launch/mapping_avia.launch)

效果如下所示：


其中对于CBD_Building_02的测试发现有存在比较明显的drift的情况。如下图所示，实验人员应该是试图回到起点的，但是最终的位置与起始的位置差别较大。并且从生成的彩色点云也可以看到柱子的地方有较为明显的偏移。
<div align="center">
  <img src="./2025-01-26 12-52-32 的屏幕截图.png" width="80%" />
<figcaption>  
</figcaption>
</div>



# 论文解读







# 代码解读
请见：[Fast-LIVO2代码解读](https://github.com/KwanWaiPang/Fast-LIVO2_comment)


# 参考资料
* [FAST-LIVO2 Github](https://github.com/hku-mars/FAST-LIVO2)
* [paper link](https://arxiv.org/pdf/2408.14035)