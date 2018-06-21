---
title: BitAssets - A Digital Assets Sidechain
show_author: true
comments: true
date: 2018-06-21 05:00:00
---

## 1. Motivation

We know that there is a market for digital collectibles[^1].

[^1]: We're not completely sure what percentage of it is "legitimate" (ie, 'productive' and 'sustainable'), but it is definitely there.

And it is quite distinct from the market for money. Let's examine two categories of use-case: digital art, and asset-backed tokens.


### A. Digital Art

Blockchain "digital art" is now, in some sense, possible. And people are interested: we see this in the 'Spells of Genesis' / 'RarePepe' / 'BitCorn' "cards" traded on Counterparty (and of course, CryptoKitties on Ethereum).

![image](https://cdn-images-1.medium.com/max/1600/1*q9cMYWcewoVaeAto-5XbWg.jpeg)

Above: Screenshot of "Book of Orbs" app, which facilitates buying/trading Spells of Genesis cards on Counterparty. Taken from [this article](https://medium.com/@Cryptokeeper/legacy-blockchain-trading-cards-as-an-investment-891052188242) by Crypto Keeper.

People have traded collectibles (including art) throughout history. Today we have "baseball cards", and "the [Met Gala](https://www.cnn.com/style/article/the-met-gala-2018-heavenly-bodies-opinion/index.html)", and even [Genesis Block newspapers](https://www.thetimes03jan2009.com/faq/).

Collectibles are frequently useful as credible signals of wealth, or productive achievement. And we do appreciate them, perhaps only for the experience of perceiving them, or for the memories that they inspire (just as we often find a family photo album, or a Fantasy Football Trophy to be inspiring).

### B. "Asset-Backed" Tokens  

#### i. Inspiration

This section, in particular, was originally inspired by [a Twitter dispute between Nick Szabo and Bruce Fenton](https://twitter.com/NickSzabo4/status/992139030530637824), and Bruce's later [full blown rant](https://twitter.com/brucefenton/status/999503508301729792) on [the subject](https://twitter.com/brucefenton/status/995125290245459969) (on the day *after* this section was written). Bruce and I independently found very similar arguments, leading me to believe that we have converged on truth.

Things later got [even](https://twitter.com/brucefenton/status/994920678141788160) [more](https://twitter.com/brucefenton/status/1001424536234090496) [heated](https://twitter.com/brucefenton/status/1001463152889028609); Bruce is now becoming a shining example of the utility of sidechains, permissionless innovation, and open-ended scientific experimentation!


#### ii. Stock and Bond Markets

The real world contains "equity markets" -- these are "stock markets" where one can trade shares of ownership in various corporations. These markets are influential -- at times, they dominate the public consciousness.

Less popularly known, but arguably more important[^2], are the "bond markets" (markets for loans and debt).

[^2]: The world's bond markets are actually [many times larger](https://www.investopedia.com/walkthrough/corporate-finance/3/bonds/market.aspx) than the world's stock markets, measured by both daily trading volumes and by total market capitalization.

These "capital markets" are essential for a modern economy. They allow different groups of people (especially: prudent savers, dedicated entrepreneurs, and professional speculators) to specialize and cooperate. These groups collectively determine which goods and services our economy should produce.

![image](https://upload.wikimedia.org/wikipedia/de/thumb/a/a8/Bull_new_york_stock_exchange.JPG/640px-Bull_new_york_stock_exchange.JPG)

Above: "Charging Bull" statue outside the NYSE, from [Wikipedia](https://de.wikipedia.org/wiki/Datei:Bull_new_york_stock_exchange.JPG).


#### iii. Can blockchain technology help?

Can a blockchain replicate the functions of a capital market? Can it do so efficiently?

First off, we can expect to lose the censorship-resistant properties (which Bitcoin has, see ["the main benefits are lost if a trusted third party is required"](http://www.truthcoin.info/blog/private-blockchains/)). This is because capital markets imply some underlying enterprise, that exists in the physical world (ie, *outside* of the digital 'blockchain land'). Therefore, it exists legally, in some geographic / political jurisdiction. And that jurisdiction will pass laws, which the corporation will have to obey (for example "corp cannot pay dividends to token holders, unless those holders have been KYC/AML-ed"). So any "shares" on a BitAsset sidechain will probably be exactly what they were before.

Nonetheless, the process by which these shares are created and traded, seems to be cumbersome.

In order to get listed in the first place, entrepreneurs need to pay fees -- these vary with the corporation's size, but are often in the $ X00,000 range.
There's also legal paperwork (for the exchange, and state and federal governments). Also, there's a minimum size -- the NYSE requires firms to have a pre-existing market value of at least $100 million (the NASDAQ requires $45 million). Furthermore, the corporation must have at least 400 [pre-listing] shareholders, the initial stock price must be above some dollar value ($4), their aggregate pre-tax income must be above $10 million for the previous three years. And then they must get approval from the NYSE board. Then there are *more* requirements for being listed globally!

Once the corporation is listed, it must pay annual fees. If investors want to trade a listed asset, they must pay brokerage fees, SEC fees, FINRA fees, etc. These vary tremendously, but seem to have an average of around $5 per trade, and $0.01 per share traded. Moreover, in order to trade at all, investors will need a checking account at a commercial bank -- this requirement alone, immediately excludes the worlds "unbanked" population. And the commercial bank charges its own fees!

A blockchain can be way more convenient. An *advanced* blockchain (ie, with the lightning network, etc), can also be more inexpensive.

We know that Overstock has already issued a "blockchain equity token", so there is at least some *supply* to meet investor demand. And we know that [Delaware recently passed a bill allowing Corps to track their shareholders on a blockchain](https://www.coindesk.com/equity-markets-blockchain-delawares-potential-impact/) so there is some interest in this area.

So it seems worth trying.

#### iv. "Asset Backed" Tokens

Consider a supposedly "third" case:  tokens which are redeemable [ostensibly] for some asset, say "a gram of gold" or "a gallon of oil", etc.

If you are feeling overwhelmed by all of these token types, then I have good news: these "commodity backed tokens" are economically indistinguishable from the "equity tokens" that we just discussed. This is because equity *is* itself a claim...on the assets of the corporation.

Admittedly, in the equity case, the amount repaid is expected to vary from payment to payment, whereas in the (for example) gold-backed case one token is supposed to equal some fixed amount of physical product. But this is not a true difference! For even in a "crypto-gold" case, there is always the possibility that the issuer will default, such that only some [or none] of the gold can actually be redeemed. (Or, the gold may be seized by the federal government and closed down, as happened with e-gold in 2009.) And this uncertainty-of-repaying hinges, in both cases, on exactly the same factors: the [1] prudent management of, and [2] economic viability of, the enterprise that is doing the "backing".

So the "second" and "third" type of token are actually the same.

In fact, the same goes for a "fourth" type, which would include "airline miles", "Marriott rewards points", and "World of Warcraft gold". All of these are "asset backed" tokens -- the asset in question just happens to be a service (a flight or lodging), and/or something entirely digital (World of Warcraft gaming experiences).

So a BitAsset sidechain can support all four types. But is this fourth type any use on a blockchain, vs a private server? 

Probably not -- but perhaps. We know, for instance, that very many "rewards points" go unclaimed each year, and that these are in fact valuable, and that most people would happily be willing to go through a KYC/AML process to acquire them. We also know that companies are happy to sell "points", as it boosts sales and cash flow (just like selling gift cards). Furthermore, the rewards points system is often outsourced to an expensive administrator, so a blockchain may be cheaper. It will be critical for someone to address the nagging questions of customer service, key management, and overall user experience.


## 2. Specification

Our blockchain will be a standard Bitcoin sidechain -- ie, a GitHub fork of Bitcoin plus some new features. Specifically, we'll use some new transactions, and --particularly-- new *outputs*.

### A. New Features

Here is my shortlist of key features. More can always be added later, of course.

    # | Description
    1 | create crypto-collectible (fixed issuance, fixed description)
    2 | create crypto-token (has an owner, who can issue/destroy tokens and edit the token description)
    3 | send crypto-asset
    4 | Dutch-auction a UTXO
    5 | reverse-Dutch-auction a UTXO
    6 | claim some of an auctioned UTXO (ie, participate in a crowdsale)
    7 | place DEX order (offer to trade X asset for Y asset)
    8 | claim DEX order (accept a placed offer)
    
This feature set allows us to replicate the three-step ERC20 formula: [1] create some token, [2] "crowdsale" it off, and [3] get it "listed" somewhere (making it liquid).

Some of these new features will be better-implemented with *transaction versions*, rather than with new *op codes*. This is because they have effects that span more than one output. Specifically, #1 and #2 each involve the creation of a transaction with two related outputs (see below). And #6 and #8 involve two related outputs being spent in one txn.

So I can imagine a total of **three new OP codes** (90:"op split" [optional], 91:"place dex order", 92:"Dutch-auction this UTXO") and **three new transaction versions** (10:"create new asset", 11:"claim DEX order", 12:"dutch auction Bid") -- purely for clarity, I number the "op code values" starting from ninety, and the "tx versions" starting from ten.


### B. Creating A New Asset

First, assets must be created.

#### i. Basics

Here are the facts:

* Creation is triggered by using a "CreateAsset" txn (txn with version number 10). (Only one new BitAsset can be created, per txn.)
* The first output of this txn is a "controller" output, of exactly "one bitasset"\*.
* The second output ("genesis") will actually be the creation of all of the new assets. Since outputs are 8-bytes (and 8-bytes can count up to ~18.4 quintillion), then up to ~18.4 quintillion of the new asset can be created in this stage. If the asset is non-art, then more can be created in a later txn.[^3]
* Any other outputs are normal BTC outupts. These would be used to pay oneself via change address, and therefore to pay a tx-fee to miners.

[^3]: Although, if users try to combine multiple huge outputs into a single output, they would likely experience integer overflow. Frankly, shouldn't 18.4 quintillion be enough?

As I will explain in the section after this one, not all of these outputs will be interpreted as being BTC-outputs. Instead, for the first two outputs, the "type" will have switched to that of the newly created asset. By normal Bitcoin standards, it would appear that this txn is spending more BTC than it loaded, but that is not the case here, because the first two outputs will not be interpreted as "Bitcoins".

![image](/images/create-bitasset.png)

\* These are not actually Satoshis anymore, because satoshi is a unit of BTC, which these are not.

Note: this project should probably ban the existence or spending of 0-value inputs. This is because this project aims to create digitally scarce assets, and this goal is more difficult to achieve if you can spend "zeros" in the same way that you can spend "ones" (in other words, if "having zero of an asset" is meaningfully similar to "having non-zero of it").

#### ii. Identifiers

Assets are defined by an 89-byte payload of data:

      7 bytes  -- Unique ticker symbol
      50 bytes -- Tagline
      32 bytes -- Arbitrary payload


While part of consensus, the first two fields (57 bytes) are for human user-interface-reasons only. ( For something with a more of an identity / domain-name focus, see [my post on an identity sidechain](http://www.truthcoin.info/blog/codex-identity-sidechain/). ) The 57 human-bytes are [ASCII encoded](https://www.asciitable.com/)[^4], and mandatory, so these fields will have to be padded with leading spaces if there are unused characters. The ticker is intended to facilitate trading, and the tagline is expected to help clarify the asset's purpose or to confer aesthetic value to it.

[^4]: Obviously, Japanese users (for example) might prefer to encode using ["JIS X 0208"](https://en.wikipedia.org/wiki/JIS_X_0208) or [Unicode](http://www.unicode.org/charts/), which they absolutely can do and should do. I specify ASCII, because of my focus on an unambiguous [consensus] connection between a digital asset and some real-world idea or asset.

In the UI, we may find new emojis to describe the non-character ascii symbols (#1-31, #127, etc).

Also, if "misleading" easily-confused symbols (such as #139-#141, #220/223, #249/#250, etc) are used, then we should have a warning appear, prompting the user to double-check the ticket symbol. We can also always display the ticker symbol and asset number (see below) simultaneously.

The last field is intended to include a double-SHA256 of some arbitrary JSON data. This JSON can be any size, and can contain any number of elements -- it could be corporate bylaws, or else it could be a photograph, or a descriptive paragraph of text. Or it could be all of these at once, serialized together. Or it could be the hash of an HD movie or 2,000 TB hard drive. The hash commitment is part of consensus, but the contents are explicitly not.

#### iii. Controller Output

For crypto-assets (NOT crypto-art), the first output of the txn is a "controller" output. It designates the "administrator" of the asset -- whoever owns this output is the administrator.

( For crypto-collectibles (ie, crypto-art), the creator explicitly designates the asset attributes/quantity as immutable. So there is no controller output. However, for ease of implementation / code modularity, I assume it is simpler to produce the output "under the hood", but to simply send it to some [provably unspendable script](https://en.bitcoin.it/wiki/Script#Provably_Unspendable.2FPrunable_Outputs). )

The administrator can: 

1. Use this output in a normal transaction (exactly as if they were sending a satoshi), in order to send it somewhere. This allows the administrator to transfer control to a new administrator, to update their keypair, or even to sell control via an atomic swap.
2. Use this output in a new "Create/Update Asset" transaction -- one which shares the same ticker symbol and which selects the "controller output" as an input. This allows the administrator to do two important things: [1] edit the tagline and/or payload (ie the final 82 bytes of the initial 87); and [2] issue new tokens (in a new genesis output).

This design allows asset-owners to become automatically notified when an administrator "updates" an asset they own. These updates could be used to prompt the user to take some action. For example, the 50-byte tagline is large enough to contain a shortened hyperlink (eg [bitly.com](https://bitly.com/) etc). An administrator could update the link, or set and update flag, prompting users to visit the URL, so that they may retrieve a message from the corporation (about votes / dividends / corporate actions), or new JSON data, etc.

#### iv. Genesis Output

The genesis output is where all of the new assets will first appear. It is defined as the second output in a crypto-asset "Create" txn.

This output can then be selected in new transactions, allowing the outputs to be spent and to circulate (just like in Bitcoin transactions).


#### v. Unique Asset Numbers


When created, assets are given a permanent, unique ID number for use in the DEX (see next section).

"Bitcoin" is itself an asset, and has the number "1".

The remaining numbers are assigned chronologically[^5]. This is meant to create some "buzz", "prestige", and historical/nostalgic value in obtaining the lower-numbered assets. It is also for efficiency -- for example, we do not need to use a full 7-bytes to describe the whole asset space until after the first 4.3 billion ticker symbols are claimed.

[^5]: If two assets are created in the same block, there is no problem. We just do what Bitcoin does, and designate outputs has happening "later" if they are more "rightward" in the block's Merkle tree.

Here is the encoding:

* The first 252 asset numbers are encoded with a single byte. (ie, "byte-value: 0" represents the first asset [BTC]; and "byte-value: 251" represents the 252nd asset).
* The next 65,537 asset numbers are encoded with one byte set to "252", and then a two-byte unsigned integer. (Thus, [252,0,0] is the 253rd asset; [252,0,1] is the 254th asset, and [252,255,255] is the 65,789th asset (being 252 + 1 + 65,536)).
* The next ~16.8 million asset numbers are encoded by setting one byte to "253", and then using 3-bytes to count from 1 to 16,777,216. (This defines assets #65,790 [253,0,0,0] through #16,843,006 [253,255,255,255]).
* The next ~4.29 billion assets numbers are encoded by setting one byte to "254", and the using 4-bytes to count from 1 to 256^4. This defines asset numbers #16,843,007 through #4,311,810,303 (which equals 16,843,007+(256^4) ).
* Finally, setting the first byte to "255" allows the user 6-bytes to use for counting. Thus we define asset numbers #4,311,810,304 - #281,479,288,520,960.

 ( The identifiers are a total of: 1, 3, 4, 5, and 7 bytes. )

Thus we've defined up to 281 trillion numbers...enough for a population of 12 billion people to each create ~23,500 unique assets.

( I guess if we need any more, we would just create a second BitAsset sidechain. )



#### vi. Example Asset List

Here I give you an example "asset list".

It is just a random example, but I think it might help give some shape and direction to the project:


    # |Ticker|Art| Tagline                                          | Payload   |  Qnty Issued|
    --|------|---|--------------------------------------------------|-----------|-------------|
    0  BTC     * "Bitcoin"                                           "9o23efs..."         N/A
    1  BRIGHTS * "Bragging Rights"                                   "4mvw010..."   1,000,000
    2  VISA      "VISA Corporation - CryptoShares bit.ly/2Hq8ZEB"    "v4u4rgl..."     500,000
    3  ELF.R   * "Three rings for the Elven-kings under the sky"     "89oiejw..."           3
    4  DWARF.R * "Seven for the Dwarf-lords in their halls of stone" "xgys748..."           7
    5  MEN.R   * "Nine for mortal men doomed to die"                 "hf2p0sv..."           9
    6  ONE.R   * "One ring to rule them all, one ring to find them"  "378v0vj..."           1
    7  GE        "General Electric Co - Common Stock bit.ly/2xXPQue" "eou34j8..."     225,000
    8  UA.RP     "United Airlines - Reward Miles"                    "98jHc93..."  50,000,000
    9  UA.A      "United Airlines - Class A CryptoShares"            "mJvOI3s..."       3,000
    10 JENNUM  * "Jenny, I got your number!"                         "2r8s8pg..."   8,675,309
    11 R.PEPE  * "PepeCash - Official cash of 4chan and /r/btc"      "ufu9vs4..." 111,111,111
    12 LUCK    * "Good Luck. The best luck around, in fact."         "pvh04h0..."   7,777,777
    13 poke006 * "Charizard"                                         "984uv9e..."      40,000 
    14 poke100 * "Voltorb"                                           "0ojev4e..."  80,000,000
    15 poke150 * "Mewtwo"                                            "wojqlkk..."       1,250
    16 XOM.o1    "Barrels of oil - Exxon Mobil bit.ly/2sPJ0Rq"       "8ve0rvi..."   8,400,000
    ...


Now that some BitAssets have been created, let us discuss how to *send* them around to each other.


### C. Asset-Specific Outputs

First we will discuss regular sends, such as sending assets to/from an website, or sending them to one's own personal accounts.

This can be done without any new transaction versions or fancy OP codes whatsoever. We will however need "asset specific outputs".

#### i. Basics

By "asset-specific outputs", I mean that the BitAsset sidechain will have outputs that may appear similar to each other, but are actually of completely different types. In other words, there are several "UTXO sets"[^6] (one per asset issued), instead of just one UTXO set. ( As I will explain, this is a tradeoff consuming more CPU work, but requiring less bandwidth and disk space. )

[^6]: In practice of course there may still literally be one UTXO "set", in a single database somewhere. But I mean that the UTXOs will be of a variety of types, and that txn-validation software will be immediately aware of these types. In other words, the UTXO set, stored locally, may need to have one extra column (actually two, see "controller" outputs below). Any mandatory "UTXO commitments" should certainly include this information, because it would be even more helpful that it would be otherwise -- the information is never included in a txn, and is always inferred from context.

The "BTC" asset (or, more precisely, "each of the outputs that are of the 'BTC' asset-type") is distinctive in a few ways: it is the "first" type; it is the "default" type; and it is the asset used to pay txn-fees to miners. But otherwise, BTC is unremarkable as an asset type.

In the figure below, a typical BTC transaction is on the left (the BitAsset sidechain can, obviously, support these "traditional" transactions). A new asset is created in the third block.

![image](/images/bitasset-utxos.png)

( In the fourth block, there is a single transaction with multiple assets. The blue asset is combined, the green and red are split (probably to pay change addresses). )

Once the assets are created, they exist in one single "genesis output". This output can then be transfered, split, or recombined, just as with any Bitcoin output.

While it asset-denominated txn-fees would be interesting, it would be complicated for miners, and place strange obligations on them. So this is discouraged, by simply not allowing it. Specifically: if a txn spends an output, it is consumed. So if the txn loads "20 Asset Z" and then does not put them into an output, they are simply destroyed.

This architecture makes it so that **assets have all of the wonderful properties of regular Bitcoin txns (cool script operations, nLockTime, Lightning Network, etc)**. It also is (hopefully) a simple and modular design.

#### ii. Tracking the Asset's Type

To make each transactions as compact as possible, the protocol infers as much information as it can. Specifically, it wants to know what *type* an output is, without asking (as this would consume many bytes per txn).

Fortunately, as I will explain, full nodes don't need to ask. Then always know this information.

In traditional Bitcoin, when a transaction selects multiple outputs [in order to spend them as inputs], the total BTC value available [to the txn] is summed.

Here, it works the same way, except that the transaction will be aware of the *variety* of output-types selected, and their *sequence* (the order they first appear, from left to right on the "inputs" side of the transaction). Asset of the same type are summed, and the transactions *outputs* are assumed to have the same type-sequence as the inputs.


#### iii. A Simple Way

From here, the easiest and simplest thing to do, is to only allow one [non-Bitcoin] Asset (nBA) to be moved, per transaction.

Further require:

* That nBAs always spend exactly as much nBA as they load. Ie, not only forbid nBA-txn fees, but also forbid the destruction of assets. So "total nBA input value" but equal "total nBA output value", or else the transaction will be considered invalid.
* That, in the TxOut ordering, that all of the nBA outputs be listed before the Bitcoin outputs.

In this way, the protocol will always know which outputs are asset outputs. Because only two types can ever be loaded at once (one an nBA type, the other BTC), the protocol will also know exactly which type of asset those outputs are. (For the protocol knows that the the first output is an asset output; and then, if it hasn't spent all asset-value, it knows that the next output is also an asset output; and then finally any outputs [after the cumulative sum of asset-input values have been exhausted] will be BTC outputs).

#### iv. Or, A Complex Way

In practice, I think users will mostly be spending only one asset at a time.

But, for fun and to demonstrate the flexibility of "asset-specific outputs", I will describe a way of sending multiple assets at once. It requires a single new opcode, "OP Split", on occasion. This opcode is actually not used as an opcode per se -- in other words, it is NOT used to encumber the output and impose constraints on spending it. Instead, the opcode is used to help the network infer the outputs type.

When a txn is "paying out" to only one output for each asset type, we will need zero total bytes to express asset types. However, if a user wants to "split" an asset into two or more outputs, we will need one byte per split (the "OP Split").

Below, I give a complicated example where six outputs are selected (left column), which are of four distinct types (orange, red, green, and blue). I then show what would happen under six different scenarios.

![image](/images/bitasset-six-exs.png)

The sequences of numbers represent the values that would be typed into the 8-byte "value" fields of the TxOut section of a transaction (see below). An asterisk represents the use of OP Split at the beginning of an output script.

![image](/images/bitasset-clarifier.png)



Now, let's try to take advantage of the blockchain's basic smart contracting abilities. 

### D. DEX Orders

Let me talk about DEX Orders, before I talk about DEX Auctions.

#### i. Intro

How do we trade assets? Well, one way would be to use a "managed exchange" (ME) such as Poloniex or ShapeShift.io.

![image](https://i.redditmedia.com/x-i-5BAvoxB_9Qu9sjNf-gC19RI58WRySPb85w-A8lg.png?s=5a720d66183845652ff76674a95b620e)

Above: This popular meme asks "When will the coin be listed on Poloniex?".

Liquidity is crucial to an asset's success. "Not all liquid assets are successful, but every successful asset is *liquid enough*."

While effective, MEs do have drawbacks. They can refuse to list a coin, and furthermore they engage in shady business practices[^7]. But they are convenient.

[^7]: Based on my imperfect, 2016-era information, much of the Poloniex / ShapeShift business model involves [what we would call] insider trading, and/or shaking down successful ICOs (charging them big $$ [...some % of the total outstanding coins!] to be listed on the exchange). Amusingly (as we just mentioned), this seems to be somewhat similar to the business model of "real" exchanges.

I think the ideal is to have both MEs and a "DEX" (ie "decentralized exchange"). The blockchain option will always be available, as a fallback. This prevents MEs from vetoing an asset. And it also *removes the ME's discretion* (in a good way). In other words, MEs *must* list all assets, because if they don't, it does NOT mean that the asset has been suppressed; it only means that the trading fees associated with that asset will be going to sidechain miners (instead of them)!


#### ii. Placing Orders

DEX orders are first "placed" (by one counterparty), and then later "accepted" (by the second counterparty).

To place a DEX order, the user just spends that output to a special script.

For example, say that Q is a BitAsset, and that Alice wants to sell "780 Q" for "4 BTC". And say she intends to pay a 0.05 BTC txn fee (in order to place this DEX order).

Alice might select two unspent outputs, one containing 2,000 Q, and the other containing 3 BTC. She would then create three new outputs.

The first allocates 1,820 (this would be interpreted as of the Q asset), She would be sending this 1,820 Q back to herself as change, since she loaded more than she intended to sell.

She would then pay 780 to a second output (using OP Split if the "complex method" is used, above, but otherwise doing nothing). This 780 Q will be paid to an output script of the form OR( OP_PlaceDexOrder, OP_Dup...OP_CheckSig ). The first clause (in the OR contract) is the DEX order (explained below); the second clause is a completely "traditional" spend, allowing Alice to "cancel" the order and reclaim her 780 Q at any time.

In the DEX order, Alice specifies:

    n-bytes The ID of the desired asset (n-bytes, recall the "Unique Asset Numbers" above).
    8-bytes Her desired quantity.
    n-bytes The script she would like these coins to be spent to.

Notes: 

* An output locked by this opcode can only be spent in a "version 11" transaction. 
* In practice the first field ("ID of desired asset") will be "Bitcoin" roughly half of the time, in which case it will consume only one byte.
* The second two items resemble a ["classical TxOut"](https://en.bitcoin.it/wiki/Transaction#General_format_.28inside_a_block.29_of_each_output_of_a_transaction_-_Txout).

Finally, the transaction's third output will of course spend 2.95 BTC from Alice back to herself as change. Thus she pays the intended txn fee (of 0.05 BTC), and recovers the 3 BTC she loaded.


#### iii. Claiming Orders

Bob claims a DEX order using a "version 11" transaction.

Version 11 txns have an extra 36-byte slot at the beginning, as follows:

![images](/images/claim-dex-order.png)

With the new 36 bytes, Bob will refer to Alice's "placed DEX order" UTXO (as this is 32 byte hash + 4 byte counter). 

In general, for a V11 txn to be valid, the following new rules apply:

* That first slot must be filled by selecting an unspent output.
* * ...and that output must be an existing DEX order. Ie, it must have the "Op Place DEX" opcode followed by the [AssetType,Quantity,Script] information.
* Bob must "pay" exactly [,Quantity,] of [AssetType,,], by selecting his own UTXOs and using them as inputs. These funds will go to Alice. Bob must be careful, and construct appropriate change outputs to himself as necessary.

If the V11 transaction is valid, then the following happen:

* Bob gets to spend all of Alice's asset. In other words, in the V11 transaction itself, he can load Alice's "780 Q" and spend this Q to whichever output script(s) he wishes to create using the V11 transaction.
* The [AT,Q,S] information (above), while starting as information within another output, will automatically be transformed (by Bob's M4 transaction) into its own bona fide output. Alice will get exactly the UTXO that she said she wanted with her placed DEX order -- her order will be transcribed verbatim (and automatically) into its own output by Bob's transaction.

( If the "implied TxOut 0" concept is too difficult, then a simpler way is to just force Bob to write out TxOut 0 as an actual verbatim copy of Alice's requested value and script. But this wastes blockchain space for no reason. )


### E. DEX Auctions

#### i. Intro

"Decentralized auctions" allow users to "crowdsale" ("ICO", etc) [on the blockchain itself](https://www.ethereum.org/crowdsale). The centralized alternative is for someone to simply set up a website and a multisig wallet for collecting money, and track all incoming payments manually. A DEX auction requires less trust, is more transparent, and is permissionless (since any user can do it).

My implementation of them here, will overwhelmingly resemble regular DEX orders (the previous section), in these ways:

* First, someone will flag an output as being for sale (using a new OP code).
* The seller will specific the script where (s)he would like the sale proceeds to eventually be sent.
* Other individuals will claim this output, using a new (in the first example below, "version 12") transactions.

The differences are:

* In DEX orders, the buyer had to buy the whole output in its entirety; not so for auctions.
* DEX orders involved one seller and one buyer, whereas *auctions* will involve one seller and *many* buyers.
* Thus, we can expect there to be many bids at once (else, the seller would have merely used a DEX Order, and not a DEX Auction).


#### ii. Auction IDs

Each auction requires a unique ID number. This is because this blockchain must be able to handle [1] multiple-auctions at once, and [2] multiple simultaneous Bids on those auctions. So the protocol will need some constant identifier amid all of this dynamism.

Thus the auctioneer must assign a 4-byte ID number for the auction. The ID can be any ID that isn't currently being used by another Auction. If two transactions attempt to use the same ID, then the latter transaction is invalid (and the block is therefore invalid). When an auction ends, its ID goes back up for grabs, and can be used again. In this sense, auction IDs also have their own "UTXO set" (just as each asset does).

The Auction IDs should be specific to each auction-type. In other words, if "92_12" and "93_13" are two different auction-types, then the user should be allowed to make a 92_12 auction with ID "0x0005", and then immediately make a 93_13 auction that also uses "0x0005". This is to address a bizarre edgecase where an eccentric person spams 4 billion auctions at once in order to exhaust the supply of active Auction IDs. To respond, we would just reassign one new OP Code (for example, assign "OP 97_17" to have the exact same behavior as the already-assigned "OP 93_13") -- this would immediately give us another 4 billion IDs to use.

#### iii. Price Format

With DEX orders, we swapped one output for another -- and so the 'market price' could be obtained by simple arithmetic.

For auctions, however, there are many circumstances in which we'd like to have the actual price. So I will standardize an 8-byte "auction price format". The value will range as low as (1/10,000th of a satoshi, or "1 dust") per asset[^8], and as high as (18.4 million BTC) per asset. This covers the full range of plausible values[^9].

[^8]: Of course, no one can receive an on-chain payment for less than a satoshi. A price of "one dust per asset" would, probably mean that the asset must be purchased at least ten-thousand units at a time.

[^9]: On the high end, no asset is expected to sell for more than 18.4 million BTC, as (for starters) no one is ever expected to own that much BTC; it represents (especially after accounting for [probable "lost BTC"](http://fortune.com/2017/11/25/lost-bitcoins/)) virtually the entire circulating supply. On the low end, the quantity "1/10000th of a satoshi" is an extremely cheap amount that could not ever realistically be worth as much as 0.01 USD in 2018 dollars -- that could only happen if Bitcoin itself achieved a value of 1e12 pennies per coin (1.0e10, or 10.0e9 dollars) ie 10 billion USD [2018 PPP] per coin.

I do this in 8-bytes, by defining "dust" as "1/10,000th of a satoshi". I then force all bid-prices to be expressed in "BTC-dust per asset".

Since dust is four decimal points beneath a satoshi, and since each satoshi is eight decimal places beneath one whole BTC, then bid-prices are expressed in units of "BTC, using twelve decimal places". Since 8-byte integers can range from 1 to 256^8 (and since 256^8 ~= 1.84e19), you can hopefully understand the range of possible prices.

See this guide:

    256^8 = 1.84e19       [max value]

    [expressed numerically]
      0        1           [digit counter]
      1234567890123456789  [digit counter]
     18400000000000000000. [max value]
     |
     |       0        1
     /       123456789012       [twelve decimal places]
    18400000.000000000000.      
    18,400,000.0000,0000,0000.  [add commas]
    18,400,000. BTC             [max: 18. million BTC]
              .0000,0000,0000.
              .0000,0001,       [one satoshi]
              .0000,0000,0001   [min: one "dust". 1/10000th satoshi]


#### iii. Two Examples 

Below I will provide two examples for one type of auction, the ["Dutch auction"](https://en.wikipedia.org/wiki/Dutch_auction). It is a popular auction style for IPOs and even US Treasury debt.

However, users are not limited to these, and are highly encouraged to develop their own auction types, and add them by soft fork[^10].

[^10]: Subject only to the usual conditions of a soft fork: [1] that the new feature is not too computationally burdensome on full nodes, and in particular [2] that the new feature does not interfere with any existing features.

* First, "92_12", a simple, traditional first-price Dutch auction [here](www.truthcoin.info/misc/dutch-auctions/#fast).
* Second, "93_13", a more complicated second-price version [here](www.truthcoin.info/misc/dutch-auctions/#slow).



## 3. Other Features

### A. Voting and Dividend Payments

I was surprised to see these features emphasized in [the Ravecoin whitepaper](https://ravencoin.org/Ravencoin.pdf) and in Bruce's video ramblings.

While they *are* important features, I don't see the need for them *at the consensus layer* of any protocol[^11].

[^11]: After all, blockchain technology cannot "magically" compel actions [dividend payments / CEO firings], except perhaps in an absurd case where the entire corporate system (including all sales, accounting, cash flow, labor, etc.) was on a blockchain. But, to me, such a case would itself be describe *a new blockchain*. Specifically, a new *sidechain* [doing whatever it was the proposed crypto-corporation was supposed to be doing].

Instead, I am confident that they are best done outside the protocol.

As I mentioned, I allow administrators to notify all asset-owners and prompt them to take some action (by updating the asset's tagline/payload, see above).

For dividend payments, administrators would designate an ["ex-dividend date"](https://www.investor.gov/additional-resources/general-resources/glossary/ex-dividend-dates-when-are-you-entitled-stock-cash), probably by specifying a block number. Then, everyone can use the blockchain to learn exactly which keypairs (or whatever) owned an asset at a given time. The corporation in question would set up a designated location (eg, a webpage). Users would visit it and submit a signed message --- an invoice demanding a dividend payment. Then the organization could process this data and administer the payments.

This process could be repeated for corporate elections -- administrators set a voting date, users are prompted to visit a website and submit a signed ballot. Then the corporation releases the results of the election, possibly with fancy cyrptography to demonstrate that they have done so properly.


### B. Asset "Groups"

Nothing would prevent third parties from constructing privately-managed "groups" of assets.

More interestingly, someone could register an asset that was *itself* a list. They could then manage the list, if it were a list of assets (such as the S&P 500). Or else, they could have an artistic, immutable list (for example, of "151 Pokemon" or something), and then that list would be fixed forever, and immune to tampering.


### C. Third-Party Triggers / Games 

Obviously, ownership of an asset could trigger arbitrary events in third-party games. Someone could own (or wager) "skins", or "World of Warcraft Gold". For users, this is as simple as signing a Bitcoin message.


## Conclusion

There is undeniable investor interest in non-money blockchain tokens (what I call "BitAssets"). These tokens predominantly take on two forms: [1] a "crypto-art" form, with immutable characteristics; and [2] an "asset-backed token" form, which can have administrators who interact with owners on an ongoing basis.

I provide a sidechain design which supports both types. BTC is used to pay network transaction fees, but new assets can be created, traded or auctioned off. Encouragingly, the basic features ("creating" and "spending" assets) are easiest to add, and the other can be added later on an ongoing basis as soft forks.

Update (June 6th): [Coinbase, Circle Vie to Create Brokerages for Crypto Securities](https://www.bloomberg.com/news/articles/2018-06-06/coinbase-seeks-broker-dealer-status-in-keystone-capital-takeover)

Update (June 14): The SEC has provided [some guidance on when tokens might meet the Howey test of a security](https://www.sec.gov/news/speech/speech-hinman-061418). Marco Santori [unpacks](https://twitter.com/msantoriESQ/status/1007317386721218560) [twice](https://twitter.com/msantoriESQ/status/1007637639829344256).


### Footnotes

-----
