# Logic
Propositional logic is the framework upon which discrete mathematics is built.

A **proposition** is a statement which is either true or false. The following
are all propositions:

1. $1+1=3$.
2. You are currently taking CS70.

The following are not:

1. $2+2$.
2. $x=6$. (What is $x$?)

And the following are not either, as they are fuzzy.

1. Tom Brady often plays football. (What is "often"?)
2. CS70 is a difficult class. (What is "difficult"?)

Propositions can be combined to form more complex statements. Let $P$ and $Q$ be
variables representing propositions. We can join them using the following 
connectives:

1. Conjunction: $P\wedge Q$("P and Q"). True only when both $P$ and $Q$ are 
true.
2. Disjunction: $P\vee Q$("P or Q"). True when either $P$ or $Q$ is true.
3. Negation: $\neg P$ ("not P"). True when $P$ is false.

Statements like these and their variables are called **propositional forms**.

The *Law of the Excluded Middle* states that for any proposition $P$, either it
is true or $\neg P$ is true, but not both. Thus, $P\vee\neg P$ is always true.

A propositional form that is always true regardless of the truth values of its
variables is a **tautology**. Conversely, a statement which is always false
(e.g. $P\wedge\neg P$) is a **contradiction**.

We can describe the possible values of a propositional form using a truth table:

|$P$|$Q$|$P\wedge Q$|
|:-:|:-:|:-:|
| T | T | T |
| T | F | F |
| F | T | F |
| F | F | F |

|$P$|$\neg P$|
|:-:|:-:|
| T | F |
| F | T |

Another kind of propositional form is an **implication**: $P\implies Q$. This
means "if P, then Q". $P$ is the hypothesis of the implication, and $Q$ is the
conclusion. For example,

"If you took CS70, you learned about propositional forms"

An implication $P\implies Q$ is only false when $P$ is true and $Q$ is false. 
The above statement is only false if you did not learn about propositional forms
when you took CS70.

|$P$|$Q$|$P\implies Q$| $\neg P\vee Q$|
|:-:|:-:|:-:|:-:|
| T | T | T | T |
| T | F | F | F |
| F | T | T | T |
| F | F | T | T |

Note $P\implies Q$ is always true when $P$ is false, which means there are many
mathematically sound statements that are nonsense in English. For example,

"If 2+2=5, then pizza is made from grass". 

When an implication is stupidly true because the hypothesis is false, then we
say it is *vacuously true*.

$P\implies Q$ is logically equivalent to $\neg P\vee Q$, as can be seen by
comparing their columns in the truth table. We write this as $(P\implies Q)
\equiv(\neg P\vee Q)$.

There are other ways to state this:

1. if P, then Q
2. Q if P
3. P only if Q
4. P is sufficient for Q
5. Q is necessary for P
6. Q unless not P

If both $P\implies Q$ and $Q \implies P$ are true, then we say "P if and only if
Q" (shortened as "P iff Q"). Logically it is written as $P\iff Q$. $P\iff Q$ is
only true if $P$ and $Q$ have the same truth values.

Given an implication $P\implies Q$, we can also define its

1. **Contrapositive**: $\neg Q\implies \neg P$
2. **Converse**: $Q\implies P$

And here are the truth tables:

|$P$|$Q$|$P\implies Q$| $Q \implies P$|$\neg Q\implies\neg P$|$P \iff Q$|
|:-:|:-:|:-:|:-:|:-:|:-:|
| T | T | T | T | T | T |
| T | F | F | T | F | F |
| F | T | T | F | T | F |
| F | F | T | T | T | T |

Notice that $P\implies Q$ and its contrapositive are *logically equivalent*. 

$$(P\implies Q)\equiv(\neg Q\implies\neg P)$$

## Quantifiers

The mathematical statements in CS70 are a little more complicated than those
from earlier, such as "If $n$ is an odd integer, so is $n^3$.

The reason the above is a statement, while $x=6$ from earlier is not? In the
example, there is an underlying "universe" that we are working in, and the 
statements are *quantified* over that universe. There are two basic quantifiers:
the *universal quantifier* $\forall$ ("for all"), and the *existential
quantifier* $\exists$ ("there exists").

Examples.

1. For all natural numbers $n$, $n^2+n+41$ is prime: $\mathbb{N}:(\forall n\in
\mathbb{N})(n^2+n+41 \text{ is prime.})$
2. There is an integer $k$ that is both even and odd: $\mathbb{Z}: (\exists k\in
\mathbb{Z})(z \text{ is both even and odd.})$

Quantifiers are not commutative. 

$$(\forall x\in\mathbb{Z})(\exists x\in\mathbb{Z}(x<y)\not\equiv(\exists y\in
\mathbb{Z})(\forall x\in\mathbb{Z})(x<y)$$.

The first statement says that given an integer, there is a larger one. The
second says that there exists a largest integer. The former is true, the latter
is not.

## Negation
De Morgan's Laws specify how negation applies to conjunctions and disjunctions:

$$\neg(P\wedge Q)\equiv(\neg P\vee\neg Q)$$

$$\neg(P\vee Q)\equiv(\neg P\wedge\neg Q)$$

Negating quantifiers also follows analogous laws:

$$\neg(\forall xP(x))\equiv \exists x\neg P(x)$$

$$\neg(\exists xP(x))\equiv \forall x\neg P(x)$$

It may be helpful to consider what De Morgan's Laws do to English statements to
convince yourself that these rules are in fact, true.