---
title: Security Budget II, Low Fees, and Merged Mining
show_author: true
comments: true
date: 2021-10-15 02:00:00
---





> BTC transaction fees are low today. They will probably stay low, forever. By themselves, they will not be enough to fund hashrate security (as Satoshi intended). Fortunately, merged mining (another Satoshi invention) will ride to the rescue.


### Executive Summary

This post is a sequel to [my first Security Budget (SB)](https://www.truthcoin.info/blog/security-budget/) post.

It can be summarized as follows:

    Part 1 -- SB is a critical parameter for Bitcoin.
                  SB is driven by P. (P is "USD per txn")
    Part 2 -- Today, P is MUCH too low.
    Part 3 -- P isn't on an upward trend.
    Part 4 -- If P ever rises, entrepreneurs/inventors
                  will innovate to bring P back toward
                  zero. It is unwise to gamble on an
                  ever-high P. High-P annoys users.
    Part 5 -- High-quality Layer2s are unlikely to
                  increase P.
    Part 6 -- Merged Mining is the only known solution
                  to the SB problem. It is already in
                  use, and has been unfairly maligned.
    Part 7 -- Conclusion
    Appendix 1 -- How the Blocksize War ruined this
                      conversation.
    Appendix 2 -- How 'Blind Merged Mining' works.


The "SB-Realists" are the people who agree with me, at least on Parts 1-5.

The "SB-Optimists" are the people who disagree -- they feel that fees will go up (of their own accord), and (therefore) there is no reason to think about Merged Mining, nor any other "solution" to the problem of SB.


## Part 1. Review -- What Every Bitcoiner Should Know, About Security Budget

### A. For Sale: The Bitcoin "Off Button"

If an adversary can pay the **[security budget](https://www.truthcoin.info/blog/security-budget/)** (SB), then they are able to turn BTC off.

This is because SB is equal to (among other things) the cost of conducting an *endless series*[^1] of 51% attacks on BTC. An endless 51% campaign would defeat PoW -- honest miners could never be paid, honest users could never get transactions confirmed. The network would be useless.

![image](/images/51-campaign.png)

Therefore: the lower the SB is, the cheaper it is to destroy BTC.[^2]

[^1]: The issue is the "endless" nature of the attack -- see the "Stock vs Flow" mistake, in section 2.

[^2]: In fact, it is *worse*. The attacker needs only *the ability* to pay the SB -- they don't need to actually "go through with it [with spending the SB]". If the adversary is truly willing-and-able to pay the SB to destroy BTC, then the equilibrium mining revenues for *honest* miners will drop to zero (as, if the BTC network is destroyed, the mining industry can no longer generate *any* revenues). So, the adversary can use the threat of 51%-campaign to *deter* BTC from coming back, *without* having to actually spend the SB (during the entirety of this "suppression period"). Nonetheless, since the adversary must be ready-and-able to pay the SB on a moment's notice (at all points now forever into the future), the SB is still the best guide, as to how expensive it is to destroy BTC (via the 51%-campaign strategy).


### B. P Drives Everything

In the future, SB will equal total transaction fee revenues (TTFR). TTFR are equal to "average price" (aka "P" -- a sat/vbyte rate) times "total quantity" (aka "Q" -- the total number of bytes sold [aka, the size of each block]).

![images](/images/fee-basics.png)

Everyone expects Q [the blocksize] to remain fixed (at its low value). Therefore, TTFR is determined by P.

And thus, P drives everything -- a high P means a high TTFR (and a high SB); a low P means a low TTFR (and a low SB).


### C. A Formula for P and SB

A formula relating P to SB (in the far future when the block subsidy is zero) is as follows...

    SB = P * Q 

Currently, those units are:

    SB (sat/block) = P (sat/vbyte) * Q (vbytes/block)

But we are going to change the units to something more useful:

    SB (Million USD/month) = P ($/txn) * Q (txns/month)

( This may seem tedious, but it pays off. Each step is just multiplication. )

First, whether P is priced in sats or USD, makes no difference whatsoever. Only the *purchasing power* of money matters -- and that PP is exactly the same, be it written down in BTC or USD. More details in part (iii) of the next section.

Second, we can estimate the precise Q (txn/month) value. One ingredient, the *blocks per month* rate, is fixed at [4,320 blocks/month].

The second ingredient, txns/block, is trickier. Currently it [maxes out at around](https://www.blockchain.com/charts/n-transactions-per-block) [2,500 txn/block]. If txns were smaller, that rate could improve. And this happened once before (March 2012, the [introduction of compressed public keys](https://bitcoin.stackexchange.com/questions/3059/what-is-a-compressed-bitcoin-key)). Unfortunately, since then, Layer1 txns have (if anything) [grown larger](https://tradeblock.com/blog/analysis-of-bitcoin-transaction-size-trends). I'm not aware of any plans, in the Bitcoin technical community, to improve the maximum [Layer1_txns/block] rate[^3] to anything significantly higher than 2,500.

[^3]: Each Bitcoin "input" is already \~148 bytes, which is itself (2/3)rds of the size of an *entire standard minimal transaction* (1 input 2 output, \~226 bytes, see [this helpful table](https://medium.com/coinmonks/on-bitcoin-transaction-sizes-part-2-9445373d17f4#7f9a)). So, it is hard to see how the **average** bytes/txn rate could get significantly beneath the value 400. With tremendous engineering effort, it could be beaten down to 200 (5-10 years from now); but not 40 or 4.

Thus, the units of Q are (txns/month). Furthermore, we know the exact value: 2,500\*4,320 = 10.8 million txns/month.

Therefore:

    SB ($/month) = P ($/txn) * 10,800,000 (txn/month)

Finally, if we price Security Budget in "millions of USD per month" (ie, "M$/m"), we have <font color="red">**the formula**Flavor</font>:

    SB = P * 10.8

Thus, if P=$1, then SB is 10.8 M$/m (ie, "Security Budget is 10,800,000 USD per month"). If P=$2 then SB is 21.6 M$/m. 



### D. Common Mistakes To Avoid, When Discussing SB

#### i. Mistake: Stock vs Flow

A common mistake, is to view SB as a "stock" (instead of as a "flow", see [here](https://en.wikipedia.org/wiki/Stock_and_flow)). In other words, critics mistakenly discuss SB as "70 million USD"; but instead they should look for the "30 million USD *per month*" figure.

This mistake leads people to mistakenly conclude that "we can react" to "the attack" via one or more *extraordinary actions*, such as: changing the PoW /  using checkpoints / using UASF / etc. Unfortunately, however, the problem is *ongoing*. So these extraordinary actions would have to become ordinary, not extra-ordinary. They would replace PoW, permanently. (Which would be the end of Bitcoin, as we know it.)

So, SB is an "off button" -- that must be *held down*.

#### ii. Mistake: More Confirmations!

Second, (and related), some SB-optimists acknowledge that PoW is weakened by low security budget, but mistakenly contend that we can respond by waiting for more confirmations (whenever we are paid via layer1 txn).

Unfortunately, if the attacker can pay the full SB, then they can control how many confirmations each transaction has (even, txns that were made long ago): the SB is the cost of renting 100% of the hashrate.

The attacker does not even need to focus on de-confirming txns at all. They could mine empty blocks, over and over again forever. (Or, blocks full of txns controlled only by them, which might appear "full" but be de facto empty).

The "wait for more confirmations" strategy, presumes that the attacker has only relative or temporary power (and that txns will settle slowly but eventually). But if the security budget is rightly regarded as a flow, not a stock, then the attack will never come to an end. In fact, the attack will eventually become "free" for the attacker to sustain (see footnote 2). And once the honest miners realize that they will lose the hash war, the SB is likely to drop to \~zero anyway.

#### iii. Mistake: Pricing SB in BTC 

A third mistake is to price SB in BTC (instead of USD). That is wrong, since it leads people to wonder if BTC price-appreciation will fix the SB problem. It cannot.

To be totally clear: even if the exchange rate *always* went up by trillions of percentage points *every* year, *forever* ... it would do *absolutely nothing* to alter TTFR ("total transaction fee revenues", see above), and therefore nothing to alter future SB.

The right way to price any cost, in economics, is **opportunity cost**. In other words, we can ask "How many sandwiches could I buy, instead of paying the fee needed to broadcast one layer1 txn?". Once we have *that* answer, we may go on to ask "How many sandwiches could I buy, if I used all my money for sandwiches, instead of for the 'Destroy\_BTC\_via\_51%\_Attacks\_Forever' project?".

So the BTC exchange rate makes zero difference[^4]. It is like pricing a sandwich in dimes vs quarters. Or, hoping that if a $3 bill is issued by the US Treasury, then this will improve profits at the sandwich shop.

[^4]: Remember that this article is focused on the long run of Bitcoin. in this article we are focused. In the short run, we can rely on the *block subsidy*. And the block subsidy **is** affected by the exchange rate -- very much so.

Instead of sandwiches, we can use anything we like. It has absolutely no effect on any of the results or conclusions. Thus, we might as well use today's unit of account: the 2021 ["purchasing power parity"](https://www.investopedia.com/updates/purchasing-power-parity-ppp/) (PPP) US dollar.

Using the "USD unit", is not saying that the USD is good (or better than BTC), nor that the USD's monetary system is good (or better than BTC's). It is a communication judgment-call that I, the author, make. It is comparable my decision to write this article in American English (instead of Portuguese), or to publish it on the internet (instead in a magazine). Or, to use Fahrenheit (instead of Kelvin). Ordinarily, Bitcoiners would want to avoid giving the USD any credit. But, in this case, that reluctance is irrational. A research article written in the USA in the year 2021, should use the USD. It is the best unit in which to render all the different costs and quantities. So that they can all be compared, apples-to-apples.


#### iv. Mistake: Being Sucked into a Conversation about 21M (or Blocksize)

Any violation of the 21 million coin limit, is the ultimate third rail in all Bitcoin conversation. If touched, then the conversation descends into mindless posturing.

I wish, that "perpetual inflation" did NOT solve the SB problem. So that it would be kicked out of the SB conversation. Unfortunately, it does (because it eliminates BTC's long-run reliance on fees). And so, people [sometimes](https://twitter.com/hasufl/status/1326514587865411584) bring up the two ideas together. Thus colliding with the rail, and destroying the SB conversation.

I have always taken it for granted, that **adding any kind of inflation to Bitcoin is impossible** and that **the 21M coin limit will never change**. Everyone should clarify their opinion on that, as soon as possible (in my opinion). And then they should refuse to talk about 21M any further than that, because of its catastrophic potential for distraction.

(Same for the blocksize, by the way.)

![images](/images/pt-21m.png)

Above: Peter Todd [wrestles with this exact dilemma](https://twitter.com/peterktodd/status/1109090592666062850).


#### v. Mistake: Focusing on Willingness-to-Pay (ie: ignoring Game Theory and Economics)

A fourth mistake (very common) is to say something like: "people really find Bitcoin valuable, therefore they are *willing to pay for security*".

Unfortunately, a high "willingness to pay" (WTP, or ["reservation price"](https://en.wikipedia.org/wiki/Reservation_price)) for something, does not mean that people actually will end up paying. Many things can sabotage them along the way -- I will discuss two of these.

##### No Market

First: a market *may not exist*, at all!

After all: back in 2007, didn't users *want* all of Bitcoin's features? Surely they did. They wanted these features, but they *weren't able* to buy them. Would "miners" have been willing to *sell* hashrate-security to those users, in 2007? Yes, surely. (The miner's experience in 2008 was, in principle, something they could have experienced in 2007.)

The 2008-market had customers and suppliers, and demand and supply. But it did not exist because it had no product. Alas: wanting something isn't enough -- someone must figure out how to make it. (Satoshi worked that out, and created the blocksize market.)

Satoshi's market makes no attempt to [price discriminate](https://en.wikipedia.org/wiki/Price_discrimination) between high-WTP customers and low. Someone new would need to undertake this task.

In particular, they'd need to solve a glaring [free rider problem](https://en.wikipedia.org/wiki/Free-rider_problem). Can we expect a few rich people to altruistically pay more, for the same service; while other rich people pay less and suffer no consequences? If you believe in that, you might as well declare for Communism.

![image](/images/willingness-to-pay.png)

![image](/images/sanders-financial-support.png)

After all, how often do *you* pay to read a paywalled article? Do you pay to listen to music?! And I bet you love music.

And that free-rider problem is just one among many.


##### High WTP, Low Market Price

Second: even when the game theory checks out, and a market exists, it is still NOT true that a high WTP indicates a high market price.

![image](/images/cheap-water.png)

For example, I have a VERY high "willingness to pay" for food. But food is cheap. Why? Well, it is due to an enormous number of **economic factors** such as: high supply of food; many suppliers; many substitutes (for each food); good technologies for storing food; low barriers to entry for food-producers; low marginal diseconomies of scale (easier for food-producers to ramp up production, if needed), monopsony intermediaries (aka "supermarkets") who value their brand & customer-relationships and who work hard to keep margins low, competition among those, etc.

For blockspace, it could easily be the same. We would have to investigate the economic factors.

That is what we will now discuss.


---


## Part 2. Today's Bleak Fee Values


In the very recent past, P has managed to hover around $2.7. (In recent weeks it has been a dreadful $1.13.)

P=$2.7 would make TTFR = 29.2 M$/m (recall: "29.2 million USD / month").

And, at zero block subsidy, SB would also = 29.2 M$/m.

Obviously, 29.2 M$/m is too low. Just think of all Bitcoin's enemies (and/or future enemies). VISA's 2020 operating *profits* [were](https://annualreport.visa.com/financials/default.aspx) 1,173 M$/m USD  -- 40 times higher than 29.2. JP Morgan's [operating profits](https://www.macrotrends.net/stocks/charts/JPM/jpmorgan-chase/operating-income) range between 3,000-4,000 M$/m. The [IRS budget](https://home.treasury.gov/system/files/266/19.-IRS-FY-2021-BIB.pdf): 1,003 M$/m. The FED's [spending on staff salaries](https://www.federalreserve.gov/aboutthefed/files/combinedfinstmt2020.pdf) (NOT including the board of governors, currency costs, open market operations, etc): 297 M$/m. In 2013, the US government spent 141.7 M$/m on [empty buildings it didn't even know that it owned](https://www.npr.org/2014/03/12/287349831/governments-empty-buildings-are-costing-taxpayers-billions). The 2021 [Chinese military budget](https://en.wikipedia.org/wiki/Military_budget_of_China): 17,471 M$/m.

Those numbers are a *lot* bigger, than Bitcoin's little 29.2 SB. Worse, they are all *growing over time* (at roughly 3-6% per year).

![images](/images/fee-realism.png)

![images](/images/fee-optimism.png)

![images](/images/todays-fee-rates.png)

So, we have to hope that our P rises. It needs to go up by *at least* 10x-100x (if not *much* much more).

Will it?

---

## Part 3. The False View of an Automatic Upward Trend in P

Unfortunately, I agree with [Hasu](https://twitter.com/hasufl/status/1281676218744680449): P has been "stubbornly low". It just won't go up.


### A. The So-Called "Trend"

Some say that P has been steadily increasing over time.

After all, just look at the data...

![naive-fee](/images/naive-fee-trend.png)

It seems to be growing geometrically over time (as the y-axis is log-scaled).

If so, it would mean that demand for blockspace is growing steadily. SB will therefore be higher in the future, potentially much higher. Even if we do nothing! Number go up!


### B. Illusions in the Data

Not so fast!

First, let's remove two illusions from the data, by making two small adjustments:

1. **Frivolous Fees** -- Every fee below $0.10 is equally meaningless to the user. There just isn't any difference in the purchasing power of 7 cents vs 4 cents vs .007 cents. They are just too small. A change from .007 cents to 7 cents doesn't represent a genuine 100x change in demand (ie, a genuine change in "willingness to pay for blockspace"). Worse, most of these "changes" are almost certainly artifacts of the arbitrary ways in which fees were hardcoded into wallets from 2009 until around 2016/2017.
2. **Euphoric Days** -- During bubbles, the price of BTC is going up, quickly! Very often, BTC will rise 5% **in a single day** (which is an APY of 54,211,841%). During such times, people really couldn't care less about "paying" a fee -- any "fee" they pay will be subsumed by their investment gains[^5]. So these fees paid certainly do NOT represent genuine demand for blockspace. (As BTC cannot sustain-ably pump at +54,000,000% per year indefinitely, haha. In the long run it can only pump at roughly the level of real GDP growth -- historically about +3%.)

[^5]: Or, in the case of the BTC-holder, the txn fee *already has* been subsumed, by the day's appreciation.

And that is really just the bare minimum. We might adjust further. For instance, we could try to figure out how many of these people are buying BTC for the very first time ever, and who therefore have just invested many hours in trying to learn about BTC (next to those hours, an additional $50 fee is not significant, and may even be the fastest way to learn). Or, we could find all the times in which the block weren't full, and delete those from the dataset (as the market clearing price will be totally different, in a world where users do not have to bid *against each other* [as they do in the world where blocks are full]).

Anyway -- after those two paltry adjustments, we get the following picture:

![images](/images/fee-graph-adjusted.png)

Above: A graph of P with the two adjustments above, so as to look closer at the underlying "trend". We see four "episodic bursts" of high P -- early2014, late2017, summer2019, and 2020-2021. During those times P rises, but it quickly falls back down to a negligible value near $1.


### C. The "Episodic Bursts"

Those four episodes coincide with *ultra-bull markets* -- huge, salient, mega-increases in the price of BTC.

We can see it easily, by adding the exchange rate to the plot (right vertical axis).

![images](/images/fee-graph-episodic-bursts.png)

It is clear-as-day: the fees only go up, when there is an enormous bull market. If we want fees to rise (above utterly negligible levels), then we need to see the market exchange rate go up by about 10X.

### D. Bull Markets Pump Up P ...Temporarily

Crucially: **after** the euphoric bull market is over, P falls right back to negligible values ($1 or so). Here is a graph of all >$1 fees:

![images](/images/fees-above-1.png)

And here is the same graph, with some triangles added:

![images](/images/fees-above-1-triangles.png)

Above: The red triangles (exchange rate) have a base with an upward slope (representing a permanent increase in exchange rate), but the blue triangles have a base with a flat slope (representing the Sisyphus-ian fees falling back down).

![sisyphus](/images/sisyphus-hummel.png)

Above: "Sisyphus", photograph by Jeffrey Hummel, 2020, from [here](https://fineartamerica.com/featured/sisyphus-jeffrey-hummel.html).

### E. Relative Magnitudes

To get P to rise above $10, it takes an enormous bull market -- from $500 to $20,000 (as in late 2017), or from $5000 to $55,000 (as in 2020-2021).

The smaller bull market in summer 2019 (which occurred near the Bitcoin2019 conference), was only enough to drive fees up to $5.

But again: while the **exchange rate gains are permanent**, the **rise in P is transitory**. P falls right back down when the fun is over.

### F. Can't Pump Forever

And it is just NOT possible for Bitcoin to have a 10x bull market forever. If BTC continues to *outperform all other assets*, then it will be worth a larger and larger share of total economic wealth. And if that continued forever, eventually the 21M BTC would just *be* worth 100% of the world's wealth, after which point Bitcoin cannot outperform anything else, since it is only competing against itself.

Thus, the true empirically-observed representative value of P (this whole time) has probably been something-like $1-$2, at best[^6]. The other higher values are just transitory Euphoria, and do not represent genuine demand for blockspace. (They represent demand for a piece of the bull market action.)

[^6]: I would not be surprised to learn that this reservation price ($1-$2) is close to the price charged by other transaction companies (ie, credit cards which charge about $0.20 + 3%; and Venmo etc which is "free" to use). After all, those specialists have been optimizing their pricing for decades.

To those who still believe that P is genuinely rising, **I pose the following challenge**: point to a continuous multi-month period, in which the BTC price was down and/or "sideways" (ie: growing at less than 100% APY), and also in which P was *above $2 AND increasing*. If many such periods can be identified, then that would show that people are genuinely interested in purchasing blockspace (vs my contention, that they are instead interested in purchasing part of a super-bull market). 

### G. Conclusion - The "Stubbornly Low" P

Unfortunately, it seems that P is both [1] very small, and [2] static (not growing over time). Therefore, something will have to change.

---


## Part 4. Theory / The Future

The empirical picture (of the past) is bleak.

But who cares? Empiricism is overrated.

The question is this: will the consumer tolerate high prices? (In our case: high fees, on BTC Layer1 Transactions [BL1Txns].) In economics, this is called *long run price elasticity of demand*.

    Elasticity
     
        Low                       High
         |-------------------------|
    SB-Optimists              SB-Realists 
     
    Consumer is able,         Consumer is unable,
    willing, and required     unwilling, or not 
    to pay high txn fees.     required to pay
                              high txn fees.


### A. The Bad News

First, some bad news:

1. Everything in the whole economy has been getting significantly cheaper, every year since forever.
2. Everything has been getting significantly more *elastic* and competitive, every year since forever.
3. One of the biggest drivers of elasticity is time-frame. Over the short term, consumers & entrepreneurs can't search for alternatives, so they must pay top dollar. But in the long run, it is the reverse.

Over time, people will get better and better at *sending crypto (incl BTC) to each other cheaply*. BL1Txns will tend to get cheaper, for the same reason that *everything* has been getting cheaper.

![image](/images/abundance-index.png)

Above: The "Prosperity Index". We humans get better and better, at getting the things we want.

Not only have prices been falling, but competitiveness has been increasing. In the past you could either attend the opera for $100 or buy a $20 opera CD. (Once upon a time, you couldn't even buy the CD). Today, you can browse innumerable $0-cost opera videos and mp3s, from numerous competing sources. But that's just half of it: in the past, opera had no competitors -- you had to listen to whatever the Maestro wanted to conduct. Now you can listen to any kind of music that you want. You can pause the music to start a Netflix series, and you can pause the Netflix series to play a videogame. The entire "entertainment" category is in cutthroat competition with itself.

Not only are prices plummeting, but the rate at which they fall is accelerating. The newer technologies, such as DNA sequencing, have [fallen in cost at some of the fastest rates ever recorded in history](https://www.humanprogress.org/the-fastest-learning-curve-in-history/). Today, the market it overwhelmed with new products. We don't have enough time to even learn about all of the new stuff being provided to us.

All of this is very good for the consumer. We get more stuff. But --if it applies to P-- then it is quite bad for the SB-Optimists.

Does it apply to P? Or are BL1Txns (Bitcoin Layer 1 Txns) txns some kind of miraculous exception to this trend?


### B. Aside: Coins vs BL1Txns


Bitcoin **coins** (the 21M) are different from **BL1Txns** (Bitcoin Layer 1 transactions).

The **coins** are, indeed, a "miraculous exception" in many ways.

The coins have ultra-strong network effects, which are impossible for competitors to imitate (since they are based on real world properties, such as liquidity, name-recognition, marketcap, etc). The coin-software solves a coordination problem, which competitors would reintroduce, just by existing. The coin-software also solves the problem of keeping inflation taxes low; but each new coin introduces new crypto-inflation.

BL1Txns, in contrast, are a transaction service, that everyone wants more of.

![image](/images/btc-blockspace-vs-coins.png)

Above: A big table to make a simple point -- BL1Txns (Bitcoin Layer 1 transactions) are different from coins. P is a statistic that is only relevant to BL1Txns; P is literally ($/BL1Txn). P is not relevant to the supply/demand for coins. Lower images taken from [here](https://marketbusinessnews.com/financial-glossary/capital-goods/) and [here](https://www.ig.com/en/shares/what-are-shares). Outline of idea from [Mises](https://mises.org/library/theory-money-and-credit/html/pp/1221).

Money-units are proportional, so the consumer has no interest in "bringing down" the BTC exchange rate.

In fact, it is the reverse. When I argue that "everything is getting cheaper", I mean that there is deflation, aka a *more expensive* Bitcoin.

    Cheaper Stuff = Deflation = BTC Moon
    Low Inflation Taxes = BTC Moon

Similarly, we can see why people would NOT want to "innovate" to bring their inflation taxes *up*. Instead, people will get better and better at *keeping the BTC supply fixed*. Ie: keeping inflation taxes low; ie, at maintaining the 21M coin limit. (Bip300 is one such example; as is the "ossification" strategy; and to some extent "toxicity" is as well.)

So, if I am right, then life will get better in two ways: one, cheaper BL1Txns; two, people will get better at keeping inflation taxes low (ie, they will get better at maintaining the 21M coin limit, and better at sending the BTC exchange rate *higher*). The long march of progress!

The problem is: the former lowers P; and the latter fades into irrelevance as the halvenings kick in.

So, am I right? Will long run BL1Txns be cheap?


### C. Transaction Competitors

As mentioned before, high WTP does not necessarily mean high P. Of particular interest are the *competitors* to BL1Txns.

These competitors include:

* Fiat Rivals (Venmo, WeChatPay, CBDC, etc)
* Rival Cryptos (Especially BTC clones)
* "Off Chain" BTC Layer2s (see Next Section)


#### i. Fiat Rivals

Fiat Competitors are threating to BL1Txns because they do things BLT1Txns cannot: they will be blessed by local governments, and widely accepted.

Worse, their "P" value will be ultra-low. Already it is approaching zero:

|Era|Time Period|Cost|
|:-:|:---------:|:---:|
|Physical Exchange Only|Most of Human History|--|
|Wires/Banking|1880-Present|$20 (1950s), $75 (today) |
|Credit Cards|1980-Present|sub-$1 + a few %|
|Venmo|2015-Present|\~Zero|


#### ii. Rival Cryptos

Of course, the black/grey markets will prefer crypto.

But will they prefer BLT1Txns? And, if so, by how much?

Reminder: we are NOT talking about **coins** to hodl; nor about coins that might try to replace BTC or Fiat. We ARE talking about the solution to a user's problem: completing **a DNM transaction**.



##### A Hypothetical Story

Imagine --hypothetically-- that you want to make an "illegal transaction". The kinds for which "crypto" is now famous. For example: you want to pay a $400 ransomware ransom; or you want to buy $400 worth of heroin on the Dark Web. You (the buyer) are just using the payment service (you are not necessarily a "crypto investor"). Your goal is to turn $400 of fiat, into crypto, and then into your purchase. Same for the seller. Their goal is to sell the product for $400, and convert the $400 of crypto into $400 of fiat.

Now, so far --in the scenario above, as I have laid it out-- the "crypto" could be anything. It is a fully interchangeable part.

And, therefore --again, as I have laid it out above-- the *blockspace* of any Altcoin is interchangeable with that of BTC.

SB-optimists hope that users will somehow be drawn to use BL1Txns, despite having no desire to hodl any crypto. How might that come about?

##### Exchange Rate Fluctuations

First, what about **exchange rate risk**? Wouldn't that drive people away from Alts and toward BTC?

Well, if that is a significant concern, the buyer and seller can conspire to complete the transaction as quickly as possible. 

    Neither party holds Bitcoin for very long
    and neither cares about the Bitcoin price
    as long as the total fees (USD →BTC, BTC
    transfer, BTC →USD) are reasonable. 
    -Jimmy Song

[Above quote](https://jimmysong.medium.com/bitcoins-path-to-method-of-payment-6cb5b3297268).

Second: the direction of change is unpredictable. In other words: exchange rate change is just as likely to benefit the seller as the buyer -- on average, it "cancels out".

If exchange rate risk is still annoying, we have to weigh this annoyance against the extra cost. (The Altcoin will have near-zero cost; vs BTC which will cost "P".) Will it be worth it to pay P, in exchange for slightly more "stable value"? People have been using BTC on DNMs for years, despite absurd exchange rate volatility -- certainly those users didn't find volatility to be a deal-breaker.

Third: If value-stability is a serious concern, then DNMs may switch to using Tether or some other stablecoin. Or buyers might buy "credits" on the site with crypto, or many other things. But these innovations will probably not happen, because the truth is that DNM customers don't care about exchange rate fluctuations.


##### The Seller's Preferences

Second, what if the seller believes strongly in **their favorite crypto** (ie, BTC)?

The seller's preferences make almost no difference. Because he has to impose them on a consenting Buyer.

The buyer will pay [$total_cost = $price_charged + $txn_fee], if they want the good (and, alternatively, if they don't want it enough, then the buyer will pay nothing). The seller will get [$total_received = $price_charged - $txn_fee]. In our example, neither the seller nor buyer cared about holding crypto at all -- to them they are all intermediate goods.

The only ways the seller's preferences could make any difference, are very contrived. They involve situations where they exchanges are unreliable (or had high fixed costs), or if the product somehow had to be purchased on-demand, or had peculiar storage costs. I doubt grandma/drug-addict is keeping a BTC balance on hand, just in case of emergency need to buy more ransomware/heroin. The users either keep it in USD, or in heroin.

And, anyway: if the seller is someone who does *many* transactions (but *not* much crypto/currency speculation), then they will tend to "prefer" a crypto with low txn costs, anyway. So, it is fortunate for the SB-Optimists (and for Bitcoiners) that the seller cannot, on a whim, alter the DNM value proposition of BTC, by temporarily preferring to be paid in something else.

##### Properties of BTC

What if BTC has **the best code**, or best features? Well, Bitcoin is open-source, so it makes no difference. If there is market demand for something BTC-like (but with lower fees), then someone will create it. It will either be LiteCoin, or just a de facto exact clone of Bitcoin Core. It can even have a *smaller* blocksize so as to be *more decentralized*. Just a bunch of "mosquito Bitcoin" networks that pop up to facilitate transactions.

There may be a slight "chicken-and-egg problem" with new networks -- few people want to use a brand new network. But this just means it will take time to find the right circumstances where we can grab one egg and one chicken at the same time. In the long run, it is more than feasible.

#### iii. Rival Cryptos Will Affect P

Therefore, as the public learns more about Altcoins, they might be: less likely to *hodl* any; but more likely to use them for USD-denominated illicit trades.

( Rival cryptos will not only evolve as a response to high P, but as a response to any problem that Bitcoin has [but refuses to solve]. ) 



### D. Summary of Part 4

Bitcoin may have a monopoly on sound money.

But BL1Txns do not have a monopoly on transactions -- both Light Markets and Dark Markets will have lots of payment providers. Whatever people like about BTC (such as SegWit or LN), can be copied into a new Alt (just as Litecoin does, regularly).

All around the world, entrepreneurs are trying to make payments as cheap as possible. Venmos/WeChatPays are an example (see ["14% of adult Americans"](https://balancingeverything.com/venmo-statistics/); and ["800 million users"](https://sampi.co/wechat-pay/)). They will have teams of people working for them, and will take advantage of the latest ideas.

High costs stimulate entrepreneurial effort. High BTC transaction costs in 2016, likely stimulated interest in ETH (and in the LN); high ETH txn costs in 2020-2021 likely stimulated interest in BSC/Solana. People just **don't want to pay a cost, if they don't have to**.

Over time, people will use intelligence, hard work, and competition to get more of what they want at a cheaper price. 

Now, on to the layer2s.


---


## Part 5. The Layer2s & P -- Friend or Foe?

### A. The Bad News

What is the relationship between Layer2s, and Layer1 fee revenues?

On one hand, Layer2s compete with BL1Txns. The *whole point* of LN is to be a cheaper, faster version of a BL1Txn. And that users would use LN txns instead of BL1Txns. That is true for every Layer2.

Furthermore, most Layer2 txns do not pay their fee to Layer1 miners. On LN, it goes to other LN nodes, to compensate them for their risk, working capital, channel management, reliability, uptime, etc. For statechains, there may not be any fee at all (or it might be paid via LN). Transaction fees on Liquid go --believe it or not-- [straight to Blockstream](https://help.blockstream.com/hc/en-us/articles/900001386846-How-do-transaction-fees-on-Liquid-work-). For custodial L2s there is likely no fee whatsoever (you merely pay with part of your soul). Certainly with [OpenDime / ColdCard etc](https://opendime.com/), and [Intel SGX / Teechan](https://arxiv.org/abs/1612.07766) no fee is paid to Layer1 miners.

|Layer 2|Layer1 Fee Pass-through|
|:---:|:---:|
|Merged-Mined Altcoins/Sidechains|\~100%|
|LN|0%|
|Custodial|0%|
|Liquid|0%|
|Statechains|0%|
|Physical Bearer Wallets|0%|
|SGX, etc|0%|
|Wrapped BTC on other chains|0%|


### B(1). The Good News

On the other hand, every L2 needs L1 to some extent; and each L2 makes L1 more useful.

You cannot even *join* any Layer2, without first sending coins there on Layer1. If a Layer1 has nice L2s, this makes people happier about using the Layer1. For example, if the L2 was super-slick, and could reliably meet all of your transaction needs for the rest of your life, then you would be really excited to join that L2. You would join Layer1, just for the purpose of joining that Layer2. So, the Layer1 "txn fee" would really just be a one-time "Layer2 onboarding fee".

How do these two effects combine?

### B(2). Actually the News is Still Pretty Bad

Unfortunately, as with the food/Communism example, higher WTP does *not* necessarily mean that the market-clearing price will increase, at all. We have to consider the economic factors.

If Bitcoin has a really really cool Lightning Network, then some competitor can copy it.

![images](/images/midwit-onboarding.png)

Above: Same image as before, plus [this](https://knowyourmeme.com/memes/iq-bell-curve-midwit/photos/page/4) (with [this](https://www.urbandictionary.com/define.php?term=Midwit) stat).

The same goes for anything that Bitcoin has, that people like. Wherever BTC has good Layer2s, a competitor can emulate them. Wherever BTC has costs, a competitor can make a cheaper version.

### C. The Fundamental Dilemma 

The **fundamental dilemma** is this: the transaction fees have to be *large enough* to deter attackers (who might try to harass Layer1), but NOT large enough to deter users (who might want to switch to different Layer1). But the final total, cannot be both large and small at once.





## Part 6. The Inevitability of Merged Mining

Luckily for us, there is one solution to the Security Budget problem. 

It was invented over 10 years ago, and has been in use ever since (albeit in a feeble form): Merged Mining.


### A. How MM Boosts Fees

With [Merged Mining](https://academy.binance.com/en/glossary/merged-mining), one can mine several cryptocurrencies at the same time.

One "leader" blockchain is mined "normally" (exactly as before). The other ("auxilliary") coins are modified in a very precise way, so that they are "inside" of the leader blockchain (without the leader protocol noticing). That's right -- it is the *followers* who must be specially configured, for merged mining -- the leader is unaffected and may not even notice that it is sharing its hashrate with other coins.

When you mine several cryptocurrencies at once, you also collect all of their revenues!

In other words, miners of BTC/Layer1, can earn revenues, from *every* transaction... even those on other blockchains (such as the Namecoin blockchain, or the Elastos blockchain, etc).

From a miner-revenue point of view, MM is an evasion of the blocksize limit. 


### B. The Great Lie About MM

#### i. The Conventional View

Yes, you heard that right -- MM evades the blocksize limit.

For years, two elite developers have claimed that MM is dangerous for that reason.

And many people believed them. Sadly, it is now the conventional view. For example, this excerpt [from Bitmex](https://blog.bitmex.com/the-growth-of-bitcoin-merge-mining/): 

    ...complex or resource intensive merge mining schemes, which
    miners may need to run in order to remain economically
    competitive, could increase mining centralisation pressure.

(Bad news for us, if this view is correct -- since we can do nothing to stop MM, as I explain in (C).)

#### ii. The Correct View

Fortunately, however, those individuals are mistaken. "Centralization" is about [how cheap it is to run a node](https://www.truthcoin.info/blog/measuring-decentralization/) -- ie, how easily a user can access and enforce the protocol.

To mine, you need a node; but to run a node, you do NOT need to mine. The MM-hate is wrong, because it gets this relationship backwards.

![images](/images/mm-paternalism.png)

It should be as easy as possible to run a node -- that is decentralization. But it should NOT be as easy as possible to find blocks! **To those who (mistakenly) want it to be easy to find blocks, I ask the following question**: why not remove Bitcoin's *difficulty adjustments*? We can set the difficulty as low as possible, and leave it there forever. Then *everyone* can find blocks, easily!

Mining should be difficult.  The difficulty adjustments are what deter attackers; they are what protect us. They are how the security budget is enforced. They focus our attention on the protocol's most dedicated stewards and defendenders. And, how do they accomplish this? By making mining *more difficult*.

Bitcoin is designed, to be indifferent to the joys and sorrows of miners. No matter how much compute-power goes into *producing* a PoW-block-header, it takes only a tiny, independent amount of cpu-power to *validate* that PoW. Miners have full freedom to change their hardware, power source, the scale of their operation, their ratio of fixed/variable costs, they may to quit or join at will, book profits or losses -- the network doesn't even notice. Earlier this year, *ALL Chinese mining shut down, and mostly moved off the continent* -- and it is plausible that the vast majority *of Bitcoin users* neither knew, nor cared. If tomorrow, that story were revealed to have been a hoax, and in fact 99% of mining still taking place in China -- it would make no difference to the network. All Bitcoiners are told: "run your own node"; but how many are told "run your own Bitcoin mine"? One job of a full node is to protect the user against miners: when invalid blocks are mined, nodes filter them out -- it is as if they never existed. But nodes never need to do anything to prove themselves to miners; a miner has never rejected a node. 

Mining should be difficult. The cost, risk, capex, time-commitment, and specialization, should all be enormous. Miners, should exploit every last process improvement. They should never leave money on the table -- they should hash as cheaply as they can; they should max their txn-revenues however they can. Any stone left unturned, is a gift our enemies (who, after all, will do whatever they see fit, in order to press the BTC "off" button). Miners should be the best of the best (comparable to Navy SEALs or Chess Grandmasters) -- they should know everything there is to know, about the state of the art, and more.

I understand that specialization makes some people uncomfortable. A specialist has an advantage, over the layperson. A Grandmaster would beat me in Chess -- maybe I'd rather play Tic-Tac-Toe. Or maybe I'd rather not play anything. But that is just another thing the MM-skeptics get backwards: in the real world, the *attacker* picks the game. They get the first move, and they decide whether or not we keep playing.

In my opinion, the anti-mining-specialists are living in a dream world. And have been for some time. This excerpt... 

    The MegaBigPower Company... has invested over $1 million into
    a custom 1.4MW facility... 30 tons of air conditioning, ...
    their fans now move 150,000 cubic feet of air per minute.

...is from [a report on mining](https://www.allied-control.com/publications/Analysis_of_Large-Scale_Bitcoin_Mining_Operations.pdf) from *March 2014*. Here's  [a similar article from Oct 2017](https://spectrum.ieee.org/bitcoin-mining). BitFury has --for 7 or so years now-- sold miners [*by the marine container*](https://bitfury.com/crypto-infrastructure/blockbox). What non-specialist could possibly afford that? (And, I might add, who among us grows and prepares his own food, builds his own shelter, defends his own borders, etc? Specialization of labor = prosperity.).

Last of all, there's the cold reality of what the difficulty adjustments literally do: they *fire half of the miners* -- the under-performing half. Every two weeks, all of the "mining designs" which are *not above average* are fired. That is, obviously, a recipe for specialization and evolution.

How did such a wrong view

#### iii. Conflicts of Interest

I'm not sure. Perhaps it was bad luck. Perhaps it is because MM is probably only understood by 5-10 people.

I do know, that the "Great MM Lie" had enormous financial consequences. It singlehandedly caused the blocksize war (altering enormous personal fortunes), delayed the arrival of sidechains (thus "pumping" life into thousands of Altcoins and Scamcoins), enshrined technocrat developers as a monopolist cartel of elites, and altered the trajectory of billions of dollars of venture capital money, stock options, salaries, conference revenues etc.

It also altered Bitcoin's culture. In the past, it was: ["Bitcoin User Not Affected"](https://i.imgur.com/R3CaKks.png) -- we were immune to the world's stupidity, and didn't have to care about anything. But today, we poke our noses into everyone's business, and enforce a vast, cheerless vigilance... all to "protect" the protocol. The "defenders of Bitcoin" are beneficiaries of the MM/anti-sidechain lie -- we give them clout, respect, speaking invitations, sponsorships, and even jobs.

To me, the answer is somewhere between [this](https://www.youtube.com/watch?v=vhgaPVO8aw8) and [this](https://meaningness.com/geeks-mops-sociopaths).

Fortunately for me, however, the "Bitcoin User Not Affected" view, is just too good to keep down. The best Bitcoiners know it, and cheer it on, especially when the issue is framed amicably:

![images](/images/cry-harder.png)

Above: [Cry Harder](https://medium.com/@francispouliot/cry-harder-31a599a2e343) -- the correct Bitcoin ethos. Bitcoin will fail if it relies on altruism, and it will also fail if status-quo-elites can modify it (based on some pretext).

Speaking of that...


### C. It's Too Late -- MM is Already Widespread

Most Bitcoin-miners already MM [in multiple forms](https://blog.bitmex.com/the-growth-of-bitcoin-merge-mining/):

    Each coinbase transaction contains commitment hashes
    to many alternative blockchain systems, sometimes as
    many as four or five.
    -BitMex

![images](/images/mm-widespread.png)

Above: A graph of one type of MM (the type used by Namecoin). Miners have been doing it for 10+ years. When BIPs 300/301 are finalized, the number will probably hit 100% and stay there forever.

Slushpool will [automatically MM several coins](https://help.slushpool.com/en/support/solutions/articles/77000433944-is-slush-pool-merge-mining-) on your behalf, including Elastos (ELA) and Vcash (VCASH), and credit you with the extra money.

Satoshi himself, [invented MMin 2010](https://bitcointalk.org/index.php?topic=1790.msg28696#msg28696):

![images](/images/satoshi-merged-mining.png)

The project he mentions ("BitDNS"), became Namecoin (in the chart above) in 2010. And we have been MM it from 2011-Present. 


### E. Tragedy of the Commons

By now, it is well known, that an unrestricted blocksize leads to a commons problem.

But if BL1Txn P is stubbornly low, then (low blocksize + no merged mining) also leads to a commons problem. In the low-P case it is the commons problem of insecure hashrate.

Hence...

### F. The Trilemma

If a low Security Budget is unacceptable (as I suggest in Part 1), and P is to be stubbornly low (as I suggest in Part 2-5), then revenues will need to come from somewhere.

To opponents of MM, I ask: where else should we get the revenues?

![images](/images/sb-trilemma.png)

Above: the trilemma. Choose one!

### G. MM Upgrades

Soon, Merged Mining will be drastically better than ever. The two improvements are:

* The MMed chains, will NOT be feeble Altcoins -- they will be super-cool ultra-useful sidechains. Every BTC owner will access these networks for "free" (ie, with the coins they already own), instead of having to buy new coins (as with Alts).
* Blind Merged Mining (Bip301), allows miners to MM without doing anything -- they just include the highest fee-paying txns. At present, to MM miners *must* run Altcoin node software (which is often buggy and resource-intensive).

Then, MM will finally take its place as one of the most important aspects of Bitcoin.




## Part 7. Conclusion

First, the terms I used:

* SB - Security Budget - A USD/month rate. This is how much it would cost to hold down the "off" button on Bitcoin. SB = Block Subsidy Revenues + TTFR. Block Subsidy Revenues "halve" every four years and will eventually be zero, at which point SB = TTFR.
* Txn - Transaction.
* BL1Txn - BTC Layer1 Transaction - The txns in "Layer1", the Bitcoin Core blockchain. Coins must travel to a "Layer2" using these. LN txns, Altcoin txns, Custodial transfers, and Sidechain txns, are all NOT BL1Txns.
* P - "price" of a txn - How expensive it is, (in $ per BL1Txn), to get a BL1Txn into a block. Expressed as an average; also equal to TTFR/Q.
* Q - "quantity" of transactions - The number of BL1Txns in a block. Capped by the 1,000,000 vbyte blocksize limit.
* TTFR - Total Transaction Fee Revenues - The total $-value of all txn fees paid (either, in a block, or just in general). TTFR = P\*Q.
* WTP - Willingness to Pay - How much a buyer *would* pay for something. WTP is privately known, and different for every person (and every good). A high WTP does *not* indicate a high market-clearing-price -- food has a low mc-price, despite ultra-high WTP. Attempts to "price gouge" are disrespectful to high-WTP buyers, who will not tolerate it in the long run.
* MM - Merged Mining - The act of mining several different blockchains at once, and collecting revenues (ie coins) from all at once. MM comes in many versions, many of which users of the parent chain cannot even detect (let along prevent).
* BMM - Blind Merged Mining - A version of MM which is ultra-convenient for miners. They no longer need to run Altcoin/Sidechain node software at all. Bip 301.
* Decentralization - The [cost of starting up a new full node](https://www.truthcoin.info/blog/measuring-decentralization/). Larger blocks are harmful to Decentralization, but MM does not affect Decentralization in the slightest.


Now, a summary of the article:

* If you can pay the SB, you can disable Bitcoin. Thus, SB cannot be too low, lest Bitcoin become trivial to disrupt. Eventually, SB = TTFR. Since TTFR = P\*Q, and since Q is fixed, it all comes down to P. 
* Today, P is much much too low. 
* P actually has not been rising over time. It has been low this entire time. The *illusion* of a trend sometimes emerges, due to unrelated factors, such as the breakout of an enormous bull run in BTC. But people are stubbornly unwilling to pay for security.
* P will probably be even *lower* in the future. Coins are not BL1Txns -- no one wants more inflation taxes, but everyone wants more plentiful Txn-throughput. Entrepreneurs and technologists are working hard, every day, to create new transaction systems, a drive equilibrium-P as close to zero as humanly possible. 
* Layer2s do not help the situation. In fact, they make things worse by providing yet-more BL1Txn competitors. Each Layer2 improve its host Layer1, but any competitor can copy these Layer2s. L1 fees must be high enough to deter attackers, but low enough to Not-Deter L1-users (from using something else).
* Bitcoin miners will eventually embrace Merged Mining, at which point the Security Budget problem will be solved. Concerns about MM are mistaken, because they get the relationship between Mining and The Protocol backwards. The delay in embracing MM, has caused enormous suffering to most Bitcoiners, whilst enriching ICO/Altcoin scammers and a few Bitcoiners.


I hoped you enjoyed reading this article. I enjoyed writing it!!

Finally, two Appendices:

---

## Appendix 1 - Why are conversations about P so terrible?

### A. The Lie of MoE "Vs" SoV

Unfortunately, the Blocksize War of 2016-2017 damaged BTC culture. One of the casualties was "discussion of P".

Specifically, the War prompted a divide between "store of value" Bitcoiners, and "medium of exchange" Bitcoiners. The former say that BTC is for saving, and the latter say that BTC is for spending.

Of course, "money" must be *both* saved and spent[^7]. (Thus, we could improve our "money" by making it easier to spend, *or* easier to save.) There is no one ["before"](https://www.youtube.com/watch?v=uKklU59m47U) the other; nor does value come ["from" one "group"](http://nakamotoinstitute.org/mempool/im-hoarding-bitcoins-and-no-you-cant-have-any/) or the other.

[^7]: Just imagine a money that you could *not* spend, at all. You cannot transfer it to someone else, and they couldn't transfer it to anyone else either. That "money" might as well be invisible! (And how would you come to "own" it, in the first place?). So, money must be spendable. Secondly: imagine a money that you could *not* save -- for instance, you would earn a "paycheck" at work and be required to *instantaneously* take the entire balance in goods and investments. That would not really be "money", either. (And, again, how would you come to "own" any of it in the first place?) In the real world, you hold a balance of money on hand (in your wallet, or checking account), in order to meet unexpected needs, and to buy things that you don't *yet* realize that you need to buy. So money must be "save-able".

What really happened was this: Bitcoin is inherently very confusing. So, we each opened our mind, to this novel idea at different times, due to our unique skills, background, temperament, social circles, and good luck:

|Group|How BTC's Value Was Demonstrated|
|:---:|:------------------------------:|
|Satoshi Nakamoto| (unnecessary) |
|Brilliant Visionaries / Fmr. Liberty Reserve Customers / DNM Users | After reading Satoshi's whitepaper and trying his software.|
|Tech-Literate Drug Addicts, Econ-literate tech enthusiasts|After learning of SilkRoad / reading the Jan 2011 Wired article.|
|Laypeople 1|After seeing the Good Wife episode (s03e13).|
|Laypeople 2|After seeing that a liquid market exists on Mt Gox.|
|Skeptics|After seeing the price crash on Mt Gox but eventually recover.|
|Other Skeptics|After seeing the late-2013 US Congressional Hearing on Bitcoin in which the govt decided to be "hands off" and that no new regulation was needed.|
|Extreme Skeptics|After seeing the community handle the blocksize dispute of (2014-2017).|
|Laypeople 3|After seeing Consensus conference in NYC year after year (or whatever).|
|Laypeople 4|After seeing Elon Musk / US listed companies buy some publicly.|
|Laypeople 5|After seeing Coinbase IPO as a tech unicorn.|


But the "Saver" side won the 2016 War, and so it became socially unacceptable to care about layer1 txn fee demand. After all, *sending* coins is "not what Bitcoin is about".



### B. Satoshi's Stubborn Unification

Unfortunately for me (and for the truth), the relation I published in the very first section (ie, that P ---> SB ---> the existential safety of Bitcoin) contradicts the view of the "Savers". My relation says that we must care about the demand for layer1 BTC block **space** -- ie, we must care about the people using BTC to **make BL1Txns**.

Satoshi's decision *to use transaction fees to power the PoW system*, has inextricably linked those two concepts. Spending BTC, is what makes Saving BTC possible; because it is *layer1* spending that generates the transaction fees that keep the network alive (and immutable).

![images](/images/double-snake-moe-sov.png)

Above: "Double Ouroboros", from [here](http://clipart-library.com/clip-art/56-563964_imagethe-double-ouroboros-double-ouroboros.htm), plus text I added around the boarders. Yes, being a good store of value helps Bitcoin be a better medium of exchange. But, without a healthy SB, the system will fail to enforce property rights.


### C. Not the LargeBlocker Argument

Unfortunately for me, a BCH argument that is false *greatly resembles* my true argument. The BCHers and "spenders" (who lost the war), said: "We want to promote Bitcoin's use for layer1 transactions, but a money that requires $70+ transaction fees is [not useful](https://twitter.com/rogerkver/status/1348316860677165057) and won't work.".

But I am saying the opposite: that **average** layer1 fees *must go up to reach* $70+ (much more), *in order* for Bitcoin to work. The BCH argument relies on a low P to drive a high Q. Whereas I assume a fixed low Q, and point out that we therefore need a high P. The BCH argument wants many people to transact, just because it wants Bitcoin to be popular; I want there to be *high layer1 transaction demand* because I want there to be high layer1 blockspace demand because (with a fixed, low Q) we need a high P to have enough TTFR and enough SB.


    Largeblocker: " $70/tx fees ...will not work
                       (they will be rejected by users)!"
    SB-Realist:   " $70/tx fees ...are *required for* Bitcoin to work
                       (without high P, there are no property rights)."


Regardless of how you feel about the blocksize, or average layer1 fees, **individually**, you **must** believe that, one day, their *product*, P\*Q, (aka TTFR, aka SB) will be high.


## Appendix 2 - How Bip301 Works

I created Bip301 (["Blind Merged Mining"](https://www.truthcoin.info/blog/blind-merged-mining/)), and so I will summarize it here quickly.

The goal is to allow miners (layer1 BTC miners) to merged mine a Sidechain/Altcoin, without running its node software (ie, without "looking" at it, hence "blind").

For example: a sidechain block contains 20,000 txns, each paying a $0.10 fee; so, therefore, the block is worth $2000 of fee-revenue. As usual: the sidechain's coinbase txn will pay this $2000 to someone (this sidechain user is called a "briber", or "virtual miner"). The difference is, under Bip301, the "briber" (who does no hashing) will instead make **one layer1 txn paying \~$1999 to the layer1 miners**. (Ie, that layer1 txn is a BL1Txn which pays a $2000 fee.)

|Item|Layer1 Miner|Briber|
|:---|:----------:|:----:|
|How much hashing?|100%|0%|
|Coins collected, on Layer2|$0|$2000|
|Coins paid, on Layer1|$1999|$0|
|Coins rec'd, on Layer1|$0|$1999|
|d(Net Worth)|+$1999|+$1|

Bip301 makes this specialization-of-labor trustless on Layer1.

Now, remember that "P" is the *average* of all the fee-rates of the BL1Txns. So P is brought upward by these superstar Bip301 BL1Txns. Perhaps there will only ever be 5-15 of these, per layer1 block -- but they may pay 90%-99% of the total layer1 fees. Which is to say: Bip301 txns may boost P by 10x or 100x or more.

These high-P txns are not due to any layer1 transactional demand -- they are just an accounting operation which transfers the value from the sidechain txns to the layer1 miners, using one layer2 fullnode-user as an economic conduit.


---

### Footnotes









<!---

### C. A Thought Experiment

A final thought experiment.

**Today's** fees are very low: around $2.

What if satoshi had hardcoded a flat *fixed* $2 fee, into the protocol (leaving aside the technical issue of how this could be done)? How much use do you think Bitcoin would have gotten, from 2009-Present?

Personally, I think Bitcoin usage would be about the same. I think back to those first customers of SilkRoad -- they would have to learn about addresses, private keys, backing up wallets, how to use TOR, how confirmations work, how change addresses work, how the SilkRoad escrow mixer worked, how to buy the coins (over IRC OTC, or via LocalBitcoins or something), etc. But somehow they managed it.

That level of effort, to me, just seems much higher than the effort needed to acquire $2 or even $20. So I think those customers would have been unaffected.

And I think, ultimately, those customers were the foundation of the entire value proposition of Bitcoin. Not a foundation built on *illegal transactions*! But a foundation built on a money that would work for **both** legal and illegal purchases. Something impartial and non-judgmental.

If you agree with me, that Bitcoin would not have been affected by a fixed $2 fee, then it is 

 ~~ not a strong point, due to the supply/demand interaction ~~ It speaks only about demand.

--->



<!---

	The first [said](https://www.youtube.com/watch?v=UrqG1a3gZcM) as follows: "money must be used as a medium of exchange, before it can 'become' a store of value."
The second is 

- Dan helds of the world who have a job pumping BTC ; feel good news ; dr Feel-Good ; industry of professional delusionists.


Anyone with common sense, knows that 

--->




<!--

## Appendix 2 -- "Fee Doubling"

In a UTXO model, everyone actually has to pay *twice* the fee-rate (aka, 2P). This is because 

### An Example

Imagine tx fees are persistently $5/txn.

(To be precise, I will imagine that they are $5 per txn-input selected -- see the next section on "UTXO management".)

Now imagine that you owe a friend $10. (You are reimbursing him for last night's beers.)

If you have a $15 UTXO, then you can pay him back, right? You just select your $15 UTXO, pay him $10 (and pay $5 in fees). Right?

Not so fast -- yes, it is true that he would now have a $10 UTXO. But, for him to use it for anything, he has to now pay a $5 txn fee himself! Thus, he can only *use* the UTXO that he got from you, in order to make a purchase of up to $5. You aren't actually paying him $10 at all, you are paying him only $5; half of what you owe him.

For him to get $10 worth of purchasing power, you must leave him with $15. But to do *that*, you need a UTXO of at least $20 or more. You must always pay the fee *twice* -- once to move your money (from you to him), and a second time to compensate him (for when he eventually converts the asset into actual purchasing power).

For example, imagine you select one $40 UTXO as your input, send $15 to your friend (to pay him back for the $10 beer), pay $20 to yourself (as change), and pay $5 in txn fees. Your $20 change output will cost $5 to spend; and so your net worth is now $15. Thus, to recap: when you had a $40 UTXO, your net worth was actually just $35; after increasing your friend's net worth by $10, it has fallen (by $20) to the value of $15.

(Instead of losing purchasing power via inflation, it is being lost by transaction fee!)

### Aside: Can UTXO Management Help?

Can we salvage the situation by periodically merging our dust UTXOs?

Not if the fees are **persistently** $5/txn. In Bitcoin it is common to wait for periods when fees are cheap, to merge many small UTXOs into one larger UTXO. (This is sometimes bad for privacy, but always good for reducing fees.) However, the cost-savings are mainly due to timing. If the fees are $5/txn, at all hours 24/7/365, then UTXO-consolidation cannot significantly shrink transaction fees.

This is because each Bitcoin "input" is already \~148 bytes, which is itself (2/3)rds of the size of an *entire standard minimal transaction* (1 input 2 output, \~226 bytes, see [this helpful table](https://medium.com/coinmonks/on-bitcoin-transaction-sizes-part-2-9445373d17f4#7f9a)). To use the money, each input (plus its witness) *must* be included in the transaction. Any savings that come from *adding* transactions, must be due to better management of the 10-11 "overhead bytes". (And these bytes must be managed so well, as to overwhelm the byte-cost of adding yet more transactions -- each new txn costs at least one input + one overhead.)

Thus, the savings are based on *timing* the fees, not some clever re-structuring of the transactions. And so if the fees are persistently high, it will not help us.

Hopefully, at any rate, you can see that I could just-as-easily modify the example -- I could hypothesize that every *txn input* cost $5. 


### Back to the Example
 

Thus, if you own $X worth of Bitcoin, your net worth is:

    $X - (UTXO_Quantity_You_Own * P) - (Quantity_Payments_You_Plan_to_Make * P)

The "quantity of UTXOs you own", 

--->
