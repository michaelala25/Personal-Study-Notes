# Crossed Products of C*-Algebras

These are notes taken following along with Brown & Ozawa's book, Chapter 4, Section 1.

**Definition:** An <u>action</u> of a (discrete) group $G$ on a C\*-algebra $A$ is a <u>group homomorphism</u> $\alpha : G\to\text{Aut}(A)$. A C\*-algebra $A$ equipped with a $G$-action is called a <u>$G$-C\*-algebra</u>.

Henceforth, we will assume $G$ is discrete, although it appears a similar construction is available for locally compact groups too.

Given a $G$-C\*-algebra for, we define $C_c(G, A)$ to be the space of compactly supported continuous functions from $G$ to $A$. Of course,  since $G$ is discrete any such function will be supported on a *finite* set, and is associated to an element of $A[G]$ (the group algebra). In other words, we can write elements of $C_c(G, A)$ as formal sums $\sum_{g\in G}a_g g$, where $a_g\in A$, and $a_g = 0$ for all but finitely many $g$.

We'd like to define some sort of convolution product on $C_c(G, A)$. 