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
Using your solution to Problem 1, find for each nonzero element of \(𝔽_9\) it's multiplicative order.

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
Element \(1\) has order of \(1\), element \(2\) has order of \(2\), elements \(x, 2x\) have order of \(4\) and elements \(x+1, x+2, 2x+1, 2x+2\) have order of \(8.\)


## Problem 3
Let \(R\) be a commutative ring with \(0_R≠1_R.\) for a polynomial \(f=∑_{i=0}^d φ_i x^i ∈ R[x],\) define the *formal derivative* \(f'∈R[x]\) of \(f\) by \[f'=∑_{i=0}^d i_R φ_i x^{i-1},\] where \(i_R=1_R+1_R+...+1_R\) obtained by taking the sum of \(i\) copies of the multiplicative identity \(1_R\) of \(R.\)

Show that the formal derivative satisfies each of the following properties:

(a) \('\) is \(R\)-linear,
(b) \('\) satisfies the Leibniz (product) rule \((fg)'=f'g+fg',\) and
(c) \('\) satisfies the chain rule \(f(g)'=f'(g)g'.\)

---

Let \(f\) and \(g\) be polynomials in \(R[x].\) Let \(\deg f=d_1\) and \(\deg g=d_2\) be their degrees.

### (a)
Let the linear combination of polynomials \(f\) and \(g\) be
\[
\begin{aligned}
αf+βg &= α ∑_{i=0}^d φ_i x^i + β ∑_{i=0}^d ρ_i x^i \\
&= ∑_{i=0}^d (α φ_i + β ρ_i) x^i
\end{aligned}
\]
where \(α,β∈R\) and \(d=\deg (αf+βg)=\max\{\deg f,\deg g\}.\)

Then the formal derivative is \(R\)-linear
\[
\begin{aligned}
(αf+βg)' &= ∑_{i=0}^d i_R (α φ_i + β ρ_i) x^{i-1} \\
&= α ∑_{i=0}^d i_R φ_i x^{i-1} + β ∑_{i=0}^d i_R ρ_i x^{i-1} \\
&= αf'+βg'.
\end{aligned}
\]

### (b)
The multiplication of the polynomials \(f\) and \(g\) can be written
\[
fg = ∑_{n=0}^{d_1}∑_{m=0}^{d_2} φ_n ρ_m x^n x^m
\]

Using linear we have
\[
\begin{aligned}
(fg)' &= \Big(∑_{n=0}^{d_1}∑_{m=0}^{d_2} φ_n ρ_m x^n x^m\Big)' \\
&= ∑_{n=0}^{d_1}∑_{m=0}^{d_2} φ_n ρ_m (x^n x^m)'.
\end{aligned}
\]
where
\[
\begin{aligned}
(x^n x^m)' &= (x^{n+m})' \\
&= (n+m)x^{n+m-1} \\
&= (n x^{n-1} x^m) + (x^n m x^{m-1}) \\
&= (x^{n})' x^m + x^n (x^{m})'. \\
\end{aligned}
\]
Now we can form the product rule
\[
(fg)' = f'g + fg'.
\]


### (c)
<!-- \[
f(g) = ∑_{n=0}^{d_1} φ_n \left(∑_{m=0}^{d_2} ρ_m x^m\right)^n
\]

TODO: multinomial theorem
\[
\left(∑_{m=0}^{d_2} ρ_m x^m\right)^n = ∑_{k=0}^{d_2n} \tilde{ρ}_{k} x^{k}
\]

... -->

Using linearity we need to only prove the case where \(f=x^n\) and \(g=x^m\)
\[
\begin{aligned}
(f(g))'&= ((x^m)^n)' \\
&= (x^{mn})' \\
&= mn x^{mn-1} \\
&= mn x^{m(n-1)+(m-1)} \\
&= (n (x^m)^{n-1}) (m x^{m-1}) \\
&= f'(g)g'.
\end{aligned}
\]


## Problem 4
## References
