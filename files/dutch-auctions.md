

    Appendix 1: Two Dutch Auctions, for the BitAsset Sidechain
    Paul Sztorc
    June 21, 2018

Appendix to [BitAssets Sidechain](www.truthcoin.info/blog/bit-assets.md).

Below I present Two Auction Types.

## 1. Fast Dutch Auction ## {#fast}

### a. Preamble

This particular auction would use "OP code 92" on the sell side (ie, to create the auction), and "version 12" transactions on the buy side (ie, to bid in the auction).

Thus it might be abbreviated "OP_92_V_12" or "92_12".

### b. Summary

The first Dutch auction emulates the "clock" style auction. We start with a high price, and the clock ticks down to a low price. Anyone can buy any quantity, at any time. 

<img src="https://upload.wikimedia.org/wikipedia/commons/c/c5/Bundesarchiv_B_145_Bild-F004491-0002%2C_Kirschenversteigerung_an_der_Mosel.jpg" alt="Dutch auction clock" width="400" height="294">

Above: A clock used in a Dutch auction, [from the wikipedia article](https://en.wikipedia.org/wiki/Dutch_auction). 

All sales are final, so to speak. It is an "open outcry, decending price auction".

It is simpler, but it has the disadvantage of being a "first price" auction. Such auctions [cause unnecessary confusion](https://en.wikipedia.org/wiki/First-price_sealed-bid_auction#Comparison_to_second-price_auction), as bidders feel obligated to conduct labor-intensive research into each other's valuations.

It also has the disadvantage of *stigma* -- a long period in which basically no one is buying anything. However, there is also *suspense* -- for the lull will be followed by a dramatic period in which almost everything will be purchased at once. Certain bidders will feel obligated to pay undivided attention to the auction throughout this entire time.

### c. Creating the Auction ("The Seller's Part")

Here is the list of parameters that must be provided, immediately following an **OP 92** (which we might call "OP FastDutchAuction"):

    4-byte Auction ID
    4-byte Starting Blocknumber (ie, the Date/Time on which the Auction begins)
    4-byte Ending Blocknumber (ie, the Date/Time on which the Auction concludes)
    8-byte Starting Price
    8-byte Ending Price
    n-byte Alice's desired destination script.

Each auction must have a 4-byte unique ID, as we mentioned above.

The starting and ending blocknumbers describe when the auction takes place.

 ( Users are allowed to set a date such that the auction wont start for a while. In fact, the start date should probably be at least six blocks from the time the auction-txn is created. If the user is accidentally trying to make the auction take place several hundred years from now, we will definitely need several UI warning prompts to appear (etc) -- as broadcasting such a transaction would lock the output up until that time. )

The minimum **bid price** is an 8-byte integer. Such an integer can count from 1 to 256^8 (which is ~1.84 \* 10^19).

Finally, if the auction succeeds, we need to know how to get Alice the money she raised.


### d. Example

Let's set up an example: Imagine Alice wants to sell a UTXO that contains 7777 of the asset "J". Alice has spent it to OP 92, and she is therefore auctioning it off in a '92_12 Auction'. She has chosen Auction ID "0x0008".

She believes that a fair price for J is approximately 0.0015 BTC per J. This comes out to 15,0000,0000 dust (ie 1.5 billion see above). But Alice knows that she may be mistaken about this. So, she will set the initial price high, and then have it expire lower. Starting price may be 7 billion dust, and the ending price may be 1 billion dust.

Suppose it is currently block number 500,000. Alice wants the auction to start roughly two weeks from now (at block 502,000), and she'd like it run for about a week (until 503,000).

'Bob the Bidder' wants at least 30 J, and will pay up to 0.06 BTC for it. Let us assume that Bob either wants the whole 30 J, or none at all. Therefore, his reservation price is equal for the whole 30 J, at 0.0020 BTC per J, (because this is .06 BTC / 30 J). (And, 0.002 BTC is equal to 0.0020,0000 statoshis, or 20,0000,0000 dust (ie 2 billion dust).

### e. Bidding in the Auction (ie "Buying")

After the auction is created, Bob can bid in it, using a **version 12** txn.

The **minimum bid price** is computed by all full nodes and used in validating V12 txns. The minimum bid price starts at "Starting Price" and ends at "Ending Price". Here I will say that it decreases linearly -- this is simplest to implement, and easiest for bidders to understand. Thus we calculate price_delta_per_block = total_delta / total_number_of_blocks. In our example the price decreases by ( (7 billion - 1 billion) / (503,000-502,000) ) = 6 million dust per block. That is 600.0000 satoshis; or .0000,0600 BTC.

Since this auction begins by offering J for sale at 0.0070 BTC each, Bob will wait to bid. He will not bid until the minimim price has decreased by a total of 0.0050 BTC (ie, from its starting value of 0.0070 to Bob's reservation price of 0.0020). This decrease will have occurred after 0.0050/0.0000,06 = ~ 834 blocks, or 5.8 days. At that point, if there is still any J left, Bob will bid on it[^1].

[^1]: Although, as I mentioned early on, Bob may try to wait even longer before placing his bid -- it depends on Bob's knowledge of rival bidder's valuations for J. This is a disadvantage of first-price auctions, in my opinion.

Bids ("version 12" txns) each have an 8-byte prefix:

    4-byte Auction ID
    4-byte Current Blocknumber (ie "fill or kill")

And they have different validity rules as follows:

* None of the TxIns should be nBAs (non-Bitcoin assets). Bob should only select Bitcoin TxIns. (Ie, Bob can't move assets in this txn, nor can he use them to place bids.)
* The first and second TxOuts of this txn are "special" (see below), but the remaining outputs are not. So with the third and later TxOuts, Bob can do regular-txn-things, such as: pay himself change, split his BTC, and pay the miner txn-fee by leaving a balance unspent.

Regarding the first two TxOuts:

* In the first TxOut (ie TxOut 0), Bob should credit himself the 30 J, and he should assign it to one of his keypairs (or to wherever he wants it to go). In other words, it would probably have the "value" field equal to 30, and the script field equal to a pay-to-pubkey-hash chosen by Bob.
* In the second TxOut (ie TxOut 1), Bob should spend 0.06 BTC to Alice's desired destination script.

In order for nodes to include such Txns in a block, they must ensure:

* That the txn "Current Blocknumber" matches the block's Blocknumber.
* That the txn's *implied Bid price* (ratio of the "value" of "TxOut 0" over that of "TxOut 1") is greater than or equal to the current *minimum bid price* (see above) of the Auction with this Auction ID.

Finally, nodes must ensure:

* That the total amount of asset spent never exceeds the amount Alice put up for auction.

After the auction ends, Alice should be able to rebuy her own asset, but spending her BTC to her own destination script. So it may not be necessary to build that part.


### f. Improvements

A better design would allow the price to decrease geometrically. This is because all prices are ratios, and so they should always be interpreted geometrically/logarithmically.

A second improvement would be to swap the per-block linear decrease, with something that involves fewer "stale bids". Instead of recomputing the minimum price *every* block, instead recompute it every n blocks. Then, 

 It would also not recompute the price every block, it would recompute it every n blocks. And instead of forcing bids to include "Current Blocknumber", they would instead reference the 




## 2. Slow Dutch Auction ## {#slow}

### a. Preamble

This particular auction would use "OP code 93" on the sell side (ie, to create the auction), and "version 13" transactions on the buy side (ie, to bid in the auction).

Thus it might be abbreviated "OP_93_V_13" or "93_13".

### b. Summary

This auction is a little more complicated to implement, but it has the advantage of being a second-price auction. Bidders can publicly bid whatever their true valuation is, and then stop paying attention. They will either get the asset at their desired price, or at an even better one.

### c. Creating the Auction ("The Seller's Part")

Here is the list of parameters that must be provided, immediately following an **OP 93** (which we might call "OP SlowDutchAuction"):

    4-byte Auction ID
    4-byte Starting Blocknumber (ie, the Date/Time on which the Auction begins)
    4-byte Ending Blocknumber (ie, the Date/Time on which the Auction concludes)
    8-byte The Minimum Price
    n-byte Alice's desired destination script.

It happens to have the same fields as the example above. And they have the same meanings.


### d. Bidding in the Auction (ie "Buying")

I will use the same "Alice vs Bob" example that I used above. In this case, however, Alice used "OP 92" and Bob will be using "version 13" txns.

Bob's reservation price (of 2 billion dust per J), is expressed below in 8 bytes of hex, as: 0x0000000077359400.

Here are the basic points for these bids:

* The V13 txn must contain a 12-byte prefix:
* * The first 4 bytes of this are the Auction ID (so that we know which auction Bob is bidding on). In this case: "0x0008".
* * The second 8 bytes is the 'bid price' (see above for format), up to which Bob is willing to pay. In our case: 0x0000000077359400.
* None of the TxIns should be nBAs. Bob should only select Bitcoin TxIns. (Ie, Bob can't move assets in this txn, nor can he use them to place bids.)
* The first and second TxOuts of this txn are "special" (see below), but the remaining outputs are not. So with the third and later TxOuts, Bob can do regular-txn-things, such as: pay himself change, split his BTC, and pay the miner txn-fee by leaving a balance unspent.

Regarding the first two TxOuts, they may have requirements that appear counter-intuitive at first:

* In the first TxOut (ie TxOut 0), Bob should act as though he has already been given the 30 J, and he should assign it to one of his keypairs (or to wherever he wants it to go). In other words, it would probably have the "value" field equal to 30, and the script field equal to a pay-to-pubkey-hash chosen by Bob. 
* In the second TxOut (ie TxOut 1), Bob should "fund" his bid, by paying his total reservation amount. In this case, 0.06 BTC. But he should send this money to himself!

At first, the first TxOut is not actually spendable.

The second is spendable -- if Bob spends it while the auction is still "in progress", his bid is canceled/withdrawn. Thus, Bob can cancel his bid at any time.


##### c. Auction "Success"

Full nodes maintaining a list of all valid bids (sorted by 'bid price'). They also maintain a "cumulative sum" of the bidder's desired asset-quantities, so that they know which bids are, currently, "winning bids". Losing bids, in contrast, are bids that are too low -- they have been outbid by some other bid.

When the auction is over (at the Ending Blocknumber, above), we check to see if there are enough bids.

If there are not, then the auction is said to have "failed". In this case, nothing happens -- the TxOut0s never become spendable, and all Bidders can withdraw their money. Full nodes stop tracking the Auction ID and it can be used for something else. Alice's auction UTXO becomes available to her again -- either this can be built into OP 93 itself, or else [back when she created the auction txn] all Alices could be made to follow a transaction template: OR( Auction, nLockTime pay-to-pubkey-hash ). Users software could ensure that Auctions are only displayed to them if the nLockTime element of the transaction is after the auction end block. (Allowing Alice to spend the coins earlier would be equivalent to allowing Alice to unilaterally cancel the auction while it is still in progress, which might be an interesting feature for some use-cases.)

If there *are* enough bids, then the auction "succeeds". Then, the following happen immediately:

1. Software identifies the final "winning bids" using [1] the decreasing-price-sorted list of bids, [2] the cumulative sum of bid quantities, and [3] the value of Alice's UTXO. We move from the top of the bid list down, making each bid a "final winner" until total buying quantity is >= total sale quantity. 
2. We set the "auction price" by looking at the "marginal bid" (defined as: the very last bid that was declared a "final winner"). The marginal bid will have the lowest bid-price (among all "final winner"s); its price becomes the "auction price".
3. We mutate the marginal bid, so that, across the whole auction, total buying quantity is *exactly equal* to total sale quality. Fortunately, since the marginal bid's price is equal to the auction price, this isn't too difficult: [1] we set the bid "desired quantity" equal to whatever quantity is remaining, and [2] we issue a credit to Bob equal to [("original quantity" - "new quantity") \* price]. (Note: whenever anyone is credited BTC in this section, *all of the arithmetic results must be truncated down to the nearest satoshi*.) We do this by appending a new TxOut to the end of Bob's txn.[^2]
4. For winning bids, the "TxOut 0"s immediately become spendable. (These Bobs get the assets they paid for.)
5. For losing bids, the "TxOut 0"s will never become spendable. (These Bobs must withdraw their bid, and get their BTC back, which they can do at any time.)
6. If the auction succeeds, then Alice gets paid her BTC. She selects her auction output (the OP 93 in section "a", above) and makes a payment in the amount of: ("auction price" * "quantity auctioned"). The destination of this payment must match the "destination script" (given in "a", above). These BTC cannot be spent, until a 100 block maturity period passes.
7. If the auction fails[^3], then Alice gets her asset-UTXO back. (She selects the auction output, and pays the entire amount to her destination script. It is an asset, not BTC, so this TxOut will have to follow the usual rules, and go before her btc/change/fee TxOut).
8. Many of the Bobs will be entitled to *refunds*. They can *partially* spend their bids (the "TxOut 1"s). Selecting this input will give Bob the following amount: [value \* ('bid price' - 'auction price')]. [^4] Bob can then spend this to himself.

[^2]: If Bob happened to use all of his outputs somehow, then we simple to *not* do it. But this is very very unlikely.

[^3]: If Alice doesn't want this to happen, she can place a high bid in the auction. She will end up paying herself for some of her asset, but the auction will nonetheless "succeed" from the perspective of the blockchain.

[^4]: Remember that this must be truncated down to the nearest satoshi.

Once Alice does her spend, and the last Bob-refund is spent, then Auction UTXO set is empty. And so the Auction ID can be reused. 

----

### Footnotes