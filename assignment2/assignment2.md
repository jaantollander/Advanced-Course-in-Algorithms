---
title: CS-E4500 Problem Set 1
author: Jaan Tollander de Balsch - 452056
date: \today
header-includes: \usepackage{unicode-math}
---
Two books used as a resource in this report are @introduction_to_algorithms, Chapter. 30, *Polynomials and FFT* and @modern_computer_algebra, Chapter. 8.2, *The Discrete Fourier Transform and the Fast Fourier Transform*.

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

The order of the resulting polynomial \(n=6\) and its inverse \(n^{-1}=11 ∈ ℤ_{13}\)

The primitive root of unity \(ω_6=4\) and its inverse \(w_6^{-1}=10 ∈ ℤ_{13}\)

Polynomials \(f\) and \(g\)

The power of the root of unity of order \(6\) are \(ω_6^0,...,ω_6^5\)
\[\left [ 1, \quad 4, \quad 3, \quad 12, \quad 9, \quad 10\right ]\]

The values of polynomial \(f\) evaluated at \(w_6^k\) are \(α_0,...,α_5\)
\[\left [ 3, \quad 8, \quad 0, \quad 1, \quad 0, \quad 7\right ]\]

The values of polynomial \(g\) evaluated at \(w_6^k\) are \(β_0,...,β_5\)
\[\left [ 1, \quad 3, \quad 1, \quad 3, \quad 1, \quad 3\right ]\]

The values of the pointwise product \(γ_k=α_k⋅β_k\) are
\[\left [ 3, \quad 11, \quad 0, \quad 3, \quad 0, \quad 8\right ]\]

The powers of the inverse of the primitive root of unity are \((ω_6^{-1})^0,...,(ω_6^{-1})^5\)
\[\left [ 1, \quad 10, \quad 9, \quad 12, \quad 3, \quad 4\right ]\]

Finally, the inverse discrete Fourier tranform gives us the coefficients \(a_0,...,a_5\) of the polynomial
\[\left [ 2, \quad 2, \quad 2, \quad 12, \quad 12, \quad 12\right ]\]


## Problem 2


## Problem 3


## Problem 4


## References
