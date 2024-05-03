---
title: All the World's Txns
show_author: true
comments: true
date: 2024-05-03 00:01:00
---



### Summary

The Bitcoin Endgame -- **6.4 trillion txns per year** (in 2022), $0.10 fee each, earning miners $640 Billion per year. Each of these figures growing at **6.2% per year**. Almost all of it on L2 sidechains. L2s which do not pay miners, are dead projects.

### A. How Many Transactions in 2022, Worldwide?

VISA / MasterCard / AmericanExpress produce **annual reports** giving their tnx volumes. VISA, for example, does [174.1 B in a year](https://annualreport.visa.com/financials/default.aspx), which grows at around 6-7% per year. (Most annual reports stress the payment volume in $, but we are not as interested in that. We want the total number of payments, independent of their $-value.)

WeChat Pay had [920 million active users](https://www.businessofapps.com/data/wechat-statistics/), in 2022.

We're all daily active users, of some form of payment or another. There are 7.95 B people on Earth. Of those, 2.06 B are "young" (between ages 0-14). Youngsters still contribute to the txn count, of course -- since their parents need to buy diapers and toys and school supplies, etc. Nonetheless, if we exclude them, we have 5.89 B shoppers.

How many txns per shopper per day? Food, coffee, ... gas, haircut, Netflix ... utilities, insurance, taxes ... etc. I would say **3 per day** is a conservative estimate.

Thus, 5.89 B \* 3 \* 365, yields **6.450 trillion transactions per year**.

### B. Growing at what rate?

Do we just project the population growth into the future?

No, we also need economic growth. WeChat Pay experienced 70% $-volume growth, in one year (2020-2021) -- during a time of Chinese population *collapse* (net loss of 850k in 2021-2022; loss of \~2 M people in 2022-2023).

Wealthier people make more transactions. A huge % of the world is rising from poverty, now with their first cell phone. So, the future will have *more* transactions, even if the population shrinks.

Consider the USA data. In 2022/2023, population grew only 0.4% and 0.5%, respectively. Yet US txn-volumes have grown much faster than that -- the FED produces [a report](https://www.federalreserve.gov/paymentsystems/fr-payments-study.htm), finding an average growth rate of card-payments of "6.2 percent per year". The whole page is filled with growth numbers -- all much higher than 0.5%. And the US population growth rate? It is comparable to [the world average rate](https://en.wikipedia.org/wiki/World_population). Poorer countries, will probably experience "catch-up" growth, faster than the USA rate ...at least at first.

VISA gives perhaps the most helpful stat of all: "Transactions processed on VISA's networks": for 2021, 2022, 2023, the figures are 164.7B, 192.5B, 212.6B ... annual growth rates of: 16.8% and 10.4%. True -- VISA is not limited to the USA only, but again, global population in 2020-2024 grew at the same rate as the US. It is true that [VISA's $-volume marketshare](https://www.statista.com/statistics/279469/market-share-of-credit-card-companies-in-the-united-states-by-purchase-volume/) has been growing. But the other payment networks have also been growing: Mastercard shows 10% "growth in cards" (total number of physical cards in circulation), their $-volumes grew by 21%. American Express $-volumes grew at 24% and 21%, in the two most recent years. Plenty of growth all-around.	

After considering these figures, I think we can "eyeball" the growth rate at **6.2%**. That is the figure from the FED's USA card-payment growth. It seems the most reliable, covers many years, and is the lowest and most conservative.


### C. Equilibrium Transaction Cost?

What will it cost, to transact using a Bitcoin L2?

It's an important question, because it determines Bitcoin's long-run equilibrium "security budget", which is equal to these four things (all the same exact value):

* The value of all money paid to miners (total mining revenues)
* The total amount of money miners will spend, on hashing (total mining costs)
* The cost of a permanent, ongoing 51%-attack (hashrate security)
* (expressed as NPV) The value of the all the world's Sha256d mining infrastructure (total mining industry value) 

All we need to do is multiply 6.4 trillion (txns), by the **fee-rate** ($/txn).

I think that $0.10 is a good estimate. We weigh the inconvenience of paying the fee, against the inconvenience of switching to a different chain (or to a custodial solution). Switching chains will be very easy -- but not infinitely so. Ten cents is very low -- probably enough to offset the difficulties of rival payment schemes (the inconvenience / security risk of using cash, or the compliance costs associated with money transmission, chargebacks and customer service, etc).

Most importantly, ten cents is enormously cheap compared to what people are paying today. [Cards](https://www.merchantmaverick.com/the-complete-guide-to-credit-card-processing-rates-and-fees/), [Venmo](https://venmo.com/purchaseprotection/seller/) "payments tagged as purchases", and [Western Union](https://www.westernunion.com/us/en/send-money/app/price-estimator) each charge approximately ($0.10 + 1.5%). The only threat will be new blockchains that are even cheaper -- but at only $0.10 total, they can save their customers only *thirty cents a day* (by our assumptions above), or $9 a month. This is probably not enough to entice people away. Thus, $0.10 will be the equilibrium, profit-maximizing $/txn fee-rate.

( I am tired of replying to the low-IQ people who ask: "Why are you using USD for these figures? USD won't exist in a hyperbitcoinized world.", or --even worse-- "Those are fees that the merchant pays, not the end user". No offense but if your IQ is this low just close truthcoin.info and never return. Find some compatriots to complain to about these inane questions. )

At ten cents, the FY 2022 security budget would be $640 Billion. And it would grow at about 6.2% per year -- in other words, doubling about every 11-12 years.

At 10% TVoM, the NPV is **16.8 trillion dollars**. What a big pile of money!


### D. The Coming L2 War -- Why Merged Mining Will Win

Who *gets* that pile of money?

The miners will get it. It will NOT be LSPs (lightning service providers). Nor will it be ARK supernodes. Nor will it be a custodian (like Venmo)?

The "who-gets-the-money question", is what I mean by "The Coming L2 War".

Why will the miners win?

To me, it is clear: every L2 can be destroyed, by 51%-hashrate. LN, ARK, BitVM -- these ideas all lose their security model, completely, if 51%-hashrate attacks them. (Bip300, ironically, survives the best -- since it was designed, in the first place, to keep hostile miners in line.) Miners have a gun pointed at every L2's head. They will pull the trigger, if a dead L2 increases their profits.

Thus, the non-merged-mined L2s will all be killed. And only the merged-mined ones will survive. Every L2 will pay the miners. This will either happen in an organized, intentional way ("merged mining") -- or it will happen in a contentious, unintentional way ("vertical integration"). In the latter, mining pools are running their own "LSPs" or "ARK Supernodes". A non-miner LSP is in a desperate, hopeless struggle -- against a miner LSP (who is quite comfortable).

In other words, every L2 will be "run by the miners". This has the inconvenient detail that most of the L2s worked on today are dead-on-arrival. ARK, BitVM, etc -- they will be "run by miners", and all of their special security guarantees will cease. The cryptography they employ will be useless. Bip300 is the only [security model](https://www.drivechain.info/blog/fees/) that is unchanged if a miner-coalition runs the L2.

### Appendix 1 -- Blockspace Napkin Math

I predict the world will have 13 L2 payment-sidechains, distributed geographically: East NA, West NA, Central America (+Caribbean), South America, West &North Europe, East Europe + Central Asia, Middle East, China, India, Japan, Oceania, Africa, Rest of World / Internet Native.

For simplicity, we divide the world's transactions evenly into thirteen. And we assume that Bitcoin rapidly takes over in approximately 2030. This gives us the following blocksizes over time:

![image](/images/blockspace-napkin-math.png)

These 13 chains would be "held together", by a single L1 chain with a forever-small 300 kb blocksize. This completes the ["Sidechain Scaling" model I presented in 2016 at Scaling III](https://www.youtube.com/watch?v=Gzg_u9gHc5Q&t=6575s).


### Appendix 2 -- Voskuil Parallelism

Some people wonder if "the network", "can handle" this level of volume.

They should not. VISA already "handles" their level of volume. So, at worst, we would have a "VISA-shaped" L2 chain -- transferring BTC instead of fiat. The L2s can be of any shape or size they want. The L1 will remain small, at 300 kb, and it will settle among the larger networks.

I call this argument "Voskuil Paraellism", after Erik Voskuil who pointed out that the transactions are already being processed -- by all the altcoins. He [calls it "natural sharding"](https://x.com/Truthcoin/status/1760364812968599787) (though only I and four other people can grasp this simple point, seemingly).

Along similar lines, people wonder if users "will tolerate" the fees. (Vitalik Buterin famously said, in 2017, "the internet of money should not cost more than 5 cents per transaction".) But our analysis of the comparative costs (above), shows that they *already are*. They tolerate worse fees today. Rudimentary microeconomics, dictates that merchants bake *all their fees* into the end-price (including the effective average VISA fee). The end user always pays the VISA fee.

### Appendix 3 -- The Decentralization Ratio & Cypherpunk Victory Ratio

So, we might have a "Mastercard-shaped L2" in Europe. Or a "WeChatPay-shaped L2" in China.

We know it is possible, but isn't there a catch?

Yes -- it is the node cost.

The "VISA-shaped L2" would have an expensive node. It would not be *as decentralized as L1*!

But... who cares?  Today's "VISA full nodes" have infinite cost. No one can run a VISA node, except VISA. So, if we can just bring our number down, to any finite value, then we have *improved decentralization*.

Why don't you take a step back a moment, and think about this: if Bitcoin is to process "all the world's txns", then *someone's* computer must be processing. The only question is who.

With lightning, people tried desperately to coral these txns, and limit the processing only to those transacting. That would have been ideal... if it had worked. Instead it has [failed horribly](https://www.truthcoin.info/blog/ln-blackpill/). This dead carcass must be thrown overboard. We cannot afford to f\*\*k up Bitcoin, just to avoid hurting some LN dev's feelings, hurting Greg Maxwell's feelings and his old canard about "global broadcast network", people who year's later want to suck Greg's dick, plus the LN-VCs will don't want their marketing angle soured. LN is a dead idea. The project of limiting the txn processing, has failed.

Bip300 succeeds where LN failed. It allows *some* people to opt-in to higher node costs -- while others ignore node costs that they don't want to pay. Via utxo-commitments, it allows permanent pruning of any blockchain data older than 6 months. So it is a **caching layer** for Bitcoin -- optional temporary data, that only a subset of user store, some of the time. These are L2 chains, so there is no requirement that anyone run them (unlike on L1). This is as good as it gets (in my opinion).

To those who disagree, I pose this challenge: come up with something better. Something that works, and is popular, and which would move **these three metrics** upward -- upward from where they are today, in May 2024:

* "Sovereign Users": those users who can run a node. In other words, those users who *can participate on equal grounds as the top participant*. We might arbitrarily define "can participate", as: "Does it cost more than 1% of their salary to run a full node?". 
* The "Decentralization Ratio", of a payment system: the (sovereign_users) divided by (all_users) . With VISA, for example, the decentralization ratio is 0%, since no one can participate on the same level as the VISA corporation. The BTC decentralization ratio is likely to be higher than 90%, since most Bitcoiners are wealthy, Western, computer-savvy, and since BTC node costs are pretty low. Users could run nodes, if they wanted.
* The "Cypherpunk Victory Ratio": the percentage of Earth's transactions, made by a Sovereign User at the time. Currently this ratio is near 0%, since few transact via "crypto". (It seems [USDT on Tron](https://thedefiant.io/news/cefi/tron-quietly-becomes-the-leading-blockchain-for-stablecoin-transfers) is leading the way, on this metric.)

But I think you'll find that difficult. As I explained (above), only merged-mined L2s are viable. So, anything which *hides the txn* from miners, is doomed. I think only Bip301 strikes the right balance. Some of these "drivechains" will have high node costs (1.8 GB blocksize in 2030). But lower than VISA, which has infinite costs. And everyone will be able to run L1 (which is the important thing). Every other model must be worse, I think.
