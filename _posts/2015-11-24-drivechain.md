---
title: Drivechain - The Simple Two Way Peg
comments: true
---


> With sidechains, altcoins are obsolete, Bitcoin smart contracts are possible, Bitcoin Core and BitcoinXT can coexist, and all hard forks can become soft forks. Cool upgrades to Bitcoin are on the way!

![Logo](/images/drivechain.png)


## Intro

### Agenda

1. Explain the principles of the sidechain-concept, and what problem must be solved to make sidechains possible.
2. Explain how an SPV proof works.
3. Propose my own SPV proof ("Drivechain" - [skip there now](#drivechain-a-simple-spv-proof)), and explain the relevant economic and technical tradeoffs.
4. [FAQ at the end](#faq), for those who read minimally (including [comparison to Blockstream's Appendix B](#other)).


### Reminder

Sidechains allow Bitcoin to be fully programmable. Unlike the 'smart contracts' of a *general* environment like Rootstock/Ethereum, each individual sidechain is completely "opt-in": by default, users won't be affected *at all* by any new programming.

#### Existing Work

In Appendix B of the [sidechains whitepaper](https://blockstream.com/sidechains.pdf), the authors declined to provide a full design, and warned that "this discussion is not exhaustive; optimizing these tradeoffs and formalizing the security guarantees is out of scope for this paper and the topic of ongoing work."

That's what we'll be doing here.


#### "What is a two way peg?"

A two way peg allows one to transform 'vanilla' Bitcoin into all the other 'flavors' of [Altchain](https://en.bitcoin.it/wiki/Alternative_chain) one might imagine...and back. The total quantity of money ('ice cream') remains the same. This combines the **best of both worlds**: developers can *modify* Bitcoin however they like, but users can keep their BTC away from any new rules ("new vulnerabilities") that they don't like.

Explained another way: a 2wp enables you to "buy" and "sell" Altcoins at a fixed rate. You could take 3 BTC, use them to purchase 3 side-Litecoin at a fixed 1:1 exchange rate, send those Litecoin to a friend on the Litecoin-chain, and then this friend can then redeem them at the same same 1:1 exchange rate (for exactly 3 BTC, which re-appears on the Bitcoin chain). Unlike today, every Altchain would start with a zero quantity of coins, and so the total number of coins, of all types, would always sum to "21,000,000" (ie, "the 'current total number of BTC', a value which asymptotically grows to 21 million).

The question is: how do we pull that off? I will first describe the problem and then my solution.


## Problem Statement
> We want to satisfy two constraints: [1] allow some BTC to change their transfer-rules, [2] prevent the original BTC from being affected by these new rules.

### Moving to New Rules ("The Easy Part")

#### Requirements

It is easy to get coins to change their protocol rules: we can already do that, with Altcoins.

However, that is a *one-way* transfer, and we need ours to be "two way". Transactions must go "from Mainchain to Sidechain" (way #1), as well as "from Sidechain to Mainchain" (way #2).

Since they are going to be two different chains, a "round trip" of a BTC to-and-from the sidechain would involve a total of four new things:

1. A BTC, owned by A, leaves the original chain ("Transfer Out of the Mainchain").
2. Then, A's BTC appears on the Sidechain ("Transfer Into the Sidechain").
3. Later, the very side-BTC in #2 (now owned by B) leaves the Sidechain ("Transfer Out of the Sidechain").
4. Finally, that BTC (owned by B) reappears on the original Bitcoin blockchain ("Transfer Into the Mainchain").

#### We're Halfway There Already

Hopefully it is clear that **the "xfer Outs" are very easy** to do: your Bitcoin is your property, and you can already send it to any address you want, including [addresses which imprison the BTC forever](https://blockchain.info/address/1BitcoinEaterAddressDontSendf59kuE).

![Waste](/images/wasting-money.jpg)


#### In fact, we're (3/4)ths there!

Ultimately, moving "from Main to Side" isn't going to be a problem either. That's a ["one way peg" and was described by Adam Back (and others) in 2013](https://www.mail-archive.com/bitcoin-development@lists.sourceforge.net/msg04315.html).

It is easy, because the two chain-types have *different* advantages: [1] the Sidechain can adopt *any rules we require* (after all, we're designing it as we speak), and [2] the Mainchain will (we assume) [a] always exist and [b] always have a healthy amount of mining power behind it.

So, we can simply **design the Sidechain such that it must watch the Mainchain for "coins imprisoned a specific way"**. Anyone wishing to transfer between the two chains, is certainly using (if not "running") a full node of each.

Specifically:

1. Joe instructs that 12 of his BTC be moved from one of his BTC (mainchain) addresses to one of his CosbyCoin (sidechain) addresses.
2. Joe's software creates a transaction such that it contains [an OP_RETURN "xfer out"](http://bitcoin.stackexchange.com/questions/29554/explanation-of-what-an-op-return-transaction-looks-like), where the extra data is simply Joe's CosbyCoin address.
3. Obviously, this transaction is valid. Joe's mainchain-BTC is transferred away (we will defer our explanation of *where* these BTC go until later), and the OP_RETURN data enters the Bitcoin blockchain.
4. The CosbyCoin protocol (being aware of the Bitcoin blockchain) allows Joe to validate a transaction which generates 12 BTC at his CosbyCoin address. This transaction references the transaction in steps 1-3.
5. This transaction "confirms" after 6 (?) blocks (remember that this chain can have new rules of any kind, and might have a 10 second blocktime, or a 20 year blocktime, or outright remove blocking/mining altogether).

![conversation](/images/cross-chain-convo.png)

Figure: it is easy to do one-way pegs. Nothing is required of Bitcoin at all (in fact people might already be one-way pegging to Bitcoin...we'd never know, and we can't stop them).

So, it's been quite easy (so far).

### Moving Back to Old Rules ("The Difficult Part")

#### Problem Dog

![ProblemDog](/images/problem-dog.png)

Getting this last quadrant (lower left) is the real trick.

|    .         |**Mainchain** | **Sidechain** |
|--------------|:-------------|:--------------|
| **xfer Out** | Very easy.   | Very easy.    | 
| **xfer In**  | Difficult.  | Pretty easy (see immediately preceding section). |


Let's focus on it.

#### What to Ignore

Recall that our original problem statement included: "[2] prevent the original Bitcoins from being affected by these new rules."

This implies that, by definition, **the Bitcoin chain <i>can't</i> even be <u>aware</u> of the Sidechain's rules**. Otherwise we'd have a **hard fork**. However, the mainchain must be aware of the sidechain's *quantity*. Otherwise, we would be at the opposite extreme, where we'd instead have an **Altcoin**. A hard fork directly affects existing BTC, and an Altcoin *indirectly* affects existing BTC; so, neither extreme meets our definition of sidechain.

#### "Just Right" Awareness

Instead, we need something which is *just <u>aware</u> enough*: ignoring the *details* of each sidechain, but observing the *net quantity deposited*. If 12 coins go in to Sidechain X, only 12 can come out.

Bitcoin can already do accounting, so (again), even in this 'problem quadrant', most of our task has already been done for us.

Only one (hard) problem remains: if one message from sidechain X says "these 12 X-coins belong to Fred's BTC address", and a *different* message from sidechain X says that, instead, "these 12 X-coins belong to *George's* BTC address", Bitcoin (the mainchain) needs a way to tell which message is from "the real X". Put another way, our solution is a validation-rule which 'condenses' the numerous off-chain tx (all of the [new] tx-validation rules of the sidechain) into a single, general, on-chain BTC validation rule (ie, "something that Bitcoin can understand", "valid or not valid").

![ValidationTable](/images/validation-table.png)

It needs to *transpose* validation from the "per transaction" domain (left column) to the "per chain" domain (right column).

#### And that's not all.

To be protocol-compatible, someone who installed Bitcoin in 2012 (and never updated it, and refuses to update it for us) must be able to tell if these transactions are valid or not! So, we must do all of this, *without creating any new validation rules*. We can only use the existing ones.

Pretty tricky, right?

#### ( Why do we need to validate at the chain-level at all? )

Well, the *only reason* Joe could have, for 'depositing' his 12 BTC to the sidechain, would be "to use them for something". All uses, of "digital value tokens", are inherently transactional: either [1] Joe will literally transact (in some different-than-Mainchain way: lower fees, 'faster' blocks, more privacy, ...) and send money to someone else, or [2] he will employ some new kind of contract (notarizations, purchases, wagers, etc) which will transact for him, automatically.

So, a sidechain is only useful if it allows a Bitcoin to change ownership. Yet, when it comes time to "withdraw" (sidechain-to-mainchain), **how can the mainchain know who the new owners are**? It can only do this if it knows that the withdrawals are valid (which, by definition, requires us to know that we are on a valid chain).

How do we validate the chain, without validating its transactions? Well, we take something that we already do, and we use it a few more times.

## The SPV Proof
> By trusting miners (to act just-selfishly-enough), we can sacrifice a little security to gain a lot of flexibility.

### SPV ([Simplified Payment Verification](https://en.bitcoin.it/wiki/Thin_Client_Security#Simplified_Payment_Verification_.28SPV.29_Clients)) of Today

SPV is the process by which a "light client" (not running a full node), simply relies on miners for **validation**.

( In [Satoshi's elegant prose](https://bitcoin.org/bitcoin.pdf): "He can't check the transaction for himself, but by linking it to a place in the chain, he can see that a network node has accepted it, and **blocks added after it further confirm the network has accepted it**." [emphasis added] )

The logic is that the miners just *won't* lie: mining consumes effort, yet only produces maximal benefits while it extends "the" longest valid chain. And, 'mining work' can be checked with the blockchain's headers alone (validating these headers is many orders of magnitude easier than running a full node).

Under SPV, if miners mined on top of X, they can convince you that X is true (even if it isn't). However, the cool thing is: **miners mine on blocks, not individual transactions**. They *must* mine on blocks (and, implicitly, a blockchain) and thus they *must* endorse an entire chain; they are unable to single out your transaction (for tampering, reversal, etc), without creating a whole new block, and a whole new blockchain (and, therefore, "wasted" work).

This type of validation successfully 'condenses' tx-validation to chain-validation, as desired.

Simple, right? Now, we simply *extend* its use (from "within a single chain", to "across chains").

### Having The Mainchain SPValidate A Sidechain


#### A Special Lockbox

How will Bitcoin learn about the status of a non-Bitcoin chain? Well, now is the time to return to [the subject which we previously deferred](http://www.truthcoin.info/blog/drivechain/#in-fact-were-34ths-there): the destination of the "Mainchain xfer Out"s. These mainchain-coins are sent to a special address, such that they can only be spent with a certain type of information. Because of P2SH, older Bitcoin clients won't need to understand this "script" (only its hash), so we've met our soft fork requirement. ( These older clients can't *securely* use sidechains, of course. ) The script ("information") which spends these coins is something which "proves" that a certain amount mining was done on an alternate chain.

Essentially: **to deposit 12 Mainchain BTC to the CosbyCoin Sidechain, you'd send 12 BTC into a box that says "To open this box, insert [1] something that says a current CosbyCoin owner wants to xfer coins back to a mainchain address, and [2] proof that 'that thing' was included in the chain, several blocks ago"**.

#### What Type of Lock-box Should We Use? 

If you're bored, skip this section (to ["Drivechain"]](http://www.truthcoin.info/blog/drivechain/#drivechain-a-simple-spv-proof)).

In Appendix B of their whitepaper, the sidechain-authors describe one thing that the box might be programmed to accept. It involves a big Bitcoin transaction which *itself* includes actual [block-headers](https://en.bitcoin.it/wiki/Protocol_documentation#Block_Headers) of a different blockchain.

But, frankly, I don't get it. It relies on "reorg" proofs (which are something of a contradiction, given that miners can [try to] filter these from blocks), and stochastic modeling (ie, an absence of very bad luck) to a degree that I feel is unnecessary.

<!-- This is way too confusing.

1. To avoid needing to dump *all* of the headers into the Bitcoin blockchain, it relies on stochastic modeling (ie, it only usually proves what it says it proves). Bitcoin itself works kind of in a similar way, but there's extra game theory behind the scenes (in that the miners are *paid in* Bitcoin and they can't use that new Bitcoin for 100 blocks) to rig the game so that it is "usually right" and "when wrong, nearly-irrelevant". In this case, being wrong could allow you to steal millions of dollars worth of locked coins.
2. Every time a *single individual* wants to move BTC from the sidechain to the mainchain, they must insert a proof that might be "tens of kilobytes" (the size of 25+ regular Bitcoin transactions). This proof is merely a "receipt for work", isolated from any (potentially useful) context. This is despite the fact that security is entirely at the chain-level, not the transaction-level. This [proof would at least double in size](http://diyhpl.us/~bryan/papers2/bitcoin/wizards/2013-12-18.txt) if the sidechain used merged-mining (which [it must](oracles)).
3. In involves "reorg proofs", such that someone can withdraw from the sidechain, and then the sidechain can reorganize (such that a different chain -with a different withdrawal- is the longest). At this point, more data needs to be dumped into Bitcoin blocks (only to cancel the original data). This introduces additional complexity, both technically as well as strategically (as miners 



Zing!

-->

The most curious things about it are:

1. Conceptually: it neglects to fully-exploit the 'condensation' of transaction-level security to chain-level security. Each transfer needs to re-prove its work, even if someone else *just submitted* a ton of similar work. This wasteful re-use of work creates an asymmetry (the theft-revenues of txns vary in size) that leads to a decoupling of incentives. Moreover, miners can "partially attack" the chain, and, on occasion, steal ~10% of the coins there, making it difficult and expensive for users to determine who is acting maliciously (and what the appropriate response should be).
2. Game-theoretically, it fails to capitalize on something called "consistent best-response functions". (No matter what form the SPV proof takes, a *malicious* majority miner-coalition has a "best response" where they effortlessly steal *all* of the BTC locked in the SPV-address).
3. Economically, it *avoids* privileging the Bitcoin chain (or, rather, it does not discuss asymmetry vs symmetry at all, or any of the related economic details).
4. I, personally, am still trying to figure out if the proof actually still works if the difficulty is not constant. I mean, can you still skip halfway down the path of headers, if the difficulty follows big sinusoidal oscillations (which it very well might)? What if the miners manipulate the difficulty (which, of course, they are able to do through the timestamps)? If the proof is save for variable difficulty, how does it deal with *diverging* difficulty? How does the "parent chain" come to understand the difficulty level of the sidechain (unless all sidechains are forced to have the same difficulty-adjustment rules)?

It just seems so complicated, and no matter what form the SPV proof takes, it can only prove SPV! Miners can, for free, steal all the coins. 


## Drivechain: A Simple SPV Proof
> Bitcoin blocks *are* SPV proofs. Since miners can always steal from a sidechain, lets give users "strength in numbers" and make the thefts unambiguous, easy-to-spot, and unforgivable.

### Specification

#### Scope

Fundamentally, a feature of any SPV proof is that miners can *fake* the proof, and steal all of the sidechained-coins. This is inherent to the *definition* of a sidechain, and, while it seems to be a vulnerability, it [isn't completely unsettling and can even be beneficial](http://www.truthcoin.info/blog/contracts-oracles-sidechains/#sidechains-the-global-contract) in cases.

As the SPV proof **must** rely on miner approval, I propose that we allow the proof to represent approval directly: have the miners "approve" these transactions in consecutive Bitcoin blocks: a "miner vote" scheme. For security and space-efficiency, the withdrawals (and hence, the votes) are infrequent, and slow, such that there is plenty of time to detect fraud and react to it.

(Please do not worry about the speed. This "slowness" is actually the key to enabling instant atomic swaps, described later.)


#### Process (Side-to-Main Transfers)

Bitcoins on the Mainchain begin the process "locked" in a special Anyone-Can-Spend Output. For clarity, I will represent these Bitcoin as "in" a Bitcoin address which [starts with a 4](https://en.bitcoin.it/wiki/Pay_to_script_hash) (call this the "lockbox address", it may have a globally known private key). There would be one such address per sidechain (and this address may as well be permanent, and it need not literally be an address).

While "anyone" can spend these coins, miners agree via soft fork not to move them unless additional constraints are met. (This might sound risky, but [P2SH was successfully rolled out the same way](https://medium.com/@octskyward/on-consensus-and-forks-c6a050c792e7#8788).)

1. A user (who owns sidechained-BTC) creates a "withdrawal transaction" (WT) on the sidechain. This transaction destroys the sidechain-coins, while specifying the mainchain-destination-BTC-address.
2. Over time, these WTs accumulate on the sidechain. After enough time has passed, these WTs are bundled (coinjoin style) into a single large "WT^" which would pay "from" the mainchain "lockbox address" (it would reference the txns which sent their coins to the lockbox) to each mainchain withdrawal address. At this time, the (mainchain-compatible) transaction ID of WT^ is included in the sidechain's block header.
3. Someone broadcasts this WT^ on the Bitcoin network, and if [1] correctly formatted (see below), and if [2] the quantity is valid (ie, the WT^ doesn't try to withdraw more Bitcoin than the lockbox address contains), this **Transaction ID** (not the tx itself) can be included [in a Bitcoin coinbase transcation](https://en.bitcoin.it/wiki/Coinbase) and interpreted as a withdrawal attempt.
4. Everyone waits for a period of, say, 3 days. This gives everyone an opportunity to make sure the same WT^ is in both the Bitcoin coinbase and the Sidechain header. If they're different, everyone has plenty of time to contact each other, figure out what is going on, and restart the process until its right.
5. For the next x=1008 blocks, miners vote on approving the TxID, by incrementing some "vote-tally" number. This number could consist of one byte to identify the sidechain, the first 119 bits of WT^, followed by 9 bits for counting, costing a total of 8 bytes per block (included in each coinbase).
6. The vote tally ("z") is bound by rules: [1] each block, z can move a maximum of 1 in either direction, and [2] after x=1008 blocks pass, the tally is erased. These rules are imposed by soft-fork.
7. If the vote tally reaches a known level, Z\*=500, WT^ can be added to the very same block, as a normal, valid Bitcoin transaction.
8. For all Bitcoin txns of this kind (those spending outputs which start with a 4), nodes much check [1] that the first 119 bits of the tx match something in the coinbase data, [2] that the coinbase data indeed has z=Z\* "votes", and [3] that the votes were accumulated over the desired x time period.

These graphics are high-resolution, and get larger if you view them in new tabs, or save them:

![WT-Timeline](/images/drivechain-timeline.png)

Above: a graphic of the Drivechain timeline.

![WT-Transactions](/images/wt-txns.png)

Above: figure of three WTs being combined into a WT^.


Notice that:

1. A miner can add *any* valid WT^ transaction that he or she likes, and can therefore redirect the "lockbox coins" anywhere. Because Bitcoin is not aware of any sidechains, it can't prevent miners from adding a WT^ which does *not* match the WT^ embedded in the sidechain header, and so the miner might attempt to simply award all the coins to himself (or to fellow members of a >50% miner-coalition).
2. Votes will only continually increase at all, if >50% of miners agree with the WT^ (because an alternation of up and down votes would generate no net progress). Thus, a Z of 504 (half of the maximal 1008 [as x was 1008 blocks]), actually implies that as many as 75% of blocks must contain an upvote (and a 26% miner coalition can veto the transaction). Thus, Z can potentially be a "low" number like 300, or 100, and still require >50% hash approval.
3. This protocol contains, within it, a second (optional) soft fork where miners outright refuse to build on a chain which does not contain "the correct" WT^. In this case, the sidechain's security is equal to that of Bitcoin's.
4. The waiting period always produces a net increase in total information, and prevents anyone from being misled (or falsely claiming to have been misled).
5. The withdrawal-process might take as long as two weeks (or more). In other words, a user who owns sidechain-BTC, and creates a transaction sending those back to his (mainchain) Bitcoin address, many need to wait a long time for that transaction to "confirm" (again, this sluggishness is what enables instant transactions, more later).


### Drivechain's Security

This model allows a 51% miner coalition to actually steal Bitcoins. How likely are they to do that? What factors influence their decision?

#### Overview

##### Increasing Safety

Keeping a sidechain alive provides two things to Bitcoin miners:

1. Bitcoin can do more stuff, hence the market value of each BTC should increase (which is good for miners, who are paid in BTC).
2. The sidechain would itself be a source of transactions, and transaction fees (paid in BTC).

##### Decreasing Safety

1. Miners can steal all of the money locked away in a given sidechain, and they can easily split this up amongst themselves.

##### Metasystem Features

1. Mining pools have brands, and suppliers (those who actually own/control the mining hardware and can point it anywhere), and customers (passionate, anarchist Bitcoiners who own guns) whom they want to please.
2. Dishonesty among miners may break a 'social contract', not only for an individual sidechain, but also for *all* current sidechains, *all* potential future sidechains, and even Bitcoin itself.

#### Security Models

I'll describe the security assumptions in levels, which *increase* as we become *more-pessimistic*.

**Level 1**: If the sidechain is popular, Bitcoin users may choose to take the optional "second soft fork" and reject any block that has an inconsistent WT^. This would make the sidechain just as secure as the mainchain. The only way that miners could attack either chain would be to rewrite and reorganize them both, which bears an economic cost (of wasted energy). The cost of this is that users are obligated to run both nodes, which is as *operationally burdensome* as a mandatory hard fork (both logistically [debating and coordinating the change] and technically [bandwidth, CPU, storage, ...]), but preserves the *ironclad security* of a soft fork (where all upgrades are optional, firewalled, and can be freely enabled and disabled]).

This is one benefit of the 3 day waiting period, and of a length confirmation process in general: users are are free to ignore the world of "sidechain transfers" completely, yet, should someone sound the alarm (on an obvious, intentional, unambiguous break of very clearly defined, slowly-enforced rules), node operators have the option of challenging miners to back down.

**Level 2**: Some users may politely decline to *forward* any block that maliciously disrupts the sidechain process. For example, miners may allow blocks which abstain from voting (and do not change z at all), yet *reject* blocks which either [1] vote against a valid WT^, or [2] vote for (or introduce) an invalid WT^. They can hold out for a "better" block, and use the one that they just received only if they absolutely have to. This policy is itself easy-to-do and decentralized, because information about WT^ is (to any miner running both nodes) objective and deterministically calculable. Everyone who chose to do this would increase the orphan risk for malicious miners, such that miners might actually want to **falsely** claim that they are attacking the sidechain (to trick <50% of miners into actually trying to attack it, to their peril). When the attack fails, the honest miners who played this tricky "double agent" game might profit as a result of their relatively lower orphan costs. Even the option to introduce this policy (or introduce new mining hardware with this policy), would tend to dissuade miners from attempting to attack the sidechain in the first place.

For **Level 3**, we'll get serious, and assume that most Bitcoin users (and miners) don't care about the sidechain at all, *and* that a 51% mining cartel exists and can easily coordinate to split the cash looted from the sidechain.


#### Some Math (ie, Feel Free to Skip)

First, we might write each miner's general financial return as:

{ 1 } .. R =  ( [ u + k ] - c ) / c

Where c is the costs of mining, u is "normal" miner revenues, and k is "attack" revenues. All variables would be a statistical [expectation](https://en.wikipedia.org/wiki/Expected_value) of [present value](https://en.wikipedia.org/wiki/Present_value), and we can assume that miners always want to maximize this return. Thanks to the ongoing difficulty adjustments, miners who fail to optimize their returns will eventually be operating at a loss. I'll assume that it isn't possible for a huge amount of malicious, financially-irrational mining power to simply appear (as such bizarre [and necessarily-rare] occurrences could probably be [singled out as unrepresentative and dealt with](http://www.truthcoin.info/blog/measuring-decentralization/#its-not-very-effective)).

Second, let's define the mathematical effect of an attack:

First, I'll simply define p = u/k . If, today, you expect to earn 10 BTC, and a sidechain has 24 BTC stored in it, then: 

* u = 10
* k = 24
* p = 2.4

I'll also break u = (a + b), such that "b" is "all of the revenues obtained from the sidechain's tx fees" (and "a" is "all other revenues the miner earns [coinbase, mainchain tx fees, etc]").

Finally, I'll define m as the "price maintenance" following any attack, where m=0 implies that the Bitcoin price has collapsed completely (to zero) as a result, and m=1 implies that no Bitcoin owners cared at all that the sidechain was attacked. Theoretically, m=1.05 could indicate that Bitcoiners were happy that the sidechain got robbed.

Thus, if PV is the present value operator at interest rate r, then:

Attack Revenues would be all the stolen money, m-discounted: m \* p \* ( a + b )
Attack Costs would be (depreciated coinbases + lost fees), or: PV( a\*(1-m) , r )  + PV( b, r )

Combined, this yields:

 { 2 } .. k = m \* p \* ( a + b )   -  [ (1-m)\*PV(a, r) + PV(b, r) ]

Hopefully, it is clear that safety will increase if [1] the sidechain is producing tons of fees for miners to enjoy, and [2] miners are forward-looking and really care about those fees.
 
#### The Most Pessimistic
 
Most pessimistically, **Level 4** will assume that r = +INF, which would indicate the miners do not care about the future (coinbases or tx fees) *at all*. This eliminates the costs half of the equation completely.
 
If we then compare:
 
 { Attack } .. R = [ (m \* u) + (p \* u)  - c ] / c
 
...to... 
 
 { Don't Attack } .. { 1 } .. R =  ( [ u + k ] - c ) / c
 
...we see **the range of parameters where R is increased by attacking**:
 
 { 3a } .. [ (m \* u) + (p \* u)  - c ] / c > ( [ u + k ] - c ) / c

 { 3b } .. u/c - 1 < m\*( (1+p) \* (u/c) ) - 1
 
which ultimately reduces to:
 
 { 4 } .. m > 1/(1+p)
 
What does this formula mean? Self-interested miners won't "grab coins", if doing-so "excessively destroys the market value of those coins".

For example, if miners can triple today's revenues by stealing from a sidechain (p = 2.0), they would only attack if the Bitcoin price could be expected to remain at least 1/3 of what it was.

Keep in mind that, to get to this point, we've intentionally ignored a great deal: the lost tx fees, and the effect that m would have on future expected mining revenues, and strategic rivalry within mining coalitions, and defensive activity of Bitcoin node operators. 
 
Notice that, if m = 0, we are always safe, because p is unable to approach +INF. The interpretation is comparable to Cold-War-era [Mutually Assured Destruction](https://en.wikipedia.org/wiki/Mutual_assured_destruction) deterrence theory, where it was assumed that rational actors would avoid doing anything that "threatened to destroy an opponent so completely that they had nothing to lose by self-destructing". Given that we're all still alive, it seems to have worked well-enough (for now).

![MAD](/images/cold-war.jpg)

Notice the archery...this is part of the logic for forcing "condensed" all-or-nothing "whole chain level" validation: we would like to force any non-zero 'p' to be just as threatening as 'max p' (ie, if someone can steal *any* coins, then they can steal *all* of them). By making "thefts" worse, we have actually made the concept of a theft **too threatening to be tolerable** (to miners). Then, we simply sacrifice speed *for the direct purpose* of making thefts "worse", while -beneficially- making transfers more infrequent, and thus easier to devote attention to.

For example, if one's nukes (above) were sensitive enough to be uncontrollably triggered by arrows, it would prevent all arrow-related violence. If the nukes would be triggered by *any* intentional military action, then there would be no intentional military action.

#### Why m might be pretty low.

One might worry that m is high, ie, that no one would care about the sidechain (such that any p>0 makes an attack inevitable). Well, **it depends on the sidechain**.

Dumb sidechains (those whose value-add and transaction fees aren't worth the network/computational resources consumed) are a waste of node/bandwidth capacity, and *should* be removed from the system. For these sidechains, [m may even be >1](http://www.truthcoin.info/blog/contracts-oracles-sidechains/#who-cares), guaranteeing an attack and eventual theft. This is desirable, and (fortunately) Drivechain encourages this desirable activity, which guarantees that (even better) no one will spend effort developing or depositing-into a "dumb sidechain". (If a sidechain becomes "dumb", miners can credibly demand that users withdraw their money from it immediately.)

"Useful" Sidechains should not be attacked, and we'd hope that m would be low for these.

It probably is. Notice:

* Miners had to agree to start merged-mining the chain, implying a commitment which is broken if they later decide to attack the chain (alternatively, Miners can "nicely" warn users -in advance- that they intend to stop supporting the sidechain [perhaps, with signals or messages in the mainchain coinbase]).
* If Miners attack a single sidechain unexpectedly, it makes it likely that miners will attack all other sidechains.
* In fact, all future sidechains are now less likely to succeed, and we can't expect them to arrive at all (or provide services / fees).
* If a 51% miner coalition forms, and destroys all sidechains, one wonders if Bitcoin itself will be attacked. Users may wish to hard fork to a different hashing algorithm, not only out of a desire for revenge/deterrence, but also out of an imminent existential need.


###  Magnifying Security 

#### AtomSwap and the Convenience-Security Tradeoff

##### Subgame Perfection

It is a known result in game theory that, if it is common knowledge that a player has the **credible** option to take some action X, (s)he can make a "credible threat" of performing X, and never has to actually carry the threat out. The threat alone, if credible, is just as good as the real thing.

##### Compliance with AtomSwap, thanks to Drivechain's Threat

There is already something which permits 2-way transfers, and, while this technique does not 1:1 peg the transfers, it is fast, convenient, and perfectly secure. It's called ["Atomic Cross-Chain Trading"](https://en.bitcoin.it/wiki/Atomic_cross-chain_trading), a name which I will shorten to "AtomSwaps".

If only these AtomSwaps were pegged, they'd be 100% perfect for sidechains. Fortunately, we can use Drivechain to add a "market peg" to AtomSwaps, thus completing the puzzle. 

We do this by providing users with a credible threat (which they never have to execute) to use Drivechain. To see how this works, temporarily assume that Drivechain's (slower / more inconvenient) 2-way-peg exists and operates with perfect reliability. Arbitrageurs would then be able to sit as middlemen, doing Drivechain behind-the-scenes and AtomSwaps for customers. These swaps would be at prices which are nearly-pegged, such that the arbitrageurs can collect a commission for their services.

##### Minimal Loss

How small is this commission likely to be? Well, the modern risk free [rates](http://www.marketwatch.com/tools/pftools/) are nearly zero, even negative in some countries. My rough calculation is that, currently, 1 USD discounted by a year is 99.69 cents. To buy a dollar next month, it would then cost about 99.974 cents, and to buy next week's dollar it would cost you 99.994 cents. These four values are nearly identical. Even when risk-free rates are at their highest (say, 20% annually), this comes out to a weekly rate of less than half a percent.

Of course, these bargan prices are only achievable if there *actually is* a risk-free alternative.

#### Is Drivechain a RiskFree Alternative to CoinSwap?

##### Risk of What?

Let's examine under the conditions under which the alternative is risky (ie, *not* risk free).

Since main-to-side transfers are fast and secure, the total quantity of sidechained-BTC can always increase "on-demand" (and, from there, AtomSwaps can take over). The only source of risk would be that the miners might coordinate to steal sidechained BTC.

##### A Bad Equilibrium

That isn't very encouraging. It is a little like saying: "Things will be fine, until they aren't."

The "bad equilibrium" (where things aren't fine) is as follows: [1] Miners attack a sidechain, [2] making it doomed, and therefore useless, leading to [3] no one wanting to own it at all (relative to BTC), leading to [4] AtomSwap (which requires a buyer and seller) not working, leading users to rely on Drivechain, yet, [5] Miners are attacking the sidechain, therefore Drivechain is unreliable. Drivechain is only reliable if Miners are honest, yet it would only need to be used if Miners are dishonest! (This paradox is no accident, as I stated above, it necessarily follows from the game theory exploited in the AtomSwap alternative).

##### Shrinking the Event Horizon

First, we will want to lean as far as possible on the security side of the security/convenience tradeoff, to make it as difficult as possible for miners to attack the sidechain. As (thanks to AtomSwaps) there really is **no** convenience tradeoff, merely the risk-free rate (one of the most forgiving tradeoff rates possible), we want a lengthy transfer period (perhaps totaling two weeks or more).

A lengthy transfer period means that, while miners can steal all funds in all sidechains (true regardless of transfer period, or even of SPV peg type), there's really no room for misinterpretation: miners are doing this because they want to do it. The clear implication, of such brazen theft, is that an SPV peg will never work, and that Bitcoin can never have sidechains ever (and instead must use [[centralizing] hard forks](http://www.truthcoin.info/blog/measuring-decentralization/#development-100-decentralized-unless-we-hard-fork) or ShapeShifted Altcoins). Either that or Bitcoin will just need to wait for [new technology](https://bitcointalk.org/index.php?topic=277389.0). Such an outcome would teach us all to reconsider Altcoins as laboratories of innovation, and would encourage bright minds to work on the problem of mining centralization.

Second, there's the roll-up of transaction security to chain-level security. This alters incentives such that, if miners plan to steal, they may as well steal everything. By eliminating the middle ground, the system can't drift toward (or away from) this equilibrium, nor can it mix with the equilibrium: it must make a conscious, deliberate leap. It also levels the playing field between small depositors and large depositors -- a kind of "transfer fungibility" (such that security does not depend on transfer size).

##### Escaping the Event Horizon

###### What can help?

We need a way of making the Miner's attack on the network less-likely to succeed.

Well, only one group of people can fight off attacking miners: other miners.

Fortunately, we may indeed be able to expect circumstances in which Miners fail to coordinate.

###### Equilibrium AtomSwap Sales

First, notice that miners are those who are most likely to offer AtomSwaps to users. Since miners know their own ability/intent to attack/prevent-attacks (whereas non-miners must estimate this), miners have a unique advantage in bearing this risk: AtomSwaps are just cheaper if the Miners do them.

Even if miners don't supply this service day-to-day, they are the obvious "supplier of last resort" and most relevant to this security analysis.

Miners would not want to ever own a proportion of "at risk" coins which significantly exceeded their proportion of mining hashrate. As their holdings increase, rival miners have more to gain by stealing from them.

For example, if we split the total network hashrate into 5 groups:

|    .    | Scenario A | Scenario B | Scenario C | Scenario D |
|---------|:----------:|:----------:|:----------:|:----------:|
| Miner 1 | 1          | 4          | -96        | 2,000      |
| Miner 2 | 1          | 0          | 25         | 2,000      |
| Miner 3 | 1          | 0          | 25         | 2,000      |
| Miner 4 | 1          | 0          | 25         | 2,000      |
| Miner 5 | 1          | 0          | 25         | 2,000      |


Where each row represents an agent with (1/5) of the hashpower, each column represents a different outcome, and the cell values represent the payoff to each miner. If 100 coins are attempting to move side-to-main, the payoffs sum to 100 if the miners act dishonestly (and steal everything), and 5 if the miners act honestly (assuming, arbitrarily, that they charge 1 for an AtomSwap service which moves 20 coins).

Scenario A is in a "good" state of equilibrium (miners bought the 100 coins and transferred them). In Scenario B, Miner 1 has undercut his opponents, and provided cheaper CoinSwaps for 0.8 each. As a result, other miners have an incentive to move to scenario C, stealing these 100 coins (all owned by "Miner 1", who purchased them for 96) for themselves; ordinary (non-miner) users are unaffected by this political in-fighting.

Hence, miners have an incentive to sell CoinSwaps in proportion to their hashing power. This helps to avoid incentive-imbalances among miners. If a miner coalition announces their intention to steal, unless they are overwhelmingly confident in their success (ie, have 80+% of the *future* network hashrate), they may find themselves involved in a "second battle" over the "pre-stolen property". Especially if reinforcements *might* arrive, days later, in the form of full node operators, it probably isn't worth it.


###### Alternative Assumptions (high m, finite r)

Scenario D is a separate "worst case scenario" reality, in which the sidechain currently contains a total of 10,000 BTC, and miners agree to steal (and split) all of them. This outcome is overwhelmingly rewarding to miners, and will only be secure (at Pessimism Level 4) if m is very low.

Scenario D is, of course, the most salient concern. The allure of the 10,000 coins requires a low m, but what if m is not low? Well, we will have to become optimistic in a different way (retreat to Level 3), and assume that miners do, in fact, care *slightly* about the future.

For starters, we can consider the transaction fees paid by users of the sidechain, which will fall to zero if miners attack the chain.

How high are these transaction fees likely to be? There's no way to know for sure, but Bitcoin itself currently pays roughly 0.125 BTC in transaction fees per block. If unchanging, this translates to 6,574 BTC per year, and discounted in perpetuity at an aggressive APY of 15%, would yield a present value of 43,826 BTC (currently worth about **14.5 million USD**). At an overwhelming rate of 40%, this stream of tx fees would instead be worth 16,435 BTC (or roughly 5.5 million USD).

If a sidechain, in steady-state, achieved similar transaction revenues as present-day Bitcoin, we can expect millions of dollars of future trading fees to be lost in the event of an attack. Moreover, even if m is not near zero, we can expect it to be <1, which reduces the value of **all** the BTC trading fees and coinbases mined on *all* chains; if there are a total of 5 other chains -all with comparable tx-fee revenues-, including the mainchain which offers a coinbase equal to, say, 5x the base tx-fee level, then, even if m is merely the relatively-high value of .95, we have losses of 5% on combined revenue streams worth 10x the sidechain tx-stream. The result is that total miner losses are *further* increased, by 50%.

Of course, chains with more transactions are likely to also contain more coins. The relevant question "Is the PV of all trading fees greater than the total quantity of coins I could steal?" is completely unanswerable at this time. However, I conclude the security analysis by noting that there will always be *some* PV of trading fees, encouraging miners to protect the network.


## FAQ

### Use of Sidechains

#### If I want to use a sidechain, how do I use it?

Just send your BTC to the sidechain's address (in a certain way), and you can use the sidechain's new rules / features immediately!

#### I've won/lost Bitcoin on the sidechain, how do I take it back to the mainchain?

Use atomic cross chain transactions, ie "AtomSwaps" to trade instantly (and securely) with someone who wants to 'buy' your sidechained coin.

#### What? What if I can't find someone who wants to buy my sidechained coin for 1 BTC?

It is overwhelmingly likely that competing professional 'investment banker types' and/or Bitcoin miners will want to buy the sidechained coin for almost exactly 1 BTC. This is because they intend to use a side-to-main Withdrawal Transaction to shift the coins back to the Bitcoin mainchain, which facilitates the 1:1 peg. By charging you a fee, these individuals can be compensated for the inconvenience of locking their BTC into an uncertain process for a few days.

Absent such individuals, you can yourself use the side-to-main Withdrawal Transaction process, which takes a few days but is otherwise "free". Once every few weeks, miners will rubber stamp the sidechain as being "in consensus", and you will then be able to spend any withdrawals from the sidechain on the Bitcoin mainchain.
 
### Security

#### What is the security risk of placing my BTC on a sidechain?

While your BTC are on the sidechain, a >51% coalition of Miners can steal your money. 

#### Wow, that sucks. Can anything be done?

Mostly, no. The definition of sidechain implies the use of SPV proofs, which implies trusting miners. Maybe something crazy like zk-snarks will be invented, but that would probably involve an upgrade to Bitcoin which would make it substantially different from what it is today.

What can be done is to arrange circumstances to make miners maximally unlikely to choose to steal your money. One way is to arrange things such that miners never have an excuse for allowing funds to be stolen: if they're stolen by anyone, we'll know that the miners stole them in a really slow, obvious, and intentional way. Such brazen theft would indicate [1] that Bitcoin would be (in the near future) without sidechains of any kind, and [2] that Bitcoin itself may be in danger from the miners (and we may need to *consider* using an alternate proof-of-work hash function).

In addition, we lump sidechain-transactions together, and deny miners the option of selectively attacking: their only option is a wildly irresponsible attack on everything (which they would probably never do). For certain extra-important sidechains, we can increase pre-commitment by having sidechain-users (selfishly) refuse to forward malicious Bitcoin blocks, increasing orphan risk for malicious miners but leaving regular miners unaffected. We can even consider destroying sidechained-coins, just before they are stolen (a threat which is reasonably credible and thus never needs to be executed).


### Other

#### How is this ("Drivechain", or "DC") different, or more specific, from the concepts in Appendix B of [the sidechains whitepaper](https://blockstream.com/sidechains.pdf) (the "Blockstream Version", or "BV")?

Drivechain itself is most-similar to this suggestion:

"If we expect many transfers per sidechain, we can maintain a special output in the parent chainwhich tracks the sidechain’s tip. This output is moved by separate SPV proofs (which may be compacted in one of the above ways), with the result that the parent chain is aware of a recent sidechain’s tip at all times."

The SPV proof is different in a few ways:

1. Asymmetry: My vision for sidechains is very asymmetric, with each sidechain as a kind of "plugin" to Bitcoin, such that everyone must run a Mainchain "full node". Moreover, I assume that all sidechains will be merged-mined, which implies that Bitcoin miners have consented to mine the sidechain, which they would only do if the sidechain [1] generated revenues in the form of BTC transaction fees and/or [2] provided Bitcoin with some kind of a service which increased the purchasing power of each Bitcoin. Moreover, as some miners are aware of the sidechain (in order to merged-mine it), I assume that all miners can become aware of a sidechain's header, within the 3 day waiting period.

2. Security: The BV relies on stochastics (ie randomness) to shrink its (huge) SPV proof. To explain via metaphor, it attempts to use weather data to prove that "10 years have passed between Date A and Date B" by pointing out that, between A and B, it can show you 140 photos of the same NYTimes [dispenser](http://preview.turbosquid.com/Preview/2014/05/16__00_00_00/2.jpg50974740-c2d9-4f9b-a18b-7ea85f5bba29Original.jpg) while it snows in the background (and you know that there are typically only 14 snowy days per year [this post coming to you from New York City]). Unfortunately, the highly random circumstances of Bitcoin, whose SHA256 hashes are [uniformly distributed](https://en.wikipedia.org/wiki/Hash_function#Uniformity), parallel our random weather fluctuations...sometimes it snows a lot, and sometimes it doesn't. These fluctuations result in "skips" (from one snowy day to the next), which can result in complex problems. DC endorses its transfers with 100% of the mainchain's work, by involving each passing Bitcoin block in the validation process.

3. Speed: The symmetric transfers described in BV take over 2 to 4 days. In DC, main-to-side transfers occur almost immediately, but side-to-main transfers are intentionally very slow (1-3 weeks) with the goal of promoting a liquid market for atomic swaps (which take place instantly).

4. Transparency. The BV constructs a proof which is checked for validity at a single point in time, whereas DC involves the user in a slower, ongoing process (which reduces surprises). Moreover, BV handles blockchain reorganizations with "reorg proofs", whereas DC handles them in realtime through the voting process (or, more precisely, not at all, because DC is so slow that a sufficiently-relevant reorg is overwhelmingly unlikely to occur in the first place). Miners may conspire to filter out / prevent-awareness of these reorg proofs (in fact, to me, the concept of a reorg proof is something of a contradiction).

5. Redundancy: BV does validation on a per-tx basis, not a per-chain basis. This means that, in BV, lots of work will need to be redone, for no reason. DC has the reverse problem, where any number of withdrawals, no matter how few, must execute the entire (slow) chain-validation process. However, again, small WTs are unlikely to occur at all, as miners can buy up many small sidechain-BTC using AtomSwap (for a mutually beneficial, low, fee) and then withdraw all of these at once.

6. Size: To enable the transactions themselves, both methods require additional data be fixed to Bitcoin transactions. BV requires each Bitcoin header to contain an additional 32-byte hash, while DC requires this of the Sidechain headers. BV also requires proofs which logarithmically contain the actual headers (each of which is [200+ bytes](https://en.bitcoin.it/wiki/Merged_mining_specification#Aux_proof-of-work_block)). The paper provides a sample figure as "into the tens-of-kilobytes range", which one could interpret as 50,000 bytes per transaction. To transfer as many as 100% of the Bitcoins back to new mainchain owners, DC requires (in the example figures provided above) 500 blocks to each contain an 8-byte indicator, making the total size 4,000 bytes. Note that BV can support an unlimited number of sidechains, whereas (with the parameters provided) DC can only support a maximum of 256 sidechains.

7. Simplicity: Some parts of the sidechains whitepaper are difficult to understand. The more complex something is, the harder it is get volunteers, including (essential) third-party reviewers, open-source developers, etc. to help out.

#### I do not know about soft forks. Clarify what it is that you propose.

Well, basically, your Bitcoin software would have to do a tiny number of additional things: 

1. Check each block's coinbase transaction for any extra data.
2. Check this coinbase data to see if any of it can be interpreted as related to WT^s. 
3. Check that WT^s are being updated according to "the rules".
4. If those first three are true, update the database to reflect this.
5. Check anything which spends a sidechain-output, against the database, to make sure that it is spendable.

In short, the "unspent outputs" of a certain category ("sidechain-outputs", which in my example are those paying to an address which starts with a '4') would need to be monitored separately. To spend these outputs, all of the existing Bitcoin rules would apply, and then more on top of that (specifically, the conditions listed above).

The downside is that, post-soft-fork, you can no longer write *just anything* to the coinbase transaction. You have to put in a tiny amount of effort to check that "the extra data you wish to insert" couldn't accidentally be misinterpreted as *invalid* WT^ data.


#### Would this drag some Bitcoin transactions "off chain"?

Yes. Moreover, the sidechain may "compete" with Bitcoin if it offers similar services (ie, a service which transfers value-tokens). This is actually the point: to allow protocols to compete on "being a good medium of exchange" *without* forcing them to also compete on "being the single store of value".  

The Bitcoin mainchain is overwhelmingly likely to remain dominant for several reasons: It is the oldest and most technically conservative (and thus the most reliable), most people are already there (network effects), and it is the only chain with coinbase rewards (ie which creates new money, in addition to collecting transaction fees). Most of all, and it is the only chain which doesn't itself support merged-mining, which makes it the natural leader (it is literally unable to follow...like a blind orchestra conductor).

Notice that Bitcoin miners get *all* transaction fees (paid in BTC), regardless of which chain they were paid on. So, if one assumes that the fee/message price does not change, then it is impossible for sidechains to cause a decrease in total transaction fees.

However, by allowing BTC to escape to other chains, the blocksize limit can be effectively circumvented. Thus, any fee-premiums which existed as a result of the supply limit would tend to disappear (which would, then, cause sidechains to decrease the fee/message price).

#### Can you talk more about the relationship between sidechains and the blocksize limit?

The use of sidechains would indirectly remove the blocksize limit altogether (by effectively creating ["extension blocks"](https://www.mail-archive.com/bitcoin-development@lists.sourceforge.net/msg08005.html) of unlimited size and quantity). Miners, by [externality logic](http://www.truthcoin.info/blog/contracts-oracles-sidechains/#comment-2272074576), would tend to want larger blocks, so they would allow extension blocks to happen. Fortunately, in this case, the commons tragedy is avoided, because users who do not wish to store more than 1MB per block, can simply decline to run the "extension nodes" that make this possible.

This seems to be, dare I say it, a "win win" solution to the blocksize problem (or, at least a strict improvement). After all, [BitcoinXT](https://bitcoinxt.software/) and/or [BitcoinUL](https://github.com/BitcoinUnlimited/BitcoinUnlimited) could simply *be* sidechains of Bitcoin Core. If users of "sidechain BitcoinXT" refused to abandon it, and refused to return to Bitcoin Core, then Core and XT could coexist (they could share mining power, and share the 21 million BTC).

#### Sounds good. Can this do anything bad to Bitcoin at all?

No, I don't think it can.

It may seem inappropriate to give such a brazen "no", for such an important (and vague) question, but, if you think about it, **sidechains = trusted third party + blockchain**.

The protocol, for both sidechains and a trusted third party, is:

1. Send money to an address.
2. Things Happen.
3. Someone withdraws money from that address.

The only difference between the two at all, is that the Things in #2 are enforced by a blockchain. So it is difficult to imagine Sidechains "doing" anything bad, because what they are able to do *is a subset of what can already be done today...by anyone*. It's like you, the consumer, worrying that  other people will shop at a store run by honest and efficient robots...well, those "other people" can *already* shop at an equivalent store run by humans, so how can altering *their* experience (by replacing humans with robots) make *you* any worse off?

If you're worried about a sidechain being somehow bad for Bitcoin, logical consistency demands that you be equally worried about "people doing Bad Things with their Bitcoin"...because they're almost the same thing: the only marginal difference is the blockchain's *increased* transparency, reliability, and immortality.

I can think of only one negative impact: those who are overwhelmingly opposed to upgrading Bitcoin, on principle, would not enjoy the fact that this software allows upgrades to be more thoroughly tested and explored (thus making these upgrades more likely to eventually take place).

That's it. ( And that single problem speaks to the [concept of "incompatible principles"](https://www.youtube.com/watch?v=TgjrS-BPWDQ&t=25m53s), which is fundamentally non-resolvable: an opposite group could, with equal justification, complain that updates are being 'pointlessly' stalled. )

Fundamentally, we are shielded from malevolence by these three facts:

1. Any bad thing would, by definition, harm the price of BTC (if allowed to happen).
2. All sidechains (and, even, "all transactions") need (ongoing) miner-approval.
3. Miners are paid in BTC (and they prefer "having more money" to "having less money").

To elaborate: while it is possible to use a Sidechain to [precommit](https://en.wikipedia.org/wiki/Precommitment) to some previously-unconvincing threat, and while it is possible to use precommitment to incentivize "something bad" (for example "difficulty oscillations"), miners can and will [decline to allow](https://en.wikipedia.org/wiki/Price_of_anarchy) these threatening phenomena. This is, in fact, yet another reason why [it is actually a *good* thing that Bitcoin miners need to approve every new sidechain](http://www.truthcoin.info/blog/contracts-oracles-sidechains/#sidechains-the-global-contract), relative to Rootstock/Ethereum's "miners", who, to accomplish something similar, would instead need to examine/demystify all network messages individually.

Because sidechains require effort on the part of the miners, they're actually quite conservative. In fact, I only expect around 10 sidechains to exist.

#### What sidechains do you expect to exist?

Here are a few:

1. Conservative Testnet (for staging upgrades to Bitcoin, which very many people might use).
2. Liberal Testnet (an "anything goes" wild wild west where new features are tested...money is lost/stolen here nearly every day).
3. [Oracle System / Financial Marketplace](http://bitcoinhivemind.com/)
4. [Coin-Mixer / Fungibility-Enhancer](http://zerocash-project.org/index)
5. Casino (Simple games of chance [non-oracle], ie "SatoshiDice+").
6. BitDNS (Some version of Namecoin or Counterparty, which allows human-readable names to "map" into other data).
7. A specialized [lightning network](https://lightning.network/) that buys and sells TOR/VPN/Mesh'ed "anonymous internet".
8. A specialized [lightning network](https://lightning.network/) that interfaces with [SWIFT](https://www.swift.com/) / traditional banking (possibly one sidechain per bank / whatever).
9. Something cool that I'd prefer not to explain right now.
10. One more, to cover everything that I didn't think of.


### Further Directions / Weird Ideas

* Have miners stake their own coins on each WT^, such that they suffer if the WT^ are determined to be malicious (this determination is bad by PoW taking place 10,000+ blocks into the future). These staked coins can be "the block's transaction fees" (which miners can increase to any level, by simply paying fees to themselves). Staked coins could be required to be some % of the total BTC outstanding on the sidechain. Comparable to [the IRS whistleblower informant award](https://www.irs.gov/uac/Whistleblower-Informant-Award/), this would encourage honest miners to trick rival miners into attacking, so that these attacking-miners can be betrayed and stolen from. The net effect is to try to increase miner-mistrust, and thus make miner-collusion more impractical.
* Drastically change Bitcoin (in a reckless and bizarre way), into a "sidechain corporation" in which anyone can buy/sell equity. This corporation is used to manage (via stake-votes) a finite 21 million BTC among 256 "sidechain slots", with the implied economic goal of maximizing the value of all coinbases / total transaction fees.
* Pour more research into mining decentralization in general, specifically things like P2Pool and remote-disabling mining hardware.


### Help Wanted

Please email me at truthcoin/at/gmail if you could like to collaborate on implementing this.

One brave developer has already volunteered to help code this, both of us are a little mystified on the appropriate way to even set up the github repo(s) of this type of project (one that contains at least two software applications, and two blockchains, which might be updated in concert), so that would be a pretty helpful Step 1.

### Note on Commenting

It might be most helpful (to everyone) if all technical questions are posted immediately below, and most news/interest/effect questions are posted on social media sites.


<!--

## Banished Sections


#### Optimizing the tradeoff

is the most forgiving value in all of finance.  

The only reason one would *not* make the side-to-main transfer *as slow as possible* would be that the benefits themselves start diminishing: people don't take a whole year to decide such things, and once they decide, they don't revise their opinion. So, likely a two week period is sufficient.
 
#### The Sidechain Equivalence Conditions

Currently, a 51% coalition of Bitcoin miners can perform double spends by [1] spending BTC and [2] constructing a longer chain which does not contain this spend. They are discouraged from doing this because the successful 51% attack would devalue their mining hardware (and the 100-block-escrowed new Bitcoins which each recent miner is forced to hold) in two ways:

1. It would damage Bitcoin's value-proposition as money, decreasing the demand for Bitcoin and harming the Bitcoin exchange rate.
2. It would scare users away from transacting, decreasing the demand for Bitcoin-transactions and reducing the total quantity of Bitcoin transaction fees (paid to miners).

Moreover, an *unsuccessful* 51% attack results in wasted work (and financial losses).

Let us define a "healthy sidechain" as one which:

1. Net-increases Bitcoin optionality. In other words, increases the number of "cool things" that individuals could do with their Bitcoins
2. Would operate by sending new tx-types around, which, in the process, would generate transaction fees for Bitcoin miners.

Therefore, [superfluous sidechains, as well as parasite sidechains](http://www.truthcoin.info/blog/contracts-oracles-sidechains/#the-parasite-contract) would not be healthy, nor would a sidechain which never generated tx fees.

Therefore, miners should be happy to support any healthy sidechain. In other words, they would [1] help to start up, and [2] not attack any sidechain because:

1. Attacking the sidechain harms the utility of each Bitcoin.
2. The sidechain generates BTC transaction fees for miners.

In other words, the Sidechains would be comparable in security to mainchain Bitcoin. They would be strictly less secure, as a much higher quantity of sidechain-Bitcoin can be double-spent, but in principle they would be similar.

Miners can use sidechains to sneak-increase the Blocksize, if and only if users go along with them.  

### An interesting result.

Since ShapeShifting is more convenient for both parties, the only condition under which one would NOT ShapeShift is when one cannot. Assuming the mainchain's permanence, this sole condition will always be a situation where "no Bitcoin users want the Sidechains anymore". This is very interesting as, if no one wants the sidechain anymore, it is likely that neither of the two Sidechain-Equivalence Conditions hold.

-->