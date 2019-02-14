---
title: CS-E4500 Problem Set 5
author: Jaan Tollander de Balsch - 452056
date: \today
header-includes: \usepackage{unicode-math}
---
This report uses algorithms from @modern_computer_algebra, chapters ???.

## Problem 1
Let \(F\) be a field, Show that a nonzero polynomial \(f∈F[x]\) of degree at most \(d\) has at most \(d\) distinct roots.

---

Let \(ξ_1,ξ_2,...,ξ_n∈F\) be \(n≥d+1\) distinct roots of polynomial \(f\). Then the polynomial can be represented using the roots as
\[
f(x) = a (x-ξ_1)^{k_1} (x-ξ_2)^{k_2} ⋯ (x-ξ_n)^{k_n}
\]
where \(a∈F\) is a scaling coefficient and \(k_1,k_2,...,k_n∈ℕ\) are the multiples of the roots. The degree of the polynomial is
\[
\begin{aligned}
\deg f(x) &= k_1 + k_2 + ... + k_n \\
&≥ \min_{k_1,k_2,...,k_n∈ℕ} (k_1 + k_2 + ... + k_n) \\
&= n \\
&≥ d+1.
\end{aligned}
\]
This implies that a polynomial that has \(d+1\) distinct roots has degree of atleast \(d+1\). Equivalently a polynomial that has degree \(d\) has at most \(d\) distinct roots.


## Problem 2
## Problem 3
## Problem 4
## References
