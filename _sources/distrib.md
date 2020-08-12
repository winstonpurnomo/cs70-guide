# Distributions

## Geometric Distribution

The geometric distribution frequently occurs in applications because we are
often interested in how long we have to wait before a certain event happens.

A random variable $X$ for which

$$\mathbb{P}[X=i]=(1-p)^{i-1}p,\text{ for }i=1,2,3,\cdots$$,

is said to have the *geometric distribution* with parameter $p$, abbreviated as
$X\sim Geometric(p)$.

As a santiy check, we can verify the total probability of $X$ is equal to 1:

$$\sum_{i=1}^\infty\mathbb{P}[X=i]=\sum_{i=1}^\infty(1-p)^{i-1}p=p\sum_{i=1}^
\infty(1-p)^{i-1}=p\times\frac{1}{1-(1-p)}=1$$.

If we plot the distribution of $X$, we get a curve that decreases monotonically
by a factor of $1-p$ at each step.

### Mean and Variance

Let $X$ be a random variable that takes in values $\{0,1,2,\cdots\}$. Then,

$$\mathbb{E}[X]=\sum_{i=1}^\infty\mathbb{P}[X\geq i]$$.

Below is the proof of what we call the **Tail Sum Formula**.

```{admonition} Proof

For notational convenience, let's write $p_i=\mathbb{P}[X=i]$, for $i=0,1,2,
\cdots$.

$$\mathbb{E}[X]=(0\times p_0)+(1\times p_1)+(2\times p_2)+\cdots\\
=p_1+(p_2+p_2)+(p_3+p_3+p_3)+\cdots=(p_1+p_2+p_3+\cdots)+(p_2+p_3+\cdots)+\cdots
\\=\mathbb{P}[X\geq 1]+\mathbb{P}[X\geq 2]+\mathbb{P}[X\geq 3]+\cdots$$.

In compact notation:

$$\mathbb{E}[X]=\sum_{j=1}^\infty j\times\mathbb{P}[X=j]=\sum_{j=1}^\infty\sum_
{i=1}^j\mathbb{P}[X=j]=\sum_{i=1}^\infty\sum_{j=i}^\infty\mathbb{P}PX=j]=
\sum_{i=1}^\infty\mathbb{P}[X\geq 1]$$.
```

For $X\sim Geometric(p)$, we have $\mathbb{E}[X]=\frac{1}{p}$.

```{admonition} Proof
The key observation is for a geometric random variable $X$,

$$\mathbb{P}[X\geq i]=(1-p)^{i-1},\text{ for }i=1,2,3,\cdots$$

We can obtain this simply by summing $\mathbb{P}[X=j]$ for $j\geq i$. Another
way of seeing this is to note that the event $X\geq i$ means at least $i$ tosses
are required, or the first $i-1$ tosses are all tails and the probability of
this event is $(1-p)^{i-1}$. 

$$\mathbb{E}[X]=\sum_{i=1}^\infty\mathbb{P}[X\geq i]=\sum_{i=1}^\infty(1-p)^
{i-1}=\frac{1}{1-(1-p)}=\frac{1}{p}$$.

```
And for $X\sim Geometric(p)$, we have $Var(X)=\frac{1-p}{p^2}$.

```{admonition} Proof
We will show $\mathbb{E}[X(X-1)]=\frac{2(1-p)}{p^2}$:

$$Var(X)=\mathbb{E}[X^2]-\mathbb{E}[X]^2=\mathbb{E}[X(X-1)]+\mathbb{E}[X]-
\mathbb{E}[X]^2\\=\frac{2(1-p)}{p^2}+\frac{1}{p}-\frac{1}{p^2}=\frac{2(1-p)+p
-1}{p^2}=\frac{1-p}{p^2}$$

To show $\mathbb{E}[X(X-1)]=\frac{2(1-p)}{p^2}$:

$$\frac{d^2x}{dy^2}(\sum_{i=0}^\infty(1-p)^i=\frac{d^2x}{dy^2}(\frac{1}{p})\\=
\sum_{i=2}^\infty i(i-1)(1-p)^{i-2}=\frac{2}{p^3}$$.

$$\mathbb{E}[X(X-1)]=\sum_{i=1}^\infty i(i-1)\times\mathbb{P}[X=i]\\=\sum_{i=2}^
\infty i(i-1)(1-p)^{i-1}p=p(1-p)\sum_{i=2}^\infty i(i-1)(1-p)^{i-2}\\=p(1-p)
\times\frac{2}{p^3}=\frac{2(1-p)}{p^2}$$.
```

## Poisson Distribution

A random variable $X$ for which

$$\mathbb{P}[X=i]=\frac{\lambda^i}{i!}e^{-\lambda},\text{ for }i=0,1,2,\cdots$$

is said to have the **Poisson distribution** with parameter $\lambda$, 
abbreviated as $X\sim Poisson(\lambda)$.

As a sanity check,

$$\sum_{i=0}^\infty\frac{\lambda^i}{i!}e^{-\lambda}=e^{-\lambda}\sum_{i=0}^
\infty\frac{\lambda^i}{i!}=e^{-\lambda}\times e^\lambda = 1$$.

where in the second to last step, we used the Taylor expansion $e^x=1+x+\frac{x
^2}{2!}+\cdots$.

The Poisson distribution is used as a widely accepted model for so-called "rare
events", such as car accidents or ICU admission at a hospital. It is appropriate
whenever the occurrences can be assumed to happen randomly with some constant
density in a continuous region (of time or space), such that occurrences in
disjoint subregions are independent.

### Mean and Variance

For a Poisson random variable $X$ with parameter $\lambda$, we have $\mathbb{E}
[X]=Var(X)=\lambda$,

```{admonition} Proof

$$\mathbb{E}[X]=\sum_{i=0}^\infty i\times\mathbb{P}[X=i]\\=\sum_{i=1}^\infty i
\times\frac{\lambda^i}{i!}e^{-\lambda}=\lambda e^{-\lambda}\sum_{i=i}^\infty
\frac{\lambda^{i-1}}{(i-1)!}\\=\lambda e^{-\lambda}e^\lambda=\lambda$$

Similarly,

$$\mathbb{E}[X(X-1)]=\sum_{i=0}^\infty i(i-1)\times\mathbb[P][X=i]\\
=\sum_{i=2}^\infty i(i-1)\frac{\lambda^i}{i!}e^{-\lambda}\\
=\lambda^2e^{-\lambda}\sum_{i=2}^\infty\frac{\lambda^{i-2}}{(i-2)!}\\
=\lambda^2e^{-\lambda}e^{\lambda}=\lambda^2$$.

Therefore,

$$Var(X)=\mathbb{E}[X^2]-\mathbb{E}[X]^2=\mathbb{E}[X(X-1)]+\mathbb{E}[X]-
\mathbb{E}[X]^2=\lambda^2+\lambda-\lambda^2=\lambda$$.

```

### Sum of Independent Poisson Random Variables

```{admonition} Theorem
Let $X\sim Poisson(\lambda)$ and $Y\sim Poisson(\mu)$ be independent Poisson
random variables. Then, $X+Y\sim Poisson(\lambda+\mu)$.
```

```{admonition} Proof
For all $k=0,1,2,\cdots$, we have

$$\mathbb{P}[X+Y=k]=\sum_{j=0}^k\mathbb{P}[X=j,Y=k-j]\\=\sum_{j=0}^k\mathbb{P}
[X=j]\mathbb{P}[Y=k-j]\\=\sum_{j=0}^k\frac{\lambda^j}{j!}e^{-\lambda}\frac{\mu^
{k-j}}{(k-j)!}e^{-\mu}\\=e^{-(\lambda+\mu)}\frac{1}{k!}\sum_{j=0}^k\frac{k!}
{j!(k-j)!}\lambda^j\mu^{k-j}\\=e^{-(\lambda+\mu)}\frac{(\lambda+\mu)^k}{k!}$$,

where the second equality follows from independence, and the last equality from
the binomial theorem.
```

By induction, we can conclude for $X_1,X_2,\cdots,X_n$ independent Poisson
random variables with parameters $\lambda_1,\cdots,\lambda_n$.,

$$X_1+\cdots+X_n\sim Poisson(\lambda_1+\cdots+\lambda_n)$$.

### Poisson as a Limit of Binomial

```{admonition} Theorem
Let $X\sim Binomial(n,\frac{\lambda}{n})$ where $\lambda>0$ is a fixed constant.
For every $i=0,1,2,\cdots$,

$$\mathbb{P}{X=i}\rightarrow\frac{\lambda^i}{i!}e^{-\lambda}\text{ as }n
\rightarrow\infty$$.
```

```{admonition} Proof
Fix $i\in\{0, 1, 2, \cdots \}$, and assume $n\geq i$ (because $n\rightarrow
\infty$). Then, because $X$ is a binomial distribution,

$$\mathbb{P}[X=i]=\binom{n}{i}p^i(1-p)^{n-i}=\frac{n!}{i!(n-i)!}(\frac{\lambda}
{n})^i(1-\frac{\lambda}{n})^{n-i}$$.

Collecting the factors,

$$\mathbb{P}[X=i]=\frac{\lambda^i}{i!}(\frac{n!}{(n-i)!}\frac{1}{n^i})(1-\frac
{\lambda}{n})^n(1-\frac{\lambda}{n})^{-i}$$.

The first parenthesis above, as $n\rightarrow\infty$, becomes

$$\frac{n!}{(n-i)!}\frac{1}{n^i}=\frac{n(n-1)\cdots(n-i+1)(n-i)!}{(n-i)!}\frac
{1}{n^i}=\frac{n}{n}\frac{n-1}{n}\cdots\frac{n-i+1}{n}\rightarrow 1$$.

The second partnhesis becomes

$$(1-\frac{\lambda}{n})^n\rightarrow e^{-\lambda}$$

Since $i$ is fixed,

$$(1-\frac{\lambda}{n})^{-i}\rightarrow(1-0)^{-i}=1$$.

Substituting these into the above equation,

$$\mathbb{P}[X=i]\rightarrow\frac{\lambda^i}{i!}e^-{\lambda}$$.
```