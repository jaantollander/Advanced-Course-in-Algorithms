---
title: Advances Course in Algorithms - Problem Set 1
author: Jaan Tollander de Balsch
date: \today
header-includes: \usepackage{unicode-math}
---
## Problem 1
### a)

\[
(x+x^2) ⋅ (1+x+x^3) = x + x^3+x^4+x^5 ∈ℤ_2[x]
\]

### b)
\[
\begin{aligned}
a &= 1+x^2+x^3+x^4+x^6 ∈ℤ_2[x] \\
b &= 1+x^3+x^4 ∈ℤ_2[x]
\end{aligned}
\]

\[
a=q⋅b+r \\
\]

\[
\begin{aligned}
q&=x+x^2 \\
r&=1+x+x^3
\end{aligned}
\]

## Problem 2
### a)

Given \(f=1234567\) and \(g=123\), find
\[
\gcd(f, g)=1
\]

Traditional euclidian algorithm
\[
\begin{aligned}
1234567 &= 10037⋅123+16 \\
123 &= 7⋅16+11 \\
16 &= 1⋅11+5 \\
11 &= 2⋅5+1
\end{aligned}
\]

Written in another form
\[
\begin{aligned}
1 &= 11 - 2⋅5 \\
5 &= 16 - 1⋅11 \\
11 &= 123 - 7⋅16 \\
16 &= 1234567 - 10037⋅123
\end{aligned}
\]

Using back substitution we obtain
\[
a⋅f+b⋅g = 1 \\
b⋅g = -a⋅f+1
\]
where
\[
\begin{aligned}
a = -23 \\
b = 230854
\end{aligned}
\]

Find \(g^{-1}∈ℤ_f\)
\[
\begin{aligned}
g⋅g^{-1}\mod f&=1 \\
g⋅g^{-1}&=k⋅f+1, k∈ℤ_f \\
g^{-1}&=b=230854.
\end{aligned}
\]


### b)
\[
\begin{aligned}
f &= 1+x+x^3+x^4 ∈ℤ_2[x] \\
g &= 1+x^4 ∈ℤ_2[x]
\end{aligned}
\]

Find
\[
\gcd(f,g)
\]

Euclidian algorithm
\[
\begin{aligned}
1+x+x^3+x^4 &= 1⋅(1+x^4)+(x+x^3) \\
1+x^4 &= x⋅(x+x^3)+(1+x^2) \\
x+x^3 &= x⋅(1+x^2)+0
\end{aligned}
\]

\[
\gcd(f,g)=1+x^2∈ℤ_2[x]
\]
