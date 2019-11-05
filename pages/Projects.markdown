Code Projects
-------------

![](/static/img/linaia-cc.png)

**Linaia-Agon** \[[code](https://github.com/gjoncas/Xenakis)\]<br>
Iannis Xenakis\'s musical piece *Linaia-Agon* consists of four zero-sum games.<br>
The games correspond to a mythical duel between Linus and Apollo.<br>
Moves in each game matrix correspond to a musical note or passage.<br>
A natural question is: what are Linus\'s odds of winning? (Hint: very low.)<br>
By simulating many duels (under various parameterizations), we can answer this.
<br><br>

![](/static/img/currency-graph-tiny.png)

**Rbitrage**<br>
If you trade $1 to euros and back, you get $1. With many currencies, you can get more than $1.<br>
So we can profit from misaligned exchange rates. This program maximizes arbritrage profits.<br>
Currencies are a graph, edges are exchange rates — can solve using shortest path algorithms.<br>
By searching for negative cycles, the Bellman-Ford algorithm solves the problem in O(n^3^) time.
<br><br>

![](/static/img/simplex-tiny.png)

**A Rose for Emily** \[[code](https://github.com/gjoncas/A-Rose-for-Emily)\]<br>
Using constraint solving in Prolog to analyze non-linear timeslines in stories.<br>
Faulkner\'s story contains various events, plus inter-temporal references.<br>
Encode these as equations: if A happened 6 years before B, then A+6=B.<br>
The constraint solver shows which orderings of events are consistent.<br>
This method formally shows the virtuality of a story—its simplex of meaning.
<br><br>

![](/static/img/neural-net-tiny.png)

**Mapping Poverty** \[[slides](https://github.com/gjoncas/Computational-Economics/blob/master/neural%20networks.pdf)\]<br>
Hour-long lecture on the use of neural networks in development economics.<br>
Explains neural nets for economists, through analogies with OLS regression.<br>
Surveys research at MIT using convolutional neural nets to estimate GDP.<br>
Plan to use in future research (based on my MA thesis) on China\'s poverty counties.
<br><br>

![](/static/img/genetic-algos-tiny.png)

**Genetic Algorithms and Taxes** \[[survey](https://github.com/gjoncas/Computational-Economics/blob/master/genetic%20algorithms.pdf)\]<br>
Genetic algorithms solve problems by computational Darwinism.<br>
Solutions ‘compete’ with each other, judged by a fitness function.<br>
Over generations, candidate solutions evolve toward an optimum.<br>
Good for problems where data is unavailable—like tax evasion.
