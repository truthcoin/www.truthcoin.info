
---
layout: default
title: Soft Forks and Bugs
comments: false
show_author: false
---


    Soft Forks and Bugs - A Dialogue With Mike Hearn
	Paul Sztorc
	August 12, 2015


Argument of the form:

1. Bugs are Unexpected Behavior, Therefore:
2. For Non-Upgrading Nodes, Soft Forks Can Only Kill Bugs

In other words: Tightening the rules only makes surprises more infrequent.

I'm putting this here, because frankly I don't want anyone deleting it. It is also easier to read in a straight line.

Original comments here: https://medium.com/@Truthcoin/mr-hearn-very-sorry-to-read-this-article-5e60c2ef741




### 1 - My Reply to Hearn's Article

Mr. Hearn, very sorry to read this article. I couldn’t disagree more with your entire perspective and I’d really like to know how it is that our interpretations diverged so completely.

My primary concern is existential risk — that some bug/attack causes BTC to be lost/censored (ending the Bitcoin project). Yes, we should aim for maximizing user-experience and minimizing costs, conditional on Bitcoin existing. I’m happiest knowing that Bitcoin held up under the years of SilkRoad, when powerful people were actively attempting to break it down (a perspective originally voiced by Gavin).

With my priority in mind, perhaps you can help me follow you from the "forwards compatibility" point to the "entire purpose of running a node" point. Forwards compatibility, being a filtration of what was (and NOT an addition of anything new), preserves the cumulative stability of the Bitcoin software, because it only shrinks Bitcoin’s phase space. In contrast, a hard fork makes new states possible. With soft forks, each change can be ignored, but with hard forks, each change must be re-compared against all of the lines of code with which it interacts, and all possible new (nonlinear, chaotic) software-states must be re-compared to the nearly-infinite variety of practical circumstances under which the Bitcoin service might be interrupted. My understanding was that there was a 100% consensus that this kind of Research Capacity is possessed by no one (see SilkRoad comment, supra).

Let me provide an analogy to illustrate my concern: my first born child lives on a giant chessboard. I know that certain spaces of the chessboard have deadly land mines, and have banned my child from traveling there. We also find it more fun to impose other rules on certain spaces, like a ‘soccer field space’ where a certain type of ball cannot be touched with hands, or a ‘library space’ where no one can make noise. …then you wander in and tell me that my policy of never visiting a banned space is a bad one because "the auditors … can arrive at the wrong answer". I don’t really care about "answers" (if such things exist), or if they are "wrong" according to Some Guy.

I’m not saying that we should never ever try to visit those banned spaces, but a 90%+ consensus does sound reasonable to me (as does creeping out from those spaces very slowly).

-Paul


### 2 - Hearn's Rebuttal

The point you’re getting at has come up a few times on reddit too.

The idea that the fork types differ in whether they add rules or remove them is a distraction …. the problem is that the social rules Bitcoin encodes don’t map 1:1 to protocol rules.

Whilst P2SH only "added rules" in some extremely pedantic technical sense, that’s not a useful way to think about it because it ended up breaking the actual social rule people want: "coins may not be stolen by random people".

The specific rules that make up the scripting language and so on are all working towards implementing that social rule, so if you break the social rule whilst claiming you are still following the technical rules, you’re kind of missing the point.


### 3 - My Clarification

Perhaps I am missing the point, because I don’t feel that your response addressed my concern.

Say x is "the probability that a severe bug is discovered in Bitcoin". Would you agree that a soft fork cannot increase x, whereas a hard fork can?


### 4 - Hearn's Rebuttal-Clarification

No. I’m not sure why you think that. It doesn’t matter how a change is rolled out, new versions of the software can always have (new) severe bugs.


### 5 - I Emphasize That Hard Forks Make Everything Possible, Even Bugs

We agree that new software can always have severe/hidden bugs.

And we agree that, if Bitcoin-1 is currently immune to "Bug Y" (a catastrophic bug that, once exploited, obliterates the Bitcoin project), then clearly a hard fork will always have (unfortunately) some chance of removing that immunity.

But how might you introduce Bug Y using only a soft fork (where older ‘Y-immune’ versions of the software must NOT flag the chain as invalid)? Isn’t it impossible?


### 6 - Hearn Believes that Soft Forks are Mandatory

I think what you’re getting at is "if a new opcode is added, what if it has a bug"  ...but it doesn’t matter. There’s no such thing as "older Y-immune software" once the fork goes into effect. You MUST upgrade. Please re-read my article, part of it is addressing this idea that people can pick and choose which features they accept. There’s no such thing. Once the majority takes the fork whether it is hard or soft is irrelevant — you will upgrade whether you like it or not, as the alternative is losing the security you are running the program to get in the first place.


### 7 - I Re-Emphasize "What is Possible" Criterion

I introduced "older Y-immune software" to explain that the movement from Older to Newer software shrunk the state space. It has nothing to do with whether or not people actually would/could run Older.

I hope you don’t mind if I try again: say that "non-trivial" soft forks change at least one thing, no matter how tiny (Bitcoin-2 is not just a copy of Bitcoin-1). If you non-trivial-soft-forked Bitcoin-1 an infinite number of times, wouldn’t you eventually end up with a Bitcoin-INF that was *entirely free of all bugs*, because it did **not** allow the user to do *anything at all*?


### 8 - Hearn Contradicts Himself (Bug = "Lack of Action", Bug = "Unintended Behavior")

Not doing anything would itself be a bug.

The term "bug" does not mean "line of code exists that crashes". Bug means "software does not do what it was intended to do". Obviously a Bitcoin that did not actually let you spend your bitcoins, or which allowed other people to steal them from you, would be catastrophically buggy.


### 9 - Hearn Doesn't Understand my Positon, So I Clarify

Do you interpret my position as "we should never hard fork, even to fix a catastrophic bug"? I did not intend to communicate anything like that (nor to change define:bug or suggest that theft-bugs were not catastrophic).

In my demonstrative example I was "intending" to have the protocol approach something where everything was not allowed (explicitly no "unintended" behavior occurred, no bugs).

Clearly you would agree that:

[P1] If someone could have killed the Bitcoin cryptosytem, they would have done it by now (Gavin’s SilkRoad point). [P2] No one has killed Bitcoin yet. So, [C1] Bitcoin is currently immune to murder.

You probably also agree with:

[P3] All that is ‘done’ must either be intentional-doing or unintentional-doing. [P4] " Bug means ‘software does not do what it was intended to do’ ". So, [C2] one who *intentionally* reduces the number of things a software ‘can do’ is *unable* of increasing the frequency of bugs ("unintended behavior").

But it then follows that:

[P5] Soft forks *intentionally* reduce the number of things a software ‘can do’. + [C2] = [C3] Soft forks are *unable* to increase the frequency of bugs ("unintended behavior").

And then:

[P6] As "unintended behavior" is "unintended", we don’t know what it is, and so "it" might include "death". + [C3] = [C4] Soft forks are unable to increase the likelihood of Bitcoin dying.

Do you agree with [C4]? In the past, I think you have argued that organic user growth under 1MB blocks will kill Bitcoin, but I feel this premise contradicts (and is inferior to) [C1].

### Aftermath

Mike Hearn stopped replying at this point.