<font size=6>Chaptcer 08 Advanced Counting Techniques 高级计数技术</font>

Part 01 Deeper Discussion About Recurrence Relations 递归关系的深入探讨

covering 8.1 ~ 8.2

------

# Applications of Recurrence Relations 递归关系的应用

跟DP里找状态转移方程比较类似，此处略去。

# Solving Linear Recurrence Relations 求解线性递归关系

## I. Terminologies 术语

- **linear**（**线性**）：即所有含未知量的项都是**一次**
- **homogeneous**（**齐次**）：所有未知量移动到左边后，右边为0
- **constant coefficients**（**常系数**）：系数为常数
- **degree**（**阶**）：$$a_n$$与前面多少项相关

## II. Solution 解法

> **基本思路**：
>
> 先求通解，再由初始条件（初值）求出定解
>
> *以下部分只讨论通解的求解*

![](../img/CH08/01_mindmap.png)

##### Characteristic Equation and Characteristic Roots 特征方程与特征根


$$
a_{n}=c_{1} a_{n-1}+c_{2} a_{n-2}+\cdots+c_{k} a_{n-k}
$$


对于上述递推关系，其**特征方程**为：
$$
r^{n}=c_{1} r^{n-1}+c_{2} r^{n-2}+\cdots+c_{k} r^{n-k}
$$
也即
$$
r^{k}-c_{1} r^{k-1}-c_{2} r^{k-2}-\cdots-c_{k-1} r-c_{k}=0
$$
其中 $$r$$ 就是此方程的**特征根**

> 背后的原理其实就是我们认为有一个初步的解的形态$$a_n=r^n$$，我们只需要在这个形态上按需调整即可。
>
> 之后的求解都是建立在这一认知之上的。

### 1. Homogeneous 齐次情况

#### 1.1 二阶（入门、特殊）

$$
a_{n}=c_{1} a_{n-1}+c_{2} a_{n-2}
$$

首先求出特征根$$r_1$$、$$r_2$$，它们满足：
$$
r^{2}-c_{1} r-c_{2}=0
$$
接下来分两种情况

##### 情况1  两个特征根不同

此情况最基本，其解为：
$$
a_{n}=\alpha_{1} r_{1}^{n}+\alpha_{2} r_{2}^{n}
$$
其中$$a_1$$、$$a_2$$为常数

> **原理**：
>
> $$a_n=r_1^n$$、$$a_n=r_2^n$$都满足$$a_{n}=c_{1} a_{n-1}+c_{2} a_{n-2}$$，由于是线性关系，因此它们的线性和也满足关系式

> **证明**：
>
> 1. $$a_n=\alpha_{1} r_{1}^{n}+\alpha_{2} r_{2}^{n}$$是解
> $$
> \begin{aligned} c_{1} a_{n-1}+c_{2} a_{n-2} &=c_{1}\left(\alpha_{1} r_{1}^{n-1}+\alpha_{2} r_{2}^{n-1}\right)+c_{2}\left(\alpha_{1} r_{1}^{n-2}+\alpha_{2} r_{2}^{n-2}\right) \\ &=\alpha_{1} r_{1}^{n-2}\left(c_{1} r_{1}+c_{2}\right)+\alpha_{2} r_{2}^{n-2}\left(c_{1} r_{2}+c_{2}\right) \\ &=\alpha_{1} r_{1}^{n-2} r_{1}^{2}+\alpha_{2} r_{2}^{n-2} r_{2}^{2} \\ &=\alpha_{1} r_{1}^{n}+\alpha_{2} r_{2}^{n} \\ &=a_{n} \end{aligned}
> $$
>
> 2. 给定初值后，解一定是$$a_{n}=\alpha_{1} r_{1}^{n}+\alpha_{2} r_{2}^{n}$$（或者说每个解都有这种形式）
>
> 等价于说明$$\alpha_1$$、$$\alpha_2$$唯一确定
>
> 假设初始条件为$$a_{0}=C_{0}, a_{1}=c_{1}$$，则：
> $$
> \begin{array}{l}{a_{0}=C_{0}=\alpha_{1}+\alpha_{2}} \\ {a_{1}=C_{1}=\alpha_{1} r_{1}+\alpha_{2} r_{2}}\end{array}
> $$
>
> 解得：$$\alpha_{1}=\frac{C_{1}-C_{0} r_{2}}{r_{1}-r_{2}}, \alpha_{2}=\frac{C_{0} r_{1}-C_{1}}{r_{1}-r_{2}}$$
>
> 在这样的一组$$\alpha_1$$、$$\alpha_2$$之下，所有$$\alpha_{1} r_{1}^{n}+\alpha_{2} r_{2}^{n}$$满足要求，由于解的唯一性可知$$a_{n}=\alpha_{1} r_{1}^{n}+\alpha_{2} r_{2}^{n}$$

注意到$$\alpha_1$$、$$\alpha_2$$的值依赖于$$r_1\neq r_2$$，由此引出情况2

##### 情况2  两个特征根相同

记$$r_0=r_1=r_2$$，则解为：
$$
a_{n}=\alpha_{1} r_{0}^{n}+\alpha_{2} n r_{0}^{n}
$$

#### 1.2 高阶（一般化、推广）

##### 情况1  无重根

$$
a_{n}=\alpha_{1} r_{1}^{n}+\alpha_{2} r_{2}^{n}+\cdots+\alpha_{k} r_{k}^{n}
$$

##### 情况2  有重根

设有$$t$$个不等根$$r_{1}, r_{2}, \cdots, r_{t}$$，其重数分别为$$m_{1},  m_{2}, \dots, m_{t}$$ ($$m_{i} \geqslant 1, i = 1,2,...,t$$ 且$$m_{1}+m_{2}+\dots+m_{t}=k$$)，则解为：
$$
\begin{aligned} a_{n}=&\left(\alpha_{1,0}+\alpha_{1,1} n+\cdots+\alpha_{1, m_{1}-1} n^{m_{1}-1}\right) r_{1}^{n} \\ &+\left(\alpha_{2,0}+\alpha_{2,1} n+\cdots+\alpha_{2, m_{2}-1} n^{m_{2}-1}\right) r_{2}^{n} \\ &+\cdots+\left(\alpha_{t, 0}+\alpha_{t, 1} n+\cdots+\alpha_{t, m_{t}-1} n^{m_{t}-1}\right) r_{t}^{n} \end{aligned}
$$

### 2. Nonhomogeneous 非齐次情况

> **解法**：
>
> 化归，转化为齐次情况（*与线性代数中对付非齐次方程组的思想完全一致*）

#### 2.1  基本思想

对于**常系数线性非齐次递推关系** (**linear nonhomogeneous recurrence relation with constant coefficients**)
$$
a_{n}=c_{1} a_{n-1}+c_{2} a_{n-2}+\cdots+c_{k} a_{n-k}+F(n)
$$
我们假设自己已经“求得”一个**特解** (**particular solution**) $$\left\{a_{n}^{(p)}\right\}$$

同时，它也存在一个**相伴的齐次递推关系** (**associated homogeneous recurrence relation**)
$$
a_{n}=c_{1} a_{n-1}+c_{2} a_{n-2}+\cdots+c_{k} a_{n-k}
$$
利用之前的知识我们已经可以求出其解$$\left\{a_{n}^{(h)}\right\}$$

那么对于这个非齐次的递推关系，我们有通解


$$
\left\{a_{n}^{(p)}+a_{n}^{(h)}\right\}
$$

> **证明**：
>
> 假设有一个特解$$\left\{a_{n}^{(p)}\right\}$$以及通解的某种形式$$\left\{b_{n}\right\}$$
> $$
> a_{n}^{(p)}=c_{1} a_{n-1}^{(p)}+c_{2} a_{n-2}^{(p)}+\dots+c_{k} a_{n-k}^{(p)}+F(n)
> $$
>
> $$
> b_{n}=c_{1} b_{n-1}+c_{2} b_{n-2}+\cdots+c_{k} b_{n-k}+F(n)
> $$
>
> 做差：
> $$
> b_{n}-a_{n}^{(p)}=c_{1}\left(b_{n-1}-a_{n-1}^{(p)}\right)+c_{2}\left(b_{n-2}-a_{n-2}^{(p)}\right)+\cdots+c_{k}\left(b_{n-k}-a_{n-k}^{(p)}\right)
> $$
> 由此注意到$$\left\{b_{n}-a_{n}^{(p)}\right\}$$是相伴的齐次递推关系的通解，即$$\left\{a_{n}^{(h)}\right\}$$
>
> 由解的唯一性知：$$b_{n}-a_{n}^{(p)} = a_{n}^{(h)}$$，即：
> $$
> b_{n}=a_{n}^{(p)}+a_{n}^{(h)}
> $$

现在问题转化为了**齐次通解 + 非齐次特解**。齐次通解已经可求；对于简单的递推关系，非齐次特解可以通过拼凑获得，但是复杂的式子特解并不容易直接看出，由此引出下一个话题——**特解的求解**。

#### 2.2 求特解

研究$$F(n)$$
$$
F(n)=\left(b_{t} n^{t}+b_{t-1} n^{t-1}+\cdots+b_{1} n+b_{0}\right) s^{n}
$$
此时又分两种情况：

##### 情况1  s不是相伴齐次递推关系的根

此时有如下形式的特解：
$$
\left(p_{t} n^{t}+p_{t-1} n^{t-1}+\cdots+p_{1} n+p_{0}\right) s^{n}
$$

##### 情况2  s是相伴齐次递推关系的根

假设此根的重数为$$m$$，则有如下形式的特解：
$$
n^{m}\left(p_{t} n^{t}+p_{t-1} n^{t-1}+\cdots+p_{1} n+p_{0}\right) s^{n}
$$