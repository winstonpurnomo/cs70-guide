# Random Variables: Variance and Covariance

## Random Walk
Let's consider an example where we have a particle, starting at position 0, that
can perform random walks in one dimension. At each time step, the particle moves
either one step to te right or left with equal probability (a *symmetric* random
walk), and the move at each time step is independent of all other moves (like a
coin flip).

The expected position of the particle after $n$ movies is back at 0, but how far
from 0 should we typically expect the particle to end up?

Let $+1$ be a right move, and $-1$ be a left move, and we can describe the 
probability space here as the set of all sequences of length $n$ over the
alphabet, $\{\pm 1\}$, each having equal probability $\frac{1}{2^n}$. Let the
random variable $S_n$ denote the position of the particle relative to our
starting point 0) after $n$ moves. Thus, we can write

$$S_n = X_1+X_2+\cdots+X_n$$.

The expectation $S_n$ can be easily computed as follows. Since $\mathbb{E}[X_i]=
(\frac{1}{2}\times 1)+(\frac{1}{2}\times(-1))=0$, applying the linearity of
expectation gives $\mathbb{E}[S_n]=\sum_{i=1}^n\mathbb{E}[X_i]=0$.

What we are really asking is: what is the expected value of $|S_n|$, the 
*distance* of the particle from 0? Rather than consider the random variable
$|S_n|$, which is difficult to work with due to the absolute value operator, we
will instead look at the $S_n^2$, which makes all deviations from positive. We
will square root it in the end. 

Now, we claim that the expected square distance after $n$ steps is equal to $n$.


```{admonition} Proof
$$\mathbb{E}[S_n^2]=\mathbb{E}[(X_1+X_2+\cdots+X_n)^2]=\mathbb{E}[\sum_{i=1}^n
X_i^2+2\sum_{i<j}X_iX_j]+\sum_{i=1}^n\mathbb{E}[X_i^2]+2\sum_{i<j}\mathbb{E}[X_i
X_j]$$.

To proceed, we must compute $\mathbb{E}[X_i^2]$ and $\mathbb{E}[X_iX_j]$ for $i
\not=j$. Since $X_i$ can only take values $\pm 1$, $\mathbb{E}[X_i^2]=1$. As for
$\mathbb{E}[X_iX_j]$, note $X_iX_j =+1$ when $X_i=X_j=+1$ or $X_i=X_j=-1$, and
otherwise $X_iX_j=-1$. Thus,

$$\mathbb{P}[X_iX_j=1]=\mathbb{P}[(X_i=X_j=+1)\vee(X_i=X_j=-1)]=\mathbb{P}[X_i=
X_j=+1]+\mathbb{P}[X_i=X_j=-1]\\=\mathbb{P}[X_i=+1]\times\mathbb{P}[X_j=+1]+
\mathbb{P}[X_i=-1]\times\mathbb{P}[X_j=-1]=\frac{1}{4}+\frac{1}{4}=\frac{1}{2}$$

where the second equality follows from the fact that the events are mutually
exclusive, while the third equality follows from the independence of the events.
In a similar vein, $\mathbb{P}[X_iX_j]=\frac{1}{2}$, hence, $\mathbb{E}[X_iX_j]=
0$.

Plugging in these values gives $\mathbb{E}[S_n^2]=\sum_{i=1}^n+2\sum_{i<j}0=n$.
```

We see the expected squared distance from 0 is $n$. However, we cannot argue
that $\mathbb{E}[|S_n|]=\sqrt{\mathbb{E}[S_n^2]}=\sqrt{n}$.

For more general random variables $X$ with expectation $\mu$, what we are really
interested in is the expected squared distance from the mean, $\mathbb{E}[(X-\mu
)^2]$. In our example above, $\mu=0$, so the definitions are equivalent.

For a random variable $X$ with expectation $\mu$, the **variance** of $X$ is
defined to be

$$Var(X)=\mathbb{E}\[(X-\mu)^2\]$$.

The square root $\sigma(X):=\sqrt{Var(X)}$ is the **standard deviation** of $X$.

An alternative definition states that $Var(X)=\mathbb{E}{X^2}-\mu^2$, which may
be easier to compute in certain scenarios.

```{admonition} Proof
$$Var(X)=\mathbb{E}[(X-\mu)^2]=\mathbb{E}[X^2-2\mu X+\mu^2]=\mathbb{E}[X^2]-
2\mu\mathbb{E}[X]+\mu^2=\mathbb{E}[X^2]-\mu^2$$
```

Another important property states that for any random variable $X$ and constant
$c$,

$$Var(cX)=c^2 Var(X)$$.

## Sum of Independent Random Variables

```{admonition} Theorem
For independent random variables $X, Y$, we have $\mathbb{E}[X]\mathbb{E}[Y]$.
```

```{admonition} Proof
$$\mathbb{E}[XY]=\sum_a\sum_bab\times\mathbb{P}[X=a,Y=b]\\=\sum_a\sum_bab\times
\mathbb{P}[X=a]\times\mathbb{P}[Y=b]\\=(\sum_aa\times\mathbb{P}[X=a])\times(\sum
_bb\times\mathbb{P}[Y=b])\\=\mathbb{E}[X]\mathbb{E}[Y]$$
```

We will now use the above property to make a conclusion about variance.

```{admonition} Theorem
For independent random variables $X, Y$, we have $Var(X+Y)=Var(X)+Var(Y)$.
```

```{admonition} Proof
$$Var(X+Y)=\mathbb{E}[(X+Y)^2]-(\mathbb{E}[X+Y])^2=\mathbb{E}[X^2]+\mathbb{E}
[Y^2]+2\mathbb{E}[XY]-(\mathbb{E}[X]=\mathbb{E}[Y])^2\\=(\mathbb{E}[X^2]-
\mathbb{E}[X]^2)+(\mathbb{E}[Y^2]-\mathbb{E}[Y]^2)+2(\mathbb{E}[XY]-\mathbb{E}
[X]\mathbb{E}[Y])$$.

Since $X, Y$ are independent,

$$Var(X+Y)=Var(X)+Var(Y)=2(\mathbb{E}[XY]-\mathbb{E}[X]\mathbb{E}[Y])=Var(X)+
Var(Y)$$
```

Neither of the above two proofs are valid when $X, Y$ are not independent.

## Covariance

The **covariance** of random variables $X, Y$, denoted $Cov(X, Y)$, is defined
as

$$Cov(X, Y)=\mathbb{E}[(X-\mu_X)(Y-\mu_Y)]=\mathbb{E}[XY]-\mathbb{E}[X]
\mathbb{E}[Y]$$

where $\mu_X = \mathbb{E}[X]$ and $\mu_Y = \mathbb{E}[Y]$.

Several key properties of covariance:

1. If $X, Y$ are independent, $Cov(X,Y)=0$. However, the converse is not true.
2. $Cov(X,X) = Var(X)$
3. Covariance is *bilinear*; for any collection of random variables $\{X_1,
\cdots ,X_n\}$,$\{Y_1,\cdots,Y_m\}$ and fixed constants $\{a_1,\cdots,a_n\}$,
$\{b_1,\cdots,b_m\}$,$Cov(\sum_{i=1}^na_iX_i,\sum_{j=1}^mb_jY_j)=\sum_{i=1}^n\sum_{j=1}^ma_ib_j
Cov(X_i,Y_j)$.

For general random variables $X$ and $Y$,

$$Var(X+Y)=Var(X)+Var(Y)+2Cov(X,Y)$$.

While the sign of $Cov(X,Y)$ is informative of how $X$ and $Y$ are associated,
its magnitude is difficult to interpret.

## Correlation

Suppose $X$ and $Y$ are random variables with $\sigma{X)>0$ and $\sigma(Y)>0$,
then the **correlation** of $X$ and $Y$ is defined as

$$Corr(X,Y)=\frac{Cov(X,Y)}{\sigma(X)\sigma(Y)}$$

Correlation is more useful than covariance because the former always ranges
between $-1$ and $+1$.

```{admonition} Proof
Let $\mathbb{E}[X]=\mu_X$ and $\mathbb{E}[Y]=\mu_Y$, and define $\tilde{X} =
\frac{X-\mu_X}{\sigma(X)}$ and $\tilde{Y}=\frac{Y-\mu_Y}{\sigma(Y)}$. Then,
$\mathbb{E}[\tilde{X}^2]=\mathbb{E}[\tilde{Y}^2]=1$, so

$$0\leq\mathbb{E}[(\tilde{X}-\tilde{Y})^2]=\mathbb{E}[\tilde{X}^2]+\mathbb{E}
[\tilde{Y}^2]-2\mathbb{E}[\tilde{X}\tilde{Y}]=2-2\mathbb{E}[\tilde{X}\tilde{Y}]
\\
0\leq\mathbb{E}[(\tilde{X}+\tilde{Y})^2]=\mathbb{E}[\tilde{X}^2]+\mathbb{E}
[\tilde{Y}^2]+2\mathbb{E}[\tilde{X}\tilde{Y}]=2+2\mathbb{E}[\tilde{X}\tilde{Y}]
$$

This implies $-1\leq\mathbb{E}[\tilde{X}\tilde{Y}]\leq +1$. Noting $\mathbb{E}
[\tilde{X}]=\mathbb{E}[\tilde{Y}]=0$, we obtain $Corr(X,Y)=Cov(\tilde{X},
\tilde{Y})=\mathbb{E}[\tilde{X}\tilde{Y}]$. Hence, $-1\leq Corr(X,Y)\leq+1$.
```