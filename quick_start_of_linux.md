# Quick start of Linux
# Abstract
This article recorded some useful fundamental commands that I came across at the beginning of my linux learning. 


# 目录结构
/ 根目录
bin           放普通用户的命令
boot         linux的核心文件 如mrb镜像 grub启动
dev          硬件 如串口
etc           系统配置文件 如config
lib            存放动态库
mnt          挂载不同设备
proc         存放cpu 内存 硬件信息
sbin          存放超级用户命令
tmp          临时名录 放置临时信息
usr          类似windows的program file   内有src(source),bin,sbin
var           存放变动性信息 log spool cache


# ls的用法

绝对路径 以/起始 如/home/user1/abc.txt
相对路径 user1/abc.txt

查找帮助：
man 命令  
info 命令
help 命令
命令 --help

TAB 敲两次 出现所有可能结果

ls -l详细列出所有文件
ls -1列出所有文件

cd..  回到上层目录

cd 回到家目录

cd -回到之前所在目录

linux中 所有以点开头的文件都是隐藏的文件

ls -a 显示所有文件 包括隐藏文件

Linux命令执行机制：翻译+执行 如ls  系统先执行ls=ls --color 然后在执行ls --color   alias ls=ls可设置回来
在比如 alias ubuntu=ls 这样执行ubuntu这条命令时 系统会把ubuntu解释成ls

输入ls -l
```
$ ls -l
-rw-r--r-- 1 bearthur bearthur 13553300 2008-12-06 09:51 AdobeAIRInstaller.bin
-rw-r--r-- 1 bearthur bearthur 13553300 2008-12-06 09:51 AdobeAIRInstaller.bin.1
-rw-r--r-- 1 bearthur bearthur      179 2011-01-28 14:24 examples.desktop
drwxr-xr-x 2 bearthur bearthur     4096 2011-01-29 17:30 f3
-rw-r--r-- 1 root     root            0 2011-01-29 17:17 file2
-rw-r--r-- 1 bearthur bearthur 19014323 2011-01-28 23:10 out.ogv
-rw-r--r-- 1 bearthur bearthur   646320 2011-01-28 23:26 wget-log
drwxr-xr-x 2 bearthur bearthur     4096 2011-01-28 14:42 公共的
drwxr-xr-x 2 bearthur bearthur     4096 2011-01-28 14:42 模板
drwxr-xr-x 2 bearthur bearthur     4096 2011-01-28 14:42 视频
drwxr-xr-x 2 bearthur bearthur     4096 2011-01-28 14:42 图片
drwxr-xr-x 2 bearthur bearthur     4096 2011-01-29 17:13 文档
drwxr-xr-x 2 bearthur bearthur     4096 2011-01-28 22:42 下载
drwxr-xr-x 2 bearthur bearthur     4096 2011-01-28 14:42 音乐
drwxr-xr-x 2 bearthur bearthur     4096 2011-01-28 23:13 桌面
```
第一列：d表示目录 -表示文件
第二到第九十列：r读 w写 x执行 -表示对应的rwx无权限   第一个rwx表示文件所有者权限，第二个表示组权限 第三个表示其他用户权限
第一个bearthur表示用户 第二个bearthur表示用户所在组 后面数字表示文件或是目录大小


chmod o-r 文件名或目录名     表示减去其他用户的可读权限
chmod g-w 文件名或目录名     表示减去组用户的可写权限



# 查看计算机信息

## 查看cpu信息：sudo cat /proc/cpuinfo
```
$ sudo cat /proc/cpuinfo
processor    : 0
vendor_id    : GenuineIntel
cpu family    : 6
model        : 23
model name    : Intel(R) Core(TM)2 Duo CPU     T6670  @ 2.20GHz
stepping    : 10
cpu MHz        : 2201.000
cache size    : 2048 KB
physical id    : 0
siblings    : 2
core id        : 0
cpu cores    : 2
apicid        : 0
initial apicid    : 0
fdiv_bug    : no
hlt_bug        : no
f00f_bug    : no
coma_bug    : no
fpu        : yes
fpu_exception    : yes
cpuid level    : 13
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm sse4_1 xsave lahf_lm ida tpr_shadow vnmi flexpriority
bogomips    : 4399.66
clflush size    : 64
cache_alignment    : 64
address sizes    : 36 bits physical, 48 bits virtual
power management:

processor    : 1
vendor_id    : GenuineIntel
cpu family    : 6
model        : 23
model name    : Intel(R) Core(TM)2 Duo CPU     T6670  @ 2.20GHz
stepping    : 10
cpu MHz        : 1200.000
cache size    : 2048 KB
physical id    : 0
siblings    : 2
core id        : 1
cpu cores    : 2
apicid        : 1
initial apicid    : 1
fdiv_bug    : no
hlt_bug        : no
f00f_bug    : no
coma_bug    : no
fpu        : yes
fpu_exception    : yes
cpuid level    : 13
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm sse4_1 xsave lahf_lm ida tpr_shadow vnmi flexpriority
bogomips    : 4399.94
clflush size    : 64
cache_alignment    : 64
address sizes    : 36 bits physical, 48 bits virtual
power management:
```
## 查看内存：sudo cat /proc/meminfo
## 查看硬盘：sudo fdisk -l
## 查看显卡：lspci
## 查看USB接口：lsusb
## 查看驱动：lsmod
##  查看kernel版本：uname
```
bearthur@bearthur-Lenovo-G450:~$ uname
Linux
bearthur@bearthur-Lenovo-G450:~$ uname -v
#33-Ubuntu SMP Sun Sep 19 20:34:50 UTC 2010
```
## 查看ubuntu版本：sudo cat /etc/issue
```
bearthur@bearthur-Lenovo-G450:~$ sudo cat /etc/issue
Ubuntu 10.10 \n \l
```

# linux文件目录管理

## 创建文件 touch                                 
## 创建目录 mkdir
## 删除文件 rm                                      
## 删除目录rm -r或者rmdir
## 查看文件 cat 或者less 或者more       
## 查看目录 cd
## 拷贝文件，目录 cp     （拷贝整个目录的话可能需要用到cp -a）
## 列表 ls
## 改名 移动 mv
## 查找 find            find .name filename当前目录下查找filename这个文件
## 压缩： tar -zcvf {.tgz-file} {files}
## 解压： tar -zxvf {.tgz-file} {files}

# 磁盘管理

## FS容量 df             df  -h
```
bearthur@bearthur-Lenovo-G450:~$ df -h
文件系统            容量  已用  可用 已用%% 挂载点
/dev/sda10             12G  3.0G  8.0G  28% /
none                 1001M  308K 1001M   1% /dev
none                 1007M  112K 1006M   1% /dev/shm
none                 1007M   96K 1006M   1% /var/run
none                 1007M     0 1007M   0% /var/lock
```
## 查看目录容量 du         du  -h   如du /home -h

## 查看磁盘分区信息：sudo fdisk -l
```
bearthur@bearthur-Lenovo-G450:~$ sudo fdisk -l

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x624aa2e0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6375    51207156    7  HPFS/NTFS
/dev/sda2            6376       38914   261362638    f  W95 Ext'd (LBA)
/dev/sda5            6376       16574    81923436    7  HPFS/NTFS
/dev/sda6           16575       26773    81923436    7  HPFS/NTFS
/dev/sda7           26774       31873    40960000    7  HPFS/NTFS
/dev/sda8           31873       37001    41192448    7  HPFS/NTFS
/dev/sda9           37001       37390     3124224   82  Linux swap / Solaris
/dev/sda10          37390       38914    12235776   83  Linux
```

## 查看硬盘速度
```
bearthur@bearthur-Lenovo-G450:~$ sudo hdparm -tT /dev/sda10

/dev/sda10:
 Timing 2 reads:   1962 MB in  2.00 seconds = 981.38 MB/sec
 Timing buffered disk reads:  114 MB in  3.02 seconds =  37.72 MB/sec
```
## 磁盘同步：sync
数据写到硬盘--其实并不是马上就写上去的，而是先写道内存中去，在到硬盘，这样加入突然断电将会导致数据丢失  所以windows遇到突然断电再次开机还需要扫描内存


# 用户管理

## 创建一个用户并给这个用户设个密码
```
bearthur@bearthur-Lenovo-G450:~$ sudo useradd user4
[sudo] password for bearthur:
bearthur@bearthur-Lenovo-G450:~$ id user4
uid=1005(user4) gid=1006(user4) 组=1006(user4)
bearthur@bearthur-Lenovo-G450:~$ su user4
密码：
su：认证失败
bearthur@bearthur-Lenovo-G450:~$ sudo passwd user4
输入新的 UNIX 密码：
重新输入新的 UNIX 密码：
passwd：已成功更新密码
bearthur@bearthur-Lenovo-G450:~$ su user4
密码：
$ whoami
user4
```

## 删除用户

```
bearthur@bearthur-Lenovo-G450:~$ su user4
密码：
$ whoami
user4
$ su bearthur
密码：
bearthur@bearthur-Lenovo-G450:~$ sudo userdel user4
userdel：用户 user4 目前已登录
```

这时候假如kill用户user4的线程的话，终端会出问题：

下面是出现的问题
```
我先创建了一个用户uer4，设了这个用户的密码，
然后切换到另外一个用户，想把user4删除:
sudo userdel user4
提示user4已登录
网上看了说要kill用户进程 于是 我：
ps aux
找到user4的进程ID号（有两个进程）
然后输入：sudo kill 2944 2784
接着出现问题了：
Session terminated, killing shell...bearthur@bearthur-Lenovo-G450:~$  ...killed.
bearthur@bearthur-Lenovo-G450:~$ sexit
这个sexit是我随便按个键，电脑自己跳出来的
接着我不管打什么命令，都有没办法显示出来，但是可以执行
为什么会这样？难道是bug？
```

等待解答, 一天后。

> 用户进程通常只有一个，就是登录的shell。使用su切换到其他用户，这时的shell，是user4用户的子进程。kill父进程，相当于自杀，当然会不正常了。结果未知。

> - 红联版主

> 要删除帐号，先把它退出, 然后用 root 登录, 然后再删除, 多简单的事~~
> - 开源CEO

> 如果要删除的帐号是图形登录的，注销，然后用在终端下用root账户登录或者如果有的系统允许root登录图形的话也行，然后删除不用的帐号。如果要要删除的帐号是终端登录的，logout 然后用root登录，之后删除不要的账户就好了, 换个终端，用新身份登录就可以了.
> - Hl.y成员:

问题over

于是我关掉终端，然后：
```
bearthur@bearthur-Lenovo-G450:~$ sudo userdel user4
bearthur@bearthur-Lenovo-G450:~$ id user4
id: user4：无此用户
提示已删除用户
```

# 进程管理
## 查看进程
```
bearthur@bearthur-Lenovo-G450:~$ ps aux
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root         1  0.0  0.0   2892  1696 ?        Ss   22:21   0:00 /sbin/init
root         2  0.0  0.0      0     0 ?        S    22:21   0:00 [kthreadd]
root         3  0.0  0.0      0     0 ?        S    22:21   0:00 [ksoftirqd/0]
root         4  0.0  0.0      0     0 ?        S    22:21   0:00 [migration/0]
root         5  0.0  0.0      0     0 ?        S    22:21   0:00 [watchdog/0]
syslog    1011  0.0  0.0  34608  1340 ?        Sl   22:21   0:00 rsyslogd -c4
102       1075  0.0  0.0   3600  1864 ?        Ss   22:21   0:00 dbus-daemon --s
avahi     1083  0.0  0.0   3016  1376 ?        S    22:21   0:00 avahi-daemon: r
avahi     1084  0.0  0.0   3016   440 ?        S    22:21   0:00 avahi-daemon: c
bearthur  1474  0.0  0.3  37888  7572 ?        Ssl  22:21   0:00 gnome-session
bearthur  1501  0.3  0.1  18636  2620 ?        Sl   22:21   0:05 /usr/bin/ibus-d
bearthur  1505  0.0  0.1  19648  3780 ?        Sl   22:21   0:00 /usr/lib/ibus/i
```
root ，bearthur都是用户，1505这是进程ID号  可以通过kill 进程ID号来杀死某个进程

## 进程树pstree
```
bearthur@bearthur-Lenovo-G450:~$ pstree
init─┬─NetworkManager─┬─dhclient
     │                └─{NetworkManager}
     ├─acpid
     ├─atd
     ├─avahi-daemon───avahi-daemon
     ├─bonobo-activati───2*[{bonobo-activat}]
     ├─clock-applet───{clock-applet}
     ├─console-kit-dae───63*[{console-kit-da}]
     ├─cron
     ├─cupsd
     ├─3*[dbus-daemon]
     ├─2*[dbus-launch]
     ├─e-addressbook-f───{e-addressbook-}
     ├─e-calendar-fact───{e-calendar-fac}
     ├─firefox───run-mozilla.sh───firefox-bin─┬─plugin-containe───8*[{plugin-co+
     │                                        └─17*[{firefox-bin}]
     ├─2*[gconfd-2]
     ├─gdm-binary─┬─gdm-simple-slav─┬─Xorg
     │            │                 ├─gdm-session-wor─┬─gnome-session─┬─applet.+
     │            │                 │                 │               ├─bluetoo+
     │            │                 │                 │               ├─cairo-d+
     │            │                 │                 │               ├─compiz─+++
     │            │                 │                 │               │        +++
     │            │                 │                 │               ├─evoluti+
     │            │                 │                 │               ├─gdu-not+
     │            │                 │                 │               ├─gnome-p+
     │            │                 │                 │               ├─gnome-p+
     │            │                 │                 │               ├─ibus-da+
     │            │                 │                 │               ├─nautilu+
     │            │                 │                 │               ├─nm-appl+
     │            │                 │                 │               ├─polkit-+
     │            │                 │                 │               ├─ssh-age+
     │            │                 │                 │               ├─update-+
     │            │                 │                 │               └─2*[{gno+
     │            │                 │                 └─{gdm-session-wo}
     │            │                 └─{gdm-simple-sla}
     │            └─{gdm-binary}
     ├─6*[getty]
     ├─gnome-keyring-d───2*[{gnome-keyring-}]
     ├─gnome-screensav
     ├─gnome-settings-───{gnome-settings}
     ├─gnome-terminal─┬─bash───pstree
     │                ├─gnome-pty-helpe
     │                └─2*[{gnome-terminal}]
     ├─gvfs-afc-volume───{gvfs-afc-volum}
     ├─gvfs-fuse-daemo───3*[{gvfs-fuse-daem}]
     ├─gvfs-gdu-volume
     ├─gvfs-gphoto2-vo
     ├─gvfsd
     ├─gvfsd-burn
     ├─gvfsd-computer
     ├─gvfsd-metadata
     ├─gvfsd-trash
     ├─ibus-x11
     ├─2*[indicator-apple───{indicator-appl}]
     ├─indicator-appli
     ├─indicator-me-se───{indicator-me-s}
     ├─indicator-messa
     ├─indicator-sessi───{indicator-sess}
     ├─indicator-sound
     ├─modem-manager
     ├─notification-ar───{notification-a}
     ├─polkitd
     ├─pulseaudio─┬─gconf-helper───{gconf-helper}
     │            └─3*[{pulseaudio}]
     ├─rsyslogd───3*[{rsyslogd}]
     ├─rtkit-daemon───2*[{rtkit-daemon}]
     ├─syndaemon
     ├─system-service-
     ├─trashapplet───{trashapplet}
     ├─udevd───2*[udevd]
     ├─udisks-daemon─┬─udisks-daemon
     │               └─{udisks-daemon}
     ├─upowerd
     ├─upstart-udev-br
     ├─wnck-applet───{wnck-applet}
     └─wpa_supplicant
```
## 其他知识点
动态查看：top
后台进程：&
调回前台：fg
调回后台：bg
优先级调整：renice
杀死进程：kill pkill xkill

# 系统管理

## 环境变量：env
有时候编译程序需要设置新的环境变量：export 环境变量=新值     //有问题待解决？？？
问题解决：export DISPLAY ="localhost:0.0" 要加" "
或者：赋值时=两边不要加空格
```
bearthur@bearthur-Lenovo-G450:~$ env
ORBIT_SOCKETDIR=/tmp/orbit-bearthur
SSH_AGENT_PID=1486
TERM=xterm
SHELL=/bin/bash
XDG_SESSION_COOKIE=c7856cbb97b9b99b583752ea00000007-1298359229.627829-1075292124
GST_ID3V2_TAG_ENCODING=GBK:UTF-8:GB18030
WINDOWID=81788933
GNOME_KEYRING_CONTROL=/tmp/keyring-iUnX8Q
GTK_MODULES=canberra-gtk-module
USER=bearthur
```

## 系统时间：date
bearthur@bearthur-Lenovo-G450:~$ date
2011年 02月 22日 星期二 15:43:19 CST

## 运行时间：time 基本命令
```
bearthur@bearthur-Lenovo-G450:~$ time ls
AdobeAIRInstaller.bin    f3       wget-log  视频  下载
AdobeAIRInstaller.bin.1  file2    公共的    图片  音乐
examples.desktop         out.ogv  模板      文档  桌面

real    0m0.004s
user    0m0.000s
sys    0m0.000s
```

## 查看历史命令：history
## 查看系统信息：dmesg
或是：
```
bearthur@bearthur-Lenovo-G450:~$ cat /var/log/dmesg
bearthur@bearthur-Lenovo-G450:~$ cat /var/log/messages
```

## 本次开机运行时间：uptime
```
bearthur@bearthur-Lenovo-G450:~$ uptime
 15:49:32 up 29 min,  2 users,  load average: 0.27, 0.32, 0.32
```

## 登录信息：last
可根据这条命令查看自己的电脑是否遭受黑客攻击
```
bearthur@bearthur-Lenovo-G450:~$ last
bearthur pts/0        :0.0             Tue Feb 22 15:30   still logged in  
bearthur tty7         :0               Tue Feb 22 15:20   still logged in  
reboot   system boot  2.6.35-22-generi Tue Feb 22 15:20 - 15:50  (00:30)   
bearthur pts/1        :0.0             Mon Feb 21 23:13 - 23:25  (00:12)   
bearthur pts/0        :0.0             Mon Feb 21 22:42 - 23:25  (00:43)   
bearthur pts/0        :0.0             Mon Feb 21 22:31 - 22:42  (00:10)   
bearthur pts/0        :0.0             Mon Feb 21 22:28 - 22:31  (00:02)   
bearthur pts/0        :0.0             Mon Feb 21 22:21 - 22:28  (00:06)   
bearthur tty7         :0               Mon Feb 21 22:21 - down   (01:21)   
reboot   system boot  2.6.35-22-generi Mon Feb 21 22:21 - 23:42  (01:21)   
bearthur pts/0        :0.0             Mon Feb 21 22:16 - 22:18  (00:02)   
bearthur pts/0        :0.0             Mon Feb 21 21:46 - 22:15  (00:29)   
bearthur tty7         :0               Mon Feb 21 21:44 - 22:18  (00:33)   
reboot   system boot  2.6.35-22-generi Mon Feb 21 21:44 - 22:20  (00:35)
```


# 网络管理
## ping
### ping的作用：测试网络是否能够连通
```
linxiongmin@bearthur-K40IE:~$ ping google.cn
PING google.cn (203.208.37.99) 56(84) bytes of data.
64 bytes from bg-in-f99.1e100.net (203.208.37.99): icmp_req=1 ttl=245 time=37.8 ms
64 bytes from bg-in-f99.1e100.net (203.208.37.99): icmp_req=2 ttl=245 time=20.6 ms
64 bytes from bg-in-f99.1e100.net (203.208.37.99): icmp_req=3 ttl=245 time=34.2 ms
64 bytes from bg-in-f99.1e100.net (203.208.37.99): icmp_req=4 ttl=245 time=20.0 ms
64 bytes from bg-in-f99.1e100.net (203.208.37.99): icmp_req=5 ttl=245 time=20.6 ms
^C
--- google.cn ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 4002ms
rtt min/avg/max/mdev = 20.028/26.686/37.860/7.736 ms
```

### ping工作流程

我们以下面一个网络为例：有A、B、C、D四台机子，一台路由RA，子网掩码均为255.255.255.0，默认路由为192.168.0.1 [1]
1.在同一网段内 　　
在主机A上运行“Ping 192.168.0.5”后，都发生了些什么呢? 首先，Ping命令会构建一个固定格式的ICMP请求数据包，然后由ICMP协议将 这个数据包连同地址“192.168.0.5”一起交给IP层协议（和ICMP一样，实际上是一组后台运行的进程），IP层协议将以地址 “192.168.0.5”作为目的地址，本机IP地址作为源地址，加上一些其他的控制信息，构建一个IP数据包，并想办法得到192.168.0.5的 MAC地址（物理地址，这是数据链路层协议构建数据链路层的传输单元——帧所必需的），(---DNS--)以便交给数据链路层构建一个数据帧。关键就在这里，IP层协议通过 机器B的IP地址和自己的子网掩码，发现它跟自己属同一网络，就直接在本网络内查找这台机器的MAC,如果以前两机有过通信，在A机的ARP缓存表应该有 B机IP与其MAC的映射关系，如果没有，就发一个ARP请求广播，得到B机的MAC,一并交给数据链路层。后者构建一个数据帧，目的地址是IP层传过来 的物理地址，源地址则是本机的物理地址，还要附加上一些控制信息，依据以太网的介质访问规则，将它们传送出去。 　　
主机B收到这个数据帧后，先检查它的目的地址，并和本机的物理地址对比，如符合，则接收；否则 丢弃。接收后检查该数据帧，将IP数据包从帧中提取出来，交给本机的IP层协议。同样，IP层检查后，将有用的信息提取后交给ICMP协议，后者处理后， 马上构建一个ICMP应答包，发送给主机A，其过程和主机A发送ICMP请求包到主机B一模一样。

2.不在同一网段内 　　
在主机A上运行“Ping 192.168.1.4”后，开始跟上面一样，到了怎样得到MAC地址时，IP协议通过计算发现D机与自己不在同一网段内，就直接将交由路由处理，也就是 将路由的MAC取过来，至于怎样得到路由的MAC，跟上面一样，先在ARP缓存表找，找不到就广播吧。路由得到这个数据帧后，再跟主机D进行联系，如果找 不到，就向主机A返回一个超时的信息。

## ifconfig的相关命令
ifconfig配置网卡：
（备注： eth0，eth1,eth2,代表网卡一，网卡二，网卡三 hw 代表hardware 硬件意思 ether 代表ethernet 以太网的意思 ）
### 配置网卡的IP地址
```
$ ifconfig eth0 192.168.0.1 netmask 255.255.255.0
```
在eth0上配置上192.168.0.1 的IP地址及24位掩码。
若想再在eth0上在配置一个192.168.1.1/24 的IP地址怎么办？用下面的命令
```
$ ifconfig eth0：0 192.168.1.1 netmask 255.255.255.0
```
这时再用ifconifg命令查看，就可以看到两个网卡的信息了，分别为：eth0和eth0：0.若还想再增加IP，那网卡的命名就接着是：eth0：1、eth0：2……想要几个就填几个。ok！
### 配置网卡的硬件地址
ifconfig eth0 hw ether xx：xx：xx：xx：xx：xx就将网卡的硬件地址更改了，此时你就可以骗过局域网内的IP地址邦定了。

### 将网卡禁用 　　ifconfig eth0 down
### 将网卡启用 　　ifconfig eth0 up
### 不带参数的ifconfig 命令可以显示当前启动的网络接口
```
linxiongmin@bearthur-K40IE:~$ ifconfig
eth0      Link encap:以太网  硬件地址 e0:cb:4e:69:41:73 
          inet 地址:192.168.1.103  广播:192.168.1.255  掩码:255.255.255.0
          inet6 地址: fe80::e2cb:4eff:fe69:4173/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  跃点数:1
          接收数据包:36830 错误:0 丢弃:0 过载:0 帧数:0
          发送数据包:34626 错误:0 丢弃:0 过载:0 载波:0
          碰撞:0 发送队列长度:1000
          接收字节:39311623 (39.3 MB)  发送字节:5085285 (5.0 MB)
          中断:43 基本地址:0x8000

lo        Link encap:本地环回 
          inet 地址:127.0.0.1  掩码:255.0.0.0
          inet6 地址: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  跃点数:1
          接收数据包:8 错误:0 丢弃:0 过载:0 帧数:0
          发送数据包:8 错误:0 丢弃:0 过载:0 载波:0
          碰撞:0 发送队列长度:0
          接收字节:480 (480.0 B)  发送字节:480 (480.0 B)

wlan0     Link encap:以太网  硬件地址 00:25:d3:f9:2e:45 
          UP BROADCAST MULTICAST  MTU:1500  跃点数:1
          接收数据包:0 错误:0 丢弃:0 过载:0 帧数:0
          发送数据包:0 错误:0 丢弃:0 过载:0 载波:0
          碰撞:0 发送队列长度:1000
          接收字节:0 (0.0 B)  发送字节:0 (0.0 B)
```

## /etc/resolv.conf
```
linxiongmin@bearthur-K40IE:~$ cat /etc/resolv.conf
# Generated by NetworkManager
nameserver 202.103.24.68
nameserver 202.103.44.150
```
## route
```
linxiongmin@bearthur-K40IE:~$ route
内核 IP 路由表
目标            网关            子网掩码        标志  跃点   引用  使用 接口
192.168.1.0     *               255.255.255.0   U     1      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth0
default         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
```


## 重启网卡
```
linxiongmin@bearthur-K40IE:~$ sudo ifconfig down
[sudo] password for linxiongmin:
down: 获取接口信息时发生错误: Device not found
linxiongmin@bearthur-K40IE:~$ sudo ifconfig eth0 down
linxiongmin@bearthur-K40IE:~$ ifconfig  //这样就找不到eth0了（与上面比较下就知道啦）
lo        Link encap:本地环回 
          inet 地址:127.0.0.1  掩码:255.0.0.0
          inet6 地址: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  跃点数:1
          接收数据包:8 错误:0 丢弃:0 过载:0 帧数:0
          发送数据包:8 错误:0 丢弃:0 过载:0 载波:0
          碰撞:0 发送队列长度:0
          接收字节:480 (480.0 B)  发送字节:480 (480.0 B)

wlan0     Link encap:以太网  硬件地址 00:25:d3:f9:2e:45 
          UP BROADCAST MULTICAST  MTU:1500  跃点数:1
          接收数据包:0 错误:0 丢弃:0 过载:0 帧数:0
          发送数据包:0 错误:0 丢弃:0 过载:0 载波:0
          碰撞:0 发送队列长度:1000
          接收字节:0 (0.0 B)  发送字节:0 (0.0 B)

linxiongmin@bearthur-K40IE:~$ sudo dhclient eth0  //使用：sudo ifconfig eth0 down效果一样
linxiongmin@bearthur-K40IE:~$ sudo ifconfig eth0 up

Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

Listening on LPF/eth0/e0:cb:4e:69:41:73
Sending on   LPF/eth0/e0:cb:4e:69:41:73
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPOFFER of 192.168.1.103 from 192.168.1.1
DHCPREQUEST of 192.168.1.103 on eth0 to 255.255.255.255 port 67
DHCPACK of 192.168.1.103 from 192.168.1.1
bound to 192.168.1.103 -- renewal in 2858 seconds.
```

## namp命令：黑客入侵必备，扫描网络端口



# 启动管理

window下修复grub，用PE进去，终端输入fdisk /mbr（慎用，我没成功）

linux下修复grub，用LIVECD进去，终端:

sudo grub

然后grub>root(hd0,n) ##后面的这个n指的是要修复grub的那块硬盘

grub>setup(hd0)    ##覆盖mbr

遇到启动grub问题，最笨的方法是重装系统！


# 任务管理
## 单次任务：at , atq ,atrm
## 周期任务：crontab -e, crontab -l, crontab -r

## 单次执行
```
linxiongmin@bearthur-K40IE:~$ date
2011年 03月 06日 星期日 12:33:48 CST
linxiongmin@bearthur-K40IE:~$ at 12:38 #编辑任务
warning: commands will be executed using /bin/sh
at> cd /root
at> <EOT> ####按ctrl+D退出
job 3 at Sun Mar 6 12:38:00 2011
linxiongmin@bearthur-K40IE:~$ atq #查看任务
3 Sun Mar 6 12:38:00 2011 a linxiongmin
linxiongmin@bearthur-K40IE:~$ atq 3 #查看任务
3 Sun Mar 6 12:38:00 2011 a linxiongmin
linxiongmin@bearthur-K40IE:~$ atrm 3 #取消任务
linxiongmin@bearthur-K40IE:~$ atq
```
## 周期执行
```
linxiongmin@bearthur-K40IE:~$crontab -e
GNU nano 2.2.4 文件： /tmp/crontab.c2H5jU/crontab 已更改
# m h dom mon dow command #分钟 小时 每个月的第几天 月份 每个礼拜的第几天 命令
15 1 * * 1-5 cd/home #每周1-5的1：15执行命令 *表示所有
```
按ctrl+x退出 保存
crontab: installing new crontab

### crontab -l #查看周期性任务
```
linxiongmin@bearthur-K40IE:~$ crontab -l #查看周期性任务
Edit this file to introduce tasks to be run by cron.
For example, you can run a backup of all your user accounts
at 5 a.m every week with:
0 5 * * 1 tar -zcf /var/backups/home.tgz /home/
m h dom mon dow command
15 1 * * 1-5 cd /home
```
### crontab -r #删除周期任务
```
linxiongmin@bearthur-K40IE:~$ crontab -r #删除周期任务
linxiongmin@bearthur-K40IE:~$ crontab -l
no crontab for linxiongmin $
```


# 关机命令
poweroff #poweroff -f 强制关机（不保存数据，慎用）
halt
shutdown -h now
init 0
普通用户一般没有权限关机的


# txt文件乱码
原因：windows下简体中文多用gb2312编码 （或gbk, gb18030）, linux下多用utf8编码，有点区别
解决办法：
终端输入：gconf-editor
展开“/apps/gedit-2/preferences/encodings/”
编辑右侧的“auto_detected”将“GB18030”添加到最顶上。以后文本编辑器就可以正常显示中文了

# 终端输入su切换到root时提示认证失败
su root提示认证失败
ubuntu root是默认禁用了，不答应用root登陆，所以先要设置root密码。
  执行：sudo passwd root 接着输入密码和root密码，重复密码。再重新启动就可以用root登陆。

# 设置上网

针对上网的问题可能是一个长篇大论，不过，ADSL用户是最简单的，首次进入系统之后，你会在上面板的右侧看到很多小指示器图标，其中有一个上 下箭头的图标，这个是网络连接指示器，右键点击“edit connections”或是“编辑连接”，在最后一个“DSL”中点击“Add”,连接名称无所谓，选中”connect automatically”,在”username” 和”password”中输入你的ADSL帐号和密码。点”apply“后关闭，左键单击网络图标，点“DSL connect”即可。如果仍不能联网，试着重启一下吧。


# 设置3D效果

step1 右键-更改桌面背景-视觉效果-拓展 （然后会提示安装显卡驱动，需要联网  安装成功后提示电脑重启 ）
step2 系统-系统管理-新立得软件管理器-然后输入密码--搜索CompizConfig -右键标记-然后安装
安装成功的话可以在系统-首选项找到
苹果工具栏：新立得软件搜索：aciro-dock


# 终端安装卸载软件
安装软件包命令：
```
$ sudo apt-get install ABC  或 sudo aptitude install ABC
```
删除软件包命令:
```
$ sudo apt-get remove ABC 和 sudo aptitude remove ABC
```
同时删除配置文件:
```
$ sudo apt-get remove --purge ABC 和  sudo aptitude purge ABC
```
注：ABC指的是某个软件名称



# 播放SWF格式的视频

使用firefox+flash插件

一般用firefox上网能看视频的话，右击SWF文件后-用其他程序打开-后选择firefox 就能播放了



# 解压缩rar文件问题（ubuntu自带的文件归档器不能打开rar文件）

压缩：apt-get install rar

解压缩：apt-get install unrar

这样直接点rar文件就能打开了

# 解决pdf乱码问题

sudo apt-get install poppler-data
sudo mv /etc/fonts/conf.d/49-sansserif.conf /etc/fonts/conf.d/49-sansserif.conf.backup


# 解决音乐播放乱码问题
因为Windows下默认采用的是GBK编码，而ubuntu默认采用的是utf8编码。
自带的rhythmbox不是很好用，建议换成audaciou
linxiongmin@bearthur-K40IE:~$ sudo apt-get install audacious
然后文件-首选项-播放列表-备用字符编码-输入GBK

# gedit 编辑器打开windows之前文本出现乱码。（ubuntu11.10）

终端输入命令：
```
$ gsettings set org.gnome.gedit.preferences.encodings auto-detected "['UTF-8', 'GB18030', 'GB2312', 'GBK', 'BIG5', 'CURRENT', 'UTF-16']"
$ gsettings set org.gnome.gedit.preferences.encodings shown-in-menu "['UTF-8', 'GB18030', 'GB2312', 'GBK', 'BIG5', 'CURRENT', 'UTF-16']"
```
#  ubuntu10.10（英文）设置中文输入法
设置步骤：
1. system-->keyboard-input-methods-->新的应该是会提示说IBUS还未启动，点YES-->然后 就打开IBUS界面了，选择input-method标签-->选择chinese-->拼音，然后别到基本上都可以不用设置来，最后 close

2. 然后就是和windows一样到切换，ctrl+space



# 更新源

```
$ sudo gedit /etc/apt/sources.list
```

然后：将sources.list文件里面的源表更新为：

```
##网易 Ubuntu 10.10 源（速度很快）
##代码:

deb http://mirrors.163.com/ubuntu/ maverick main universe restricted multiverse
deb-src http://mirrors.163.com/ubuntu/ maverick main universe restricted multiverse
deb http://mirrors.163.com/ubuntu/ maverick-security universe main multiverse restricted
deb-src http://mirrors.163.com/ubuntu/ maverick-security universe main multiverse restricted
deb http://mirrors.163.com/ubuntu/ maverick-updates universe main multiverse restricted
deb http://mirrors.163.com/ubuntu/ maverick-proposed universe main multiverse restricted
deb-src http://mirrors.163.com/ubuntu/ maverick-proposed universe main multiverse restricted
deb http://mirrors.163.com/ubuntu/ maverick-backports universe main multiverse restricted
deb-src http://mirrors.163.com/ubuntu/ maverick-backports universe main multiverse restricted
deb-src http://mirrors.163.com/ubuntu/ maverick-updates universe main multiverse restricted
```
接着更新：
```
$ sudo apt-get update
```

# VirtualBox USB setting

点击“系统”－－“系统管理”－－“用户和组”－－“管理组”－－选中“vboxusers”，点“属性”，将root及你的用户名选中，注销--就可以了使用USB了。

在VBOX里不能用USB，只是个权限的小问题


# 开机自动启动 Ubuntu iBus 输入法 

Ubuntu 的默认输入法是 ibus，但是发现系统启动时它不会自动启动。

Google 的说法是：Ubuntu 系统安装后虽然自带了 ibus 输入法，但在英语环境下默认不启动。

要开机启动，其实也很简单，只要在［System］->［administration］->［Language Support］

里选择［Keyboard input method system］为［ibus］就可以了。


# smplayer出问题打不开媒体文件

mplayer has finished unexpectedly exit code:1

解决方法：

右键-subtitles 将 closed caption 设置为disable (就是enable closed caption前面不能有勾)

# 自动挂载

修改/etc/fstab的参数

# ldd 查看依赖库，常用于移植程序时寻找依赖库。

# rootfs 
Root File System 系统启动时，Uinx要在内存中开辟出一块特殊的文件系统rootfs来帮助真实的文件系统成功挂载上。

# 当前目录是“./” 而“~/”是当前用户的home目录

# 文件名后面有个～ 指的是备份文件，好像gedit以后会自动产生

# 解压
tar.bz2 解压命令 以gcc-4.1.0.tar.bz2为例说明
第一步：bzip2 -d  gcc-4.1.0.tar.bz2
---上面解压完之后执行下面的命令。

第二步：tar -xvf gcc-4.1.0.tar 或 tar -xvf *.tar
解完之后会出现多一个文件夹 gcc-4.1.0


# source命令用法

source FileName 作用:在当前bash环境下读取并执行FileName中的命令。 注：该命令通常用命令“.”来替代。 如：source .bash_rc 与 . .bash_rc 是等效的。 注意：source命令与shell scripts的区别是， source在当前bash环境下执行命令，而scripts是启动一个子shell来执行命令。这样如果把设置环境变量（或alias等等）的命令写进scripts中，就只会影响子shell,无法改变当前的BASH,所以通过文件（命令列）设置环境变量时，要用source 命令。

$ source /opt/poky/1.1.1/environment-setup-x86_64-poky-linux

# 查看linux内核版本：
cat /proc/version

```
bear@bear-K40IE:~$ cat /proc/version
Linux version 3.0.0-14-generic (buildd@palmer) (gcc version 4.6.1 (Ubuntu/Linaro 4.6.1-9ubuntu3) ) #23-Ubuntu SMP Mon Nov 21 20:34:47 UTC 2011
```
# 制作iso镜像的方法：
把/dev/cdrom目录制作为镜像，名字为/root/rh1.iso
方法1：dd if=/dev/cdrom of=/root/rh1.iso
方法2：#cat /dev/cdrom >;/root/1.iso
方法3：mkisofs -r -o myiso.iso /dev/cdrom
方法4：cp -r /home/user name.iso
生成iso镜像以后，就可以用linux下的DVD进行刻录，刻录为DVD光盘了。

# 烧制iso镜像到U盘

dd是Linux/UNIX 下的一个非常有用的命令,作用是用指定大小的块拷贝一个文件,并在拷贝的同时进行指定的转换。

用以下命令前必须卸载u盘
```
dd if=xxx.iso of=/dev/sdb bs=1M
```
# rmmod  删除模块

语　　法：rmmod [-as][模块名称...]

补充说明：执行rmmod指令，可删除不需要的模块。Linux操纵系统的核心具有模块化的特性，应此在编译核心时，务须把全部的功能都放如核心。你可以将这些功能编译成一个个单独的模块，待有需要时再分别载进它们。


# 一般出错信息被记录在文件/var/log/messages中
```
# cat /var/log/messages |tail
```
# 查看串口数量：
```
dmesg | grep tty*
```

# wget的用法
```
wget http://downloads.yoctoproject.org/releases/yocto/yocto-1.1.1/adt_installer/adt_installer.tar.bz2
```
下载adt_installer.tar.bz2这个文件

# linux几种快速清空文件内容的方法
```
　　$ : > filename #其中的 : 是一个占位符, 不产生任何输出.
　　$ > filename
　　$ echo “” > filename
　　$ echo /dev/null > filename
　　$ echo > filename
　　$ cat /dev/null > filename
    $ cp /dev/null filename
```

# 查看文档末几行
```
$ tail -20 result  ##查看末20行
```

# 远程登录学校的server
```
ssh xilin@fc.isima.fr
```
然后输入密码，不过在宿舍登录不了。

# 创建多级文件夹
```
$mkdir -p /home/pi/server/www 
```

# 查看隐藏文件
进入自己主目录，按ctrl+h.就能看见以点号开头的隐藏文件
终端：
```
lin@lin-K40IE:~$ ls -a 
```

# 如何写shell脚本
很简单，把command写进文档里，然后sh命令执行即可。
sleep.sh
```
cd /home/lin 
echo "hello lin, why not go to sleep?" 
```
执行:
```
lin@lin-K40IE:~$ sh delete 
hello lin, why not go to sleep? 
```
# 显示当前文件夹的文件树状图
```
$ tree                #一次看个够
$ tree | more     #细水长流
```

# 将终端输出结果输出到文件
```
$ tree >> ~/test 
```

# 查看正在运行的所有线程及其子线程
（Prints running processes with child processes, recursively.）
```
$ pstree 
```
# 查看socket统计状态
(Outputs Socket Statistics.)
```
$ ss 
$ ss 
State         Recv-Q Send-Q          Local Address:Port              Peer Address:Port   
SYN-SENT      0         1                 172.26.49.6:51008          123.123.123.123:http    
SYN-SENT      0         1                 172.26.49.6:51009          123.123.123.123:http    
ESTAB            0         0                 172.26.49.6:53799           74.125.195.188:https   
CLOSE-WAIT   1         0                 172.26.49.6:35995             91.189.94.25:http    
ESTAB            0         0                 172.26.49.6:47081           173.194.32.121:http    
ESTAB            0         0                 172.26.49.6:49713          108.160.165.181:http    
ESTAB            0         0                 172.26.49.6:55006           119.167.145.21:http 
```
# Traceroute 路由跟踪
```
$ traceroute google.com
```
Traceroute is a command which can show you the path a packet of information takes from your computer to one you specify. It will list all the routers it passes through until it reaches its destination, or fails to and is discarded. In addition to this, it will tell you how long each hop from router to router takes.

# 显示历史命令 history
```
$ history        #show history commands
$ history -c    #clear history commands in terminal (就是没办法通过向上键得到上一条命令)
```

如果想history命令也输出时间戳，执行下面的命令，再执行history
```
export HISTTIMEFORMAT="%F %T " 
```
可以在终端用Ctrl＋R搜索历史命令，快速！
注:看到你想要的命令后按下左键或者右键,就可以在执行这条命令之前编辑它了］

默认情况下，命令历史被储存在.bash_history文件中，即使$ history -c ，历史也还在。



# 复制一个文件的内容到另一个文件

将 shell.md文档的内容复制到shell_script_guide.txt 文档中（覆盖shell_script_guide.txt ）
```
$ cat shell.md > shell_script_guide.txt  ##  '>' 是重定向的意思，即覆盖原文件的内容
```
将 shell.md文档的内容复制到shell_script_guide.txt 文档末尾（不覆盖shell_script_guide.txt ）
```
$ cat shell.md >> shell_script_guide.txt  ##  '>' 是重定向的意思，即覆盖原文件的内容
```
# 查找目录下的所有文件中是否含有某个字符串 
```
$ find .|xargs grep -ri "IBM" 
```
或：
```
$ grep -rn "implement" ~/Dropbox/COURSES/android/lab/ 
```
查找目录下的所有文件中是否含有某个字符串,并且只打印出文件名 
```
$ find .|xargs grep -ri "IBM" -l 
```
或:
```
$ grep -rn "implement" ~/Dropbox/COURSES/android/lab/ -l
```

# ls -lh     -h表示shows in a human way
```
lin@lin-K40IE:~/Dropbox$ ls -lh 
total 7.8M 
-rw-rw-r--  1 lin lin 2.7M Nov  5 10:18 2014_HIT-UBP_Master_Thesis_PENG_Xuesong_终稿.pdf 
-rw-rw-r--  1 lin lin  71K Oct 19 00:21 2014年IT公司薪酬.pdf 
-rw-rw-r--  1 lin lin 148K Nov 16 22:22 2015校园招聘.pdf 
-rw-r-----  1 lin lin 572K Dec  1 00:29 612edf3ajw1emtbiy2ggcj20c82xgqij.jpg 
drwxrwxr-x  2 lin lin 4.0K Dec  4 12:41 app.log.20141127 
-rw-r-----  1 lin lin 1.5M Dec  2 11:44 app.log.20141127.zip 
drwxrwxr-x  3 lin lin 4.0K Dec 25 20:51 Apps 
drwxrwxr-x  2 lin lin 4.0K Nov 24 00:54 Canada 
drwxrwxr-x  2 lin lin  36K Dec 26 23:12 Chargements appareil photo 
-rw-------  1 lin lin 880K Nov 16 22:53 course.png 
drwxrwxr-x  2 lin lin 4.0K Oct  4 15:06 coursera 
drwxrwxr-x 11 lin lin 4.0K Dec  4 17:47 COURSES 
drwxrwxr-x  4 lin lin 4.0K Dec 19 22:40 database_oracle 
-rw-rw-r--  1 lin lin 1.3M Dec 17 22:51 database practical work.pdf 
drwxr-xr-x  6 lin lin 4.0K Nov 11 21:30 Documents 
drwxrwxr-x  2 lin lin 4.0K Dec 25 19:32 English Learning 
drwxrwxr-x  4 lin lin 4.0K Nov 22 19:34 French Learnning 
drwxrwxr-x  9 lin lin 4.0K Dec 11 21:51 Github 
drwxrwxr-x  4 lin lin 4.0K Nov 15 19:04 ISIMA-Embbedded LINUX Lab work 
drwxrwxr-x 12 lin lin 4.0K Dec 26 22:42 ISIMA_Share 
drwxrwxr-x  4 lin lin 4.0K Dec 26 23:45 Linux Learning 
-rw-rw-r--  1 lin lin    0 Nov 24 23:17 ofii~ 
drwxrwxr-x  6 lin lin 4.0K Dec 14 15:28 Project_SEES_2014 
-rw-r-----  1 lin lin 116K Dec  7 00:21 Resume Xiongmin Lin (1).docx 
drwxrwxr-x  4 lin lin 4.0K Sep 26 19:08 SEES summary_2014_09_26 
-rw-rw-r--  1 lin lin 161K Oct  7 23:19 SQL Server 和 Oracle 以及 MySQL 有哪些区别.pdf 
-rw-rw-r--  1 lin lin 386K Oct 11 16:57 中国历代纪元表&历史地图.pdf 
drwxrwxr-x  2 lin lin 4.0K Dec 15 09:59 大项目 
drwxrwxr-x  2 lin lin 4.0K Oct 27 14:16 学习笔记 
-rw-rw-r--  1 lin lin 1.1K Dec 25 21:00 学习规划 
-rw-rw-r--  1 lin lin  843 Dec 25 20:47 学习规划~ 
```


# mkdir -p 创建多级文件夹
```
lin@lin-K40IE:~/Dropbox$ mkdir parent/child/ 
mkdir: cannot create directory `parent/child/': No such file or directory 
lin@lin-K40IE:~/Dropbox$ mkdir -p parent/child/ 
lin@lin-K40IE:~/Dropbox$ ls parent/ 
child 
```

# 更改完bash配置， 记得刷新
安装android studio配置32位电脑
```
$ gedit .bashrc
paste this text:
export ANDROID_EMULATOR_FORCE_32BIT=true
refresh source:
$ source ~/.bashrc
```
# du -h 查看当前文件夹的大小

# Open a pdf document
```
$ evince PAM_2015_TP.pdf 
```
# Display an image and run it in a background mode
```
$ display Canny_Detector_Tutorial_Original_Image.jpg 
^C 
$ display Canny_Detector_Tutorial_Original_Image.jpg & 
[1] 5480 
$ bg 1 
bash: bg: job 1 already in background 
$ fg 1 
display Canny_Detector_Tutorial_Original_Image.jpg 
^Z  //Ctrl + Z, pause the task
[1]+  Stopped                 display Canny_Detector_Tutorial_Original_Image.jpg 
$ fg 1 
display Canny_Detector_Tutorial_Original_Image.jpg 
^C // Ctrl + C, kill the task
```
# How to use vi editor
## vi编辑器三种模式

编辑模式；命令模式；ex模式。
按esc键可以转到命令模式，按很多键可以转到编辑模式（比如i），按"："可以进入ex模式。

## 常见命令（命令模式下）
* 进入退出命令： bear@bear-K40IE:~$ vi makefile
* 保存：":w"
* 退出：":q"
* 保存退出：":wq"
* 不保存退出：":q!"或是"ZZ"
## 编辑命令
* 光标的移动：上下左右，enter键。或是：左（h）；右（l，空格键）；上（k）；下（j）
* 在当前光标前插入字符："i"
* 在当前光标后插入字符："a"(光标会自动往后面跳一格，效果跟"i"一样)
* 将当前光标处字符替换："R"（只替换一个字符后自动返回到命令模式）
* 跳到行末尾进行编辑："A"
* 在当前行下面插入一行："o"(小写字母o)
* 在当前行上面插入一行："O"(大写字母O)
* 从当前光标处往右删除（剪切）一个字符："x"或是"Delete"
* 从当前光标处往左删除（剪切）n个字符："nx"(n是某个数字，比如3x)
* 删除整行："D"或"dd"
* 复制本行："Y"或"y"
* 向下复制n行："nY"(n代表数字，比如2Y,必须大写)
* 粘帖到下一行："p"（小写）
* 粘帖到上一行："P"（大写）
* 撤销："u","U"(大写：回退到进入本行后的所有操作)
* 重复执行前一次命令："."
## 搜索命令
* "/字符或是字符串" "？字符或是字符串"  比如/line查找line这个单词，再按"n"向后查找，"N"向前查找

## ex命令
前面带":"的都是ex命令
* 显示行号：":set number" or "se nu"
* 关闭行号：":set nonumber" or "se nonu"

# 使用SSH
## SSH介绍
> Secure Shell（缩写为SSH），由IETF的网络工作小组（Network Working Group）所制定；SSH为一项创建在应用层和传输层基础上的安全协议，为计算机上的Shell（壳层）提供安全的传输和使用环境。

> 传统的网络服务程序，如rsh、FTP、POP和Telnet其本质上都是不安全的；因为它们在网络上用明文传送数据、用户帐号和用户口令，很容易受到中间人（man-in-the-middle）攻击方式的攻击。就是存在另一个人或者一台机器冒充真正的服务器接收用户传给服务器的数据，然后再冒充用户把数据传给真正的服务器。

> 而SSH是目前较可靠，专为远程登录会话和其他网络服务提供安全性的协议。利用SSH协议可以有效防止远程管理过程中的信息泄露问题。通过SSH可以对所有传输的数据进行加密，也能够防止DNS欺骗和IP欺骗。

> - [维基百科](http://zh.wikipedia.org/wiki/Secure_Shell)

* ssh client (以ssh标识)
* ssh server (以sshd标识)
      

## 查看SSH连接状态

```
$ ps aux | grep ssh 
```
      

## 连接raspberry

Access to a raspberry board through ssh:

```
$ ssh pi@192.168.42.91 

```
输入密码即可。


## PC复制文件到Raspberry

将当前文件夹下的main.cpp复制到/home/pi/project2015/testScilab目录。

```
$ pscp main.cpp pi@192.168.42.91:/home/pi/project2015/testScilab 

```

## PC从Raspberry提取文件

将Raspberry的/home/pi/project2015/testScilab目录下的main.cpp复制到PC当前文件夹

```
$ pscp pi@192.168.42.91:/home/pi/project2015/testScilab/main.cpp ~/ 

```

## 使用SSH退出符切换SSH会话

已经连接上raspberry， 但是又想在PC上做一些操作， 除了按ctrl + shift + T以外，也可以先按“～”符，再按ctrl + z.

```
$ ~^Z [suspend ssh]  //按"~",终端无显示，需按ctrl + z 以后，命令才执行。

```

# shell编程基础
 
Shell的种类:bash(较常用) ；ksh； Csh

## 查看用户信息
```
linxiongmin@bearthur-K40IE:~$ vi /etc/passwd
root:x:0:0:root:/root:/bin/bash
 
daemon:x:1:1:daemon:/usr/helloin:/bin/sh
bin:x:2:2:bin:/bin:/bin/sh
sys:x:3:3:sys:/dev:/bin/sh
sync:x:4:65534:sync:/bin:/bin/sync
games:x:5:60:games:/usr/games:/bin/sh
man:x:6:12:man:/var/cache/man:/bin/sh
lp:x:7:7:lp:/var/spool/lpd:/bin/sh
mail:x:8:8:mail:/var/mail:/bin/sh
news:x:9:9:news:/var/spool/news:/bin/sh
uucp:x:10:10:uucp:/var/spool/uucp:/bin/sh
proxy:x:13:13:proxy:/bin:/bin/sh
www-data:x:33:33:www-data:/var/www:/bin/sh
backup:x:34:34:backup:/var/backups:/bin/sh
list:x:38:38:Mailing List Manager:/var/list:/bin/sh
irc:x:39:39:ircd:/var/run/ircd:/bin/sh
gnats:x:41:41:Gnats Bug-Reporting System (admin):/var/lib/gnats:/bin/sh
nobody:x:65534:65534:nobody:/nonexistent:/bin/sh
libuuid:x:100:101::/var/lib/libuuid:/bin/sh
syslog:x:101:103::/home/syslog:/bin/false
messagebus:x:102:105::/var/run/dbus:/bin/false
avahi-autoipd:x:103:108:Avahi autoip daemon,,,:/var/lib/avahi-autoipd:/bin/false
avahi:x:104:109:Avahi mDNS daemon,,,:/var/run/avahi-daemon:/bin/false
couchdb:x:105:113:CouchDB Administrator,,,:/var/lib/couchdb:/bin/bash
uhellomux:x:106:46:uhellomux daemon,,,:/home/uhellomux:/bin/false
speech-dispatcher:x:107:29:Speech Dispatcher,,,:/var/run/speech-dispatcher:/bin/sh
kernoops:x:108:65534:Kernel Oops Tracking Daemon,,,:/:/bin/false
pulse:x:109:114:PulseAudio daemon,,,:/var/run/pulse:/bin/false
rtkit:x:110:117:RealtimeKit,,,:/proc:/bin/false
saned:x:111:118::/home/saned:/bin/false
hplip:x:112:7:HPLIP system user,,,:/var/run/hplip:/bin/false
gdm:x:113:120:Gnome Display Manager:/var/lib/gdm:/bin/false
linxiongmin:x:1000:1000:linxiongmin,,,:/home/linxiongmin:/bin/bash
linxiongmin:x:1000:1000:linxiongmin,,,:/home/linxiongmin:/bin/bash
```
(共七个域)
用户：linxiongmin
密码：x（已保护）：
用户ID ：1000
用户组ID：1000
帐号说明（这里为空）
用户登录时的主目录：/home/linxiongmin
用户登录的shell：/bin/bash

## 查看用户组信息
```
linxiongmin@bearthur-K40IE:~$ vi /etc/group*
linxiongmin:x:1000:
```

## 创建和运行SHELL脚本程序
```
$ cat example2_1.sh
echo `date +%Y%m%d` ####注意是反引号``````不是单引号''''##echo 显示
$ sh ./example2_1.sh
20110320
```

## shell环境变量
环境变量是一个具有特定名字的对象，它包含了一个或者多个应用程序所将使用到的信息。例如path，当要求系统运行一个程序而没有告诉它程序所在的完整路径时，系统除了在当前目录下面寻找此程序外，还应到path中指定的路径去找。用户通过设置环境变量，来更好的运行进程。

## 管道符号：|
```
linxiongmin@bearthur-K40IE:~$ ls
Desktop MSDN.desktop VirtualBox VMs 模板 图片 下载 桌面
examples.desktop unnamed 公共的 视频 文档 音乐
linxiongmin@bearthur-K40IE:~$ ls | wc -l ##ls 的输出作为wc -l的输入 计数13个文件
13
linxiongmin@bearthur-K40IE:~$ ls | more
Desktop
examples.desktop
MSDN.desktop
unnamed
VirtualBox VMs
公共的
模板
视频
图片
文档
下载
音乐
桌面
linxiongmin@bearthur-K40IE:~$ ls | less
```


# gcc编译器

静态链接库在链接后，被引用的代码讲被复制到最终的可执行文件中，可脱离函数库直接运行。
动态链接库在内存中只包含一份可执行的映像，所有链接到动态链接库的程序都共享这份映像！


## 编译链接（静态链接库）

```
bear@bear-K40IE:~/program/sec$ ls
add.c add.o first1.c lib src
bear@bear-K40IE:~/program/sec$ ar rv libtools.a add.o
ar: creating libtools.a
a – add.o
bear@bear-K40IE:~/program/sec$ ls
add.c add.o first1.c lib libtools.a src
bear@bear-K40IE:~/program/sec$ vi sub.c
bear@bear-K40IE:~/program/sec$ ls
add.c add.o first1.c lib libtools.a src sub.c
bear@bear-K40IE:~/program/sec$ gcc -c -O sub.c
bear@bear-K40IE:~/program/sec$ ls
add.c add.o first1.c lib libtools.a src sub.c sub.o
bear@bear-K40IE:~/program/sec$ ar rv libtools.a sub.o
a - sub.o
bear@bear-K40IE:~/program/sec$ mv libtools.a ./lib

bear@bear-K40IE:~/program/sec/lib$ vi my.h
bear@bear-K40IE:~/program/sec/lib$ ls
libtools.a my.h
bear@bear-K40IE:~/program/sec$ vi first1.c
bear@bear-K40IE:~/program/sec$ gcc -c -I./ first1.c
bear@bear-K40IE:~/program/sec$ ls
add.c add.o first1.c first1.o lib my.h src sub.c sub.o
bear@bear-K40IE:~/program/sec$ gcc -c first1.c
ear@bear-K40IE:~/program/sec$ gcc first1.o -L./lib -ltools -o first1
bear@bear-K40IE:~/program/sec$ ls
add.c add.o first1 first1.c first1.o lib my.h src sub.c sub.o
bear@bear-K40IE:~/program/sec$ ./first1
VALUE+10=110
VALUE-10=90
bear@bear-K40IE:~/program/sec$ gcc first1.o -o first1
first1.o: In function `main':
first1.c:(.text+0x19): undefined reference to `add'
first1.c:(.text+0x48): undefined reference to `sub'
collect2: ld returned 1 exit status
```
这是add.c文件：
```
#include <stdio.h>
int add(int a,int b)
{
  return a+b;
}
```
这是sub.c文件:
```
#include<stdio.h>
int sub(int a,int b)
{
  return a-b;
}
```
这是first1.c文件：
```
#include<stdio.h>
#include"my.h"
main ()
{

  fprintf(stderr,"VALUE+10=%d\n",add(VALUE ,10));
  fprintf(stderr,"VALUE-10=%d\n",sub(VALUE ,10));
}
```



## 编译链接 （动态链接库）
```
bear@bear-K40IE:~/program/third$ vi first.c
bear@bear-K40IE:~/program/third$ gcc -fPIC -c first.c
bear@bear-K40IE:~/program/third$ ls
first.c first.o
bear@bear-K40IE:~/program/third$ file first.o
first.o: ELF 32-bit LSB relocatable, Intel 80386, version 1 (SYSV), not stripped
bear@bear-K40IE:~/program/third$ gcc -shared -o libabc.so first.o
bear@bear-K40IE:~/program/third$ ls
first.c first.o libabc.so
bear@bear-K40IE:~/program/third$ ls
first.c first.o libabc.so
bear@bear-K40IE:~/program/third$ vi hello.c
bear@bear-K40IE:~/program/third$ ls
first.c first.o libabc.so hello.c
bear@bear-K40IE:~/program/third$ gcc -c hello.c -O
bear@bear-K40IE:~/program/third$ ls
first.c first.o libabc.so hello.c hello.o
bear@bear-K40IE:~/program/third$ gcc hello.o -L./ -labc -s hello
gcc: hello: No such file or directory
bear@bear-K40IE:~/program/third$ echo LD_LIBRARY_PATH
LD_LIBRARY_PATH
bear@bear-K40IE:~/program/third$ export LD_LIBRATY_PATH=./
bear@bear-K40IE:~/program/third$ gcc hello.o -L./ -labc -s hello
gcc: hello: No such file or directory
bear@bear-K40IE:~/program/third$ gcc hello.o -labc -s hello #少了个-o
gcc: hello: No such file or directory
bear@bear-K40IE:~/program/third$ ls
first.c first.o libabc.so hello.c hello.o
bear@bear-K40IE:~/program/third$ gcc hello.o -labc -s -o hello
/usr/bin/ld: cannot find -labc
bear@bear-K40IE:~/program/third$ ls
first.c first.o libabc.so hello.c hello.o
bear@bear-K40IE:~/program/third$ echo LD_LIBRARY_PATH #少了个$
LD_LIBRARY_PATH
bear@bear-K40IE:~/program/third$ export LD_LIBRATY_PATH="./"
bear@bear-K40IE:~/program/third$ echo LD_LIBRARY_PATH
LD_LIBRARY_PATH
bear@bear-K40IE:~/program/third$ echo $LD_LIBRARY_PATH

bear@bear-K40IE:~/program/third$ export LD_LIBRATY_PATH=./ #注意拼写啊！
bear@bear-K40IE:~/program/third$ echo $LD_LIBRARY_PATH

bear@bear-K40IE:~/program/third$ echo $LD_LIBRARY_PATH

bear@bear-K40IE:~/program/third$ export LD_LIBRARY_PATH=./
bear@bear-K40IE:~/program/third$ echo $LD_LIBRARY_PATH
./
bear@bear-K40IE:~/program/third$ gcc hello.o -L./ labc -s -o hello
gcc: labc: No such file or directory
bear@bear-K40IE:~/program/third$ gcc hello.o -L./ -labc -s -o hello
bear@bear-K40IE:~/program/third$ ls
first.c first.o libabc.so hello hello.c hello.o
bear@bear-K40IE:~/program/third$ ./hello
240 is the result
```

这是first.c文件：
```
#include <stdio.h>
int fx(int a,int b)
{
  return a*b;
}
```
这是hello.c文件：
```
#include <stdio.h>
main()
{
  fprintf(stderr,"%d is the result \n",fx(10,24));
}

```


