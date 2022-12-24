# Groupoids

$$
\newcommand{\mc}[1]{\mathcal{#1}}
\newcommand{\supp}{\operatorname{supp}}
\newcommand{\llbracket}{[\![}
\newcommand{\rrbracket}{]\!]}
$$

## 1 - Topological Groupoids

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

**Fact:** Let $G$ be a (locally compact, Hausdorff) topological groupoid. Then each of the vertex groups $G(x)$ are also (locally compact, Hausdorff) topological groups. We get local compactness because $G(x)$ is always <u>closed</u>.

**Proof:** It is not hard to see that the topology on $G(x)$ inherited from $G$ keeps the inverse/multiplication maps continuous, so $G(x)$ is topological. Once we establish that $G(x)$ is closed, it will automatically be locally compact. Let $\gamma_n\in G(x)$ be a net converging to some $\gamma\in G$. Then by continuity we have $x = \lim_n s(\gamma_n) = s(\gamma)$ and $x = \lim_n r(\gamma_n) = r(\gamma)$, whence $\gamma\in G(x)$, so $G(x)$ is closed. $\square$

**Question:** Let $G\rightrightarrows G^{(0)}$ be a topological group. Are any of the following true?

1. If $U\subseteq G$ is open and $A\subseteq G$, the set $AU := \{au\ |\ a\in A, u\in U,\ (a, u)\in G^{(2)}\}$ is open.
2. In a topological group, around any point $x$ in an open set $U$ one can find an open neighbourhood $V$ of the identity such that $VxV\subseteq U$. Is a similar idea feasible in a topological groupoid?
3. If $H\rightrightarrows H^{(0)}$ is a subgroupoid, then so is $\overline{H}\rightrightarrows \overline{H^{(0)}}$.
4. If $H\rightrightarrows H^{(0)}$ is an *open* subgroupoid then it is automatically closed.
   1. The graph-connected components of $G$ are *topologically*-connected, whence clopen.

**Lemma:** Let $G\rightrightarrows G^{(0)}$ be an étale groupoid. Then $G^{(0)}$ is open.

**Proof:** For each $g\in G$, let $U_g$ be an open set on which $r|_{U_g}$ is a homeomorphism. Then $G^{(0)} = r(G) = r\left(\bigcup_{g\in G}U_g\right) = \bigcup_{g\in G}r(U_g)$, so $G^{(0)}$ is open. $\square$

**Lemma:** Let $G\rightrightarrows G^{(0)}$ be a topological groupoid. Then $G^{(0)}$ is closed if and only if $G$ is Hausdorff.

**Proof:** Assume $G$ is Hausdorff. Let $x_i\in G^{(0)}$ be a net converging to $g\in G$. By continuity of the range maps, we have $x_i = r(x_i)\to r(g)$, so $x_i$ converges to $r(g)$, and similarly to $s(g)$. By Hausdorffness, the limit point is unique, so $g = r(g) = s(g)$, whence $g\in G^{(0)}$. 

Now assume $G^{(0)}$ is closed.  $\square$

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

**Example (Relation Generated by a Groupoid):** Given a groupoid $G$, there is a natural equivalence relation defined on $G^{(0)}$, which we denote by $R(G^{(0)})$. We say two units $x, y\in G^{(0)}$ are equivalent iff there exists some $\gamma\in G$ such that $s(\gamma) = x$ and $r(\gamma) = y$. This new relation $R(G^{(0)})$ is itself a groupoid, and we have a *groupoid homomorphism* $\varphi : G\to R(G^{(0)})$ given by taking $\gamma\mapsto (s(\gamma), r(\gamma))$. It is not hard to show that a groupoid $G$ is principal *if and only if* this map is injective, in which case $G$ is isomorphic to a subrelation of $R(G^{(0)})$. In other words, a groupoid $G$ is principal if and only if it is isomorphic to an equivalence relation.

**Example (Matrix Groupoid):** Let $R_N$ denote the set of pairs $(i, j)$ with $1\le i, j\le N$. Define composability by $(i, j)(j, k) = (i, k)$, with units $(i, i)$. Then $R_N$ is a groupoid, which can be thought of as "the groupoid of dimensions of matrices which are compatible for multiplication".

**Example (Bundle of Groups):** Let $X$ be a set, and $G_x$ a group for each $x\in X$. Then $\bigcup_{x\in X}\{x\}\times G_x$ ($= \bigsqcup_x G_x$) is a groupoid, with units given by $(x, e_x)$ (where $e_x\in G_x$ is the identity element) and composition between $(x, g)$ and $(y, h)$ available if and only if $x = y$, in which case $(x, g)(x, h) = (x, gh)$. Obviously much finer structure can be imposed on this construction, allowing us to produce for instance <u>fibre bundles of groups</u> (a.k.a <u>group bundles</u>), <u>smooth group bundles</u>, <u>Lie group bundles</u>, etc.

**Example (Isotropy Subgroupoid):** Given a groupoid $G$, we define $\text{Iso}(G)$ to be subgroupoid of $G$ consisting of the bundle of groups over $G^{(0)}$, for which the fibres are the vertex groups $G(x)$. In other words, $\text{Iso}(G) = \bigsqcup_{x\in G^{(0)}}G(x)$. We defined a groupoid $G$ to be *principal* precisely if $\text{Iso}(G) = G^{(0)}$.

**Example (Transformation Groupoid):** Let $G$ be a group acting on a set $X$. We denote by $X\rtimes G$ the groupoid whose underlying set is $X\times G$. Given $(x, g)\in X\times G$, the source of $(x, g)$ is $x$ and the range is $g\cdot x$, so $(x, g), (y, h)\in X\rtimes G$ are composable if $y = g\cdot x$, in which case $(y, h)(x, g) := (x, hg)$. The units of $X\rtimes G$ are the elements $(x, e)$, where $e$ is the unit of $G$. 

To make this example topological, let $X$ be locally compact, Hausdorff, and second-countable, and $G$ a locally compact group acting on $X$ by homeomorphisms (that is, each $x\mapsto g\cdot x$ is a homeomorphism). Then $X\rtimes G$ is a locally compact Hausdorff groupoid with the topology just the product topology (this begs the question why the notation $X\rtimes G$ is even needed). 

If $G$ is discrete, then $X\rtimes G$ is étale, since the source map is simply the map $(x, g)\mapsto x$, and around any point $(x, g)\in X\rtimes G$ we can simply take an open neighbourhood $U$ of $x$ an restrict the source map to $U\times\{g\}$. In fact, $X\rtimes G$ is étale if and only if either $X$ or $G$ is discrete: if $G$ is not discrete, take $g\in G$ such that every open neighbourhood $U$ of $g$ contains some other $h\neq g$, then the only neighbourhood of $(x,g)$ on which the source map restricts to a homeomorphism is $\{x\}\times U$ (for any open neighbourhood $U$ of $g$).

**Example (Deaconu-Renault Groupoids):** Let $X$ be a set, $\Gamma$ an abelian group acting on $X$, and $S\subseteq \Gamma$ a monoid (unital, closed under multiplication and associative, but without inverses). Let
$$
\mathcal{G} := \{(x, s - t, y)\ |\ x, y\in X,\ s, t\in S,\ s\cdot x = t\cdot y\}
$$
Put $\mathcal{G}^{(0)}$ be the set of all $(x, e, x)$, and identify this set with $X$. Define $r(x, g, y) = x$ and $s(x, g, y) = y$, and $(x, g, y)^{-1} = (y, -g, x)$. Suppose $s_1\cdot x = t_1\cdot y$ and $s_2\cdot y = t_2\cdot z$. Then
$$
(s_1 + s_2)\cdot x = s_2\cdot(s_1\cdot x) = s_2\cdot(t_1\cdot y) = t_1\cdot(s_2\cdot y) = t_1\cdot(t_2\cdot z) = (t_1 + t_2)\cdot z
$$
Thus we can define the composition $(x, s_1 - t_1, y) (y, s_2 - t_2, z)= (x, (s_1 + s_2) - (t_1 + t_2), z)$, or more succinctly $(x, g, y)(y, h, z) = (x, gh, z)$. Under these operations, $\mathcal{G}$ is a groupoid.

Let $K(S)$ denote the Grothendieck group arising from $S$, acting on $X$ via $[(s, t)]\cdot x := (s - t)\cdot x$ (where $s - t$ is well-defined in the ambient group $\Gamma$). Then there is a groupoid isomorphism from $X\rtimes K(S)$ to $\mathcal{G}$ given by taking $(x, [(s, t)])\mapsto (x, s - t, (s - t)\cdot x)$. However, if there is no ambient group $\Gamma$ in which $S$ sits, then it is not possible to define an action of $K(S)$ on $X$.

To topologize $\mathcal{G}$, let $X$ be locally compact Hausdorff and second countable, and $\Gamma$ (or just $S$) discrete, and define a topology on $\mathcal{G}$ generated by the basic open sets
$$
Z(U, s, t, V) = \{(x, s - t, y)\ |\ x\in U, y\in V,\ s\cdot x = t\cdot y\}
$$
indexed by open sets $U, V$ in $X$ and pairs $s, t\in S$.

**Example:** Let $X = 2^\mathbb{N}$, and $R$ be tail equivalence on $X$. Define a topology on $R$ generated by the basic open sets $Z(v, w) := \{(vx, wx)\ |\ x\in X\}$. We will see that this topology turns $R$ into a locally compact Hausdorff (étale?) groupoid, but this topology is finer than the product topology ($X$ equipped with it's usual metrizable topology).

**Example (Graph Groupoids):**

## 2 - Groupoid C\*-Algebras

**Lemma:** Let $G$ be a locally compact Hausdorff, second countable, étale groupoid. For $f, g\in C_c(G)$ and $\gamma\in G$, the set $\{\alpha\in G\ |\ \alpha\in G^{r(\gamma)}\ \text{and}\ f(\alpha)g(\gamma^{-1}\alpha)\neq 0\}$ is <u>finite</u>.

**Proof:** The sets $G^{r(\gamma)}$ are discrete since $G$ is étale, so $G^{r(\gamma)}\cap \text{supp}(f)$ is compact and discrete, whence finite. We necessarily have
$$
\{\alpha\in G\ |\ \alpha\in G^{r(\gamma)}\ \text{and}\ f(\alpha)g(\gamma^{-1}\alpha)\neq 0\}\subseteq G^{r(\gamma)}\cap \text{supp}(f)
$$
and so the result follows. $\square$

**Definition:** Let $G$ be as above. We define the <u>convolution</u> of $f, g\in C_c(G)$ to be the function
$$
(f*g)(\gamma) = \sum_{\alpha\in G^{r(\gamma)}}f(\alpha)g(\alpha^{-1}\gamma) \quad \left(=\sum_{\alpha\beta=\gamma}f(\alpha)g(\beta)\right)
$$
We also define an <u>involution</u> ${}^*$ on $C_c(G)$ by setting
$$
f^*(\gamma) = \overline{f(\gamma^{-1})}
$$
**Proposition:** For $f, g\in C_c(G)$, then $f * g$ is continuous, compactly supported, and $\text{supp}(f * g)\subseteq \text{supp}(f)\text{supp}(g)$.

To prove this, we'll first prove the following lemma.

**Lemma:** If $G$ is as described above, then $C_c(G) = \text{span}\{f\in C_c(G)\ |\ \text{supp}(f)\ \text{is a bisection}\}$. ($G$ doesn't even have to be second countable for this, technically).

**Proof:** Given $f\in C_c(G)$, we can cover $\text{supp}(f)$ in finitely many open bisections, $U_1, ..., U_n$. Since our space $G$ is locally compact Hausdorff, we can choose a partition of unity $h_i$ subordinate to this open cover (so $\sum_i h_i = 1$, $\text{supp}(h_i)\subseteq U_i$.) Then $f = \sum_i h_i f$ is in the span of functions supported on bisections. $\square$

We can now prove our previous proposition by invoking this lemma.

**Proof of proposition:** Take $f, g\in C_c(\mathcal{G})$. Since $*$ is bilinear, it suffices to assume $f, g$ are both supported on open bisections $U, V$ respectively. Notice then that
$$
\begin{aligned}
(f * g)(\gamma) & = \sum_{\alpha\in \mathcal{G}^{r(\gamma)}}f(\alpha)g(\alpha^{-1}\gamma) = \sum_{\alpha\in \mathcal{G}^{r(\gamma)}\cap U}f(\alpha )g(\alpha^{-1}\gamma) \\
\end{aligned}
$$
However, $\mathcal{G}^{r(\gamma)}\cap U$ contains at most one element $\alpha$ since $U$ is a bisection, so either $(f*g)(\gamma) = 0$ (when the intersection is empty), or $(f*g)(\gamma) = f(\alpha)g(\alpha^{-1}\gamma)$, where $\alpha$ is the unique element in $\mathcal{G}^{r(\gamma)}\cap U$. In other words, when $(f*g)(\gamma)\neq 0$, there is a unique composable pair $(\alpha, \beta)$  such that $\alpha\beta = \gamma$ and $f(\alpha)g(\beta)\neq 0$, from which we obtain $(f*g)(\gamma) = f(\alpha)g(\beta)$. 

Consider the set $W_U := \{\gamma\ |\ \mathcal{G}^{r(\gamma)}\cap U\neq\emptyset\}$, which can also be expressed as $r^{-1}(r(U))$, which is clearly open. Define the function $\alpha : W_U\to U$ taking $\gamma$ to the unique element $\alpha(\gamma)\in\mathcal{G}^{r(\gamma)}\cap U$, so that $(f*g)(\gamma) = f(\alpha(\gamma))g(\alpha(\gamma)^{-1}\gamma)$. We can explicitly write $\alpha(\gamma) = r|_U^{-1}(r(\gamma))$, which is clearly continuous. So $(f*g)|_{W_U}$ is continuous, and $(f*g)|_{\mathcal{G}\backslash \text{supp}(f*g)}$ is continuous (it's identically zero). Since both $\mathcal{G} = W_U\cup (\mathcal{G}\backslash\text{supp}(f*g))$ (since $\text{supp}(f*g)\subseteq W_U$), and both sets are open, we can apply the pasting lemma to see that $f*g$ is in fact continuous on all of $\mathcal{G}$.

In the general case, take $f = \sum_i f_i$ and $g = \sum_j g_j$ the sum of functions supported on open bisections, so that $f*g = \sum_{ij}f_i*g_j$ is the finite sum of continuous functions, whence is itself continuous.

As for the support of $f*g$, we see that
$$
\begin{aligned}
\{\gamma\ |\ (f*g)(\gamma)\neq 0\} & = \{\alpha\beta\ |\ f(\alpha)g(\beta)\neq 0\} \\
& = \{\alpha\ |\ f(\alpha)\neq 0\}\{\beta\ |\ g(\beta)\neq 0\} \subseteq \text{supp}(f)\text{supp}(g)
\end{aligned}
$$
whence $\text{supp}(f*g) \subseteq \text{supp}(f)\text{supp}(g)$, the latter set being closed since it's compact (we are, after all, working in a Hausdorff groupoid $\mathcal{G}$), and compact since it's the image of a compact set ($(\text{supp}(f)\times\text{supp}(g))\cap \mathcal{G}^{(2)}$) under a continuous map (multiplication). In fact in this case we also have
$$
\text{supp}(f)\text{supp}(g) = m\left(\overline{\{f\neq 0\}\times\{g\neq 0\}}\right)\subseteq \overline{m(\{f\neq 0\}\times\{g\neq 0\})} = \overline{\{f*g\neq 0\}}=\text{supp}(f*g)
$$
so in fact $\text{supp}(f*g) = \text{supp}(f)\text{supp}(g)$. This, however, is only true for functions $f, g$ supported on bisections (as this is what allowed us to obtain $\{f*g\neq 0\} = \{f\neq 0\}\{g\neq 0\}$) in general we will only have $\text{supp}(f * g)\subseteq \text{supp}(f)\text{supp}(g)$.

In general, we have
$$
\begin{aligned}
(f*g)(\gamma) & = \sum_{\alpha\in G^{r(\gamma)}}f(\alpha)g(\alpha^{-1}\gamma) \\
& = \sum\left\{f(\alpha)g(\alpha^{-1}\gamma)\ |\ \alpha\in \mathcal{G}^{r(\gamma)}\cap\text{supp}(f)\cap\gamma\text{supp}(g)^{-1}\right\}
\end{aligned}
$$
It's clear that if $\alpha\in \text{supp}(f)\cap\gamma\text{supp}(g)^{-1}$, then $\gamma = \alpha\beta$ for some $\beta\in\text{supp}(g)$ (namely $\beta = \alpha^{-1}\gamma$),  and so $\gamma\in\text{supp}(f)\text{supp}(g)$. Thus if $\gamma\not\in\text{supp}(f)\text{supp}(g)$, then $\text{supp}(f)\cap\gamma\text{supp}(g)^{-1} = \emptyset$, whence $(f*g)(\gamma) = 0$ (the sum is empty). Thus
$$
\text{supp}(f*g)\subseteq\text{supp}(f)\text{supp}(g)
$$
As above, this immediately tells us that $\text{supp}(f*g)$ is compact. $\square$

**Fact:** There is a natural embedding of $C_c(\mathcal{G}^{(0)})$ into $C_c(\mathcal{G})$. Moreover, if $f\in C_c(\mathcal{G})$ is supported on a bisection, then

* $f^**f\in C_c(\mathcal{G}^{(0)})$, and is supported on $s(\text{supp}(f))$, on which it is given by $(f^**f)(s(\gamma)) = |f(\gamma)|^2$.
* $f*f^*\in C_c(\mathcal{G}^{(0)})$, and is supported on $r(\text{supp}(f))$, on which it is given by $(f*f^*)(r(\gamma)) = |f(\gamma)|^2$.

Additionally if $f\in C_c(\mathcal{G})$ and $h\in C_c(\mathcal{G}^{(0)})$, we have $(h*f)(\gamma) = h(r(\gamma))f(\gamma)$ and $(f*h)(\gamma) = f(\gamma)h(s(\gamma))$.

**Proof:** Fairly straightforward. $\square$

Notice that this fact implies that for any two $f, g\in C_c(\mathcal{G}^{(0)})$, $(f*g)(\gamma) = f(\gamma)g(\gamma)$, so convolution on $C_c(\mathcal{G}^{(0)})$ coincides with pointwise multiplication.

### Construction of the Full C*-Algebra

This construction is due to Robin Deeley, and the presentation by Aidan Sims.

**Theorem:** Let $G$ be a second-countable, locally compact, Hausdorff, étale groupoid. For each $f\in C_c(G)$, there is a constant $K_f\ge 0$ such that $\|\pi(f)\|\le K_f$ for every $*$-representation of $C_c(G)$. If $f$ is supported on a bisection, we can take $K_f = \|f\|$ (the usual supremum norm).

**Proof:** For arbitrary $f\in C_c(G)$, let $f = \sum_i f_i$, where each $f_i$ is supported on a bisection. Set $K_f := \sum_i \|f_i\|_\infty$. Given a $*$-representation of $C_c(G)$, this clearly descends to a $*$-representation of $C_c(G^{(0)})$, but this is a commutative $*$-algebra. Not only that, $C_c(G^{(0)})$ is the union of C\*-algebras:
$$
C_c(G^{(0)}) = \bigcup_{K\subseteq G^{(0)}\ \text{compact}}C(K)
$$
On each of these subalgebras, $\pi$ restricts to a $*$-homomorphism of C\*-algebras, whence $\pi$ is norm-decreasing on these spaces, whence on all of $C_c(G^{(0)})$. This, in combination with the fact that $f^**f\in C_c(G^{(0)})$ tells us that
$$
\|\pi(f)\|^2 = \|\pi(f)^*\pi(f)\| = \|\pi(f^**f)\| \le \|f^**f\|_\infty = \|f\|_\infty^2
$$
from which the result follows. $\square$

**Definition:** Let $G$ be a second-countable, locally compact, Hausdorff, étale groupoid. Define 
$$
\rho_{\max}(f) := \sup\{\|\pi(f)\|\ :\ \pi : C_c(G)\to\mathcal{B}(H)\ \text{a $*$-rep}\}
$$
This quantity is a well-defined C\*-seminorm (by the previous theorem) on $C_c(G)$, and $N := \{f\in C_c(G)\ :\ \rho_{\max}(f) = 0\}$ is an ideal. Define the **full groupoid C\*-algebra** $C^*(G)$ to be the completion of $C_c(G)/N$ with respect to the norm $\|[f]\|_{\max} := \rho_{\max}(f)$. There is a natural $*$-homomorphism $\pi_{\max} : C_c(G)\to C^*(G)$ given by taking $f$ to $[f]$ - what we'd like to show is that this $*$-homomorphism is actually *injective*, but we have a bit of work to do before we can prove that.

**Remark:** Given any $*$-representation $\psi : C_c(G)\to\mathcal{B}(H)$, by definition $\psi$ descends to a well-defined map on $C_c(G)/N$, which is continuous with respect to the max norm. Thus, $\psi$ extends to a well-defined $*$-homomorphism $\widetilde{\psi} : C^*(G)\to\mathcal{B}(H)$, and moreover $\widetilde{\psi}\circ\pi_{\max} = \psi$, so $\psi$ factors through $C^*(G)$.

**Example:** Given a discrete group $G$, by definition it is not hard to see that the full groupoid C\*-algebra is the same as the full group C\*-algebra.

**Example:** Let $R_N$ be the matrix groupoid described prior, equipped with the discrete topology. Then $C_c(R_N) = \mathbb{C}[R_N]$, and convolution in $\mathbb{C}[R_N]$ is just matrix multiplication, so $C_c(R_N) = M_N(\mathbb{C})$.

**Example:** Let $\Gamma$ be a discrete group acting on a locally compact Hausdorff space $X$. One can show via a universality property of the crossed product that $C^*(X\rtimes\Gamma)\cong C(X)\rtimes\Gamma$.

**Example:** Let $R_{2^\infty}$ denote the relation groupoid of tail equivalence on $\{0, 1\}^\mathbb{N}$ with the topology described above. Then $C^*(R_{2^\infty})\cong M_{2^\infty}$ (also known as the CAR algebra).

**Definition:** A <u>unitary representation</u> of a groupoid $G$ is a triple $(H, p, U)$, where $\mu$ is a Borel measure on $G^{(0)}$, $H = \bigsqcup_{x\in G^{(0)}}H_x$ is a $\mu$-measurable field of Hilbert spaces, and $U = \{U_\gamma\ |\ \gamma\in G\}$ is a family of unitary operators $U_\gamma : H_{s(\gamma)}\to H_{r(\gamma)}$ satisfying $U_\alpha U_\beta = U_{\alpha\beta}$, $U_{\alpha^{-1}} = U_\alpha^*$, and $\gamma\mapsto \langle U_\gamma\xi(s(\gamma))\, \ \eta(r(\gamma))\rangle$ is measurable for each pair $\xi, \eta$ of measurable sections of $H$. Every unitary representation $(H, \mu, U)$ of $G$ induces a $*$-representation
$$
\pi_{(H, \mu, U)} : C_c(G) \to \mathcal{B}\left(\int_{G^{(0)}}^\oplus\mathcal{H}_x\text{d}\mu(x)\right)
$$
characterized by
$$
\left\langle\pi_{(H, \mu, U)}(f)\xi\ ,\ \eta\right\rangle = \int_{G^{(0)}}\sum_{\gamma\in G_x}\left\langle f(\gamma)U_\gamma\xi(x)\ ,\ \xi(r(\gamma))\right\rangle\text{d}\mu(x)
$$
This representation is called the **integrated form** of $(H, \mu, U)$. Renault's disintegration theorem tells us that every representation arises this way.

### Construction of the Reduced C\*-Algebra

In order to show that the map $\pi_{\max} : C_c(\mathcal{G})\to C^*(\mathcal{G})$ is injective, we need to show that there exists at least one injective representation of $C_c(\mathcal{G})$. We will construct this in a similar way to how we construct the left regular representation of a group $G$.

**Definition:** Let $\mathcal{G}$ be a locally compact Hausdorff étale second countable groupoid. For each unit $x$, there is a $*$-representation $\pi_x : C_c(\mathcal{G})\to\mathcal{B}(\ell^2(\mathcal{G}_x))$ given by $\pi_x(f)\delta_\gamma = \sum_{\alpha\in \mathcal{G}_{r(\gamma)}}f(\alpha)\delta_{\alpha\gamma}$ (or equivalently $\pi_x(f)\delta_\gamma = \text{``}f*\delta_\gamma\text{"}$, the quotation marks here denoting that the convolution has not really been defined for the (possibly) discontinuous function $\delta_\gamma$), called the left-regular representation of $C_c(\mathcal{G})$ associated to $x$. 

**Remark:** To see how this is truly a "diagonal" operator, let's consider the case for a discrete group $G$, in which case $C_c(G) = \mathbb{C}[G] = \text{span}\{g\ :\ g\in G\}$. The usual diagonal operator $\pi : \mathbb{C}[G]\to\mathcal{B}(\ell^2(G))$ is defined by $\pi(g)\delta_h = \delta_{gh}$. Extending by linearity to the rest of $\mathbb{C}[G]$ gives the same formula as above.

**Definition:** Let $\pi_r$ denote the $*$-representation $\bigoplus_{x\in\mathcal{G}^{(0)}}\pi_x : C_c(\mathcal{G})\to\mathcal{B}\left(\bigoplus_{x\in \mathcal{G}^{(0)}}\ell^2(G_x)\right)$. The <u>reduced C\*-algebra</u>, denoted $C_r^*(\mathcal{G})$, is the completion of $\pi_r(C_c(\mathcal{G}))$ in the operator norm. We denote by $\|\cdot\|_r$ the C\*-norm on $C_r^*(\mathcal{G})$.

By definition, $\|\pi_r(f)\|_r\le \rho_{\max}(f) = \|[f]\|_{\max}$. 



**Some Questions and Important Remarks:**

* Is there an inclusion of $C_c(\mathcal{G})$ in $C_r^*(\mathcal{G})$?

There is naturally an inclusion of $C_c(\mathcal{G})$ in $C_r^*(\mathcal{G})$ and $C^*(\mathcal{G})$, since both $\oplus_x\pi_x$ and $\pi_{\max}$ are injective. 

* $C_r^*(\mathcal{G})$ in $C^*(\mathcal{G})$?

There is, generally, no inclusion of $C_r^*(\mathcal{G})$ in $C^*(\mathcal{G})$, rather the opposite is true: $C_r^*(\mathcal{G})$ is a quotient of $C^*(\mathcal{G})$.

* Which subgroupoids $\mathcal{H}$ of $\mathcal{G}$ induce an inclusion $C^*(\mathcal{H})\hookrightarrow C^*(\mathcal{G})$?

Let $\mathcal{H}$ be an open subgroupoid of $\mathcal{G}$. There is a natural isometric inclusion of $C_c(\mathcal{H})$ in $C_c(\mathcal{G})$, given by extending $f$ to $0$ outside of $\mathcal{H}$. Clearly $\|f\|_{C^*(\mathcal{G})}\le \|f\|_{C^*(\mathcal{H})}$ for any $f\in C_c(\mathcal{H})$, since every representation of $C_c(\mathcal{G})$ restricts to a representation of $C_c(\mathcal{H})$.

Now suppose $\mathcal{H}$ is a *clopen* subgroupoid. Then the restriction map $C_c(\mathcal{G})\to C_c(\mathcal{H})$ is well-defined (and $\text{supp}(f|_{\mathcal{H}}) = \text{supp}(f)\cap\mathcal{H}$, which doesn't hold if $\mathcal{H}$ isn't closed). Consider the following commutative diagram:

<img src="C:\Users\Michael\AppData\Roaming\Typora\typora-user-images\image-20221106232048777.png" alt="image-20221106232048777" style="zoom:50%;" />

Here $\pi_{\max}$ and $\rho_{\max}$ are the canonical maps, and the inclusion of $\mathcal{C}^*(\mathcal{H})$ into $\mathcal{B}(\mathcal{K})$ is isometric. The map $\psi$ exists by the factorization theorem for $C^*(\mathcal{G})$ above, so $\psi\circ\pi_{\max} = \rho$, where $\rho : C_c(\mathcal{G})\to\mathcal{B}(\mathcal{K})$ is composition of arrows above. We may as well assume $\psi$'s codomain is $C^*(\mathcal{H})$, since $\rho$'s codomain is (an isometric copy of it in $\mathcal{B}(\mathcal{K})$). So really we have a diagram

<img src="C:\Users\Michael\AppData\Roaming\Typora\typora-user-images\image-20221106232421548.png" alt="image-20221106232421548" style="zoom:50%;" />

where $\rho(f) = \rho_{\max}(f|_{\mathcal{H}})$. Then
$$
\begin{aligned}
\|f_\mathcal{H}\|_{C^*(\mathcal{H})} & = \|\rho_{\max}(f|_{\mathcal{H}})\|=\|\psi(\pi_{\max}(f))\| \\
& \le \|\pi_{\max}(f)\| = \|f\|_{C^*(\mathcal{G})}
\end{aligned}
$$
where the jump from the first to the second line is due to the fact that $\psi$ is a $*$-homomorphism, whence contractive. Thus, in the case of clopen subgroupoids $\mathcal{H}$ of $\mathcal{G}$, we have a natural inclusion $C^*(\mathcal{H})\hookrightarrow C^*(\mathcal{G})$. Thus, for example, in a Hausdorff étale groupoid $\mathcal{G}$ we have a natural inclusion $C^*(\mathcal{G}^{(0)})\hookrightarrow C^*(\mathcal{G})$.

* Is $C^*(\mathcal{G}^{(0)})$ abelian?

Yes: $C^*(\mathcal{G}^{(0)})$ is the norm-closure of $C_c(\mathcal{G}^{(0)})$, which is itself abelian (since convolution restricts to pointwise multiplication on $\mathcal{G}^{(0)}$).

* Is $C^*(\mathcal{G}^{(0)})$ a masa in $C^*(\mathcal{G})$?

* How are $C_r^*(\mathcal{G})$ and $C_0(\mathcal{G})$ related?

There is an injective, norm-decreasing map $j : C_r^*(\mathcal{G})\to C_0(\mathcal{G})$, for which $j(f) = f$ for any $f\in C_c(\mathcal{G})$.

* How are $C_r^*(\mathcal{G})$ and $C_0(\mathcal{G}^{(0)})$ related?

In the next section, we will see how the restriction map $C_c(\mathcal{G})\to C_c(\mathcal{G}^{(0)})$ restricts to a faithful conditional expectation $\Phi : C_r^* (\mathcal{G})\to C_0(\mathcal{G}^{(0)})$. Moreover, the sequence $C_c(\mathcal{G}^{(0)})\hookrightarrow C_r^*(\mathcal{G})\overset{\Phi}{\to} C_0(\mathcal{G}^{(0)})$ telescopes to the inclusion of $C_c(\mathcal{G}^{(0)})\subseteq C_0(\mathcal{G}^{(0)})$.

* What is the relationship between $\Phi$ and $j$?

Let $\iota$ denote the inclusion of $C_c(\mathcal{G}^{(0)})$ in $C_c(\mathcal{G})$. Since $\Phi(\iota(f)) = f$ and $j(\iota(f)) = \iota(f)$, we have $j(f)|_{\mathcal{G}^{(0)}} = \Phi(f)$ for every $f\in C_c(\mathcal{G})$.

* Is $C_0(\mathcal{G})$ the completion of $C_c(\mathcal{G})$ with respect to the max (resp. reduced) norm in $C^*(\mathcal{G})$ (resp. $C_r^*(\mathcal{G})$)?

**No**. Of course not - the completion of $C_c(\mathcal{G})$ with respect to the max (resp. reduced) norms is *precisely* $C^*(\mathcal{G})$ (resp. $C_r^*(\mathcal{G})$). If $C_0(\mathcal{G})$ were the completion with respect to either of these norms, this would mean that these norms coincide with the sup-norm on $C_c(\mathcal{G})$.

* Is $C_0(\mathcal{G}^{(0)})$ the completion of $C_c(\mathcal{G}^{(0)})$ with respect to the max (resp. reduced) norm in $C^*(\mathcal{G})$ (resp. $C_r^*(\mathcal{G})$)?

**Yes**, perhaps a little surprisingly at first (given the fact above). Recall that while $\|f\|_{\infty}\le\|f\|_r\le \|f\|_{\max}$ for any $f\in C_c(\mathcal{G})$, when <u>$f$ is supported on a bisection</u>, then $\|f\|_{\max}\le \|f\|_\infty$. What do you know, $\mathcal{G}^{(0)}$ is a bisection, so all three norms coincide when restricted to $C_c(\mathcal{G}^{(0)})$. This means $C_0(\mathcal{G}^{(0)})$ is the completion of $C_c(\mathcal{G}^{(0)})$ with respect to *any* of these norms, and so $C_0(\mathcal{G}^{(0)})$ is contained isometrically in both $C^*(\mathcal{G})$ and $C_r^*(\mathcal{G})$.











## Effective Groupoids, Conditional Expectations, and Ideals in $C^*(\mathcal{G})$

**Definition:** An étale groupoid $\mathcal{G}$ is said to be **effective** if $\text{Iso}(\mathcal{G})^\circ = \mathcal{G}^{(0)}$. The definition is inspired by the definition of an *effective action*. The action of a discrete group $\Gamma$ on a locally compact Hausdorff space $X$ is said to be **effective** if, for each $g\in\Gamma$, the set $X_g := \{x\in X\ |\ g\cdot x = x\}$ has empty interior (or equivalently, since $X_g$ is closed, we require each $X_g$ be *nowhere dense*).

**Fact:** If $\Gamma\curvearrowright X$ is an effective action, then the action groupoid $X\rtimes \Gamma$ is effective.

**Proof:** 

**Theorem:** Let $\mathcal{G}$ be a second-countable, étale groupoid. Then $\mathcal{G}$ is effective if and only if $\{x\ |\ \mathcal{G}(x)\ \text{is trivial}\}$ is *dense* in $\mathcal{G}^{(0)}$. That is, $\mathcal{G}$ is effective if and only if "most units have trivial vertex group".

**Theorem:** Let $\mathcal{G}$ be étale. Then there is a *faithful conditional expectation* $\Phi : C_r^*(\mathcal{G})\to C_0(\mathcal{G}^{(0)})$ such that

* $\Phi(f) = f|_{\mathcal{G}^{(0)}}$ for all $f\in C_c(\mathcal{G})$
* $\forall a\in C_r^*(\mathcal{G})$, $j(\Phi(a)) = j(a)|_{\mathcal{G}^{(0)}}$, where $j : C_r^*(\mathcal{G})\to C_0(\mathcal{G})$ is the injective, norm-decreasing map defined in the prior section.

Tomiyama's theorem guarantees that for C*-algebras $B\subseteq A$, an idempotent, contractive map $\Phi : A\to B$ which fixes $B$ is automatically a conditional expectation.

**Theorem:** Let $\mathcal{G}$ be an *effective*, *étale* groupoid. Suppose $\varphi : C_r^*(\mathcal{G})\to A$ is a bounded $*$-homomorphism, and $\varphi$ is injective on $C_0(\mathcal{G}^{(0)})$. Then $\varphi$ must be injective.

### Ideal Structure

**Definition:** A set $U\subseteq\mathcal{G}^{(0)}$ is called **invariant** if $r(\mathcal{G}U)\subseteq U$: that is, taking any edge out of a unit in $U$ leads us back to a unit in $U$.

**Lemma:** Let $I\subseteq C^*(\mathcal{G})$ be an ideal. Then there exists an open invariant subset $U\subseteq\mathcal{G}^{(0)}$ called the **support** of $I$, such that $I\cap C_0(\mathcal{G}^{(0)})\cong C_0(U)$.

**Theorem:** Let $\mathcal{G}$ be étale, and $U\subseteq\mathcal{G}^{(0)}$ an open, invariant set. Let $W := \mathcal{G}^{(0)}\backslash U$. Then $C_c(\mathcal{G}U)\hookrightarrow C_c(\mathcal{G})$ extends to an **injective $*$-homomorphism** $\iota_U : C^*(\mathcal{G}U)\to C^*(\mathcal{G})$, and the set $I_U := \iota_U(C^*(\mathcal{G}U))$ is an ideal in $C^*(\mathcal{G})$. Moreover, there exists a **surjective $*$-homomorphism** $\pi_U : C^*(\mathcal{G})\to C^*(\mathcal{G}W)$ such that $\forall f\in C_c(\mathcal{G})$, $\pi_U(f) = f|_{\mathcal{G}W}$. Finally, the sequence
$$
0\to C^*(\mathcal{G}U)\overset{\iota_U}{\to}C^*(\mathcal{G})\overset{\pi_U}{\to}C^*(\mathcal{G}W)\to 0
$$
is exact.

**Theorem:** Let $\mathcal{G}$ be an *amenable*, étale groupoid. Then $U\mapsto I_U$ is an **injective map** from the open invariant subsets of $\mathcal{G}^{(0)}$ to the set of ideals of $C^*(\mathcal{G})$.

**Definition:** An étale groupoid $\mathcal{G}$ is said to be **strongly effective** if for all closed invariant sets $W\subseteq\mathcal{G}^{(0)}$, the groupoid $\mathcal{G}W$ is effective.

**Theorem:** If $\mathcal{G}$ is *étale*, *amenable*, and *strongly effective*, then the map $U\mapsto I_U$ is **bijective**.

**Proof:** The idea is to show that $I_\text{supp(I)} = I$.

**Definition:** A groupoid $\mathcal{G}$ is said to be **minimal** if $\forall x\in\mathcal{G}^{(0)}$, $r(\mathcal{G}_x)$ is dense in $\mathcal{G}^{(0)}$. In other words, $\mathcal{G}$ is minimal if every unit has an edge leading outward to "almost" every other unit.

**Lemma:** If $\mathcal{G}$ is any minimal groupoid (not just étale), then $\emptyset$ and $\mathcal{G}^{(0)}$ are the only invariant open subspaces of $\mathcal{G}^{(0)}$.

**Theorem:** Suppose $\mathcal{G}$ is étale and amenable. Then $C^*(\mathcal{G})$ is simple *if and only if* $\mathcal{G}$ is both *effective* and *minimal*.

**Theorem:** If $\mathcal{G}$ is effective, minimal, and étale (not necessarily amenable), then $C_r^*(\mathcal{G})$ is simple.

This is stronger than the "if" direction of the previous theorem, since we don't necessarily need $\mathcal{G}$ to be amenable. If it were, 















## Kumjian-Renault Theory

Main references: 

* Renault's book "A groupoid approach to C\*-algebras"
* A. Kumjian, "On C\*-diagonals"
* J. N. Renault, "Cartan subalgebras in C\*-algebras"

**Definition:** Let $\mathcal{G}$ be an étale groupoid. A <u>twist</u> over $\mathcal{G}$ is a sequence
$$
\mathcal{G}^{(0)}\times \mathbb{T}\overset{\iota}{\to}\mathcal{E}\overset{\pi}{\to} \mathcal{G}
$$
where $\mathcal{G}^{(0)}\times\mathbb{T}$ is regarded as a trivial group bundle with fibres $\mathbb{T}$, $\mathcal{E}$ is a locally compact Hausdorff groupoid, and $\iota,\pi$ are continuous groupoid homomorphisms which restrict to homeomorphisms on the unit spaces. We identify $\mathcal{E}^{(0)}$ with $\mathcal{G}^{(0)}$ via $\iota$. We also further require:

1. $\iota$ is injective.
2. $\mathcal{E}$ is a locally trivial $\mathcal{G}$-bundle: each $\alpha\in\mathcal{G}$ has a bisection neighbourhood $U$ on which there exists a continuous section $S : U\to\mathcal{E}$ satisfying $\pi\circ S = \text{id}_U$, and such that $(\alpha, z)\mapsto \iota(r(\alpha), z)S(\alpha)$ is a homeomorphism of $U\times\mathbb{T}$ onto $\pi^{-1}(U)$.
   * *Remark:* Notice that this condition implies $\pi$ is surjective, since $\pi(S(\gamma)) = \gamma$.
   * *Remark:* In these notes, I call bisections $U$ with the above property "trivializing" bisections, since they induce local trivializations of $\mathcal{E}$.
3. $\pi^{-1}(\mathcal{G}^{(0)}) = \iota(\mathcal{G}^{(0)}\times\mathbb{T})$.
   * *Remark:* This condition generalizes the idea that in an exact sequence, $\text{ran}(\iota) = \text{ker}(\pi)$.
4. $\iota(\mathcal{G}^{(0)}\times\mathbb{T})$ is central in $\mathcal{E}$ in the sense that $\iota(r(\varepsilon), z)\varepsilon = \varepsilon\iota(s(\varepsilon), z)$ for all $\epsilon\in\mathcal{E}$ and $z\in\mathbb{T}$.

**Remark:** Property three tells us that $\pi(\iota(g, z)) \in\mathcal{G}^{(0}$ for any $(g, z)\in\mathcal{G}^{(0)}\times\mathbb{T}$, but in fact we can say more than that. Since $\pi, \iota$ are groupoid homomorphisms, they commute with the range and source maps, whence for any $(g, z)\in\mathcal{G}^{(0)}\times\mathbb{T}$,
$$
\begin{aligned}
r(\pi(\iota(g, z))) = \pi(\iota(g, 1)) = g & \quad\text{by identification of unit spaces} \\
s(\pi(\iota(g, z))) = \pi(\iota(g, 1)) = g
\end{aligned}
$$
Since $\pi(\iota(g, z))$ is a unit, this forces $\pi(\iota(g, z)) = g$, for *any* $z\in\mathbb{T}$. Thus we in fact have $\pi\circ\iota = \pi_1$, the projection onto the first coordinate.

**Remark:** If $\mathcal{G} = \Gamma$ is a discrete group, then a twist is simply a central extension of $\Gamma$: an exact sequence $1\to A\to E\to G\to 1$ where $A$ is included in the centre of $E$.

To see this, note first that if $\mathcal{G}$ is just the discrete group $\Gamma$, then $\mathcal{G}^{(0)} = \{e\}$ is just the identity of $\Gamma$, and so a twist over $\Gamma$ reduces to a sequence $\mathbb{T}\overset{\iota}{\to}\mathcal{E}\overset{\pi}{\to}\Gamma$. Since $\mathcal{E}^{(0)}$ is homeomorphic to $\mathcal{G}^{(0)}$, which is trivial, we see that $\mathcal{E}$ is itself a group, and so $\iota$ and $\pi$ are just *group* homomorphisms. We assume $\iota$ is injective, and $\pi$ is surjective by assumption 2. Moreover, condition 3 tells us that $\pi^{-1}(\{e\}) = \iota(\mathbb{T})$, which is just saying $\text{ker}\pi = \text{ran}\iota$. Thus, we have an *exact* sequence $0\to\mathbb{T}\overset{\iota}{\to}\mathcal{E}\overset{\pi}{\to}\Gamma\to 0$. Finally, since $r(\epsilon) = s(\epsilon) = e$ for all $\epsilon\in\mathcal{E}$, condition 4 reduces to saying $\iota(z)\varepsilon = \varepsilon\iota(z)$ for all $\varepsilon\in \mathcal{E}$, $z\in\mathbb{T}$, whence $\text{ran}\iota\subseteq Z(\mathcal{E})$, so $\mathcal{E}$ is a central extension of $\Gamma$ by $\mathbb{T}$.

There is an additional bit of structure on $\mathcal{E}$ in this case, imposed by condition 2. Since $\Gamma$ is étale, the only bisective neighbourhood of a point $g\in\Gamma$ is the singleton $\{g\}$, so we have to take $U = \{g\}$. The "section" $S : U\to\mathcal{E}$ is then just a single element, which we denote $s_g\in\mathcal{E}$, such that $\pi(s_g) = g$ (so $s_g\in\pi^{-1}(g)$), and for which the map $z\mapsto\iota(z)s_g$ induces a homeomorphism of $\mathbb{T}$ with $\pi^{-1}(\{g\})$.

**Remark:** In many instances, we will see that a twist $\mathcal{E}$ is actually *frequently* non-étale, irrespective of the étale-ness of $\mathcal{G}$. 

**Fact:** If $\mathcal{E}\to\mathcal{G}$ is a twist, then $\iota(\mathcal{G}^{(0)}\times \mathbb{T})$ is open. Additionally, if $\mathcal{G}$ is Hausdorff, then $\iota(\mathcal{G}^{(0)}\times\mathbb{T})$ is closed.

**Proof:** Suppose $\iota(g, z)\in\iota(\mathcal{G}^{(0)}\times\mathbb{T})$. Choose an open bisection $U\subseteq\mathcal{G}$ containing $g$, and for which $\pi^{-1}(U)\cong U\times\mathbb{T}$. Since $\mathcal{G}$ is étale, $\mathcal{G}^{(0)}$ is open, so we can consider the neighbourhood $V := U\cap\mathcal{G}^{(0)}$, which is easily checked to satisfy $\pi^{-1}(V)\cong V\times\mathbb{T}$. Of course, $\pi^{-1}(V)$ is open, and $g\in\pi^{-1}(V)\subseteq\iota(\mathcal{G}^{(0)}\times\mathbb{T})$, whence $\iota(\mathcal{G}^{(0)}\times\mathbb{Z})$ is open.

Assume $\mathcal{G}$ is Hausdorff, so that $\mathcal{G}^{(0)}$ is closed. A similar method as above yields the desired result: consider $\varepsilon\not\in\iota(\mathcal{G}^{(0)}\times\mathbb{T})$, and choose an open bisection $U$ such that $\pi(\varepsilon)\in U$ and $\pi^{-1}(U)\cong U\times\mathbb{T}$. Since $\mathcal{G}^{(0)}$ is closed, $V := U\backslash \mathcal{G}^{(0)}$ is open, $\varepsilon\in\pi^{-1}(V)\cong V\times\mathbb{T}$, and $V\times\mathbb{T}$ is disjoint from $\iota(\mathcal{G}^{(0)}\times\mathbb{T})$.

 $\square$

**Definition:** If $\mathcal{E}\to\mathcal{G}$ is a twist, then $\mathcal{E}$ is naturally a left/right $\mathbb{T}$-space, with the (left) action defined by taking $\varepsilon\mapsto z\cdot\varepsilon := \iota(r(\varepsilon), z)\varepsilon$. Indeed it's not hard to check that $z\cdot(w\cdot \varepsilon) = (zw)\cdot\varepsilon$, and $1\cdot\varepsilon = \varepsilon$.

Notice that $r(z\cdot\varepsilon) = r(\varepsilon)$ and $s(z\cdot\varepsilon) = s(\varepsilon)$, so the action of $\mathbb{T}$ on $\mathcal{E}$ preserves the edge sets $\mathcal{E}_x$ and $\mathcal{E}^x$, whence also the vertex groups $\mathcal{E}(x) = \mathcal{E}_x\cap\mathcal{E}^x$. Additionally, if $(\varepsilon, \delta)\in\mathcal{E}^{(2)}$, then $(z\cdot\varepsilon)(w\cdot\delta) = (zw)\cdot(\varepsilon\delta)$ for any $z, w\in\mathbb{T}$, since
$$
\begin{aligned}
(z\cdot\varepsilon)(w\cdot\delta) & = \left(\iota(r(\varepsilon), z)\varepsilon\right)\left(\iota(r(\delta), w)\delta\right) \\
& = \iota(r(\varepsilon), z)\left(\varepsilon\iota(s(\varepsilon), w)\right)\delta \\
& = \iota(r(\varepsilon), z)\iota(r(\varepsilon), w)\varepsilon\delta = (zw)\cdot(\varepsilon\delta)
\end{aligned}
$$
These identities tell us that $\mathcal{E}/\mathbb{T}$, the set of orbits of $\mathcal{E}$ under $\mathbb{T}$, inherits a natural topological groupoid structure from $\mathcal{E}$.

**Fact:** If $\mathcal{E}\to\mathcal{G}$ is a twist, then $\mathcal{E}/\mathbb{T}\cong\mathcal{G}$ (as groupoids), via the map $\widetilde{\pi}([\varepsilon]) := \pi(\varepsilon)$. Moreover, whenever $\pi(\varepsilon) = \pi(\delta)$, there exists a *unique* $z\in\mathbb{T}$ such that $\delta = z\cdot\varepsilon$. The map $\widetilde{\pi}$ is continuous, but when $\pi$ is additionally an open map (an assumption which holds fairly frequently), $\widetilde{\pi}$ is a homeomorphism.

**Proof:** First we'll check that the map $\widetilde{\pi}$ is well-defined. Suppose $[\varepsilon] = [\delta]$, so there exists $z\in\mathbb{T}$ such that $\delta = z\cdot\varepsilon$. Then $\pi(\delta) = \pi(z\cdot\varepsilon) = \pi(\iota(r(\varepsilon), z)\varepsilon) = \pi(\iota(r(\varepsilon), z))\pi(\varepsilon)$. Recall that $\pi^{-1}(\mathcal{G}^{(0)})=\iota(\mathcal{G}^{(0)}\times\mathbb{T})$, so $\pi(\iota(r(\varepsilon), z))$ is a unit, and thus is equal to it's own range, which is $r(\varepsilon)$ ($= \pi(r(\varepsilon))$, since we've associated $\mathcal{E}^{(0)}$ homeomorphically with $\mathcal{G}^{(0)}$ via the restriction of $\pi$). Therefore, $\pi(\delta) = \pi(\varepsilon)$, so the map $\widetilde{\pi}$ is well-defined. $\widetilde{\pi}$ is also clearly surjective, since $\pi$ is surjective.

Now assume $\pi(\varepsilon) = \pi(\delta)$. Then $\pi(\varepsilon^{-1}\delta) = s(\varepsilon)\in\mathcal{G}^{(0)}$. To see this, recall that since $\pi$ is a groupoid homomorphism, $\pi(\varepsilon)^{-1}\pi(\delta) = \pi(\varepsilon^{-1}\delta)$. But $\pi(\varepsilon)^{-1}\pi(\delta) = s(\pi(\varepsilon)) = \pi(s(\varepsilon))$ ($r$ and $s$ commute with $\pi$ since, again, it's a groupoid homomorphism). Of course, since we've identified $\mathcal{E}^{(0)}$ and $\mathcal{G}^{(0)}$ via $\pi$, we have $\pi(s(\varepsilon)) = s(\varepsilon)$.

So we now know that $\varepsilon^{-1}\delta\in \pi^{-1}(\mathcal{G}^{(0)})$, which, by assumption, is equal to $\iota(\mathcal{G}^{(0)}\times\mathbb{T})$, so there exists $z\in\mathbb{T}$ such that $\varepsilon^{-1}\delta = \iota(s(\varepsilon), z)$. Such $z$ is unique since $\iota$ is injective. Finally, this tells us $\delta = z\cdot\varepsilon$, so $[\delta] = [\varepsilon]$.

We leave it as an easy exercise to the reader that $\widetilde{\pi}$ is a groupoid homomorphism. We will check, however, that $\widetilde{\pi}$ is continuous. Let $q : \mathcal{E}\to\mathcal{E}/\mathbb{T}$ denote the quotient map. It's well-known that the map $q$ is an open map. For any open set $U\subseteq\mathcal{G}$, $\widetilde{\pi}^{-1}(U) = q(\pi^{-1}(U))$, which is open since $\pi$ is continuous. If additionally $\pi$ is open, then $\widetilde{\pi}(q(U)) = \pi(U)$ is open for every $U$ open in $\mathcal{E}$, which is enough to prove $\widetilde{\pi}$ is open since sets of the form $q(U)$ form a basis for the topology on $\mathcal{E}/\mathbb{T}$.

$\square$

**Corollary:** If $\mathcal{E}\to\mathcal{G}$ is a twist, then the fibres of $\pi$ are all homeomorphic to $\mathbb{T}$: for all $\gamma\in\mathcal{G}$, $\pi^{-1}(\gamma) \cong \mathbb{T}$.

**Proof:** For all $\varepsilon, \delta\in\pi^{-1}(\delta)$, $\pi(\varepsilon) = \pi(\delta) = \gamma$, so we can apply the prior fact to obtain $\varepsilon = z\cdot\delta$ for *fixed* $\delta$. $\square$

**Example:** The groupoid $\mathcal{G}\times\mathbb{T}$ is a twist over $\mathcal{G}$ in the obvious way. This is called the trivial twist over $\mathcal{G}$.

**Example:** We define a <u>continuous, normalised $\Gamma$-valued 2-cocycle</u> on a groupoid $\mathcal{G}$, (acting on $\Gamma$ a locally compact abelian group) to be a continuous map $\sigma : \mathcal{G}^{(2)}\to\Gamma$ such that $\sigma(r(\gamma), \gamma) = \sigma(\gamma, s(\gamma)) = 1$ for all $\gamma\in\mathcal{G}$, and for any $(\alpha,\beta,\gamma)\in\mathcal{G}^{(3)}$, 
$$
\sigma(\alpha,\beta)\sigma(\alpha\beta,\gamma) = \underbrace{(\alpha\cdot\sigma(\beta,\gamma))}_{\text{or just}\ \sigma(\beta,\gamma)\ \text{ if the action is trivial}}\sigma(\alpha,\beta\gamma)\qquad\text{(Cocycle Identity)}
$$
Don't be any more frightened by this than you'd normally be for group cohomology, because this is precisely the definition of a 2-cocycle for a group $G$ acting on an abelian group $\Gamma$, extended to groupoids. Functions of this type form an abelian group under pointwise multiplication, which we denote $Z^2(\mathcal{G}, \Gamma)$. Notice also that the cocycle identity and normality implies
$$
\sigma(\alpha, \alpha^{-1}) = \sigma(\alpha, \alpha^{-1})\sigma(\alpha\alpha^{-1},\alpha) = \sigma(\alpha^{-1}, \alpha)\sigma(\alpha, \alpha^{-1}\alpha) = \sigma(\alpha^{-1}, \alpha)
$$
Given a continuous normalised $\mathbb{T}$-valued 2-cocycle on a groupoid $\mathcal{G}$ (acting trivially on $\mathbb{T}$), we can turn $\mathcal{G}\times\mathbb{T}$ into a sort of "twisted groupoid" $\mathcal{E}_\sigma$, which has the same underlying set as $\mathcal{G}\times\mathbb{T}$ with identical source and range maps, but with
$$
(\alpha, w)(\beta, z) := (\alpha\beta, \sigma(\alpha,\beta)wz),\qquad (\alpha, w)^{-1} := (\alpha^{-1}, \overline{\sigma(\alpha^{-1}, \alpha)w})
$$
There is a natural groupoid inclusion $\mathcal{G}^{(0)}\times\mathbb{T}\hookrightarrow\mathcal{E}_\sigma$ which we dub $\iota$, and a natural projection morphism $\pi : \mathcal{E}_\sigma\to \mathcal{G}$ given by taking $(\alpha, w)$ to $\alpha$. Then $\mathcal{E}_\sigma$ is a twist over $\mathcal{G}$. The first, third, and fourth conditions are easy enough to check. As for the second condition (that $\mathcal{E}_\sigma$ be a locally trivial $\mathcal{G}$-bundle),

**Remark:** In the above example, we can recover the cohomology class of the 2-cocycle $\sigma$. In general, when a twist $\mathcal{E}$ admits a continuous (global) section, then one can construct from this section a 2-cocycle $\sigma$ for which $\mathcal{E}$ is isomorphic to $\mathcal{E}_\sigma$, equivariantly with $\iota$ and $\pi$. However, it is not always the case that a twist admits a continuous section.



### $\mathbb{T}$-Equivariant Functions and Convolution

Since $\mathcal{G}$ is étale, each of the sets $\mathcal{G}^x$ is discrete, and moreover $\pi^{-1}(\mathcal{G}^x) = \mathcal{E}^x$. This, combined with the fact that $\pi^{-1}(\{\gamma\})\cong\mathbb{T}$ tells us that $\mathcal{E}^x\cong\bigsqcup_{\gamma\in \mathcal{G}^x}\pi^{-1}(\{\gamma\})=\bigsqcup_{\mathcal{G}^x}\mathbb{T}$, so $\mathcal{E}^x$ looks like the disjoint union of $|\mathcal{G}^x|$ copies of $\mathbb{T}$. This allows us to endow $\mathcal{E}^x$ with a measure $\lambda^x$, the pull-back by $\pi$ of the Haar measures on each fibre $\mathbb{T}$, such that the measure of each $\pi^{-1}(\{\gamma\})$ is $1$. Moreover, such a measure is easily seen to be $\mathbb{T}$-invariant. We define an analogous measure $\lambda_x$ on $\mathcal{E}_x$.

**Question:** Can we always choose $\lambda^x$ such that $\{\lambda^x\}$ forms a <u>continuous system of probability measures</u>? (That is, such that for each $f\in C_c(\mathcal{E})$, the map $x\mapsto \int_{\mathcal{E}}f\text{d}\lambda^x$ is continuous?)

**Definition:** Let $\mathcal{E}\to\mathcal{G}$ be a twist. We write $\Sigma_c(\mathcal{G}; \mathcal{E}) := \{f\in C_c(\mathcal{E})\ :\ f(z\cdot\varepsilon) = zf(\varepsilon)\}$ to denote the space of compactly supported, $\mathbb{T}$-equivariant continuous functions on $\mathcal{E}$. Let $\lambda^x$ be the measures on $\mathcal{E}^x$ defined above. Then $\Sigma_c(\mathcal{G}; \mathcal{E})$ comes equipped with a natural convolution, given by
$$
(f*g)(\varepsilon) := \int_{\mathcal{E}^{r(\varepsilon)}}f(\delta)g(\delta^{-1}\varepsilon)\ \text{d}\lambda^{r(\varepsilon)}(\delta)
$$

**Remark:** Suppose that $\pi(\delta) = \pi(\delta')$, so $\delta, \delta'\in\mathcal{E}^{r(\varepsilon)}$ occupy the same fibre. Then there exists some (unique) $z\in\mathbb{T}$ such that $\delta = z\cdot\delta'$, whence
$$
\begin{aligned}
f(\delta)g(\delta^{-1}\varepsilon) & = f(z\cdot\delta')g\left((z\cdot\delta')^{-1}\varepsilon\right) = f(z\cdot\delta') g\left(z^{-1}(\delta')^{-1}\varepsilon\right) \\
& = f(\delta')g((\delta')^{-1}\varepsilon)
\end{aligned}
$$
In other words, the integrand of $f*g$ is <u>fibrewise-constant</u>. Since the measures of each fibre are $1$, the integral is just the sum of $f(\delta)g(\delta^{-1}\varepsilon)$, where $\delta$ enumerates the fibres of $\mathcal{E}^{r(\varepsilon)}$. In other words, we can choose a section $S : \mathcal{G}^{r(\varepsilon)}\to\mathcal{E}^{r(\varepsilon)}$ (which doesn't have to be continuous, or even measurable, just stitch together sections on bisections covering $\mathcal{G}^{r(\varepsilon)}$) we have
$$
(f*g)(\varepsilon) = \sum_{\beta\in\mathcal{G}^{r(\varepsilon)}}f(S(\beta))g(S(\beta)^{-1}\varepsilon)
$$
We also make note of the subspace $D_c\subseteq\Sigma_c(\mathcal{G}; \mathcal{E})$ consisting of those $f$ for which $\text{supp}(f)\subseteq\iota(\mathcal{G}^{(0)}\times\mathbb{T})$. This space is naturally isomorphic to $C_c(\mathcal{G}^{(0)})$, via the isomorphism taking $f\in C_c(\mathcal{G}^{(0)})$ to $\widetilde{f}\in\Sigma_c(\mathcal{G}; \mathcal{E})$ defined by $\widetilde{f}(\iota(g, z)) = zf(g)$ for any $(g, z)\in\mathcal{G}^{(0)}\times\mathbb{T}$, and otherwise $\widetilde{f}(\varepsilon) = 0$. The new function $\widetilde{f}$ is of course continuous since $\iota(\mathcal{G}^{(0)}\times\mathbb{T})$ is open, so we can write $\mathcal{E} = (\mathcal{E}\backslash\text{supp}(f))\cup\iota(\mathcal{G}^{(0)}\times\mathbb{T})$ as the union of open sets, for which $\widetilde{f}$ is continuous when restricted to either, whence allowing us to apply the pasting lemma.

**Remark**: Many of the results about $C_c(\mathcal{G})$ relied on the fact that each $f$ was the linear combination of functions supported on bisections.  We can't quite do the same thing in $\mathcal{E}$ (since it's not even étale), but $\mathcal{E}$ is "étale modulo $\mathbb{T}$", so we can do something similar with relative ease. 

Given $f\in \Sigma_c(\mathcal{G};\mathcal{E})$, we know that $\pi(\text{supp}(f))$ is compact in $\mathcal{G}$, and so we can cover $\pi(\text{supp}(f))$ in finitely many open bisections $\{U_i\}_{i=1}^n$. Choose a partition of unity $\{h_i\}_{i=1}^n$ in $C_c(\mathcal{G})$ subordinate to this open cover. Extend $h_i$ to functions $\widetilde{h}_i$ in $C_c(\mathcal{E})$ by letting $h_i(\gamma) = h_i(\pi(\gamma))$, which is clearly supported on $\pi^{-1}(U_i)$. These $\widetilde{h}_i$'s are still a partition of unity in $C_c(\mathcal{E})$, now subordinate to $\{\pi^{-1}(U_i)\}_{i=1}^n$, and $f = \sum_i f\widetilde{h}_i$ is the sum of $\mathbb{T}$-equivariant functions supported on the preimage of bisections. 

We can do the same thing with <u>trivializing</u> bisections $U_i$, with the additional nicety that when $f$ is supported on the preimage of a trivializing bisection, then we can think of $f$ as just being the "expected" $\mathbb{T}$-equivariant extension of a function supported on a bisection in $\mathcal{G}$. Suppose $f\in \Sigma_c(\mathcal{G}; \mathcal{E})$ is supported on $U\times\mathbb{T}$, $U$ a trivializing bisection. Then we can write $f(\varepsilon) = f(\gamma, z)$ where $\varepsilon\mapsto (\gamma, z)$ implements the bijection between $\pi^{-1}(U)$ and $U\times\mathbb{T}$. Then by $\mathbb{T}$-equivariance, we have $f(\gamma, z) = zf(\gamma, 1)$, and $\gamma\mapsto f(\gamma, 1)$ is a function in $C_c(\mathcal{G})$ supported on a bisection.

*Remark:* There's a nuance in the paragraph above, did you catch it? We need the homeomorphism between $\pi^{-1}(U)$ and $U\times\mathbb{T}$ to *itself*  be $\mathbb{T}$-equivariant. Fortunately if you go back to the definition of a twist and look at precisely what this homeomorphism is, you can see that it is indeed $\mathbb{T}$-equivariant.

As in the untwisted case, convolution has a nice formula for functions supported on the preimage of bisections. Given $f, g\in\Sigma_c(\mathcal{G}; \mathcal{E})$, $\text{supp}(f)\subseteq \pi^{-1}(U)$, $\text{supp}(g)\subseteq \pi^{-1}(V)$, then $\text{supp}(f*g)\subseteq \pi^{-1}(UV)$, and for any $\varepsilon = \alpha\beta\in \pi^{-1}(UV)$, $(f*g)(\varepsilon) = f(\alpha)g(\beta)$. Thus $D_c$ is a commutative *-subalgebra of $\Sigma_c(\mathcal{G}; \mathcal{E})$.









### Twisted Groupoid C*-Algebras

With these ideas in mind, many of the non-twisted results about $C_c(\mathcal{G})$ carry over to twisted counterparts in $\Sigma_c(\mathcal{G}; \mathcal{E})$, including the following:

**Theorem:** For each $f\in \Sigma_c(\mathcal{G}; \mathcal{E})$, there is a constant $K_f$ such that whenever $\pi : \Sigma_c(\mathcal{G}; \mathcal{E})\to\mathcal{B}(\mathcal{H})$ is a $*$-representation, $\|\pi(f)\|\le K_f$. Moreover, we can take $K_f = \|f\|_\infty$ when $f$ is supported on the preimage of a bisection. From this, in the same manner as before, we can construct the full <u>twisted</u> groupoid C\*-algebra $C^*(\mathcal{G}; \mathcal{E})$, from which we have an injective $*$-homomorphism $\pi_{\max} : \Sigma_c(\mathcal{G}; \mathcal{E})\to C^*(\mathcal{G}; \mathcal{E})$,  

As prior, we can show $\pi_{\max}$ is injective by looking at the *reduced* C\*-algebra.

**Definition (Equivariant Left Regular Representations, and Reduced C*-Algebra):** Let $\mathcal{E}\to\mathcal{G}$ be a twist. Given $x\in\mathcal{G}^{(0)}$, we define the space $L^2(\mathcal{G}_x; \mathcal{E}_x)$ to be the space of square-integrable functions from $\mathcal{E}_x$ to $\mathbb{C}$ which are $\mathbb{T}$-equivariant (integrable with respect to the measure $\lambda_x$). Define $\pi_x : \Sigma_c(\mathcal{G}; \mathcal{E})\to\mathcal{B}(L^2(\mathcal{G}_x;\mathcal{E}_x))$ by "extending convolution", as prior when defining the left regular representations of an ordinary groupoid: $\pi_x(f)$ is the operator taking a function $g$ to the function $\pi_x(f)g$, defined by
$$
(\pi_x(f)g)(\gamma) := \int_{\mathcal{E}_{r(\gamma)}}f(\delta)g(\delta\gamma)\text{d}\lambda_{r(\gamma)}(\delta)
$$
We then define $\oplus_x\pi_x := \bigoplus_{x\in\mathcal{G}^{(0)}}\pi_x$, which we use to define the **reduced twisted groupoid C*-algebra**, $C_r^*(\mathcal{G}; \mathcal{E})$, as merely the closure of $\oplus_x\pi_x(\Sigma_c(\mathcal{G}; \mathcal{E}))$. The representation $\oplus_x\pi_x$ is injective, and so $\Sigma_c(\mathcal{G}; \mathcal{E})$ sits inside $C_r^*(\mathcal{G}; \mathcal{E})$.

We denote by $D_r$ the completion of $D_c$ in $C_r^*(\mathcal{G}; \mathcal{E})$, and by $D$ the completion of $D_c$ in $C^*(\mathcal{G}; \mathcal{E})$.

*Remark:* As in the untwisted case, each of the three norms $\|\cdot\|_{\infty}$, $\|\cdot\|_{r}$ and $\|\cdot\|_{\max}$ *coincide* on functions which are supported on the preimage of bisections. Since $\iota(\mathcal{G}^{(0)}\times\mathbb{T}) = \pi^{-1}(\mathcal{G}^{(0)})$ is the preimage of a bisection, we see that all three norms coincide on $D_c$, and so both $D_r$ and $D$ are naturally isometrically isomorphic to $C_0(\mathcal{G}^{(0)})$.

**Example:** In the case of the trivial twist $\mathcal{G}\times\mathbb{T}$, there is an isometric $*$-isomorphism between $\Sigma_c(\mathcal{G}\times\mathbb{T})$ and $C_c(\mathcal{G})$ (preserving convolution), and so the twisted groupoid C\*-algebras coincide with the usual, untwisted groupoid C\*-algebras.









### Normalizers and Cartan Pairs

**Definition:** Let $B\subseteq A$ be C\*-algebras. The **normalizer** of $B$ in $A$, denoted $N(B)$, is defined as the set
$$
N(B) := \{n\in A\ :\ nBn^*\subseteq B,\quad n^*Bn\subseteq B\}
$$
If we restrict our attention to unitaries, we get $N(B)\cap U(A) = \{u\in U(A)\ :\ uB = Bu\}$. Notice also that $B\subseteq N(B)$, and $N(B)$ closed (topologically), and is closed under multiplication and involution: $N(B)\cap U(A)$ is a closed subgroup of $U(A)$. $B$ is said to be **regular** in $A$ if $N(B)$ generates $A$ as a C*-algebra.

**Definition:** Let $B\subseteq A$ be C*-algebras. We say $(A, B)$ is a **Cartan pair** if $B$ is a masa in $A$, $B$ is *regular* in $A$, $B$ contains an approximate identity for $A$, and there is a faithful conditional expectation $\Phi$ of $A$ onto $B$.

**Remark:** When $B$ is a masa in $A$, and $A$ is unital, then $B$ automatically contains an approximate unit for $A$ (not an obvious fact, due to Wassermann (2007)).

**Example:** Consider the C\*-algebra $A = M_n$, and the abelian subalgebra $B = D_n$ consisting of diagonal matrices. $B$ is clearly maximal in $A$, and there is a conditional expectation given by taking a matrix to it's diagonal (one can check that this is a bimodule map directly, or merely invoke Tomiyama's theorem noting that restriction to the diagonal is contractive).

It is not too hard to check that a matrix $N$ normalizes $B$ if and only if $N$ is a permutation *matrix* multiplied by a diagonal matrix, so $N(B) = \{P_\sigma D\ |\ D\in B,\ \sigma\in S_n\}$, and these matrices clearly generate $A$ as a C\*-algebra.

We remark also that $A$ coincides with the full (or reduced) group C\*-algebra of the <u>matrix groupoid</u>, $R_n$, with $B$ with the subalgebra $D$ (or $D_r$).

**Example:** Consider the <u>one-sided dimension drop algebra</u> $J_{m,n} := \{f\in C([0, 1], M_m\otimes M_n)\ |\ f(0)\in M_m\otimes 1_n\}$, and the subalgebra $C_{m,n} := \{f\in C([0, 1], D_m\otimes D_n)\ |\ f(0)\in D_m\otimes 1)\}$. Then $(J_{m, n}, C_{m, n})$ is a Cartan pair.

**Example:** Let $\mathcal{G}$ be an effective, étale groupoid and $\mathcal{E}$ a twist over $\mathcal{G}$. Then $(C_r^*(\mc G;\mc E), D_r)$ is a Cartan pair.

Indeed, there is a faithful conditional expectation $\Phi_r : C_r^*(\mathcal{G}; \mathcal{E})\to D_r$ given by extending the map which restricts functions in $\Sigma_c(\mathcal{G}; \mathcal{E})$ to the subspace $\iota(\mathcal{G}^{(0)}\times\mathbb{T})$. This map is clearly contractive and idempotent, and so by Tomiyama's theorem is also a bimodule map.

Given any other $\Psi : C_r^*(\mc G;\mc E)\to D_r$, we have $\Psi(af^2) = \Psi(faf)$ for any $a\in C_r^*(\mc G;\mc E)$, $f\in D_r$. Let $a\in\Sigma_c(\mc G;\mc E)$ have support disjoint from $\iota(\mc G^{(0)}\times\mathbb{T})$. Choose $hah = 0$, $h>0$, repeatedly until $a\sum_i h_i^2 = a$, and $h_iah_i = 0$, implying $\Psi(a) = 0$. So $\Psi$ agrees with $\Phi_r$ on $D_r$ and $D_r^\perp$, whence on $\Sigma_c(\mc G;\mc E) = D_r+D_r^\perp$.

Next let's check that $D_r$ is maximal in $C_r^*(\mc G;\mc E)$. Let $a\in C_r^*(\mc G;\mc E)\backslash D_r$, and consider the function $j(a)\in C_0(\mc G)$.

Now let's check that $D_r$ is regular in $C_r^*(\mc G;\mc E)$. Given any $n\in\Sigma_c(\mc G;\mc E)$ supported on the preimage of a bisection, $\pi^{-1}(U)$, and $h\in D_r$, we have
$$
\begin{aligned}
\supp(n^**h*n)&\subseteq\supp(n^*)\supp(h)\supp(n) \\
& \subseteq \pi^{-1}(U^{-1})\iota(\mc G^{(0)}\times\mathbb{T})\pi^{-1}(U) \\
& = \pi^{-1}(U^{-1})\pi^{-1}(U)\iota(\mc G^{(0)}\times\mathbb{T}) \\
& = \pi^{-1}(U^{-1}U)\iota(\mc G^{(0)}\times\mathbb{T}) \subseteq \iota(\mc G^{(0)}\times\mathbb{T})
\end{aligned}
$$
and so $n$ is a normalizer for $D_r$. Since $C_r^*(\mc G;\mc E)$ is generated by elements of the same form as $n$, $D_r$ is regular in $C_r^*(\mc G;\mc E)$.







### Motivating The Construction of the Weyl Groupoid

**Broad question:** given a C\*-algebra $A$ which arises from a groupoid $\mathcal{G}$, does $A$ alone contain enough information to "reconstruct" $A$?

Suppose we're given an étale groupoid $\mathcal{G}$, and we restrict our attention solely to the Cartan pair $(A, B)$ described above ($A = C_r^*(\mathcal{G}), B = D_r$). Is it possible, from this information $(A, B)$, to reconstruct our original groupoid $\mathcal{G}$? The Cartan subalgebra $B$ tells us what the <u>unit space</u> will be, since $B$ is just $C_0(\mathcal{G}^{(0)})$, so the unit space will be the <u>spectrum</u> of $B$. Does the *way* the algebra $A$ move around $B$ tell us something about how $\mathcal{G}$ moves around $\mathcal{G}^{(0)}$?











Given a Cartan pair $(A, B)$, define
$$
\begin{aligned}
\text{dom}(n) & = \overline{\{\phi\in\widehat{B}\ :\ \phi(n^*n)>0\}} \\
\text{ran}(n) & = \overline{\{\phi\in\widehat{B}\ :\ \phi(nn^*)>0\}}
\end{aligned}
$$
where $\widehat{B}$ denotes the <u>spectrum</u> of $B$ (i.e. the locally compact Hausdorff space for which $B\cong C_0(\widehat{B})$ isometrically). Clearly $\text{dom}(n^*) = \text{ran}(n)$, and also $\text{dom}(n^*n)=\text{dom}(n)$, $\text{dom}(nn^*) = \text{ran}(n)$ We will let $\text{dom}^\circ(n)$ and $\text{ran}^\circ(n)$ denote the sets above *without* the closures.

**Remark:** Let $B\subseteq A$ be C\*-algebras, and suppose $B$ contains an approximate identity for $A$. Then given  $n\in N(B)$, both $n^*n\in B$ and $nn^*\in B$.

**Proof:** $nn^* = \lim_\lambda ne_\lambda n^*$, which is clearly in $B$. $\square$ 

This observation tells us that we can consider $n^*n$ and $nn^*$ as continuous functions in $C_0(\widehat{B})$, so
$$
\begin{matrix*}[l]
\text{dom}(n) & = & \overline{\{x\in\widehat{B}\ :\ n^*n(x) > 0\}},&\quad & \ \text{ran}(n) & = & \overline{\{x\in\widehat{B}\ :\ nn^*(x) > 0\}} \\
& = & \text{supp}(n^*n) & & & = & \text{supp}(nn^*)
\end{matrix*}
$$
It's also not hard to check the following identities:
$$
\text{dom}(n^*n) = \text{ran}(n^*n) = \text{dom}(n),\qquad \text{dom}(nn^*) = \text{ran}(nn^*) = \text{ran}(n)
$$

It's also not hard to see that for $b\in B$, $\text{dom}(b) = \text{ran}(b) = \text{supp}(b)$. 



**Theorem:** Let $(A, B)$ be a Cartan pair. For any $n\in N(B)$, there is a homeomorphism $\alpha_n : \text{dom}^\circ(n)\to\text{ran}^\circ(n)$, defined by the requirement that for all $b\in B$ and $x\in \text{dom}(n)$,
$$
n^*bn(x) = b(\alpha_n(x))n^*n(x)
$$
**Proof:** Let us work in $B\subseteq A\subseteq A^{**}$, the enveloping von Neumann algebra of $A$. Given any $n\in N(B)$, we can write $n = v|n|$, where $v\in A^{**}$ is a partial isometry and $|n| = (n^*n)^{1/2}\in B$. We also require $v$ to be the *unique* isometry such that $\ker v = \ker n$ (which, if you don't like reference to the implicit Hilbert spaces, is also just the unique $v$ for which whenever $p\in A^{**}$ is a projection for which $np = 0$, then $vp = 0$).

Consider the ideal $I_n := C_0(\text{dom}^\circ n)\subseteq B$, and take $f\in I_n$. Then $\text{supp}(f)\subseteq\text{dom}^\circ n$, which is to say that whenever $f(x)$ is nonzero, $n^*n(x)$ is nonzero (for all $x\in\widehat{B}$), so $n^*n$ is *invertible* on $\text{supp}(f)$. Thus, there exists $g\in I_n$ such that $|n|g|n| = f$ (just take $g = \frac{f}{n^*n}$ defined on $\text{supp}(f)$, and set to zero elsewhere). Then $v|n|g|n|v^* = ngn^* = vfv^*$, but $ngn^*\in B$, so $vfv^*$ is also in $B$. In other words, $v$ is a normalizer.

Now consider the map $\beta_n : I_n\to B$ given by taking $f\mapsto vfv^*$. First we observe $\beta_n(f^*) = \beta_n(f)^*$, but also that $\beta_n(f)\beta_n(g) = vfv^*vgv^*$, but since $v$ is a normalizer we have $v^*v\in B$, and so it commutes with $g$, giving $\beta_n(f)\beta_n(g) = vfgv^*vv^* = vfgv^*$ (since $v$ is a partial isometry), so $\beta_n(fg) = \beta_n(f)\beta_n(g)$. So $\beta_n$ is a $*$-homomorphism.

As $v$ is a normalizer and a partial isometry, $v^*v$ is a projection in $B$, and so corresponds to the characteristic function of some compact open subset of $\widehat{B}$. How can we tell what the support of $v^*v$ is? 

Well if $E\subseteq \widehat{B}$ is some Borel set disjoint from $\text{supp}(f)$, then $\chi_E\in A^{**}$ is a projection for which $f\chi_E = 0$, whence $v\chi_E = 0$, and in turn $v^*v\chi_E = 0$. Writing $v^*v = \chi_{E_v}$ for some compact open $E_v$, we thus see that $E_v\cap E = \emptyset$ for all $E$ disjoint from $\text{supp}(f)$, and so	

Finally notice that for all $0\le f\in I_n$, $vfv^*\le \|f\|vv^*\in I_{n^*}$ (why?), and so since ideals are hereditary, $vfv^*\in I_{n^*}$. This implies $\beta_n : I_n\to I_{n^*}$.

Now, let $n^* = w|n^*|$ be the polar decomposition of $n^*$, uniquely chosen as above. It can be shown that $w = v^*$. Then
$$
\beta_{n^*}\circ\beta_n(f) = v^*(vfv^*)v = (v^*v)f(v^*v) = f(v^*v) = f
$$
Thus we have a $*$-isomorphism between $I_n$ and $I_{n^*}$, which implements a homeomorphism between their corresponding spectra, namely $\alpha_n := \widehat{\beta}_{n^*} : \text{dom}^\circ(n)\to\text{ran}^\circ(n)$. For all $f\in I_n$, by definition we have
$$
f(\alpha_n(x)) = \beta_{n^*}(f)(x) = v^*fv(x)
$$
which implies
$$
f(\alpha_n(x))n^*n(x) = |n|(x)f(\alpha_n(x))|n|(x) = |n|v^*fv|n|(x) = n^*fn(x)
$$
$\square$

It should be noted that the defining formula for $\alpha_n$ actually *uniquely identifies* $\alpha_n$, since $\alpha_n$ induces an isomorphism between $C_0(\text{ran}^\circ n)$ and $C_0(\text{dom}^\circ n)$, which coincides with $\beta_n$.

One immediate observation we can make is that for $b\in B$, $\alpha_b$ is just the identity, and so $\alpha_{n^*n}$ and $\alpha_{nn^*}$ are the identity on $\text{dom}(n)$ and $\text{ran}(n)$ respectively. Additionally, for all $m, n\in N(B)$, $\alpha_m\circ\alpha_n = \alpha_{mn}$, wherever the former is defined. To see this, first note that
$$
\begin{aligned}
(mn)^*b(mn)(x) & = b(\alpha_{mn}(x))(mn)^*(mn)(x) = b(\alpha_{mn}(x))n^*(m^*m)n(x)\\
& = b(\alpha_{mn}(x))m^*m(\alpha_n(x))n^*n(x) \\
\\
(mn)^*b(mn)(x) & = n^*(m^*bm)n(x) = m^*bm(\alpha_n(x))n^*n(x) \\
& = b(\alpha_m\circ\alpha_n(x))m^*m(\alpha_n(x))n^*n(x) \\
\end{aligned}
$$
Since this is true for all $b\in B$ and $x$ where defined, we conclude that $\alpha_{mn} = \alpha_m\circ\alpha_n$. A similar calculation yields that $\alpha_n^{-1} = \alpha_{n^*}$.

**Definition (Weyl Groupoid):** Let $(A, B)$ be a Cartan pair. Let $\mathcal{G}_{(A, B)}$ denote the **groupoid of germs** of the **pseudogroup** consisting of the $\alpha_n$'s. More explicitly, consider the set of pairs $\mc N:=\{(n, x)\ |\ n\in N(B),\ x\in\text{dom}^\circ(n)\}$, and impose an equivalence relation by requiring
$$
(m, x)\sim (n, y)\quad\iff\quad x = y,\ \text{ and }\ \exists U\ni x\ \text{ s.t. }\ \alpha_m|_U = \alpha_n|_U
$$
so that $[m, x]$ is the *germ* of $\alpha_m$ at $x$. There is a natural groupoid structure given by letting
$$
\mathcal{G}_{(A, B)}^{(0)} = \{[b, x]\ |\ b\in B,\ x\in\text{supp}^\circ(b)\} \\
s([m, x]) = [mm^*, x],\qquad r([m, x]) = [m^*m, \alpha_m(x)] \\
[m, \alpha_n(x)][n, x] = [mn, x],\qquad [n, x]^{-1}=[n^*, \alpha_n(x)]
$$
We then equip $\mathcal{G}_{(A, B)}$ with the topology generated by sets of the form $Z(n, U):=\{[n, x]\ |\ x\in U\}$, where $U$ is an open subset of $\text{dom}^\circ(n)$. With this topology, $\mathcal{G}_{(A, B)}$ becomes a locally compact, Hausdorff, <u>effective</u> étale groupoid, and in this topology $Z(n, U)$ are open bisections. We also remark that there is a natural identification of $\mc G_{(A, B)}^{(0)}$ with $\widehat{B}$, given by taking $[b, x]\mapsto x$: indeed, given any two $b, b'\in B$ with $x\in\supp^\circ(b)\cap\supp^\circ(b')$, clearly $\alpha_b$ and $\alpha_{b'}$ on an open neighbourhood of $x$, since they're both the identity map.

**Proof:** We'll show that under this topology, $\mathcal{G}_{(A, B)}$ is effective. The rest we leave as an exercise.

First, we remark that
$$
\text{Iso}(\mathcal{G}_{(A, B)}) = \{[n, x]\ |\ x\in\text{dom}^\circ(n)\cap\text{ran}^\circ(n),\ \alpha_n(x) = x\}
$$
Suppose we have $[n, x]\not\in \mathcal{G}_{(A, B)}^{(0)}$. This means for all $b\in B$, and all open $U\subseteq\widehat{B}$ containing $x$, $\alpha_n|_U\neq \alpha_b|_U$, but of course $\alpha_b = \text{id}_{\text{supp(b)}}$, so this is just saying $\alpha_n|_U\neq \text{id}_U$. In other words, for all open $U$ we can find $y\in U$ such that $\alpha_n(y)\neq y$.

Now consider the open set $Z(n, U)\ni [n, x]$. If we can show that there is some $[n, y]\in Z(n, U)\backslash\text{Iso}(\mathcal{G}_{(A, B)})$, then we'll have shown that $[n, x]\not\in\text{Iso}(\mathcal{G}_{(A, B)})^\circ$, implying $\mathcal{G}_{(A, B)}$ is effective. As we just noted, no matter what our open neighbourhood $U$ is, there exists $y\in U$ such that $\alpha_n(y)\neq y$, so $[n, y]\in Z(n, U)$, but $[n, y]$ cannot be in the isotropy groupoid by the above characterization, thus proving the result. $\square$

**Theorem:** Let $\mathcal{E}\to\mathcal{G}$ be a twisted groupoid, and consider the Cartan pair $(A, B) = (C_r^*(\mathcal{G}; \mathcal{E}), D_r)$. Then there is an isomorphism $\theta : \mathcal{G}\to\mathcal{G}_{(A, B)}$.

**Proof:** Let $n\in \Sigma_c(\mathcal{G}; \mathcal{E})$, and $h\in D_r\cong C_0(\mc G^{(0)})$. One can then calculate that
$$
(n^**h*n)(\gamma) = \sum_{\alpha\beta = \gamma}n^*(\alpha)n(\beta)h(r(\beta))
$$
which is a little messy. If we assume $n$ is supported on $\pi^{-1}(U)$ for some bisection $U\subseteq\mc G$ (which we recall is enough to guarantee $n^**h*n\in D_r$), then for any $\gamma\in \pi^{-1}(U)$, 
$$
(n^**h*n)(s(\gamma)) =  h(r(\gamma))n^*n(\gamma),\qquad \forall h\in D_r
$$
Doesn't that look awfully familiar? This is the defining formula for the homeomorphism $\alpha_n$. In other words, we've just shown that
$$
\alpha_n(s(\gamma)) = r(\gamma),\qquad \gamma\in \pi^{-1}(U)
$$
So all along, the $\alpha_n$'s have been encoding precisely what we need: a way for $A$ to explain how units, the elements of $\widehat{B}$, get moved around in our groupoid.

We define $\theta$ as follows: given $\gamma\in\mc G$, choose an open bisection $U\ni \pi(\gamma)$, and an $n\in\Sigma_c(\mc G; \mc E)$ supported on $\pi^{-1}(U)$. Then we set
$$
\theta(\gamma) := [n, s(\gamma)]
$$
Is $\theta$ well-defined? Well let's say we choose open bisections $U, V$ in $\mc G$ containing $\pi(\gamma)$, and $m, n\in\Sigma_c(\mc G; \mc E)$ supported on $\pi^{-1}(U)$, $\pi^{-1}(V)$ respectively. Then for all $h\in D_r$ and $\delta\in \pi^{-1}(U\cap V)$,
$$
m^*hm(s(\delta))\quad =\quad h(r(\delta))m^*m(\delta) \\
n^*hn(s(\delta))\quad =\quad h(r(\delta))n^*n(\delta)
$$
and so $\alpha_m|_{s(\pi^{-1}(U\cap V))} = \alpha_n|_{s(\pi^{-1}(U\cap V))}$. Checking that $\theta$ is in fact a groupoid homomorphism is relatively straightforward.

Is $\theta$ bijective?

Is $\theta$ continuous?

Is $\theta$ an open map?

$\square$



**Definition and Theorem:** Let $(A, B)$ be a Cartan pair. We can impose a *different* equivalence relation on $\mc N=\{(n, x)\ |\ n\in N(B),\ x\in\text{dom}(n)\}$ by requiring
$$
(m, x)\approx (n, y)\quad\iff\quad x = y,\ \text{ and }\ \exists b, b'\in B\ \text{ s.t. }\ b(x), b'(x)>0,\ mb=nb'
$$
Then $\mc E_{(A, B)}:=\mc N/\approx$ is a groupoid, with precisely the same units, source, range, multiplication and inversion as defined for $\mc N/\sim\ = \mc G_{(A, B)}$. We let $\llbracket m, x\rrbracket$ denote the equivalence classes under this new relation. We equip $\mc E_{(A, B)}$ with the topology generated by the sets $\widetilde{Z}(n, U) := \{\llbracket n, x\rrbracket\ |\ x\in U\}$. Then $\mc E_{(A, B)}$ becomes a locally compact Hausdorff groupoid, and the sets $\widetilde{Z}(n, U)$ are open bisections.

**Proof:** Before showing that $\mc E_{(A, B)}$ is a groupoid, let's make an observation: if $\llbracket m, x\rrbracket = \llbracket n, x\rrbracket$, then $[m, x] = [n, x]$. This is because if $mb = m'b'$, then $\alpha_m = \alpha_m\circ\alpha_b = \alpha_{mb} = \alpha_{m'b'} = \alpha_{m'}\circ\alpha_{b'}=\alpha_{m'}$, wherever they're defined (which is easily seen to be on some open set containing $x$). This tells us there's a well-defined surjective map $\pi_{(A, B)} : \mc E_{(A, B)}\to\mc G_{(A, B)}$, taking $\llbracket n, x\rrbracket\mapsto[n, x]$. Once we check that $\mc E_{(A, B)}$ is a groupoid, it will be clear by definition that $\pi_{(A, B)}$ is a continuous, open, groupoid homomorphism.

Showing that the source and range are well-defined is straightforward. To check that multiplication is well-defined, assume $\llbracket n, x\rrbracket = \llbracket n', x\rrbracket$ and $\llbracket m, \alpha_n(x)\rrbracket = \llbracket m', \alpha_{n'}(x)\rrbracket$ (which is possible since $\alpha_n$ and $\alpha_{n'}$ agree on an open neighbourhood of $x$). Choose $b, b'$ such that $b(\alpha_n(x)), b'(\alpha_{n'}(x))>0$ and $mb = m'b'$, and similarly $c, c'$ such that $c(x), c'(x)>0$ and $nc = n'c'$. Then
$$
\begin{aligned}
mn(cn^*bn) & = m(nn^*)bnc = mb(nn^*)nc = m'b'(nn^*)nc \\
& = m'(nn^*)b'nc = m'n(n^*b'n)c = m'(nc)(n^*b'n) \\
& = m'(n'c')(n^*b'n) = m'n'(c'n^*b'n)
\end{aligned}
$$
and so $\llbracket mn, x\rrbracket = \llbracket m'n', x\rrbracket$.

The rest follows fairly easily. $\square$

**Theorem:** Let $(A, B)$ be a Cartan pair. Then $\mc E_{(A, B)}\to\mc G_{(A, B)}$ is a twist.

Precisely speaking, let $B = C_0(\widehat{B})$, and let $\iota_{(A, B)} : \widehat{B}\times\mathbb{T}\to\mc E_{(A, B)}$ denote the map $(x, z)\mapsto \llbracket b, x\rrbracket$, where $b\in B$ is any choice for which $b(x) = z$. Let $\pi_{(A, B)} : \mc E_{(A, B)}\to \mc G_{(A, B)}$ denote the map taking $\llbracket n, x\rrbracket\mapsto [n, x]$. Then the following sequence is a twist:
$$
\widehat{B}\times\mathbb{T}\xrightarrow{\ \iota_{(A,B)}\ }\mc E_{(A, B)}\xrightarrow{\ \pi_{(A,B)}\ }\mc G_{(A, B)}
$$
**Proof:** We've already seen that the map $\pi_{(A, B)}$ is a continuous, open, surjective groupoid homomorphism. Let's check $\iota_{(A, B)}$.

I personally find it easier to look at the inverse of $\iota_{(A, B)}$ on it's range. That is, we can define an identification of $\mc E_{(A, B)}^{(0)} = \{\llbracket b, x\rrbracket\ |\ b\in B,\ b(x)\neq 0\}$ with $\widehat{B}\times\mathbb{T}$, given by taking $\llbracket b, x\rrbracket\mapsto \left(x, b(x)/|b(x)|\right)$. It's not hard to see that this map is well-defined, and clearly surjective. If $b, b'$ are two functions in $B$ which are nonzero at a point $x$, then there is a neighbourhood $U$ of $x$ on which both $b$ and $b'$ are nonzero. Choose some function $h\in B$ such that $\text{supp}(h)\subseteq B$. Then
$$
bh = b'\left(\frac{b}{b'}h\right) = b'h'
$$
implying $\llbracket b, x\rrbracket = \llbracket b', x\rrbracket$, so this association of a subset of $\mc E_{(A, B)}$ with $\widehat{B}\times\mathbb{T}$ is bijective. Checking that $\iota_{(A, B)}$ is a continuous groupoid homomorphism is a routine task.





**Theorem:** Let $\mc E\to\mc G$ be a twist, and let $(A, B) = (C_r^*(\mc G;\mc E),\ D_r)$. Then there is an isomorphism $\zeta : \mc E\to \mc E_{(A, B)}$. Moreover, along with the isomorphism $\theta : \mc G\to\mc G_{(A, B)}$, the following diagram commutes, implying we have an isomorphism of twists.

<img src="C:\Users\Michael\AppData\Roaming\Typora\typora-user-images\image-20221111151552823.png" alt="image-20221111151552823" style="zoom:50%;" />

**Proof:**



**Theorem:** The map taking a twist $\mc E\to\mc G$ to the Cartan pair $(C_r^*(\mc G;\mc E), D_r)$ induces a *bijection* between isomorphism classes of twists and isomorphism classes of Cartan pairs. In other words, Cartan pairs *always arise from twisted groupoids*.

**Proof:**

Given a Cartan pair $(A, B)$, we'd like to show that $A\cong C_r^*(\mc G_{(A, B)}; \mc E_{(A, B)})$ and $B\cong D_r$.