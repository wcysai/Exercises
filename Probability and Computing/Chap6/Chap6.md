## Exercise 6.1

(a) Assign each variable with True or False uniformly and independently at random. Let $X$ be the random variable denoting number of satisfied clauses. Since there are $m$ clauses and each is satisfied with probability $1-2^{-k}$, there's $\mathbb{E}[X]=m(1-2^{-k})$, which implies there exists an assignment that satisfies at least $m(1-2^{-k})$ of the clauses.

To establish a lower bound for the probability of the algorithm returning an assignment that satisfies at least $m(1-2^{-k})$ clauses, we let $p=Pr\big(X\geq m(1-2^{-k})\big)$, and observe that $X\leq m$. Therefore,

$$ m(1-2^{-k})=\mathbb{E}[X]$$

$$=\sum\limits_{i<m(1-2^{-k})}Pr(X=i)i+\sum\limits_{i\geq m(1-2^{-k})}Pr(X=i)i$$
$$\leq (1-p)(m(1-2^{-k})-1)+pm$$

which implies that $p\geq \frac{1}{1+m2^{-k}}$. Therefore the expected number of trials before finding a valid answer is $1+m2^{-k}$. Since each trial takes $O(mk)$ time. The expected running time of the Las Vegas algorithm is $O(mk+m^{2}k2^{-k})$.



(b) Similar to the method used for derandomization of the algorithm of finding a large cut, We assign values to each variable deterministically, one at a time, in an arbitrary order $v_1,v_2,\dots,v_n$ , letting $x_i$ be the truth value of $v_i$ and show inductively that $\mathbb{E}[X\vert x_1,x_2,\dots, x_k]\leq \mathbb{E}[X\vert x_1,x_2,\dots, x_{k+1}]$.

The base case of the induction is trivial. Now consider assigning $v_{k+1}$ randomly,then $\mathbb{E}[X\vert x_1,x_2,\dots, x_{k+1}]=\frac{1}{2}\mathbb{E}[X\vert x_1,x_2,\dots, x_{k+1}=\text{True}]+\frac{1}{2}\mathbb{E}[X\vert x_1,x_2,\dots, x_{k+1}=\text{False}]$. It follows that $\max(\mathbb{E}[X\vert x_1,x_2,\dots, x_{k+1}=\text{True}],\mathbb{E}[X\vert x_1,x_2,\dots, x_{k+1}=\text{False}])\geq \mathbb{E}[X\vert x_1,x_2,\dots, x_{k}]$

, therefore we only need to compute both two values, and take the maximum, which should yield an assignment satisfying at least $m(1-2^{-k})$ clauses.

## Exercise 6.2

(a) Color all edges with either of the two colors uniformly and independently at random. Let $X$ be the random variable denoting the number of monochromatic copies of $K_4$. Since for each clique of size $4$, the probability that it's colored mono-chromatically is $2^{-5}$, and there are $\binom{n}{4}$ such cliques, thus $\mathbb{E}[X]=\binom{n}{4}2^{-5}$. Thus by the expectation argument, there exists a coloring of the edges of the complete graph $K_n$ by two colors so that the total number of monochromatic copies of $K_4$ is at most $\binom{n}{4}2^{-5}$.



(b)  Still, we color all edges with either of the two colors uniformly and independently at random. Let $p=Pr(X\leq \binom{n}{4}2^{-5})$. Therefore,

$$\binom{n}{4}2^{-5}=\mathbb{E}[X]$$

$$=\sum\limits_{i\leq \binom{n}{4}2^{-5}}Pr(X=i)i+\sum\limits_{i>\binom{n}{4}2^{-5}}Pr(X=i)i$$

$$\geq p\cdot 0+(1-p)(\binom{n}{4}2^{-5}+1)$$

which implies that $p\geq \frac{1}{\binom{n}{4}2^{-5}+1}$. Thus the expected number of trials to find a valid coloring is at most $\binom{n}{4}2^{-5}+1$. We then have a Las Vegas algorithm that runs in expected time polynomial in $n$.



(c) We color each edge deterministically, one at a time, in an arbitrary order $e_1,e_2,\dots,e_n$ , letting $x_i$ be the color of $e_i$ and show inductively that $\mathbb{E}[X\vert x_1,x_2,\dots, x_k]\leq \mathbb{E}[X\vert x_1,x_2,\dots, x_{k+1}]$.

The base case of the induction is trivial. Now consider assigning $v_{k+1}$ randomly,then $\mathbb{E}[X\vert x_1,x_2,\dots, x_{k+1}]=\frac{1}{2}\mathbb{E}[X\vert x_1,x_2,\dots, x_{k+1}=\text{black}]+\frac{1}{2}\mathbb{E}[X\vert x_1,x_2,\dots, x_{k+1}=\text{white}]$. It follows that $\max(\mathbb{E}[X\vert x_1,x_2,\dots, x_{k+1}=\text{True}],\mathbb{E}[X\vert x_1,x_2,\dots, x_{k+1}=\text{black}])\geq \mathbb{E}[X\vert x_1,x_2,\dots, x_{k}]$

, therefore we only need to compute both two values, and take the maximum, which should yield a coloring so that the total number of monochromatic copies of $K_4$ is at most $\binom{n}{4}2^{-5}$.

## Exercise 6.3

(a) Suppose for the sake of contradiction that there exists a subset $S(\sigma)$ which isn't an independent set in $G$. It follows that there exists two vertices $i,j\in S(\sigma)$ such that $i,j$ are neighbors in $ G$. Assume without loss of generality that $i$ precedes $j$ in the permutation $\sigma$, which leads to a contradiction for vertex $j$. Therefore each $S(\sigma)$ is an independent set in $G$.



(b) The algorithm is to generate the permutation uniformly at random, that is, each permutation of order $n$ appears with probability $\frac{1}{n!}$. Then for each vertex $i$, $i\in S(\sigma)$ means that $i$ comes first in the vertex set containing both $i$ and all its neighbors in $G$, with happens with probability $\frac{1}{d_i+1}$, where $d_i$ denotes the degree of vertex $i$. Let $X$ be the random variable denoting the cardinality of $S(\sigma)$ and $X_i=\begin{cases} 1 & i\in S(\sigma)\\ 0& i \notin S(\sigma)\end{cases}$ . Then the expected cardinality of $S(\sigma)$ is $\mathbb{E}[X]=\sum\limits_{i=1}^{n}\mathbb{E}[X_i]=\sum\limits_{i=1}^{n}\frac{1}{d_i+1}$.



(c) To prove that $G$ has an independent set of size at least $\sum\limits_{i=1}^{n}\frac{1}{d_i+1}$, one only has to show that the independent set of $G$ has an one-to-one relation with $S(\sigma)$. It is already shown in (a) that $S(\sigma)$ is an independent set in $G$. For each independent set $I=\{v_1,v_2,\dots,v_k\}$ of $G$ where the vertices are sorted by their labels in an increasing order, we need to show that there always exists an $S(\sigma)$ that corresponds to this set. To do this, we can construct a permutation $\sigma=(v_1,v_2,\dots,v_k,u_1,u_2,\dots, u_{n-k})$  where the $u_1,u_2,\dots,u_{n-k}$ are vertices of $V \setminus I$ , in arbitrary order. One can see that $S(\sigma)$ correctly corresponds to $I$, which finishes the proof.

## Exercise 6.4

(a) Winning strategy: Each time chooses the set with the larger cardinality. Thus each time the cardinality of the size is at least half as that of the original set. When $k\geq 2^n$, the game consists of at most $\lfloor \log_{2}{k}\rfloor\geq n$ rounds, which is already enough for the choose to finish with a token reaching $n$.

(b)  One strategy for the remover is each time to choose one of the two sets uniformly at random. In this way, we can consider that each number is removed with probability $\frac{1}{2}$. Then for a certain number $i$, the probability that $i$ isn't removed after $n$ rounds is $\frac{1}{2^n}$. Let $X$ be the random variable denoting the number of remaining number after $n$ rounds, and $X_i=\begin{cases} 1 & i\text{ remains after $n$ rounds}\\ 0& i\text{ is removed after $n$ rounds}\end{cases}$ Therefore the expected number of remaining numbers after $n$ rounds is $\mathbb{E}[X]=\sum\limits_{i=1}^{k}\mathbb{E}[X_i]=\frac{k}{2^n}<1$. Since $X$ can only take integer values, there must exists a case with nonzero probability where $X=0$. It follows that there must exist a winning strategy for the remover when $k<2^n$.



(c) We choose sets deterministically, one at a time, in an arbitrary order $v_1,v_2,\dots,v_n$ , letting $x_i$ be the chosen set $v_i$ and show inductively that $\mathbb{E}[X\vert x_1,x_2,\dots, x_k]\leq \mathbb{E}[X\vert x_1,x_2,\dots, x_{k+1}]$.

The base case of the induction is trivial. Now consider assigning $v_{k+1}$ randomly,then $\mathbb{E}[X\vert x_1,x_2,\dots, x_{k+1}]=\frac{1}{2}\mathbb{E}[X\vert x_1,x_2,\dots, x_{k+1}=A]+\frac{1}{2}\mathbb{E}[X\vert x_1,x_2,\dots, x_{k+1}=B]$. It follows that $\max(\mathbb{E}[X\vert x_1,x_2,\dots, x_{k+1}=A],\mathbb{E}[X\vert x_1,x_2,\dots, x_{k+1}=B])\geq \mathbb{E}[X\vert x_1,x_2,\dots, x_{k}]$

, therefore we only need to compute both two values, and take the maximum, which should yield an winning strategy for the remover.

## Exercise 6.5

Let's prove this result inductively. Cases when $m=0$ is trivial, so from now on we only consider cases when $m>1$. For cases when $n=1$ and $n=2$, it is clear that the result holds. For $n\geq 3$. We choose a pair of vertices $(u,v)$ such that $(u,v)\in E$. Recall the strategy used in the derandomization part of finding a large cut. When a vertex has an odd number of neighbors that is already determined, we can have a $\frac{1}{2}$ bonus in the conditional expectation. Here by choosing to determine $u$ before $v$, or determining $v$ before $u$, we can guarantee this bonus. Let $E'$ be the set of edges containing neither $u$ nor $v$ as an endpoint and $\vert E'\vert =m'$ . By induction there exists a partition for the vertices other than $u$ and $v$ such that at least $\frac{m'(n-2)}{2n-3}$ edges cross the partition. By the above argument we can obtain at least $\frac{m-m'}{2}+1$ edges cross the partition for the newly-added $m-m'$ edges. Therefore  exists a partition for the $n$ vertices such that at least $\frac{m'(n-2)}{2n-3}+\frac{m-m'}{2}+1 $ edges cross the partition. In order to finish the proof, we need to show that $\frac{m'(n-2)}{2n-3}+\frac{m-m'}{2}+1\geq \frac{nm}{2n-1}=\frac{m}{2}+\frac{m}{4n-2}$ . Since $\frac{m'(n-2)}{2n-3}+\frac{m-m'}{2}+1 =\frac{m'}{4n-6}+\frac{m}{2}+1$, we only need to prove that $\frac{m'}{4n-6}+1\geq \frac{m}{4n-2}$, which is true under the fact that $m-m'\leq 2n-3$ and $m\leq \binom{n}{2}$(the detail is omitted here). Therefore we have proved that there exists a partition such that at least $\frac{mn}{2n-1}$ edges cross the partition.

## Exercise 6.6

Assign each vertex with one of the two sets uniformly and independently at random. Let $X$ be the random variable denoting the sum of weights over edges connecting vertices in different sets, and $X_i=\begin{cases} 1 & e_i\text{ connects two vertices in different sets}\\ 0& e_i\text{ connects two vertices in the same set}\end{cases}$. Then the expected value of a cut is $\mathbb{E}[X]=\sum\limits_{i=1}^{m}\mathbb{E}[X_i]=\frac{m}{2}$. 

For the generalized case of $k$-cut, also assign each vertex with one of the two sets uniformly and independently at random. Let $X$ be the random variable denoting the sum of weights over edges connecting vertices in different sets, and $X_i=\begin{cases} 1 & e_i\text{ connects two vertices in different sets}\\ 0& e_i\text{ connects two vertices in the same set}\end{cases}$. Then the expected value of a cut is $\mathbb{E}[X]=\sum\limits_{i=1}^{m}\mathbb{E}[X_i]=\frac{km}{k-1}$. since the probability that $e_i$ connects two vertices in different sets is $\frac{k-1}{k}$.

For derandomization, We choose set of each vertex deterministically, one at a time, in an arbitrary order $v_1,v_2,\dots,v_n$ , letting $x_i$ be the set of $v_i$ and show inductively that $\mathbb{E}[X\vert x_1,x_2,\dots, x_k]\leq \mathbb{E}[X\vert x_1,x_2,\dots, x_{k+1}]$.

The base case of the induction is trivial. Now consider assigning $v_{k+1}$ randomly,then $\mathbb{E}[X\vert x_1,x_2,\dots, x_{k+1}]=\sum\limits_{i=1}^{k}\frac{1}{k}\mathbb{E}[X\vert x_1,x_2,\dots, x_{k+1}=v_i\text{ is in the $k$th set}]$. It follows that $\max\limits_{i=1}^{k}\mathbb{E}[X\vert x_1,x_2,\dots, x_{k+1}=v_i\text{ is in the $k$th set}]\geq \mathbb{E}[X\vert x_1,x_2,\dots, x_{k}]$

, therefore we reach a deterministic algorithm for finding such a cut.

## Exercise 6.7

Consider the following randomized algorithm of generating a dominating set:

1. choose each vertex of $G$ independently and uniformly at random with equal probability $p$. 

2. For each edge $e$ that is not yet dominated, choose a vertex $v\in e$ uniformly at random.

Then, let $X$ be the number of vertices chosen in the first step of the algorithm, $Y$ be the number of vertices chosen in the second step of the algorithm. It follows that $\mathbb{E}[X]=np$ and $\mathbb{E}[Y]=m(1-p)^r$ since each the number of vertices chosen at the second the second is equal to the number of edges remaining, and each edges survives the first step with probability $m(1-p)^r$. Therefore, the expected size of the dominating set is $\mathbb{E}[(X+Y)]=\mathbb{E}[X]+\mathbb{E}[Y]=np+m(1-p)^r$. Then by expectation argument, there is a dominating set of size at most $np+(1-p)^rm$ for every real number $0\leq p\leq 1$. To show that there is a dominating set of size at most $\frac{m+n\ln{r}}{r}$, we take $p=\frac{\ln{r}}{r}$, then we need to show that $(1-\frac{\ln{r}}{r})^r\leq \frac{1}{r}$. By taking logarithms on both sides, we have $\ln(1-\frac{\ln{r}}{r})+\frac{\ln{r}}{r}\leq 0$. By studying the property of function $f(x)=\ln(1-x)+x$, we know $f(x)=0$ and $f'(x)=1-\frac{1}{1-x}<0$ when $x\in [0,1]$. Therefore $\ln(1-\frac{\ln{r}}{r})+\frac{\ln{r}}{r}\leq 0$ is thus proved.

## Exercise 6.8

Consider the following randomized algorithm:

1. color each vertex of $K_n$ independently and uniformly at random with two colors

2. For each monochromatic clique of size $k$, choose one of its $k$ vertices uniformly at random, then erase it and all its incident edges.

Let $X$ be the number of vertices remaining after the execution of the algorithm. For each clique of size $k$, the probability that it's monochromatic is $2^{1-\binom{n}{2}}$, and there are $\binom{n}{k}$ such cliques. Therefore $\mathbb{E}[X]=n-\binom{n}{k}2^{1-\binom{n}{2}}$. By the expectation argument, there exists a way to $2$-color the edges of $K_x$ so that there is no monochromatic clique of size $k$ when $x=n-\binom{n}{k}2^{1-\binom{n}{2}}$.

