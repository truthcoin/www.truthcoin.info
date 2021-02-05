
Hard Fork Wishlist


Accumulators


Eliminate Class-4 block-flaws via accumulators, as I describe [here](https://www.truthcoin.info/blog/fraud-proofs/#hard-fork).


Specifically:

1. During block construction, take the "txn vector", turn it into an "expanded vector" (defined below), before calculating the Merkle Tree as normal.
2. During block validation, we take the Merkle Root, the supplied "txn vector". Transform the "txn vector" into an "expanded vector", before calculating the Merkle Tree and checking it against the Root in the block header. We then check the "accumulators" (the "inserts" in the expanded vector) as we check the txns.

The "expanded vector" is a vector such that...

    Regular Txn Vector: [Tx1, Tx2, Tx3, ..., TxN]
     "Expanded" Vector: [ Tx1, (z1,z2)_1, Tx2, (z1,z2)_2, ..., TxN, (z1,z2)_N ]

...the each transaction is "snug" against its "accumulators". In other words, in the Merkle Tree, each TxID is adjacent to the information that would prove it were guilty of a Class IV Block Flaw. 

As a reward for doing these two extra steps, SPV nodes gain new powers...

Previously, SPV nodes could only be warned:

1. of an invalid txn lurking in a block, and 
2. of the fact that a given txn is actually not included in any block.

...but with this new Accumulator-Merkle-Tree, SPV nodes can now be warned (efficiently and succinctly) that: [3] a block violates the blocksize/SigOps limits, or [4] the txn fees of the block don't add up properly to what the miner is paying themselves in the block's coinbase txn.

---


Related:

Fixing the merkle-mutuation bug in Bitcoin Core
----------------------------------------------

https://github.com/Bitcoin-ABC/bitcoin-abc/blob/master/src/consensus/merkle.cpp

Just change the "hashes.back()" on line 56, to a new uint256 that is always zero. Or --even simpler-- just change the word "back" to the word "front".

Then you could slowly remove all the mutation stuff (for a tiny speedup), and remove the big scary warning as well.

