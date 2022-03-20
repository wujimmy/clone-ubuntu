2022-3-20
说明 by wujimmy
ubuntu 克隆
- 一、新硬盘分区设置：
- 1、查找硬盘所在盘号 fdisk -l ，假如为 /dev/sda
- 2、修改成1个分区，并格式化成ext4
-   1）设置分区： fdisk /dev/sda ,进入fdisk命令中，d删除分区，n添加分区：再输入p设为主分区，w把分区表写入硬盘
-   2）格式分为ext4分区：mkfs.ext4 -n /dev/sda1
- 二、系统拷贝：
- 3、下载拷贝脚本并进行分区拷贝，选择目标分区，必须是ext4分区。
wget  https://raw.githubusercontent.com/wujimmy/clone-ubuntu/master/clone-ubuntu.sh && chmod a+x clone-ubuntu.sh && sudo clone-ubuntu.sh
- 4、修复引导记录：
-   1）挂载分区到目录/mnt/ubuntu/
-   2）修复：sudo grub-install --boot-directory=/mnt/ubuntu/boot /dev/sd*  (说明，这里sd*应该是新硬盘所在的盘号，不是分区号，即不带数字的)

- 
参考自：
https://www.howtogeek.com/114884/how-to-repair-grub2-when-ubuntu-wont-boot/
The Terminal Method 下面的内容


clone-ubuntu.sh
a bash for clone ubuntu to another disk
reference:https://askubuntu.com/questions/1028604/bash-script-to-backkup-clone-ubuntu-to-another-partition/1028605#1028605
used by:https://www.toutiao.com/i6759054484191576579/
