# Inclusion-Exclusion Principle

The Principle of Inclusion-Exclusion is used to count the number of elements
in the union of non-disjoint sets, and states that 

$$A_1\cup\cdots\cup A_n =\sum_{k=1}^n(-1)^{k-1}\sum_{S\subset{1,\cdots,n}:|S|
=k}|\cap_{i\in S}A_i|$$

Consider the smaller example where $n=2$. To count the number of elements in
the union of $A_1$ and $A_2$, where they are not disjoint, $|A_1\cup A_2| =
|A_1|+|A_2|-|A_1\cap A_2|$, to correct for overcounting their common elements.

Likewise, when $n=3$, we first subtract $|A_1\cap A_2| + |A_2\cap A_3| + |A_1
\cap A_3|$ from the sum of $|A_i|$'s. However, now we have undercounted; we
are ignoring elements where $|A_1\cap A_2\cap A_3|$. So the full formula becomes
$|A_1|+|A_2|+|A_3|-|A_1\cap A_2|-|A_2\cap A_3|-|A_1 \cap A_3|+|A_1\cap A_2
\cap A_3|$.

The Principle of Inclusion-Exclusion is only a generalization of this concept.

There are two ways to prove this,
1. Induction on $n$.
2. Combinatorial Proof.

Both are left as an exercise.

More importantly, we can apply this to the previous concept of derangements.
Let $A_i$ denote the set of all permutations where $i$ if a fixed point. Since
there are $n!$ distinct permutations of $\{1,\cdots,n\}$ and 
$|A_1\cup\cdots\cup A_n|$ counts the number of permutations with at least one
fixed point, we have

$$\begin{gather}D_n=n!-|A_1\cup\cdots\cup A_n|\end{gather}$$

What is the cardinality of $A_i$? Since $i$ maps to $i$, and the remaining
elements can be arranged in any which way, $|A_i|$ is thus $(n-1)!$. For $i
\not = j$, $i$ maps to $i$ and $j$ maps to $j$, while the remaining $n-2$
elements can be arranged arbitrarily, giving $|A_i\cap A_j|=(n-2)!$.

In general, for any subset $S\subset\{1,\cdots,n\}$ of size $|S|=k$, $|\cap_
{i\in S}A_i|=(n-k)!$, while there are $\binom{n}{k}$ such subsets. Thus,
the inclusion-exclusion formula gives:

$$|A_1\cup\cdots\cup A_n|=\sum_{k=1}^n(-1)^{k-1}\binom{n}{k}(n-k)!$$
$$=\sum_{k=1}^n(-1)^{k-1}\frac{n!}{k!(n-k)!}=n!\sum^n_{k=1}\frac{(-1)^{k-1}}{k!}$$

Substituting this into (1) gives us:

$$D_n=n!-n!\sum^n_{k=1}\frac{(-1)^{k-1}}{k!}
=n!\sum^n_{k=1}\frac{(-1)^k}{k!}$$
