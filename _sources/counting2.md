# Counting with Replacement
Suppose we want to consider the scenario where after selecting something,
we replace it back into the set we choose from, and where order still 
matters. We can now have $n$ ways of choosing at every round, and we can
now select $n^k$ different sequences of objects in choosing $k$ items from
a set of $n$.

A good example would be coin tosses. In tossing two coins, getting heads
the first time does not preclude you from getting heads the second time.
Another example would be rolling a dice; tossing two dice allows you to
get two sixes, two fives, two fourths, or so on and so forth.

## Zeroth Rule of Counting
We now want to consider sampling with replacement where order does not 
matter. 

The **Zeroth Rule of Counting** states that if a set $A$ has a bijection
with the set $B$,then $|A| = |B|$.

For example, consider the scenario where we have an unlimited supply of
cooking ingredients in lettuce, tomatoes, carrots and zucchinis, and we 
want to select 3 ingredients to make a simple salad. 

In this example, $S = {L, T, C, Z}$, and $k = 3$. Ordering does not matter
because selecting a tomato then a lettuce leads to the same salad as
selecting a lettuce then a tomato.

We cannot apply the Second Rule of Counting because the number of ordered
options (the denominator) varies depending on which unordered object we
are considering. Thus, we must consider the problem using a different
approach.

Assume we have one bin for each unique element of $S$ for a total of $n$
bins. If we selected 2 tomatoes and 1 carrot, then bin 2 would have 2
elements, and bin 3 would have 1 element. In order to count the number of
multisets, we need to count how many different ways there are to fill the
4 bins with $k$ elements.

Visualize this by denoting $k$ elements with 0 in binary, and the separation
between bins with a 1. So in a scenario where bin 1 has 2 elements, and bin
3 has 1 element, but bin 2 is empty, we would denote this with $00110$. In
a different scenario where bins 1 and 3 are empty, but bin 2 has all 3
elements, then we would denote this with $10001$.

We can generalize to see the length of this binary string is $k+n-1$, and
there are $k$ zeros, while the remaining $n-1$ digits will have ones. Order
does not matter, and once we pick a location for one zero, we cannot pick it
again. Apply the Second Rule of Counting now to get $\binom{n+k-1}{k}$.

In the scenario above, we will have the solution as $\binom{4+3-1}{3}=
\binom{6}{3}$. 
