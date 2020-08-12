# Proofs in Combinatorics
We would now like to dive a little bit into proofs involving combinatorial
theory. Let's first start by proving the binomial theorem, which states
that:

$$ (a+b)^n = \sum^{n}_{k=0}\binom{n}{k}a^kb^{n-k} $$

## Binomial Theorem Proof

```{admonition} Proof
$$ (a+b)^n = \sum^{n}_{k=0}\binom{n}{k}a^kb^{n-k} $$
$$ \underbrace{(a+b)\times(a+b)\times\cdots\times(a+b)}_{n}=\sum^{n}_{k=0}
\binom{n}{k}a^kb^{n-k} $$

When $(a+b)\times(a+b)\times\cdots\times(a+b)$ is expanded via
multiplifcation, it will result in a sum over $2^n$ monomials, and to each
monomial in the sum, each factor $f_i$ contributes either an $a$ or a $b$.

The monomial $a^kb^{n-k}$ is obtained when $k$ copies of $a$'s and
$n-k$ copies of $b$'s are multiplied. There are exactly $\binom{n}{k}$ ways
to choose $k$ copies of $a$'s and $n-k$ copies of $b$'s from the $n$ factors
of $(a+b)$.

```

This theorem has numerous applications. For example,

$$\sum^n_{k=-}(-1)^k\binom{n}{k}=0, \forall n\in \mathbb{N}$$

## Hockey-Stick Proof

$$\binom{n}{k}=\binom{n-1}{k}+\binom{n-2}{k}+\cdots+\binom{k}{k}$$

```{admonition} Proof
We can verify this proof by considering what it means to choose $k+1$
elements from a set $S={1,2,\cdots, n}$.

Imagine we pick the lowest-numbered eleemnt of $X$. If we picked 1, to finish
constructing $S$, we would then have to choose $k$ elements from the remaining
$n-1$ elements, which is expressed by $\binom{n-1}{k}$. In another scenario,
we select the lowest numbered element as 2, and the ways we can select the
remaining elements is expressed by $\binom{n-2}{k}$. This goes on until 
$n-k$ is selected as the lowest numbered element, because we cannot complete
the set if we select any higher number.

These possibilities are all unique, so we can directly sum them to build

$$\binom{n-1}{k}+\binom{n-2}{k}+\cdots+\binom{k}{k}$$
```

## Derangements

A permutation with no fixed points is called a **derangement**.

What is a fixed point? Consider the scenario where in a class of $n$
students, we collect and randomly redistribute their homework. If we repeated
this experiment many times, on average how many students receive their own
homework?

Label the homeworks as $1, 2, \cdots, n$. Let $\pi_i$ denote the homework
returned to the $i$-th student. $\pi_1, \cdots, \pi_n$ corresponds to a
permutation of the set $\{1, 2, \cdots, n\}$. In total, there are $n!$
distinct permutations of $\{1, 2, \cdots, n\}$.

A student receives their own homework iff $\pi_i=i$. This turns the question
into, on average, how many indices for which $\pi_i=i$? These are known as
*fixed points* of the permutation $\pi$.

Consider when $n=3$. Derangements of this set are $\{2, 3, 1\}, \{3,1,2\}$.
When $n=4$, derangements are $\{2,1,4,3\},$ $\{2,4,1,3\},$ $\{4,1,2,3\},$
$\{4,3,2,1\},$ $\{3,4,2,1\},$ $\{2,3,4,1\},$ $\{3,4,1,2\},$ $\{4,3,1,2\},$
$\{3,1,4,2\}$.

**Theorem**: For an arbitrary positive integer $n\geq3$, the number of
derangements of $\{1,2,\cdots,n\}$ $D_n$ satisfies

$$D_n=(n-1)(D_{n-1}+D_{n-2})$$.

```{admonition} Proof
In a derangement $(\pi_1, \cdots, \pi_n)$, suppose $\pi_n=j\in
\{1,\cdots,n-1\}$, which states $j$ is what $n$ maps to under the
permutation. There are $n-1$ choices for $j$, which gives rise to the $n-1$
in the theorem (we exclude $j=n$ because we are counting derangements).

For a given value of $j\in{1,\cdots,n-1}$, there are two possible cases:


1. If $\pi_j=n$, then $j$ and $n$ get swapped and there is a one-to-one
correspondence between the set of derangements of the remaining elements, and
the set of derangements of $\{1, \cdots, n-2\}$. This gives $D_{n-2}$.

2. If $\pi_j\not =n$, then $n$ satisfies the same constraint as $j$, so
there is a one-to-one correspondence between the set of rearrangements of
$\{1,\cdots, j-1, j+1, \cdots, n\}$, and the set of derangements of $\{1,
\cdots, n-1\}$. This gives $D_{n-1}$.

Together with the boundary conditions of $D_1=0$ and $D_2=1$ by logic, $D_n$
can be efficiently determined in linear time using recursion and memoization.
We can even solve the recursion to yield an explicit formula:

$$D_n = n!\sum^n_{k=0}\frac{(-1)^k}{k!}$$
```