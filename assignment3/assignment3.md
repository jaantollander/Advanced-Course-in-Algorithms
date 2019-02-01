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

The multiplication for radix point numbers in base \(B\) is defined as \[(s, e, α)·(s',e',α')=(s⋅s', e+e', α⋅α').\]

Then the multiplication of the two numbers given is
\[
(1, 12, 2212221201)+(1, 12, 2212122001)=(1, 101, 22022010111020220201)
\]
equivalently using the radix-point notation
\[
22122.21201 ⋅ 22121.22001 = 2202201011.1020220201
\]

### (b)
Let us work in base \(B = 7\). Add \(145.2332632\) and \(1345053.103\). Present the result
in radix-point representation.

---

The addition for radix point numbers in base \(B\) is defined as \[(s, e, α)+(s',e',α')=(s⋅s', e, α+α'⋅B^{e-e'}), e≥e'.\]

Then the addition of the two numbers given is
\[
(1, 10, 1452332632)+(1, 3, 1345053103)=(1, 10, 13452313362632)
\]
equivalently in radix-point notation
\[
145.2332632+1345053.103=1345231.3362632
\]


## Problem 2

\[
a = q b + r
\]

\[
f(x) = a_0 + a_1 x + … + a_n x^n
\]

\[
\begin{aligned}
x^n f(x^{-1}) &= x^n (a_0 + a_1 x^{-1} + … + a_n x^{-n}) \\
&= x_0 x^n + a_1 x^{n-1} + ... + a_n \\
&= \operatorname{rev}_n f(x)
\end{aligned}
\]

\[
\begin{aligned}
\operatorname{rev}_n a(x) &= x^n a(x^{-1}) \\
&= x^n (q(x^{-1}) b(x^{-1}) + r(x^{-1})) \\
&= x^n q(x^{-1}) b(x^{-1}) + x^n r(x^{-1}) \\
&= (x^{n-m} q(x^{-1})) (x^m b(x^{-1})) + x^{n-m+1} (x^{m-1} r(x^{-1})) \\
&= \operatorname{rev}_{n-m} q(x) \operatorname{rev}_m b + x^{n-m+1} \operatorname{rev}_{m-1} r
\end{aligned}
\]


## Problem 3
- problem 1b

\[
(\max(d-e, \tilde{d}-\tilde{e}, 1) + 1) + \max(e, \tilde{e}) + 1
\]

- max of the numbers of digits
- max of the radices
- one digit from possible carry
- one digit denoting the sign

## Problem 4


## References
