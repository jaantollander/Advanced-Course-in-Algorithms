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

<!-- TODO: digits of \(m\) as a binary number? -->

<!-- The upper bound for \(k\) as a function of \(m\), i.e. the upper bound for the number of additions, is the case where
\[
m = 2^1 + 2^2 + ... + 2^k < 2^{k+1}.
\]
Which gives
\[
k < \log m - 1 < \log m.
\] -->

The powers of two of the polynomial \(f\) can be computed recursively upto power \(2^n\) starting with \(f^1=f\) by
\[
\begin{aligned}
f^2 &= (f^1 ⋅ f^1) \operatorname{rem} g \\
f^4 &= (f^2 ⋅ f^2) \operatorname{rem} g \\
&⋮ \\
f^{2^n} &= (f^{2^{n-1}} ⋅ f^{2^{n-1}}) \operatorname{rem} g, n∈ℕ.
\end{aligned}
\]

The full algorithm ...

* **Input** \(f\) \(m\) \(g\)
* **Output**

\(\operatorname{Square-and-Multiply-Modular-Exponentiation}(f, m, g)\)

1) Decompose \(m\) into \(n_1, n_2, ..., n_k\)
2) \(h=0\)
3) \(\tilde{f}=f^1\)
4) **for** \(n = 1,2,...,n_k\)
5) ..... **if** \(n ∈ n_i\)
6) ..... ..... \(h = h + \tilde{f}\)
7) ..... \(\tilde{f}=(\tilde{f}⋅\tilde{f}) \operatorname{rem} g\)
8) **return** \(h\)

Analysis

- Addition \(O(d)\)
- Multiply \(O(d \log d)\)
- Fast remainder \(O(...)\)


## Problem 3
## Problem 4
## References
