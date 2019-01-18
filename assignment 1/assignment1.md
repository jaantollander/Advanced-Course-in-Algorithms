---
title: Advances Course in Algorithms - Problem Set 1
author: Jaan Tollander de Balsch
date: \today
header-includes: \usepackage{unicode-math}
---
## Problem 1
### a)
Multiply \(a=x+x^2∈ℤ_2[x]\) and \(b=1+x+x^3∈ℤ_2[x]\).

---

\[
a⋅b=x+x^3+x^4+x^5 ∈ℤ_2[x]
\]

### b)
Divide \(a=1+x^2+x^3+x^4+x^6 ∈ℤ_2[x]\) and \(b=1+x^3+x^4 ∈ℤ_2[x]\). Present a quotient \(q∈ℤ_2[x]\) and a remainder \(r∈ℤ_2[x]\) such that  \(a=q⋅b+r\) and \(\deg r<\deg b.\)

---

First division gives us
\[
a=q_1 b+r_1,
\]
where the quotient \(q_1=x^2\) and the remainder \(r_1=1+x^3+x^4+x^5\). Since \(\deg r_1>\deg b\) we'll divide again. Second division given us
\[
r_1=q_2 b+r_2,
\]
where the quotient \(q_2=x\) and the remainder \(r_2=1+x+x^3\). The division terminates because \(\deg r_2<\deg b\). Lets collect the terms
\[
\begin{aligned}
a &= q_1 b+r_1 \\
&= q_1 b + (q_2 b + r_2) \\
&= (q_1+q_2) b + r_2 \\
&= q b + r.
\end{aligned}
\]
We see that the quotient and the remainder takes the form
\[
\begin{aligned}
q&=q_1+q_2=x+x^2 \\
r&=r_2=1+x+x^3.
\end{aligned}
\]


## Problem 2
### a)
Find the greatest common divisor of \(f=1234567\) and \(g=123\) in \(ℤ\). Using the output of the algorithm, find \(g^{-1}∈ℤ_f.\)

---

Using the Traditional Euclidian algorithm on \(f\) and \(g\) gives us
\[
\begin{aligned}
1234567 &= 10037⋅123+16 \\
123 &= 7⋅16+11 \\
16 &= 1⋅11+5 \\
11 &= 2⋅5+1.
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

Now using back substitution on the equation we can obtain coefficients for the Diophantine equation
\[
a⋅f+b⋅g = 1.
\]
where \(a = -23\) and \(b = 230854\).

Written in another form
\[
b⋅g = -a⋅f+1
\]
we see that the coefficient \(b\) is answer for \(g^{-1}∈ℤ_f\) because
\[
\begin{aligned}
g⋅g^{-1}\mod f&=1 \\
g⋅g^{-1}&=k⋅f+1, k∈ℤ_f
\end{aligned}
\]
where \(k=-a=23\) and \(g^{-1}=b=230854.\)


### b)
Find a greatest common divisor of \(f=1+x+x^3+x^4\) and \(g=1+x^4\) in \(ℤ_2[x]\).

---

Using Traditional Euclidian algorithm on \(f\) and \(g\) gives us
\[
\begin{aligned}
1+x+x^3+x^4 &= 1⋅(1+x^4)+(x+x^3) \\
1+x^4 &= x⋅(x+x^3)+(1+x^2) \\
x+x^3 &= x⋅(1+x^2)+0.
\end{aligned}
\]
From the output we can see that
\[
\gcd(f,g)=1+x^2∈ℤ_2[x].
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

### b)
\[
R_i =
\left[\begin{matrix}
s_i & t_i \\
s_{i+1} & t_{i+1} \\
\end{matrix}\right]
\]

**Base case** \(i=0\) is true by definition. We'll assume \(i=n\) to be true and we'll show that also \(i=n+1\) is then true.
\[
\begin{aligned}
R_{n+1}
&=
\left[\begin{matrix}
s_{n+1} & t_{n+1} \\
s_{(n+1)+1} & t_{(n+1)+1} \\
\end{matrix}\right]
\\
R_n
&=
Q_{n+1}^{-1}
\left[\begin{matrix}
s_{n+1} & t_{n+1} \\
s_{(n+1)+1} & t_{(n+1)+1} \\
\end{matrix}\right]
\\
&=
\left[\begin{matrix}
q_{n+1} & 1 \\
1 & 0
\end{matrix}\right]
\left[\begin{matrix}
s_{n+1} & t_{n+1} \\
s_{(n+1)+1} & t_{(n+1)+1} \\
\end{matrix}\right]
\\
&=
\left[\begin{matrix}
q_{n+1} s_{n+1} + s_{n+2} & q_{n+1} t_{n+2} + t_{n+1} \\
s_{n+1} & t_{n+1} \\
\end{matrix}\right]
\\
&=
\left[\begin{matrix}
s_n & t_n \\
s_{n+1} & t_{n+1} \\
\end{matrix}\right].
\end{aligned}
\]

### c)
The output of Euclidian algorithm is as follows.
\[
\begin{aligned}
r_0 &= q_1 r_1 +r_2 \\
r_1 &= q_2 r_2 +r_3 \\
r_2 &= q_3 r_3 +r_4 \\
&⋮ \\
r_{l-2} &= q_{l-1} r_{l-1} +r_{l} \\
r_{l-1} &= q_{l} r_{l} +r_{l+1} \\
\end{aligned}
\]

Then the algorithm terminates when \(r_{l+1}=0\). This means that \(r_{l-1}\) is divisible by \(r_l\) and then also \(r_i\) where \(0≤i≤l-1\) is divisible by \(r_l\).
\[
\begin{aligned}
r_{l+1}=0 &⟹ r_{l}∣r_{l-1} \\
&⟹ r_{l}∣r_{l-2} \\
&⋮ \\
&⟹ r_l∣r_{0}
\end{aligned}
\]

Divisor \(r_l\) is greatest otherwise some \(r_i=0\) where \(i∈[0, l]\).


### d)
By using the statements proven in (a) and (b) we have
\[
\begin{aligned}
R_i
\left[\begin{matrix}
f \\ g
\end{matrix}\right]
&=
\left[\begin{matrix}
r_i \\ r_{i+1}
\end{matrix}\right]
\\
\left[\begin{matrix}
s_i & t_i \\
s_{i+1} & t_{i+1} \\
\end{matrix}\right]
\left[\begin{matrix}
f \\ g
\end{matrix}\right]
&=
\left[\begin{matrix}
r_i \\ r_{i+1}
\end{matrix}\right]
\end{aligned}
\]
which implies
\[
s_i f + t_i g = r_i.
\]
