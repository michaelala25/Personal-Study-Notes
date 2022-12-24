# Weak Containment of Representations and Amenability

**Definition:** Let $\Gamma$ be a (locally compact) group, and $\pi : \Gamma\to\mathcal{U}(\mathcal{H})$ and $\rho : \Gamma\to\mathcal{U}(\mathcal{K})$ two unitary representations. We say $\pi$ is a **subrepresentation** of $\rho$ if there is an isometry $V : \mathcal{H}\to\mathcal{K}$ such that $V\pi(g)V^* = \rho(g)$ for all $g\in\Gamma$.

**Definition:** Given $\pi, \rho$ as above, we say $\pi$ is **quasi-contained** in $\rho$ if $\pi$ is unitarily equivalent to a subrepresentation of an amplification of $\rho$.

**Theorem:** Let $W^*_\pi(\Gamma) := \pi(\Gamma)''$. Then $\pi$ is quasi-contained in $\rho$ if and only if the identity map on $\Gamma$ extends to a normal $*$-homomorphism $W_\rho^*(\Gamma)\to W_\pi^*(\Gamma)$.

**Definition:** Let $\pi, \rho$ be unitary representations, as above. We say $\pi$ is **weakly contained** in $\rho$ (denoted $\pi\prec\rho$) if for all $\xi\in\mathcal{H}$, $F\subset\Gamma$ compact (or finite?), and $\epsilon > 0$, there exists $\eta_1, ..., \eta_n\in\mathcal{K}$ such that
$$
\left|\langle\pi(\gamma)\xi, \xi\rangle - \sum_{j=1}^n\langle\rho(\gamma)\eta_j, \eta_j\rangle\right| < \epsilon,\qquad \forall\gamma\in F
$$
**Question:** Is it true that $\pi\prec\rho$ if and only if the map $\rho(g)\mapsto\pi(g)$ extends to a $*$-homomorphism of C\*-algebras?

**Definition:** Given a unitary representation $\pi$ as above, we say $\pi$ **almost has invariant vectors** if $\forall F\subseteq\Gamma$ compact and $\epsilon > 0$, there exists $\xi\in\mathcal{H}$ such that $\|\pi(\gamma)\xi - \xi\| < \epsilon$ for all $\gamma\in F$. Equivalently we can require each $\xi$ be a unit vector.

**Definition:** We say $\pi$ admits **<u>an</u> almost invariant vector** $(\xi_n)_{n\in\N}$ (notice the subtle difference in language) if for all $\gamma\in\Gamma$, $\lim_n\|\pi(\gamma)\xi_n - \xi_n\| = 0$, and each $\xi_n$ has <u>norm 1</u> (equivalently $\sup_n\|\xi_n\|<\infty$).

**Proposition:** Let $\pi : \Gamma\to\mathcal{U}(\mathcal{H})$ be a unitary representation of a <u>locally compact</u>, <u>second countable</u> group. Then if $\pi$ almost has invariant vectors, then $\pi$ has an almost invariant vector. If $\pi$ is continuous (e.g. if $\Gamma$ is discrete) then $\pi$ almost has invariant vectors if and only if $\pi$ has an almost invariant vector.

**Proof:**  $(\implies)$: Suppose $\pi$ almost has invariant vectors. Since $\Gamma$ is locally compact and second countable, it admits a countable increasing cover of compact sets $\{F_n\}_{n\in\mathbb{N}}$. Choose $\xi_n$ such that $\|\pi(\gamma)\xi_n - \xi_n\| < \frac1n$ for all $\gamma\in F_n$. Then it is not hard to see that $(\xi_n)_{n\in\N}$ is an almost invariant vector for $\pi$.

$(\impliedby):$ Suppose $\pi$ is continuous, $(\xi_n)_{n\in\mathbb{N}}$ an approximate invariant vector. Let $F\subseteq\Gamma$ be compact and $\epsilon > 0$. For each $\gamma\in F$, choose an open neighbourhood $U_\gamma$ such that $\|\pi(\gamma) - \pi(\gamma')\| < \epsilon/2$ for all $\gamma'\in U_\gamma$. Cover $F$ with finitely many $U_\gamma$'s, say $(U_{\gamma_i})_{i=1}^k$. For each $\gamma_i$, choose $N_i\in\mathbb{N}$ such that for all $n\ge N_i$, $\|\pi(\gamma)\xi_n - \xi_n\| < \epsilon/2$. Let $n\ge \max\{N_1, ..., N_k\}$, and $\xi = \xi_n$. Then it is not hard to check that $\|\pi(\gamma)\xi - \xi\| < \epsilon$ for all $\gamma\in F$. $\square$

### Relationship to Amenability

Consider the left-regular representation $\lambda$. The existence of almost invariant vectors for $\lambda$ *kind of* looks like the existence of a Følner sequence/net, right?

What we're going to do is show that if $\Gamma$ is amenable if and only if $\lambda$ admits almost invariant vectors, and then show that this is equivalent to $\lambda$ weakly containing the trivial representation (taking $\gamma\mapsto I_{\mathcal{H}}$).