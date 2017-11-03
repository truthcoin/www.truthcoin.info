---
title: More Terminology -- Forks and Splits
show_author: true
comments: true
date: 2017-11-02 05:03:00
---



> While the word "fork" would appear to be synonymous with "split", they are in fact completely different and mutually exclusive. Splits are bad for blockchains, because they "un-blockchain" them.

### Forks are Not Splits

The terms "hard fork" and "soft fork" refer to [protocol upgrades](http://www.truthcoin.info/blog/protocol-upgrade-terminology/). They don't (and *can't*, as I'll show) refer to "splits", cases where one protocol diverges into two different living protocols.

This is confusing because the word "fork" explicity refers to a split! As in the phrase "fork in the road":

![images](/images/blockchain-fork-term.png)

However, in the Bitcoin world, a "fork" is exactly that which does *not* split. Our words are backwards! On behalf of the Bitcoin community [if I may], I apologize for the confusion this must cause.

This state of affairs dates back to [the original Nov 2012 meaning of soft fork](https://bitcointalk.org/index.php?topic=126798.0), which was that it meant that two blocks just happened to be found at around the same time. This was "soft" because it would arise naturally, and solve itself naturally, and go away naturally.

![image](/images/fork-etymology.png)

Human language is constantly changing and improving, and Bitcoin jargon is no exception. The "soft" part is derived, as near as I can tell, from [a June 2012 clarification by Gavin Andresen](https://gist.github.com/gavinandresen/2355445/revisions) in which he drew a distinction between hard and soft **"changes"** (not "forks", because he correctly knew that such changes did *not* cause any 'splitting').

Eventually, this *phenomenon of fork-resolution* was tapped as an upgrade tool[^n], where the miners would conspire to resolve the 'soft fork' always in a certain way. People then started using the term interchangably: to refer to both [a] a protocol upgrade, as well as [b] the resolution of an ambiguous chain-extension situation.

[n]: I vaguely remember this being Amir Taaki's idea, but I could not find a link for this, or any other source. In fact, I couldn't find a single thing that jogged my memory. Please let me know if you know the origin of the idea!

As time went on, software upgrades were discussed more, and fork resolutions were discussed less. Fork-resolution become very obscure topic mostly discussed among miners -- and these miners had become a professional, insular community. The original 'fork' problem was substantially mitigated by FIBRE, ['spv'](https://bitslog.wordpress.com/2016/01/08/spv-mining-is-the-solution-not-the-problem/) and ['spy'](https://bitcoinmagazine.com/articles/why-bitcoin-mining-pools-aren-t-incentivized-to-broadcast-blocks-quickly-1475249510/) mining, and other developments. The reverse, however, is true of software upgrades: they have only gotten more and more exciting and complicated. Thus, the second meaning became more dominant.


Below, let me try to present *my* definitions, with examples, before explaining them.


## Glossary

My definitions for various terms.

![image](/images/fork-terminology-clarified.png)

Image references:

[1]. [ETH/ETC Split](https://steemit.com/ethereum/@pauls/ethereum-fork-step-by-step-guide-to-safely-splitting-your-eth-etc) (Summer 2016) -- One has immutability, the other has a DAO-fix. ETH was technically released [July 2016](https://blog.ethereum.org/2016/07/20/hard-fork-completed/), [a year after ETC](https://en.wikipedia.org/wiki/Ethereum_Classic) was released; but the names are reversed. [More info.](http://nakamotoinstitute.org/mempool/who-controls-ethereum/)
[2]. [Qeditas](https://bitcointalk.org/index.php?topic=998559.msg10849564#msg10849564) (March 2015), [Bitcoin Cash](https://www.bitcoincash.org/) (August 2017)
[3]. Litecoin (October 2011), Primecoin (July 2013), Ethereum itself (July 2016), other well-known Alts.
[4]. Bitcoin Core 0.8.0, 0.9.0, 0.10.0, etc. 
[5]. [Bitshares 0.7](https://bitsharestalk.org/index.php?topic=5381.0) (July 2014), [Ethereum "Byzantium"](https://www.coindesk.com/ethereum-client-update-sets-byzantium-hard-fork-date/) (October 2017, assuming old chain stays dead) 


## Implications



### Upgrades Can't Be Splits

There's something of a paradox when refering to a "fork" as both a software upgrade and a "split".

An "upgrade" needs to be of the format "from X, to Y". For example, when someone upgrades "from v0.13.0 to v0.14.0", or when they upgrade "from a Honda to a Mercedes".

Consider the case of X and Y, below:

![images](/images/upgrades-vs-splits.png)

Curiously, the word "upgrade" does not apply to *either* of the two cases above. In the upper case, X merely remained as X. In the lower case, there is simply Y, and no X ever existed (Y merely appeared out of nowhere). Doubtless some **users** upgraded "from the old software to the new software", but we cannot say that the underlying protocol upgraded (ie, we cannot say that "Bitcoin was upgraded by a hard fork" -- instead we must say that "Bitcoin split into two protocols"). And, while Y might remember being X, since X is still here. X can't simultaneously be itself and not-itself, nor can X = Y (as, by definition, they are different).

So cases where the blockchain splits into two must be "spinoffs". And spinoffs must be different from hard forks.

This is why hard forks [the 'hard fork upgrade'] are said to require 100% support...they require the old chain to die. (In fact, I define a hard fork as: a split where the older chain dies.)

This leads us to the **hard fork fallacy** -- when someone falsely believes that a hard fork is "easy", because they only consider the lines of code that need to be changed, and neglect to consider the political effort involved in killing the old network. The hard fork is a political (or game-theoretic) endeavor, not an engineering one.


### Claiming the Old Name

If one thing splits into two things, they are no longer fungible with each other and hence they must have different names. In the case of the spinoff, it is clear that the older network will, by default, have the stronger claim to the original name. (Although, Ethereum demonstrated [in Summer 2016] that it is possible for the old network to lose its claim to the name.)


### Pre- and Post-Spinoff Values 

However, the *reverse* is true of the total value of the network (measured by market capitalization). If one thing splits into two things, they can always [henceforth] be bought and sold as a set (ie, one of each). And, of course, pre-split [before they were two things] these two tokens were also [necessarily] being bought and sold as a set. Thus, in the case of the split and the spinoff (and technically, also, the upgrade), in order to properly compare the pre-split network to the post-split networks, we must compare the value of the first to the sum of the value of the children.

( If you share [my views on True Money](/images/true-money.md), then all of these money-types are just portions of a single global money called "purchasing power". )



### Unenforced Rules are Meaningless


If we say that something has "introduced a change", without somehow also *enforcing* the change? Without enforcement, the change will simply change-back. Or perhaps it is a trivial "change" in name only, one which does not actually alter anything in the real world (like a non-binding United Nations Resolution, or a reddit post).

Soft forks introduce a change, *and* they enforce it. In fact, theoretically the soft fork "protocol" *allows* old beahviors, but in practice the blocks containing these behaviors will never be mined.

So, if hard forks are to parallel soft forks, they would need to both [1] introduce and [2] enforce their changes.

However, as I mentioned earlier, enforcing the rules requires the old network to die. If the old network remains, then **that** [old] network remains unchanged -- so we do not have a "change"!. In other words, we do not have a protocol upgrade or software upgrade.

Thus, just has the soft fork uses hashrate to enforce its new ruleset, so too must the hard fork use some kind of device or contrivance to enforce its new rules. Otherwise, it will merely become a new alternative, not a change to something existing.



### Dangers of Splits and Spinoffs

Splits are inherently undesirable as they contradict the very purpose of the blockchain -- which is to synchronize everyone's computers.

In particular, Bitcoin is *supposed* to be a form of internet cash. However, for the total duration of a split, neither of the two Bitcoin networks can reliably perform this service. It is easy to see in the extreme -- if Bitcoin split not once but many times, we would approach a situation where each user is on his/her own chain, at which point these networks would entirely fail to achieve their original purpose.

Ironically, despite the libertarianism they inspire in their users, blockchains operate in a rather socialist manner. Everyone is treated equally..."peer to peer". We're all "in this together". No one can pay extra to get a better service; there's no "blockchain premium". Its very much a public good!

Blockchains are a kind of community...with difficult-to-alter laws that are quickly and efficiently enforced. Like all communities, blockchains grow stronger as they include more and more people, provided that they can still cooperate effectively. However, since blockchains are about promoting community and cooperation among people, the split/spinoff is a contradictory re-assertion of individualism. There's certainly nothing wrong with individualism in general, but we should recognize that blockchains are for cooperation. Since blockchains have extraordinarily high [social scalability](http://unenumerated.blogspot.com/2017/02/money-blockchains-and-social-scalability.html), one blockchain network will probably grow into a community that dominates all others.


### More About Splits

A split implies the essence has changed -- the three concepts "whole" vs "left" vs "right" are categorically different from each other. Something that splits into two is usually two halves of what it was. Not so in the case of an upgrade (in which one thing becomes a new thing -- not two new things).


### Coercion

Hard forks (mandatory upgrades) are coercive, as are splits. But spinoffs are not. This assumes you define coercion as "an unwanted interaction from another person". And it also assumes that at least one person prefers to remain with the old protocol -- if the HF truly meets the nigh-unmeetable standard of "100% full consensus from everyone", then it would not be coercive, I suppose.

Soft forks are really "spinoffs" that occur within-one-network. They are spinoffs of feature-set, instead of protocols/networks. (see below)

With the sole exception of the soft fork, better blockchain designs are either [1] "Altcoin launches" (something new) or else they are [2] "political campaigns" (ie, they are 'efforts to convince a group of people to do something').


## Other Mysteries


### The Counting Rule

Bitcoin achieves consensus by examining data to meet certain criteria for relevance: validity and heaviness. But the Bitcoin system is clever in the strategy it employs to examine this data in practice. First, the software examines the headers, which are very small and easy to check. Then it validates the header-heaviness, which is small and easy to check, but very difficult to forge. Last, it examines the validity of the whole block, which is hardest to check. The protocol *rejects* blocks that are invalid, but of those blocks which are valid, only one "chain" of blocks is chosen to be The True Chain (ie, the "active" chain).

My point in bringing this up, is that while the "counting rule" (for measuring heaviness) is a "protocol rule", it is not a "validity rule". The *content* of the blockchain is the same; what is different is [possibly] how we resolve double-spends. Satoshi famously [changed the counting rule from "longest chain" to "heaviest chain"](https://github.com/bitcoin/bitcoin/commit/40cd0369419323f8d7385950e20342e998c994e1#diff-118fcbaaba162ba17933c7893247df3aL1215) in July 2010. Earlier, I expressed [my confusion over whether this change was a hard or soft fork](http://www.truthcoin.info/blog/protocol-upgrade-terminology/#none-of-the-above). Bram Cohen noted an interesting fact -- that [this rule could be changed by soft fork](https://lists.linuxfoundation.org/pipermail/bitcoin-dev/2017-March/013744.html).

The question is relevant because there is a dispute over the nature of a "Proof-of-Work algorithim change". Is this [a defining feature of Bitcoin](https://coinjournal.net/greg-maxwell-prospects-segwit2x-bitcoin-developers-may-leave-project-succeeds/)? Is it a "hard fork"; to what extent is it comparable to other hard forks?

Clearly, as I have just argued, it is not a "validity rule", and in that way it is *less* essential to Bitcoin's nature.

However, the act of changing it does un-make Bitcoin's double-spend protection, for un-upgraded users. And it clearly [creates a new protocol](/blog/better-fork-terminology).


![image](/images/counting-vs-validity.png)

Therefore, if you ask me, desite its quirkiness, and despite not being a validity rule, the counting rule is part of the protocol. Ignoring it would be an abandonmnet of "governance-by-algorithm" Satoshian Consensus, in favor of a [hopefully minimal] return to governance-by-men. Therefore, changing the counting rule is not only a hard fork in practice, but it is also a hard fork in spirit.[^n] And it deserves our suspicion as such.

[n]: Although, since the purpose of Satoshian Consensus is to resolve double-spends, if the miners attacked the network with a large reorganization, then it would be easy for each individual user to independently decide that the PoW-change was warranted. However, there would be confusion over *which* PoW to change to. To alleviate this confusion, I support a decision to ship Bitcoin with a deterministic, ordered list of replacement PoW algorithms.


### Evil Fork vs Extension Block

[The "Evil Fork"](https://petertodd.org/2016/forced-soft-forks#radical-changes) is generally considered to be a very bad thing. It destroys all of our precious consensus rules, and allows them to be arbitrarily rewritten. In that way, they may [harm decentralization (by making it more difficult for users to validate the blockchain)](http://www.truthcoin.info/blog/measuring-decentralization/).

But it seems that, as a category, \[mandatory\] [extension blocks](https://lists.linuxfoundation.org/pipermail/bitcoin-dev/2015-May/008356.html) would need to be considered to be exactly as bad.

![image](/images/evil-vs-extension.png)

Dr. Back acknowledges this in his post ["Here lies the risk - this imposes a security downgrade on the 1MB non-upgraded users..."], and he attempts to address it by going immediately to the reverse extreme, and making the entire sidechain block quasi-optional and creating new kinds of less-secure 1MB-coins. ([Drivechain](http://www.drivechain.info/) aims to make the new blocks fully optional, even for miners, and aims to achieve comparable security for returning txns.)

However, I'm not exactly sure what meaning the word "optional" is supposed to convey, in the context of extension blocks. Your node is trying to advise you on whether or not a given payment "went through". But with a soft fork it will assume that certain blocks are valid, even when perhaps they are *not* valid -- at least, not to everyone. Hence, when an old node encounters an 'unverifiable block', it might get a anxious.

In your typical garden-variety soft fork, there is little cause for anxiety. Typically, you can expect all miners to be validating using the newest rules, because the new rules can be expected to be more-or-less as easy to check as the old rules were. Therefore, should a dispute arise, you can expect the side with the tighter rules to ultimately prevail. Thus, there is a decent guarantee that all new rules will always be followed.

However, in the case of extension blocks, your node might need to be *very* nervous. Explicitly, some (most?) miners are not validating all of the rules, nor are some (most?) nodes. And this would be precisely *because* the new rules are more costly to validate than the old [or because there was some other dispute about validating them]. For that very reason, should a dispute arise, there is some uncertain chance that the side with the *looser* rules will ultimately prevail. For example, miners may decide "this is too much work for us to do, and furthermore we suspect this is too much work for most (all?) nodes, as well". Thus, nodes with a "mandatory" extension block might become very confused and frustrated, as the extension block is instead abandoned! The converse is true for an "optional" extension block -- it can unexpectedly become mandatory. For example, most of the network may believe (falsely) that all rules have been followed on all chains. Unfortunately, some miner is alerted to a tiny problem in one txn in an extension block 10 blocks ago. Perhaps the situation is plagued by even more ambiguities -- the problematic txn is a very trivial one, and it is located in one of the most-obscure, most difficult-to-validate extension blocks. Will the entire network go back, to fix this mistake? If miners decide that the answer is "yes", then the "optional" extension block turned out to be mandatory in practice [and there will be a 10+ block reorganization].

So, unfortunately, older nodes are responsible [to some degree] for checking the "new" extension block rules, and running the "new" code...at least in practice. So, there is a sense in which extension blocks are a mandatory upgrade, just like evil forks.

The second defining feature of the evil fork, is that it forces users off the regular blockchain system. It does this by barring all txns from the regular, non-extension part of the block. However, this is not a defining feature of any fork (ie, of a protocol-change); instead it is perfectly normal within-protocol behavior. Miners could instead continuously *fill* the blocks with transactions of their own making, [paying tx fees from themselves to themselves](/blog/miners-and-tx-selection), and the end result would be the same. Or else, all miners could decide to require an infinite fee/kb rate [as is their right].

Thus, extension blocks seem (to me) to be fully equivalent to evil forks. And, therefore, SegWit (which uses a mandatory extension block) was arguably Bitcoin's first evil fork! People who didn't want a blocksize increase are now on the hook for it, whether they like it or not.


## Conclusion

I have tried to lay down some definitions, emphasizing consistency. Interestingly, the concepts of an "upgrade" and "split" are mutually exclusive, so I use the word "fork" to refer only to the first (which is much more consistent with the historical usage). Changes in the counting rule are hard forks, and extension blocks try to be the best of all worlds but end up being the evil fork, the worst of all worlds.



-----

### Footnotes