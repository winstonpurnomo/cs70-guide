# Induction
Mathematical nduction is an additional method of proofing that we will cover in 
further detail. Induction is a tool that can be used to establish the truth of a
statement over all natural numbers.

* Goal: To prove $P$ for all values of $n$.
* Approach:
  1. Prove $P$ is true for a base case (usually $n=0$ or $n=1).
  2. Assume $P$ is true for some arbitrary $n=k$.
  3. Show $P$ is true for $n=k+1$, assuming $P$ holds for $n=k$.

```{admonition} Theorem
$$\forall n\in\mathbb{N}, \sum_{i=0}^ni=\frac{n(n+1)}{2}$$.
```

```{admonition} Proof
*Base case* ($n=0$): $\sum_{i=0}^0i=0=\frac{0(0+1)}{2}$. The base case holds.

*Induction Hypothesis*: For an arbitrary $n=k\geq 0$, assume that $\sum_{i=0}^k
i=\frac{k(k+1)}{2}$.

*Inductive Step*:

$$\sum_{i=0}^{k+1}i=\sum_{i=0}^{k}i+(k+1)=\frac{k(k+1)}{2}+(k+1)=\frac{k(k+1)+
2(k+1)}{2}=\frac{(k+1)(k+2)}{2}$$,

where the second equality follows from the Induction Hypothesis. By the 
principle of mathematical induction, the claim follows.
```

## Strengthening the Inductive Hypothesis
When using induction, it is possible to choose a statement that is too broad or
general to prove. For example, suppose we were proving the following statement:
*for all $n\geq 1$, the sum of the first $n$ odd numbers is a perfect square.*

```{admonition} Proof
*Base case*($n=1$): This holds.

*Induction Hypothesis*: Assume the sum of the first $k$ odd numbers is a perfect
square, say $m^2$.

*Inductive Step*: The $(k+1)^{st}$ odd number is $2k+1$. By the I.H., the sum
of the first $k+1$ odd numbers is $m^2+2k+1$, which doesn't prove anything.
```

Now, if we strengthened the inductive hypothesis to:
*for all $n\geq 1$, the sum of the first $n$ odd numbers is $n^2$.*

```{admonition} Proof
*Base case*($n=1$): This holds.

*Induction Hypothesis*: Assume the sum of the first $k$ odd numbers is a perfect
square $k^2$.

*Inductive Step*: The $(k+1)^{st}$ odd number is $2k+1$. By the I.H., the sum
of the first $k+1$ odd numbers is $k^2+2k+1=(k+1)^2$. Thus, bu the principle of
induction, the theorem holds.
```

## Strong Induction
What we have done so far is a notion of induction known as *simple* or *weak*
induction. We will now use a different notion called *strong* induction, where 
we modify the induction hypothesis: instead of assuming just $P(k)$ is true, we
assume the stronger statement that $P(i\leq k), \forall i \in\mathbb{N}$ is
true.

There is no difference in the power of strong and weak induction: there are no
statements you can only prove with strong induction and not weak induction. But
strong induction can make proofs easier and more concise.

```{admonition} Theorem
Every natural number $n>1$ can be written as a product of one or more primes.
```

```{admonition} Proof
*Base case*($n=2$): Clearly, $P(2)$ holds since 2 is a prime.

*Induction Hypothesis*: Assume $P(n)$ is true for all $2\leq n\leq k$.

*Inductive Step*: We have two cases, either $k+1$ is a prime number, or it is
not.

In the first case, if $k+1$ is a prime number, then we are done as it is the
product of one prime, itself.

In the second case, if $k+1$ is not a prime, then by definition, $k+1=xy$ for
some $x, y\in\mathbb{Z}^+$ satisfying $1<x,y<k+1$. By the I.H., $x$ and $y$ can
each be written as the product of primes (since $x,y\leq n$). This therefore
implies $k+1$ can also be written as a product of primes.
```