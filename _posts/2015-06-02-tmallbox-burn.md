---
layout: post
title: "给迈乐M6-天猫魔盒刷v1.2.1的系统"
quote: 刷的过程还是比较顺利的
image: false
video: false
---

# 使用sd卡刷

我只有micro sd卡，但是加上一个SD卡套，就可以当SD卡使用了

v1.2.1 固件下载与说明地址 [迈乐M6](http://www.hdpfans.com/thread-442690-1-1.html)

我为什么要刷v1.2.1  

因为我需要同时在hdmi与av输出音频信号，之前的天猫v1.6.x的系统不支持

## 备份系统

我为什么要备份系统?  

因为我的micro sd卡是来自我的树莓派的，里面有安装系统了，所以要对系统进行备份  
于是我在我的mac下备份:  

- 插入**读卡器**
- 使用*diskutil unmountdisk*卸载sd卡，`注意：不要使用eject，否则无法dd成功`
- 使用[dd](http://zh.wikipedia.org/wiki/Dd_%28Unix%29)命令去把磁盘数据导出为img文件

- 下面是标准命令,`bs`是指一次复制多少内容，`count`是指复制多少次
> dd bs=10m count=500 if=/dev/rdisk2 of=./backup.img

- 需要压缩的话可以这样：
> dd bs=10m count=500 if=/dev/rdisk2 | gzip -9 > ./backup.img.gz

- 压缩文件的系统还原
> gzip -c -d backup.img.gz | dd bs=10m of=/dev/rdisk2

- 查看dd执行进度

dd 是一个效率非常低的工具，但是却最可靠  

在另外一个终端下执行下面的命令
> watch -n 5 killall -USR1 dd


## [刷固件教程](http://bbs.mele.cn/showtopic-2270.aspx)
1.把sd卡烧录好后  

2.把魔盒断电  

3.插入SD卡  

4.魔盒加电    

5.魔盒指示灯开始闪烁   

6.指示灯不闪烁并且不亮就是刷机成功   

7.拔下sd卡，并且断电

8.刷机成功，可以接上电视了

-----

made by sherpper，just for learn something!



