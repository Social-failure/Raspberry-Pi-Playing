时间	2020/1/22

# 树莓派安装

这算是我第一次写完整的过程经历（之前安装Ubuntu是在大佬的帮助下安装的，自己啥也不懂，也没搜到什么能解惑的东西，所以也写不了）

记录下来方便后人(不要是坑后人就行哈哈)

那我们开始吧！

## 准备材料

Raspberry Pi 3b+

microSD 128G A1(SanDisk Ultra)

手机充电头(我这个是荣耀20的充电头，emm可能手机充电器都可以吧)

USB接口鼠标

Wifi

自家电视机(HDMI线，从机顶盒上拔了下来。都有电脑了还要什么电视机)

SD卡读卡器(我的电脑没有自带SD读卡器，只能USB转接)

笔记本电脑(Ubuntu 20.04)



## 步骤

1. 阅读raspberry官网上的getting started教程
2. 然后是设置SD卡
   1. 下载[imager](https://www.raspberrypi.org/software/)
   2. 然后是下载操作系统(或者说是发行版？)的``.img``文件，推荐是到国内镜像(清华源有)下载，下载好zip文件之后解压。
   3. 接着是把SD卡插入USB转接(???可能这么叫)，插入笔记本电脑
   4. 然后打开imager，选择待烧写OS，选择Use custom，把已经解压好的``.img``写入SD卡

![](/home/liqingwei/mygit/Raspberry-OS-Installation-and-Playing/Pictures/Installation1.png)

>  可能要先erase一下再安装（我是这样做才成功的）

3. ​	接下来，如果你想要无鼠标无键盘开启树莓派，**请不要直接把SD卡插到树莓派上启动**
   1. 首先在SD卡的boot分区(注意不是rootfs文件夹下的`/boot`)根目录新建``ssh``空白文件
   2. 同样的位置新建``wpa_supplicant.conf``，然后是在文件中添加


```
country=CN
ctrl_interface=DIR=/var/run/wpa_supplicant GROUP=netdev
update_config=1
network={
    ssid="Wifi名称"
    psk="Wifi密码"
}
```

> 该文件内容引自[慕课网手记](http://www.imooc.com/article/268242)，里面还讲到了对其他Wifi加密方式的写法，WPA-PSK是WPA/WPA2加密方式对应的写法，Wifi加密方式可以通过Wifi Setting查看（原谅Ubuntu小白的不漂亮的查看方式）

另外，最好将``rootfs``下的``/etc/apt/source.list``修改成国内镜像，这样下载的时候方便一些，可以不用通过`ssh`连接到树莓派再在上面修改(感觉还是有点麻烦，所以直接在本机上用自己熟悉的编辑器修改，或者用`sed`也行，不过本菜不太会用这些小trick，相对熟悉vim)

​		  3. 之后就可以安全退出U盘，将SD卡插入树莓派的SD卡插口了(之前上网搜看到有人把SD卡也通过USB转接插到树莓派上了没成功，所以还是仔细找找SD卡插口)

4. 如果你有USB鼠标与键盘，那么你就可以直接把烧好的SD卡插到树莓派上
5. 接着就是接显示器，接电源开机了，are you ready?

