---
title: centos8干掉了ntpdate而选择了更为先进的chrony作为时间同步工具，其中原因是什么？
date: 2021-11-01 16:48:55
tags: centos
categories: 技术
description: 作为操作系统上最为操作系统上最为基础也最为重要的功能时间同步，他们的迭代也需要运维人员格外注意
---

centos 7默认使用的时间同步软件是ntpdate

从centos 8开始在官方的仓库中移除了ntp软件，换成默认的chrony进行时间同步的服务

虽然也可以通过添加第三方的源安装ntp，但是毕竟官方推荐的我们还是需要给点面子的

安装之前先检查下是否已经安装过了

```sh
rpm -q chrony
```

使用yum 安装

```sh
yum install chrony -y

systemctl start chronyd

systemctl enable chronyd
```

检查同步情况（不知为何这个命令一直'506 Cannot talk to daemon',直接系统reboot一下就行)

```sh
chronyc tracking
```

看到下面场景，就说明配置成功了

```sh
[root@localhost ~]# chronyc tracking
Reference ID    : CA760151 (time.neu.edu.cn)
Stratum         : 2
Ref time (UTC)  : Mon Nov 01 09:37:08 2021
System time     : 0.000139006 seconds fast of NTP time
Last offset     : -0.000002700 seconds
RMS offset      : 0.000551544 seconds
Frequency       : 29.121 ppm fast
Residual freq   : +0.010 ppm
Skew            : 2.033 ppm
Root delay      : 0.016828496 seconds
Root dispersion : 0.000497294 seconds
Update interval : 64.2 seconds
Leap status     : Normal
```

总结：我写这篇博客的主要目的就是为了记住centos8换时间同步工具的事，至于chrony相比ntpdate的优势在何处，可以参考这篇文章[Comparison of NTP implementations](https://chrony.tuxfamily.org/comparison.html)


