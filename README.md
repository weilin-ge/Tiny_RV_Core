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
| 日          | 一          | 二          | 三          | 四          | 五          | 六          |
|:-----------:|:-----------:|:-----------:|:-----------:|:-----------:|:-----------:|:-----------:|
| 1           | [2](#112)   | [3](#113)   | [4](#114)   | [5](#115)   | [6](#116)   | [7](#117)   |
| [8](#118)   | [9](#119)   | [10](#1110) | [11](#1111) | [12](#1112) | [13](#1113) | [14](#1114) |
| [15](#1115) | [16](#1116) | [17](#1117) | [18](#1118) | [19](#1119) | [20](#1120) | [21](#1121) |
| [22](#1122) | [23](#1123) | [24](#1124) | 25          | 26          | 27          | 28          |
| 29          | 30          |

# Log

## 11.24
- 总线模块设计
>
> 学业以及其他原因，花在这里的时间明显减少了
>
> 要做调整以及规划
>

## 11.23
- 学习AHB总线协议
- 总线仲裁设计（未果）

## 11.22
- 学习总线（AHB、AXI）最终决定使用AHB总线（多主多从）

## 11.21
##### 代码实战
- 添加R型指令的译码部分，依据设计其他模块不需要修改也能工作
- 添加B型指令的译码部分
- 通过git管理代码


## 11.20
##### 代码实战
- 想修改regfile的结构，不知道为什么vvp仿真一直出不了结果，最终改回了原来的方案。
- 修改了ALU Adder的位宽，调整了输入加法器的输入信号
- 调整了slt、sltu操作的检测位


## 11.19
##### 代码实战
- 修改Decode模块（RISC-V 指令版本修改前后不一致）
- Debug ALU模块
##### 工具整合
- 编译risc-v工具链
- 编辑链接文件
- 添加Makefile文件
- 编写转换测试文件的小工具

## 11.18
##### 代码实战
- 编写alu算数模块的功能(slt, sltu, xor, or, and, sll, srl, sra)

## 11.17
##### 代码实战
- 完成其他I型指令的译码器
- 添加了alu的算数解码功能(具体功能未实现)
- 完成了线路连线

## 11.16
##### 实践
- I型指令jalr的结构设计
##### 代码实战
- jalr指令的实现
- 预备其他I型指令


## 11.15
##### 实践
- 修改ROM的实现方式，可以立即获取ROM的值
- 编写软核PLL，实现1Hz的时钟（可配置）。减缓时钟，方便查看效果
- 使其他的复位与核心的复位分离，单独查看核心复位情况
- 时钟连续/手动可调
##### 方向调整
- 预备跳转指令的架构设计
- 研究跳转分支的实践
- Load-Store延后设计
- 计划攻下总写接口（这个部分比较重要，处理器内核主要从这部分获取数据）


## 11.14
##### 代码实战
- 完成wbu模块
- 整理修改代码结构以及命名
- 联合调试，仿真无误

##### 硬件测试
- 编写测试顶层文件
- 调和联通各个部分
- 学会使用IP核
- 学会调试探针
- 完成硬件测试，并验证通过

## 11.13
#### 代码实战
- 编写ALU加法器部分，没有解决数据相关问题。由于设计的原因，数据相关问题需要慎重考虑。(草率了)


## 11.12
##### 结构设计
- 设计ALU加法器的架构


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

