# Conditional Probability
In probability theory, **conditional probability** is a measure of the
probability of an event occurring given that another event has occurred. For
example, given that you have already gotten an ace in your hand of poker, what
is the probability you get another ace?

Let $B$ denote the event that you already have an ace and let $A$ denote the 
event that you get another ace. In the language of conditional probability, we
wish to calculate "the probability of A given B", denoted by $\mathbb{P}[A|B]$.

To calculate this, because event $B$ is guaranteed to happen, we should not look
at the whole sample space $\Omega$, but at the smaller sample space consisting
of the sample points in $B$. Sum the probabilities of the sample points in $B$,
then sum the probabilities of those where $A$ occurs. For events $A, B \subseteq
\Omega$ in the same probability space such that $\mathbb{P}[B]>0$, the
conditional probability of $A$ given $B$ is:

$$\mathbb{P}[A|B]=\sum_{\omega\in A\cap B}\mathbb{P}[\omega|B]=\sum_{\omega\in A
\cap B}\frac{\mathbb{P}[\omega]}{\mathbb{P}[B]}=\frac{\mathbb{P}[A\cap B]}
{\mathbb{P}[B]}$$

## Bayesian Inference
Conditional probability is at the heart of *Bayesian inference*, a way to update
knowledge after making an observation. For example, after estimating $\mathbb{P}
[A]$, event $B$ occurs, and we might adjust this estimate to $\mathbb{P}[A|B]$.
$\mathbb{P}[A]$ can be thought of as a *prior* probability, reflecting our prior
knowledge, while $\mathbb{P}[A|B]$ can be interpreted as the posterior
probability of $A$ after the observation, reflecting our updated knowledge.

An example would be a random person whom we suspect of having COVID-19. There is
a test that has a false negative rate of 10%, and a false positive rate of 20%.
In city X, we estimate 5% of the population has COVID-19; how do we update our
probability of this person having COVID-19, after he tests negative?

* The sample space is all people in city X.
* Let $A$ be the event a person chosen at random has COVID-19.
* Let $B$ be the event a person chosen at random tests positive.

Rewrite the information above as:

* $\mathbb{P}[A]=0.05$
* $\mathbb{P}[B|A]=0.9$
* $\mathbb{P}[B|\overline{A}]=0.2$

*Equation 1*:

$$\mathbb{P}[A|B]=\frac{\mathbb{P}[A\cap B]}{\mathbb{P}[B]}=\frac{\mathbb{P}
[B|A]\mathbb{P}[A]}{\mathbb{P}[B]}$$

where we obtained the second equality by applying the definition of conditional
probability. We still need to calculate $\mathbb{P}[B]$:

*Equation 2*:

$$\mathbb{P}[B]=\mathbb{P}[A\cap B]+\mathbb{P}[\bar{A}\cap B]=\mathbb{P}[B|
A]\mathbb{P}[A]+\mathbb{P}[B|\bar{A}]\mathbb{P}[\bar{A}]=\mathbb{P}[B|A]
\mathbb{P}[A]+\mathbb{P}[B|\bar{A}](1-\mathbb{P}[A])$$

We combine the above two equations to get the following formula:

$$\mathbb{P}[A|B]=\frac{\mathbb{P}[B|A]\mathbb{P}[A]}{\mathbb{P}[B|A]\mathbb{P}
[A]+\mathbb{P}[B|\bar{A}](1-\mathbb{P}[A])}$$

## Bayes' Rule and Total Probability Rule
Equations 1 and 2 are very useful in their own right: equation 1 is the **Bayes'
Rule**, while equation 2 is the **Total Probability Rule**.

The Bayes' Rule is useful when one wants to calculate $\mathbb{P}[A|B]$ but
given $\mathbb{P}[B|A]$ instead. The Total Probability Rule is a strategy of
dividing into cases, where either A happens or does not happen. If we know the
probability $B$ happens when $A$ happens or does not happen, and also the 
probability $A$ happens, we can use the Total Probability Rule to find $\mathbb{
P}[B]$.

### Generalized Bayes' and Total Probability

An event $A$ is partitioned into events $n$ events $A_1, \cdots, A_n$ if:

1. $A = A_1 \cup A_2 \cup \cdots \cup A_n$, and
2. $A_i \cap A_j$ for all $i\not = j$($A_1, \cdots, A_n$ are mutually exclusive)

In other words, each outcome in $A$ belongs to exactly one of its partitions.

Now, let $A_1,\cdots, A_n$ be a partition of the sample space \Omega$. The Total
Probability Rule for any event $B$ is:

$$\mathbb{P}[B]=\sum_{i=1}^n\mathbb{P}[B\cap A_i]=\sum_{i=1}^n\mathbb{P}[B|A_i]
\mathbb{P}[A_i]$$

while Bayes' rule, assuming $\mathbb{P}[B]\not =0$, is given by:

$$P[A_i|B]=\frac{\mathbb{P}[B|A_i]\mathbb{P}[A_i]}{\mathbb{P}[B]}=\frac{\mathbb{
P}[B|A_i]\mathbb{P}[A_i]}{\sum_{j=1}^n\mathbb{P}[B|A_j]\mathbb{P}[A_j]}$$

where the second equality follows from the Total Probability Rule.

## Combinations

In many situations, we are interested in things like $\mathbb{P}[\cup_{i=1}^nA_i
]$ and $\mathbb{P}[\cap^n_{i=1}A_i]$, where the $A_i$ are simple events. The
intersection corresponds to the logical "AND" of events $A_i$, while the union
correspond to the logical "OR" of events $A_i$.

### Independent Events

Two events $A, B$ in the same probability space are said to be **independent**
if $\mathbb{P}[A\cap B]=\mathbb{P}[A]\times\mathbb{P}[B]$.

In other words, the probability of $A$ is not affected by whether or not $B$
occurs. Intuitively, $\mathbb{P}[A|B]=\mathbb{P}[A]$. Examples of independent
events include rolls of the dice or coin flips. 

We can generalize our above definitions to the following two:

Events $A_1,\cdots,A_n$ are said to be **mutually independent** if for every
subset $I\subseteq\{1,\cdots,n\}$ with size $|I|\geq 2$,

$$\mathbb{P}[\cap_{i\in I}A_i]=\prod_{i\in I}\mathbb{P}[A_i]$$

An equivalent definition of the above is:

Events $A_1,\cdots,A_n$ are said to be **mutually independent** if for all $B_i
\in \{A_i, \bar{A_i}\}, $i=1,\cdots,n$.

In the second defintion, $2^n$ constraints are imposed, vs. the $2^n-n-1$ by the
first definition. The additional $n+1$ constraints imposed by the second
definition turn out to be redundant.

### Intersections of Events

Below is the **Product Rule**:

```{admonition} Theorem
For any events $A,B$, we have

$$\mathbb{P}[A\cap B]=\mathbb{P}[A]\mathbb{P}[B|A].$$

More generally, for events $A_1,\cdots,A_n$,

Events $A_1,\cdots,A_n$ are said to be **mutually independent** if for every
subset $I\subseteq\{1,\cdots,n\}$ with size $|I|\geq 2$,
```

```{admonition} Proof
The first assertion follows directly from the definiiton of $\mathbb{P}[B|A]$
(and is in fact a special case of the second assertion with $n=2$).

To prove the second assertion, we will use induction on $n$. The base case is
$n=1$, and states $\mathbb{P}[A]=\mathbb{P}[A]$, which is true. Assume for
arbitrary $n>1$, assume the following is ture:

$$\mathbb{P}[\cap_{i=1}^{n-1}A_i]=\mathbb{P}[A_1]\times\mathbb{P}[A_2|A_1]\times
\cdots\times\mathbb{P}[A_{n-1}|\cap_{i=1}^{n-2}]$$

Now, apply the definition of conditional probability to the two events $A_n$ and
$\cap_{i=1}^{n-1}A_i$ to deduce that:

$$\mathbb{P}[\cap{i=1}^nA_i]=\mathbb{P}[A_n\cap(\cap_{i=1}^{n-1}A_i)]=
\mathbb{P}[A_n|\cap_{i=1}^{n-1}A_i]\times\mathbb{P}[\cap_{i=1}^{n-1}A_i]\\
=\mathbb{P}[A_n|\cap_{i=1}^{n-1}A_i]\times\mathbb{P}[A_1]\times\mathbb{P}[A_2|
A_1]\times\cdots\times\mathbb{P}[A_{n-1}|\cap_{i=1}^{n-2}]$$

where in the last line we use the inductive hypothesis, completing the proof.
```

The Product Rule is useful when we can view our sample space as a sequence of
choices. The next few examples illustrate this point.

### Unions of Events
In the union of events, you should use the **Principle of Inclusion-Exclusion**,
which is recapped as:

```{admonition} Theorem
Let $A_1, \cdots, A_n$ be events in some probability space where $n\geq 2$.
Then, we have

$$\mathbb{P}[A_1\cup\cdots\cup A_n]=\sum_{k=1}^n(-1)^{k-1}\sum_{S\subseteq\{1,
\cdots,n\}:|S|=k\mathbb{P}[\cap_{i\in S}A_i]$$

where the right hand side can be written as:

$$\mathbb{P}[\cup_{i=1}^nA_i]=\sum_{i=1}^n\mathbb{P}[A_i]-\sum_{i<j}\mathbb{P}
[A_i\cap A_j]+\sum_{i<j<k}\mathbb{P}[A_i\cap A_j\cap A_k]-\cdots+(-1)^{n-1}
\mathbb{P}[A_1\cap A_2\cap \cdots A_n]$$
```

When $n$ is large, the Inclusion-Exclusion formula is essentially useless as it
involves computing the probability of every non-empty subset of the events, and
there are $2^n-1$ of these! Sometimes, we can just use the first few terms and
forget the rest, as the subsequent terms give over and under-estimates that get
better as we go along.

In many events, we can even get away with only using the first term:

1. If the events $A_1, \cdots, A_n$ are mutually exclusive, then $\mathbb{P}
[cup_{i=1}^nA_i]=\sum_{i=1}^n\mathbb{P}[A_i]$.
2. Let $A_1, \cdots, A_n$ be events in some probability space. Then, for all
$n\in\mathbb{Z}^+$,$\mathbb{P}[\cup_{i=1}^nA_i]\leq\sum_{i=1}^n\mathbb{P}[A_i]$.