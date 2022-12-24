# A Note on the Gelfand Transform

$$
\newcommand{\ev}{\operatorname{ev}}
$$



Let $A$ be a commutative C\*-algebra. Then the Gelfand transform $\Gamma_A : A\to C_0(\widehat{A})$ is a $*$-isomorphism.

A continuous map $\Phi : X\to Y$ between locally compact Hausdorff spaces induces a $*$-homomorphism $\widetilde{\Phi} : C_0(Y)\to C_0(X)$ given by taking $f\mapsto f\circ\Phi$.

Suppose we have a $*$-homomorphism $\Psi : A\to B$ of commutative C\*-algebras. This induces a homomorphism of their *spectra*, $\widehat{\Psi} : \widehat{B}\to\widehat{A}$, given by taking $\varphi\in\widehat{B}$ to $\varphi\circ\Phi\in\widehat{A}$.

Now suppose we replace $A, B$ by $C_0(X)$ and  $C_0(Y)$. We'd like the induced map $\widehat{\Psi}$ to be a map between $Y$ and $X$, rather than the "unwieldy" expression
$$
\widehat{\Psi} : \widehat{C_0(Y)}\to \widehat{C_0(X)}
$$
This requires us to analyze the relationship between $X$ and $\widehat{C_0(X)}$, which is sort of the "inverse dual" of the Gelfand transform. In other words, what is the inverse of the operation $\Phi\mapsto\widetilde{\Phi}$?

Given $\varphi\in \widehat{C_0(X)}$, there exists a unique $x\in X$ such that $\varphi = \ev_x$, where $\ev_x(f) = f(x)$. Let $\Delta_X : X\to \widehat{C_0(X)}$ take $x\mapsto \text{ev}_x$ (which is clearly continuous with respect to the weak-* topology on the codomain). Then
$$
\Gamma_{C_0(X)} = \widetilde{\Delta_X^{-1}}
$$
Assuming then we have a map $\Psi : C_0(X)\to C_0(Y)$, the induced spectral map is
$$
\Sigma_\Psi := \Delta_X^{-1}\circ\widehat{\Psi}\circ\Delta_Y : Y\to X
$$
What exactly is this map doing? Given $y\in Y$, $\Sigma_\Psi(y)$ computes the unique value $x\in X$ such that $\ev_x = \ev_y\circ\Psi$. In other words,
$$
f(\Sigma_\Psi(y)) = \Psi(f)(y)
$$
**Example:** This example comes from Kumjian-Renault theory. Let $(A, B)$ be a Cartan pair (of C\*-algebras), and $n\in N(B)$ a normalizer. Consider $B\subseteq A\subseteq A^{**}$, and let $n = v|n|$ be the unique polar decomposition of $n$ such that $\ker n = \ker v$ (after embedding isometrically in $\mathcal{B}(\mathcal{H})$, or via an equivalent purely algebraic description). One can show that $f\mapsto v^*fv$ implements an isomorphism $\beta_n$ between $C_0(\text{supp}^\circ(nn^*))$ and $C_0(\text{supp}^\circ(n^*n))$.

Let $\alpha_n := \Sigma_{\beta_n} : \text{supp}^\circ(nn^*)\to\text{supp}^\circ(n^*n)$. Then $\alpha_n$ is a homeomorphism such that
$$
f(\alpha_n(x)) = vfv^*(x),\qquad\forall x\in\text{supp}^\circ(n^*n)
$$
and so
$$
f(\alpha_n(x))n^*n(x) =|n|(x)f(\alpha_n(x))|n|(x) = |n|v^*fv|n|(x) = n^*fn(x)
$$

