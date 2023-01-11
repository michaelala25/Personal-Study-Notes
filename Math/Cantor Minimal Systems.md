# Cantor Minimal Systems

These are my collected notes while studying the book "Cantor Minimal Systems" by Ian F. Putnam. These notes only *loosely* follow the flow of the book, skipping over certain chapters and details that are extraneous to my required understanding.

## Groupoids, Bratteli Diagrams, and $\mathbb{Z}$-Actions on Cantor Sets

There's some sort of correspondence between our things.

## Cantor Spaces

We all know and love the standard ternary Cantor set $C$, the subset of the unit interval obtained by recursively removing the middle third of the previous set of intervals. $C$ has a number of cute properties which are fun little exercises for third year topology students to play with: $C$ is *compact*, *totally disconnected*, *metrizable*, and *perfect*. We recall the definitions of the second and fourth terms below:

**Definition:** A topological space $X$ is **totally disconnected** if the connected components of $X$ are the singletons $\{x\}$, for each $x\in X$. In other words, $X$ has no non-trivial connected sets.

It is easy to think that this implies the topology on $X$ is discrete, but this is not always the case. The connected components of a topological space are certainly always *closed*, but they are not necessarily open. An analogous notion of totally *path*-disconnected would indeed be equivalent to discreteness, since path-components are clopen. Additionally, a locally path-connected totally disconnected space would necessarily be discrete, since in locally path-connected spaces the path components and connected components coincide.

*Remark:* There is also a notion of an *extremally disconnected* space $X$, which is the case if the closure of every open set is open. In this scenario, any open set $U$ allows us to construct a separation for $X$, namely $(U, (U^c)^\circ)$. Such spaces are *necessarily* totally disconnected, but the converse is not true.

**Definition:** A topological space $X$ is **perfect** if $X$ has no isolated points.

Each of the four properties of $C$ stated above are **topological properties**, in the sense that they are preserved under homeomorphism. Many such representations of $C$ exist: a classical one being the space $\{0, 1\}^{\mathbb{N}}$ endowed with the product topology (each $\{0, 1\}$ endowed with its discrete topology). $C$ is also homeomorphic to the space of $p$-adic integers.

**Theorem:** Given a metric space $X$, $X$ is compact if and only if $X$ is the continuous image of $C$.

**Rough Proof:** The easiest way to "witness" this truth is to use $C = \{0, 1\}^\mathbb{N}$. If $X$ is compact, then we can obtain covers of $X$ with finitely balls with fixed radii, and we can do se while letting these radii tend to zero. Hypothetically, we should be able to *partition* $X$ this way: cover $X$ in$ \frac12\text{diam}(X)$ balls, then $\frac14\text{diam}(X)$ balls, then $\frac18\text{diam}(X)$ balls, and so on. Then an infinite $\{0, 1\}$-sequence identifies a path through this partition, which uniquely identifies a point in $X$. We leave out a formal proof of this fact, since the details are messy.

**Definition:** A **Cantor set** is a non-empty topological space which is compact, totally disconnected, metrizable, and perfect.

**Theorem:** Any two Cantor sets are homeomorphic.

## Bratteli Diagrams

**Definition:** A **Bratteli diagram** $(V, E)$ is an infinite graph consisting of a set $V = \bigsqcup_{n\ge 0}V_n$ of vertices, and a set $E = \sqcup_{n\ge 0}E_n$ of edges, such that each $V_n$ and $E_n$ is finite, $V_0 = \{v_0\}$ consists of a single point, the edges of $E_n$ connect the vertices of $V_n$ to the vertices of $V_{n+1}$, and there are no sinks or sources other than $v_0$.

**Definition:** An **ordered Bratteli diagram** $(V, E, \ge)$ is a Bratteli diagram equipped with a partial order $\ge$ defined on the sets of edges $E_n$, such that two vertices $e, f\in E_n$ are comparable if and only if $r(e) = r(f)$.

**Definition:** Given a Bratteli diagram $(V, E)$, we define the **infinite path space** $X_E$ by
$$
X_E := \{(x_1, x_2, x_3, ...)\ |\ x_n\in E_n,\ r(x_n) = s(x_{n+1})\}
$$
and we endow $X_E$ with a metric $d$ given as follows:
$$
d(x, y) = 2^{1-n},\qquad \text{where $n$ is the first position where $x_n\neq y_n$}
$$

## Ordered Groups and Inductive Limits

Recall that a **(linearly) ordered group** is a group equipped with a (total) order $\le$ which is translation-invariant: whenever $a\le b$, we also have $ca\le cb$ and $ac\le bc$ for all $c\in G$ (for left/right translation invariance respectively). We will work primarily with left-invariant orders, since a left-invariant order can be obtained from a right-invariant order by considering $g\le_{\text{left}} h$ iff $h^{-1}\le_{\text{right}} g^{-1}$. We remark that in order for a group $G$ to be linearly orderable, $G$ must be torsion-free (since if $g^n = e$ and say $e\le g$, then we obtain a chain $e\le g\le g^2\le \cdots\le g^{n-1}\le e$, forcing $g = e$).

Given a set $C\subseteq G$ containing $e$, and such that whenever $g, h\in C$, $gh\in C$ (a **cone**), $C$ induces a left-invariant order $\le_C$ on $G$, where $g\le_C h$ if and only if $g^{-1}h\in C$. Given a left invariant order $\le$ on $G$, define the **cone of positive elements** $G^+$ to be the set of those $g\in G$ for which $g\ge e$. The set $G^+$ is indeed a cone, and the relation $\le_{G^+}$ is identical to the original relation. In the case of linear orders, we additionally require $C$ satisfy $C\cup C^{-1} = G$ (which effectively gives totality of $\le_C$). Often our ordered groups $G$ will be dented by $(G, G^+)$, where $G^+$ is  the positive cone.

In the category of ordered groups, we require that our morphisms be group homomorphisms which *preserve order*: that is, if $\varphi : (G, G^+)\to (H, H_+)$ is a homomorphism, then $\varphi$ is order preserving if $\varphi(g)\le\varphi(h)$ whenever $g\le h$.

The inductive limit of a system $(G_i, \varphi_{ij})$, where $i\in I$ with $(I, \le)$ some *directed set*, and $\varphi_{ij} : G_i\to G_j$, is defined as the quotient of $\bigsqcup G_i$ under the equivalence relation $\sim$, where $g\in G_i$ and $h\in G_j$ are equivalent if and only if there is some $k\in I$ such that $i, j\le k$, and $\varphi_{ik}(g) = \varphi_{jk}(h)$. The connecting maps are also required to satisfy a sort of semigroup law of composition: $\varphi_{jk}\circ\varphi_{ij} = \varphi_{ik}$ for all $i\le j\le k$, and $\varphi_{ii} = \text{id}_{G_i}$.

When the inductive limit is taken in the category of groups, we need to ensure that the resulting limit object is itself a group. Given elements $(i, g)\in G_i$ and $(j, h)\in G_j$, there exists $k\in I$ for which both $k\ge i$ and $k\ge j$. Then, irrespective of our choice of $k$, we can define the product of $[(i, g)]$ and $[(j, h)]$ as $[\varphi_{ik}(g)\varphi_{jk}(h)]$.The inverse of an element $[(i, g)]$ is simply $[(i, g^{-1})]$. To see that this is well-defined, suppose $k'\in I$ is also greater than both $i, j$. Let $\ell\in I$ be greater than both $k$ and $k'$. Then
$$
\begin{aligned}
\varphi_{k\ell}(\varphi_{ik}(g)\varphi_{jk}(h)) & = (\varphi_{k\ell}\circ\varphi_{ik})(g)(\varphi_{k\ell}\circ\varphi_{jk})(h) = \varphi_{i\ell}(g)\varphi_{j\ell}(g) \\
& = (\varphi_{k'\ell}\circ\varphi_{ik'})(g)(\varphi_{k'\ell}\circ\varphi_{jk'})(h) \\
& = \varphi_{k'\ell}(\varphi_{ik'}(g)\varphi_{jk'}(h))
\end{aligned}
$$
Thus $\varphi_{ik}(g)\varphi_{jk}(h)\sim\varphi_{ik'}(g)\varphi_{jk'}(h)$. The identity element in the limit is represented by $(i, e_i)$ for any $i\in I$.

The limit of the system is denoted $\varinjlim (G_i, \varphi_{ij})$.

When the inductive limit is further taken over *ordered* groups, we require that the connecting maps be order-preserving, and we must ensure there is a notion of an induced order on the limit object. The natural way to do this is to define a cone on the inductive limit. Consider the set $G^+ := \{[(i, g)\ |\ i\in I, g\in G_i^+]\}$ (where $G_i^+$ is the positive cone of $G_i$). Given $[(i, g)], [(j, h)]\in G^+$, it's not hard to check that the product remains in $G^+$: write
$$
[(i, g)][(j, h)] = [(k, \varphi_{ik}(g)\varphi_{jk}(h))]
$$
Since $g\in G_i^+$ and $h\in G_j^+$, and the maps $\varphi_{ik}$, $\varphi_{jk}$ are order-preserving, $\varphi_{ik}(g)\in G_k^+$ and $\varphi_{jk}(g)\in G_k^+$, so their product is also in $G_k^+$, whence in $G^+$.

Let $q_i : G_i\to G$ denote the natural map into the inductive limit (taking $g\mapsto [(i, g)]$). Then $G^+ = \bigcup_i q_i(G_i^+)$. Moreover, notice that the $q_i(G_i^+)$'s are upwards directed, since $q_i(G_i^+) = q_j(\varphi_{ji}(G_i^+)) \subseteq q_j(G_j^+)$.

**Remark:** There's a bit of a subtlety in how we've defined the inductive limit of partially ordered groups: we began by looking at the inductive limit *in the category of groups*, which we then equipped with a suitable order to turn it into a partially ordered group, such that the natural maps $q_i$ are positive homomorphisms. We would *also* have to check that this is an inductive limit *in the category of partially ordered groups* (inductive limits have a definition in an arbitrary category, irrespective of the constituent "elements" of the objects (e.g. elements of a group)). Fortunately the two notions turn out to be identical.

## Simplicial Groups and Dimension Groups

We define a **simplicial group** to be one of the ordered abelian groups $(\mathbb{Z}^n, \mathbb{Z}^n_+)$. A **dimension group** is an inductive limit of simplicial groups. In other words, it is the inductive limit of a system $((\mathbb{Z}^{n_i}, \mathbb{Z}^{n_i}_+), A_i)$, where the $A_i\in\mathbb{Z}_+^{n_{i+1}\times n_i}$ are the connecting maps. It is important to recognize that when in order for the connecting maps $A_i$ to be order-preserving, they must indeed consist of all *positive* integers: if $A\in\mathbb{Z}^{m\times n}$ is order preserving, then since $0\le e_i$, we see that $0 \le Ae_i = \text{Col}_i(A)$, whence $\text{Col}_i(A)\in\mathbb{Z}^m_+$ for all $i$.

**Example 1:** Consider the inductive limit of the system $\mathbb{Z}\overset{2}{\to}\mathbb{Z}\overset{2}{\to}\mathbb{Z}\overset{2}{\to}\cdots$ (the connecting maps being multiplication by $2$). Take $(i, m), (j, n)\in\bigsqcup\mathbb{Z}$ (here $i, j\in\mathbb{N}$ are the indices of *which copy* of $\mathbb{Z}$ the elements are in). Then $(i, m)\sim (j, n)$ if and only if $n = 2^{j-i}m$. The equivalence classes we obtain can be uniquely identified by the elements $(i, m)\in\mathbb{N}\times\mathbb{Z}$, where $2^i\nmid m$. For instance, we have $[(0, m)] = \{(0, m), (1, 2m), ..., (i, 2^im), ...\}$ for all $m\in\mathbb{Z}$, $[(1, 2m-1)] = \{(1, 2m-1), ..., (i, 2^{i-1}(2m-1)), ...\}$ for all $m\in\mathbb{Z}$, and so on. Addition in this group is given by $[(i, m)] + [(j, n)] = [(j, 2^{j-i}m + n)]$ (assuming $i\le j$), but we remark that $(j, 2^{j-i}m + n)$ is not necessarily in "lowest terms" (that is, $j$ is not the minimal index) even if the summands are (for instance, $[(1, 1)] + [(1, 1)] = [(1, 2)] = [(0, 1)]$).

It's not hard to check that there is a bijection between $\mathbb{Q}_{2}$ (the *dyadic rationals*, also denoted $\mathbb{Q}_2^{\infty}$) and this inductive limit, taking $(i, m)$ to $\frac{m}{2^i}$. Moreover, this map is easily seen to be a group homomorphism, whence an isomorphism. Thus the resulting dimension group is simply $\mathbb{Q}_2$.

**Example 2:** The $p$-adic rationals $\mathbb{Q}_p$ for any prime $p$ can be obtained via the inductive limit of $\mathbb{Z}\overset{p}{\to}\mathbb{Z}\overset{p}{\to}\cdots$, given a prime $p$. In fact, given any *supernatural number* $r = \prod_{p\text{ prime}}p^{n_p}$, $n_p\in\{0, 1, ..., \infty\}$, we can obtain $\mathbb{Q}_r$ as an inductive limit. We merely need an enumeration $\{\iota_n\}_{n\in\mathbb{N}}$ of the distinct prime factors of $r$ (counted with multiplicity), in which case we define $\mathbb{Q}_r$ to be the inductive limit of $\mathbb{Z}\overset{\iota_1}{\to}\mathbb{Z}\overset{\iota_2}{\to}\mathbb{Z}\overset{\iota_3}{\to}\cdots$. The subgroups $\mathbb{Q}_r$ actual exhaust all subgroups of $\mathbb{Q}$.

**Example 3:** Another simple example, consider the system $\mathbb{Z}^n\overset{N}{\to}\mathbb{Z}^n\overset{N}{\to}\cdots$, where $N$ is a nilpotent matrix. Given $(i, x)$ in the $i$th copy of $\mathbb{Z}^n$ and $(j, y)$ in the $j$th copy of $\mathbb{Z}^n$, we can always choose $k$ large enough such that $N^{k-i} = N^{k-j} = 0$, in which case $N^{k-i}x = N^{k-j}y$. Thus, there is only a single equivalence class in the limit group, so the group is trivial.

**Example 4:** Now consider the inductive limit $\mathbb{Z}^2\overset{\begin{bmatrix}1 & 1 \\ 0 & 1\end{bmatrix}}{\to}\mathbb{Z}^2\overset{\begin{bmatrix}1 & 1 \\ 0 & 1\end{bmatrix}}{\to}\cdots$. The map $\begin{bmatrix}1 & 1 \\ 0 & 1\end{bmatrix}$ is not only invertible, it's inverse is an integer matrix as well. In other words, the connecting maps are *isomorphisms*. The resulting inductive limit is then rather trivial: every $(i, m)$ is equivalent to $(0, \varphi_{0, i}^{-1}(m))$, and so the disjoint union collapses under the quotient to simply $\mathbb{Z}^2$.

On the other hand, the inductive limit $(\mathbb{Z}^2, \mathbb{Z}^2_+)\overset{\begin{bmatrix}1 & 1 \\ 0 & 1\end{bmatrix}}{\to}(\mathbb{Z}^2, \mathbb{Z}^2_+)\overset{\begin{bmatrix}1 & 1 \\ 0 & 1\end{bmatrix}}{\to}\cdots$ of *ordered groups* has a different structure. This is because the inverse of $\begin{bmatrix}1 & 1 \\ 0 & 1\end{bmatrix}$ is $\begin{bmatrix}1 & -1 \\ 0 & 1\end{bmatrix}$, a map which *isn't* order-preserving. The resulting *partially ordered group* we get in the limit will thus have a non-trivial order structure.

As defined above, the positive cone in the inductive limit will be the union of the cones $\{[(i, x)]\ |\ i\in\mathbb{N}, x\in\mathbb{Z}_+\}$. Since the connecting maps are invertible, we will associate to each element $[(i, x)]$ its representation at level $0$, namely $[(i, x)] = [(0, A^{-i}x)]$ (where $A = \begin{bmatrix}1 & 1 \\ 0 & 1\end{bmatrix}$ is the connecting map).

At level $i = 1$, a positive element $\left[\left(1, \begin{bmatrix} x \\ y\end{bmatrix}\right)\right]$ is equivalent to $\left[\left(0, \begin{bmatrix}x - y\\ y\end{bmatrix}\right)\right]$, and so the positive cone includes all those $\begin{bmatrix} x - y \\ y\end{bmatrix}$ where $x, y\ge 0$.

At level $i$ (arbitrary), a positive element $\left[\left(i, \begin{bmatrix}x \\ y\end{bmatrix}\right)\right]$ is equivalent to $\left[\left(0, \begin{bmatrix}x - iy \\ y\end{bmatrix}\right)\right]$, and so the positive cone includes all these vectors as well.

In total, the positive cone consists of all those vectors $\begin{bmatrix}x - iy \\ y\end{bmatrix}$, where $x, y\ge 0$ and $i\in\mathbb{N}$ is arbitrary. Equivalently, this is the set $\left\{\begin{bmatrix}x \\ y\end{bmatrix}\ |\ y > 0\ \text{or}\ (y = 0\ \text{and}\ x\ge 0)\right\}$.

**Example 5:** Let's look at another example, $\mathbb{Z}^2\overset{A}{\to}\mathbb{Z}^2\overset{A}{\to}\cdots$, where $A = \begin{bmatrix}1 & 1 \\ 1 & 0\end{bmatrix}$. Here, the powers of $A$ are given by
$$
A^n = \begin{bmatrix}F_{n+1} & F_n \\ F_n & F_{n-1}\end{bmatrix},\qquad A^{-n} = (-1)^n\begin{bmatrix}-F_{n-1} & F_n \\ F_n & -F_{n-1}\end{bmatrix},\qquad n> 0
$$
where $F_n$ are the Fibonacci numbers. As in the prior example, since the connecting maps are all invertible, each element of the inductive limit is identifiable by its representative at level $0$: $[(i, x)] = [(0, A^{-i}x)]$. Here, however, the positive cone consists of those vectors $\begin{bmatrix}x \\ y\end{bmatrix}$ for which there is $n\in\mathbb{N}$ such that $A^n\begin{bmatrix}x \\ y\end{bmatrix} \in\mathbb{Z}^2_+$. In other words, those points for which
$$
F_{n+1}x + F_ny \ge 0,\qquad F_nx + F_{n-1}y\ge 0
$$
Or equivalently, $y\ge \max\left(-\frac{F_{n+1}}{F_n}x, -\frac{F_n}{F_{n-1}}x\right)$, which we'll briefly denote $f_n(x)$. This looks a little scary, perhaps, but we must remember that $\lim_n\frac{F_{n+1}}{F_n} = \varphi$, the golden ratio, so in fact the condition that there exists $n$ for which $y\ge f_n(x)$ is equivalent to simply $y \ge -\varphi x$. Hence, the positive cone in our inductive limit is the set
$$
\left\{\begin{bmatrix}x \\ y\end{bmatrix}\in\mathbb{Z}^2\ |\ \varphi x + y \ge 0\right\}
$$
Such a group actually has a trivial presentation: it's positively isomorphic to the group $\mathbb{Z}+\varphi\mathbb{Z}$, equipped with the cone $(\mathbb{Z}+\varphi\mathbb{Z})\cap\mathbb{Z}_+$.

**Example 6:** In fact, it is possible to obtain the group $(\mathbb{Z} + \theta\mathbb{Z}, (\mathbb{Z} + \theta\mathbb{Z})\cap\mathbb{Z}_+)$ for any positive irrational $\theta$ as an inductive limit. Every irrational number $\theta$ can be represented *uniquely* as a **regular continued fraction**:
$$
\theta = a_0 + \dfrac{1}{a_1 + \dfrac{1}{a_2 + \cdots}} =: [a_0; a_1, a_2, ...]
$$
where each of the $a_i$'s is a positive integer. Let $A_n := \begin{bmatrix}a_n & 1 \\ 1 & 0\end{bmatrix}$. Then we can inductively show that
$$
A_n\cdots A_0 = \begin{bmatrix}p_n & q_n \\ p_{n-1} & q_{n-1}\end{bmatrix}\qquad\text{where}\quad \frac{p_n}{q_n} = [a_0; a_1, ..., a_n]
$$
In other words, the rows of $A_n\cdots A_0$ are the successive **convergents** of $\theta$, which are given by the formulas
$$
p_{n+1} = a_{n+1}p_n + p_{n-1},\qquad q_{n+1} = a_{n+1}q_n + q_{n-1}
$$
Consider the system $\mathbb{Z}^2\overset{A_0}{\to}\mathbb{Z}^2\overset{A_1}{\to}\mathbb{Z}^2\overset{A_2}{\to}\cdots$. Each of the maps $A_i$ is invertible with integer-valued inverse, so again the equivalence classes in the limit are identifiable by their representations at level $0$: $[(n, x)] = [(0, (A_n\cdots A_0)^{-1}x)]$. An element $[(0, x)]$ in the limit is positive if and if there is an $n$ for which $A_n\cdots A_0x\in\mathbb{Z}_+$.  But from our formula above,
$$
A_n\cdots A_0\begin{bmatrix} x \\ y\end{bmatrix} = \begin{bmatrix}p_nx + q_n y \\ p_{n-1}x + q_{n-1}y\end{bmatrix}
$$
which is $\ge 0$ if and only if $y\ge \max\left(-\frac{p_n}{q_n}x,\ -\frac{p_{n-1}}{q_{n-1}}x\right)$. As $\lim_n \frac{p_n}{q_n} = \theta$, the resulting limit cone is $\left\{\begin{bmatrix}x \\ y\end{bmatrix}\in\mathbb{Z}^2\ |\ y + \theta x\ge 0\right\}$.

### Effros-Handelman-Shen

**Definition:** A partially ordered group $(G, G^+)$ is said to be **unperforated** if $g^n\in G^+$ for some positive $n\in\mathbb{Z}$ implies $g\in G^+$. In other words, we cannot have non-positive elements with positive powers (or *multiples* in the abelian setting).

**Definition:** A partially ordered group satisfies the **Riesz interpolation property** if, whenever $x_1, x_2, y_1, y_2$ are such that $x_i\le y_j$ for all $i, j$, there exists a $z$ with $x_i\le z\le y_j$.

The Riesz interpolation property might look a little strange at first - it doesn't seem implausible that every partially ordered group satisfies this requirement. Perhaps this confusion comes from the fact that a rather large class of groups "automatically" satisfies this property: the **lattice groups**, which are the groups in which every two elements $a, b$ have a **meet** $a\land b$ and a **join** $a\lor b$, acting as the greatest lower bound and least upper bound respectively. In such groups, we can clearly simply take $z = x_1\lor x_2$ or $y_1\land y_2$.

The Riesz interpolation property is a relaxation of this lattice requirement: instead of requiring every two elements have a max and a min, we merely require every *four* elements have "something in-between them". Often for simplicity we will write "$G$ has **interpolation**".

**Theorem:** Let $(G, G^+)$ be a partially ordered <u>abelian</u> group. Then TFAE:

1. $(G, G^+)$ has interpolation.
2. Given $x, y_1, y_2\in G^+$ such that $x\le y_1 + y_2$, there exist $x_1, x_2\in G^+$ such that $x = x_1 + x_2$ and $x_i\le y_i$ for each $i$.
3. Given $x_1, x_2, y_1, y_2\in G^+$ such that $x_1 + x_2 = y_1 + y_2$, there exist $z_{11}, z_{12}, z_{21}, z_{22}\in G^+$ such that the row sum of $[z_{ij}]_{i,j=1}^2$ is $\begin{bmatrix}x_1 \\ x_2\end{bmatrix}$ and the column sum is $\begin{bmatrix}y_1 & y_2\end{bmatrix}$.








$$
\begin{matrix}
\theta(a_k^1a_\ell^2*) & = & b_{r_1}^1a_{\rho_1(k,\ell)}^2* & \qquad & k\in\{1, ..., r_1\},\ \ell\in\{1,...,d_2\} \\
\theta(a_k^1a_\ell^2*) & = & b_k^1a_{r_2-d_2+\ell}^2* & & k\in\{1,...,r_1\},\ \ell\in\{d_2+1,...,q_2-r_2\} \\
\theta(b_k^1b_\ell^2*) & = & a_{r_1}^1b_{\rho_1(k,\ell)}^2* & & k\in\{1,...,r_1\}, \ell\in\{1,...,d_2\}
\end{matrix}
$$
At this stage, we've defined $\theta$ for all $a_k^1a_\ell^2*$, all $b_k^1b_\ell^2*$, and some mixed paths. What we're *missing* is:
$$
\begin{matrix}
b_k^1a_\ell^2*,& \ k\in\{1,...,r_1-1\},& \ \ell\in\{1,...,r_2\} \\
a_k^1b_\ell^2*,& \ k\in\{1,...,r_1-1\},& \ell\in\{1,...,r_2\}
\end{matrix}
$$
We continue as follows. For all $i\in\{1,...,r_1-1\}$, define
$$
\begin{matrix}
\theta(b_i^1a_k^2a_\ell^3*) & = & a_i^1b_{r_2}^2a_{\rho_2(k,\ell)}^3* & \qquad & k\in\{1,...r_2\},\ \ell\in\{1,...,d_3\} \\
\theta(b_i^1a_k^2a_\ell^3*) & = & a_i^1b_k^2a_{r_3-d_3+\ell}^3* & & k\in\{1,...,r_2\},\ \ell\in\{d_3+1,...,q_3-r_3\} \\
\theta(a_i^1b_k^2b_\ell^3*) & = & b_i^1a_{r_2}^2b_{\rho_2(k,\ell)}^3* & & k\in\{1,...,r_2\},\ \ell\in\{1,...,d_3\}
\end{matrix}
$$
At this stage, we've defined $\theta$ for *all* $b_i^1a_k^2a_\ell^3*$, *all* $a_i^1b_k^2b_\ell^3*$ (if it seems like some cases are missing in the second-stage definition, go back and check the first stage), and, again, some mixed paths. What we're missing are some paths of the form $a_i^1b_k^2a_\ell^3*$ and $b_i^1a_k^2b_\ell^3*$. In particular:
$$
\begin{matrix}
a_i^1b_k^2a_\ell^3* & i\in\{1,...,r_1-1\},\ & k\in\{1,...,r_2-1\},\ & \ell\in\{1,...,r_3\} \\
b_i^1a_k^2b_\ell^3*
\end{matrix}
$$
For all $i_1\in\{1, ..., r_1-1\}$, $i_2\in\{1,...,r_2-1\}$, define
$$
\begin{matrix}
\theta(a_{i_1}^1b_{i_2}^2a_k^3a_\ell^4*) & = & b_{i_1}^1a_{i_2}^2b_{r_3}^3a_{\rho_3(k,\ell)}^4* & \qquad & k\in\{1,...,r_3\},\ \ell\in\{1,...,d_4\} \\
\theta(a_{i_1}^1b_{i_2}^2a_k^3a_\ell^4*) & = & b_{i_1}^1a_{i_2}^2b_k^3a_{r_4-d_4+\ell}^4* & & k\in\{1,...,r_3\},\ \ell\in\{d_4+1,...,q_4-r_4\}\\
\theta(b_{i_1}^1a_{i_2}^2b_k^3b_\ell^4*) & = & a_{i_1}^1b_{i_2}^2a_{r_3}^3b_{\rho_3(k,\ell)}^4* & & k\in\{1,...,r_3\},\ \ell\in\{1,...,d_4\}
\end{matrix}
$$
Then what's missing is
$$
a_{i_1}^1b_{i_2}^2a_k^3b_\ell^4*,\ b_{i_1}^1a_{i_2}^2b_k^3a_\ell^4*,\ i_1\in\{1,..., r_1-1\},\ i_2\in\{1,...,r_2-1\},\ k\in\{1,...,r_3-1\},\ \ell\in\{1,...,r_4\}
$$
I think we're starting to get the idea.



We can describe what $\theta$ does as follows:

1. Given a word $w$, find the longest prefix $p$ taking one of the following forms:

   * $a_{i_1}b_{i_2}a_{i_3}\cdots *$
   * $b_{i_1}a_{i_2}b_{i_3}\cdots *$

   where $i_\nu\in \{1, ..., r_\nu - 1\}$ for al $\nu$. Write $w = pv$.

2. If $v$ is empty, $\theta(w)$ interchanges $a$'s and $b$'s.

3. 





Here's, broadly speaking, what $\theta$ does (this is just a heuristic):

1. It looks at a sequence $x$ and first assesses what the longest prefix of $x$ is which is of the form $abab...$ or $baba...$, where the $a$ and $b$ indices are *not* "final". Let $w$ be this prefix, and $x = wy$.
2. $\theta$ flips all $a$'s in $w$ to $b$'s, and vice versa, while maintaining the indices.
3. Next, $\theta$ looks to the first two characters of $y$.
4. It takes $a_ka_{\text{low }\ell}$ to $b_{\text{final}}a_{\text{low mixture of $k$, $\ell$}}$. Here, there are *not enough* $k$'s and $\ell$'s to obtain all $a$ indices after the $b_{\text{final}}$.
5. It takes $a_ka_{\text{high }\ell}$ to $b_ka_{\text{high }\ell}$ (without changing $\ell$).
6. Finally, it takes $b_kb_\ell$ to $a_{\text{``final"}}b_{\text{mixture of $k,\ \ell$}}$. Here, there *are* enough $k$'s and $\ell$'s to obtain every $b$ index after $a_{\text{final}}$.

This definition leaves out $y = b_{k\text{ (not final)}}a_{\text{low }\ell}*$ and $y = a_{k\text{ (not final)}}b_\ell*$, from which we continue to inductively define $\theta$.






$$
(R_\ell)_{i_1i_0}(D_{\ell+1})_{i_2i_1} = (R_{\ell+1})_{i_2i_1} \qquad
\sum_{k=1}^{m_{\ell+1}} (R_\ell)_{ki} \equiv 0\ (\text{mod }r_\ell) \qquad
\sum_{k=1}^{m_{\ell+1}} (D_\ell)_{ki} \equiv d_\ell\ (\text{mod }r_\ell)
$$


## A Worked Example

Let $D := \Z^2\overset{\begin{bmatrix}1 & 1 \\ 1 & 0\end{bmatrix}}{\to}\cdots$ and $r = 2^\infty$, giving torsion component $\Q_{2^\infty}/\Z$. What Bratteli diagram gives $D\oplus\Q_{2^\infty}/\Z$? Let $r_n = 2^n$, and $d_n = 2$ for all $n\in\N$.

At each level aside from the first, there are four vertices: $v_1^\ell, v_2^\ell$, $w_1^\ell$ and $w_2^\ell$. There are $(A_\ell)_{ij} - r^\ell_i$ edges from $v_j^\ell$ to $v_i^{\ell+1}$, $r_i^\ell$ edges from $v_j^\ell$ to $w_i^{\ell+1}$, $(A_\ell)_{ij} - (D_\ell)_{ij}$ from $w_j^\ell$ to $v_i^{\ell+1}$, and $(D_\ell)_{ij}$ from $w_j^\ell$ to $w_i^{\ell+1}$.

Let's start by choosing $r_1^1, r_2^1$, such that $r_1^1 + r_2^1 \equiv 0\ (\text{mod}\ 2)$. Let's start by trying $r_1^1 = r_2^1 = 1$.

The second level $r$'s, $r_1^2, r_2^2$, are related to the first level $r$'s via the matrix $D$: $r_j^\ell(D_{\ell+1})_{kj} = r_k^{\ell+1}$.

We'll need to choose $D_2$ such that $r_1^2 + r_2^2\equiv 0\ (\text{mod}\ 4)$. In particular, this means we can't simply choose $(D_2)_{ij} = 1$, since this would give $r_1^2 + r_2^2 \equiv 2\ (\text{mod}\ 4)$. We could try, for instance, $D_2 = \begin{bmatrix}2 & 2 \\ 2 & 2\end{bmatrix}$.

There's an additional constraint on $D_\ell$, namely $\sum_k (D_{\ell+1})_{ki}\equiv d_\ell\ (\text{mod}\ r_\ell)$. This constraint is indeed satisfied by our choice of $D_2$.

This gives $r_1^2 = r_2^2 = 2$. Now we need to choose $D_3$ such that $r_1^3 + r_2^3 \equiv 0\ (\text{mod } 8)$, and
$$
(D_3)_{11} + (D_3)_{21}\equiv (D_3)_{12} + (D_3)_{22}\equiv 2\ (\text{mod}\ 4)
$$
Unfortunately here we run into a roadblock: since $r_1^3 = r_1^2(D_3)_{11} = 2(D_3)_{11}$, and similarly $r_2^3 = 2(D_3)_{21}$, the first condition says $(D_3)_{11} + (D_3)_{21} \equiv 0\ (\bmod 4)$, but the second condition requires that this be $\equiv 2\ (\bmod 4)$, which is impossible.

**Question:** If $r_i^\ell = c_\ell$ for all $i$, will this *always* cause a problem at level $\ell + 2$?

### Trying Again - Choosing a Different $D_2$

Let's try $D_2 = \begin{bmatrix}2 & 2 \\ 6 & 6\end{bmatrix}$. Then $r_1^2 = (D_2)_{11}r_1^1 = (D_2)_{12}r_2^1 = 2$, and $r_2^2 = (D_2)_{21}r_1^1 = (D_2)_{22}r_2^2 = 6$. As desired, $r_1^2 + r_2^2\equiv 0\ (\bmod 4)$.

Now we need $D_3$ such that
$$
(D_3)_{11}r_1^2 + (D_3)_{21}r_2^2\equiv 0\ (\bmod 8) \\
(D_3)_{11} + (D_3)_{21}\equiv (D_3)_{12}+(D_3)_{22}\equiv 2\ (\bmod 4)
$$

### Trying Again - Choosing Different $r_i^1$'s

One thing we can try differently is $r_1^1 = 1$, $r_2^1 = 3$.

Note that if we have even a single $r_i^\ell = 0$ for some $i, \ell$, then every $r_j^{\ell+1}=0$ for all $j$ since $r_j^{\ell+1} = (D_{\ell+1})_{ji}r_i^\ell = 0$. While it is possible that this makes sense according to the constraints on the $r$'s and $D$'s, having all $r$'s zero is problematic for our Bratelli diagram since it implies none of the $v$ edges connect to any of the $w$ edges in the following layer, which is necessary in order for our construction to work. So we need to choose $r_1^1$ and $r_2^1$ to be (likely different) odd numbers.

Now we have to choose $D_2$. Notice that $(D_2)_{ki}/(D_2)_{kj} = r_j^1/r_i^1$ is *constant* in $k$. In fact, if we start by choosing $(D_2)_{k1}$, then $(D_2)_{k2} = \frac{r_1^1}{r_2^1}(D_2)_{k1} = (D_2)_{k1}/3$. In other words, the first column of $D_2$ consists of multiples of $3$. We could try, for example, $D_2 = \begin{bmatrix} 3 & 1 \\ 3 & 1\end{bmatrix}$. Then
$$
(D_2)_{11} + (D_2)_{21}\equiv 6\equiv 2\ (\bmod 2) \\
(D_2)_{12} + (D_2)_{22}\equiv 2\ (\bmod 2)
$$
so this choice of $D_2$ satisfies the desired constraints. 

### General Procedure

Given $r_1^{\ell-1}, r_2^{\ell-1}$, satisfying $r_1^{\ell-1} + r_2^{\ell-1}\equiv 0\ (\bmod 2^{\ell-1})$, we need to find $D_{\ell}$ such that
$$
(D_{\ell})_{11}r_1^{\ell-1} = (D_{\ell})_{12}r_2^{\ell-1},\qquad (D_{\ell})_{21}r_1^{\ell-1} = (D_{\ell})_{22}r_2^{\ell-1} \\
(D_{\ell})_{11}r_1^{\ell-1} + (D_{\ell})_{22}r_2^{\ell-1} \equiv 0\ (\bmod 2^\ell) \\
(D_{\ell})_{11} + (D_{\ell})_{21}\equiv 2\ (\bmod 2^\ell) \\
(D_{\ell})_{12} + (D_{\ell})_{22} \equiv 2\ (\bmod 2^\ell)
$$
In which case $r_1^\ell = (D_\ell)_{11}r_1^{\ell-1}$ and $r_2^\ell = (D_\ell)_{22}r_2^{\ell-1}$, and we repeat the procedure inductively. The third condition above is the requirement that $r_1^\ell + r_2^\ell \equiv 0\ (\bmod 2^\ell)$, but written so as to look "diagonal".

Let us, for the time being, denote $D_\ell = \begin{bmatrix}A & B \\ C & D\end{bmatrix}$, and $x_i = r_i^{\ell-1}$, to get rid of the sub/superscripts. The first two conditions tell us that
$$
Ax_1 = Bx_2,\qquad Cx_1 = Dx_2
$$
Suppose we start by choosing $A$ and $C$. Then $B = Ax_1/x_2$, which tells us that $Ax_1\equiv 0\ (\bmod x_2)$, and similarly $D = Cx_1/x_2$, with $Cx_1\equiv 0\ (\bmod x_2)$. Substituting these formulas for $B$ and $D$ give
$$
Ax_1 + Cx_1\equiv 0\pmod{2^\ell} \\
A+C\equiv 2\pmod{2^\ell} \\
Ax_1/x_2 + Cx_1/x_2\equiv 2\pmod{2^\ell}
$$
Of course, the second equation can be substituted into the first and the third to yield:
$$
2x_1\equiv 0\pmod{2^\ell},\qquad A+C\equiv 2\pmod{2^\ell},\qquad 2x_1/x_2\equiv 2\pmod{2^\ell}
$$
The first equation is equivalent to $x_1\equiv 0\pmod{2^{\ell-1}}$. Of course, we had initially required that $x_1 + x_2\equiv 0\pmod{2^{\ell-1}}$, and so we must also have $x_2\equiv 0\pmod{2^{\ell-1}}$. 

Let us write $x_i = 2^{\ell-1+m_i}y_i$, for $i = 1, 2$, with $2\nmid y_i$. The third equation then reads
$$
2^{m_1-m_2+1}y_1/y_2\equiv 2\pmod{2^\ell}
$$
 but since $2\nmid y_2$, we must have $y_2\mid y_1$, so $y_1 = ky_2$, from which the equation reads
$$
2^{n+1}k\equiv2\pmod{2^\ell}
$$
where $n = m_1 - m_2$, or equivalently
$$
2^nk\equiv 1\pmod{2^{\ell-1}}
$$
which, assuming $\ell > 1$, is only solvable for $n = 0$. So $x_1 = 2^{\ell-1+m}ak$, $x_2 = 2^{\ell-1+m}a$, for some $m\ge0$ and $k\equiv 1\pmod{2^{\ell-1}}$, and $2\nmid a$.



