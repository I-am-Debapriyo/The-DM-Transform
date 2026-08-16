# The-DM-Transform
<div align="center">

# The Mukherjee Identity
### *Parity-Folded Piecewise Summation*

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)
[![Python 3.8+](https://img.shields.io/badge/python-3.8+-brightgreen.svg)](https://www.python.org/)
[![Math](https://img.shields.io/badge/Mathematics-Number%20Theory-orange.svg)]()

**A novel, piecewise approach to calculating the sum of the first $n$ natural numbers using half-length sequences and linear correction terms.**

*Discovered and formulated by **Debapriyo Mukherjee***

---

</div>

##  Executive Summary

The classical summation formula discovered by Carl Friedrich Gauss calculates the sum of the first $n$ natural numbers as:

$$S_n = \frac{n(n+1)}{2}$$

**The Mukherjee Identity** introduces an alternative perspective. Instead of evaluating the sequence over the full range $n$, it reduces the primary arithmetic progression to roughly **half the length** ($\frac{n}{2}$ for even numbers, or $a = \frac{n-1}{2}$ for odd numbers), scales the result by a factor of 4, and applies a linear parity correction.

---

##  The Formulas

### 1. Even Parity ($n$ is even)

For any even natural number $n$:

$$S_n = 4 \left( \sum_{k=1}^{n/2} k \right) - \frac{n}{2}$$

> **Expanded Form:**
> $$S_n = 4 \left( 1 + 2 + 3 + \dots + \frac{n}{2} \right) - \frac{n}{2}$$

---

### 2. Odd Parity ($n$ is odd)

For any odd natural number $n$, let $a = \frac{n - 1}{2}$:

$$S_n = 4 \left( \sum_{k=1}^{a} k \right) + a + 1$$

> **Expanded Form:**
> $$S_n = 4 \left( 1 + 2 + 3 + \dots + a \right) + a + 1$$

---

## 🔍 Step-by-Step Examples

| $n$ | Parity | Half-Length Index | Core Sub-Sum $\sum k$ | Formula Calculation | Final Result |
| :---: | :---: | :---: | :---: | :---: | :---: |
| **4** | Even | $\frac{4}{2} = 2$ | $1 + 2 = 3$ | $4(3) - 2$ | **10** |
| **5** | Odd | $\frac{5-1}{2} = 2$ | $1 + 2 = 3$ | $4(3) + 2 + 1$ | **15** |
| **10** | Even | $\frac{10}{2} = 5$ | $1 + \dots + 5 = 15$ | $4(15) - 5$ | **55** |

---

## 🔬 Mathematical Proofs

<details>
<summary><b>▶ Click to expand Proof for Even Parity</b></summary>

<br>

Let $m = \frac{n}{2}$. Substituting the classical sum $\sum_{k=1}^{m} k = \frac{m(m+1)}{2}$ into the formula:

$$S_n = 4 \left( \frac{m(m+1)}{2} \right) - m$$

$$S_n = 2m(m+1) - m = 2m^2 + m$$

Now substitute $m = \frac{n}{2}$ back into the equation:

$$S_n = 2 \left(\frac{n}{2}\right)^2 + \frac{n}{2} = \frac{n^2}{2} + \frac{n}{2} = \frac{n(n+1)}{2} \quad \blacksquare$$

</details>

<details>
<summary><b>▶ Click to expand Proof for Odd Parity</b></summary>

<br>

Let $a = \frac{n-1}{2}$. Substituting the classical sum into the formula:

$$S_n = 4 \left( \frac{a(a+1)}{2} \right) + a + 1$$

$$S_n = 2a(a+1) + a + 1 = 2a^2 + 3a + 1$$

Now substitute $a = \frac{n-1}{2}$ back into the equation:

$$S_n = 2 \left(\frac{n-1}{2}\right)^2 + 3\left(\frac{n-1}{2}\right) + 1$$

$$S_n = \frac{n^2 - 2n + 1}{2} + \frac{3n - 3}{2} + \frac{2}{2} = \frac{n^2 + n}{2} = \frac{n(n+1)}{2} \quad \blacksquare$$

</details>

---

## 💻 Code Implementations

### Python

```python
def mukherjee_sum(n: int) -> int:
    """Calculates the sum of first n natural numbers using The Mukherjee Identity."""
    if n <= 0:
        raise ValueError("n must be a positive integer.")

    if n % 2 == 0:
        half = n // 2
        sub_sum = (half * (half + 1)) // 2
        return 4 * sub_sum - half
    else:
        a = (n - 1) // 2
        sub_sum = (a * (a + 1)) // 2
        return 4 * sub_sum + a + 1


# Test cases
if __name__ == "__main__":
    print(f"Sum of 1..100 : {mukherjee_sum(100)}")  # Output: 5050
    print(f"Sum of 1..99  : {mukherjee_sum(99)}")  # Output: 4950
