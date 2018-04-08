---
layout: default
title: Fork Futures Appendix -- How Trading Works
comments: false
show_author: false
---

    Fork Futures Appendix -- How Trading Works
    Paul Sztorc
    October 12, 2017


This uses [Robin Hanson's market scoring rule](http://blog.oddhead.com/2006/10/30/implementing-hansons-market-maker/), but good explanations of it on the Internet basically don't exist. So I will explain it in detail.

And please contact me if you are a major exchange and you would like free help implementing this.


### Overview

Benefits:

* The market never has *zero* liquidity. This is because users make a trade by signing a message, and sending this message to you [to the exchange]. They do not need to find another trader who believes the opposite of them. [At least, not *directly*.]
* Each trade is instant and atomic, and always goes through.
* A fully audit-able trade log is always available to everyone.
* Takes care of all questions related to issuing and redeeming the token.


Financial Requirements:

* You must sacrifice an arbitrary amount of money, to get the market started. I will give this money to you (see below), if you meet my conditions!

Technical Requirements:

* Per user, you must track 8 numerical values. These are "quantity owned" of each of the 8 tokens.
* You must also track 8 values for *yourself*. These will be the "total shares outstanding" -- a kind of mirror of each user's purchases. The sum of all user purchases should equal the shares outstanding.
* You must track two additional numbers, per trade. The market "score".
* Your criteria for executing trades are completely different than they were before.

That's it! It is really easy! Call me if you need help.


### Caveat

This is quite different from the traditional double-auction order books that everyone is used to. That's because: the double-auction method is used for assets that have already been issued. In Bitcoin trading, the USD and the BTC both exist *outside* the exchange. In other words, they have to be xfered in and out. But our case is different -- we will have to issue (and destroy) our token dynamically.

So please forget everything that you 'know' about how computerized trading works. It will only confuse you. 

### Reminders

If we want to conduct trading, we'll need to talk quantities and prices.

First, the quantities. Recall that there are two markets, and four token-types:

    Market 1 : "Futures of 1x"         Market 2 : "Futures of 2x"
         Short   Long                     Short     Long
          q1      q3                       q5        q7
          q2      q4                       q6        q8
          ----------                       ------------
         "d1"    "d3"                     "d1"      "d3" 
         "d2"    "d4"                     "d2"      "d4" 

The q values, (q1, q2, q3, ... q8), represent the "quantity outstanding" of tokens, across both markets. They will all start at zero (and they'll all end at zero, as well).

The two markets will be separate, and we do the same trading calculations, per market. So, it is important to note that *within* each market there are only four tokens. To emphasize this, I have given the d values above. The quantity d3 is equal to q3 if we are in Market 1; but in Market 2 else d3 = q7. The d's are specific to the market. I label them q1-q8 so that it is easier for me to talk about differences across markets, but from the trading-computer's perspective there are just two markets that each have a d1-d4. Better notation would be ( q1_1, q2_1, q3_1, q4_1, q1_2, ... , q4_2 ) but it is very ugly.

Second, recall that each token is going to have (at any given time) a market value, priced in USD, between $0.00 and $1.00. In this scheme, the "shares outstanding" and the "market price" of each token are, astounding though this may seem, the exactly same quantity -- only expressed in different units.


### Overview

It's as easy as 1-2-3:

1. The 'shares outstanding' (the d's) will, all by themselves, determine the current market prices. In other words, f(d1, d2, d3, d4) = (p1, p2, p3, p4). I will give the f() for this, below.
2. Each market will have a score, also a function of the shares outstanding. s = g(d1, d2). g() is also given below.
3. Traders who want to buy or sell, compute what the new score would be. And they then pay the difference in scores. (Or, if they are selling, they pay the difference in d's, and receive the difference in scores).

    Market 1 : "Futures of 1x"          Market 2 : "Futures of 2x"
         Short   Long                     Short     Long
         p1_1     p3_1                    p1_2      p3_2
         p2_1     p4_1                    p2_2      p4_2
              Score: s_1                          Score: s_2


### Details

As promised, here is f(). For all "b" (a parameter we will explain shortly), and e ~= 2.718 (of course), market prices (aka p1, p2, p3, p4) are a function of shares outstanding (d1, d2, d3, d4) given by:

	function d:

	    define z(x):
            z(x) = e^(x/b)

	    SUM = z(d1) + z(d2) + z(d3) + z(d4)
    
	    p1 = z(d1) / SUM
	    p2 = z(d2) / SUM
        p3 = z(d3) / SUM
        p4 = z(d4) / SUM

        return(p1,p2,p3,p4)

	Thus, f(d1, d2, de) = (p1, p2, p3, p4)

And g() is given as (using the same b and SUM, above; ln() is the natural log function):

    g(d1, d2, d3, d4) = b * ln(SUM)

#### Example

Imagine further that, in Market 2, (d1,d2,d3,d4) = (4500, 2500, 3300, 0). And the parameter b is 500.

Then:

    Token prices are f(4500, 2500, 3300, 0) = ( .902, .017, .082, .000 )

    Market expects fork to activate at a likelihood of (.902+.082) = .983 
    Ie, 98.3% likely. Participants are very confident that the hard fork will manifest itself.

    The "expected future price" of SegWit2x Chain is:
     IF FORK:
        (.082/.983) * 70000 = $5,839.27
        fyi: If you don't truncate, it is $ 5,822.088755 .
     IF NO FORK:
        (.000/.017) * 70000 = $ 0.

Now imagine that someone wants to take $20 and short this market. They *don't* know anything about the activation likelihood, they just don't believe 2x should be worth that much. So they will be buying d1 and d2 ; d1 shorts the market IF FORK, d2 shorts the market IF NO FORK.

By tinkering, I notice that buying 21.75 shares each of d1 and d2 will cost a total of $20.
There is an easy formula for this, but I'm too lazy to look it up. But I will go through the normal calculation, going "forwards" from (+21.75, +21.75, +0, +0) to $20.

    > Compute The Score As It Is Now
    .. SUM = e^(4500/500) + e^(2500/500) + e^(3300/500) + e^(0/500)
    .. SUM = 8987.59
    .. g(4500,2500,3300,0) = 500 * ln(8987.59)
    .. score is 4551.8
    ..
    > Compute the New Score, (+21.75, +21.75, +00.00, +00.00)
    .. g(4521.75, 2521.75, 3300.00, 0) = 4571.8
    ..
    > Compute the difference
    .. 4571.8 - 4551.8 = 20.0

    The purchase of 43.5 total shares (21.75 each of d1 and d2) costs $20.

    User pays $20.00 and receives (+21.75, +21.75, +00.00, +00.00). New market-state is (4521.75, 2521.75, 3300.00, 0), the new expected price of SegWit2x is 5594 USD/BTC, down (-$228) from 5822.

The trader has completed the trade. His trade went through instantaneously! He didn't need to find a rival trader.

#### Bounded Loss

The parameter b affects the liquidity of the market. The above market was not quite that liquid...a $20 trade knocked the 'expected future SegWit2x price' down by about $230.

Why not make b really really high?

Well, unfortunately, to get this scheme going, the exchange will have to pay the first score, the score where all d's equal zero. This is equal to b\*ln(4) in this case. And exchanges will have to front this money twice, once for Market 1 and again for Market 2. With b=500, exactly $693 must be risked for each market. Without getting bogged down by details of where this money goes and how it might return, I expect the exchange to be able to recover more than half of this money. So, since there are two markets, the total capital required outlay for two b=500 markets will be around $1380, of which 40% (or $552) will probably be lost forever.

As b increases, the market has more liquidity for traders, but more startup-capital is required, and (again) 40% of this will probably be lost forever. At b=2000, a similarly-situated $20 trade[^n] knocks the price down by only about $58 (instead of $228). But the financial loss will probably be $2218 (instead of $552).

[^n]: I used d=(9700,1200,4900,0), b= 2000.


But where do we get the startup capital? Who bears the risk and ultimate loss? Well, Ben Davenport once offered to put together a $1,000,000 fund to "resolve the scaling debate". So we can take that fund and give $693 to Market 1, $693 to Market 2, and then deposit the remaining $998,614 into my personal bank account.

In all seriousness, this is a tiny amount of money. The exchanges should be happy to front some cash (or, more precisely, some of their *investor's* cash), for the privilege of providing their customers and potential customers with very liquid markets. And we have lots of BTC early adopters who could chip in.

Or, I would be to provide the $970, to any exchange that can't afford it. In return, I would like half of all revenues generated from trading fees in this futures market. A win-win.

One could demand, with some justification, that the people who want a fork so badly, be the ones to pony up the cash..in order to demonstrate convincingly that they aren't going to crash this spacecraft directly into the ground.

In particular, the miners have a very, very, strong interest in figuring out exactly how much more money they might be able to *make*, if they facilitate an upgrade to WhateverFork that lots of people really *like*.


## Conclusion

Hopfully my description of all the novel features (above) has enticed you into considering this possibility.

There are [even cooler possibilities](https://www.cs.cmu.edu/~sandholm/liquidity-sensitive%20automated%20market%20maker.teac.pdf) as well. [Message me](https://twitter.com/truthcoin)!

----

### Footnotes
