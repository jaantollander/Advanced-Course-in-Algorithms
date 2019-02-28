---
title: CS-E4500 Problem Set 6
author: Jaan Tollander de Balsch - 452056
date: \today
header-includes: \usepackage{unicode-math}
---

## Problem 1
Let \(F\) be a field with at least \(q\) elements.

### (a)
Let \(f,\tilde{f}∈F[x]\) be polynomials of degree at most \(d.\) Show that if \(f≠\tilde{f}\) then a uniform random \(ξ∈F\) satisfies \(f(ξ)≠\tilde{f}(ξ)\) with probability at least \(1-d/q.\)

---

By assuming that the polynomials are not equal \(f≠\tilde{f}\) the polynomial \(g=f-\tilde{f}\) is nonzero. The roots \(ξ\) of the polynomial \(g\) satisfy \(f(ξ)=\tilde{f}(ξ).\) Since \(g\) is nonzero it has at most \(d\) distinct roots \(ξ∈F.\) Therefore there is at most a probability \(d/q\) of picking a uniform random value \(ξ\) in \(F\) such that it satisfies \(f(ξ)=\tilde{f}(ξ)\). Equivalently, there is at least \(1-d/q\) probability that \(ξ\) satisfies \(f(ξ)≠\tilde{f}(ξ).\)

### (b)
Let \(a,b,c∈F[x]\) be three polynomials, each of degree at most \(d\) and each given as a sequence of coefficients. Present a randomized test that verified \(c=ab\) and uses \(O(d)\) operations in \(F.\) If \(c=ab\) the test must accept with probability \(1\); if \(c=ab\) the test must reject with probability at least \(1-d/q.\)

---

The probability is quaranteed by results from (a).

Evaluate the polynomials \(a, b, c\) at uniform random \(ξ∈F\) using the Horner's rule. Horner's rule uses \(O(d)\) operations in \(F\) and assumes constant \(O(1)\) complexity for addition and multiplication in \(F\). Then compute \(b(ξ)c(ξ)\) and do the comparison \(a(ξ)=b(ξ)c(ξ)\) which reduces to addition \(a(ξ)-b(ξ)c(ξ)=0\). Therefore the total number of operations required in for the test is \(O(d)+O(1)+(1)=O(d)\).


## Problem 2
Let \(A,B,C\) be three \(n×n\) matrices with entries in a field \(F.\) Present a randomized algorithm that tests whether \(C=AB\) using \(O(n^2)\) operations in \(F.\) When \(C=AB\), your algorithm must always assert that \(C=AB.\) When \(C≠AB,\) your algorithm must assert that \(C≠AB\) with probability at least \(1/2.\)

---

We have the following equality
\[
\begin{aligned}
C &= AB \\
Cx &= (AB)x \\
Cx &= A(Bx)
\end{aligned}
\]
where \(x∈F^n\) is a vector. Using this form of the equality, the equality testing will only require \(O(n^2)\) operations since the product of \(F^{n×n}\) matric and \(F^n\) vector has dimension of \(F^n\) and uses \(O(n^2)\) operations in \(F\) (unlinke naive matrix multiplication, which uses \(O(n^3)\)).

By assuming \(C≠AB\) we have nonzero matrix \(D=(C-AB)≠\mathbf{0}.\) Let \(x∈Ω=\{0,1\}^n⊆F^n\) be a binary vector. Then the probability that we choose a uniform random \(x\) such that \(Dx≠0\) is the same as the probability that \(Dx=0\) due to a symmetry.

**Proof**: Let the star \(⋆\) represent an element that is either \(0\) or \(1\). Let \(x∈Ω\) be a vector such that \(Dx≠0\). Then \(x\) consists of elements \(1\) and \(⋆\). Then we can construct a vector \(y∈Ω\) such that \(Dy=0\) by substituting all \(1\) with \(0\), but keeping stars \(⋆\) as stars. As an example:
\[
Dx=\left[\begin{matrix}
ε&0 \\
0&0
\end{matrix}\right]
\left[\begin{matrix}
1 \\
⋆
\end{matrix}\right] ≠ \mathbf{0}
\text{ then }
Dy=\left[\begin{matrix}
ε&0 \\
0&0
\end{matrix}\right]
\left[\begin{matrix}
0 \\
⋆
\end{matrix}\right] = \mathbf{0}
\]
where \(ε≠0\).

Because there is a vector \(y\) for every vector \(x\) this means that the probabilities are equal
\[
P(Dx=0)=P(Dx≠0).
\]
Also, probability theory gives us
\[
P(Dx=0)+P(Dx≠0)=1.
\]
Therefore the probability
\[
P(Dx≠0) = \frac{1}{2}.
\]


## Problem 3
## Problem 4
## References
