---
title: CS-E4500 Problem Set 7
author: Jaan Tollander de Balsch - 452056
date: \today
header-includes: \usepackage{unicode-math}
---
Material used in this report: [@modern_computer_algebra, Sections 14.1–2, 25.3–4].

## Problem 1
### (a)
Find a monic irreducible polynomial of degree \(2\) in \(ℤ_3[x].\)

---

Let \(f\) be a monic polynomial of degree \(d=2\) in \(ℤ_p[x]\) where \(p=3\) is a prime. It can be written in the form \[f = φ_0 + φ_1 x + x^2.\] Then the set of all possible coefficient pairs \((φ_0,φ_1)\) is \[S=ℤ_3×ℤ_3.\]

Let \(\tilde{f}\) be a reducible monic polynomial of degree \(2\) in \(ℤ_3[x]\)
\[
\begin{aligned}
\tilde{f} &= gh \\
&= (a+x)⋅(b+x) \\
&= a⋅b + (a+b) x + x^2
\end{aligned}
\]
where \(a,b∈ℤ_3\) and \(g,h∈ℤ_3[x]\) and \(g,h∉ℤ_3.\) Then the set of all coefficient pairs which form a reducible monic polynomial of degree \(2\) is \[S'=\{(a⋅b, a+b)∣a,b∈ℤ_3\}.\]

Therefore all coefficients pairs which form monic irreducible polynomials of degree \(2\) are given by the set difference
\[
S∖S' = \left\{\left ( 1, \quad 0\right ), \left ( 2, \quad 1\right ), \left ( 2, \quad 2\right )\right\}.
\]

We can choose \[f=1+x^2\] as our monic irreducible polynomial of degree \(2\) in \(ℤ_3[x].\)


### (b)
Using your solution to part (a), present addition and multiplication tables for \(𝔽_9.\) For each nonzero element of \(𝔽_9,\) present its multiplicative inverse in \(𝔽_9.\)

---

The set of elements of the finite field \(F = 𝔽_{p^d} = ℤ_p[x]/⟨f⟩= 𝔽_{3^2} = ℤ_3[x]/⟨f⟩\) are the set of all polynomials of degree at most \(d-1=1\) in \(ℤ_3[x]\)
\[
S = \left\{0, 1, 2, x, 2 x, x + 1, x + 2, 2 x + 1, 2 x + 2\right\}
\]

Addition table
\[
\left[\begin{matrix}0 & 1 & 2 & x & x + 1 & x + 2 & 2 x & 2 x + 1 & 2 x + 2\\1 & 2 & 0 & x + 1 & x + 2 & x & 2 x + 1 & 2 x + 2 & 2 x\\2 & 0 & 1 & x + 2 & x & x + 1 & 2 x + 2 & 2 x & 2 x + 1\\x & x + 1 & x + 2 & 2 x & 2 x + 1 & 2 x + 2 & 0 & 1 & 2\\x + 1 & x + 2 & x & 2 x + 1 & 2 x + 2 & 2 x & 1 & 2 & 0\\x + 2 & x & x + 1 & 2 x + 2 & 2 x & 2 x + 1 & 2 & 0 & 1\\2 x & 2 x + 1 & 2 x + 2 & 0 & 1 & 2 & x & x + 1 & x + 2\\2 x + 1 & 2 x + 2 & 2 x & 1 & 2 & 0 & x + 1 & x + 2 & x\\2 x + 2 & 2 x & 2 x + 1 & 2 & 0 & 1 & x + 2 & x & x + 1\end{matrix}\right]
\]

Multiplication table
\[
\left[\begin{matrix}0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0\\0 & 1 & 2 & x & x + 1 & x + 2 & 2 x & 2 x + 1 & 2 x + 2\\0 & 2 & 1 & 2 x & 2 x + 2 & 2 x + 1 & x & x + 2 & x + 1\\0 & x & 2 x & 2 & x + 2 & 2 x + 2 & 1 & x + 1 & 2 x + 1\\0 & x + 1 & 2 x + 2 & x + 2 & 2 x & 1 & 2 x + 1 & 2 & x\\0 & x + 2 & 2 x + 1 & 2 x + 2 & 1 & x & x + 1 & 2 x & 2\\0 & 2 x & x & 1 & 2 x + 1 & x + 1 & 2 & 2 x + 2 & x + 2\\0 & 2 x + 1 & x + 2 & x + 1 & 2 & 2 x & 2 x + 2 & x & 1\\0 & 2 x + 2 & x + 1 & 2 x + 1 & x & 2 & x + 2 & 1 & 2 x\end{matrix}\right]
\]

Multiplicative inverses can be read from the multiplication table
\[
\begin{aligned}
1 ⋅ 1 &= 1 \\
2 ⋅ 2 &= 1 \\
x ⋅ 2x &= 1 \\
(x+1) ⋅ (x+2) &= 1 \\
(2x+1) ⋅ (2x+2) &= 1.
\end{aligned}
\]


## Problem 2
Using your solution to Problem 1, find for each nonzero element of \(𝔽_9\) its multiplicative order.

---

The order of a nonzero element \(a∈𝔽_q∖\{0\}\) is the least positive integer \(k\) such that \(a^k=1.\)

For the elements \(𝔽_9\) we have
\[
\begin{aligned}
1^1 &= 1 \\
2^2 &= 1 \\
x^4 &= (2x)^4 = 1 \\
(x+1)^8 &= (x+2)^8 = (2x+1)^8 = (2x+2)^8 = 1.
\end{aligned}
\]


## Problem 3
## Problem 4
## References
