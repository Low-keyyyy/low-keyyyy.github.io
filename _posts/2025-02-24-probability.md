---
layout: distill
title: The Probability Lifesaver
description: A study note about the book, which is the Princeton Textbook.
tags: distill formatting
giscus_comments: true
date: 2024-02-25
featured: true
mermaid:
  enabled: true
  zoomable: true
code_diff: true
map: true
chart:
  chartjs: true
  echarts: true
  vega_lite: true
tikzjax: true
typograms: true

authors:
  - name: Lowkeyyyy
    affiliations:
      name: Nanjing University

# Optionally, you can add a table of contents to your post.
# NOTES:
#   - make sure that TOC names match the actual section names
#     for hyperlinks within the post to work correctly.
#   - we may want to automate TOC generation in the future using
#     jekyll-toc plugin (https://github.com/toshimaru/jekyll-toc).
toc:
  - name: 基本概率定律
  - name: 随机变量
  - name: 数学工具
  - name: 特殊分布
  - name: 极限定理

_styles: >
  d-article{
    p {
      font-family: fangsong;
    }
  }
---

## 基本概率定律

### $$\sigma$$ 代数

设 $$\varOmega$$ 是一个集合, $$\varSigma$$ 是由 $$\varOmega$$ 的子集构成的一个非空集合. 则满足以下前提的 $$\varSigma$$ 是一个 $$\sigma$$ 代数.

(1) 如果 $$A\in\varSigma$$, 那么有 $$A^{c}\in\varSigma$$.

(2) 如果每一个 $$A_{i}$$ 均满足 $$A_{i}\in\varSigma$$, 那么有 $$\cup_{i}A_{i}\in\varSigma$$.



### 概率公理

设 $$\varSigma$$ 是集合 $$\varOmega$$ 的一个 $$\sigma$$ 代数. 我们可以定义一个概率函数 $$Prob$$ : $$\varSigma \to [0, 1]$$. 其中 $$Prob$$ 满足以下公理：

(1) 对于任意的事件 $$A\in\varSigma$$, 均有 $$0\le Pr(A) \le 1$$.

(2) 如果 $$A = \varOmega$$, 那么 $$Pr(A)=1$$.

(3) 如果 $$\{A_{i}\}$$ 是 $$\varSigma$$ 中可数个两两不相交的集合, 那么 $$ Pr(\cup_iA_{i})=\sum_{i}Pr(A_{i})$$.

我们称 $$(\varOmega, \varSigma, Prob)$$ 是一个概率空间. 其中, $$\varOmega$$ 称为样本空间/结果空间, 任意 $$A\in \varSigma$$ 称为事件, $$Pr(A)$$ 称为概率. 



### 样本空间的划分

样本空间 $$\varOmega$$ 的一个划分 $$\mathcal{P}$$ 就是满足下列条件的可数个集合 $$\{A_{1},A_{2},\cdots \}$$.

(1) 如果 $$i \ne j$$, 那么 $$A_{i}\cap A_{j} = \empty$$.

(2) 全体 $$A_{i}$$ 的并就是整个样本空间： $$\cup_{i}A_{i} = \varOmega$$.



### 条件概率

设事件 $$B$$ 满足条件 $$ Pr(B) > 0 $$. 那么已知 $$B$$ 发生时 $$ A$$ 发生的概率称为条件概率, 记为 $$Pr(A|B)$$. 且有以下等式：
$$
Pr(A|B) = \frac{Pr(A\cap B)}{Pr(B)}
$$


### 全概率公式

若存在一组事件 $$B_{i}(i = 1,2,\cdots)$$ 构成了样本空间 $$\varOmega$$ 的一个划分, 同时任意事件概率 $$Pr(B_{i})>0$$. 那么对于任意的$$A\subset \varOmega$$ 都有：
$$
Pr(A) = \sum_{i} Pr(A|B_{i})\cdot Pr(B_{i})
$$


### 独立性

**两个事件**

如果事件 $$A$$ 和 $$B$$ 满足：
$$
Pr(A\cap B) = Pr(A) \cdot Pr(B)
$$
那么事件 $$A$$ 和 $$B$$ 就是独立的.

**一般情形**

如果一组事件 $$A_{1},A_{2},\cdots, A_{n}$$ 满足：

(1) $$Pr(\cap_{i=1}^{n}A_{i})=\prod_{i=1}^{n}Pr(A_{i})$$ .

(2) $$\{A_{1},A_{2},\cdots,A_{n} \}$$ 的任意一个非空子集都是相互独立的.

那么 $$A_{1},A_{2},\cdots, A_{n}$$ 就是相互独立的.



### 贝叶斯定理

任意条件概率 $$Pr(A|B)$$ 满足：
$$
Pr(A|B) = Pr(B|A)\cdot\frac{Pr(A)}{Pr(B)}
$$
**推广**

设 $$\mathcal{P} = \{ A_{1},A_{2},\cdots \}$$ 是样本空间的一个划分, 那么有：
$$
Pr(A|B) = \frac{Pr(B|A)\cdot Pr(A)}{\sum_{i} Pr(B|A_{i})\cdot Pr(A_{i})}
$$
其中, $$A$$ 就是某一个 $$A_{i}$$.



### 容斥原理

设事件 $$A_{1},A_{2},\cdots,A_{n}$$. 则有以下等式成立：
$$
Pr(\cup_{i=1}^{n}A_{i}) = \sum_{t=1}^{n} \left( (-1)^{t-1}\sum_{1\le l_{1}<{l_{2}<\cdots<l_{t}\le n}}Pr(A_{l_{1}}\cap A_{l_{2}}\cap \cdots\cap A_{l_{t}}) \right)
$$


### 错排公式

$$ n$$ 个元素的错排数记为 $$ D_{n}$$. 
$$
D_{n} = n!-\sum_{i=1}^{n}(-1)^{{i-1}}\frac{n!}{i!}=n!\sum_{i=0}^{n}\frac{(-1)^{i}}{i!}
$$

$$
Pr = \frac{D_{n}}{n!}=\sum_{i=0}^{n}\frac{(-1)^{i}}{i!}\approx e^{-1}\space\space\space\space\space(n\to +\infty)
$$



### 二项式系数 & 多项式系数

**二项式系数**
$$
(x+y)^{n} = \sum_{k=0}^{n} \binom{n}{k}x^{k}y^{n-k}
$$
其中, $$\binom{n}{k} = \frac{n!}{k!(n-k)!}$$.

**多项式系数**
$$
(x_{1}+x_{2}+\cdots+x_{t})^{N} = \sum_{\substack{0\le n_{1},n_{2},\cdots,n_{t}\le N \\ n_{1}+n_{2} \cdots+n_{t} = N}}\binom{N}{n_1,n_2,\cdots,n_{t}}x_{1}^{n_{1}}x_{2}^{n_{2}}\cdots x_{t}^{n_{t}}
$$
其中, $$\binom{N}{n_{1},n_{2},\cdots,n_{t}}=\frac{N!}{n_{1}!n_{2}!\cdots n_{t}!}$$.





## 随机变量

### 离散型随机变量

离散型随机变量 $$X$$ 就是定义在一个离散的结果空间 $$\varOmega$$ 上的实值函数. 具体地说, 我们为每个元素 $$\omega \in \varOmega$$ 指定了一个实数 $$X(\omega)$$.



### 离散型随机变量的概率密度函数 (probability density of function, PDF)

设 $$X$$ 是一个定义在结果空间 $$\varOmega$$ 上的离散型随机变量. 那么 $$X$$ 的概率密度函数就是 $$X$$ 取某个特定值的概率：
$$
f_{X}(x)=Prob(\omega\in \varOmega: X(\omega)=x)
$$


### 离散型随机变量的累计分布函数 (cumulative distribution function, CDF)

设 $$X$$ 是一个定义在结果空间 $$\varOmega$$ 上的离散型随机变量. 那么 $$X$$ 的累计分布函数就是 $$X$$ 不超过某个特定值的概率：
$$
F_{X}(x)=Prob(\omega \in \varOmega:X(\omega)\le x)
$$


### 连续型随机变量、概率密度函数和累积分布函数

设 $$X$$ 是一个随机变量. 如果存在一个实值函数 $$f_{X}$$ 满足：

(1) $$f_{X}$$ 是一个分段连续函数.

(2) $$f_{X}(x)\ge0$$.

(3) $$\int_{-\infty}^{+\infty}f_{X}(x)dx = 1$$.

那么 $$X$$ 是一个连续型变量, $$f_{X}$$ 是 $$X$$ 的概率密度函数. $$X$$ 的累积分布函数 $$F_{X}(x)$$ 就是 $$X$$ 不大于 $$x$$ 的概率：
$$
F_{X}(x) = Prob(X\le x) = \int_{-\infty}^{x} f_{X}(x)dx
$$


### 对潜在概率密度函数的标准化

如果 $$f_{X}$$ 是一个非负的分段连续函数, 并且它的积分值是有限的, 那么
$$
g_{X}(x)= \frac{f_{X}(x)}{\int_{-\infty}^{+\infty}f_{X}(x)dx}
$$
就是一个概率密度函数.



### 累积分布函数的极限

设 $$F_{X}$$ 是随机变量 $$X$$ 的累积分布函数. 那么有：
$$
\lim_{x\to -\infty} F_{X}(x) = 0 \space\space\space\space\space \lim_{x\to + \infty} F_{X}(x) = 1
$$
如果 $$y>x$$, 那么 $$F_{X}(y) \ge F_{X}(x)$$.





## 数学工具

### 期望值和矩

设 $$X$$ 是定义在 $$\mathbb{R}$$ 上的随机变量, 它的概率密度函数是 $$f_{X}$$. 函数 $$g(X)$$ 的期望值是：
$$
\mathbb{E}[g(X)] = \left\{ \begin{aligned} 
&\int_{-\infty}^{+\infty}g(x)\cdot f_{X}(x)dx &&X\space is \space a\space continuous \space variable.
\\&\sum_{i} g(x_{i})\cdot f_{X}(x_{i}) &&X\space is \space a\space discrete \space variable.
\end{aligned}\right.
$$
如果 $$g(x)=x^{r}$$, 我们称 $$\mathbb{E}[X^{r}]$$ 为 $$X$$ 的 $$r$$ 阶矩, $$\mathbb{E}[(X-\mathbb{E}[X])^{r}]$$ 为 $$X$$ 的 $$r$$ 阶中心距.



### 均值

设 $$X$$ 是一个随机变量, 那么 $$X$$ 的均值便是 $$\mathbb{E}[X]$$, 也可记作 $$\mu_{X} $$.



### 方差和标准差

设 $$X$$ 是一个随机变量, 那么 $$X$$ 的方差便是 $$\mathbb{E}[(X-\mathbb{E}[X])^{2}]$$, 也可记作 $$\sigma^{2}_{X} $$ 或 $$Var(X)$$. 并且有：
$$
\sigma^{2}_{X} = \mathbb{E}[X^{2}] - \mathbb{E}^{2}[X]
$$
而 $$X$$ 的标准差记为 $$\sigma_{X}$$, 且 $$\sigma_{X} = \sqrt{\sigma^{2}_{X}}$$.



### 联合分布

**联合概率密度函数**

设 $$X_{1},X_{2},\cdots,X_{n}$$ 都是连续型随机变量, 它们的概率密度函数分别是 $$f_{X_{1}},f_{X_{2}},\cdots,f_{X_{n}}$$. 假设每个 $$X_{i}$$ 都定义在 $$\mathbb{R}$$ 的一个子集上. 那么, $$(X_{1},X_{2},\cdots,X_{n})$$ 的联合概率密度函数就是一个非负可积函数 $$f_{X_{1},X_{2},\cdots,X_{n}}$$, 满足对于每一个恰当的集合 $$S \subset \mathbb{R}^{n}$$, 均有：
$$
Prob((X_{1},X_{2},\cdots,X_{n})\in S) =  \int\cdots\int_{S} f_{X_{1},X_{2},\cdots,X_{n}}(x_{1},x_{2},\cdots,x_{n})dx_{1}dx_{2}\cdots dx_{n}
$$


**边缘概率密度函数**

$$X_{i}$$ 的边缘概率密度函数记作 $$f_{X_{i}}$$.
$$
f_{X_{i}}(x_{i}) = \int_{x_{1} = -\infty}^{+\infty} \cdots \int_{x_{i-1} = -\infty}^{+\infty}\int_{x_{i+1} = -\infty}^{+\infty}\cdots \int_{x_n = -\infty}^{+\infty}\prod_{\substack{j=1\\j\ne i}}^{n}dx_{j}
$$
其中这 $$n$$ 个随机变量相互独立, 当且仅当：
$$
f_{X_{1},X_{2},\cdots,X_{n}}(x_{1},x_{2},\cdots,x_{n}) = \prod_{i=1}^{n} f_{X_{i}}(x_{i})
$$
对于离散型变量, 只需要将积分替换成求和即可.



### 期望的线性性质

设 $$X_{1}, X_{2}, \cdots, X_{n}$$ 是随机变量, 并设 $$g_{1},g_{2},\cdots,g_{n}$$ 是满足下列条件的函数：$$\mathbb{E}[|g_{i}(X_{i})|]$$ 存在且有限. 令 $$a_{1},a_{2},\cdots,a_{n}$$ 表示任意实数.

那么：
$$
\mathbb{E}[a_{1}g_{1}(X_{1})+a_{2}g_{2}(X_{2})+\cdots+a_{n}g_{n}(X_{n})] = a_{1}\mathbb{E}[g_{1}(X_{1})] +a_2\mathbb{E}[g_{2}(X_{2})]+\cdots+a_{n}\mathbb{E}[g_{n}(X_{n})]
$$


### 均值和方差的性质

如果 $$X$$ 和 $$Y$$ 是相互独立的随机变量, 那么有：
$$
\mathbb{E}[XY] = \mathbb{E}[X]\mathbb{E}[Y]
$$
设 $$X_{1},X_{2},\cdots,X_{n}$$ 是 $$n$$ 个随机变量, 均值分别是 $$\mu_{X_{1}},\mu_{X_{2}},\cdots,\mu_{X_{n}}$$, 方差是 $$\sigma_{X_{1}}^{2},\sigma_{X_{2}}^{2},\cdots,\sigma_{X_{n}}^{2}$$. 如果 $$X = X_{1} +X_{2}+\cdots+X_{n}$$, 那么有：
$$
\mu_{X} = \mu_{X_{1}}+\mu_{X_{2}}+\cdots+\mu_{X_{n}}
$$
如果随机变量是相互独立的, 那么还有:
$$
\sigma_{X}^{2} = \sigma_{X_{1}}^{2} + \sigma_{X_{2}}^{2} + \cdots + \sigma_{X_{n}}^{2}
$$
如果这些随机变量是独立同分布的, 那么可以得到：
$$
\mu_{X} = n\mu \space\space\space\space\space \sigma_{X}^{2} = n\sigma^{2}
$$


### 偏斜度与峰度

偏斜度是三阶中心距, 测量了分布的不对称性. 峰度是四阶中心矩, 测量了分布的峰值的平稳程度.



### 协方差

设 $$X$$ 和 $$Y$$ 是两个随机变量. $$X$$ 和 $$Y$$ 的协方差记作 $$\sigma_{XY}$$ 或者 $$Cov(X,Y)$$, 其表达式为：
$$
\sigma_{XY} = \mathbb{E}[(X-\mu_X)(Y-\mu_Y)] = \mathbb{E}[XY] - \mu_{X}\mu_{Y}
$$
如果 $$X_{1},X_{2},\cdots,X_{n}$$ 都是随机变量, 并且 $$X=X_{1}+X_{2}+\cdots + X_{n}$$. 那么有：
$$
Var(X) = \sum_{i=1}^n Var(X_{i}) + 2 \sum_{1\le i < j\le n} Cov(X_{i},X_{j})
$$
注意：协方差只能测量两个变量的线性相关程度, 协方差为正则是正相关, 协方差为负则是负相关, 协方差为 $$0$$ 无法说明二者是相互独立的.



### 相关系数

相关系数是协方差的标准化, 记作 $$\rho$$.
$$
\rho = \frac{Cov(X,Y)}{\sigma_{X}\sigma_{Y}} = \frac{Cov(X,Y)}{\sqrt{Var(X)Var(Y)}}
$$
我们始终有 $$\rho \in [-1,1]$$, 他描述了两个变量之间的线性相关强度. 相关系数越接近 $$-1$$ 或 $$1$$, 线性相关性就越强.



### 卷积

设 $$X$$ 和 $$Y$$ 是定义在 $$\mathbb{R}$$ 上的两个相互独立的连续型随机变量, 它们的概率密度分别是 $$f_{X}$$ 和 $$f_{Y}$$. $$X$$ 和 $$Y$$ 的卷积记作 $$f_{X} *f_{Y}$$, 其表达式为：
$$
(f_{X}*f_{Y})(z) = \int_{-\infty}^{+\infty}f_{X}(t)f_{Y}(z-t)dt
$$
如果 $$X$$ 和 $$Y$$ 是离散型随机变量, 那么有：
$$
(f_{X}*f_{Y})(z) = \sum_{i} f_{X}(x_{i})f_{Y}(z-x_{i})
$$
设 $$X$$ 和 $$Y$$ 是定义在 $$\mathbb{R}$$ 上的两个相互独立的连续型或离散型随机变量, 它们的概率密度分别是 $$f_{X}$$ 和 $$f_{Y}$$. 如果 $$Z=X+Y$$, 那么有：
$$
f_{Z}(z) = (f_{X}*f_{Y})(z)
$$
并且, 卷积满足交换律和结合律.

设 $$X_{1},X_{2},\cdots,X_{n}$$ 是相互独立的随机变量, 它们的概率密度函数分别是 $$f_{X_{1}},f_{X_{2}},\cdots,f_{X_{n}}$$, 那么有：
$$
f_{X_{1}+X_{2}+\cdots+X_{n}}(z) = (f_{X_{1}}*f_{X_{2}}*\cdots*f_{X_{n}})(z)
$$


### 变量替换

设 $$X$$ 是一个概率密度函数为 $$f_{X}$$ 的连续型随机变量, 并设存在一个区间 $$I\subset\mathbb{R}$$ 使得当 $$x\notin I$$ 时, $$f_{X}(x) = 0$$. 设 $$g:I\to\mathbb{R}$$ 是一个可微函数, 并存在反函数 $$h$$. 如果令 $$Y = g(X)$$, 则 $$X = h(Y)$$, 那么有：
$$
f_{Y}(y) = f_{X}(h(y))\cdot|h^{'}(y)|
$$
证明：
$$
f_{Y}(y) = |\frac{d}{dy}F_{X}(h(y))| = |f_{X}(h(y))\cdot\frac{d}{dy}h(y)| = f_{X}(h(y))\cdot| h^{'}(y) |
$$


### 随机变量的运算

设 $$X$$ 和 $$Y$$ 是相互独立的随机变量, 它们的概率密度函数分别是 $$f_{X}$$ 和 $$f_{Y}$$. 设 $$Z = g(X,Y)$$, 并且能解出函数关系 $$Y=h(	X,Z)$$,

那么有：
$$
f_{Z}(z) = \int_{t_{1}}^{t_{2}} f_{X}(t)f_{Y}(h(t,z))| \frac{\part h(t,z)}{\part z} |dt
$$
其中积分范围 $$(t_{1},t_{2})$$ 取决于具体的函数限制.



### 微分恒等式

设 $$\alpha,\beta,\gamma,\cdots,\omega$$ 是一些参数. 设
$$
\sum_{n=n_{min}}^{n_{max}}f(n;\alpha,\beta,\cdots,\omega) = g(\alpha,\beta,\cdots,\omega)
$$
其中 $$f$$ 和 $$g$$ 是关于 $$\alpha$$ 的可微函数. 如果 $$f$$ 退化到足以保证求和与求微分的次序可以交换, 那么：
$$
\sum_{n=n_{min}}^{n_{max}} \frac{\part f(n;\alpha,\beta,\cdots,\omega)}{\part \alpha} = \frac{\part g(\alpha,\beta,\cdots,\omega)}{\part \alpha}
$$

### 斯特林公式

当 $$n\to\infty$$ 时, 我们有：
$$
n!\approx n^{n}e^{-n}\sqrt{2\pi n}
$$





## 特殊分布

### 离散分布

#### 伯努利分布

记作 $$X \sim Bern(p)$$.
$$
f_{X}(x=1) = p \space\space\space\space\space f_{X}(x=0) = 1-p
$$

$$
\mu_{X} = p \space\space\space\space\space \sigma_{X}^{2} = p(1-p)
$$



#### 二项分布

记作 $$X\sim Bin(n,p)$$.
$$
f_{X}(x=k) = \binom{n}{k} p^{k}(1-p)^{n-k} \space\space\space\space\space k\in\{0,1,\cdots,n\}
$$

$$
\mu_{X} = np \space\space\space\space\space \sigma_{X}^{2} = np(1-p)
$$



#### 多项分布

记作 $$X \sim Multinomial(n,k,p_{1},p_{2},\cdots,p_{k})$$.
$$
f_{X}(x = (x_{1},x_{2},\cdots,x_{k})) = \binom{n}{x_{1},x_{2},\cdots,x_{k}}p_{1}^{x_{1}}p_{2}^{x_{2}}\cdots p_{k}^{x_{k}} \space\space\space\space\space x_{1}+x_{2}+\cdots+x_{k} = n
$$


#### 几何分布

记作 $$X\sim Gemo(p)$$.
$$
f_{X}(x=n) = p(1-p)^{n-1} \space\space\space\space\space n\in\{1,2,3,\cdots\}
$$

$$
\mu_{X}=\frac{1}{p} \space\space\space\space\space \sigma^{2}_{X} = \frac{1-p}{p^{2}}
$$



#### 负二项分布

记作 $$X\sim NegBin(r,p)$$.
$$
f_{X}(x=k) = \binom{k+r-1}{k} p^{k}(1-p)^{r} \space\space\space\space\space k\in\{0,1,2\cdots\}
$$

$$
\mu_{X} = \frac{pr}{1-p} \space\space\space\space\space \sigma_{X}^{2} = \frac{pr}{(1-p)^{2}}
$$



#### 泊松分布

记作 $$X \sim Pois(\lambda)$$. 
$$
f_{X}(x=n) = \frac{\lambda^{n}}{n!}e^{-\lambda} \space\space\space\space\space n\in\{0,1,2,\cdots\}
$$

$$
\mu_{X} = \lambda \space\space\space\space\space \sigma_{X}^{2} = \lambda
$$



#### 超几何分布

记作 $$X\sim H(n,M,N)$$.
$$
f_{X}(x=k) = \frac{\binom{M}{k}\binom{N-M}{n-k}}{\binom{N}{n}} \space\space\space\space\space k\in\{0,1,2,\cdots,min(n,M)\}
$$

$$
\mu_{X} = \frac{nM}{N} \space\space\space\space\space \sigma_{X}^{2} = \frac{nM}{N}(1-\frac{M}{N})\frac{N-n}{N-1}
$$



### 连续型随机变量

#### 均匀分布

记作 $$X\sim Unif(a,b)$$.
$$
f_{X}(x) = \frac{1}{b-a} \space\space\space\space\space a\le x\le b
$$

$$
\mu_{X} = \frac{b+a}{2} \space\space\space\space\space \sigma^{2}_{X} = \frac{(b-a)^{2}}{12}
$$



#### 指数分布

记作 $$X\sim Exp(\lambda)$$.
$$
f_{X}(x) = \frac{1}{\lambda}e^{-\frac{x}{\lambda}} \space\space\space\space\space x>0
$$

$$
\mu_{X} = \lambda \space\space\space\space\space \sigma_{X}^{2} = \lambda^{2}
$$



#### 正态分布

记作 $$X\sim N(\mu,\sigma^{2})$$.
$$
f_{X}(x) = \frac{1}{\sqrt{2\pi\sigma^{2}}}e^{-\frac{(x-\mu)^{2}}{2\sigma^{2}}}
$$

$$
\mu_{X} = \mu \space\space\space\space\space \sigma_{X}^{2} = \sigma^{2}
$$

如果 $$\mu = 0$$ 并且 $$\sigma^{2} = 1$$, 则称 $$X$$ 服从标准正态分布.
$$
f_{X}(x) = \frac{1}{\sqrt{2\pi}} e^{-\frac{x^{2}}{2}}
$$
如果 $$X_{i}\sim N(\mu_{i},\sigma_{i}^{2})$$ 是相互独立且都服从正态分布的随机变量, 那么有：
$$
X_{1}+X_{2}+\cdots+X_{n} \sim N(\mu_{1}
+\mu_{2}+\cdots+\mu_{n},\sigma_{1}^{2}+\sigma_{2}^{2}+\cdots+\sigma_{n}^{2})
$$



#### 伽马函数

**伽马函数定义**

如果 $$s>0$$, 那么伽马函数 $$\Gamma(s)$$ 就是：
$$
\Gamma(s) = \int_{0}^{+\infty}e^{-x}x^{s-1}dx
$$
**$$\Gamma(s)$$ 的函数方程**
$$
\Gamma(s+1) = s\Gamma(s)
$$
于是可以得到, 若 $$n$$ 是一个非负整数, 那么 $$\Gamma(n+1) = n!$$. 伽马函数是阶乘函数在 $$\mathbb{R}$$ 上的解析延拓.

**余元公式**

如果 $$0<s<1$$, 则有：
$$
\Gamma(s)\Gamma(1-s)=\frac{\pi}{\sin(\pi s)}
$$
由此立得 $$\Gamma(\frac{1}{2})=\sqrt{\pi}$$.



#### 伽马分布

记作 $$X\sim Gamma(k,\sigma)$$.
$$
f_{k,\sigma}(x) = \frac{1}{\Gamma(k)\sigma^{k}}x^{k-1}e^{-\frac{x}{\sigma}} \space\space\space\space\space x\ge0
$$
​                



#### 贝塔函数

当 $$a,b>0$$ 时, 函数的定义为：
$$
\Beta(a,b) = \int_{0}^{1}t^{a-1}(1-t)^{b-1}dt=\frac{\Gamma(a)\Gamma(b)}{\Gamma(a+b)}
$$


#### 贝塔分布

记作 $$X\sim Beta(a,b)$$.
$$
f_{a,b}
(t)=\frac{\Gamma(a+b)}{\Gamma(a)\Gamma(b)}t^{a-1}(1-t)^{b-1} \space\space\space\space\space 0\le t \le 1
$$


#### 韦布尔分布

记作 $$X\sim W(k,\sigma)$$.
$$
f_{k,\sigma}(x) = \frac{k}{\sigma}\left(\frac{x}{\sigma}\right)^{k-1}e^{-\left(\frac{x}{\sigma}\right)^
{k}}\space\space\space\space\space x\ge0
$$


#### 卡方分布

记作 $$X\sim \chi^{2}(\nu)$$.
$$
f_X(x) = \frac{1}{2^{\frac{\nu}{2}}\Gamma(\frac{\nu}{2})}x^{(\frac{\nu}{2}-1)}e^{-\frac{x}{2}} \space\space\space\space\space x\ge0
$$
**卡方分布与正态分布的关系**

如果 $$X_{1},X_{2},\cdots,X_{n}$$ 是相互独立且服从标准正态分布的随机变量, 设 $$Y=\sum_{i=1}^{n}X_{i}^{2}$$, 那么有 $$Y\sim \chi^{2}(n)$$. 若 $$Y_{i}\sim \chi^{2}(\nu_{i})$$, 则 $$Y=\sum_{i=1}^{n}Y_{i}\sim\chi^{2}(\sum_{i=1}^{n}\nu_{i})$$.





## 极限定理

### 不等式

#### 马尔可夫不等式

设 $$X$$ 是一个均值有限的非负随机变量, 均值为 $$\mathbb{E}[X]$$. 那么对于任意的正数有 $$a$$ 有：
$$
Prob(x\ge a) \le \frac{\mathbb{E}[X]}{a} 
$$


#### 切比雪夫不等式

设 $$X$$ 是随机变量, 它的均值 $$\mu_{X}$$ 和方差 $$\sigma^{2}_{X}$$ 都是有限的. 那么对于任意的 $$k>0$$ 有：
$$
Prob(|X-\mu_{X}|\ge k\sigma) \le \frac{1}{k^{2}}
$$


#### 布尔不等式

设 $$A_{1},A_{2},\cdots,A_{n}$$ 是一组有限多个集合. 那么：
$$
Prob(\cup^{n}_{i=1}A_{i})\le\sum_{i=1}^{n}Prob(A_{i})
$$


#### 邦弗伦尼不等式

设 $$A_{1},A_{2},\cdots,A_{n}$$ 是一组有限多个集合. 引入符号 $$S_{k}$$, 且定义如下：
$$
S_{k} = \sum_{1\le i_{1}<i_{2}<\cdots<i_{k}\le n} Prob(A_{i_{1}}\cap A_{i_{2}}\cap \cdots \cap A_{i_{k}})
$$
那么有不等式：
$$
\sum_{k=1}^{2l}(-1)^{k-1}S_{k} \le Prob(\cup^{n}_{i=1}A_{i})\le\sum_{k=1}^{2m-1} (-1)^{k-1}S_{k}
$$


### 收敛类型

#### 依分布收敛

对于随机变量序列 $$\{X_{n}\}$$ 和随机变量 $$X$$, 对应的累积分布函数分别记为 $$\{F_{n}\}$$ 和 $$F$$. 如果对于所有连续点 $$x$$ 都有：
$$
\lim_{n \to \infty}F_{n}(x) = F(x)
$$
则称 $$\{X_n\}$$ 依分布收敛于 $$X$$. 记作 $$X_{n}\xrightarrow{d} X$$.



#### 依概率收敛

对于随机变量序列 $$\{X_{n}\}$$ 和随机变量 $$X$$, 如果对于任意的 $$\epsilon>0$$, 都有：
$$
\lim_{n \to \infty} Prob(| X_{n}-X |\ge\epsilon) = 0
$$
则称 $$\{X_n\}$$ 依概率收敛于 $$X$$. 记作 $$X_{n}\xrightarrow{p} X$$.



#### 几乎必然收敛

对于随机变量序列 $$\{X_{n}\}$$ 和随机变量 $$X$$, 如果有：
$$
Prob(\lim_{n\to\infty}X_{n}= X) = 1
$$
则称 $$\{X_n\}$$ 几乎必然收敛于 $$X$$. 记作 $$X_{n}\xrightarrow{a.s.} X$$.



#### 必然收敛

对于随机变量序列 $$\{X_{n}\}$$ 和随机变量 $$X$$, 如果对任意的 $$\omega\in\Omega$$ 都有：
$$
\lim_{n\to\infty}X_{n}(\omega) = X(\omega)
$$
则称 $$\{X_n\}$$ 必然收敛于 $$X$$. 记作 $$X_{n}\xrightarrow{sure} X$$.



### 大数定律

#### 弱大数定律

设 $$X_{1},X_{2},\cdots,X_{n}$$ 是独立同分布的随机变量, 且分布的均值为 $$\mu$$, 设 $$\bar{X}_{n}=\frac{1}{n}\sum_{i=1}^{n}X_{i}$$. 那么有：
$$
\bar{X}_{n}\xrightarrow{p}\mu
$$


#### 强大数定律

设 $$X_{1},X_{2},\cdots,X_{n}$$ 是独立同分布的随机变量, 且分布的均值为 $$\mu$$, 设 $$\bar{X}_{n}=\frac{1}{n}\sum_{i=1}^{n}X_{i}$$. 那么有：
$$
\bar{X}_{n}\xrightarrow{a.s.}\mu
$$

