---
title: CS-E4500 Problem Set 5
author: Jaan Tollander de Balsch - 452056
date: \today
header-includes: \usepackage{unicode-math}
---
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
The solution to this problem are based on [@modern_computer_algebra, chapter 11.1]. Let a polynomial \(f\) be defined
\[
f = f_n x^{n} + f_{n-1} x^{n-1} + ... + f_0 ∈ 𝔽[x]
\]
where the leading coefficient \(f_n≠0\) and \(n=\deg f\) is the degree. A **truncated polynomial** is defined
\[
f↾k = f \operatorname{quo} x^{n-k} = f_n x^{k} + f_{n-1} x^{k-1} + ... + f_{n-k},
\]
where \(k∈ℤ\). Then the polynomial \(f\) can be written in form
\[
f = (f↾k) x^{n-k} + r,
\]
where \(r∈𝔽[x]\) and \(\deg r < n-k\) and \(k≤n\).

<!-- \[
\begin{aligned}
f↾k &= 0, k<0 \\
f↾-∞ &= 0 \\
0↾k &= 0
\end{aligned}
\] -->

<!-- For all \(i∈ℕ_0\) we have
\[
(f x^i)↾k=f↾k
\] -->

---

Let \(f,g,f' ,g'\) be polynomials in field \(𝔽[x]\) such that \(\deg f ≥ \deg g≥0\) and \(\deg f'≥\deg g'≥0\) and which **coincide up to** \(k∈ℕ_0\)
\[
(f, g) ≡_k (f', g').
\]
Equivalently written
\[
\begin{aligned}
f↾k &= f'↾k, \\
g↾(k-(\deg f - \deg g)) &= g'↾(k-(\deg f' - \deg g')).
\end{aligned}
\]

Then written in the division form with quotients and remainders
\[
\begin{aligned}
f &= qg + r, \deg r < \deg g \\
f' &= q'g' + r', \deg r' < \deg g' \\
\end{aligned}
\]
the remainders \(q=q'\) are equal.

---

**Proof**: (This might not be the cleanest way to prove this.)

For simplicity lets denote the degrees with
\[
\begin{aligned}
\deg f &= n \\
\deg g &= m \\
\deg f' &= n' \\
\deg g' &= m'.
\end{aligned}
\]

We have
\[
k≥n-m=n'-m'=δ≥0
\]
then
\[
\begin{aligned}
f↾k &= f'↾k, \\
g↾k' &= g'↾k',
\end{aligned}
\]
where
\[
k'=k-(n-m)=k-(n'-m')=k-δ.
\]

We also have the following indentities
\[
\begin{aligned}
n = n'+δ \\
m = m'+δ \\
m-k'=n-k
\end{aligned}
\]

Now by writing the polynoamials in terms of their *truncations* we obtain
\[
\begin{aligned}
f' &= (f'↾k) x^{n'-k} + r_{f'}, \deg r_{f'} < n'-k \\
\end{aligned}
\]

\[
\begin{aligned}
f &= (f↾k) x^{n-k} + r_f, \deg r_f< n-k \\
&= (f'↾k) x^{n'-k} x^δ + r_f \\
&= (f'-r_{f'}) x^δ + r_f
\end{aligned}
\]
and
\[
\begin{aligned}
g' &= (g'↾k') x^{m'-k'} + r_{g'}, \deg r_{g'} < m'-k'
\end{aligned}
\]

\[
\begin{aligned}
g &= (g↾k') x^{m-k'} + r_g, \deg r_g < m-k' \\
&= (g'↾k') x^{m'-k'}x^δ + r_g \\
&= (g'-r_{g'})x^δ + r_{g}
\end{aligned}
\]

Then substituting them into the division formula
\[
\begin{aligned}
f &= qg + r \\
(f'-r_{f'}) x^δ + r_f &= q((g'-r_{g'})x^δ + r_{g}) + r \\
f' x^δ &= q g' x^δ + (r-r_f+qr_g+(r_{f'}-qr_{g'})x^δ) \\
f' &= q g' + ((r-r_f+qr_g) x^{-δ}+r_{f'}-qr_{g'}) \\
f' &= q' g' + r'. \\
\end{aligned}
\]
In order to prove that \(q=q'\) we need to prove that \(\deg r' < \deg g' = \deg g\). The degree of the quotient \(q\) is \(\deg q = \deg f - \deg g=δ\). Then the degree of the remainder \(r'\)
\[
\begin{aligned}
\deg r' &= \deg ((r-r_f+qr_g) x^{-δ}+r_{f'}-qr_{g'}) \\
& = \max\{\deg rx^{-δ}, \deg-r_fx^{-δ}, \deg qr_gx^{-δ}, \deg r_{f'}, \deg -qr_{g'}\} \\
&= \max\{\deg r - δ, \deg r_f - δ, \deg r_g, \deg r_{f'}, δ+\deg r_{g'}\} \\
&< \deg g=\deg g'
\end{aligned}
\]

1) \(\deg r - δ < \deg r < \deg g\)
2) \(\deg r_f - δ < n - k - δ ≤ m - k < \deg g\)
3) \(\deg r_g < m-k' = m-k-δ=m-(k+δ) < \deg g\)
4) \(\deg r_{f'} < n'-k = (n-δ)-k = m-k < \deg g\)
5) \(\deg r_{g'} + δ < m'-k'+δ = m'-(k-δ)+δ \\ = m'-k=(m-δ)-k<\deg g\)

Therefore \(\deg r'<\deg g=\deg g'\). \(□\)

---

This answers to the question why the division \(f,g≡_4(\tilde{f}, \tilde{g})\) produce the same quotient for the polynomials in question.


## Problem 4
The proof made in the problem 3 should atleast partially answer this question.


## References
