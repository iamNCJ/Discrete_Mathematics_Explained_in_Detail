# 001

We will sometimes use the notation $\bigvee_{j = 1}^{n} p_j$ for $p_1 \vee p_2 \vee ... \vee p_n$ and $\bigwedge_{j = 1}^n p_j$ for $p_1 \wedge p_2 \wedge ... \wedge p_n$. Using this notation, the extended version of De Morgan's laws can be written concisely as $\lnot (\bigvee_{j = 1}^n p_j) \equiv \bigwedge_{j = 1}^n p_j $ and $\lnot (\bigwedge_{j = 1}^n p_j) \equiv \bigvee_{j = 1}^n \lnot p_j$.(Methods for proving these identities will be given in Section 5.1.)

# 002

| **Name**            | **Equivalences**                                             |
| ------------------- | ------------------------------------------------------------ |
| Identity laws       | $p \wedge T \equiv p, p \vee F \equiv p$                     |
| Domination laws     | $p \vee T \equiv T, p \wedge F \equiv F$                     |
| Idempotent laws     | $p \vee p \equiv p, p \wedge p \equiv p$                     |
| Double negation law | $\lnot \lnot p \equiv p$                                     |
| Commutative laws    | $p \vee q \equiv q \vee p, p \wedge q \equiv q \wedge p$     |
| Associative laws    | $(p \vee q) \vee r \equiv p \vee (q \vee r), (p \wedge q) \wedge r \equiv p \wedge (q \wedge r)$ |
| Distributive laws   | $p \vee (q \wedge r) \equiv (p \vee q) \wedge (p \vee r), p \wedge (q \vee r) \equiv (p \wedge q) \vee (p \wedge r)$ |
| De Morgan's laws    | $\lnot (p \wedge q) \equiv \lnot p \vee \lnot q, \lnot (p \vee q) \equiv \lnot p \wedge \lnot q$ |

