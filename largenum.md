# Law of Large Numbers and Central Limit Theorem

## Law of Large Numbers

The estimation we use in previous chapters is a principle we widely accept: the
Law of Large Numbers (LLN), which states that if we observe a random variable
many times, and take the average of these observations, the average will
converge on a single value, the expectation of the random variable. In other
words, averaging tends to smooth out large fluctuations, and the more averaging
we do the better the smoothing.

In more mathematical terms, 

Let $X_1, X_2, \cdots$ be a sequence of independent and identically distributed
random variables with common finite expectation $\mathbb{E}[X_i]=\mu,\forall i$.
Their partial sums $S_n=X_1+X_2+\cdots+X_n$ satisfy

$$\mathbb{P}[|\frac{1}{n}S_n-\mu|<\epsilon]\rightarrow1, \text{ as } n
\rightarrow\infty$$

for every $\epsilon>0$, however small.

```{admonition} Proof
Let $Var(X_i)$=\sigma^2$ be the common variance of therandom variables, assuming
$\sigma^2$ is finite (a proof that does not assume this is much more 
complicated). The LLN is an immediate consequence of Chebyshev's Inequality;
since $X_1, X_2, \cdots$ are i.i.d. random variables with $\mathbb{E}[X_i]=\mu$
and $Var(X_i)=\sigma^2$, we have $\mathbb{E}[\frac{1}{n}S_n]=\mu$ and $Var(\frac
{1}{n}S_n)=\frac{\sigma^2}{n}$. So by Chebyshev's Inequality, we have

$$\mathbb{P}[|\frac{1}{n}S_n-\mu|\geq\epsilon]\leq\frac{Var(\frac{1}{n}S_n)}{
\epsilon^2}=\frac{\sigma^2}{n\epsilon^2}\rightarrow 0, \text{ as } n\rightarrow
\infty$$

Hence, $\mathbb{P}[|\frac{1}{n}S_n-\mu|<\epsilon] = 1-
\mathbb{P}[|\frac{1}{n}S_n-\mu|\geq\epsilon]\rightarrow 1, \text{ as } n
\rightarrow\infty$.
```

Notice the LLN says the probability of *any* deviation $\epsilon$ from the mean,
however small, tends to zero as the number of observations $n$ in our average
tends to infinity. By making $n$ large enough, we can make the probability of 
any given deviation as small as we like.

## Central Limit Theorem

Recall the Law of Large Numbers from earlier: we can actuall strengthen it even
further, deriving from the density of the normal distribution.

```{admonition} Theorem
Let $X_1,X_2,\dots$ be a sequence of i.i.d. random variables with common finite
expectation $\mathbb{E}[X_i]=\mu$ and finite variance $Var(X_i)=\sigma^2$. Let
$S_n=\sum_{i=1}^n X_i$. Then, the distribution of $\frac{S_n-n\mu}{\sigma
\sqrt{n}}$ converges to $N(0,1)$ as $n\rightarrow \infty$. In other words, for
constant $c\in \mathbb{R}$,

$$\mathbb{P}[\frac{S_n-n\mu}{\sigma\sqrt{n}}\leq c]\rightarrow\frac{1}{\sqrt{2
\pi}}\int^c_{-\infty}e^{-\frac{x^2}{2}}dx\text{ as }n\rightarrow\infty$$.
```

The Central Limit Theorem essentially states that if we take an average of $n$
observations of any arbitrary random variable $X$, then the distribution of that
average will be a bell-shaped curve centered at $\mu=\mathbb{E}[X]$. Thus, all
trace of the distribution of $X$ disappears as $n$ gets large, no matter how
complex the distribution, making it look like the normal distribution when
averaged. The only effect of the original distribution is through the variance
$\sigma^2$, which determines the width of the curve for a given value of $n$n,
and hence the rate at which the curve shrinks to a spike.