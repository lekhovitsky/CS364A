# Problem Set I

### Problem 1

Let's consider a situation at the Ukrainian National Economics Tournament I took part in a few years ago.
While the mechanism designer is, expectedly, the organizing committee of the tournament, the participants are not participating students but rather the judges, whose incentives sometimes involve giving the higher grades to the teams they favor.

The tournament took place in the Ukrainian city Sumy, and most of the judges were the teachers and professors from there.
The interesting situation happened at the semi-final stage.
There were 9 teams, divided into 3 groups of 3 teams.
Each group played one round, and the team with the highest score from each group proceeded to the final.
There were 3 teams from Sumy, and by some coincidence they all got into different groups.

Guess what happened?
Yup, since most of the judges were their teachers, they won in each group, so the final stage was a competition of three local teams, who were far from being the strongest, which caused major unsatisfaction of other participants, judges and organizers.

So, judges' strategic behavior of giving higher scores to the teams they favor contradicts with the organizers' intention to run the tournament as fair as possible.
There exist multiple solutions to this:
* put the local teams into as few groups as possible;
  * although completely solves the problem, it's usually impossible since the grid is random;
* decrease the proportion of local teachers among the judges, or at least try to make the set of judges in every group as diverse as possible;
  * this is being more or less successfully used these days;
* instead of 1 semi-final game, run 2, with different group splits;
  * also used when the resources allow.

### Problem 2

(a) Let's consider two cases.

If $b_i < v_i$, we can take any $\mathbf{b}\_{-i}$ such that its largest component (call it $B$) satisfies $b_i < B < v_i$.
By  bidding truthfully, $i$ would win the auction and get positive utility of $v_i - B$, and by bidding $b_i$ instead, $i$ would lose and get zero.

If $b_i > v_i$, we can take any $\mathbf{b}\_{-i}$ such that its largest component $B$ satisfies $v_i < B < b_i$.
By bidding truthfully, $i$ would get 0, and by bidding $b_i$ instead, $i$ would win and get negative utility of $v_i - B$.

(b) Let's fix an arbitrary set of players $S \subset N$ and arbitrary valuations $\mathbf{v}$ of bidders.
Let $i$ be the winner of the auction under truthful bidding.

If $i \notin S$ (implying $\forall j \in S\ v_j < v_i$), the total payoff of $S$ is zero in the original auction.
To change this, the coalition must submit such bids that someone from $S$ is a winner in the new auction.
This would result in a payment of at least $v_i$ (because $i$ would still play his dominant strategy), making the payoff negative.

If $i \in S$, the coalition already gets the maximum possible surplus, and can increase the payoff by decreasing the payment.
To do so, all of them must bid below the second highest bid in the original auction.
Of course, this will have the desired effect only if the second highest-valuation bidder is also in $S$.

The maximum decrease in payment can be achieved if $\forall j \in S \backslash \\{i\\} \ b_j \le \max_{n \in N \backslash S} v_n$.
As a trivial example, if $S = N$, all players except $i$ might bid 0, effectively eliminating the payment.

So, the subset $S$ of players can effectively collude and increase their collective payoff if and only if first and second highest-valuation bidders are in $S$.

(c) Let's fix a player $i$.
In Vickrey auction, non-truthful bidding by $i$ changes the outcome in two cases (other players' actions fixed):
* $i$ doesn't win the auction and pays 0; then, overbidding leads to $i$'s victory, and $i$ pays above the valuation;
* $i$ wins the auction and pays below valuation; then, underbidding leads to $i$'s defeat, and $i$ pays 0.

To make truthful bidding dominant, we must thus require that in both cases $i$'s utility cannot increase by cheating:

$$
\displaylines{
\forall\ p_i \ge v_i\ u_i(0, 0) \ge u_i(v_i, p_i), \\
\forall\ p_i \le v_i\ u_i(0, 0) \le u_i(v_i, p_i).
}
$$

  ### Problem 3

(a) Well, GSP is non-DSIC since it doesn't use the payments from the Myerson's lemma, so some valuations must lead to non-truthful reporting.
Let's construct one.

Assume WLOG $v_1 > v_2 > \dots v_n$, all players start by bidding truthfully, the winner $i$ gets $\alpha_i (v_i - v_{i+1})$.
Overbidding can only make the payoff negative in this setup, so we need to investigate underbidding.

If player $1$ bids $v_3 < b_1 < v_2$, they receive $\alpha_2 (v_1 - v_3)$.
Let's find such relationship between $v_1$, $v_2$, and $v_3$ that their payoff increases:

$$
\alpha_2 (v_1 - v_3) > \alpha_1 (v_1 - v_2) \Rightarrow v_1 < \frac{\alpha_1 v_2 - \alpha_2 v_3}{\alpha_1 - \alpha_2}.
$$

Since $\frac{\alpha_1 v_2 - \alpha_2 v_3}{\alpha_1 - \alpha_2} > \frac{\alpha_1 v_2 - \alpha_2 v_2}{\alpha_1 - \alpha_2} = v_2,$ the inequality $v_2 < v_1 < \frac{\alpha_1 v_2 - \alpha_2 v_3}{\alpha_1 - \alpha_2}$ is satisfied for some non-empty set of $v_1$'s, so we've just constructed a set of valuations that make GSP auction non-truthful.

(b) *[intentionally left blank]*

(c) *[intentionally left blank]*

(d) Let $l \in \\{1,\ \dots,\ n-1\\}$. Let's substitute local envy-free conditions a few times:

* $i \to l$, $j \to l+1$:

$$
\alpha_l (v_l - b_{l+1}) \ge \alpha_{l+1} (v_l - b_{l+2})
\Rightarrow
(\alpha_l - \alpha_{l+1}) v_l \ge \alpha_l b_{l+1} - \alpha_{l+1} b_{l+2};
$$

* $i \to l+1$, $j \to l$:

$$
\alpha_{l+1} (v_{l+1} - b_{l+2}) \ge \alpha_l (v_{l+1} - b_{l+1})
\Rightarrow
\alpha_l b_{l+1} - \alpha_{l+1} b_{l+2} \ge (\alpha_l - \alpha_{l+1}) v_{l+1}.
$$

We assumed $\alpha_l - \alpha_{l+1} > 0$, so $v_l \ge \frac{\alpha_l b_{l+1} - \alpha_{l+1} b_{l+2}}{\alpha_l - \alpha_{l+1}} \ge v_{l+1}$, and $v_1 \ge v_2 \ge \dots \ge v_n$.

Let now  $l \in \\{1,\ \dots,\ n - 2\\}$.
Substitute local envy-free conditions with $i \to l+1$, $j \to l+2$:

$$
\displaylines{
\alpha_{l+1} (v_{l+1} - b_{l+2}) \ge \alpha_{l+2} (v_{l+1} - b_{l+3})
\Rightarrow
\frac{\alpha_{l+1} b_{l+2} - \alpha_{l+2} b_{l+3}}{\alpha_{l+1} - \alpha_{l+2}}
\le v_{l+1} \le v_{l} \\
\Rightarrow
\alpha_{l+1} (v_l - b_{l+2}) \ge \alpha_{l+2} (v_l - b_{l+3}).
}
$$

Combining with an inequality for $i \to l$, $j \to l+1$ (written above), we get $\alpha_l (v_l - b_{l+1}) \ge \alpha_{l+2} (v_l - b_{l+3})$, so the conditions hold for all $i$ and $j = i + 2$.

Let now $l \in \\{2,\ \dots,\ n-1\\}$.
Substitute local envy-free conditions with  $i \to l-1$, $j \to l-2$:

$$
\displaylines{
\alpha_{l-1} (v_{l-1} - b_{l}) \ge \alpha_{l-2} (v_{l-1} - b_{l})
\Rightarrow
\frac{\alpha_{l-2} b_{l-1} - \alpha_{l-1} b_{l}}{\alpha_{l-2} - \alpha_{l-1}}
\ge v_{l-1} \ge v_{l} \\
\Rightarrow
\alpha_{l-1} (v_{l} - b_{l}) \ge \alpha_{l-2} (v_{l} - b_{l}).
}
$$

Combining with an inequality for $i \to l$, $j \to l-1$ (not written above), we get $\alpha_l (v_l - b_{l+1}) \ge \alpha_{l-2} (v_l - b_{l})$, so the conditions hold for all $i$ and $j = i - 2$.

We can continue this process and show they hold for all $j \ne i$, and given bids vector is indeed globally envy-free.

(e) Let's fix $\alpha_j$'s and $v_i$'s, and, WLOG, assume $b_1 \ge b_2 \ge \dots \ge b_n$.

First, since allocation of a GSP auction equilibrium must coincide with that of a truthful auction, we can say that $v_1  \ge v_2 \ge \dots \ge v_{k+1}$. 

Next, since the payments of a GSP equilibrium coincide with those of a truthful auction, we can write

$$
p_i = b_{i+1} = \frac{1}{\alpha_k} \sum_{j=i}^k (\alpha_j - \alpha_{j+1}) v_{j+1},\ i \in \\{1,\ \dots,\ k\\}.
$$

Other $b_i$'s are arbitrary (but ordered). Let's now show that this vector of bids is locally envy-free.

First, let $i \in \\{1,\ \dots\ k-1\\}$ (for remaining $i$'s everything is trivial because alphas are 0):

$$
\displaylines{
\alpha_i (v_i - b_{i+1}) = \alpha_i v_i - \sum_{j=i}^k (\alpha_j - \alpha_{j+1}) v_{j+1}, \\
\alpha_{i+1} (v_i - b_{i+2}) = \alpha_{i+1} v_i - \sum_{j=i+1}^k (\alpha_j - \alpha_{j+1}) v_{j+1}, \\
\alpha_i (v_i - b_{i+1}) - \alpha_{i+1} (v_i - b_{i+2})
= (\alpha_i - \alpha_{i+1})(v_i - v_{i+1}) \ge 0 \\
\Rightarrow
\alpha_i (v_i - b_{i+1}) \ge \alpha_{i+1} (v_i - b_{i+2}).
}
$$

Similarly, for $i \in \\{2,\ \dots,\ k\\}$ (for remaining $i$'s everything is trivial because alphas are 0):

$$
\displaylines{
\alpha_i (v_i - b_{i+1}) = \alpha_i v_i - \sum_{j=i}^k (\alpha_j - \alpha_{j+1}) v_{j+1}, \\
\alpha_{i-1} (v_i - b_i) = \alpha_{i-1} v_i - \sum_{j=i-1}^k (\alpha_j - \alpha_{j+1}) v_{j+1}, \\
\alpha_i (v_i - b_{i+1}) - \alpha_{i-1} (v_i - b_i)
= (\alpha_i - \alpha_{i-1}) v_i + (\alpha_{i-1} - \alpha_i) v_i = 0 \\
\Rightarrow
\alpha_i (v_i - b_{i+1}) = \alpha_{i-1} (v_i - b_i).
}
$$

Thus, the bids vector is indeed locally envy-free.
We've previously shown that a locally envy-free bids vector is also envy-free (assuming strictly decreasing bids), which automatically makes it equilibrium.
So, there always exists an equilibrium in a GSP auction that matches truthful auction's allocation and payments.

### Problem 4

(a) A good review of FPTAS for the Knapsack problem: https://math.mit.edu/~goemans/18434S06/knapsack-katherine.pdf

(b) First let's note that the pseudo-polynomial time algorithm is inherently monotone, so we only need to show that bid scaling is monotone as well.
The bid scaling function can be written as $v_i^{\prime\prime} = \lceil \frac{v_i}{K} \rceil$ where $K = \frac{V \epsilon}{n}$.
When $V$ is fixed up front, this is a non-decreasong function of $v_i$, moreover, it does not depend on other bids and does not affect others' scaled bids.

(c) Things get a little trickier when $V = \max_i v_i$ because now some bidders might affect others' scaled bits when changing their bid.
Particlarly, the highest-bid bidder might decrease scaled bids of some bidders by increasing their bid even more.
I'll now give a conceptual example of how this can lead to a winning bidder losing by increasing their bid.

Imagine there are 5 bidders with scaled bids 5, 4, 4, 2, 2 and sizes $C - 2 \delta$, $\frac{C}{2}$, $\frac{C}{2}$, $\delta$, $\delta$ respectively, with $\delta \ll C$.
The pseudo-polynomial algorithm will choose bidders 1, 4, 5 as winners.

With certain original bids and choice of $\epsilon$, it might happen that if bidder 1 increases their bid, the new scaled bids would be as follows: 5, 4, 4, 1, 1.
Now, the pseudo-polynomial algorithm will choose bidders 2 and 3 as winners.

So we see that FPTAS allocation does not define a monotone allocation rule.

(d) :(

(e) The described allocation rule is not monotone because there can be situations in which a bidder who is originally winning can lose by increasing the bid.

Let's consider a conceptual example of how it can happen.

Imagine that in both knapsacks the winners were chosen via the greedy rule.
Let's consider some winner of the second knapsack who increases their bid in such a way that they become a greedy-rule winner of the first knapsack, blocking some other winners.
Under unfortunate circumstances, this can make the total surplus of this new group smaller than that of the highest bidder, who now becomes the winner of the first knapsack.
And under even more unfortunate circumstances, our bidder might not fit into the greedy-rule winners of the second knapsack.

Unfortunately I struggle with concrete numerical examples for this problem.

(f) :(

### Problem 5

(a) Let’s say we have a graph $G$ with a set of nodes $N = \\{1, 2, \dots, n\\}$, set of edges $M$, and weights $V = \\{v_1, v_2, \dots, v_n\\}$ associated with nodes.

Let’s associate each node $i$ with a bidder, each edge $m$ with a good, and each weight $v_i$ with bidder $i$’s valuation.
Also, let $T_i$ be the set of goods corresponding to the edges adjacent to node $i$. Since the maximum degree in this graph is $d$, the cardinality of $T_i$ is also at most $d$.

The maximum-weight independent set of $G$ is a set of nodes (bidders) that has a maximum total weight (social surplus) among those sets no two nodes of which are adjacent (among all feasible player sets).
So, finding the maximum-weight independent set of a graph with a maximum degree $d$ reduces to the problem of maximizing the social surplus of bidders who each desire a set $T_i$ of goods with cardinality at most $d$.
The former problem is known to be NP-hard, so the latter is also NP-hard.

(b) Consider a bidder $k$ in re-indexed array.
Let's say they modify their bid to  $b_k^\prime$ while other bids stay the same, and see how it affects their allocation:
* if $b_k^\prime$ is sufficiently high, $k$ will be considered at an earlier iteration with a broader set $X$ then initially, so they might get a chance to win something (if they weren't winning already), and $x_k$ can't decrease;
* if $b_k^\prime$ is sufficiently low, $k$ will be considered at a later iteration with a more narrow set $X$ than before, so they might lose the chance to win (if they were winning at all), and $x_k$ can't increase.

So, the algorithm defines a monotone allocation rule.

(с) When $d = 1$, the algorithm allocates each good to the bidder with the highest valuation among those who want that good, and the resulting surplus is maximum possible, which satisfies the relationship we're trying to prove.

Consider a case when $d > 1$.
On every iteration $i$, when the greedy algorithm chooses a winner with valuation $v_i$, it can "block" at most $d$ bidders that win in the optimum, each with a valuation less than or equal to $v_i$.
For example, let's say on iteration $i$ the goods $m_1$ and $m_2$ are still not allocated, and $b_i = 2$, $T_i = \\{m_1, m_2\\}$, $b_{i+1} = b_{i+2}= 1.99$, $T_{i+1} = \\{m_1\\}$, $T_{i+2} = \\{m_2\\}$.
Then, the greedy algorithm would allocate $m_1$ and $m_2$ to $i$ and "block" bidders $i+1$ and $i+2$ who have total valuation of $3.98$ and should be in optimal allocation instead of $i$.
Other bidders may also be "blocked" (say, $b_{i+3}$ who also wants $m_1$ with valuation $1.98$), but they don't win in the optimum.

Then, the social surplus of the greedy algorithm is $V_{\mathrm{greedy}} = \sum_{i \in S_{\mathrm{greedy}}} v_i$, and the maximum social surplus is

$$
V_{\mathrm{opt}} \le \sum_{i \in S_{\mathrm{greedy}}} d v_i = d V_{\mathrm{greedy}},
$$

so the greedy algorithm indeed gives the social surplus at least $\frac{1}{d}$ times that of the maximum possible.

### Problem 6

(a) Let's fix an arbitrary player $i$, their valuation $v_i$, and bidding strategies of other players $b_j(v_j) = \frac{n-1}{n} v_j$.

Let's try to optimize $i$'s expected utility $u_i$ w.r.t. the bid size $b$.
If all other players bid below $b$, $i$ wins and gets $v_i - b$, otherwise, $i$ gets 0.
We can write down $u_i(b)$ as the following integral:

$$
u_i(b) = \idotsint_V (v_i - b) \mathbf{d} \mathbf{v}\_{-i},
$$

where $V = \left\[0;\ \frac{n}{n-1} b \right\]^{n-1}$.

The integral calculation is trivial:

$$
u_i(b) = C (v_i - b) b^{n-1},\  C = \left(\frac{n}{n-1}\right)^{n-1}.
$$

Now we should maximize $u_i$ to find $i$'s best response.
We do it by solving $u_i^\prime(b) = 0$:

$$
u_i^\prime(b)
    = - C b^{n-1} + C (n-1) (v_i - b) b^{n-2}
    = C \left\[(n - 1) v_i - nb\right\] b^{n-2}.
$$

$b = 0$ is not of much interest, so the final best-response bidding rule is

$$
b_i(v_i) = \frac{n-1}{n} v_i.
$$

Since $i$ was selected arbitrarily, same logic applies for other players as well, and the profile $\left( \frac{n-1}{n} v_1, \dots, \frac{n-1}{n} v_n \right)$ is indeed a Bayes-Nash equilibrium in a first-price auction.

(b) First, let's prove a helpful lemma.

**Lemma**. If $\\{x_1, \dots, x_n\\}$ are i.i.d. draws from $\mathrm{Unif}(0, a)$, then $\mathbb{E}\[\max_i x_i\] = \frac{n}{n+1} a$.

**Proof**.

$$
\displaylines{
\mathbb{E}\[\max_i x_i\]
    = \sum_i \mathbb{E}\[x_i \mid \forall j \ne i\ x_i > x_j\]
    = n \cdot \mathbb{E}\[x_1 \mid \forall j \ne 1\ x_1 > x_j\] \\
    = n \int_0^a x_1 \prod_{j \ne i} \left( \int_0^{x_1} \mathrm{d}x_j \right) \mathrm{d}x_1
    = n \int_0^a x_1^n \mathrm{d}x_1
    = \frac{n}{n+1} x_1^{n+1} \bigg|\_0^a
    = \frac{n}{n+1}a.
}
$$

Now, we can use this lemma to find expected revenues of first-price and second-price auctions.

In a *first-price auction*, revenue equals $\max_i b_i$.
In BNE, $b_i = \frac{n-1}{n} v_i$, and since $v_i \sim \text{Unif}(0, 1)$,

$$
b_i \sim \text{Unif}\left(0, \frac{n-1}{n}\right)
\Rightarrow
\mathbb{E}\[\max_i b_i\] = \frac{n}{n+1} \frac{n-1}{n} = \frac{n-1}{n+1}.
$$

In a *second-price auction*, revenue equals to the second-largest bid, and under truthful bidding $b_i = v_i$.

Let $b=\max_i b_i$ be the largest bid in this auction.
We can say that the rest $n-1$ bids are sampled i.i.d. from $\mathrm{Unif}(0, b)$.
By our lemma, the expected value of the largest of them (which is a second-largest bid overall) is $\frac{n-1}{n} b$.
The expected value of this expression (applying our lemma one more time)

$$
\mathbb{E}\left\[\frac{n-1}{n} b\right\]
    = \frac{n-1}{n} \mathbb{E}\left\[\max_i b_i\right\]
    = \frac{n-1}{n} \frac{n}{n+1} = \frac{n-1}{n+1}
$$

gives us the expected revenue in a second-price auction, which equals to the expected revenue of a first-price auction derived above.

(c) I'll break down the solution into 4 steps: useful integral, general FPA BNE bidding derivation, FPA expected revenue and SPA expected revenue.

**Step 0.**
Let's evaluate the following integral, which will come in handy in further steps:

$$
I_k = \int_0^1 x F(x)^k f(x) \mathrm d x.
$$

Let's use integration by parts.
Set $u = x F(x)^k$, $\mathrm d v = f(x) \mathrm d x$.
Then, $\mathrm d u = (F(x)^k + k x F(x)^{k-1} f(x)) \mathrm d x$, $v = F(x)$, and

$$
\displaylines{
I_k
    = x F(x)^{k+1} \Big|\_0^1 - \int_0^1 F(x)^{k+1} \mathrm d x - \int_0^1 k x F(x)^k f(x) \mathrm d x \\
    = 1 - \int_0^1 F(x)^{k+1} \mathrm d x - k I_k.
}
$$

From here, we have

$$
I_k = \frac{1}{k+1} \left(1 - \int_0^1 F(x)^{k+1} \mathrm d x\right).
$$

**Step 1.**
Let's try to find a symmetric BNE, i.e., some bidding function $b(\cdot)$ that all the bidders follow.
We will assume that $b$ is strictly increasing and that $b(0) = 0$.

Let's fix an arbitrary player $i$ who can submit an arbitrary valuation $x$, while other bidders submit their true valuations.
$i$'s expected utility is then

$$
\displaylines{
u_i(x)
    = (v_i - b(x)) \mathbb P \[\forall j \ne i\ b(x) > b(v_j)\]
    \underset{\text{$b$ is increasing}}{=} (v_i - b(x)) \mathbb P \[\forall j \ne i\ x > v_j\] \\
    = (v_i - b(x)) \left(\int_0^x f(t) \mathrm d t\right)^{n-1}
    = (v_i - b(x)) F(x)^{n-1}.
}
$$

Now, in symmetric equilibrium all the players submit their true valuations into the bidding strategy, so $i$'s expected utility must be maximized when $x = v_i$, or

$$
\displaylines{
0
    = u_i^\prime (x) \big|\_{x=v_i}
    = -b^\prime(v_i) F(v_i)^{n-1} + (v_i - b(v_i)) (F^{n-1})^\prime(v_i) \\
    \Rightarrow
    b^\prime(v_i) F(v_i)^{n-1} + b(v_i) (F(v_i)^{n-1})^\prime = v_i (F^{n-1})^\prime(v_i) \\
    \Rightarrow
    \left\[ b(v_i) F(v_i)^{n-1} \right\]^\prime = v_i (F^{n-1})^\prime(v_i).
}
$$

Remember that our unknown is $b$, so let's rename $v_i$ to $x$ in the last equation and integrate it from $0$ to $v_i$ (recall that $b(0) = 0$):

$$
\displaylines{
b(v_i) F(v_i)^{n-1}
    = \int_0^{v_i} x (F^{n-1})^\prime(x)\mathrm d x
    = (x F(x)^{n-1}) \big|\_0^{v_i} - \int_0^{v_i} F(x)^{n-1} \mathrm d x \\
    \Rightarrow
    b(v_i) = v_i - \frac{\int_0^{v_i} F(x)^{n-1} \mathrm d x}{F(v_i)^{n-1}}.
}
$$

We also need to show that $u_i^\prime$ changes the sign at $x = v_i$.

$$
b^\prime(v_i)
    = 1 - \frac{F(v_i)^{2(n-1)} - (F^{n-1})^\prime(v_i)\int_0^{v_i} F(x)^{n-1} \mathrm d x}{F(v_i)^{2(n-1)}}
    = \frac{(F^{n-1})^\prime(v_i) \int_0^{v_i} F(x)^{n-1} \mathrm d x}{F(v_i)^{2(n-1)}},
$$

so 

$$
\displaylines{
u_i(x)
    = - \frac{(F^{n-1})^\prime(x) \int_0^{x} F(t)^{n-1} \mathrm d t}{F(x)^{2(n-1)}} F(x)^{n-1}
    + \left(v_i - x + \frac{\int_0^{x} F(t)^{n-1} \mathrm d t}{F(x)^{n-1}} \right) (F^{n-1})^\prime(x) \\
    = (v_i - x) (F^{n-1})^\prime(x),
}
$$

which indeed is positive when $x < v_i$ and negative when $x > v_i$.

The function we found isn't really defined at $v_i = 0$, but $b(v_i) \to 0$ as $v_i \to 0$ (left as an exercise to the reader), so we may use its continuous extension.
Besides that, $F$ is non-negative and $f$ is positive on $\[0; 1\]$, so $b(v_i)^\prime$ is also positive and $b$ is indeed strictly increasing.

**Step 2.**
The expected revenue of the first-price auction equals the expected value of the maximum of $n$ bids:

$$
\displaylines{
\mathbb E \[R_{\mathrm{FPA}}\]
    = \sum_i \mathbb E \[b(x_i) \mid \forall j \ne i\ b(x_i) > b(x_j)\]
    \underset{\text{$b$ is increasing}}{=} n \mathbb E \[b(x_1) \mid \forall j > 1\ x_1 > x_j\] \\
    = n \int_0^1 b(x) \left( \int_0^x f(t) \mathrm d t \right)^{n-1} f(x) \mathrm d x
    = n \int_0^1 \left(
        x - \frac{\int_0^x F(t)^{n-1} \mathrm d t}{F(x)^{n-1}}
    \right) F(x)^{n-1} f(x) \mathrm d x \\
    = n \left\[I_{n-1} - \int_0^1 \left(\int_0^x F(t)^{n-1} \mathrm d t \right) f(x) \mathrm d x \right\]
    = 1 - \int_0^1 F(x)^n \mathrm d x - n \int_0^1 \left(\int_0^x F(t)^{n-1} \mathrm d t \right) f(x) \mathrm d x.
}
$$

Let's compute the last integral by parts.
Set $u = \int_0^x F(t)^{n-1} \mathrm d t$, $\mathrm d v = f(x) \mathrm d x$.
Then, $\mathrm d u = F(x)^{n-1} \mathrm d x$, $v = F(x)$, and

$$
\int_0^1 \left(\int_0^x F(t)^{n-1} \mathrm d t \right) f(x) \mathrm d x
    = \left(F(x)  \int_0^x F(t)^{n-1} \mathrm d t \right) \bigg|\_0^1
    - \int_0^1 F(x)^n \mathrm d x
    = \int_0^1 F(x)^{n-1} \mathrm d x - \int_0^1 F(x)^n \mathrm d x.
$$

Finally,

$$
\mathbb E \[R_{\mathrm{FPA}}\] = 1 + (n-1) \int_0^1 F(x)^n \mathrm d x - n \int_0^1 F(x)^{n-1} \mathrm d x.
$$

**Step 3.**
Since bids are truthful, the expected revenue of the second-price auction equals the expected value of the second-highest value among $n$ valuations:

$$
\displaylines{
\mathbb E \[R_{\mathrm{SPA}}\]
    = \sum_i \sum_{j \ne i} \mathbb E \[ x_i \mid x_i < x_j \land \forall k \ne i,j\ x_i > x_k \]
    = n (n - 1) \mathbb E \[ x_1 \mid x_1 < x_2 \land \forall k > 2\ x_i > x_k \] \\
    = n (n - 1) \int_0^1
	       x
	       \left( \int_x^1 f(t) \mathrm d t \right)
	       \left( \int_0^x f(t) \mathrm d t \right)^{n-2}
	       f(x) \mathrm d x
    = n (n - 1) \int_0^1 x (1 - F(x)) F(x)^{n - 2} f(x) \mathrm d x \\
    = n (n - 1) (I_{n-2} - I_{n-1})
    = n (n - 1) \left\[
        \frac{1}{n - 1} \left(1 - \int_0^1 F(x)^{n-1} \mathrm d x\right)
        - \frac{1}{n} \left(1 - \int_0^1 F(x)^n \mathrm d x\right)
    \right\] \\
    = n \left(1 - \int_0^1 F(x)^{n-1} \mathrm d x\right)
    - (n - 1) \left(1 - \int_0^1 F(x)^n \mathrm d x\right) 
    = 1 + (n - 1) \int_0^1 F(x)^n \mathrm d x - n \int_0^1 F(x)^{n-1} \mathrm d x.
}
$$

We see that the expected revenues of first-price and second-price auctions are indeed equal.
