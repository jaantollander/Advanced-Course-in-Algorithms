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

---

By assuming \(C≠AB\) we have \((C-AB)≠\mathbf{0}\). Then what is the probability that
\[
(C-AB)x≠0,
\]
where \(x∈\{0,1\}^n⊆F^n\) is a binary vector.

- \(2^n\) binary strings
- \(2^{n^2}\) matrices
- How many binary vectors \(x\) there are such that \(Cx≠A(Bx)\) when \(C≠AB\)
- What about \(Cx=A(Cx)\)
- TODO: the probability that \(Cx≠A(Bx)\) when \(C≠AB\) for some \(x\)
- TODO: symmetry to prove that probability is \(1/2\)


## Problem 3
## Problem 4
## References
