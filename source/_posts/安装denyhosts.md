---
title: 安装denyhosts
date: 2017-08-23 11:22:55
tags: denyhosts
categories: 技术
description: 阻止暴力破解
---

在外网放台机器，开一个ssh服务，如果不改默认端口，使用密码登录，那每天吸引暴力破解数万次是轻轻松松，如果你的机器所处的环境再恶劣些，能收集到的恶意ip量级就非常可观了。恰巧我的全球监测点都符合使用密码登录不改默认端口的特征。

denyhosts是一款很不错的软件，使用python编写，跨平台，逻辑优雅，代码量小，花半天时间足以看完，
