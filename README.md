# 简述
- 手写处理器内核
    - 架构：risc-v
    - 模块
        - rv32i
        - timer
        - rtc
        - interrupt
        - mmu
        - mpu
        - M mode
        - U mode
        - S mode
    - 目标
        - 能够运行I型基础指令
        - 超标量处理器：2发射结构
        - 实现mmu
        - 实现mpu
        - 能够运行操作系统

# Date 
### 11月
| 日        | 一        | 二          | 三          | 四        | 五        | 六        |
|:---------:|:---------:|:-----------:|:-----------:|:---------:|:---------:|:---------:|
| 1         | [2](#112) | [3](#113)   | [4](#114)   | [5](#115) | [6](#116) | [7](#117) |
| [8](#118) | [9](#119) | [10](#1110) | [11](#1111) | 12        | 13        | 14        |
| 15        | 16        | 17          | 18          | 19        | 20        | 21        |
| 22        | 23        | 24          | 25          | 26        | 27        | 28        |
| 29        | 30        |

# Log

## 11.11
##### 代码实战
- 完成整体框架的设计
- 编写部分代码用于调试
- 完成寄存器文件的编写
- 完成能够应用与测试的取址模块
- 完成用于测试使用的代码rom模块以及相应文件

## 11.10
##### 解析e203源代码
- 解析总线的数据通路，试图找到非字节对齐的数据如何处理，但未得到结果。
- 总线的数据通路较为复杂，涉及到好几个模块的数据通信，解析起来有困难。




## 11.9
##### 解析e203源代码
- 通用任意位宽写、读ram的实现。
- itcm的写端口关闭，不知道为什么，处理器在初始化时数据不知道如何加载到ITCM当中
- 查看了几个博文，了解了ITCM的本质、FIFO、bypass buffer
- dtcm的存储数据通路（只是数据4字节对齐的数据），非对齐的字节对齐未研究。


## 11.8
师弟来访，放假一天。


## 11.7
##### 解析e203源代码
- 取指的数据通路(ICB\BIU)
##### 研究实战
- 实现一个纯逻辑实现的addi译码器。
##### 心得 
首次将研究得来的知识付诸实践，期间虽然有一些错误，但还是完成了一个译码器。


## 11.6
##### 解析e203源代码
- ifu模块的分析
valid-ready握手信号设计(疑惑)
##### e203总线
- 了解icb总线
##### 心得
目前还没有查看verilog代码的方法与技巧，难以掌握各个模块之间的调用、连接、数据通路的情况。基本拿到源代码就无从下手，有些迷茫。这个也是在学习e203的设计结构构成了一定的困难。

## 11.5
##### 解析e203源代码
- add指令跟踪数据同路失败(19:53)
- 找到并且记录add指令的数据通路。(20:35)
- 解惑(查找了一遍数据同路没发现always块)：使用了sirv_gnrl_dff*触发器代替always语句块。有数据存储与防止数据贯通的作用。
##### 电脑状况分析
由于突然更新导致固件与新版本windows不兼容，导致处理器降频。目前刷回旧版固件，能够正常使用。


## 11.4
##### 突发状况
今天电脑突然降频，未知道什么原因造成，今天把系统恢复一下希望能够解决问题。
如果系统重置了也不行的话，那就刷一个bois试试了。
再不行就只能求助于售后服务了。
##### 想法
今天我反思了一下，制作处理器内核，我最大的问题是期间很多的内容都是空白的，并没有一个直接可用的例子供我使用。
当然，手里还有e203的源代码可以研究，目前主要是研究源代码来先提升一下自己。
不过，在以后要处理内存管理单元的时候，可能难以有资源学习了。可能到时候不一样呢，一切皆有可能，以后会更好。



## 11.3
##### 完成
- 确定使用五级流水线
- 初步规划R型指令的数据通路
- 初步规划R型指令的模块接口设计
##### 下一步完成内容
- 模块设计加入数据相关处理


## 11.2
- 确定架构，项目启动，收集资料。
- 下载rv官方规范文档
- 下载rv官方特权模式规范文档

