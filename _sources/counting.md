# Counting

## Counting with Replacement
Before we get into probabilities, let us first learn how to count the number of
outcomes. In this section, we will consider counting in scenarios where we
cannot choose two of the same object/event.

### First Rule of Counting
First, consider the scenario with the set $S_1=\{1,2,\cdots,n\}$, where we would 
like to choose k elements, where k is an integer less than n. How many ways
are there to do this?

The First Rule of Counting states that if an object can be made by a 
succession of $k$ choices, where there are $m_1$ ways to make the first
choice,  and for every way of making the first choice there are $m_2$ ways
of making the second choice, and for every way of making the second choice
there are $m_3$ ways of making the third choice (and so on and so forth 
until the $m^{th}_k$ choice), then the total number of distinct objects
that can be made in this way is $m_1\times m_2 \times \cdots \times m_k=
\prod^k_{i=1}m_i$.

So in the example above, after selecting the first element, there are
$n−1$ ways to make the second choice, and $n−2$ ways to make the third, so
on and so forth, until there are $n−k+1$ ways to make the $k$-th choice.

### Second Rule of Counting
Consider the scenario where we have the set S2, and we want to select k 
distinct elements in any order. How many ways are there to choose these
elements to obtain the same outcome?

The Second Rule of Counting states that assuming an object is made by a 
succession of choices in which the order does not matter, if there exists 
an m-to-one function f from the set of ordered objects to the set of 
unordered objects, we can count the number of ordered objects by pretending
the order matters, then divide by $m$ (the number of ordered objects per
unordered objects) to obtain the number of unordered objects, $|B|$. In 
other words, $|B|=\frac{|A|}{m}$.

For example, in a friend group of 10 people, how many ways are there to
pick 4 people to be on your team? We can first count how many different 
ways there are to pick 4 people to be on our team assuming the order 
matters, then divide by the number of ways 4 people on one team can be 
ordered. This is equal to $\frac{10!}{6!}\times{1}{4!}$.

This notation is so common, there is a special way to write it 
$\binom{n}{k}=\frac{n!}{(n−k)!k!}$.

## Counting with Replacement
Suppose we want to consider the scenario where after selecting something,
we replace it back into the set we choose from, and where order still 
matters. We can now have $n$ ways of choosing at every round, and we can
now select $n^k$ different sequences of objects in choosing $k$ items from
a set of $n$.

A good example would be coin tosses. In tossing two coins, getting heads
the first time does not preclude you from getting heads the second time.
Another example would be rolling a dice; tossing two dice allows you to
get two sixes, two fives, two fourths, or so on and so forth.

### Zeroth Rule of Counting
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
