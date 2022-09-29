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

## Dimension Groups

### Ordered Groups and Inductive Limits

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



