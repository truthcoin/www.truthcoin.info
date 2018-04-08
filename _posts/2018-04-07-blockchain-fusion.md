---
title: Blockchain Fusion (via Compensated Sidechains)
show_author: true
comments: true
date: 2018-04-07 02:00:00
---



> An incentive-compatible way of fusing several blockchains into one. The effect is as if we could time-travel an Altcoin to the past, and add it as a sidechain then.

    Therefore thus saith the LORD of hosts, the God of Israel;
	Behold, I will punish the king of Babylon and his land
    --Jeremiah 50:18


I was writing [a post about a simple-enough way of fusing the UTXO sets of the Core and Cash blockchains back together](/images/blockchain-fusion-via-utxos/) into a single UTXO set of a single blockchain. But: there is a much better way -- easier to do, simpler to understand, and *more effective* as it allows for greater **replay** both of transactions and of code.

My view of "replay" is (apparently) somewhat rare. I wrote [a piece about this already](http://www.truthcoin.info/blog/mahf-and-replay/) but I will add more to the fusion-specific ideas below, before proceeding to the actual Fusion idea.


## Part 1. -- Replay and Other Background Claims

> "Replay" as a helpful tool, letting the best ideas compete fairly on their merits.

### A. Replay as Experimental Control ## {#replay-as-control}

My take on "replay" is that it is a good thing, akin to "controls" in experimental science.

They allow a project to [compete on as few **dimensions**](/files/multifactor-competition/) as possible, which is ideal.

I will discuss two types of replay, and how they control for various factors.

#### i. Transaction Replay

If a newcomer "Chain B" replays all of the txns from its predecessor "Chain A" (which [will always be possible](/blog/mahf-and-replay/#full-replay)), this controls for:

* Transaction fees, as any fees paid by A-txns will also be paid in B-txns. (However, these fees will be crypto-denominated, so their economic signifiance will not necessarily be the same.)
* The UTXO set (ie, **investors**), because, by default, any who invest in A will also invest in B (whether they like it or not).
* **Exchange**-adoption, for the same reason. Typically an exchange can veto a coin, by *declining* to list it. But they cannot de-list B, unless they are also willing to de-list A. If an exchange accepts A, it will nonetheless end up receiving an equivalent amount of B. When it sends this A away, it will also be sending the B away.

These factors all work together to unmake A's anti-competitive network effect. Crucially, the *defectors* (defined as: the all-important "investors who want to switch from A to B") must solve a few **coordination problems**:

1. The Loyalty Threshold -- *Should* we switch to B? Or should we wait for an even better coin? Once we switch to B, how loyal should we be to it? Should we defend it at all costs, or should we be ready to defect to a better coin when it arrives? How much loyalty should we show to networks in general -- should we each keep selfishly defecting (until we are each alone on our own networks)? If not, why are we leaving A in the first place?
2. Timing -- *When* should everyone switch? After all, even if the defectors amount to a majority (say 70%), it is necessary for them to all switch at the same time. If 20% try to split "early", they will be defeated by the remaining 80% (and 50% of these 80% will be, tragically, their own teammates).

If there is enough uncertainty on either problem, it can lead to self-fulfilling prophecies of [rational ignorance](https://en.wikipedia.org/wiki/Rational_ignorance) and failure.

It is the second problem ("Timing") which is solved by a "pro-replay policy". Such a policy acts to place everyone's money is in a kind of synchronized "dropbox folder" -- a user's "A wallet" and his "B wallet" are being kept "in sync" across both networks. Thus, *someone who does nothing* can never "miss the boat" on "the" transition from A to B ("their boat" is always "kept waiting" for them).

In other words, the "do-nothing-ers" are placed on both sides at once, not only now but also at all future times. This is **crucial** because, without the pro-replay policy, these individuals would belong to Network A. But, with the policy, they are the property of *neither*. As a result of this, the conflict between A and B must be decided only by users who decide to take "active action". And for such users, there is no "network effect" biasing the contest in one direction or the other.

Conveniently, the *first* problem ("Loyalty Threshold") can be solved by "sidechains technology" itself (assuming B has it, and A lacks it). This tech would make B objectively better than A, but more importantly it acts as a kind of "final solution": it provides a guarantee that users of B will *never* need to switch again (in terms of actively abandoning the network via hard fork), as the B-network can copy rival networks using sidechain tech. So, for the users, it is "one effort to end all efforts".


#### ii. GitHub Replay

It is also necessary to control for the influence of **developers**. There are strong network effects to codebases, as well --it takes so much effort to *read* code, and the Bitcoin codebase changes so frequently. There are also psychological pressures keeping people "in" groups -- basic specialization of labor (and conflict-avoidance), desire to be a part of a "big" [meaningful](https://www.meltingasphalt.com/a-nihilists-guide-to-meaning/) project (and one that future employers will recognize).

As a result all of the best people are in one "big" group, which Trace Mayer (for one) [has referred to as](https://twitter.com/TraceMayer/status/818467929394135040) the "Dream Team".

![image](/images/trace-dream-team.png)

But we would like to eliminate this standard of comparison as well (the "developer skill" standard of comparison). Because we want to control for as many variables as possible.

Fortunately, it is quite simple to do: just organize the code so that it contains as few changes as possible, and make these changes in a very modular way. And then invest all of your effort in rebasing early and often.

I call this "GitHub Replay" -- just try to make the codebase of B match the codebase of A, as much as you possibly can. This includes "good features" as well as "controversial features" as well as "bugs".

The reasons for this are many-fold. One is that it makes maintaining the project easy -- the maintainers of A are doing it for you (again, whether they want to or not). A second is that you get access to cool new features -- whenever they are released on A, they will also be released on B. Third, there is no need to engage in any kind of imperfect "governance" or "dispute resolution" process over which features should-or-should-not make it into the codebase. But the most important reason is to neutralize Trace-Mayer-"dream team"-style arguments -- we want *all users and investors* to **know** that the technological improvements will be identical for both projects.

The biggest challenge when implementing "GitHub Replay" will certainly be: fighting off the do-gooders who insist on adding *that really awesome feature* to "B". "After all", they will say (missing the point completely), "this is a really good feature". These people must not only be prevented from adding their feature, but they (and anyone who took them seriously) must be openly humiliated. They are a threat to the project (much like major corporations and governments cannot even *joke* about defaulting on their debts) and their influence should be zero.

If "B" has a policy of "GitHub replay", then the appropriate way to modify B's codebase (with a "really good feature") is to make the necessary modifications in "A". If A won't let you make those modifications, then too bad! Start your own project, far away from B!


#### iii. Controlling for Past Mistakes via "Compensation"

As seen above, the replay techniques above ("Transaction" and "Github") can make a 'competitor project' (there called "B") very competitive indeed. But in "Blockchain Fusion" we will control for one additional thing: the investors past mistakes. We will be playing the part of Christ (instead of Nietzsche), and forgiving past sins (at least, for a few chosen people), using something called a *compensated sidechain* (see below). We will do this in order to bring those people over to our side; we need them in order to build a "winning coalition" (one with >50% marketshare). We need this winning coalition, in order to convince the losers to give up -- in other words, to intimidate them into settling for an *uncompensated sidechain*.

#### iv. Terminology Overview

* Bitcoiner -- Someone who invests in Bitcoin [[likely](/images/blockchain-fusion-via-utxos/) to own BCH and Btc-Gold, as well as BTC]. 
* Alt-chain -- A blockchain with "alternative" rules; (usually) a non-bitcoin blockchain. BCH and BTC are Alt-chains of each other. 
* Altcoin   -- A non-Bitcoin blockchain token that is made available for investment; (usually) non-BTC money.
* Sidechain -- An alt-chain that is not an Altcoin. As with "Alt-chain", one must be a sidechain "of" something.
* Altcoiner -- Someone who invests in Altcoins.
* Bitcoin Maximalism -- The practical observation that money has strong network effects, and that the Internet cannot be partitioned into >1 'optimal currency area'. It is also a moral observation: that "altcoin competition" is inferior to "sidechain competition", because the former involves grave (and pointless) offenses to truth and to human decency.
* Uncompensated Sidechain -- A sidechain whose success would bankrupt the Altcoiners of its predecessor-Altcoin.
* Compensated Sidechain -- A sidechain whose success will not alter the net worth of its Altcoiners.

The details of the "Compensated Sidechain" are in the next section, but I wanted to introduce the concept here. It summarizes our situation: people these days do not say "Bitcoin", they say "Bitcoin and cryptocurrency" (see ["Bitcoin Post-maximalism"](/blog/bitcoin-post-maximalism/).

![image](https://upload.wikimedia.org/wikipedia/commons/3/37/Wpdms_physics_proton_proton_chain_2.svg)


## Part 2. -- The Fusion Process

> Merging two or more crypto communities, without permission (ie, "veto-immune").

### A. Process Steps

#### Caveat

In the explanation I am about to give, I will use two variables: the **marketcap** of a coin, and the **quantity of coins outstanding**, and I will use them separately and for two different purposes. While the equation "marketcap = quantity_outstanding \* price" is a true one, it will not help readers understand the fusion technique below, and instead I believe it is likely to be distracting.

#### Basics

In this technique, we aim to replace the multi-coin landscape with a single-coin landscape.

So we start with some **basic steps**:

1. Soft-fork Bitcoin Core to add sidechains tech; and softfork it again to add all of the 'Target Altcoins' as 'sidechains' of Bitcoin Core. A draft of [this technology is available here](https://github.com/drivechain-project/bitcoin/tree/mainchainBMM).
2. Make the usual modifications to each Altcoin's codebase transform an Altcoin into a sidechain: change the coinbase txn so that it does not "mint" new coins, add support for merged mining (or blind merged mining), and add the "main-to-side" and "side-to-main" transfers.

However, for Blockchain Fusion, we *also* aim to leave the *relative wealth* of all Altcoiners unchanged. In fact, we want individual net worth to be unchanged for anyone who owns anything in the "Fusion Set", which is "all the blockchains we are fusing together (1 main + X side)". 

#### Special

So we now do some **special steps**:

1. In the mainchain (Bitcoin Core): hardfork in order to counterfeit new BTC, and immediately deposit these BTC to each sidechain, such that the post-hardfork "coin proportions" are equal to present day[^1] "marketcap proportions" (see table below).
2. Inside each sidechain itself: modify the GUI code, such that it displays altered coin amounts to the user. Specifically, it displays lower amounts than those stored in the database of the blockchain itself -- the amounts are adjusted downward to compensate for lower "marketcap proportion" as well as higher "initial Altcoin supply". The "side-to-main" transfers must also be rescaled with this in mind.


![image](/images/fusion-table.png)

[^1]: To make the metric robust to last-minute manipulation, it would be best to take an average over some two week period.



#### Terminology Review

Here were some new terms we used:

* Mainchain -- The "source of truth" when a blockchain disagrees with its sidechain. Has less risk but fewer abilities. "Bitcoin Core" in this example.
* Sidechain -- The "plugin" to the Mainchain -- has the benefit of being optional for network users, but the drawback of new (hopefully minimal) risks.
* Target Altcoins -- All of the Altcoins we would like to fuse together into one interoperable economic system.
* Fusion Set -- The 'Target Altcoins' plus the Mainchain (BTC in our example). The "guest(s)" plus the "host".



### C. The Results

These steps create a completely new project, but one that is overwhelmingly similar to the existing Fusion Set.

More crucially, this creation is highly permissionless. Exchanges can NOT withhold support for the coin, they must list it whether they want to or not. Developers can NOT withhold support for the coin, they must developer for it whether they want to or not. The same for all researchers and promoters.

The coins will remain entwined for a long time, until they eventually decouple. But this is desirable as, without it, you can never "win" (you can merely "tie" for first place indefinitely). The trick is to just avoid insta-losing for a time, so as to give your new ideas [a fair shake](https://www.merriam-webster.com/dictionary/fair%20shake).


### D. Political Fallout

If this idea succeeds, there will be winners and losers.

Some of these may depend on optional steps (see next section).

Big Winners:

1. Altcoin Investors (Fusion Set only) -- pre-Fusion, these investors face a large risk of ruin (via competition); post-fusion that risk is removed.
2. Altcoin Developers (Fusion Set only) -- pre-fusion, they were social outcasts; post-fusion, they are nearly on par with Bitcoin Core Developers.


Winners:

1. Bitcoin investors (assuming effects from [1] Metcalfe's law, and [2] new monopolistic barriers-to-entry).
2. "Non-partisan" Bitcoiners / People who find the scaling debate boring / people who are tired of hearing the phrase "Bitcoin and crypto-currencies".
3. Pro-sidechainers.
4. Bitcoin Miners (if no PoW change) -- in addition to higher BTC price (see 1), these miners now receive all txn-fees on all chains (Fusion Set only).
5. BTC Custodians (such as Coinbase) who are baffled by how to handle new spinoff coins. Post-fusion it is easy: ignore all of them; they should be instead be sidechains.


Losers:

1. Holdouts for 'Orthodox' Bitcoin Maximalism (for example, [Tone Vays](https://twitter.com/tonevays/status/793257954464202752) (R)) -- pre-Fusion, there was opportunity to profit at the demise of the Altcoins; post-fusion, there has instead been a compromise 'surrender' with *some* Altcoins.
2. Similarly, people who [naively] mistake the "inflation" in this idea for the "inflation tax". The latter is an [arbitrary redistribution of wealth from someone to the counterfeiter](http://steshaw.org/economics-in-one-lesson/chap23p1.html), but the former is just [an *acknowledgment*](http://www.truthcoin.info/images/true-money/) of the present situation (an acknowledgment of the inflation that has already taken place). We are trying to stem the bleeding. But some people won't see it that way -- they will feel as if they've lost something dear.
3. Prestigious BTC Core developers -- Pre-Fusion, these are monopolist border guards demanding to see ["papers"](https://opinionator.blogs.nytimes.com/2014/08/08/papers-please/) justifying the passage of code from one repository to another; post-fusion, users can always opt to use a sidechain simulator to travel (without permission) and so border guards are not necessary.
4. Business Models linked to "Developer Prestige" -- a "special arrangement" or "exclusive access" to these border guards (see 3, above) is no longer as valuable. The most famous example is Blockstream, but the business model is prevalent among both Democrats and Republicans.
5. People who secretly enjoy the scaling drama. This includes:
    * "Sheep" -- uncritical, gossipy people who have nothing useful to contribute to any community, other than the political noise they make.
    * "[Blockchain] Justice Warriors" -- people who join a cause so as to feel more righteous (usually because they know that, deep down, they are themselves ethically impoverished and un-righteous) and who then become addicted to fighting it. They do not know how to win respect in the usual ways, and don't know what they would do with themselves if the war ended.
6. "Party Leaders" / campaign managers / pollsters / propagandists / anti-propagandists / etc (such as /u/theymos (R) and John Blocke (D)) -- They are now unnecessary, because it is no longer a "single winner" zero-sum game. There is no election 
7. People who tried to solve scaling in the past, and failed. A newcomer's success will reflect badly on them.


Big Losers:

1. Altcoin miners -- their equipment is worthless.
2. Current Bitcoin Miners (if PoW change) -- their equipment is worthless.
3. Altcoin investors (NOT in the Fusion Set) -- their investment is (likely) worthless.
4. Scammers / Crazies who come up with "new" blockchain "ideas" -- post-fork these crazies are unlikely to be able to monetize their new ideas.

### E. Optional Add-Ons

#### 1. Also change the proof-of-work algorithm.

Many people (most notably, Elite Core Developer Luke Dashjr and Bitcoin.org domain owner "Cobra"), feel unsatisfied with the level of service provided by our current miners. They feel that the time has come to change providers. (For what it's worth, I am indifferent.) 

Since the proposal already requires a hard fork, it is easy to "tack on" a PoW algo change. The costs to us are very low, but we may benefit greatly by gaining support from influential people.

If the PoW is changed, the difficulty should also be reset completely (to zero). And we should also add a warning to users that, at least at first, they should wait for *many* confirmations (say, 100 or so). This would allow hobbiest miners again, for a very short time, and create a lot of "buzz" around the fork event.

( I don't think we should take any other ["hard fork wishlist"](https://en.bitcoin.it/wiki/Hardfork_Wishlist) items, for a few reasons. Some of those reasons are similar to the "Github Replay" reasons above. Another is that doing so would open a [potentially endless, and unproductive] discussion over which wishlist items to take, and which to leave. )


#### 2. Announce the Fusion well in advance / Hype it up!!

One of the numerous weakness of Bitcoin Cash is what it was "stealth launched" unexpectedly on August 1st. Worse, it was framed as a superfluous / at-best experimental project, and then re-framed in November as a "payments blockchain". And even worse, this reframing was ambiguous and occured slowly over months.

All of that (above) is anti-coordinative "network effect fuel" for BCH's competitor BTC. People who are indifferent, or who could not understand the conflict, may have already received BTC during this period, and they are then hostages of the BTC network.

Instead, it is better to announce a competitor well in advance, and have it marked by a salient, well-known date.

(And, as I've said above, even that is not enough. We need to protect the indifferent folks from capture, by relaying as many of their txns as possible.)

With this in mind, it follows that it is a good idea to announce the Fusion well in advance (say 6 months), and to talk about this event as often as possible.

( However, the compensation ratio should be frozen as soon as the Fusion is *announced*. Otherwise the intra-Fusion Set valuations could become highly unstable [and pointlessly so]. )


#### 3. ERC20 Scamtoken for Meme Fuel / Privatization

For maximum hype, it may be desirable for someone to create an ERC20 token "for the purpose of financing the required development work".

That reason is in quotes because it is, of course, merely a *pretext*, aka a "good sounding (but ultimately fake) reason that provides cover for the true reason". The true reason would be to create large amounts of hype and buzz, and give investors early skin in the game.

It would work (despite my explaining it) because there really *is* a small but non-negligible amount of work to be done, and someone needs to do it; and it really *is* beneficial to allow the free market to go to work on this idea as early as possible. Money is a meme, and we know that the ERC20 token is effective at virulently spreading memes.

The token could be guaranteed to have a future value, in exactly the same way that the "compensated sidechains" would be guaranteed to have a future value: by fusing it in, as well!

Of course, this token really shouldn't be allowed to have *too* high a value. After all, the entire cryptocoin marketcap is currently ~ $370 Billion, and how much money does it take to do 'basic coin promotion' for a few months? Surely a few million is overkill -- so the value of the token could be capped at, say, 1/10,000th of the total new BTC supply (bringing it to ~ 37 million USD).

Such a token would give us some "project owners" -- individuals with an incentive to move the project over the finish line. This "privatization" is effective (even though [the transactions costs of negotiating it are often prohibitive](https://en.wikipedia.org/wiki/Theory_of_the_firm)).

Perhaps, the best way would be to just overcompensate the Monero chain (or any fungibility-optimized chain -- we don't want them blacklisted/tainted later) with 2,000 extra units or so. A project administrator could award these to the people who contributed most to the Fusion's success.


#### 4. "Split Aware" Clients

The "Fusion software" could very easily be made aware of which of its tokens are "in sync" with their originator Altcoins/mainchains. A quick-and-dirty way would be to just compare the UTXO of the local fusion coin, against a query to a predefined blockexplorer. 

This makes it easy to see where other people stand (which is, hopefully, still 100% synchronized).

The level of synchronization will, of course, be steadily falling over time. There will be various ways of (slowly) "de-syncing" your coins (by mixing with coinbase txns, or by sending to/from sidechains). When the synchronization level falls below 50%, we can look at the marketcap of the "Fusion BTC" coin: if it is very high the project has succeeded, and if it is very low the project has failed.


#### 5. Specialization of Labor

If we are changing from a mono-chain to a multi-chain world, I think we may decide to take an opportunity to achieve *specialization* by [making two of the networks more different from each other](https://www.youtube.com/watch?v=Gzg_u9gHc5Q&t=6575s).

Specifically, we could decrease the Core blocksize (say, after a transition period of 6 months [26,000 blocks]) from (1,4)MB to (0.35,1.4)MB. Meanwhile, we could program the Cash blocksize to [steadily increase from 8 MB to 8,000 MB over the next five years](/blog/gigachain/). In this way, we could please several different groups of currently-disenfranchised people at once.


#### 6. Achieving Laziness via Hobbesian Trap

The less work, the better. This idea requires some development work (details above) to be done on each Altcoin in the Fusion Set.

Perhaps, this work will be voluntarily (and quickly) done by the Altcoin developers themselves, and not the proponents of this project. Why? Because an Altcoin *cannot* join the Fusion Set unless this work is done. And not being in the set is fine if the Fusion fails, but it is disastrous if the Fusion succeeds! Risk-averse Altcoin investors may insist on it!

It is a kind of [Hobbesian Trap](https://en.wikipedia.org/wiki/Hobbesian_trap), in our favor.


#### 7. Tx "ffff" / Faster Initial Synchronization

Probably easiest to create the new BTC in one special txn (perhaps with Tx version "ffff").

And, since the security model is already hard-fork-based, there may as well be a validation checkpoint right after this txn.

This has the funny side-benefit of making initial synchronization much much faster, as all of the validation can (indeed, must) be skipped.

#### 8. Sidechain Security Assumptions

One could argue that Fusion is relatively disadvantaged, because it inherits a security risk from drivechain (the 51% coin-theft attack -- I of course have published extensively on this risk and its corresponding reward).

But it actually does not need to inherit any new security assumptions, unless it wants to. Instead, one could force all users to fully validate all blocks. Then all rules everywhere would be mandatory, and there would be zero new security assumptions.


### F. FAQ

#### Inflation? Have you completely lost your mind?!?

Well I don't think it is that simple.

First of all, for a fusion of just Core and Cash, most users have not split their coins. So most users will not experience any inflation tax -- they will have more coins, but the same proportion of overall coins. For them, it will be like switching from dollars to cents.

So most users will actually not experience any inflation.

Second, sacrifice is a natural consequence of a compromise. Fusion is an alternative to "fighting". If one "fights" and wins, then one is better off than compromising. But if one "fights" and loses, then one is worse off.

In other words, many investors hold an intentionally "undiversified" portfolio -- they want to profit off of the downfall of rival crypto-currencies. BTC wants to profit from the downfall of BCH, and BCH wants to profit from the downfall of BTC. Logically, only one group can get their way, and this group will face a consequence that is identical to one where an infinite inflation tax has destroyed all of their wealth.

So it is a question of degree, not principle. It is a question of which wealth-destruction risks one prefers to take.  

Third, by Metcalfe's law, the fused network should be stronger than any of its pieces. In Bitcoin's case, we have Bitcoin.org and Bitcoin.com advocating different networks. The resulting confusion is a deadweight loss on both projects. Does anyone in BTC have a workable plan to get BCH-supporters to surrender? Or vice-versa?

Fourth, there are unique benefits to a Core-Cash Fusion. One is that it partially solves the "default network" problem -- the idea that, while sidechains tech allows users to use any blockchain they like, it does not put their coins on their preferred blockchain by default (because the software doesn't know what the user's preferred blockchain is, of course!). Users must make a transaction on the host blockchain in order to emigrate from it. This is especially problematic for low-value UTXOs, which would be trapped on a smallblock mainchain, even if they were free on a largeblock sidechain.

#### You still believe in Bitcoin Maximalism, yet you propose this "surrender" idea?!

Yes, my confidence in Bitcoin Maximalism is now a little lower than it was. Whereas in the past, BTC was 99+% likely to be the world reserve currency (conditional on cyptos succeeding as world reserve currency), today I believe the likelihood has fallen to 75% or so.

The failure scenario would involve: specific government ban; heavy promotion of a bunch dumber project (to a critical mass of unintelligent users); intentional displacement of BTC with cheaper alternatives, while intentionally *not* harassing full nodes (or even protecting them by law) so as to neutralize Bitcoin's decentralization advantage. Today, this combination of factors is downright likely -- anyone with a brain will figure it out and do it, and Bitcoin has many enemies.

So I think we should at least talk about doing something that would bring it back up to 99+%.

#### Are you currently working on this?

No. It is an idea, free for anyone to use.

I myself am not really sure if I like it or not.

Also, I think the traditional idea of "*campaigning* for features" doesn't really apply in Bitcoin (see below).

#### Why write this post?

One reason is that I kept hearing that it as "impossible" to re-merge the two chains. But I believe that I've found a very easy way to do it -- one just needs to recognize that [the dreaded](https://en.bitcoin.it/wiki/Hardfork_Wishlist#Currency_changes) [inflation](http://steshaw.org/economics-in-one-lesson/chap23p1.html) has [already taken place](http://www.truthcoin.info/images/true-money/).

In fact, it may be so easy as to [be inevitable](https://twitter.com/CobraBitcoin/status/945678874049990658).

 ( With a little cleverness, the user is not even burdened with a [multifactor competition](/images/multifactor-competition/) problem. In fact, even the new drivechain security assumptions can be torn out -- by making all of the sidechains mandatory, we would technically still have achieved the objective of "fusing two or more blockchains". )

Second, I have been waiting patiently to launch [my Prediction Markets project](www.BitcoinHivemind.com) as a sidechain for a while now. However, in the process of waiting, I've been able to observe the rise of Monero in particular. Monero hard forks every six months, but it is unclear to me how they would continue this tradition as a sidechain (it could be done in a few different ways, and each way has its pros and cons). It made me wonder if my own project would need one or two post-launch hardforks (I hope not).

And in turn this led me to wonder if other alt-chain projects would also like that flexibility. So, in order to accomodate those people, here is another alternative: to launch as an Altcoin first, and then merge with Bitcoin later as a compensated sidechain. (The mainchain might try to prevent this, by responding with an uncompensated sidechain.) Not my first choice, but something I am considering.

Finally, to mention a solution to the "default network" problem (mentioned above).

#### To what extent will you associate with / help anyone who wants to do this?

I'm happy to help! Just as with all of my other ideas.

#### What was that about "campaigning for ideas"?

Yes. Two points. First: Bitcoin is different from other open source projects -- you *need* a critical mass of the community to go along with you, else you will not succeed. So changes are inherently political, not technical.

But second: Bitcoin is also different from an election. In an election, if 3 people vote "A", and 4 vote "B", and 19,993 abstain from voting, then "B" will win the election and govern all 20,000. But, in Bitcoin, "B" would not win. Instead...nothing would win. The status quo would prevail.

Bitcoin is more like a house party. Perhaps, all of the guests are hanging out in the living room, and you want everyone to head to the backyard swimming pool. Your best strategy is to state your case, and reasoning, but then not to press the issue. So, mention how the house is 95 degrees F and has no ventilation, and that the pool area has the perfect amount of shade and a stocked minifridge and grill nearby.

But if people want to stay and chat for the time being, you basically just need to let them. I mean, what do you want to do...go out there alone? And then dejectedly come back inside after no one joins you? That's pretty lame. No one wants to be that guy.

So if you are too direct, people will know that their 'network effect' is being ...appropriated. So, be mindful of this, and **read the room**. Hashrate signaling (soft fork only) is one fast and easy way, and [fork futures](/blog/fork-futures/) are the more cumbersome, but more accurate way ([MAHFs](/blog/mahf-and-replay/) and UASFs).

To that end, I think it would be great if an exchange made fork futures of this idea. Everyone could learn how popular it is, including me.


#### Do you think this is an "attack" on Bitcoin?

In the sense of being a strong competitor, the answer is yes. But that is precisely the way in which BTC is "an attack" on the US Dollar.

The currencies are all in a constant state of attacking each other. This is why Bitcoin Maximalism is actually the correct *moral* position in addition to being the most reasonable -- sadly, very many people are incapable of grasping this simple point, especially the fraud Tim Swanson. We maximalists just wanted peace and harmony for all.

People can have very strong views when it comes to politics and money, and these often lead to boorish *performances* (eg, virtue signaling) in place of real thoughts. But anyone who supports consumer sovereignty, competition, and disruptive technological progress would probably be open-minded about Bitcoin Fusion. It is a very "cheap" experiment to run, because there is no marginal risk to user's funds. Users incur no new risks that they are no already incurring.

My view is still that there would be no need for Altcoins at all, if Bitcoin had working sidechains. And so there would also be no need for Fusion. But it seems that almost no one agrees with me (because if instead they *did* agree, Altcoin [prices would already be](https://en.wikipedia.org/wiki/Efficient-market_hypothesis) near-zero). Instead, the market seems to expect sidechains to never arrive.


#### What coin(s) do you think should be Fused?

Unfortunately, one contender is certainly Core + Ethereum. This immediately puts the Fusion coin at a healthy 60+%, and Ethereum has the strongest community after Bitcoin. I'm not really a fan of Ethereum as I find its design to be ridiculous.

A second contender would be to start with the "Bitcoin Children": Core + Cash + Gold + Litecoin + Zcash. Unfortunately, these amount to only (45% + 4% + 0.1% + 2.5% + 0.1%) = 51.7%, which is just barely a majority.

Perhaps this second group could be modified to include Dash and Monero, picking up an additional 2%. Perhaps it would also include Sia (but this adds only another <1%).

But the simplest, easiest, least-contentious fusion would probably be BTC and BCH, of course. 

#### Do you actually think this will happen?

I really don't know. Certain communities, such as Monero and Litecoin investors, would probably be strong supporters of this idea.

Possibly, BCH supporters who are having second thoughts, would want to use a Fusion to de-risk their position.

But there will be a lot of loud opposition, because today it is popular to pretend to be unconcerned about blockchain technology's eroding network effects (more below).

I think it would be quite healthy for a community to be made up of people who each *begin* with some store-of-value coins AND some medium-of-exchange coins (the "default network" problem, above).

#### What do you say to holdouts (incl [Peter Thiel](https://www.cnbc.com/2018/03/15/peter-thiel-is-betting-on-bitcoin-to-be-the-online-equivalent-to-gold.html)) who think Bitcoin Core will just win on its own merits, ie without help from Fusion? #### {#holdouts}

I believe in network effects just as much as them, if not more!! But the one thing I would ask them to explain is [the rise of the "Others" category](https://coinmarketcap.com/charts/#dominance-percentage). We've observed this phenomenon consistently over the past five years[^2], and it seems to be an empirical challenge to the network-effect theory.

[^2]: In the beginning, this metric stood at zero. From there, it rose to 1.2% by March 2013, and then steadily to 5.3% by March 2017. From 3/2017 to 3/2018, in accelerated erratically to 18.09%, and is now the #2 category. It has been ahead of Ethereum (the #2) for the last three months.

See: ["On the Use of Marketcap as a Measure of Cryptocurrency Value"](/files/on-marketcap/)

It is possible that each blockchain has network effects, but that "blockchains" as a whole do not. In other words, within each blockchain-network, "more users"="more value per user". But users do *not* always prefer to join the largest network.

Why might this be? We can look at the costs and benefits of joining a new blockchain network.

Newcomers have a larger risk with a new community, but also a greater reward. So the benefits are higher -- adopters get kudows for being 'trendy', like getting "into" a new band, or a new fashion, before one's peers. This explanation seems to be a good one, as it also explains the rise of Litecoin (especially) and Altcoins (generally) in the first place. And it explains comorbid symptoms: feelings of having "missed out", the desire to locate "the next Bitcoin" (or "next X"), Alt-community kindness towards newcomers.

On the costs side, let us appreciate that newcomers have it easy realative to, for example, "learning a new language" or "learning how to drive a stick-shift automobile". Because of [Gwern's observation](https://www.gwern.net/Prediction-markets#fnref14), one only needs a few ["not more than ten"] of a new coin. Thus, Altcoin communities are cheap to join, and so joining does not represent a big unalterable commitment.

While I agree that one should ["bet on the biggest"](https://www.cnbc.com/2018/03/15/peter-thiel-is-betting-on-bitcoin-to-be-the-online-equivalent-to-gold.html), ironically, BTC is today *smaller* than a Fusion of all of the Non-BTC. So, in that sense, Bitcoin is not really the biggest.

#### Isn't it completely insane to propose altering the 21 Million coin limit?

Yes, I think so. But I have been wrong several times before -- I thought that both the SmallBlockers and LargeBlockers would embrace sidechains as a solution to their problems. Instead, however, it is endorsed by neither as it competes with both the Lightning Network and with Bitcoin Cash. It seems the community effects are so strong as to be utterly overwhelming. So an idea that takes this view seriously (that communities are valuable and that we can safely unite them into a larger stronger community), may be useful.

And, keep in mind, that Fusion could be [accomplished via UTXO-merging](/files/blockchain-fusions-via-utxos/). This would "keep" the 21 million coin limit, but users would have a smaller actual coin-balance. Mathematically these are the identical outcomes! So **any Fusion technique will necessary involve some "theft"**, whether this be via inflation or else by explicitly reducing an account balance.

After all, the "BTC-only" holdouts (above) plan to profit on the failure of their BCH rivals. But "BCH-only" fundamentalists have the equal and opposite view. And each group is logically consistent -- if they "challenged and won", they would be better off than if they "compromised". But these views are fundamentally non-integrate-able -- we cannot have two winners.

Meanwhile, the conflict is holding everyone back -- lots of time is wasted online sh\*tposting, time which could be spent building cool stuff. Users who are forced to choose between BTC and BCH, will probably instead decide that "Bitcoin" is not a meaningful term, and that instead they should invest in some kind of index fund or portfolio of "crypto". Or else they will turn to Ethereum.

New technology (ie, lightning network, Schnorr, sidechains) is not reversing these trends. They started badly in 2013, and have consistently gotten worse ever since.

As the [market concentration](https://www.investopedia.com/terms/h/hhi.asp) falls (and Pluralism increases), Fusion will become more and more attractive; and it will get more and more "expensive" (ie, require more inflation). This should worry single-coin holders (and miners who fear a tacked-on PoW change).


## Two More Points

### Altcoin Circular Logic Valuation

Some might argue that Fusion has the problem of setting a bad precedent. It gives Altcoin valuations a kind of circular logic, such that no matter what value they are, that value can always be justified via a hypothetical immediate Fusion at that value. And hence it leads quickly to contradiction.

It is true that users should worry about what they (collectively) do, because what they do is relevant.

But I think this is a slippery slope fallacy -- just because Fusion is done once, does not mean that it will be done again. And if the first Fusion succeeds, it is no guarantee that later fusions succeed.

So the precedent that is *actually* set is one of "the users being awesome and making more money for themselves". If XYZ works, then people should do it, and they'll probably succeed in doing it. If XYZ doesn't work, then people shouldn't do it and they also probably fail in doing it.

It reminds me of the claim that Wladimir "controls" Bitcoin development, because he controls the GitHub repository. This claim is significantly untrue, because if a non-Wladimir released more-useful Bitcoin software, then users would switch to it and so the network would ultimately come to rely on it. And then this neo-Wladimir could himself be usurped by yet another challenger. Truly, it is the user who "writes" all the software.


### On Measuring Support

As I hinted at above, the "loud" supporters of each side plan to profit from their rival's demise. Therefore, we can expect them to dislike this idea -- instead, they want to win unilaterally.

Since both groups will loudly dislike the idea, it will *appear* as though the Fusion idea is very unpopular. But the appearance is, perhaps, likely to be deceiving. [Most coins/UTXOs haven't moved since the left-right Aug 1 split](https://forks.network/dashboard/db/bch-btc-fork?orgId=1), so most people have no dog in the fight whatsoever. In fact, if one accounts for bias in the metric, due to the imposed mandatory replay protection, the true level of divergence may be as little as 10%, or smaller. So I wonder if there isn't a very large "silent majority" that would support Fusion. If so, they could be cheaply detected via appropriate [Fork Futures](/blog/fork-futures/).



### Conclusion

    Every great magic trick consists of three parts or acts.
	The first part is called "The Pledge".
	The second is called "The Turn" -- the magician takes the ordinary something and makes it do something extraordinary. 
	But you wouldn't clap yet. Because making something disappear isn't enough; you have to bring it back.
	That's why every magic trick has a third act, the hardest part, the part we call "The Prestige".
	-- The Prestige (2006)

Metcalfe's law states that Bitcoin would be more valuable in general, if it were more valuable relative to other coins. Teamwork is valuable.

![images](/images/council-of-elrond.jpg)

I am not sure if Fusion is the best way to go, but someone will probably do it eventually. So I am glad to have written down my thoughts on it.

------

### Footnotes

