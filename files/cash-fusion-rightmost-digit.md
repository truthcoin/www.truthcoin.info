 
    Breaking CashFusion With Pen & Paper (But Only Sometimes)
    Paul Sztorc
    11 December 2020



### Intro

CashFusion is [a proposed mixing scheme](https://www.bitcoin.com/cashfusion-fund/) for BCH. Roger Ver has taken up the battle-cry of "more potential combinations than there are atoms in the universe" (see [here](https://www.reddit.com/r/btc/comments/fvznf5/roger_ver_bitcoin_cash_transactions_will_soon/) and [here](https://twitter.com/rogerkver/status/1329809991671353346?s=20)).

There was [a little bit of talk on this](https://www.mail-archive.com/bitcoin-dev@lists.linuxfoundation.org/msg08576.html) on the bitcoin-devs mailing list, and it attracted my curiosity.

So in April I sunk an afternoon into investigating this matter. I read ([this article](https://bitcoinmagazine.com/articles/do-coinjoins-really-require-equal-transaction-amounts-for-privacy-part-one-cashfusion) by Aaron van Wirdum), and spent a day typing up this mini-post -- I hope you enjoy.

I'd hate for people to read too much into this, as it is one of my lowest-effort posts of all time. (Hence the delay in publishing it.) 

### Summary

* The "more potential combinations than atoms in universe" line, comes from a mathematical technique for counting "the number of ways to arrange X objects into Y groups". It completely *ignores* the fact, that the transaction's input-values must add up to the output values.
* It is occasionally easy to defeat CashFusion completely, if the input-amounts have zeros in very unlucky places. I show this with three examples.
* CashFusion could work pretty well in practice -- I tried to break a small one but gave up after 40 minutes. CF works *much* better if:
* * [1] there are as many inputs and outputs as possible, 
* * [2] the outputs all use the same orders of magnitude and significant digits (no "unlucky zeros"),
* * [3] the fee is shared by the participants somewhat chaotically, and
* * [4] if each user splits their funds into at least two or three outputs.
* I still think that CoinJoin isn't the philosophically the best direction to take for privacy. Privacy implies that the conformist-bootlicker-types are blending in perfectly with subversive-criminal-progressive-types -- but the conformist-bootlickers will abandon CoinJoin the moment they are asked to. Privacy can only be achieved if either [1] anti-privacy individuals are forced to use the scheme (not practical), or if the privacy feature is "meta-private" (you can plausibly deny that you've ever used it).



## 1. The Stirling Heuristic

The source of that "atoms in the universe" line is [this calculation](https://www.wolframalpha.com/input/?i=sum+over&assumption=%7B%22F%22%2C+%22Sum%22%2C+%22sumlowerlimit%22%7D+-%3E%221%22&assumption=%7B%22F%22%2C+%22Sum%22%2C+%22sumfunction%22%7D+-%3E%22stirlings2%5B53%2Cx%5D+*+stirlings2%5B38%2Cx%5D+%22&assumption=%7B%22F%22%2C+%22Sum%22%2C+%22sumupperlimit2%22%7D+-%3E%2238%22), which involves [Stirling numbers of the second kind](https://en.wikipedia.org/wiki/Stirling_numbers_of_the_second_kind).

I will call this the "Stirling Heuristic".

Does it always accurate describe CashFusion? I'm afraid not.

Many of the "possible ways" (of combining inputs into outputs), are in fact *not possible*, because the output-values won't add up.

Ie, something like...
    
      In     Out
     8000   12000
     9000    5000
        2       0.9
        4       1
                1
                3.1

...would have 266 possibilities according to the Stirling Heuristic. But in reality, there is only one possibility: 8000 and 9000 merged into 17000 then split into 1200 5000; 2 merged into 2 and then split into 1 and 1; 4 merged into 4 and then split into 0.9 and 3.1.

The Stirling Heuristic *would* apply perfectly, if the situation looked like this...

      In     Out
    8000      ?
    9000      ?
       2      ?
       4      ?
              ?
              ?

...and furthermore if it were the case that *every combination* of left-?s could add up to *every combination* of right-?s.

But of course that is a little silly.


## 2. Examples Where the Stirling Heuristic Collapses Completely

With extremely bad luck, the Striling Heuristic is 100% misleading, as instead of being "many possible comibinations" there is just *one* possible combination.

### A. One Valid Partition

Part of the pitch for CF is that, even if a valid partition is discovered, there could be "many valid partitions".

    For example, with hundreds of inputs and outputs,
    it is not just computationally impractical to iterate
    through all partitions, but even with infinite
    computing power, one would find a large number of
    valid partitions.

"Many valid partitions" means that even if the attacker discovers a way to group the inputs into outputs, they will not know if they have found **the** way that was actually used.

However, with what I am about to show, they will *know* they've found it. Furthermore, they can *prove* that they've found "the" single way.

### B. Example 1 - Small Example

#### i. Setup

Here's a small CashFusion (6 in, 5 out), to warm up:

    In:         Out:
     
     2.         10.  
     6.3        10.2 
     8.4        10.3 
     9.2        10.4 
    11.         10.41
    14.41

First, let us label the inputs (A through F), and outputs (i through v).

We will begin with the right-most digit.

For both the Inputs and Outputs, I will check and see which types of digit are achievable (via addition).

#### ii. Asterisk Rules

On the input side, if is the case that we MUST use a given input to reach a given digit, then both that digit and the special input(s) will be starred. On the output side, if is the case that we MUST send a given digit to a SINGLE output, then both that digit and the associated output will be starred.


      In          Out
    A 02.00    i   10.00
    B 06.30    ii  10.20
    C 08.40    iii 10.30
    D 09.20    iv  10.40
    E 11.00    v   10.41*
    F 14.41*   =========
    =======            0
          0            1*
          1*

Whenever we have a match ("1\*" matching "1\*", in this case), we know that the starred-input MUST be a part of the starred-output.

     We know that F --> v

Since we've nailed down that input, we delete it and start over. We also subtract the value of F from v.

      In          Out
    A 02.00    i   10.00
    B 06.30    ii  10.20
    C 08.40    iii 10.30
    D 09.20    iv  10.40
    E 11.00    v   -4.00
    =======    =========
          0            0

If no asterisks, we delete the right-most digit, and travel leftward to the next one.

      In          Out
    A 02.0    i   10.0
    B 06.3*   ii  10.2*
    C 08.4*   iii 10.3*
    D 09.2*   iv  10.4*
    E 11.0    v   -4.0
    ======    ========
         0           0
         3*          3*
         4*          4*
         2*          2*
         7*          --
         5*          --
         6*          6
         9*          9

You can see how this starts to get useful quickly. How could B not go to output iii? Output iii ends in ".3", but there just isn't any way to get to ".3" without using input B. Similarly, we can't get to ".2" without using input D. Nor can we get to iv without using C.

     We know that B --> iii
     We know that D --> ii
     We know that C --> iv

Delete and subtract...

      In          Out
    A 02.0    i   10.0
    E 11.0    ii   1.0
    ======    iii  4.0 
         0    iv   2.0
              v   -4.0
              ========
                     0

We are done with this digit. Move leftward...

     In      Out
    A 02*   i   10
    E 11*   ii   1*
    ====    iii  4
       2*   iv   2*
       1*   v   -4
            ======
                 0
                 1*
                 2*

Thus, we know that A must be linked to iv, and E must be linked to ii. 

     We know that A --> iv
     We know that E --> ii

Delete and subtract...

     Out
    i   10
    ii -10
    iii  4
    iv   0
    v   -4
    ======

#### iii. Solution

So, we now know everything:

     We know that A --> iv
     We know that B --> iii
     We know that C --> iv
     We know that D --> ii
     We know that E --> ii
     We know that F --> v

     i and ii have the same owner: the owner of D,E
     iii and v have the same owner: the owner of B,F
     iv is owned by: the owner of A,C

#### iv. Claimed Privacy, vs Reality

[Theoretically](https://www.wolframalpha.com/input/?i=sum+over&assumption=%7B%22F%22%2C+%22Sum%22%2C+%22sumlowerlimit%22%7D+-%3E%221%22&assumption=%7B%22F%22%2C+%22Sum%22%2C+%22sumfunction%22%7D+-%3E%22stirlings2%5B6%2Cx%5D+*+stirlings2%5B5%2Cx%5D+%22&assumption=%7B%22F%22%2C+%22Sum%22%2C+%22sumupperlimit2%22%7D+-%3E%225%22), this CashFusion had...

    > Sum[StirlingS2[6, x] StirlingS2[5, x], {x, 1, 5}]

    3381

...3381 "possible combinations of input and output". But we can see easily that, in reality there is only ONE possible combination. And everyone can not only learn it, but prove it!


That was just a small example. What about when it gets bigger?

After all, the CashFusion spec says:

    In CashFusion, we have opted to abandon the
    equal-amount concept altogether. While this
    is at first glance no different than the old
    naive schemes, mathematical analysis shows
    it in fact becomes highly private by simply
    increasing the numbers of inputs and outputs.


### C. Example 2

#### i. Setup

If you followed the logic above, you may already see that we *could* add more inputs with certain "unlucky" last-digits...

    In:

    02.00
    06.30
    08.40
    09.20
    11.00
    14.41
    + 14.42 +
    + 14.44 +
    + 14.48 +

    Note:  0 is a dead ("non-unique") digit already, 1 is already
           unique. 2 can be made unique. 3 is dead because it
           could be reached by 1+. 4 is alive because so far we
           can only produce 0,1,2,(3). 5 is dead because we could
           make it with 1+4. 6 can be made with 2+4, so it is dead. Is 7 alive? Unfortunately, it is not, because
           so it via 1+2+4. Thus, so far we can make: 0,1,2,(3),4,(5),(6),(7). That means 8 is alive. Notice
           that 8 further deadens 0, because 8+2=0 -- but it 
           doesn't matter because zero was already dead.
           8+1 = 9, therefore 9 is dead.

    Out

    10.00
    10.20 + 14.42 = 24.62
    10.30 + 14.44 = 24.74
    10.40
    10.41 + 14.48 = 24.89


...without gaining a shred of additional privacy. These new inputs all have unique right-most digits, so they are all immediately eliminated in the first two rounds of the right-digit-algorithm.

Watch:

    Round One
     
      In          Out
    A 02.00    i   10.00
    B 06.30    ii  24.62
    C 08.40    iii 24.74
    D 09.20    iv  10.40
    E 11.00    v   24.89*
    F 14.41*   =========
    G 14.42*           0
    H 14.44*           1* -- can only be sent to "9"
    I 14.48*           2
    =======            4  -- could be sent to "4" or "9"
          0            8* -- can only be sent to "9"
          1* -- can only be obtained from F
          2* -- can only be obtained from G
          4* -- can only be obtained from H
          8* -- can only be obtained from I

    Round Two
     
      In          Out
    A 02.00    i   10.00
    B 06.30    ii  24.62*
    C 08.40    iii 24.74*
    D 09.20    iv  10.40
    E 11.00    v   -4.00
    -------    =========
    G 14.42*           0
    H 14.44*           2 -- can only be sent to "2"
    -------            4 -- can only be sent to "4"
    =======             
          0            
          2*
          4*

    Round Three
     
      In          Out
    A 02.00    i   10.00
    B 06.30    ii  10.20
    C 08.40    iii 10.30
    D 09.20    iv  10.40
    E 11.00    v   -4.00
    -------    =========
    -------            0
    -------
    -------
    =======             
          0            

And you see that the right-digit algorithm has already reduced this larger problem back to the original smaller problem.

#### ii. Solution

So, the solution is:

     We know that A --> iv
     We know that B --> iii
     We know that C --> iv
     We know that D --> ii
     We know that E --> ii
     We know that F --> v
     We know that G --> ii
     We know that H --> iii
     We know that I --> v

     i and ii have the same owner: the owner of D,E,G
     iii and v have the same owner: the owner of B,F,H,I
     iv is owned by: the owner of A,C, 


#### iii. Claimed Privacy, vs Reality

Our Modified "Medium Example 1" CashFusion, added three inputs.

Supposedly, these three extra inputs should open the door to many more combinations. Instead of 3381 combinations, there should be...

    > Sum[StirlingS2[(6+3), x] StirlingS2[5, x], {x, 1, 5}]
     
    164,102

...164,102 "possible combinations of input and output". But, just as with the first toy example, **in truth there was only ONE possible combination**. Everyone can learn it **and prove it**, using simple arithmetic.


### D. Example 3

#### i. Setup

Hopefully, by now it is clear that I can make CashFusion look even worse, with a more contrived example that has more "bad luck that is right-digit based".

For example, what if we just take Example 2, copy the inputs and outputs, lower them by four orders of magnitude, and add them back into the problem.

This is a little silly, but I also think it makes for a good explanation.


    In:

    A 02.00
    B 06.30
    C 08.40
    D 09.20
    E 11.00
    F 14.41
    G 14.42
    H 14.44
    I 14.48
    + J .0002,00
      K .0006,30
      L .0008,40
      M .0009,20
      N .0011,00
      O .0014,41
      P .0014,42
      Q .0014,44
      R .0014,48

    Out

    i    10.00
    ii   24.62
    iii  24.74
    iv   10.40
    v    24.89
    + vi   .001000
      vii  .002462
      viii .002474
      ix   .001040
      x    .002489


I hope it is obvious that the right-digit algorithm I've outlined, will solve the rightmost "half" of the problem immediately, before it even notices the "left half".

With the right half out of the way, it solves the left half, exactly as easily as it did before.

The "higher number of inputs and outputs" had absolutely zero significant effect on how long it takes to solve the algorithm. Instead of taking 1/100th of a second, it might take 2/100ths of a second.

So again, with trivial arithmetic, the entire problem is solved.

#### ii. Solution

     We know that A --> iv
     We know that B --> iii
     We know that C --> iv
     We know that D --> ii
     We know that E --> ii
     We know that F --> v
     We know that G --> ii
     We know that H --> iii
     We know that I --> v
     ---------------------
     We know that J --> ix
     We know that K --> viii
     We know that L --> ix
     We know that M --> vii
     We know that N --> vii
     We know that O --> x
     We know that P --> vii
     We know that Q --> viii
     We know that R --> x

     i and ii have the same owner: the owner of D,E,G
     iii and v have the same owner: the owner of B,F,H,I
     iv is owned by: the owner of A,C, 
     vi and vii have the same owner: the owner of M,N,P
     viii and x have the same owner: the owner of K,O,Q,R
     ix is owned by: the owner of J,L, 


#### iii. Claimed Privacy, vs Reality

Now we will get a *very* good look at the treacherous nature of the Stirling Heuristic. Because Example 3 added *many* inputs and outputs, but all of it amounted to only 2x additional attacker compute time.

Let us see what the heuristic reports, now that we have doubled the inputs to 18 and outputs to 10.

    > Sum[StirlingS2[18, x] StirlingS2[10, x], {x, 1, 10}]

    5,161,826,943,804,663

So, we have gone from a claimed "3381 combinations", to a claimed "164,102 combinations", to a claimed **"over 5.16 quadrillion" combinations**.

But all of these claims are false, because in all three cases there was never a need to check all of these combinations exhaustively. In fact, there was never a need to check a single combination.


## 3. Example With Random Digits

### A. Contrived vs Random

The examples above are all contrived -- I made them up to show the unreliability of the Stirling Heuristic.

Now I will try again with a small more realistic example. To CashFusion's credit, I found this impossible to do by hand, and even wrote a tiny computer program to help. Even then, I failed to completely crack it after about 45 minutes of trying. But I still guess that a specialized computer program would crack it easily.

### B. Example 4

#### i. Setup

Here, in the fourth and final example, all of the digits were taken from a uniformly random distribution. (I took random digits from random.org.) I did change some of the leftmost input-digits to 8 to intentionally make them more similar to each other, so as to make my job *harder*. Then I randomly added them together.


    In:               Out:
     
    A 8.4809,2042      i     6.5004,3459
    B 6.5831,7609      ii    9.2833,7262
    C 4.3501,4451      iii  15.2334,3000
    D 3.3066,6320      iv   18.3707,5971
    E 8.7799,3110 
    F 7.1220,0016 
    G 8.6618,0705 
    H 2.1033,5439

#### ii. Round One
 
    Round One
     
    In:                Out:
     
    A 8.4809,2042      i     6.5004,3459
    B 6.5831,7609      ii    9.2833,7262
    C 4.3501,4451      iii  15.2334,3000
    D 3.3066,6320      iv   18.3707,5971
    E 8.7799,3110      =================
    F 7.1220,0016                      9 
    G 8.6618,0705                      2 
    H 2.1033,5439                      0
    =============                      1
                0 -- D, E, B+C
                1 -- C, H+A, F+G
                2 -- A, C+F+G
                3 -- A+C, or B+G
                4 -- G, A+B+H
                5 -- C+G, B+F
                6 -- A+G, F
                7 -- C+F, C+A+G, A+B+F
                8 -- A+F, C+G+H
                9 -- B, or A+C+F
     
     We are defeated this round, and must move leftward.

#### iii. Round Two

    Round Two
     
    In:                Out:
     
    A 8.4809,2042      i     6.5004,3459
    B 6.5831,7609      ii    9.2833,7262
    C 4.3501,4451      iii  15.2334,3000
    D 3.3066,6320      iv   18.3707,5971
    E 8.7799,3110      =================                
    F 7.1220,0016                     59 -- must go to i
    G 8.6618,0705                     62 -- must go to ii
    H 2.1033,5439                     00 -- must go to iii
    =============                     71 -- must go to iv
                ...
               59 -- can't be reached without 20, nor 39
               62 -- can't be reached without 42
               00 -- can't be reached without 10, nor 39
               71 -- can't be reached without 20

I wrote a tiny program to compute the various ways that one could add up the two rightmost digits of the 8 inputs.

The program did NOT do any other obvious things. One such thing would have been to, while adding up these digits, *also* add up the entire value to check and see if it is implausibly large. For example, my program found a way to achieve the digits "71", by adding 42,9,51,20,10, and 39, to make "171". But that cannot possibly be the real way that we get to the "71" of output iv, because the other three outputs have nearly 30 Bitcoin in them total, and only remaining inputs (F and G) don't add up to anywhere close to that.

Also, to save space, I've only listed on the left, the digits that would have appeared on the right.

The inputs of 20 and 39 are both being double-claimed. That seems to be a contradiction, so I'm not really sure how to interpret that. Perhaps it indicates the presence of 'other valid partitions'. After all, 20 (D) can't go to both 59 (i) and 71 (iv).

I selected the link between 10 (E) and 00 (iii), to see if it could shed light on 20 and 39...

#### iv. Round Three

    Round Three
     
    In:                Out:
     
    A 8.4809,2042      i     6.5004,3459
    B 6.5831,7609      ii    9.2833,7262
    C 4.3501,4451      iii   6.4534,9890
    D 3.3066,6320      iv   18.3707,5971
    E -----------      =================                
    F 7.1220,0016                     59 -- must go to i
    G 8.6618,0705                     62 -- must go to ii
    H 2.1033,5439                     90 -- must go to iii
    =============                     71 -- must go to iv
                ...
               59 -- can't be reached if 20, 39 are removed
               62 -- can't be reached if        42 is removed
               90 -- can't be reached if     39 is removed
               71 -- can't be reached if 20 is removed

...but it shed no additional light on anything.

At this point I'm pretty confused about the persistant dual-appearance of 20 and 39, so I checked my Answer Key (after all, I made this problem). 39 is supposed to go to iii (ie, "90"). I also checked and 20 is supposed to go to 71. Perhaps it is a general rule that, a finding with 2 contradictions should always lose to 1 contradiction. Or perhaps not.

I'm doing this for fun and I'm already getting very bored, so I'll just do the 39 output...

#### v. Rounds 4,5,6


    Round Four
     
    In:                Out:
     
    A 8.4809,2042      i     6.5004,3459
    B 6.5831,7609      ii    9.2833,7262
    C 4.3501,4451      iii   4.3501,4451
    D 3.3066,6320      iv   18.3707,5971
    E -----------      =================                
    F 7.1220,0016                     59 -- must go to i
    G 8.6618,0705                     62 -- must go to ii
    H -----------                     51 -- must go to iii
    =============                     71 -- must go to iv
                ...
               59 -- can't be reached if any of 42, 9, 51, 20, 16, 5 are removed
               62 -- can't be reached if any of 42,        20,       are removed
               51 -- can be reached (no matter what is removed)
               71 -- can't be reached if                   20         is removed

...after which point, there is least now a compelling logical reason to assign 20 to 71.

    Round Five
     
    In:                Out:
     
    A 8.4809,2042      i     6.5004,3459
    B 6.5831,7609      ii    9.2833,7262
    C 4.3501,4451      iii   4.3501,4451
    D -----------      iv   15.0640,9651
    E -----------      =================                
    F 7.1220,0016                     59 -- must go to i
    G 8.6618,0705                     62 -- must go to ii
    H -----------                     51 -- now a collission
    =============                     
                ...
               59 -- can't be reached if any of 42, 9, 51, 16, 5 are removed
               62 -- can't be reached if any of 42, 9, 51, 16, 5 are removed
     

But, actually, if you just look at it you see that C is the exact same value as iii. Beginner's luck I guess.

    Round Six
     
    In:                Out:
     
    A 8.4809,2042*     i     6.5004,3459
    B 6.5831,7609*     ii    9.2833,7262
    C -----------      iii             0
    D -----------      iv   15.0640,9651
    E -----------      =================                
    F 7.1220,0016*                   459
    G 8.6618,0705*                   262
    H -----------                    651 
    =============                    ---
                                     721 = (459+262)
                                     913 = (262+651) 
              459                    110 = (459+651)
              262
              651

Unfortunately, my simple simple algorithm isn't noticing that i+ii add up to F+G (which would lead it immediately to the right answer and full solution). Turns out that the idea of re-splitting the outputs helps a great deal -- earlier [in Round Three] it tried to trick the algorithm into assigning 42 [A] to 62 [ii], which would have been a mistake. 

Oh well. Maybe someone can improve it. An obvious improvement would be to convert all the numbers to binary, first (since the zero digit is so problematic). Probably, there already exist specialized cryptographic / combinatorial algorithms for fast cracking.

### C. Summing Up Example 4

Obviously I got a little overconfident here, after three examples that were (by construction) trivial to break with a pen and paper, I bit off more than I could chew with Example 4. I think if it just had one fewer input, I could have done it easily, but then again that is the whole point of CashFusion, right? If there are many outputs, it quickly becomes impractical.

Anyway, some guidelines for good CashFusions:

* Only use amounts that are as similar as possible. Certainly, at the very least, they should be the *same order of magnitude*, and have the same number of decimal places.
* The digit "0" is extremely problematic and should be avoided, especially at the end of the value.
* Use a lot more than 10 inputs and outputs.



## 4. Conclusions

### Striling Heuristic is Probably Unreliable

In any event, I do think I have shown the limitations of the "stirling heuristic". Often it does not apply at all.

When amounts differ substantially, the entire Fusion can be cracked open by hand with just a pen and paper and some arithmetic.

[This paper](https://www.comsys.rwth-aachen.de/fileadmin/papers/2017/2017-maurer-trustcom-coinjoin.pdf) seems to be a much much better direction, than just naively relying on the Stirling Heuristic.
