# Continuous Probabilities

Until now, we have focused on *discrete* sample spaces $\Omega$, where the
number of sample points $\omega \in \Omega$ is either finite or countably
infinite, and thus, focused on discrete random variables. But many quantities
in real life are *real-valued*. We will discuss how to extend the concepts we've
seen to a *continuous* setting.

Previously, we discussed uniform probability as the total probability divided by
the number of sample points. However, in a continuous setting, there are
infinitely many sample points $\omega$; if we assign $\mathbb{P}[\omega]$ to be
any positive value, then the sum of all probabilities $\mathbb{P}[\omega]$ will
be $\infty!$ Then, $\mathbb{P}[\omega]$ must be zero, which would render us
unable to assign meaningful probabilities to any events!

Consider any interval $[a,b]\subseteq[0,\mathcal{l}]$ where $b>a$. Can we assign
a non-zero probability value to this interval? Since the total probability
assigned to $[0, \mathcal{l}]$ must be 1, and since we want our probability to be
uniform, we can conclude the probability of an interval is proportional to its
length

$$\frac{\text{length of }[a,b]}{\text{length of }[0,\mathcal{l}]}=\frac{b-a}
{\mathcal{l}}$$

Note that intervals are subsets of the sample space $\Omega$, and are therefore
*events*. Unlike discrete probability, where we assigned probabilities to
*points* in the sample space, in continuous probability we are assigning
probabilities to certain basic events (in this case, intervals).

By specifying the probability of intervals, we have also specified the 
probability of any event $E$ which can be written as the disjoint union of (a
finite or countably infinite number of) intervals. $E=\cup_iE_i$. For then we
can then write $\mathbb{P}[E]=\sum_i\mathbb{P}[E_i]$.

## Continuous Random Variables
Instead of specying $\mathbb{P}[X=a]$ as in the discrete case, we specify
$\mathbb{P}[a\leq X\leq b]$ for all intervals $[a,b]$, using a probability
density function.

A **probability density function** (p.d.f.) for a real-valued random variable
$X$ is a function $f: \mathbb{R}\rightarrow\mathbb{R}$ satisfying:

1. $f$ is non-negative: $f(x)\geq 0$ for all $x\in\mathbb{R}$.
2. The total integral of $f$ is equal to 1: $\int^\infty_{-\infty}f(x)dx=1$.

Then the distribution of $X$ is given by:

$$\mathbb{P}[a\leq X\leq b]=\int^b_a f(x)dx,\text{ for all }a<b$$.

$f$ works similary to the "histogram" we sometimes draw to picture the 
distribution of a discrete r.v. The first condition of non-negavtivity ensures
no event has a negative robability. The second condition ensures it defines a
valid probability distribution, because the r.v. $X$ must take on real values:

$$\mathbb{P}[X\in\mathbb{R}]=\mathbb{P}[-\infty <X < \infty]=\int_{-\infty}^
\infty f(x)dx=1$$.

It is tempting to think of $f(x)$ as a probability. However, $f(x)$ itself does
not correspond to the probability of anything, and there is no requirement that
$f(x)$ be bounded by 1. Rather, we can think of it as "probability per unit
length" in the vicinity of $x$.

### Cumulative Distribution Function

For a continuous random variable, one often discusses the **cumulative
distribution function** (c.d.f), which is the function 
$F(x)=\mathbb{P}[X\leq x]$. It is closely related to the p.d.f. of $X$, as 

$$F(x)=\mathbb{P}[X\leq x]=\int^x_{-\infty}f(z)dz$$.

Thus, one can describe an r.v. $X$ by its c.d.f. denoted by $F(x)$, which gives
its p.d.f. $f(x)$ as

$$f(x)=\frac{dF(x)}{dx}$$.

To connect to discrete probability, one might think of approximating a
continuous random variable $X$ as the set of probabilites for $X$ being in one
of a countably infinite set of intervals of length $dx$ on the real line. That
is the set of probabilities $\mathbb{P}[x_k<X\leq x_k+dx]$ where $x_k=k dx$
for $k\in\mathbb{Z}$.. In this view, $\mathbb{P}[X\leq x_i]=\sum_{j\leq i}
\mathbb{P}[x_j<X\leq x_j+dx]$. Connecting to the p.d.f., we have

$$\mathbb{P}[x_j<X\leq x_j+dx]\approx f(x_j) dx$$

for small "dx", and 

$$F(x_j)=\mathbb{P}[X\leq x_i]\approx\sum_{j\leq i}f(x_j) dx$$.

Taking the limit as $dx$ goes to zero yields the integral for the c.d.f.

### Expectation and Variance

The **expectation** of a continuous random variable $X$ with the p.d.f. $f$ is

$$\mathbb{E}[X]=\int_{-\infty}^{\infty}xf(x)dx$$.

The integral plays the role of summation in the discrete case. Likewise, the
**variance** of a continuous random variable $X$ with the p.d.f. $f$ is

$$Var(X)=\mathbb{E}[(X-\mathbb{E}[X])^2]=\mathbb{E}[X^2]-\mathbb{E}[X]^2=
\int_{-\infty}^\infty x^2f(x)dx-(\int_{-\infty}^\infty xf(x) dx)^2$$.

### Joint Distribution
A joint density function for two random variables $X, Y$ is a function $f:
\mathbb{R}^2\rightarrow\mathbb{R}$ satisfying:

1. $f$ is non-negative: $f(x,y)\geq 0$ for all $x,y\in \mathbb{R}$.
2. The total integral of $f$ is equal to 1: $\int^\infty_{-\infty}
\int^\infty_{-\infty}f(x,y)dx dxy=1$.

The joint distribution of $X$ and $Y$ is given by:

$$\mathbb{P}[a\leq X\leq b,c\leq Y\leq d]=\int^d_c\int_a^bf(x,y)dx dy,\text{ for
all }a\leq b \text{ and } c\leq d$$.

In analogy with the above, we can connect the joint density $f(x,y)$ with
probabilities by looking at a very small square $[x, x+dx]\times[y,y+dy]$ close
to $(x, y)$; then we have

$$\mathbb{P}[x\leq X\leq x+dx, y\leq Y\leq y+dx]=\int_y^{y+dx}\int_x^{x+dx}
f(u,v)du dv\approx f(x,y)dx dy$$.

Thus, we can interpret $f(x,y)$ as the "probability per unit area" in the
vicinity of $(x,y)$.

### Independence
Two continuous random variables $X, Y$ are independent if the events $a\leq X
\leq b$ and $c\leq Y\leq d$ are independent for all $a\leq b$ and $c\leq d$:

$$\mathbb{P}[a\leq X\leq b, c\leq Y\leq d]=\mathbb{P}[a\leq X\leq b]\mathbb{P}
[c\leq Y\leq d]$$.

For small $dx, dy$:

$$f(x,y)dx dx \approx \mathbb{P}[x\leq X\leq x+dx, y\leq Y\leq y+dy]\\
=\mathbb{P}[x\leq X\leq x+dx]\mathbb{P}[y\leq Y\leq y+dy]\\
\approx f_X(x)dx \times f_Y(y) dy=f_X(x)f_Y(y)dx dy$$

where $f_X$ and $f_Y$ are the marginal densities of $X$ and $Y$ respectively, so
we get 

$$f(x,y)=f_X(x)f_Y(y)\text{ for all }x,y\in\mathbb{R}$$.

## Exponential Distribution

The exponential distribution is a continuous version of the geometric
distribution. An example is, if we are waiting for an apple to fall off a tree,
it can be at any time, not necessarily on the tick of a discrete clock. Such
events are naturally modelled by exponential distribution:

For $\lambda > 0$, a continuous random variable $X$ with the p.d.f.

$$f(x)=\begin{cases}\lambda e^{-\lambda x},&\text{if }x\geq 0,\\0,&
\text{otherwise},\end{cases}$$

is called an exponential random variable with parameter $\lambda$, written as
$X\sim Exp(\lambda)$.

By definition, $f(x)$ is non-negative. Moreover,

$$\int^\infty_{-\infty}f(x)dx=\int^\infty_0\lambda e^{-\lambda x}dx=-e^
{-\lambda x}\rvert^\infty_0=1$$.

### Mean and Variance

Let $X$ be an exponential random variable with parameter $\lambda > 0$. Then,

$$\mathbb{E}[X]=\frac{1}{\lambda},\textit{ and } Var(X)=\frac{1}{\lambda^2}$$.

```{admonition} Proof

Using integration by parts,

$$\mathbb{E}[X]=\int^\infty_{-\infty}xf(x)dx=\int^\infty_0\lambda xe^{-\lambda
x}dx=-xe^{-\lambda x}\rvert^\infty_0+\int^\infty_0e^{-\lambda x}dx=0+(-\frac{e
^{-\lambda x}}{\lambda})\rvert^\infty_0=\frac{1}{\lambda}$$.

$$\mathbb{E}[X]=\int^\infty_{-\infty}x^2f(x)dx=\int^\infty_0\lambda x^2e^{-
\lambda x}dx=-x^2e^{-\lambda x}\rvert^\infty_0+\int^\infty_02xe^{-\lambda x}dx=
0+\frac{2}{\lambda}\mathbb{E}[X]=\frac{2}{\lambda^2}$$.

Therefore,

$$Var(X)=\mathbb{E}[X^2]-\mathbb{E}[X]^2=\frac{2}{\lambda^2}-\frac{1}{\lambda^2}
=\frac{1}{\lambda^2}$$.
```

### Geometric Vs. Exponential

Like geometric distribution, exponential distribution has a single parameter
$\lambda$ which characterizes the rate at which events happen. Note exponential
distribution satisfies for $t\geq 0$,

$$\mathbb{P}[X\geq t]=\int^\infty_t\lambda e^{-\lambda x} dx=-e^{-\lambda x}
\rvert^\infty_t=e^{-\lambda t}$$.

In other words, the probability that we have to wait more than time $t$ for the
event to happen is $e^{-\lambda t}$, which is an exponential decay. Consider a
discrete-time setting where we perform one trial every $\delta$ seconds (where
we can take $\delta\rightarrow 0$ to make time "continuous"), and our success
probability $p$ is $\lambda\delta$. Letting $Y$ denote the time in seconds until
we get a success,

$$\mathbb{P}[Y>k\delta]=(1-p)^k=(1-\lambda\delta)^k, \text{ for any integer }k
\geq 0$$.

For any $t>0$, we have

$$\mathbb{P}[Y>t]=\mathbb{P}[Y>(\frac{t}{\delta})\delta]=(1-\lambda\delta)^
\frac{t}{\delta}\approx e^{-\lambda t}$$

where the final approximation holds in the limit as $\delta\rightarrow 0$ with
$\lambda$ and $t$ fixed, ignoring the detail of rounding $\frac{t}{\delta}$ to
an integer since we are only doing an approximation.

We see this distribution has the same form as the exponential distribution with
parameter $\lambda$, where $\lambda$ plays an analogous role $p$, though 
$\lambda$ is not constrained to be $\leq$ 1.

## Normal Distribution

The **normal**, or **Gaussian** distribution has two parameters $\mu\in\mathbb
{R}$ and $\sigma>0$, a continuous random variable $X$ with p.d.f.

$$f(x)=\frac{1}{\sqrt{2\pi\sigma^2}}e^{-\frac{(x-\mu)^2}{2\sigma^2}}$$

is called a normal random variable with parameters $\mu$ and $\sigma^2$, and we
write $X\sim N(\mu,\sigma^2)$. In the special case $\mu=0$ and $\sigma=1$, $X$
is said to have the *standard normal distribution*.

By definition $f(x)\geq 0$. In addition,

$$\int^\infty_{-\infty}f(x)dx=\frac{1}{\sqrt{2\pi\sigma^2}}\int^\infty_{-\infty}
e^{-\frac{(x-\mu)^2}{2\sigma^2}}dx=1$$.

The fact that this integral evaluates to 1 is a routine exercise in
multivariable integral calculus.

A plot of the p.d.f. reveals the classic bell curve symmetric around $x=\mu$,
and a width determined by $\sigma$. The normal distribution has a nice property
with respect to shifting and rescaling.

```{admonition} Lemma
If $X\sim N(\mu,\sigma^2)$, then $Y=\frac{X-\mu}{\sigma}\sim N(0,1)$.
Equivalently, if $Y\sim N(0,1)$, then $X=\sigma Y+\mu\sim N(\mu,\sigma^2)$.
```

```{admonition} Proof
Given $X\sim N(\mu,\sigma^2)$, we can calculate the distribution of $Y=\frac{X-
\mu}{\sigma}$ as

$$\mathbb{P}[a\leq Y\leq b]=\mathbb{P}[\sigma a+\mu\leq X\leq \sigma b+\mu]=
\frac{1}{\sqrt{2\pi\sigma^2}}\int^{\sigma b+\mu}_{\sigma a+\mu} e^{-\frac{(x-
\mu)^2}{2\sigma^2}} dx=\frac{1}{\sqrt{2\pi}}\int^b_a e^{-\frac{y^2}{2}} dy$$.
```

### Mean and Variance

```{admonition} Theorem
For $X\sim N(\mu,\sigma^2)$, 

$$\mathbb{E}[X]=\mu\textit{ and } Var(X)=\sigma^2$$.
```

```{admonition} Proof
Consider the case when $X\sim N(0,1)$. By definition, its expectation is

$$\mathbb{E}[X]=\int^\infty_{-\infty}xf(x)dx=\frac{1}{\sqrt{2\pi}}\int^\infty_
{-\infty} e^{-\frac{x^2}{2}} dx=\frac{1}{\sqrt{2\pi}}(\int^0_{-\infty}xe^{-\frac
{x^2}{2}}dx+\int^\infty_0xe^{-\frac{x^2}{2}dx})=0$$.

The last step follows from the fact that $e^{-\frac{x^2}{2}}$ is symmetrical
about $x=0$, so the two integrals are the same except for the sign. For
variance,

$$Var(X)=\mathbb{E}[X^2]-\mathbb{E}[X]^2=\frac{1}{\sqrt{2\pi}}\int^infty_
{-\infty}x^2e^{-\frac{x^2}{2}}dx\\=\frac{1}{\sqrt{2\pi}}(-xe^{-\frac{x^2}{2}})
\rvert^\infty_{-\infty}+\frac{1}{\sqrt{2\pi}}\int_{-\infty}^\infty e^{-\frac{
x^2}{2}}dx\\=\frac{1}{\sqrt{2\pi}}\int^\infty_{-\infty}e^{-\frac{x^2}{2}}dx=1$$.

In the first line we have used the fact $\mathbb{E}[X]=0$, in the second line we
used integration by parts, and in the last line we used the special case. So in
the standard normal distribution, $\mathbb{E}[X]=\mu$ and $Var(X)=\sigma^2$.

Now, consider the general case. By the Lemma, we know $Y=\frac{X-\mu}{\sigma}$
is a standard normal random variable, so $\mathbb{E}[Y]=0$ and $Var(Y)=1$, as we
have established above. Therefore, using linearity,

$$0=\mathbb{E}[Y]=\mathbb{E}[\frac{X-\mu}{\sigma}]=\frac{\mathbb{E}[X]-\mu}
{\sigma},$$

and hence $\mathbb{E}[X]=\mu$. For variance,

$$1=Var(Y)=Var(\frac{X-\mu}{\sigma})=\frac{Var(X)}{\sigma^2},$$

and hence $Var(X)=\sigma^2$.
```

### Sum of Independent Normal Random Variables

The sum of *independent* random normal variables is also normally distributed.
Let $X\sim N(0,1)$ and $Y\sim N(0,1)$ be independent standard normal random
variables, and suppose $a,b\in \mathbb{R}$ are constants. Then $Z=aX+bY\sim
N(0,a^2+b^2)$.

```{admonition} Proof
Since $X$ and $Y$ are independent, by the theorem we know the joint density of 
$(X,Y)$ is

$$f(x,y)=f(x)f(y)=\frac{1}{2\pi}e^{-\frac{x^2+y^2}{2}}$$.

The key observation is that $f(x,y)$ is rotationally symmetric around the origin
(i.e. $f(x,y)$ only depends on the value $x^2+y^2$, the distance of the point
$(x,y)$ from the origin $(0,0)$.

Thus, $f(T(x,y))=f(x,y)$ where $T$ is any rotation of the plane $\mathbb{R}^2$
about the origin. It follows that for any set $A\subseteq\mathbb{R}^2$. Now,
given any $t\in\mathbb{R}$, we have

$$\mathbb{P}[Z\leq t]=\mathbb{P}[aX+bY\leq t]=\mathbb{P}[(X,Y)\in A]$$

where $A$ is the half plane $\{(x,y)|ax+by\leq t\}$. The boundary line $ax+by=t$
lies at a distance $d=\frac{t}{\sqrt{a^2+b^2}}$ from the origin. Therefore, set 
$A$ can be rotated into the set 

$$T(A)=\{(x,y)\rvert x\leq\frac{t}{\sqrt{a^2+b^2}}\}$$.

This rotation does not change probability:

$$\mathbb{P}[Z\leq t]=\mathbb{P}[(X,Y)\in A]=\mathbb{P}[(X,Y)\in T(A)]\\=
\mathbb{P}[X\leq\frac{t}{\sqrt{a^2+b^2}}]=\mathbb{P}[\sqrt{a^2+b^2}X\leq t]$$.

Since the equation above holds for all $t\in\mathbb{R}$, we can conclude $Z$ has
the same distribution as $\sqrt{a^2+b^2}X$. Since $X$ has standard normal 
distribution, we know by the lemma that $\sqrt{a^2+b^2}X$ has normal 
distribution with mean 0 and variance $a^2+b^2$, hence we conclude $Z=aX+bY$
has the same values.
```

The general case follows such that:

```{admonition} Theorem
Let $X\sim N(\mu_X,\sigma_X^2)$ and $Y\sim N(\mu_Y,\sigma^2_Y)$ be independent
normal random variables. Then for any constants $a, b \in \mathbb{R}$, the
random variable $Z=aX+bY$ is also normally distributed with mean $\mu=a\mu_X+
b\mu_Y$ and variance $\sigma^2=a^2\sigma^2_X+b^2\sigma^2_Y$.
```

```{admonition} Proof
By the lemma, $Z_1=\frac{X-\mu_X}{\sigma_X}$ and $Z_2=\frac{Y-\mu_Y}{\sigma_Y}$
are independent standard normal random variables. We can write

$$Z=aX+bY=a(\mu_X+\sigma_XZ_1))+b(\mu_Y+\sigma_YZ_2)=(a\mu_X+b\mu_Y)+(a\sigma_X
Z_1+b\sigma_YZ_2)$$.

By the previous theorem, $Z'=a\sigma_XZ_1+b\sigma_YZ_2$ is normally distributed
with mean $0$ and variance $\sigma^2=a^2\sigma^2_x+b^2\sigma_Y^2$. Since $\mu=
a\mu_X+b\mu_Y$ is a constant, by the lemma we conclude that $Z=\mu+Z'$ is a
normal random variable with mean $\mu$ and variance $\sigma^2$.
```