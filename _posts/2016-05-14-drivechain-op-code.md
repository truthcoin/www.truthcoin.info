---
title: The Drivechain OP Code
comments: true
---


### "Smart Contracts"

[Many](http://www.coindesk.com/smart-contract-1-million-bitcoin-rootstock/) [people](http://counterparty.io/news/proposal-for-ethereum-smart-contracts-on-counterparty-mainnet/) *think* [that](http://www.coindesk.com/turing-complete-smart-contracts/) [they](https://www.cryptocoinsnews.com/smart-contracts-future-blockchain/) [want](https://www.youtube.com/watch?v=d0hxWC7sP2k&feature=youtu.be&t=1h8m30s) ["smart contracts"](http://motherboard.vice.com/read/smart-contracts-sound-boring-but-theyre-more-disruptive-than-bitcoin).

Unfortunately, the phrase "smart contracts" is undefined. Mostly, in my opinion, this is because these people are too confused to know what they want.

I will clarify, on their behalf: the smart contracts we want are called **Sidechains**. Examples include: The [Elements Project](https://elementsproject.org/elements/), as well as [Hivemind](http://bitcoinhivemind.com/).


### Two Strategies for Bitcoin Smart Contracts

I will now draw a distinction between:

| .| Sidechain Method | Ethereum/Rootstock Method |
|------------------|---------------------------|
| New functionality ("new protocol") is added...| Slowly (and deliberately) | Instantly (and without deliberation)|
| New messages are added to blocks... | Instantly | Instantly|
| Messages per protocol...|Many (ie, 400 Bitcoin tx, 28 Namecoin tx)| One (each message contains its own protocol)|


Here is the distinction visually:

![two-sc-methods](/images/two-sc-methods.png)

This image is from [a presentation I recently recorded](https://www.youtube.com/watch?v=xGu0o8HH10U&list=PLw8-6ARlyVciMH79ZyLOpImsMug3LgNc4&index=1), which argues that **the Sidechain Method is right and the Ethereum method is wrong**.


### Getting There From Here 



Sidechains need [a lot of things](http://www.truthcoin.info/blog/drivechain/). The full code library might be a lot of work.


### The Pull Request

The Bitcoin soft fork, in contrast, is very simple. Presented compactly, it would require the following:

	1. Generate a "MinerDB"...
    	...which scans all coinbase transactions for 'inserted data'...
    	...and discriminates the signals in that data as [1] "uninterpretable / something else", [2] "adding a sidechain", [3] "proposing a withdrawal", and [4] "upvoting or downvoting a withdrawal"...
		...and stores/accumulates that data in a database.

	2. A new OP Code "OP_CheckWorkScoreVerify"...
    	...which freezes coins, such that they can only be moved if...
    	...they are spent by a transaction where...
		...the tx-ID matches a Withdrawal Entry in the MinerDB...
     	...and the Withdrawal Entry has achieved the appropriate 'miner score' (see below).
		

The MinerDB of part (1) checks "Work Score" using the following rules:

	1. (Once Per Sidechain) A sidechain is added (MinerDB item [2]), with a special coinbase data format, which might be some encoding of the following information: AddSidechain(PrivateKey = 5JQrzT..., WaitingPeriod = 2016, VotingPeriod = 1000, ReqScore = 200). I'll consistently use these specific values throughout this example.
	2. (Once per Withdrawal) Withdrawals proposed from the sidechain must meet a few requirements:
		* Each must be the txid of a correctly-formatted Bitcoin transaction.
		* Each must only select inputs 'from' the correct sidechain address: GetBitcoinAddress(GetPublicKey(5JQrzT...)).
		* The transaction must be valid (no double-spending, etc).
	3. These withdrawals must have a score of zero for 2016 blocks. After this, miners are allowed to increment the score upwards or downwards by one. This continues, one incriment per block, for 1000 blocks.
	4. After a Withdrawl has endured both the 2016 waiting period and the 1000 voting period (3016 blocks total), the database entry would be labeled "ended" or "concluded", and its score would stop changing.
	5. If the statment (required score <= the final score) were TRUE, the transaction could be included in a Bitcoin block.

Upvote/downvote messages would ideally be very small -- details in [step 5 here](http://www.truthcoin.info/blog/drivechain/#process-side-to-main-transfers).
		
### Help Wanted

I think that I am too busy to code the OP code myself. Moreover, my relative productivity is not maximized at "write Bitcoin C++ code". Basic econ says I should cough up some $$$, instead of my time.

Ideally, I would attract someone with commit access to Bitcoin Core, as they -presumably- are most intimately familiar with the quality standards and formatting norms.

I think that $1000 / day is a fair rate, considering the rarity of such individuals. That's $125/hour ($260K annually).

Moreover, I feel that it would take, at most, 3 days (16 hours). To account for the planning fallacy, we'll make it 4 days.

#### Official Terms

To be clear, you get $4000 if one of these conditions are met:

* You code a Drivechain OP_Check<font color="green">WorkScore</font>Verify pull request which makes it into Bitcoin Core.
* You code a Drivechain OP_Check<font color="green">WorkScore</font>Verity pull request (which is not immediately the subject of ridicule for being invalid, poorly formatted, difficult to understand, etc), but the pull request is rejected **because** the Drivechain proposal is itself rejected for any reason. (If Drivechain is substantially modified, this might count as a "rejection" of the original.)

These conditions are necessary, because I have a limited ability / availability to review coded submissions. Furthermore, my review would be redundant / irrelevant -- what matters is Bitcoin Core process.

#### Suggested Schedule

My guess is that the first day would be spent groking [the concept](http://www.truthcoin.info/blog/drivechain/). The second day would probably be spent experimenting/meditating on the appropriate way to build the MinerDB. The code itself could probably be written in a 5 hour sprint, with 3 hours for breaks. Then a whole fourth day to cover The Unforseen.

Keep in mind, this is *only* "the Bitcoin piece". Sidechains require more (for example, the sidechain itself, whatever its features, must be able to scan the mainchain for deposit transactions, and it must be able to form and collate withdrawal transactions).

### The Debate -- Is Drivechain Good for Bitcoin?

Nothing should make it into Bitcoin without discussion!

Here I will now publish two presentations:

* [Sidechain Privatization](https://www.youtube.com/watch?v=xGu0o8HH10U&list=PLw8-6ARlyVciMH79ZyLOpImsMug3LgNc4&index=1) (maximizing smart contract value, handling net-negative in-fighting among smart contracts)
* The Potentially Detrimental Effects of Sidechains, And What To Do About Them (forthcoming)

For details about Drivechain itself, please consult [my lengthy exposition](http://www.truthcoin.info/blog/drivechain/) of the proposal.