---
title: Sidechains for Privacy -- zSide and Melt/Cast
show_author: true
comments: true
date: 2021-2-5 05:00:00
---

## 1. Intro

    Thou shalt not covet.
    -Old Testament

### A. Motivation

![images](/images/dnm-monero-only.png)

Above: A [story](https://thecryptobasic.com/2020/12/31/darknet-marketplace-now-accepts-monero-only-not-bitcoin/) about a darknet market switching away from Bitcoin, towards a coin with greater privacy technology. Is this something the marketplace really wants? We have no way of knowing for sure, but why should Bitcoin take the risk!?

### B. ZCash Sidechain to Help Bitcoiners

**"zSide"** is what I call *the Altcoin "zCash" adopted as a BTC Sidechain*. It helps Bitcoiners in three ways:

1. Fully anonymous z-to-z **"Private Transactions"**.
2. *Non-interactive* de-tainting of coins, which I call **"Melt/Cast"**.
3. Private fusion of small UTXOs into larger ones (also Melt/Cast).


![image](/images/zside-screenshot.jpg)

Above: screenshot of the [next version](https://www.drivechain.info/releases/index.html) of zSide (work in progress!).


## 2. Existing Privacy Tech

### A. Deniability's Ever-Shrinking UTXOs

[Deniability](https://www.truthcoin.info/blog/deniability/) is still **the** best privacy tool in Bitcoin.

(No one believes me when I say this, but I have decided that I am OK with that.) 

However, Deniability requires that your UTXOs get split into ever smaller and smaller pieces -- there is no way to Fuse your small UTXOs into a large one -- This is a BIG problem, because at the very least you must fuse some UTXOs together at the time of purchase (when they are all common inputs to one single txn). In other words, you really, really prefer to spend as few UTXOs as possible per purchase (ideally just one), since they will become publicly linked at that time. But this means you need to make sure they are the right size -- they can't shrink forever as they do with Deniability.

### B. The Perils of Interactivity

*Interactive* protocols require you interact with someone else on the internet.

To me, this is a pretty big drawback. Adversaries can (and do) watch the internet to see who is messaging who. Even if the messages are encrypted, observers can still learn a lot just from the timing of messages.

A more fundamental problem is that, with an *interactive* protocol, the person you are interacting with might BE your adversary!

For example, perhaps you are a follower of Matt Odell, and you want to try to use Whirlpool to do a 5-in-5-out CoinJoin. To do this, you will have to interact with Whirlpool's servers, as well as 4 other strangers, and then broadcast a CoinJoin txn. It is possible that an adversary, just by watching the timing of messages entering and leaving each computer, will learn that this CoinJoin belongs to you. They may be able to get the IP Address (ie physical location) of your computer (and the other 4 participants) just from timing analysis. It is also possible that the adversary *is* the Whirlpool server (or is emulating one), or it is possible that the adversary is all four of the other people you are "mixing" with. Now you are paying the adversary, to use "their mixing service", which in reality is mixing nothing at all.


### C. PayJoin - Doxxing a Merchant

[PayJoin](https://en.bitcoin.it/wiki/PayJoin) ie, a txn where the *merchant* contributes at least one input. The user's txn fee rises a shade, but in return both parties get greater privacy and better UTXO-management[^1]. When a critical mass of payments are done via PayJoin, PayJoins will lose their suspicious quality. (Also, PayJoin is philosophically a step in the right direction -- emphasizing *interpretations* of the blockchain, over mathematical scrambling of numbers.)

[^1]: The merchant in particular avoids having to "fuse" the UTXOs they get from customers. Micro-economically speaking, the cost of dust-UTXO-cleanup is one that merchants would have to pass on to consumers anyway, so it is efficient and direct, for merchants to force customers to pay them via PayJoin.

One disadvantage of PayJoin is that the merchant can be insta-doxxed, for free (the attacker merely offers to buy something from them). With this doxxed UTXO in hand, the attacker can now watch the downward stream of txns from that UTXO, and guess which of these are PayJoins. (If the guesses are accurate, the privacy is completely defeated.) The attacker can use other intel on the merchant (ie: estimated sales figures, prices of various goods, how much the merchant pays to which suppliers and when, etc) to make better guesses.

(And of course, if the merchant cannot defend against this, by hiding their coins in many UTXOs -- the attacker can repeat this process many times, until all of the merchant's UTXOs are doxxed.)

PayJoin also happens to be interactive (you cannot do it unilaterally, you need someone else [in this case, the merchant] to cooperate with you to make the txn). Whenever interaction is required, game theory enters the picture, and so the analysis becomes very complex -- interactive techniques are "flaky"! Instead, our toolkit needs a non-interactive de-taint technique -- a technique which the user can do all by themselves at home.

Nonetheless, PayJoin is a great idea. Merchants and buyers should enthusiastically use it, in situations where both parties really believe that the customer intends to make a purchase (and is not just doxxing the merchant's UTXOs).


### D. Drawbacks of z-to-z "Private Transactions"

Super-secretive people will probably enjoy sending secret transactions back and forth to each other on the zCash sidechain. And that's a good thing. Again -- it has its place in the toolbox (probably, in this case: when both parties know that they are doing something ...unpopular, see [here](https://bitcoinmagazine.com/articles/darknet-markets-cant-live-with-or-without-bitcoin).

However, z-transactions have two big drawbacks (in comparison to regular Bitcoin txns):

1. They are more suspicious to use (because they are more resource-intensive, and the only benefit is privacy; and because they Mask instead of Blend, see next section). Therefore, a reasonable merchant/taxpayer would shun them, so as to keep themselves cast in the best possible light.
2. The "assay cost" of shielded coins is much higher -- ie, it is harder for their owner to be sure that they *truly do possess* a z-address coin. (Their immense cryptographic secrecy, impinges on self-sovereignty[^2].)

[^2]: Self-sovereignty is an all-important Bitcoin virtue. In Bitcoin, there is no "customer service" number that users can call for help. Users are responsible for their coins -- responsible for storing their coins safely, sending them off to the right destination, and checking to make sure that coins they receive are real. When coins are in a normal blockchain, you can compare what is reported by your node, to a public blockexplorer. (This can compromise your privacy, of course, if you don't adopt Bloom Filters or a policy of continuously checking many addresses at random throughout the day.) But the mere fact that it is possible, adds a lot of transparency to the banking process. It gives Bitcoin legitimacy. Everyone can see that is working.

In the zCash z-to-z world, all of the coins are interchangeable and unlinkable. This is great for privacy, but I can imagine *most people* feeling uncomfortable with the idea of storing large amounts of money in the z-to-z shielded pools, for long periods of time.

Instead, I guess that there is a different way of making use of z-address, on a *temporarily* and "as needed" basis. I will discuss it in Part 3.


## 2. Digression: The Social Nature of Privacy, Masking vs Blending

This section is philosophical and can be skipped.

### A. Prefer Not to Answer

Observe the paradox of the following survey question:

![image](/images/prefer-not-to-answer.png)

Above: The "prefer not to answer" choice is **not** meta-private. From [here](https://esmemes.com/i/question-1-of-3-or-fewer-have-you-ever-searched-19679256
).

It highlights an important problem with privacy: to achieve True Privacy, the privacy-seekers must be able to say, loudly and credibly, that they don't want privacy. But nonetheless, somehow, everyone needs to ignore them.

Why would privacy-advocates *say* that they want **less** privacy? The answer is simple: if people truly are under duress (and need privacy), then most of them will hasten to submit to the tyrant (so as to evade his wrath). And the tyrant will be throwing out hackneyed platitudes such as "if you have nothing to hide, you have nothing to fear", etc.

### B. Definitions

For something to be truly private, **the Freedom-Fighters must resemble the Slave-Loyalists** in every way. To accomplish this, one needs "meta-privacy": privacy about whether or not someone is *using* a certain privacy technique.

I can now define the terms precisely:

**Masking** (the lame version) is when you *openly* conceal something. For example:

* Wearing a ski mask to hide your face indoors.
* Checking a box which reads "prefer not to answer", on a survey question.
* Running a business where you accept only z2z "private transactions" because "privacy is important to us".
* Running a Matt Odell-style blog that is explicitly "about privacy".

**Blending** (the cool version) is when you conceal something *whilst revealing as much of your private information as other people do* (ie, while "blending in" with the loyal servants of the King). For example:

* On a sensitive survey question, shunning the "prefer not to answer" box, and instead simply lying (and checking whichever box you believe to be most socially-acceptable).
* A ["black ball"](https://en.wikipedia.org/wiki/Blackballing) fraternity-style rule saying that all big decisions must pass an unanimous vote taken by secret ballot. (And -importantly- the fraternity cannot remove this rule, unless *that* decision also passes an unanimous vote taken by secret ballot).

Finally:

**Meta-Privacy** is "privacy about privacy" -- when no one can tell who cares about privacy, or how much. Alternatively: when you are able to conceal information, *without anyone knowing* that it is you who is doing the concealing.

Blending, is meta-private, but Masking is not.


### C. Applied to Bitcoin / Private Txns

When discussing Bitcoin privacy, we need to focus on Blending (and we need to stop paying so much attention to the vastly inferior Masking). In other words, we need a "taint-free de-tainting process". The de-taint process must itself be free of taint.

"Private z-to-z Txns" do not have this property. A merchant who forces customers to pay them via z-address is openly doxxing themselves as privacy-focused. (Instead, they should be pushing for customers to pay them in the most tax-transparent, regulator-ily-compliant way.)


### D. For Privacy, The UI is Fundamental

#### i. Hating on UI-Devs

User-Interface work is often maligned. In the crypto space, programmers who choose to work on UI never get invited to the prestigious conferences (all expenses paid, in exotic locations) and they certainly never get the $200k+ sinecures. Any programmer who works in UI will see their career suffer!

( This is a little curious, given the success of Apple/SteveJobs, and of mantras emphasizing the "user experience". I think we can attribute it to the fact that UT work is ignorable and does not ["bitcreep"](https://www.gwern.net/Holy-wars#bitcreep). So UI developers have less monopoly power; they are more in perfect competition. Plus, UI work is less overtly impressive/pretentious -- it barely even has equations. )

#### ii. Two Reasons to Love UI-Dev

When it comes to real-world privacy, the UI's lack of prestige is a mistake.

First of all, most privacy mistakes are the result of *user error* -- the user "slipping up", and doing something they aren't supposed to do. A single slip up can compromise all the privacy. We can fix this by streamlining and controlling the entire process, thus making it impossible for the user to do the wrong thing.

Second of all, recall that privacy is inherently about "blending" different individuals together into one large group. And: the larger the group, the easier it is to blend quirky people into it. So, a privacy technique must be easily attainable to as wide a variety of people as possible (and, of course, to as many people as possible). Ideally, a "privacy protocol" would be default behavior (either the default operation of some software, or the default cultural behavior of individuals).

### E. The Inherently Social Nature of Privacy

Privacy is therefore inherently social -- it is about other people and what they do, and what the wider society does, and why.

In a world where the government had full surveillance access to all of our smartphones, then (if we cared about privacy) we might try to just *do without a smartphone*. But this strategy will fail if it is pursued in insufficient numbers (say 5 people out of a town of 50,000) -- it will become "masking" (not blending), and thus invite suspicion and retribution.[^3]

[^3]: Instead, we would want to "blend". We could try to use our smartphones as much as everyone else, and in the same way. And then (to communicate secretly) we would need to take full advantage of rare moments when the smartphones are out of earshot (for instance, when they are charging at night).

If a crime is committed nearby, then law enforcement may pin it on a smartphone-less citizen nearby. They could craft an argument of the form: "How could it be that we have no idea who did it? Well, this is the only guy around without a smartphone. He is the only one with opportunity. He *claims* that he just doesn't want a smartphone for privacy reasons. But, members of the jury, why do you think *That* might be...?".

Thus, our pursuit of privacy is intrinsically bound to the decisions and ways-of-life of the people around us. We cannot "blend" in with them unless we know them.

Hence: "Melt/Cast".


## 3. Melt/Cast

Melt/Cast is a User-Interface scheme designed to be used with zSide (zcash drivechain), which provides ultra-secure ultra-user-friendly "click button"-level coin anonymization.

The UI is simple, in order to (as mentioned above) prevent accidental misuse, and encourage adoption.

![image](/images/zside-ux.jpg)

Try it [here](https://www.drivechain.info/releases/index.html)!

First, what does it mean to have "tainted" (ie, "Doxxed") your coins? 

### A. Digression: Tainted Coins / Doxxed Coins

**"Taint"** refers to two problems in Bitcoin:

* A user may make a mistake, and has "doxxed" their UTXOs (by linking them to their real-life identity).
* A user may wish to consolidate many small outputs, without revealing (to the world) that all these outputs have the same owner.

![image](/images/cashout-of-scam-coins.png)

Above: Coins from the [Summer 2020 Twitter hack](https://en.wikipedia.org/wiki/2020_Twitter_bitcoin_scam). For the attacker to cash out, these "shameful" coins must somehow be mixed into the pool of "normal" coins. (Someone "sold" a fraudulent giveaway, thus "shaming" the coins.) Via [tomrobin](https://twitter.com/tomrobin/status/1283858847833169942).

( "Tainted coins" and "tainted transactions" are the same thing -- the first is from the merchant's point of view, and the second is from the buyer's point of view. Tying your identity to some coins, is called "doxxing your coins". )

### B. Whirlpool vs Melt/Cast

The most popular de-taint technique today, is a version of CoinJoin called "Whirlpool".

Here is a table comparing Whirlpool to zSide's Melt/Cast:

![image](/images/meltcast-vs-whirlpool.png)

\*See [here](https://www.reddit.com/r/WasabiWallet/comments/c5l1ju/is_wasabi_better_than_samourai_wallets_new).
\*\*See [here](https://6102bitcoin.com/faq-whirlpool/#install).

Melt/Cast seems to be better in every respect.


**Update** (Mar 19 2021): The great CoinJoin Dustup of 3/2021. See [here](https://twitter.com/matt_odell/status/1372681937186340875) and [here](https://twitter.com/francispouliot_/status/1372349324500348938). [Etc](https://twitter.com/francispouliot_/status/1372701027607191558) [etc](https://twitter.com/matt_odell/status/1372358767229165573). I unironically agree with the sardonic conclusion [here](https://twitter.com/francispouliot_/status/1372901299193274377). CoinJoin just isn't good enough in my humble opinion.

A big difference is the row labeled: "Each user increases the anonymity set". That feature allows Melt/Cast to be both cheap and Sybil-resistant. A second big differences is CoinJoin's need for interactivity.


### C. Why Melt/Cast?


People [occasionally complain](https://twitter.com/fluffypony/status/1264127539821363202) --*with justification*-- that **zCash-users misuse the software**. Thus ruining the privacy for themselves and others. In particular, zCash-users make the mistake of synchronizing coin-amounts, and transfer-times.

For example, a well-meaning-but-inept user might send 73.094 Bitcoin into a z-address, and then "unshield" 73.091 BTC right afterward. They would think that they had "covered their tracks" and de-tainted their coin. Unfortunately, they have done nothing of the kind.

We can fix this problem, by making a few UX changes. The new UX is a protocol that I will call "Melt/Cast". (Since the user first "melts" each t-address" into a big pool of fungible slag, and then "casts" this slag into common coin amounts at common times.)

### D. How M/C Works

#### i. Overview

The key attribute of Melt/Cast is that it is VERY EASY for users to extract coins from the shielded pool in "common amounts at common times". As I will show, users can do this without interacting with each other.

![images](/images/melt-cast.jpg)

Above: Diagram of Melt/Cast. Different ("tainted") coins first go individually into the "black box" of the sheilded z-address world. They then emerge from the box in standardized amounts at standardized times -- the coins that emerge from the box are **identical in every way** (even in their value-amount and the time which they emerge from the box). They are truly fungible.


#### ii. Forcing Common Amounts (Without Interaction)

"Common amounts" could be achieved by predefining fixed "bill values".

![image](/images/coin-powers-of-two.jpg)

Above: Satoshis of different quantities. I have named them after US Presidents[^4], and am referring to them as "bills" -- partly as a joke, partly so that I may use them in the explanation below, and partly to help people draw an accurate analogy to the cash bills we use today.

[^4]: In practice, of course, we could name anything -- "A","B","C"; Roman Numerals; "Kulaks","Tǔgǎi","Junkers","fluchtsteuer". In zSide today they are just unnamed.

For example, 0.75 BTC can be withdrawn via "1 Hay" + "1 Harrison" + "1 KcKinlie" + "1 TeddyR". That portfolio sums to 0.7444,8896 BTC, which is 99.26% of 0.75 BTC.

The residual 0.0055,1104 would stay un-withdrawn, in the user's z-address on the z-sidechain, to be withdrawn later. Of course, if the user is will to use more bills, then they can withdraw more of it immediately. They would use 1 "Taftie" to withdraw .0052,4288 of the 0.0055,1104, and then 1 "FreddyD" to withdraw 0.0001,6384 of (what would now be) the residual 0.0002,6816.

You can see that, under a power of two system, each marginal bill decreases the residual z-addr balance by somewhere between 50%-100%. Thus, no matter how much value is in a z-address, at least 93.75% of this value can be withdrawn via 4 bills or fewer[^5]. (And that is just the worst-case-scenario. Normally \~98% can be withdrawn and sometimes even 100%, via just 4 bills or fewer.)

[^5]: A "powers of 10" system is more intuitive but performs much worse -- it takes *nine bills* to guarantee that at least *\~90%* of an arbitrary value-amount can be withdrawn.

#### iii. Common Timings

For "common timings", we adopt the convention that certain "bills" are always de-shielded on certain days.

![image](/images/withdrawal-days.png)

![image](/images/common-days-ex.png)

See these excel sheets ([here](/images/bills.xlsx) and [here](/images/melt-cast-days-example.xlsx)) for the images above. The second sheet has two examples.

#### iv. "No Unshielded Merges"

Thirdly, and finally, we can improve Melt/Cast further, by capping the number of t-addr inputs at 1. This prevents users from accidentally linking their UTXOs.

To merge small [t-UTXOs](https://electriccoin.co/blog/anatomy-of-zcash/) into larger ones, users would "shield" each one. (Ie, they would send them --one at a time-- from their [transparent] t-addrs to their [hidden] z-addrs.) Only when they are all in z-addrs (and thus ["out of sight"](https://explorer.zcha.in/transactions/de1d78ee310ba2c9fbeb13881f431fdc8b55aa5f79e61dd3c294177401878f11)), would users fuse these small UTXOs into larger ones (in the form of multiple t-addr "bills").

### D. Other Applications of Melt/Cast

**Every** single coin-privacy / coin-swap technique can be defeated, if the user is careless with the timing and magnitude of their entrances and exits.

So, it is possible that other privacy techniques will be able to make use of the "common amounts" and "common times" the come with Melt/Cast.


## 5. Drivechain Side-to-Main Withdrawals, Taproot

### A. Drivechain Happens to Mix Coins, Passively

Drivechain happens to inadvertently add some privacy. This is because the "in protocol" Drivechain withdrawal process is deliberately very slow. Instead, most users will be impatient and "swap" out.

![images](/images/sc-fresh-coins.png)

Above: An image tracing A's UTXO as it travels from the mainchain to a sidechain (via Drivechain deposit), and then is "swapped" back onto the mainchain (via HTLC, PTLC, or "withdrawal service" such as [SideShift.ai](https://sideshift.ai/btc/eth)).

As a beneficial side-result of this, users of Melt/Cast will get *completely* separate coins -- separate even from the coins that came *out* of the Melt/Cast operation!

This is really really great, but unfortunately it is *interactive*. As mentioned earlier, interavtivity means that the user must communicate with some other person (who is possibly an adversary, or under survelliance by an adversary).

### B. Much Better with Taproot

Worse, until Taproot is activated, these atomic swap transactions will stick out like a sore thumb.

But once Taproot is activated, the atomic swap txns will blend in, and exactly resemble all other Taproot-txns.

Melt/Cast will stop the user from doxxing themselves via the amount/timing information, and since Melt/Cast "rinses" the coins *before* the interactive step, not *too* much damage is done by the interactivity (although it would still be the most unsatisfactory piece).

Thus, with Drivechain + Melt/Cast + Taproot, BTC's coins may actually become fungible.

### C. De-Taint Specialists?

In a complex world such as ours, people are different. Some will not be able to touch "tainted" coins (for some legal or social reason), but others will be easily able to make use of them.

Drivechain's market for cross-chain swaps will naturally allow taint-vulnerable people to swap coins with taint-immune people, to the benefit of both parties.

Not only will people be able to de-taint their coins at the cheapest cost possible, but it will greatly discredit the entire concept of a "tainted coin".


## 6. Appendix 1: What is Privacy? How do we get it?

We should identify and destroy privacy-problems head-on.

But what are those problems, exactly?

1. People want to hide **how much Bitcoin they own**.
2. People want to hide the fact that **they paid-for/sold something embarrassing** (this is intimiately related to coin "taint"/"fungibility").

For example:

![image](/images/lost-coins-meme.png)

Above: the ["tragic boating accident"](https://twitter.com/fluffypony/status/943493541182963712?lang=en) meme, via [abrkn](https://twitter.com/abrkn/status/1209406031194984448).

In essence, the first problem asks "How can Bitcoin-users *pass* as non-Bitcoin-users?", and the second asks "How can tainted coins *pass* as non-tainted coins?".


### First Problem: Envy and Net Worth

[Deniability](http://www.truthcoin.info/blog/deniability/) lets your friends [or lawyers] tell an adjacent Gestapo that "our friend doesn't own any Bitcoin", in a way that is believable. No one is ever sure of your Bitcoin Net Worth.

The fundamental problem of [Envy](http://falkenblog.blogspot.com/2010/03/why-envy-dominates-greed.html), is that other people might want what you have, and might "persuade" you to hand it over. Thus, man's desire to create and produce has historically been offset by guilt and fear of theft/retribution/alienation -- one of the most productive things a society can do is [stamp out Envy](http://falkenblog.blogspot.com/2020/01/helmut-schoecks-envy.html). This is not always possible, but with **money** in particular[^6], an easy way to eliminate nearly all Envy, is to make it *impossible* for *anyone* to determine how much money you own. Then, any citizen who works to obtain more money, will obtain only advantage for himself; never disadvantage.

[^6]: Once this seed of privacy / non-Envy is planted, in society's money, it will likely grow. For example, imagine a situation where two things are the case: [1.] Society starts up an Envy-powered tax, levied on the owners of expensive cars or homes, or owners of stock portfolios; and [2.] Cryptocurrency wealth is not measurable, and is therefore immune to all taxes. Then, wealthy citizens would tend to react to the tax, by moving *out* of cars / homes / equities, and *into* tax-free cryptocurrency. Eventually, culture and fashions would change -- travel, expensive hotel rooms, car rentals, and carefree minimalism would become chic and high-status. (Meanwhile, "owning large manors" and "entrepreneurship" would become stiff and old-fashioned.) Sooner or later, society will understand that, if citizens can't spend their money in a private, property-right-respectful way, then they will resort to hoarding it (and hoarding other inherently-private wealth, such as leisure time). With such a strong Champion of Privacy already in the game, society will probably have to become more privacy-oriented... just to compete. 

Since "Deniability" obscures your network, it solves this first problem.

### Second Problem: Concealing Financial Records

The zcash sidechain can solve this second problem. First, by enabling z2z Private Txns. And second via Melt/Cast.

The mere existence of a Zcash sidechain makes it less reasonable to investigate individual txns or UTXOs -- doing so would just drive future "wrongdoers" (ie, those who would be blacklisted) to the ZCash sidechain.

The sidechain is non-interactive -- users can use the "shielded transactions" to melt down tainted coins and withdraw them secretly. And you can even plausibly deny that you've ever used the ZCash sidechain -- just walk the coins back the the mainchain, and then send them to yourself a few times. None of this involves interacting with another human being.


## 7. Appendix 2: Multiple Periodic Zcash Sidechains = Shrink Nullifier Set

    Update Feb 11 (Forgot to mention)

The zk-snarks used by zCash-tecth, have the problem of an [ever-growing "nullifiers set"](https://twitter.com/oleganza/status/1090771283321675776). The set must grow with each z-transaction, forever.

The only known way to reduce the set, is to reduce it all the way -- *eliminate 100% of the set* by closing down the entire blockchain and starting over with a new blockchain. Obviously, in a single-blockchain world, this a non-starter! But in a sidechain-world, it is [relatively harmless](https://twitter.com/specialenmity/status/1339943814061043713).

Thus, a periodic "revolving door" of *multiple zSide sidechains*, is much more effective than a single zSide (or a single zCash).

-----
### Footnotes




<!--

\
, CoinJoin, CashFusion, and [CoinSwap](https://gist.github.com/chris-belcher/9144bd57a91c194e332fb5ca371d0964#payjoin-with-coinswap)


Why is that a problem?

#### Interactivity Is Often Fine, But Sometimes It Isn't

For most "casual" transactions (eg buying a coffee, shopping on Amazon, etc), this is unproblematic, because the two transacting parties are already interacting in a "brightly lit" region of the Internet -- one with high-bandwidth and customer-service-chatbots standing by. Since the computers will do most of the talking, there really isn't any *marginal interaction*. They were already interacting.

At other times, the two parties will be neither willing, nor able, to interact with each other. If the transaction is criminal -- logs -- everything they touch will be toxic.

-->


<!--
### ZK-SNARKS / The Z-Cash Sidechain



But a ZCash sidechain 


When the sidechain *is* interactive, things get even better. This is because the interactivity is "meta-private" -- you might be interacting with a de-taint specialist, but *no one will know* that you are. This is because you


 [PayJoin](https://news.bitcoin.com/bitcoin-mixing-concept-payjoin-makes-a-huge-mess-for-blockchain-surveillance/).


Among all the ways to merge smaller UTXO into large one, a *very large* CashFusion (with many inputs, consisting of random digits) probably does pretty darn well, at very minimal effort and complexity.

-->
