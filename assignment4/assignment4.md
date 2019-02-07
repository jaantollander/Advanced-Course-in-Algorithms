---
title: CS-E4500 Problem Set 4
author: Jaan Tollander de Balsch - 452056
date: \today
header-includes: \usepackage{unicode-math}
---
## Problem 1
Let \(F\) be a finite field. In this case \(F=ℤ_p=\{0,1,...,p\}\) for \(p\) prime. Let \(φ_0∈F\) be a **secret** that we'll split into \(s\) **shares** such that **knowledge** of any \(k\) shares enables recovery of the secret. [@modern_computer_algebra, chapter 5.3]

### 1.
Let \(ξ_1,ξ_2,...,ξ_s∈F\) be **distinct** and **nonzero**.


### 2.
Select elements \(φ_1,φ_2,...,φ_{k-1}\) independently and uniformly at random.


### 3.
Let \(f=φ_0+φ_1x+φ_2x^2+...+φ_{k-1}x^{k-1}∈F[x].\)


### 4.
For \(j=1,2,...,s\) share \(j\) is the pair \((ξ_j, f(ξ_j))∈F^2.\)


### Recovering the Secret
The secret can be recovered by interpolating the \(k\) shares back into polynomial \(f\) and evaluation the polynomial at \(f(ξ_0)=f(0)=φ_0.\)

TODO: Lagrange interpolation


## Problem 2
Let \(R\) be a ring and let \(q,r∈R[x]\) with \(a = q b + r\) and \(\deg r < \deg b\) where \(b\) monic.

### (a)
Show that for all \(ξ∈R\) and \(f∈R[x]\) we have \(f(ξ)=f \operatorname{rem}\,(x-ξ).\)

---

Let \(a=f\) and \(b=(x-ξ)\) then
\[
\begin{aligned}
f(x) &= q(x)⋅(x-ξ) + r(x) \\
f(ξ) &= q(ξ)⋅(ξ-ξ) + r(ξ) \\
f(ξ) &= r(ξ) \\
f(ξ) &= f \operatorname{rem}\, (x-ξ). \\
\end{aligned}
\]

### (b)
Let \(a,b,c∈R[x]\), with \(b\) and \(c\) monic, and suppose that \(c\) divides \(b\). Show that \(a\operatorname{rem}c=(a\operatorname{rem}b)\operatorname{rem}c.\)

---

We have equalities \(a = q_1 b + r_1\) and
\(b = q_2 c + r_2\) where the remainders are \[r_1=a \operatorname{rem} b\] and \(r_2=0\) since \(c\) divides \(b\).

The remainder \(r_1\) can also be written in this form \(r_1 = q' c + r'\) where \(\deg r'<\deg c\). Then we have a remainder
\[
r'=r_1 \operatorname{rem} c = (a\operatorname{rem}b)\operatorname{rem}c.
\]

We also have
\[
\begin{aligned}
a &= q_1 b + r_1 \\
a &= q_1 (q_2 c) + (q' c + r') \\
a &= (q_1 q_2 + q') c + r'. \\
\end{aligned}
\]
Then the remainder \(r'\) has equivalency
\[
r'=a \operatorname{rem} c.
\]

By combining the equivalencies for the remainder \(r'\) we have
\[
a \operatorname{rem} c = (a \operatorname{rem} b) \operatorname{rem} c.
\]


## Problem 3
## Problem 4
## References
