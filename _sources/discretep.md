# Discrete Probability

A **random experiment** consists of drawing a sample of $k$ elements from a set
$S$ of cardinality $n$. The possible outcomes are exactly the objects we counted
in the previous chapter. 

Let's say we toss a coin four times. $S=\{H,T\}$, and we are drawing 4 elements
with replacement. An example of a sample point is $HTHT$, and the sample space 
$\Omega$ has 16 elements.

A **probability space** is a sample space $\Omega$, together with a probability
$\mathbb{P}[\omega]$ (also denoted $Pr[\omega]$) for each sample point $\omega$,
such that:

* $0\leq\mathbb{P}[\omega],\forall\omega\in\Omega$
* $\sum_{\omega\in\Omega}\mathbb{P}[\omega]$, the sum of probabilities over
all outcomes is 1.

The easiest way to assign probabilities to sample points is to do so uniformly.

The probability of an event $A$ is the sum of probabilities of sample points in
$A$. For any event $A\subseteq\Omega$, we define its probability to be

$$\mathbb{P}[A]=\sum_{\omega\in A}\mathbb{P}[\omega]$$

Note that $0\leq\mathbb{P}[A]\leq 1$ for all $A\subseteq\Omega$, and $\mathbb{P}
[\Omega]=1$.

## The Monty Hall Problem

In a famous game show hosted by Monty Hall, contestants are given a choice of
three doors: behind one door is a prize, while behind the other two are goats.
The contestant picks a door without opening it, then Hall's assistant opens one
of the other two doors, revealing a goat (the assistant always knows which door
has the prize). The contestant is then given the choice of staying with their
choice, or switching.

Intuitively, all three doors have an equal probability, and with only two doors
remaining, they still have an equal probability of having the prize. However, it
is actually beneficial to switch!

Here's why. When the contestant first picks the door, they have a $\frac{1}{3}$
of picking the right door. The other doors have a $\frac{2}{3}$ chance of having
the prize. But after the assistant opens the door with the goat behind it, these
probabilities do not change, and thus, the door you can switch to continues to
have a $\frac{2}{3}$ chace of having the prize!

We can describe the outcome of the game in the form of $(i, j, k)$, where $i, j,
k \in\{1, 2, 3\}$. The values $i$i, $j$, $k$ respectively specify the location
of the prize, the initial door chosen by the contestant, and the door opened by
the assistant. Taking out invalid entries (e.g., (1,2,1)) shows us there are 12
sample points.

There are six winning outcomes, each having $i=j$, and we have completely
defined our probability space. The sum of probabilities of all outcomes is 1.

Let's supposed the contesant decides to switch doors. In order to win, their
initial choice cannot be equal to the prize fdoor. All outcomes of this type
cannnot be the prize door, and all outcomes of thys type correspond to a win for
the contestant. $\mathbb{P}[\omega]=6\times\frac{1}{9}=\frac{2}{3}$