---
title: Oracles are the Real Smart Contracts
comments: true
---


> Smart Contracts need Oracles, Oracles need Governance, Governance needs Sidechains. Ethereum cannot support Oracles, and has no use-cases.

## When Shackles Empower: The [Autonomy](https://www.youtube.com/v/_lOT2p_FCvA?&version=3&autoplay=1)-[Coordination](https://www.youtube.com/v/93walxW7mjQ?start=146&end=442&version=3&autoplay=1) Tradeoff
> Some freedoms contradict each other. By oppressing contradictory freedoms, total freedom can actually increase.

Skip this section (To "The Anarchy of Ethereum") if you already buy this (obvious) premise.

### In Extreme

Imagine a world where we all had the ability ("freedom") to fold a "magic paper airplane" and throw it into the sky, at which point it would travel magically toward, and into, the sun...causing the sun to magically explode, destroying all life on this planet.

![plane](/images/paper-plane.jpg)

Obviously, in this world, governments would be (with the utmost diligence) scanning the skies for paper-airplanes, and burning them down with long range space-lasers (or something), and then tracking down those responsible.

What would society do to someone caught throwing such a doom-plane? Jail them at the very least. What if other objects (fireworks, kites, baseball, ...) interfered with plane-scanning systems? Obviously these previously-enjoyed activities would all be totally banned. We would lose some of our "freedoms", and that's sad.

But, dead people aren't "free" to do anything (and "anything" includes "fireworks"), so not-banning is more-sad.


### In Our Society

Less-extreme versions of that "restrict options to maximize them" story play out every day.

[Intellectual property / copyright is one example](https://en.wikipedia.org/wiki/Patent#Rationale): if bootleggers can copy an original Star Wars (1979) and sell it for Low Cost = {Their Labor + Blank VCR}, these sales will be competitive (guaranteeing this person a job) and they would tend to displace *all* sales of the original Star Wars (which must sell at High Cost = {Low Cost + Film Production Costs}).

The problem with this seemingly-good, "cheap Star Wars VCR" scenario is that George Lucas won't have (nor will he be able to get) [any money to make Empire Strikes Back](https://en.wikipedia.org/wiki/Hold-up_problem#Underinvestment). In fact, no big budget movies will be produced *by anyone* from this point on.

While we *might* have enjoyed the option ("freedom") to buy The Empire Strikes Back at the bootleg price of $5, now that we've accidentally prevented it from existing, we don't have the option to buy it at $5 or ANY price.

Again, by *restricting* an option (to buy bootlegs), we have actually *increased* the total optionality. As long as we **know** that [the bootleg option really *would* have *killed* the underlying project](https://en.wikipedia.org/wiki/Software_patent_debate#Hinders_research_and_development) (and that its restriction causes no [undesirable](https://en.wikipedia.org/wiki/Corruption) [side-effects](https://en.wikipedia.org/wiki/Censorship)), **this restriction was unambiguously helpful to everyone!**



### In Nature

As with nearly everything, Mother Nature is **way** ahead of us. Individual Honey Bees are compelled to sacrifice their (easily replaced) lives to protect the (less replaceable) hive/queen. In parallel, many social mammals experience emotions which *prevent* selfish "autonomous" behaviors but (passively) *cause* coordinated group behaviors.

![Cheers](/images/dr-grant.png)

(above) Dr. Grant instinctively shields some young children from Velociraptors, Jurassic Park (1993). It's suicidal, but he *wouldn't be able to <b>LIVE</b> with himself* if he let something happen to those little kids. We like him more and would help him if we could (especially if our future-associates are watching).

Consider the affliction of cancer: when individual cells "break **free**" of their growth constraints, they eventually cause their resident organism to die (killing themselves in the process).

Even George Orwell, Freedom Warrior, PhD, [understood](http://orwell.ru/library/essays/Spanish_War/english/esw_1) that a soldier's orders "had got to be obeyed".


## The Anarchy of Ethereum
> Ethereum allows *anyone* to make a smart contract about *anything*. In other words, it has no ability to move intelligently along the autonomy-coordination tradeoff. The autonomy it provides will actually prevent many things from taking place.

From now on:

* "Contract" refers to "a set of ledger-modification instructions that self-execute on a blockchain" (ie, "if x sends > $9000 to y, send $20 to z").
* "Oracle" refers to "blockchain software asking a human for information" (ie, Software prompts "According to X, what was the USD/BTC exchange rate yesterday?").
* "Sidechain" refers to "[two-way-pegged blockchains](https://blockstream.com/sidechains.pdf) (that the 21 million BTC can only change quality, not quantity) which are also merge-mined (where Bitcoin miners have a free option to mine on any or all sidechains)".
* The term "Ethereum" is interchangeable with "any smart contract platform with permissionless smart-contract-creation".


(...unless specified otherwise). That'll save us some space.


### Honest Oracles Need To [Overcharge](https://en.wikipedia.org/wiki/Myerson%E2%80%93Satterthwaite_theorem)

The free market uses "brands" as robust indicator of reputation (allowing merchants to "add" quality to a good and "sell" it), but these brands don't work if competitors are free to copy them.

![poor-oracle](/images/oracle-dies.png)

#### Fool Me Once

In all interesting cases, Oracles will have an incentive to lie today (if they don't, we don't need to worry about them at all, and can safely use multisig). However, we can sometimes overwhelm this lie-incentive with an even bigger incentive to remain honest.

How? Consider the Oracle's job: Before the Oracle publishes its work, the same [nothing](https://en.wikipedia.org/wiki/Cheap_talk) is observed by anyone. After it submits, it is too late to do anything about the result!

Clearly, we must somehow *use multiple results*...but multiple results delivered *at one time* will all be attacked simultaneously (proof by simple addition, or task-redefinition). The real trick is to use multiple results *across time*: the Oracle has *its future* to lose.

Why, the very concept of "Honesty" *requires* "Memory" (and "Identity").


Then, our focus is this very interesting and very common position: [non-compliance is *short-run* profitable](https://www.youtube.com/v/F0VHiONkot8?start=331&end=360&version=3&autoplay=1), but **a period of <i>lengthy</i> compliance generates greater total well-being**. [A group can harvest that surplus and divide it up](https://www.youtube.com/v/l-bflQuRLbU?start=125&end=150&version=3&autoplay=1), effectively <a href="https://en.wikipedia.org/wiki/Folk_theorem_(game_theory)">coordinating their mutually-prosperous joint-future</a>.


But if there are no stable identities ("brands"), there's no way to remember "who" complied in the past. If you are paired with a new faceless player each round, "your interactions" aren't really "repeated"; you [might as well be playing all of the rounds at the same time](https://en.wikipedia.org/wiki/Information_set_(game_theory)); the "long run" is non-existent!

So we need that long-run surplus to exist (which it often does), and we need a way to get The Surplus to the right people. Keep that in mind. We'll get right to it, after a restatement of the above from the field of game theory.

#### "We need the money." -Mechanism Design

[Mechanisms](https://en.wikipedia.org/wiki/Mechanism_design), including [all those which would accurately produce external data](https://en.wikipedia.org/wiki/Revelation_principle), seek to satisfy several desirable conditions, but, according to underlying mathematical theory (and [depending on the specifics](http://www.eecs.harvard.edu/~parkes/cs286r/spring02/lectures/class6.pdf)), the designer usually [can't satisfy them all](http://coin.wne.uw.edu.pl/kiuila/AM/Wojtek/Lecture%208.pdf) and must choose [one to break](http://www.cs.berkeley.edu/~christos/agt11/notes/lect9.pdf).

In [*practice*](https://en.wikipedia.org/wiki/Information_asymmetry), two conditions aren't realistically breakable ("incentive compatibility" and "individual rationality"), but the typical third is ripe for breakage: "balanced budget", which assumes that the mechanism does *not* have to pay out any money of its own (ie, the "doubling" of the cash in the money-bowl experiment).

![Myserson](/images/myerson.png)

"Mechanisms that get external data" are going *to need to pay* data-providers, not just for their time/effort, but also for [their honesty and cooperation](https://en.wikipedia.org/wiki/Quasi-rent) (their "brand").

Yet this implies that *the info-providers are always going to need to be <b>over</b>paid* relative to "bootleg" info-parasites. The problem is fundamental unavoidable.

Speaking of unavoidable:

### Ethereum Can't Overcharge

#### Anything Goes!

Ethereum allows users to create *any* "Smart Contract" they want, without having to re-do the (HARD) work of building a new community of miners, full nodes, or users. 

As you might imagine, I was a little thrown by this idea. For starters, I had just spent the month of November making sure that [my own project](http://www.truthcoin.info/papers/truthcoin-whitepaper.pdf) wouldn't inadvertently create [assassination markets](https://en.wikipedia.org/wiki/Assassination_market). In [contrast](https://bitcoinmagazine.com/21626/future-smart-contracts-positive-social-innovation-criminal-activity/), no one at Ethereum [seemed to even know what it was for](https://www.youtube.com/v/yQvhEUuwJCk?start=175&end=195&version=3&autoplay=1), [let](http://www.truthcoin.info/images/enron.txt) alone [care](http://definitions.uslegal.com/d/depraved-indifference/).

![Cheers](/images/eth-cheers.png)

But of course today's point is that **permissionless** smart contracting systems introduce contradictions in incentives which destroy all interesting use-cases.

#### The Parasite Contract

Behold this outline for a Smart Contract:

1. Offer all the functionality of a pre-determined "Host" Oracle Contract.
2. Wait for the Oracle to report. In other words:
	1. Access the database of the Host's blockchain (by tracking things like block number, block date, SPV proofs, etc).
	2. Scan the database for anything perfectly-correlated to the External Data fetched by the Host Oracle (contract state, payouts to certain addresses).
3. Use that Host-Data to alter the Parasite's state (without paying the Host anything).

Because of this, any Host (external-data contract) can't grow to a significant size without being invaded by Parasites and leeched to death. While the production of a bootleg movie at least takes *some* effort on the part of the criminal, and the movie has *some* inferiority to the original, these Parasites are nearly-free to make, and have the ability to mimic their Host *perfectly*.



#### (Probably) Nothing Can Fix This

How might we prevent Ethereum from supporting Parasite Contracts? These are merely Contracts that scan *their own blockchain* for data. They [don't need to understand the Host Oracle](https://www.reddit.com/r/ethereum/comments/3ht8rx/who_will_build_a_better_prediction_market_augur/cuasel3), only the actions it takes. Ultimately, one can even build [a second Ethereum](https://bitcointalk.org/index.php?topic=1155284.0) to circumvent any imposed limitations, or a "Parasite Oracle", which uses humans to fetch the (batched) target data.

I don't think it's fixable at all. The *generality is the problem*: the power of contracts, including a social contract like Bitcoin, is that they are a mutual *restriction* of freedom. Bitcoin is *all about* what you are *not* allowed to do (spend other people's money, counterfeit, etc).



Of course, [a single chain](http://image.slidesharecdn.com/2ndethereummeetup-140430180708-phpapp01/95/2nd-ethereum-meetup-2-638.jpg?cb=1398881427) might enforce a globally-optimal set of rules, but *who decides* these rules? How do we manage the permissiveness-security tradeoff without a central administrator? If there is a **dispute** over which rules should be included, who should resolve it?


Well, now I'll stop [complaining about broken things](http://www.xenodochy.org/article/popper.html), and show you an idea that will probably work.



## Sidechains: The Global Contract
> Using Sidechains, a decentralized group of self-interested miners can remove contradictions in coin-abilities such that total coin-ability is maximized.

### Bitcoin's Limited Government

The world of Sidechains has the ideal *global* incentives for a prosperous blockchain-universe. Miners coordinate the global "law", governed by a clear [**principle**](https://en.wikipedia.org/wiki/Principle): maximize the total sale value of the Bitcoins that they mine. This governing principle is desirable for users: the sale value is maximized when miners [1] construct a "portfolio of sidechains" which presents **maximally-useful** Bitcoins to users (as measured [by exchange rate](https://en.wikipedia.org/wiki/Economic_calculation_problem)), and [2] optimize the **usage** of these useful-Bitcoins (measured by transaction-fees).

This essentially **a perfect delegation** of "the user's preference for safe, useful cryptocoin features" to a governing authority. Especially because my expectation is for a very small number of active Sidechains (fewer than 10), making the decision making process very straightforward.

Cool, right?

### The [Monopoly on Violence](https://en.wikipedia.org/wiki/Monopoly_on_violence)

#### So Far, So Good

[Peter Todd emphasizes](https://twitter.com/petertoddbtc/status/525586857136893952) a key sidechain characteristic: **miners can destroy/steal-from any sidechain that they merged-mine** *...at no direct cost*. But with the bad comes the good: miners (as a group) can and *should* censor any sidechain which threatens the value of the "sidechain portfolio" (or affects it superfluously).

Consider "useful sidechains" (those which increase the market value of each Bitcoin). For these, miners are unlikely to 51% attack the sidechain, for the very **same reasons that they haven't yet 51% attacked the main Bitcoin chain**: a *failed* attack would be costly to the miners (in the opportunity cost of wasted hashes), and a *successful* attack would also be costly to the Miners (in the devaluation of the Bitcoins rewarded to miners, and corresponding decrease in mining ROI). In fact, after endorsing a sidechain, for the mining community to suddenly betray it would almost certainly call into question their general dependability.

#### The Long Arm of the Law

What of a pegged sidechain which does NOT merge-mine? Can such a sidechain escape the governance of the merge-miners?

Who cares? Non-mergers won't get the 25-BTC-per-10-minute coinbase; they'll *only* get transaction fees. Therefore, the hashrate is likely to be overwhelmingly insecure at all times: [1] at first, when the transaction volume is zero, [2] should the transaction volume ever fall toward zero *for any reason, at any time in the future*, or [3] should *the Bitcoin [exchange rate suddenly rise](http://www.investopedia.com/articles/investing/052014/why-bitcoins-value-so-volatile.asp)* (making theft of the pooled funds more-profitable), for any reason at any future time.

Every pegged sidechain needs a trove of at-risk BTC. An unreliable hashrate makes that initial-BTC hard to find. Once found, that BTC might vanish at any time, on *the mere rumors* of future tx-fee problems (impending theft, new competition, disagreements with rival miners, government action, ...).

Thus, the Bitcoin community is protected against globally inefficient ("parasitic") sidechains, as long as they are pegged to Bitcoin.


What about Altcoin Smart Contracts (neither pegged nor merged-mined)?


## Counterfeiters vs. Capitalists
> Selective Sidechains can safely emulate Smart Contracts, but the reverse is impossible. When coupled with the network-effects of money, the resulting competition will likely obliterate any Altcoin smart contract system.

Let's examine the relative situation of these two "Families" of Blockchain: Oracle Family (BTC pegged sidechains governed by miners) and Contract Family (non-merged Altcoin, where anything goes).

### Oracles *Are* Smart Contracts

Hopefully obvious: every question that you can ask a computer ("2+2"), you can ask a human ("What is two plus two?"). In fact, you can always ask a human *to just ask their* (hopefully [post-1999](https://github.com/ethereum/wiki/wiki/Ethereum-Development-Tutorial#gas)) *computer*. 

Oracles can go well beyond Contracts, and do [many, many other things](http://www.truthcoin.info/papers/3_PM_Applications.pdf) (for example, tap useful financial datafeeds with "What is the BTC/USD exchange rate?", "What is the price of Gold?", etc).

![oracleknows](/images/oracle-knows.png)

One might argue that it is "more expensive" to ask a human being vs. a computer. Perhaps, [perhaps](http://www.salon.com/2006/07/24/turks_3/) [not](http://eprint.iacr.org/2015/702.pdf). Moreover, Oracles can *actually be* mere computers. The only requirement I outline here is that Oracles must be "overpaid" ([compensated](https://en.wikipedia.org/wiki/Quasi-rent) for their *honesty* in addition to their *labor*). They don't need to be humans.

### Can "Introspective Ethereum" Survive?

One problem common to all sidechains, including "parasitic" ones, is [the tremendous expense](http://www.coindesk.com/mike-hearn-underfunding-leaving-bitcoin-development-crisis/) involved in [maintaining software](http://www.catb.org/jargon/html/S/software-rot.html). To get by, a software project of this immense scale and inter-connectivity needs large social networks (of dedicated people) and large monetary networks (to find the money required to keep these people away from higher-paying jobs). It helps if [a high-status organization (like MIT) can back a project as being technically useful and socially beneficial](https://medium.com/mit-media-lab-digital-currency-initiative/launching-a-digital-currency-initiative-238fc678aba2).

Given that Ethereum supports permissionless smart contracts, it can *not* support Oracles (it can't look "outside itself") and will be necessarily adversarial with them (everywhere).

Where does that leave it?

#### Who Cares?

It actually doesn't matter. Not only can Oracles emulate Contracts in general, but a specific Sidechain can emulate a(ny) specific Contract(s). Once someone copies *any profitable non-parasite Contract* into a new pegged sidechain, the only relevant difference between the two projects would be that one uses Bitcoin (the dominant internet money) and the other does not.


Of course, this leaves a "Parasite Domain" consisting entirely of *profitable parasite contracts* which are neither merged-mined nor pegged. Will this domain support life? Will it be like the internet, where IP-defying torrent sites (ThePirateBay, et al) endure despite opposition?

No.

#### Double Parasite and Network-Effect Strategy

Parasite Contracts are too good at what they do. They differ from (branded, reputable) websites (like PirateBay) and biological parasites (built out of organic matter) in that [1] they are much **easier to create** quickly and that [2] subsequent Parasite Contracts are at **no disadvantage**.

In other words, the Parasites not only drain their Host of resources, but they also compete *with each other* for these drained resources. This [perfect competition](https://en.wikipedia.org/wiki/Perfect_competition) implies that the [equilibrium behavior](https://en.wikipedia.org/wiki/Nash_equilibrium) is for there to be a single Parasite per Host, operating as-cheaply-as-possible. Result: *all* economic surplus is transferred from Hosts **to the Users** (none to Parasites), such that no second Parasite can profitably enter.

The parasites all (theoretically) survive, at cost. But, they aren't hard to kill: First, create a *copy of each parasite* with yourself as the owner. Now, all the parasites (including your half) are alive but unprofitable. Second, commit to doing this every time a new host is infected. Now it is unprofitable to create a parasite.

While "de-parasiting" costs time and effort, this is the "cheapest" move played in this game so far: the programmer of the second Parasite merely needs to make a tiny change (the crypto-"Owner" value of an already-made Contract...a highly ironic "meta-parasitism"). But who would pay this tiny, nonzero cost?

<!--
zzz..boring

~international waters, pirates betraying each other~
![image](http://img.lum.dolimg.com/v1/images/swords_35f00986.jpeg?height=473&mode=crop&region=0%2C0%2C1580%2C880&width=630)

Here's an analogy: the Bitcoin Family (network of Sidechains with highest-quality Smart Contracts including Oracles) is like a large nation, coordinated-and-protected by a limited government, police and military. The Parasite Family (non-BTC Contract platforms) is like a much smaller and mostly ineffective group of sea pirates who live on islands just offshore. When merchants venture into international waters (where the BTC-military has limited authority), the pirates can interrupt trade and cause economic havoc (although there's so much infighting between  this leaderless rabble that the warring tribes never truly benefit from the piracy). With no military, in international waters, **the merchants have to defend themselves** against this (overwhelmingly minor) threat. As all merchants tweet photos of pirates as they attack, a rich merchant just has to **hire some thugs to rough up problematic pirates**. Eventually, **people abandon the pirate society** altogether.

To reverse the analogy, the merchants would be "Votecoin owners" in Truthcoin (or, generally: whoever is being compensated for their data-honesty). While there is a slight free-rider problem in both cases, the cost of de-parasiting is so low as to likely make it worth it for some Voters. Even without de-parasitism, the Parasite blockchains are entirely unprofitable, will be unable to afford developers, and will succumb to extinction.

-->

Those who are currently being "overpaid", for a start. There is a free-rider problem, but the cost of de-parasiting is so tiny that it is unlikely to make a difference. 

Ultimately, as Bitcoin takes over [the internet](https://en.wikipedia.org/wiki/Optimum_currency_area), all non-Bitcoin projects (of any kind) will be treated with the ridicule afforded a US resident who tries to pay for his milk with Japanese yen. Eventually, interest in using a non-Bitcoin will fall to zero. Altcoins, even somehow-useful ones, don't have a future.

So, the use-cases of Introspective Ethereum will either be absorbed into Sidechains (or [businesses](http://www.truthcoin.info/blog/limits-of-blockchain/)) designed for such a purpose, or simply fade away.

What if they don't? It still doesn't matterm, because:

## Non-Oracle Smart Contracts Are Useless, Anyway
> Ethereum's value proposition was something *general* (enabling a high rate of project-creation). However, Ethereum's use cases are few (if not nonexistent), making the "generality" objective inappropriate.

Let's start by locating the problem Ethereum is trying to solve.

### All "definitely-enforced" Contracts are already "Smart"

#### Self-Enforcing Contracts

Long before computers, our society invented a "good enough" way to make all contracts cheaply "smart" (self-enforcing): allow users to appeal to some **Authority** (court, king, mob boss, ...) who would settle the matter with finality. If the Authority were "just", it then followed that there was *no point in actually escalating* a dispute to the Authority. Anyone who knew they'd lose, wouldn't bother trying.

Even today, contracts are mostly self-enforced by *the party who feels he <b>would</b> lose* (ie, lose to the Authority that **he** never plans to see).

Of course, that "**IF** the Authority were 'just'..." was a big "if".

#### Getting the Good Authority

In the old days, **competition** kept Authorities in line. For example, in [The Merchant of Venice](http://shakespeare.mit.edu/merchant/merchant.4.1.html), Shylock is trying to get a contract enforced by an Authority:

    The pound of flesh, which I demand of him,
    Is dearly bought; 'tis mine and I will have it.
    If you deny me, fie upon your law!
    There is no force in the decrees of Venice.

Those first three lines are directed *to* the court, but the fourth is a "what if" warning, hurled dramatically to the court's nearby (non-participating) audience. By which he means "if **we (Venice)** violate the principle of contract-enforcement, **we (Venice)** will suffer".

That's what Shakespeare thought his *16th century* audience would buy.

Our modern world has seen the decline of the city-state in favor of the nation-state, resulting in (among other things) decreased levels of inter-Authority competition. Bitcoin has [multisig](https://en.bitcoin.it/wiki/Contract#Example_2:_Escrow_and_dispute_mediation) ([pretty close](http://gavintech.blogspot.com/2014/06/bit-thereum.html)), but can Ethereum go the distance and add "computers" to the list of Authority-competitors?

No.

### A Fundamental Limitation: CryptoLaw [without CryptoPolice](https://www.youtube.com/v/H_imYEe1FA8?start=1223&end=1290&version=3&autoplay=1)

Although it purports to be "crypto-law", real "law" can be **enforced** on *real people*. Ethereum can only **edit** *ledgers in computers*; it can't get Shylock any flesh. At worst, it can [subtract your *digital* assets](http://www.truthcoin.info/blog/limits-of-blockchain/) (if, and only if, you choose to subject them to this risk). If Ethereum wants to affect the non-digital "real world", it will *lose all of the benefits of being a P2P computer network*, (and be in conflict with Real Law, which *does* have an armed police force).



### No Oracles, Nothing Physical...What's left?

So, the "law" is limited to "consensual ledger decrease", [1] physical is out. The [M-S result](https://en.wikipedia.org/wiki/Myerson%E2%80%93Satterthwaite_theorem), combined with our inability to feed (non-BB) a [revelation](https://en.wikipedia.org/wiki/Revelation_principle) mechanism (see above), means that [2a] Oracles are out. It would also suggest [2b] that all contract-info would have to remain "close by" (be brought willingly by the players themselves, and then subject only to objective/symmetric mathematical computations).

I'm not sure what this leaves.

#### Circular Reasoning

Were an *entire financial system* on-blockchain, the derivatives on that blockchain ("pay Q to X if closing price of A is above Y", "pay Q to X if A defaults on payment Z") will be very "close by" (won't need an Oracle). That's nice, but [corporations](https://en.wikipedia.org/wiki/Limited_liability) have a built-in Oracle-need in the form of [accounting statements](http://www.investopedia.com/articles/fundamental-analysis/10/decoding-earnings-reports.asp), and just about [everything](https://en.wikipedia.org/wiki/Bond_%28finance%29) [they](http://www.investopedia.com/exam-guide/series-3/studyguide/chapter4/offsetting-contracts-settlements-delivery.asp) [do](http://www.accounting-degree.org/scandals/) is enforced by [courts](https://en.wikipedia.org/wiki/United_States_bankruptcy_court) and [actual](http://www.metroftz.com/) police officers. If the government won't enforce these contracts ("this was an [unregistered securities](http://www.investopedia.com/terms/u/unregistered-shares.asp) offering"), the underlying shares have no meaning.

#### The TOR Alternative

So the *entire business*, suppliers to customers, has to be on blockchain. But **it must avoid relying on reusable human-input**, ie *no labor*. If, instead, the laborers are going to be the owners, such laboers don't need to bother writing any code, they can simply start [an independent business on TOR](https://en.wikipedia.org/wiki/Silk_Road_%28marketplace%29). There are no incentive problems, or software bugs, at all, if the business-owner is making all of the administrative decisions directly!

### The Money Calculator is good for...a Casino?

Seemingly, the only activities which reliably cut out the external world are "calculator+" [perfect information games](https://en.wikipedia.org/wiki/Perfect_information), and games of chance, particularly because they are self-contained, well-defined, and comparably easy to program. Ethereum even [described "smart contracts" as "chess"](https://www.youtube.com/v/AHAAktdxSOE?start=332&end=387&version=3&autoplay=1) once.


#### The Calculator in Practice

We can check this theory against [a published list of every DAPP](https://docs.google.com/spreadsheets/d/1VdRMFENPzjL2V-vZhcc_aa5-ysf243t5vXlxC2b054g/edit?pli=1#gid=0) (accessed August 2015). Here's all that (supposedly) made it to the "demo" level:

![EthDapps](/images/eth-dapps.png)

Black strikethroughs are for "[intermediate goods](https://en.wikipedia.org/wiki/Intermediate_good)" (only as useful as whichever [final good](https://en.wikipedia.org/wiki/Final_good) [they support](https://en.wikipedia.org/wiki/Circular_reasoning)), red denotes "already in Bitcoin", green denotes "Oracle" (will not survive parasitism), and blue denotes "casino". So, including the new [provably-fair pyramid scheme](http://www.coinbuzz.com/2015/08/10/ethereum-offers-first-verifiable-pyramid-schemes/), "casino" characterizes 3 of the 7 discovered uses.

None of the four errors (orange arrows) concern me: they are so clearly Bad Ideas (which are either [1] asking users to pay tx-fees for what they can already do for free, or [2] so prohibitively [vague](http://www.scribd.com/doc/252917347/IBM-ADEPT-Practictioner-Perspective-Pre-Publication-Draft-7-Jan-2015)/[complex](http://www.informationisbeautiful.net/visualizations/million-lines-of-code/) that I have a hard time believing they are really at the "demo" stage). So, I'm confident that this theory will continue to hold up over time.

Of course, a Bitcoin-accepting website *can* easily emulate a casino (especially the more "fun" parts: the bright lights and entertaining sounds, to say nothing of *physical casinos* and their expansive venues, free drinks, and live entertainment). Unlike with Ethereum, there's no way to prove that such a Bitcoin website is being "fair" in its random number generation, but that's already true of the machines in physical casinos today. And *what difference could dishonesty even make*, given that **all casino games have a negative expected value**, anyway!

### [Where's the beef?](https://en.wikipedia.org/wiki/Where%27s_the_beef%3F)

On January 9th, 2009, Bitcoin was published to the cryptography mailing list. **Three days later**, Hal Finney received a payment from Satoshi Nakamoto over the internet. The payment was revolutionary: it had almost every desirable feature of money rolled into one, on the information superhighway no less. Simply: the payment promised a new world of better payments. 

On July 30th, 2015, Ethereum "launched". Three days later, nothing of any significance happened whatsoever. Months after that, the [publicized list](https://www.ethereum.org/) of "Some Projects Using Ethereum", in addition to *solely* consisting of Oracle and Physical projects (which, again, are *incompatible* with Ethereum), are [laughable](http://slock.it/index.php?c=20150901_vision) [id](https://www.youtube.com/v/qX8R7NMFSME&version=3&autoplay=1)[eas](https://www.youtube.com/v/tPrPozLdYZg&start=2108&end=2215&version=3&autoplay=1), [fraudulent misinterpretations of my own (Oracle-dependent) work](http://www.augur.net/), projects which [misunderstand the very purpose of loans by ignoring the essential concept of liquidity and assuming that someone who needs to borrow $1 in cash is willing to front $1.50 in cash](https://makerdao.com/), and, believe it or not, [projects whose entire website, locate-able codebase, and documentation comprises all of *six sentences*](http://airlock.me/). 

Things are actually worse, in practice, than I expected they'd be, when I drafted this post (January 2015). Why is it so bad??


### A Problem in General (Reprise)


Even assuming that Ethereum itself never has any conflicts or problems with whatever use-case you do come up with, you still, upon creation of a new Smart Contract, have **all of your work ahead of you**.

After all, the contracts *actually used* are not General Contracts but Specific Contracts at a Specific Time with Specific People (to quote a [psychometrics](https://en.wikipedia.org/wiki/Psychometrics#Theoretical_approaches) professor of mine: "You'll never meet 'A General Person'").

What if Satoshi had shipped a C++ compiler (a "general blockchain-creation platform")? What if Shakespeare had shipped [26 letters](https://en.wikipedia.org/wiki/The_Library_of_Babel) (a "general script-creation platform")? If a student clips a fresh pen to his blank exam, has he "solved" it "for all answers"? Of course not: the work *was* the specifics.

Is a new complier useful if it can only be used to write casino software? Is a new alphabet useful if it can only be used within a casino? Is a pen useful if it can only write the word "casino"? Of course not: generality's value is in being *unrestricted* and able to meet many needs.

And even supposing you *do* find a specific use-case, and you *do* write a quality piece of software, you *still* have the problem of [learning](https://twitter.com/jgarzik/status/645229506266038273) that it is [secure](https://www.youtube.com/v/Y6hZhdZuct0?start=1023&end=1090&version=3&autoplay=1) and [worth using](https://www.youtube.com/v/Y6hZhdZuct0?start=1143&end=1172&version=3&autoplay=1) and [*convincing others of what you've learned*](http://forum.truthcoin.info/index.php/topic,119.msg386.html#msg386). The accumulation of *security* isn't general (across contracts) at all (unlike with a sequence of Oracle-questions, where it **is** the same Honest-or-Not mapping each time).

And, on top of that, unless Ethereum is redesigned to give contracts the equivalent of a soft fork, [any accumulated security is obliterated upon every software update](http://www.truthcoin.info/blog/measuring-decentralization/).



## Conclusion

Ignore Smart Contracts; if anything, Oracles are the future of Bitcoin. Although Smart Contracts harm Oracles, a global governance mechanism (a single chain, or portfolio of Sidechains) can prevent this harm.

#### For My Next Trick

My next post will primarily focus on some (in this part of town, overlooked) game theory concepts, in the hopes of helping Bitcoin Developers nail down their increasingly-vague Threat Model.

After that, it will be time to wrap The CryptoEconomics Arc up: I will [1] destroy colored coins / embedded consensus systems, and [2] (business deals permitting) explain why private blockchains are (contrary to the currently-prevailing expert opinion) great, and how we can all make use of them.

Then I will probably move to more-important topics like Ethics, Science, Government, Finance, etc.
