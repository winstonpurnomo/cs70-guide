# Proofs

As a CS70 student, you will be taught how to prove logical statements. Proofs
*guarantee* a statement is true, and can be very powerful. They are a finite
sequence of steps called *logical deductions* which establishes the truth of a
desired statement. It uses *finite* means to guarantee the truth of a statement
with *infinitely many cases*.

A proof is often structured as follows. First, there are certain statements
called *axioms* that we accept without proof. Starting from these, a proof
consists of a sequence of logical deductions: simple steps that apply the rules
of logic. Each statement follows from previous statements.

This note will first cover each proofing technique, then give an example.

```{admonition} Preamble

In this section, we will use the following notation and basic mathematical
facts.

* Let $\mathbb{Z}$ denote the set of integers ($\mathbb{Z}=\{\cdots,-1,0,1,2,
\cdots\}$).
* Let $\mathbb{N}$ denote the set of natural numbers ($\mathbb{N}=\{0,1,2,
\cdots\}$).
* The sum or product of two integers is an integer; we say the set of integers
is *closed* under addition and multiplication.
* The same is true for natural numbers.
* Given integers $a$ and $b$, we say $a$ divides $b$ (denoted $a|b$) iff there
exists an integer $q$ such that $b=aq$. (For example, $2|10$).
* $:=$ is used to indicate a definition. (For example, $q:=6$ defines the
variable $q$ as having the value 6).
```

## Direct Proof
A direct proof proceeds as follows. For each $x$, the proposition we are trying
to prove is of the form $P(x)\implies Q(x)$. A direct proof of this starts by
assuming $P(x)$ for a generic value of $x$ and eventually concludes $Q(x)$ 
through a chain of implications.

* Goal: To prove $P\implies Q$.
* Approach:
  1. Assume $P$
  2. $\cdots$
  3. Therefore $Q$.

```{admonition} Theorem
For any $a, b, c \in\mathbb{Z}$, if $a|b$ and $a|c$, then $a|(b+c)$.
```

```{admonition} Proof
Assume that $a|b$ and $a|c$. There exists integers $q_1$ and $q_2$ such that
$b=q_1a$ and $c=q_2a$. Then, $b+c=q_1a+q_2a=(q_1+q_2)a$. Since $\mathbb{Z}$ is
closed under addition, we conclude $(q_1+q_2)\in\mathbb{Z}$, so $a|(b+c)$ as
desired.
```

The key insight in the above proof is that we did not assume any specific values
for $a, b$ and $c$, so our proof holds for arbitrary values of $a, b, c\in
\mathbb{Z}$!.

## Proof by Contraposition
Recall from the previous topic that $(P\implies Q)\equiv(\neg Q\implies\neg P)$.
Sometimes, the latter can be easier to prove than the former.

* Goal: To prove $P\implies Q$.
* Approach:
  1. Assume $\neg Q$
  2. $\cdots$
  3. Therefore $\neg P$.

```{admonition} Theorem
Let $n$ be a psoitive integer and let $d$ divide $n$. If $n$ is odd, then $d$
is odd.
```

Proving this via the technique of direct proof seems difficult, since we have
no easy way to proceed after assuming $n$ is odd. But the contraposition
technique is easier!

```{admonition} Proof
Assume $d$ is even. By definition, $d=2k$ for some $k\in\mathbb{Z}$. Because
$d|n, n=dl$ for some $l\in\mathbb{Z}$. Combining these two statements, $n=dl=
(2k)l=2(kl)$. We conclude that $n$ is even, thus by contraposition, the
statement is true.
```

## Proof by Contradiction
The idea in proof by contradiction is to assume the claim you wish to prove is
false. Then you show this leads to a conclusion which is utter nonsense: a 
contradiction; hence, the claim must in fact have been true.

Proof by contradiction is a good technique for proving something you think is
obviously true.

* Goal: To prove $P$.
* Approach:
  1. Assume $\neg P$.
  2. $\cdots$
  3. $R$
  4. $\cdots$
  5. $\neg R$
* Conclusion: $\neg P\implies\neg R\wedge R$, which is a contradiction, 
therefore $P$ holds.

```{admonition} Theorem
There exist no integers $a$ and $b$ for which $18a+6b=1$.
```

The credit for this proof goes to Dr. Jonathan Senning at Gordon College, from
Math 231: Transition to Higher Mathematics class from Fall 2014.

```{admonition} Proof
Assume there exist integers $a$ and $b$ for which $18a+6b=1$.

Dividing by 6, we obtain $3a+b=\frac{1}{6}$.

This is a contradiction, since by the closure properties, $3a+b$ is an integer,
but $\frac{1}{6}$ is not. Therefore, it must be that no integers $a$ and $b$ can
exist for which $18a+6b=1$.
```

## Proof by Cases
The idea behind proof by cases is that sometimes, when we wish to prove a claim,
we don't know which of a set of possible cases is true, but we know at least one
of the cases is true. We can instead prove *all* the cases; then, clearly, the
claim must hold.

```{admonition} Theorem
There exist irrational numbers $x$ and $y$ such that $x^y$ is rational.
```

```{admonition} Proof
We proceed by cases. The statement is quantified by an existential quantifier,
thus it is sufficient to demonstrate a single example, $x$ and $y$, where the
statement is true. To do so, let $x=\sqrt{2}$ and $y=\sqrt{2}$.

Let us divide our proof into two cases, exactly one of which must be true:

1. $\sqrt{2}^\sqrt{2}$ is irrational, or
2. $\sqrt{2}^\sqrt{2}$ is rational

Assume that $\sqrt{2}^\sqrt{2}$ is rational. Our first guess for $x$ and $y$
was not quite right, but now we have a new irrational number, 
$\sqrt{2}^\sqrt{2}$. Let $x=\sqrt{2}^\sqrt{2}$ and $y=\sqrt{2}$. Then,

$$x^y=(\sqrt{2}^\sqrt{2})^\sqrt{2}=\sqrt{2}^{\sqrt{2}\sqrt{2}}=\sqrt{2}^2=2$$

We started with two irrational numbers $x$ and $y$ and obtained a rational $x^y$
in this case. In the other case, our claim is immediately yielded. Thus, since
one of the two cases must hold, we conclude the theorem must be true.
```

The above is an example of a $non-constructive$ proof. We do not know which
of the two pairs of values we set $x$ and $y$ to is actually true: we've
proven some object $X$ exists, without explicitly revealing what $X$ is!