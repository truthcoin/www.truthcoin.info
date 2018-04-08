
    Fusing Two Coins
    Paul Sztorc
    Jan 15, 2018



Note: The below post is just a draft. You will notice that many of the images I plan to make I just haven't made. So this draft is for historical purposes only, I suppose, as I now strongly prefer the sidechain-based Fusion process.

This post is about fusing two blockchains into a new, third blockchain. 

(This post is not about how to make the new blockchain useful, nor about how to convince people to use it.)


### Core and Cash

    "We're not so different, you and I."
    -Dr. Evil to Austin Powers, Austin Powers: International Man of Mystery (1997)
    

[^1]: Ironically, the roles of Dr. Evil and Austin Power are both played by actor Mike Myers.

Once a blockchain [splits](/blog/forks-and-splits) into two, it becomes very hard to put them back together. In practice, it may be impossible.

On the other hand, it might not be so bad. Bitcoin Core and Cash are overwhelmingly similar in nature. Most of the code is exactly the same, most of the messages are exactly the same.

Even most of the *owners* are still exactly the same! Check out [this resource](https://forks.network/) (ht [Jameson Lopp](https://twitter.com/lopp/status/941873621466787840)), which shows [the divergence of the two chains](https://forks.network/dashboard/db/bch-btc-fork?orgId=1).

~~image comparing them on outputs moved and coins moved~~

These numbers show that 76.4% of the accounts, and 53.3% of the economic value, haven't been touched at all since before August 1. The two networks are *at least* that synchronized. They may in fact be much more synchronized, because BCH's mandatory replay protection means that all outputs will be permanently split, whether or not this is what the user intends. For example, Alice could send Bob 2% of her BTC and later 2% of her BCH. On an individual basis, the networks would be 100% synchronized, even though on a UTXO basis they are only 98% (or possibly 96%) synchronized.

I find it remarkable that, after many months (five since Aug 1st, two since [Nov 8th](https://lists.linuxfoundation.org/pipermail/bitcoin-segwit2x/2017-November/000685.html)) of drama and contention, we know empirically that at least 76% (and possibly 100%) of the network state is still the same. Perhaps this is why a few people will speak

### You Are Your UTXO Set

Theoretically, if two [Monies](/images/true-money/) have the exact same ownership set, they must be the same. For example, US dollars and US cents have the exact same ownership set -- anyone who owns 4.73 US dollars automatically also owns 473 US cents. US dollars and cents also have a mandatory [Full Replay](/blog/mahf-and-replay/) of each other -- not only is there no replay protection, but everything is 100% replayed. If someone buys a two dollar cup of coffee at Starbucks, then we can define --without loss of meaning-- them as having "broadcast a txn" on "the US dollar blockchain" which "spends two dollars". After putting the transaction in those terms, we can say in turn that their "US dollar transaction" was "replayed" on "the US cent blockchain".

(Luke-Jr was one of the first to recognize the centrality of the UTXO[^2] when he put together a flowchart about hard vs soft forks[^3].)

[^2]: Failure to appreciate the Centrality of the UTXO has contribued to confusion in other areas. A popular recent issue is "Bitcoin Governance". "Bitcoin" as "money" (ie, as an evolving UTXO set) is quite different from "Bitcoin" as a GitHub repository or Bitcoin as a piece of software or Bitcoin as a set of rules. The first is a Wladimir dictatorship, the second and third are equivalent to each other and do not involve governance at all, as there is no "group decision" and indeed no group at all. In contrast to those examples, "Bitcoin as money" (ie, Bitcoin as in the phrase 'I own 45 Bitcoin') does involve a 'group decision' and is therefore subject to a conversation about "governance", ie how this question is decided. Certainly, most of the answer is 'Satoshian Consensus' (ie "consensus", "cryptography", "the blockchain", "Proof of Work", etc), but this is not complete. Money is social information, and all social information has a kind of circular definition: it is whatever other people say it is. This is not to say, however that the definition is useless or unstable. All English words have definitions which are stable and useful, despite the fact that the definitions are also update-able. For example, the definition of "server" originally had nothing to do with computers. Words and money are cooperative tools. Satoshi's blockchain is a tool to make it easier for human beings to synchronize with their trading partners, just as a hammer makes it easier to build a house, or a car makes it easier to travel great distances.

[^3]: Unfortunately I can no longer find it.


We can apply this theory to Core and Cash. At the moment Cash forked from Core (around August 1st), the two had identical histories and therefore each could be called "Bitcoin". They were still quite similar as of Nov 8th when the SegWit2x fork was called off and [the price of BCH tripled](https://coinmarketcap.com/currencies/bitcoin-cash/).

However, they have been steadily diverging from each other. This implies that one of them is becoming "less Bitcoin-like" (because each distinct concept needs to have its own distinct label)[^4]. Of the two, BCH has lower levels of network activity (specifically, [fewer transactions](https://bitinfocharts.com/comparison/transactions-btc-bch.html)), and a much lower[^5] [market capitalization](https://coinmarketcap.com/currencies/bitcoin-cash/) (indicating that the market believes that Core is more likely than Cash to be useful in the future); and both of those disparities are very stable as they cover the entire lifetime of BCH's existence. So BCH is less-used today and will probably be less-used in the future. If it could succeed on one of the two metrics it might have hope, but since it falls short on both metrics, I think we can clearly say that it is BCH that is **in the "diminishing position"**. By this, I mean that as the UTXO sets diverge, BCH becomes less and less equal to Bitcoin.

[^4]: I suppose that it is theoretically possible for *both* children of a blockchain-split to become less like their parent over time. But this is clearly not what is happening with Core and Cash. Although, it would explain the inclination of many Cash-supporters to try to brand the Core side as "Bitcoin Segwit". "Core" referring to something which predates SegWit2x, but "SegWit" [at least, in the sense of: 'a network with SegWit activated on it'] referring to a concept that arose at around the time of the split (ie, around August 1st). In other words, the Cash supporters want their rival to have a name that is just as "new" as their name. See [this image](https://www.bitcoin.com/wp-content/uploads/2017/10/bitcoin-forks.png) on [this Bitcoin.com page](https://www.bitcoin.com/info/bitcoin-cash-is-bitcoin) to see this technique in action.

[^5]: The appropriate interpretation of the chart, in the context of my argument, is to notice that the golden line labeled "Price (BTC)" never rises above the value of 1.0.

If I am right, then the BCH-ers should be getting desperate for a compromise. By [Metcalfe's Law](https://en.wikipedia.org/wiki/Metcalfe%27s_law), a compromise may maximize the market value of each BTC. If so, we can use a prediction market to easily determine the optimal compromise -- below I will use a 75-25 compromise for simplicity.


## Blockchain Fusion

As I've explained above, critical aspect of the Core and Cash blockchains is their respective UTXO sets. I will now discuss a practical way of fusing two different UTXO sets.

The method was motivated by some basic observations:

1. It is most practical to start with a hard fork (so that we can break whatever rules we need) of a "host" blockchain. The host will start as one of the two child blockchains, in our case Bitcoin Core. It will then end up as the third new blockchain -- the refused combination.
2. The hard fork will allow one "special block" (SB) which will allow one or more "special transactions" (STs). (These txns may have version 'ffff' to underscore their explicit abnormality). The STs are only valid in while inside of SBs, but they are "special" txns because they can do anything. We will simply whitelist the ST (as well as the SB), so these txns will always be valid (no matter what they do).
3. Preparation will be required. We need to examine both blockchains and calculate the desired outcome. Then we can manipulate the host into transforming into that desired outcome.

From those, here is the most-practical recipe I could imagine:

1. First, prepare by examining both blockchains. Specifically, the goal is to be looking at a table/database of the UTXO set of each network.
2. Flag each UTXO as belonging to one of three categories. First: "both" for UTXOs that are present in both child-blockchains (ie, both Core and Cash). Second: "host_only" for UTXOs that are only in the first of the two child-blockchains (in our example, this would be money that could be spent by a Bitcoin Core wallet, but not by a Bitcoin Cash wallet). And third: "donor_only" for UTXOs that are only in the donor blockchain (ie, only on the Cash network).
3. Define an 'aggregation function' to use on the values of each UTXO set (see below).
4. Use the aggregation function to compute a new partial-UXTO set. In other words, we want to know what the final UTXO set should look like, and we know that the "both" UTXOs will be unchanged. So we need to combine the other two sets into one combined set.
4. Use an ST to spend the host_only outputs, even though they don't belong to us. We will select the host_only outputs, and spend them to the combined set.


### The Aggregation Function

In other words, imagine someone owns 10 BTC and 32 BCH, distributed across UTXOs in the following manner: 7 in a "both" UTXO, 2 in a "host_only" UTXO, 1 in a different "host_only" UTXO (this makes 7+2+1=10 BTC) and finally 25 in a single "donor_only" UTXO. The aggregation function would determine how much they would own of the new, third token (let us call it BFC for "Bitcoin Fusion Coin"). As I mentioned above, I will use a 75% 25% weighted average so as to make for a simplified demonstration, but in practice the optimal aggregation may be anything, see below.

    ~~ (75%, 25%) ; (10%, 90%) ; sum everything ;; anything above z=10 coins ~~

With one sidechain-enabled network, Core and Cash should have identical feature-sets (or strictly superior feature-sets). Post-sidechain, Core and Cash should be more valuable combined than separate, by Metcalfe's Law. But, how exactly should we combine them? We might use a prediction market to forecast the optimal mixture (which may very will be (100%,0%)).


    ~~ Diagrams , creepy dark transaction ; block validation checkpoint ~~

Viola! The chains have been recombined.


### Ignoring Dust


We can be confident that "dust" outputs (outputs of 1-100 satoshis, worth fractions of a penny) which existed on August 1 have not been moved since. So, they are near-certain to be in the 'both' category. 

Dust outputs that have been created since, will be more of a thorn in our side. First, we do unappreciated work -- the ST must become larger, as an entire new output must be selected (as an ST input), but it is almost certain that the coin's owner has written off this output and does not care about it. Second, we cannot (with current technology) create fractions of a satoshi. So any outputs of just a single satoshi leave us with a problem.

It is probably best to immediately assign any host-dust to the 'both' category, leaving it unchanged. Donor-dust we might simply ignore. These outputs supposedly represent [less than 0.05% of the economic value of the chain](https://eprint.iacr.org/2017/1095.pdf), so hopefully we can be forgiven for abandoning them.


## Fusion-Fission -- Jumpstarting A LargeBlock Sidechain

Again, by Metcalfe's law, it should be better to have one network instead of two. So, it should be best to have Core and Cash merged into one sidechain-enabled blockchain. However, it costs one Core-txn for Cash-supporters to escape to the hypothetical Cash sidechain.

Why not *guess* which UTXOs are a better fit for a LargeBlock sidechain, and automatically teleport them to the sidechain. We will use again use ST (ie, use hardforks to "cheat", ie to get around paying for expensive miner-based tx-state updating).

    ~~ second image ~~