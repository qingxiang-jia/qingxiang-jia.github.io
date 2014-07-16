---
layout: post
title: 转自｛UBUNTU 使用日记｝：Ubuntu Linux操作系统常用命令详细介绍
categories:
- Diandian
tags:
- Linux

---
Udo apt－get install 软件名 安装软件命令
<br />
<br />sudo nautilus 打开文件（有root权限）
<br />
<br />su root 切换到“root”
<br />
<br />ls 列出当前目录文件（不包括隐含文件）
<br />
<br />ls -a 列出当前目录文件（包括隐含文件）
<br />
<br />ls -l 列出当前目录下文件的详细信息
<br />
<br />cd .. 回当前目录的上一级目录
<br />
<br />cd - 回上一次所在的目录
<br />
<br />cd ~ 或 cd 回当前用户的宿主目录
<br />
<br />mkdir 目录名 创建一个目录
<br />
<br />rmdir 空目录名 删除一个空目录
<br />
<br />rm 文件名 文件名 删除一个文件或多个文件
<br />
<br />rm -rf 非空目录名 删除一个非空目录下的一切
<br />
<br />shixinyu
<br />
<br />mv 路经/文件 /经/文件 移动相对路经下的文件到绝对路经下
<br />
<br />mv 文件名 新名称 在当前目录下改名
<br />
<br />find 路经 -name “字符串” 查找路经所在范围内满足字符串匹配的文件和目录
<br />
<br />fdisk fdisk -l 查看系统分区信息
<br />
<br />fdisk fdisk /dev/sdb 为一块新的SCSI硬盘进行分区
<br />
<br />chown chown root /home 把/home的属主改成root用户
<br />
<br />chgrp chgrp root /home 把/home的属组改成root组
<br />
<br />Useradd 创建一个新的用户
<br />
<br />Groupadd 组名 创建一个新的组
<br />
<br />Passwd 用户名 为用户创建密码
<br />
<br />Passwd -d用户名 删除用户密码也能登陆
<br />
<br />Passwd -S用户名 查询账号密码
<br />
<br />Usermod -l 新用户名 老用户名 为用户改名
<br />
<br />Userdel–r 用户名 删除用户一切
<br />
<br />tar -c 创建包 –x 释放包 -v 显示命令过程 –z 代表压缩包
<br />
<br />tar –cvf benet.tar /home/benet 把/home/benet目录打包
<br />
<br />tar –zcvf benet.tar.gz /mnt 把目录打包并压缩
<br />
<br />tar –zxvf benet.tar.gz 压缩包的文件解压恢复
<br />
<br />tar –jxvf benet.tar.bz2 解压缩
<br />
<br />make 编译
<br />
<br />make install 安装编译好的源码包
<br />
<br />reboot Init 6 重启LINUX系统
<br />
<br />Halt Init 0 Shutdown –h now 关闭LINUX系统
<br />
<br />uname -a 查看内核版本
<br />
<br />cat /etc/issue 查看ubuntu版本
<br />
<br />lsusb 查看usb设备
<br />
<br />sudo ethtool eth0 查看网卡状态
<br />
<br />cat /proc/cpuinfo 查看cpu信息
<br />
<br />lshw 查看当前硬件信息
<br />
<br />sudo fdisk -l 查看磁盘信息
<br />
<br />df -h 查看硬盘剩余空间
<br />
<br />free -m 查看当前的内存使用情况
<br />
<br />ps -A 查看当前有哪些进程
<br />
<br />kill 进程号(就是ps -A中的第一列的数字)或者 killall 进程名( 杀死一个进程)
<br />
<br />kill -9 进程号 强制杀死一个进程
<br />
<br />常用apt命令：
<br />
<br />apt-cache search package 搜索包
<br />
<br />apt-cache show package 获取包的相关信息，如说明、大小、版本等
<br />
<br />sudo apt-get install package 安装包
<br />
<br />sudo apt-get install package - - reinstall 重新安装包
<br />
<br />sudo apt-get -f install 修复安装”-f = –fix-missing”
<br />
<br />sudo apt-get remove package 删除包
<br />
<br />sudo apt-get remove package - - purge 删除包，包括删除配置文件等
<br />
<br />sudo apt-get update 更新源
<br />
<br />sudo apt-get upgrade 更新已安装的包
<br />
<br />sudo apt-get dist-upgrade 升级系统
<br />
<br />sudo apt-get dselect-upgrade 使用 dselect 升级
<br />
<br />apt-cache depends package 了解使用依赖
<br />
<br />apt-cache rdepends package 是查看该包被哪些包依赖
<br />
<br />sudo apt-get build-dep package 安装相关的编译环境
<br />
<br />apt-get source package 下载该包的源代码
<br />
<br />sudo apt-get clean &amp;&amp; sudo apt-get autoclean 清理无用的包
<br />
<br />sudo apt-get check 检查是否有损坏的依赖
<br />
<br />清理所有软件缓存（即缓存在/var/cache/apt/archives目录里的deb包 ）
<br />
<br />sudo apt-get clean
<br />
<br />删除系统不再使用的孤立软件
<br />
<br />sudo apt-get autoremove
<br />
<br />
<br />1 文件管理 # ls ls -a 列出当前目录下的所有文件，包括以.头的隐含文件
<br />
<br />文件管理 # ls ls -l或ll 列出当前目录下文件的详细信息
<br />
<br />文件管理 # pwd pwd 查看当前所在目录的绝对路经
<br />
<br />文件管理 # cd cd .. 回当前目录的上一级目录
<br />
<br />文件管理 # cd cd - 回上一次所在的目录
<br />
<br />文件管理 # cd cd ~ 或 cd 回当前用户的宿主目录
<br />
<br />文件管理 # cd cd ~用户名 回指定用户的宿主目录
<br />
<br />2 文件管理 # mkdir mkdir 目录名 创建一个目录
<br />
<br />文件管理 # mkdir mkdir –p 递归式去创建一些嵌套目录
<br />
<br />文件管理 # rmdir Rmdir 空目录名 删除一个空目录
<br />
<br />3 文件管理 # rm rm 文件名 文件名 删除一个文件或多个文件
<br />
<br />文件管理 # rm rm -rf 非空目录名 递归删除一个非空目录下的一切，不让提式-f
<br />
<br />4 文件管理 # cat cat文件名 一屏查看文件内容
<br />
<br />5 文件管理 # more more文件名 分页查看文件内容
<br />
<br />6 文件管理 # less less 文件名 可控分页查看文件内容
<br />
<br />7 文件管理 # grep grep字符 文件名 根据字符匹配来查看文件部分内容
<br />
<br />8 文件管理 # mv mv 路经/文件 /经/文件 移动相对路经下的文件到绝对路经下
<br />
<br />文件管理 # mv mv 文件名 新名称 在当前目录下改名
<br />
<br />9 文件管理 # cp cp /路经/文件 ./ 移动绝对路经下的文件到当前目录下
<br />
<br />10 文件管理 # find find 路经 -name “字符串” 查找路经所在范围内满足字符串匹配的文件和目录
<br />
<br />11 文件管理 # ln ln 源文件 链接名 创建当前目录源文件的硬链接
<br />
<br />ln /home/test /usr/test1 在/usr下建立/home/test的硬链接
<br />
<br />12 文件管理 # ln Ln -s a b 创建当前目录下a的符号链接b
<br />
<br />13 文件管理 # touch touch file1 file2 创建两个空文件
<br />
<br />14 磁盘管理 # df df 用于报告文件系统的总容量，使用量，剩余容量。
<br />
<br />15 磁盘管理 # du du -b /home 查看目前/HOME目录的容量(k)及子目录的容量(k)。
<br />
<br />16 磁盘管理 # fdisk fdisk -l 查看系统分区信息
<br />
<br />17 磁盘管理 # fdisk fdisk /dev/sdb 为一块新的SCSI硬盘进行分区
<br />
<br />18 磁盘管理 # mkfs.ext3 Mkfs.ext3 /dev/sdb1
<br />
<br />为第一块SCSI硬盘的第一主分区格式化成
<br />
<br />ext3的文件系统
<br />
<br />mkfs.ext2 Mkfs.ext2/dev/sdb2 格式化成ext2文件系统
<br />
<br />19 磁盘管理 # mount mount -t 文件系统类型 设备路经 访问路经
<br />
<br />磁盘管理 # 文件系统类型
<br />
<br />Iso9660 光驱文件系统
<br />
<br />vfat Fat文件系统(windows)
<br />
<br />挂载光驱 # mount –t iso9660 /dev/cdrom /mnt/cdrom
<br />
<br />挂载FAT # mount –t vfat /dev/hda5 /mnt/cdrom 挂第一个ide的第五个逻辑分区
<br />
<br />17 磁盘管理 # Umount /mnt/cdrom 卸载/mnt/cdrom为空
<br />
<br />18 文件权限 # chmod chmod u+s file 为file的属主加上特殊权限
<br />
<br />chmod g+r file 为file的属组加上读权限
<br />
<br />chmod o+w file 为file的其它用户加上写权限
<br />
<br />chmod a-x file 为file的所有用户减去执行权限
<br />
<br />chmod 765 file 为file的属主设为完全权限，属组设成读写权，其它用户具有读和执心权限
<br />
<br />19 文件权限 # chown chown root /home 把/home的属主改成root用户
<br />
<br />20 文件权限 # chgrp chgrp root /home 把/home的属组改成root组
<br />
<br />21 打印管理 # redhat-config-printer-tui 进入安装打印机界面
<br />
<br />22 打印管理 # lp lp –d hptr file 打印file到hptr的打印机上
<br />
<br />23 打印管理 # lpq Lpq –P 打印机名 查看打印机的状态
<br />
<br />24 打印管理 # lprm Lprm –P 打印机名 a 删除打印机内的打印作业
<br />
<br />25 打印管理 # disable Disable –r “changing paper” HPtr 禁用打印机并提示原因
<br />
<br />26 打印管理 # enable Enable HPtr 重新启用被禁用的
<br />
<br />27 用户管理 # useradd Useradd 创建一个新的用户
<br />
<br />28 用户管理 # groupadd Groupadd 组名 创建一个新的组
<br />
<br />29 用户管理 # passwd Passwd 用户名 为用户创建密码
<br />
<br />30 用户管理 # Passwd -d Passwd -d用户名 删除用户密码也能登陆
<br />
<br />31 用户管理 # Passwd -l Passwd -l用户名 锁定账号密码
<br />
<br />32 用户管理 # Passwd -u Passwd -u用户名 解锁账号密码
<br />
<br />33 用户管理 # Passwd -S Passwd -S用户名 查询账号密码
<br />
<br />34 用户管理 # Usermod -l Usermod -l 新用户名 老用户名 为用户改名
<br />
<br />35 用户管理 # Usermod -L Usermod -L 要锁定用户名 锁定用户登陆
<br />
<br />36 用户管理 # Usermod -U Usermod –U解锁用户名 解锁用户登陆
<br />
<br />37 用户管理 # Usermod -u Usermod –u 501用户名 改变用户UID
<br />
<br />38 用户管理 # Userdel Userdel–r 用户名 删除用户一切
<br />
<br />39 用户管理 # Groupmod -n Groupmod –n新用户名 老用户名 为组改名
<br />
<br />40 用户管理 # Groupmod -g Groupmod –g 501 组名 改变组GID
<br />
<br />41 用户管理 # groupdel Groupdel组名 先应删它的用户 删除组
<br />
<br />42 用户管理 # gpasswd -a gpasswd -a 用户名 组名 增加用户到组
<br />
<br />43 用户管理 # Id id 用户名 查用户信息
<br />
<br />44 软件管理 # rpm -qa rpm –qa | less 查询已安装RPM
<br />
<br />45 软件管理 # rpm –qa | grep ftp 查询指定RPM
<br />
<br />46 软件管理 # rpm -q rpm -q 已安装的RPM包 查是否安装
<br />
<br />47 软件管理 # rpm -q telnet-server 查看telnet服务器包
<br />
<br />48 软件管理 # rpm -qi rpm –qi 软件包名称 查看软件的描述信息
<br />
<br />49 软件管理 # rpm -ql rpm –ql软件包名称 查询软件包的文件列表
<br />
<br />50 软件管理 # rpm -qf rpm –qf软件包名称 查询某个文件所属的软件包
<br />
<br />51 软件管理 # rpm -qp rpm –qp软件包全名 查询未安装的软件包信息
<br />
<br />52 软件管理 # rpm -e rpm –e 软件包名称 删除具体的软件包
<br />
<br />53 软件管理 # rpm -U rpm –Uvh软件包全名 升级软件包并显示过程
<br />
<br />54 软件管理 # rpm -ivh rpm –ivh 软件包全名 安装软件包并显示过程
<br />
<br />55 软件管理 # rpm -V rpm –V软件包名称 验证软件包的大小，类型等
<br />
<br />56 软件管理 # tar -c 创建包 –x 释放包 -v 显示命令过程 –z 代表压缩包
<br />
<br />57 软件管理 # tar -cf tar –cvf benet.tar /home/benet 把/home/benet目录打包
<br />
<br />58 软件管理 # tar -czf tar –zcvf benet.tar.gz /mnt 把目录打包并压缩
<br />
<br />59 软件管理 # tar –tf tar –tf benet.tar 看非压缩包的文件列表
<br />
<br />60 软件管理 # tar –tzf tar –tf benet.tar.gz 看压缩包的文件列表
<br />
<br />61 软件管理 # tar –xf tar –xf benet.tar 非压缩包的文件恢复
<br />
<br />62 软件管理 # tar –zxvf tar –zxvf benet.tar.gz 压缩包的文件解压恢复
<br />
<br />63 软件管理 # tar -jxvf tar –jxvf benet.tar.bz2
<br />
<br />64 软件管理 # diff diff file1 file2 &gt; 补丁名.patch 为新旧文件生成补丁文件
<br />
<br />65 软件管理 # diff diff file1 file2 比较两个文件的区别
<br />
<br />66 软件管理 # Patch Patch file补丁名.patch 打补丁
<br />
<br />67 软件管理 # ./configure –prefix=/usr/local/ 编译前配置
<br />
<br />68 软件管理 # make 编译
<br />
<br />69 软件管理 # make install 安装编译好的源码包
<br />
<br />70 启动管理 # reboot Init 6 重启LINUX系统
<br />
<br />71 启动管理 # Halt Init 0 Shutdown –h now 关闭LINUX系统
<br />
<br />72 启动管理 # runlevel 显示系统运行级
<br />
<br />73 启动管理 # Init [0123456] 改变系统运行级,7种
<br />
<br />74 启动管理 # Chkconfig –-list [服务名称] 查看服务的状态
<br />
<br />75 启动管理 # Chkconfig –-level on|off|set 设置服务的启动状态
<br />
<br />76 启动管理 # Chkconfig on|off|set 设置非独立服务启状态
<br />
<br />77 进程管理 # Top动态 Ps-aux静态 进程树pstree 查看系统进程
<br />
<br />78 进程管理 # 程序名 &amp; 后台运行程序
<br />
<br />79 进程管理 # fg 把后台运行的进程调回前台
<br />
<br />80 进程管理 # bg 把前台运行进程调到后台
<br />
<br />81 进程管理 # renice Renice +1 180 把180号进程的优先级加1
<br />
<br />82 进程管理 # kill Kill PID 终止某个PID进程
<br />
<br />83 进程管理 # at at 5pm + 3 days
<br />
<br />/bin/ls 指定三天后下午5:00执行/bin/ls
<br />
<br />84 进程管理 # crontab Crontab -e 用VI的形式来编辑自动周期性任务
<br />
<br />85 进程管理 # crontab Crontab -l 查看自动周期性任务
<br />
<br />86 进程管理 # crontab Crontab -r 删除自动周期性任务
<br />
<br />87 进程管理 # crond Service crond
<br />
<br />马上启动自动周期性服务 Service crond
<br />
<br />实现磁盘配额 (注安装LINUX时建立/home分区）
<br />
<br />目标：对用户zhao在/home目录上实现soft limit为5k,hard limit 为10k的磁盘配额
<br />
<br />实现步骤：
<br />
<br />1. 修改包含/home的行， #vi /etc/fstab， 改为：defaults,usrquota。也就是增加usrquota项。然后保存退出。
<br />
<br />2、卸载/home目录 #umount /home
<br />
<br />3. 挂接/home目录 #mount /home
<br />
<br />4、增加用户zhao #useradd zhao
<br />
<br />5、修改密码 #passwd zhao
<br />
<br />6、生成关于/home目录的quota信息 # quotacheck -cmug /home
<br />
<br />#quotacheck -vu /home
<br />
<br />7、查看所有用户的信息 #repquota -au
<br />
<br />8、设置配额 #edquota -u zhao
<br />
<br />将soft 和hard 分别改为5和10
<br />
<br />9、保存并退出 #wq!
<br />
<br />10、修改时间 #edquota -t
<br />
<br />11、 #wq!
<br />
<br />12.开启/home上的磁盘配额功能 #quotaon /home
<br />
<br />13.查询配额 #quota -u zhao
<br />
<br />14.验证配额 #su - zhao
<br />
<br />$touch myfile