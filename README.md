# Hackintosh Hp-Prodesk-400G2-DM OpenCore 0.62 EFI

**电脑参数：**[Hp Prodesk 400G2  DM][1]
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
|BIOS|N23 Ver.02.49 07/12/2020| 
|引导|OpenCore 0.62| 

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

## BIOS设置
只需要注意这几项即可，其他按自己爱好设置即可。
- Secure Boot 关闭
- Fast Boot 关闭
- VTd 关闭
- 显存大小 512M


## 截图预览
### Catalina
安装macOS Catalina 10.15.7版，暂未发现有卡顿现象。
![macOS Catalina][2]
### CPU
CPU 变频正常，日常 CPU 待机功耗 6~7W 相当节能。
![CPU][3]
### 无线蓝牙
无线正常，蓝牙正常，英特尔 AC 7265。
![无线与蓝牙][4]
### 显示器
支持4K分辨率输出，需将EFI文件里的config4k.plist改成config.plist（不建议使用4K,可能会卡顿/花屏现象）
![分辨率][5]

 [1]: https://support.hp.com/ie-en/document/c04843458
 [2]: https://github.com/july929/Hackintosh-Hp-Prodesk-400G2-DM-EFI/blob/main/images/about.png
 [3]: https://github.com/july929/Hackintosh-Hp-Prodesk-400G2-DM-EFI/blob/main/images/cpu.png
 [4]: https://github.com/july929/Hackintosh-Hp-Prodesk-400G2-DM-EFI/blob/main/images/wifi.png
 [5]: https://github.com/july929/Hackintosh-Hp-Prodesk-400G2-DM-EFI/blob/main/images/display.png
