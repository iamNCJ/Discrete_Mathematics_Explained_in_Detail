<font size=6> Chaptcer 05 Induction and Recursion 归纳与递归</font>

Part 01 Induction

covering 5.1~5.2

------

# Mathematical Induction 数学归纳法

## Framework 基本框架

Prove $$\forall nP(n)$$ by mathematical induction:

1. **Basis step** : Establish P(1)

2. **Inductive step** : Prove that $$P(k)\to P(k+1) \text{for}\ k\geq1$$

- **Conclusion**:  $$\forall nP(n)$$, where the domain is the set of positive integers 

Express this in the proposition form:

$$P(1)\wedge\forall k(P(k)\to P(k+1))\to\forall nP(n)$$

This is the (first) principle of Mathematical Induction, and it also has the following form
$$P(1)\\\underline{\forall k(P(k)\to P(k+1))}\\\therefore\forall nP(n)$$

## The Validity of Mathematical Induction 数学归纳法的有效性

The validity of mathematical induction follows from **the well-ordering property**（**良序性公理**） for the set of positive integers.

## the Well-Ordering Property 良序性公理

A set S is well ordered  if every nonempty subset of S has a least element.

For example, 

1. N is well ordered

2. Z is not well ordered under the $$\leq$$ relation (Z has no smallest element).

3. (0, 1) is not well ordered since (0,1) does not have a least element. 

**The well-ordering property** : Every nonempty set of nonnegative integers has a least element. 

### Proofs Using the Well-ordering property

#### e.g.1

Use the well-ordering property to prove the division algorithm. The division algorithm states that if a is an integer and d  is a positive integer, then there are unique integers q and r, with $$0\leq r<d$$ such that $$a=dq+r$$.

> **The existence part**
>
> Let S be the set of nonnegative integers of the form a-dq, where q is an integer. This set is nonempty.
>
> By the well-ordering property, S has a least element r=a-dq0.
>
> The integer r is nonnegative. It is also the case that r<d. If it were not, then there would be a smaller nonnegative element in S, namely, $$s=a-d(q_0+1)$$.
>
> Consequently, there exist integers q and r with 0≤r<d.

#### e.g.2

In a round-robin tournament every player plays every other player exactly once and each match has a winner and loser. We say that the players $$p_1,p_2,…,p_m$$ form a cycle if $$p_1$$ beats $$p_2$$, $$p_2$$ beats $$p_3$$, …, $$p_{m-1}$$ beats $$p_m$$, and $$p_m$$ beats $$p_1$$.
Using the well-ordering principle to show that if there is a cycle of length m ($$m\geq 3$$) among the players in a round-robin tournament, there must be a cycle of three of these players

> **Solution**
>
> We assume that there is no cycle of three players. Because there is at least one cycle in the round-robin tournament, the set of all positive integers n for which there is a cycle of length n is nonempty. By the well-ordering property, this set of positive integers has a least element k, which by assumption must be greater than three. Consequently, there exists a cycle of players $$p_1,p_2,…,p_k$$ and no shorter cycle exists.
>
> Because there is no cycle of three players, we know that k > 3. Consider the first three elements of this cycle, $$p_1$$, $$p_2$$, and $$p_3$$. There are two possible outcomes of the match between $$p_1$$ and $$p_3$$. 
>
> 1. If $$p_3$$ beats $$p_1$$, it follows that $$p_1$$, $$p_2$$, $$p_3$$ is a cycle of length three, contradicting our assumption that there is no cycle of three players. 
> 2. If it is the case that $$p_1$$ beats $$p_3$$, this means that we can omit $$p_2$$ from the cycle $$p_1$$, $$p_2$$, $$p_3$$, . . . , $$p_k$$ to obtain the cycle $$p_1,p_3,p_4,...,p_k$$ of length k − 1, contradicting the assumption that the smallest cycle has length k. 
> 
> - We conclude that there must be a cycle of length three.

## Why Mathematical Induction is Valid

Proof:

Assume that there is at least one positive integer for which *P*(*n*) is false.

*S*: the set of positive integers for which *P*(*n*) is false.

Then *S* is nonempty.

By the well-ordering property, *S* has a least element, which will be denoted by *m*.

Then $$m\ne1$$, *m*-1 is a positive integer. *m-1* is not in *S.* So *P*(*m* -1) is true.

Since the implication $$P(m-1)\to P(m)$$ is also true, *P*(*m*) must be true. 

By contradiction, $$\forall nP(n)$$ 

## The Good and Bad of Mathematical Induction

### The Good

- can be used to prove a conjecture once it is has been made and is true

### The Bad

- Proofs do not provide insights as to why theorems are true

  > You can prove a theorem by M.I. even if you do not have the slightest idea why it is true!

- Cannot be used to find new theorems

## More General Form 广义形式

$$\forall n\geq b(P(n))$$

> The usage only differs at the basic step, we need to establish **P(b)** here!

# Strong Induction 强归纳法

## Framework 基本框架

1. **Basis Step**: We verify that the proposition P(1) is true.
2. **Inductive Step**: We show that the conditional statement $$[P(1)\wedge P(2)\wedge...\wedge P(k)]\to P(k+1)$$ is true for all positive integers k.

- **Conclusion**: $$\forall n\geq n_0P(n)$$

This is also the second principle of Mathematical Induction

$$(P(n_0)\wedge\forall k\geq n_0(P(n_0)\wedge P(n_0+1)\wedge...\wedge P(k)\to P(k+1)))\to\forall n\geq n_0(P(n))$$

# Comparison Between M.I and S.I 两种归纳法的对比

Take a problem as an example.

Prove that every amount of postage of 12 cents or more can be formed using just 4-cent and 5-cent stamps

|     Method     |                    Mathematical Induction                    |                       Strong Induction                       |
| :------------: | :----------------------------------------------------------: | :----------------------------------------------------------: |
|   Basis Step   | P(12) is true because postage of 12 cents can be formed using three 4-cent stamps |             P(12), P(13), P(14), and P(15) hold              |
| Inductive Step | The inductive hypothesis P(k) for any positive integer k.Then to show P(k + 1) where k ≥ 12, we consider two cases a) <br>a) If at least one 4-cent stamp has been used, then a 4-cent stamp can be replaced with a 5-cent stamp to yield a total of k + 1 cents.<br>b)Otherwise, no  4-cent stamp have been used and at least three 5-cent stamps were used. Three 5-cent stamps can be replaced by four 4-cent stamps to yield a total of k + 1 cents. | Assume that P(j) is true for all positive integers j with 12 ≤ j ≤ k, where k ≥ 15. Show that P(k+1) is true under the assumption.<br>Using the inductive hypothesis, $$P(k-3)$$ holds since k − 3 ≥ 12.  To form postage of  k + 1 cents, add a 4-cent stamp to the postage for k − 3 cents |

> **Note**:
>
> 1. The validities of both mathematical induction and strong induction follow from the well-ordering property.
>
> 2. In fact, mathematical induction, strong induction, and  well-ordering are all equivalent principles.

# Connection Between the Three Things 三者关系

The Mathematical Induction, the Strong Induction, and the well-ordering property is actually the same thing!

## 1. From W.P to M.I

See the validity of M.I, where the proof from W.P to M.I is given. We will omit the proof here.

## 2. From W.P to S.I

> Show that strong induction is a valid method of proof by showing that it follows from the well-ordering property

Assume that the well-ordering property holds. Suppose that P(1) is true and that the conditional statement $$[P(1)\wedge P(2)\wedge· · ·\wedge P(n)]\to P(n+1)$$ is true fore very positive integer n. Let S be the set of positive integers n for which P(n) is false.We will show S = ∅. Assume that $$S\neq \emptyset$$. Then by the well-ordering property there is a least integer m in S.We know that m cannot be 1 because P(1) is true. Because n = m is the least integer such that P(n) is false, P(1), P(2), . . . , P (m−1) are true, and m−1 ≥ 1. Because $$[P(1)\wedge P(2)\wedge· · ·\wedge P(m-1)]\to P(m)$$ is true, it follows that P(m) must also be true, which is a contradiction. Hence, S = ∅.

## 3. From M.I to W.P

>  Show that the well-ordering property can be proved when the principle of mathematical induction is taken as an axiom.

Suppose that the well-ordering property were false. Let S be a nonempty set of nonnegative integers that has no least element. Let P(n) be the statement “$$i\notin S\ for\ i=0,1,...,n$$” P(0) is true because if 0 ∈ S then S has a least element, namely, 0. Now suppose that P(n) is true. Thus, $$0\notin S,1\notin S,...,n\notin S$$. Clearly, n+1 cannot be in S, for if it were, it would be its least element. Thus P(n+1) is true. So by the principle of mathematical induction, $$n\notin S$$ for all nonnegative integers n. Thus, S = ∅, a contradiction.

