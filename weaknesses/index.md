---
layout: page
title: Weaknesses
---

[Linkable/Pullable GitHub Version](https://github.com/truthcoin/www.truthcoin.info/blob/gh-pages/weaknesses/index.md)

This section is a constant work-in-progress. **Please help by offering your constructive criticism.**  

Most importantly, keep in mind that **the design can certainly be improved**. It has already happened `3` times.

Also (although this is certainly a cop-out), keep in mind that the existence of multiple competing Branches may cause "clever" human-behaviors to emerge.  
For example:

- Branch owners publishing their real identities or using web-of-trust/similar technologies.
- Authors/Traders waiting to act (add Decisions / start trading) on a given Branch until after the Branch completes an upcoming round of Voting.
- Voters buying shares from traders pre-resolution.
- Vote-Ownership reacting to Author/Trader suspicion.
- Mining pools offering branded/reputable veto-assurance services.



## Might be a problem

<!--

Removed as I think it would be best for people to turn to the whitepaper for this.

### A Malicious User Buys >Phi% of a Branch, Disrupts the Honest Resolution of Outcomes and Exploits Traders

This is the most severe failure case, and deserves a bit of discussion.

- Damage Control:
	- Only Decisions on the attacked-Branch are compromised. Decisions on other Branches are safe. Markets which contain Decisions from several Branches are only contaminated along the dimension of the attacked-Decision(s).
	- Only Decisions from one single Ballot, within the Branch, are "profitably" compromised. Once the first Ballot has been attacked, no one will expect future Ballots to be resolved honestly, largely limiting the damage to one "surprise". The Listing Fees are structured to encourage equal-size Ballots across time, so it is unlikely (but clearly possible) that there will be one disproportionately consequential Ballot. Their equal-size minimizes the (still high) damage (which would occur at max(BallotRevenue_t)).


- Recourse:
	- High, Uncertain, Nonlinear Costs of Buying: If buying up 20% of a Branch costs x, then buying up 40% necessarily costs >2x. This is because sellers of Branch-VTC will not have exactly the same willingness-to-sell, and those with higher w-t-s will be selling before those with lower w-t-s. The cost of buying up Phi% (which is always >50%) is highly uncertain, and may even be infinite (if 1-Phi% refuse to sell at all). Of course, if an attacker could credibly commit to purchasing >Phi%, this cost would fall to zero (the future [post-attack] value of the Branch's VTC). However, as long as VTC-owners have some reason to retain their coins, this credible commit will itself always cost the "high value".
	- VTC-Owners can simply refuse to sell, or can even counter-buy. As long as an honest group controls between (1-Phi%) and 50% of the vote, they can force an Audit, and profit if the Audit agrees with them (by getting *half* the Voter-total of Trading Fees, instead of *their ownership-%*). With (1-Phi%) oneself (or with a sufficiently loyal backing), one can trigger an attack of this kind and profit from its failure.
	- Miners can veto Ballots; by doing so, the Vote simply has no effect at all. Miners can also veto Branches, allowing Decision-Authors to pull the Decisions from that vetoed-Branch onto a different Branch. One would expect Miners to always act in the best interest of the currency they mine, although Miners may also be lazy and uncoordinated (less so if the attacked-Ballot is truly devastating). Distressed users might actually rent hashpower themselves, to force vetos into the longest chain.


- Discouragement / Prevention:
	- Scale-Gaming: Likely, the cost of Phi% of a Branch (lost post-attack) necessitates a correspondingly large expected attack-revenue. In other words, only huge attacks are likely to be profitable. However, rare/huge attacks are precisely those which would receive the most attention (or, even, any attention) from Miners, and rare/huge attacks are also those in which it is cheapest for Miners to halt.
	- Attacker has most MarketCap At Stake.
		- Post-attack, the entire market cap of the Branch would likely be wiped out, costing the attacker disproportionately (Phi is always > .5).
		- 'Big' doesn't need to imply 'Evil'. A user with a high % of the Vote also has proportionally more to gain by acting honestly.
	- High Market Cap: The higher the market cap, the more difficult it is to own a high % of the market cap. This would favor the creation of few, large Branches over many small ones.
	- An "Honest Coalition" might reveal their identity publicly, and proclaim openly (or sign binding legal documents affirming their intention) to always vote honestly. 
	- Competition Among Branches
		- In economics, the phrase "Market for Lemons" refers to a situation where the buyer, wary of what the seller is selling, simply decides to assume the worst (and not buy). It is then the seller's problem to create trust, which he can do in any number of creative ways.
		- One way would be for Branch owners to purchase huge quantities of "Branch Insurance" (bets on honest resoulution) from other Branches. Skeptical traders can try to hedge this way, and market prices can give some indication of reliabiliy and/or coverage.
	- Change Requiring Miners to be Voters
		- Mining and Voting are quite different, and in-particular, the use of merged mining implies that we re-use the existing set of miners (who wouldn't be happy about being asked to do additional work).
		- However, if one wanted true Sybil-attack resistance, the inevitable conclusion would be to create a one-block, one-vote rule, and then perform SVD on the sealed blocks. The obvious downside is that, because there are only about 1000 blocks per week, only so many voters would have their votes counted. The appropriate aggregation of the two vote-dimensions (work and VTC-ownership) would also require some thought.

-->

### Design is Too Complex

While this project aspires to be the simplest "Bitcoin 2.0 project" (consisting of Bitcoin with new dimensions [Branches, Votecoins, Decisions, Markets, and Shares] and new message types). Nonetheless, Bitcoin had several severe bugs (enabling counterfeiting or outright theft) which were only discovered after years of real-world testing. It is likely that this project will have a correspondingly higher number of bugs, discovered over a correspondingly longer period of time (several years).





### Project Inspires Widespread Legality/Social-Acceptance of Prediction Markets

While "software" in general continues to improve, individual pieces of software die off quickly. (Similar to biological evolution: while a species may become more adapted to its environment over time, each member of the species dies very quickly). While prediction market software can only continue to improve, this particular piece of software can likely be out-competed by any organization which would legally bind itself to provide accurate data (the so-called "trusted third party"). All [value-storers](http://www.truthcoin.info/blog/limits-of-blockchain/) have historically been targets for theft, fraud, racketeering, and taxation, but some value-storers are targeted more than others. Bitcoin is likely to outlast the entire financial-services industry (which is rife with middlemen of all kinds), where as Truthcoin may not be able to compete with a prediction-market internet-business operating in a pro-business jurisdiction.





## Probably Not a Problem

### Voters don't follow Branch Instructions on What Counts as an 'Unclear' Question

The outcome-resolution process works best when there is tacit ("unspoken") coordination among voters. To make coordination tacit, the scheme encourages voters to act as "double-agents", and try to form-and-betray small attack-coalitions which fail.

![Reward Function](/images/agreement_reward.svg)

Therefore, voters may lie to each other on how they plan to vote, in general (which makes the only credible coordination tacit). While ordinarily fine, this might be somewhat inconvenient on 'Unclear', which is fine, but for the fact that ambiguity is itself ambiguous. This might lead to 'too much work' being done by Voters (who neurotically attempt to answer even the most perplexing questions), or Voter-anger as the SVD-resolution doesn't turn out exactly as expected.

**If there is *any* degree of confusion or discomfort about an outcome, Voters should report it as 'Unclear' or '.5'. This is a crucial element of the design.**

However, the damage is limited to Voters only: Traders are only affected if they trade on "unclear Decisions", which they wouldn't do (because, for a start, they wouldn't know what they were buying). Expectations of low-trading would discourage Authors from ever making "unclear Decisions", so they are unlikely to exist.

### Miners are too lazy to ever veto anything, making the miner-veto an empty threat. (Or: "Veto is overly complicated and unnecessary).

The Miner-Veto accomplishes several goals at once (a "threat" being only one of them). The most important is to serve as a 'fail-safe' to prevent any blockchain reorganization for vote-strategic reasons (in other words, an effort to say "we didn't like the vote-outcome, so we are hard forking the entire transaction history). The Miner-Veto is in no way a requirement for the outcome-resolution process.

Nonetheless, the Miner-Veto is not an 'empty' threat, as it supplies uncertainty to attackers. Attacker coalitions will be concerned with "pretend-attacks" to draw them off equilibrium, so all sources of attacker-uncertainty are valuable in disrupting cartels.

Ultimately, the Miner-Veto is actually quite important, as if we take only the fundamental assumptions made by Bitcoin (that no attacker controls a majority of hashing power), and if we are further comfortable with the extensions to that assumption made by sidechains (that a 51% miner-coalition will not form, even when it can now steal a known quantity of coins [instead of merely pseduo-steal coins by reversing a subset of transaction history]), then we would achieve perfect zero-trust by allowing miners to vote, with one-block-one-vote encrypted votes.

This perfect-security comes at the cost of practicality: miners do not actively manage the blockchain, except under the gravest of rare circumstances. Sadly, the "miners-as-voters" concept does not scale to even a few Decisions. However, we can exploit differences in the scale of rewards and costs to try to get the best of all worlds: the only profitable attacks being large ones which are almost entirely disruptive, and these being exactly the types of attack which miners would veto.

![Scale Differential](/images/attack_scaling.jpg)

Above: Attack-Scale figure from whitepaper. Notice that the cost-of-truth has been matched (triangles) with the realistically-expected usage: More expensive truth-sources are rarer.


### (With Audits) X% of Voting-Influence ( 50% < x < Phi% ) Attack the Outcome Resolution Process 

A coalition of attackers will not be able to easily coordinate on what they attack, primarily because they cannot guarantee [1] what this will cost, or [2] that they will be able to 'settle up' after the fact (as they might arrange whilst planing the attack).

It then stands to reason that an attacker would acquire a large proportion of voting power, and then simply attack many (or all) of the Decisions at the next opportunity. However, this is discouraged by the Audit.

 When many Decisions are targeted at once, it is very easy to tell, in the Audit, that a mistake has been made. This is because Auditors do not need to assess each Decision, only the 5 most popular unique Ballots (large sets of Decision-choices). In practice, because of the incentive scheme of SVD-consensus, there will likely be only 2 unique Ballots for Auditors to consider. The more Decisions targeted, the easier it is for each Auditor to notice (and communicate to others) that one of the two is simply wrong. (For an interestingly-parallel but purely-coincidental discussion along these lines, see [this](http://www.scottaaronson.com/blog/?p=1820)).

Quite by design, the Audit becomes 'harder to clear with the severity of the attack' in other ways. The first is that, in attacking for large profits, the attack must tie up capital as speculative bets within many Markets. However, only 'free money' can be used to vote in the Audit. The Auditor-votes are, by accounting definition, third-parties to the dispute. The second effect a severe-attack will have on Audit-reliability will be to provide a greater reward (more Trading Fees disputed over) and therefore encourage thoughtful participation.

### Between 50% and Phi% Voters Voters attack only a few things at once

The attacker-coalition probably wouldn't make enough money to be worth it. Strategic frictions (which few do we attack?, who attacks what?) would likely unravel the attacking coalition.


### Authors Won't Make "Enough" Money Back

That is primarily for the Authors to worry about, who may be playing more than one role or have complex motivations. Authors can choose not only how much they pay upfront, but also the fraction of trading volumes they receive.

Trading fees are collected from literal MSR-powered trades, but also from 'transfers' of MSR-created shares (ie, traditional stock market trades).

For popular 'stock market' assets, these trading volumes are measured in the trillions. Despite its numerous disadvantages, InTrade saw trading volumes in the [10's of millions USD on its more popular markets](https://www.intrade.com/v4/markets/contract/?contractId=743474). 50% of .1% of that is still $10,000.

If only popular markets were authored, that would seem to be "mission accomplished".

### Scalability

If scalability is neither a problem [in Bitcoin](https://en.bitcoin.it/wiki/Scalability) nor in [the more-ambitious Namecoin](https://wiki.namecoin.info/index.php?title=Scalability), I have yet to discover a reason why Truthcoin would be especially subject to scalability problems. Unfortunately this is kind of a "big if" as Bitcoin appears to be having some trouble with scalability.

The vote-matrix (only assembled once per Tau of each Branch) is Voter by Decisions, but both are economically constrained: Decisions are capped, and within the cap Decisions are restrained by increasing fees, and Voters have a diminishing return for constant work (this strongly discourages dust-voters). Each Branch creates a new set of Voters, and a new Vote-matrix...this scales linearly.

Moreover, Vote-Matrices, their Decisions, and their Markets will "fall out" of the blockchain as they are resolved and sold off. Only the currently used data structures need to be available to anyone.

Moreover, Truthcoin is different from Bitcoin in that, even with only a few hundred (rich, informed) users, the project could still have a tremendous impact on society. Most of the benefits lie in the cheap *option* to participate, which does not need to be exercised, and in simply displaying the blockchain's data. Likely, TC will have fewer users than Bitcoin. People purchase several times a day, but very rarely does any individual bet/invest/trade as often.

Whatever the case may be, clever people are thinking up new scalability solutions all the time.


## Definitely Not a Problem

### Ballot-Stuffing (Sybil attacks on Voting)

Only Votecoin-owners can vote, and votes are weighted by percent-of-total-ownership. Votes are weighted by proportional-ownership in an abstract-corporation, so there is a cost (and opportunity cost) to obtaining more voting-influence.  

This would be comparable to buying all of the shares of a bank, and then attempting to vote to give yourself all of the bank's money, while hoping that the depositors do not withdraw their money from the bank.

### Exploitation of the Automated Market Maker

The concept of an AMM does make individuals nervous, but the market-maker does not need to exercise any judgment or decide anything. It is a completely deterministic representation of the trade-history and nothing more. It also happens to be nothing more than a single simple formula for cost (who's derivative is the prices). See my [Excel demo](http://www.truthcoin.info/papers/LogMSR_Demo.xlsx), and scroll down the rows to learn more.

### Markets about Vague Events, Gibberish or Personal Opinions

There is a fail-safe-option, to vote directly between True and False, or at the midpoint of a Scaled Decision, and so coordinate on "the" common answer to such questions. In this way, traders will be able to perfectly understand the future value of nonsense-assets.

Resolving to this failsafe may have negative repercussions for the Decision Author, I haven't decided yet. As Decisions already cost Listing Fees (as an economic control), there might be no real reason for imposing any penalty.

### Voter Exhaustion

Voters are given an incentive to vote on every Decision, and for this reason the total number of Decisions is capped per Branch. Voters can own as many Branches as they can tolerate working for.

Moreover, it would be entirely possible to have "overflow Decisions", which would be different from standard Decisions in 3 ways: no requirement to vote, voter-reward only goes to those voters who chose to vote, voting-rewards limited to the trading fees accumulated to each Decision. In this way, we could likely list as many Decisions as we wished, with the Decision-author being directly responsible for bootstrapping their Decision's trading fees.

### Markets Resolving "Too Slowly"

Decisions will likely resolve in large batches, every 2 months or so. Many assume that this process is too slow, and that something should be done to provide "faster" (or "instant") resolutions. It is elementary Finance that markets react instantly to information about future asset values; Markets do not track the value of the future assets themselves. During a volatile event, such as election night on a close presidential race, prices will rise and fall nearly-instantaneously (as expectations change), and settle near their final values (as expectations settle). At this later point, individuals can cash out by selling to Investment-Banker-types

The key is resolution-accuracy, resolution time is a nearly-irrelevant detail.

### Many Decisions on the Same Topic

One might think that, as this relies on "individuals having different priorities on what to lie about, while existing in one single universe", one could run that logic in reverse, and force at Vote Matrix to be mostly "about" a specific thing one was going to lie about, and (relatively) less-about other goings-on in the rest of the universe.

This actually won't work, because Markets (from which attack-profits are derived) are actually *defined* by the Decisions they reference (so the attack would be pointless either because all Markets reference one Decision [why have the others?], or  because many Markets reference many different Decisions [who cares about the 'question theme'?]), and are each treated equally, as separate columns, by SVD-resolution. 

In fact, because it lowers total info-search cost for the Vote Matrix, a thematically-similar Vote Matrix is probably harder to attack.

