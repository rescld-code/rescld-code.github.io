---
title: 高等数学前置知识
date: 2023-01-10
comments: false
categories: 高等数学
tags:
  - 高等数学
  - 初等数学
  - 三角函数
---

## 函数基本知识

> 函数定义： 设数集 $D \subset R$ ，则称映射 $f: D \rightarrow R$ 为定义在 $D$ 上的函数，通常简记为 $y = f(x), x \in D$ ，其中 $x$ 称为<font color=red>自变量</font>，$y$ 称为<font color=red>因变量</font>，$D$ 称为<font color=red>定义域</font>
>
> 对每个 $x \in D$ ，按对应法则 $f$ ，总有<font color=red>唯一确定的值 $y$ </font> 与之对应

![映射](https://images.rescld.cn/image-20230110231923640.png)



> 反函数定义：设函数 $f: D \rightarrow f(D)$ 是<font color=red>单射</font>，则它的存在逆映射 $f^{-1}: f(D) \rightarrow D$，称此映射 $f^{-1}$ 为函数 $f$ 的反函数
>
> 按此定义，对每个 $y \in f(D)$，有唯一的 $x \in D$，使得 $f(x) = y$，于是有 $f^{-1}(y) = x$

![反函数](https://images.rescld.cn/image-20230110232624923.png)

> 反函数的图像性质：一个函数和反函数之间的曲线关于直线 $y = x$ 轴对称

![反函数的图像性质](https://images.rescld.cn/image-20230111232941147.png)



## 三角函数与反三角函数

![三角函数单位圆](https://images.rescld.cn/image-20230111232429905.png)

> 常用三角函数值

| 角度 | $0^{\circ}$ | $30^{\circ}$ | $45^{\circ}$ | $60^{\circ}$ |
| ---- | ----------- | ------------ | ------------ | ---------- |
| 弧度 | 0 | $\frac{\pi}{6}$ | $\frac{\pi}{4}$ | $\frac{\pi}{3}$ |
| sin | 0 | $\frac{1}{2}$ | $\frac{\sqrt{2}}{2}$ | $\frac{\sqrt{3}}{2}$ |
| cos | 1 | $\frac{\sqrt{3}}{2}$ | $\frac{\sqrt{2}}{2}$ | $\frac{1}{2}$ |
| tan | 0 | $\frac{\sqrt{3}}{3}$ | 1 | $\sqrt{3}$ |

### 基本公式

$tan \theta= \frac{sin \theta}{cos \theta}$ 

$csc\theta = \frac{1}{sin\theta}$ 

$sec\theta = \frac{1}{cos\theta}$ 

$cot\theta = \frac{1}{tan\theta} = \frac{cos\theta}{sin\theta}$ 

---

$cos^2x + sin^2x = 1$ 

$tan^2x + 1 = sec^2x$ 

---

$sin(A+B)  = sinAcosB + cosAsinB$ 

$sin(A-B) = sinAcosB - cosAsinB$ 

---

$tan(A+B)  = \frac{tanA + tanB}{1 - tanAtanB}$ 

$tan(A-B) = \frac{tanA - tanB}{1 + tanAtanB}$ 

---

> 倍角公式与半倍角公式

$sin2\alpha = 2sin\alpha cos\alpha$ 

$cos2\alpha = cos^2\alpha - sin^2\alpha = 1 - 2sin^2\alpha = 2cos^2\alpha - 1$ 

---

$cos^2\frac{\alpha}{2} = \frac{1+cos\alpha}{2}$ 

$cos^2\alpha = \frac{1+cos2\alpha}{2}$ 

---

$sin^2\frac{\alpha}{2} = \frac{1-cos\alpha}{2}$ 

$sin^2\alpha = \frac{1-cos^2\alpha}{2}$ 

---

> 和差化积

$sin\alpha + sin\beta = 2sin\frac{\alpha+\beta}{2}cos\frac{\alpha-\beta}{2}$ 

$sin\alpha - sin\beta = 2cos\frac{\alpha+\beta}{2}sin\frac{\alpha-\beta}{2}$ 

$cos\alpha + cos\beta = 2cos\frac{\alpha+\beta}{2}cos\frac{\alpha-\beta}{2}$ 

$cos\alpha - cos\beta = -2sin\frac{\alpha+\beta}{2}sin\frac{\alpha-\beta}{2}$ 

> 积化和差

$sin\alpha cos\beta = \frac{sin(\alpha + \beta) + sin(\alpha - \beta)}{2}$ 

$cos\alpha sin\beta = \frac{sin(\alpha + \beta) - sin(\alpha - \beta)}{2}$ 

$cos\alpha cos\beta = \frac{cos(\alpha + \beta) + cos(\alpha - \beta)}{2}$ 

$sin\alpha sin\beta = -\frac{cos(\alpha + \beta) - cos(\alpha - \beta)}{2}$ 

### 反三角函数

> 反正弦函数

$y = arcsinx$ 

$x = siny$ 

$x \in [-1, 1], y \in [-\frac{\pi}{2}, \frac{\pi}{2}]$ 

![反正弦函数图像](https://images.rescld.cn/image-20230111233116654.png)

> 反余弦函数

$y = arccosx$ 

$x = cosy$ 

$x \in [-1, 1], y \in [0, \pi]$ 

![反余弦函数图像](https://images.rescld.cn/image-20230111233433552.png)

> 反正切函数

$y = arctanx$ 

$x = tany$ 

$x \in R, y = [-\frac{\pi}{2}, \frac{\pi}{2}]$ 

![反正切函数图像](https://images.rescld.cn/image-20230112160613430.png)



## 指数函数与对数函数

![指数函数](https://images.rescld.cn/image-20230111235757435.png)

> 常用公式

$log_a(M\cdot N) = log_aM + log_aN$ 

$log_a\frac{M}{N} = log_aM - log_aN$ 

$log_aM^n = nlog_aM$ 

$log_{a^n}M = \frac{1}{n}log_aM$ 

$log_ab = \frac{log_cb}{log_ca}$ 

---

$a^{log_ab}=b(a>0, a\neq 1, b>0)$ 

$a = e^{lna}$ 

$a^b=e^{blna}$ 

## 排列组合与二项式定理

> 从 $n$ 个元素中选 $m$ 个元素进行排列，有 $A_n^m$ 个排列方案

$A_6^2 = 6\times 5 = 30$ 

$A_6^3 = 6\times 5\times 4 = 120$ 

$A_n^n = n!$ 

$A_n^m = \frac{n!}{m!}$ 

> 从 $n$ 个元素中选 $m$ 个元素组合（不考虑前后顺序），有 $C_n^m$ 个组合方案

$C_6^3 = \frac{6\times 5\times 4}{3!}$ 

$C_6^4 = \frac{6\times 5\times 4\times 3}{4!} = \frac{6\times 5}{2!} = C_6^2$ 

$C_n^m = \frac{A_n^m}{n!}$

$C_n^m = C_n^{n-m}$ 

### 二项式定理

$(x+y)^n = C_n^0x^ny^0 + C_n^1x^{n-1}y^1 + ...+C_n^{n-1}y^{n-1}+C_n^nx^0y^n$ 

> 推导

$(x+y)^2 = (x+y)(x+y) = x^2 + xy + yx + y^2 = x^2 + 2xy + y^2$ 

$(x+y)^3$ 

$= (x+y)(x+y)(x+y)$ 

$= x^3 + 3x^2y + 3x^1y^2+y^3$ 

$=C_3^0x^3 + C_3^1x^2y + C_3^2x^1y^2 + C_3^3y^3$ 

> 推广

$\sqrt{1.1} = (1 + 0.1)^\frac{1}{2}$

$=1+\frac{\frac{1}{2}}{1!}\times 0.1 + \frac{\frac{1}{2}\times (-\frac{1}{2})}{2!}\times 0.01 + \frac{\frac{1}{2}\times (-\frac{1}{2})\times(-\frac{3}{2})}{2!}\times 0.001 + ....$ 

= 1.04880........

## 常用代数公式

> 等差数列求和

$S_n = a_1n + \frac{n(n-1)d}{2} = \frac{n(a_1+a_n)}{2}$ 

数列首项 $a_1$，公差 $d$，项数 $n$ 

> 等比数列求和

$S_n = \frac{a_1(1-q^n)}{1-q}$ 

数列首项 $a_1$，公比 $q\neq 1$，项数 $n$ 

> $n$ 次方差公式

$a^n - b^n = (a - b)(a^{n-1}+a^{n-2}b+a^{n-3}b^2+...+ab^{n-2}+b^{n-1}), n \in N^*$ 

$=(a-b)($公比 $\frac{b}{a}$ ，$n$ 项求和$)$ 

> $n$ 次方和公式

$a^n + b^n = a^n - (-b)^n, n\in (2N^* + 1)$ 

> 分子有理化

$\sqrt{a} - \sqrt{b} = \frac{(\sqrt{a} - \sqrt{b})(\sqrt{a} + \sqrt{b})}{\sqrt{a} + \sqrt{b}} = \frac{a-b}{\sqrt{a}+\sqrt{b}}$ 

## 极坐标

![极坐标](https://images.rescld.cn/image-20230112235229205.png)

- $r$ 表示点到原点（也成为“极点”）的距离，被称为“极径”，$r\in [0, +\infty]$ 
- $\theta$ 表示点到原点连线与 $x$ 轴（也成为“极轴”）正向之间的夹角大小，被称为“极角”，$\theta\in [0, 2\pi)$ 

> 极坐标转直角坐标

$x = rcos\theta$ 

$y = rsin\theta$ 

> 直角坐标转极坐标

$r = \sqrt{x^2 + y^2} $

$\theta = arctan\frac{y}{x}$ 



