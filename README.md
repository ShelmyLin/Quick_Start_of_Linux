# Quick Start of Linux

## 第一章 Linux 文件管理
> * 目录结构
> * 列表显示 ls
> * 打开目录 cd
> * 查看文档 cat
> * 创建新文件或心目录
> * 删除命令 rm
> * 改名与移动 mv
> * 压缩与解压 tar
> * 查找文件 find
> * 查找文件内容 grep
> * 修改文件权限 chmod

### 目录结构
| 名称        |  解释                                                 |
| ----------- | :--------                                             |
|/            | 根目录                                                | 
| bin         | 放普通用户的命令                                      |
| boot        | linux的核心文件 如mrb镜像 grub启动                    |
| dev         | 硬件 如串口                                           |
| etc         | 系统配置文件 如config                                 |
| lib         | 存放动态库                                            |
| mnt         | 挂载不同设备                                          |
| proc        | 存放cpu 内存 硬件信息                                 |
| sbin        | 存放超级用户命令                                      |
| tmp         | 临时名录 放置临时信息                                 |
| usr         | 类似windows的program file   内有src(source),bin,sbin  |
| var         | 存放变动性信息 log spool cache                        |

绝对路径: 以/起始 如/home/user1/abc.txt
相对路径: user1/abc.txt
### 列表显示 ls
| 命令        |  解释                                                 |
| ----------- | :--------                                             |
| ls -l       | 详细列出所有文件, 一般用 ll 也可以                    |
| ls -a       | 显示所有文件 包括隐藏文件                             |
| ll -h       | -h 表示show in a human-friend way                     |

* linux中 所有以点开头的文件都是隐藏的文件
* TAB 敲两次 出现所有可能结果
* Linux命令执行机制：翻译+执行 如ls  系统先执行ls=ls --color 然后在执行ls --color   alias ls=ls可设置回来
再比如 alias ubuntu=ls 这样执行ubuntu这条命令时 系统会把ubuntu解释成ls
* 查找某一命令的详解，使用man，比如 
```
$ man ls
```
```
$ ll -h
total 228K
drwx------ 10 lin lin 4.0K Mar 22 15:29 ./
drwxrwxr-x  4 lin lin 4.0K Mar  5 14:57 ../
drwx------  2 lin lin 4.0K Mar 21 15:21 android/
-rw-rw-r--  1 lin lin  18K Mar 17 16:17 break_vigenere.md
drwxrwxr-x  2 lin lin 4.0K Mar 19 22:56 computer_system/
-rw-------  1 lin lin  463 Mar  5 14:13 France.md
drwx------  2 lin lin 4.0K Mar  5 14:13 French_Learning/
```
第一列：d表示目录 -表示文件
第二到第九十列：r读 w写 x执行 -表示对应的rwx无权限   第一个rwx表示文件所有者权限，第二个表示组权限 第三个表示其他用户权限
第一个lin表示用户 第二个lin表示用户所在组 后面数字表示文件或是目录大小

### 打开目录 cd
| 命令        |  解释                                                 |
| ----------- | :--------                                             |
| cd          | 回到home目录                                          |
| cd ..       | 回到上层目录                                          |
| cd -        | 回到之前所在目录                                      |
| pwd         | 显示当前目录                                          |

./  表示当前目录
../ 表示上一级目录

```
$ pwd
/home/lin
$ cd /usr/local/MATLAB/
$ pwd
/usr/local/MATLAB/
$ cd -
/home/lin
$ pwd
/home/lin
$ cd ..
$ pwd
/home
$ cd
$ pwd
/home/lin

```
### 查看文档 cat
| 命令                         |  解释                                                 |
| -----------                  | :--------                                             |
| cat filename                 | 在终端查看文档                                        |
| head filename                | 在终端查看文档，前十行                                |
| head -n filename             | 在终端查看文档，前n行                                 |
| tail filename                | 在终端查看文档，后十行                                |
| tail -n filename             | 在终端查看文档，后n行                                 |
| cat filename_1 >> filename_2 | 将文档输出至filename_2的末尾                          |
| cat filename_1 > filename_2  | 将文档输出至filename_2(覆盖)                          |

```
$ head -2 hello.txt 
hello, this is line 1
hello, this is line 2

$ tail -2 hello.txt 
hello, this is line 11
hello, this is line 12
```

### 创建新文件或新文件夹
| 命令                                     |  解释                                       |
| -----------                              | :--------                                   |
| touch filename                           | 创建名为filename的新文档                    |
| mkdir foldername                         | 创建名为foldername的新文件夹                |
| mkdir -p folder/new_folder1/new_folder2  | 创建多级新文件夹                            | 

```
$ mkdir hello
$ cd hello/
$ pwd
/home/lin/Dropbox/hello
$ ls
$ mkdir -p hello_01/hello_02
$ ls
hello_01
$ ls hello_01/
hello_02
```

### 删除命令 rm
| 命令                                     |  解释                                       |
| -----------                              | :--------                                   |
| rm filename                              |  删除某一文件                               |
| rm -r foldername  或rmdir                |  删除某一文件夹                             |
| rm *                                     |  删除当前目录下所有文件                     |
```
$ ll
total 24
drwxrwxr-x 3 lin lin 4096 Mar 22 15:59 ./
drwxrwxr-x 3 lin lin 4096 Mar 22 15:59 ../
drwxrwxr-x 2 lin lin 4096 Mar 22 15:59 hello_02/
lin@lin-K40IE:~/Dropbox/hello/hello_01$ rm -r hello_02/
lin@lin-K40IE:~/Dropbox/hello/hello_01$ ll
total 16
drwxrwxr-x 2 lin lin 4096 Mar 22 16:04 ./
drwxrwxr-x 3 lin lin 4096 Mar 22 15:59 ../

```
### 改名与移动 mv
| 命令                                     |  解释                                              |
| -----------                              | :--------                                          |
| mv filename_1 filename_2                 | 将filename_1文件重命名为filename_2                 |
| mv filename_1 ../filename_2              | 将filename_1文件移动至上层目录并重命名为filename_2 |

```
$ touch hello.txt
$ mv hello.txt ../hello_02.txt 
$ ls hello.txt
ls: cannot access hello.txt: No such file or directory
$ ls ../hello_02.txt 
../hello_02.txt
$ mv ../hello_02.txt ./hello.txt
$ ls ../hello_02.txt 
ls: cannot access ../hello_02.txt: No such file or directory
$ ls hello.txt 
hello.txt

```

### 压缩与解压 tar

| 命令                                     |  解释                                              |
| -----------                              | :--------                                          |
| tar -zcvf {.tgz-file} {files}            | 将{file}压缩为{.tgz-file}，c代表compress           |
| tar -zxvf {.tgz-fiile}                   | 将{.tgz-file} 解压到当前文件夹                     |

```
$ ls AITR-720.pdf 
AITR-720.pdf
$ tar -zcvf test.tar.gz AITR-720.pdf 
$ ls test.tar.gz 
test.tar.gz

```

### 查找文件 find
| 命令                                     |  解释                                              |
| -----------                              | :--------                                          |
| find {folder} -name "*string*"             | 在{folder}目录下查找文件名含有string的文件       |

```
$ find ./ -name "*android*"
./android
./android/android_forum.md
./android/android_theory.md

```

### 查找文件内容 grep
| 命令                                     |  解释                                                        |
| -----------                              | :--------                                                    |
| grep "string" ./*                        | 在当前目录下（不含子目录）查找含有string内容的文件           |
| grep -r "string" ./*                     | 在当前目录下（含子目录）查找含有string内容的文件             |
| grep -rn "string" ./*                    | 在当前目录下（含子目录）查找含有string内容的文件,并打印行号  |

```
$ grep -rn "hello" test/*
1:this is an example of grep, i want to find "hello"
```

### 修改文件权限 chmod

这里先复习以下ls命令
```
$ ll
total 12
drwxrwxr-x 2 lin lin 4096 Mar 22 22:24 ./
drwxr-xr-x 4 lin lin 4096 Mar 22 22:25 ../
-rw-rw-r-- 1 lin lin   66 Mar 22 22:24 hello.txt

```
第二到第九十列：r读 w写 x执行 -表示对应的rwx无权限   第一个rwx表示文件所有者权限，第二个表示组权限 第三个表示其他用户权限。若用二进制加以区分不同的权限的话，111（即十进制的7）代表可读可写可执行，110（即十进制的6）代表可读可写但是不可执行，以此类推。

| 命令                                     |  解释                                                                               |
| -----------                              | :--------                                                                           |
| chmod 权限值 文件名                      | 给文件赋以相应的权限，如chmod 666 hello.txt,表示所有用户都可对hello.txt进行读写操作 | 

```
$ chmod 666 hello.txt 
$ ll
total 12
drwxrwxr-x 2 lin lin 4096 Mar 22 22:24 ./
drwxr-xr-x 4 lin lin 4096 Mar 22 22:25 ../
-rw-rw-rw- 1 lin lin   66 Mar 22 22:24 hello.txt
```

## 第二章 Linux 信息查询
### 查看计算机信息
#### 查看cpu信息：sudo cat /proc/cpuinfo
#### 查看内存：sudo cat /proc/meminfo
#### 查看硬盘：sudo fdisk -l
#### 查看显卡：lspci
#### 查看USB接口：lsusb
#### 查看驱动：lsmod
#### 查看kernel版本：uname
#### 查看ubuntu版本：sudo cat /etc/issue
#### 查看目录容量 du du -h 如du /home -h
#### 查看磁盘分区信息：sudo fdisk -l
#### 查看硬盘速度
#### 查看系统信息：dmesg
#### 查看本次开机运行时间：uptime
#### 查看登录信息

### 查看进程
### 查看历史命令

## Linux 用户管理
### 创建用户
### 删除用户
### 用户权限管理
### 用户组


## Linux 网络管理
### ping命令

### ifconfig 相关命令
#### 配置网卡的IP地址
#### 配置网卡的硬件地址
#### 将网卡禁用 　　ifconfig eth0 down
#### 将网卡启用 　　ifconfig eth0 up
#### 不带参数的ifconfig 命令可以显示当前启动的网络接口
#### 重启网卡
### route 命令
### 使用ssh

## Linux 编程基础
### 使用Ctags快速查看代码
### nano编辑器
### vi编辑器
### gcc编译器
#### 编译
#### 链接
### 如何写makefile文件
### 使用gdb调试程序
### shell基础

## Github的使用
## 使用Markdown写技术博客

## Linux下MySQL的使用

## 常用的Linux快捷键


## 常见linux问题及解决办法


