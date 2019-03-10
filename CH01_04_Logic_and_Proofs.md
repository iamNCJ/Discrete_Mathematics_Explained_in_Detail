<font size=6> Chapter 01 Logic and Proofs 逻辑与证明</font>

Part 04

Covering 1.6~

------

# Rules of Inference 推理规则

> Proofs in mathematics are ***valid arguments***
>
> An ***argument***（**论证**） is a sequence of statements that end with a conclusion
>
> By ***valid***（**有效性**）, we mean the conclusion must follow from the truth of the preceding statements (premises（**前提**）)

## Valid Arguments in Propositional Logic 命题逻辑的有效论证

An **argument** in propositional logic is a sequence of  propositions. 

All but the final proposition in the argument are called **premises** and the final proposition is called the **conclusion**. 

**An argument** **is** **valid** if the truth of all its premises implies that the conclusion is true.

An **argument form**（**论证形式**） in propositional logic is a sequence of compound propositions involving propositional variables.

**An argument form is valid** if no matter which particular propositions are substituted for the propositional variables in its premises, the conclusion is true if the premises are all true. 

$p_1\\p_2\\...\\p_n\\ - \\∴q​$

An argument in propositional logic is valid when **its argument form is valid**.

e.g.

![1552051586938](C:\Users\Tao Chiang\AppData\Roaming\Typora\typora-user-images\1552051586938.png)

## Rules of Inference 推理原则

### Rules of Inference for Propositional Logic 命题逻辑的推理原则

|       Rule of Inference       |            Tautology             |                             Name                             |
| :---------------------------: | :------------------------------: | :----------------------------------------------------------: |
|     $p\\p → q\\ --- \\∴q$     |       $(p ∧ (p → q)) → q$        |                    Modus ponens 假言推理                     |
|    $¬q\\p → q\\---\\∴ ¬p$     |       $(¬q ∧ (p → q))→¬p$        |                     Modus tollens 取拒式                     |
| $p → q\\q → r\\---\\∴ p → r$  | $((p → q) ∧ (q → r)) → (p → r)$  |              Hypothetical syllogism 假言三段论               |
|     $p ∨ q\\¬p\\---\\∴ q$     |        $((p ∨ q)∧¬p) → q$        |               Disjunctive syllogism 析取三段论               |
|       $p\\---\\∴ p ∨ q$       |          $p → (p ∨ q)$           |                       Addition 附加律                        |
|       $p ∧ q\\---\\∴ p$       |          $(p ∧ q) → p$           |                    Simplification 化简律                     |
|     $p\\q\\---\\∴ p ∧ q$      |     $((p) ∧ (q)) → (p ∧ q)$      |                      Conjunction 合取律                      |
| $p ∨ q\\¬p ∨ r\\---\\∴ q ∨ r$ | $((p ∨ q) ∧ (¬p ∨ r)) → (q ∨ r)$ | Resolution 消解律（**Pay Attention!**This rule has been used widely in many programmes） |

> ***A valid argument can lead to an incorrect conclusion if one of its premises is wrong/false!***

#### Resolution 消解律

Computer programs have been developed to automate the task of reasoning and proving theorems. Many of these programs make use of a rule of inference known as resolution. This rule of inference is based on the tautology

$((p ∨ q) ∧ (¬p ∨ r)) → (q ∨ r)$

The final disjunction in the resolution rule, $q ∨ r$, is called the **resolvent**（消解式）

### Rules of Inference for Quantified Statements 量化命题的推理规则

|                   Rule of Inference                   |                Name                 |
| :---------------------------------------------------: | :---------------------------------: |
|                 $∀xP(x)\\---\\∴ P(c)$                 |  Universal instantiation 全称实例   |
|  $P(c) for\ an\ arbitrary\ c\\----------\\∴ ∀xP(x)$   |  Universal generalization 全称引入  |
| $∃xP(x)\\------------\\∴ P(c)\ for\ some\ element\ c$ | Existential instantiation 存在实例  |
| $P(c)\ for\ some\ element\ c\\-----------\\∴ ∃xP(x)$  | Existential generalization 存在引入 |

### Combining Rules of Inference for Propositions and Quantified Statements 命题和量化命题的组合使用

#### Universal Modus Ponens 全称假言推理

$∀x(P(x) → Q(x))\\P(a),\ where\ a\ is\ a\ particular\ element\ in\ the\ domain\\------------------------\\∴ Q(a)​$

#### Universal Modus Tollens 全称取拒式

$∀x(P(x) → Q(x))\\¬Q(a),\ where\ a\ is\ a\ particular\ element\ in\ the\ domain\\------------------------\\∴ ¬P(a)$

## Using Rules of Inference to Build Arguments 使用推理规则建立论证

> To prove that an argument is valid
>
> - Assume the premises are true
>
> - Use the rules of inference and logical equivalences to determine that the conclusion is true

e.g.1 Propositional Logic 命题逻辑

![1552052562944](C:\Users\Tao Chiang\AppData\Roaming\Typora\typora-user-images\1552052562944.png)

![1552052590682](C:\Users\Tao Chiang\AppData\Roaming\Typora\typora-user-images\1552052590682.png)

**Note**: the second example added an additional premise for the conclusion is always true when r is false, so all we need to proove if that it's true when r is true!

**Note**: If the conclusion is given in a form of $p → q$ , we can convert the argument $p_1∧p_2∧...∧p_n→(p→q)$ to $p_1∧p_2∧...∧p_n∧p→q$ , because they are logically equivalent

e.g.2 Quantified Statements 量化命题

![1552125602790](C:\Users\Tao Chiang\AppData\Roaming\Typora\typora-user-images\1552125602790.png)

![1552125638066](C:\Users\Tao Chiang\AppData\Roaming\Typora\typora-user-images\1552125638066.png)

e.g.3 Combination 组合使用

![1552059049039](C:\Users\Tao Chiang\AppData\Roaming\Typora\typora-user-images\1552059049039.png)

## Fallacies 谬误

Several common fallacies arise in incorrect arguments. These fallacies resemble rules of inference,
but are based on contingencies rather than tautologies.

### Fallacy of denying the hypothesis 否定假设的谬误

> If you overslept, you’ll be late.
>
> You didn’t oversleep.
>
> Therefore: You aren’t late.

**WRONG!!**

$p→q\\¬p\\---\\∴¬q$

### Fallacy of affirming the conclusion 肯定结论的谬误
> If you are in China, you’re in Asia.
>
> You are in Asia.
>
> Therefore: You are in China.

**WRONG!!**

$p→q\\q\\---\\∴p​$

