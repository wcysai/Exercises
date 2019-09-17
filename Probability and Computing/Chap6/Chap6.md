## Exercise 6.1



.-(a) Assign each variable with True or False uniformly and independently at random. Let $X$ be the random variable denoting number of satisfied clauses. Since there are $m$ clauses and each is satisfied with probability $1-2^{-k}$, there's $\mathbb{E}[X]=m(1-2^{-k})$, which implies there exists an assignment that satisfies at least $m(1-2^{-k})$ of the clauses.

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

## Exercise 6.9

(a) Choose the ranking $R$ uniformly at random, i.e. , each possible ranking is chosen with equal probability $\frac{1}{n!}$. Let $X$ be the random variable denoting the number of edges that disagree with $R$, then $\mathbb{E}[X]=\frac{\binom{n}{2}}{2}$, therefore by expectation argument, there exists a ranking that disagrees with at most $50\%$ of the edges.



(b) Suppose that this time we generate a tournament uniformly at random,   i.e. , each possible tournament is chosen with equal probability $\frac{1}{2^{\binom{n}{2}}}$. Let $X$ be the random variable denoting the number of edges that disagree with the ranking. Since $X$ is the sum of $0-1$ independent random variables, by applying Chernoff's bound with $\mu=\frac{1}{2}$ and $\delta=0.02$, we can obtain that $Pr(X\leq (1-\delta)\mu)\leq e^{\frac{-\mu\delta^2}{2}}=e^{-\Omega(n^2)}$ By taking a union bound over all possible rankings we have the probability that $Pr[\text{there exists a ranking that disagrees with less than $49\%$ of the edges}]\leq n!e^{-\Omega(n^2)}$  As we can see, for sufficiently large $n$, $n!e^{-\Omega(n^2)}<1$. Therefore the exists a tournament such that every ranking disagrees with at least $49\%$ of the edges in the tournament.



## Exercise 6.10

(a) Let $\mathcal{F}$ be the family of all subsets of $\{1,2,\dots,n\}$ of size $\lfloor\frac{n}{2}\rfloor$ of. It's clearly that $\mathcal{F}$ satisfies the given property and has cardinality $\binom{n}{\lfloor\frac{n}{2}\rfloor}$.

(b) Choose a random permutation of the numbers from $1$ to $n$. Let $X_k=1$ if the first $k$ numbers in the permutation yield a set in $\mathcal{F}$ and $X=\sum\limits_{k=0}^{n}X_k$. Following the definition of antichain, there's at most one set in $\mathcal{F}$, which implies that $\mathbb{E}[X]\leq 1$. By counting in another way we can yield the required inequality:

$$\mathbb{E}[X]=\sum\limits_{k=0}^{n}\frac{f_k}{\binom{n}{k}}\leq 1$$

(c) Following the theorem of binomial coefficients that $\binom{n}{k}\leq \binom{n}{\lfloor\frac{n}{2}\rfloor}$ for any $k$, we have $$1\geq \sum\limits_{k=0}^{n}\frac{f_k}{\binom{n}{k}}\geq \sum\limits_{k=0}^{n}\frac{f_k}{\binom{n}{\lfloor\frac{n}{2}\rfloor}}=\frac{\vert \mathcal{F}\vert}{\binom{n}{\lfloor\frac{n}{2}\rfloor}}$$

## Exercise 6.11

(a) $\mathbb{E}[X]=\sum\limits_{i=1}^{\binom{n}{3}}\mathbb{E}[X_i]=\binom{n}{3}p^3$

(b) By a union bound argument we have $Pr(X>0)\leq \sum\limits_{i=1}^{\binom{n}{3}}p^3=\binom{n}{3}p^3$, which approaches $0$ as $pn\to 0$.

(c) $Var[X_i]=\mathbb{E}[X_i^2]-(\mathbb{E}[X_i])^2=p^3-p^6\leq p^3$

(d) For pairs $i\neq j$, If the triplets represented by $i$ and $j$ share two vertices, then $Cov(X_i,X_j)=\mathbb{E}[X_iX_j]-\mathbb{E}[X_i]E[X_j]=p^5-p^6$, otherwise $X_i$ and $X_j$ are independent, thus $Cov(X_i,X_j)=0$. It can be seen that there are$O(n^4)$ such pair of triplets that share two vertices.

(e) $$Var[X]=Var[\sum\limits_{i=1}^{\binom{n}{3}}X_i]=\mathbb{E}[X]+\sum\limits_{i=1}^{\binom{n}{3}}Var[X]+\sum\limits_{i=1}^{n}\sum\limits_{j=i+1}^{n}Cov(X_i,X_j)=O(n^3p^3+n^4(p^5-p^6))$$

(f) $Pr(X=0)\leq \frac{Var[X]}{(\mathbb{E}[X])^2}=O(\frac{n^3p^3+n^4p^5-n^4p^6}{n^6p^6})=O(\frac{1}{(np)^3})+O(\frac{p-p^2}{(np)^2})$, which clearly approaches $0$ when $np\to \infty$

## Exercise 6.12

Clearly, for each clique of size $4$, there are $\binom{n-4}{4}$ cliques sharing no vertices with it, $4\binom{n-4}{3}$ cliques sharing one vertex with it, $6\binom{n-4}{2}$ cliques sharing two vertices with it, $4\binom{n-4}{1}$ cliques sharing three vertices with it, and exactly one clique sharing four vertices with it. Thus

​        $$ \mathbb{E}[X^2]=\sum\limits_{i=1}^{\binom{n}{4}}Pr(X_i=1)\mathbb{E}[X\vert X_i=1]=\binom{n}{4}p^6(\binom{n-4}{4}\cdot p^6+4\binom{n-4}{3}\cdot p^6+6\binom{n-4}{2}\cdot p^5+4\binom{n-4}{1}\cdot p^3+1)$$

Therefore, 

$$Var[X]=\mathbb{E}[X^2]-(\mathbb{E}[X])^2=\binom{n}{4}p^6(\binom{n-4}{4}\cdot p^6+4\binom{n-4}{3}\cdot p^6+6\binom{n-4}{2}\cdot p^5+4\binom{n-4}{1}\cdot p^3+1)-(\binom{n}{4})^2p^{12}$$



## Exercise 6.13

The threshold function should be $p=f(n)=o(n^{-\frac{2}{k-1}})$. Here we use conditional expected equality for proving that the threshold function is correct for $k=5$.

for each clique of size $5$, there are $\binom{n-5}{5}$ cliques sharing no vertices with it, $5\binom{n-5}{4}$ cliques sharing one vertex with it, $10\binom{n-5}{3}$ cliques sharing two vertices with it, $10\binom{n-5}{2}$ cliques sharing three vertex with it,$10\binom{n-5}{2}$ cliques sharing four vertices with it and ,exactly one clique sharing five vertices with it. Thus $\mathbb{E}[X\vert X_i=1]=\sum\limits_{i=1}^{\binom{n}{4}}\mathbb{E}[X_i\vert X_j=1]=\binom{n-5}{5}\cdot p^{10}+5\binom{n-5}{4}\cdot p^{10}+10\binom{n-5}{3}\cdot p^9+10\binom{n-5}{2}\cdot p^7+10\binom{n-5}{1}\cdot p^4+1$

Then by the conditional expectation inequality, it follows that

$Pr(X>0)\geq\sum\limits_{i=1}^{\binom{n}{5}}\frac{Pr(X_i=1)}{\mathbb{E}[X\vert X_i=1]}=\frac{\binom{n}{5}p^{10}}{\binom{n-5}{5}\cdot p^{10}+5\binom{n-5}{4}\cdot p^{10}+10\binom{n-5}{3}\cdot p^9+10\binom{n-5}{2}\cdot p^7+10\binom{n-5}{1}\cdot p^4+1}$, which approaches $1$ as $n$ grows large when $p=f(n)=\omega(n^{-\frac{1}{2}})$, which suits the generalized threshold function.

## Exercise 6.14

Let $X$ be the number of isolated vertices in $G$, and $X_i=\begin{cases} 1 & i \text{ is an isolated vertex}\\ 0 & \text{ otherwise} \end{cases}$. Then $Pr(X>0)\geq \sum\limits_{i=1}^{n}\frac{Pr(X_i=1)}{\mathbb{E}[X\vert X_i=1]}=\frac{n(1-p)^{n-1}}{1+(n-1)(1-p)^{n-2}}=\frac{1}{\frac{1}{n(1-p)^{n-1}}+\frac{n-1}{n(1-p)}}$, which approaches $1$ as $n\to \infty$ under the constraint that $p=c\ln{n}$ and $c<1$.

## Exercise 6.15

Since $X$is nonnegative, by Markov's inequality, we have $Pr(X\geq 1)\leq \mathbb{E}[X]=\binom{n}{3}p^3\leq 1$.

For the second inequality, we apply conditional expectation inequality:

$$ Pr(X\geq 1)\geq \sum\limits_{i=1}^{\binom{n}{3}}\frac{Pr(X_i=1)}{\mathbb{E}[X\vert X_i=1]}=\frac{\binom{n}{3}p^3}{\binom{n-3}{3}\cdot p^3+\binom{n-3}{2}\cdot p^3+\binom{n-3}{1}\cdot p+1}$$, which approaches $\frac{1}{7}$ as $n\to \infty$, therefore $\lim\limits_{n\to \infty}Pr(X\geq 1)\geq \frac{1}{7}$.

## Exercise 6.16

(a) Consider the trapezoid rule and apply a similar method in this problem, then we have $\ln{n!}=\int\limits_{1}^{n}\ln{x} dx+\frac{1}{2}\ln{n}-\sum\limits_{i=1}^{\infty}\epsilon_{j}=n\ln{n}-n+1-(\sum\limits_{j=1}^{\infty}\epsilon_j-\sum\limits_{j=n}^{\infty}\epsilon_j)$ where $\epsilon_j$ is the remainder term of the difference between the integral and the trapezoid.

By not considering the remainder term we arrived at Equation (5.5). Here we directly take the exponential on both sides, and get $n!=e^{1-\sum\limits_{j=1}^{\infty}\epsilon_j}\sqrt{n}(\frac{n}{e})^ne^{\sum\limits_{j=n}^{\infty}\epsilon_j}\leq e^{1-\sum\limits_{j=1}^{\infty}\epsilon_j}\sqrt{n}(\frac{n}{e})^n $

By [Wallis product](https://en.wikipedia.org/wiki/Wallis_product) we can derive that $e^{1-\sum\limits_{j=1}^{\infty}\epsilon_j}=\sqrt{2\pi}$, therefore the bound is established: $n!\geq \sqrt{2\pi n}(\frac{n}{e})^n$

(b) Let $k$ be the number of $Y_i$ s that are equal to $1$. If $k\leq c\sqrt{m}$, then it's clear that $Pr(\vert \sum\limits_{i=1}^{m}b_iY_i\vert\leq c\sqrt{m})$