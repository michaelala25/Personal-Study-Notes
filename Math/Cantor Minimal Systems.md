# Cantor Minimal Systems

These are my collected notes while studying the book "Cantor Minimal Systems" by Ian F. Putnam. These notes only *loosely* follow the flow of the book, skipping over certain chapters and details that are extraneous to my required understanding.

## Groupoids, Bratteli Diagrams, and $\mathbb{Z}$-Actions on Cantor Sets

There's some sort of correspondence going on between the three items in this subsection's title. Let's first define them.

## 1 - Groupoids

Recall that a **small category** is one for which the object and homsets are all *sets* rather than *proper classes*.

**Definition:** A **groupoid** is a small category $G$ all of whose morphisms are invertible. Alternatively, one can view a groupoid $G$ as merely a set with some additional structural and algebraic properties. For one, there is a distinguished set of **units**, $G^{(0)}\subset G$ (often the groupoid is denoted by $G\rightrightarrows G^{(0)}$). Additionally we impose the existence of two maps $s, r : G\to G^{(0)}$ called the **source** and **range** maps respectively. These maps allow us to define the set of **composable** elements $G^{(2)}:=\{(a, b)\in G\times G\ :\ s(a)=r(b)\}$. The final bit of structure we need is a **composition map** from $G^{(2)}\to G$, taking $(a, b)$ to the element of $G$ denoted $ab$. We additionally impose the following restrictions on our structure maps:

* $r(x) = s(x) = x$ for all $x\in G^{(0)}$.
* $as(a) = a = r(a)a$ for all $a\in G$.
* $r(ab) = r(a)$ and $s(ab) = s(b)$ for all $(a, b)\in G^{(2)}$.
* If $(a, b), (b, c)\in G$, then $(a, bc), (ab, c)\in G^{(2)}$ (necessarily due to the property above), and $a(bc) = (ab)c$.
* Every $a\in G$ has an inverse $a^{-1}\in G$ such that $r(a) = s(a^{-1})$ and $s(a) = r(a^{-1})$ (whence $(a, a^{-1})\in G^{(2)}$), and $aa^{-1} = r(a)$, $a^{-1}a = s(a)$.

Comparing with the (far simpler) category theoretic definition, the units $G^{(0)}$ are simply the **identity maps** on the objects of the underlying category of $G$, and the elements of $G$ are the **morphisms** of this category. The source, range, and composition maps take on their expected analogous purposes.

**Why are they an extension of groups?** Given a group $G$, we can define a groupoid $\mathcal{G}$ by letting the unit set $\mathcal{G}^{(0)}$ consist of a single unit, $\{e\}$ ($e$ the identity of $G$), and letting the remaining elements of $\mathcal{G}$ be the remaining elements of $G$ with $r(g)=s(g)=e$ for all $g\in G$. In other words, a group is a groupoid with a single unit.

**Fact:** In a groupoid, inverses are unique: if $a, b$ are composable and $ab = r(a)$, $ba = s(a)$, then $b = a^{-1}$.

**Proof:** $ab = r(a)$ implies $a^{-1}ab = a^{-1}r(a) = a^{-1}s(a^{-1}) = a^{-1}$, but $a^{-1}a = s(a)$ and $s(a) = r(b)$, so $a^{-1}ab = s(a)b = r(b)b = b$, thus $b = a^{-1}$. $\square$

As far as the algebraic theory of groups goes, the similarities between groups and groupoids are akin to the similarities between a car and a carpet: they stop at the name.

It is important to note that $G^{(0)}$ is **not** uniquely defined as the set $\{x\in G\ :\ s(x)=r(x)\}$, nor even by the stricter condition $\{x\in G\ :\ s(x)=r(x)=x^{-1}\}$. The former set consists of **automorphisms**, and the latter **involutions**. For this reason, we introduce the following definition.

**Definition:** A groupoid $G\rightrightarrows G^{(0)}$ is said to be **principal** if the only **automorphisms** are $G^{(0)}$.

**Definition:** A **subgroupoid** $H\rightrightarrows H^{(0)}$ of a groupoid $G\rightrightarrows G^{(0)}$ is a subcategory which is itself a groupoid (simply put, the objects of $H$ are a subset of the objects of $G$, and the morphisms of $H$ a subset of the morphisms of $G$). A **wide** subcategory (and thus a wide subgroupoid) is one which contains all the objects of it's parent category. A **full** subcategory $H$ of a category $G$ (and thus a full subgroupoid) is one such that for any two objects in $H$, the morphisms between these objects in $H$ consist of *precisely* the morphisms between these objects in $G$.

There is a certain sense in which groupoids are just "dissipated groups".

Given a groupoid $G\rightrightarrows G^{(0)}$ and $x\in G^{(0)}$, we let $G(x)$ denote the **vertex group** of $G$, which consists of those elements of $G$ whose source and range equals $x$. Clearly each $G(x)$ is a group. If $x, y\in G^{(0)}$ and there is $f\in G$ such that $s(f) = x$ and $r(f)=y$, then $G(x)\cong G(y)$ via the isomorphism taking $g\mapsto fgf^{-1}$. Thus, if a groupoid is **connected** (in the sense of a *category*), then all its vertex groups are isomorphic, so $G$ just looks like a graph whose nodes are the group $G(x)$ (for any unit $x$), with some additional algebraic structure conjoining the vertices. 

**Definition:** Given two functors $F, G : C\to D$ between categories, a **natural transformation** $\eta : F\to G$ is a family of morphisms satisfying the following properties:

1. For each object $X\in\text{ob}(C)$, $\eta_X$ is a morphism from $F(X)\to G(X)$, called the **component** of $\eta$ at $X$.
2. For every $f : X\to Y$ in $\text{hom}(C)$, we have $\eta_Y\circ F(f) = G(f)\circ \eta_X$.

**Definition:** An **equivalence of categories** $C, D$ consists of a functor $F : C\to D$, a functor $G : D\to C$, and two natural isomorphisms $\epsilon : FG\to \bf{I}_D$ and $\eta : \bf{I}_C\to GF$, where $\bf{I}$ denotes the *identity functor*.

**Proposition:** A connected groupoid is equivalent (as a category) to a group.

**Proof:** 

**Definition:** An **AF-groupoid** $G$ is one which is the inductive limit of

**Definition:** A **topological groupoid** $G$ is a groupoid equipped with a topology such that the *source*, *range*, and *inverse* maps are **continuous**, as well as the *composition map* is continuous with respect to the inherited product topology on $G^{(2)}$.

*Aside:* I'm still struggling to envision what an "open set" really looks like in a groupoid. We can impose all sorts of other conditions on the topology, such that it be Hausdorff, locally compact, second countable, have totally disconnected units, etc.

**Definition:** A topological groupoid $G$ is **étale** (or **r-discrete**) if the range and source maps are **local homeomorphisms**. We recall that a local homeomorphism $f : X\to Y$ between topological spaces is a map such that, around each $p\in X$ there is an open neighbourhood $U_p\ni p$ such that $f(U_p)$ is open, and $f|_{U_p}$ is a homeomorphism.

*Remark:* One needs only check that the range map is a local homeomorphism to conclude the same for the source map. This is because $\gamma\mapsto\gamma^{-1}$ is always a homeomorphism (it is its own inverse after all), and $r(\gamma) = s(\gamma^{-1})$.

**Important Remark:** In most cases, our topological groupoids will be assumed to be <u>locally compact</u> with <u>$G^{(0)}$ Hausdorff</u>.

**Question:** Let $G\rightrightarrows G^{(0)}$ be a topological group. Are any of the following true?

1. If $U\subseteq G$ is open and $A\subseteq G$, the set $AU := \{au\ |\ a\in A, u\in U,\ (a, u)\in G^{(2)}\}$ is open.
2. In a topological group, around any point $x$ in an open set $U$ one can find an open neighbourhood $V$ of the identity such that $VxV\subseteq U$. Is a similar idea feasible in a topological groupoid?
3. If $H\rightrightarrows H^{(0)}$ is a subgroupoid, then so is $\overline{H}\rightrightarrows \overline{H^{(0)}}$.
4. If $H\rightrightarrows H^{(0)}$ is an *open* subgroupoid then it is automatically closed.
5. The graph-connected components of $G$ are *topologically*-connected, whence clopen.

**Lemma:** Let $G\rightrightarrows G^{(0)}$ be an étale groupoid. Then $G^{(0)}$ is open.

**Proof:** For each $g\in G$, let $U_g$ be an open set on which $r|_{U_g}$ is a homeomorphism. Then $G^{(0)} = r(G) = r\left(\bigcup_{g\in G}U_g\right) = \bigcup_{g\in G}r(U_g)$, so $G^{(0)}$ is open. $\square$

**Lemma:** Let $G\rightrightarrows G^{(0)}$ be a topological groupoid. Then $G^{(0)}$ is closed if and only if $G$ is Hausdorff.

**Proof:** Assume $G$ is Hausdorff. Let $x_i\in G^{(0)}$ be a net converging to $g\in G$. By continuity of the range maps, we have $x_i = r(x_i)\to r(g)$, so $x_i$ converges to $r(g)$, and similarly to $s(g)$. By Hausdorffness, the limit point is unique, so $g = r(g) = s(g)$, whence $g\in G^{(0)}$. 

Now assume $G^{(0)}$ is closed. $\square$

These two lemmas tell us that the unit group in a Hausdorff étale groupoid is *clopen*, and so forms a separation for the groupoid. In other words, the connected component of any unit is contained entirely in the unit set, and the connected component of any non-unit is entirely disjoint from the unit set.

**Definition:** A set $U\subseteq G$ is called a <u>bisection</u> if there exists an open set $V\supseteq U$ such that $r|_V$ and $s|_V$ are both homeomorphisms.

**Lemma:** If $G$ is <u>second-countable</u>, <u>Hausdorff</u>, <u>étale</u>, then $G$ has a countable base of <u>open bisections</u>.

**Proof:** Let $\{U_i\}_{i\in\mathbb{N}}$ be a countable base for the topology on $G$, and $\{V_x\}_{x\in G}$ a cover of $G$ by open sets in such that $x\in V_x$ and $r|_{V_x}, s|_{V_x}$ are simultaneously homeomorphisms. For each $i$, choose $x_i\in U_i$, and consider the family of open bisections $\{U_i\cap V_{x_j}\}_{i, j\in \mathbb{N}}$. Then for all $U\subseteq G$ open and $x\in U$, choose $j$ such that $x\in V_{x_j}$ and $i$ such that $x\in U_i\subseteq U$. Then $x\in U_i\cap V_{x_j}\subseteq U$. $\square$

**Definition:** Given $x\in G^{(0)}$, we define $G_x := \{\gamma\in G\ |\ s(\gamma) = x\}$ and $G^x := \{\gamma\in G\ |\ r(\gamma) = x\}$. 

**Theorem:** If $G$ is <u>étale</u> then $G_x$ and $G^x$ are both <u>discrete</u> for all $x$.

**Proof:** For each $\gamma\in G_x$, choose an open bisection $U\ni \gamma$. Then $U\cap G_x = \{\gamma\}$ (indeed, if there were another $\gamma'\in U\cap G_x$ then we would have $s(\gamma) = s(\gamma') = x$, which is impossible since s is injective on $U\cap G_x$). Thus these sets are open in $G_x$, so $G_x$ is discrete. $\square$

This surprisingly simple fact is a necessary step in the construction of <u>convolution algebras</u> of groupoids.

**Theorem:** For any topological groupoid $G$ for which $r$ is an open map, multiplication is <u>also</u> an open map.

**Proof:** Observe that if $r$ is an open map then so is $s$ since $s(\gamma) = r(\gamma^{-1})$ and $\gamma\mapsto\gamma^{-1}$ is a homeomorphism.

**Corollary:** If $G$ is étale and $U, V\subseteq G$ are open, then $UV$ is open.

**Proof:** If $G$ is étale, then $r$ is an open map: write $U = \bigcup_{x\in U}U_x$ where each $x\in U_x\subseteq U$ is an open bisection, so that $r(U) = \bigcup_{x\in U}r(U_x)$. $\square$

**Example (Relation):** Let $R$ be an equivalence relation on a set $X$ (which we realize as a subset of $X\times X$, where a pair $(x, y)\in R$ if and only if $xRy$). Then $R$ can be realized as a groupoid, with the units given by the pairs $(x, x)$ and the composable pairs given by $((x, y), (y, z))$, for $x, y, z\in X$. The composition of such a pair is then $(x, z)$, which is in $R$ since $R$ is an *equivalence* relation. The inverse of $(x, y)$ is easily seen to be $(y, x)$. Groupoids arising in this way will show up frequently in our discussion of topological dynamics.

**Example (Bundle of Groups):** Let $X$ be a set, and $G_x$ a group for each $x\in X$. Then $\bigcup_{x\in X}\{x\}\times G_x$ ($= \bigsqcup_x G_x$) is a groupoid, with units given by $(x, e_x)$ (where $e_x\in G_x$ is the identity element) and composition between $(x, g)$ and $(y, h)$ available if and only if $x = y$, in which case $(x, g)(x, h) = (x, gh)$. Obviously much finer structure can be imposed on this construction, allowing us to produce for instance <u>fibre bundles of groups</u> (a.k.a <u>group bundles</u>), <u>smooth group bundles</u>, <u>Lie group bundles</u>, etc.

**Example (Isotropy Subgroupoid):** 

**Example (Transformation Groupoid):** Let $G$ be a group acting on a set $X$. We denote by $X\rtimes G$ the groupoid whose underlying set is $X\times G$. Given $(x, g)\in X\times G$, the source of $(x, g)$ is $x$ and the range is $g\cdot x$, so $(x, g), (y, h)\in X\rtimes G$ are composable if $y = g\cdot x$, in which case $(y, h)(x, g) := (x, hg)$. The units of $X\rtimes G$ are the elements $(x, e)$, where $e$ is the unit of $G$. 

**Example (Deaconu-Renault Groupoids):** 

#### Groupoid C*-Algebras

One route through which groupoids are studied is indirectly via their *convolution algebras*, whose completions (with respect to an appropriately chosen representation) are C*-algebras.

#### Topological Groupoid Cohomology



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

### Bratteli Diagrams

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
