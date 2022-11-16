# Problem Set II

## Problem 7

I'm writing slightly more than required in this problem because understanding of revenue curve and virtual valuation function will help in the next problems.

First of all, note that there are two ways to define the revenue curve: in terms of sale probability $q$ (given in the problem statement) and in terms of posted price $r$ (given in the lecture).
Both formulations are useful for different purposes.

Next, maximizing revenue curve over $q$ gives us the optimal sale probability $q^\ast$.
The corresponding posted price $r^\ast = V(q^\ast)$ is precicely the monopoly price of $F$, which also turns out to be $\varphi^{-1}(0)$.
Indeed, $r^\ast$ maximizes $R(r) = r (1 - F(r))$, so the derivative $R^\prime(r) = 1 - F(r) - r f(r)$ at $r^\ast$ equals zero, or

$$
r^\ast = \frac{1 - F(r^\ast)}{f(r^\ast)} \Rightarrow r - \frac{1 - F(r^\ast)}{f(r^\ast)} = 0
\Rightarrow \varphi(r^\ast) = 0 \Rightarrow r^\ast = \varphi^{-1}(0).
$$

An interesting conclusion is that $\mathrm{OPT}_F$ is simply the Vickrey auction with reserve equal to the monopoly price of $F$.

(a) If $v \sim \mathrm{Unif} (0; 1)$, $F(v) = v$, $F^{-1}(1 - q) = 1 - q$, and $R(q) = q (1 - q)$.

(b) Derivative of the revenue curve:

$$
R^\prime(q) = V(q) + q V^\prime(q) = V(q) + q \frac{(1 - q)^\prime}{F^\prime(F^{-1}(1-q))} = V(q) - \frac{q}{f(V(q))}.
$$

Virtual valuation function:

$$
\varphi(V(q)) = V(q) - \frac{1 - F(V(q))}{f(V(q))} = V(q) - \frac{1 - (1 - q)}{f(V(q))} = V(q) - \frac{q}{f(V(q))}.
$$

As we see, these are the same expressions, so indeed $\varphi(V(q)) = R^\prime(q)$.

Note that the similar relationship also holds in terms of reserve price:

$$
\varphi(r) = - \frac{R^\prime(r)}{f(r)}.
$$

(c) Distribution $F$ is called regular if its virtual valuation function is strictly increasing, i.e. $\forall x$ $\varphi^\prime(x) > 0$. $V$ is a bijective decreasing function of $q$, so this means that $\frac{\mathrm d \varphi}{\mathrm d q} < 0$ for all $0 \le q \le 1$. But based on the result from (b), it is equivalent to $R^{\prime\prime}(q) < 0$, which in turn is equivalent to $R$ being concave.

(d) As we've shown in (c), since the distribution is regular, the revenue function is concave.
This means that $\forall x, y \in [0; 1]$ and $\forall \alpha \in [0; 1]$

$$
R(\alpha x + (1 - \alpha) y) \ge \alpha R(x) + (1 - \alpha) R(y).\ \ \ \ (\ast)
$$

Also remember that $R(0) = R(1) = 0$.

This would be sufficient for us to show the desired inequality directly but I'll take a slightly longer path that produces an intermediate result that is useful for one of the next problems. In fact, lets show that

$$
\mathbb E_{q \sim \mathrm{Unif}(0; 1)} [R(q)] \ge \frac{1}{2} R(q^\ast).
$$

Let $q \in [0; q^\ast]$. If we now plug values $x = q^\ast$, $y = 0$ and $\alpha = \frac{q}{q^\ast}$ into $(\ast)$, we get

$$
R(q) \ge \frac{q}{q^\ast} R(q^\ast).
$$

Let now $q \in [q^\ast; 1]$. If we now plug $x = q^\ast$, $y = 1$ and $\alpha = \frac{1 - q}{1 - q^\ast}$ into $(\ast)$, we get

$$
R(q) \ge \frac{1 - q}{1 - q^\ast} R(q^\ast).
$$

Now,

$$
\displaylines{
\mathbb E_{q \sim \mathrm{Unif}(0; 1)} [R(q)]
    = \int_0^1 R(q) \mathrm d q
    = \int_0^{q^\ast} R(q) \mathrm d q + \int_{q^\ast}^1 R(q) \mathrm d q \\
    \ge R(q^\ast) \left[
        \frac{1}{q^\ast} \int_0^{q^\ast} q \mathrm d q
        + \frac{1}{1 - q^\ast} \int_{q^\ast}^1 (1 - q) \mathrm d q
    \right] \\
    = R(q^\ast) \left[
        \frac{1}{q^\ast} \frac{q^2}{2} \bigg|_0^{q^\ast}
        - \frac{1}{1 - q^\ast} \frac{(1 - q)^2}{2} \bigg|_{q^\ast}^1
    \right] \\
    = R(q^\ast) \left[\frac{q^\ast}{2} + \frac{1 - q^\ast}{2} \right]
    = \frac{1}{2} R(q^\ast).
}
$$

We arrived at the important result that using a sale probability $q$ sampled from the uniform distribution (which is equivalent to posting price $r$ sampled from $F$) on expectation gives us at least half of the maximum revenue achived by posting the monopoly price.

We now only need to apply Jensen's inequality for expectations to conclude that $R\left(\frac{1}{2}\right) \ge \mathbb E_{q \sim \mathrm{Unif}(0; 1)} [R(q)]$, which gives us the desired final result that meadian price is $\frac{1}{2}$-approximation of the optimal posted price.

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

## Problem 9

(a) This generalization of Bulow-Klemperer is rather simple and the proof is almost the same.
We construct a mechanism $\mathcal A$ for an auction with $n + k$ bidders and $k$ identical goods which acts as follows:
1. Run $\mathrm{OPT}_F$ with the first $n$ bidders;
2. Arbitrarily allocate the remaining goods (if any) for free between the remaining $k$ bidders.

This mechanism allocates all $k$ goods and has the same expected revenue as $\mathrm{OPT}_F$ with $n$ bidders.

Now, the Vickrey auction with $n+k$ bidders and $k$ goods achieves the best expected revenue among those mechanism that allocate all goods, so its expected revenue must be greater than or equal to that of $\mathrm{OPT}_F$ with $n$ bidders.

(b) Let's slightly reformulate the problem to make it more approachable.
What we want to show is that the expected revenue of Vickrey auction with $n \ge 1$ bidders and random reserve $r \sim F$ (expectation both over reserve and valuations) is at least half of the expected revenue of $\mathrm{OPT}_F$ with the same number of bidders.
We then simply need to combine this with lemma we proved in exercise 27 (that connects revenues of $\mathrm{OPT}_F$ with $n$ and $n+1$ bidders) to get the final result.

Notice how for $n = 1$ we can just use the result from problem 7 (d) without any modifications.
The proof for arbitrary $n$ reduces to the very similar problem, but has to take into account that each bidder has to overbid not only the reserve price but also the critical bid in order to win.

Let's fix an arbitrary bidder $i$, bids $\mathbf v_{-i}$ by others and reserve price $r$, and try to reason about the expected revenue that comes from $i$.

Recall that in a single-bidder setting, $R(q)$ was the expected revenue from $i$ when sale probability induced by reserve price was $q$.
This time things get slightly messier as $i$ needs to overbid both reserve price and critical bid (think $k$-th highest bid from $\mathbf v_{-i}$).
Let's call the corresponding values in sale probability space $q$ and $q_i$ respectively.
Then, expected revenue from $i$ (denote it $R_i(q)$ for simplicity) is $R(\min\\{q, q_i\\})$.

We'll now focus on showing that $\int_0^1 R_i(q) \mathrm d q \ge \frac{1}{2} R_i(q^\ast)$ where $q^\ast$ is sale probability that corresponds to the monopoly price $r^\ast$.
By taking the expectation over $\mathbf v_{-i}$ and summing over $i$ we will then get the desired result.

We're still assuming that $F$ is regular so $R$ is concave.
Also, $R$ is still maximized at $q^\ast$, and equals zero when $q = 0$ or $q = 1$.

Let's start with a simpler case when $q_i \ge q^\ast$.
* $R_i(q^\ast)$ just equals $R(q^\ast)$.
* When $q \le q_i$, $R_i(q)$ equals $R(q)$.
* When $q \ge q_i$, $R_i(q)$ equals $R(q_i)$ which is greater than or equal to $R(q)$ since $R$ is decreasing on $[q^\ast; 1]$.

Combining everything,

$$
R_i(q) \ge R(q) \Rightarrow \int_0^1 R_i(q) \mathrm d q \ge \int_0^1 R(q) \mathrm d q
\underbrace{\ge}\_{\text{7(d)}} \frac{1}{2} R(q^\ast) = \frac{1}{2} R_i(q^\ast).
$$

Now let's consider a case when $q_i \le q^\ast$.
* $R_i(q^\ast)$ equals $R(q_i)$.
* When $q \le q_i$, $R_i(q)$ equals $R(q)$, and we can use concavity of $R$: plug $x = q_i$, $y = 0$, $\alpha = \frac{q}{q_i}$ into $(*)$ and get $R(q) \ge \frac{q}{q_i} R(q_i)$;
* When $q \ge q_i$, $R_i(q)$ equals $R(q_i)$.

Combining everything,

$$
\displaylines{
\int_0^1 R_i(q) \mathrm d q
    = \int_0^{q_i} R_i(q) \mathrm d q
    + \int_{q_i}^1 R_i(q) \mathrm d q
    \ge \frac{R(q_i)}{q_i} \underbrace{\int_0^{q_i} q \mathrm d q}\_{= \frac{q_i^2}{2}}
    + (1 - q_i) R(q_i) \\
    = \left(1 - \frac{q_i}{2} \right) R(q_i)
    \ge \frac{1}{2} R(q_i)
    = \frac{1}{2} R_i(q^\ast).
}
$$

So, in both cases, $\int_0^1 R(q) \mathrm d q \ge R_i(q^\ast)$, which is what we wanted to show.

## Problem 10

(a) $F_i$ is an MHR distribution if $\frac{f_i(v_i)}{1 - F_i(v_i)}$ is nondecreasing in $v_i$.
This means that $\frac{1 - F_i(v_i)}{f_i(v_i)}$ is nonincreasing in $v_i$ and $\varphi_i(v_i)$ is increasing as a difference of increasing and nonincreasing functions.
So, $F_i$ has increasing virtual valuation function and is thus regular.

(b) When $x \sim \mathrm{Unif}(0; 1)$, $F(x) = x$, $f(x) = 1$, and $\frac{f(x)}{1 - F(x)} = \frac{1}{1 - x}$ which is an increasing function in $x$, so the uniform distribution is MHR. Similar for general uniform distributions.

When $x \sim \mathrm{Exp}(\lambda)$, $F(x) = 1 - e^{- \lambda x}$, $f(x) = \lambda e^{-\lambda x}$, so $\frac{f(x)}{1 - F(x)} = \frac{\lambda e^{-\lambda x}}{1 - (1 - e^{-\lambda x})} = \lambda$ which is constant (so, nondecreasing), and the exponential distribution is also MHR.

(c) In problem 7 we've shown that for monopoly price $r_i$ it holds that $r_i = \frac{1 - F_i(r_i)}{f_i(r_i)}$.
$F_i$ is MHR, so for $v_i \ge r_i$ it holds that $\frac{1 - F_i(r_i)}{f_i(r_i)} \ge \frac{1 - F_i(v_i)}{f_i(v_i)}$.
Combining, we get

$$
r_i \ge \frac{1 - F_i(v_i)}{f_i(v_i)} \Rightarrow r_i + v_i - \frac{1 - F_i(v_i)}{f_i(v_i)} \ge v_i \Rightarrow r_i + \varphi_i(v_i) \ge v_i.
$$

(d) Convinced :)

(e) Here we need to observe that $\mathcal M^\ast$ chooses an outcome from those that $\mathcal M$ optimizes over, i.e., the chosen outcome $T$ (i) is feasible and (ii) only contains bidders with $v_i \ge r_i$ (so $T \subset S$).
The first statement is trivial.
To see that the second statement is true, imagine that $\mathcal M^\ast$ chooses a feasible outcome $T^\prime$ that contains a bidder $j$ for who $v_j \lt r_j$.
Since $F_j$ is MHR, the latter inequality implies that $\varphi_j(v_j) \lt 0$, and $\mathcal M^\ast$ would be strictly better off without $j$.
Luckily, the environment is downward-closed, so if $T^\prime$ is feasible then $T^\prime \setminus \\{j\\}$ is also feasible.
This way, we can remove all bidders that don't meet their reserve price.

Finally we conclude that $\mathcal M$ optimizes surplus over feasible subsets of $S$ and its surplus is thus greater than or equal to the surplus of any other feasible subset of $S$, including the one chosen by $\mathcal M^\ast$.

(f) Let's fix valuations $\mathbf v$ for a second.
The way $\mathcal M$ is defined, from $x_i(\mathbf v) = 1$ follows that $v_i \ge r_i$.
Using (c) we can now write

$$
\sum_i x_i(\mathbf v) v_i
    \le \sum_i x_i(\mathbf v) (r_i + \varphi_i(v_i))
    = \sum_i x_i(\mathbf v) r_i + \sum_i x_i(\mathbf v) \varphi_i(v_i).
$$

Now, if $x_i(\mathbf v) = 1$, $i$ pays the criticial bid $p_i(\mathbf v)$ which is guaranteed to be at least $r_i$.
So our inequality becomes

$$
\sum_i x_i(\mathbf v) v_i \le \sum_i x_i(\mathbf v) p_i(v) + \sum_i x_i(\mathbf v) \varphi_i(v_i).
$$

Finally, let's take expectation over $\mathbf v$.
On the left we end up with $\mathcal M$'s expected surplus, and on the right we have a sum of two different expressions for $\mathcal M$'s expected revenue.
Thus we conclude that the expected revenue of $\mathcal M$ is at least half of its expected surplus.

(g) From (f) we have that the expected revenue of $\mathcal M$ is at least half of its expected surplus.
From (e) we have that the expected surplus of $\mathcal M$ is at least the expected surplus of $\mathcal M^\ast$.
Also, for every DSIC mechanism (including $\mathcal M^\ast$) its expected surplus is greater than or equal to its expected revenue (because $\varphi (x) \le x$).
Combining these three we can conclue that the expected revenue of $\mathcal M$ is at least half of the expected revenue of $\mathcal M^\ast$.

## Problem 11

(a) For a second, let's fix prices $\mathbf p = (p_1, \dots, p_n)$ and valuations $\mathbf v = (v_1, \dots, v_n)$.

Let $R_{\mathbf p}(\mathbf v)$ denote the revenue in a single-consumer problem when we post prices $\mathbf p$ and consumer's valuations for goods are $\mathbf v$.
This revenue equals either $p_i$ where $i = \arg \max_i (v_i - p_i)^+$ or $0$ if for all $i$ $v_i \lt p_i$.

Let's also consider a mechanism $\mathcal M (\mathbf p)$ for a single-good problem, that posts reserve prices $\mathbf p$ for bidders whose valuations are $\mathbf v$.
The mechanism allocates the good to the bidder $i$ where $i$ is defined as above or to nobody if no bidders meet the reserve price.
Note that this allocation rule is monotone, so it can be augmented with a critical bid payment rule to make the mechanism DSIC.
Notice that because the critical bid is at least $p_i$ (otherwise $i$ wouldn't be able to win at all), the revenue $R_{\mathcal M(\mathbf p)} (\mathbf v)$ of this mechanism is always greater than or equal to $R_{\mathbf p}(\mathbf v)$, no matter what $\mathbf p$ and $\mathbf v$ are.

Now let $\mathbf p^\ast = \arg \max_{\mathbf p} \mathbb E_{\mathbf v} [R_{\mathbf p} (\mathbf v)]$ be the prices that maximize the revenue in a single-consumer problem.
It is clear that

$$
\mathbb E_{\mathbf v} [R_{\mathbf p^\ast} (\mathbf v)] 
\le \mathbb E_{\mathbf v} [R_{\mathcal M(\mathbf p^\ast)} (\mathbf v)].
$$

But $\mathcal M(\mathbf p^\ast)$ is just an arbitrary mechanism for a single-good problem, and its expected revenue itself is less than or equal to that of $\mathrm{OPT}_F$.

Combining, we can conclude that the maximum achievable expected revenue in a single-consumer problem is bounded above by the maximum expected revenue in a single-good problem.

(b) :(

## Problem 12

(a) Let's slightly modify our notation: let $\mathbf b$ be submitted valuations (as functions of outcomes $\omega$), $f(\omega; \mathbf b) = c(\omega) + \sum\limits_{i=1}^n w_i b_i(\omega)$ be our affine maximizer, and $f_{-i}(\omega; \mathbf b) = c(\omega) + \sum_{j \ne i} w_j b_j(\omega)$ for each player $i$.

Consider the following mechanism:
* allocation: $x(\mathbf b) = \omega^\ast$ where $\omega^\ast = \arg \max_{\omega \in \Omega^\prime} f(\omega; \mathbf b)$;
* payments: $p_i(\mathbf b) = \frac{1}{w_i} \left[ \max_{\omega \in \Omega^\prime} f_{-i}(\omega; \mathbf b) - f_{-i}(\omega^\ast; \mathbf b) \right]$.

It's easy to show that this mechanism satisfies the desired properties.
When $\mathbf b = \mathbf v$, the allocation indeed maximizes $f$ over $\Omega^\prime$.
To show that it is DSIC, consider player $i$'s utility in $\omega^\ast$:

$$
\displaylines{
v_i(\omega^\ast) - p_i(\mathbf b)
    = v_i(\omega^\ast) - \frac{1}{w_i} \left[
        \max_{\omega \in \Omega^\prime} f_{-i}(\omega; \mathbf b)
        - f_{-i}(\omega^\ast; \mathbf b)
    \right] \\
    = \frac{1}{w_i} \left[
        \underbrace{c(\omega^\ast) + w_i v_i(\omega^\ast) + \sum_{j \ne i} w_j b_j(\omega^\ast)}\_{\text{equals $f(\omega^\ast; \mathbf b)$ when $v_i = b_i$}}
        - \underbrace{\max_{\omega \in \Omega^\prime} f_{-i}(\omega; \mathbf b)}\_{\text{does not depend on $b_i$}}
    \right].
}
$$

We see that if $i$ submits their valuation truthfully, allocation rule turns out to maximize $i$'s objective as well, so telling the truth is a dominant strategy for $i$.
This holds for other players, so the mechanism is DSIC.

(b) Let $\mathcal N$ denote the set of all players, and $\mathcal A = \{i \in \mathcal N : |T_i^\ast| \ge \sqrt{m}\}$. Since there are only $m$ goods, it must be that $|\mathcal A| \le \sqrt{m}$.

Next, consider a player $j \in \mathcal A$ whose valuation in the optimum is the highest amongst $\mathcal A$. $j$'s valution is obviously greater than or equal to the average valution amongst $\mathcal A$ in the optimum, i.e. $v_j(T_j^\ast) \ge \frac{1}{|\mathcal A|} \sum_{i \in \mathcal A} v_i(T_i^\ast)$.

Now, combine everything we now about the problem:

$$
v_j(\mathcal S)
    \underbrace{\ge}\_{\text{$v_j$ monotone}} v_j(T_j^\ast)
    \underbrace{\ge}\_{\text{our choice of $j$}} \frac{1}{|\mathcal A|} \sum_{i \in \mathcal A} v_i(T_i^\ast)
    \underbrace{\ge}\_{\text{definition of $\mathcal A$}} \frac{1}{\sqrt{m}} \sum_{i \in \mathcal A} v_i(T_i^\ast)
    \underbrace{\ge}\_{\text{lopsided}} \frac{1}{2 \sqrt{m}} \sum_{i \in \mathcal N} v_i(T_i^\ast).
$$

So, in the problem that is lopsided, the allocation that gives all the goods to a single player $j$ who has the highest valuation in the optimum amongst $\mathcal A$ achieves at least $\frac{1}{2\sqrt{m}}$ of the maximum surplus.

(c) Let's consider an arbitrary player $i$. Let aslo $s_i^\ast = \arg \max_{s \in T_i^\ast} v_i(s)$.
Since valuations are subadditive, it holds that $v_i(T_i^\ast) \le \sum_{s \in T_i^\ast} v_i(s) \le |T_i^\ast| v_i(s_i^\ast) \Rightarrow v_i(s_i^\ast) \ge \frac{1}{|T_i^\ast|} v_i(T_i^\ast)$.

Next, the problem is not lopsided, so $\sum_{i \in \mathcal A} v_i(T_i^\ast) \lt \frac{1}{2} \sum_{i \in \mathcal N} v_i(T_i^\ast)$.
This immediately implies $\sum_{i \in \mathcal N \setminus \mathcal A} v_i(T_i^\ast) \ge \frac{1}{2} \sum_{i \in \mathcal N} v_i(T_i^\ast)$.
Also, if $i \in \mathcal N \setminus \mathcal A$ then $|T_i^\ast| \le \sqrt{m}$.

Again, combine everything:

$$
\sum_{i \in \mathcal N \setminus \mathcal A} v_i(s_i^\ast)
    \underbrace{\ge}\_{\text{$v_i$ subadditive}} \sum_{i \in \mathcal N \setminus \mathcal A} \frac{1}{|T_i^\ast|} v_i(T_i^\ast)
    \underbrace{\ge}\_{\text{definition of $\mathcal A$}} \frac{1}{\sqrt{m}} \sum_{i \in \mathcal N \setminus \mathcal A} v_i(T_i^\ast)
    \underbrace{\ge}\_{\text{not lopsided}} \frac{1}{2\sqrt{m}} \sum_{i \in \mathcal N} v_i(T_i^\ast).
$$

So, in the problem that's not lopsided, the allocation that gives each player $i$ from $\mathcal N \setminus \mathcal A$ the item from $T_i^\ast$ that $i$ values the most achieves at least $\frac{1}{2\sqrt{m}}$ of the maximum surplus.

(d) In parts (b) and (c) we've shown that good allocations _exist_ for lopsided and not lopsided problems.
Those allocations are pretty useless though because they actually use optimal allocation in their construction.
Luckily, knowing they exist is sufficient because we can construct simple allocations that produce better results than those and get the desired lower bound.

Let's start with simpler case when the problem is lopsided.
We know that there exists some player $j$ such that allocating all the goods to them gives us at least $\frac{1}{2\sqrt{m}}$ of the maximum surplus.
We don't even need to know $j$ since we can simply allocate all goods to the player who values them the most, giving us even higher surplus.
This solution takes linear time.

Slightly trickier case is when the problem is not lopsided.
We proved that there exists a solution that achieves the same lower bound, and we know that in this solution every player gets at most one good.
Well, let's optimize over all such outcomes.
Luckily, there's a polynomial-time way to do that.

Consider a bipartite graph with the set of players $\mathcal N$ on the left side, the set of goods $\mathcal S$ on the right side, and the weight of each edge $(i, s)$ equal to the valuation $v_i(s)$.
Matching (a set of edges that don't have common vertices) in this graph corresponds to the allocation in which each player gets at most one good.
We're interested in the maximum-weight matching, and we can use one of classical algorithms (say, Hungarian method) to find the solution in polynomial time.
This solution is guaranteed to have the surplus at least that of one from (c), so it also satisfies the lower bound.

Well, normally we don't know in advance if the problem is lopsided or not, but we can run both described algorithms and take the better result.

To summarize, the polynomial-time $\Theta(1 / \sqrt{m})$-approximate surplus maximization algorithm for subadditive valuations is the following:
1. Run Hungarian algorithm to find the maximum-weight matching in the bipartite graph with players on the left, goods on the right, and valuations as edges;
2. Find the player who values the bundle $\mathcal S$ of all goods the most;
3. Return the better allocation of those found in steps 1 and 2.

(e) In part (a) we proved that for every affine maximizer $f$ and every subset of outcomes $\Theta^\prime$ there exists a DSIC mechanism that maximizes $f$ over $\Theta^\prime$ and wrote down its allocation and payment rules.

In parts (b) through (d) we found the polynomial-time algorithm that maximizes social surplus (that's $f$) over all outcomes in which either all goods are allocated to a single player or at most one good is allocated to each player (that's $\Theta^\prime$).
We also proved that this algorithm achieves at least $\frac{1}{2\sqrt{m}}$ of maximum social surplus over all possible outcomes.

The polynomial-time DSIC combinatorial auction for subadditive valuations which achieves at least $\frac{1}{2\sqrt{m}}$ of maximum social surplus:
1. Collect players' valuations for each good separately and for the bundle of all goods (note that we collect less info);
2. Run the algorithm in (d) to determine the surplus-maximizing allocation;
3. For every player, charge according to the rule from (a), using algorithm from (d) as a subroutine for computing $\max f_{-i}$.

## Problem 13

:(
