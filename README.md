# TU131黑苹果项目
本项目是关于如何在无牌笔记本**TU131**上安装和使用黑苹果系统，主要共享Clover配置文件、DSDT/SSDT补丁等。
项目主页：https://github.com/sail1972/TU131

## 我的机器
由于**TU131**系列机器有多款、多批次的机器，我的配置文件与系统补丁仅供参考。我的机器配置如下：

配置项 |型号 |驱动情况
:--------:|:-------:|----------
CPU     | I5-4200U | 使用原生SSDT，在Clover中勾选C/Pstates两个选项，可识别并驱动，正常变频。
核显     | HD4400 | 从SSDT中把核显配置移到DSDT中并打补丁，识别为HD5000，可驱动但偶有开机花屏现象，HDMI输出正常。
有线网卡 | Realtek 8168 | 加入相应的驱动后，可识别并驱动。
无线网卡 | AR5B195（带蓝牙）| 悲催的2B卡无法自动识别，通过仿冒驱动，在IO80211Familly.kext下面的Plugins：AirPortAtheros40.kext的Info.plist中加入“pci168c,2b”识别代码即可。另外，据说在DSDT中也可打补丁，不用仿冒，未测试。
声卡     | Realtek ALC282 | 1、安装VoodooHDA，可识别驱动但有爆音，内置喇叭与外接输出只能手动切换，麦克风正常，HDMI无测试；2、安装仿冒声卡AppleHDA，可识别驱动无爆音，内置喇叭与外接输出可自动切换，但麦克风无输入，HDMI输出正常。
USB3.0  | Intel 0x9c31 | 1、使用原生AppleUSBXHCI，可识别驱动，但会有睡死现象；2、使用第三方GenericUSBXHCI，可识别驱动，无睡死现象。
摄像头   | Alcor Micro 0x5608 | 可识别并驱动，但使用不了，黑屏
读卡器   | Realtek 0x0129 | 可识别为USB2.0-CRW，但仿冒ID后也无法驱动

## 我的分享
[**远景论坛**](http://bbs.pcbeta.com)上我发表的关于TU131-2黑苹果的讨论贴链接：

1. [山寨本TU131-2高分版黑苹果成功经验分享](http://bbs.pcbeta.com/viewthread-1534188-1-1.html)
2. [TU131-2音频AppleHDA解决方法（需要dsdt修改）](http://bbs.pcbeta.com/viewthread-1542989-1-1.html)
3. [解决睡眠无声的EAPD-Codec-Commander最新版2.2.1](http://bbs.pcbeta.com/viewthread-1546461-1-1.html)
4. [山寨本TU131-2安装beta4懒人版并升级beta5成功！](http://bbs.pcbeta.com/viewthread-1548655-1-1.html)


## 使用的工具

1. [系统引导工具Clover](http://sourceforge.net/projects/cloverefiboot/)
2. [DSDT修改工具MaciASL](http://sourceforge.net/projects/maciasl/)
3. [ACPI DSDT/SSDT提取工具源码](https://acpica.org/downloads)
4. [Clover配置修改工具](http://mackie100.webwacemaster.altervista.org/)
5. [SSDT变频文件生成工具](https://github.com/Piker-Alpha/ssdtPRGen.sh)
6. [HDMI音频输出修改工具](https://github.com/Piker-Alpha/AppleIntelFramebufferAzul.sh)
7. [PCI设备配置工具](http://sourceforge.net/projects/dpcimanager/)
8. [苹果设备配置注册信息观察工具](http://sourceforge.net/projects/iojones)

## 使用的驱动(几乎全是[Rehabman](https://github.com/RehabMan)大神的贡献）

1. [有线网卡驱动](https://bitbucket.org/RehabMan/os-x-realtek-network)
2. [USB3驱动](https://bitbucket.org/RehabMan/os-x-generic-usb3)
3. [键盘、触摸板驱动](https://bitbucket.org/RehabMan/os-x-voodoo-ps2-controller)
4. [显示面板背光调节驱动](https://bitbucket.org/RehabMan/os-x-acpi-backlight)
5. [电池驱动](https://bitbucket.org/RehabMan/os-x-acpi-battery-driver)
6. [声卡驱动](http://sourceforge.net/projects/voodoohda)
7. [声卡睡眠后重新激活驱动](https://bitbucket.org/RehabMan/os-x-eapd-codec-commander)
8. [蓝牙韧体装载驱动](https://code.google.com/p/os-x-atheros-3k-firmware/)
9. [FakeSMC驱动及HWSensors](http://hwsensors.com/releases)
10. 仿冒声卡AppleHDA驱动见我在远景论坛上的[分享](http://bbs.pcbeta.com/viewthread-1542989-1-1.html) 

## 使用的补丁（还是[Rehabman](https://github.com/RehabMan)大神贡献的）
1. 请在MaciASL中加入补丁资源：[http://raw.github.com/RehabMan/Laptop-DSDT-Patch/master](http://raw.github.com/RehabMan/Laptop-DSDT-Patch/master)

