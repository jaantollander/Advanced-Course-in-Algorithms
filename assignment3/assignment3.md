---
title: CS-E4500 Problem Set 3
author: Jaan Tollander de Balsch - 452056
date: \today
header-includes: \usepackage{unicode-math}
---
@modern_computer_algebra


## Problem 1
Arithmetic with rational numbers in radix-point representation.

### (a)
Let us work in base \(B=3\). Multiply \(22122.21201\) and \(22121.22001\). Present the
result in radix-point representation.

---

<!-- FIXME -->
<!-- The multiplication for radix point numbers in base \(B\) is defined as \[(s, e, α)·(s',e',α')=(s⋅s', e+e', α⋅α').\] -->

<!-- Then the multiplication of the two numbers given
\[
(1, ???, 2212221201)+(1, ???, 2212122001)=(1, 101, 22022010111020220201)
\] -->

<!-- equivalently using the radix-point notation -->
\[
22122.21201 ⋅ 22121.22001 = 2202201011.1020220201
\]

### (b)
Let us work in base \(B = 7\). Add \(145.2332632\) and \(1345053.103\). Present the result
in radix-point representation.

---

<!-- FIXME -->
<!-- The addition for radix point numbers in base \(B\) is defined as \[(s, e, α)+(s',e',α')=(s⋅s', e, α+α'⋅B^{e-e'}), e≥e'.\] -->

<!-- Then the addition of the two numbers given is
\[
(1, 10, 1452332632)+(1, 3, 1345053103)=(1, 10, 13452313362632)
\] -->
<!-- equivalently in radix-point notation -->
\[
145.2332632+1345053.103=1345231.3362632
\]


## Problem 2
The relation between a polynomial
\[
f(x) = a_0 + a_1 x + … + a_n x^n
\]
and its *\(n\)-reversal*
\[
\begin{aligned}
x^n f(x^{-1}) &= x^n (a_0 + a_1 x^{-1} + … + a_n x^{-n}) \\
&= x_0 x^n + a_1 x^{n-1} + ... + a_n \\
&= \operatorname{rev}_n f(x)
\end{aligned}
\]

Then the reversal of the polynomial
\[
a(x) = q(x) b(x) + r(x), a,b,q,r∈R[x]
\]
where \(n=\deg a≥\deg b=m\) and \(\deg r≤m-1\) is
\[
\begin{aligned}
\operatorname{rev}_n a(x) &= x^n a(x^{-1}) \\
&= x^n (q(x^{-1}) b(x^{-1}) + r(x^{-1})) \\
&= x^n q(x^{-1}) b(x^{-1}) + x^n r(x^{-1}) \\
&= (x^{n-m} q(x^{-1})) (x^m b(x^{-1})) + x^{n-m+1} (x^{m-1} r(x^{-1})) \\
&= \operatorname{rev}_{n-m} q(x) \operatorname{rev}_m b + x^{n-m+1} \operatorname{rev}_{m-1} r.
\end{aligned}
\]


## Problem 3
Two numbers in radix-point representation
\[
α=s B^e ∑_{i=0}^{d-1} α_i B^{-i}
\]
and
\[
\tilde{α}=\tilde{s} B^{\tilde{e}} ∑_{i=0}^{\tilde{d}-1} \tilde{α}_i B^{-i}
\]
can be summed by matching the radix points of the numbers, padding the *missing* digits with zeros and then using integer addition. The resulting number will also be in the radix-point representation potentially shifting the radix point and increasing the number of digits.

Let choose the operands \(α\) and \(\tilde{α}\) such that \(e≥\tilde{e}\). Then the addition can also be represented in the radix point representation
\[
\begin{aligned}
\hat{α}&=α+\tilde{α} \\
&= \hat{s} B^{\hat{e}} ∑_{i=0}^{\hat{d}-1} \hat{α}_i B^{-i}
\end{aligned}
\]

where the exponent \(\hat{e}=\max\{e,\tilde{e}\}=e\) or \(\hat{e}=\max\{e,\tilde{e}\}+1=e+1\) if there is a carry and
\[
\hat{d}=\max\{d, \tilde{d}+(e-\tilde{e})\}+1
\]
is the number of digits in sum where \(+1\) accounts for the carry.
<!-- The digits \(\hat{α}_i\) are the sum of -->


## Problem 4


## References
