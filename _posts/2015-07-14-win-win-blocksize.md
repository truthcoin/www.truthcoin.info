---
title: The Win-Win Blocksize Solution
comments: true
---


> Leave this lunatic "debate" behind. With a simple (temporary, and optional) sidechain, one can buy a "refund" on unwanted Bitcoin-blocksizes. The prices of these refunds give us unanimously-agreed info which is clear, accurate,  and unbiased (unlike the info we currently get).

## The "Decentralized Governance" Problem

### Why The Blocksize Conversation Matters

Disaster has struck the Bitcoin community. For the first time, **something un-ignoreable** has been proposed: a protocol change  (“hard fork”). 

Ordinarily, the protocol's network-effects would protect the community from "anyone capable of causing serious damage to Bitcoin". However, today they make the blocksize conversation mandatory and dangerous. All users, regardless of intelligence or expertise or other virtue, will be forced to adopt whichever network they think everyone else is adopting.

This compulsion means that, for the first time, the opinion of the ignorant masses (if misled, or merely divided) **can actually destroy Bitcoin**.

### The Problem Isn't Tech...It's Info

With the stakes this high, and with “the opinions of uninformed community members” now a kind of “asset” (manipulable “votes” in a pseudo-democracy), nothing could be more important than a rational and productive discussion of the relevant facts.

![BlocksizeMarket](/images/blocksize-subreddit.png) 

And this is merely the first "contentious hard fork", of who knows how many.

## The Prediction Market Solution
> Buy only the Bitcoin-type you want. Bet-on / profit-from the foolishness of others. View all of the relevant blocksize-info in one easy-to-understand location.

### A Good Fit

[Prediction Markets](https://en.wikipedia.org/wiki/Prediction_market) (PMs) excel at aggregating, filtering, and broadcasting information.

They work best when we have:
 1. Many, heterogeneous information-sources (ie, the problem has many facets and perspectives, each of unknown relevance and reliability, which must all be considered simultaneously).
 2. A clear and measurable goal-metric (ie, USD/BTC exchange rate in the future) and decision-metric (Blocksize increase).
 3. (Optional) funding to subsidize the market (to help ‘pay’ for the information).


PMs can easily outshine the talk-alternative (ie, the Bitcoin subreddit, more below), and the wait-and-see alternative (which, in this case, is a rather disconcerting one...as the damage done to Bitcoin’s reputation by a contentious hard fork is potentially catastrophic).

![BlocksizeMarket](/images/blocksize-DM.png) 

Consider the 2x2 prediction market (above).

1. It is inherently viable (can passively entice trading) in two ways:
	* It produces a “BitUSD” with the purchase of states {1, 2}.
	* It creates arbitrage opportunities between the real-world exchange rate the PM’s horizontal dimension (State 1 vs. 3, and 2 vs. 4).
2. It allows individuals to **insure against the transition to a new blocksize** (or against the failure to transition). Purchases of {1, 3} grant the owner cash (in BTC) if Bitcoin does not increase its blocksize, and purchases of {2, 4} grant the owner cash if Bitcoin does increase its blocksize. 
3. Best of all, it allows users to do something truly extraordinary: make purchases either of one type of Bitcoin or the other; **if Bitcoin evolves in a direction in which traders do not approve, these traders get all of their original investment back**.


### Opt-Out of the "Conversation"

(For greater technical detail, check out the Blocksize Tab of [my MSR Excel sheet](http://www.truthcoin.info/papers/LogMSR_Demo.xlsx) or a browser-friendly [google docs spreadsheet](https://docs.google.com/spreadsheets/d/10XWBs3ZbpRV6-1-Mo2IMKNbBV2uNA5QVVM-uB7XQzk0/edit?usp=sharing) I threw together for this post.)

A “pro-increase portfolio” (PIP), has states {1, 3, 4\*} purchased in specific quantities: 1 of {1}, 1 of {3}, and enough of {4} to achieve a total investment outlay of 1 unit (1 BTC, 1 mBTC, etc).

* If the blocksize fails to increase...share {4} will be worthless, but {1} and {3} must together be worth 1 unit, producing the full refund.
* If the blocksize does increase...{1} and {3} are worth zero, but the remaining shares of {4} grant traders a long position in the Bitcoin exchange rate. The quantity of {4} shares, determined earlier, will sell for an amount of revenue that, combined with the given original cost of 1 unit, always replicates the return on the Bitcoin exchange rate itself.

Buying the PIP is **like buying a “Bitcoin” that you can return if the blocksize doesn’t increase**.

Of course, there's no "free lunch" in finance: as the market "prices in" expectations about the relationship between blocksize and exchange rate (see below), the single current BTC exchange rate will actually diverge into two. The PIP will become more expensive (and offer lower returns) if the market believes that an increased blocksize would result in a relatively higher exchange rate. Conversely, if the market felt that increasing the blocksize would lead to a relatively lower exchange rate, the PIP would become cheaper (and offer higher returns). As always, markets reward those who earliest provide accurate information the most.

It should be obvious that this logic is identical for the converse “anti-increase” portfolio (consisting of states {2, 4, 3\*}), which entitles traders to “Bitcoin” unless the blocksize increases, in which case they get a refund. Other portfolios exist, for example {1, 2, 3\*}, a kind of “hard-fork fear portfolio”: one goes long Bitcoin if the network keeps the 1 MB blocksize, goes short Bitcoin if the network increases the blocksize, but, regardless of which happens, gets refunded if the price of Bitcoin collapses (a full refund, in BTC [see below], if the price collapses to $0, the minimum value in this example).

### Win-Win-Win: Prices Create Reliable Information

As trading progresses, onlookers would, today, be able to use current market prices to see and compare two future exchange rates: the first where the future blockchain uses a 1 MB blocksize, and the second where the future blockchain uses a >1 MB blocksize. From there, **the community would know the implications of the blocksize-decision** (ie “if we increase the blocksize, Bitcoin will fall to $150”). Those who “disagree” are either lying, choosing not to maximize their expected value, or experiencing some kind of psychological episode of self-ignorance (or "bias"). All three types can (and should) be safely ignored.

### Changing the Units

Astute readers will notice that, when the user gets their "refund", it will be 1 sidechained-Bitcoin (to match the single sidechained-Bitcoin which they invested). This is rather annoying, as, by the time this refund actually settles, "a Bitcoin" could be something we don't like: a BigBlock-Bitcoin, a SmallBlock-Bitcoin, or some worthless shadow of Bitcoin's former glory. The general problem is: in the time between our purchase-of and sale-of the portfolio (both times for 1 BTC), the *value of that 1 BTC* might have *fallen*. To escape all of these problems, it would be nice if we were betting in something non-BTC, like US Dollars (or Gold, DJIA, etc).

To do that Peer-to-Peer might seem, at first glance, to be impossible. Even Blockstream, arduously crafting their 2-way peg, can only roll out competing blockchains refundable in BTC, not in USD. What kind of technical magic could enable something so beautiful?

Well, I think it's easier than it looks:

![BlocksizeMarketBitUSD](/images/blocksize-DM-usd.png) 

As long as the price of BTC doesn't fall exactly to zero (making both the BTC and sidechained-BTC completely valueless [and, in fact, the "exchange rate" values should probably be "log(exchange rate)" for this and other reasons]), purchases of States 1-4 would gain value as the future USD/BTC price falls, and lose value as the future USD/BTC price rises.

The precise math gets a little more complicated, but it still checks out: one can spend X dollars on something, and if the blocksize doesn't do what you want it to do, get at least X dollars back. If the blocksize does do what you want it to do, you get more cash if your goal metric (whatever it is) increases, and less cash if it decreases.

If it still feels impossible, here are some sneaky finance tricks that those of you in the computer science department might not know about.

#### With leverage, Correlation can become Replication.

If initial prices for something are .25, and final prices cannot go above 1.0, then it might seem that the highest possible return would be multiplying one's investment by 4, or +300%. But if the exchange rate falls from $300 to $30, it will have decreased by a factor of 10. How can we ever hope to win enough Bitcoin back (x4) to make up for our losses (x 1/10)?

On the other hand, as the markets min and max get higher, and closer, we have the reverse problem. If the min is 1,000 and the max is 1,005, the PM prices might shift from 0.2 to 1.0, which would multiply an investment by 5 (+400%), despite the fact that this (probably) corresponds to a shift from 1,001 to 1,005 (a return of ~000.399%).

There's a theoretical solution to these problems: invest a *percentage* of the investment principal. Someone looking to invest $500 might only actually spend 70$ on the portfolio, and keep the remaining $430 in cash, de-levering the portfolio and reducing the magnitude of the gain/loss returns. Correspondingly, one can start with $500, and use debt to invest more than 100%, increasing the magnitude of the returns.

Of course, all of this stops working immediately if the real-life value crashes into either the min or max bound. At this point we no longer have something perfectly correlated with the underlying asset (in fact it is now completely uncorrelated).

#### Arbitrage Guarantees that PV(Forward) = Spot 

Although the upper dimension refers only to the exchange rate on a single future date, the price of that dimension (the price of sum(1,2,3,4) versus sum(States 5,6,7,8)) will always track the current USD/BTC exchange rate on *all* dates, at all times.

To see why, imagine any case where the PM price differed from "the current Bitcoin price + some interest". For example, say the PM price is $400, but the current real-world exchange rate is $300. In this case, anyone can conduct profitable arbitrage by shorting in the PM (purchasing sum(1,2,3,4), which gets the inverse of a BTC-return, expecting +$400) and buying a real-world BTC (which gets the [non-inverse] BTC-return, expecting -$300); when the values equalize in the future the arbitrageur will enjoy risk-free profits (of FV($100)). Traders constantly seek out and exploit these risk-free profits, ensuring that the upper-dimension tracks the USD/BTC exchange rate at all times.


### Possibilities

We can have as many Markets as we like, on as many topics as the "oracles" (below) will tolerate.

For example, one might produce one with 8 states: 4 blocksize-possibilities against 2 exchange rate extremes (instead of [ [Top: “Base”, Bottom: “ > 1MB”], [Left: “$0”, Right: “$50000”] ] we could extend this to [ [Top: “Base”, Upper: “2 MB”, Lower: “8 MB”, Bottom: “20 MB”], [Left: “$0”, Right: “$50000”] ]).  This would allow us to infer the “optimal” block size for this metric. Some protest the timing of the (to them, ultimately necessary) blocksize increase; to address the optimal timing which we could instead label the rows "Increase to 8 MB blocksize after date 1, Increase to 8 MB blocksize after date 2 etc".

It would also be useful to use different goal metrics to address other concerns:  “VC investment in Bitcoin infrastructure”, “number of full nodes (6 month average)”, “average blockchain propagation time (6 month average)”, “likelihood of another hard fork after this one”, etc. In all cases, individuals can predict the effect of the blocksize on each metric, and be rewarded if correct, and punished if incorrect. **These incentive-compatible predictions about the future, produce market prices (reliable data) for us to examine today.**

![BlocksizeGeneral](/images/blocksize-general.png) 


## Practical Decentralized Governance
> If Bitcoin governance is centralized, that governance can be attacked as a central point of failure (and may be Bitcoin's new weakest point). Yet informal internet conversations are unstable and ineffective. Markets are -by far- the most efficient and scalable governance structure, and they are also (now) capable of being decentralized.

### This Idea's Requirements

My own project for entirely P2P prediction markets is nearly finished, but it still requires quite a bit of formal review and testing. Meanwhile we can strip it down to the bare, well-behaved, tried-and-true essentials and ask the federated "functionaries" to do just a little more work.

#### Ingredients

* Semi-trust in [the sidechains technology, including federated peg (page 17)](https://blockstream.com/sidechains.pdf).
* Semi-trust in some individuals or group ("oracle(s)") to accurately report (after the fact) a few simple data points:
	* True/False on a number of blockchain choices (1 MB, 6 MB, 20 MB).
	* Numerically on any relevant goal metrics in which we are interested (the exchange rate in the future, the number of full nodes, cost to run a full node, etc).
	* True/False on any supporting choices we might be interested in ([Meni's Pigouvian tax](https://bitcointalk.org/index.php?topic=1078521.0), [Lighting Network deployment](http://lists.linuxfoundation.org/pipermail/bitcoin-dev/2015-June/009229.html), etc).
* To "trust" that the software has been assembled correctly.
* (Optional but helpful) some money to place at the center of the MSR to permanently imbue it with liquidity.

#### Recipe

1. Technical agreement on feasibility (see above) and desirability (see below).
2. Strip down the existing work [here](https://github.com/truthcoin/truthcoin-cpp) (and [here](https://github.com/psztorc/truthcoin) and the documentation [here](http://www.truthcoin.info/papers/)) to a bare-bones "element" consisting of just a few predefined markets (and purposefully lacking any abilities other than: [1] deposit BTC, [2] withdraw BTC, [3-6] buy/sell/redeem/donate-liquidity in these 4 predefined Markets, [7] oracle-functionaries fix final prices). 
3. Selection of the oracle-functionaries (possibly: individuals who own or manage long-term, reputable Bitcoin-businesses or organizations, or individuals who are Bitcoin wealthy).
4. Test, and turn on the sidechain.
5. Traders trade, we learn what to do.
6. Much later, oracle-functionaries fix final prices by submitting their  signed answers.
7. Traders redeem at final prices. Everyone gets what they bought.


In the process, we'd all learn a lot about decentralized markets, sidechains, and staging updates to Bitcoin. The experiment could easily be repeated for every new governance question.


### Our Current Alternatives Suck

I refer to our *conversation / information* alternatives: [/r/bitcoin](http://www.reddit.com/r/bitcoin) and the (more technical) mailing lists and chatrooms.


#### The Basics

Let's breeze through the currently known problems with the alternatives, mainly r/bitcoin: that those who seek expertise can’t validate (or even identify) what they read, those with expertise report frustration at having their views de-emphasized or misrepresented, bias goes undetected (or over-detected), conversations are duplicated (or misplaced), falling signal-to-noise ratios invite a septic futility into each stultified conversation. Almost no one is polite, and generally everyone behaves in a way that would drive off any Thinking Person.

#### The Do-er Alone Learneth

OK, let's take it to the next level. After all, this is the governance of Bitcoin we're talking about.

On the subreddit/mailing-list a few people write, and many people read.

![Socrates](/images/socrates.jpg) 

The (spoken) thoughts of [Socrates](https://en.wikipedia.org/wiki/Socrates) on the written word are worth mentioning:

"""For this invention [writing] ... You have invented **an elixir not of memory, but of reminding**; and you offer your pupils the appearance of wisdom, not true wisdom, for **they will read many things without instruction and will therefore seem to know many things, when they are for the most part ignorant** and hard to get along with, since they are not wise, but only appear wise.
...
He who thinks, then, that he has left behind him any art in writing, and he who receives it in the belief that anything in writing will be clear and certain, would be **an utterly simple person**, and in truth ignorant of the prophecy of Ammon, **if he thinks written words are of any use except to *remind* him-who-knows the matter about which they are written**."""
--(Socrates, Phaedrus 274c-275b, emphasis added)

Occasionally, reddit is used to enable a dialogue (the "AMA"). In such cases, everyone *who asked a question* would probably merit Socrates' approval. On mailing lists, the Q&A are seemingly the only relevant sections of the entire discussion (other than to state mind-numbing tautologies like "we must be careful" or "Bitcoin won't scale the way it is configured right now").

My personal opinion is that, from the entire blocksize "discussion" thus far, I have (reliably) learned almost nothing. If anything, I have only learned about who, individually, I dislike (which does not really help with the underlying blocksize question). The state of the debate seems to reflect no technical info whatsoever, instead merely the ratio of BigBlock-Users (users who pay transaction fees, but do not run nodes) to SmallBlock-Users (those who run full nodes, but do not pay transaction fees), and who was friends with who before the conversation started.


#### The Internet is Not Representative

Haven't you noticed a big difference between arguments experienced in real life, and arguments experienced on the internet? The real-life arguments ultimately produce the phenomenon of "agreement", where online people seem more contentious.

![InternetWrong](http://imgs.xkcd.com/comics/duty_calls.png)

I think that this is because of "free exit": those who learn the answer leave the conversation (and do so without altering the conversation's state: no having to admit that they were wrong, no feeling obligated to go back and convince others, etc). Say a website has 10,000,000 viewers, of which 5,000 agree with a given statement, and 5 disagree. What will the public see in the comments section? 1 principal dissenter arguing with 1 principal endorser...until? If one drops out, another takes his place. Observers will have no easy way to tell when (if) the debate has concluded, or what the conclusion was. On the internet, no one can tell how many people agree with something.

[Here is an internet discussion](http://forum.bodybuilding.com/showthread.php?t=107926751) containing a "debate" over *how many days there are in a week*. The "debate" can, if you are not careful, almost make you second-guess even one of life's most self-evident facts. Imagine the internal chaos an "internet debate" can do to you, when you don't *already know* that the issue is a settled one (at "seven").

For example, almost every technical person has given up on Proof of Stake, to the point where it is openly laughed at and ridiculed at conferences. But you wouldn't know it from The Internet, where it seems like "pro-PoS" and "anti-PoS" are each one of two equally-endorsed points of view. The technical elite are simply tired of repeating themselves.

Yet the voice of The Market speaks tirelessly. The PoS holdouts struggle to obtain 1/250th of Bitcoin's marketcap, and, even more telling for an upstart, command almost none of the space's VC funding / capital investment. They consistently lose to completely-valueless Copycoins like Litecoin and Dogecoin.

That's my message: markets > discussions.

### My Concerns With This Idea

1. That "the really important goal-metric" actually *isn't* easily-measurable (it is something vague, like 'precedent is set for future hard forks').
2. That the important goal-metric won't be measurable *until the far future* (it's something like "Bitcoin survives, without a government takeover, until 2020") which means that individuals might need to lock in their bets for a long time.
3. That legal/regulatory forces interfere with the establishment of this idea.
4. The influential heavy-hitters on both sides see this as a challenge to their personal niche as blockchain-experts, and conspire to reject the idea (or discard the idea) in order to maintain their monopoly on relevance.

## Conclusion

Blocksize PMs seem to be **doable**, they would allow Bitcoin-owners to **opt-out of the low-quality decision-process** in which they are currently trapped, and allow the community as a whole to gain access to **highly reliable information** about the consequences of a blocksize increase (info which is valuable and which we currently do not have).