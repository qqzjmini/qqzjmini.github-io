---
title: 概率统计
description: Create beautiful interactive image gallery using Markdown
date: 2024-09-18 00:00:00+0000
image: 2.jpg
math: true
---

## 概率

期望存在的条件：

- 离散：$\Sigma X(w)p(w)$ 必须绝对收敛，否则求和顺序会影响结果
- 连续：积分存在？

密度函数：

- 非负
- 归一化条件（可积）

连续随机变量充分必要条件：

- $\{\omega:X(\omega)\leq X\}$ 可测（等价于存在分布函数）

二元：
$$
E(\varphi(X,Y))=\int_{-\infty}^{\infty}\int_{-\infty}^{\infty}\varphi(u,v)f(u,v)dudv.
$$

令 $\varphi=I_S$，$S\subseteq \mathbb{R}^2$，有：

$$
P((X,Y)\in S)=\iint_Sf(u,v){\rm d}u{\rm d}v
$$

条件概率结论：

$\begin{aligned}\mathsf{P}(\mathsf{A}_1\mathsf{A}_2\cdots\mathsf{A}_n)&=\mathsf{P}(\mathsf{A}_1)\mathsf{P}(\mathsf{A}_2|\mathsf{A}_1)\mathsf{P}(\mathsf{A}_3|\mathsf{A}_1\mathsf{A}_2)\\&\cdots\mathsf{P}(\mathsf{A}_n|\mathsf{A}_1\mathsf{A}_2\cdots\mathsf{A}_{n-1}).\end{aligned}$
（要求 $\mathsf{P}(\mathsf{A}_1\mathsf{A}_2\cdots\mathsf{A}_n)>0$）

Bayes公式：
$$P(A_n|B)=\frac{P(A_n)P(B|A_n)}{\sum_kP(A_k)P(B|A_k)}.$$
（条件：$P(B)>0$，即左边有定义）
若 $P(A_k)=0$，直接令那项为零即可，不用顾虑 $P(B|A_k)$ 的存在性。

序列抽样：假设一个盒子里有 $b$ 个黑，$r$ 个红，不放回抽样，有：第 $n$ 次抽取抽到黑球：$P(B_n)=\frac{b}{b+r}$. (考虑抽取序列为一个尾部为黑的排列)

随机变量的独立：

- 可数：$$P(X_1=x_1,\cdots,X_n=x_n)=P(X_1=x_1)\cdots P(X_n=x_n).$$
- 一般：$\{X_1\leq x_1\},\{X_2\leq x_2\},\cdots,\{X_n\leq x_n\}$ 独立，等价于：$$F(x_1,\cdots,x_n)=F_1(x_1)\cdots F_n(x_n),$$ 推出：$$f(u_1,\cdots,u_n)=f_1(u_1)\cdots f_n(u_n).$$

Banach 火柴问题：（P210）
$$p_k=\binom{2n-k}n\left(\frac12\right)^{2n-k}.$$

$X=\max\{X_1,X_2,\ldots,X_n\}$ 的分布函数：
$$F_X(x)=F(X_1)F(X_2)\cdots F(X_n)$$

若 $X$, $Y$ 独立，并且期望存在，有
$$E(XY)=E(X)E(Y).$$

边际分布：只看一个变量，可以通过求和或者积分来求解，也可以直接通过概率来求。

高阶力矩存在，低阶力矩一定存在吗？

- 离散：由于要求绝对收敛，放缩可证
- 连续：直接放缩，对正负分开处理
  所以方差存在，期望也必存在，二阶矩也存在

若 $X_1,\cdots,X_n$ 独立，则
$$\sigma^2(X_1+\cdots+X_n)=\sigma^2(X_1)+\cdots+\sigma^2(X_n).$$

期望的 Cauchy-Schwarz 不等式：
$$[E(XY)]^2\leq E(X^2)E(Y^2).$$
（内积）
同样的，$E(X_0Y_0)$ 也满足上述条件
协方差：
$$\mathrm{Cov}(X,Y)=E(XY)-E(X)E(Y)=E(X_0Y_0)$$

关联系数：
$$\rho(X,Y)=\frac{\mathrm{Cov}(X,Y)}{\sigma(X)\sigma(Y)}\in[-1,1]$$
$X$ 和 $Y$ 独立，则 $\rho(X,Y)={\rm Cov(X,Y)}=0$，然而反过来不一定。

多项式分布的边际分布是二项式分布

**生成函数**（非负整数）：生成函数和分布是一一对应
$$g(z)=E(z^X)$$
$$E(X)=g^{\prime}(1),\quad E(X^2)=g^{\prime}(1)+g^{\prime\prime}(1),$$
$$\sigma^2(X)=E(X^2)-(E(X))^2=g^{\prime}(1)+g^{\prime\prime}(1)-(g^{\prime}(1))^2$$
定理：

- 若随机变量$x_1,\cdots,x_n$独立，生成函数分别为$g_1,\cdots,g_n$, 则其和$x_1+\cdots+x_n$的生成函数$g$为各个随机变量生成函数的乘积，即$g=g_1\cdots g_{n}$。
  （证明：独立推出期望可乘）

生成函数对于

- 取值非负的连续随机变量：Laplace 变换
  $$E(e^{-\lambda X})=\int_{-\infty}^{\infty}e^{-\lambda u}f(u)du.$$
- 取值为 $\mathbb{R}$ 的随机变量：Fourier 变换
  $$E(e^{i\theta X})=\int_{-\infty}^\infty e^{i\theta u}f(u)du,$$

**Poisson 分布**的由来：二项式分布的极限 ($B(n,\alpha/n)$)
$$\lim_{n\to\infty}a_0(n)=e^{-\alpha},\quad\lim_{n\to\infty}\frac{a_{k+1}(n)}{a_k(n)}=\frac\alpha{k+1}.$$
于是：
$$\lim_{n\to\infty}A_k(n,\frac\alpha n)=\pi_k(\alpha)=\frac{\alpha^k}{k!}e^{-\alpha}.$$


- 已知函数$\varphi$定义在$[0,\infty)$上的非负、单减、不恒为零的函数，满足方程（Cauchy 性质）$$
  \varphi(s+t)=\varphi(s)\varphi(t),\forall s,t\geq0.
  $$则存在某个$\lambda\geq0$使得$\varphi(t)=e^{-\lambda t},\forall t\geq0$。

所以，满足 Markov 性质的分布，其密度函数和分布函数一定是指数。

矩母函数：$E(e^{\lambda X})$，前提是积分存在。

**正态分布**来源：
De Moivre-Laplace 定理：二项分布正规化后，极限趋近于正态分布。
证明： Stirling 公式

正态分布性质：
尾部估计：
$$1-\Phi(x)=\int_x^\infty\varphi(u)du\leq\frac{\varphi(x)}x=\frac{e^{-x^2/2}}{\sqrt{2\pi}x}.$$
矩母函数：$M(\theta)=e^{\theta^2/2}$
“矩母“，可以生成力矩，用泰勒展开易证， $M^{(n)}(0)$ 为随机变量的 $n$ 阶力矩。

正态分布 $N(m,\sigma^2)$ 

- 密度函数：
  $$\frac{1}{\sqrt{2\pi}\sigma}\exp\left(-\frac{(x-m)^{2}}{2\sigma^{2}}\right)=\frac{1}{\sigma}\varphi\left(\frac{x-m}\sigma\right)$$
- 矩母函数：$$M(\theta)=e^{m\theta+\sigma^2\theta^2/2}$$（不要算积分，用期望变换）
- 特征函数：$$E(e^{i\theta X})=e^{-\theta^2/2}$$

正态分布的和：

- 设随机变量 $X_j$ 独立，具有正态分布$N(m_j,\sigma_j^2)$, 则$X_1+X_2+\cdots+X_n$ 具有正态分布$N(m_1+\cdots+m_n,\sigma_1^2+\cdots+\sigma_n^2).$
  证明：矩母函数之积

**中心极限**定理：任意独立同分布变量之和的正规化，极限均为正态分布。
（De Moivre-Laplace 定理是特例， Bernoulli 分布）
证明：证明特征函数趋近于正态分布特征函数，然后可得分布函数亦趋近。（由特征函数到分布函数证明不要求）
特征函数的趋近来源于两个点：

- 特征函数的泰勒展开系数与期望和均值有关；
- 重要极限（ $e$ 的定义）

中心极限的意义在于，在重复次数够大的时候，可以忽略单个变量具体是什么分布。

**Chebyshev 不等式**: 设随机变量$X$第2阶力矩有限，则对任意常数$c>0$,
$$
\mathbb{P}\left(|X|\geq c\right)\leq\frac{\mathbb{E}(X^2)}{c^2}.
$$
（估计两尾至少为平方级衰减）
如果 $n$ 阶力矩存在，则以 $1/c^n$ 级别衰减。

**大数定律:**
设中心极限定理假设满足，则对任意固定常数 $C>0$,
$$\lim_{n\to\infty}\mathbb{P}\left(\left|\frac{S_n}n-m\right|<c\right)=1.$$
（用中心极限）
推广的大数定律和中心极限独立：

*推广的*大数定律: 
设随机变量$\{X_j,j\geq1\}$独立，满足
$$\mathbb{E}(X_j)=m_j,\quad \sigma^{2}(X_{j})=\sigma_{j}^{2}$$
且存在常数$M<\infty$使得对所有j，$\sigma_j^2\leq M$，即 $\{\sigma_n^2\}$ 有界
则对任意 $c>0$，
$$\lim_{n\to\infty}\mathbb{P}\left(\left|\frac{S_n-s_n}n\right|<c\right)=1,$$
其中 $S_n=X_1+\cdots+X_n,s_n=m_1+\cdots+m_n$.

注意，现在不需要同分布了，用 Chebyshev 可证。
大数定律的意义：随机变量和的均值收敛于均值的均值。
（应用中还是同分布居多，所以基本上都用中心极限）

## 统计

背背背！

**样本平均**：$\overline{X}$

- 期望：$\mu_\overline{X}=\mu$
- 方差：
  - 放回：$\sigma^2_\overline{X}=\sigma^2/n$
  - 不放回：$\sigma^2_\overline{X}=(\sigma^2/n)\times(N-n)/(N-1)$
    具体分布：
- 总体服从正态，样本量够大：$\overline{X}$ 的正规化服从单位正态。

**样本方差**：$S^2$ ，（以及 无偏 $\widehat{S}^2$）

- 期望：$\mu_{S^2}=\frac{n-1}{n}\sigma$, 不放回需要乘 $N/(N-1)$
  具体分布：
  设 $Z=\frac{nS^2}{\sigma^2}$，有：
- 若总体服从正态，样本量足够大，$Z$ 服从自由度为 $n-1$ 的卡方分布
  证明：利用 $\sum^{n}_{i=1}(X_i-\overline{X})^2=\sum^{n}_{i=1}X_i^2-n\overline{X}^2$，以及平均的分布。

**t检验**：$T=\frac{\overline{X}-\mu}{\widehat{S}/\sqrt{n}}=\frac{\overline{X}-\mu}{S/\sqrt{n-1}}$
即在样本平均的正规化中，使用样本的无偏方差 $\widehat{S}^2$ 估计总体方差，结论是 $T$ 服从自由度为 $n-1$ 的 $t$ 分布。注意，$\widehat{S}$ 是有偏的。
证明：设 $Y=\frac{\overline{X}-\mu}{\sigma/\sqrt{n}}$，即 $\overline{X}$ 的正规化，则 $T=\frac{Y}{\sqrt{Z/(n-1)}}$，由 $t$ 分布定义即证。

频率直方图的简化计算：设 $x_i=a+cu_i$
$$\overline{x}=a+\frac cn\sum fu:=a+c\overline{u},$$
$$s^2=c^2\left(\overline{u^2}-\overline{u}^2\right)=c^2\left[\frac{\sum fu^2}n-\left(\frac{\sum fu}n\right)^2\right]$$
有效估计：方差更小的估计量

**区间估计**：利用上述 $Y$，$Z$ 和 $T$。

- $Y$ 总体方差已知，样本量够大，通过正态分布估计总体**均值**
- $T$ 总体方差未知，样本较小，通过 $t$ 分布估计总体**均值**
- $Z$ 用样本方差，估计总体**方差**，通过卡方分布实现。（注意不对称）

**极大似然估计**：用于估计已知分布的总体，密度函数中出现的参数 $\theta$ 
设密度函数为 $f(x,\theta)$ ，一个样本的联合密度函数为：
$$L=f(x_1,\theta)f(x_2,\theta)\cdots f(x_n,\theta)$$
则取 $\frac{\partial L}{\partial \theta}=0$ 的 $\theta$ （是一个 $x_1,\ldots,x_n$ 的函数）为估计值。（对数求导）

正态分布的极大似然估计：均值为 $\overline{X}$，方差为 $S^2$（符合直觉）

**Bayes 估计**：
假设已知分布 $f(x,\theta)$ ，以及样本值，乘上先验 $g(\theta)$，得到联合分布 $h(x,\theta)$，然后求 $x$ 的边际分布 $m(x)$，使用条件概率公式得到后验分布 $\pi(\theta|x)$，然后取均值（也可以取其他统计量）作为 $\theta$ 的估计。

由于：
$$P(x\leq x_0)P(\theta\leq \theta_0|x\leq x_0)=P(\theta\leq \theta_0,x\leq x_0)$$
所以对应的密度函数：
$$ m(x)\pi(\theta|x)=h(x,\theta)=f(x,\theta)g(\theta)$$
实际上，可以不用求 $m(x)$，只需要对 $h$ 使用 $\theta$ 归一性条件即可。

- 二项式分布：与 Beta 分布对偶，
  - 先验为 $[0,1]$ 均匀分布（$\alpha=\beta=1$ 的 Beta 分布）：后验服从 $B(x+1,n-x+1)$，估计值为 $\frac{x+1}{n+2}$ 
  - 先验为 $B(\alpha,\beta)$：后验也是 Beta 分布，估计值为 $\frac{x+\alpha}{n+\alpha+\beta}$
- 正态分布：
  - 估计均值：假设均值也服从正态分布，则后验也是正态



## Syntax

```markdown
![Image 1](1.jpg) ![Image 2](2.jpg)
```

## Result

![Image 1](1.jpg) ![Image 2](2.jpg)

> Photo by [mymind](https://unsplash.com/@mymind) and [Luke Chesser](https://unsplash.com/@lukechesser) on [Unsplash](https://unsplash.com/)