-   [使用OpenCore引导黑苹果](#使用opencore引导黑苹果)
-   [**简介**](#简介)
-   [帖子更新内容查询：](#帖子更新内容查询)
    -   [](#section)
    -   [**2.1 Config----ACPI**](#config-acpi)
        -   [**2.1.1 Config----ACPI-----Add**](#config-acpiadd)
        -   [**2.1.2 Config----ACPI-----Block**](#config-acpiblock)
        -   [**2.1.3 Config----ACPI-----Patch**](#config-acpipatch)
        -   [**2.1.4 Config----ACPI-----Quirks**](#config-acpiquirks)
    -   [**2.2 Config-----Booter**](#configbooter)
        -   [**2.2.1
            Config---Boot---MmioWhitelist**](#configbootmmiowhitelist)
        -   [**2.2.2 Config---Boot---Quirks**](#configbootquirks)
    -   [**2.3 Config-----DeviceProperties**](#configdeviceproperties)
        -   [**2.3.1 声卡**](#声卡)
        -   [**2.3.2 核心显卡**](#核心显卡)
        -   [**2.3.3 Block**](#block)
    -   [**2.4 Config-----Kernel**](#configkernel)
        -   [**2.4.1 Config-----Kernel-----Add**](#configkerneladd)
        -   [**2.4.2 Config-----Kernel-----Block**](#configkernelblock)
        -   [**2.4.3
            Config-----Kernel-----Emulate**](#configkernelemulate)
        -   [**2.4.4 Config-----Kernel-----Patch**](#configkernelpatch)
        -   [**2.4.5
            Config-----Kernel-----Quirks**](#configkernelquirks)
    -   [**2.5 Config----Misc**](#config-misc)
        -   [**2.5.1
            Config-----Misc-----BlessOverride**](#configmiscblessoverride)
        -   [**2.5.2 Config-----Misc-----Boot**](#configmiscboot)
        -   [**2.5.3 Config-----Misc-----Debug**](#configmiscdebug)
        -   [**2.5.4 Config-----Misc-----Entries**](#configmiscentries)
        -   [**2.5.5
            Config-----Misc-----Security**](#configmiscsecurity)
        -   [**2.5.6 Config-----Misc-----Tools**](#configmisctools)
    -   [**2.6 Config----NVRAM**](#config-nvram)
        -   [**2.6.1 Config-----NVRAM-----Add**](#confignvramadd)
        -   [**2.6.2 Config-----NVRAM-----Block**](#confignvramblock)
        -   [**2.6.3
            Config-----NVRAM-----LegacyEnable**](#confignvramlegacyenable)
        -   [**2.6.4
            Config-----NVRAM-----LegacySchema**](#confignvramlegacyschema)
    -   [**2.7 Config----PlatformInfo**](#config-platforminfo)
        -   [**2.7.1
            Config-----PlatformInfo-----Automatic**](#configplatforminfoautomatic)
        -   [**2.7.2
            Config-----PlatformInfo-----Generic**](#configplatforminfogeneric)
        -   [**2.7.4
            Config-----PlatformInfo-----剩余部分**](#configplatforminfo剩余部分)
    -   [**2.8 Config----UEFI**](#config-uefi)
        -   [**2.8.1
            Config-----UEFI----ConnectDrivers**](#configuefi-connectdrivers)
        -   [**2.8.2 Config-----UEFI----Drivers**](#configuefi-drivers)
        -   [**2.8.3 Config-----UEFI----Input**](#configuefi-input)
        -   [**2.8.4
            Config-----UEFI----Protocols**](#configuefi-protocols)
        -   [**2.8.5 Config-----UEFI----Quirks**](#configuefi-quirks)
    -   [**2.9 小节**](#小节)
    -   [**3.1 模拟NVRAM**](#模拟nvram)
    -   [**3.2
        建立自己的开机选择系统目录**](#建立自己的开机选择系统目录)
        -   [**3.2.1 第一部分**](#第一部分)
        -   [**3.2.2 第二部分**](#第二部分)
    -   [**3.3 提取DSDT**](#提取dsdt)
    -   [**3.4 加载原生电源管理**](#加载原生电源管理)
    -   [](#section-1)
    -   [**3.5 加载节能五项**](#加载节能五项)
    -   [**3.6 Mac OS
        10.15下解锁S/L/E目录**](#mac-os-10.15下解锁sle目录)
    -   [**3.7 关于EC控制器**](#关于ec控制器)
        -   [**3.7.1 禁用EC控制器**](#禁用ec控制器)
        -   [](#section-2)
        -   [**3.7.2 USBX供电**](#usbx供电)
    -   [**3.8 RTC相关问题**](#rtc相关问题)
        -   [**3.8.1
            存在AWAC的情况下修复RTC**](#存在awac的情况下修复rtc)
        -   [**3.8.2
            不存在AWAC的情况下修复RTC**](#不存在awac的情况下修复rtc)
    -   [**3.9 FCPX加速**](#fcpx加速)
    -   [**3.10 睡眠即醒的相关问题**](#睡眠即醒的相关问题)
        -   [**3.10.1
            方法一：OC版本的0D/06补丁**](#方法一oc版本的0d06补丁)
        -   [](#section-3)
        -   [**3.10.2
            方法二：沿用Clover版本的0D/06补丁&展示TgtBridge在OC下的用法**](#方法二沿用clover版本的0d06补丁展示tgtbridge在oc下的用法)
        -   [](#section-4)
        -   [**3.10.3 方法三：配合SSDT+重命名的强制睡眠补丁
            （重点推荐）**](#方法三配合ssdt重命名的强制睡眠补丁-重点推荐)
        -   [**3.10.4
            方法四：从白果DSDT中学习到的睡眠补丁**](#方法四从白果dsdt中学习到的睡眠补丁)
        -   [**3.10.5
            10.15.1中发现的无法自动睡眠问题**](#中发现的无法自动睡眠问题)
    -   [](#section-5)
    -   [**3.11
        中高端类消费级CPU的变频优化**](#中高端类消费级cpu的变频优化)

使用OpenCore引导黑苹果
======================



目前为止，最新版的OpenCore(V0.5.1)已经证明了自己在10.14.6至10.15 beta
11上的稳定性。考虑到即将来临的10.15正式版，我想现在写一份关于z390等比较新的主板，如何使用OpenCore去引导新系统是一个不错的时间点。

最近好多小伙伴问我要我的配置哈，都是买了一样的配置再问我要efi，真是厚爱了！我的efi在群文件里都有，配置如下：

**我的电脑配置**

-   Motherboard/主板: Gigabyte Z390 Elite
    
-   External Hard Drive/硬盘: Samsung 970 Pro 1T M.2 NVMe SSD
    
-   CPU: I7-9700K 散片，购于本地电脑城
-   Graphic Card/显卡: Sapphire RX5700XT 8G 超白金
    
-   Wireless Card/网卡: BCM943602CS 3-Antenna
    
-   RAM/内存: G-Skill 皇家戟RGB灯条 DDR4 3200 8G x 4
    
-   Tower Case/机箱: 酷冷至尊 MasterCase H500
    
-   Others/其他1: Gigabyte GC-Titan Ridge Thunderbolt 3 Card
    
-   Others/其他2: Qnap QNA-T310G1T Thunderbolt 3 to 10GbE Adapter
    
-   Monitor/显示器1: LG Ultrafine 4K
    
-   Monitor/显示器2: KOIOS 2418U
    
-   Keyboard/键盘: Apple 妙控键盘
    
-   Touchpad/触摸板: Apple 妙控板 2
    

**简介**
========

OpenCore(OC)是一种新的引导方式，随着越来越多的kexts开始放弃Clover,
我相信提早使用OC会对你未来使用黑苹果会有很大的帮助。这是一个自然的现象，就像变色龙被Clover淘汰，而现在OC代替Clover也是大势所趋。你应该需要看一些相关的文章，来帮助你理解我的正文内容，同时也需要下载我推荐的软件：

-   [Opencore Vanilla Desktop
    Guide](https://khronokernel-2.gitbook.io/opencore-vanilla-desktop-guide/)

-   [Getting Started With
    OpenCore](https://github.com/khronokernel/Getting-Started-With-OpenCore)

-   [OpenCore
    Configuration](https://blog.xjn819.com/wp-content/uploads/2019/10/Configuration.pdf)

-   [精解OpenCore](https://blog.daliansky.net/OpenCore-BootLoader.html)

-   Xcode （从app
    store或其他地方下载，强烈建议使用v10版本的xcode，v11花里胡哨已经劝退=。=)

-   [ProperTree](https://blog.xjn819.com/wp-content/uploads/2019/10/ProperTree.zip)最新推荐的config编辑器

-   [OpenCore](https://github.com/williambj1/OpenCore-Factory/releases)
    (下载最新的release版本)

-   [Hackintool](http://headsoft.com.au/download/mac/Hackintool.zip)

-   [MaciASL](https://blog.xjn819.com/wp-content/uploads/2019/10/MaciASL.zip)

-   [IORegistryExplorer](https://blog.xjn819.com/wp-content/uploads/2019/10/IORegistryExplorer.zip)

-   [宪武大大oc部件](https://github.com/daliansky/OC-little)

帖子更新内容查询：
==================

2019-11-16：

1.增加我的电脑配置及购物链接，问的人太多了。

2019-11-09：

1.修改章节2.6.1为中文，谢谢网友提醒，哈哈哈哈。

2.对config设置里，比较重要的设置改为红字提醒。

2019-11-08：

1.重点推荐Propertree作为config的编辑工具，再次提示不要使用opencore
configurator！！！！下载地址：https://github.com/corpnewt/ProperTree。\[Opencore
v0.5.3\]

2019-11-03：

1.重改EC章节，对台式机和笔记本进行区别对待。\[Opencore v0.5.3\]

2.增加强制睡眠相关教程，留言板说想知道一些SSDT的知识，那我在这里顺便也展示几种SSDT/Hotpatch/TgtBridge在OC下的使用说明。\[Opencore
v0.5.3\]

3.删除章节1.0中EmuVariableRuntimeDxe.efi的相关要求。\[Opencore v0.5.3\]

4.修改章节2.4.4关于applertc的说明。\[Opencore v0.5.3\]

2019-10-31：

1.添加OC
0.5.2正式版中新增加的variable相关说明，包括PowerTimeoutKernelPanic（章节2.4.5）以及ReconnectOnResChange（章节2.7.4）。\[Opencore
v0.5.2\]

2019-10-27：

1.在2.4.4段中补充了关于华硕主板重启后丢失BIOS设置以及需要按F1跳过安全模式的RTC设置，同时在3.8段中提供RTC的完整解决办法。\[Opencore
v0.5.2\]

2.在3.7.1段中补充了usb电流相关设置。\[Opencore v0.5.2\]

3.在3.7段的仿冒EC中发现OC官方样本的BUG，重新写了一下。\[Opencore
v0.5.2\]

2019-10-16：

\\1. 加入Booter/MmioWhiteList说明。\[Opencore v0.5.2\]

**0.0 BIOS设置**

直接抄袭\@黑果小兵了\~嘻嘻嘻

禁用如下：

  英文                                   中文
-------------------------------------- ----------------------------------------------------------
  Fast Boot                              快速启动
  CFG Lock (MSR 0xE2 write protection)   CFG 锁 (MSR 0xE2 写入保护)
  VT-d                                   [VT-d](https://zhidao.baidu.com/question/495526512.html)
  CSM                                    兼容性支持模块

启用如下：

  英文                   中文
---------------------- ----------------------------------------------------------
  VT-x                   [VT-x](https://zhidao.baidu.com/question/495526512.html)
  Above 4G decoding      大于 4G 地址空间解码
  Hyper Threading        处理器超线程
  Execute Disable Bit    执行禁止位
  EHCI/XHCI Hand-off     接手 EHCI/XHCI 控制
  OS type: other types   操作系统类型: 其他

**1.0 整理OPENCORE目录**

-   打开下载好的最新版OC(0.5.1)，把Doc文件夹下面的SampleFull.plist改名为config.plist，并把此文件移动到EFI目录下面。
-   打开EFI---Kexts，我们把常用的一些kexts先放进去，一般情况下你需要放如下Kexts:

 \*Lilu.kext ----------
Acidanthera驱动全家桶的底层依赖/[下载地址](https://github.com/acidanthera/Lilu/releases)

 \*Applealc.kext ----------
声卡驱动/[下载地址](https://github.com/acidanthera/AppleALC/releases)

 \*VirtualSMC.kext --------- 传感器驱动依赖
/[下载地址](https://github.com/acidanthera/VirtualSMC/releases)

 \*SMCProcessor.kext ---------- CPU核传感器/同上

 \*SMCSuperIO.kext ---------- IO传感器/同上

 \*WhateverGreen.kext ----------
核显&显卡驱动/[下载地址](https://github.com/acidanthera/WhateverGreen/releases)

 \*IntelMausi.kext ----------
Intel类千兆网卡驱动/[下载地址](https://github.com/acidanthera/IntelMausi/releases)

 \*Usbinjectall.kext ---------- USB驱动
（你也可以定制自己的USB补丁）/[下载地址](https://bitbucket.org/RehabMan/os-x-usb-inject-all/downloads/)

-   注意，一些机型用了1820A,1560,1830等网卡，需要自己放对应驱动；有线螃蟹卡也自己放一下驱动；笔记本类需要更多传感器的，请自行补齐VirtualSMC的那些传感器补丁；

-   打开EFI---Drivers，我们把常用的一些.efi文件放进去，一般情况下你需要放如下补丁:

 \*ApfsDriverLoader.efi ----------
APFS格式支持/[下载地址](https://github.com/acidanthera/AppleSupportPkg/releases)

 \*MemoryAllocation.efi ----------
帮助z390系列空出第一个512MB内存，为后面的内存注入做铺垫，若要使用hibernation功能请不要使用它/[下载地址](https://blog.xjn819.com/wp-content/uploads/2019/10/MemoryAllocation.efi_.zip)

 \*FwRuntimeServices.efi ---------- 内存寻址补丁/
[下载地址](https://github.com/acidanthera/AppleSupportPkg/releases)

 \~\~\*EmuVariableRuntimeDxe.efi ----------
帮助无原生Nvram的主板实现nvram模拟。Z370, x299,
C422主板不需要这个文件/[下载地址](https://blog.xjn819.com/wp-content/uploads/2019/10/EmuVariableRuntimeDxe.efi_.zip)\~\~已经被FwRuntimeServices合并

 \*VBoxHfs.efi ----------
HFS格式支持/[下载地址](https://github.com/acidanthera/AppleSupportPkg/releases)//在测试过程中我发现hfsplus.efi的效果更好。

 \*UsbKbDxe.efi ----------
键盘组合键的使用，有一些键盘不能放这个，比如苹果键盘/[下载地址](https://github.com/acidanthera/AppleSupportPkg/releases)

 \*VirtualSmc.efi ---------- 传感器依赖/
[下载地址](https://github.com/acidanthera/VirtualSMC/releases)

下载完成后，我们的整个EFI文件夹如下图所示：

![img](https://blog.xjn819.com/wp-content/uploads/2019/10/Screen-Shot-2019-10-07-at-2.57.00-PM.png)

**2.0 Config.plist 修改**

这一章会把config的各个大项目分开来，内容会写的繁琐一点，为了让小白明白各个选项的用途，当然有能力的人可以直接看我最前面的几个链接来配置config.plist。我这里强制要求你使用XCode
10或者propertree来编辑Config.plist，其他的任何软件我都不建议使用，包括Plistedit
pro。

**2.1 Config----ACPI**
----------------------

ACPI包括了四个部分：Add, Block, Patch,
Quirks。这里我们先把root下面的两条\#WARNING -- 1和\#WARNING --
2删除，这两条没有实际意义。

### **2.1.1 Config----ACPI-----Add**

这部分主要填写我们使用的SSDT以及DSDT文件，如果没有请把0-8的ssdt全部删除。如果你有修改的SSDT或者DSDT文件，请先将文件放入EFI/OC/ACPI下。

因为我使用雷电卡，我需要添加两条关于雷电卡的ssdt文件：

1.  Item 0
2.   Comment String Thunderbolt3-DTGP
    //填一个你自己能辨别的名字，方便知道是啥
3.   Enable Boolean YES //表示加载此SSDT，反之NO则为不加载
4.   Path String SSDT-DTGP.aml
    //为你ssdt放在EFI/OC/ACPI下的文件名，必须一致
5.  6.  Item 1
7.   Comment String Thunderbolt3\
8.   Enable Boolean YES\
9.   Path String SSDT-TB3.aml

### **2.1.2 Config----ACPI-----Block**

这个目录下是禁用一些SSDT/DSDT，似乎没什么用，我把下面的item全都删了。

### **2.1.3 Config----ACPI-----Patch**

这里我们需要填写一下热补丁。

-   在10.15中，[一些资料](https://blog.daliansky.net/Common-problems-and-solutions-in-macOS-Catalina-10.15-installation.html)指出我们需要把EC控制器(EC0)改名为EC来确保能进入10.15系统

1.  Comment: EC0 to EC
2.  Count:0
3.  Enabled:YES
4.  Find:\<4543305F\>
5.  Limit:0
6.  Mask:\<\>
7.  OemTable:\<\>
8.  Replace:\<45435F5F\>
9.  ReplaceMask:\<\>
10. Skip:0
11. TableLength:0
12. TableSignature:\<\>

需要注意的是，一些主板的EC控制器名字可能会叫H\_EC等，请自行提取DSDT并搜索PNP0C09，来获取EC控制器的名字，这些内容会在第三章中写出。

-   华擎、华硕、微星主板可能会遇到RTC问题而无法进入系统，这同样需要添加hotpatch补丁来解决：

1.  Comment: RTC fix
2.  3.  Count:0
4.  5.  Enabled:YES
6.  7.  Find:\<A00A9353 54415301\>
8.  9.  Limit:0
10. 11. Mask:\<\>
12. 13. OemTable:\<\>
14. 15. Replace:<A00A910A FF0BFFFF>
16. 17. ReplaceMask:\<\>
18. 19. Skip:0
20. 21. TableLength:0
22. 23. TableSignature:\<\>

### **2.1.4 Config----ACPI-----Quirks**

此目录下有五项，选择与解释如下：

------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  **Quirks**         **Value**   **解释**
------------------ ----------- -----------------------------------------------------------------------------------------------------------------------------------------------------------
  FadtEnableReset    NO          一些旧的主板需要对FADT进行标记来激活电脑的开机和关机功能，这里我们不许要启动它（如果你遇到关机变重启，可以打开试试，我们之后也会在nvram中将这个问题修复）

  NormalizeHeaders   YES         清理ACPI头，一些主板的ACPI表需要打开这个修复启动。但如果补丁点亮系统，请试试NO

  RebaseRegions      NO          换硬件、升级BIOS等对硬件的操作会对ACPI表产生影响，一般不需要打开

  ResetHwSig         NO          休眠相关项，台式机不需要

  ResetLogoStatus    NO          顾名思义了，关了
  ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

**2.2 Config-----Booter**
-------------------------

内存相关选项设置。

### **2.2.1 Config---Boot---MmioWhitelist**

默认的第一项是为Haswell芯片提供的内存寻址修复，如果此类芯片碰到内存相关问题，请开启它(enable选择yes)。

默认第二项是开机卡PCI Configuration这里。ACPI、PCI
device同时释放到内存时发生0x1000内存地址被占用而卡在PCI
Configration.如果碰到此类问题，请开启它。

### **2.2.2 Config---Boot---Quirks**

此项与Fwruntimeservice.efi有关。在aptiomemoryfix停更后，此补丁已经更名为Fwruntimeservice,
并将一些功能与OC合并、模块化。对于z390等无法原生nvram的主板来说，这里的选项需要格外注意。当然我也会把像z370、x299、c422这样支持原生nvram的选择方法一并写进去。

-   AvoidRuntimeDefrag:大部分UEFI都会写入时间、电源管理等信息，这个所有黑苹果主板都应该选择YES。

-   DevirtualiseMmio:内存注入方式包括KASLR方式(分布式注射到各个内存地址中）以及连续性方式。在使用KASLR时，PCIE加载到内存，可能会占据所有所有avaliable值而导致OC的内核以及内核缓存无法注入，导致启动失败。使用KASLR方式很容易出错，我们更适合使用连续性的内存注入方式，并在boot
    args中添加slide=1（这个之后会写）。因为我们之后会添加这个slide=1去使用连续性的内存注入方式，所以这个选项我们选择NO。（不知道你能不能理解，意思是所有的主板都选NO!
    我暂时还没发现能用KASLR的台式机，哈哈哈哈）。

-   DisableSingleUser:这里关乎主机是否能开启单用户模式。什么是单用户模式，请[看此文章](https://support.apple.com/zh-cn/HT201573)。如果你觉得有用就开启它，我选择NO，我不需要。

-   DisableVariableWrite:非原生NVRAM主板需要模拟nvram.plist进而写入variable值，因此我们要禁止此项来防止其他程序对nvram进行写入，我们这里选YES。需要注意一点，如果你的主板支持原生nvram(z370/x299/c422)，请选择NO！

-   DiscardHibernateMap:当电脑从休眠(hibernation)中唤醒时,硬盘里的资料会恢复到内存中去，但这个时候OC的内核以及内核缓存等也会写入，这样可能导致冲突，这个选项是帮助我们解决这个问题的。而目前来看，除了z370/x299/c422都无法进行休眠（注意睡眠sleep和休眠hibernation是两个概念），台式机的话就更不需要休眠功能了，这里我选择NO。这里我们也不讨论如何休眠。

-   EnableSafeModeSlide:安全模式下是否启用连续性的内存注入方式。这个不是那么重要，你不会每天进安全模式的。像z390这样本来也不用分布式注入内存方式的（KASLR），我就选择YES，与正常情况下保持一致。

-   EnableWriteUnprotector:保证nvram能正常写入而不受到UEFI内的一些服务的影响，无论什么主板都要选择YES。

-   ForceExitBootServices:这个选项是让那些非常老旧的主板也能使用内存寻址，正常情况下选NO。

-   ProtectCsmRegion:官方对此项目的解释与AvoidRuntimeDefrag类似，除非你明白这是什么，不然选择NO，其实我也不明白。

-   ProvideCustomSlide:是否使用slide值。其实我自己也没有机会使用KASLR这种内存注入方式，所以我一直都是选择连续性注入内存并配合slide，所以我选择YES。如果你对KASLR有一定的认知并会运用，请注意这个值。

-   SetupVirtualMap:是否建立虚拟内存并对物理内存进行映射。我们在开机时，OC的程序需要一块连续性的内存进行存放内核等东西，而实际的物理内存一般都是分散的。因此，我们通过虚拟内存建立连续性内存供OC使用，并映射到分散的物理内存中。这里我们选择YES。

-   ShrinkMemoryMap:苹果的内核对内存的规范性有具体的要求。目前来看新的主板的规范性都是符合苹果的要求的，我们并不需要启动它，选择NO。如果你出现内存问题而无法开机，请打开此项测试。

**2.3 Config-----DeviceProperties**
-----------------------------------

此项是用来注入你的设备的，主要是显卡和声卡两部分。同样你也可以定制一些设备到你的关于本机--系统报告--PCI列表中，尽管没有多大的意义。

### **2.3.1 声卡**

这里首先我们需要找自己声卡的地址，打开hackintool，到PCI列表中寻找IOReg
IOname那栏，一般声卡的设备名称叫做HDEF或者HDAS:![img](https://blog.xjn819.com/wp-content/uploads/2019/10/Screen-Shot-2019-10-09-at-1.07.42-AM.png)

这里我们找到的声卡PCI路径为PciRoot(0x0)/Pci(0x1f,0x3)。我们把预先填写在那里的PciRoot(0x0)/Pci(0x1b,0x0)项替换成我们真正的声卡路径。后面一段我们看到预先填写的声卡ID为\<01000000\>，这里我们需要把它换成自己系统的ID。

-   打开先前要求下载的Hackintool，到声卡选项部分，我们可以看到自己的声卡编号，我的是ALC1220。![img](https://blog.xjn819.com/wp-content/uploads/2019/10/Screen-Shot-2019-10-08-at-11.54.12-PM.png)

-   打开黑果小兵关于声卡的[博客](https://blog.daliansky.net/AppleALC-Supported-codecs.html)，并搜索我们的声卡型号:ALC1220，我们发现我们的声卡型号对应1,
    2, 3, 5, 7, 11, 13, 15, 16, 27, 28, 29, 34的layout
    ID。我们需要一个个测试过去，选定自己能用的。这里我们选择7这个ID进行测试，将7转化成16进制格式为07，后面为了满足格式要求添加6个0，则为07000000，将这个值替换刚才预先填的01000000中；如果我们测试ID为27，27的16进制为1b，补上6个0则为1b000000。

-   一些奇怪的声卡可能需要注入device ID才能用，不知道为啥：

1.  PciRoot(0x0)/Pci(0x1f,0x3)
2.  device-id data \<70a10000\> //这个device
    id是固定的，不要问为什么是这个id
3.  layout-id data \<0b000000\> //这个Layout id我瞎写的，你按实际情况写

-   如果你测试的ID都无效，请确保你的操作过程正确、并测试用万能声卡补丁来替换AppleALC这个补丁。如果都不行，你可能需要[自行编译声卡补丁](https://blog.daliansky.net/Use-AppleALC-sound-card-to-drive-the-correct-posture-of-AppleHDA.html)。

### **2.3.2 核心显卡**

打开PciRoot(0x0)/Pci(0x2,0x0)这项，此项为驱动核心显卡。驱动核心显卡我们要分情况讨论:1.只有核心显卡的DP显示器用户
(HDMI我会在进阶设置中写）；2.没有核心显卡的用户；3.有核心显卡并用独显做主力的用户。注意，这里我们只讨论8代和9代CPU的机器，其他CPU机型的请在论坛或者[黑果小兵博客](https://blog.daliansky.net/Intel-core-display-platformID-finishing.html)中搜索相关代码。

#### **2.3.2.1 只有核心显卡的DP显示器用户**

8代和9代的核显ID为:3E9b0007，device
ID为3e9b0000，但是我们需要符合一定的顺序格式填入进去，至于为什么是这么奇怪的一个顺序，我也不知道，你照抄就是了：

1.  AAPL,ig-platform-id data \<07009b3e\>
2.  device-id data \<9b3e0000\>
3.  enable-hdmi20 data \<01000000\>
    //如果你的hdmi不是2.0的（主板说明书会写）,不需要填写这行。
4.  framebuffer-unifiedmem data \<00000080\> //核显显存相关

#### **2.3.2.2 没核心显卡的用户**

cpu带f的cpu (e.g. 9100f 9900kf),
Xeon等不带核心显卡的用户不需要管这项，直接把AAPL,ig-platform-id选项卡删了。

#### **2.3.2.3 有核心显卡并用独显做主力的用户**

这种情况我们一般把核心显卡作为加速用，而显示则用独立显卡。这样，我们填一个作为加速用的核显ID即可了：

1.  AAPL,ig-platform-id data \<0300983e\>

### **2.3.3 Block**

这里是禁用一些设备的，我们按默认就行了，不需要任何修改。

**2.4 Config-----Kernel**
-------------------------

这里是内核相关选项。

### **2.4.1 Config-----Kernel-----Add**

这里我们需要填写kexts的相关资料。值得注意的是OC的kexts填写必须注意顺序，比如applealc的依赖是lilu，那么lilu必须填在第一个；SMCProcessor.kext依赖于Virtualsmc.kext。那virtualsmc必须放在SMCProcessor.kext之前。

这里默认情况下很多我们需要的补丁已经被加载里面了，但是enabled那块我们要手动改成yes去开启它，把一些不用的删了：

1.  Item 0
2.   BundlePath String Lilu.kext //kext的名字
3.   Comment String //你自己填一个注释，可以不填
4.   Enabled Boolean YES //启动此补丁，反之则为关闭
5.   ExecutablePath String Contents/MacOS/Lilu
    //通过右键kext显示包内容查找lilu运行文件的真正路径
6.   MaxKernel String
    //此补丁支持的最大系统版本，填19为10.15，18位10.14；我们一般情况下留空
7.   MinKernel String //此补丁支持的最小系统版本
8.   PlistPath String Contents/Info.plist
    //kext的plist位置，可以右键kext显示包内容查找正确路径
9.  10. ............
11. ............
12. 13. Item 4
14.  BundlePath String WhateverGreen.kext\
15.  Comment String\
16.  Enabled Boolean YES\
17.  ExecutablePath String Contents/MacOS/WhateverGreen.kext\
18.  MaxKernel String\
19.  MinKernel String\
20.  PlistPath String Contents/Info.plist\
21. 22. ............
23. ............
24. Item 7
25.  BundlePath String USBPorts.kext\
26.  Comment String\
27.  Enabled Boolean YES\
28.  ExecutablePath String //一些没有执行文件的kext不需要填写
29.  MaxKernel String\
30.  MinKernel String\
31.  PlistPath String Contents/Info.plist\
32. 33. ............
34. ............

### **2.4.2 Config-----Kernel-----Block**

禁用一些kexts，这里好像没啥用，不用理会。

### **2.4.3 Config-----Kernel-----Emulate**

此选项帮助Ivy Bridge
和一些不受支持的CPU加载电源管理的，我们这里不做此方面讨论（我没这么老的CPU）。所有选项按默认即可。

### **2.4.4 Config-----Kernel-----Patch**

这里是为一些kext打补丁用的。

我们可以看到样本里面有四个补丁，都是关闭着的，其中有两个是关于APPLE
RTC的，这对于华硕主板来说相对比较重要，这里我们需要对appleRTC相关的两个补丁一一测试，打开-----Enabled---YES其中一个，即可。如果不行，关闭一个打开另一个。这样能解决华硕主板重启丢失BIOS设置以及需要按F1跳过安全模式，当然RTC仍然需要进一步的设置，我会在进阶教程中详细写一下这一块。

### **2.4.5 Config-----Kernel-----Quirks**

这里是内核相关的快捷选项，比较重要。

AppleCpuPmCfgLock:请确保你的BIOS中已经关闭了CFG锁。如何解CFG锁我在[这篇文章](https://blog.xjn819.com/?p=317)中有详细教程。如果你不会解这个锁，你就选择YES，解锁的情况下选择NO。注意，CFG的解锁对之后的进阶教程相关度极高，有能力还是解一下吧！

AppleXcpmCfgLock: 同上！

AppleXcpmExtraMsrs: 主要在没有原生电源管理的CPU上启用，一般是Haswell-E,
Broadwell-E, Skylake-X这三种CPU需要填写YES。除此之外的CPU选择NO。

CustomSMBIOSGuid: 戴尔笔记本专用项，我们选择NO。

DisableIoMapper:
禁用vt-d，我们在BIOS里已经禁用vt-d了，这里我们选择NO就行了。

ExternalDiskIcons:
AHCI控制器相关，现在的主板都对AHCI支持的很好，一般选择NO。

LapicKernelPanic: 适用于HP笔记本的内核奔溃选项，我们选择NO。

PanicNoKextDump:
防止kext出错打报告而让我们看不到真正的panic原因，这个随便选，我选择NO。

PowerTimeoutKernelPanic:
当你遇到睡眠不能唤醒，只有重启后才能睡眠唤醒，请试试选择YES。

ThirdPartyTrim:
开启Sata类SSD的trim功能，我没有sata类的ssd，我选择NO。自行根据情况选择。

XhciPortLimit: 解除15个端口限制，我选择YES。

**2.5 Config----Misc**
----------------------

这里都是一些开机引导类的设置。

### **2.5.1 Config-----Misc-----BlessOverride**

这个选项是帮助我们寻找一些不寻常的EFI位置的，除非你有这种情况，不然我们不需要填写任何东西。

### **2.5.2 Config-----Misc-----Boot**

ConsoleBehaviourOs:
一般是留空，如果留空开机显示效果不佳，请填ForceText。

ConsoleBehaviourUi: 同上。

HibernateMode:
检测休眠模式。我们的机器一般都不支持休眠，选none。如果你的主板支持原生nvram、并想测试休眠，可以考虑填auto。

HideSelf: 隐藏自身的EFI引导盘选项，选YES。

PollAppleHotKeys:是否开启一些热键功能，包括Cmd+K;Cmd+S。我选的是yes。如果你开机发现键盘无法选择，也选NO，并且删除OC/Drivers下的UsbKbDxe.efi
。

Resolution:
开机分辨率。比如我的显示器是4K、16：9的，我就填写3840×2160。这个你根据情况填写或者不填。如果遇到开机苹果LOGO很大，你需要按你的分辨率填写。另外，我发现了一件很神奇的事情：技嘉的主板LOGO大小跟开机的大雕图的尺寸相关，我把大雕图换成了4K，开机的苹果LOGO也变成4K了。。。。神奇

ShowPicker: 是否显示开机启动盘选项，比如MAC,WINDOWS那些。我们选择YES。

Timeout:
倒计时进入指定硬盘，这里我们按需求填写，我填写5，代表5秒钟进入指定硬盘。

UsePicker:
是否使用OC的开机启动盘选项，我们选YES。之后可能会有新的第三方主题支持的话，我们需要选NO。

### **2.5.3 Config-----Misc-----Debug**

是否开启debug模式，这里我们暂时不需要，全部忽略过。

### **2.5.4 Config-----Misc-----Entries**

这里是帮助我们添加一些你希望的引导路径，这个会在之后的进阶教程中讲，这里暂时略过不填写。

### **2.5.5 Config-----Misc-----Security**

AllowNvramReset:
是否在开机引导项中加入重置nvram缓存功能的选项，我们选YES。

ExposeSensitiveData: 因为要使用到nvram，这个数值我们必须填3。

HaltLevel: 按默认设置即可。

RequireSignature: 黑苹果的vault加密方式，我们不需要这个功能，选择NO

RequireVault: 是否开启黑苹果加密，不需要，选NO

ScanPolicy:
这里暂时填0。我们也许会碰到开机的时候默认进入的系统永远是WINDOWS，并无法更改，之后我们在进阶教程中讲述，如何让MAC盘排在第一个，让WIN排在后面。

### **2.5.6 Config-----Misc-----Tools**

这里是加入一些开机时候的工具的。其实我觉得只有重置nvram的工具是有用的，但之前的设置里面我们已经开启了，这个选项就没啥用了，不用理会。

**2.6 Config----NVRAM**
-----------------------

这是关于nvram的选项卡。

### **2.6.1 Config-----NVRAM-----Add**

1.  4D1EDE05-38C7-4A6A-9CC6-4BCCA8B38C14
2.  3.   UIScale Data \<02\>
    //这里填写01为普通的UI显示模式，02为开启HIDPI的UI显示模式，我选择02
4.  5.  7C436110-AB2A-4BBB-A880-FE41995C9F82
6.   boot-args String Slide=1 darkwake=0 -v
    //slide=1表示从第一组内存开始连续注入；darkwake=0代表一键唤醒机器并偏好设置中节能选项的小憩功能。如果你要用小憩功能请填8；
    -v是跑代码，在没装好稳定的黑果前我建议加上，方便定位错误，弄完后再删除-v
7.   bootercfg String log=0 debug=0 level=0
    //这条自己添加进去，是关闭开机时的代码的。
8.   csr-active-config Data <e7030000> //关闭SIP保护
9.   nvda\_drv Data \<31\>
    //对10.13系统之前的N卡的相关设置，我们不做讨论。
10.  prev-lang:kbd Data \<[7a68 2d48 616e 733a 3235
    32]{style="color: #ff0000;"}\>
    //语言设置相关，记得改成这个，这个是中文

### **2.6.2 Config-----NVRAM-----Block**

禁用一些nvram变量，我们这里按默认设置不必理会。

### **2.6.3 Config-----NVRAM-----LegacyEnable**

如果你的主板不支持原生NVRAM，请一定要选择YES!
如果你的主板是z370/x299/c422/z270等支持原生nvram的，填no。

### **2.6.4 Config-----NVRAM-----LegacySchema**

这里是nvram的变量设置，大部分默认已经填好，我们只需添加两个变量即可。

打开7C436110-AB2A-4BBB-A880-FE41995C9F82这一栏，添加两个item如下：

1.  item 11 String efi-boot-device
2.  item 12 String efi-boot-device-data

**2.7 Config----PlatformInfo**
------------------------------

这里我们填合适的机型。对于最近一代的主板来说，一般的原则，只有核显的机器我们选Macmini8,1；只有独显的机器我们选择iMac
Pro 1,1;有核显和独显的我们选择iMac 19,1。

因为这部分内容太过复杂，其实很多内容都不必要填写，我们直接删除Datahub,PlatfromNVRAM,SMBIOS这三项，无需填写。

### **2.7.1 Config-----PlatformInfo-----Automatic**

这里意思是是否自动填写系统信息。因为后面的很多选项都好繁琐，我们只要认真填几个选项就行了，这里我选YES，不重要的信息让它自动填。

### **2.7.2 Config-----PlatformInfo-----Generic**

这里是我们需要填写的三码部分。获得三码，我们可以运用一下Clover的[Clover
Configurator](https://blog.xjn819.com/wp-content/uploads/2019/10/Clover-Configurator.zip)帮我们生成一下相关的数据：

-   打开Clover
    configurator，并到SMBIOS选项卡中，选择合适的机型，这里我们以iMac19,1
    为例：

![img](https://blog.xjn819.com/wp-content/uploads/2019/10/Screen-Shot-2019-10-09-at-4.36.37-PM.png)

-   我们换到Rt
    variables里，点击ROM下的生成，获得一个ROM编号，这样我们就获得了所有需要的信息了。![img](https://blog.xjn819.com/wp-content/uploads/2019/10/Screen-Shot-2019-10-09-at-4.40.19-PM.png)

-   我们整理一下刚才获得的信息并依次填入Generic下面即可。

-   ~~值得注意的是，SystemUUID这一项最好留空，让OC自动生成，它会影响你的WINDOWS激活状态。~~

### **2.7.4 Config-----PlatformInfo-----剩余部分**

UpdateDataHub:选择YES

UpdateNVRAM:选择YES

UpdateSMBIOS:选择YES

UpdateSMBIOSMode:选择Create

UEFI:UEFI相关的补丁以及设置项。

ConnectDrivers:是否加载所有UEFI补丁，这里我们选YES

**2.8 Config----UEFI**
----------------------

这里我们需要填写UEFI相关的设置。

### **2.8.1 Config-----UEFI----ConnectDrivers**

是否加载补丁，我们选择YES

### **2.8.2 Config-----UEFI----Drivers**

把我们之前放在OC/EFI/Drivers下面的驱动一一填上，这里我们也注意一下填入的顺序：

1.  Drivers
2.   item0 String ApfsDriverLoader.efi
3.   ........................ MemoryAllocation.efi
4.   ........................ FwRuntimeServices.efi
5.   ........................ VBoxHfs.efi
6.   ........................ UsbKbDxe.efi

### **2.8.3 Config-----UEFI----Input**

此选项是原生apple开机热键的选项，需要配合我们之前设置的PollAppleHotKeys=yes以及UsbKbDxe.efi补丁一起用。下面的设置完全按照默认情况就行了。因为我的键盘是苹果原生键盘，不支持这个功能，所以我直接PollAppleHotKeys里填了NO,这里也不会生效的。

有一点需要说，如果你是华硕的z87或者z97，你需要打开PointerSupport这个选项。

### **2.8.4 Config-----UEFI----Protocols**

AppleBootPolicy: 虚拟机的mac需要用的，我们选择NO。

AppleEvent: 虚拟机并具有vault的mac需要用的，我们选择NO。

AppleImageConversion: 重建apple图标，选择NO。

AppleKeyMap: 重建苹果功能键，选择NO。

AppleUserInterfaceTheme: 似乎是支持主题了？没看懂，选择NO。

ConsoleControl: 主机控制界面，我们选择YES。

DataHub:重建datahub，这里我们选NO。

DeviceProperties: 虚拟机需要，我们选NO。

FirmwareVolume: VAULT相关项，我们选NO。

HashServices: VAULT相关项，我们选NO。

UnicodeCollation: 旧的主板需要，我们选NO。

### **2.8.5 Config-----UEFI----Quirks**

AvoidHighAlloc: 回避高位内存寻址，我们已经用了slide了，这里选No吧。

ClearScreenOnModeSwitch: 好像是新的选项，暂时不知道干嘛的，选No吧。

ExitBootServicesDelay:旧主板需要给予主板退出时间（单位为微秒），较新的主板直接填0。旧的主板比如Z87pro，填3000000-5000000

IgnoreInvalidFlexRatio：如果你没有在bios中解锁CFG，一定要选YES。

IgnoreTextInGraphics:
一些固件会同时输出文字和视频信息导致花屏，如果出现这种情况试试选NO，我这里选YES。

ProvideConsoleGop:在选择系统画面前，你可能看到一些你config配置错误的信息，你可以根据这信息调整自己的配置，也可以选择YES忽略，我选择YES。

ReconnectOnResChange:
如果你遇到开机直到登录界面之前一直是黑屏，请试试选择YES。

ReleaseUsbOwnership:大部分的主板都有自动释放USB所有权的功能，我们选NO。如果你开机键盘鼠标卡死了，或者USB失灵，试试选Yes。

ReplaceTabWithSpace:看不懂，选no。

RequestBootVarRouting: 如果你要使用"启动磁盘"
选项，你需要选择YES，这里选择YES。

SanitiseClearScreen: 清理屏幕分辨率，选择YES。

**2.9 小节**
------------

到这里，我们应该可以通过OC正确引导MAC
OS了，但是还有很多问题需要去修补，包括模拟nvram，寻找EC控制器并做一个，原生的电源管理等。我会在下一个章节写这些东西。

**3.0 OpenCore 完善**

**3.1 模拟NVRAM**
-----------------

对OC而言，NVRAM是非常核心的一环，不管是原生还是模拟的。如果你是原生nvram的主板(z270/z370/x299/c422)，请不必理会这章节。这张的主要内容为生成模拟的NVRAM.plist。

-   首先打开我们之前下载好的opencore，进入目录下的Utilities/LogoutHook，并将LogoutHook放入一个安全的位置。这里我推荐将他放到文档目录下。

-   右键finder，前往目录，填/Users,
    再点进入以你名字命名的文件夹，既能看到Documents(文档）目录了，把我们的LogoutHook放在里面。

-   打开Terminal （终端），输入一下命令：

1.  sudo defaults write com.apple.loginwindow LogoutHook
    /Users/你的用户名/Documents/LogoutHook/LogoutHook.command
2.  比如：
3.  sudo defaults write com.apple.loginwindow LogoutHook
    /Users/xjn/Documents/LogoutHook/LogoutHook.command

-   终端会提示要求你输入密码（密码打进去不会显示）

-   重启后，你会在/EFI/下看到nvram.plist，代表已经成功模拟了。

-   ~~值得一提，nvram.plist在开机的加载需要之前我们要求放入的EmuVariableRuntimeDxe.efi来读取，请确保此补丁存在。~~

**3.2 建立自己的开机选择系统目录**
----------------------------------

这个教程主要针对的是非原生nvram主板的用户，如果你是原生nvram的用户，直接在偏好设置---启动磁盘中选定你希望设置为默认启动的磁盘即可，不必往下看浪费时间！

非原生nvram用户必须完成我之前要求生成的nvram.plist。

这章我分成两部分，第一部分是让OC只扫描我们的MAC盘，第二部分是在开机选项中将win等其他系统排在mac后面。

### **3.2.1 第一部分**

我们首先要对Config---Misc---Security---scanpolicy这个值进行修改，默认的是0，代表着扫描所有硬盘，而我们现在只让它扫我们的苹果系统硬盘。

感谢\@xlivans提供的OC扫描策略：

> \#\# OC-引导扫描策略
>
> -- 设置位置：`Misc\Security\ScanPolicy`
>
> -- \*\*\*\*定义：\*\*\*\*
>
> （01）0x00000001 --- 限定为文件系统，由以下`允许扫描文件系统子项`开启
>
> （02）0x00000002 --- 限定为设备类型，由以下`允许扫描设备类型子项`开启
>
> `允许扫描文件系统子项`：
>
> （03）0x00000100 --- 允许扫描APFS文件系统
>
> （04）0x00000200 --- 允许扫描HFS文件系统
>
> （05）0x00000400 --- 允许扫描EFI系统分区文件系统
>
> `允许扫描设备类型子项`：
>
> （06）0x00010000 --- 允许扫描SATA设备
>
> （07）0x00020000 --- 允许扫描SAS和Mac NVMe设备
>
> （08）0x00040000 --- 允许扫描SCSI设备
>
> （09）0x00080000 --- 允许扫描NVMe设备
>
> （10）0x00100000 --- 允许扫描CD / DVD设备
>
> （11）0x00200000 --- 允许扫描USB设备
>
> （12）0x00400000 --- 允许扫描FireWire设备
>
> （13）0x00800000 --- 允许扫描读卡器设备
>
> `扫描策略数值`=（01）+（02）+1个或数个`允许扫描文件系统子项`+1个或数个`允许扫描设备类型子项`
>
> 例如：希望扫描对象是APFS文件系统的USB设备，`扫描策略数值`=（01）+（02）+（03）+（11），经16进制加法计算得出，`扫描策略数值`=`0x200103`。
>
> `注意`，使用时需将16进制转换为10进制。示例最终`扫描策略数值`=`2097411`
>
> -- 几种扫描策略
>
> -- `F0103`
> ---官方推荐值：（01）+（02）+（03）+（06）+（07）+（08）+（09）
>
> 最终`扫描策略数值` = `983299`
>
> -- `0`---允许扫描所有已知文件系统+允许扫描所有已知设备类型。
>
> -- `2F0303` ---官方推荐值+允许扫描HFS文件系统+允许扫描USB设备
>
> 最终`扫描策略数值` = `3080963`



我们这里让OC只扫描MAC盘。根据说明，（1）+（2）是必须选的；因为我的MAC是APFS，所以系统子项类我选（3）；我的MAC是安装在NVME上的，所以我在设备类型上选择（09），如果你是安装在sata盘上的，你应该选（6）。

这样我们的公式就是：

1.  （1）+（2）+（3）+（9）= 0x00000001+0x00000002+0x00000100+0x00080000

拿起苹果自带的计算器，按住coomand+3切换到编程型计算器，并转换到16进制模式：

![img](https://blog.xjn819.com/wp-content/uploads/2019/10/Screen-Shot-2019-10-12-at-3.54.31-PM.png)

输入：

1.  1+2+100+80000=80103

得到数值后，我们再按一下转换10进制的按键，得出524547这个数值。

我们把524547填到scanpolicy中，重启，你就会看到第一个选项就是你的MAC盘了。但如果你还安装了WINDOWS什么的，选项中却没有了，别急，我们现在要把WIN的引导添加到mac的后面去。注:似乎oc还不能引导ubuntu，请用Bios快捷键进入，未证实。

### **3.2.2 第二部分**

现在我们要在开机画面中，将其他的一些系统排在mac后面。此项能需要你下载debug版本的Opencore,请在文章开始部分提到的Opencore程序下载界面进行下载，并备份好你目前的EFI。

首先我们需要把下载好的Opencore-Debug版本里的efi/boot/BOOTx64.efi
以及efi/OC/OpenCore.efi两个文件替换到你正在使用中的EFI里去。用XCODE修改你正在使用的EFI/OC/Config.plist，修改内容如下：

1.  Misc
2.   Debug
3.   DisableWatchDog Boolean YES
4.   Target Number 65
5.  6.  7.   Security
8.   ScanPolicy Number 0
    //这里我们要先改为0来寻找windows的地址，之后找到后改回之前算出来的即可

接着，我们需要寻找你其他系统的UUID，我们打开终端，输入：

1.  diskutil list

我们找到你需要的盘的盘名，比如我的windows在disk0这个位置，而引导WIN的EFI文件夹的盘位是disk0s1。注意，这里我们不讨论Gpt格式的WIN引导位置该在哪里，如果你实在不清楚，可以把disk0s1以及dsik0s2都记录下来。![img](https://blog.xjn819.com/wp-content/uploads/2019/10/Screen-Shot-2019-10-12-at-5.22.43-PM.png)

接着输入：

1.  diskutil info disk0s1

在输出内容里，我们需要的是`Disk / Partition UUID`，我的是FF555974-AB3F-40B7-8530-AE6462E197CE，把它记下来。

现在我们通过oc的开机选项直接重启到windows，我们打开diskgenius，并且到我们mac的EFI盘符下，我们看到有一个日志报告opencore-xxxxx-xxxxx生成，为了好记，我们右键把它改名叫111.txt。

![img](https://blog.xjn819.com/wp-content/uploads/2019/10/QQ%E6%88%AA%E5%9B%BE20191012085747.png)

重启回到mac，加载efi分区，打开刚才的111.txt，我们搜索刚才记录下来的FF555974-AB3F-40B7-8530-AE6462E197CE，我们搜到如下内容，而标注的即是WINDOWS的引导路径：![img](https://blog.xjn819.com/wp-content/uploads/2019/10/Screen-Shot-2019-10-12-at-5.29.00-PM.png)

把之前我们备份好的EFI，全部替换回去。把disablewatchdog，target，scanpolicy都改回原来的。这样我们的EFI又回到正式版本了，而不是DEBUG版本了。

打开config，我们把win的引导路径添加到misc----entries，并在此下面添加一个item,输入如图内容：

![img](https://blog.xjn819.com/wp-content/uploads/2019/10/Screen-Shot-2019-10-12-at-5.32.22-PM.png)

保存即可，重启后，你会看到windows10放在了mac的下面。

tips:
你可以在config----misc---boot---showpicker选择no，就不会看到选择界面了，而当你需要时，只需要在开机时候按住option或者esc就可以唤出选择界面了，非常白果的体验哦。

**3.3 提取DSDT**
----------------

提取DSDT是我们之后完善系统的必需品，没有他我们无法找到相关的硬件位置，我们可以通过Clover直接提取，这里我们需要一个空的U盘。我的教程是非常偏向小白的，所以这里提取我也会用到windows，以及[Diskgenius](http://www.diskgenius.cn/download.php)这个软件，做最简单的示范。

-   插入U盘，我们打开diskgenius，选中我们的U盘，并选择顶部菜单栏的快速分区：

![img](https://blog.xjn819.com/wp-content/uploads/2019/10/Screen-Shot-2019-10-11-at-10.39.45-PM.png)

-   严格按照我的图示选择，不要创建esp msr分区，并且分区格式为fat32。

-   格式化完成后，放入我从黑果小兵镜像包提取出来的[EFI（点击下载）](https://blog.xjn819.com/wp-content/uploads/2019/10/EFI-1.zip)放进去。这是一个clover引导，但并不能引导你的系统，只能提取DSDT。

-   插上U盘，重启，通过U盘引导，看到Clover界面，我们按F4，这样原始的DSDT文件就收集好了。

-   重新通过OC引导进入系统，我们打开U盘，EFI/Clover/ACPI/Orgin下，有我们的原始ACPI内容，我们只需要DSDT.aml这个就行了，保存到安全的地方。

**3.4 加载原生电源管理**
------------------------

在提取dsdt后，我们可以得到相关里硬件名字及目录，这样我们就可以加载原生电源管理。这里非常感谢宪武大大在ssdt这块的付出成果！我们先下载一下宪武大大的[OC-SSDT包](https://blog.xjn819.com/wp-content/uploads/2019/10/OC-little.zip)。

以下的内容，你需要文章开始阶段提供下载的MaciASL以及刚才提取的DSDT.aml

-   用MaciASL打开DSDT.aml
-   搜索你cpu的名字。一般情况下，CPU的名字可能是:
    `PR.CPU0`,`PR.P000`,`PR.PR00`,`SB.CPU0`,`SB.P000`,`SB.PR00`,
    `SCK0.C000`,
    `SCK0.CPU0`。请依次搜索直到找到自己的CPU名字，比如我的就是`SB.PR00![img](https://blog.xjn819.com/wp-content/uploads/2019/10/Screen-Shot-2019-10-14-at-4.54.52-PM.png)`

打开宪武大大的OC-SSDT包，到x86目录下，我们看到宪武大大已经把大部分不同名字的CPU的dsl文件都做好了。我的cpu名字叫`SB.PR00`，我直接打开SSDT-PLUG-\_SB.PR00.dsl这个文件，左上角另存为（save
as), 其中文件格式(file format)必须选择ACPI Machine Language
Binary，文件名字随便写吧，我就叫plug-xcpm.aml，记住后缀为aml。

将plug-xcpm.aml放入EFI/OC/ACPI下，并在config.plist中添加加载此aml文件:

1.  <dict>
2.  <key>Comment</key>
3.  <string>XCPM</string>
4.  <key>Enabled</key>
5.  <true/>
6.  <key>Path</key>
7.  <string>plug-xcpm.aml</string>
8.  </dict>

加载后，重启，并清理一次nvram，我们看到偏好设置--节能中，原生电源管理已经被加载了。![img](https://blog.xjn819.com/wp-content/uploads/2019/10/Screen-Shot-2019-10-14-at-6.18.38-PM.png)

**3.5 加载节能五项**
--------------------

节能五项是白果台式机中，偏好设置---节能中的选项。在加载原生电源管理后，我们一般有4项节能出现，而第五项"断电后重启"这项还需要加载PPMC才能出现。虽然说这项功能没啥鸟用，但对于强迫者而言，少一个一定很难受吧。如果你是笔记本，不需要看这章，白果笔记本本身就没有。

写吐了，花里胡哨的东西以后再写了。。。

**3.6 Mac OS 10.15下解锁S/L/E目录**
-----------------------------------

在10.15系统中，尽管你已经通过config解锁了SIP，但系统目录仍然需要命令去开启。这里群友bugprogrammer给出了一个一劳永逸的解决方案，请到他的博客中查看方法：[解锁macOS10.15的系统分区](http://www.bugprogrammer.me/2019/07/13/unlockSystem.html)

**3.7 关于EC控制器**
--------------------

EC控制器是电脑自带的一个叫embedded
controller的部件。在10.15的系统环境中，笔记本电脑必须重命名原来的EC，而一些台式机主板则需要禁用。下面我会分开来讲解如何禁用EC、如何加载USB电源管理支持。

### **3.7.1 禁用EC控制器**

之前我在2.1.3章节中提供了重命名这种方式去讲EC0更名为EC，其实这种方法是只适合笔记本的，台式机最好还是禁用EC。

我这里会把笔记本重命名EC以及台式机禁用EC写在一起。

打开之前提取出来的DSDT.aml，搜索`PNP0C09`，这里我搜到我的ec真实名字叫做H\_EC，你的可能叫EC0或者别的什么奇怪的名字。

这里我可以看到我的H\_EC已经是屏蔽掉的，怎么判定，你看下面有一个Return
(Zero)，意味着这个部件是不生效的，即禁用。这样的情况我们不需要做任何SSDT去禁用这个真的EC。

![img](https://blog.xjn819.com/wp-content/uploads/2019/10/Screen-Shot-2019-10-14-at-11.19.44-PM.png)

那么什么样的情况是需要我们去屏蔽的呢？我发现基本上华硕的台式机主板都会启用这个EC控制器，这里我截图了一张华硕主板的EC部件图，我们同样在DSDT中搜索`PNP0C09`，我们看到这种情况下，这个叫EC0的EC控制器是开启的，注意他没有return
(Zero)这个语句，我们需要通过SSDT去屏蔽它。

![img](https://blog.xjn819.com/wp-content/uploads/2019/10/Screen-Shot-2019-10-27-at-9.28.46-PM.png)

这里我提供了一个禁用EC0的补丁，请直接下载，打开后左上角另存为（save as),
其中文件格式(file format)必须选择ACPI Machine Language
Binary，文件名字随便写吧，我就叫ssdt-no-EC.aml，记住后缀为aml。记得将ssdt-no-EC.aml放入EFI/OC/ACPI下，并在config.plist中添加加载此aml文件。

[SSDT-no-EC.dsl](https://blog.xjn819.com/wp-content/uploads/2019/10/SSDT-no-EC.dsl_.zip)

如果你的EC名字叫H\_EC或者别的什么的，你打开这个.dsl文件，改一下图中红线中的字即可。

![img](https://blog.xjn819.com/wp-content/uploads/2019/10/Screen-Shot-2019-10-27-at-9.40.29-PM.png)

对笔记本而言，我们不能禁用EC，因为禁用EC后会直接导致笔记本没有电池。那么我们怎么去重命名EC呢？按照上面提到的方法，找到你EC的真实名字，在章节2.1.3中我提供了假如你的笔记本的EC叫做EC0时候的重命名办法，那如果你的EC叫别的乱七八糟的名字呢？

我们先找到你的EC名字，比如你的EC叫做H\_EC，我们打开在线的[HEX转换器](https://tool.lu/hexstr/)，输入H\_EC，并点击下面的16进制转换，就可以看到转换出来的值是485F4543，把这个值替换到find这个选项卡中就行了。你也会注意到，EC的hex-16进制为45435F5F，刚好是Replace的值。这就是一个非常简单实用的OC重命名。但切记！OC万不得已不要用重命名！笔记本的EC是实在没有办法。

1.  Comment: H\_EC to EC
2.  Count:0
3.  Enabled:YES
4.  Find:[\<485F4543\>]{style="color: #ff0000;"}
5.  Limit:0 Mask:\<\>
6.  OemTable:\<\>
7.  Replace:\<45435F5F\>
8.  ReplaceMask:\<\>
9.  Skip:0
10. TableLength:0
11. TableSignature:\<\>

### 

### **3.7.2 USBX供电**

我们在使用过程中可能会遇到睡眠唤醒后，插着的U盘掉了，要重新拔插才能识别，这是因为我们还没对USB的供电进行修复。我们如何辨别USB供电正不正常，你可以比较下面两张图，显然第二张是正确的。

![img](https://blog.xjn819.com/wp-content/uploads/2019/10/2950238ACDFA2F16DFFB5C8B0C69FD4A.png)

![img](https://blog.xjn819.com/wp-content/uploads/2019/10/CB146700519BD381650D03AA1CC115F9.png)

从10.15开始，USB电源的控制被直接分配到了IOResources上面：

![img](https://blog.xjn819.com/wp-content/uploads/2019/10/Screen-Shot-2019-10-29-at-8.12.18-PM.png)

我们只需要一个简单的KEXT补丁来加载USB电源控制

[USBPower.kext](https://blog.xjn819.com/wp-content/uploads/2019/10/USBPower.kext_.zip)

请你确定你已经用hackintool定制了你的usb口，并使用了usbports.kext（或者你直接实用USBInjectAll也行）！而不是ssdt类的定制，ssdt类的端口定制并没有对win进行判断请不要用！如何定制自己的usbports.kext，请看黑果小兵的视频教程：https://www.bilibili.com/video/av38860673

下载这个KEXT补丁，你可能需要对补丁进行修改才能用。右键kext显示包内容，一直点进去，直到打开info.plist。我们展开IOKitPersonalities\_x86\_64，可以看到机型是iMac19,1，请把它改成你正在使用的机型，把补丁放入OC/kexts下，并在config.plist中加载这个补丁，重启即可。

![img](https://blog.xjn819.com/wp-content/uploads/2019/10/Screen-Shot-2019-10-29-at-8.31.23-PM.png)

**3.8 RTC相关问题**
-------------------

一些华硕主板的用户反馈给我说，他们的黑苹果在OC下总是重启后BIOS重置或者需要按F1跳过bios的安全模式，或者因RTC出现睡眠问题等等。其实关于这样的一些情况，主要是没有原生的APPLE
RTC，这个我已经在章节2.4.4中解释过了。但是还有一个问题，就是在之前的教程里我提供了一个rtc
fix的重命名补丁（见2.1.3章节）。对OC而言，重命名就是比较忌讳的，而且我也非常讨厌重命名，所以这个不能忍啊！

因此，我们现在需要通过对RTC进行修复，来抛弃那个RTC重命名补丁。

调整RTC可以分成两种情况，一种是你的ACPI表中具有AWAC部件，第二种情况是你的ACPI表中不具备AWAC。如何去确定你的ACPI中有AWAC，打开IO
Registry
Explorer，我们查找AppleACPIEventController栏目下有没有AWAC这个部件，下面截图中是有AWAC这种情况：

![img](https://blog.xjn819.com/wp-content/uploads/2019/10/Screen-Shot-2019-10-27-at-10.36.15-PM.png)

根据是否有AWAC，我们可以分两种情况来修复RTC，有AWAC的情况下修复RTC 以及
没有AWAC的情况下修复RTC。

### **3.8.1 存在AWAC的情况下修复RTC**

这里我们直接使用宪武大大提供的ssdt，放入acpi目录下并在config中载入即可。（这个包是宪武大大在群里面发的最新版，他的github还未更新此文件，目前是10月28日）。加载此补丁后，你再打开IO
Registry
Explorer，你会发现awac已经没有了，并且多出了一个rtc部件，表示此补丁生效，并且你也可以删除之前在config里面添加的rtc
fix补丁。

[SSDT-RTC\_Y-AWAC\_N.aml](https://blog.xjn819.com/wp-content/uploads/2019/10/SSDT-RTC_Y-AWAC_N.aml_.zip)

### **3.8.2 不存在AWAC的情况下修复RTC**

其实这种情况下，rtc一般是没有问题的，但是强迫症啊，白果的rtc叫做artc，那我们就禁用一下rtc然后再仿冒一个叫artc的部件吧。

加载此ssdt并在config中添加它，重启后打开IO Registry
Explorer，你会看到rtc部件已经没有了，多了一个artc，这个是白果的描述方式，凑个热闹吧。如果你在config中添加了rtc
fix补丁，也可以删掉了（似乎没有awac都不需要rtc fix补丁）。

[SSDT-ARTC.aml](https://blog.xjn819.com/wp-content/uploads/2019/10/SSDT-ARTC.aml_.zip)

**3.9 FCPX加速**
----------------

FCPX在黑果下主要有两个问题：1.核显无法拉到最满的1.2GHZ，独显尤其是vega芯片的显卡不满载工作，看戏。这里我们主要针对具有核显和独显的机器进行优化（只有核显或者只有独显的不用试了），让核显跑满速度，提升整个FCPX的效率。至于只有独显的机器，我暂时没有找到比较好的方案，这也是我为什么不推荐买带f的cpu，毕竟黑果没有t2芯片，我们需要核显来支撑一些东西。提示：z170,z270,z370因BIOS缺陷可能无法使用。

这本来是一个比较繁琐的教程，多亏了群友\@Bugprogrammer将whatevergreen简化了：[博主魔改版Whatevergreen解析，还你正常核显频率(1.2g)](https://www.bugprogrammer.me/2019/10/03/fix-igpu-with-weg.html)

这里我已经帮大家编译好了，把原版的whatevergreen替换了就行了。此[WhateverGreen.kext](https://blog.xjn819.com/wp-content/uploads/2019/10/WhateverGreen.kext_.zip)保留了AGDP黑屏补丁、开机紫条补丁以及改名补丁，非常精简。

现在看核显（GFX）整个工作效率都能维持在1.2GHZ上，（我这里对CPU做了优化，可能实际没我这么夸张）如图：

![img](https://blog.xjn819.com/wp-content/uploads/2019/10/Screen-Shot-2019-10-15-at-12.40.42-AM.png)

什么？效率还是不够高？大哥是开影视工作室的吗！？好吧，请看"CPU的变频优化"这章，记得CPU要有水冷哦！

**3.10 睡眠即醒的相关问题**
---------------------------

睡眠即醒很大程度上跟USB的定制相关，一般一个好的USB定制就能解决睡眠即醒的问题。当然系统的更新，MacOS的也在做不断的调整，比如蓝牙不能在HUB下进行内建，比如雷电卡必须将4个端口全部内建才行，等等。甚至有些时候我们都不知道为什么黑果会睡不着，那有没有一个办法让黑果强制睡眠呢？答案是有的。经过我的摸索，有几种方法能达到强制睡眠的效果，只是方法不同而已，但主要围绕的还是0d/6d的数值来做一些工作。那刚好，这些方法涉及了很多黑果领域的一些小技巧，我也顺便展示给大家。

注意：0d/6d补丁的本质是阻止一些部件参与唤醒工作，这其中包括了xhc部件，这意味着你无法使用鼠标键盘唤醒，只能用电源键唤醒。尽管还有别的办法让鼠标键盘唤醒（后面再提）

### **3.10.1 方法一：OC版本的0D/06补丁**

300系列的主板一般有5个部件是直接参与唤醒工作的，这五个部件分别是XHC（USB控制器）、CNVW（CNVI网卡，如果你的主板自带的话）、GLAN（有线网卡）、XDCI（USB相关）、HDEF（音频）。旧的一些主板可能会有不同的命名，比如XHC有叫EH01，HDEF叫做HDAS等，这里不做讨论。而这些设备往往会直接影响睡眠，比如你输入小兵哥哥经常说的这个命令：

    log show --last 1d | grep "Wake reason

我们有时候会看到如下结果：![img](https://blog.xjn819.com/wp-content/uploads/2019/10/7D60152C2653941D6DFE18100BC303D4.jpg)

那么即是这两个部件导致了睡眠出现了问题。于是，我们用几种方法去屏蔽或者说修改这些部件，来达到电脑正常睡眠的效果。

我们打开之前提取的SSDT，随便搜索五大部件中的一个，比如说XDCI：![img](https://blog.xjn819.com/wp-content/uploads/2019/10/%E6%88%AA%E5%B1%8F2019-11-07%E4%B8%8B%E5%8D%8811.06.02.png)

### 

我们主要是看上图中XDCI下的\_PRW属性值，可以直接看到Return的值为GPRW
(0x6D,
0x04)。其中6D这个数值看主板而定，有些主板叫做0D，而后面04这个值的含义为S4级别的电源管理，即休眠甚至关机情况下的唤醒；有些后面的数值是03，代表着S3级电源管理。这个我打一个大家比较熟悉的例子，GLAN这个部件的PRW值也是0x04，为什么要是04呢？因为这样我们可以使用远程通过网络启动主机功能。

那说了这么多，我们到底要做什么呢？我们要做的就是屏蔽掉他们，不让他们参与主机唤醒这个工作。这样可以彻底解决睡眠即醒的问题。

首先通过DSDT里确定你的返回值到底是0D还是6D，比如我这里返回的是6D，就记住自己是6D的。照旧打开宪武大大的OC-SSDT包，打开目录下的0D6D补丁包，看到两个plist的更名文件，我是6D的就直接实用6D更名补丁，打开我们看到两个patches，一个是把03（即S3级别电源管理）改名为00（即取消它的参与唤醒工作）。另一个是把04（S4级电源管理）改成00（取消它的参与唤醒工作）。

整个过程其实很简单，就是把宪武大大的两个补丁加到自己的CONFIG里去而已。这里主要运用的方法是HOTPATCH的重命名功能。

### **3.10.2 方法二：沿用Clover版本的0D/06补丁&展示TgtBridge在OC下的用法**

宪武大大做的clover版本的0d/6d补丁，其实没啥必要讲，只是有留言问了tgtbridge在oc下怎么用，那我就展示一下吧。这个补丁原理是一样的，通过重命名的方式改\_prw。

直接下载宪武大大的[clover
hotpatch补丁包](https://github.com/daliansky/P-little)，打开"11-1-睡了即醒(0D/6D)补丁"下的plist文件，按照clover的方式，其实把这些补丁直接拖到clover下就行了。那我们拿出一组数据来讲解怎么把它翻译成oc版本：

1.  Comment String XHC:\_PRW to XPRW
2.  Disabled Boolean True//此补丁并未生效，这里要改成false才会生效
3.  Find 5F505257 //hex转text的含义即是：\_PRW
4.  Replace 58505257 //hex转text的含义即是：XPRW
5.  TgtBridge 5848435F //hex转text的含义即是：XHC\_

这里我来解释一下，这组改名是对xhc下的PRW进行改名为xprw，这样的话，之前prw下的(0x6D,
0x04)即不生效了。而指定xhc的方法即是使用了tgtbridge，因为整张dsdt上有几十上百个\_PRW，你必须通过tgtbridge来指定到底是哪一个部件的\_PRW。

那么OC到底怎么使用tgtbridge来特定某一部件下的内容重命名呢？我们先把上面一段clover的补丁转换成oc的版本先吧：

1.  Comment String XHC:\_PRW to XPRW
2.  Count Number //需要重点解释\
3.  Enabled Boolean True //表示应用此补丁，不应用选False\
4.  Find Data 5F505257 //hex转text的含义即是：\_PRW
5.  Limit Number 0 //这个按默认即可 不去管他
6.  Mask Data \<\> //这个按默认即可 不去管他
7.  OemTableId Data \<\> //这个按默认即可 不去管他
8.  Replace Data 58505257 //hex转text的含义即是：XPRW
9.  ReplaceMask Data \<\> //这个按默认即可 不去管他
10. Skip Number //需要重点解释
11. TableLength Number 0 //这个按默认即可 不去管他
12. TableSignature Data 44534454
    //hex转text的含义即是：DSDT，这里按默认即可，代表对dsdt进行修改

这里就是一个还没全部翻译好的oc版改名xhc的prw。那么如何定位xhc下的\_prw呢，主要是填写`Count`和`Skip`。其实oc的tgtbridge是通过一个个数过去来定位具体哪一个位置的。比如xhc的prw是整张dsdt里面的第55个，那skip填54，意味着跳过前54个，从第55个开始执行。那执行多少次呢？执行一次count就填1；比如你要同时改第55个和56个，那count就填2。说了这么多，我来实操一下吧：

打开dsdt，在左下角直接搜索\_PRW，就能把整张表的\_PRW筛选出来了：

![img](https://blog.xjn819.com/wp-content/uploads/2019/10/%E6%88%AA%E5%B1%8F2019-11-08%E4%B8%8A%E5%8D%882.57.43.png)

我总共数了一下，一共有56个\_PRW。我们再在主内容栏上按command+f搜索xhc，直接找到xhc的\_PRW，刚好我们看到我的xhc实在整张表的倒数第4个，也就是正数第53个：

![img](https://blog.xjn819.com/wp-content/uploads/2019/10/%E6%88%AA%E5%B1%8F2019-11-08%E4%B8%8A%E5%8D%883.00.36.png)

### 

那么我们就可以补充完整张表了：

1.  Comment String XHC:\_PRW to XPRW
2.  Count Number 1
3.  Enabled Boolean True
4.  Find Data 5F505257
5.  Limit Number 0
6.  Mask Data \<\>
7.  OemTableId Data \<\>
8.  Replace Data 58505257
9.  ReplaceMask Data \<\>
10. Skip Number 52
11. TableLength Number 0
12. TableSignature Data 44534454

如果你想第53、54、55个都改掉，那count就写3，意味着顺序执行3次。好了，就这样，有问题留言。

### **3.10.3 方法三：配合SSDT+重命名的强制睡眠补丁 （重点推荐）**

我之前也提过，我是一个比较反对在oc下进行直接重命名的用户，如果真的要用重命名，也一定是搭配ssdt去做重命名，所以这个方法也是宪武大大和我最推荐的一种方法。

打开宪武大大的OC-SSDT包，找到0D/6D文件夹，打开SSDT-GPRW.dsl。我来解释一下里面的内容

1.  //
2.  // In config ACPI, GPRW to XPRW
3.  // Find: 47505257 02
4.  // Replace: 58505257 02
    //这里提示你要应用这个补丁，你必须在config中的ACPI-PATCH里面加入如上重命名内容\
5.  //
6.  DefinitionBlock (\"","SSDT", 2,"ACDT","GPRW\", 0)
7.  {
8.   External(XPRW, MethodObj)
    //寻找dsdt表中叫做XPRW的内容，这是要你在config中先把gprw改名成xprw才会生效，这就是为什么这个补丁的重命名必须是这个ssdt和重命名一起用的原因，你第一个重命名不生效，这个ssdt也不会生效。
9.   Method (GPRW, 2, NotSerialized)
10.  {
11.  If (\_OSI ("Darwin"))
    //为了不破坏dsdt完整性，这里做了系统判断，当你运行windows的时候，此ssdt不生效
12.  {
13.  If ((0x6D == Arg0)) //如果你的dsdt中是6D进行判断
14.  {
15.  Return (Package ()
16.  {
17.  0x6D,
18.  Zero
19.  })
20.  }
21. 22.  If ((0x0D == Arg0)) //如果你的dsdt中是0D进行判断
23.  {
24.  Return (Package ()
25.  {
26.  0x0D,
27.  Zero
28.  })
29.  }
30.  }
31.  Return (XPRW (Arg0, Arg1))
    //当运行mac系统时，如果你的dsdt中XPRW为6d，或者0d时返回为0，即屏蔽。
32.  }
33. }

这个ssdt不需要你改任何内容，打开后左上角另存为（save as),
其中文件格式(file format)必须选择ACPI Machine Language
Binary，文件名字就叫，记住后缀为aml。记得将ssdt-gprw.aml放入EFI/OC/ACPI下，并在config.plist中添加加载此aml文件：

![img](https://blog.xjn819.com/wp-content/uploads/2019/10/%E6%88%AA%E5%B1%8F2019-11-08%E4%B8%8B%E5%8D%883.21.46.png)

并且，我们需要在ACPI---Patch中增加一条配合此ssdt的重命名：

![img](https://blog.xjn819.com/wp-content/uploads/2019/10/%E6%88%AA%E5%B1%8F2019-11-08%E4%B8%8B%E5%8D%883.23.40.png)

### **3.10.4 方法四：从白果DSDT中学习到的睡眠补丁**

最近群友在看白果的dsdt中发现白果的5大部件\_PRW值都是(0x69,0x03)。那么何不试试把这5大部件的s4级电源管理都改成s3级呢？实践证明在某一些机器上把04改成03是有效的，方法如下：

![img](https://blog.xjn819.com/wp-content/uploads/2019/10/%E6%88%AA%E5%B1%8F2019-11-08%E4%B8%8B%E5%8D%885.28.59.png)

### **3.10.5 10.15.1中发现的无法自动睡眠问题**

最近发现10.15.1必须开启小憩才能自动进入睡眠。但开启小憩意味着电脑会隔1个小时左右时间醒一次，来收发邮件等工作，再继续睡。如果你不喜欢这样的话，试试加载[SSDT-SBUS.aml](https://blog.xjn819.com/wp-content/uploads/2019/10/SSDT-SBUS.aml_.zip)。至于原理是啥，我也不懂。

**3.11 中高端类消费级CPU的变频优化**
------------------------------------

需要CFG解锁
