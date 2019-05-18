---
title: TensorFlow Ubuntu Configuration
layout: post
categories: TensorFlow
tags: TensorFlow Ubuntu
excerpt: TensorFlow environmental installation and configuration

---
#### TensorFlow������װ������ <span id="home">
---

__�������£�Continually update��������__

---

##### ����
��װ������CUDA9.1+cuDNN7.1+Anaconda3.5+python3.6+TensorFlow1.7������װ������

https://zhuanlan.zhihu.com/p/28494550
--- 
###����Ubuntu��̬��ַ

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

>sudo gedit /etc/resolvconf/resolv.conf.d/base(����Чʹ��) 

---
###����U��
>sudo mkdir /mnt/usb

>df

>sudo mount /dev/sda1 /mnt/usb
>cd /mnt/usb

>sudo umount /mnt/usb
>sudo umount /dev/sda1 /mnt/usb
  
###�û���ubuntu����sudoers�ļ��У����½�������
>sudo gedit /etc/sudoers��ӣ�
>ubuntu  ALL=(ALL:ALL) ALL 

###Ubuntu16.04 �´������û�yang������sudoȨ��
>adduser username
>sudo gedit /etc/sudoers
>yang  ALL=(ALL:ALL) ALL 
---

###�޸�root����

>sudo passwd root

---
###Ubuntu 16.04+CUDA 9.1+cuDNN v7+OpenCV 3.4.0+Caffe+PyCharm ��ȫ��װָ�ϣ�������ȫ��(����CUDA 9.0)
https://blog.csdn.net/qq473179304/article/details/79444609

###Ubuntu16.04 ��װ CUDA9.2
https://blog.csdn.net/EliminatedAcmer/article/details/80528980

###tensorflow ��װGPU�汾�������ܽᣬ����Ƚ���ϸ
https://blog.csdn.net/gangeqian2/article/details/79358543

###Ubutu16.04+Cuda9.2/9.0+Cudnn7.12/7.05+TensorFlow-gpu-1.8/1.6
http://www.cnblogs.com/wjy-lulu/p/9119905.html

###Ubuntu 16.04 + Nvidia �Կ����� + Cuda 8.0 �������ܽ� + ���������
https://blog.csdn.net/zafir_410/article/details/73188228?utm_source=itdadao&utm_medium=referral

###Ubuntu+Tensorflow+CUDA8.0+cudnn
https://blog.csdn.net/icehui2012/article/details/62219008
http://www.52nlp.cn/%E6%B7%B1%E5%BA%A6%E5%AD%A6%E4%B9%A0%E4%B8%BB%E6%9C%BA%E7%8E%AF%E5%A2%83%E9%85%8D%E7%BD%AE-ubuntu16-04-geforce-gtx1080-tensorflow

###Ubuntu + CUDA9.0 + tensorflow-gpu ��װ����
https://blog.csdn.net/qq_35976351/article/details/79325476

---------
###1.��װ������
>sudo apt-get update   

>sudo apt-get install libprotobuf-dev libleveldb-dev libsnappy-dev libopencv-dev libhdf5-serial-dev protobuf-compiler  

>sudo apt-get install --no-install-recommends libboost-all-dev  
  
>sudo apt-get install libopenblas-dev liblapack-dev libatlas-base-dev  
  
>sudo apt-get install libgflags-dev libgoogle-glog-dev liblmdb-dev  
  
>sudo apt-get install git cmake build-essential  

###2.��װ�Կ�����
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

###Ubuntu�����޷�����ϵͳ���⣨NVIDIA�Կ�������أ�
https://blog.csdn.net/ezhchai/article/details/78788564
https://blog.csdn.net/ezhchai/article/details/80525207
>sudo vim /etc/default/grub 

GRUB_CMDLINE_LINUX_DEFAULT=��quiet splash���ĳ�GRUB_CMDLINE_LINUX_DEFAULT=��quiet splash nomodeset��

>sudo update-grub

###3.���û�������
>sudo gedit ~/.bashrc  

    export LD_LIBRARY_PATH=/usr/lib/x86_64-linux-gnu:$LD_LIBRARY_PATH  
    export LD_LIBRARY_PATH=/lib/x86_64-linux-gnu:$LD_LIBRARY_PATH

###4.��װ CUDA 9.1
>sudo apt-get install freeglut3-dev build-essential libx11-dev libxmu-dev libxi-dev libgl1-mesa-glx libglu1-mesa libglu1-mesa-dev  

>sudo sh cuda_9.1.85_387.26_linux.run --no-opengl-libs 

>sudo gedit ~/.bashrc 

    export PATH=/usr/local/cuda/bin:$PATH
    export LD_LIBRARY_PATH=/usr/local/cuda/lib64:$LD_LIBRARY_PATH  

>source ~/.bashrc  

>cd /usr/local/cuda-9.1/samples/1_Utilities/deviceQuery  
>sudo make  
>./deviceQuery  

###��װcuDNN v7
>cd cuda/include
  
    sudo cp cudnn.h /usr/local/cuda/include/ #����ͷ�ļ�
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
###Ubuntu16.04��װAnaconda3.5
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
###�鿴�Ѱ�װTensorFlow�汾�Ͱ�װ·��
>python

>import tensorflow as tf

    tf.\__version__
    tf.\__path__
---
###��ȫж��tensorflow
�鿴tensorflow�汾
>sudo pip show tensorflow

ж�أ�
>sudo pip uninstall protobuf
>sudo pip uninstall tensorflow
��װ��
>sudo pip install --upgrade https://storage.googleapis.com/tensorflow/linux/cpu/tensorflow-0.8.0-cp27-none-linux_x86_64.whl
###��װpip
>sudo apt-get install python-pip python-dev build-essential
sudo pip install --upgrade pip
sudo -H python -m pip install --upgrade pip

    ���⣺ʹ��pip����
    Traceback (most recent call last):
    File "/usr/bin/pip3", line 9, in <module>
    from pip import main
    ImportError: cannot import name 'main'
>sudo python -m pip uninstall pip && sudo apt install python-pip --reinstall

    ��ubuntu��ʹ��pip��һ�´���: 
    /usr/bin/pip: No such file or directory pip can no longer be found:

���Բ������·�ʽ���
>which pip 
>pip 
>type pip 
>hash -r 

###Anaconda��jupyter notebook������tensorflow
(���ImportError : No Moduled Name "tensorflow)
>��/home/ubuntu/anaconda3/lib/python3.6/site-packages

    �½�path.pth,��ӣ�
>/home/ubuntu/anaconda3/envs/tensorflow36/lib/python3.6/site-packages

###jupyter notebook��python2��python3����
https://www.cnblogs.com/pertor/p/8728291.html
 �����װ��python2����python3��
>python2 -m pip install ipykernel
>python2 -m ipykernel install --user

>python3 -m pip install ipykernel
>python3 -m ipykernel install --user 
###Ubuntu16.04��װTeamviewer

https://www.teamviewer.com/zhcn/download/linux/

>sudo apt-get -f install
>sudo dpkg -i teamviewer_13.1.8286_amd64.deb
>teamviewer
---
### Ubuntu16.04��װ�ѹ�ƴ�����뷨���������뷨��
https://www.cnblogs.com/darklights/p/7722861.html
###Ubuntu 16.04��װ�ȸ� Chrome �����
https://blog.csdn.net/wql2014302721/article/details/78571362

---

###Ubuntu16.04��װpycharm
https://blog.csdn.net/yucicheung/article/details/79336258

http://www.jetbrains.com/pycharm/download/#section=linux

sh ./pycharm.sh #�ڽ�ѹ���ļ�Ŀ¼��bin/��ִ��

---
###Ubuntu 16.04 �û���¼������ѭ������Ľ��
    ����1��
>CTRL+ALT+F1�����ı�ģʽ
> sudo apt-get remove nvidia-*
> sudo apt-get autoremove
> sudo nvidia-uninstall
>reboot
>Ctrl+Alt+F1
>sudo service lightdm stop
>sudo bash NVIDIA-Linux-x86_64-390.48.run -no-x-check -no-nouveau-check -no-opengl-files

https://blog.csdn.net/miclover_feng/article/details/79201865

    ����2��
>sudo add-apt-repository ppa:graphics-drivers/ppa
>sudo apt-get update
> sudo apt-get remove --purge nvidia-*
>sudo apt-get autoremove #�ر���Ҫ
>sudo apt-get install -f #�ر���Ҫ
>sudo reboot
>sudo apt-get install nvidia-384

https://www.jianshu.com/p/d45434f28ca0 

---
### ubuntu��װϵͳ
���⣺nouveau 000:01:00.0: fifo: SCHED_ERROR 08
  1. BIOSѡ�������U�̣���˶��������������ԣ���F8���롣
��ʾInstall Ubuntu���Ȳ�Ҫ��install Ubuntu���ѡ���F6����
��e��������༭ҳ�棬�ڵ����ڶ����У�ro quiet splash�������nomodeset����������ϵͳ�󲻻���Ϊ����������������º����ˡ�
   2. ��������ESC�����뵽grub����e������༭�������ڶ����ҵ�quiet splash�� ��quiet splash $vt_handoff��Ϊquiet splash nomodeset��ctrl+x������

###�鿴�Կ�����

>lshw -c video

�鿴configurure��driver����

>nvidia-smi

----

###�鿴GPU�ͺ�

>lspci | grep -i vga

---

###�鿴NVIDIA�����汾

>sudo dpkg --list | grep nvidia-*

###�鿴���̿ռ�
>sudo fdisk -l

>df -h

###ubuntu��which��find��whereis��locate����
>which ֻ��Ѱ�ҿ�ִ���ļ� ������PATH��������Ѱ�ҡ�
find ��ֱ����Ӳ������Ѱ������ǿ�󣬵���Ӳ�̣�һ�㲻Ҫ�á�
whereis ��linux�ļ����ݿ⣨/var/lib/slocate/slocate.db��Ѱ�ң������п����ҵ��ո�ɾ��������û�з����½����ļ���ȫ��ƥ�䡣
locate ͬ��,�����ļ����ǲ���ƥ�䡣

---

### 1���鿴�ڴ�Ĳ�������Ѿ�ʹ�ö��ٲ�ۡ�ÿ���ڴ�����ʹ���ڴ���
>sudo dmidecode|grep -P -A5 "Memory\s+Device"|grep Size|grep -v Range

### 2���鿴�ڴ�֧�ֵ�����ڴ�����

>?sudo dmidecode|grep -P 'Maximum\s+Capacity'

### 3���鿴�ڴ��Ƶ��

>sudo dmidecode|grep -A16 "Memory Device"

>sudo dmidecode|grep -A16 "Memory Device"|grep 'Speed'

---

> �����ƣ�To be added~��

---


##### �ο����� <span id="4">
* [Your CPU supports instructions that this TensorFlow binary was not compiled to use: AVX2 FMA](https://blog.csdn.net/hq86937375/article/details/79696023)
* [�����deeplearning�γ���ҵ����](https://blog.csdn.net/pkrobbie/article/details/79346722)
* [Tensorflow Ubuntu16.04�ϰ�װ��CPU����tensorboard��CNN��RNNͼ�Ľ̳�](https://blog.csdn.net/wizen641372472/article/details/72675549)
* [Win10 �°�װUbuntu 16.04˫ϵͳ���](https://blog.csdn.net/cqfdcw/article/details/79522509)


---
##### **����[����](#home)**