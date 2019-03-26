<font size=6> Chaptcer 02 Basic Structures 基本结构</font>

Part 03 Cardinality of Sets

Covering 2.5

------

# Cardinality of Sets 集合的基数

[TOC]

## Relation between Sets and Mapping 集合与映射的关系

The cardinality of a set A is equal to the cardinality of a set B, denoted | A | = | B |, iff **there exists a bijection from A to B**.

If **there is an injection from A to B**, the cardinality of A is less than or the same as the cardinality of B and we write  |A| ≤ |B|. When |A| ≤ |B| and A and B have different cardinality, we say that the cardinality of A is less than the cardinality of B and write |A| < |B|.

## Countable Sets 可数集

A set that is either **finite** *or* has the **same cardinality as the set of positive integers** called **countable**（**可数的**）

A set that is not countable is called **uncountable**（**不可数的**）

When an infinite set S is countable, we denote the cardinality of S by $\aleph_0$ (**aleph null**（**“阿里夫零”**）)

If |A| = | Z+ |, the set A is **countably infinite**（**可数无限**）

> Below we will list some examples of countably infinite sets

### Hilbert’s Grand Hotel 希尔伯特大酒店

Hilbert’s Grand Hotel （希尔伯特大酒店）是一个很有意思的问题，它有很多细分小问题，每个小问题的证明思想都能被用于其他问题的证明，可谓思想的游戏。篇幅有限不过多介绍，有兴趣可以参看《离散数学及其应用》的例题和习题。

### Show that a set is countable 可数性证明

> **Key**: ***Find a bijection!***

#### Method 1. Linear Mapping 简单的线性映射

##### e.g.1 The set E of even positive integers 偶数集

Let f(x) = 2x. Then,  f is a bijection from $Z^+$ to $E$

| **x**    | **1** | **2** | **3** | **4** | **……** |
| -------- | ----- | ----- | ----- | ----- | ------ |
| **f(x)** | **2** | **4** | **6** | **8** | **……** |

> The numbers of positive even integers is the same as positive integers
>
> E is a proper subset of $Z^+$, but $|E|=|Z^+|$

##### e.g.2 The set of integers Z 整数集

$Z=\{0,1,-1,2,-2,...\}$

$$f(n)=
\begin{cases}
-(n-1)/2& \text{n is odd}\\
n/2& \text{n is even}\\
\end{cases}​$$

#### Method 2. Cantor Table 利用Cantor表构造映射

##### e.g.3 The set of positive rational numbers $Q^+$ 有理数集

$∀x∈Q^+,x=p/q,\ p,q∈Z^+$

Let $S=\{(p,q)|p,q∈Z^+\}=Z^+×Z^+$

###### Step 1 Prove $|Q^+|≤|S|$

$r=\frac{p}{q}∈Q^+$

$\frac{p}{q}→(p,q)$ is injective

Hence, $|Q^+|≤|S|$

###### Step 2 Prove $|S|=|Z^+|$

Cantor Table

|       | **1** | **2** | **3** | **…** | **p** | **…** |
| :---: | :---: | :---: | :---: | :---: | :---: | :---: |
| **1** | (1,1) | (2,1) | (3,1) |   …   | (p,1) |   …   |
| **2** | (1,2) | (2,2) | (3,2) |   …   | (p,2) |   …   |
| **3** | (1,3) | (2,3) | (3,3) |   …   | (p,3) |   …   |
| **…** |   …   |   …   |   …   |   …   |   …   |   …   |
| **q** | (1,q) | (2,q) | (3,q) |   …   | (p,q) |   …   |
| **…** |   …   |   …   |   …   |   …   |   …   |   …   |

for any pair (p,q), $n=1+2+3+...+(p+q-2)+q=\frac{(p+q-2)(p+q-1)}{2}+q$

this mapping is invertable, which means we found a **bijection**

> An infinite set is countable iff it is possible to list all the elements of the set in a sequence

###### Step 3 Prove $|Z^+|≤|Q^+|$

$∵Z^+⊆Q^+$

$∴|Z^+|≤|Q^+|$

All in all, $|Q^+|=|S|=|Z^+|$

> **Note**:
>
> The set of **all rational numbers Q**, positive and negative, is also countable infinite. 

##### e.g.4 Show that the set of the real numbers with decimal representations consisting of all 1s is countable

We can arrange the numbers in a 2-dimensional table as follows:

|       |       **1**       | **2**  |  **3**   |   **4**   |   **5**   | **…** |
| :---: | :---------------: | :----: | :------: | :-------: | :-------: | :---: |
| **1** |   $.\overline1$   |  $.1$  |  $.11$   |  $.111$   |  $.1111$  |   …   |
| **2** |  $1.\overline1$   |  $1$   |  $1.1$   |  $1.11$   |  $1.111$  |   …   |
| **3** |  $11.\overline1$  |  $11$  |  $11.1$  |  $11.11$  | $11.111$  |   …   |
| **4** | $111.\overline1$  | $111$  | $111.1$  | $111.11$  | $111.111$ |   …   |
| **5** | $1111.\overline1$ | $1111$ | $1111.1$ | $1111.11$ | $1111.111$ |   …   |
| **…** |         …         |   …    |    …     |     …     |     …     |       |

Then number these numbers as before, like 1 to $.\overline1$, 2 to $.1$, 3 to $1.\overline1$, 4 to $.11$, 5 to $1$……

Thus, we found a bijection!

Q.E.D.

#### Method 3. Define an order for strings 字符串的“运算符重载”

##### e.g.5 Show that the set of finite strings S over a finite alphabet A is countably infinite

Assume an alphabetical ordering of symbols in A. Show that the strings can be listed in a sequence. First list

1. All the strings of length 0 in alphabetical order.
2. Then all the strings of length 1 in lexicographic (as in a dictionary) order.
3. Then all the strings of length 2 in lexicographic order. 
4. And so on.

This implies a bijection from N to S and hence it is a countably infinite set.

##### e.g.6 Show that the set of all Java programs is countable

A computer program written in a programming language can be thought of as a string of symbols from a finite alphabet

Hence, using the conclusion form the last example, we know this statement is true.

### The properties of the countable sets 可数集性质

1. No infinite set has a smaller cardinality than a countable set

2. The union of two countable sets is countable

   > **Proof**:
   >
   > Suppose that A and B are both countable sets. Without loss of generality, we can assume that A and B are disjoint.
   >
   > - Case 1: A and B are finite. (Obviously…)
   > - Case 2: A is infinite and B is finite. (Obviously…)
   > - Case 3: A and B are both countably infinite. (We can list their elements as $a_1,a_2,a_3,...,a_n,...$ and $b_1,b_2,b_3,...,b_n,...$ respectively. By alternating terms of these two sequences, we can list the elements of A∪B in the infinite sequence $a_1,b_1,a_2,b_2,a_3,b_3,...,a_n,b_n,...$, hence A∪B is countably infinite)
   >
   > Q.E.D.

3. The union of finite number of countable sets is countable

4. The union of a countable number of countable sets is countable

## Uncountable Sets 不可数集

> We mainly talks about how to prove a set is uncountable

### Examples of Proof 证明举例

#### Method 1. Cantor Diagonalization Argument 康托尔对角线法

##### e.g.1 The set of real numbers between 0 and 1 is uncountable

$A=\{x|x∈(0,1)∧x∈R\}$

###### Step 1 Prove $|Z^+|≤|A|$

$B=\{\frac{1}{n+1}|n∈Z^+\}$

$∵|B|=|Z^+|$

and $B∈A$

$∴|Z^+|≤|A|$

###### Step 2 Prove $|Z^+|≠|A|$

Assume A is countable, then let $A=\{r_1,r_2,r_3,...,r_n,...\}$

Represent each real number in the list using its **decimal expansion**（**十进制表示**）

> List:
>
> - $r_1=0.d_{11}d_{12}d_{13}d_{14}d_{15}d_{16}...$
> - $r_2=0.d_{21}d_{22}d_{23}d_{24}d_{25}d_{26}...$
> - $r_3=0.d_{31}d_{32}d_{33}d_{34}d_{35}d_{36}...$
>
> - …

**Now construct a new number x**

$x=0.x_{1}x_{2}x_{3}x_{4}x_{5}x_{6}x_{7}...$

$$x_i=
\begin{cases}
6& d_{ii}≠6\\
7& d_{ii}=6\\
\end{cases}$$

>  明白“对角线法”的意思了吗？简而言之就是将对角线上的元素$d_{ii}$换掉

**Then x is not equal to any number in the list**

So whatever sequence we construct, there is always at least a new number that is not included!

Hence, no such list can exist and hence the interval (0,1) is uncountable

##### e.g.2 Show that the set of the real numbers with decimal representations consisting of all 1s or 9s is uncountable

Denote the set as A, assume A is countable, then let $A=\{r_1,r_2,r_3,...,r_n,...\}$

Represent each real number in the list using its **decimal expansion**（**十进制表示**）

> List:
>
> - $r_1=0.d_{11}d_{12}d_{13}d_{14}d_{15}d_{16}...$
> - $r_2=0.d_{21}d_{22}d_{23}d_{24}d_{25}d_{26}...$
> - $r_3=0.d_{31}d_{32}d_{33}d_{34}d_{35}d_{36}...$
>
> - …

**Now construct a new number x**

$x=0.x_{1}x_{2}x_{3}x_{4}x_{5}x_{6}x_{7}...$

$$x_i=
\begin{cases}
1& d_{ii}=9\\
9& d_{ii}=1\or d_{ii}=0\\
\end{cases}$$

Then x is not equal to any number in the list

So whatever sequence we construct, there is always at least a new number that is not included!

Hence, no such list can exist and hence A is uncountable

> 这题与可数集的例题4很像，但是一个可数一个不可数，本质原因在于例题4中的基数为$\aleph_0$，而这里增加了一个9后，基数变为了$2^{\aleph_0}$，而这个数是不可数的，后面会给它一个记号c或者$\aleph_1$

#### Method 2. Find a bijection to an uncountable set 找出到已知不可数集的双射

##### e.g.3 The set of real numbers has the same cardinality as the set (0,1)

 $f(x)=tan(x)$

f(x) is a bijection from $(-\frac{\pi}{2},\frac{\pi}{2})$ to R

$∵|(-\frac{\pi}{2},\frac{\pi}{2})|=|(0,1)|$

$∴|R|=|(0,1)|=c$

> $c=2^{\aleph_0}$

#### Method 3. Schrőder-Bernstein Theorem

**Schrőder-Bernstein Theorem** : If A and B are sets with $|A|≤|B|$ and $|B|≤|A|$ then $|B|=|A|$. 

In other words, if there are one-to-one functions f from A to B and g from B to A, then there is a one to –one correspondence between A and B.

> 有点像夹逼定理……

##### e.g.4 Show that the cardinality of [0,1] is c

$A=[0,1]=\{x|x∈R,0≤x≤1\}$

$B=(0,1)=\{x|x∈R,0<x<1\}$

$B⊆A⇒|B|≤|A|$

Let $g(x)=\frac{1}{2}x+\frac{1}{4},x∈[0,1]$

Hence, g(x) is a bijection from [0,1] to $[\frac{1}{4}, \frac{3}{4}]​$

and $[\frac{1}{4}, \frac{3}{4}]\subset (0,1)​$

Thus $|A|≤|B|​$

$∴|A|=|B|=c​$

### [Summary 小总结] How to Prove $|A|≤|B|$

通过以上几道例题可以发现，$|A|≤|B|$的证明经常被用到，这里总结证明此式子的三大方法

#### Method 1. Find an injective 找到一个单射

> in e.g.1 Step1
>
> Prove $|Z^+|≤|A|$

#### Method 2. Prove $A⊆B$

> in e.g.3
>
> $A=[0,1]=\{x|x∈R,0≤x≤1\}$
>
> $B=(0,1)=\{x|x∈R,0<x<1\}$
>
> $B⊆A⇒|B|≤|A|$

#### Method 3. Prove $|A|=|C|,C\subseteq B$ 在B中找到与A基数相同的子集

> in e.g.3
>
> $|A|=[\frac{1}{4}, \frac{3}{4}]$ and $[\frac{1}{4}, \frac{3}{4}]\subset (0,1)$
>
> Thus $|A|≤|B|$

## Applications 理论应用

### Computability 可计算性

We say that a function is **computable**（**可计算的**） if there is a computer program in some programming language that finds the values of this function. If a function is not computable we say it is **uncomputable** （**不可计算的**）

To show that there are uncomputable functions, we need to establish two results. 

First, we need to show that the set of all computer programs in any particular programming language is countable. (Proved before)

Next, we show that there are uncountably many different functions from a particular countably infinite set to itself.

**So now, there are only a countable number of computer programs. Consequently, there are only a countable number of computable functions. However, there are an uncountable number of functions, so not all functions are computable.**

### The Continuum Hypothesis 连续统假设

> In brief, $\aleph_0=|Z^+|<|P(Z^+)|=|R|=\aleph_1$
>

#### 1. Show that $|P(Z^+)|=|R|$

- First, for any $S\in P(Z^+)$, there is a real number r in (0,1) whose **decimal** expansion is

  $r=0.d_1d_2d_3...$

  $$d_i=
  \begin{cases}
  6& i\in S\\
  7& i \notin S\\
  \end{cases}$$

  Then we have constructed a one-to-one function from $P(Z^+)$ to (0, 1)

- Second, for any r in (0,1), it has a **binary** expansion $r=0.d_1d_2d_3...$ 

  Then there is a set $\{i|d_i=1\}$

  So we constructed a one-to-one function from (0, 1) to $P(Z^+)$

  > **P.S.**
  >
  > In order that our function from (0, 1) to $P(Z^+)$ to be well-defined, we must choose which of two equivalent expressions to represent numbers thath ave terminating binary expansions to use (for example, $0.10010\overline1$ versus $0.10011\overline0$); we can decide to always use the terminating form, the one ending in all 0’s.)

- By the Schrőder-Bernstein theorem we have $|P(Z^+)|=|(0,1)|=|R|=c$
- Hence, $c=2^{\aleph_0}$

#### 2. Show that $|Z^+|<|P(Z^+)|$

> **Cantor’s theorem**
>
> The cardinality of the power set of an arbitrary set has a greater cardinality than the original arbitrary set
>
> > **Proof**:
> >
> > ***Step 1***
> >
> > >  We convert this problem into showing that ***there does not exist an onto function f from S to P(S)***
> >
> > Suppose that f is a function from S to P(S). We must show that f is not onto.
> >
> > Let $T=\{s\in S|s\notin f(s)\}$. Although T is in the codomian of f, which is P(S), we will show that T is not in the range of f.
> >
> > If it were, then we would have f(t) = T for some $t\in S$
> >
> > 1. Suppose that $t\in T$, then according to the definition of T, $t\notin f(t)$, thus, $t\notin T$, which is a contradiction
> > 2. Suppose that $t\notin T$, then $t\notin f(t)$, then t follows the definition of T, so $t\in T$, which is again a contradiction
> >
> > Hence, f is not onto. 
> >
> > In other words, ***there does not exist an onto function f from S to P(S)***
> >
> > ***Step 2***
> >
> > The function sending x to {x} for each $x\in S$ is a one-to-one function from S to P(S), hence $|S|\leq|P(S)|$
> >
> > ***Step 3***
> >
> > Since there is no onto from S to P(S), then there is no one-to-one correspondence, which implies that $|S|\neq|P(S)|$
> >
> > ***All in All***
> >
> > $|S|<|P(S)|$

Hence, by the Cantor’s theorem, $|Z^+|<|P(Z^+)|$, which can be expressed as $\aleph_0<2^{\aleph_0}=c$

#### 3. The Hypothesis

The famous continuum hypothesis asserts that there is no cardinal number X between $\aleph_0$ and c

It tells us that the smallest infinite cardinal numbers forms an infinite sequence $\aleph_0,\aleph_1,\aleph_2,\aleph_3,...$

There are no other cardinal numbers between $\aleph_n$ and $\aleph_{n+1}$, also $\aleph_ {n+1}$is the cardinal number of the power set of a set S, whose own cardinal is $\aleph_n$

When we talk about $\aleph_0$ and $\aleph_1$, the continuum hypothesis (CH) asserts that there is no cardinal number （基数） *a* such that $\aleph_0<a<\aleph_1$

Hence, $c=2^{\aleph_0}=\aleph_1$