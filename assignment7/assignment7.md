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

Let \[f = φ_0 + φ_1 x + x^2\] be a monic polynomial of degree \(2\) in \(ℤ_3[x].\) Then the set of all possible coefficient pairs \((φ_0,φ_1)\) is \(ℤ_3×ℤ_3.\)

Let \(\tilde{f}\) be a reducible monic polynomial of degree \(2\) in \(ℤ_3[x]\)
\[
\begin{aligned}
\tilde{f} &= gh \\
&= (a+x)⋅(b+x) \\
&= a⋅b + (a+b) x + x^2
\end{aligned}
\]
where \(a,b∈ℤ_3\) and \(g,h∈ℤ_3[x]\) and \(g,h∉ℤ_3.\) Then the set of all coefficient pairs which are reducible is \(\{(a⋅b, a+b)∣a,b∈ℤ_3\}.\)

Therefore all irreducible coefficients pairs are
\[
ℤ_3×ℤ_3 ∖ \{(a⋅b, a+b)∣a,b∈ℤ_3\} = \left\{\left ( 1, \quad 0\right ), \left ( 2, \quad 1\right ), \left ( 2, \quad 2\right )\right\}
\]

For example, \(f=1+x^2\) is a monic irreducible polynomial in \(ℤ_3[x].\)


### (b)


## Problem 2


## Problem 3
## Problem 4
## References
