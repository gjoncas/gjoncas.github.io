---
title: The Associativity Law for Monads
tags: haskell
---

During quarantine, I’ve been pursuing a goal I’ve had for years: to grok monads.
In a word, monads are the [pons asinorum](https://en.wikipedia.org/wiki/Pons_asinorum) of functional programming: once you get them, you’re part of the ‘club’.

A pithy [definition](https://stackoverflow.com/questions/17590842) I’ve found is that monads are a “type for output impurity”.
Even from this we can see how much the concept is tied to the functional programming paradigm, and makes little sense outside of it.
Within that paradigm, however, monads are a deeply elegant solution to a variety of problems, and continually give new ‘aha’ moments as one progresses deeper and deeper.

This post documents one such moment — a tiny one, but one that tripped me up for quite a while.
To follow along, the reader should have read and understood the [Haskell wikibook](https://en.wikibooks.org/wiki/Haskell/Understanding_monads) page on monads.

***

Associativity means it doesn’t matter what order we evaluate a statement, typically written as:

`(a ∘ b) ∘ c = a ∘ (b ∘ c)`

However, in Haskell the associativity law is written as follows:

`(𝑚 >>= f) >>= g  =  𝑚 >>= (\x -> f x >>= g)`

Yeesh. It’s not at all obvious that these are the same. For this reason, many people prefer the Kleisli composition operator (or ‘fish’), which lets us write the above as:

`(f >=> g) >=> h  =  f >=> (g >=> h)`

This gives us the structure we want, but just hides the whole problem within the definition of >=>, which is just as hairy, namely: `f >=> g = \x -> f x >>= g`. Gag me with a spoon.

Here I want to explain my Eureka moment in finally getting the associativity law for bind.

***

First, note that the type signature for bind (>>=) is as follows:

`(>>=) :: Monad m => m a -> (a -> m b) -> m b`

So when used as an infix, the left-hand argument must be a monadic object, 
while the right-hand argument must be a function that takes a non-monadic object, and makes it into a monadic object.
(Note that 𝑚 is not the same as m.)

In the left-association `(𝑚 >>= f) >>= g`, the bracketed part gives the two arguments we need for bind: `𝑚 :: m a`, and `f :: (a -> m b)`.
Evaluating these gives a new term `𝑥 :: m b`. 
This is a monadic object, which is exactly what we expect on the left-hand side of the next bind.
Therefore the next step is to apply g to 𝑥, giving a new monadic object, and then we’re done. Easy.

Right-association, on the other hand, is a pain in the ass. Again:

`𝑚 >>= (\x -> f x >>= g)`

To understand why we have to write it this monstrous way, let’s see how it would look if we didn’t:

`a >>= (b >>= c)`

Here, b is a monadic object, and c is a function. Applying bind to these gives a new monadic object 𝑦. Then the next step is to evaluate `a >>= 𝑦`.

Here we have a problem, because 𝑦 needs to be both a monadic object (as output of `b >>= c`) and a function (as input to `a >>= 𝑦`), which doesn’t really make sense.

To understand right-association (`𝑚 >>= (\x -> f x >>= g)`), let’s start from the first bind. 
We know the left-hand side 𝑚 is a monadic object. 
We also know that the right-hand side needs to be a function, which is satisfied due to the lambda-term (i.e. `\x ->`).

In evaluating `𝑚:: m a`, the first bind ‘unwraps’ the 𝑎 from its monadic wrapper, and feeds it to the function on the right-hand side. 
So this 𝑎 is an ordinary non-monadic object, and we’re using it as an input for our function, which has type `(a -> m b)`.

But this 𝑎 is precisely the argument x that is called for in the lambda-function \\x. 
Once it gets that argument, we can just ignore the function part (`\x ->`), and only need to deal with `f x >>= g`.

Well, f has type `(a -> m b)`, so it takes this argument 𝑎 (or x) to produce a monadic object m b, which is what we expect on the left-hand side. 
Then we unwrap the b and pass it to the function g, which is likewise typed `(a -> m b)` in general, or in this case `(b -> m c)`. 
Thus, the end result of this double bind is a monadic object `m c`. Hooray!

***

To recap: with left-associativity `(𝑚 >>= f) >>= g`, things are easy because we can simply evaluate the expression in brackets, and then feed the result as an argument to the remaining expression.

With right-associativity `𝑚 >>= (\x -> f x >>= g)`, we can’t quite do that, because of this pesky \\x. Instead, the 𝑎 term from `𝑚 :: m a` is used as the x argument, and *then* we can evaluate the bracketed part independently.

I’ve reread the monad laws many times, and this eluded me up until now.
This is likely one of those things that will seem ‘obvious’ going forward, but even as I wrote this post I almost lost the main insight, due to a minor confusion about 𝑚.
(My mistake was: I briefly thought the first bind passed all of 𝑚 to \\x, not just the 𝑎 term.)

Given how garrulous this post was, it’s no wonder most treatments of the monad laws just glance over associativity.
The step I was missing was so profoundly simple, but easily lost among the mess of symbols.
Therefore I hope this post helps not only ‘advanced beginners’ like myself, but also reminds experienced coders how to think of monads from the ground up.