# Modular Arithmetic

Modular arithmetic is a way of reducing problems to work on a smaller range of
numbers $\{0,1,\cdots,N-1\}$, and wraps around when you try to leave this range;
for example, the time of day (where $N=12$).

We define $x \pmod{m}$ ("x modulo m") to be the remainder $r$ when we divide $x$
by $m$. $(x \pmod{m}=r)\implies(x=mq+r)$ where $0\leq r\leq m-1$ and $q$ is an
integer. Thus, $16\pmod{12}\equiv 4$ and $70\pmod{5}\equiv 0$.

### Computation
Notice that $(x+y)\pmod{m} \equiv x\pmod{m}+y\pmod{m}$. For example, if $x=70, 
y=61$ and $m=20$, we can either do:

$$70+61\pmod{20}=131\pmod{20}\equiv11$$

or

$$70\pmod{20}+61\pmod{20}\equiv10+1=11$$.

Likewise, we could save significant effort with this on multiplification: $(x
\times y)\pmod{m} \equiv x\pmod m + y\pmod m$.

$$70\times61\pmod{20}=4270\pmod{20}\equiv10$$

$$70\pmod{20}\times61\pmod{20}\equiv10\times1=10$$.

More generally, while carrying out any sequence of additions, subtractions or
multiplifications mod m, we can get the same answer if we reduce any
intermediate results, which can considerably simplify calculations.

## Set Representation

There is an alternative view of modular arithmetic that can help make this more
understandable. For any integer $m$, we say $x$ and $y$ are congruent modulo $m$
if they differ by a multiple of $m$, or in symbols,

$$x\equiv y\pmod{m}\iff m\text{ divides }(x-y)$$.

For example, 31 and 3 are congruent modulo 14 because 14 divides $31-3$. We can
also write $22 \equiv -2\pmod{12}$. Notice that congruent modulos have the same
remainder modulo $m$.

In general, if we work modulo $m$, we get $m$ such disjoint sets whose union is
the set of all integer: these are often called *residue classes mod m*. We can
think of each set as represented by the unique element it contains in the range
$(0, \cdots, m-1)$. The set represented by element $i$ would be all numbers $z$
such that $z=mx+i$ for some integer $x$. Observe all of these numbers have 
remainder $i$ when divided by $m$; therefore they are congruent modulo $m$.

With this knowledge, we will prove our statement above in the "Computation"
section:

```{admonition} Theorem
If $a\equiv c \pmod{m}$ and $b\equiv d\pmod{m}$, then $a+b\equiv c+d\pmod{m}$.
```

```{admonition} Proof
We know that $c=a+km$ and $d=b+lm$ for integers $k, l$, so $c+d=a_km+b+lm=
a+b+(k+l)m$, which means that $a+b\equiv c+d\pmod{m}$. The proof for
multiplication is similar.
```

## Exponentiation
Another standard operation in arithmetic algorithms is raising one number to a
power modulo another number: $x^y\pmod{m}$, where $x,y,m$ are natural numbers
and $m>0$? Here is a fast approach:

```
algorithm mod-exp(x,y,m)
	if y=0
		return(1)
	else
		z=mod-exp(x,y div 2,m)
		if y mod 2 = 0
			return(z * z mod m)
		else
			return(x * z * z mod m)
```

This algorithm uses the fact any $y>0$ can be written as $y=2a$ or $y=2a+1$,
where $a=\lfloor \frac{y}{2}\rfloor$ (which we have written as `y div 2` in the
above pseudo-code), plus the facts:

$$x^{2a}=(x^a)^2,\text{ and } x^{2a+1}=x(x^a)^2$$.

The number of recursive calls is exactly equal to the number of bits $n$ in
$y$. If we charge only constant time for each arithmetic operation, the running
time for `mod-exp` is $O(n)$, which is very efficient!

This is of course, only an elementary approach to understanding runtime. A
fuller analysis of such algorithms is performed in CS170.

## Bijections

## Inverses

### Euclid's Algorithm

### Extended Euclid's Algorithm

## Chinese Remainder Theorem