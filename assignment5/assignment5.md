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
Reed-Solomon codes.

### (a)
Encoding: Suppose we want ot encode data vector \(Φ=(7,6,5,4,3)∈𝔽_{11}^{5}\) using the evaluation points \(Ξ=(0,1,2,3,4,5,6)∈𝔽_{11}^{5}.\) Find the encoding \(Ψ=f(Ξ)∈𝔽_{11}^{7}.\)

---

Create a polynomial \(f\) by using \(Φ\) as the coefficients
\[
f(x) = 3 x^{4} + 4 x^{3} + 5 x^{2} + 6 x + 7 ∈ 𝔽_{11}[x].
\]
Then evaluate the polynomial at points \(Ξ\) to obtain the encoding
\[
f(Ξ) = \left ( 7,  3,  9,  3,  2,  7,  3\right ) ∈ 𝔽^7_{11}.
\]

### (b)
Decoding in the presence of errors. Suppose that \(Ξ=(1,2,3,4,5,6)∈𝔽_{13}^6\) and that \(Γ=(3,8,6,7,1)∈𝔽_{13}^6.\) Find the unique polynomial \(f∈𝔽_{13}[x]\)  of degree at most \(1\) such that \(f(Ξ)\) agrees iwth \(Γ\) in all but at most \(2\) coordinates, or conclude that no such \(f\) exists.

---

The decoding can be done using Gao's algorithm [@gao2002]. I used Python with the Sympy library to calculate the polynomial operations on finite fields.

We have
\[
\begin{aligned}
e &= 6 \\
d &= 1 \\
\end{aligned}
\]

The polynomial \(g_0\) is constructed as
\[
g_0 = ∏_{i=0}^e (x-ξ_i) = x^{6} + 5 x^{5} + 6 x^{4} + 6 x^{3} + 12 x^{2} + 4 x + 5.
\]
The polynomial \(g_1\) is obtained using Lagrange interpolation in points \((ξ_i, φ_i)\) for all \(i=1,2,...,e\)
\[
g_1 = 7 x^{5} + 5 x^{4} + 9 x^{3} + x + 7
\]

The initial values of the Bezout coefficient
\[
\begin{aligned}
t_0=0 \\
t_1=1
\end{aligned}
\]

Then we apply extended Euclidian algorithm to \(g_0\) and \(g_1\) to produce the concecutive remainders \(g_h,g_{h+1}\) with \(\deg g_h≥D\), and \(\deg g_{h+1} < D\) for \(D = (e+d+1)/2 = 4\)

First iteration: \(g_0 = q_1 g_1 + g_2\)
\[
\begin{aligned}
q_1 &= 2x + 3 \\
g_2 &= 12 x^{4} + 5 x^{3} + 10 x^{2} + 10 \\
t_2 &= t_0  - q_1 t_1 = 11x + 10 \\
\deg g_2 &= 4 ≥ D
\end{aligned}
\]

Second iteration: \(g_1 = q_2 g_2 + g_3\)
\[
\begin{aligned}
q_2 &= 6x + 12 \\
g_3 &= 6 x^{3} + 10 x^{2} + 6 x + 4 \\
t_3 &= t_1 - q_2 t_2 = 12x^2 + 3x + 11 \\
\deg g_3 &= 3 < D
\end{aligned}
\]

By dividing \(g_3\) with \(t_3\) we obtain quotient
\[
f = g_3 / t_3 = 7x + 11
\]
with remainder \(r=0\). The decoding is succesful and the reconstructed data vector is
\[
(11, 7).
\]

We can see that \(Γ\) has two errors
\[
\begin{aligned}
f(Ξ) &= [5, 12, 6, 0, 7, 1] ≠ \\
Γ &= [3, 8, 6, 0, 7, 1].
\end{aligned}
\]


## Problem 3
## Problem 4
## References
