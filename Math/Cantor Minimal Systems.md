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
