---
title: CS-E4500 Problem Set 3
author: Jaan Tollander de Balsch - 452056
date: \today
header-includes: \usepackage{unicode-math}
---
@modern_computer_algebra


## Problem 1
Arithmetic with rational numbers in radix-point representation.

---

A number in base \(B\) represented with radix-point representation can be written as a tuple \((d_B,r_B),\) where \(d_B\) are digits and \(r_B\) is the index of the radix point counted from right.

### (a)
Let us work in base \(B=3\). Multiply \(22122.21201\) and \(22121.22001\). Present the
result in radix-point representation.

---

The multiplication for radix point number is defined as \[(d_B,r_B)·(d_B,r'_B)=(d_B·d'_B,r_B+r'_B).\]

Then the multiplication of the two numbers given is
\[
(2212221201_3, 5_{10})+(2212122001_3, 5_{10})=(22022010111020220201, 10_{10})
\]
equivalently using the radix-point notation
\[
22122.21201_3 ⋅ 22121.22001_3 = 2202201011.1020220201_3
\]

### (b)
Let us work in base \(B = 7\). Add \(145.2332632\) and \(1345053.103\). Present the result
in radix-point representation.

---

The addition for radix point numbers is defined as
\[(d+pad(d', r-r'), r), r≥r',\]
where the operation \(pad(n,m)\) pads the integer \(n\) with \(m\) zeroes. This is mathematically equivalent to multiplying with \(B^{m}\).

Then the addition of the two numbers given is
\[
(1452332632_7, 7_{10})+(1345053103_7, 3_10)=(13452313362632_7, 7_{10})
\]
equivalently in radix-point notation
\[
145.2332632_7+1345053.103_7=1345231.3362632_7
\]


## Problem 2

## Problem 3
## Problem 4


## References
