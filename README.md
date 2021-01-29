# proj61-linux-address-range-memory-mirroring

### 项目描述

高端的 X86 和 ARM 服务器芯片支持局部内存镜像技术（Address Range Memory Mirroring），允许配置部分内存做成镜像，这部分内存区域对OS来说，可靠性更强。如果让关键数据或程序使用这部分内存，则可以提升系统的整体可靠性。比如：

* 让内核跑在镜像内存区域，防止因内存硬件出现多 bit 错误导致的系统 crash

但是当前内核实现的方案中，如果内核用光了已分配的镜像内存，则不能再分配新内存，会因内存不足产生OOM（out-of-memory）。很多使用者很难判断自己需要设置多少镜像内存，这限制了该特性的使用场景。本题希望解决这个问题，使系统可以：

* 内核可以在镜像内存用光的情况下，使用非镜像内存。

### 所属赛道

2021全国大学生操作系统比赛的“内核实现”赛道

### 参赛要求

- 以小组为单位参赛，最多三人一个小组，且小组成员是来自同一所高校的本科生（2021年春季学期或之后本科毕业的大一~大四的学生）
- 如学生参加了多个项目，参赛学生选择一个自己参加的项目参与评奖
- 请遵循“2021全国大学生操作系统比赛”的章程和技术方案要求



### 项目导师

谢秀奇、荆向峰

* gitee [Xie XiuQi](https://gitee.com/xiexiuqi)，jingxiangfeng

* email xiexiuqi@huawei.com, jingxiangfeng@huawei.com



### 难度

困难



### 特征

- 优化镜像内存的分配和使用方式，内核用完镜像内存时，可以使用普通内存

- 系统性能不出现明显的下降

  

### 文档

[[v4,0/2] mm: Introduce kernelcore=mirror option](https://lore.kernel.org/patchwork/cover/633555/)

[RE: [PATCH v3 2/2] mm: Introduce kernelcore=mirror option](https://lkml.org/lkml/2015/12/17/530)

[Address Range Memory Mirroring](https://www.fujitsu.com/jp/documents/products/software/os/linux/catalog/LinuxConJapan2016-Izumi.pdf)

[Demonstrating the Memory RAS Features of Lenovo ThinkSystem Servers](https://lenovopress.com/lp0778.pdf)

### License

- GPLv2 (https://www.gnu.org/licenses/old-licenses/gpl-2.0.en.html)



## 预期目标

### 注意：下面的内容是建议内容，不要求必须全部完成。选择本项目的同学也可与导师联系，提出自己的新想法，如导师认可，可加入预期目标



### 基于 Linux kernel 4.19 或 5.10 或社区主线版本实现

* 完成相关内核代码，可以编译安装运行
* 模拟测试，镜像内存不足时，内核可以使用非镜像内存
* 补丁推送到社区主线（可选）