## Exercise 7.2

$$P_{0,0}^t=\sum\limits_{i=0}^{\lfloor \frac{t}{2}\rfloor}\binom{t}{2i}(1-p)^{2i}p^{t-2i}$$

## Exercise 7.3

The process doesn't satisfy Definition 7.1 since the transition matrix isn't fixed. Adding one state representing the current parity of time would make a process that's equivalent to the given, also satisfying Definition 7.1.

## Exercise 7.6

Again, we have a system of linear equations:

$$h_n=0$$

$$h_{j}=\frac{h_{j-1}}{2}+\frac{h_{j+1}}{2}+1, 1\leq j\leq n-1$$

$$h_0=h_1+2$$

By solving this system of linear equations, it follows that $h_0=n(n+1)$

## Exercise 7.7

By starting with an assignment chosen uniformly at random, we start from position $j$ with probability $\frac{\binom{n}{j}}{2^j}$. Therefore the expected time becomes $\sum\limits_{j=0}^{n}\frac{\binom{n}{j}}{2^n}(n^2-j^2)$.

Here we wish to simplify $\sum\limits_{j=0}^{n}\binom{n}{j}j^2$, which can be done by considering generating function $(1+x)^n=\sum\limits_{j=0}^{n}\binom{n}{j}x^j$, two times taking derivative on both sides, and plug into $x=1$, we then have 

$\sum\limits_{j=0}^{n}\binom{n}{j}j^2=n(n+1)2^{n-2}$. Therefore the expected number of time until a satisfying assignment is found becomes $\frac{3n^2-n}{4}$.

