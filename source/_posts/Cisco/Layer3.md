---
title: Cisco 实验报告 | 网络层实验
date: 2024-11-07
mathjax: true
comments: false
categories: 计算机网络
tags:
    - 计算机网络
    - Cisco
---

## 任务要求

搭建小型企业网络，要求部门内部正常通信，部门与部门之间相互独立。
要求在财务部搭建静态VLAN，行政部直连三层交换机并开启路由功能，技术部与市场部通过路由器组网。

- 掌握网络设备IP地址、子网掩码、默认网关配置
- 掌握静态VLAN配置
- 掌握三层交换机VLAN与路由功能配置
- 掌握路由器跨网段转发配置

![任务要求](https://images.rescld.cn/20241106221834.png)

## 前置知识

### IP地址分类

IP地址由4字节组成一共32位，我们通常使用 <font color="red">点分十进制</font> 记法，每个字节之间使用点隔开。

IP地址又分为两个部分，即 <font color="red">网络地址</font> 与 <font color="red">主机地址</font>，划分五类IP地址

![IP分类](https://images.rescld.cn/20241106224728.png)

### 子网掩码

子网掩码由32位组成，用来屏蔽IP地址的一部分以区分网络号与主机号。
网络号部分使用1表示，主机号部分使用0表示。

任何一个IP地址与其子网掩码进行 <font color="red">与运算</font> 得到的结果就是其所属的 <font color="red">网络地址</font> 。

![计算网络地址](https://images.rescld.cn/20241106230040.png)

通过子网掩码还可以利用主机号的部分进行三级IP划分

![三级IP](https://images.rescld.cn/20241106231211.png)

> CIDR 通过在IP地址后面加上 `/n` 的方式指定子网掩码前缀1的位数。
> CIDR 消除了前面固定的IP分类方式，可以更加自由的划分IP段

## 配置IP地址

题目要求四个部门都在 `192.168.1.0/28` 的网络下分配IP地址，该网络由28位网络号与4位主机号组成。

![二进制表示](https://images.rescld.cn/20241106233852.png)

该企业有4个部门，需要2个二进制位给四个部门分配不同的网段

![划分不同子网](https://images.rescld.cn/20241108210948.png)

本文将网段内的第一个可用IP地址当作网关地址使用

![配置IP地址](https://images.rescld.cn/20241106235143.png)

## 配置VLAN

部门内部主机使用 <font color="red">直连线</font> 连接交换机，交换机使用 <font color="red">交叉线</font> 连接三层交换机。

![财务部接线](https://images.rescld.cn/20241107000229.png)

### 交换机1

这里要求给财务部配置 VLAN，直接打开交换机1 CLI 进入配置模式

```cisco
S1> enable
S1# configure terminal
S1(config)#
```

先给交换机1创建一个 VLAN 并设置 VLAN 名称

```cisco
S1(config)# vlan 10
S1(config-vlan)# name vlan10
S1(config-vlan)# exit
```

财务部两台设备分别到了交换机1的 `Fa0/1-2` 两个端口，需要将这两个端口加入到 VLAN 当中

```cisco
S1(config)# interface range FastEthernet 0/1-2
S1(config-if)# switchport mode access
S1(config-if)# switchport access vlan 10
S1(config-if)# exit
```

###  三层交换机

交换机1配置好之后，也需要给三层交换机创建<font color="red">相同</font>的 VLAN，并设置VLAN名称

```cisco
MS(config)# vlan 10
MS(config-vlan)# name vlan10
MS(config-vlan)# exit
```

然后进入这个创建的 VLAN 接口将 IP 地址配置为该网络的网关地址

```cisco
MS(config)# interface vlan 10
MS(config-if)# ip address 192.168.1.1 255.255.255.240
MS(config-if)# no shutdown
MS(config-if)# exit
```

最后，需要共享交换机1与三层交换机之间的端口，选择连接交换机1的 `Fa0/1` 接口启动 Trunk 模式

```cisco
MS(config)# interface FastEthernet 0/1
MS(config-if)# switchport trunk encapsulation dotlq
MS(config-if)# switchport mode trunk
MS(config-if)# exit
```

## 三层交换机路由

这里跟上面几乎一模一样
<font color="red">注意：</font>这里是直连三层交换机，不需要配置 VLAN

![设备直连三层交换机](https://images.rescld.cn/20241107010641.png)

由于这边不需要配置 VLAN，所以完全不需要配置交换机，只需要给三层交换机开启路由模式并配置一个IP地址即可

```cisco
MS(config)# ip routing
```

选择连接下面网络的接口 `F0/2` ，三层交换机接口默认都是 `switch` 模式，将其关闭并配置IP地址为该网络的网关地址

```cisco
MS(config)# interface FastEthernet 0/2
MS(config-if)# no switchport
MS(config-if)# ip address 192.168.1.17 255.255.255.240
MS(config-if)# no shutdown
MS(config-if)# exit
```

## 路由器

路由器的配置更简单，只需要配置一个网关IP并开启动态路由即可

![路由器接线](https://images.rescld.cn/20241107013118.png)

Cisco 默认的路由器都只有两个接口，这里路由器需要连接三个设备，所以要拓展一个网口

![拓展网口](https://images.rescld.cn/20241107012819.png)

路由器重启之后，进入 CLI 标签会提示做一些初始配置，直接输入 `no` 

![初始配置](https://images.rescld.cn/20241107013655.png)

这个路由器连接了三个网口，需要为这三个网口分别配置IP地址
`Fa0/0` 连接着 `192.168.1.32/28` 的网络，就需要为其配置一个该网络内的IP地址作为网关

```cisco
S1(config)# interface FastEthernet 0/0
S1(config-if)# ip address 192.168.1.33 255.255.255.240
S1(config-if)# no shutdown
S1(config-if)# exit
```

路由器连接三层交换机这边题目规定了网段为 `192.168.1.248/30`

![路由器与三层交换机](https://images.rescld.cn/20241107015141.png)

由于子网掩码前缀30位，所以主机号只有两位

![路由网段](https://images.rescld.cn/20241107015012.png)

两位主机号，去除全0与全1的情况，实际可用的IP地址只有 `01` 或 `10`，正好分别配置给三层交换机与路由器

```cisco
S1(config)# interface FastEthernet 0/1
S1(config-if)# ip address 192.168.1.249 255.255.255.252
S1(config-if)# no shutdown
S1(config-if)# exit
```

最后的最后，给路由器和三层交换机开启动态路由即可
路由器1连接了三个网络，所以需要宣告3个网络地址，同理三层交换机也一样

<font color="red">特别注意：</font>宣告网络，宣告的一定是一整个网络地址，而不是某个特定的主机地址！！！！！！

```cisco
S1(config)# router rip
S1(config-router)# version 2
S1(config-router)# no auto-summary
S1(config-router)# network 192.168.1.32
S1(config-router)# network 192.168.1.248
S1(config-router)# network 192.168.1.252
S1(config-router)# end
```

## 温馨提示

当你忘记该使用哪个命令，或忘记某个命令的用法时，请大胆的打出 `?`，Cisco会自动提示所有可能的情况，并附带简单的说明

![帮助文档](https://images.rescld.cn/20241107020937.png)