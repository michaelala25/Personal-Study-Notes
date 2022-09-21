# Elements of KK-Theory

These notes are my collected walkthrough of the book "Elements of KK-Theory" by Kjeld Knudsen Jensen and Klaus Thomsen. Some of the proofs are my own (but not all of them, I'm not that smart T_T) and some are omitted for brevity (these are essentially notes to help me get "up to speed".)

## Hilbert C*-Modules

### The Basics

**Definition:** A <u>pre-Hilbert $B$-module</u> is a <u>complex vector space</u> $E$, which is also a <u>right $B$-module</u>, which comes equipped with a function $\langle\cdot,\cdot\rangle : E\times E\to B$ which acts as a sort of "$B$-valued inner product." It is required to satisfy the following properties:

1. It is <u>linear</u> in the <u>second variable</u>.
2. $\langle x, yb\rangle = \langle x, y\rangle b$
3. $\langle x, y\rangle^* = \langle y, x\rangle$
4. $\langle x, x\rangle\ge 0$
5. $x\neq 0$ implies $\langle x, x\rangle \neq 0$.

In a sense, a pre-Hilbert $B$-module can be thought of as merely a generalization of an inner-product space, where instead of letting the *scalar field* $\mathbb{C}$ act on the vectors, we are replacing it with a general C*-algebra.

Notice that the axioms imply that $\langle\cdot, \cdot\rangle$ is *antilinear* in the first argument, and $\langle xb, y\rangle = b^*\langle x, y\rangle$.

**Lemma:** Given a pre-Hilbert $B$-module $E$, define $\|x\| := \|\langle x,x\rangle\|^{1/2}$. Then $\|\cdot\|$ is a *norm* on $E$, and moreover satisfies the following properties:

1. (Generalized Algebra-Norm Property) $\|xb\| \le \|x\|\|b\|$
2. (Generalized Cauchy-Schwarz) $\|\langle x, y\rangle\|\le \|x\|\|y\|$.

**Proof:** 1 is easy. The proof of 2 mimics the standard proof of Cauchy-Schwarz. We start by observing that
$$
0\le \langle tx + y, tx + y\rangle = \langle x, x\rangle t^2 + 2\Re\langle x, y\rangle t + \langle y, y\rangle
$$
For any state $\phi$ on $B$, we have $0\le \phi(\langle x, x\rangle)t^2 + 2\Re\phi\langle x, y\rangle t + \phi\langle y, y\rangle$, and an analysis of the discriminant reveals that
$$
\Re\phi(\langle x, y\rangle)\le\phi(\langle x, x\rangle)\phi(\langle y, y\rangle) \le \|\langle x, x\rangle\|\|\langle y, y\rangle\|
$$
Fortunately we can choose $\phi$ such that $\phi(\langle x, y\rangle\langle x, y\rangle^*) = \|\langle x, y\rangle\|$.

The proof that $\|\cdot\|$ is a norm follows from these properties. $\square$

**Definition:** A Hilbert $B$-module is a pre-Hilbert $B$-module which is complete with respect to the induced norm.

The following facts are easy to verify.

**Facts:**

1. Given a pre-Hilbert $B$-module $E$, the completion with respect to the induced norm is a Hilbert $B$-module. 
2. The $B$-valued inner product on a Hilbert $B$-module $E$ is continuous.

**Example:** Given a C\*-algebra $B$, $B$ is its own Hilbert $B$-module, with $B$-valued inner product given by $\langle a, b\rangle = a^*b$.

**Example:** Given a C*-algebra $B$, consider the space $E := \oplus_{c_{00}}B$ the set of sequences of elements in $B$ which are <u>eventually zero</u> (which we take pause to recall the distinction with <u>converging to zero</u>), with natural right $B$-module structure. Define
$$
\langle(a_n)_n, (b_n)_n\rangle := \sum_n a_n^*b_n
$$
Then $E$ is a pre-Hilbert $B$-module, and we denote the completion by $H_B$. When $B = \mathbb{C}$, the construction obtains the Hilbert space $H_{\mathbb{C}} := \ell^2(\mathbb{N})$. In general, $H_B$ consists of the sequences $(a_n)_n$ of elements of $B$ for which the infinite sum $\sum_n a_n^*a_n$ exists. We remark that this is a *strict superset* of the space of *square-summable sequences in $B$*: a sequence for which $\sum_n \|a_n\|^2<\infty$ is necessarily one for which $\sum_n a_n^*a_n$ exists.

From hereon-in we will primarily be working with Hilbert C\*-modules rather than pre-Hilbert C\*-modules.

**Fact:** Denote by $\langle E, E\rangle$ the closed linear span of the set $\{\langle x, y\rangle\ :\ x, y\in E\}$. It is not hard to check that this is a <u>closed, two-sided ideal in $B$</u>.

**Lemma:** Let $E$ be a Hilbert $B$-module and let $\{u_i\}$ a net in $\mathbb{B}(B_{sa})$ such that $\lim xu_i = x$ for all $x\in \langle E, E\rangle.$ Then $\lim eu_i = e$ for all $e\in E$.

**Proof:** Straightforward.

### Maps Between Hilbert $B$-Modules

**Definition:** For Hilbert $B$-modules $E, F$, denote by $\mathcal{L}_B(E, F)$ the set of functions $T : E\to F$ for which there exists an "adjoint" map $T^* : F\to E$ such that $\langle Tx, y\rangle = \langle x, T^*y\rangle$ for all $x\in E, y\in F$.

It is not hard to check that the requirement of the existence of an "adjoint" necessitates that both $T$ and $T^*$ be <u>linear maps</u>, and are moreover both $B$-module maps.

**Fact:** $\mathcal{L}_B(E, F)$ is a subset of the Banach space of bounded linear maps $\mathcal{B}(E, F)$. In other words, each $T\in\mathcal{L}_B(E, F)$ is bounded.

**Proof:** We have to check that the set $\{Tx\ |\ x\in \mathbb{B}(E)\}$ is bounded. Consider the family of continuous linear operators $T_x : E\to B$, indexed by $x\in\mathbb{B}(E)$, defined by taking $y\mapsto T_xy := \langle Tx, y\rangle = \langle x, T^*y\rangle$. For any $\|y\|\le 1$, the set $\{\|T_x(y)\|\ :\ \|x\|\le 1\}$ is bounded, since $\|T_x(y)\| = \|\langle x, T^*y\rangle\|\le \|T^*y\|$. Thus by Uniform-Boundedness, $\{\|T_x\|\ :\ \|x\|\le 1\}$ is also bounded. Notice that $\|T_x\|\le \|Tx\|$  but also $\|T_x\|\ge \left\|T_x\left(\frac{Tx}{\|Tx\|}\right)\right\| = \|Tx\|$, and so the set $\{Tx\ |\ x\in\mathbb{B}(E)\}$ is indeed bounded. $\square$

**Proposition:** $\mathcal{L}_B(E, F)$, equipped with the norm inherited from $\mathcal{B}(E, F)$, is a Banach space. Moreover, the space $\mathcal{L}_B(E) := \mathcal{L}_B(E, E)$ is a C*-algebra.

**Proof:** WIP.



#### GNS Representations of $\mathcal{L}_B(E)$

**Definition:** Take $\phi\in S(B)$ (the state space of $B$). Define $N_\phi = \{x\in E\ :\ \phi(\langle x, x\rangle) = 0\}$. Then $N_\phi$ is a Hilbert $B$-submodule of $E$. The proof mirrors that of the GNS construction (in fact, if $B = E$ and $\langle x, y\rangle = x^*y$, then the construction is identical), but uses the additional fact that $|\phi(\langle x, y\rangle)| \le \phi(\langle x, x\rangle)\phi(\langle y, y\rangle)$ which we derived in the proof of the Cauchy-Schwarz inequality.

The quotient module $E/N_\phi$ comes with an induced $B$-valued inner product: $\langle x + N_\phi, y + N_\phi\rangle = \langle x, y\rangle$, but also with an *ordinary* inner product given by $\langle x + N_\phi, y + N_\phi\rangle := \phi(\langle x, y\rangle)$. The completion of $E/N_\phi$ with respect to this inner product is the *Hilbert space* denoted $H_\phi$.

**Definition:** We define a representation $\pi_\phi : \mathcal{L}_B(E) \to \mathcal{B}(H_\phi)$ given by taking $T$ and mapping it to the operator $\pi_\phi(T)$ defined by $\pi_\phi(T)(a + N_\phi) := T(a) + N_\phi$.