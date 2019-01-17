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


## Problem 4
Initial values
\[
\begin{aligned}
r_0=f, s_0=1, t_0=0, \\
r_1=g, s_1=0, t_1=1, \\
\end{aligned}
\]

\[
\begin{aligned}
q_i = quo(r_{i-1},r_i) \\
r_{i+1} = r_{i-1} - q_i r_i \\
s_{i+1} = s_{i-1} - q_i s_i \\
t_{i+1} = t_{i-1} - q_i t_i
\end{aligned}
\]

\[
\begin{aligned}
R_0 =
\left[\begin{matrix}
s_0 & t_0 \\
s_1 & t_1 \\
\end{matrix}\right]
\end{aligned}
\]

\[
\begin{aligned}
Q_i =
\left[\begin{matrix}
0 & 1 \\
1 & -q_i \\
\end{matrix}\right]
\end{aligned}
\]

\[
R_i = Q_i Q_{i-1} ⋯ Q_1 R_0
\]

\[
Q_i^{-1}=
\left[\begin{matrix}
q_i & 1 \\
1 & 0
\end{matrix}\right]
\]

### a)
\[
R_i
\left[\begin{matrix}
f \\ g
\end{matrix}\right]
=
\left[\begin{matrix}
r_i \\ r_{i+1}
\end{matrix}\right]
\]

**Base case**: \(i=0\)
\[
\begin{aligned}
R_0
\left[\begin{matrix}
f \\ g
\end{matrix}\right]
=
\left[\begin{matrix}
r_0 \\ r_{1}
\end{matrix}\right]
\\
\left[\begin{matrix}
1 & 0 \\
0 & 1 \\
\end{matrix}\right]
\left[\begin{matrix}
f \\ g
\end{matrix}\right]
=
\left[\begin{matrix}
r_0 \\ r_{1}
\end{matrix}\right]
\\
\left[\begin{matrix}
f \\ g
\end{matrix}\right]
=
\left[\begin{matrix}
r_0 \\ r_{1}
\end{matrix}\right]
\end{aligned}
\]

We will assume that the **case** \(i=n\) is true. Then we'll show that also case \(i=n+1\) is true.

\[
\begin{aligned}
R_{i+1} &= Q_{i+1} Q_i Q_{i-1} ⋯ Q_1 R_0 \\
&=Q_{i+1} R_i
\end{aligned}
\]

\[
\begin{aligned}
r_{i+1} &= r_{i-1} - q_i r_i \\
r_{i+1} + q_i r_i &= r_{i-1} \\
\end{aligned}
\]

\[
\begin{aligned}
R_{n+1}
\left[\begin{matrix}
f \\ g
\end{matrix}\right]
&=
\left[\begin{matrix}
r_{n+1} \\ r_{(n+1)+1}
\end{matrix}\right]
\\
Q_{n+1} R_{n}
\left[\begin{matrix}
f \\ g
\end{matrix}\right]
&=
\left[\begin{matrix}
r_{n+1} \\ r_{(n+1)+1}
\end{matrix}\right]
\\
R_{n}
\left[\begin{matrix}
f \\ g
\end{matrix}\right]
&=
Q_{n+1}^{-1}
\left[\begin{matrix}
r_{n+1} \\ r_{(n+1)+1}
\end{matrix}\right]
\\
&=
\left[\begin{matrix}
q_{n+1} & 1 \\
1 & 0
\end{matrix}\right]
\left[\begin{matrix}
r_{n+1} \\ r_{(n+1)+1}
\end{matrix}\right]
\\
&=
\left[\begin{matrix}
q_{n+1} r_{n+1} + r_{n+2} \\ r_{n+1}
\end{matrix}\right]
\\
&=
\left[\begin{matrix}
r_{n} \\ r_{n+1}
\end{matrix}\right].
\end{aligned}
\]
