---
title: The Trusted 3rd Party Doesn't Scale (But Blockchains Do)
comments: true
---

>  At large scales, it would seem that only blockchain technology is likely to remain secure.

## Background Info

This post aims to compare two different ways of "controlling" data that you "own": [1] the "trusted 3rd party" vs. [2] "the blockchain".

### Agency

The "separation of ownership and control" is one of the most quintessential problems in economics (where it is known as ["the principal-agent problem"](https://en.wikipedia.org/wiki/Principal%E2%80%93agent_problem)).

Satoshi applied this framework to money, observing that, at times, banks "controlled" money which they did not "own"...and mis-used that control. This observation led him to criticize the "trust" placed in banks, and to propose an alternative where trust was minimized.

![sat-trust](/images/satoshi-trust.png)

Bitcoin is different; everything happens locally. With one exception, you fully "control" the BTC that you "own". That sole exception is *mining* -- a (network wide) process which aims to resolve disputes surrounding the temporal order of messages.

More about mining later.

### Security and Scale

More-important systems require more security.

Small systems are usually "secured by indifference". Large systems, however, offer any potential attacker correspondingly larger rewards. Examples include the [Target Hack](http://krebsonsecurity.com/2014/01/target-names-emails-phone-numbers-on-up-to-70-million-customers-stolen/), the [Snapchat Hack](http://techcrunch.com/2013/12/31/hackers-claim-to-publish-list-of-4-6m-snapchat-usernames-and-numbers/), and the [IRS Hack](http://krebsonsecurity.com/2016/02/irs-390k-more-victims-of-irs-gov-weakness/). All are similar in that they were *one* single system, protecting *many* accounts.

A safe protecting $20,000 should be pretty strong. However, how *much stronger* should a safe be if it is to protect $20 million? What about $20 billion?

Ultimately, you can [rent a diamond-edged saw for 40 bucks](http://www6.homedepot.com/tool-truck-rental/PRO_Electric_Concrete_Saw_12/3512434/index.html), and it can [cut through pretty much anything](https://www.youtube.com/watch?v=j8EY1qiXBcg) (and be reused many times). If "physical safe" is the *only* security feature of a system (ie, no guards, no alarms, no police), the system can never store more than a few dollars.

<!-- zzz boring

#### What is the relationship between 'security' and 'account quantity per system'?

The difference between 3 million and 4 million users, to the principles (both, the "owners" of the data, and the "theives" [aka "new owners"]) is immense, yet the difference to the agent (the "controller") of the data is -at least at first- nonexistent. At the most basic 'contract level', the agent [1] collects his payment and [2] provides a service. The relationship of 'the service' to 'the outcome' is (in his words) "not my problem".

#### The p-a problem has reduced productivity. What can prevent this reduction?

The agent ("data controller") can be *incentivized* to take security seriously. A firm specializing in network security has a brand, resumes, 'reputational capital' on the line. They charge more, but have greater effectiveness. If computer security problems are costing businesses money, entrepreneurs will step in; they will use their expertise to minimize this actuarial cost (and, if none have this expertise, individuals will make investments in expertise) -- this is basic (micro)economics.


---
The problem, in the above paragraph, is the word "greater" in the phrase "greater effectiveness". There are technological limits to what can be accomplished -- no matter what talent, luck, and/or resources are assembled, we simply *do not know how* to produce a desired outcome (faster-than-light communication being a clear example).

-->


## Computer Security Under Agency - Fundamental Incentive Limits

It is [much much harder to break a digital safe](http://miguelmoreno.net/wp-content/uploads/2013/05/fYFBsqp.jpg), than it is to break open a physical one.

Unfortunately, most people do not use 'digital safes' (for a variety of reasons), and instead they **trust** a third party to secure their digital assets (their money, their documents, their social media, ...).  

My view is this: **when security is organized using "the trusted 3rd party"**, the *inevitable* ownership-control disparities *routinely* become so large, that they produce *insurmountable* problems -- failure is guaranteed.

My "failure is guaranteed" viewpoint is the product of two factors.

### Factor 1: The "Critical Bribe"

What does **ten million dollars** buy you? For a start, if you can get a 3% real return on that money, you are earning $300,000 per year, just for doing nothing. That's $25,000 a month, forever.

If you move to a tax haven, you can keep most (or all) of it. Tax havens usually contain beautiful things, for comfortable living.

![cayman-islands](/images/cayman-islands.jpg)


Thus, a single person might be compelled to do *anything* for $10 million. A group of 8 people might be compelled to do anything for a grand total of $80 million.

The right 8-person conspiracy can circumvent most security systems today. This include systems which are simply worth *more than $80 million*. For example: any commercial bank, all Facebook logins, a prison, etc.

To solve this problem, in the real world, we rely on *punishment* -- post hoc, we punish those who accept, or merely propose, a bribe. 

### Factor 2: Lack of Inherent Identity = No Blame, No Punishment

Computers do not (currently) have a concept of identity. Instead, systems have 'secret info' which is -theoretically- known to one person uniquely. When Mr. Smith enters his password, we can say that Smith is using the computer "as Mr. Smith". However, this is not necessarily the case. Mr. Smith may have had his password **stolen**, or he may have **sold** his password.

Epistemologically, there is very little difference between a password-**theft** and a password-**sale**. This ambiguity grants *plausible deniability* to anyone who might want to sell their password. This ambiguity is further exacerbated by [1] the [myriad ways](http://www.scientificamerican.com/article/computers-can-be-hacked-using-high-frequency-sound/) a hacker can [easily steal](http://petapixel.com/2014/08/29/heres-iphone-thermal-cameras-can-used-steal-pin-codes/) the 'secret info', and [2] the unforgiving/discontinuous nature of info-theft (one little mistake, one piece of bad luck, and the attacker has the whole password).

![gox-deniability](/images/mt-gox-deniability.png)

( In fact, *consequentially* there is no difference, either. The attacker "buys" the 'secret info'...whether the purchase is in the form of a bribe, or in the form of expertise/surveillance-technology, makes no ultimate difference to him. A clever attacker would 'shop around' to circumvent the security at the lowest cost. My main point is that, no matter the technology, the bribe-route will always be available. )

There is one way to tell a bribe from a theft: post-hack identification of the bribe-takers. As soon as these criminals buy a new house/car, they can be identified (and punished).

On the other hand, monitoring is expensive, particularly if the number of potential criminals is large. Moreover, the monitors can themselves be bribed. Criminals can react to monitoring, by slowly funneling their earnings through 10-99s (without having to work a day in their lives).

The worst case, for such individuals, is a relaxed, modest, private life of leisure. As far as "worst cases" go, that's pretty much as good as it gets.


### Combined

My hypothetical "safe only system" had a security margin of just a few dollars.

A trusted 3rd party setup (ie, a "centralized" setup) has, I believe, a security margin of about $200 million\* dollars.

This may explain why ultra-valuable systems like "the stock market" or "the military" have *resisted* full computerization for so long. Our leaders foresee the security failures: Russia or China can bribe one or two key people (and these people escape, happily, to a beach somewhere) and foreign governments can hack right into the President's iPhone. The prospect of governments (or rich individuals), wreaking havoc on the stock market / military / basic utilities, is outright unacceptable. Hence, these systems remain -wisely- "low tech".

Of course, "low-tech"-ness makes them slow, expensive, and subject to all kinds of potential for fraud, rent-seeking, corruption, etc. Low-tech systems cannot operate in cool, new ways.

Worse still, as daily life becomes more digital, a greater percentage of daily life will end up in a +$200M system. Identity theft will produce greater and greater revenues, as will cyber [blackmail](http://www.csoonline.com/article/2996614/cyber-attacks-espionage/ddos-scammers-collect-20-000-with-ashley-madison-extortion.html) / [extortion](http://www.slate.com/articles/technology/future_tense/2016/02/hollywood_presbyterian_medical_center_paid_17_000_to_free_computers_from.html). The Ashley Madison and Snapchat hacks would not have been possible in the 90's.

\*In practice, due to carelessness, complexity, agency problems, and attacker-patience (ie, "sheer luck"), the critical threshold will be much *lower* than $200 million dollars.

## Blockchain Security

### Mining (The Only Non-Local Process)

Now, we return to the previously-deferred topic of mining. 

The long-term reliability of mining is unknown, but -so far- **it has performed as advertised**. Never, in all the 7 years that Bitcoin has operated, has the mining process failed to resolve message-order disputes in a timely manner.

( The *management of* the mining process has not been as reliable. In one instance, a reckless novice (and [possible saboteur](https://www.reddit.com/r/Bitcoin/comments/3d26tk/did_mike_hearn_work_in_sigint_does_he_now/)) [caused a malfunction](https://www.reddit.com/r/Bitcoin/comments/39yaug/the_history_of_mike_hearn_and_why_you_should_not/cs7pmgz) in the Bitcoin network such that the mining process operated on two separate blockchains instead of one. During the error, the mining process worked perfectly on both child-chains, and, after the error was detected, *only* those who had run the newer, buggy code were affected by the subsequent dispute-resolution. In [a separate case](https://bitcointalk.org/index.php?topic=1108304.0), a miner intentionally chose to 'cheat' the rules, and broadcast an invalid block. This cheating happened to, coincidentally, occur during some laziness on the part of a few other miners. The net effect resembled a mining-failure, but was not. With no influence from any humans whatsoever, the network fixed itself immediately and normal users were never affected in any way. Honest miners enjoyed disproportionate rewards during this period, and the cheaters [lost over $50,000](http://cointelegraph.com/news/miners-lost-over-50000-from-the-bitcoin-hardfork-last-weekend). )

### Scalability of Mining

Is mining secure, at all scales? No one knows for sure.

However, mining *does* have a security margin which is **related to the value of the underlying database**: when the underlying Bitcoins increase in value, the network security margin automatically increases to match it. Given this connection, it might be reasonable to assume that mining will continue to work reliably, as scale increases.

## Conclusion

Mining is unproven. However, what is known, with certainty, is that **blockchains solve the principal-agent problem**. You "control" what you "own", there are no 3rd parties and no trust. You, therefore, have some incentive to protect a 20 BTC wallet which you own; and you have *100x that incentive* to protect a 2,000 BTC wallet which you own.

For these reasons, I believe that the blockchain is the (only) future of all large-scale computing systems. These systems simply cannot remain secure under the trusted 3rd party model. Either large systems will reunite ownership and control ("blockchain-tech"), or they will use deliberately-slow and non-automated authentication processes.

Or, they will be hacked on a frequent and regular basis.