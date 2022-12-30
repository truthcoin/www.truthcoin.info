---
title: Lightning Network -- Fundamental Limitations
show_author: true
comments: true
date: 2022-04-04 05:00:00
---


I use basic arithmetic to derive limitations of the Lightning Network. Because the analysis is so basic, I hope it will [1] stand the test of time, and [2] be easier for everyone to understand.

### Summary

* Channel-open transactions must be broadcast on L1, but there is simply not enough L1-space.
* "Factories" can onboard more users per L1 txn. Unfortunately, they can be sabotaged for free. CoinPool has the same problem (when it comes to LN-onboarding). The limitation is fundamental.
* There are scenarios where LN-users consume *more* bytes than L1 "onchain" users. These are interesting, especially when it comes to use of HTLCs.

The "conventional layer2 strategy" (of: "Core + LN + nothing else") is almost certainly not viable. But a modified strategy, of "Core + Largeblock Sidechain + LN" is viable.


## 1. The Onboarding Problem (With No Factories)

### A. The (Implausible) Best Case Scenario

Consider these "best case scenario" LN onboarding-assumptions[^1]:

[^1]: I did this type of analysis [on the bitcoin-dev mailing list, two months ago](https://lists.linuxfoundation.org/pipermail/bitcoin-dev/2022-February/020018.html). No one seems to have challenged it.

1. Blocks are *only* used for LN-onboarding. (100% of the blockspace is used for LN-open txns.)
* Each block consists of two transactions: the coinbase, and one transaction selecting one input and paying out to 23,251 taproot outputs.
* Approximately 999,750 vbytes would be used for new channel-open-outputs. The remaining 250 vbytes allow for the (required) coinbase; plus the (required) overhead of the second txn (one input, nLockTime, change output, etc).
2. Each channel-open costs 43 vbytes.
* Unfortunately, taproot outputs (P2TR) [are 43 bytes](https://bitcoin.stackexchange.com/questions/91531/would-a-schnorr-pubkey-be-a-different-length-than-a-taproot-pubkey-like-p2wpkh-a) (vs P2SH 2-2 multisig outputs, which [are just 32](https://medium.com/coinmonks/on-bitcoin-transaction-sizes-part-2-9445373d17f4#7f9a)). So, taproot makes this problem worse, by a factor of 1.34. Taproot saves an enormous amount (over 100 bytes), during channel closes, however. So it is actually the more efficient choice.
* In practice, this would require the "cohort" (aka, the 23,250 new people) to coordinate with one single "rich guy" (aka, the user who already owns a lot of BTC on layer1, in one of his UTXOs). This "rich guy" would use one txn, to onboard all 23,250 new users at once, giving each a channel with its own magnitude, opening-balance (if any), and pubkey.
3. Users never need a second channel.
* The user's new channel, is enough to last them the rest of their lives. It never has any problems with [liquidity](https://medium.com/@peter_r/the-answer-to-yesterdays-lightning-network-quiz-was-a-1-coin-d8125c056758) /balancing /routing /uptime /hotwallet-crashing /[attacks](https://bitcoinops.org/en/topics/channel-jamming-attacks/) /etc. There are no problems with ln-fees /extortion /pay-capacity, despite each user being beholden to one channel-counterparty for all of their routes. 
* Users do not desire >1 channel for other reasons: an alt identity, or on behalf of an organization (corporation, church, etc).
4. The world population remains flat at 8 billion people.

Now we can do arithmetic:

    999,750 / 43 = 23,250 users onboarded, per block [see above]
    6*24*365 = 52,560 blocks per year [6 blocks/hour]
    -------------
    1,222,020,000 onboards per year

    8 billion people per Earth, 
    divided by 1,222,020,000 onboards/year

    = 6.54 years, to onboard one Earth

But that is only if the assumptions above are accurate.

Which, of course, they are not! In fact, they are quite absurd.


### B. Realistic Assumptions

Let's get some more realistic assumptions:
* The effective onboard rate will NOT be 43 vbytes per onboard (via a laughably implausible single 1-input-23250-output txn). Instead, there will be roughly one input per output (for the "rich guy" story to play out, we must also include a second "change output"). So the effective rate would be closer to 143.5 vbytes ([41 + 66/4] + [43] + [43], see [P2TR here](https://medium.com/coinmonks/on-bitcoin-transaction-sizes-part-2-9445373d17f4#7f9a)) per onboard. (Even this assumes that we never need more than 1 input, which is highly optimistic.)
* Similarly, each user will need at least 5 channels, in practice. And these will not be permanent -- they will last (on average) perhaps 1 year[^2]:.
* Moreover, when channels close and reopen (sometimes un-cooperatively[^3]), they will consume blockspace, leaving less for LN-onboarding. So, 99.97% onboarding block portion is not realistically achievable, let's go with 90%. (Still very optimistic.)

[^2]: Each channel-rollover, is theoretically the equivalent of one new onboard. Basically, a user must "re-onboard" themselves. To do so, they need 1 input + 1 witness + 2 outputs. 

[^3]: See Part 3, "The LN Byte-Gambit".

So, if we redo the analysis with non-absurd numbers, we get:

    900,032 / 143.5 = 6,272 channels opened, per block [see above]
    6,272 / 5 channels per user = 1255 users onboarded per block
    6*24*365 = 52,560 blocks per year [6 blocks/hour]
    -----------
    65,962,800 users onboarded per year
    
    8 billion people per Earth, 
    divided by 65,962,800 onboards/year
    
    = 121.28 years

In other words, each year we'd only onboard 0.82% of the world[^4].

[^4]: Interestingly, this "121 year" figure is consistent, indirectly, with the "133 MB" figure, in [the original LN whitepaper](https://lightning.network/lightning-network-paper.pdf) (page 55): "to enable 7 billion people to make two channels per year with unlimited transactions inside the channel, it would require 133 MB blocks (presuming 500 bytes per transaction and 52560 blocks per year)." Both calculations reach the conclusion that the LN onboarding rate is currently too slow, by a factor of \~100x.

Worse: if channels last merely one year, then by Jan 1 2025, we will need to re-onboard the people who joined on Jan 1 2024. In *that* world, *only* 0.82% of Earth's population, max, can be *bona fide* Bitcoin users (at any one time).

Monetary network effects are very strong -- you need to use the money that other people are using. So a 0.82% ceiling is not viable.

### C. Custodial "Lightning" (aka, Dodging the Question)

Some might respond as follows: "only elites will use the BTC network; the hoi polloi will use custodial services". Perhaps so, but that has nothing to do with the LN. That is just an argument that BTC itself (onchain+LN) is unscalable (past the 0.82% ceiling)[^5].

[^5]: Interestingly, Tadge Dryja [inventor of the LN] says this (more or less), April 2019: (26:22) "...it's tricky though, I've talked to Peter Wuille, and he's like 'Yeah, I don't think everyone can use Bitcoin ... we don't know how to make that happen' ...I think most people agree: we want more people to use it [but we don't know how]."

A "custodial" wallet can never be an LN wallet. Custodial wallets aren't "Bitcoin wallets", of any type -- they are bank accounts.

Gold went down the Custodial Path. And gold-money was replaced by banknote-money.

Would BTC go down the same path? Let us compare the 0.82% BTC figure, to the gold-banknote equivalent: how many people were paying in physical gold, in 1971? Basically no one. So: that's good for BTC.

But I think the true threat lies ahead, not behind. Monetary history will likely progress as follows: [Reputation/Memory] --> [Beads/Shells] --> [Gold] --> [Banknotes] --> [BTC] --> [Something New]. We won't go back to banknotes, for the same reason that we won't go from banknotes to gold, nor from gold to Shells. Progress is a one-way street. In other words: the story of "how Gold lost to banknotes", is not a story of 'good vs. evil', nor is it a story about the inherent power of banks. Instead, the story is this: a new product or service came out, and it was *better for the user*; the old product became obsolete.

"Can't BTC just make use of that New Thing, when we see it?" Unfortunately, I don't think so. BTC culture is so LN-obsessed, that I fear that today's Bitcoiners will likely treat all new non-LN scaling ideas with hatred and revulsion (especially any which are objectively superior to LN).

Can't "channel factories" help with onboarding?


## 2. Onboarding via Channel-Factories (or CoinPool)

    One bad apple spoils the bunch.
    -English Idiom

### A. What are Channel Factories?

**Factories** are a technique which allow *more than one* person to onboard, using the same 43-vbyte output.

Taproot multisig outputs (MTOs) are 43-vbytes, regardless of the n-of-n configuration. It doesn't matter if the MTO is 2-of-2, 33-of-88, or 100-of-100. MTOs always require just 43 onchain-vbytes. 

Thus, our "wealthy Bitcoiner" (from the above examples) can onboard 99 newbies, instead of just one. He would use a 100-of-100 MTO (instead of 2-of-2), and call this MTO a "factory". It has exactly the same on-blockchain size as a "channel" (aka, a 2-of-2 MTO).

Of course: the *transaction* spending a factory, is much larger than one which spends a channel. But: the factory MTO *might never need to be spent*. After all, it provides its group, with unlimited channel-opens within the factory. If a [few "super-spreaders"](https://www.youtube.com/watch?v=sF1wy6OkeLE) join many factories (and factory with each other), then everyone can *always* construct a route to everyone else (all 100% off-chain).

So far, so good.

### B. Fragile Factories

Now for the first problem.

If **any** person, in the factory-group, stops cooperating, then *the entire factory* must close on-chain, and reopen on-chain. The original 43-vbytes were wasted (and new vbytes are needed). 

![images](/images/cdecker-factories.png)

![images](/images/fragile-factories.png)

Above: [Conversation](https://twitter.com/Snyke/status/1500507299928027136) between Christian Decker (inventor of channel factories, and Researcher at Blockstream), and myself. Also: excerpt from [the Factories paper](https://tik-old.ee.ethz.ch/file//a20a865ce40d40c8f942cf206a7cba96/Scalable_Funding_Of_Blockchain_Micropayment_Networks%20(1).pdf).

In channels, you only have one counterparty who might become unresponsive -- in factories, you have many.

### C. Factory Sabotage

This is particularly bad for *onboarding* via factory, since the Ideal Onboard is going to look something like this:

    Rich Guy Input 80 Coins --->  [43 byte Taproot Output]: Rich Guy   -- Factory Slot #1  -- 80 Coins
                                                            Newbie #1  -- Factory Slot #2  --  0 Coins
                                                            Newbie #2  -- Factory Slot #3  --  0 Coins
                                                            ...        -- ...              --  ...
                                                            Newbie #99 -- Factory Slot #99 --  0 Coins

Each "Newbie" has two big reasons for becoming unresponsive (and, as a result, sabotaging the factory): 

1. Newbies start with zero coins (ie, almost nothing to lose).
2. Newbies are "new", and unfamiliar with the technology.

On top of that, what if they aren't a "Newbie" at all... but a "Saboteur"! Saboteurs can join every channel, **for free**, and sabotage them all *by doing nothing*. (The "attack", is just the attacker closing down his software application.)

What if, instead, each factory-member is required to bring in money, when the factory is opened? It makes no difference: the attacker can always (by definition) spend 100% of this money out. (Via the lightning network itself.) Then they attack, *after* doing so, since they now have nothing to lose.

Fundamentally: *anyone* whose channel balance falls toward zero (at any time), is a potential liability.

### D. Efficient Sabotage via "Recycling" Funds

Attackers can maximize efficiency, by "recycling" their money, as in the following example:

1. Borrow $20M from Roger Ver.
2. (If 1000 factories are opened per block, then 1M are opened per week.)
3. Join *all 1,000,000* Week 1 factories, with $20 per factory, starting with the Sunday factories.
4. On Tuesday, "spend" the BTC out of the Week1_Sunday factories. Use that money to obtain "new" BTC (or USD, or however the factory-"rich man" is charging you).
5. On Wednesday, "spend" the BTC out of the Week1_Monday factories ... [repeat]
6. By the time Saturday rolls around, you have enough money to repeat the process. You can join all 1 M of the Week2_Sunday factories.
7. Repeat this for a year. Then stop (see next section).
8. Give Roger Ver back his $20M.
9. (You have now disabled 100% of the factories opened this year.)


### E. "Traffic" Chain-Reaction

When you sabotage a factory, you don't just "ruin" the 43 onboarding vbytes.

In order to "repair" the sabotage, those users have to --first-- bring the factory back on-chain, and then --second-- build a new factory.

How many bytes will this take? It depends[^6], (on the n-size of the group, and on the configuration of channels). However, 430 vbytes is a conservative estimate. Later in this essay, I estimate the comparable number (the non-cooperate rollover byte-cost) for a *single* 2-of-2 channel, as: 338.5 vbytes. And one single 2-of-2 channel, is much smaller than a 20-of-20 channel factory.

[^6]: I actually think, that no one has done the math. I asked several LN-devs, but no one seems to have given it any thought.

Thus, while each factory cost only 43-vbytes to **open**, the process of **fixing** each sabotaged factory will cost[^7] at least 430-vbytes.

[^7]: More bad news: whoever *does the closing*, pays the miners. The attacker does not pay the miners, since they won't close the factory (they will simply abandon it in an unalterable state).

So, after borrowing $20 M from Roger Ver to disable 100% of the 52.5 M factories opened this year, you can sit back and relax: your victims, trying to regain access to their money, will broadcast large "factory-repair" txns to the mainchain, doing *ten times* as much byte-damage as you yourself did. You just need to smash up Year 1 -- Years 2 through 11 will take care of themselves.


### F. A Fundamental Problem

Maybe, instead of factories, we will invent something new, that solves this problem.

However -- *someone* must pay for layer1 blockchain bytes. This is a fundamental limitation.

So, pick your poison: either factory-eviction is *possible* or *impossible*.

If it is *impossible*, then you are in the scenario I outlined above.

If *possible*, then the attacker will just start evicting innocent victims... *thus forcing them to pay for blockspace, against their will*!

What of a third, crossover possibility? Where *you* pay, to evict someone else out of a factory. Minimally, this will cost [1 input + 1 witness\] (which is how you pay these txn fees), plus at least one output (to pay the evicted person), plus (probably) a second output (to give you your "change"). This amounts to 143.5 bytes (that you have to pay for), which would have been enough space for 3.33 new factories.

Ultimately, the attacker can always make it your problem. Then, they can refuse to cooperate. This forces you to pay to bring more bytes on-chain.

(Since miners earn 100% of this extra money, they arguably have a strong incentive to perform all of these attacks.)

### G. CoinPool

CoinPool is a factory which makes it slightly more convenient for one single person to leave.

But it does nothing to solve that fundamental problem of factories (unresponsive group-members). In fact, it makes that particular problem *worse* (as far as I can tell):

![image](/images/somsen-coinpool.png)

Above: Ruben Somsen (inventor of Statechains, Softchains, and Spacechains) [on CoinPool](https://twitter.com/SomsenRuben/status/1495829490802515968).

So, I consider the factories idea to be a dead-end for now.

Back to channels (the regular 2-of-2 variety in use today).


## 3. The LN Byte-Gambit

### A. Channels

#### i. How Channels are Like Russian Roulette

In Russian Roulette, the odds are (1/6) of death, and (5/6) of winning.

Channels have a similar concept, only with bytes instead of death. Usually, everything will go fine. In which case you save bytes. But occasionally, things will go wrong. You will have to do the "uncooperative close", and bring bytes on chain.

Let's calculate the bytes that we risk, in the channel case.

#### ii. What must a non-cooperative close, always require?

Well, each non-cooperative close requires, at least: 1 LN input script + 2of2 multisig witness + 2 outputs + residual txn overhead [version, qin, input selection, qout, nLocktime]. As best I can tell, this amounts to: 32 vbytes [at least] + [64 bytes [assuming 1 Schnorr sig]]/4 + 2\*43 + [4+1+(4+32)+1+4] = 180 vbytes. (We can check this against [Bolt Appendix A](https://github.com/lightning/bolts/blob/master/03-transactions.md#appendix-a-expected-weights=), which gives a minimal txn as ( 500 + [172\*0] + 224 )/4 = 181 vbytes.)

Thus, we see that every non-cooperative close txn, takes up 180 vbytes.

#### iii. Non-cooperative Closes Cannot Be Dual-Used as Rollovers

The bad news is that non-cooperative closes can *not* (as far as I can tell) be re-used as channel rollovers. For that to be so, Alice's txn (which was signed by the now-uncooperative Bob) must **already** contain an output that pays into a new 2of2 multisig with Barney (aka Bob II).

But, couldn't it contain such an ouput? Why not? Why do I say it is impossible?

Well, it depends on whether or not Alice was *surprised* by Bob's non-cooperation. If Alice was **not** surprised, then she got Bob to sign off, on Alice-paying-into-a-new-2of2-multisig-between-her-and-Barney, which Alice broadcasts. For all intents and purposes, it is a cooperative close.

On the other hand, if Alice **was** surprised, then the paradox moves from Alice to Barney. Barney cannot use this hypothetical Alice-Barney channel, until that txn is broadcast and confirmed on chain. (In other words, Barney cannot use the Alice-Barney channel while Alice is still "in a relationship" with Bob.) Barney cannot be waiting around, to see if Bob will later "surprise" everyone by becoming uncooperative. He intended to open a channel, and he intended to use it. So, this case also doesn't make sense.

Neither of the two cases made sense. Therefore, whenever you are non-cooperative, you must take two actions: go on chain to sort out the mess; and then pick a new channel-counterparty and open a new channel with them.

#### iv. Full Cost of "Losing" the Channel Bet

Thus, the full cost of a non-cooperative close, is the 180 vbytes of the close-txn, *plus* the additional bytes needed to reopen a channel. (In this case, there is no need for a change output, since Alice will re-spend 100% of her money; but we still need to select Bob's input, so the onboard txn will cost (2\*(41 + 66/4)) + 43 = 158 vbytes. Thus: 338.5 vbytes total. This is what Alice must spend, to "get back" to where she would have been[^8], if the original Alice-Bob channel had met all her economic needs (and never had to be closed).

[^8]: In fact, of course, it is worse. Alice must also *wait*. Since she triggers the non-cooperative close, it is *Bob* who gets his money immediately. Alice must wait two weeks [or whatever].

#### v. Aside: Joining, Then Quitting the LN

A "non-cooperative rollover", is a [channel_close + channel_open].

That quantity, happens to exactly equal the quantity [channel_open + channel_close]. The latter quantity is the cost of joining the LN and then later quitting LN to go back to on-chain payments. Both of those actions, cost 338.5 vbytes.

#### vi. The Channel-Ratio

A [minimal layer1 txn](https://www.truthcoin.info/blog/thunder/#b-smaller-txns) can cost as little as 1+36+(64/4)+32+28+28 = 141 vbytes. (Here, I have edited the Thunder txn, to swap the 71-byte ECDSA signature for a new 64 byte Schnorr sig.)

We can now divide 338.5 / 141 = 2.4. What does this 2.4 magnitude mean? It makes that, when you join the LN, you are hoping you will be able to use it for at least three off-chain txns. If you only use LN for two off-chain txns, then quit, then you have actually consumed more blockspace by using LN than you would have if you had not used LN.[^9]

[^9]: This ratio gets worse for LN (but not by much), if we remove the "witness discount" (which we should, since it is irrational). The non-cooperative rollover cost, having 3 signatures, is 338.5 + 3\*(-(64/4)+64) = 482.5 bytes. The minimal onchain txn is 1+36+64+32+28+28 = 189 bytes. The ratio is now 482.5/189 = 2.55.

Equivalently, when you must do a non-cooperative close, you "lose" the gambit. And you must pay the equivalent of 2.4 ultra-minimal txns. So, if you are very unluckly, you might be using *more* layer1 bytes with the LN, than if you had stuck to vanilla onchain transactions. You must make at least 3 LN-txns for every time you need to rollover the channel.

Which seems pretty favorable to the LN, to me.

But now I will repeat this style of analysis, with HTLCs. And it will be less favorable.

### B. HTLCs

#### i. The Concept (of this section)

Imagine a world where it costs $20 to take someone to court. Even if *you knew you would win*, you would **never** sue someone for <$20. By "winning" the lawsuit, your net worth would decrease. If instead you let them get away with it, you would be wealthier.

#### ii. The Cost of Justice, in LN

Each HTLC costs 172 wbytes, or (172/4) = 43 vbytes.

How much does that cost, in txn fees?

Let's assume that txn fees are $5/txn, and txns are ultra-compact size of 141 vbytes. Then, *merely the HTLC part* (of the LN-channel-txn) will cost *the broadcaster* (43/141)\*$5 = $1.52. That is the cost of the "ink", needed to write the HTLC part-of-the-txn into the blockchain.

Worse -- you aren't truly "done", until you spend that HTLC money. In its current, unspent form, it is an "accounts payable" to the miners -- a liability against your net worth. When you spend the HTLC, you will need to select it as an input, *and* provide the hash, *and* provide your signature. This will cost [32+4] + [32] + (64/4) = 84 vbytes. So the total cost is 43+84 = 127 vbytes. The total USD cost, of enforcing the HTLC, (in a world of $5 fees), is (127/141)\*$5 = $ 4.50.

#### iii. The HTLC-Ratio

$4.50 is of course, very close to the $5.00 I assumed a minimal txn would cost. (Specifically, $4.50 is 90% of $5.)

That is because HTLC-enforcement, requires practically as much bytes as a regular txn. (A "minimal" 1-input 2-outputs on-blockchain txn.)

Since txn fee-rates fluctuate, we can now derive a general rule of thumb: HTLCs should not be used, for any payment of $X or less, where $X is the current fee/txn rate.

For example, if onchain fees are currently "$5 per txn", then LN HTLCs should not be used for "offchain" payments of $5 or less.

( That is just the HTLC output. The whole rollover will cost (as we've just discussed) 338.5 vbytes, which will take up $12.00 worth of ink. (And indeed, $12/$5 = 2.4, the ratio we discussed earlier.) )

![image](/images/rusty-ln-enforcement.png)

Above: Rusty Russell, Blockstream dev and Creator of c-lightning, [here](https://twitter.com/rusty_twit/status/1133566028162785282).

( Matt Corallo has published a far more horrifying version of this issue ["we're talking about extra outputs out the wazoo for hopefully-unnecessary edge cases involving transactions entering the mempool which a user wants to avoid confirming! This severely cuts into the lowest-value HTLCs which can be sent 'safely' "](https://lists.linuxfoundation.org/pipermail/lightning-dev/2020-April/002639.html), summarized [here](https://bitcoinops.org/en/newsletters/2020/04/29/), which AFAIK has not be resolved. )

#### iv. Aside: How important Are HTLCs?

In the above argument, the LN *itself* can still be used, just not the HTLCs. Let me repeat: the sub-$X HTLCs are not trustless, as their enforcement would be detrimental to both victim and perpetrator [only the Miners would benefit].

Lack of HTLCs, is particularly vexing for the "intermediate" LN-routing-nodes -- the "Bob" and "Carol" who sit between Alice and Dave. When Alice pays Dave $5; then the idea of LN is that Bob pays Carol $5. Ordinarily, all payments are conditional on the same HTLC, but without HTLCs, Bob is just going to have to pay Carol $5 for no real reason (or else, Alice is going to have to pay Bob for no real reason).

Can the LN be used without intermediary routing-nodes? Yes, but without these routing nodes, you can *only* transact with people that have opened channels with you. This largely defeats the point of the LN.

( This (and other things) are discussed in [this Jan 2019 talk on HTLCs](https://www.conferencecast.tv/talk-24515-htlcs-considered-harmful-sbc-19#.talkPage-header=), at 18:45.)

#### v. Catch-22s

From our work on HTLCs, we now see two "dammed if you do, damned if you don't" paradoxes:

* If L1 feerates are high (as in the silly Vortex-Rusty twitter exchange), then HTLCs won't work, making LN useless for payments. On the other hand, if L1 feerates are low, then then LN itself is somewhat superfluous. 
* LN is also bad for low-value payments, as these cannot use HTLCs. But, on the other hand, LN is bad for high-value payments, since channel-capacity is [a minimization function](https://medium.com/@peter_r/the-answer-to-yesterdays-lightning-network-quiz-was-a-1-coin-d8125c056758).


## 4. The Unfortunate State of LN Dialog

Taken together, the previous three sections paint a somewhat bleak picture of LN: 

1. LN's design requires that channels be opened on L1, which guarantees that almost no one will be able to use it.
2. The much-hyped "new LN tech" (factories etc) doesn't hold up against basic adversarial analysis.
3. HTLCs are what transform bidirectional channels into a global network. But their tolerance to fees, is paradoxically, more-or-less the same as that of regular on-chain txns. This creates a paradox of fee-expectations.

Yet LN is super super hyped. How do I explain this vast discrepancy?

### A. This Post is in Error

I wrote this entire post with basic byte-arithmetic. I didn't really share it with anyone before posting it, so maybe it is all wrong.

I am not that interested in LN. I usually don't talk to Lightning experts.

(On the other hand, I did [*write LN into my own P2P oracle project*](https://bitcoinhivemind.com/blog/lightning-network/), back in March 2016. So in that sense I am a Lightning mega-OG.)

### B. Polarization Has Purged Bitcoin of Scientific Discourse

Tadge Dryja (creator of the Lightning Network), [said in 2019](https://www.youtube.com/watch?v=LnG5H62I7Ko) (27:50), 

    So, yeah: increase the blocksize ...
    (or some kind of extension block, who knows),
    these [scaling solutions] *all* have to happen in concert...
    and I think that most of the Core Developers have said that
    ...It's weird...it [scaling] became this polarized thing. 

At (43:20), Peter responds "This isn't the call I expected...I expected a very pro-lightning [talk]". Tadge then says, again:

    I've seen, like, a tribal ... everyone's like:
    "LN is the gonna be the best thing ever".
    Wait, uh, [LN] can't actually do that.
    ...
    [LN] is a part of a scaling solution,
    but I think there's other stuff.

I think Tadge is spot-on. It is polarization and tribalism.

Largeblockers preferred largeblocks, so they criticized LN even though they didn't really know anything about it. In contrast, the smallblockers *promoted* LN, even though they also didn't know anything about it. (I personally recall many examples of this -- many "LN supporters" who didn't know: that you needed to be online to receive money; that your LN node needed to connect to a Bitcoin Core full node in order to do anything; that the 12 word LN seed did not restore your money in the event of a crash; 

![images](/images/blocksize-war-polarization-meme.png)

Tadge can openly criticize LN, because he is the *creator* (with Joseph Poon) of LN. Tadge's LN-affirming status is not in question. That's why you only hear it from him and no one else. (See also [this video](https://twitter.com/BCoreCommunity/status/1111800709861834754).)

If I am write about this reason, then I present to you this image, of LN critiques *by people who work on LN*:

![image](/images/real-ln-tweets.png)

### C. Unreliable LN Critiques

If there is polarization, then the *LN-supporters* will be irrational. But the *critics* will also be irrational.

While researching this post, I found [this repository of LN Critiques](https://github.com/davidshares/lightning-network). Some of them are good. But some are bad. And many of them are not relevant (or else, they will only be relevant for a short amount of time, or else, they can be eventually fixed with more engineering).

I can see why a LN-user would just ignore the whole repo, and write it off as mindless LN-hate.

(That is why I, with this post, tried to focus on three specific issues.)

### D. "Dumb Money" VCs (?)

The smartest investment to make --as we all know-- is to *buy Bitcoin*.

For some reason, though, VC don't take this advice. Instead, they give money to people. (Why do they do this? I have no idea.)

Anyway: after years of watching Dan Larimer and Vitalik earn millions of dollars, don't you *deserve* yours?

All you need to do, is find something that the VCs like. Preferably something that you can do, and that is too esoteric for them to really figure out. Then specialize in that thing, and collect your $$. Finally --this is essential-- be sure to vociferously *discredit* anyone who refuses to toe your line. That way you can keep the grift going. That's how you stack BTC and become a "real Bitcoiner".

Sort of a cynical, unfriendly way of looking at the world, I admit. But hey -- if VCs are going to give all of this money away, I can see why many people would take it. (After all, you never know what new ideas you'll discover along the way.)

( In case it isn't clear, I blame the VCs, for this. Sadly, "Investment" doesn't always make the world a better place. It does, if the investment is good. But if the investment is bad, or fails, then you instead made the world a *worse* place.[^10] Investors should accept a moral responsibility for each of their investments. )

[^10]: For example, consider the Theranos investors. They lost their money. But they also [1] misled (and endangered) many customers; [2] wasted the time, attention, and reputations of Theranos staff (and of Theranos suppliers and contractors); [3\] (probably) misled and discouraged many rival inventors/entrepreneurs (who may have concluded that they were doing something wrong, and/or were too far behind, on their own blood-testing ideas); [4] more generally, disrupted the progress of science, by altering which topics were given attention and why; [5] consumed the scarce time and attention of regulators and law enforcement.

### E. The Specialization Grift (?)

Engineers have a bias, toward anything where engineers are likely to be hired to work on it.

![dilbert](https://assets.amuniversal.com/268f57809f72012f2fe600163e41dd5b)


    [Once] division of labor has set in ... I wish the price of
    everything I buy to be low ...but it is in my interest for
    the price of [everything] I provide to be high.
    ...
    Just as there is no technical improvement that would not
    hurt someone, so there is no change in public taste or
    morals, even for the better, that would not hurt someone.
    An increase in sobriety would put thousands of bartenders
    out of business. ... A growth of male chastity would ruin
    the oldest profession in the world. ...Preachers would
    have less to complain about; reformers would lose their
    causes ... If there were no criminals we would need fewer
    lawyers, judges...firemen...jailers... locksmiths.

Above: The Last Chapter of H. Hazlitt's ["Economics in One Lesson"](https://www.hacer.org/pdf/Hazlitt00.pdf). Comparisons to "devs", "VCs" or toxic Twitter personalities, are in your imagination only.


## 5. Finally: LN & The LargeBlock Sidechain

These LN limitations are fundamental. They are inherent to the design of LN (and its reliance on layer1 bytes for onboarding and enforcement).

But the limitations are mostly irrelevant, if LN is a "layer3" on top of a low-fee LargeBlock sidechain layer2. In that scenario, LN-onboarding is cheap and easy; factories (& similar complex tech) are no longer needed; and fee-rates are low, allowing HTLCs to be easily enforced.

In that scenario, LN would mainly be valuable for the two things that *only* it can do: instant payment settlment, and [Fraud Proofs](https://www.truthcoin.info/blog/fraud-proofs/).

**Update (Aug 2022)**: A new [LN video](https://www.youtube.com/watch?v=BjFjK-f9ts0) has come out, seemingly confirming that the LN situation is much more dire than is widely believed. So, if you don't take it from me, then take it from them!


---

### Footnotes