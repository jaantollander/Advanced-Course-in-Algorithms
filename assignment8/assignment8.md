---
title: CS-E4500 Problem Set 8
author: Jaan Tollander de Balsch - 452056
date: \today
header-includes: \usepackage{unicode-math}
---
Material used in this report: @modern_computer_algebra, Sections 12.1-3, 14.6.

## Problem 1
Factor the polynomial \(f= 1+x+x^2+2x^3+x^4∈ℤ_3[x].\)

---

First, lets evaluate the polynomial \(f\) in all points in \(ℤ_3\)
\[
\begin{aligned}
f(0) = 1, 
f(1) = 0, 
f(2) = 0.
\end{aligned}
\]
As can be seen, the polynomial has two roots, \(1\) and \(2\). Therefore \((x-1)\) and \((x-2)\) are its factors. Now, diving the polynomial \(f\) by the product of these factors will give us the polynomial
\[
\frac{f}{(x-1) (x-2)} = \frac{f}{(x+2) (x+1)} = x^2 + 2x + 2
\]
which is irreducible (from last week's problem 1). Therefore all of the factors of \(f\) are \((x-1)\),  \((x-2)\) and \((x^2 + 2x + 2).\)


## Problem 2
Square-and-multiply modular exponentiation. Let \(q\) be a prime power. Present an algorithm that, given \(m∈ℤ_{≥1}, f∈𝔽_q[x],\) and \(g∈𝔽_q[x]∖\{0\}\) with \(\deg f, \deg g≤d∈ℤ_{≥1}\) as input, computes \(f^m \operatorname{rem} g\) in \(O(M(d) \log m)\) operations in \(𝔽_q.\) Carefully justify the number of operations used by your algorithm.

---

Decompose the polynomial \(f^m \operatorname{rem} g\) into sum polynomials \(f^{2^i} \operatorname{rem} g\)
\[
f^m \operatorname{rem} g = f^{2^{n_1}} \operatorname{rem} g + f^{2^{n_2}} \operatorname{rem} g + ... + f^{2^{n_k}} \operatorname{rem} g.
\]
This is done by decomposing \(m\) into [a sum of powers of two](https://math.stackexchange.com/a/1553928)
\[
m = 2^{n_1} + 2^{n_2} + ... + 2^{n_k}
\]
such that \(\log m ≥ n_1 > n_2 > ... > n_k ≥ 0\) and \(k∈ℕ.\) The decomposition can be computed with \(\log m\) successive divisions by \(2\).

The powers of two of the polynomial \(f\) can be computed recursively upto power \(2^n\)
\[
\begin{aligned}
f^1 &= f \\
f^2 &= (f^1 ⋅ f^1) \operatorname{rem} g \\
f^4 &= (f^2 ⋅ f^2) \operatorname{rem} g \\
&⋮ \\
f^{2^n} &= (f^{2^{n-1}} ⋅ f^{2^{n-1}}) \operatorname{rem} g, n∈ℕ.
\end{aligned}
\]

The full algorithm for square-and-multiply modular exponentiation using the ideas above gives:

* **Input**: Let \(q\) be a prime power, the inputs are \(m∈ℤ_{≥1}\), \( f∈𝔽_q[x],\) and \(g∈𝔽_q[x]∖\{0\}\) with \(\deg f, \deg g≤d∈ℤ_{≥1}.\)
* **Output**: The polynomial \(h=f^m \operatorname{rem} g∈𝔽_q[x].\)

\(\operatorname{Square-and-Multiply-Modular-Exponentiation}(f, m, g)\)

1) Compute \(N=\{n_1, n_2, ..., n_k\}\) from the decomposition of \(m\)
2) \(h=0\)
3) \(\tilde{f}=f^1\)
4) **for** \(n = 0,1,...,n_k\)
5) ..... **if** \(n ∈ N\)
6) ..... ..... \(h = h + \tilde{f}\)
7) ..... \(\tilde{f}=(\tilde{f}⋅\tilde{f}) \operatorname{rem} g\)
8) **return** \(h\)

**Analysis**: There are \(\log m+1\) iterations in the for-loop. Inside the for-loop, there are the following operations

- Maximum of one polynomial addition. *Polynomial addition (Horner's rule) \(O(d).\)*
- One polynomial multiplication. *Fast polynomial multiplication \(O(M(d)).\)*
- One polynomial remainder. *Fast polynomial remaindering (Euclidean algorithm) \(O(M(d) \log d).\)*

The total number of operations in \(𝔽_q[x]\) is
\[
O((M(d) \log d) \log m).
\]

**NOTE**: I'm not sure how to get rid of the \(\log d\) term arising from the remainder.


## Problem 3
Formal derivative of a factorization. Let \(q\) be a prime power. Let \(f∈𝔽_q[x]\) be monic with factorization \(f=f_1^{d_1}f_2^{d_2}⋯f_r^{d_r}\) into distinct irreducible polynomials \(f_1,f_2,...,f_r∈𝔽_q[x]\) and \(d_1,d_2,...,d_r∈ℤ_{≥1}.\) Show that the formal derivative of \(f\) satisfies
\[
f' = d_1 f_1' \frac{f}{f_1} + d_2 f_2' \frac{f}{f_2} + ... + d_r f_r' \frac{f}{f_r}∈𝔽_q[x].
\]
Above we write \(d_j\) for a sum of \(d_j\) copies of the multiplicative identity of \(𝔽_q.\)

---

Let \(f\) and \(g\) be polynomials in \(𝔽_q[x].\) The formal derivative satisfies two properties:

1) The product rule
\[
(fg)'=f'g + fg'
\]
2) The chain rule
\[
(f(g))'=f'(g)g'
\]

The product rule where \(f=f_1 f_2 ⋯ f_r\) can be generalized into
\[
\left(∏_{i=1}^r f_i\right)' = ∑_{i=1}^r f_i' \frac{f}{f_i}.
\]

Also, the chain rule gives the derivative
\[
(f^d)'=d f^{d-1} f', d∈ℤ_{≥1}.
\]

Therefore using the rules above, the formal derivative satisfies
\[
\begin{aligned}
f' &= (f_1^{d_1}f_2^{d_2}⋯f_r^{d_r})' \\
&= \left(∏_{i=1}^r f_i^{d_i}\right)' \\
&= ∑_{i=1}^r \left(f_i^{d_r}\right)' \frac{f}{f_i^{d_r}} \\
&= ∑_{i=1}^r d_r f_i^{d_r-1} f_i' \frac{f}{f_i^{d_r}} \\
&= ∑_{i=1}^r d_r f_i' \frac{f}{f_i} \\
&= d_1 f_1' \frac{f}{f_1} + d_2 f_2' \frac{f}{f_2} + ... + d_r f_r' \frac{f}{f_r}.
\end{aligned}
\]


## Problem 4
Squares and non-squares. Let \(q\) be a prime power and let \(γ∈𝔽_q^×\) be an element with multiplicative order \(q-1.\) For \(k∈ℤ_{≥2}\) let us say that an element \(α∈𝔽_q\) is a \(k\)-th power if there exists an element \(β∈𝔽_q\) with \(α=β^k.\)

### (a)
Let \(k≥2\) divide \(q-1.\) Show that \(α∈𝔽_q^×\) a \(k\)-th power if and only if there exists an \(s∈\{0,1,...,q-2\}\) such that \(γ^s=α\) and \(k\) divides \(s.\)

---

Multiplicative order of \(q-1\) implies that \(γ\) is a generator of the multiplicative group \(𝔽_q^×=𝔽_q∖\{0\}.\) Therefore forall \(β∈𝔽_q^×\) there exists unique \(a∈A=\{0,1,...,q-2\}\) such that
\[
γ^a=β.
\]
Then all \(k\)-th powers \(α\) can be generated such that for all \(a∈A\)
\[
α=β^k=(γ^a)^k=γ^{ak}=γ^{ak\mod(q-1)}=γ^s.
\]

Therefore \(s=ak\) which implies \(s\) is divisible by \(k.\)

<!-- TODO: modulo \(q-1\)? -->


### (b)
Suppose that \(q\) is odd. Show that \(𝔽_q^×\) has exactly \((q-1)/2\) elements that are squares and exactly \((q-1)/2\) elements that are non-squares. Show that for each square \(α∈𝔽_q^×\) it holds that \(α^{(q-1)/2}=1,\) and that for each non-square \(α∈𝔽_q^×\) it holds that \(α^{(q-1)/2}=-1.\)

---


Let \(A=\{0,1,...,q-2\}\) be a set and its cardinality be \(|A|=q-1.\)

Then all squares are generated
\[
β^2=(γ^{a})^2=γ^{2a}=γ^{2a\mod (q-1)}=γ^s.
\]
where for any \(a∈A.\) Equivalently \(γ^s\) is a square if
\[
\begin{aligned}
s∈2A&=\{2a\mod(q-1)|a∈A\} \\
&=\{0,2,...,q-3\}.
\end{aligned}
\]
The amount of squares is therefore
\[
|2A|=|A|/2=(q-1)/2.
\]
If for all squares \(α∈𝔽_q^×\) there exists \(β∈𝔽_q^×\) such that \(α=β^2\). Therefore
\[
α^{(q-1)/2}=β^{q-1}=(γ^a)^{q-1}=(γ^{q-1})^a=1^a=1.
\]

Similarly \(γ^t\) is a non-square if
\[
t∈(A∖2A).
\]
The amount of non-square is
\[
|A∖2A|=|A|-|2A|=(q-1)/2.
\]
For all non-squares \(μ\)
\[
μ^{(q-1)/2} = (γ^{2a+1})^{(q-1)/2} = (γ^a)^{q-1} γ^{(q-1)/2} = γ^{(q-1)/2}.
\]
**NOTE:** Not sure how this is equal to \(-1.\)


## References
