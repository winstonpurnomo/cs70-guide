# Random Variables: Distribution and Expectation
A **random variable** $X$ on a sample space $\Omega$ is a function $X: \Omega
\rightarrow \mathbb{R}$ that assigns to each sample point $\omega\in\Omega$ a
real number $X(\omega)$.

In this chapter, we discuss *discrete* random variables, which take values in a
range that is finite or countably infinite. This means even though we define $X$
to map $\Omega$ to $\mathbb{R}$, the actual set of values $\{X(\omega):\omega\in
\Omega$ that $X$ takes is a discrete subset of $\mathbb{R}$.

The term "random variable" is a bit of a misnomer: it is a function and there is
nothing random about it, nor is it a variable! What is random is which sample
point of the experiment is realized, and hence the value that the random
variable maps the sample point to.

## Distributions

Like with basic probability space, the most important things about any random
variable are:

1. The set of values it can take.
2. The probabilities with which it takes on the values.

Since a random variable is defined on a probability space, we can calculate
these probabilities given the probabilities of the sample points. Let $a$ be any
number in the range of a random variable $X$. Then, the set

$$\{\omega\in\Omega:X(\omega)=a\}$$

is an *event* in the sample space because it is a subset of $\Omega$. We usually
abbreviate this event to simply "$X=a$", and we discuss its probability $\mathbb
{P}[X=a]$. The collection of these probabilities for all possible values of $a$
is known as the distribution of the random variable $X$.

Formally, the **distribution** of a discrete random variable $X$ is the
collection of values $\{(a, \mathbb{P}[X=a]): a\in\mathscr{A}\}$, where
$\mathscr{A}$ is the set of all possible values taken by $X$.

Note the collection of events $X=a$, for $a\in\mathscr{A}$, satisfy two key
properties:

1. Any two events $X=a_1$ and $X=a_2$ with $a1\not=a_2$ are disjoint.
2. The union of these events is equal to the entire sample space $\Omega$.

The collection of events thus form a *partition* of the sample space.

### Bernoulli Distribution
A simple yet useful probability distribution is the *Bernoulli* distribution
of a random variable which takes value in $\{0,1\}$. 

$$\mathbb{P}[X=i]=\begin{cases}p,&\text{if i = 1,}\\1-p,&\text{if i =0,}
\end{cases}$$

where $0\leq p\leq1$. We say that $X$ is dsitributed as a *Bernoulli* random
variable with parameter $p$, and write $X \sim Bernoulli(p)$.

### Binomial Distribution

The binomial distribution is the discrete probability distribution of the number
of successes in a sequence of $n$ independent experiments, each asking a yes
–no question, and each with its own boolean-valued outcome with probability $p$. 

$$\mathbb{P}[X=i]=\binom{n}{i}p^i(1-p)^{n-i}, \text{ for } i = 0, 1, \cdots, n$$

A random variable with this distribution is called a *binomial* random variable,
and we write $X \sim Bin(n,p)$.

### Hypergeometric Distribution
The *hypergeometric* distribution is a discrete probability distribution that
describes the probability of $k$ successes (random draws for which the object
drawn has a specified feature) in $n$ draws, without replacement, from a finite
population of size $N$ that contains exactly $B$ objects with that feature,
wherein each draw is either a success or a failure.

$$\mathbb{P}[Y=k]=\binom{n}{k}\frac{\frac{B!}{(B-k)!}\frac{(N-B)!}{(N-B-(n-k))!}
}{\frac{N!}{(N-n)!}}=\frac{\binom{B}{k}\binom{N-B}{n-k}}{\binom{N}{n}}, \text{
 for } k \in \{ 0, 1, \cdots, n \}$$.

A random variable with this distribution is called a *hypergeometric* random
variable with parameters $N, B, n$, and we write $Y \sim Hypergeometric(N,B,n)$.

## Joint Distributions
We are often interested in multiple random variables on the same sample space.
The **joint distribution** for two discrete random variables $X$ and $Y$ is the
collection of values $\{((a, b),\mathbb{P}[X=a,Y=b]):a\in\mathscr{A},b\in
\mathscr{B}\}$, where $\mathscr{A}$ is the set of all possible values taken by
$X$, and $\mathscr{B}$ is the set of all possible values taken by $Y$.

When we are a joint distribution for $X$ and $Y$, the distribution $\mathbb{P}
[X=a]$ for $X$ is called the *marginal dsitribution* for $X$, and can be found
by "summing" over the values for $Y$:

$$\mathbb{P}[X=a]=\sum_{b\in\mathscr{B}}\mathbb{P}[X=a,Y=b]$$

The marginal distribution for $Y$ is analogous. In the case of more than 2
variables, we sum over all possible values for all other variables. In some
cases, it may be obtained more simply.

Random variables $X$ and $Y$ are said to be **independent** if the events $X=a$
and $Y=b$ are independent for all values $a, b$. Equivalently, the joint
distribution of independent random variables decomposes as

$$\mathbb{P}[X=a,Y=b]=\mathbb{P}[X=A]\mathbb{P}[Y=b],\forall a,b$$.

## Expectation

The **expectation** of a discrete random variable $X$ is defined as

$$\mathbb{E}[X]=\sum_{a\in\mathscr{A}}a \times\mathbb{P}[X=a]$$,

where the sum is over all possible values taken by the random variable.

The expectation can be thought of as *summarizing* the distribution into a more
compact, convenient form that is also easier to compute. The expectation can be
thought of as a "typical value" for the random variable (though note it may not
be a discrete value that $X$ can actually take).

### Linearity of Expectation

For any two random variables $X$ and $Y$ on the same probability space, we have

$$\mathbb{E}[X+Y]=\mathbb{E}[X]+\mathbb{E}[Y]$$. 

For any constant $c$, we have 

$$\mathbb{E}[cX]=c\mathbb{E}[X]$$.

```{admonition} Proof
$$\mathbb{E}[X]=\sum_{a\in\mathscr{A}}a \times\mathbb{P}[X=a]$$

Consider a particular $a\times\mathbb{P}[X=a]$ in the above sum. By definition,
$\mathbb{P}[X=a]$ is the sum of $\mathbb{P}[\omega]$ over those sample points
$\omega$ for which $X(\omega)=a$. We know every sample point $\omega\in\Omega$
is in exactly one of those events $X=a$. This means we can write out the above
definition as

$$\mathbb{E}[X]=\sum_{\omega\in\Omega} X(\omega)\times\mathbb{P}[\omega]$$.

Now we apply this to $\mathbb{E}[X+Y]$:

$$\mathbb{E}[X+Y]=\sum_{\omega\in\Omega}(X+Y)(\omega)\times\mathbb{P}[\omega]\\
=\sum_{\omega\in\Omega}(X(\omega)+Y(\omega))\times\mathbb{P}[\omega]\\
=\sum_{\omega\in\Omega}(X(\omega)\times\mathbb{P}[\omega])+
\sum_{\omega\in\Omega}(Y(\omega)\times\mathbb{P}[\omega])\\
=\mathbb{E}[X]+\mathbb{E}[Y]$$.

This completes the proof of the first equality; the proof of the second is left
as an exercise.
```