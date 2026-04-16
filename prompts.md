# Spaced Repetition Prompts

This file contains the exact prompts to embed after each section of the blog post. Place an `<orbit-reviewarea>` (or equivalent fallback component) at the end of the corresponding section, containing exactly the prompts listed below. Do not add, remove, or reword prompts.

Prompts may contain LaTeX math notation. Render it appropriately (e.g., with KaTeX) in both the question and answer fields.

---

## After Section 1: The Lattice

**Prompt 1.1**
- Q: In the toric code on an $L \times L$ lattice, where are the qubits placed?
- A: On the edges of the lattice. There are $2L^2$ qubits total ($L^2$ horizontal edges and $L^2$ vertical edges).

**Prompt 1.2**
- Q: What are the two types of stabilizers in the toric code?
- A: X-type (plaquette) stabilizers, which apply $X$ to the four edges bounding a face, and Z-type (vertex) stabilizers, which apply $Z$ to the four edges incident to a vertex.

**Prompt 1.3**
- Q: On the torus, how many faces does each edge border?
- A: Exactly two, because of the periodic boundary conditions. (No edge is on a "boundary" of the lattice.)

---

## After Section 2: The Chain Complex over $\mathbb{F}_2$

**Prompt 2.1**
- Q: What does the boundary map $\partial_2$ do to a single face $F(x,y)$?
- A: It returns the sum (over $\mathbb{F}_2$) of the four edges bounding that face: $H(x,y) + H(x,y+1) + V(x,y) + V(x+1,y)$.

**Prompt 2.2**
- Q: For a set of faces $\mathcal{F}$, when is an edge $e$ in $\partial_2(\mathcal{F})$?
- A: When exactly one of the two faces bordering $e$ is in $\mathcal{F}$.

**Prompt 2.3**
- Q: What does the property $\partial_1 \circ \partial_2 = 0$ mean geometrically?
- A: The boundary of a boundary is empty — the perimeter of any set of faces has no dangling endpoints (every vertex appears an even number of times).

---

## After Section 3: Cycles, Boundaries, and Homology

**Prompt 3.1**
- Q: What is a 1-cycle?
- A: An edge-set where every vertex has even degree — 0, 2, or 4 edges of the set meet at each vertex.

**Prompt 3.2**
- Q: What is a 1-boundary?
- A: An edge-set that equals $\partial_2(\mathcal{F})$ for some set of faces $\mathcal{F}$ — the perimeter of a set of faces.

**Prompt 3.3**
- Q: Why is every boundary automatically a cycle?
- A: Because $\partial_1 \circ \partial_2 = 0$: applying $\partial_1$ to any boundary gives 0, meaning every vertex has even degree.

**Prompt 3.4**
- Q: When are two cycles $c$ and $c'$ homologous?
- A: When they differ by a boundary: $c + c' \in B_1$. Equivalently, they represent the same element of $H_1 = Z_1 / B_1$.

---

## After Section 4: Connection to the Toric Code

**Prompt 4.1**
- Q: An X-type operator on edge-set $c$ commutes with all Z-type stabilizers if and only if $c$ satisfies what condition?
- A: $c$ is a cycle — every vertex has even degree in $c$.

**Prompt 4.2**
- Q: A non-trivial X-type logical operator corresponds to what kind of cycle?
- A: A cycle that is not a boundary — a non-trivial element of $H_1 = Z_1 / B_1$.

**Prompt 4.3**
- Q: What is the dual lattice of the $L \times L$ torus, and why is it useful?
- A: It places a vertex at the center of each primal face, connects them by dual edges (one per primal edge), and turns primal vertices into dual faces. Z-type logicals on the primal lattice correspond to cycles on the dual lattice, so we can reuse the same homological framework for both X-type and Z-type distance.

---

## After Section 5: Dimension of $H_1$

**Prompt 5.1**
- Q: What is $\dim(H_1)$ for the $L \times L$ torus over $\mathbb{F}_2$?
- A: 2. This means the toric code encodes 2 logical qubits and $H_1$ has $2^2 = 4$ cosets.

**Prompt 5.2**
- Q: In the computation of $\dim(Z_1)$, why do we analyze the transpose $\partial_1^T$ instead of $\partial_1$ directly?
- A: Because $\ker(\partial_1^T)$ is easy to characterize: it consists of vertex-labelings where adjacent vertices always agree, which forces the labeling to be constant (by connectedness). This gives $\dim(\ker(\partial_1^T)) = 1$, so $\operatorname{rank}(\partial_1) = L^2 - 1$.

**Prompt 5.3**
- Q: Why is $\dim(\ker(\partial_2)) = 1$?
- A: A face-set $\mathcal{F}$ is in $\ker(\partial_2)$ iff every edge borders an even number of faces in $\mathcal{F}$. Since each edge borders exactly two faces, adjacent faces must have the same membership. Connectedness forces $\mathcal{F}$ to be either empty or all faces.

---

## After Section 6: The Invariants $h$ and $v$

**Prompt 6.1**
- Q: What does $h(c)$ measure?
- A: The parity (mod 2) of the number of horizontal edges of $c$ at any fixed $x$-coordinate.

**Prompt 6.2**
- Q: Why is $h(c)$ the same at every $x$-coordinate (for a cycle $c$)?
- A: Summing the even-degree condition over a column of vertices at $x = x_0 + 1$: the two vertical edge sums cancel (they run over the same set mod $L$), leaving $h_{x_0}(c) + h_{x_0+1}(c) \equiv 0$.

**Prompt 6.3**
- Q: What are $h(b)$ and $v(b)$ for any boundary $b$?
- A: Both are 0. This is why $\varphi([c]) = (h(c), v(c))$ is well-defined on homology classes: adding a boundary doesn't change $h$ or $v$.

---

## After Section 7: The Isomorphism $H_1 \cong \mathbb{F}_2^2$

**Prompt 7.1**
- Q: What are the four cosets of $H_1$, and what $(h, v)$ values do they have?
- A: $(0,0)$: boundaries (trivial). $(1,0)$: horizontal loops. $(0,1)$: vertical loops. $(1,1)$: both.

**Prompt 7.2**
- Q: How do we know the horizontal loop $c_h$ is not a boundary?
- A: $h(c_h) = 1$, but every boundary has $h = 0$ (Lemma 6.3). So $c_h$ cannot be a boundary.

**Prompt 7.3**
- Q: Why does surjectivity of $\varphi: H_1 \to \mathbb{F}_2^2$ imply that $\varphi$ is an isomorphism?
- A: $\varphi$ is a linear map between vector spaces of the same dimension (both 2). A surjective linear map between equal-dimensional spaces is automatically injective.

---

## After Section 8: The Distance Theorem

**Prompt 8.1**
- Q: What is the upper bound argument for $d_X \leq L$?
- A: The horizontal loop $c_h$ has exactly $L$ edges and is a non-trivial cycle (since $h(c_h) = 1 \neq 0$). So $d_X \leq L$.

**Prompt 8.2**
- Q: Why does $h(c) = 1$ imply that $|c| \geq L$?
- A: $h(c) = 1$ means $c$ has an odd number of horizontal edges at each of the $L$ distinct $x$-coordinates. Odd $\geq 1$, and these $L$ sets are pairwise disjoint, so $|c| \geq L$.

**Prompt 8.3**
- Q: Why does $d = \min(d_X, d_Z)$ hold for a CSS code?
- A: Any non-trivial logical $P = X^a Z^b$ has at least one non-trivial part ($a$ or $b$). Its weight $|\operatorname{supp}(a) \cup \operatorname{supp}(b)| \geq \max(|a|, |b|)$, which is $\geq d_X$ or $\geq d_Z$. So every non-trivial logical has weight $\geq \min(d_X, d_Z)$.
