# Concentration Inequalities

Suppose we have a biased die, but we don't know what the bias is. A good
estimate of the bias might come from calculating the average, and comparing
that with the expected value. Since $\mathbb{E}[S_n]=np$, our estimator $p'$
has the expected value of $\mathbb{E}[p']=\frac{1}{n}\mathbb{E}[S_n]=p$. This
tells us that if $n$ is sufficiently large, we can expect $p'$ to be close to p,
thanks to the Law of Large Numbers.

How large does $n$ need to be? There is no good answer. We can never guarantee
with absolute certainty that $|p'-p| \leq \epsilon$, where $\epsilon$ is some
error. Instead, we can state that $|p'-p| \leq \epsilon$ with a confidence $1-
\delta$, such that $\mathbb{P}[|p'-p|\leq \epsilon]\geq 1-\delta$. There is a
small probability $\delta$ that the error is more than $\epsilon$.

To put this into a formula:

$$n\geq\frac{1}{4\epsilon^2\delta}$$

In order to prove this, let's take a detour to Markov's Inequality.

## Markov's Inequality
For a *nonnegative random variable X (i.e. $X(\omega) \geq 0, \forall \omega\in
\Omega$)* with a finite mean,

$$\mathbb{P}[X\geq c]\leq\frac{\mathbb{E}[X]}{c}$$,

for any positive constant $c$.

```{admonition} Proof
Let $\mathscr{A}$ denote the range of $X$, and consider any constant $c\in
\mathscr{A}$. Then,

$$\mathbb{E}[X]=\sum_{a\in\mathbb{A}}a\times\mathbb{P}[X=a]  \geq\sum_{a\geq c}
a\times\mathbb{P}[X=a]\geq\sum_{a\geq c} c\times\mathbb{P}[X=a] \\
= c\sum_{a\geq c}\mathbb{P}[X=a]=c\times\mathbb{P}[X\geq c]$$
```

The proof starts with the definition of expectation, then uses the fact that $X$
is a nonnegative random variable, and rearranging the last inequality gives us
the desired result.

We can define a slicker proof using the indicator function $I\{\bullet\}$,
defined as:

$$I\{statement\}=\begin{cases}1,&\text{if statement is true}\\0,&\text{if
statement is false}\end{cases}$$

```{admonition} Proof
Since $X$ is a nonnegative random variable and $c>0$, we have, $\forall \omega
\in \Omega$,

$$\begin{gather}X(\omega)\geq cI\{X(\omega)\geq c\},\end{gather}$$

since the right hand side is 0 if $X(\omega)<c$ and is $c$ if $X(\omega)>c$.
Multiply both sides by $\mathbb{P}[\omega]$ and sum over $\omega\in\Omega$ to
give,

$$\mathbb{E}[X]\geq c\mathbb{E}[I\{X\geq c\}]=c\times\mathbb{P}[X\geq c]$$

where the first inequality follows from (1) and the fact that $\mathbb{P}[
\omega] \geq 0, \forall \omega \in \Omega$ , while the last inequality follows
from the fact that $I\{X\geq c\}$ is an indicator random variable.
```

### Generalized Markov's Inequality
Let $Y$ be an arbitrary random variable with finite mean. For any positive
constants $c$ and $r$,

$$\mathbb{P}[|Y|\geq c]\leq\frac{\mathbb{E}[|Y|^r]}{c^r}$$.

```{admonition} Proof
For $c>0$ and $r>0$ (if $r$ were negative, the last inequality below does not
hold), we have,

$$|Y|^r\geq |Y|^rI\{|Y|\geq c\}\geq c^rI\{|Y|\geq c\}$$.

Taking the expectations of both sides,

$$\mathbb{E}[|Y|^r]\geq c^r\mathbb{E}[I\{|Y|\geq c\}]=c^r\mathbb{P}[|Y|\geq c]$$

Divde by $c^r$ to find the desired result.
```

## Chebyshev's Inequality
For a random variable $X$ with a finite expectation $\mathbb{E}[X]=\mu$,

$$\mathbb{P}[|X-\mu|\geq c]\leq \frac{Var(X)}{c^2}$$

```{admonition} Proof
Let $Y=(X-\mu)^2$, and note that $\mathbb{E}[Y]=\mathbb{E}[(X-\mu)^2]=Var(X)$.

$$|X-\mu|\geq c\implies Y=(X-\mu)^2\geq c^2$$

Therefore, $\mathbb{P}[|X-\mu|\geq c]=\mathbb{P}[Y\geq c^2]$. Since $Y$ is
nonnegative, applying Markov's inequality yields

$$\mathbb{P}[|X-\mu|\geq c]=\mathbb{P}[Y\geq c^2]\leq \frac{\mathbb{E}[Y]}{c^2}=
\frac{Var(X)}{c^2}$$
```

And here's another proof using the generalized theorem:

```{admonition} Proof
Let $Y=X-\mu$. Then, since $|Y|^2=(X-\mu)^2$, we have $\mathbb{E}[|Y|^2]=\mathbb
{E}[(X-\mu)^2]=Var(X)$. Hence,

$$|X-\mu|\geq c\implies Y=(X-\mu)^2\geq c^2$$

follows from applying Generalized Markov's Inequality to $Y=X-\mu$ with $r=2$.
```

Stopping to consider what Chebyshev's Inequality means, it tells us that the
probability of any given deviation, $c$, from the mean is at most $\frac{Var(X)}
{c^2}$. If the variance is small, the deviation probability is small. This has
the immediate consequence of making the following statement true:

For any random variable $X$ with finite expectation $\mathbb{E}[X]=\mu$ and
finite standard deviation $\sigma=\sqrt{Var(X)}$, 

$$\mathbb{P}[|X-\mu|\geq k\sigma]\leq\frac{1}{k^2}$$

for any constant $k>0$, where $c=k\sigma$ in Chebyshev's Inequality.

This means that, for example, the probability of deviating from the mean by more
than 2 standard deviations on either side is at most $\frac{1}{4}$, allowing
standard deviation to be a good working definition of the "spread" of a
distribution.