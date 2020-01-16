# **__那些年走过的坑__**
# ROS

> ## [install]
    >> ros安装步骤简单,但安装过程困难,若安装不成功考虑以下步骤:
    >>> 1. 换源(换为国内源)
    >>> 2. 修改timeout limit
    >>> 3. 修改hosts

> ## [Command]
    >>  cmd | comment
    >> |:----:|:----:|:----:|
    >>  roscore | 开启ros 
    >>  rosrun | 运行一个node
    >>  roslaunch | 运行一个launch文件
    >>  rospack | 对系统中的pkg操作
    >>  rosmsg | 对系统中的msg操作
    >>  rossrv | 对系统中的srv操作
    >>  rostopic | 对正在运行的topic操作
    >>  rosservice | 对正在运行的service操作
    >>  rosparam | 对正在运行的param操作
    >>  rosbag | 录制或播放rosbag
    >>  catkin_make | initial工作空间 或则 编译工作空间
    >>  ---
    >>  tip:当发现一些命令不好使时,直接 source devel/setup.bash


> ## [Build]
    >> __package.xml__ 文件
        >>> 1. 添加所依赖的pkg即可
        >>> 2. 若有自定义消息类型, 需要添加一下两行
            >>>> __<build_depend>message_generation</build_depend>__
            >>>> __<exec_depend>message_runtime</exec_depend>__
        >>> 3. 若使用工程中其他pkg的文件,也需要啊添加工程中的这个pkg
    >>
    >> __CMakeLists.txt__ 文件
        >>> 1. 在 __find_package(catkin REQUIRED COMPONENTS pkg_name ...)__ 中添加所需要的pkg, 这一项代表的是find catkin所需要的pkg
        >>> 2. __catkin_package()__ 选项中目的是告诉catkin_workspace, 在当前pkg中有include..., 相当于向外公布,以便于其他的pkg使用当前pkg中的.h或者其他
        >>> 3. __include_directories(include  ${catkin_INCLUDE_DIRS})__ 是针对与当前pkg的, 其目的是告诉当前的pkg,所需要的.h以及其他所在的位置, 选项中的:  
        __include__ 是指当前pkg中的include文件夹,   
        __${catkin_INCLUDE_DIRS}__ 指的是catkin_workspace中的.h

> ## [ROS_python]
    >> 1. 使用 __ROS_python__ 时, scripts文件中的.py文件不能与ros pkg重名
    >> 2. __ROS_python__ 编程, 第一行需添加 __#!/usr/bin/env python3__ 意为选择编译程序的编译器
    >> 3. 运行Python节点方法:  
    ①python3 + file_name;  
    ②(推荐) 将file chmod 755 为可执行文件, 然后 rosrun pkg_name file_name