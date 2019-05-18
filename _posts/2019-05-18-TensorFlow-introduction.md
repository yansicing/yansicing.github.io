---
title: TensorFlow Ubuntu Configuration
layout: post
categories: TensorFlow
tags: TensorFlow Ubuntu
excerpt: TensorFlow environmental installation and configuration

---
#### TensorFlow环境安装与配置 <span id="home">
---

__持续更新（Continually update···）__

---

##### 内容
安装环境：CUDA9.1+cuDNN7.1+Anaconda3.5+python3.6+TensorFlow1.7环境安装与配置

https://zhuanlan.zhihu.com/p/28494550
--- 
###配置Ubuntu静态地址

>sudo gedit /etc/network/interfaces

    interfaces(5) file used by ifup(8) and ifdown(8)

    auto enp6s0

    iface enp6s0 inet static

    address 192.168.0.26

    netmask 255.255.255.0

    broadcast 192.168.0.255

    gateway 192.168.0.1

>sudo gedit /etc/resolv.conf

    nameserver 114.114.114.114

>sudo /etc/init.d/networking restart

>sudo gedit /etc/resolvconf/resolv.conf.d/base(如无效使用) 

---
###挂载U盘
>sudo mkdir /mnt/usb

>df

>sudo mount /dev/sda1 /mnt/usb
>cd /mnt/usb

>sudo umount /mnt/usb
>sudo umount /dev/sda1 /mnt/usb
  
###用户名ubuntu不在sudoers文件中，此事将被报告
>sudo gedit /etc/sudoers添加：
>ubuntu  ALL=(ALL:ALL) ALL 

###Ubuntu16.04 下创建新用户yang并赋予sudo权限
>adduser username
>sudo gedit /etc/sudoers
>yang  ALL=(ALL:ALL) ALL 
---

###修改root密码

>sudo passwd root

---
###Ubuntu 16.04+CUDA 9.1+cuDNN v7+OpenCV 3.4.0+Caffe+PyCharm 完全安装指南，国内最全！(适用CUDA 9.0)
https://blog.csdn.net/qq473179304/article/details/79444609

###Ubuntu16.04 安装 CUDA9.2
https://blog.csdn.net/EliminatedAcmer/article/details/80528980

###tensorflow 安装GPU版本，个人总结，步骤比较详细
https://blog.csdn.net/gangeqian2/article/details/79358543

###Ubutu16.04+Cuda9.2/9.0+Cudnn7.12/7.05+TensorFlow-gpu-1.8/1.6
http://www.cnblogs.com/wjy-lulu/p/9119905.html

###Ubuntu 16.04 + Nvidia 显卡驱动 + Cuda 8.0 （问题总结 + 解决方案）
https://blog.csdn.net/zafir_410/article/details/73188228?utm_source=itdadao&utm_medium=referral

###Ubuntu+Tensorflow+CUDA8.0+cudnn
https://blog.csdn.net/icehui2012/article/details/62219008
http://www.52nlp.cn/%E6%B7%B1%E5%BA%A6%E5%AD%A6%E4%B9%A0%E4%B8%BB%E6%9C%BA%E7%8E%AF%E5%A2%83%E9%85%8D%E7%BD%AE-ubuntu16-04-geforce-gtx1080-tensorflow

###Ubuntu + CUDA9.0 + tensorflow-gpu 安装过程
https://blog.csdn.net/qq_35976351/article/details/79325476

---------
###1.安装依赖包
>sudo apt-get update   

>sudo apt-get install libprotobuf-dev libleveldb-dev libsnappy-dev libopencv-dev libhdf5-serial-dev protobuf-compiler  

>sudo apt-get install --no-install-recommends libboost-all-dev  
  
>sudo apt-get install libopenblas-dev liblapack-dev libatlas-base-dev  
  
>sudo apt-get install libgflags-dev libgoogle-glog-dev liblmdb-dev  
  
>sudo apt-get install git cmake build-essential  

###2.安装显卡驱动
https://www.geforce.cn/drivers
>sudo gedit /etc/modprobe.d/blacklist-nouveau.conf 

    blacklist nouveau  
    options nouveau modeset=0 

>sudo update-initramfs -u  

>lsmod | grep nouveau  

>sudo apt-get remove nvidia-*
sudo apt-get autoremove
sudo nvidia-uninstall
reboot
Ctrl+Alt+F1
sudo service lightdm stop
sudo bash NVIDIA-Linux-x86_64-390.48.run -no-x-check -no-nouveau-check -no-opengl-files
sudo service lightdm restart

>nvidia-settings  

###Ubuntu开机无法进入系统问题（NVIDIA显卡驱动相关）
https://blog.csdn.net/ezhchai/article/details/78788564
https://blog.csdn.net/ezhchai/article/details/80525207
>sudo vim /etc/default/grub 

GRUB_CMDLINE_LINUX_DEFAULT=”quiet splash”改成GRUB_CMDLINE_LINUX_DEFAULT=”quiet splash nomodeset”

>sudo update-grub

###3.配置环境变量
>sudo gedit ~/.bashrc  

    export LD_LIBRARY_PATH=/usr/lib/x86_64-linux-gnu:$LD_LIBRARY_PATH  
    export LD_LIBRARY_PATH=/lib/x86_64-linux-gnu:$LD_LIBRARY_PATH

###4.安装 CUDA 9.1
>sudo apt-get install freeglut3-dev build-essential libx11-dev libxmu-dev libxi-dev libgl1-mesa-glx libglu1-mesa libglu1-mesa-dev  

>sudo sh cuda_9.1.85_387.26_linux.run --no-opengl-libs 

>sudo gedit ~/.bashrc 

    export PATH=/usr/local/cuda/bin:$PATH
    export LD_LIBRARY_PATH=/usr/local/cuda/lib64:$LD_LIBRARY_PATH  

>source ~/.bashrc  

>cd /usr/local/cuda-9.1/samples/1_Utilities/deviceQuery  
>sudo make  
>./deviceQuery  

###安装cuDNN v7
>cd cuda/include
  
    sudo cp cudnn.h /usr/local/cuda/include/ #复制头文件
>cd ../lib64

    sudo cp lib* /usr/local/cuda/lib64/   
    cd /usr/local/cuda/lib64/   
    sudo rm -rf libcudnn.so libcudnn.so.7  
    sudo ln -s libcudnn.so.7.0.5 libcudnn.so.7
    sudo ln -s libcudnn.so.7 libcudnn.so 

>sudo apt-get install vim-gtk  

>sudo vim /etc/ld.so.conf.d/cuda.conf  

    /usr/local/cuda/lib64

>sudo ldconfig

>sudo ldconfig -v

>nvcc -V 
----
###Ubuntu16.04安装Anaconda3.5
>sudo bash  Anaconda3-5.1.0-Linux-x86_64.sh

    anaconda-navigator

>sudo gedit /etc/profile

    sudo vim /etc/profile
    sudo vim ~/.bashrc

>export PATH="/home/ubuntu/anaconda3/bin:$PATH"

> source /etc/profile

    source ~/.bashrc

  > echo $PATH

    python --version

    conda --version

    conda list

   > conda info --envs

>conda update -n base conda

    conda update conda

> conda create -n tensorflow36 python=3.6

    conda remove -n tensorflow36 --all

>conda config --add channels 
    https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/free/
>conda config --set show_channel_urls yes

>conda install numpy

>source activate tensorflow36

    source deactivate

>sudo apt install python3-pip

    python3 -m pip install --upgrade pip --force-reinstall

> pip install \
  -i https://pypi.tuna.tsinghua.edu.cn/simple/ \
  https://mirrors.tuna.tsinghua.edu.cn/tensorflow/linux/gpu/

>python
  
    import tensorflow as tf

    hello=tf.constant('hello,Tensorflow')

    sess=tf.Session()

    print(sess.run(hello))

>pip3 install tf_nightly-1.6.0.dev20180114-cp36-cp36m-manylinux1_x86_64.whl
---
###查看已安装TensorFlow版本和安装路径
>python

>import tensorflow as tf

    tf.\__version__
    tf.\__path__
---
###完全卸载tensorflow
查看tensorflow版本
>sudo pip show tensorflow

卸载：
>sudo pip uninstall protobuf
>sudo pip uninstall tensorflow
安装：
>sudo pip install --upgrade https://storage.googleapis.com/tensorflow/linux/cpu/tensorflow-0.8.0-cp27-none-linux_x86_64.whl
###安装pip
>sudo apt-get install python-pip python-dev build-essential
sudo pip install --upgrade pip
sudo -H python -m pip install --upgrade pip

    问题：使用pip出现
    Traceback (most recent call last):
    File "/usr/bin/pip3", line 9, in <module>
    from pip import main
    ImportError: cannot import name 'main'
>sudo python -m pip uninstall pip && sudo apt install python-pip --reinstall

    在ubuntu中使用pip报一下错误: 
    /usr/bin/pip: No such file or directory pip can no longer be found:

可以采用以下方式解决
>which pip 
>pip 
>type pip 
>hash -r 

###Anaconda的jupyter notebook中配置tensorflow
(解决ImportError : No Moduled Name "tensorflow)
>在/home/ubuntu/anaconda3/lib/python3.6/site-packages

    新建path.pth,添加：
>/home/ubuntu/anaconda3/envs/tensorflow36/lib/python3.6/site-packages

###jupyter notebook下python2和python3共存
https://www.cnblogs.com/pertor/p/8728291.html
 如果安装了python2和者python3：
>python2 -m pip install ipykernel
>python2 -m ipykernel install --user

>python3 -m pip install ipykernel
>python3 -m ipykernel install --user 
###Ubuntu16.04安装Teamviewer

https://www.teamviewer.com/zhcn/download/linux/

>sudo apt-get -f install
>sudo dpkg -i teamviewer_13.1.8286_amd64.deb
>teamviewer
---
### Ubuntu16.04安装搜狗拼音输入法（中文输入法）
https://www.cnblogs.com/darklights/p/7722861.html
###Ubuntu 16.04安装谷歌 Chrome 浏览器
https://blog.csdn.net/wql2014302721/article/details/78571362

---

###Ubuntu16.04安装pycharm
https://blog.csdn.net/yucicheung/article/details/79336258

http://www.jetbrains.com/pycharm/download/#section=linux

sh ./pycharm.sh #在解压缩文件目录的bin/下执行

---
###Ubuntu 16.04 用户登录界面死循环问题的解决
    方法1：
>CTRL+ALT+F1进入文本模式
> sudo apt-get remove nvidia-*
> sudo apt-get autoremove
> sudo nvidia-uninstall
>reboot
>Ctrl+Alt+F1
>sudo service lightdm stop
>sudo bash NVIDIA-Linux-x86_64-390.48.run -no-x-check -no-nouveau-check -no-opengl-files

https://blog.csdn.net/miclover_feng/article/details/79201865

    方法2：
>sudo add-apt-repository ppa:graphics-drivers/ppa
>sudo apt-get update
> sudo apt-get remove --purge nvidia-*
>sudo apt-get autoremove #特别重要
>sudo apt-get install -f #特别重要
>sudo reboot
>sudo apt-get install nvidia-384

https://www.jianshu.com/p/d45434f28ca0 

---
### ubuntu重装系统
问题：nouveau 000:01:00.0: fifo: SCHED_ERROR 08
  1. BIOS选择启动项到U盘，华硕主板电脑启动电脑，按F8进入。
显示Install Ubuntu，先不要点install Ubuntu这个选项。按F6，再
按e键，进入编辑页面，在倒数第二行中，ro quiet splash后面添加nomodeset，这样进入系统后不会因为独显驱动问题而导致黑屏了。
   2. 重启，狂按ESC，进入到grub，按e，进入编辑。导数第二行找到quiet splash， 将quiet splash $vt_handoff改为quiet splash nomodeset，ctrl+x重启。

###查看显卡驱动

>lshw -c video

查看configurure有driver字样

>nvidia-smi

----

###查看GPU型号

>lspci | grep -i vga

---

###查看NVIDIA驱动版本

>sudo dpkg --list | grep nvidia-*

###查看磁盘空间
>sudo fdisk -l

>df -h

###ubuntu的which、find、whereis、locate命令
>which 只能寻找可执行文件 ，并在PATH变量里面寻找。
find 是直接在硬盘上搜寻，功能强大，但耗硬盘，一般不要用。
whereis 从linux文件数据库（/var/lib/slocate/slocate.db）寻找，所以有可能找到刚刚删除，或者没有发现新建的文件，全部匹配。
locate 同上,不过文件名是部分匹配。

---

### 1、查看内存的插槽数，已经使用多少插槽。每条内存多大，已使用内存多大
>sudo dmidecode|grep -P -A5 "Memory\s+Device"|grep Size|grep -v Range

### 2、查看内存支持的最大内存容量

>?sudo dmidecode|grep -P 'Maximum\s+Capacity'

### 3、查看内存的频率

>sudo dmidecode|grep -A16 "Memory Device"

>sudo dmidecode|grep -A16 "Memory Device"|grep 'Speed'

---

> 待完善（To be added~）

---


##### 参考文献 <span id="4">
* [Your CPU supports instructions that this TensorFlow binary was not compiled to use: AVX2 FMA](https://blog.csdn.net/hq86937375/article/details/79696023)
* [吴恩达deeplearning课程作业环境](https://blog.csdn.net/pkrobbie/article/details/79346722)
* [Tensorflow Ubuntu16.04上安装及CPU运行tensorboard、CNN、RNN图文教程](https://blog.csdn.net/wizen641372472/article/details/72675549)
* [Win10 下安装Ubuntu 16.04双系统详解](https://blog.csdn.net/cqfdcw/article/details/79522509)


---
##### **返回[顶部](#home)**