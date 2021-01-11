---
title: Open Elections - Auditable, Fast, Private, Secure Voting
show_author: true
comments: true
date: 2021-01-10 01:00:00
---



> Can we make voter fraud impossible? Look up your vote at home, to make sure it was counted correctly! Yet privacy is maintained. Computers are used, but they are not a "black box" process.


### Introduction

![voting](/images/voting_software.png)

Above: From [xkcd](https://xkcd.com/2030/). Hopefully I can do better than that.


## 1. Motivation

The 2020 election left many Americans dissatisfied with the process:

* **Speed**
* * Counting votes takes too long.
* **Integrity**
* * Concerns about voter fraud / vote integrity.
* * Concerns about *fake allegations* about voter fraud (intended to de-legitimize the process).
* **Safety**
* * Voting in person might be unsafe in times of pandemic.
* * Voting by mail is vulnerable to...
* * * ...coercion (unlike a voting booth, an adversary can watch you as you fill out your ballot),
* * * ...and manipulation (an adversary can intercept your ballot and change it).

It ultimately culminated in political violence. See [here](https://www.businessinsider.com/dc-police-chief-capitol-riots-close-to-a-coup-attempt-2021-1) and [here](https://www.businessinsider.com/trump-attacks-pence-for-not-having-courage-to-overturn-election-2021-1) for example. This particular outbreak of political violence was entirely feeble and mostly performative, but political violence (of this kind) is nonetheless unacceptable.

Election Reliability happens to be of independent interest to me -- as a proponent of [Futarchy](https://www.youtube.com/watch?v=dJLYRADcPP4), I need the election system to work reliably. Today, it is easier to "hack the vote" at the brain level, but post-futarchy the Achilles' Heel of of democracy will move back to the level of physical ballot-counting.

In any event: the election should be *provably secure*. It should be secure in a way that **any** observer can demonstrate the security to **any** other citizen.


## 2. Computers

The strategy I am about to advocate, requires that we vote by computer.

( There is a section about "Hacking!" at the very end. If you want to skip to it now, be my guest. Preceding it, there is a section dealing with other types of impropriety. )

Computers are needed because they let us do important things, like: count quickly and make audit-able outcomes.

Computers sometimes scale poorly. In other words, during "rush hour" (when many voters arrive at once) it is very easy to get more pens (so that people can fill out many ballots at once), but very difficult to suddenly purchase and configure more computers.

We can try to address this by trying to ensure that computers are never the "bottleneck" of the voting process. We can make "ballots" available online in advance, and on mobile phone, and on large printouts in the voting lines. Therefore, by the time citizens get in front of the voting kiosk (in the voting booth), they know exactly what to do, and can do it in just a few seconds (hopefully). Their time in line can be spent rehearsing the sequence of inputs they must make to the real kiosk.



## 3. Process Outline

1. Citizen shows up to their polling place on election day; passes the eligibility screening. (Ie, the people who look up your name and determine that you are indeed allowed to vote.)
2. Citizen is randomly assigned a kiosk computer.
* A poll worker goes up to an empty kiosk and enters a simple 6 digit code (ie, "QROXHJ" "VDHZEE", just like at an airport check-in). The codes are generated in advance, and don't need to be kept secret -- they just move things along, avoid the problem of hard-to-spell names / common names, and prevent people from accidentally voting twice.
* The poll worker, after helping the citizen by entering this code, returns to the front desk to help the next citizen.
3. Citizen enters their choices; "are you sure" screen; Submit Ballot.
4. Finally, kiosk will tell the voter **their Ballot ID**. They should write this down[^1], or memorize it. This will let them look up their ballot later. The Ballot ID can be presented to the citizen in multiple interchangeable forms: one that is easy to write down (ie "HGOJ", "QRAB"), and one that is easy to remember (ie, "flag wrestle", "toe swear").
* * To audit their vote, citizens will also need their polling place and **Kiosk ID**. But these are overwhelmingly less important. After all, anyone can look up their polling place at any time. And only a handful of kiosks will be at each polling place (so if the user forgets the kiosk ID it isn't a big deal -- they can get it from trial-and-error later). Polling places should publish a map of the polling room, containing the spatial location of each kiosk within the room. Kiosks can be given special memorable names -- named after local public schools or parks (or whatever). This way it should be very easy for citizens to recover their Kiosk ID, even if they didn't write it down. Perhaps the polling place will even keep record of which citizen got which kiosk -- it makes no difference.
5. After the polls close, the poll-workers will publish *all* the ballots on a website. These will be linked only to their Kiosk ID and Ballot ID, not to any citizen's real name. When looking up your vote, at home, you just scroll (or cntrl+f) through the entire list[^2], until you get to your Ballot ID.

[^1]: Ballot ID could be two BIP39 words! Kiosk could pick a random (unused) number from between 1 and 262,144 (which is 2^(11+7)) and use this as the ID. It could then use BIP39's trick of the 4 bit checksum, to forge two words from a 2048-word list. Each kiosk could then serve up to 262,144 voters. 

[^2]: Obviously, we would need to dump all ballots onto one webpage (for the user to scroll through). Anything else, would threaten the user's privacy (since users' interaction with the webpage would depend on their Ballot ID; and henceforth nothing can).

There -- now votes can be counted quickly and accurately. In fact, anyone with an internet connection and basic data science skills can download every single vote and count them all, all by themselves. 



## 4. Refinements

### A. "Decoy" BallotIDs

Election theorists say that, to guard against coercion, it should never be possible to prove that you voted a certain way.

For example, under this scheme, an abusive spouse might be waiting at home, to demand that you hand over the BallotID that you wrote down, so that **they** can look up your vote later (and punish you, if the vote doesn't look the way they told you to vote).

To address this after-the-fact coercion, the kiosk cam give out "decoy Ballot IDs" in addition to the voter's true BallotID. After voting, citizens can glance at the list of decoys, and identify a BallotID that would pacify the coercer. Then, they can write down that BallotID and pretend to have voted that way.

Of course, the very first person to use a given kiosk will not have any decoys available to him/her. And the person second-in-line will effectively learn the vote of the person in front of them (as it will be the only decoy available for the kiosk to display). This is most unsatisfactory.

We can solve it in a few ways:

* Input a critical mass of absentee ballots first (ie, early in the morning on election day, before the doors open).
* Or, by telling the kiosk to wait until it has collected n>=50 votes, before giving out decoys. We would then need to hope that those who are under duress, could find some pretext for turning up to the polling place late (such that they will be at least (50\* total number of kiosks)th place in line).
* Or, we could have each kiosk cast a real vote for each option -- this would not affect the outcome (as they would then cancel each other out -- we could even subtract out the net effect of the kiosk's fake votes before reporting the results, if we wished), but it would allow the kiosk to hand people decoy BallotIDs immediately.

Remember that, eventually, the kiosk will reveal *all* of the ballots, to everyone. So, revealing just a few at random to just one citizen can't hurt. So the cost is minimal. It is even minimal in terms of UX damage -- if citizens are confused by this, they can safely ignore it.

But while the cost is low, the frustration dealt to the Coercers is pretty significant. Even if the Coercer is able to obtain (by force) self-reported BallotIDs from many victims, his ability to retaliate is still curtailed. If he is very lucky, he may observe that few different people have claimed the same single BallotID as one another. Since this is impossible, he knows that exactly n-1 of them are lying to him. But he will not know who the single truth-teller is. So he will not necessarily know who to punish and who to reward.

Furthermore, the final screen can display a PSA: "Voter Intimidation is a Crime", with a telephone hotline.

If the population of a polling place is low, it might have all its Kiosks set to the same ballot ID. This would pool all of their votes. There is some small risk[^3] of duplicating Ballot IDs if they do this. This risk can easily be reduced to zero with a pre-configuration step[^4].

[^3]: Given that there are 2^64 possible Ballot IDs (4 alphabetic characters), it is very unlikely that the Kiosk will assign people the same ID, even for a population as high as 5000, even if it did so "birthday paradox" style (ie, with 5000 kiosks that were each used once, see https://www.wolframalpha.com/input/?i=%2826%5E4%29%21+%2F+%28+%28%2826%5E4%29%5E2000%29+*+%28%2826%5E4%29-2000%29%21+%29 )

[^4]: If multiple kiosks share a Kiosk ID, they can nonetheless ensure that they never inadvertently give out the same BallotID. They would do this by being pre-configured to each grab just a subset of the 2^64 region. For example, if there are three kiosks sharing the same Ballot ID, and k  = 26^4, then the first kiosk could claim the [0, (1/3)\*k] range, the second could claim the [1/3 \* k , 2/3 \* k] range, and the third kiosk could claim the [ 2/3 \*k , k] range.


### B. Absentee Voting

Absentee voting is straightforward: just print out a ballot, fill it in, and mail it to the polling place.

* On election night, the poll workers will enter it into the kiosk in the voter's stead.
* * They can enter it at any time. (Perhaps, they can do so whenever the polling place has "down time" with few voters).
* * For security, the convention can be: that three poll workers must be present, to enter the choices correctly, and to ultimately learn the BallotID (which they will put back in an envelope and mail back to you).
* You can then check to make sure that they entered your ballot right, in the exact same way as everyone else.
* As mentioned above, these votes would be perfect as a supply of the initial n=50 pool of "decoy BallotIDs". This is because absentee voters never stand in line, and do not have the problem of being "outed" to the people directly behind them in line if the kiosk only has collected one ballot and throws it as a potential decoy. So it would be nice to enter a healthy quantity of absentee ballots at the beginning of the day, right before the polls open.

### C. How to ensure that absentee votes are not filled out under duress?

There should never be *any* opportunity for anyone to be intimidated while voting -- not even by a spouse, family, friends, etc. We must make it so that, even if someone truly *wanted* to reveal how they voted, they are unable to.

* We could perhaps require that absentee votes be filled out in the presence of either a notary public or a police offer -- that officer would watch carefully (watch the situation, not the ballot!) to make sure that no one observes / pressures the voter as they fill out their ballot. The officer/notary would then also sign, and the envelope would then be sealed. Police departments could offer this service at some known times -- come down to the police station on Tuesday and Thursday mornings (or whatever), as could banks (since they usually have notaries). They could do big roomfuls of people at a time.
* * (And they could have a big stack of blank absentee votes -- all the paperwork could be done at one time or place.)
* * (Furthermore, police could also collect and store the ballots until election time. There could be special lockboxes there.)
* * As a further refinement, the absentee ballot can include a section where the citizen indicates whether or not they would like to be mailed-back a decoy BallotID (they can get the real BallotID from the police station later). As usual, ordinary voters can safely ignore this complex step, as this feature would only need to be used by people who are living in such extreme duress that they cannot even privately open their own mail.


## 5. Cost

How much would it cost to put these kiosks everywhere?

### A. The Competition

First let us check out the baseline:

* "...a single state, Pennsylvania, plans to spend at least $125 million to upgrade its voting machines...
* "...state and local agencies would need nearly $2.2 billion over the next five years to adequately shield elections from tampering..."
* "...Congress allotted $380 million to the states in 2018..."

From [NY Times](https://www.nytimes.com/2019/09/25/us/mitch-mcconnell-election-security-bill-.html).

### B. How Many Kiosks?

Second, let us eyeball the size of the problem:

"More than 230,000 polling places were used in the 2018 general election, according to the 2018 Election Administration and Voting Survey (EAVS) report released by the U.S. Election Assistance Commission (EAC)"

From [NCSL](https://www.ncsl.org/research/elections-and-campaigns/polling-places.aspx).

### C. Cost Per Kiosk

Currently, for the layperson consumer to buy a computer + touchscreen + plastic case, on Amazon, the total cost is $146. See [here](https://www.amazon.com/hz/wishlist/ls/2OGHR6UD7IIR5?ref_=wl_share).

### D. Total Cost

If each polling place had, on average, 10 kiosks, then the total cost, to equip the entire country, would be $336 million. Obviously, immense scale-economies would bring that figure down by at least 15-20%. Furthermore, computing equipment tends to become cheaper and cheaper over time, in spite of CPI inflation and GDP growth. So, call it $285 million.

That is still about $100 million *less* than what Congress allotted the states in 2018.

And since these computers would be so rarely used, we probably wouldn't need to replace them that often. (Although, of course, we would need to replace them, as we can expect some to be lost/stolen/damaged intentionally.) So the big cost would be upfront.

Obviously, we can continue to use the cubicles, tables, privacy shields, etc that are already in use.

So, the costs seem reasonable. It would indeed be expensive to equip the entire nation with raspberry-pi kiosks. But not more than our nation already spends on the existing election infrastructure.

### E. Cost in Context

And consider the risk. What is the "cost" associated with a fraudulent election? Mental distress, lost productivity, disrespect of the law, racketeering/corruption, rioting, possibility of civil war, etc.



## 6. Dealing with Impropriety / "What if I look up my vote and it is wrong?!"

### A. Scope of Possible Fraud

This scheme, has the property that any malfeasance will be detected **with certainty** by at least *as many people as votes were changed*. This is because they will each look up their vote online, and notice that it was mis-recorded (or is missing).

In order to change *enough votes to affect the outcome*, the fraudsters would probably need to change *very many* votes, thus alerting *very many* people. And thus increasing the likelihood that the fraud will be detected and addressed.

Nonetheless, it might happen.

Suppose that you look up your vote on the OpenVote website, and see that it has been seemingly misrecorded. What should you do?

First, you may have misremembered or mis-entered your ballot. Second, if fraud did occur, it probably isn't a vast conspiracy (though it might be). Instead, it is probably malfeasance at your local polling place. If the voting machines are working properly, someone would need to have reset the machines, and then secretly re-entered fake ballots.

How do you catch that person and bring them to justice (and get your *real* votes re-cast)?

### B. Responsibility and Accountability

The first and most essential step, is to assign **blame** correctly. Every polling place, every kiosk should be "owned" (in the sense of being exclusively "controlled") ultimately by **one single** real-life individual. This is the person who will suffer, if any malfeasance is demonstrated.

This is not at all to say that there will be dictators! While one person will be blamed (if something goes wrong), *everyone* will observe and judge their conduct. They would be true civil servants.

For example, imagine that Mr. X is the person responsible for Kiosk 5 on election day. Mr X is responsible for testing kiosk 5, he is responsible for making it available for others to test, he is responsible for resetting Kiosk 5 the morning of the election, he is responsible for reporting the tallies from Kiosk 5 accurately. Being human, Mr. X will occasionally need to go to the bathroom and eat lunch, etc -- he will have to work out who is watching over Kiosk 5 in his absence. He should do this in whichever way seems best to him -- perhaps friends will help him, or fellow Kiosk workers, or an official polling place policy (that he trusts). Perhaps no one will help him -- he could close down Kiosk 5 (indeed, *lock it* closed) until he gets back from the bathroom or whatever.

Similarly, Mrs. Y could be the person responsible for (for example) polling place #521 in the State of Connecticut. She (and her crew) could be responsible for setting up the tables, setting up posters, checking people's voting eligibility, securing the absentee ballots (and later entering them into kiosks), and so forth. 

The crucial point is that, should anything go wrong, there should be people who *are responsible* and therefore who suffer as a result. What must be avoided, at all cost, is a bureaucratic 'round robin' where it is difficult to figure out who to blame for what. Such a round robin introduces security vulnerabilities, because it ensures that no one will actually care about the election (since anyone overseeing it can just weasel out of responsibility).

Yet another crucial point, is that *the people who dispute the election* must now pick and choose specific people, and actions, which they say were Wrong. They cannot just make vague claims about the election being "stolen" -- they have to say that "Mr X did the wrong thing" (when he wrongly reported the results from Kiosk 5). Or that "Mrs Y did the wrong thing" (by not checking people's drivers licenses carefully enough). Therefore, they must look Mr X (or Mrs Y) in the eye and tell them that they should be punished, for such-and-such reason. (And then we all must listen to Mr X's reply.)[^5]

[^5]: This new risk of punishment, may tend to deter people from volunteering to work at polling places. But I say: if we must *pay* these people a high equilibrium wage, then so be it. In general, you get what you pay for. Furthermore, the public should be given every reason to scrutinize the activities of the poll workers.

So, now you know who to blame. And you also know where to look, for potential allies. But you will still need *evidence* that your suspicions are warranted. How can we get some?

### C. Livestream the Election

Second, we can put cameras everywhere, and "live stream" every polling place -- only very recently has this become technologically possible. The video footage can be stored and reviewed in the event of any disputes.

We cannot risk revealing people's votes, so the cameras (obviously) cannot face the touchscreens. But we could contrive the kiosk-hardware, such that the physical switch which "manages" them (which starts the kiosk up, clears the votes from memory, or tallies the votes) is in the back of the machine, and the touchscreen is in the front. There could even be a separate screen in the back, which reports the ultimate tallies (to make reporting of the results transparent, as it would just be pressing a switch and then stepping back, so that the camera gets a clear view of the screen).

Great, now you know who to blame, and how to nail them.

### D. Audits

Third, the kiosks know who voted for what. (By design, they are the *only* entities who know this -- and kiosks are designed to "forget" this information when they are reset.)

In the event of a dispute, we could instead force the kiosk to reveal everything that it knows.

Obviously this destroys voter privacy (for everyone who had the misfortune of using that one kiosk). But --under the right conditions-- it could prove invaluable. First, it allows us to test the kiosks easily in the time leading up to the election (see next section). But second, it allows a court to oversee the examination of a suspicious kiosk ("under seal", as they call it).

Thus, whoever is trying to tamper with kiosks is vulnerable -- they will have to contend with the fact that they might be caught and blamed after the fact.

However, consider this paradox: By design, there is no way for citizens to "prove" that they voted a certain way (lest this be used against them, by a coercer). Yet, therefore, there is no way of ever *proving* that a kiosk misbehaved, either. It's one voter's word, against one kiosk's! And --interestingly-- a voter might plausibly have *more* of a reason to lie, than would the kiosk (since a voter may be under duress, or be trying to de-legitimize the process, or just be *trolling* the process with frivolous complaints). After all, even if a kiosk reports that 100% of its votes went Democrat, who's to say that they didn't? Who's to say that the voters aren't in a big conspiracy to discredit poor innocent Mr X?

This brings me to my last idea for defeating voter-fraud.

### E. "Proven" Votes

We could established a trusted organization (some new government department) which produces people who *it knows* voted in a certain way.

For example, the Department recruits 200 people in secret, and asks 100 to vote Blue and 100 to vote Red. (Since an equal number of votes are cast for each party, it cannot possibly affect the outcome.)

Where does it obtain these 200 people? Perhaps it drafts volunteers (or conscripts them, as we do with jury duty). Preferably, it employs them. So as to allow them to also vote (two times total, once freely as a citizen and once bound as an employee of the department), this department might conjure new citizens out of the air, on paper (as we do with the federal witness protection program). It doesn't really matter, as long as they get to vote, and receive a BallotID (one that is treated exactly the same as everyone else's).

If **this** vote is recorded improperly, it would be taken as unilaterally definitive evidence of fraud. Moreover, the government department would be aware of the fraud almost immediately (and could move quickly to investigate), but the fraudster would not be aware (at all) that they had been detected. If the department did not find evidence of tampering with the kiosk, it would turn its sights on the department employee (who might be a rouge agent, or incompetent).

This idea (of a new government department) is somewhat far-fetched, and complex. But the hope is that *the mere knowledge* that some of these "department people" are out there, would be enough to discourage vote-tampering. (The vote-tamperer would have to live in fear of these people.)

With these measures in place, the vote is extremely secure. Even if an attacker *can* hack *every* voting machine in the country, it is unclear that they would even be able to make practical use of this ability. They would almost certainly be caught and punished. Since the polling place knows (potentially) which kiosks it assigned to which people, the polling place could even invite back *exactly those people who had the misfortune of being assigned a tampered-kiosk*, to have them re-cast their vote (all of these re-voters would use a single new kiosk).


## 7. HACKING!

Vote via *computers*?! What about hacking!

### A. Basic Anti-Hacking Strategies

* All software will be open source; all hardware will be of the commoditized, mass-produced variety.
* The kiosks will not be internet-aware, will not connect to the internet ever. Humans will only interact with them via physical USB port.
* Ideally, the computers will be so "poorly networked" that they won't even have any way of learning the current time. (Instead, they will only know how long it has been since they were last "reset", see below.)
* Frequent and easy audits (see below).
* Store all the kiosks in a room with 24/7 surveillance. Live-stream the storage (and all the audits, see below). We're lucky to live in a time when live-streaming is so cheap and easy, and widespread.
* Have a whistle-blower program where, if testimony contributes to a conviction for Vote-Hacking (in a trial, no plea bargains), then the whistle-blower is awarded a huge cash prize (say, $100K; anonymously).

### B. Remark: Let's give up on "Education", and instead push the "Audit"

Most citizens have no idea how software works (nor hardware). And they aren't going to learn anytime soon. So let's just admit: any computerized system will be a "black box" to 99+% of citizens.

So we need a way for the layperson citizen to be able to **audit** the system, over and over, to make sure that it really behaves the way that they think it should behave.

Thus, the kiosks should be set up two weeks in advance, and the public should be allowed to come in and test them, via "mock elections". They just "reset" the kiosk (via a physical switch in the back); each enter their votes; and finally tell it that the election is over (again, via physical switch). These citizen-auditors can then see what the kiosk reports back. They can do this over-and-over, all day, if they like.

Moreover, the hardware/software should be generally available at all times. Any member of the public should be able (in principle) to obtain it and run mock elections on it. To encourage the kiosk to perform the same on election day as on every other day, the kiosk software/hardware should be designed **not to know what day/time it is at all**.

### C. Keeping the Votes Private Even If Hackers Hack Everything

Since anyone can audit their own vote, it very difficult for a hacker to change anyone's vote, and get away with it.

However, we might worry that someone would hack the kiosk. Since it knows which BallotIDs it gave to which voters, it can reveal everyone's true vote.

* * We might be tempted to put another layer of obfuscation between the server and the real-world identities. But this is misguided -- it will either make the vote non-auditable, or be defeated by a simple database inner join. So it is ineffective.
* * Instead, it is best to have kiosks output as little information as possible. When all the votes are in, the kiosk should report only: [1] the totals for each ballot initiative (ie, the election results, for fast nation-wide tallying); and [2] all the ballot information, properly formatted (in html or json or whatever) so that it can be uploaded immediately and directly to the Audit-My-Vote site. The secret information (which BallotID was paired with each VoterID) should stay on the kiosk, and would never touch the internet at all.
* * The kiosk can each be given unique and memorable names ("Joyce", "Darth Vader") -- this information would also be uploaded to the Audit-My-Vote site, for greater transparency. When you check your vote, you should recognize the kiosk that you used.
* * As long as each kiosk processes many voters, it should be infeasible for anyone to use the totals to determine who voted for what, even if there are many ballot initiatives. Plus, no matter what happens, each individual voter will have plausible deniability. (Unless, of course, something really did get zero votes, on a particular kiosk -- in which case no one can claim to have voted for it!)
* * Other configurations are possible (such as connecting many kiosks to some kind of wired intra-net, for more aggregation), but they add complexity. The voting process should be very simple, so that only few can doubt its integrity.


## 8. On Election Night

To "quick count" the vote (on election night), just have a group of volunteers go around to each kiosk at 7 PM (or whatever), and get the totals from each kiosk. They can yell out the totals (now displayed on each kiosk) to a different group back at the front table of the polling place. Each of the kiosk-totals is punched into some simple spreadsheet, and (to double-check) yelled back to the group that is touring the kiosks. Thus, they can easily clear out a whole room full of 20 kiosks, in under 10 minutes.

Then, they just add up the numbers on their spreadsheet, and call these in (to CNN/FOX/whatever). No more waiting until 3 AM for the election results.

( The polling place employees can then go around with USB sticks, to get all the OpenVote data, and upload it to the internet. Which citizens can check for themselves, the next day. )

## 9. Limitations

This article does not address "eligibility" (dead people absentee-voting, fake people voting), nor "registration" (people registering twice under fake names, registering in places other than where they live, etc). Further attempts to refine elections, might focus on those areas. Perhaps by ensuring that voter registration databases are fully transparent, and that there are individuals who will be held responsible if they contain erroneous entries.



<!--

passages from an older (more complex, and probably worse) design

#### A. Long Ballots w/ Many Questions

Sometimes, ballots contain multiple measures. This is a problem because, for example, your friends may know that you support "Prop 2" (whatever it is), but they may not know that you are a closet Trump supporter! Since your friends know you are in favor of Prop 2, when they look up your ballot, they would be able to tell whether or not you were an up person or down person!
* * The easiest way to fix this, is to have a "Report Opposite" checkbox button next to every single ballot question. You can fill out the whole ballot normally, but for any questions of which you are ashamed, you can check the "Report Opposite" box. The rule is: if ashamed, then check the box. 
* * Then, when the ballot is submitted, it will give you the "up" and "down" versions, as before. But for each question that you selected "Report Opposite", the displayed answers will be flipped. So if you were an "up" person, your Up ballot will have you supporting Prop 2, but it would also show you voting for Biden. Just like being up-vs-down, the question of which answers are reversed is just a secret between you, the kiosk, and the central vote-counting server.
* * The system will not allow the user to select "Report Opposite" for every single ballot question -- they would only do this if they misunderstood the feature. If users are confused by this feature they should just not use it.

#### B. More Than Two Options

Since there are only two ballot variants ('up', and 'down'), each ballot can have only two options.

America uses "first past the post", so this is probably desirable. Protestors can always leave a question blank (in which case it will be blank in both the "up" and "down" versions). Voting for a third party can be fun, but if a citizen is truly dissatisfied with the two choices, then what they should do is vote against the incumbent. They should do this every election, until they feel they are given at least one suitable candidate.

Other refinements are possible, such as adding more variants (instead of up/down, there could be rock/paper/scissors, or hearts/diamonds/clubs/spades). Or there could be other schemes, in which variant-ballots have votes pushed in a pre-established direction (ie, push all the votes "up" by one slot, if you are "up"). But these all add complexity, and would probably confuse and frustrate a significant number of voters.

-->



-----

### Footnotes

