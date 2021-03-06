---
layout: post
title: "如何根据自身情况选购硬盘"
tagline: ""
description: ""
category: 经验总结
tags: [hard-drive, computer, ssd, hdd, guide, data-storage,]
last_updated:
---

因为加入了一些 PT 的关系，本地的硬盘空间立即捉襟见肘，毕竟有些蓝光原盘动不动就 40+GB，所以陆陆续续给威联通也加了一些硬盘，之前一直买的是酷狼的 4T 盘，但是用了一年快两年的样子[竟然挂了](/post/2019/07/qnap-moving-system-volume.html)，这是我最初买的那一块所以也[折腾了一下](/post/2019/07/qnap-moving-system-volume.html)，因为系统和一些配置都在这一块盘上。所以强烈建议重要资料一定多处备份，不仅需要通过本地冗余备份，最好也多地备份，比如本地和其他云端备份服务实时同步。

再回到这次的主题，关于如何选购一块硬盘。打开京东能看到主流的硬盘厂商提供了种类丰富的各种用途的磁盘。但对于消费者而言，很多人其实并不知道其中的具体技术细节。很多人可能知道酷狼是 NAS 盘，酷鱼是普通家用盘，但谁也没有具体分析过这二者的区别，商家宣传也不会刻意宣传技术细节。

## 硬盘技术

硬盘的技术最早在 1956 年被 IBM 发明，之后便迅速成为了 60 年代通用计算机的组成部分 [^origin]。 历史上最多的时候有超过 200 家硬盘制造厂商 [^company]，经过兼容合并后目前市场上比较著名的就只有 Seagate， Toshiba 和 Western Digital 了。再之后的故事大家都知道了，随着 SSD(Solid-state Drive) 的兴起，尤其是 NAND 技术的发展，HDD 逐渐式微，但不可否认的是 HDD 目前依然保留着自己在计算机领域的地位。

目前市场是两个主要的硬盘大小就是 3.5 寸，主要给台式机用，和 2.5 寸主要给笔记本用。HDD 通过 PATA(Parallel ATA), SATA(Serial ATA, 600MB/s), USB 和 SAS(Serial Attached SCSI, 12Gb/s) 接口和其他硬件系统连接。

### 主要构造
我们知道计算机的世界其实是一个二进制的世界，底层都是 0 和 1 的无尽组合，对于数据来说也是，那么作为二进制数据的存储设备硬盘而言，就是要记录下 0 和 1 的组合。在网上可以看到很多的硬盘拆解的图片，能看到一个大大的一个像 CD 一样的盘片，在盘片上会有很多磁性物质，通过盘片的快速旋转和磁头的移动来读写数据。但实际上可能要更加复杂一些。

硬盘的主要构造：

![main components of hdd](/assets/Hard_drive-en.svg)

说明：

- Platter: 磁盘盘片，真正用来存储数据的地方，磁盘由非磁性材料制成，通常为铝合金、玻璃或陶瓷。它们被涂上一层浅浅的磁性材料，深度通常为 10-20 纳米，外层有一层碳保护层。盘片在硬盘正常工作时以非常高的速度旋转。
- HEAD: 磁头，盘片高速旋转时用来读取或者写入数据，磁头和盘片之间有一个纳米级别的空隙，所有的磁头连接在一个控制器上，控制器负责磁头的运动，磁头可以沿着盘片的半径方向（斜切向）运动。每一个磁头同一时刻必须是同轴的（也就是从上问下看磁头任何时候都是重叠的，一起移动）
- Spindle: 主轴
- Actuator: 读写臂，操作硬盘磁头在介质表面进行数据读写的组件，每一个记录磁头位于移动读写臂的尾端
- Actuator Arm: 磁头臂
- Actuator Axis: 磁头轴

![hard drive magnetic head](/assets/hard-drive-magnetic-head.svg)

上面也提到盘片是真正用来存储数据的地方，那么盘片是如何做到的呢？盘面和磁带的原理比较相似，在磁盘的表面有一层磁性材料，而磁头通常是线圈缠绕在磁芯上

- 在写入数据时，磁头线圈通电，周围产生磁场，电流的方向改变会引发磁场的变化，磁场会磁化磁盘表面的磁性物质。切换不同的磁场方向，磁性颗粒的方向也会不同。那么其方向的不同就可以来代表二进制世界的 0 和 1。
- 写数据时同理，磁头线圈切割磁感线产生了感应电流，磁性材料的磁场方向不同，电流方向也不同，磁头通过感应旋转的盘片上磁场的变化来读取数据

虽然原理很简单，但是盘片，磁头，以及机械内部的制作都是需要非常精密的工艺和材料的。

### 盘片

具体再看纵向每一个盘片之间。

![magnetic hard disk mechanism](/assets/magnetic-hard-disk-mechanism.jpg)

图片源自 [Cameron Hart](https://slideplayer.com/slide/6358804/)

说明：

所有的盘片都固定在主轴上，所有盘片之间都是平行的，每一个盘片的存储面都有一个磁头，现在主流的硬盘盘面都会有上下两面。

- Arm assembly 组合臂，控制磁头的机械结构
- track 磁道，盘片上的同心圆叫做磁道，磁道从外向里进行编号，从 0 开始，大容量的磁盘可能有更多的磁道。 磁头靠近主轴的最内圈，线速度最小，不存放任何数据，称为 Landing Zone。离主轴最远的就是 0 磁道，数据从最外圈开始存储。
- sector 扇区，每一段圆弧叫做扇区
- cylinder: 柱面，所有盘面上同一磁道构成的一个圆柱称为柱面，每个圆柱上的磁头从上到下，从 0 开始编号。数据的读写在柱面进行，磁头读写数据首先在同一柱面 0 磁头开始，依次向下在同一柱面不同的盘面的磁头上操作，同一柱面所有的磁头全部读写完后磁头才转移到下一个柱面。


操作系统以扇区的形式将信息存储在硬盘上，每个扇区包括 512 字节的数据和一些其他信息。每一个扇区有两个部分数据：

- 存储数据的地点标识符
- 存储数据的数据段，包括数据和数据校验 ECC 纠错码

扇区头标，包括：

1. 盘面号（或者又叫做柱面号），在第几个盘面的位置；
2. 柱面号（又被称为磁头号），用来确定磁头径向，在盘面中的位置；
3. 扇区号，在磁道上的位置

这三个部分可以唯一确定一块数据的具体地址。

### 盘面区域
盘片盘面区域

![hard drive sectors](/assets/hard-drive-sectors.jpg)

- Disk Sector 扇面
- Cluster 簇，物理相邻的几个扇区称为一个簇，操作系统读写磁盘的基本单位是扇区，但文件系统的基本单位是簇。簇的大小一般 4K, 8K ,16K,32K, 64K 等，簇越大存储性能越好，但空间浪费严重；簇越小性能相对越低，空间利用率高。


## 硬盘读写数据过程
在了解了硬盘的物理结构后，再来看真实过程中硬盘如何读写数据。

当系统需要从磁盘读取数据时，系统将数据逻辑地址传给磁盘，磁盘的控制电路按照寻址逻辑将地址翻译成物理地址，确定要读取的数据在哪一个盘面，哪一个磁道，哪一扇区。为了读写这个扇区的数据需要做以下步骤：

- 磁头沿着半径移动到要读取的扇区所在磁道上方，这段时间称为寻道时间 (Seek time)，一般为 2~30ms，平均为 9ms 左右
- 磁头到达磁道后，通过盘片旋转使得要读取的扇区旋转到磁头下方，这段时间叫旋转延迟时间 (Rotational latencytime)
- 定位具体可读写的扇区后，如果是读数据，控制器计算此数据 ECC 码，然后将 ECC 码和磁盘记录的 ECC 码比较；如果是写数据，控制器计算此数据的 ECC 码与数据一起存储。

一个 7200 转 / 每分钟的硬盘，旋转一周所需时间 60*1000/7200 = 8.33ms，平均旋转延迟时间，假设为半圈也就是 4.17ms。平均寻道时间和平均旋转时间称为平均存取时间。

	磁盘单次 IO 时间 = 寻道时间 + 旋转时间 + 存取时间

总结上面磁盘的读写可以知道数据的读写是按照从上到下，在盘面上从外向内进行。

### 局部性原理
因为硬盘的这种机械构造，所以磁盘本身的存取速度要比内存慢很多，再加上机械运动更加耗时。

#### 预先读
所以为了提高硬盘的效率，减少磁盘 IO，磁盘往往不是严格的按需读取，而是每次都预先读取，即使只需要一个字节，磁盘也会从这个位置开始，顺序读取后面一定长度的数据放入内存。这样做的依据是计算机科学中著名的局部性原理，当一个数据被用到时，其附近的其他数据通常也会马上被用到。

页 (Page) 是许多计算机存储管理器的逻辑块，硬件和操作系统往往将主存和磁盘存储区域分割为连续的大小相等的块，每一个存储块称为一页（通常为 4k)，主存和磁盘以页为单位交换数据。当程序要读取的数据不在主存中，会产生一个缺页异常，系统会向磁盘发出读盘信号，磁盘会找到数据的起始位置并向后连续读取一页或几页载入内存中，然后异常返回，程序继续运行。

#### 延迟写

一般硬盘上都会带一个比较小的磁盘缓冲存储器，将要写的数据缓冲，进而减少磁头移动，再一次性写入。


## 保护磁盘的方法

### 减小震动
硬盘内部因为是机械结构，在磁头和盘片之间有一个很小的空隙，如果硬盘有震动或者抖动，那么就可能造成磁盘数据损毁，所以在硬盘通电后就尽量不要移动硬盘，并且要尽量减缓硬盘转动可能带来的共振。

### 防尘
机械硬盘的内部构造必须保证觉得无尘，一旦有小的灰尘进入硬盘密封层，和磁头与盘片发生碰撞就可能造成机械设备的损坏。

### 使用 UPS 不间断电源
另外也不要对正在运行的磁盘突然断电，用正常的方式关闭系统，等待系统将缓存数据写回磁盘，然后再断电。所以如果家里有 NAS，建议还是购入 UPS，以免家中停电或者跳闸时可能对数据造成损害。

## 存储与分区
介绍了硬盘物理的构成，现在回到操作系统软件层面，相信装过机的人一定知道分区，在安装系统的时候要给系统划分一个系统分区。那么硬件启动的时候引导然后在硬盘上对应的地方启动系统。那么这里就需要知道整个磁盘的第一个扇区。

每一块物理硬盘的第一个扇区记录了整块磁盘的重要信息，包括：

- 主引导分区 (MBR, Master Boot Record)，安装引导程序的地方，446bytes。系统开机时会去读取这个分区
- 分区表 (Partition Table)，记录整块硬盘分区，64bytes

以前在使用 Windows 的时候有一个不小的疑惑，一块硬盘只能够划分四个分区（主分区 + 扩展分区），原因就在这里，分区表只有 64 bytes 大小，最多只能容纳四个分区。但实际上 Windows 可以通过逻辑分区来划分更多的分区。

## PMR vs SMR
再上面说了那么多原理之后，假如硬盘厂商要提高硬盘的容量会怎么做呢？数据是存放在盘片上的，而具体数据是存在扇区上的。所以很自然的会想到：

- 增加盘片数量
- 增加磁盘面积
- 增加磁盘盘片上存储数据的密度

前两者会增加硬盘的体积和重量，而现在的硬盘标准是固定的，随意改变硬盘大小必然会引起问题。所以目前大部分的解决方案就是提高单个磁盘数据存储的密度。于是这个公司的硬件工程师就提出了各种各样的办法。

### LMR
最早期磁性颗粒平铺在盘片上，磁感应的方向是水平的，这类技术被称为 LMR(Longitudinal magnetic recording, 水平磁性记录）。这种方式有一个缺点，盘片利用率不高，当磁力颗粒很小，相互靠近时，容易受到干扰，方向发生混乱。所以 LMR 时代，单盘存储的数据有限。

### PMR
为了解决 LMR 容量的限制，工程师们又想出了让磁性颗粒和磁感应方向相对盘片垂直。这个就叫做 PMR(Perpendicular Magnetic Recordking, 垂直磁性记录）。

在 PMR 技术下，3.5 寸盘，单碟磁盘的容量可以达到 1TB 左右。

### SMR
不过随着互联网发展人们要存储的东西越来越多，PMR 逐渐不够用了，所以硬件工程师又想出了 SMR(Shingled Magneting Recordking，叠瓦式磁记录技术）。

SMR 利用了磁道与磁道之间的距离，通常硬盘的磁道与磁道之间存在一个保护距离，保护不同磁道直接的磁性颗粒不造成干扰。另外一个现实情况便是，硬盘信息的读取和写入是两个不同的操作，读取磁头和写入磁头也是不一样的。现代硬盘读写的磁头不同，写入磁头是传统的磁感应磁头，比较宽，读取磁头是新型的 MR 磁头，比较窄，磁道在划分的时候，需要满足最宽的标准。但是写入磁头在工作的时候，实际上对于每一个磁道，写入的信息宽度和读取的宽度是一样的，那么，磁道的空间就造成了浪费。于是工程师想到，把这部分浪费的磁道重叠起来，和房屋的瓦片一样，写入的时候沿着每条磁道上方写入，中间留下一小段保护距离，然后接着写另一条磁道。

使用 SMR 技术的硬盘又被网友称为叠瓦盘。

![smr hdd](/assets/smr-hdd.jpg)

在 SMR 技术的帮助下，磁盘存储的容量大大增加了，但是缺点也很明显。首先是磁盘信息密度高，转速不能太快。另外 SMR 硬盘，单纯读问题不大，但是如果要修改某个磁道上的数据就比较麻烦，磁道间隙小，磁头比较宽，修改相邻磁道数据必然会相互影响。

解决这个问题的方法就是，每重叠一部分磁道时，隔开一些，另外就是设置专用缓冲区，当修改磁道 2 数据时，把磁道 3 的数据先取出来放到缓冲区，等磁道 2 数据改完再将磁道 3 数据写回。

也正是因为这个原因，一般的 SMR 硬盘具有**大缓存**的特点，一般可以达到 256MB，而普通的硬盘 64MB 足够。因为这样特殊的设计，在修改大量数据时会比较慢，时间久了会对硬盘读写性能造成影响。

### 总结
相较于 PMR 硬盘，SMR 硬盘不适合用来当作系统盘或者需要频繁读写的硬盘来使用

- 更适合当作仓储盘，用来备份数据
- 冷数据存储盘

## NAS 盘与普通盘的区别
NAS 盘和普通盘的本质区别在于 Time Limited Error Recovery，TLER 技术（希捷叫 ERC，ErrorRecovery Control）[^tech]。

一块硬盘长时间运行过程中，可能会因为各种情况出现读写错误，并且运行时间越长，出现的可能性越大，但是出现错误后，硬盘不会因此而损坏，硬盘内部的控制器会尝试进行修复，转移，纠错等操作，这一过程根据修复的难度，会用时几秒到几百秒左右，在这期间，硬盘会处于一个停止响应的状态。

在 [RAID](/post/2018/04/raid.html) 中，一旦发现一块硬盘在一定时间内无响应，就会认为硬盘损坏，剔除该硬盘。如果硬盘硬因为一个可恢复的读写错误进入无响应状态，而刚好这个硬盘处于一个 RAID 阵列，无响应时间一旦超过 8 秒的阈值，RAID 控制器自然会认为硬盘损坏，并开始一系列恢复操作。这时 TLER 就派上了用场，有 TLER 功能的硬盘将执行正常的错误恢复，但 7 秒后，会向 RAID 控制器发出错误消息，并将错误恢复任务推迟到稍后的时间。通过协调错误处理，硬盘驱动器不会从 RAID 阵列中删除，从而避免了整个 RAID 恢复、替换、重建和返回操作。也就是说有 TLER 功能的硬盘，在硬盘恢复期间，会每隔 7 秒向 raid 控制器报告一次"正常"从而阻止阵列的重建。

有 TLER 功能的 NAS 盘更加适合在 RAID 阵列中工作，TLER 不会减少读写时可能造成的错误，也不会加快错误恢复速度，但可以在纠错中保护未响应的硬盘不被 RAID 控制器因为超时而误判为硬盘损坏。

NAS 盘只有在 RAID 阵列中才能体现其价值。



## 总结
在看了硬盘的工作原理，再回到如何选购一块硬盘的主题上。相信到这里，再去看硬盘的配置信息，比如转速 5400 RPM，7200 RPM，缓存 64MB, 256MB ，使用的 PMR， 还是 SMR 技术，就比较清楚了，然后再根据自身的情况酌情选购即可。

## reference

- 《Visual Inspection Technology in the Hard Disk Drive Industry》Paisarn Muneesawang && Suchart Yammen
- <https://zhuanlan.zhihu.com/p/27926239>
- <https://blog.csdn.net/hguisu/article/details/7408047>
- <http://products.wdc.com/library/other/2579-001098.pdf>
- <https://www.ithome.com/0/436/608.htm>

[^origin]: <https://en.wikipedia.org/wiki/Hard_disk_drive>

[^company]: <https://en.wikipedia.org/wiki/List_of_defunct_hard_disk_manufacturers>
[^tech]: <http://products.wdc.com/library/other/2579-001098.pdf>
