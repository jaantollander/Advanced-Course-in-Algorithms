---
title: CS-E4500 Problem Set 4
author: Jaan Tollander de Balsch - 452056
date: \today
header-includes: \usepackage{unicode-math}
---
[@modern_computer_algebra, chapter 5.1-5.4 and 10.1-10.3]

## Problem 1
Let \(F\) be a finite field. In this case \(F=ℤ_p=\{0,1,...,p\}\) for \(p\) prime. Let \(φ_0∈F\) be a **secret** that we'll split into \(s\) **shares** such that **knowledge** of any \(k\) shares enables recovery of the secret.

1) Let \(ξ_1,ξ_2,...,ξ_s∈F\) be **distinct** and **nonzero**.
2) Select elements \(φ_1,φ_2,...,φ_{k-1}\) independently and uniformly at random.
3) Let \(f=φ_0+φ_1x+φ_2x^2+...+φ_{k-1}x^{k-1}∈F[x].\)
4) For \(j=1,2,...,s\) share \(j\) is the pair \((ξ_j, f(ξ_j))∈F^2.\)

The secret can be **recovered** by interpolating the \(k\) shares back into polynomial \(f\) and evaluation the polynomial at \(f(ξ_0)=f(0)=φ_0.\) We'll use Lagrange interpolation as the interpolating algorithm.

---

```python
from sympy import *
init_printing("mathjax")
import random
```

```python
a = 0
b = 99
p = nextprime(b)
a, b, p
```

$$\left ( 0, \quad 99, \quad 101\right )$$

```python
Z_p = list(range(p+1))
secret = random.randint(a, b)
shares = 10
knowledge = 5
secret,shares,knowledge
```

$$\left ( 42, \quad 10, \quad 5\right )$$

**Step 1**
```python
xi = random.sample(Z_p[1:], shares)
xi
```

$$\left [ 3, \quad 51, \quad 85, \quad 33, \quad 7, \quad 35, \quad 81, \quad 2, \quad 1, \quad 26\right ]$$

**Step 2**
```python
phi = random.sample(Z_p, knowledge-1)
phi
```

$$\left [ 17, \quad 42, \quad 50, \quad 9\right ]$$

**Step 3**
```python
x = symbols('x', integer=True, positive=True)
f = Poly(reversed([secret]+phi), x)
f
```

$$\operatorname{Poly}{\left( 9 x^{4} + 50 x^{3} + 42 x^{2} + 17 x + 42, x, domain=\mathbb{Z} \right)}$$

**Step 4**
```python
f_xi = [f(x)%p for x in xi]
f_xi
```

$$\left [ 25, \quad 11, \quad 30, \quad 55, \quad 73, \quad 2, \quad 42, \quad 81, \quad 59, \quad 53\right ]$$

```python
pairs = list(zip(xi, f_xi))
pairs
```

$$\left [ \left ( 3, \quad 25\right ), \quad \left ( 51, \quad 11\right ), \quad \left ( 85, \quad 30\right ), \quad \left ( 33, \quad 55\right ), \quad \left ( 7, \quad 73\right ), \quad \left ( 35, \quad 2\right ), \quad \left ( 81, \quad 42\right ), \quad \left ( 2, \quad 81\right ), \quad \left ( 1, \quad 59\right ), \quad \left ( 26, \quad 53\right )\right ]$$

**Recovering the secret**
```python
data = random.sample(pairs, knowledge)
data
```

$$\left [ \left ( 81, \quad 42\right ), \quad \left ( 3, \quad 25\right ), \quad \left ( 1, \quad 59\right ), \quad \left ( 7, \quad 73\right ), \quad \left ( 85, \quad 30\right )\right ]$$

```python
xi2, f_xi2 = list(zip(*data))
xi2, f_xi2
```

$$\left ( \left ( 81, \quad 3, \quad 1, \quad 7, \quad 85\right ), \quad \left ( 42, \quad 25, \quad 59, \quad 73, \quad 30\right )\right )$$

Source: https://stackoverflow.com/questions/4798654/modular-multiplicative-inverse-function-in-python/4798776

```python
def egcd(a, b):
    if a == 0:
        return (b, 0, 1)
    else:
        g, y, x = egcd(b % a, a)
        return (g, x - (b // a) * y, y)

def modinv(a, m):
    g, x, y = egcd(a, m)
    if g != 1:
        raise Exception('modular inverse does not exist')
    else:
        return x % m
```

```python
def lagrange_interpolation(u, v):
    assert len(u) == len(v)
    n = len(u)
    P = 0
    for i in range(n):
        s = v[i]
        for j in range(n):
            if i == j:
                continue
            s *= (x - u[j])*modinv((u[i]-u[j])%p, p)
        P += s
    return poly(expand(P, modulus=p))
```


```python
P = lagrange_interpolation(xi2, f_xi2)
P
```

$$\operatorname{Poly}{\left( 9 x^{4} + 50 x^{3} + 42 x^{2} + 17 x + 42, x, domain=\mathbb{Z} \right)}$$

Lets verify that our interpolation polynomial is correct.

```python
f==P
```

    True

Now we can recover the secret and verify that it is correct.

```python
P(0)
```

$$42$$

```python
P(0) == secret
```

    True


## Problem 2
Let \(R\) be a ring and let \(q,r∈R[x]\) with \(a = q b + r\) and \(\deg r < \deg b\) where \(b\) monic.

### (a)
Show that for all \(ξ∈R\) and \(f∈R[x]\) we have \(f(ξ)=f \operatorname{rem}\,(x-ξ).\)

---

Let \(a=f\) and \(b=(x-ξ)\) then
\[
\begin{aligned}
f(x) &= q(x)⋅(x-ξ) + r(x) \\
f(ξ) &= q(ξ)⋅(ξ-ξ) + r(ξ) \\
f(ξ) &= r(ξ) \\
f(ξ) &= f \operatorname{rem}\, (x-ξ). \\
\end{aligned}
\]

### (b)
Let \(a,b,c∈R[x]\), with \(b\) and \(c\) monic, and suppose that \(c\) divides \(b\). Show that \(a\operatorname{rem}c=(a\operatorname{rem}b)\operatorname{rem}c.\)

---

We have equalities \(a = q_1 b + r_1\) and
\(b = q_2 c + r_2\) where the remainders are \[r_1=a \operatorname{rem} b\] and \(r_2=0\) since \(c\) divides \(b\).

The remainder \(r_1\) can also be written in this form \(r_1 = q' c + r'\) where \(\deg r'<\deg c\). Then we have a remainder
\[
r'=r_1 \operatorname{rem} c = (a\operatorname{rem}b)\operatorname{rem}c.
\]

We also have
\[
\begin{aligned}
a &= q_1 b + r_1 \\
a &= q_1 (q_2 c) + (q' c + r') \\
a &= (q_1 q_2 + q') c + r'. \\
\end{aligned}
\]
Then the remainder \(r'\) has equivalency
\[
r'=a \operatorname{rem} c.
\]

By combining the equivalencies for the remainder \(r'\) we have
\[
a \operatorname{rem} c = (a \operatorname{rem} b) \operatorname{rem} c.
\]


## Problem 3
Let \(R\) be a ring, let \(ξ_0,ξ_1,...,ξ_{e-1}∈R\), and \(λ_0,λ_1,...,λ_{e-1}∈R\) be given as input. The form of the Lagrange interpolation polynomial suggests that one should first seek to construct the coefficients of the polynomial
\[
L_e(x)=∑_{i=0}^{e-1} λ ∏_{i=0\\i≠j}^{e-1}(x-ξ_j)∈R.
\]
Show that we can compute the coefficients of \(L\) in \(O(M(e)\log e)\) operations in \(R\). You may assume that \(e=2^k\) for a nonnegative integer \(k\). Here \(M(e)=e\log e \log\log e.\)

---

By expanding the Lagrange polynomials \(e∈\{1,2,4\}\) we can notice the common substructure within the computations
\[
\begin{aligned}
L_1(x)=& λ_0 \\
L_2(x)=& λ_0 (x-ξ_1) + λ_1 (x-ξ_0) \\
L_4(x)=& λ_0 (x-ξ_1) (x-ξ_2) (x-ξ_3) + \\
       & λ_1 (x-ξ_0) (x-ξ_2) (x-ξ_3) + \\
       & λ_2 (x-ξ_0) (x-ξ_1) (x-ξ_3) + \\
       & λ_3 (x-ξ_0) (x-ξ_1) (x-ξ_2) \\
      =& (λ_0 (x-ξ_1) + λ_1 (x-ξ_0)) ⋅ (x-ξ_2) (x-ξ_3) + \\
       & (λ_2 (x-ξ_3) + λ_3 (x-ξ_2)) ⋅ (x-ξ_0) (x-ξ_1).
\end{aligned}
\]

It can be generalized into a formula


---

In each non-root node the algorithm does the following computations:
\[
\begin{aligned}
s =& s_0 ⋅ s_1 \\
l =& l_0 ⋅ s_1 + l_1 ⋅ s_0.
\end{aligned}
\]
Since \(n=\deg s_i>\deg l_i\) for \(i\in\{0,1\}\) the total computational cost in each node is \(O(n \log n)\) using fast polynomial multiplication.

---

Total cost from multiplication operations, i.e. number of nodes \(2^i\) in depth \(i\) × the cost multiplying polynomials with maximum degree of \(n_i=2^{\log e - i}\)
\[
\begin{aligned}
& ∑_{i=0}^{\log e} 2^{i} ⋅ O(2^{\log e - i} \log 2^{\log e - i}) \\
=& ∑_{i=0}^{\log e} O(2^{i} ⋅ 2^{\log e - i} \log 2^{\log e - i}) \\
=& ∑_{i=0}^{\log e} O(2^{\log e} \log 2^{\log e-i}) \\
=& O(e \log e)
\end{aligned}
\]


## Problem 4


## References
