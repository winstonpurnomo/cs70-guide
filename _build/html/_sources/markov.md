# Markov Chains

Markov chains are models of random motion in a finite set, capturing a vast
array of systems encountered in applications in a simple manner that can be
described using elementary matrix algebra. 

An example is modeling a system of webpages, and the likelihood of a user
visiting certain pages of the site. On average, how many steps might it take
before a user visits a certain page. 

![Figure 1](markov-chain.png)

Above is an example of a simple Markov chain describing a random motion in the
set $\{A, B\}$. The position at time $n=0, 1, 2, \cdots$ is $X_n \in \{A, B\}$.
We call $X_n$ the state of the Markov chain at time $n$.

Let $A=0, B=1$. The above figure can be described by the following set of 
equations:

$$\begin{gather} Pr[X_{n+1}=0|X_n=0, X_{n-1}, \cdots, X_0]=0.6\\
				 Pr[X_{n+1}=1|X_n=0, X_{n-1}, \cdots, X_0]=0.8\\
				 Pr[X_{n+1}=0|X_n=1, X_{n-1}, \cdots, X_0]=0.4\\
				 Pr[X_{n+1}=1|X_n=1, X_{n-1}, \cdots, X_0]=0.2\end{gather}$$

Figure 1 summarizes the rules above, which specify the **transition
probabilities**. The Markov chain is **amnesic**: at step $n$, it forgets what
it did before getting to the current state and its future steps only depend on
that current state. 

We define the transition probability matrix $P$ by $P(0,0)= 0.6, P(0,1)=0.4,
P(1,0)=0.8, P(1,1)=0.2$. That is,

$$ P = \begin{bmatrix}
0.6 & 0.4\\
0.8 & 0.2
\end{bmatrix} $$

Hence, $Pr[X_{n+1}=j|, X_n=i, X_{n-1}, \cdots, X_0] = P(i,j) \text{ for } n\geq
0 \text{ and } i, j \in {0,1}$.

## Finite Markov Chains
One defines a general finite Markov chain as follows. The state space is
$\mathscr{K} = \{1, 2, \cdots, K\}$ for some finite $K$. The transition
probabiility matrix $P$ is a $K\times K$ matrix such that:

$$P(i,j)\geq 0,\forall i, j \in \mathscr{K}$$

and 

$$\sum_{j=1}^KP(i,j)=1,\forall i\in\mathscr{K}$$.

The *initial distribution* is a vector $\pi_0=\{\pi_0(i), i\in\mathscr{K}$ where
$\pi_0(i)\geq 0,\forall i\in\mathscr{K}$ and $\sum_{i\in\mathscr{K}}\pi_0(i)=1$.

One defines the random sequence $\{X_n,n=0,1,2,\cdots\}$ by

$$Pr[X_0=1]=\pi_0(i),i\in\mathscr{K}\\
Pr[X_{n+1}=j|X_n=1,X_{n-1},\cdots,X_0]=P(i,j),\forall n\geq0,\forall i,j\in
\mathscr{K}$$

Note that 

$$Pr[X_0=i_0,X_1=i_1,\cdots,X_n=i_n] = \\Pr[X_0=i_0]Pr[X_1=i_1|X_0=i_0]\cdots
Pr[X_n=i_n|X_0=i_0,X_1=i_1,\cdots,X_{n-1}=i_{n-1}]\\=\pi_0(i_0)P(i_0,i_1)\cdots
P(i_{n-1},i_n)$$

Consequently,

$$Pr[X_n=i_n]=\sum_{i_0,\cdots,i_{n-1}}Pr[X_0=i_0,X_1=i_1,\cdots,X_n=i_n]=\sum_
{i_0,\cdots,i_{n-1}}\pi_0(i_0)P(i_0,I_1),\cdots,P(i_{n-1},i_n)\\
=\pi_0P^n(i_n)$$

Where's the last expression is component $i_n$ of the product of the row vector
$\pi_0$ times the $n$-th power of the matrix $P$.

Thus, if we designate by $\pi_n$ the distribution of $X_n$, so that $Pr[X_n=i]=
\pi_n(i)$, then the last derivation proves the following result:

```{admonition} Theorem
One has

$$\pi_n=\pi_0P^n,n\geq 0$$

In particular, if $\pi_0(i)=1$ for some $i$, then $\pi_n(j)=P^n(i,j)=Pr[X_n=j|
X_0=i]$.
```

## Balance Equations
A distribution $\pi$ is invariant for the transition probability matrix $P$ if
it satisfies the following balance equations:

$$\pi=\pi P$$

```{admonition} Theorem

$$\pi_n=\pi_0,\forall n\geq 0$$

if and only if $\pi_0$ is invariant.
```

```{admonition} Proof
If $\pi_n=\pi_0$ for all $n\geq 0$, then $\pi_0=\pi_1=\pi_0P$, so that $\pi_0$
satisfies the definition of invariance.

If $\pi_0P=\pi_0$, then $\pi_1=\pi_0P=\pi_0$. Also, if $\pi_n=\pi_0$, then $\pi_
{n+1}=\pi_nP=\pi_0P=\pi_0$. 
```

## Time
A Markov chain is **irreducible** if it can go from every state $i$ to every
other state $j$, possibly in multiple steps. It is only irreducible if and only
if its state transition diagram is a directed graph with a single connected
component.

```{admonition} Theorem
Consider a finite irreducible Markov chain with state space $\mathscr{K}$ and
transition probability matrix $P$. Then, for any initial distribution $\pi_0$,

$$lim_{n\rightarrow\infty}\frac{1}{n}\sum^{n-1}_{m=0}1\{X_m=i\}=\pi(i),\forall
i \in\mathscr{K}$$

In the above equation, $\pi=\{\pi(i),i\in \mathscr{K}$\} is an invariant
distribution. Consequently, the invariant distributon exists and is unique.
```

It is not always the case that $Pr[X_n=i]$ converges to some value as $n$
increases. A simple example is our two state Markov chain, where $Pr[X_n=0]$ is
oscillating between 0 and 1; such a Markov chain is said to be **periodic**.

```{admonition} Theorem
Consider an irreducible Markov chain on $\mathscr{K}$ with transition
probability matrix $P$. Define

$$d(i):=gcd\{n>0|P^n(i,i)=Pr[X_n=i|X_0=i]>0\},i\in\mathscr{K}$$

$d(i)$ has the same value for all $i \in\mathscr{K}$. If that value is 1, the
Markov chain is said to be aperiodic. Otherwise, it is said to be periodic with
period $d$. If it is aperiodic, then $Pr[X_n=i]\rightarrow\pi(i),\forall i\in
\mathscr{K}$, as $n\rightarrow\infty$, where $\pi$ is the unique invariant
distribution.
```