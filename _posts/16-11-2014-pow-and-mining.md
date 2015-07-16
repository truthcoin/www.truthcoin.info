---
title: Long Live Proof-of-Work, Long Live Mining
comments: true
---

> Satoshi got it right: [1] proof of work ensures distributed consensus, and [2] mining ensures an economically-viable network.


## A Day's Pay for a Day's Proof-of-Work

> Econ 101: Marginal Cost = Marginal Revenue. If a block releases X dollars worth of coins to the creator, X dollars will be spent creating it.

It's been said that Proof of Work (PoW) "wastes" billions (or whatever) of dollars per year, and/or that it "wastes" energy.

"Waste" implies a more prudent alternative, and indeed these Anti-Satoshians try propose a "cheaper" way of distributing coins, despite the fact that this goal is nonsensical.

### For Auction: 100 US Dollars

Whatever "it" is, if it creates $100 worth of value, but costs <$100, everyone will be doing it as fast as possible. Applied to blockchains, if X dollars of coins are being released by each new block, then X dollars are going to be spent mining that block.

It really is that simple. It would be obvious to anyone who understood [economic rent](http://en.wikipedia.org/wiki/Economic_rent) and [opportunity cost](http://en.wikipedia.org/wiki/Opportunity_cost) (for example, as applied in the [Law of Rent](http://en.wikipedia.org/wiki/Law_of_rent)).

Why isn't this widely known in the Bitcoin community? Well, it would seem that prevailing disagreement with today’s FED Policy (a contentious, real world, imperfect attempt to execute on one particular strategy [chosen among many] – a strategy, confined completely to the applied half of the “monetary policy” subset of the “policy” subset of the “macro” discipline of the field of economics) has led Bitcoiners to a sort of groupthink-powered, willful ignorance of economic science.

Which is a shame, because just by visiting [certain corners](http://en.wikipedia.org/wiki/Cost-of-production_theory_of_value) of Wikipedia, certain 2.0 "designers" could have saved themselves a lot of time.



### Working on What?

What will these individuals spend their X dollars on, to produce the block? Maybe they'll be generating lots of addresses, or using computing power to examine many alternate block histories (under proof-of-stake (PoS), both of these use CPU power to increase the likelihood of generating coins).  

The true answer: Who cares?! Whatever is done will consume ("waste") $X of economic activity. We have merely transformed the PoW algorithm into something less straightforward and less cumulative.

For example, switching the payout-trigger to a social or political dimension (as in Delegated-PoS) would merely transpose the work-expenditures correspondingly to the realms of bribery and propaganda, which [Bitshares has already seen](https://bitsharestalk.org/index.php?topic=6096.45). Others worry about [a 'black market' for once-full-but-now-empty private keys](https://blog.ethereum.org/2014/10/03/slasher-ghost-developments-proof-stake/). Of course, a stable solution to these problems is *definitionally* impossible: by definition, there is always an incentive to work until marginal cost equals marginal revenue.

### PoW Is Cumulative (and Stable) - An Analogy

I compare the Satoshian Blockchain to watching a TV series. Every 10 minutes: a new 5-second episode comes out, viewers tune in, verify that this is the "same show" (ie, the plot continues logically from where it left off), and pass judgment on its quality. At first, the hit tv-series had precious few producers, and viewers were happy to get anything at all, even episodes thrown-together by amateur-volunteers. Over time, however, professional actors/directors/animators got involved, and it now takes a pretty serious production-outfit just to get one good episode out there to the jaded audience.

If you haven't yet figured the analogy: episodes are blocks, episode-producers are miners, the episode-quality is the difficulty, the plot is the block-validity-rules, and the audience/viewers are the Bitcoin-users.

It is easy to see how someone, waking from a 6 month coma, will be able to catch up on the episodes they missed (what happened to their favorite characters while they were away) without consulting a third party: if the show-quality drops off, they ask their friends if they are watching the canonical version. If attackers attempted to mislead the coma-patient by writing a different show, it would be of obviously inferior quality.

In fact, anyone can "get into" the show by knowing only the title of the first episode.

Under PoS, users would not determine "the" canonical series based on its quality (in fact, each episode would look very "cheap"/low-quality), but instead based on claims made by the characters in the story themselves. In Episode 43, Homer Simpson might say that "In Episode 53, I will eat a banana". Users would take all of these statements and continue watching whichever series had the most of them correct.

![Abed](/images/abed.png)

These 'in-story claims' would have to be triggered deterministically by details in 'free actions' taken by characters (such as the number of milliseconds between two successive lines).



Now obviously it is a joke to take this idea seriously. Attackers can go back to an early episode, or even the first episode, and cheaply rewrite the show in parallel ways. They can (and will) do this to the extent of their computing power. Instead of working on the 'quality' of a new episode, they would work on the 'quantity' of good-enough rewrites of a whole section of the series.

We now see that just as much "work" is done under PoS as is done under PoW. The work done is only work that is less-directly-observed. We also see that with PoW, security accumulates (the attacker finds it reasonable to attack only the most recent blocks), whereas under PoS attackers may cheaply submit hundreds of *complete* alternate realities.


## Mining Solves Two Problems

> Money is all about the network. Even with high-quality Food, Drink, and Entertainment, a party with no Guests is a complete failure.

Some designs ditch the "introduce new coins with each block" feature; this allows them to dodge my coinbase-criticisms (above). However, it does immediately beg the question: where are these coins coming from, and to whom do they go?



### Is the 2.0-Dev-Community Lazy or Just Illiterate?

To examine the purpose of mining, let's go to an obscure and seemingly-irrelevant tome, hidden completely from all blockchain-2.0-developers by virtue of its placement on the bitcoin.org website: [Satoshi's original blockchain whitepaper](https://bitcoin.org/bitcoin.pdf), of which Section 6 states:

>"By convention, the first transaction in a block is a special transaction that starts a new coin owned
by the creator of the block. This **adds an incentive for nodes** to support the network, and **provides
a way to initially distribute coins** into circulation, since there is no central authority to issue them." (emphasis added)

Above I have highlighted the **two** purposes of mining. The second is a stroke of purest genius and universally under-appreciated.

### Initial Distributions are Critical to Network-Effects

For Bitcoin, operating correctly is not good enough...nowhere near good enough! Bitcoin, as a money-network, must *persuade a critical mass of users to switch* from their existing currency to Bitcoin.

Users will only switch if they believe that something is in it for them (ie, that the network has a shot at making or saving them some money). Users won't want to be on an abandoned crypto-coin project.


### Coin Drops

#### Objectively Better Because I Say So

Any initial coin distribution can be copied-and-adjusted, so any initial "coin-drop" (giveaway) of all the coins requires **a critical mass to agree that the chosen distribution is optimal**.

#### The Deal-Breakers

Coin-dropping and then slowly destroying or shuffling coins (as seen in NXT / Ripple / Bitshares) disproportionately favors the users who got all of the coins! This is true even if the initial coins are in some way auctioned, as the 'free option' to participate in the auction is only present to those individuals who [a] know that the auction is taking place and [b] happen to arbitrarily possess the relevant background for understanding the risks/reward of the auction. 

Hopefully it is obvious: it is impossible to be aware of everything at all times (and costly to maintain an increased awareness), and impossible to have all trainings/backgrounds (and extremely costly to add training/experience). Individuals can't be held hostage to: "Trust me- you want to learn X or consult X-ers so that you can make an educated assessment of this investment opportunity." Sure, with hindsight we see that "cryptography" validated such a belief *in this one Bitcoin case*, but hindsight by-definition validates all "good investment opportunities". Investing is about recognizing unseized opportunities: the opposite of hindsight.

Secondly, an immediate giveaway ("Act now or lose out forever!") is a deal-breaker because it places an arbitrary and unjustified discount on empiricism, the virtue of waiting patiently for evidence about a system to accumulate. Thus, a coin-drop-auction also disproportionately rewards [c] unjustified optimism (gullibility). 



#### Objectively Better Because Everyone Says So (And They Prove It)


A per-block-distribution (PBD) remains fair across time: users have the 'free option' to buy, but also the 'free option' to learn more about their buy-option before exercising it. PBDs act as a literal decentralized, permissionless exchange - anyone can 'buy' Bitcoin by spending fiat currency on electricity.

The exchange kickstarts a de-facto market and market price, derived indirectly from the cost of electricity. This in turn ensures *allocative efficiency*: that **at all times** only those who are most interested in Bitcoin end up owning the coins. This opportunity to invest allows the dedicated and resourceful to own the Bitcoins whose destiny they intend to shape and control.

> "Community cannot for long feed on itself; it can only flourish with the coming of others from beyond, their unknown and undiscovered brothers." - Howard Thurman



### Green Plants and Mining

![plants](/images/plants.png)

What can plants teach us about algorithm stability?

If we could design plants, they would be purple. The light reaching this planet is most energy-dense at green, making it wasteful to *reflect* all of that green light. Instead, we should do the opposite of that, and absorb it.

![ColorWheel](/images/color_wheel.jpg)

Is this a mistake? How did plants get it so wrong?

#### Why Plants are Green

> Oxygenic photosynthesis evolved as a "make the best of it" technology, but the oxygen it produced killed off the competition (and keeps it dead).

Back in the day, all the tiny light-eating lifeforms *were* purple. Being more efficient overall, the "purple gang" greedily sucked down all the light they could get, and grew and multiplied as quickly as possible.

However, there was then an opportunity in using the waste purple light bouncing off of the "purple gang". It so happened that a "green gang" emerged, which did things quite differently: they used water as an electron donor (instead of hydrogen sulfide) and CO2 for Carbon-fixation. It wasn't ideal, but they had no choice: competing with the "purple gang" (sun-charged superbacteria) for food would have meant certain starvation.

As a tiny detail, this process ("oxygenic photosynthesis") broke H20 into Hydrogen and Oxygen. It is pretty easy to find a use for Hydrogen, which is literally just one proton (and everything is built out of protons), but the Oxygen began to accumulate in the atmosphere, seeping into the far corners of the planet where it rotted away all of the free floating fuel and starved the purple gang nearly to extinction.

However, the on-demand availability of O2, the fuel-burner, allowed organisms to quickly store up and release large amounts of energy (compare the damage done by rust to that of a gasoline explosion). This then set the stage for large, multicellular life (us).

With the purple gang dying off, the green gang began to compete heavily for the total light supply. More light was becoming available naturally as the purple gang died, so there was (for now) no reason to re-jump to a completely new biochemistry. In fact, the O2 was practically a light-maker, cleaning the ocean's windows of their purple residue.

With the light-competitors dying off, why bother with all of the work required to switch back? Of course, you'd also need a new purple light-catching biochemistry which didn't rely on the now-spoiled food used by the old "purple gang".


#### Contextual Equilibria
What does the story of oxygenic photosynthesis have to do with Bitcoin mining?

Instead of:

1. Green Life Evolves to Eat {Purple Light, CO2, Water}
2. Oxygen is Produced
3. Oxygen {Spoils Other Foods, [Makes Larger Body Sizes Possible](http://link.springer.com/article/10.1007/s11120-010-9593-1#page-1)}
4. Today, we see Large Green plantlife but not Large Purple plantlife.

...we have:

1. Mining Eats {Electricity, Capital} to Produce Coins
2. An Initial Distribution is Produced
3. The Initial Distribution {Creates a Dominant Money-Network, Destroys Rival Money-Networks}
4. We see only the Dominant Money Network


Individuals bought coins, or mining equipment, with a certain expectation. As more and more individuals do this, it becomes harder and harder for cryptocoin-competitors to compete with the network-effect of money. For the same reason, it becomes harder and harder for any *Bitcoin version* to compete with the original Bitcoin version. Even long after the *initial coin distribution* serves its **initial** purpose of creating a viable network, the *present-day coin distribution* will be forever serving its **present-day** purpose of creating monetary network-effects. 

## Conclusion
For the foreseeable future, there is no meaningful alternative to either proof of work or mining.