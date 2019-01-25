---
title: CS-E4500 Problem Set 1
author: Jaan Tollander de Balsch - 452056
date: \today
header-includes: \usepackage{unicode-math}
---
Two books used as a resources in this report are @introduction_to_algorithms, Chapter. 30, *Polynomials and FFT* and @modern_computer_algebra, Chapter. 8.2, *The Discrete Fourier Transform and the Fast Fourier Transform*.


## Problem 1
Multiplication with the discrete Fourier tranform. Let us multiply \(f=1+x+x^2∈ℤ_{13}[x]\) and \(g=2+12x^3∈ℤ_{13}[x]\) using the dicrete Fourier transform.

---

Let \(ω_n^k\) be the roots of unity for \(k=0,1,…,n-1\).

1) Evaluate the polynomials as the roots of unity (DFT)
\[α_k=f(ω_n^k)\]
\[β_k=g(ω_n^k)\]

2) Multiply the polynomials pointwise
\[γ_k=α_k⋅β_k\]

3) Recover the coffiecients of the polynomial using inverse DFT
\[a_j=n^{-1}∑_{k=0}^{n-1}γ_k (ω_n^{-1})^{kj}\]

---

The order of the resulting polynomial \(n=6\) and its inverse \(n^{-1}=6^{-1}=11 ∈ ℤ_{13}.\)

The primitive root of unity \(ω_6=4\) and its inverse \(w_6^{-1}=4^{-1}=10 ∈ ℤ_{13}.\)

The power of the root of unity of order \(6\) are \(ω_6^0,...,ω_6^5\)
\[\left [ 1, \quad 4, \quad 3, \quad 12, \quad 9, \quad 10\right ]\]

The values of polynomial \(f\) evaluated at \(w_6^k\) are \(α_0,...,α_5\)
\[\left [ 3, \quad 8, \quad 0, \quad 1, \quad 0, \quad 7\right ]\]

The values of polynomial \(g\) evaluated at \(w_6^k\) are \(β_0,...,β_5\)
\[\left [ 1, \quad 3, \quad 1, \quad 3, \quad 1, \quad 3\right ]\]

The values of the pointwise product \(γ_k=α_k⋅β_k\) for \(k=0,...,5\) are
\[\left [ 3, \quad 11, \quad 0, \quad 3, \quad 0, \quad 8\right ]\]

The powers of the inverses of the primitive roots of unity are \((ω_6^{-1})^0,...,(ω_6^{-1})^5\)
\[\left [ 1, \quad 10, \quad 9, \quad 12, \quad 3, \quad 4\right ]\]

Finally, the inverse discrete Fourier tranform gives us the coefficients \(a_0,...,a_5\) of the polynomial
\[\left [ 2, \quad 2, \quad 2, \quad 12, \quad 12, \quad 12\right ]\]

We can verify that
\[
f⋅g=2+2x+2x^2+12x^3+12x^4+12x^5∈ℤ_{13}[x]
\]
using for example the naive multiplication algorithm.


## Problem 2
The convolution identity. Let \(ω∈R\) be a primitive root of unity of order \(n\) in a ring \(R\). Show that for all \(f,g∈R[x]/⟨x^n-1⟩\) we have \(DFT_ω(fg)=DFT_ω(f)⋅DFT_ω(g)\).

---

The polynomial \(fg∈R[x]/⟨x^n-1⟩\) is given by the convolution
\[
(f*g)≡f·g\mod x^n-1.
\]
The by evaluation \(f*g\) in the roots of unity \(ω^j\) for \(j=0,1,...,n-1\) gives us
\[
\begin{aligned}
(f*g)(ω^j) &= f(ω^j)⋅g(ω^j) + q(ω^j)⋅(ω^j-1), ω^j-1=0 \\
&= f(ω^j)⋅g(ω^j).
\end{aligned}
\]

This proves the indentity
\[
\begin{aligned}
DFT_ω(f * g) &= [(f*g)(ω^0),...,(f*g)(ω^{n-1})] \\
&= [f(ω^0)⋅g(ω^0),...,f(ω^{n-1})⋅g(ω^{n-1})] \\
&= [f(ω^0),...,f(ω^{n-1})] ⋅ [g(ω^0),...,g(ω^{n-1})] \\
&= DFT_ω(f)⋅DFT_ω(g).
\end{aligned}
\]


## Problem 3



## Problem 4


## References
