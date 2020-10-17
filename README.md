# Hackintosh Hp-Prodesk-400G2-DM OpenCore EFI
# Hp Prodesk 400G2  DM 黑苹果OC配置 i5-6600T HD530

闲鱼花280元价格捡了台惠普Hp Prodesk 400G2 Mini 六代小主机（准系统）。博主用的是35W的i5-6600t CPU 追求更高性能的可以上i7-6700t或者标压款的i5-6600，需搭配95W/135W电源。700元组装成的一台黑苹果日常用来办公，学习，写码还是相当不错的。分享一下本机黑苹果EFI配置，博主用的是OpenCore.0.62版制作。
![Hp Prodesk 400G2  DM][1]
## 电脑配置
**电脑参数：**[Hp Prodesk 400G2  DM][2]
|配置|型号|
|----|----|
|系统|macOS Catalina 10.15.7|
|CPU|Intel Core i5-6600t @ 2.7GHz 4核4线程|
|显卡|Intel HD Graphics 530 1536 MB|
|内存|金士顿 DDR4 2133MHz 8GB|
|硬盘|光威 GLOWAY STK1.5TS3-S7（1.5Tb/固态硬盘）|
|网卡|Intel Dual Band Wireless-AC 7265|
|声卡|Realtek ALC221|
|SMBIOS|Mac mini (2018)| 

## 实现功能
- ✅ CPU 睿频变频
- ✅ 核显 HD530 显存 1536MB
- ✅ 硬件加速 4K HEVC/H.265解码
- ✅ USB2.0/USB3.0
- ✅ 声卡 内建 layout-id 为 11
- ✅ 节能五项
- ✅ 睡眠唤醒
- ✅ 有线网卡
- ✅ 无线正常(AC7265)
- ✅ 蓝牙正常 (AC7265)

## 存在问题
- ❌ 麦克风不工作
- ❌ 睡眠黑屏可唤醒
## 系统镜像
这里博主提供2个镜像给大家，一个是黑果小兵的原版镜像Catalina 10.15.7，另一个为博主制作的原版纯净恢复版Catalina 10.15.6，图个方便博主使用了恢复版还原系统，用原版安装的话可跳过下边的系统还原教学。
|系统|版本|下载|
|--|--|--|
|macOS|Catalina 10.15.7 19H2|[原版镜像][3]|
|macOS|Catalina 10.15.6 19G2021|[恢复版镜像][4]|
**注：** 恢复版镜像下载解压，里面附带 `DiskGenius`,`EasyUEFI`,`Paragon Hard Disk Manager 16.5`工具
## 磁盘划分
首先硬盘分区类型要是GUID分区，分一个60G大小的空间用来安装 MacOS
步骤：此电脑 → 右键 → 管理 → 磁盘管理 
空出一个60G的分区出来，不分配盘符，不格式化。
![磁盘划分][5]
## 安装系统
在Windows系统上安装 `Paragon Hard Disk Manager 16.5`还原工具，进行还原
![还原系统][6]
## 引导EFI
下载适用于Hp Prodesk 400G2 的EFI文件，这里博主制作了2个，一个CLOVER，一个OpenCore自行选一个放入EFI文件夹。无线网卡/蓝牙驱动已经放入EFI，下载WiFi客户端即可正常使用。

|引导文件|下载链接|
|--|--|
|CLOVER|[Hp Prodesk 400G2 10.15.7 CLOVER 5120.zip][7]|
|OpenCore|[Hp Prodesk 400G2 10.15.7 OpenCore 0.62.zip][8]|
|WiFi 客户端|[HeliPort.dmg][9]|


## 无线驱动
[button color="black" icon="glyphicon glyphicon-star" url="https://github.com/OpenIntelWireless/itlwm" type=""]GitHub项目[/button]
Intel内置无线网卡驱动大部分型号都是不兼容Mac的，需要更换网卡。但随着 Github 大佬们的深入研究，目前已经可以正常驱动了，缺点是性能和信号相对较弱。这台Hp Prodesk 400G2 采用因特尔 AC7265 无线网卡，用itlwm来驱动无线体验还是很棒的。
[button color="black" icon="glyphicon glyphicon-star" url="https://github.com/OpenIntelWireless/itlwm/releases" type=""]驱动下载[/button]
### itlwm.kext
`下面是各网卡型号兼容性列表：`
|PCI ID|Device Name|Supported|
|--|--|--|
|0x08b1|AC 7260|Yes|
|0x08b2|AC 7260|Yes|
|0x08b3|AC 3160|Yes|
|0x08b4|AC 3160|Yes|
|0x095a|AC 7265|Yes|
|0x095b|AC 7265|Yes|
|0x3165|AC 3165|Yes|
|0x3166|AC 3165|Yes|
|0x24f3|AC 8260|Yes|
|0x24f4|AC 8260|Yes|
|0x24f5|AC 4165|Yes|
|0x24f6|AC 4165|Yes|
|0x24fb|AC 3168|Yes|
|0x24fd|AC 8265|Yes|
|0x2526|AC 9260|Yes|
|0x9df0|AC 9560|Yes|
|0xa370|AC 9560|Yes|
|0x31DC|AC 9560|Yes|
|0x30DC|AC 9560|Yes|
|0x271C|AC 9560|Yes|
|0x271B|AC 9560|Yes|
|0x42a4|AC 9462|Yes|
|0x00a0|AC 9462|Yes|
|0x00a4|AC 9462|Yes|
|0x02a0|AC 9462|Yes|
|0x02a4|AC 9462|Yes|
|0x40a4|AC 9462|Yes|
|0x0060|AC 9461|Yes|
|0x0064|AC 9461|Yes|
|0x0260|AC 9461|Yes|
|0x0264|AC 9461|Yes|
|0x2723|AX200|Yes|
|0x2720|AX201|Yes|
|0x43F0|AX201|Yes|
|0xA0F0|AX201|Yes|
|0x34F0|AX201|Yes|
|0x02F0|AC 9462|Yes|
|0x3DF0|AC 9462|Yes|
|0x06F0|AX201|Yes|

### 测试驱动
解压驱动，执行如下两条命令来安装测试驱动（及时加载方便调试 重启后即失效）：
```Bash
# 给驱动分配执行权限
sudo chown -R root:wheel itlwm.kext
# 加载驱动
sudo kextload -v itlwm.kext
```
安装完驱动，目前还是看不到 WiFi 的，只要提示已经加载驱动就可以了，不要着急，我们得安装对应的软件来使用 WiFi

[scode type="blue"]将测试没有问题的驱动 放到 CLOVER - kexts - Other 目录下即可，下次开机会自动加载，无需再次命令行加载了。[/scode]

### WiFi 客户端
[button color="black" icon="glyphicon glyphicon-star" url="https://github.com/OpenIntelWireless/HeliPort" type=""]Github项目[/button]
HeliPort 是 ltlwm WiFi 驱动的专用客户端，使用界面和功能已经无限接近苹果官方的界面了，下面是界面对比图：
![左侧是 官方原生 右侧是 HeliPort][10]

## 蓝牙驱动
[button color="black" icon="glyphicon glyphicon-star" url="https://github.com/OpenIntelWireless/IntelBluetoothFirmware" type=""]Github项目[/button]
IntelBluetoothFirmware 是一个用于在 macOS 中启用原生蓝牙的固件上传驱动，固件的二进制文件来自 Linux。
[button color="black" icon="glyphicon glyphicon-star" url="https://github.com/zxystd/IntelBluetoothFirmware/releases/latest" type=""]驱动下载[/button]
解压驱动，执行如下命令来安装测试驱动（及时加载方便调试 重启后即失效），建议大家一个个尝试去加载驱动，观察蓝牙的使用效果，如果使用异常重启即可，比较方便自己摸索：
- 驱动程序上传固件
```Bash
# 给驱动分配执行权限
sudo chown -R root:wheel IntelBluetoothFirmware.kext
# 加载驱动
sudo kextload -v IntelBluetoothFirmware.kext
```
- 设置面板上启用打开/关闭开关
```Bash
# 给驱动分配执行权限
sudo chown -R root:wheel IntelBluetoothInjector.kext
# 加载驱动
sudo kextload -v IntelBluetoothInjector.kext
```

## 截图预览
### Catalina
安装macOS Catalina 10.15.7版，暂未发现有卡顿现象。
![macOS Catalina][11]
### CPU
CPU 变频正常，日常 CPU 待机功耗 6~7W 相当节能。
![CPU][12]
### 无线蓝牙
无线正常，蓝牙正常，英特尔 AC 7265。
![无线与蓝牙][13]
### 显示器
支持4K分辨率输出，需将EFI文件里的config4k.plist改成config.plist（不建议使用4K,可能会卡顿/花屏现象）
![分辨率][14]
## 常用命令
### 解锁分区
10.15解锁系统分区
```Bash
sudo mount -uw / && killall Finder
```
### 重建缓存
Mac OS重新建立缓存
```bash
sudo rm /System/Library/PrelinkedKernels/prelinkedkernel
sudo rm /System/Library/Caches/com.apple.kext.caches/Startup/kernelcache
sudo chmod -R 755 /System/Library/Extensions
sudo chmod -R 755 /Library/Extensions
sudo chown -R root:wheel /System/Library/Extensions
sudo chown -R root:wheel /Library/Extensions
sudo touch /System/Library/Extensions
sudo touch /Library/Extensions
sudo kextcache -q -update-volume /
sudo kextcache -system-caches
sudo kextcache -i /
```
### 任何软件
Mac OS开启安装任何来源软件
```bash
sudo spctl --master-disable
```
### 睡眠优化
Mac OS系统睡眠优化代码
```bash
sudo pmset -a hibernatemode 0
sudo rm -rf /var/vm/sleepimage
sudo mkdir /var/vm/sleepimage
sudo pmset -a standby 0
sudo pmset -a autopoweroff 0
```


  [1]: http://storage.yangwenqing.com/Website/images/2020101801.png
  [2]: https://support.hp.com/ie-en/document/c04843458
  [3]: https://blog.daliansky.net/macOS-Catalina-10.15.7-19H2-Release-version-with-Clover-5122-original-image-Double-EFI-Version-UEFI-and-MBR.html
  [4]: https://pan.yangwenqing.com/MacOS/macOS/macOS%20Mojave%2010.14.6(18G103)%E6%81%A2%E5%A4%8D%E7%89%88.zip
  [5]: http://storage.yangwenqing.com/Website/images/2020090601.gif
  [6]: http://storage.yangwenqing.com/Website/images/2020090602.gif
  [7]: https://pan.yangwenqing.com/MacOS/HackintoshTool/EFI/%E5%B0%8F%E7%B1%B312.8%E5%AF%B82%E4%BB%A3%20M3-7y30+10.15.6+CLOVER.zip
  [8]: https://pan.yangwenqing.com/MacOS/HackintoshTool/EFI/%E5%B0%8F%E7%B1%B312.8%E5%AF%B82%E4%BB%A3%20M3-7y30+10.15.6+OpenCore.zip
  [9]: https://pan.yangwenqing.com/MacOS/Software/HeliPort.dmg
  [10]: http://storage.yangwenqing.com/Website/images/2020090502.png
  [11]: http://storage.yangwenqing.com/Website/images/2020-10-18.01.09.04.png
  [12]: http://storage.yangwenqing.com/Website/images/2020-10-18.01.07.10.png
  [13]: http://storage.yangwenqing.com/Website/images/2020090506.png
  [14]: http://storage.yangwenqing.com/Website/images/2020-10-18.01.17.09.png
