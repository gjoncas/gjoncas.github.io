---
title: Topos-theoretic Social Science
subtitle: David Sallach on Social Type Theory
---

David Sallach is a mathematical sociologist at Argonne National Laboratory, and senior fellow at the University of Chicago’s Computation Institute.
Over the past decade he has researched category theory as a foundation for computational social science, with topos theory as his main framework.
 
In philosophy circles, topos theory is best known as the machinery behind Badiou’s *Logics of Worlds*.
It is often brought up by Zalamea, who outlines how the closely-related sheaf theory opens up novel relations between local and global that philosophy should take up in turn.
Yet, due to the obvious barriers to entry, most attempts at this have just been exercises in hand-waving.

This post aims to give a general overview of Sallach’s research project, from the preliminary concepts it started with,
onward to the process of narrowing down among competing frameworks, and finally to the new ideas that topos theory can bring for social analysis.
I assure you, I am in no position to talk about these things, but no-one else is going to do it, so what the heck.

### Categorical Sociology

Sallach comes from a background in computational social science, which at this point is essentially a hodgepodge of agent-based simulations and social network modelling.
While it’s possible to make highly practical models, lack of underlying theory makes it very hard to draw general conclusions.

An obvious reason why category theory suggests itself is its potential to tie together many disparate formalisms currently in use.
Culture is a network of networks, where social distinctions create ingroups and outgroups, with an associated core and periphery (2011: 7).
The main unit here is discrete agents, but it’s also natural to think of macro-level trends as if they were continuous.

Curiously, a major part of Sallach’s initial metaphors come from topological quantum field theory.
Rather than quantitative metrics, here we are interested in topology change, a far more ‘qualitative’ kind of reasoning, much like how we think of transforming social structures.
We want to analyze degrees of freedom as capacities for variation, and how changes propagate through them (2011: 10).

Similarly, it seldom makes sense to say that two social tendencies are ‘equal’ in a mathematical way, and a major benefit of categories is to allow weaker forms of equality.
Objects in a category are specified only ‘up to isomorphism’, where instead of spelling out how two things are the same, they are simply taken as indistinguishable.
Further, if two things are equivalent up to isomorphism, these equivalences can likewise be equivalent from the point of view of a higher category, in a “recursive weakening of the notion of uniqueness” (Baez & Dolan, [1998](https://arxiv.org/pdf/math/9802029.pdf)), allowing various levels of granularity.

However, categorical objects tend to be viewed as invariants, of which there are few in the social world — death and taxes excepted. 
To get around this problem, for Sallach the main objects of categorical social theory are ideal types, never appearing in pure form empirically (2012a: 12).

Sallach extends this notion of ideal type by drawing from Karl Popper’s propensity interpretation of probability.
The paradigmatic example here is rolling a die: we know the odds of getting a given side are 1 in 6, 
but frequentist probability must justify this through a complex rigmarole of supposing an infinite sequence of dice rolls that would solidify these probabilities.
It’s far more cogent to say these probabilities are built into the structure of the die (6 equal sides, etc.).
Thus: “Propensity measures the causal pressure exerted by certain conditions toward the realization of certain events” (2011: 11).

Especially in contexts like quantum theory, we want to talk about the chances of an atom decaying, even though it will decay only once — i.e\. single-case statistics.
Analogously, we also want to be talk about probability in the case of broad social tendencies whose conditions can never be replicated again.
Hence, Urbach (1980) extends the notion of propensity in a direction that Popper himself would have hated, to encompass the holistic forces dealt with in sociology.
His key example is Durkheim’s study of suicide, which found a remarkable persistence in suicide rates irrespective of mortality rates,
with equally-persisting discontinuities across state and demographic boundaries.

Because ‘propensity’ is such an underdetermined concept, it applies to vastly different social fields and forces, 
making it ideal for the level of abstraction in category theory (2012b: 7-8); in fact, a metaphorical inspiration here is quantum spin networks (2011: 11).
The next step is to find morphisms *g*: A ⇒ B, i.e\. processes carrying a system from state A to state B (2011: 10).
The wealth of categorical abstractions lets us express dynamics subject to local entanglements, as actors’ endogenous behaviour gives rise to emergent structure.

In sum, the appeal of category theory in social science is to bridge continuous and discrete patterns, 
and allow ‘calibrated generalization’ of social transformations rather than strict equality (2012b: 2).
Most of all it offers a form of recursive locality, giving a unified way to analyze bottom-up emergent effects of aggregated agents, 
plus top-down structural effects on micro-level decisions (2012b: 6).

### Social Homotopy Types

In 2013, some of the greatest mathematicians in the world published a new foundations of mathematics: homotopy type theory.
Naturally, this is exciting stuff, which led Sallach into a detour to see how HoTT might bear upon social science.
I feel like not much actually came out of this project, but it’s still worth seeing how he went about it.

Type theory originated in response to a paradox in the foundations of mathematics. 
Russell’s paradox runs: if a barber shaves everyone who doesn’t shave himself, who shaves the barber? 
If he does, he doesn’t; if he doesn’t he does. 
The paradox extends to set theory, at that time the main building block for all mathematics. 
Russell & Whitehead’s *Principia Mathematica* used type theory to circumvent it. 
Imagine a village with a system of castes **1**,**2**,**3**,**4**, where **4** is higher than **3**, **3** than **2**, **2** than **1**. 
A person may only be shaved by someone of a lower caste (e.g\. a **3** by a **2** or **1**). 
Since there is no self-shaving, there is no paradox (Doxiadis & Papadimitriou, 2009: 174-5).

In this sense, type theory refutes the claim that “everything is a set” (de Bruijn, 1995: 28). 
However, until quite recently it was unclear just how the two differ. 
One property peculiar to types is that “any definable property of objects is invariant” (Awodey, 2014: 7). 
The solution, it turns out, is to view types as *spaces*, and examine them with a branch of math that concentrates on spaces: topology.

Topology is the mathematics of squishing shapes into other shapes. 
A well-known result is that, squish as you might, a sphere can’t be made into a doughnut without tearing it. 
That is, there exist invariants to the squishability of shapes. 
If a shape is only a squish or two away from another shape — that is, there exists a *homotopy* between the two — the shapes are ‘homotopy equivalent’.

To put this more formally, 
if **T** is a topological space, then two elements *a* and *b* in **T** are identical if **T** has a continuous path from *a* to *b* (Leslie-Hurd & Haworth, 2013: 101). 
Given functions *f* and *g* mapping **T** onto another space **U**, a homotopy morphs one map into another. 
This means that a homotopy can “cleanly lift the notion of identity from elements *a* and *b* to functions *f* and *g*” (ibid.).

HoTT closely corresponds to *n*-category theory, which uses layers of categories to leverage weak equivalences, thereby incorporating greater complexity (2012a: 14).
The appeal of HoTT for social science is the high expressiveness afforded by its higher-order logic, which allows (2014: 2):

<ol>
<li> an ability to customize equivalences,</li>
<li> a means of demarcating discourse boundaries, and</li>
<li> creation of specialized spaces and shapes to which social processes can be mapped.</li>
</ol>

While the notion of isomorphism lets us ignore all the quantitative details of social transfomation, HoTT can talk about this topologically. 
Identity in HoTT means two objects are the same homotopy type, so their transformations through deformation will be isomorphic; 
social interaction can thereby be seen as progession along one such path (2014: 6).
It also lets us attribute agency to these transformations by means of type constructors:
“a social actor can be an elicitor, a role in which one seeks to alter the motive pattern of another, and thus change the other’s social type” (2014: 8).

One last interesting detail about HoTT is that it can be used as a proof language to formally verify theorems.
Thus it lends itself to axiomatic approaches to social science, such as that attempted in Austrian economics.
Given social scientists’ well-known inability to agree on even the simplest of terms, the odds seem stacked against such a project.
Still, perhaps such a highly abstract language can identify common ground among seemingly incommensurate approaches, such as the following otherworldly axioms (2016a: 8):

<blockquote>
**Axiom 4a**. The more directly that the path of a social actor or cultural trend approaches an idealized conceptual pole, the higher is the n-category required to characterize its structure.<br><br>
**Axiom 5**. The more rapidly a social actor or cultural trend approaches an idealized conceptual pole, the more morphisms it manifests.
</blockquote>

Overall, Sallach prefers to use HoTT metaphorically, mapping from qualitative social concepts to mathematical ones. 
Yet, I’d be far more impressed if he approached it from a quantitative angle, showing how one well-known model in the social sciences topologically morphs into another.
Still, given its Rosetta stone-like translation into categories, HoTT may prove to be a powerful tool for implementing categorical social science,
by means of tools such as cubical type theory that make HoTT into a computable language.
As a language for theorizing, however, topos theory sounds far more promising, as we will see next.

### Topos-theoretic Social Science

To give an idea of their mathematical expressiveness, a topos can be defined in 13 different ways, via different mathematical languages (2015: 41, fn. 2).
For our purposes, the simplest is that a topos is a category with two additional conditions: it is ‘Cartesian closed’ and it has a subobject classifier (Bhattacharyya, 2012: 16).
The first condition is easy to understand if you’ve run into group theory: a cartesian closed category admits a basic algebra whereby objects have products and exponents.

For the second condition, a subobject classifier provides a category with a logic of wholes and parts.
Viewed through the lens of social science, a subobject classifier is a structured way to provide graduated, indexed and/or spectral distinctions within a stable set of values, and lets agents assess how incremental differences affect spaces or structures of interest (2015: 41-2).

Unlike the humanities where ‘topos’ is an incredibly pretentious word for a theme or topic, a topos in math should be thought of as an extended notion of place (Zalamea, 2018: 255).
Topos theory makes space a more primary concept than points, unlike set-theoretic approaches that must spell out space as an aggregate of points (Plotnitsky, 2012: 355).
This opens the way for ‘point-free’ topology, with objects defined only through flux processes (Zalamea, 2018: 255).
In short, topoi allow an “*algebraic* concept of space, which applies to conventional spatial objects but extends beyond them” (Plotnitsky, 2012: 355).

The concept of sheaf becomes important here, where sheaves behave as “global comprehensions…where all local information…become glued together” (Zalamea, 2018: 261).
In fact, a topos can be defined as a category of sheaves over an abstract topology (ibid., 254).
The clearest definition of sheaf I’ve found is given by Plotnitsky (2012: 362-3):

<blockquote>
A sheaf is a particular kind of arrow space, Y ⇒ X, over (projected onto) a given space, X, associating a space A, to each point of X, which is why it is called a ‘sheaf’, a sheaf of spaces over a given space, which can, again, be a single point. By making each topos a whole *category* of sheaves and thus *spaces* (plural) over and indeed defining a given space, the concept topos ‘multiplies’ this concept into an immensely rich architecture, again, even if X is a single point.
</blockquote>

More concisely, a sheaf is “just two topological spaces related by a projection with a good local behaviour” (Zalamea, 2018: 253).
These sheaves can be glued together or restricted to produce processes coupled across levels (Sallach, 2015: 42).
Much like relativity theory, sheaves act like reference frames, where each sheaf in a topos has its own local logic (ibid., 44).

This is the sense in which Badiou draws upon topoi to express ‘logics of worlds’.
A topos can encode a logic, such as fuzzy logic where truth values occur along the interval [0,1], 
or paraconsistent logic “where we can have local contradictions without forcing global contradictions, which would destroy the system” (Zalamea, 2018: 254).
Curiously, Badiou leans heavily on this logical interpretation of topoi, 
while adopting a more spatial perspective allows us to talk about a plurality of possible ontologies, rather than only a plurality of logics (Plotnitsky, 2018: 361).
Rather than a universe of sets, we can move to a multiverse of topoi, each with its own dialectic of wholes and parts (Bhattacharyya, 2012: 17).

In this light, Sallach (2015: 46-7) raises a compelling example of the kind of new insights that topos theory can bring to social science.
Since a topos allows local definition of truth, each social actor can have their own private method of attributing truth,
which can differ by power relations, ingroup/ outgroup status, or hierarchical scale. 
Hence, topos theory should make it possible to simulate the aggregate effects of diverse truth-attribution practices among agents.
Adding more quantitative machinery, it should even be possible to study statistical distributions of truth-attribution.

All this sounds promising as a way to formalize social theories that are currently only expressed in a qualitative way.
The baby examples that Sallach provides aren’t quite enough to sway a skeptic, but I hope to have shown that the overall idea is sound.
Topos theory opens up new questions of elasticity versus rigidity of social transformations, or continuity versus separation of societal fields,
and offers “a dynamical study of dynamics” (Zalamea, 2018: 254) with the immense power of abstraction that social theory needs.

### Conclusion

Sallach has been radio-silent since about 2016 — which could mean he’s working on a treatise that will revolutionize social science, or that he’s retired.
I’m always excited to hear about new types of math being applied in social science, and am confident that such a powerful formalism can generate radical new ideas.
It just hasn’t yet.
While I’m not in a position to give substantive criticism, Sallach’s project clearly suffers a lot from a lack of collaboration with mathematicians,
as well as his desire to reconstruct social theory from scratch rather than work with what’s already there.

While topos-theoretic social science still lacks any killer applications, it could just be that the idea is too far ahead of its time.
A recent book by Schultz & Spivak ([2019](https://arxiv.org/pdf/1710.10258)) uses topos theory to develop a ‘temporal type theory’
that can analyze and compare systems with both continuous dynamics (e.g\. differential equations) or discrete dynamics (e.g\. jumps).
One highly practical application has been to construct a provably correct air traffic control system, and I hope there is much more to come.

***

### <br>References
<ul>
<li>Awodey, S. ([2014](https://www.andrew.cmu.edu/user/awodey/preprints/siu.pdf)). “Structuralism, Invariance, and Univalence.” *Philosophia Mathematica* 22(1), pp\. 1-11</li>
<li>Bhattacharyya, A. ([2012](https://bat020.files.wordpress.com/2014/03/setcat.pdf)). “Sets, Categories and Topoi: approaches to ontology in Badiou’s later work.” Working Paper.</li>
<li>de Bruijn, N. ([2005](http://alexandria.tue.nl/repository/freearticles/597627.pdf)). “On the roles of types in mathematics,” in de Groote, P. (Ed.). *The Curry-Howard isomorphism*. Academia-Bruyland: Université Catholique de Louvain, pp\. 27-54</li>
<li>Doxiadis, A. & Papadimitriou, P. (2009). *Logicomix*. New York: Bloomsbury.</li>
<li>Leslie-Hurd, J. & Haworth, G. ([2013](http://centaur.reading.ac.uk/33158/1/HoTT.pdf)). “Computer Theorem Proving and HoTT.” *ICGA Journal* 36(2). pp\. 100-103</li>
<li>Plotnitsky, A. ([2012](https://web.ics.purdue.edu/~plotnits/PDFs/ap%20exp%20with%20ontologies.pdf)). “Experimenting with ontologies: sets, spaces, and topoi with Badiou and Grothendieck.” *Environment and Planning D: Society and Space* 30, pp\. 351-68</li>
<li> Sallach, D. ([2011](http://www.mat.uc.pt/~ct2011/talks/Sallach.pdf)). “Categorial Social Analysis.” Paper presented at the International Category Theory Conference, Vancouver.</li>
<li> Sallach, D. ([2012a](https://www.researchgate.net/publication/275584554_Categorical_Social_Science_Theory_Methodology_and_Design)). “Categorical Social Science: Theory, Methodology & Design.” Working Paper.</li>
<li> Sallach, D. ([2012b](https://www.researchgate.net/publication/276206642_Social_Coordination_Toward_a_Category-Theoretical_Synthesis)). “Social Coordination: Toward a Category-Theoretical Synthesis.” Proceedings of the World Congress on Social Simulation, Taipei.</li>
<li> Sallach, D. ([2013](http://www2.econ.iastate.edu/tesfatsi/Sallach2013RecogLogicSocialConflictTopos.AESCS.pdf)). “Recognition-Based Logic and Social Conflict: Toward a Topos Model.” 8th International Workshop on Agent-based Approach in Economic and Social Complex Systems.</li>
<li> Sallach, D. ([2014](https://www.researchgate.net/publication/276206925_Theoretical_Mathematics_and_Endogenous_Social_Models)). “Theoretical Mathematics and Endogenous Social Models.” Working Paper.</li>
<li> Sallach, D. ([2015](https://link.springer.com/chapter/10.1007/978-4-431-55236-9_4)). “Topos Modeling of Social Conflict: Theory and Methods,” in Nakai, Y., Koyama, Y. & Terano, T. (2015). *Agent-Based Approaches in Economic and Social Complex Systems VIII*. Heidelberg: Springer, pp\. 39-51</li>
<li> Sallach, D. ([2016a](https://apps.dtic.mil/dtic/tr/fulltext/u2/1025131.pdf)). “Homotopy Types and Social Theory: Theoretical Foundations of Strategic Dynamics.” Defense Technical Information Center, Technical Report AD1025131.</li>
<li> Sallach, D. ([2016b](https://www.researchgate.net/publication/276207807_Universal_Constraints_on_Social_Order_A_Formal_Foundation)). “Universal Constraints on Social Order: A Formal Foundation.” Working Paper.</li>
<li> Urbach, P. (1980). “Social Propensities.” *British Journal for the Philosophy of Science* 31(4), pp\. 317-28</li>
<li>Zalamea, F. ([2018](https://outernationale.memoryoftheworld.org/Maria%20Voyatzaki/Architectural%20Materialisms_%20Nonhuma%20(6976)/Architectural%20Materialisms_%20Non%20-%20Maria%20Voyatzaki.pdf)). “Grothendieck Toposes: Architectural and Plastic Imagination beyond Material Number and Space,” in Voyatzaki, M. (Ed.). (2018). *Architectural Materialisms: Nonhuman Creativity*. Edinburgh: Edinburgh University Press, pp\. 251-66</li>
</ul>