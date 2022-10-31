# Problem Set II

## Problem 7

(a) If $v \sim \mathrm{Unif} (0; 1)$, $F(v) = v$, $F^{-1}(1 - q) = 1 - q$, and $R(q) = q (1 - q)$.

(b) Derivative of the revenue curve:

$$
R^\prime(q) = V(q) + q V^\prime(q) = V(q) + q \frac{(1 - q)^\prime}{F^\prime(F^{-1}(1-q))} = V(q) - \frac{q}{f(V(q))}.
$$

Virtual valuation function:

$$
\varphi(V(q)) = V(q) - \frac{1 - F(V(q))}{f(V(q))} = V(q) - \frac{1 - (1 - q)}{f(V(q))} = V(q) - \frac{q}{f(V(q))}.
$$

As we see, these are the same expressions.

(c) Distribution is called regular if its virtual valuation function is strictly increasing, i.e. $\forall v$ $\varphi^\prime(v) > 0$.
Since $F$ is strictly increasing, $V$ is bijective, and this condition is equivalent to $(\varphi(V(q)))^\prime > 0$.
But based on the result from (b), it is equivalent to $R^{\prime\prime}(q) > 0$, which is equivalent to $R$ being concave.

(d) As we've shown in (c), since the distribution is regular, the revenue function is concave.
This means that $\forall x, y \in \[0; 1\]$ and $\forall \alpha \in \[0; 1\]$

$$
R(\alpha x + (1 - \alpha) y) \le \alpha R(x) + (1 - \alpha) R(y).\ \ \ \ (\ast)
$$

Also remember that $R(0) = R(1) = 0$.

Now, let $q^\ast = \arg \max_{q} R(q)$.

Consider the case when $q^\ast \in (0; \frac{1}{2}\]$.
Let $x = \frac{1}{2}$, $y = 0$, $\alpha = 2 q^\ast \le 1$.
$(\ast)$ now turnes into

$$
R(q^\ast) \le 2 q^\ast R\left(\frac{1}{2}\right) \le 2 R\left(\frac{1}{2}\right)
\Rightarrow
R\left(\frac{1}{2}\right) \ge \frac{1}{2} R(q^\ast).
$$

Now consider the case when $q^\ast \in \[\frac{1}{2}; 1)$.
Let $x = \frac{1}{2}$, $y = 1$, $\alpha = 2 (1 - q^\ast) \le 1$.
$(\ast)$ turnes into

$$
R(q^\ast) \le 2 (1 - q^\ast) R\left(\frac{1}{2}\right) \le 2 R\left(\frac{1}{2}\right)
\Rightarrow
R\left(\frac{1}{2}\right) \ge \frac{1}{2} R(q^\ast).
$$

So, indeed, the median price is a $\frac{1}{2}$-approximation of the optimal price.
