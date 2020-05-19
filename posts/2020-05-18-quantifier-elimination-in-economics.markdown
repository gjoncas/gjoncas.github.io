---
title: Quantifier Elimination in Economics
subtitle: Automated Reasoning in Mathematica
---

Viewed abstractly, formal verification sounds deeply conservative: we want software to work the way we intend, without any unexpected bugs. 
To those with more worldly experience, let’s pause. Imagine a world where bureaucrats can’t hide behind a faulty computer to divest themselves of personal responsibility. 
Imagine having to spell out the exact assumptions for the model behind a business decision — giving both the freedom to change one’s mind, and accountability for error. 
Now we see the *real* reason no-one uses formal methods.

There may well be a day when formal proof is a gold standard, separating those who tell people what they want to hear, from those who tell it like it is. 
That’s a ways away. Yet, just as we smirk at poor Milton Friedman taking hours to run a regression using punch cards, 
so shall we be jeered for assuming that if an idea makes sense in our head, this is evidence for its correctness.

Here, I would like to examine a very specific project led by Casey B. Mulligan at the University of Chicago, on automated reasoning in economics using quantifier elimination
— a tool from logic for systematically proving statements about polynomial inequalities of real variables,
which can prove theorems, generate counterexamples, and automate counterfactual statements on economic policy.

Quantifier Elimination
--------

Suppose we want to find the set of coefficients for parabolas with real roots — 
values of *b* and *c* that solve the equation for a u-shaped curve, where *x* is a real number: {(*b*,*c*) ∈ ℝ² |  ∃𝑥(x² + *b*x + *c* = 0)}.

This is easy if we remember the quadratic formula, namely the part √(*b*² − 4*ac*). 
If 4*ac* is bigger than *b*², then we’re taking the square root of a negative number, so the value of *x* is not real anymore. 
Therefore the answer to our question is {(*b*,*c*) ∈ ℝ²: *b*² ≥ 4*ac*}, where *a*=1 by assumption.

Notice that our entire deduction takes the form of eliminating the quantifier ∃𝑥. 
If ∃x is a question, then x without ∃ is the answer. 
If we want to check if a parabola is in the set, with the quantified definition we would have to check all possible values of *x*, 
but with the quantifier-free definition we just need to see if *b* and *c* satisfy the inequality (2016: 2).

We can also think of quantifier elimination by analogy with Boolean satisfiability (SAT), which takes a logic formula made up of variables that can be `True` or `False`, 
and finds values for the variables so the formula evaluates to `True`. 
This was one of the first problems to be proven NP-complete, i.e\. we don’t have a general algorithm to solve all such problems, but we do have lots of smaller ones. 

[//]: # (NB: added complexity b/c different inequalities can contain same variables)

Satisfiability modulo theories (SMT) are a step up that allows inequalities (e.g. *a* ≥ *b*), which lets us tackle far richer questions with numbers. 
(This is similar to [constraint solving](https://gjoncas.github.io/posts/2019-11-07-a-rose-for-emily.html).) 
Quantifier elimination is a type of SMT that involves polynomials like *a*x² + *b*x + *c*, or with even higher powers. 

So the main ‘unit’ in quantifier elimination is Tarski formulas: boolean combinations of polynomial equalities and inequalities. 
We input a Tarski formula, and quantifier elimination gives us `True`, `False`, or (if there are any unquantified variables, as above) an equivalent quantifier-free formula.

Cylindrical Algebraic Decomposition
--------

Now we get what quantifier elimination is. Now let’s look at how it works.

Broadly, we want to show that for all values of a set of variables, our assumptions under those variables imply our hypothesis: ∀v, A(v) → H(v).
Possible results can be tabulated as follows.

+-+-+-+-+-+-+-+-+------------:+:-------------:+:----------:+
| | | | | | | | |             |  ~∃v(A ^ ~H)  | ∃v(A ∧ ¬H) |
+-+-+-+-+-+-+-+-+------------:+:-------------:+:----------:+
| | | | | | | | |  ∃v(A ^ H)  | True          | Mixed      |
+-+-+-+-+-+-+-+-+------------:+:-------------:+:----------:+
| | | | | | | | | ~∃v(A ^ H)  | Contradiction | False      |
+-+-+-+-+-+-+-+-+------------:+:-------------:+:----------:+

If all values support H and none support ¬H, then H is `True`; if the other way around, H is `False`.
More likely, some values will support the hypothesis, while some will support its negation (`Mixed`).
Last, if our assumptions are contradictory, any implication is vacuously true (`Contradiction`).

If we want to prove a hypothesis is `True`, we just show that (A ∧ ¬H) is false for all v.
Once we have a `True` result, we can try to weaken it by removing assumptions, and finding any that are irrelevant.
Likewise, for a `Mixed` result we can add assumptions until it becomes `True` or `False`.

There is also a clever way to generate examples or counterexamples (Mulligan, 2018: 5, fn. 9):

<blockquote>
Existentially quantify N−1 of the variables in the Tarski formula leaving free, say, x₁, and then eliminate quantifiers. The result is a formula in x₁ alone. 
Choose a real number for x₁ that satisfies the formula and substitute that value into the original N-variable Tarski formula, making it an (N−1)-variable Tarski formula. 
Repeat the process for x₂, etc., until real numbers are assigned to all N variables.
</blockquote>

Now we can see how quantifier elimination lets us investigate theories, not just play with formulas.

The main algorithm behind quantifier elimination is cylindrical algebraic decomposition (CAD). 
The steps of a CAD are themselves a proof (2016: 35), and the fewer steps it takes, the shorter and more intelligible the proof.
CAD actually has a nice geometric interpretation — in a word: “Removing existential quantifiers from the formula defining a set in ℝⁿ is 
the algebraic equivalent of projecting that set into the space of free variables” (or on the origin, if there are no free variables).

For the gory details, the most cogent explanation I’ve found is from Caviness \& Johnson ([1998](https://link.springer.com/chapter/10.1007/978-3-7091-9459-1_1): 2):

<blockquote>
The CAD method for QE can be briefly described as a method that extracts the polynomials occurring in the input formula (having first trivially reduced all atomic formulas to the forms A = 0 and A > 0) and then constructs a decomposition of real *r*-dimensional space, where *r* is the number of variables in the formula, into a finite number of connected regions, called cells, in which each polynomial is invariant in sign. Moreover these cells are arranged in a certain cylindrical manner. From this cylindrical decomposition it is then quite straightforward to apply the quantifiers by using a sample point from each cell to determine the (invariant) truth value of the input formula in that cell. This application of quantifiers reveals which cells in the subspace of the free variables are true. It then remains to construct an equivalent quantifier-free formula from this knowledge. In Collins’ original QE method this problem was solved by a method called augmented projection that provided a quantifier-free formula for each of the true cells.
</blockquote>

Don’t worry if you didn’t get all that. The main takeaway is the rather beautiful idea that 
SMT solvers in computer science and projection in algebraic geometry are just different perspectives of the same automated reasoning problem (Mulligan, 2018: 8).

The main reason quantifier elimination is seldom used its that its complexity is double-exponential (`O[d^2^(2n+8) * m^2^(n+6)]`), 
where *d* is the highest power (degree) in the polynomial, and we see that its exponent has an exponent, meaning processing time increases **really** fast as *d* gets larger.

Yet, computational complexity measures worst-case behaviour, which can be much better in practice — especially when most economic problems have low degree (x³ at worst).
Order of variables also matters for CAD’s time and proof length, and since the number of combinations is *n*!, we can only check a few. 
Interestingly, recent research uses [machine learning](https://arxiv.org/abs/1404.6369v1) to find an order that will work well.

The CAD algorithm can be improved by ignoring irrelevant cases (cells), constructing a ‘partial CAD’. 
Other tricks take advantage of repeating substructures.
Virtual term substitution sounds especially promising for economic problems, whose degree tends to be low,
and which are ‘sparse’, i.e\. “most variables are absent from most of the polynomials in the Tarski formula” (Mulligan, 2018: 22).

Automated Deduction in Economics
--------

We saw above that deductive reasoning can be thought of as a process of quantifier elimination; 
likewise, if–then statements are implicitly just eliminating ‘for all’ quantifiers from a `True` sentence (Mulligan, 2018: 1 \& 28).
Quantifier elimination goes well with economic theory because much of economics is counterfactuals about polynomial equations and inequalities.

Mulligan and his coauthors have assembled over 45 problems that can be solved in this way, 
ranging from the Laffer curve to arguments about the gender gap for wages (nonparametric [Roy model](https://en.wikipedia.org/wiki/Roy_model)). 
While above I focused on the implementation, their goal is to create a domain-specific language so economists can simply plug in theorems and test them.
They use [Mathematica](http://models.economicreasoning.com/pdfdownloads.html) because it has a nicer visual display for calculus,
but also have [code](https://zenodo.org/record/1226892) for other SMT solvers such as Z3, Redlog, and Maple.

Mulligan makes a provocative claim that “Published theoretical results should be coded and made available[, just] 
as empirical economists are already expected to do with data-processing code” ([here](youtu.be/Ewd_V8YodQg), around 44:20).
He also frequently compares theorem-provers to matrix inversion — many famous economists such as Paul Samuelson got RA jobs that were simply inverting matrices,
which (happily!) is now entirely done by computers, and no-one would even think to verify them by hand.

In fact, Mulligan is writing a grad-level textbook that leans heavily on quantifier elimination.
I think this is amazing, and may be the start of a really important change in how economics is done.

Curiously, [revealed preference](https://en.wikipedia.org/wiki/Revealed_preference) arguments — very tedious to do on paper — are far more amenable 
to quantifier elimination than the more standard pedagogical method of inspecting first-order conditions (‘local analysis’). 
Likewise, more ‘global’ forms of analysis are often easier to deal with, while specific functional forms are intractable.
Statements about Cobb-Douglas production functions (of the form ANᵅKᵅᐨ¹) are polynomial inequalities, but it’s often easier to treat them using functional forms like *f*(*n*),
since the CAD algorithm doesn’t work if α is a variable, and fractional exponents can take immense amounts of time (5 times longer with `n^5/8`, 3000 times longer with `n^23/30`).

From the other direction, solving these problems led to some new tricks for encoding integrals, 
and vectors with an indeterminate number of elements (e.g\. number of goods in an economy) via statements about their dot product. The pollination may well go both ways.

A paper as recent as 2014 claimed that five variables were a practical limit for quantifier elimination methods. 
By contrast, Mulligan’s problems have on average 19.2 polynomials and 17.2 variables (Mulligan et al., [2018](https://arxiv.org/abs/1806.11447v1): 10).
That said, at least one problem with 18 variables couldn’t be solved even in 5 days of processing (2016: 29-30), illustrating just how bad double-exponential complexity can be.

Most compelling for me is the other avenues that quantifier elimination in economics could open up. 
By adding slack variables to our Tarski formula, quantifier elimination lends itself to polynomial optimization: 
maximizing a polynomial subject to polynomial inequality constraints (Caviness \& Johnson, 1998: 1).
Further, it can handle complex scheduling problems, where some machines can process several tasks in parallel, or some jobs require more than one machine in parallel.
Even more curiously, it allows *hierarchical* scheduling, where in two steps 
“a second objective function is optimized under the assumption of an optimal solution wrt. a first objective function” (Dolzmann, Sturm, \& Weispfenning, 1999: 237-8).
Quantifier elimination may well turn out to be a gateway drug.

Conclusion
--------

Mulligan’s favorite example is from [Paul Krugman](https://krugman.blogs.nytimes.com/2012/11/03/soup-kitchens-caused-the-great-depression) in the *New York Times*, 
to the effect that whenever taxes on labor supply are primarily responsible for a recession, then wages increase.
With much schadenfreude, Mulligan shows by running this through a theorem prover that this is only so when 
“labor supply is at least as sensitive to wages as labor demand” (Mulligan et al., [2018](https://arxiv.org/abs/1804.10037v2): 3-4).

Cursory familiarity with economics culture drives it home that this will only catch on if it has an idiot-proof point-and-click interface.
It’s hard enough to get economists to use LaTeX or anything more advanced than Stata, and even this is orders of magnitude better than elsewhere.
Ideally, it should be just as easy for a theorist to verify a theorem as it is for an applied economist to run a regression.

A formal proof means the difference between reading a paper by an independent scholar and having faith in the results, versus relying on the brand names of academic old boys’ clubs. 
It means clarity: thinking from the bottom up. 
And my favorite, mechanized proof is an intellectual foundation for cognition-curdling fuckery that would otherwise be dismissed purely out of boorishness.

***

### <br>References
<ul>
<li> Caviness, B. \& Johnson, J. (Eds.). ([1998](https://link.springer.com/book/10.1007/978-3-7091-9459-1)). *Quantifier Elimination and Cylindrical Algebraic Decomposition*. New York: SpringerWienNewYork.</li>
<li> Dolzmann, A., Sturm, T., Weispfenning, V. ([1999](https://link.springer.com/chapter/10.1007%2F978-3-642-59932-3_11)). “Real Quantifier Elimination in Practice,” in Matzat, B., Greuel, G., Hiss, G. (Eds.). (1999). *Algorithmic Algebra and Number Theory*. Heidelberg: Springer, pp\. 221-47</li>
<li> Mulligan, C. ([2016](https://www.nber.org/papers/w22922)). “Automated Economic Reasoning with Quantifier Elimination.” NBER Working Paper No. 22922.</li>
<li> Mulligan, C. ([2018](https://www.nber.org/papers/w24601)). “Quantifier Elimination for Deduction in Econometrics.” NBER Working Paper No. 24601</li>
<li> Mulligan, C., Bradford, R., Davenport, J., England, M., \& Tonks, Z. ([2018](https://arxiv.org/abs/1806.11447v1)). “Non-linear Real Arithmetic Benchmarks derived from Automated Reasoning in Economics,” in Bigatti, A. \& Brain, M. (Eds.). (2018). *Proceedings of the 3rd Workshop on Satisfiability Checking and Symbolic Computation*. Oxford, UK: University of Oxford, pp\. 48-60</li>
<li> Mulligan, C., Bradford, R., Davenport, J., England, M., \& Tonks, Z. ([2018](https://arxiv.org/abs/1804.10037v2)). “Quantifier Elimination for Reasoning in Economics.” Working Paper.</li>
<li> Mulligan, C., Davenport, J. \& England, M. ([2018](https://arxiv.org/abs/1806.11447v1)). “TheoryGuru: A Mathematica Package to Apply Quantifier Elimination Technology to Economics,” in Davenport, J., Kauers, M., Labahn, G., Urban, J. (2018). *Mathematical Software – ICMS 2018*. Heidelberg: Springer, pp\. 369-78</li>
</ul>
