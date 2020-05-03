# **__那些年走过的坑__**
# Linux_ubuntu 16.04 

> ## [U盘 copy]
> 1. 通过U盘copy,会发现文件夹中的所有文件都变为了绿色.修复方法:
    >>使用以下命令修改所有文件夹的权限 <p>find src/ -type d -exec chmod 775 {} \;</p>
    >>使用以下命令修改所有文件的权限 <p>find src/ -type f -exec chmod 664 {} \;</p>

> ## [软件安装]
> **换源操作**
    >> 1. __系统换源__: Ubuntu系统可以通过 系统设置->软件和更新->ubuntu软件 选择源
    >> 2. __pip换源__: 使用python pip安装包时常常会因为网络原因出现一大'红色错误', 换为国内源后下载速度快了,红色错误也消失了. 
        >>> __操作__: 
        >>> * mkdir ~/.pip -> vim .pip/pip.conf -> input 
        >>> * [global]
        >>> * index-url = https://pypi.tuna.tsinghua.edu.cn/simple
        >>> * trusted-host = pypi.tuna.tsinghua.edu.cn
    >> * tip:在linux下使用python, 直接使用自带的即可,强行更换可能会使系统崩溃        
>        
> **软件**
    >>  软件 | 类型 | 功能 
    >> |:----:|:----:|:----:|
    >> VScode-insider | IDE | for code
    >> matlab | IDE | for code
    >> ROS | develope | for ROS code
    >> chrome | explorer | for surf internet
    >> wechart | Social-contact | for communication
    >> terminator | \ | for linux
    >> System-monitor | \ | for cup & mem

> ## [常用命令]
> **查找**
    >> 1. find \<path> [-name|-type] [pattern] | grep/-exec
    >> 2. grep -rn \<pattern> <path|file>
>
> **压缩**
    >> 1. tar 
    >> * 压缩: tar zxvf 压缩包名字.tar.gz [-C 解压path] 
    >> * 解压: tar zcvf 压缩包名字 压缩对象...
    >>
    >> 2. rar
    >> * 压缩: rar a 压缩包名字 压缩对象 [-r:压缩目录]
    >> * 解压: rar x 压缩包名字 指定目录
    >>
    >> 3. zip
    >> * 压缩: zip 压缩包名字 压缩对象 [-r:压缩目录]
    >> * 解压: unzip 压缩包名字 [-d:解压目录]
     
