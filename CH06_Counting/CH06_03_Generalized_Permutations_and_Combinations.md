<font size=6>Chaptcer 06 Counting 计数</font>

Part 03 Generalized Permutations and Combinations 排列组合推广

covering 6.5

------

> 所谓推广，主要是两个方面——重复的出现以及物体盒子模型。

# I. Repetition 重复

|                          |  **Without Repetition （限重）**  |            **With Repetition （有重）**             |
| :----------------------: | :-------------------------------: | :-------------------------------------------------: |
| **Permutation （排列）** |  $$P(n,r)=\frac{n !}{(n-r) !}$$   |                       $$n^r$$                       |
| **Combination （组合）** | $$C(n,r)=\frac{n !}{r !(n-r) !}$$ | $$H^n_r=C(n+r-1,n-1)=\frac{(n+r-1) !}{r !(n-1) !}$$ |

## Combination with Repetition 有重组合

$$H^n_r=\frac{(n+r-1) !}{r !(n-1) !}$$

指用n种充分供应对象中填充r个位置

### Proof 证明方法

插板法

### Example 例子

> How many solutions are there to the inequation？
> 
> $$x_{1}+x_{2}+x_{3}+x_{4} \leq 16$$

We can introduce an auxiliary（辅助的） variable $$x_5$$ so that

$$x_{1}+x_{2}+x_{3}+x_{4}+x_{5}=16$$

$$H_{5}^{16}=C(5-1+16,16)=C(20,16)=C(20,4)$$



# II. Object & Box Model 物体盒子模型

> Distinguishable & Indistinguishable 可区分性&不可区分性

## Lemma: Permutations with Indistinguishable Objects 引理：具有不可区分物体集合的排列

The number of different permutations of $$n$$ objects, where there are $$n_1$$ indistinguishable objects of type 1, $$n_2$$ indistinguishable objects of type 2, . . . , and $$n_k$$ indistinguishable objects of type k, is $$\frac{n !}{n_{1} ! n_{2} ! \cdots n_{k} !}$$

### Proof 证明方法

$$
\begin{array}{l}{C\left(n, n_{1}\right) C\left(n-n_{1}, n_{2}\right) \cdots C\left(n-n_{1}-\cdots-n_{k-1}, n_{k}\right)} \\ {=\frac{n !}{n_{1} !\left(n-n_{1}\right) !} \frac{\left(n-n_{1}\right) !}{n_{2} !\left(n-n_{1}-n_{2}\right) !} \cdot \cdots \frac{\left(n-n_{1}-\cdots-n_{k-1}\right) !}{n_{k} ! 0 !}} \\ {=\frac{n !}{n_{1} ! n_{2} ! \cdots n_{k} !}}\end{array}
$$

### Example 例子

How many different strings can be made by reordering the letters of the word SUCCESS?

> This word contains three Ss, two Cs, one U, and one E.

$$
\begin{aligned} C(7,3) C(4,2) C(2,1) C(1,1) &=\frac{7 !}{3 ! 4 !} \cdot \frac{4 !}{2 ! 2 !} \cdot \frac{2 !}{1 ! 1 !} \cdot \frac{1 !}{1 ! 0 !} \\ &=\frac{7 !}{3 ! 2 ! 1 ! 1 !} \\ &=420 \end{aligned}
$$

## [Model I] Distinguishable Objects and Distinguishable Boxes 可辨物体与可辨盒子

The number of ways to distribute $$n$$ distinguishable objects into k distinguishable boxes so that $$n_i$$ objects are placed into box $$i$$, $$i = 1, 2, . . . , k$$, equals $$\frac{n !}{n_{1} ! n_{2} ! \cdots n_{k} !}$$

### Analysis 分析

这个公式与引理中的公式一样，因为它们本质上说的是同一个事情

Distributing n distinguishable objects into boxes numbered from 1 to n is completely determined by assigning a box number (from 1 to k ) to each object, which leads us to a sequence of box numbers $$a_1,a_2,...,a_n$$, where $$a_i$$ is the box into which object $$i$$ goes. Since we want $$n_i$$ objects to go into box $$i$$, this sequence must contain $$n_i$$ copies of the number $$i$$ (for each $$i$$ from 1 to $$k$$ ). This is precisely a permutation of $$n$$ objects with $$n_i$$ indistinguishable objects of type $$i$$.

### Example 例子

How many ways are there to distribute hands of 5 cards to each of four players from the standard deck of 52 cards?
$$
\begin{aligned} C(52,5) C(47,5) C(42,5) C(37,5) &=\frac{52 !}{47 ! 5 !} \cdot \frac{47 !}{42 ! 5 !} \cdot \frac{42 !}{37 ! 5 !} \cdot \frac{37 !}{32 ! 5 !} \\ &=\frac{52 !}{5 ! 5 ! 5 ! 5 ! 32 !} \end{aligned}
$$

## [Model II] Indistinguishable Objects and Distinguishable Boxes 不可辨物体与可辨盒子

这种情况等价于$$H^n_r=C(n+r-1,n-1)=\frac{(n+r-1) !}{r !(n-1) !}$$，因为这提示就是一个分堆问题

### Example 例子

How many ways are there to place 10 indistinguishable balls into eight distinguishable bins?

$$C(8+10-1,10)=C(17,10)=\frac{17 !}{10 ! 7 !}=19448$$

## [Model III] Distinguishable Objects and Indistinguishable Boxes 可辨物体与不可辨盒子

### Stirling numbers of the second kind 第二类斯特林数

the number of ways to distribute $$n$$ distinguishable objects into $$j$$ indistinguishable boxes so that no boxes is empty

#### Notation 记号

$$S(n,j)$$

#### Property & Recursive Definition 性质&递归定义 

1. $$S(r, 1)=S(r, r)=1 \quad(\mathrm{r} \geq 1)$$
2. $$S(r, 2)=2^{r-1}-1$$
3. $$S(r, r-1)=C(r, 2)$$
4. $$S(r+1, n)=S(r, n-1)+nS(r, n)$$

> 性质1~3都很好说明，只简单谈谈性质4
>
> 当我们尝试分配$$(r+1)$$个物体时，可以先将某一个物体拿出来讨论
>
> 1. 当这一个物体单独放进某一个箱子时，余下的$$r$$个物体将被放进$$(n-1)$$个箱子，这种情况下可行的方案数为$$S(r, n-1)$$
> 2. 如果此物体不单独成堆，就需要在余下的$$r$$个物体将被放进$$n$$个箱子之后，在这$$n$$个箱子之中挑选一个放入，根据乘法原则这种情况下的可行方案数为$$n\times S(r, n)$$
>
> 求和即可

#### Formula 公式

$$
S(n, j)=\frac{1}{j !} \sum_{i=0}^{j-1}(-1)^{i} \left( \begin{array}{l}{j} \\ {i}\end{array}\right)(j-i)^{n}
$$

#### Note 说明

1. $$S(n,j)$$ is the number of ways to partition the set with $$n$$ elements into $$j$$ nonempty and disjoint subsets

2. $$S(n,j)j!$$ is the number of ways to distribute $$n$$ distinguishable objects into $$j$$ distinguishable boxes so that no boxes is empty

   > The number of **onto functions** from a set with $$n$$ elements to a set with $$j$$ elements is $$S(n, j) j !=\left(\sum_{i=0}^{j-1}(-1)^{i} C_{j}^{i}(j-i)^{n}\right)$$

3. The number of ways to place $$n$$ distinguishable objects into $$k$$ indistinguishable boxes is $$\sum_{j=1}^{k} S(n, j)=\sum_{j=1}^{k}\left(\left(\sum_{i=0}^{j-1}(-1)^{i} C_{j}^{i}(j-i)^{n}\right) / j !\right)$$

### Example 例子

How many ways are there to put four different employees into three indistinguishable offices, when each office can contain any number of employees?

#### Solution 1

Enumeration 枚举

- {{A,B,C,D}}

- {{A,B,C},{D}},  {{A,B,D},{C}},  {{A,C,D},{B}},  {{B,C,D},{A}}
- {{A,B},{C,D}},  {{A,C},{B,D}},  {{A,D},{B,C}}
- {{A,B},{C},{D}},  {{A,C},{B},{D}},  {{A,D},{B},{C}},  {{B,C},{A},{D}},  {{B,D}},{A},{C}},  {{C,D},{A},{B}}

Total: 14 ways

#### Solution 2

S(4,1) + S(4,2) + S(4,3) = 1 + 7 + 6 = 14

## [Model IV] Indistinguishable Objects and Indistinguishable Boxes 不可辨物体与不可辨盒子

等价于正整数划分

> $$n$$个物体分到$$j$$个盒子里，等价于将正整数$$n$$划分成$$j$$个正整数

***没有巧妙方法，只能枚举！！！***

### Example 例子

How many ways are there to pack six copies of the same book into four identical boxes, where a box can contain as many as six books?

6
5, 1
4, 2
4, 1, 1
3, 3
3, 2, 1
3, 1, 1, 1
2, 2, 2
2, 2, 1, 1

Total: 9 ways