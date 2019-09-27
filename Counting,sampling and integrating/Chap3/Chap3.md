##  Exercise 3.5

Let $C(G)$ be the set  of $q$-colorings of graph $G$. For the proof of this problem, we let $G_i$ be the graph obtained from $G_i$ by deleting the vertex $v_i$. Still we let $\varrho_{i}=\frac{C(G_{i-1})}{C(G_i)}$. Then one can establish a bound for $\varrho_i$ similar to $(3.5)$:

$$\frac{1}{q}\leq \varrho_i\leq 1$$

Therefore, a result analogous to Proposition 3.4 can be proved. The detailed proof is omitted here.

## Exercise 3.10

For every two states $x$ and $y$ reachable from each other(that is, the matching represented by $x$ and $y$ differs by exactly one edge.), then it's clear that $P(x,y)=P(y,x)$. Since this MC is clearly irreducible, then according to Lemma 3.7, the stationary distribution of the MC of Example 3.9 is uniform over $M(G)$.