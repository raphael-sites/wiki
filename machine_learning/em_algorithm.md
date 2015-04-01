### EM Algorithm

<h3 id="General-formulation">General formulation<a class="anchor-link" href="#General-formulation">&#182;</a></h3><p>Recall <strong>Jensen's inequality</strong>:</p>
<blockquote><p>Let $f$ be a convex function (<em>i.e.</em> $f^{\prime\prime} \ge 0$) of a random variable X. Then:
$f(E[X]) \le E[f(X)]$</p>
</blockquote>
<p>And when $f$ is <em>strictly</em> convex, then:</p>
$$E[f(X)] = f(E[X]) \iff X = E[X]$$<p>with probability 1.</p>
<p>Consider again the joint density $P(x,z|\theta)$, where only $x$ is observed. We want to be able to maximize:</p>
$$\begin{aligned}
l(x \,|\, \theta) &= \sum_i \log P(x_i \,|\, \theta) \\
&= \sum_i \log \sum_{z_i} P(x_i, z_i \,|\, \theta)
\end{aligned}$$<p>however, evaluating this is difficult when the $\{z_i\}$ are unobserved.</p>
<p>The EM algorithm iteratively calculates <em>lower bounds on the likelihood</em> for the current values of the parameters, then <em>maximizes the lower bound</em> to update the parameters.</p>
<p>Since $z_i$ is a random variable, perhaps we can construct its density $Q_i$ and use it to marginalize the joint likelihood:</p>
$$\sum_i \log \sum_{z_i} P(x_i, z_i \,|\, \theta) = \sum_i \log \sum_{z_i} Q_i(z_i) \frac{P(x_i, z_i \,|\, \theta)}{Q_i(z_i)}$$<p>This turns the inner summation into an expectation.</p>
$$\sum_i \log \sum_{z_i} Q_i(z_i) \frac{P(x_i, z_i \,|\, \theta)}{Q_i(z_i)} = \sum_i \log E_{Q_i} \left[ \frac{P(x_i, z_i \,|\, \theta)}{Q_i(z_i)} \right]$$<p>Now, if we apply Jensen's inequality:</p>
$$\begin{aligned}
\sum_i \log E_{Q_i} \left[ \frac{P(x_i, z_i \,|\, \theta)}{Q_i(z_i)} \right] &\ge \sum_i  E_{Q_i} \log \left[ \frac{P(x_i, z_i \,|\, \theta)}{Q_i(z_i)} \right] \\
&= \sum_i \sum_{z_i}  Q_i(z_i) \log \left[ \frac{P(x_i, z_i \,|\, \theta)}{Q_i(z_i)} \right]
\end{aligned}$$<p>We need to ensure that the equality condition holds true, which we can do by choosing $Q_i$ appropriately. Specifically, we want a $Q_i$ such that:</p>
$$\frac{P(x_i, z_i \,|\, \theta)}{Q_i(z_i)} = C$$<p>which implies:</p>
$$Q_i(z_i) \propto P(x_i, z_i \,|\, \theta)$$<p>Since $Q_i$ is a density,</p>
$$\begin{aligned}
Q_i(z_i) &= \frac{P(x_i, z_i \,|\, \theta)}{\sum_{z_i} P(x_i, z_i \,|\, \theta)} \\
&= \frac{P(x_i, z_i \,|\, \theta)}{P(x_i \,|\, \theta)} \\
&= P(z_i \,|\, x_i, \theta)
\end{aligned}$$

# References
- http://nbviewer.ipython.org/github/fonnesbeck/Bios366/blob/master/notebooks/Section3_3-Expectation-Maximization.ipynb
- https://www.cs.utah.edu/~suyash/Dissertation_html/node9.html