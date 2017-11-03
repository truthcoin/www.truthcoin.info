---
title: ASICBoost is Worthless
show_author: true
comments: true
date: 2017-11-02 05:01:00
---


> The equilibrium value of ASIC-Boost is zero.


### Let's Get This Over With

There is a tight connection between these two concepts:

* ASIC-Boost significantly improves mining efficiency.
* *Every* miner is using ASIC-Boost.

For if a miner had a significant disadvantage, they would be very quickly pushed out of business.

This conclusion is significant because of the implications of the second bullet point (above). If *every* miner is using ASIC-Boost (AB), then there is no controversy about shutting AB down and denying it to everyone. This is because any efficiency improvement that *every* miner has, will simply be cancelled out by the difficulty adjustment. An efficiency improvement can only impact miner profitability if it is *relative* to other miners. The one exception is the relatively small inconvenience of going ~half a difficulty period without AB (but this would be quite tolerable during 2017, a year of considerable BTC price appreciation). Mining efficiency improvements are either small, or they are so large that the competition is forced out (at which point you are competing against the most efficient person remaining -- yourself).


And AB may indeed have [forced out KNC Miner](https://archive.is/2vmSE), for example.

( Although, notably, Sam Cole of KNCMiner [actually does *not* agree that AB was the secret advantage](https://hackernoon.com/asicboost-655a73d48ae4). More [here](https://bitcoinmagazine.com/articles/breaking-down-bitcoins-asicboost-scandal/). )

But in any case that was 18 months ago, or about *forty difficulty adjustments* worth of time. Each difficulty adjustment [fires the bottom half of all mining-configurations](http://www.truthcoin.info/images/efficient-hasher-hypothesis/). If the USD/BTC price is currently skyrocketing, then the process of firing miners is greatly slowed...but if the price is instead falling then the firing process is greatly accelerated. 

So it is simply not possible that Bitmain is the only one using ASIC-Boost. Such a scenario would only be possible if BitFury and other Bitmain competitors had some kind of *other* (non-AB) efficiency technology that was effective to a comparable degree. But what is more likely is that all the miners constantly copying each other's best practices (by reverse-engineering each other's chips, poaching employees, formal industrial espionage, or just by progressing down the same path of objective engineering knowledge). If ASIC-Boost is more efficient, there is probably all kinds of sleight-of-hand going on, so that [everyone can get around the patent](https://bitcoinmagazine.com/articles/bitmain-may-be-infringing-asicboost-patent-after-all/) and use it.

So it is clear to me that *everyone* is using ASICBoost, and has been for some time. Or else, it must be that ASIC-Boost is simply not very important (in which case, whether or not "everyone is using it" is a moot point).



### Explained Again

Since the point is (apparently) so important, let me go over it a second time.


[Greg's message](https://lists.linuxfoundation.org/pipermail/bitcoin-dev/2017-April/013996.html) contains the following:

    Exploitation of this vulnerability could result in payoff of as much as $100 million USD per year at the time this was written (Assuming at 50% hash-power miner was gaining a 30% power advantage and that mining was otherwise at profit equilibrium). This could have a phenomenal centralizing effect by pushing mining out of profitability for all other participants, and the income from secretly using this optimization could be abused to significantly distort the Bitcoin ecosystem in order to preserve the advantage.

( A practictioner has estimated](https://medium.com/@vcorem/the-real-savings-from-asicboost-to-bitmaintech-ff265c2d305b) that the $100 M figure is off by two orders of magnitude. Jimmy Song [attributes this to three disputes](https://medium.com/@jimmysong/mining-profitability-and-asicboost-ffdb779ef6dd#dbb7) over parameters. )

The more important thing to notice, however, is that the second sentence contains two mutually-exclusive ideas: [1] pushing out competitors, and [2] leeching $100 M (from live competitors) in perpetuity. This is because all miners "compete" against the difficultly level, and miners only *indirectly* against each other. Within a two week period, all the miners are "on the same team". If we if we make the [realistic assumption](http://www.truthcoin.info/blog/mining-threat-equilibrium/#3-2-logistics-ie-info-shipping) of [spy-mining](https://bitcoinmagazine.com/articles/why-bitcoin-mining-pools-aren-t-incentivized-to-broadcast-blocks-quickly-1475249510/), then, within a two-week period, each miner's profitability is 100% independent of what other miners do. It is only *across* multiple two-week periods that they are competitors. And each miner competes not only against other's performance during the preceding two-weeks, but also against *their own* performance (during all previous two-week periods).

In short, if AB actually represented a significant efficiency improvement, then A-Boosting would increase in prevalence until it reached 100%. Either each miner will have voluntarily adopted AB to stay alive, or else they will be involuntarily put out of business by rival A-Boosters. However, by the time that A-Boost has put rivals out of business, the difficulty has already adjusted to **erase** most of the benefits of A-Boost -- and two weeks after the last non-Booster has been eliminated, the difficulty will adjust *again*, and A-Boosters will be exactly where they were before AB was introduced.

### Cases of Sustainable Profits

For sustainable profits, I think two conditions must be met: [1] one miner must have a monopoly on a hashing technology (no one else can use it), AND [2] the monopolist must decide to deliberately under-utilize it.

#### Example 1 -- Ten Miners

For example, imagine that there are 10 miners, and each of these hashes at prices up to and including $0.60 per gigahash per second, which is the equilibrium rate (ie, each gigahash has expected value $0.60, and the cited $0.60 cost includes all relevant economic rents, opportunity costs, etc). Then, a monopolist discovers a new permanently-inimitable tech, such that when his production can reach 1 gigahash per second while only costing him $0.30 per gigahash. If he produces the same number of hashes (during each two week period) as before, his profitability will increase, but network difficulty will stay the same. No rival miners can ever use his inimitable technology, thus, his profitability increases permanently.

However, the monopolist has a strong incentive to ramp up production, as each hash that he can produce at a cost below $0.60 is one which increases his ROI and earns him more money. So he will employ marginally more-expensive sources of electricity, labor, land, etc; and will continue to hash until his marginal cost is $0.60 per hash. Two weeks after he does so, the difficulty will adjust upward, and all of the monopolist's rivals will find that their earnings have decreased. If the rivals were already at the optimal scale (as they would be, in equilibrium), they would all be forced out of business. Eventually the monopolist will take over production, producing more hashes singlehandedly than all ten original miners combined. Eventually, the difficulty adjustments will return his profitability to the typical rate, the same rate it was before the technology was invented.

#### Example 2 -- One Miner

Consider a second situation, where ~100% of the mining is controlled by one person. This omni-miner can choose not only how many hashes *he* produces, but also how many the entire network experiences in any two-week period. The omni-miner can thus trick the network, by giving an appearance that very few people are hashing. He can therefore step-down the difficulty, only produce hashes in cheaper ways, restrict the total number of hashes produced, "sell" the blocks to users at full value, and earn arbitrary profits.

However, this is almost a proof by contradiction. Mining is designed such that anyone can join the mining force at any time. So, in what way can the omni-miner restrict the total number of hashes produced? In practice, I do not think it is possible. Hashing is done anonymously, so there is no way for any miner to credibly commit to only producing a certain number of hashes.

And neither of these two scenarios is specific to ASIC-Boost. The first would apply to any secret hashing technology, and the second applies in all cases of permanent miner-monopoly.

#### The Requirements

The general principle is that sustainable profits will appear, if miners are allowed to slack off. In other words, if miners can operate, *without* being kept in check by rival miners.

The second condition (under-utilization, above) is largely driven by the first condition (inimitable technology). If a technology is imitable, then it will be copied by everyone soon, and so a miner's only advantage in possessing it today, is his ability to make unique use of it for as long as possible. In other words, he must start using it immediately. Therefore, in general, the imitable technologies are utilized quickly and to their fullest extent.

In practice, then, to make sustainable profits with ASIC-Boost, you would need to:

1. Invent ASIC-Boost.
2. Take steps to prevent any "rouge" hashers from ever gaining unmonitored access to the AB tech.
3. Be very confident that no one would independently produce AB or gain access to it in any way.
4. Carefully under-utilize *all* of the ASIC-Boost chips you make, thus making sure that the total set of AB-chips doesn't produce *too* many hashes.

Eh, I just don't buy it.

I mean, supposedly Greg reverse-engineered A-Boost *from a chip they sell to the public*. And it is common knowledge that patents aren't enforced in China. And in Venezuela *mining itself* [is illegal](https://www.washingtonpost.com/news/worldviews/wp/2017/03/10/bitcoin-mining-is-big-business-in-venezuela-but-the-government-wants-to-shut-it-down/?utm_term=.499014c6da45) (with harsh punishments), so you might as well infringe on the patent while you're at it. So how exactly is this grand conspiracy being accomplished? Surely its more likely that the ASIC chip-designers just build-in every efficiency that they can find, as soon as possible. And that everyone is taking advantage of it, one way or another.

I would believe that a tech was sustainably profitable, if we discovered a warehouse full of mining chips that had a never-before seen design. The most persuasive evidence, would be the existence of some kind of mechanism for under-utilizing the chips. I would then assume there were profits, and I would attribute these revenues to a kind of "secrecy [rent](https://en.wikipedia.org/wiki/Economic_rent)".

And, if it later came out that these chips were incompatible with SegWit, then opposition to SegWit might be explained by profits that the chips would no longer create.

### Some Naive Empiricism on the SegWit-ASICBoost-Profitability Relationships

Look at the network hashrate:

![images](/images/hashrate-segwit.png)

If a bunch of chips were about to be *disabled* (by SegWit) on August 24th, it is strange that the hashrate rises so much from that point. August 24th doesn't seem to have made much of a difference.

BitMain's pool supposedly had [25% hashrate in mid-July](https://www.buybitcoinworldwide.com/mining/pools/), and [it has just 20% today](https://www.buybitcoinworldwide.com/mining/pools/). That might indicate that BitMain's profitability has fallen tremendously. But "pool popularity" is quite different from "chip efficiency", making such a comparison very dubious.

BitMain is still in business, still sells chips, and still [advertises them as "the world's most efficient"](https://shop.bitmain.com/antminer_s9_asic_bitcoin_miner.htm). It's not like they suddenly stopped being the market leader after August 24th.



### Conclusion

It has been claimed that AsicBoost results in a sustainable revenue advantage for some miners. However, in Bitcoin Mining, all revenue advantages are ultimately unsustainable.

If everyone's mining speed [hashes per second] doubled tomorrow, we would have 5 minute blocks for a short time (the length of one difficulty adjustment cycle), but thereafter be back exactly where we started. Miners would benefit during the two-week transition period (as faster blocks = ROI arriving earlier), but not at all afterward.

If everyone's mining efficiency [hashes per dollar] doubled tomorrow, then miners would be finding $50,000 blocks at a cost of $25,000. Their **risk-adjusted** ROI would be quite excessive (as the ROI is higher, but the risk is unchanged). They would respond to this by investing more until the total investment (across all miners) had ~doubled. These investments would ~double the global hashes-per-second rate, and we would be in precisely the situation of the preceding paragraph.

The *user* does benefit [slightly] in both cases -- more efficiency yields more hashes, which means that the hashrate security of the network increases. Increases in mining efficiency must always ultimately work *against* miners, and *for* users.
