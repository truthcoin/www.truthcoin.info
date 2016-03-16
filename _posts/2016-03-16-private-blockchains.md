---
title: Private Blockchains, Demystified
comments: true
---

> Blockchains are specifically designed to obviate private firms. Industry refusal to acknowledge this point has resulted in multiple misunderstandings, which have persisted for a variety of reasons.  



Let's get this party started!

![private-blockchains](/images/private-blockchains.png)

FYI, today's post is something of a sequel to [this shorter one from 2014](http://www.truthcoin.info/blog/limits-of-blockchain/).

## Blockchains Compete with Firms
> The *absence of a firm* was Satoshi's whole design goal.

Satoshi had to *replace* many of today's institutions with *inferior* virtual-only substitutes. 

### The Blockchain is [C2C](https://en.wikipedia.org/wiki/Customer_to_customer)

The idea of a "Blockchain Company" is a walking contradiction. It's like [YellowPages.com](http://www.yellowpages.com/), or the [New York Times](http://finance.yahoo.com/echarts?s=NYT+Interactive#symbol=NYT;range=my) Twitter.

The whole point of "Blockchain" is that you *don't need* a business. You can do everything yourself. 100% [disintermediation](http://www.truthcoin.info/blog/scaling-security/#agency).


![blockchain-vs-firm](/images/blockchain-vs-firm.png)

Above: a tale of two GUI Windows -- one Bitcoin-Qt, and the other a web browser pointed at an online bank. Each window does, basically, the same thing.

Those individuals who spent their time "working on blockchain" are either Bitcoin developers or academic researchers.

Everyone else is "working on *using* the [Bitcoin] blockchain". Usually, this takes the form of [fiddling with software to create](http://www.coindesk.com/meet-adam-draper-man-behind-100-bitcoin-startups/) interesting [Bitcoin URIs](https://github.com/bitcoin/bips/blob/master/bip-0021.mediawiki). Much in the way that Uber does not build "cell phone technology", these companies do not "build" blockchain technology.

This is especially true of the exchanges (and exchange-equivalents: purse.io, Gyft, BitPay, ...). These are blockchain-**users**, in addition to being half-money-transmitters.

### Mining Competes with Identities

The idea of "Know Your Miner (KYM)" / "Mining as a Service (MaaS)" is also a contradiction.

Any digital signature, from any **known** *anyone*, is more secure than *any* quantity of "mining"; mining is categorically weaker than [signatures](https://en.wikipedia.org/wiki/Public-key_cryptography).

So why would a system jump to signature-land, and *then retreat* to mining? It would be redundant and inferior. 

It's like hailing a cab, and asking the driver if he can order you an Uber. It's like a smartphone app which contracts someone to use a typerwriter to transcribe-and-mail your e-mails.

Some businessmen believe that they "don't need mining". They're right, because...

### Proof-of-Work Competes with Courts/Police

Databases sometimes have trouble syncing up.

If two database-states each claim to be the latest, "proof-of-work" **resolves the dispute** over which state is allowed to continue forward in time.

Virtually, at least.

Over in the physical world, disputes are resolved by police officers, lawyers, and judges (or, more routinely, the [credible *threat* of a guilty verdict](http://www.truthcoin.info/blog/contracts-oracles-sidechains/#self-enforcing-contracts)). It's slow, expensive, and imperfect.

Can technology can offer an improvement?

[Only for phenomena which are entirely virtual](http://www.truthcoin.info/blog/contracts-oracles-sidechains/#a-fundamental-limitation-cryptolaw-without-cryptopolicehttpswwwyoutubecomvhimyee1fa8start1223end1290version3autoplay1). Blockchains have only the power to alter the numbers displayed on a computer screen -- that isn't much, when compared to a court order enforced by men with guns.

Let's examine *all* of the differences between the two dispute-resolution processes:

|Courts/Police|Proof-of-Work|
|----------------|------------------|
|Nation-specific.|Global / without-location.|
|Requires identification of guilty parties.|Anonymous.|
|Outcome is interpretable to humans, but not computers.|Outcome is readily interpretable to computer.|

Two of those three differences vanish, when [the blockchain has a mailing address](https://twitter.com/derosetech/status/639166667797491712). The third difference is irrelevant to a [command firm](http://www.slate.com/blogs/moneybox/2013/09/03/ronald_coase_s_theory_of_the_firm.html) with a CTO / IT Department.


## Four Central Misunderstandings

### 1. The Definition of a Blockchain

Charlatans are trying to mislead you, and trick you into giving them money. Use knowledge to protect yourself from fraud!

#### From the Horse's Mouth 

Satoshi gives the definition as: **a set of blocks satisfying the proof-of-work requirements**.

![blk-def](/images/blockchain-definition.png)

From the original [main.h file](https://github.com/bitcoin/bitcoin/blob/8dca7864f793072701f810e4c5ea12a6e1087085/main.h#L806-L816) of [the first Bitcoin release](https://bitcointalk.org/index.php?topic=68121.10;wap2/).

In other words, a database with a "cumulative [hash](/images/hash-explain.txt)".

Satoshi's protocol is laid out very clearly:

1. The **block** with the "highest ID number" wins (ie, "gets added to the chain").
2. The **chain** with the highest sum of block-IDs wins (ie, "is the one which appears on the user's computer display").

![blk-def-cumul](/images/cumul-hash.png)



#### Re-derived from Scratch

The word "block" refers to data blocks, ie 'collations of data'. Obviously.

The word "chain" has two obvious meanings. First, "chain" describes the data structure -- that each block refers ([somehow](https://en.wikipedia.org/wiki/Cryptographic_hash_function#Verifying_the_integrity_of_files_or_messages)) to precisely one earlier block, such that, if laid out visually, the blocks would resemble a chain.

![chain-of-blocks](/images/chain-of-blocks.png)

Secondly, a "chain" also refers to "something which restricts". As defined in the white paper and code, the proof-of-work is the slow forging of each "binding" link in the chain.

( Unlike a regular chain, which is only as strong as its weakest link, Satoshi's chain is as strong as the *sum* of its links. It gets cumulatively stronger over time [hence the "cumulative hash", above]. )

#### More Details

Satoshi's term "block chain" is admirable in its clarity. Through the use of [barely supra-Kindergarten English words](/images/block-vocab.png), it conveyed quite a complex topic.

How *flexible* is this definition? Is proof-of-work *required* for a blockchain?

Like all good definitions, it is 0% flexible. Proof of work *is* required.

To see why, ask yourself older-than-kindergarten "adult questions", like:

* Where do these blocks come from? What are they made of?

( After all, the 'Eastern **Bloc**' was made *of* Soviet Countries, and a 'city **block**' is made *of* land/buildings/addresses. )

In a computer network, the obvious answer *must be* "digital messages".

Now, here's something a real "critical thinker" would ask:

* Why are there blocks at all?

After all, each of Satoshi's blocks contains a redundant list of exactly those transactions which were *already broadcast*, to every member of the network. Why do it twice? Why so much extra overhead (identifiers, timestamps, block-size,...)?

Well, the **only** difference between [1] a discretized "block" of updates and [2] realtime ("per-message") updating, is **a longer "time between database state-changes"**.

So, all blockchains must have a lot of time in between state changes. Instead of changing with each message, the state idles for a while and then spasmodically lurches forward.

How does "time between state changes" contribute to "anything we care about"? There [is an answer](https://en.wikipedia.org/wiki/Byzantine_fault_tolerance), but we won't go into it. Instead, notice that **there's only one known way** to **objectively** lengthen the "time between state changes". It is called HashCash, known today as "proof of work".

Blockchain = cumulative proof-of-work = cumulative hash.

Quod erat demonstrandum.


### 2. Private Blockchain vs. Database

[Some](http://www.coindesk.com/four-boring-predictions-for-private-blockchains-in-2016/) [have](http://startupmanagement.org/2014/12/27/the-blockchain-is-the-new-database-get-ready-to-rewrite-everything/) [claimed](https://www.youtube.com/watch?v=ycMCGBuDJLQ) that "Blockchain" is "nothing [much more](https://www.youtube.com/v/c9CjWz2N5Hs&version=3&start=2500&end=2620&autoplay=1) than a database".

That's wrong.

If someone makes such a claim, ask them these questions:

* If a blockchain is 'just a database', why was 'the blockchain' invented *over 50 years* after ['the database' was invented](http://quickbase.intuit.com/articles/timeline-of-database-history)? [What's new](https://www.youtube.com/v/c9CjWz2N5Hs&version=3&start=2030&end=2130&autoplay=1)?
* Why do all cryptocurrencies (100% of production-grade 'blockchain' software) *construct their own internal database* (Bitcoin [uses LevelDB](https://en.bitcoin.it/wiki/Bitcoin_Core_0.11_(ch_2%29:_Data_Storage))?
* Why doesn't Bitcoin just leave the data sequence as "LevelDB", and broadcast data-updates in LevelDB format?


A blockchain *uses* a database, but so does almost every computer-thing.

A protocol is more than the medium in which it is stored. The game of Chess "needs" a chessboard to "store" its "game state". But *Chess is more than the board*; the board merely *assists* human brains in the computation and enforcement of the game's rules. iPhone Chess can replace the board.

Chess, the protocol (not the board), is a mutually-agreed ceremony of **rules**. If one player insists on breaking those rules (making illegal moves, or upending the board and storming off) it doesn't matter.  *Everyone* who knows Chess' (pre-defined) rules, also knows exactly what to ignore. 

Similarly, **blockchains filter messages for rule-compliance**. They are only useful if the "rules" are chosen wisely.

So far, only Satoshi has invented a game that's actually fun to play.



### 3. Why Blockchains are Efficient

In one image:

![blk-eff](/images/blockchain-efficiency.png)

Applied to Bitcoin: banks overwhelmingly [believe that 'Bitcoin's blockchain' is an *IT improvement* (ie, an improvement in mankind's use of IT)](https://www.youtube.com/v/Vcq0_h1_J30&version=3&start=44&end=79&autoplay=1), when it is instead, clearly, a *banking improvement*.

IT improvements are things like "the CD-ROM" or "copper wiring". The Bitcoin doesn't do anything new, database-wise.

In fact, as we will see, its database technology is deliberately slow and cumbersome.


### 4. Why Blockchains Are So Cumbersome

No one chooses to mine.


#### Teleportation Metaphor

Imagine a Magical Kingdom where anyone can teleport anywhere. However, if you remain in the same place for too long, then you are frozen in time, forever.

Things are pretty awesome in this world. However, because [1] people need to teleport constantly, and [2] because they often live very far from each other (owing to the instant travel-times), there are occasional communication problems. 

#### Teleportation is Pretty Awesome if You Know Where to Go

Normally, when people want to meet, they use cell phones to agree on the location.

#### Lost in the Infinite Void of State

How do people find each other, without using Cell Phones?

Well, they play "the rock game".

1. First, they teleport to the Genesis Rock (taught to all children, famously located on the planet of mud-and-boulders).
2. Then, they look around for any 'trench-arrows' which lead away from the Genesis Rock.
3. They follow that trench until it interests with another rock.
4. Once at a new rock, they climb on top of it, and look around for more trench-arrows that point to *this boulder* that you are on.
5. Repeat steps 3-4, until you meet up with everyone else. Find your group, and once you've met up you can teleport somewhere together.
6. If they ever reach a point where there are no trench-arrows around, they immediately start digging a new trench-arrow which points to the last boulder they were on.
7. Remember to constantly retrace all of your steps to look for more trenches that might have appeared. If there are two (or more) trenches pointing away from any given boulder, ignore all but the longest trench.


Meeting like this is inconvenient.

If someone new wants to finish the game, or if an existing member gets lost and needs to start over, they can be wandering for days! The group, painfully aware of this inconvenience, tries to help stragglers/newbs, as best they can, by digging at a sluggish pace of just 3-7 earth-heaves per second.

Why don't they just leave a chalkboard at the Genesis Rock, and write the latest coordinates there?

Well, it would introduce a single point of failure to the process. Anyone could vandalize the chalkboard, or capture it (in order to extort the poor lost people). If gives the process a "head" that can be cut off...an "Achilles Heel".

![decent-prin](/images/satoshi-principle.png)




## Why No One Told You
> In Blockchain, thought leadership spreads peer-to-peer. Anarchist programmers aren't "peers" with bankers or consultants.

It seems hard to believe, that [so *many* "experts" could have invested into  an ultimately-doomed idea](https://en.wikipedia.org/wiki/Subprime_lending#Subprime_crisis). How do we explain this?

Why does information about "Blockchain Technology Best Practices" spread so slowly? I mean, it's been *over 7 years*!

The signal *is* out there (as the sheer quantity of Youtube-recorded meetups and conferences can attest) but it is buried in noise. Why is that happening?


### 1. Bitcoin has no press agent.

Bitcoin, the system, has no "owner". Only individuals own Bitcoins -- thus, the benefits to 'general Bitcoin promotion' are diffuse. In contrast, Preston J Byrne or Blythe Masters is promoting *their* company -- the benefits are *concentrated*.


Truly "great ideas" are impossible to invest in. For example: "free speech", "evolution by natural selection", "free markets",  and "nullius in verba". These ideas are so good, that they work for free. No one can own them, implying a tragedy of the commons problem.

![podium](/images/btc-podium.png)

Similarly, while "good idea" diet books and (insidiously calibriated) gym memberships rake in fortunes, the "great idea" is free: eat whatever you want, fast occasionally, and walk 6-10 hours a day. Throw in some pull-ups (we are apes, after all) and sit ups, and/or carry heavy stuff around [while you walk or stand](http://www.artofmanliness.com/2014/09/05/why-barbells-are-better-than-machines/).



### 2. In fact, these people are through talking with you.


Many Bitcoiners distrust large banks, large corporations in general and large governments.

Being skilled in cryptography, they tend to be obsessed with privacy, and over-cautious when it comes to questions of "who knows what".

Many of them feel that -by sharing their expertise- they will be *accused* of sitting on fat pile of untraceable e-cash, and then threatened or extorted or audited or worse.

Finally, recognizing that [Satoshi's purpose is incompatible with the purpose of large banks](http://network-economies.com/mike-hearn-failure-bitcoinxt-r3cev/), any knowledgeable Bitcoiner would feel uncomfortable talking to bankers...out of sheer *politeness*. Meeting with banks would be analogous to meeting their wife's ex-boyfriends.



### 3. The "Maximalist" Red Herring

Unfortunately, there's a strong element of overlap between "knowledgeable about the space" and "conflict of interest in the promotion of Bitcoin". This overlap tempts "blockchain-newbies" to write off the "blockchain-experts" as biased.

![btc-dog](/images/btc-dogfood.png)


Hence, Blockchain scammers can protect themselves against a simple fact -- that the people who have been working on Blockchain the longest (the Bitcoin developers) have already explored all of the good ideas -- by accusing their expert critics as "biased" or "self-interested". The truth is the reverse.

The reality, in this case, is simple: 

1. People learn about blockchain technology, and then...
2. ...they [purchase Bitcoin](btc-dogfood) and become Bitcoin advocates.

As previously mentioned, once these people *become* Intelligent Bitcoiners, they don't feel the need to correct this ongoing misinterpretation.

Secondly, there is an ongoing misunderstanding over the technical features of "proof-of-work network effects". Simply: [it is both (1) most secure and (2) most inexpensive for all chains to be on one proof-of-work system](http://www.truthcoin.info/blog/one-chain/#merged-mining). Anyone can "plug in" to Bitcoin for free, even if they don't use BTC the currency. Ignorant people hear this technical claim, and mistake it for some kind of 'arbitrary obsession' with Bitcoin.


### 4. Hypocrisy Powers the World

#### Those Employees Aren't Going to Fire Themselves

The Catcher in the Rye, by J.D. Salinger, is now old enough to retire. But its message, of childhood naviety, gasping for air, as it drowns alone in the merciless ocean that is our omni-dissapointing reality, is timeless.

In other words, those engineers [I just mentioned as "not understanding the deal they were turning down"](http://www.truthcoin.info/blog/one-chain/#conclusion), well, they probably either *do* understand the deal, or they just never cared enough in the first place.

They just have no reason to open their mouths! Explain that your boss' ideas are bad! Explain that the project is pointless, and [that you aren't really necessary](http://www.30rockquotes.net/seasons/Season_5/30rockquotes_the_fabian_strategy.cfm?highlight=189#line185)?! Dear me, that isn't done! Not by any Truly Intelligent Employee.

And, with something complex like Blockchains, only the TIEs will probably know the game they're playing. If they speak up, their days of getting paid to surf the Bitcoin-internet will be over. ( Sorry, guys! )

#### Plausible Deniability

The elevation of the "lie" to Team Sport, is where the magic really gets going. Together, a lie can be sustained for longer and at greater scales.

When this scheme falls apart, executives can say (with some justification) that "they were misinformed" or ["no one saw it coming"](http://www.uclm.es/actividades/2009/workshopESHET-UCLM/Bezemer_-_No_one_show_this_comming.pdf).

Engineers / specialists can say that they were ["just following orders"](http://rationalwiki.org/wiki/Nuremberg_defense). Moreover, they own no equity and can (and probably will) jump ship at the appropriate moment.

Thus, the two can collectively shirk off the blame, where one could not.

It works for everyone, except the investor.

( But, you know, if the investor is really rich, and only wants to impress his investor-friends at cocktail parties..."blockchain startups are all the rage, this year"...then it even works for him. )

### 5. Tactical Blockchain [Juke](https://en.wikipedia.org/wiki/Juke_%28football_move%29)

People don't always say what they mean.

#### Blockchain As Signaling

Paradoxically [useless investments can be useful](http://www.kenosha.org/wp-museumstore/wp-content/uploads/2015/12/KPM_peacock.jpg), because [only the most successfully-resourced can afford to waste resources](http://www.dailymail.co.uk/tvshowbiz/article-2376311/Kanye-West-Kim-Kardashian-flush-nearly-1-million-gold-plated-toilets-new-Bel-Air-mansion.html). 

Consider the chimerical [Hounduras-Factom Land Deal](http://www.coindesk.com/factom-land-registry-deal-honduran-government/), the nosedeaf Microsoft-Azure ["Blockchain as a Service"](https://azure.microsoft.com/en-us/blog/azure-blockchain-as-a-service-update/), and/or [whatever this is](https://bitcoinmagazine.com/articles/ukraine-government-plans-to-trial-ethereum-blockchain-based-election-platform-1455641691).

Such Potemkin Projects serve two purposes. First, and foremost, they allow decision-makers to make an impressive display of "caring about technology / transparency / progress / tech-trendiness / efficiency". Secondly, they provide a vehicle for measuring and conveying loyalties.

Even *assuming* that efficiency-gains exist, these decision-makers will be long gone (promoted, probably) by the time improvements are realized.

( The cleverest people of all, are *very* willing to invest in a project with no benefits, especially if [they are spending "other people's money"](https://en.wikipedia.org/wiki/Agency_cost#Agency_costs_in_corporate_governance). )

Last, but not least: a pervasive phenomenon, of which we can only discuss a little.

#### Blockchain as an Excuse (BaaE)

Often, it is the case that *everyone* in an organization will *know* that something needs to be done.

For example:

* "We need to update our wire transfer software...it's like 20 years old! You can overnight a box of cash to someone faster than this!"

However, despite a clear need, the change goes un-made.

Why? Well, most large organizations have internal political structures which resist change. Thus, the organization is trapped, often freed only by some salient event ("arrival of competitors"), or [the hiring of outside consultants](http://www.overcomingbias.com/2012/01/why-so-much-consulting.html) to call a spade a spade. Finally, the problem becomes un-ignoreable, and action is galvanized.

So, "blockchain" might just be a clever *excuse*, to start *getting other things done*. It might not have anything to do with Satoshi Nakamoto or Bitcoin at all. Call it **"blockchain without blockchain"**, but if it helped to "get things done" it would still be helpful for organizations to form "blockchain committees" and "blockchain roadmaps" for arbitrary database or IT projects.


## A Superior Alternative

As part of this evidence against private blockchains, I have constructed a classier version which I call "The Peer Database". Much more impressively, I have tried to document the possible use-cases of such a database.

It appears in [tomorrow's blog post](http://www.truthcoin.info/blog/peer-database/).

But, I wouldn't get your hopes up. That we, the most [experienced](https://bitcointalk.org/index.php?topic=1860.0) and [successful](https://coinmarketcap.com/) Blockchain Engineers in all of history, might all have discovered some way to [raise millions of dollars and start our own company](https://digitalasset.com/press/digital-asset-closes-funding-exceeding-50-million.html)...and *passed* on it, is rather unlikely.


## Conclusion

Typically, groundbreaking work is done in the open source / academic communities. Then, that work is "commercialized" by industry.

As we have seen, Blockchains are a rare exception to this rule. Lacking an identity, they are everyone and they are no one. This makes them inherently public.

Innovators and entrepreneurs would do better to follow the example of The Internet, and work toward making this public resource more accessible to consumers.

...and, stop dropping the "the". It [makes you look ridiculous](https://www.youtube.com/watch?v=UlJku_CSyNg&feature=youtu.be&t=48s). 


### Kudos

Kudos to [Chris DeRose](http://www.americanbanker.com/bankthink/private-distributed-ledgers-miss-the-point-of-a-blockchain-1077435-1.html) and [Josh Unseth](https://www.reddit.com/r/bitcoinarchy), as well as [Marc Andreessen](https://twitter.com/pmarca/status/691407998107815936) and countless others, for trying to generate and popularize these ideas.