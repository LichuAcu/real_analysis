# Axioms of the reals

*Pages 9-16 in the book.*

The reals form an *ordered* field. We have two binary operations (addition and multiplication) under each of which the reals form an <u>abelian group</u> (associative, commutative, identity, inverse). These two operations are linked by the distributive property (axiom): $a(b+c)=ab+ac$, $(b+c)a = ba + ca$. Note that by commutativity, both results are the same.

For this field to be ordered, we need the <u>order axiom</u>. This states that there exists a set $P \subset \r$ (the "positives") such that $a,b \in P \implies a+b, ab \in P$ and for any $a \in \r$ either $a \in P, a = 0, \text{or} -a \in P$ (**exactly** one). The usual order operations, such as $a > b$, are defined in terms of this, this one meaning $a - b \in P$ (note $a-b$ means $a$ plus the additive inverse of $b$).

We are not done yet! Observe that the rational numbers also satisfy all these axioms. To separate the reals from the rationals, we need the <u>least upper bound axiom</u>, also known as the completeness axiom. This axiom implies that there are no "wholes" in the reals. Formally, it claims that for any set $S \subset \r$ bounded above there exists a *supremum* $a \in \r$ (not necessarily in $S$), also known as least upper bound. The supremum $a$ is an upper bound for $S$ such that if $b$ is an upper bound for $S$, then $b \leq a$. Think of the set $S = \{x: x^2 < 2\}$. In the reals, we see (but shall prove!) that $\sqrt{2}$ is a (the) supremum of $S$. Note that if we were in the rationals, there would be no supremum for this set.

<u>Observation:</u> a statement equivalent to the LUB axiom, and usually more useful, is that a least upper bound $a$ of the set $S$ is an upper bound of $S$ such that if $b < a$, there exists $x \in S$ with $b < x$ (since $b$ is not an upper bound of $S$).

<u>Observation:</u> note that addition and multiplication are only defined for two elements. This is, $a+b+c$ is not properly defined. However, thanks to the associative property, we know $(a+b)+c = a+(b+c)$ (now we are thinking of $(a+b)$ and $(b+c)$ as single elements), and therefore by $a+b+c$ we simply mean any of those. We can inductively extend this to any number of elements in our operation.

<u>Next step:</u> we will now draw some consequences from these axioms, paying special attention to the LUB axiom. The order we will follow is important, as we will have *LUB $\implies$ MCP $\implies$ Bolzano-Weierstrass $\implies$ things about Cauchy sequences*. As we saw, the rationals $\mathbb{Q}$ do not satisfy LUB, therefore they will not necessarily satisfy this consequences.

# Monotone convergence property

*Page 50 in the book.*

<u>Theorem:</u> a monotone sequence $\{a_n\}$ is convergent if and only if $\{a_n\}$ is bounded.

We will suppose $\{a_n\}$ is increasing. Similar procedures prove the result for a decreasing $\{a_n\}$.

Convergent $\implies$ bounded is easy to see, as wee can pick $\eps = 1$ (or any other positive value), get $N$ such that $|a_n - L| \leq 1$ for all $n \geq N$, and then $max\{a_1,\ldots,a_{n-1},1+L\}$ is an upper bound for our sequence. The lower bound is $a_1$.

Bounded $\implies$ convergent is a bit more interesting. **By the least upper bound axiom**, the set of all the elements in the sequence, i.e. $X = \{a_n : n \in \mathbb{N}\}$, has a least upper bound $L \in \r$. Given $\eps > 0$, we know that $L - \eps$ is *not* an upper bound for $X$ (since $L$ is the *least* upper bound), therefore there is $N$ such that $L - \eps < a_N$. Since $\{a_n\}$ is increasing, for any $n \geq N$ we have $a_N \leq a_n$, hence for $n \geq N$ we have $L - \eps < a_N \leq a_n \leq L < L + \eps$. Then, $\{a_n\}$ converges to $L$.

# Bolzano-Weierstrass theorem

*Pages 58-59 in the book.*

<u>Theorem:</u> every bounded real sequence $\{a_n\}$ has a convergent subsequence.

It would be interesting if we could find a *monotone* subsequence of $\seq$, so we can apply MCP. I have the intuition that this is possible to do, although our proof will be different.

The key behind the proof is that, if we split the interval where $\seq$ takes values into halves, at least one of them will have infinitely many elements of $\seq$. Then we can split that half into halves, and the same will happen. We keep splitting these halves into more halves, getting exponentially small *nested* intervals each containing infinitely many elements of $\seq$, which allows us to create a subsequence $\{a_{n_k}\}$ with the $k$-th element being in the $k$-th interval. We see **by the monotone convergence property** that the sequences $\seq[b]$ and $\seq[c]$ formed by the lower and uppers limits of these intervals respectively form monotone bounded sequences in $\r$, so they converge, and in particular they converge to the same limit $L$. By the squeeze theorem (not difficult to prove) we therefore get that $\{a_{n_k}\}$ also converges to $L$.

A visual intuition (using different notation):

![proof|450](https://upload.wikimedia.org/wikipedia/commons/thumb/7/7a/Bolzano%E2%80%93Weierstrass_theorem_-_step_7.svg/1200px-Bolzano%E2%80%93Weierstrass_theorem_-_step_7.svg.png)

Refer to the book for the complete proof.

# Properties of Cauchy sequences

*Pages 59-61 in the book.*

A sequence $\seq$ is Cauchy if for every $\eps > 0$ there exists $N$ such that for all $m,n \geq N$ we have $|a_m - a_n| < \eps$.

It is not difficult to see that any convergent sequence is Cauchy, using $\eps / 2$ in the definition of convergence and using the obtained $N$ in the Cauchy condition. The converse is also true: any Cauchy sequence is convergent.

<u>Theorem:</u> Cauchy $\iff$ convergent.

We now want to show Cauchy $\implies$ convergent. If $\seq$ is Cauchy, we see that $\seq$ is bounded using similar logic to the one we used to prove convergence $\implies$  bounded. For $\eps = 1$ and its corresponding $N$, we have for all $n \geq N$ that $|a_n - a_N| < 1$ (we are using $N$ as $m$ in the definition of the Cauchy condition, which is perfectly valid) hence $|a_n| \leq |a_n - a_N| + |a_n| < 1 + |a_N|$ (we use triangle inequality here, but this should look intuitive!). Therefore, $\seq$ is bounded by $max\{|a_1|, \ldots, |a_{N-1}|, 1 + |a_n|\}$. Note that the definition of bound we are using here is $B$ such that $|a_n| \leq B$ for all $n$ (i.e., we are looking at the absolute value, or in other words at the interval $[-B,B]$).

Now that $\seq$ is bounded, we can **use the Bolzano-Weierstrass theorem** to get a *convergent* subsequence $\subseq$, with limit $L$. It should now seem intuitive that $\seq$ itself also converges to $L$. For $\eps > 0$, we use $\eps / 2$ in the Cauchy property and get $N'$ such that $|a_m - a_n| < \eps/2$ for $m,n \geq N'$. We also use $\eps /2$ in the definition of convergence and get $N''$ such that $a_{n_k} - L < \eps / 2$ for $k \geq N''$. To combine these two properties, let $K = max\{N',N''\}$. Note that for any $k$ we have $n_k \geq k$, therefore $K \geq N' \implies n_K \geq K \geq N' \implies n_K \geq N'$. Then for any $n \geq N'$, we have $|a_n - L| \leq |a_n - a_{n_K}| + |a_{n_K} - L| < \eps/2 + \eps/2 = \eps$, which completes the proof.

<u>Personal note:</u> this last step may be a bit confusing, so take your time to digest it. Since $a_{n_k}$ vanishes, it may seem that it is irrelevant, but it is not! We have that $a_n$ is close to $a_{n_K}$ because of the Cauchy property (again, note $n_K \geq K \geq N'$ so we can use it), and $a_{n_K}$ is close to $L$ because $\subseq$ converges to $L$ and $K \geq N''$. Note that the choice of $K$ is "generous", i.e. it is not necessarily the smallest we could have made, since the only requirements for $K$ are $n_K \geq N'$ and $K \geq N''$. In particular, we are being generous with the first requirement. We made such choice of $K$ just for simplicity. We could have also just said 'choose (the smallest) $K$ such that $n_K \geq N'$ and $K \geq N''$', which we know exists simply because $n_K$ goes to infinity as $K$ grows.

# Debrief

Note that all we did here is a consequence of the least upper bound axiom. As mentioned before, we proved *LUB $\implies$ MCP $\implies$ Bolzano-Weierstrass $\implies$ properties of Cauchy sequences*. Again, this shows the importance of this axiom, and reminds us that none of these properties (necessarily) hold in the rationals.

# Macros

$\newcommand{\r}{\mathbb{R}}$
$\newcommand{\eps}{\varepsilon}$
$\newcommand\seq[1][a]{\{#1_n\}}$
$\newcommand\subseq[1][a]{\{#1_{n_k}\}}$