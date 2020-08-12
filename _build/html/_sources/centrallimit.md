# Central Limit Theorem

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