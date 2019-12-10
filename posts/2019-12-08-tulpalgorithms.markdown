---
title: Tulpalgorithms
subtitle: On Computational Egregorics
---

I just started my first real job, which is lovely and I like it a lot, but it’s pretty overwhelming to 
enter into a new social network, especially since throughout my life I haven’t known many people. 
Curiously, this dovetails with a recent *idée fixe* of mine, namely: tulpas.

The idea starts from [Dunbar’s number](https://en.wikipedia.org/wiki/Dunbar%27s_number), inferred from brain size of primates, 
that human social networks can sustain up to 150 people, and beyond this get too complex to handle.

A *tulpa* is an internal representation of another person.<br>
The key from Dunbar’s number is that human minds can only support a finite number of them.

Thus, tulpas operate at a level between the (largely arbitrary) distinction between 
psychology / individuals and sociology / groups, where this division is precisely what’s at issue.

Further, if tulpas are a scarce resource, this raises many economic questions about how to optimally allocate them.
Yet, one tulpa can be assigned to multiple people (\"You’re just like my sister\"). 
This brings to the forefront the ‘[tulpalgorithms](https://twitter.com/youtopos/status/1187040993037692928)’ we use to compress and even transmit tulpas.

This theme has long been a staple on weird twitter, but I think we can actually represent tulpas using mathematics. 
Here I’d like to conjecture what a formal science of tulpas might look like.


Economics of Tulpas
--------

If supply of tulpas is limited, then they implicitly have a price.

Tulpas aren’t only for real people, mind you. 
In philosophy, it’s crucial to have high-fidelity tulpas for various famous philosophers. 
Fiction-writing is essentially manufacturing tulpas. 
Religion, especially polytheism (e.g\. the various saints in Catholicism), is another example.

This view helps explain empirical links between philosophers and solitude. Likewise with readers of fiction. 
The most cogent way to think about introversion vs\. extroversion is in terms of ‘energy’, 
where introverts lose energy from interactions and extroverts gain it — hearkening back to Freud’s libidinal economy, now considered passé. 
Tulpas give a finer view of this divide, where extroverts enjoy shuffling their internal social representations, 
while introverts focus more on high-fidelity.

Of course, tulpas are dynamic: anyone meets new people, or switches social circles. 
Keeping social links has costs, often high. Choices have to be made, which account for these costs, as well as returns. 
It’s hardly farfetched to posit some kind of optimizing behaviour here.

The core question is ‘tulpa-worthiness’. By what criteria do we allocate a tulpa-slot?
There’s a fun parallel to this in economics, which nicely illustrates how we can bring math to bear on this issue.

In an episode of *Seinfeld*, Elaine’s favorite contraceptive stops being sold, and now for every potential lover she has to weigh in whether he is ‘spongeworthy’. 
An economics professor at Princeton wrote a paper on this, and it was actually published in *Economic Inquiry* 
(Dixit, [2012](http://gen.lib.rus.ec/scimag/10.1111%2Fj.1465-7295.2011.00377.x)).

In a nutshell, Elaine has to decide how to allocate a scarce resource among time periods in the presence of uncertainty (about quality of men and so on). 
Mutatis mutandis, that’s what people do when they allocate income throughout their lifetime. 
So this is actually a classic economic problem, thus given a decent specification (e.g\. how impatient Elaine is), 
we can use mainstream tools such as dynamic programming to find numerical solutions — at least after a few minor tweaks.

Unlike a sponge, we can reuse a tulpa, albeit with some kind of mental  processing cost. 
Like with Elaine, we have to decide whether to assign a tulpa-slot now, or wait until someone better comes along. 
Another curious difference is that in a sense, there exists a market for tulpas, though its completeness depends on how fine-grained we want to get.

The main problem is that internal costs aren’t observable (time discounting, processing cost, etc.). 
Nor is the general value that someone can bring to a relationship, though it would be interesting to experiment with different indexes here.

This is the sort of situation where simulations are invaluable. 
The idea is to replicate various situations involving tulpas, experimenting to see which parameters match each outcome. 
One of my current goals is to learn dynamic programming, which is precisely the kind of math that’s needed here, 
so I think it’s actually feasible in the near future to pull this off.


Data Structures & Compression
--------

By analogy with sponges, we treated tulpas as discrete, but that’s too simple.
Tulpas overlap, as anyone can attest. 
I once worked with an awful woman who looked just like a professor I was fond of, so I was far nicer to her than she deserved. 
I’m sure there’s a whole subliminal network of irrational behaviour that tulpas account for.

The simple fact is that all of us will encounter more than 150 people. Some of us do every day. 
Most of us don’t actually have to *know* everybody enough to have an internal representation of them, 
but others (like diplomats) are professional networkers, forced into elaborate mnemotechnic encodings.

Personality typologies are a nice example of this. 
With Myers-Briggs we have four sets of binary oppositions, leading to 2^4^ = 16 personality types, such as INTJ (me) or ESFP. 
That’s quite a lossy compression, with 134 tulpas to spare.

My own favorite is the Enneagram — probably the craziest thing I believe, but it works. 
Here, there are nine types arranged in a circle, and each type has an adjacent number as a ‘wing’, 
in the form 5w4 (me), 1w9, and so on, for `9*2 = 18` types. 
(Myers-Briggs maps onto the enneagram in a straightforward way, but excludes the 3s.) 

There’s a related typology I pair it with: instinctual subtypes. 
Briefly, there are three instincts: self-preservation (SP), social (SO), and pleasure (or sexual: SX). 
These are arranged in order, where the first one is literal, the second one is abstract, and the third is dormant. 
So SP/\_/\_ means the person might be very sensitive (or very insensitive) to cold or diet; 
SX/\_/\_ means the person pursues physical pleasures like food. 
Similarly, for \_/SX/\_ the person prefers more abstract pleasures like music; 
or for \_/SO/\_ someone prefers people in the abstract to people in the concrete (which would be SO/\_/\_). 

This gives `3! = 3*2*1 = 6` combinations, so paired with the enneagram it’s `6*18 = 108`. 
That’s a reasonable degree of fidelity, with 42 tulpas left over for Deleuze and my mum or whatever.

The latter two typologies mesh nicely because there’s no overlap. In general, we can’t count on this. 
This is where computer science comes in, notably its rich resources on compression such as error-correcting codes. 

I hesitate to say much about this, as it’s not a kind of math I know well. 
In a sense that’s the charm — our ‘tulpalgorithms’ for handling overlap deeply impact how we optimize, differently from any other commodity. 
Information theory should be crucial here, with tools such as Kolmogorov complexity to judge whether one encoding is better than another. 
Unsurprisingly these are seldom used in economics, but they would help ground in theory what would otherwise be disparate simulations.

Computational Egregorics
--------

So far, tulpas have mapped onto humans — concrete like my mum, or abstract like Deleuze 
(whose books I can read, but I’ll obviously never meet him) or fictional characters.

We’re already making lots of arbitrary distinctions. 
Is there really a qualitative difference to a tulpa if I’ve met that person in meatspace? 
What about a tulpa for my dog, who certainly has some kind of personality? 
(Parenthetically, I find that the instinctual subtypes help for animals.) 
Is my self-concept a tulpa? 
What about higher-order tulpas, like what I think you think of me?

Within this conceptual framework there is another closely-related notion: egregores. 
Egregores don’t necessarily map onto humans. 
Rather than a hard-and-fast distinction, it’s more helpful to think of tulpas as a subtype of egregores, perhaps of the highest intensity.

This is because egregores leech off of our tulpas. 
They are artificial entities that feel real (like actual beings), precisely because they’re parasitic. 
So brands, for instance, are egregores. 
An organization (workplace) or symbol (flag) or abstract idea can be egregoric. 
Fictional characters seem like tulpas insofar as they’re ‘people’, but they’re also egregores in that they’re not ‘real’. 

I think it’s bad to hard-code a distinction between ‘real’ and ‘not-real’ into a conceptual system. 
One can imagine only ever communicating with someone via letters, and yet they feel far more real than most people around you; 
you may even discover that the whole time, your interlocutor was a neural network. 
So it’s far simpler to take egregores as the main unit, 
and tulpas as just a shorthand for anthropomorphic egregores, more intense because we encounter them more often.

Crucially, Dunbar’s number brings to light a deeply insidious aspect to brands and symbols. 
At face value, it corresponds somewhat with banal critiques of ‘media society’ subtracting from ‘real human relationships’ and so on. 
The flip-side of this is xenofeminist praise of tulpa-decentralization, an alienation of internal representations away from the anthropomorphic.

The notion of compression adds far more nuance. Suppose a fictional character reminds me of my friend; 
by watching a movie, I feel like I’m hanging out with my friend, helping me to maintain that tulpa even if I haven’t seen them for years. 
So large social networks create tulpa externalities which can be positive or negative.

Further, media personalities might crowd out acquaintances in meatspace, but on the other hand, there are such legions of them that they create myriad 
new distinctions, which might motivate me to meiotically split a tulpa that otherwise would have contained several diverse people.

Most fascinating of all is the idea that social networks force us to develop more efficient ways to mnemotechnically encode conflicting tulpas. 
Are there different methods of reaching equilibrium (whatever that means here), such as regret minimization as compared to Nash equilibrium? 
Can we show that some methods are bad and we shouldn’t use them? Can we use egregorics to explain the persistence of seemingly irrational types of behaviour?

Conclusion
--------
The sort of simulations I have in mind are entirely feasible, akin to iterated prisoner’s dilemma or Schelling’s model of segregation. 
As hard as it would be to translate any insights from this into actionable results, 
I can imagine textual analysis of ad copy into separate categories in order to identify opportunities for parasitism, 
or comparing lexical choices of various people in one’s twitter feed as a barometer of egregoro-dynamics. 

One could even actively engineer one’s egregoric ecology by creating sensory associations of certain people with exotic animals or landmarks.
People surely use such strategies already, in more or less watered-down ways.
Tulpas are even exchanged through gossip, and acculturation into a new society takes the form of ‘tulpa-mining’ as we catch up with common knowledge.

Just as we accept that our bodies are composed of myriad cellular organisms with a high degree of autonomy, 
egregorics provides a multi-agent view of the self where, moreover, these agents are distributed among members of society.
Unlike semiotics where symbols are simply ‘given’, or memetics where memes spread through you like a virus, egregores are feeding on you as we speak.
Egregorics must be computational, so machines can tell us what our tulpas don’t want us to know.
