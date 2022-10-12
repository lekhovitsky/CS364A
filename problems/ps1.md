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



### Problem 5



### Problem 6

(a) Let's fix an arbitrary player $i$, his valuation $v_i$, and bidding strategies of other players $b_j(v_j) = \frac{n-1}{n} v_j$.

Let's try to optimize $i$'s expected utility $u_i$ w.r.t. the bid size $b$.
If all other players bid below $b$, $i$ wins and gets $v_i - b$, otherwise, $i$ gets 0.
We can write down $u_i(b)$ as the following integral:

$$
u_i(b) = \idotsint_V (v_i - b) \mathbf{d} \mathbf{v}\_{-i},
$$

where $V = \left[0;\ \frac{n}{n-1} b \right]^{n-1}$.

The integral calculation is trivial:

$$
u_i(b) = C (v_i - b) b^{n-1},\  C = \left(\frac{n}{n-1}\right)^{n-1}.
$$

Now we should maximize $u_i$ to find $i$'s best response.
We do it by solving $u_i^\prime(b) = 0$:

$$
u_i^\prime(b)
    = - C b^{n-1} + C (n-1) (v_i - b) b^{n-2}
    = C \left[(n - 1) v_i - nb\right] b^{n-2}.
$$

$b = 0$ is not of much interest, so the final best-response bidding rule is

$$
b_i(v_i) = \frac{n-1}{n}v_i.
$$

Since $i$ was selected arbitrarily, same logic applies for other players as well, and the profile $\left( \frac{n-1}{n} v_1, \dots, \frac{n-1}{n} v_n \right)$ is indeed a Bayes-Nash equilibrium in a first-price auction.

(b) First, let's prove a helpful lemma.

**Lemma**. If $\\{x_1, \dots, x_n\\}$ are i.i.d. draws from $\mathrm{Unif}(0, a)$, then $\mathbb{E}[\max_i x_i] = \frac{n}{n+1}a$.

**Proof**.

$$
\displaylines{
\mathbb{E}[\max_i x_i]
    = \sum_i \mathbb{E}[x_i \mid \forall j \ne i\ x_i > x_j]
    = n \cdot \mathbb{E}[x_1 \mid \forall j \ne 1\ x_1 > x_j] \\
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
\mathbb{E}[\max_i b_i] = \frac{n}{n+1} \frac{n-1}{n} = \frac{n-1}{n+1}.
$$

In a *second-price auction*, revenue equals to the second-largest bid, and under truthful bidding $b_i = v_i$.

Let $b=\max_i b_i$ be the largest bid in this auction.
We can say that the rest $n-1$ bids are sampled i.i.d. from $\mathrm{Unif}(0, b)$.
By our lemma, the expected value of the largest of them (which is a second-largest bid overall) is $\frac{n-1}{n} b$.
The expected value of this expression (applying our lemma one more time)

$$
\mathbb{E}\left[\frac{n-1}{n} b\right]
    = \frac{n-1}{n} \mathbb{E}\left[\max_i b_i\right]
    = \frac{n-1}{n} \frac{n}{n+1} = \frac{n-1}{n+1}
$$

gives us the expected revenue in a second-price auction, which equals to the expected revenue of a first-price auction derived above.
