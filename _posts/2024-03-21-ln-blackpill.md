---
title: The LN Blackpill
show_author: true
comments: true
date: 2024-03-21 07:00:00
---



This is kicked off by [John Carvalho's interview](https://www.youtube.com/live/faoG_aDHIYk?si=50OdZsy5z5zFpnw2&t=450), and people's [reaction to it](https://x.com/theonevortex/status/1770811861534933406?s=20).

Apparently, word is still not "out": that LN is dead, and it will collapse Theranos-style.

I hope I am wrong about that, but I do spend a lot of time in this industry.

Here is what I'm seeing!



### From Elite Lightning Devs

* Tadge Dryja, Creator of LN, 2019,
* * ["Everyone's like: 'LN is the gonna be the best thing ever'. Wait, uh, [LN] can't actually do that."](https://www.youtube.com/watch?v=LnG5H62I7Ko) (43:20 // 27:50)
* Rene Pickhardt, Author of ["Mastering Lightning"](https://www.amazon.com/Mastering-Lightning-Network-Blockchain-Protocol/dp/1492054860) and top contributor to LN StackOverflow
* * April 2023, 2023, MIT Bitcoin Expo - [Fundamental Limits of Lightning](https://www.youtube.com/watch?v=B2cEyoh4R3g) - "bitcoin often ... is being very much hyped ... and we should also discuss the shortcomings ... creating p2p cash is very hard."
* * Aug 2020, ["The more I study the lightning network the more I realize with shock that there are so many misconceptions about the privacy of Lightning in the wild for which often just the opposite seems to be true // I am scared that even in Mastering lightning we won't be able to fix that :("](https://twitter.com/renepickhardt/status/1298918019159207942?s=20)
* * Dec 2022, next paper: ["Principle limitations of the #LightningNetwork for #Bitcoin payments"](https://twitter.com/renepickhardt/status/1605189724293169153?s=20)
* BlueMatt, 10th known contributor to Bitcoin Core
* * May 2023 ["Honestly, lightning today is kinda a joke, look at BTCPayServer - you can install lightning with one click, and then you will generate invoices that are unpayable cause you have no inbound liquidity! Never heard of inbound liquidity? I dunno google it or something..."](https://twitter.com/TheBlueMatt/status/1654713334506168321)
* * Nov 2022, Presentation, ["Lightning is Broken (AF) .. but we can fix it (I hope)"](https://www.youtube.com/watch?v=s9KMRWkcwtE)
* * https://twitter.com/TheBlueMatt/status/1556448996159377414?s=20
* Alex Bosworth, head of Lightning Liquidity at Lightning Labs, July 2021, ["No algorithm can ever solve LN pathfinding/peering, because it is a 2 sided market system, just like no spam filter can ever get every spam and no targeted ad system can ever only show you only what you will buy. Heuristics can move the needle a long ways but they can never solve"]( https://twitter.com/alexbosworth/status/1420398649087971336?s=20)
* "I worry whichever way you slice it things could all end in tears" -- https://twitter.com/alexbosworth/status/1601059715060236288?s=20
* https://twitter.com/alexbosworth/status/1616100850841300993?s=20
* Aug 2022, Corallo / Decker / Bastien Teinturier [Lightning Limitations Panel](https://www.youtube.com/watch?v=BjFjK-f9ts0) -- 2 Hours of experts talking of LN problems
* Antonie Riard
* * Oct 2023, ["Effective now, I'm halting my involvement with the development of the lightning network and its implementations"](https://lists.linuxfoundation.org/pipermail/lightning-dev/2023-October/004154.html)
* * Dec 2023, [Twitter Space where I interview Antonie](https://twitter.com/i/spaces/1gqxvQzmVABJB)
* Andreas Brekken (creator of SideShift, the 1st exchange to add lightning & Liquid), March 2024, ["we removed lighting support from @sideshiftai last week to focus on scaling with sidechains/L2s"](https://twitter.com/abrkn/status/1770685548442628601)
* This [image I made](https://www.truthcoin.info/images/real-ln-tweets.png)

### From Others

* FiatJaf, May 2023, ["Lightning is looking more and more not the solution we need for Bitcoin."](https://twitter.com/fiatjaf/status/1655368938081984512?s=20)
* "Seth", ["Yeah, one of the many privacy paradoxes in Lightning... \\ Unannounced channels remove any plausible deniability for payments going through them (and can still be probed and discovered by malicious actors anyways)."](https://twitter.com/sethforprivacy/status/1532817167703588864?s=20)
* Francis Pouliot, Bitcoin Embassy 2013-2017, Dec 2021, ["Lightning was hyped too aggressively, too quickly, setting unrealistic expectations and timelines for users which necessarily required compromise (custody and centralization) to fulfill as functional end-user products."](https://twitter.com/francispouliot_/status/1473665832534294536?s=20)
* Matt Ahlborg, Nov 2020 ["As BTC fees have gone up recently, It's been interesting to see that LTC, not lightning, has been seeing increased payments on @bitrefill"](https://twitter.com/MattAhlborg/status/1330926883643469826)


### From Me

* I worked on LN tech in the ancient past:
* * [March 2016](https://bitcoinhivemind.com/blog/lightning-network/) -- "A Lightning Network for Hivemind" -- In which I take the LN idea, and modify it, so that A & B cannot defraud oracle C.
* * [April 2018](https://www.truthcoin.info/blog/fraud-proofs/) -- Where LN technology enables fraud proofs. See: "'SPV+ nodes' must have a payment channel open with a full node, or a LN-connection to a full node."
* But I have since written this: https://www.truthcoin.info/blog/lightning-limitations/
* And this: https://x.com/Truthcoin/status/1719388665107947959?s=20



### Basic Facts

* Almost no BTC are on the LN. Only 4,900 -- far less than 1% of the 19.5M BTC in circulation. The actual figure is 00.0250%. This number has been [heading down](https://bitcoinvisuals.com/ln-capacity) both as a % and in absolute terms. It is less than what has been raised by all LN startups.
* An L1 channel is required to join the LN, so there is not enough space for everyone to join.
* LN stops working when fees are high/volatile.
* Most LN capacity is in one of 5 "LSP"s. And most LN transactions are custodial.
* See [here](https://x.com/Truthcoin/status/1719388665107947959?s=20) for more
* There is not a chance --at all-- zero chance that LN will [compete with a Bip300 sidechain L2](https://www.truthcoin.info/blog/thunder/).


### Fake Support

(There are tons of examples of this, this is just the only one I could remember)

* https://x.com/ercwl/status/1725903544660705728?s=20


<!--

### Other

Michael Saylor said, to me in person:

* "why can't we just put zCash, on a layer3 on top of a lightning super-node"
* "everyone, every company, will have thousands of thousands of lightning channels" (in response to the "not everyone can have a LN channel" math)
* "it won't matter if the nodes are custodial or not"

-->


### Send me more

This is not a typical blog post. Instead, it is a kind of database I threw together in one day.

Send me more links and I will add them over time.