---
title: The Limits of Blockchain Tech
comments: true
show_author: true
---

> Putting software "on a blockchain" is an inconvenience, justified only in cases involving a global public ledger. These ledger-cases are likely to be limited to Money, Reputation, and Names.  This limitation suggests that other "DACs" are not economically viable, and Ethereum may be "a solution in search of a problem".


Are there really [84 different blockchain-uses](http://ledracapital.com/blog/2014/3/11/bitcoin-series-24-the-mega-master-blockchain-list)? Will "[a thousand chains blossom](http://letstalkbitcoin.com/blockchain-2-0-let-a-thousand-chains-blossom/)?
If [Bitcoin is just the "first DAC"](http://theumlaut.com/2014/01/21/bitcoin-2-0-decentralized-corporations-derivatives-and-information-markets/), then how many DACs will there be? Will there be many distinct [sidechains](http://www.blockstream.com/), or will they be mostly for staging upgrades? How many [Ethereum](https://www.ethereum.org/) contracts will we see in use?

Why would we use blockchains at all?

![Hype](/images/gartner_hype_cycle.png)



## What Blockchains Do
> Blockchain = CryptoSignatures + PoW Clock = "Who owns what, when?"


### The Blockchain Niche

Blockchains can only provide **codeable** services (digital information only, nothing physical). This limitation aside, Blockchains are very **reliable** (software always does the same job, regardless of the time of day, location, or the user's age/race/religion/criminal-record/intentions).

Bitcoin is a perfect example: wealth transfers were **easy to code** (basic arithmetic), and the **marginal reliability** was extreme ({taxes, inflation, bank hours, e-gold} were unreliable in the sense that you were treated worse if you were {high-income, unbanked/unpopular, day-job-employed, e-gold customer}).


### Where Reliability Is Crucial: Owning Assets

Compare the bankruptcy of two different types of business: [1] "money-accepters" (like retailers), and [2] "money-storers" (like banks).

Money-accepters can go bankrupt almost painlessly: Soon a new one will appear to fill the unmet market demand, and you can continue your shopping there (think of Bitcoin's "Silk Road(s)"). If you are extremely unlucky, and happen to be shopping mid-bankruptcy, you might permanently lose some value: that of the single transaction you were mid-conducting.

However, if a bank (money-storer) closes, an entire lifetime of savings can be wiped out permanently. **If** a new bank opened (from where does it get its initial deposits?), users would have to start saving all over again. Money-storage has higher stakes: owners/employees/hackers/lawyers/politicians can target the stored asset for theft, extracting a "ledger [rent](https://en.wikipedia.org/wiki/Economic_rent)". The damage is permanent, and the pain excruciating.

![Storers](/images/bitcoin_gone.jpg)



The story isn't limited to bankruptcy (it is simply easier to use this extreme to see the difference between accepters and storers). Instead, imagine each type did *anything* you don't like. With money-accepters (retailers) you can take your business elsewhere.  For money-storers, if you've already deposited you are screwed. All you ever owned was a promise to be repaid: the usefulness of that promise is *defined* by its reliability.




### Storage and Retrieval

The "ownership" concept implies [certain](http://en.wikipedia.org/wiki/Excludability) [requirements](http://en.wikipedia.org/wiki/Rivalry_%28economics%29) (one can't "own" the fresh, outdoor air). Blockchain tech (an uncensorable database and a distributed timestamp server) enabled digital assets to meet these requirements. However, **the assets themselves are still digital**: while it may one day be possible to buy a "smart property" car using only the Bitcoin blockchain, **the value of the car will not be protected from a sledgehammer** in the same way that each Bitcoin *is* protected (from a sledgehammer) by the blockchain.


![SmartProperty](/images/dumb_property.png)




## Ledgers: Dimensions of Programmable Value
> Normally, "what other people own" doesn't affect "what you own". So far, the rare exceptions are: Money, Status, and Names.



### Money / Finance (Bitcoin)

Raw value-storage? Bitcoin.  Stocks/Bonds/"Wall St."? Colored Bitcoins. And more besides: we have multisig, nLockTime, and sequence numbers, which greatly enhance the user's security and transfer experience. When [Andreas Antonopoulos says that "currency is just the first app", he means apps involving the Bitcoin protocol](http://www.activistpost.com/2014/01/andreas-antonopoulos-bitcoin-will-cause.html), not new blockchain-apps/protocols.

Bitcoin is **only** weak on **purposefully storing** value (it only describes where value is currently stored). Those businesses which store customer's Bitcoin (namely exchanges and betting sites) routinely lose or steal those funds. Bitcoin is P2P money: it was not designed for *someone else* to control your money. It was designed for *you* to control your money.



### Status / Reputation / Expertise / Branding (Truthcoin's "Votecoins")

Purposeful value-storage is what I created Truthcoin to address: it has blockchain rules which store up Bitcoin and conditionally pay it out...a prediction marketplace containing a trustless outcome-resolution service (ie, an escrow running entirely on greed and not on second-order abstractions such as 'honesty').

To do this, Truthcoin had to add a new *dimension of ownership* to the blockchain: that of 'reputation' (the Votecoins). Some individuals may have greater subject-matter expertise than others: *when groups disagree* it is best to weight individual opinions according to their relative expertise. We must divide our limited attention span, and consider only the most-relevant knowledge-sources. Correspondingly, status is a zero-sum game: if you're on top, [you lose when others do well](http://www.youtube.com/v/NlpxjBgG-7E?start=420&end=500&version=3&autoplay=1), and if you're below, you benefit from the misfortune of others.

![NewtIntrade](/images/newt_small.png)


### Identities / Names (Namecoin)


I searched for other zero-sum, 'necessarily-scarce assets', but I could only find one other: Names (you can't have someone taking yours, for example). [The case for digially-scarce names](http://www.aaronsw.com/weblog/squarezooko) already [been made](https://bitcointalk.org/index.php?topic=1790.222), but, more importantly, [the name-software itself has already been developed](http://namecoin.info/)! 



## The DAC Delusions
> Some people want to "decentralize all the things", not realizing that most of them are already decentralized.


Many have made the following mistakes:

### #1 Forgetting that Our Economy Is Already Decentralized


With Bitcoin and an internet connection, anyone can start a business selling anything. This takes an already-decentralized economy, and turns the decentralization up to 11. Some services require customers to escrow their Bitcoin, which may require the creative use of multisig, reputation, insurance, fidelity bonds, etc. Finally, there are business arrangements which are impossible without a trustless escrow. These (few) services can use Truthcoin (and tap the reputation dimension of ownership).

Unless you've come across another "dimension of digital scarcity" (see above), blockchains aren't worth your effort! **Just start a normal business instead!** You can flexibly adjust your prices and service offerings as you, the manager and entrepreneur, see fit! .

![SilkRoad](/images/silk-road.jpg)

(Note that there have been many SilkRoad businesses *using Bitcoin* but no SilkRoad DACs *using the blockchain*...coding the required functionality would take too much work).

Some things aren't codeable, and "reliability" can be very constraining (you'll want to treat some customers differently from others). Software bugs, miner attacks...these can crash blockchains permanently! Put those skills toward writing a great piece of software (which you sell for Bitcoin)

Which brings me to...


### #2 Confusing "DACs" with "Software"

When I claim that that the blockchain is an inefficient model, I am not claiming that software is an inefficient model.

Our world contains several "software businesses". Google / Facebook run operations in almost the same way that Bitcoin does: a group of programmers meeting to collaborate on software. New software might be sold for Bitcoin, or used to build a business which earns Bitcoin. However, that "the tech will improve" doesn't change the **relative** disadvantages a blockchain has over a firm.

Take Storj, for example. With the tech tools we already have, anyone can already sell or rent their spare hard-drive space. Obviously, new software can help coordinate buyers, sellers, payments, and terms, but this software does not have to use a blockchain, it only needs to use Bitcoin the currency.

The freedom to manage can be very helpful, but a business can remove these freedoms as required (consider the zero-knowledge backup service SpiderOak, who's employees cannot read user's files). The same goes for transparency (think provably-fair online gambling sites), and even for decentralization (think [Bitmessage](https://bitmessage.org/wiki/Main_Page), or [Bittorrent](http://www.bittorrent.com/), which are completely decentralized but have no need for a distributed clock). These are purely software/tech improvements. No blockchain required. 


### #3 Ignoring Software Rot


![SoftwareRot](/images/bit-rot.jpg)

Software development and maintenance requires a great deal of highly-skilled work. On top of that, post-development you still have all your work ahead of you, because [software "rots"](http://en.wikipedia.org/wiki/Software_rot) as it gradually becomes obsolete. Bitcoin is supported by users in forums, in lieu of salesmen/customer-service-reps. The work is done by volunteers, but it still requires effort. Generally, open source software projects can thrive on community-autopilot, but they are also regularly abandoned (and many Bitcoin-projects have already achieved vaporware status). Bitcoin's unique status as money not only incentivizes development/maintenance but also co-opts money's-status-as-a-network-effect to onboard and coordinate programmers.

It may be difficult for programmers to believe (or accept), but **software is long-run inefficient**. An entrepreneur can easily copy a DAC, especially an open source one, with a website and some free time. The reverse, a DAC replicating even a simple business model, is a monumental project. Ethereum is a perfect example of this: anyone can start "Ethereum.com", collect and run contracts, and then manually authorize payments to beneficiaries. Blockchain-Ethereum has taken months of highly-skilled effort. Is Blockchain-Ethereum worth the wait? That depends on the codeability-reliability tradeoff (for a start).

But even with Ethereum built and fully-functional, *each contract* would require extensive development, be adamantly inflexible, and suffer software rot. With all labor likely unpaid...why do this? Just start a website and become an entrepreneur!



## Conclusion


The Bitcoin Blockchain was invented 6 years ago. Since then, Bitcoin has been used by thousands of thriving **firms**, but no **DACs** yet exist (with the possible exception of the very first alt-chain, Namecoin). In general, the Blockchain has only been used for one other useful project (Namecoin), and my own project (Truthcoin) might be the third and last. While more Bitcoin-accepters (and even Bitcoin-business) are planned each day, **even the [Ethereum](https://forum.ethereum.org/categories/services-and-decentralized-applications) [forum](https://forum.ethereum.org/categories/projects) doesn't have a single concrete plan for an on-Blockchain business ("DAC")** (in fact, I could not find any concrete plan for any [final good](http://en.wikipedia.org/wiki/Final_good) at all...point them out in the comments if you find them).

Although this essay concerns the "why" of blockchains, it does not concern the "how". New blockchain-engineering can certainly *provide a better way* of managing money, status, and names. On that we will likely still see tremendous innovation.

Update: A previous version of this essay included Bitmessage as a "useful blockchain project", until a reader pointed out [via tweet](https://twitter.com/roasbeef/status/538944309790539776) that Bitmessage does not use a blockchain. (Which makes perfect sense, as "other people's messages" don't affect "your messages"). I was allowing Namecoin and Bitmessage to share the 'Name' concept, even though BM is actually designed to use NMC for identities. This version has been edited to clarify that Namecoin is the useful blockchain project, not Bitmessage.



