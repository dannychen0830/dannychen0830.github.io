<script
  src="https://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-AMS-MML_HTMLorMML"
  type="text/javascript">
</script>

[Back](./blog.md)

## Interesting(-ish) Interview Question

So, while I was looking for jobs this summer, I encountered this question: _If I give you samples from a uniform distribution distributed along the interval $$(0, d)$$, how do you find $d$?_ 

My nervous adrenaline-packed brain started its scambled search through my statistics database. I immediately replied: "I remember that the maximum likelihood estimate for $$d$$ is the max out of all samples." I was quite confident in this answer as I can still recall some details in the derivation. However, the interviewer rejected my answer (politely, of course) and asked me to think about the expectation of the uniform distribution. The second answer became obvious given this hint: the expectation of a uniform distribution with support $$(0,d)$$ is $$d/2$$ and the typical averaging would do the job (upon rescaling). 

I was a bit bamboozled because maximum likelihood estimates are, well, _maximum likelihood_ estimates. If we're given a uniform distribution without specifying the lower bound, the trick would not have worked. I thought to myself, as the interviewer had spent more time on this question than I had, he's probably right. And we moved on. 

So, I'll dedicate this blog to finding out who's more right. I'll present three views before presenting the big reveal. _If you're reading this page and find anything wrong with the following calculations, please let me know and I would be happy to fix/try out your suggestion_. 

With that being said, let's begin with a formal problem statement: given $$n$$ i.i.d. samples of random variable $$X$$ that is uniformly distributed along the support $$(0,d)$$, where $$d$$ is uknown, estimate $$d$$. 

### Method 1: Maximum likelihood 

We assumed i.i.d. samples (makes my life easy), meaning that the likelihood function looks like the product of marginals. 

\begin{align}
\mathcal L(d) &= \prod_{i=1}^n \frac{1}{d} 1_{(0,d)}(x_i) \\
&= \frac{1}{d^n} \prod_i 1_{(x, \infty)}(d) \\
&= \frac{1}{d^n} 1_{(\max \{x_i: i \in [n]\})}(d)
\end{align}

where $1_A(x)$ is the indicator function ($$1$$ if $$x \in A$$ and $$0$$ otherwise). The second equality is by squinting: we get $$1$$ if $$0 \leq x_i \leq d$$, or equivalently in the $d$-parameter-space, $$x_i \leq d < \infty$$. The third equality is by noticing that only the biggest $$x_i$$ win. We want the maximum likelihood estimate, which I'll denote with a rather weird (but less confusing notation because I don't want $$d$$'s floating all over) $$\mathcal E_1$$ for being the first estimate I write down. 

$$ \mathcal E_1 = \max_{d \in \mathbb R} \mathcal L(d)

Notice that the likelihood function is $$0$$ before $$\max \{x_i\}$$ and monotonically decreasing (and positive) for $$d > \max \{x_i\}$$, so the maximum occurs if we catch it first jumping up to something non-zero and before it starts eroding away. 

$$ \mathcal E_1 = \max \{x_i: i \in [n]\}$$ 

Great! My memory was performing well despite having to catch a flight at 7 in the morning. Now, we want to look at how good this estimator is. To do so, we would look at the probability that our estimate lies outside of the true parameter by some $$\epsilon$$. For the MLE, we can use some results from order statistics (or by basic probability arguments).

$$\mathbb P (\mathcal E_1 > x) = 1 - \mathbb P (X \leq x)^n$$

So: 

\begin{align}
\mathbb P(\vert \mathcal E_1 - d \vert < \eosilon) &= \mathbb P(\mathcal E_1 > d - \epsilon) \\
&= 1 - \mathbb (X \leq d - \epsilon)^n \\
&= 1 - \left(1 - \frac{\epsilon}{d})^n
\end{align}

We actually got quite a good bound (in fact, an exact and non-asymptotic one!) describing how $$\mathcal E_1$$ behaves: the probability that the deviation is larger than some $$\epsilon$$ decreases exponentially with $$n$$. That's darn fast! My intuition says that this is hard to beat, but we can't declare winners just yet without a fair treatment of the interviewer's proposal. 
