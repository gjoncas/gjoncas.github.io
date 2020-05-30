Code Projects
-------------

<table>
    <thead>
        <tr>
            <th></th>
            <th><br>**Linaia-Agon** <span style="font-weight:normal">\[[code](https://github.com/gjoncas/Xenakis)\]</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td rowspan=5>![](/static/img/linaia-cc.png)</td>
            <td>Iannis Xenakis\'s musical piece *Linaia-Agon* consists of 4 zero-sum games.</td>
        </tr>
        <tr>
            <td>The games correspond to a mythical duel between Linus and Apollo.</td>
        </tr>
        <tr>
            <td>Moves in each game matrix correspond to a musical note or passage.</td>
        </tr>
        <tr>
            <td>A natural question is: what are Linus\'s odds of winning? (Hint: very low.)<br>
			    By simulating many duels (under various parameters), we can answer it.</td>
        </tr>
    </tbody>
</table>


<table>
    <thead>
        <tr>
            <th></th>
            <th><br>**Rbitrage** <span style="font-weight:normal"></th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td rowspan=4><span style="color:white"><\span>![](/static/img/currency-graph.png)<span style="color:white">.<\span></td>
            <td>Trading $1 to euros and back: get $1. Many currencies: can get over $1.</td>
        </tr>
        <tr>
            <td>This program finds maximum profits from misaligned exchange rates.</td>
        </tr>
        <tr>
            <td>Currencies are a graph, edges are exchange rates – use graph algorithms.<br>
			    Shortest path algorithm (Bellman-Ford) finds negative cycles in O(n^3^) time.</td>
        </tr>
    </tbody>
</table>



<table>
    <thead>
        <tr>
            <th></th>
            <th><br>**A Rose for Emily** <span style="font-weight:normal">\[[code](https://github.com/gjoncas/A-Rose-for-Emily)\] 
				\[[blog](https://gjoncas.github.io/posts/2019-11-07-a-rose-for-emily.html)\]</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td rowspan=5>![](/static/img/simplex-tiny.png)</td>
            <td>Constraint solving in Prolog to analyze non-linear timeslines in stories.</td>
        </tr>
        <tr>
            <td>Faulkner\'s story contains various events, plus inter-temporal references.</td>
        </tr>
        <tr>
            <td>Encode these as equations: if A happened 6 years before B, then A+6=B.<br></td>
        </tr>
        <tr>
            <td>The constraint solver shows which orderings of events are consistent.<br>
			    This method formally shows a story\'s virtuality, or simplex of meaning.</td>
        </tr>
    </tbody>
</table>

<table>
    <thead>
        <tr>
            <th></th>
            <th><br>**Mapping Poverty** <span style="font-weight:normal">
			    \[[slides](https://github.com/gjoncas/Computational-Economics/blob/master/neural%20networks.pdf)\]</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td rowspan=5>![](/static/img/neural-net-tiny.png)</td>
            <td>Hour-long lecture on using neural networks in development economics.</td>
        </tr>
        <tr>
            <td>Explains neural nets for economists, by analogies with OLS regression.</td>
        </tr>
        <tr>
            <td>Surveys research at MIT using convolutional neural nets to estimate GDP.</td>
        </tr>
        <tr>
            <td>Shows how satellite images can proxy for GDP in countries without data.<br>
			    Plan to use in research (based on my thesis) on China\'s poverty counties.</td>
        </tr>
    </tbody>
</table>



<table>
    <thead>
        <tr>
            <th></th>
            <th><br>**Genetic Algorithms and Taxes** <span style="font-weight:normal">
			        \[[survey](https://github.com/gjoncas/Computational-Economics/blob/master/genetic%20algorithms.pdf)\]<br></th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td rowspan=5>![](/static/img/genetic-algos-tiny.png)</td>
            <td>Genetic algorithms solve problems by computational Darwinism.</td>
        </tr>
        <tr>
            <td>Solutions ‘compete’ with each other, judged by a fitness function.</td>
        </tr>
        <tr>
            <td>Over generations, candidate solutions evolve toward an optimum.</td>
        </tr>
        <tr>
            <td>Good for problems where data is unavailable—like tax evasion.</td>
        </tr>
    </tbody>
</table>