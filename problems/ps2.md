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
This means that $\forall x, y \in [0; 1]$ and $\forall \alpha \in [0; 1]$

$$
R(\alpha x + (1 - \alpha) y) \le \alpha R(x) + (1 - \alpha) R(y).\ \ \ \ (\ast)
$$

Also remember that $R(0) = R(1) = 0$.

Now, let $q^\ast = \arg \max_{q} R(q)$.

Consider the case when $q^\ast \in (0; \frac{1}{2}]$.
Let $x = \frac{1}{2}$, $y = 0$, $\alpha = 2 q^\ast \le 1$.
$(\ast)$ now turnes into

$$
R(q^\ast) \le 2 q^\ast R\left(\frac{1}{2}\right) \le 2 R\left(\frac{1}{2}\right)
\Rightarrow
R\left(\frac{1}{2}\right) \ge \frac{1}{2} R(q^\ast).
$$

Now consider the case when $q^\ast \in [\frac{1}{2}; 1)$.
Let $x = \frac{1}{2}$, $y = 1$, $\alpha = 2 (1 - q^\ast) \le 1$.
$(\ast)$ turnes into

$$
R(q^\ast) \le 2 (1 - q^\ast) R\left(\frac{1}{2}\right) \le 2 R\left(\frac{1}{2}\right)
\Rightarrow
R\left(\frac{1}{2}\right) \ge \frac{1}{2} R(q^\ast).
$$

So, indeed, the median price is a $\frac{1}{2}$-approximation of the optimal price.

## Problem 8

(a) Took me some time to realize that the signs in the hint should be the other way around.
In fact, we want to define $\hat t$ such that $q(\hat t) := \mathbb P [\pi^\ast \lt \hat t] \le \frac{1}{2} \le \mathbb P [\pi^\ast \le \hat t] =: Q(\hat t)$, where $\pi^\ast = \max_i \pi_i$.

Let's also introduce some notation for threshold strategies.
Let $s(t)$ be the smallest $i$ such that $\pi_i \ge t$ (or $n$ if there's no such $i$), and $S(t)$ be the smallest $i$ such that $\pi_i \gt t$ (or, again, just $n$).

By the same argument as in the lecture, we can show that

$$
\mathbb E [\pi_{s(t)}] \ge (1 - q(t)) t + q(t) \sum_{i=1}^n \mathbb E [(\pi_i - t)^+]
$$

and

$$
\mathbb E [\pi_{S(t)}] \ge (1 - Q(t)) t + Q(t) \sum_{i=1}^n \mathbb E [(\pi_i - t)^+]
$$

(this holds for arbitrary $t$, and for our choice $\hat t$ in particular).

Also recall that for any $t$

$$
\mathbb E [\pi^\ast] \le t + \sum_{i=1}^n \mathbb E [(\pi_i - t)^+].
$$

For compactness, let $\hat \pi = \sum\limits_{i=1}^n \mathbb E [(\pi_i - \hat t)^+]$ (so $\mathbb E [\pi^\ast] = \hat t + \hat \pi$), and consider two cases.

Case A: $\hat t \ge \hat \pi$.
Consider the expected payoff of $s(\hat t)$:

$$
\displaylines{
\mathbb E [\pi_{s(\hat t)}]
\ge (1 - q(\hat t)) \hat t + q(\hat t) \hat \pi
= \frac{1}{2} \hat t + \left(\frac{1}{2} - q(\hat t)\right) \hat t + \frac{1}{2} \hat \pi - \left(\frac{1}{2} - q(\hat t)\right) \hat \pi \\
= \frac{1}{2} (\hat t + \hat \pi) + \underbrace{\left(\frac{1}{2} - q(\hat t)\right)}\_{\ge 0} \underbrace{(\hat t - \hat \pi)}\_{\ge 0} \ge \frac{1}{2} \mathbb E [\pi^\ast].
}
$$

So, $s(\hat t)$ satisfies the Prophet inequality.

Case B: $\hat t \le \hat \pi$.
The expected payoff of $S(\hat t)$:

$$
\displaylines{
\mathbb E [\pi_{S(\hat t)}]
\ge (1 - Q(\hat t)) \hat t + Q(\hat t) \hat \pi
= \frac{1}{2} \hat t + \left(\frac{1}{2} - Q(\hat t)\right) \hat t + \frac{1}{2} \hat \pi - \left(\frac{1}{2} - Q(\hat t)\right) \hat \pi \\
= \frac{1}{2} (\hat t + \hat \pi) + \underbrace{\left(\frac{1}{2} - Q(\hat t)\right)}\_{\le 0} \underbrace{(\hat t - \hat \pi)}\_{\le 0} \ge \frac{1}{2} \mathbb E [\pi^\ast],
}
$$

and in this case $S(\hat t)$ satisfies the Prophet inequality.

So indeed the result generalizes for discotinuous distributions.

(b) Consider the simple scenario where $\pi_1$ is always $1$ and $\pi_2$ is $\frac{1}{\alpha}$ with probability $\alpha \in (0; 1)$ and $0$ otherwise.
All stopping strategies have the expected payoff of at most $1$.
At the same time, the expected payoff of the prophet is $1 (1 - \alpha) + \frac{1}{\alpha} \alpha = 2 - \alpha$.
For a given $c \gt \frac{1}{2}$, we want $1 \lt c (2 - \alpha)$; and, solving for $\alpha$, we get $\alpha \lt 2 - \frac{1}{c}$, which is always a non-empty subset of $(0; 1)$.

So indeed, for a given $c \gt \frac{1}{2}$, there always exist distributions such that the expected payoff of any stopping strategy is smaller than $c$ times the epxected payoff of the prophet.

(c) When all the distributions are identical (i.e., $G_1 = \dots = G_n = G$), the function $q(t)$ equals $G(t)^n$.

The argument is the same as in the lecture except for the single point: instead of writing $\mathbb P [\pi_j < t\ \forall j \ne i] \ge q(t)$, we can write $\mathbb P [\pi_j < t\ \forall j \ne i] = G(t)^{n-1}$, and the expression for the lower bound of the expected payoff becomes

$$
\mathbb E[\pi_{s(t)}] \ge (1 - G(t)^n) t + G(t)^{n-1} \sum \mathbb E [ (\pi_i - t)^+ ].
$$

Now we can define $t^\ast$ to be the solution of $1 - G(t)^n = G(t)^{n-1}$, and the stopping rule $s(t^\ast)$ will give us the approximation factor of $G^{n-1}(t^\ast)$.
Note that $t^\ast$ should exist at least for continuous distributions because it's the intersection of increasing and decreasing functions.

While finding $t^\ast$ itself might be hard, the expression for the approximation factor is quite simple:

$$
1 - G(t^\ast)^n = G(t^\ast)^{n-1} \Rightarrow G(t^\ast)^{n-1} = \frac{1}{1 + G(t^\ast)}.
$$

$G$ is CDF, so $G(t^\ast) \lt 1$, and the approximation factor is greater than $\frac{1}{2}$ (there's a feeling tho that it converges to $\frac{1}{2}$ as $n \to \infty$).
