---
title: CS-E4500 Problem Set 9
author: Jaan Tollander de Balsch - 452056
date: \today
header-includes: \usepackage{unicode-math}
---
Material used in this report: @modern_computer_algebra, Sections 19.1-3, 19.5.

## Problem 1
Factor the integer \(N=2028455971.\)

---

Given \(s\) and \(t\) such that \(s^2≡t^2 \mod N\) and \(\gcd(s, N)=\gcd(t, N)=1\) there exists integer \(q\) with \
\[
s^2-t^2 = (s-t) (s+t) = qN.
\]
Thus
\[
\gcd(s+t, N)
\]
is a proper divisor of \(N\) unless \(N\) divides \(s-t\) or \(N\) divides \(s+t.\)

We are given \(s=702505371\) and \(t=188270011\) then
\[
\gcd(s+t, N) = 46073
\]
is prime and a factor of \(N\). Dividing \(N\) by this number gives
\[
N / 46073 = 44027,
\]
which is also a prime and a factor of \(N.\) Therefore the factors of \(N\) are \(44027\) and \(46073.\)


## Problem 2
De Bruijn's lower bound. Show that for all \(x≥1\) and \(k∈ℤ_{≥1}\) we have \(Ψ(x^k, x)≥\binom{π(x)+k}{k}≥\left(\frac{π(x)}{k}\right)^k.\)

---

Let \(Ψ(M, B)\) be the number of \(B\)-smooth positive integers \(N\) at most \(M\). Let \(π(x)\) denote the number of prime numbers at most \(x.\)

The factorization of \(B\)-smooth positive integer \(N\) at most \(M\) is
\[
N = p_1^{z_1} p_2^{z_2} ⋯ p_r^{z_r} ≤ M
\]
where \(p_1, p_2, ..., p_r ≤ B\) are its distinct primes factors, \(z∈ℤ_{≥0}\) the coefficients and \(r=π(B)\) the number of distinct prime factors.

Using the definition
\[
\begin{aligned}
N &= p_1^{z_1} p_2^{z_2} ⋯ p_r^{z_r} \\
&≤ B^{z_1} B^{z_2} ⋯ B^{z_r} \\
&= B^{z_1 + z_2 + ... + z_r} \\
&= M.
\end{aligned}
\]

Substituting \(M=x^k\) and \(B=x\) and \(r=π(x)\) gives
\[
\begin{aligned}
x^{z_1 + z_2 + ... + z_r} &= x^k \\
z_1 + z_2 + ... + z_r &= k.
\end{aligned}
\]
The amount of solutions to this inequality is
\[
\binom{r+k}{k} = \binom{π(x)+k}{k}.
\]
Giving us the lower bound of
\[
Ψ(x^k, x)≥\binom{π(x)+k}{k}.
\]

---

Using the definition for the binomial \[\binom{m}{k}=\frac{m!}{k!(m-k)!}\] and for the factorial \[m!=1⋅2⋯m≤m^m\] the lower bound can be furher refined into
\[
\begin{aligned}
\binom{r+k}{k} &= \frac{(r+k)!}{k!((r+k)-k)!} \\
&= \frac{(r+k)!}{k!⋅r!} \\
&= \frac{(r+1) (r+2)⋯(r+k)}{1⋅2⋯k} \\
&≥ \frac{r^k}{k^k} \\
&= \left(\frac{r}{k}\right)^k.
\end{aligned}
\]

Therefore
\[
Ψ(x^k, x)≥\binom{π(x)+k}{k}≥\left(\frac{π(x)}{k}\right)^k.
\]


## Problem 3
## Problem 4
## References
