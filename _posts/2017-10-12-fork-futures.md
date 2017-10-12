---
title: Fork Futures (via the Exchanges)
show_author: true
comments: true
date: 2017-10-12 05:00:00
---


> How exchanges can help us, and also profit! While very simple (1 equation!), this includes conditional trades (auto-refunding) and conditional prices ("1x would be worth XYZ if we called off the NYA").

Skip the pitch and go right to [the proposal itself](/blog/fork-futures#exchange-fork-futures).

## Why Fork Futures

Yes -- we're still talking about the blocksize debate!

### What Is The Point In Dispute?

Some things are not disputed:

1. That Bitcoin Miners, and Bitcoin Developers, both serve the *users*.
2. That Hard forks require widespread support.
3. That those who campaign for a "disliked" hard fork [ie, one that users dislike], are "attacking" Bitcoin and damaging it.

What *is* disputed is: <b>do the users actually *like* this hard fork, or not?</b> For SegWit2x, some say yes. Some say no.

### How We Resolve It (Or, Rather, How We "Don't") # {#how-we-resolve-it}

Today, we have bad tools for unraveling this mystery. They include: "social media", "what Greg Maxwell / Roger Ver assumes is good for everyone", and "opt-in coin voting".

Of these, only "coin voting" makes an effort to be truly representative -- but it suffers from the typical voting-problems (no "skin in the game", rational ignorance / inconvenience / "no upside", etc).

And there are questions that even coin-voting can't answer. How *strongly* do coin-owners hold their views? What do *prospective* (but not current) owners of Bitcoin believe?

And Condorcet's Paradox / Arrow's result indicates that voting can only work for, at most, one question at a time. That's too slow.

![image](/images/arguing-senate.jpg)


The question of "is this/any hard fork good?" is one that is made of innumerable sub-questions.

Here are a few of them:

* What is it about the hard fork that users (dis)like? the timing? the content? the precedent? 
* Is there an even better hard fork right around the corner? Or a better *sidechain* maybe? Or will that take too long / be problematic?
* Will developers leave Bitcoin, if SegWit2x goes through? Does it matter if they do? Are there better devs around the corner, [just waiting for the existing leadership to die off](http://www.nber.org/papers/w21788)?. Or are the current devs the only 'unmoved movers' -- the only irreplaceable piece of the machine?
* How will miners react to the fork? If there is *unconditional* support from 95% hashrate, then the minority chain would take *over a year* ( 1/.05 * 2 weeks = 40, + .25/.05 * 2 = 10, + 0.0625/.05 * 2 = 2.5 ; 52.5+ weeks ) to function normally again. But why would support be unconditional? Miners will earn more, if they mine the blockchain which is producing the most profitable coinbase transaction. But *which* blockchain will this be? And how *large* is the expected difference in profitability?
* If coin-owners, devs, and miners disagree about something, how do we decide who's vote is more important, and *by how much* is it more important, and in what context?

### The Spinoff Option

Some argue that we should just create [a spinoff (an Altcoin with Bitcoin's UTXO set)](/blog/forks-and-splits/#glossary), and \*ahem\* let the free-market work everything out.

Unfortunately, this very expensive -- a little like starting a Civil War to change governments. First, it is hard to accept payments on either network during the period of "civil war" -- but since Bitcoin exists *for* the purpose of accepting payments, this approach *disables Bitcoin* during the war. Second, it is directly inefficient -- during the period of war, there are two pieces of software to maintain, two databases to store on one's computer, two prices for users to track, and so forth. Thirdly, during the war, resources are spent slandering / promoting one coin -- but we have no reason to believe that "more resources" will tend to be spent on a "better" chain (in fact, if anything it is likely the reverse). So --even at best-- this is wasteful "zero sum" competition -- those resources could have been spent elsewhere on something useful.

    "The laughter of Mordor will be our only reward, if we quarrel."
    -Gandalf, to the Men of Rohan

Thus, the spinoff is an expensive experiment.

Unfortunately, I do not think it is a very informative experiment either. It does not achieve its goal, which is to measure the relative merit of each chain. The biggest reason for this, is that the Old Chain [the original, "status quo" chain] gets a bunch of supporters that it objectively does not deserve: the indifferent. These people are indifferent between chains (objectively neutral), but since they started on the old chain, they will tend to remain there.

In one sense, of course, this is a very good thing. But in the narrow sense in which I speak today --the sense of trying to measure which chain is "best" for users-- it is a hindrance. 

Moreover, the spinoff option imposes costs on the Old Chain. Users on the Old Chain must suffer fork attempt after fork attempt, one after the other. Like mosquitoes at a Summer barbecue, these fork-attempts command (or "steal", really) our attention -- non-indifferent Old Users may prefer to ignore these-attempts, but sadly we cannot. Since "the indifferent" are a valuable resource, pro-fork campaigners have a reason to assault them. This 'Hard-Fork Harassment' reaches into all of Bitcoin's stakeholders: owners, devs, miners, and users.

In response, people are now *campaigning* for their preferred fork. Yuck!! Or, worse, thinking of themselves as ["defenders of Bitcoin's pristine virtue"](http://lesswrong.com/lw/lz/guardians_of_the_truth/). ( A new blog post on this horrible trend, and how to reverse it, is forthcoming. )


### My Solution -- Futures Markets

As [Kyle Torpey wrote recently in Forbes](https://www.forbes.com/sites/ktorpey/2017/08/31/this-solution-to-bitcoins-scaling-drama-has-been-available-for-over-two-years/), I proposed a solution to this entire set of problems over two years ago. It's slowly gaining popularity -- Jameson Lopp [tweeted about it](https://twitter.com/lopp/status/911994715331022849) a few weeks ago. Last week, [BitFinex announced](https://www.bitfinex.com/posts/221) that they had [implemented fork futures](https://www.bitfinex.com/legal/cst/segwit2x).

Today I'm going to describe my vision for exchanged-based fork futures!

First, I will quickly contrast them with my Old Version. [ You may skip this section. ]

### The Old [July 2015] Version ### {#the-old-version}

My [July 2015 article](http://www.truthcoin.info/blog/win-win-blocksize/) made the case for quickly assembling trustless, 100% software-based, private, "fork futures" to resolve this simple empirical question: If Bitcoin hard-forked into BitcoinXT, would the USD/BTC price increase, decrease, or stay the same?

My project used Bitcoin to operate, but users could actually create synthetic USD (ie the so-called ["BitUSD"](http://www.truthcoin.info/blog/bitusd/)...which, by the way, somehow an entire industry of 'blockchain professionals' is still struggling to make, two years later) and use *that* to trade. This BitUSD would last for the duration of trading on the two 'fork-futures'.

The 2015 version was very permissionless, decentralized, private, and software-based. But it did have a drawback: it required us to pick a trusted federation -- these individuals would be responsible for, if needed, signing a single (very observable, very transparent), multisig message, at the *end* of the process (the maturation of the futures). This message would have the final world, in case people disagreed with what the algorithms said that they could withdraw in BTC. Which was not bad for July 2015 era blockchain technology. I [presented it](https://www.youtube.com/watch?v=TgjrS-BPWDQ&t=1557s) at Scaling Montreal (or tried to, at least).

### Today's Version

The old version had a lot of overall cypherpunk-ness to it. Which was the problem. It turns out, that while 100% cypherpunk probably *is* the best, if you can't reach 100%, you should probably turn around and head back toward 60%. The tradeoffs just fall out that way, if you ask me.

So today I'm presenting the New "60% Cypherpunk" version -- the exchange version. It might initially seem worse, because it:

* Requires users to use an exchange (therefore: fewer eligible traders, and a large loss of privacy). The old way was pure BTC, pure software.
* Requires users to trust that the exchange will pay as promised (and won't get hacked, etc).
* Introduces the possibility of several identical markets, which is bad because liqudity will be diffused among them for no reason. (Although, this may incentivize some exchange to be the "first" to take the risk/reward of offering this kind of trading).
* Is possibly illegal / in violation of CFTC rules. (Good luck figuring that out!)

But it actually is much better, because it:

* Doesn't require "the community" to understand futures markets.
* Is much simpler overall.
* Involves me, Paul Sztorc, doing less work (which is great because I'm a busy guy).
* Allows private exchanges to make money off of this idea. Either by charging trading fees, or just by drawing new customers in / promoting their brand.

As I see it, the chief flaw of the 2015 version was that it *did* require a few important peopl to understand / believe in / endorse the concept of futures markets. Especially since I asked for a panel of ~seven or so functionaries, I was implicitly asking them to endorse the scheme. And [my interest in blockchain prediction markets](http://www.bitcoinhivemind.com/) is precisely because I am convinced that PMs are unlikely to ever receive such endorsements! Like the paradox of "trusting trust", there is a prediction market paradox of "convincing the already-convinced" ie "convincing the overconfident" and/or "convincing the experts". It is like asking the CEO to fire himself, as I will explain [later](/blog/bad-pm-criticisms).

Anyway, today's method (the exchange method) requires less "buy-in" from "the community". And exchanges have a selfish incentive to implement the idea. And people *already* seem to trust exchanges sufficiently. And this isn't as bad as it used to be -- exchanges used to get hacked all the time, but in late 2017 they seem to have gotten much better. So an exchange version is much less of a deal-breaker.


## Exchange Fork Futures

> An appeal to exchanges. The system below might seem a little strange, but it is very easy to implement, and it should make everyone happy.

### Background

#### BitFinex vs Olivier

So if you follow this area, you know that [BitFinex published their exact Terms and Conditions](https://www.bitfinex.com/legal/cst/segwit2x), and that prominent LargeBlocker Olivier Janssens [didn't like them](https://medium.com/@olivierjanss/why-bitfinexs-chain-split-tokens-are-completely-biased-towards-the-small-block-side-again-698395bae619).

In general, I think that BitFinex did a very good job. But it isn't exactly what I would have done, and my way actually addresses OJ's major complaint.

BitFinex correctly noticed that:

1. Symmetry is desirable. The contracts should try to "control" for all other variables...by keeping them the same across both contracts.
2. [Therefore,] there should be two different markets -- one for each token. There needs to be a futures market for the "incumbent chain".
3. Definitions are very important.

However, Olivier isn't satisfied. He has noticed a problem with BitFinex's setup, which is that **the Finex market is about two things** at once: [1] whether or not a fork manifests itself before a certain date, and [2] the market price of the fork, conditional on it existing. Oliver and BitFinex each try to address this problem in opposite ways: BitFinex says if there's no fork, then that is Olivier's problem. They justify this by saying that there is a pool of value which will be split by the fork, and if there is no fork then therefore this implies that 100% of the existing value has remained on the Old Chain. But Olivier says if there's no fork, it should be the exchange's problem: he got gypped and he wants his money back -- therefore the exchange should refund everyone's token.

Both approaches are mistaken! OJ has a justifiable complaint, but he wrong to want *everyone's tokens* to be refunded -- such a policy has many problems! (The biggest is that anyone with a shred of fork-doubt can never have any upside, only downside). But it is fine for OJ to want *his money* back, in the event of some contingency. There's a very important difference!

We can make everyone happy by acknowledging the true nature of the problem: not *enough* futures markets! The solution is: more futures markets!

![image](/images/smith-moar.png)

#### Not Enough Markets

BitFinex created two tokens BT1 and BT2. But I would instead create *eight* new tokens, arranged into *two* markets, in order to fully partition the space of possible outcomes.

                                                "1x Market"        "2x Market"
                                              Short  |  Long     Short  |  Long
     Upper Row -- 2x Fork Appears                1       3         5        7
     Lower Row -- 2x Fork Does Not Appear        2       4         6        8

These tokens are *not* trade-able blockchain tokens, nor will they ever be. Instead, they are ledger entries in the exchange's database -- much more like USD deposits. When the futures mature, all of these tokens will be swapped for their cash value and then destroyed. It is better for them to settle directly in cash, because they can allow users to speculate on scenarios/outcomes that may never actually happen.

#### Is this too confusing?

I think this setup is not as overwhelming as it might first appear, for four reasons:

1. Half of these (tokens 1,2,5, and 6) only enable full-reserve shorting. I'm sure BitFinex has their own system for shorting/margin, which they'd prefer you use. But I much prefer this, where you *buy* a token in order to short. It is part of what allows you to make these magical "refund portfolios" that Janssens wants.

2. I would re-use a fancy trick that I used in my [Hivemind project](http://bitcoinhivemind.com/) -- the automated market maker (details in [appendix](/images/fork-futures-trading-appendix)). This trick provides permanent and generous liquidity across all eight tokens, and it also forces there to be a fully transparent log of all trades (one that can be re-derived from the price chart). It is also much much easier than maintaining eight order books -- trades occur atomically with a single formula, the exchange only needs to track the quantity of tokens issued. Users can *always* trade against the market-maker, so a counterparty always exists -- even for weird trades.

3. This two-dimensional (two dimensions per market, for each market) might appear to be more-confusing to the end-user, but it might only be a matter of good UI. In this post, I am describing what happens under the hood. The user probably doesn't need to see any more than one token at a time -- at the end of this post I will describe optimal combinations of tokens that make purposeful "portfolios". Maybe, in the UI you only buy those. In general, I think that people learn pretty quickly when it's their money on the line.

4. Token 8 should always have a price of zero, by my definitions (below). So no one should be trading it (although in our current ICO world who knows LOL!). And, optionally, Token 3 should also always have a price of zero (see below). So this setup is really not as overwhelming as it might first appear.

From this setup, we gain a lot of benefits. We can learn:

1. [From 1 and 3] What the USD/BTC price of 1x is expected to be, post fork-event. This represents how loyal investors are to the SmallBlockers.
2. [From 2 and 4] What the USD/BTC price of 1x is expected to be, if the NYA is called off and there is no fork-event. If this value is high, it could be used as evidence to call off the NYA.
3. [From 1, 3, 5 and 7] The likelihood of the "Chain Split Event" happening, expressed as a percentage. If this is very low, then the entire discussion is moot because the fork isn't happening. The true damage is the time wasted, talking about something that was never likely to be significant.
4. [From 5 and 7] What the USD/BTC price of 2x would be, if 2x is earnestly attempted. This is what LargeBLockers want to buy, and they can buy it today...maybe even at a discount.

Most important of all, we can wager on each of these things. By wagering on #4, we can build Olivier Janssens his refund portfolio (see [last section](/blog/fork-futures#the-janssens-portfolio)).

Let me first describe how I would do the Terms and Conditions.



### Terms and Conditions

Again, I think that [BitFinex did a pretty good job](https://www.bitfinex.com/legal/cst/segwit2x), but I have some comments.

#### 1. Defining the Chains

Some people correctly noticed that the [BitFinex's two tokens](https://www.bitfinex.com/legal/cst/segwit2x) were not quite properly defined.

The **current dispute** is whether or not "switching to a 2 MB [non-witness] blocksize" will **cause** the network to "become more valuable". The "2x hardfork" is the independent variable, and the "network value" is the dependent variable. And those are the two variables of interest -- one "action" and its "outcome".

So, I would define the "2x Network" (in contrast to the "1x Network") by following the following steps:

1. On January 1, 2018, examine all of the chains traded on major exchanges.
2. Subset these, to those which are "Bitcoin-like" (ie, they have the same chain history, UTXOs, 21 million coin limit / issuance schedule).
3. Subset that subset, to include the Bitcoin-like chains which recently forked to double their [non-witness] blocksize from 1 MB to 2 MB.
4. Of all the networks which did hardfork, select the single network with the highest market capitalization. This is the "2x" chain.

Those steps are a little vague, but you get the general idea.

The "1x Network", in contrast, *can* be defined by simply referring people to these hyperlinks...

* https://bitcoin.org/bin/bitcoin-core-0.14.2/
* https://github.com/bitcoin/bitcoin

...because it is the status-quo. The "control group", as it were.

The exchange should say that they will run Bitcoin Core 0.14, and see what it connects to, and what transactions they can still make with it. That is the 1x network.

#### 2. Controversy Over "Discretion"

Some people have a problem which the following language, of Section 6: "In the unlikely event that only one blockchain exists...then a determination may be made, in the sole and absolute discretion of Bitfinex, as to whether that blockchain is more compatible with...Incumbent...or with Segwit2x".

Personally, I am fully in favor of language like this. The alternative (trying to specify every minute detail in writing in advance) is a lost cause. It will lead to the legal equivalent of software bugs, and DAO-like consequences. And it will lead, also, to long boring confusing paragraphs that no one reads.

In practice, I believe that it will be very easy to tell the 1x chain from the 2x chain. So I don't see anything to be gained by obsessing over it.

In contrast to that, however...


#### 3. Defining the Fork Event

##### This Is Important

In my scheme, the question of whether or not 2x has been "earnestly attempted" is a very important one. If it *has* been earnestly attempted, then four of my eight tokens will have zero value. On the other hand, if it *hasn't* been attempted, then those aforementioned tokens will have some non-zero value, but the *remaining* set of four tokens will be worthless.

The cool thing is that each user has the opportunity to buy some of each set, such that most of them will be *indifferent* between the event happening or not. But we still have to do a great job of defining it.

##### My Criteria

I would say that the (fork_event_has_happened = YES), if all of the following criteria are met:

1. We are able to find a valid 2x chain anywhere (see above process), on or before January 1, 2018.
2. The 2x chain is 'healthy', ie mining enough blocks for transactions to reliably confirm. Specifically, we may say that, between Dec 11 and Dec 22, the 2x chain must advance by at least 600 blocks. And, they must be "legitimate blocks" -- it must be possible (in principle) for the exchange in question to actually make transactions in most [>60%] of these 600 blocks. (This is easy to check, as the exchange probably *will* be making such transactions, possibly in every one of the 600 blocks.)
 
 One very interesting third criterion would be:
3. If, a unique [see first edge-case below] rival 1x Network exists, it must find *fewer than 600 1x blocks* between Dec 11 and Dec 22. This provision would mean that SegWit2x would not "exist" unless the old Core Chain was dead. (In this case, Token #3 would share the "always worthless" fate of Token #8). This adds a very strong dose of symmetry, and may be a better referendum on "whether the NYA actually went through".

![image](/images/tug-of-war.png)

However, to be clear, this criterion #3 should include something-like: "If the 1x network is also the 2x network (ie, if the 1x network has soft-forked to a non-witness blocksize of 2MB or greater [see below]), then this criterion can be ignored." Otherwise, we would contradict our action-outcome principle above.


##### Edge-Cases

For these rules, let us try to clarify some strange edge-cases:

1. If "1x" [ie "Bitcoin Core"] *soft forks* to bump the non-witness capacity to 2MB or more (for example, by using an opt-in extension block or drivechain), and if this network [the "Core-after-it-is-softforked-to-2MB" network] has the highest marketcap of all Bitcoin marketcaps, then the Core network would be *both* the 1x network and the 2x network.

 This has a number of interesting consequences, depending on the inclusion and wording of criterion #3 (above). As currently written, if such a soft fork is expected to happen with 100% probability, then the "fork event" would count as having taken place. Tokens 2,4,6,8 would be worth zero, and the (1,3) pair will be trading for the same values as the (5,7) pair.
 Part of what makes this bizarre is that miners could unilaterally deploy a 2MB extension block at any time. Although that is a bizarre feature of the scaling debate in general, and is not specific to futures markets. For some reason, the pro-forkers are *insisting* on a hard fork. Those who wager that a larger blocksize will yield a higher price, will still earn money under the scheme defined here.
2. If Bitcoin Core "evil forks" to 2 MB, via hard fork, then Core would become the 2x network. It might, theoretically, be the 1x network as well, but (as we will see below) the 1x network will have a price of zero in this case, because it will not have tokens post-fork, and we will not be able to find it's representative price.

 Again, this is rather bizarre, because miners completely control the evil fork. Personally, if you ask me, it is just yet-another-wonderful-thing-about-prediction-markets that they expose all of these contradictions for what they are.

Anyway, now that the dimensions of this setup have been defined (they were: "going long vs. short", "1x Network vs. 2x", "fork event vs. no fork event"), we can talk about the tokens inside of the market.

### Final Token Values

#### Fitting to (0,1)

First, I will be fitting the regular USD/BTC price, the one that we all know and love (defined in the next section), into a narrow unit range (ie, a [0,1] range).

To do this, imagine three metrics:

    Price_A : The USD/BTC value (which ranges from 0 to +Inf)
    Price_B : Price_A, but capped at 70,000 ($/BTC).
    Price_C : Price_B divided by 70,000. 

I chose a max of 70,000 USD/BTC (and a min of zero) because I don't think Bitcoin could realistically trespass this limit before January 2018. These transformations don't affect the user's return on investment.

For example, if Bitcoin Core is worth $4200, then Price_A is 4200 , Price_B is 4200, and Price_C is 0.06. If SegWit2x Coin is worth $0, then all three prices are 0. If SegWit2x is worth $40 million, then Price_A is 40,000,000, Price_B is 70,000, and Price_C is 1.00.

But I have gotten ahead of myself -- where did this "XYZ is worth" measurement come from? How do we get to Price_A?

#### Price_A -- The "Representative Price"

To get Price_A for both the 1x and 2x networks, we need price data from an exchange somewhere.

Probably, the 'exchange providing the futures market' should use its own price data. So the fork futures of BitFinex would use the USD/BTC data of Bitfinex's own BTC/USD trading pair. To do this, BitFinex would need to commit to listing both tokens (conditional on the fork manifesting itself). (Which they should, because it re-emphasizes our concept of symmetry.) I think that this approach is much better than "averaging data across multiple exchanges" or "using an index".

However, how do we turn a stream of "price data" into a single "Price_A"?

I say that we take the closing price for the days Dec 11th through Dec 22nd, and take their geometric average (which is: multiply all values and then take the 12th root [ \*^(1/12) ]). In this way, our definition has some nice properties: it is [1] clear, [2] known to all parties in advance, [3] reasonably resistant to manipulation, but still [4] easy to calculate transparently.

However, I wonder what happens if an exchange has to close during these days? To account for this, we can throw out the four most extreme or missing values, and then take the geometric average of the remaining eight. If anything strange happens (such as an exchange closure) during the 12 critical days, we can discard those days (as one of the four "most extreme" values).

The Dec 11 through 22 dates are arbitrary, but they should be a healthy amount of time *after* the Fork Event would hypothetically happen.

#### Reminder

As previously mentioned, exchanges will be creating eight token-types. Uses will buy these with USD (or with BTC that is automatically insta-converted to USD at time of purchase), and each token will trade at prices that range between $0.00 and $1.00. On December 31st, trading will end, and then in January the final prices for each token will be calculated, and users will automatically be cashed out.

                                                "1x Market"   |    "2x Market"
                                              Short  |  Long  |  Short  |  Long
     Upper Row -- 2x Fork Appears                1       3    |    5        7
     Lower Row -- 2x Fork Does Not Appear        2       4    |    6        8

#### The Rows

We might restrict our attention to the "upper row" (see below), for the time being. These tokens all have a value of zero if there is no fork. However, if there is a fork, they will have a value (in fact, in this case, each pair [1,3] and [5,7] will consist of two prices that sum to value of $1.00). Token 3 is for going long on 1x BTC, Token 1 is for shorting 1x BTC; Token 7 is for going long 2x BTC, and Token 5 is for shorting 2x BTC.

   In the case where the 2x Fork Event is said to occur...

    Market 1 : "Futures of 1x"    |     Market 2 : "Futures of 2x"
          Short   Long            |        Short     Long
            1       3             |          5         7

The "lower row" is exactly the same, except that it tackles the reverse scenario. These tokens are only valuable if the fork *does not* appear. If we go through with the NYA, then the four "lower row" tokens are worth zero. If instead we call the NYA off, then it is the upper row which is worth zero.

As we will see, Token 8 must always have a final value of zero. Either the fork was attempted, in which case Tokens (2,4,6,8) are all worth zero; or else the fork was not attempted, in which case Tokens (1,3,5,7) are worth zero meaning that tokens (5,6,7,8) are worth exactly (0,1,0,0). We will exploit this fact to build OJ his magically-refunding portfolio at the end of this post.

#### The Markets

Now that we understand how the upper and lower rows work, let's talk about the two markets.

The left market is for the 1x coin, and the right market is for the 2x coin. In principle, we could add a "3x" market -- we would just create four new tokens. Or we could create an "8x market" or a "1GB market". Each market has four tokens -- each of the four tokens trades at prices between $0.00 and $1.00, and the four prices of a single market will always sum to the value of $1.00 (as we will see).

#### The Final Values

Ok, enough explaining! Below I give the calculations for the final value of each token.

I assume that we have the representative price of the 1x and 2x networks, and therefore we have Price_C (see above) of 1x and 2x. I also assume that we know which row we are zeroing out. Therefore we only need to make four calculations. We input four zeros for the failed row, and input our calculations (below) for the successful row.

                                                "1x Market"   |    "2x Market"
                                              Short  |  Long  |  Short  |  Long
     Upper Row -- 2x Fork Appears                1       3    |    5        7
     Lower Row -- 2x Fork Does Not Appear        2       4    |    6        8
                                                              |
                                              SLOT A   SLOT B | SLOT C    SLOT D

The explanations are purposefully out of order:

* SLOT B = Price_C of 1x
* SLOT D = Price_C of 2x
* SLOT A = ( 1 - SLOT B )
* SLOT C = ( 1 - SLOT D )

In other words:

    Token_1_price = 0 if (Fork_Event = FALSE), else = (1 - Token_3)
    Token_2_price = 0 if (Fork_Event = TRUE), else = (1 - Token_4)
    Token_3_price = 0 if (Fork_Event = FALSE), else = (Price_C of 1x)
         ...
    Token_8_price = 0 if (Fork_Event = TRUE), else = Price_C of 2x


### Three Examples

That's probably confusing, so let's look at three examples.

#### Example 1

Imagine that it is November 7th, and futures market prices currently look like this:

        "2x Market"
      Short |  Long
      .79     .06
      .15     .0
    
What is going on here? Well, first let us do a little bit of addition, to get some marginal values (literally -- the word "marginal" means: the values "in the margins of the page").

        "2x Market"
      Short |  Long
      _____________
      .79     .06  |  .85
      .15     .00  |  .15
      -------------
      .94     .06

The two prices in the "long" column sum to .06, which implies that this market values the SegWit2x coin at (70,000 \* .06) = 4200 USD/BTC. The market also expects an 85% likelihood that the Fork Event (ie, the "NYA") will go through (because the two prices in the upper row sum to .85).

Ultimately, if the NYA *does* indeed go through...

          "2x Market"
       Short      Long
     .79 /.85   .06/.85    | 1.00
         0          0      |  0

...then the market expects the long price to end up at (.06/.85), which = .07 , and which corresponds to $4941. In other words, SegWit2x is expected to be worthless if it isn't created, but if it is created it is expected to be worth $4941. Since it only has an 85% chance of being created, it is currently expected to have a value of ($4941 \* .85) = $4200.


#### Example 2

Let us imagine it is November 12th, five days later. Example 1 has now changed very slightly -- Token 5 is now four cents cheaper, and Token 7 is four cents more expensive.

        "2x Market"
      Short |  Long
      .75     .10
      .15     .0

Now, we do our addition, as before:

        "2x Market"
      Short |  Long
      _____________
      .75     .10  |  .85
      .15     .00  |  .15
      -------------
      .90     .10

Market participants still believe that the NYA has an 85% likelihood of success.

What's different is their appraisal of SegWit2x's value. This market expects SegWit2x to be worth ((.1/.85) \* 70,000) = $8,235 if it is legitimately tried. So the expected value today, considering it has 85% chance of being tried, is (8235\*.85) = $7000.

#### Example 3

Finally, this last example will be 'full-size' and feature both of the two markets. And lets say that it is November 15th. Over the three days, things have changed for 2x dramatically!

                                                "1x Market"   |    "2x Market"
                                              Short  |  Long  |  Short  |  Long
     Upper Row -- 2x Fork Appears              .372     .028  |   .388     .012
     Lower Row -- 2x Fork Does Not Appear      .552     .048  |   .60      .0

This market has many things to show us!

We still do our addition:

        "1x Market"   |                "2x Market"   |
      Short  |  Long  |              Short  |  Long  |
       .372     .028  | .40           .388     .012  | .40
       .552     .048  | .60           .60      .0    | .60
    --------------------------------------------------------
       .924     .076                  .988     .012


Market participants believe that the NYA could very well fail -- they give it only a 40% likelihood (above, right margin).

    Current               value of 1xBTC = $ 5,320   (ie, .076 * 70k)
    Current [theoretical] value of 2xBTC = $   840   (ie, .012 * 70k) 



The $5320 calculation above should mirror the current price of 1x exactly. In other words, at all times (including on November 15th in this example), the value of .076 should be exactly 1/70000th the *real* Bitcoin price. By "real Bitcoin price" I mean the ["spot price"](http://www.investopedia.com/terms/s/spotprice.asp), the price that is in a normal market (LocalBitcoins or whatever) of the day; not any futures market. If the futures price and spot price are different, we can use this to measure the "risk premium" of the futures market -- it may indicate that the market is biased or that counterparty risk is higher on this specific exchange.

Whatever the biases of this particular exchange may be, the $5,320 price for the 1x network should be an almost perfect apples-to-apples comparison to the $840 price for the 2x network. That's one of the advantages of a setup like this.

Finally, these prices reveal the *really* good stuff -- the conditional info.

    1. If Yes Fork, value of 1x:  $ 4900
    2. If  No Fork, value of 1x:  $ 5600    
    3. If Yes Fork, value of 2x:  $ 2100
    4. If  No Fork, value of 2x:  $    0

They were calculated (from the eight market prices, far above) as follows:

    1. ( .028/.40 ) * 70k
    2. ( .048/.60 ) * 70k 
    3. ( .012/.40 ) * 70k
    4. (   0 /.60 ) * 70k

This market implies that all of its participants believe, collectively, that 2x is less valuable than 1x. It says that, while 1x is currently worth $5320, if we forked to 2x then that token would only be worth $2100. Interestingly, however, this market thinks that we *should* fork! This is because, if we fork, the original coin will only go down by $420 (from $5320 to $4900). But we will get a new token (for free) that is worth $2100. So that is a user-surplus of $1680!

While this is good for users, it is, amusingly, bad news for miners! Miners can only mine one chain at a time. So even if they pick the more-valuable chain, they must take a loss of $420.

( If only miners could mine all the chains at once...using some kind of mysterious merged-mining-sidechains technology...) 

Ok, now for the big payoff, in the next (and last) section.


## The Janssens Portfolio

Now we are going to use some financial engineering to build Olivier Janssens his magically self-refunding portfolio.

![image](/images/alchemy-book.png)


### Setup

Imagine that, at present, the market has attained the following prices:

     Market 2 (Current Prices)
      -----------  
      .799    .051   
      .15     .0  


Again, here are the interpretations:

      SegWit2x likelihood: 85%
      SegWit2x price (if we  fork): .06,  aka $4200       (.06 = .051/.85)
      SegWit2x price (if we don't): .00,  aka $   0

Imagine that Mr. Janssens believes that $4200 is too low of a price.

"The 2x coins should be worth more, $7000 at least!", Janssens says, "But *only* if 2x gets a fair shot! Otherwise, I want my money back."

Well, we can do OJ one better than that. Instead of getting his money back, he can *profit* if the fork never happens. In fact, he only loses money at all, if we *do* fork and the SegWit2x price turns out to be *lower* than $4200.


### Portfolio

In fact, our goal will be to guarantee that OJ gets the exact SAME return-on-investment, whether the fork happens or not.

 ( Thus, he has no excuse for not investing! )

To do this, he buys a few fractions of a Token 6, for each whole Token 7 that he buys. The Token 6 purchases act as *insurance* for his Token 7 investment.

What is this special fraction, you ask? Well, it should always be equal to OJ's expected SegWit2x price, in this case it is 0.10 (which corresponds to the value $7,000). The [proof of this](/images/janssesns-hedge.txt) is a very simple one, but you will see it happen live in the example below.

So, for each Token 7 that he buys, he instead buys two things:

    1.0 of token_7 at price 0.051 ... cost  .051
    0.1 of token_6 at price 0.150 ... cost  .015
              -----------------------------------
                                total cost  .066

If we do NOT fork, he owns:

    1.0 of token_7, now worth 0  ... revenue   .0
    0.1 of token_6, now worth 1  ... revenue  0.1
             ------------------------------------
                                total revenue  .1


If we DO fork, and the post-fork price hits $7000 exactly\* he owns:

    1.0 of token_7, now worth 0.10 ... revenue  0.1
    0.1 of token_6, now worth 0.00 ... revenue   .0
             --------------------------------------
                                  total revenue  .1


He has the same revenue, 10 cents, in either case! But each unit of this portfolio only cost him 6.6 cents. So he gets a [rather large] ROI of .10/.066, which is = +51%.

\*This is not strictly required, of course. It is merely the only value that will give OJ the exact same return in both cases. If the price his higher his return will be larger *if we fork*, and if it is lower it will be lower *if we fork*. But, in the case of NoFork, +51% is the return that OJ locks-in in at the time of the trade.

Therefore, OJ multiplies his money by 1.5. The only way he loses anything is if we fork to SegWit2x and the price goes *down* from $4200 to something lower.



### No Free Lunch

Of course, while +51% is quite a large return, it isn't quite as high as ( $7000/$4200 ), which would have come to +66%. That +66% return is what OJ could have gotten if he had *not* purchased the insurance.

Interestingly, the insurance will tend to become free (and the +51% return will tend to approach the +66% return exactly), as the SegWit2x fork becomes more likely. And it becomes more expensive (and the +51% return approaches +0%), if the SegWit2x fork becomes less likely. You can't expect to buy fire insurance on a house that's already on fire, *and* expect it to be cheap!

So, if the insurance is too expensive, Barry Silbert would probably want to Note that fact, and figure out if everyone is still in agreement about the NYA plan; and if they are, why the traders in this market don't believe that to be the case.

### Portfolios For Everyone

In the above example, OJ felt that $4200 was too low a price, for the SegWit2x coin. So he went long by buying Token 7. But someone who believes that $4200 is too *high* a price can short 2x the exact same way -- and they only lose money if we do fork and then SegWit2x *increases* in value.

And people can long/short the 1x market in the exact same way as the 2x market. Or, they can go *long* 1x, but only if we don't fork. We can even add a *third* market (which four new tokens), representing a PoW-hardfork to a near-identical new chain -- call it "1X_new_PoW". Or we could add an "8X" market or "1GB" market.

We could also add more rows, to examine the effect of other mutually-exclusive states across *all* the markets we have.

The possibilities are endless!

 ( If you are excited by this kind of thing, you might be interested in my [Hivemind](http://bitcoinhivemind.com/) project, which is all about *permission-less* conditional futures markets, on anything that you can think of, but without needing to trust an exchange or counterparty! )


## Appendix

For details on how to easily implement permanently-liquid trading in such markets, please refer to [the appendix](/images/fork-futures-trading-appendix/).

## Disclaimer

Please don't blame me if the exchange in question gets hacked / goes bankrupt and loses all of your money.

If you want a futures market that can't steal your money, you can support my project, [Bitcoin Hivemind](www.BitcoinHivemind.com). ...you could have supported it in Feburary 2014 when I published it, in which case it would certainly have been ready today! So, tell me exactly: who's to blame for the fact that the exchange can steal your money?

## Conclusion

I have presented a way that exchanges might offer us a "fork futures" service. It may present a user-experience problem, and it may appear to be a little complicated on the backend, but it has some great benefits:

1. Very easy to implement.
2. Generates revenues for exchanges.
3. Allows many types of traders to buy/sell cool things.
4. Warns us all on which fork proposals are serious, and which are not.
5. Advises us on what the user wants.

Absent the counterparty risk question (which cannot be solved with present technology), it seems to be something that would make everyone happy.

Please stay tuned for my next blog post: "bad arguments for ignoring futures markets".