---
title: BTC Codex - The Digital Identity Sidechain
comments: true
---

> With a social theory of identity, combined with blockchain bearer tokens, we might achieve a realistic improvement over PGP.

Motivation & Scope
--------------------

(Basics) Any private computer system implies the existence of identities. Without identities, privacy and most commerce would be impossible, and the web would be overrun by spam, Sybil attacks, and so forth. Fortunately, authentication (usernames and passwords) was invented, allowing individuals to control, and "own" a private slice of cyberspace.

(Today) Many authentication methods are used today. They might best be arranged along a "convenience-security tradeoff": On one extreme, Snowden used PGP, and insisted that his correspondents use it as well (despite their considerable reluctance). On the other extreme, all Americans today use their Social Security Number as an ID (and as a password) -- it is used to file taxes, apply for credit, and fulfill civic obligations.  The SSN is convenient because enrollment is free, automatic, and universal.

This project aims at neither extreme, and instead seeks an intelligent trade-off between convenience and security. 

![extremes](/images/id-extremes.png)

By the metric of "convenience", the SSN is the most successful.

![extremes](/images/ssn-convenient.png)

However, by the metric of "security", PGP is the most successful.
(As far as we know, the security is invincible.)

### Comparison Table


|Feature                                     |  PGP |  SSN | Codex |
|:-------------------------------------------|------|------|-------|
| Forgot your password? (Reclaim lost ID).   |  No  |  Yes |   Yes |
| Identities are "human readable".           |  No  |  Yes |   Yes |
| You own your identity -- no administrator. |  Yes |   No |   Yes |
| Utilizes modern cryptography (signatures). |  Yes |   No |   Yes |
| Transfer identity to new crypto-key.       |  Yes |   No |   Yes |



This project DOES address these problems:

* Identity Namespace Collisions (Will the real "John Smith" please stand up?)
* Allowing a single identity to prove that it signed various things at various points in time (so as to facilitate reputation / credit reporting / Sybil-protection). This is superior to the "WoT strategy" of collapsing 'reputation' to a single dimension, because reputation is multidimensional.
* Users who pick insecure passwords.
* Security [that scales with value](http://www.truthcoin.info/blog/scaling-security/).
* Password Reuse / The fact that passwords are used at all (when we could instead use signatures).
* Humans have powerful software in their brains already. This software has modules for (the meatspace equivalent of) 'identity management' and 'identity theft'. However, this meat-software goes unused (mostly because the imposition of [awkward passwords](https://xkcd.com/936/) actively circumvents it).
* Competing standards (vs "something unique/inimitable about *this standard*, so that we can coordinate on one").
* Corporations / Refrigerators can have their own "identity", if you care about that kind of thing.

This project DOES NOT address these problems:

* Someone might learn my name, or my age or whatever...even if *I don't want them to!* (This is a lost cause, thanks to Google / e-Verify / LinkedIn / Whitepages / the "database join").
* How can we *decentralize* identity? (PGP already does this).
* How can we use unbreakable h4kk0r encryption to thwart *The Man*'s violation of our *Freedoms*? (Again, PGP does this already).


![id-claims](/images/id-claims.png)

Design
-------

Our design calls for a blockchain\* which tracks and updates key-value pairs. Whereas, typically, blockchains are used to achieve decentralization, in this case one is used for security and uniqueness. Security: a single administrator cannot steal *all* of society's most valuable identities. Uniqueness: the question of "Why should I switch to your ID standard?" (which is of immense practical importance) is met with the answer that *this* one is public. There are many ways of privatizing something (one per owner), but -per algorithm- only one *public* system.

\*A merge-mined Bitcoin sidechain.

The sidechain is financed by transaction fees. The transactions are paid by users who wish to add or update entries to the database. Nodes are run by anyone who wants (or, for compliance purposes, is required) to verify identities "properly". (Everyone else would just use Google's node).

In general, the **value proposition** is that digital service providers (Facebook, YouTube, Disqus, etc) can replace several labor-intensive services with software. In particular, customer support tickets related to resetting accounts: either because the passwords are lost, or because accounts/identities were stolen. Moreover, the existence of a durable, long term, multipurpose digital identity may allow new services to be rendered (tiered Spam prevention, for example), and may improve existing services (encrypted email, accurate routing of payments, secure filing of taxes, etc).

The identities are associated with cryptographic keys, and these keys are managed **in a way similar to how humans use physical keys**. Namely, on television show Seinfeld, the main characters all have copies of each other's apartment keys, for emergencies.

In this system, entries are added with the form:
   
    add( name=(First, Middle, Last), public_key=H(U), Friends=(U1, U2, ...), Weights=(W1, W2, ...) )

With this command, someone joins the network. They declare their name, a newly generated public key (for which they have the private key), a set of trusted friends, and a set of weights for each friend. They also receive their private key, represented as a 12 word seed, which they write down.

Although I notate "U" for public key, in practice I use a hash of the private key. This saves valuable blockchain space at no cost. Users are free to broadcast their actual public key at any time. They may include the key with each email (at which point it can be verified by hashing it).

(Moreover, the hash can actually be H(RSA_Pubkey + BTC_Stealth_Address), facilitating anonymous Bitcoin payments to any identity.)

Crucially, the user can ask *their friends* to 'reset their password', with:

    reset( name, new_public_key=U, Signatures = (S1, S2, ...) )

For security reasons, you can not reset your own password (of course, you can set yourself as one of your "friends", and give yourself great weight). The reset process prompts everyone with alerts (that the process is taking place), and advice about how to check identity properly, as well as latest tips for avoiding phishing / scams. For fun, the blockchain may report each user's "shame score", which is a count of how frequently a given user forgets his/her password.

Finally, to account for the ever-shifting landscape of friendship, each user can:

    update( name, new_friend=U_n, Signature = S)

Which adds 5% weight to the new public key. This can only be done once per week.

Finally, for name-changing (most urgently required for marriages), we have:

    rename( name, new_name, Signature = S )

This can only be done once per *year*, and only if it survives a grace period (of one month). During this grace period, your friends can cancel the name change. This is to protect identity thieves from forcing one to adopt a false name for a year.

Other functionality is possible. For example, identity theft "alerts", which are broadcast for a fee and which alert id-checkers to be extra diligent.


Use Cases
----------

* Unique IDs
	* More private than SSNs ("we need the last four of your social")
	* Helps even with paper forms:
		* Filing Taxes
		* Voting
		* Jury Duty
* Better Logins (Potentially, for All Websites)
	* Standardized Login Process
	* Use of Signatures = more secure.
* Positive Proofs -- Ie, prove that "it was you" who signed those contracts (which were so fulfilled)
	* employment contracts / sales contracts (for self-employed / contractors)
		* I hired this person.
		* This person terminated employment here, in a professional way.
	* debt / mortgage / etc
	* sales purchases (credit card purchases / bank checks)
	* arrest record / background check
* Assertions
	* "I claim, under penalty of perjury, that I am...<at least 21 years of age>".
	* <citizenship, residence, physical appearance, etc>
	* (These attestations are not "on the blockchain", which is ideal).
* Spam Control
	* Filter accounts unless someone is using a name that was registered <more than 1 year ago>.
	* (Account ages would be as long as human ages).
* Payments
	* IDs could be associated with "reusable BTC addresses" (aka Stealth Addresses), giving users their own bank. If so, Bitcoin "Vaults" may assist with time-locked security.


Proof Diagram
---------------

![proof-diag](/images/id-contracts.png)

Notice that, if a private key is stolen, the attacker cannot forge *past* contracts. This is because forged contracts will have the wrong date (they will not have been inserted into the Bitcoin blockchain at the appropriate time).

After IDs are reset (using the social mechanism), contracts would automatically be "retroactively unsigned".

Conversely, if keys are misused by their *current* owners, then cryptographic proof of this misuse will exist permanently. For example, if "John Smith 28" signs thousands of contracts (each with different, mutually-exclusive wordings and conditions) and [Tierion-timestamps](https://tierion.com/) all of these, he *does* have the option of picking-and-choosing desirable contracts -from this set- after the fact. In this way, he has the semi-power to backdate contracts. However, if these mutually-incompatible contracts are discovered (at any point in the future), blame can be cryptographically ascribed to John Smith 28.

Scale
--------

Total economic costs are unknown, but we can estimate one cost: storage.

Under the following assumptions:

* Six billion humans use the Codex.
* No one forgets their password ever.
* 100 bytes, per Name field.
* 3 bytes, per sequence field
* 20 bytes, per Hash Commitment

We have 6 billion users * ( 100 + 3 + 20 bytes/user ) = 738 Gigabytes. 

A 1,000 GB hard drive costs roughly 80 USD. According [to Gallup](http://www.gallup.com/poll/166211/worldwide-median-household-income-000.aspx), this amount is about 8 tenths of one percent of median household income.


Problems
----------

**1] Miners might just censor updates from people they don't like.**

Not really a problem, because the database doesn't need to be realtime interactive...as long as the current database-state exists, anyone can look up a (Name, Pubkey) pair. Since they have the current pubkey (and since the pubkeys rarely change).

For the duration a 51% miner-coalition is in control, however, victims will not be able to change their Name, Public Key, or Associates. So, for them, convenience has temporarily degraded to the PGP level. Nonetheless, they retain any identities they possessed before the attack began.

**2] Front-Running Names**

This is not really a problem here (as it would be in the case of Namecoin). If "Paul Felix Sztorc" is taken, the protocol will just auto-register "Paul Felix Sztorc II" on my behalf. Then I will communicate my number to my friends.

For a business, it may be more of a problem. Businesses may not need their own cryptographic identities, however (as each and every employee will have one).

**3] Friendship Drama**

"The whole world will know that we're not best friends anymore!""

Yes, yes. Very tragic. Choose family, or co-workers for this reason, then.

**4] "Now *they* know who to torture/blackmail!"**

First of all, if adversaries were going through with physical capture and torture, they probably willing to put in the comparatively small effort it takes to to locate ones friends. In other words, they knew anyway.

Secondly, they need 50% of your friend-weight (and, they need them at around the same time). If you choose a large enough quantity of friends, and/or individuals who are geographically distributed, then crime against the group as a whole becomes more difficult.

**5] This is putting too many eggs in one basket! Once an attack gets this key, they'll get into all of my stuff!**

Not necessarily. Even if this Identification method becomes widespread, to the point where it becomes the "single sign on" for the internet, it does *not* necessarily need to replace *all* the security features of, say, gmail. For one example, most websites today use two factor authentication. A second example: most websites track the *physical devices* which connect to their servers for authentication. Google will often ask you to "add a device" if your device is unfamiliar. Meanwhile, it will notify you about foreign devices which are claiming to have you behind them. These practices could (and should) persist.

**6] My mean "friends" *stole* my identity and won't give it back!**

The individuals you "chose" are not your friends! Create a new identity and start over. Children should have their parent's / parent's friends as the ID-resetters. The elderly might use their own children as the resetters.

Alternatively, sue them for identity theft. (It's not like you don't know where to find them.)

**7] I'm very unpopular and/or too paranoid to trust friends.**

Use PGP. (And, don't forget your password!) Or, use your lawyer.



Appendix
===========


Theory
-------

What is an identity? I argue that: Identity is social.

Identity, in a practical sense, *isn't* individual -- I already know who *I* am...and I always will. If I become someone else, through brain damage, then it won't really matter if neo-I gets a new identity, will it?

Let's address the problem which digital identity might solve. Imagine I get the following email:

    Dear Paul,
    I am "Francis Bacon". Please reply at your earliest convenience. But, beware! Lots of people are going around pretending to be me, via email! Don't trust them and don't reply to them.
    Sincerely,
    Francis

And further suppose that I receive a *nearly identital* email from someone who also claims to be Francis Bacon! Now I have two emails with contradictory claims. How would I tell which Francis Bacon is the "real" one, especially if I had never met him before?

Well, I might rely on *other people* who *had* known Francis. I might call his parents, or work colleagues, and ask them for their opinion -- "Which email address is the right one?". This is likely to be sufficient evidence.

Choosing Unique Identities
----------------------------

The entire point of a name is that it distinguishes "you" from "not you". Thus, the sharing of names is undesireable.

Historically, names have achieved uniqueness in several ways:

* Leonardo "da Vinci" (place of birth)
* Adam "Smith" "(b. 1723)" (family name, year of birth)
* "King" Henry "VIII" (unique title, numeric sequence)

Most of these would appear to be discriminatory:

* Age (in most cultures, it is impolite to be compelled to reveal this -- for women in particular)
* Place of Birth (may be a basis for discrimination)
* Job Title (titles of nobility are inherently anti-egalitarian)

In fictional world of "Game of Thrones", identities and names (particularly family names) are of preeminent geopolitical significance (even, mortal significance). A character introduces herself as "Daenerys Stormborn, of House Targaryren, First of Her Name, Queen of Meereen, Queen of the An...Breaker of Chains, Mother of Dragons". This introduction uses, in order: "given name", "weather conditions at birth", "title of nobility", "family name", "numeric sequence", and "job titles / resume".

Since job titles are transient and transferable (as are titles of nobility), it would seem appropriate to establish the identity first, and only later link the identity to titles and achievements.

It would seem that:

    <First> <Middle> <Last> <Sequence>
	
...is the most appropriate naming syntax. With geographical partitioning automatically occuring (as an consequence of names in different languages). Some cultures, like the Chinese, have no middle name, However, new traditions are emerging (where Chinese adopt an additional Western given name, so that they have three total). On the other hand, some cultures have more than three total names. These can be all ascribed to the "middle name" slot, subject to a character limit.

The use of three names makes it less likely that the 'Sequence' field will leak information about the individual's age. The <Sequence> field may also give parents useful information about name uniqueness!

The [proper encoding of names](http://kunststube.net/encoding/) is, to me, unknown. Capital letters may be unnecessary (the convention being universally known), yet international characters (for example, the Spanish tilde) would certainly be required.

For the sequence field, two bytes (up to 65,536) may not be sufficient. The current most-popular US name has [a frequency of nearly 40,000](http://www.dailymail.co.uk/news/article-2487263/James-Smith-tops-list-13-popular-combinations-U-S.html), and the (first) name "Muhammad" is apparently shared by 150 million individuals worldwide. Three bytes should be sufficient.


Establishing Identity in the Real World
----------------------------------------

To get a passport, one must bring other identification documents (from a predefined list). There is, hence, a principle of "redudancy" as well as one of "circularity".

In addition, there are still penalties for attempting to subvert the document-issuance process. Those who sell fake ID may spent a considerable time in prison.

We have three principles: redundancy, circularity, and punishment. Redundancy and Circularity have simple software-parallels (multiple ways to reset or reclaim an identity, all of which are distinct but related to each other). Punishment is more difficult.

![id-redundancy](/images/id-docs.png)
