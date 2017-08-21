---
title: The Efficient Hasher Hypothesis
comments: false
show_author: true
---

    The Efficient Hasher Hypothesis
    Paul Sztorc
    January 29, 2017


### 1. Claim

Theoretically, one hasher will be the best (ie, have the lowest costs-per-hash). Eventually, this hasher will be the last man standing. He will earn the lowest return on his capital (the 'risk free rate'), and all his laborers will be paid as little as possible.

How do I know this?

### 2. Proof

The proof is two parts. The first is a simple proof-by-contradiction: it is impossible for the mining industry to consistently deliver [economic profit](https://en.wikipedia.org/wiki/Profit_%28economics%29). The second, is that Bitcoin's [difficulty](https://en.bitcoin.it/wiki/Difficulty) adjustments force half of the miners to endure profits which are below the industry average. These below-average miners will be forced out of business, and this process will continue until only one miner remains (or, until several miners tie for first place).

### 3. Part One

Imagine "H" is the group of Hashers. Furthermore, imagine r\* is the rate-of-return on 'rival investment opportunties' (ie, projects of similar risk-profile and tax-treatment). If the average return on hashing, mean(r_H), is higher than r\*, then more of society's capital will be directed toward Bitcoin mining. As a result, H will grow, and inter-block time will shorten. Soon afterward, difficulty will increase. Higher difficulty means less miner profitability, which causes all r_H's to fall, across the board.

Restated: If H are ever enjoying disproportionate profits, they soon won't be. H will increase, there will be one period of 'big H', 'high profits', and then the remaining periods will see r\* level profits.

The converse is also true: If H-profits are disproportionately, low, the least-effective H's will tap out, and ease the suffering of their fellows.

The result is that mean(r_H) and r\* will be constantly drawn toward each other. The interpretation is ['red queen'](https://en.wikipedia.org/wiki/Red_Queen_hypothesis) style cutthroat competition, where any profitable ideas are used once, for small gain, but thereafter become mandatory for everyone.

For example, if miners decide to pay their employees less, they can inflate mean(r_H). But if any miner does this, mean(r_H) will rise, new capital will be called in, difficulty will adjust, and mean(r_H) will return to its permanent home of r\*.

### 4. Part Two

Notice two simple facts:

1. There is never an incentive to invest in a sub-r\* project. (Instead, pull the money out and put it in an r\* project, or the stock market, ...).
2. If miners are heterogenous, someone's mining project is returning below mean(r_H). (Potentially, [as many as](\images\averages.txt) half of all miners).

All that remains, now is to establish a link between r\* and mean(r_H). Which is precisely what we demonstrated above; r\* = mean(r_H) .

The practical effect of the difficulty adjustments is to "fire" half of the Hashers.

Let me be clear that the Hash-Projects are fired, not flesh-and-blood people. We can therefore rest our symphathies.

<!--

###### (Aside) Rank and Yank

Enron reportedly had a system called "rank and yank", where [the bottom 15% performers were fired every year](http://www.laweekly.com/news/rank-and-yank-at-enron-2134275).

Yawn! Bitcoin's protocol fires the bottom 50% Hashers...every two weeks! Assuming a million employees, the Enron New-Year's-Eve party could expect 850,000 repeat-attenders. At "Hash-ron", only ~30,000 of those at the New Year's party would still be employed for St. Patrick's Day (10 weeks later, .5^(10/2)). 

Let me be clear that, fortunately, we speak of soulless Hash-projects, and not flesh-and-blood people. We can therefore rest our sympathies.

-->


### 5. Is This Hypothesis Really Correct?

In practice, we do see high rates of project-turnover in Hashing. Hashers are constantly improving (ie 'firing' old projects and replacing them with stronger performers). These improvements take many forms: [1] ASIC chip efficiency, [2] co-location with cheap power, [3] co-location in countries with strict capital controls, [4] inventive software tweaks (spv mining), and so forth.

In addition to high project-turnover, we also see tremendous firm-turnover (ie, not only must miners invest constantly in new projects, but, to add insult to injury, many of them go bankrupt anyway). Slush recently made it [a point of pride](https://twitter.com/slushcz/status/786522033337225216), that they were **the only firm** to even *survive* in a list of 'top ten' for six measily years!

Everyone else was fired.

Mankind will always innovate; new Hasher-projects will constantly be generated. However, anyone with a basic appreciation for physics, would expect Hashing-innovation to slow over time (if not halt altogether). Eventually, the bi-weekly difficulty adjustments will catch up.

Therefore, in the future all miners will be "Optimal Hashers" who all hash at the same (lowest possible) price.

#### Characterists of Optimal Hashers

What can we guess, about this future filled only with totally-homogenous, cheapest-price-possible Hashers?

For one thing, the economies of scale differ, for capital vs. operating costs.

For capital, it is probably cheapest for every Hasher to [1] allow the current optimal ASIC design to be R&D'd, [2] purchase this ASIC from the sole optimal manufacturer. Therefore, there will likely be one or two manufacturers of optimal hardware. These firms might regularly steal employees / trade-secrets from each other, competing in a kind of [Cournot Duopoly](https://en.wikipedia.org/wiki/Cournot_competition). Or there may be (short lived) monopolies or cartels. While such monopolists would posses 'secret and superior' Hasher-tech, this tech should sell at a commensurate premium, and would therefore leave Bitcoin's security model unchanged.

Operating (electrical) costs are different. Firstly, electrical power generation does indeed have economies of scale -- turning a turbine is difficult and produces energy, and turning a larger turbine is only a little-more-difficult and produces a lot-more-energy. However, there are also scale limits -- only so much water can flow over the turbine in a given 24 hour period (..only so much sunlight can strike the panels, only so much wind will blow, only so much uranium / coal / gas is at hand, etc).

So, on one hand the Optimal Hashers will all use the same equipment and software, but, on the other, they are likely to be geographically distributed near sources of cheap electrical power.

<!--

#### Remarks

~ fix ~

People worry about things like -- all miners in same place, all miners using same equipment, all miners run by same operators, all miners use same 'best practices'. These worrys are unfounded. 

A competitive meritocracy will inevitably concentrate power. This does not alter the economics of Bitcoin's security model, even though it may make miner-coordination easier.

Meritocracy *is* exclusionary. It excludes people with low merit! 

~ move this ~

#### Practice

In practice, these are the hardware owners who 'point' their miners 'at' a mining pool. If they aren't happy with their pool, they just switch to another one.

We have seen a consistent and intense homogenization of Hashers already. Where Hashers once used PCs of all shapes and sizes, now the equipment is super-specialized and comes from 2 or 3 elite vendors.

~ move this ~

#### Influence

With respect to Hashing, nothing can be done to slow or forestall this future. It is a direct function of Satoshi's protocol, which calls for difficulty adjustments every 2 weeks.

Changing the PoW algorithm (itself problematic) would only redefine H (as would a decision to scheduling frequent and/or random changes to the algo, or H itself).

To prevent this, we would need to remove the difficulty adjustments altogether...obliterating the coin issuance schedule and [profoundly damaging Bitcoin's network effect](http://www.truthcoin.info/blog/pow-cheapest/#the-coinbase-rot-paradox-less-is-more) and value proposition.

-->
