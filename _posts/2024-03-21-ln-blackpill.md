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

* Tadge Dryja -- Creator of LN, 2019,
* * ["Everyone's like: 'LN is the gonna be the best thing ever'. Wait, uh, [LN] can't actually do that."](https://www.youtube.com/watch?v=LnG5H62I7Ko) (43:20 // 27:50)
* Matt Corallo, 10th known contributor to Bitcoin Core
* * Nov 2022, Presentation, ["Lightning is Broken (AF) .. but we can fix it (I hope)"](https://www.youtube.com/watch?v=s9KMRWkcwtE)
* * May 2023 ["Honestly, lightning today is kinda a joke, look at BTCPayServer - you can install lightning with one click, and then you will generate invoices that are unpayable cause you have no inbound liquidity! Never heard of inbound liquidity? I dunno google it or something..."](https://twitter.com/TheBlueMatt/status/1654713334506168321)
* Burak Keceli -- inventor of ARK, and [hacker who crashed most of the Lightning Network for fun in 2022](https://www.coindesk.com/tech/2022/11/02/rogue-actor-disrupts-lightning-network-with-a-single-transaction/)
* * June 2023, 1:25 ["I've always been a big critic of Lightning. I had severe objections, right? ..from inbound liquidity, to inbound receiving interactivity ... I wanted [with ARK] to address the inbound liquidity problem, but I really couldn't find a cure for it. ... I fail to see Lightning scaling."](https://www.youtube.com/watch?v=EocWax43QgQ)
* Alex Bosworth -- head of Lightning Liquidity at Lightning Labs
* * July 2021, ["No algorithm can ever solve LN pathfinding/peering, because it is a 2 sided market system, just like no spam filter can ever get every spam and no targeted ad system can ever only show you only what you will buy. Heuristics can move the needle a long ways but they can never solve"]( https://twitter.com/alexbosworth/status/1420398649087971336?s=20)
* * [This image I made](https://www.truthcoin.info/images/real-ln-tweets.png)
* * Dec 2022, ["I worry whichever way you slice it things could all end in tears"](https://twitter.com/alexbosworth/status/1601059715060236288?s=20)
* Corallo + Decker + Bastien Teinturier
* * Aug 2022, [Lightning Limitations Panel](https://www.youtube.com/watch?v=BjFjK-f9ts0) -- 2 Hours of LN experts bemoaning LN
* Antonie Riard
* * Oct 2023, ["Effective now, I'm halting my involvement with the development of the lightning network and its implementations"](https://lists.linuxfoundation.org/pipermail/lightning-dev/2023-October/004154.html)
* * Dec 2023, [Twitter Space where I interview Antonie](https://twitter.com/i/spaces/1gqxvQzmVABJB)
* Rene Pickhardt -- Author of ["Mastering Lightning"](https://www.amazon.com/Mastering-Lightning-Network-Blockchain-Protocol/dp/1492054860) and top contributor to LN StackOverflow
* * Aug 2020, ["The more I study the lightning network the more I realize with shock that there are so many misconceptions about the privacy of Lightning in the wild for which often just the opposite seems to be true // I am scared that even in Mastering lightning we won't be able to fix that :("](https://twitter.com/renepickhardt/status/1298918019159207942?s=20)
* * Dec 2022, next paper: ["Principle limitations of the #LightningNetwork for #Bitcoin payments"](https://twitter.com/renepickhardt/status/1605189724293169153?s=20)
* * April 2023, 2023, MIT Bitcoin Expo - [Fundamental Limits of Lightning](https://www.youtube.com/watch?v=B2cEyoh4R3g) - "bitcoin often ... is being very much hyped ... and we should also discuss the shortcomings ... creating p2p cash is very hard."
* [CalleBTC](https://twitter.com/callebtc), creator of [Cashu (LN Chaumian e-cash)](https://valuestack.xyz/cashu-chaumian-mints-explained/)
* * Sept 2023, ["He asked why he needed a new channel. He already had one! ... Fvck"](https://x.com/callebtc/status/1701486817806082232)
* Jameson Lopp, Creator of [Statoshi](https://blog.lopp.net/statoshi-developer-s-guide/) and [Casa](https://bitcoinmagazine.com/business/bitcoin-company-casa-raises-21-million-launches-api)
* * ["we dropped lightning support later as a result of re-evaluating the tech and business."](https://x.com/lopp/status/1782838127721099317)
(https://twitter.com/udiWertheimer/status/1785733163446063569)
* Andreas Brekken -- creator of SideShift, the 1st exchange to add lightning & Liquid
* * March 2024, ["we removed lighting support from @sideshiftai last week to focus on scaling with sidechains/L2s"](https://twitter.com/abrkn/status/1770685548442628601)
* FiatJaf -- creator of lntxbot (and nostr)
* * May 2023, Tweet ["Lightning is looking more and more not the solution we need for Bitcoin."](https://twitter.com/fiatjaf/status/1655368938081984512?s=20)
* *  July 2023, Article ["Reasons why Lightning is not that great"](https://fiatjaf.com/04e9e814.html)




### From Others

* Nov 2020, Matt Ahlborg, ["As BTC fees have gone up recently, It's been interesting to see that LTC, not lightning, has been seeing increased payments on @bitrefill"](https://twitter.com/MattAhlborg/status/1330926883643469826)
* Dec 2021, Francis Pouliot, Bitcoin Embassy 2013-2017, ["Lightning was hyped too aggressively, too quickly, setting unrealistic expectations and timelines for users which necessarily required compromise (custody and centralization) to fulfill as functional end-user products."](https://twitter.com/francispouliot_/status/1473665832534294536?s=20)
* June 2022, "Seth", ["Yeah, one of the many privacy paradoxes in Lightning... \\ Unannounced channels remove any plausible deniability for payments going through them (and can still be probed and discovered by malicious actors anyways)."](https://twitter.com/sethforprivacy/status/1532817167703588864?s=20)
* May 2024, Udi Wertheimer, ["lightning sucks ... our company built a lightning service from scratch and onboarded almost 10,000 paying users ... and I'm telling you it sucks"]



### From Me

* I worked on LN tech in the ancient past:
* * [March 2016](https://bitcoinhivemind.com/blog/lightning-network/) -- "A Lightning Network for Hivemind" -- In which I take the LN idea, and modify it, so that A & B cannot defraud oracle C.
* * [April 2018](https://www.truthcoin.info/blog/fraud-proofs/) -- Where LN technology enables fraud proofs. See: "'SPV+ nodes' must have a payment channel open with a full node, or a LN-connection to a full node."
* But I have since written this: https://www.truthcoin.info/blog/lightning-limitations/
* And this: https://x.com/Truthcoin/status/1719388665107947959?s=20


### Other Compilations

* [David Shares](https://github.com/davidshares/Lightning-Network/blob/main/README.md) -- compilation of negative LN links
* ["Lightning's Best Moments](https://t.me/lightningfantasy) -- Telegram Compliation
* [Nostr Htlc_nbot](https://nostrrr.com/p/npub1l8wk5a39qcnqkw9z60jmgepp8shy073cwapfl60wvrs8rgc6qltsq66m2c) -- A bot tracking HTLCs and how expensive/pointless/unreliable they are.
* [MSN Overview Article -- Are Developers Losing Faith In Lightning?](https://www.msn.com/en-us/news/technology/are-bitcoin-developers-losing-faith-in-lightning/ar-BB1kXyOt)


### Fake Support

* Feb 2018, [Tone Vays, advocating for LN but not knowing that an online LN-node is needed to receive funds](https://www.youtube.com/watch?t=40m4s&v=9_WCaqcGnZ8)
* Nov 2023, [Brad Mills, on the cap table of dozens of LN startups, has no idea how channels work](https://x.com/ercwl/status/1725903544660705728?s=20)
* Apr 2024, [Four LN supporters arguing that it is better if people NOT use the LN iself, and instead trust a custodian](https://twitter.com/DontTraceMeBruh/status/1777616386149191757?t=_16ccamNMXNGuHZCm4i90w&s=19); [Again](https://x.com/day_nft_io/status/1777275649591304696)


### Basic Lightning Facts You Should Know

* Almost no BTC are on the LN. Only 4,900 -- far less than 1% of the 19.5M BTC in circulation. The actual figure is 00.0250%. This number has been [heading down](https://bitcoinvisuals.com/ln-capacity) both as a % and in absolute terms. It is less than what has been raised by all LN startups.
* An L1 channel is required to join the LN, so there is not enough space for everyone to join.
* LN stops working when fees are high/volatile.
* Most LN capacity is in one of 5 "LSP"s. And most LN transactions are custodial.
* See [here](https://x.com/Truthcoin/status/1719388665107947959?s=20) for more
* There is not a chance --at all-- zero chance that LN will [compete with a Bip300 sidechain L2](https://www.truthcoin.info/blog/thunder/).


### Random Problems

* [Fake Lightning Channels](https://thebitcoinmanual.com/articles/fake-lightning-channels/)
* [Aqua 21% Fee](https://fxtwitter.com/NEEDcreations/status/1778953732178296858)
* [Lightning Loop needs decentralized liquidity -- which is not there](https://twitter.com/alexbosworth/status/1616100850841300993?s=20)
* [Disappeared on the way](https://twitter.com/silentlink1/status/1786075954751639561)



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