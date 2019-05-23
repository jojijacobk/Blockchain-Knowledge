   * [What is a blockchain?](README.md#what-is-a-blockchain)
   * [A simple use case of blockchain technology](README.md#a-simple-use-case-of-blockchain-technology)
      * [Betting game](README.md#betting-game)
      * [Blockchain solution for the betting game](README.md#blockchain-solution-for-the-betting-game)
   * [Bitcoin, the first blockchain application](README.md#bitcoin-the-first-blockchain-application)
      * [Transaction request](README.md#transaction-request)
      * [Transaction encryption](README.md#transaction-encryption)
      * [Transaction message structure](README.md#transaction-message-structure)
      * [Transactions grouped as blocks](README.md#transactions-grouped-as-blocks)
      * [How a block is formed](README.md#how-a-block-is-formed)
      * [Mining](README.md#mining)
      * [Implementing the Consensus Algorithm](README.md#implementing-the-consensus-algorithm)
      * [Why is mining needed ?](README.md#why-is-mining-needed-)
      * [Lifecycle of a transaction in Blockchain visualized through different pictures](README.md#lifecycle-of-a-transaction-in-blockchain-visualized-through-different-pictures)
   * [Footnotes](README.md#footnotes)
      * [Hash function](README.md#hash-function)
      * [Wallet](README.md#wallet)
      * [How fraud is prevented by blockchain?](README.md#how-fraud-is-prevented-by-blockchain)
      * [Oraclization](README.md#oraclization)
   * [References](README.md#references)


# What is a blockchain?

![](attachments/820083932/825506329.png)

<img src="attachments/820083932/826221569.png" width="400"/><br/>

  

<img src="attachments/820083932/826221594.png" width="250"/><br/>

  

A blockchain is an immutable, sequential chain of blocks. Each block can
contain transactions, files or any data you like. But the important
thing is that they are chained together using hashes. 

-   It is a type of distributed ledger. 
-   It is like a network of replicated databases, which are synchronized
    via the internet, and are visible to anyone within the network.

Blockchain networks can be :

-   private with restricted membership similar to an intranet (eg: OBCS)
-   public, like the Internet, accessible to any person in the world.
    (eg: bitcoin)

# A simple use case of blockchain technology

## Betting game

Imagine you and I bet $50 on tomorrow’s weather here. I bet it will be
sunny, you that it will rain.

Today we have the following options to manage this transaction:

1.  We can trust each other. Rainy or sunny, the losing one will give
    $50 to the winner. However, one can easily not pay the other.
2.  We can turn the bet into a contract. With a contract in place both
    parties will be more prone to pay, however, should any of the two
    decide not to pay, the winner will have to go with legal processes
    which is not cool.

As we can’t trust strangers and also enforcing a contract requires time
and money to pay for legal proceedings, there is a new better
alternative - which is to use blockchain technology to power this
betting game.

## Blockchain solution for the betting game

Blockchain allows us to write a program (in this case a betting program)
and install that code into the chain. To participate in bet, both of us
can send $50 to the program. This program will keep the $100 safe and
check tomorrow’s weather automatically on several data sources based on
our code's logic. Sunny or rainy it will transfer automatically the
whole amount to the winner. Each party can check the contract logic,
and once it’s running on the blockchain it can’t be changed or stopped.

# Bitcoin, the first blockchain application

The most known and discussed application of the blockchain technology is
the digital currency called Bitcoin. As Bitcoin is the first application
of blockchain technology, it makes sense to learn how a blockchain works
by understanding bitcoin.

If I want to send some of my bitcoin to you, I publish my intention and
the nodes scan the entire bitcoin network to validate that I

-   I have the bitcoin that I want to send, and
-   I haven't already sent it to someone else. 

Once that information is confirmed, my transaction gets included in a
"block" which gets will be attached to the already existing previous
block in the chain - hence the term "blockchain

## Transaction request

<img src="attachments/820083932/822633977.png" width="400"/><br/>

This is a sample of blockchain network in the picture, where each node
represents a computer connected to the blockchain network. Each node
stores a file called the ledger, which keeps track of all Bitcoin
transactions. Scanning this ledger file gives us clear knowledge on the
amount of Bitcoins each of us owns.

If **David** wants to send Bitcoins to **Sandra**,

1.  **David** broadcasts a message to the network that describes about
    the transaction : **David** 5 BTC → **Sandra**. David would encrypt
    this transaction with the private key of his wallet, so that this
    could be decrypted by other nodes only through David's public key.
    Thus other nodes ensures that this particular transaction request is
    initiated by David, only if this message can be decrypted using
    David's public key. This verifies source and authenticity of a
    transaction.
2.  Each node in the network will receive the message and apply the
    requested transaction to their copy of the ledger, and re-broadcast
    message to other nodes.
3.  Thus on the blockchain everyone can see everyone’s else
    transactions. In fact it is this feature that enables blockchain
    network to check how much Bitcoins do a person possess when he try
    to make a transaction.  
    In our bank system we only know our own transactions and account
    balances.

In simple words a transaction flow looks like this :

•David <span class="underline">creates</span> a transaction message  
•David <span class="underline">encrypts</span> the transaction with his
own <span class="underline">private</span> <span
class="underline">key</span>  
•David <span class="underline">b</span><span
class="underline">roadcasts</span> the encrypted message to network  
•Network <span class="underline">decrypts</span> the transaction with
<span class="underline">David’s public key</span>.  
•Network <span class="underline">v</span><span
class="underline">erifies</span> <span class="underline">source</span> &
authenticity of transaction  
•Network <span class="underline">verifies balance</span> in David’s
bitcoin account  
•Network <span class="underline">apply</span> the transaction to
ledgers  
•Network <span class="underline">order</span> this transaction into a
<span class="underline">block</span>  
•Network performs <span class="underline">mining</span> - the proof of
work  
•Network <span class="underline">verifies the proof of work</span>  
•Wow! A new block is added to blockchain.

## Transaction encryption

<img src="attachments/820083932/822634505.png" width="400"/><br/>

## Transaction message structure

  

<img src="attachments/820083932/824773187.png" width="400"/><br/>

During a transaction, the sender has to generate a transaction request
that includes links to previous incoming transactions (known as inputs)
as shown in the picture. The total balance of inputs should be \>=
number of Bitcoins being sent out (known as output). **i.e, input \>=
output.** Nodes verify “balance” of sender by checking if each inputs
embedded in that transaction request has been redeemed yet or not.

To know your wallet balance, blockchain need to analyze and verify all
the transactions that ever took place on the whole network connected
to your wallet. This is because ledger in fact does not keep track of
balances, it only keeps track of every transaction that is broadcasted
within the Bitcoin network. 

## Transactions grouped as blocks

<img src="attachments/820083932/824774276.png" width="400"/><br/>

The Bitcoin network orders transactions by putting them together
into groups called block, each block contains a definite amount
of transactions and a link to the previous block. Each block contains
within itself, the hash of the previous Block. This link is crucial
because it’s what gives blockchains immutability. If an attacker
corrupted an earlier Block in the chain then all subsequent blocks will
contain incorrect hashes. Blocks are organized into a time
related chain, that gives the name to the whole system: blockchain.

## How a block is formed

From the pool of unconfirmed transactions, those transactions happened
at same time period are put into a block. Each node can group
transactions together into a block and broadcast it to the network as a
suggestion to include it as next block in the chain. In order to be
added to the blockchain, each block must contain the answer to a complex
mathematical problem. The only way to solve such mathematical problem is
to guess random numbers that combined with the previous block content
generate a defined result (usually a number below a certain value). It
could take about a year for a typical computer to guess the right number
and solve the mathematical problem. However, due to the high number of
computers in the network that are guessing numbers a block is solved on
average every 10 minutes. Nodes get together in groups that divide the
number of guesses each one has to try. These nodes are called miners.
The node that solves such mathematical problem acquires the right to
place the next block on the chain and broadcast it to the whole network.
And if two nodes solve the problem at the same time and spread their
blocks to the network simultaneously, nodes will adopt only the longest
chain.

Here’s an example of what a single Block looks like:

**a block**

``` xml
{  
   'index':1,
   'timestamp':1506057125.900785,
   'transactions':[  
      {  
         'sender':"8527147fe1f5426f9dd545de4b27ee00",
         'recipient':"a77f5cdfa2934df3954a5c7c7da5df1f",
         'amount':5,

      }
   ],
   'proof':324984774000,
   'previous_hash':"2cf24dba5fb0a30e26e83b2ac5b9e29e1b161e5c1fa7425e73043362938b9824"
}
```

## Mining

Bitcoin creators wanted to limit the “growth” of the blockchain by
introducing complex mathematical calculations, implemented through hash
functions (cryptography). Mining is the process performed by nodes to
solve a complex mathematical puzzle (that is part of the bitcoin
program), and to include the answer in the block. The puzzle that needs
solving is to find a number that, when combined with the number mined
previously for last block when passed through a hash function, produces
a result that is within a certain range. This number is called a
"nonce", which is a concatenation of "number used once." In the case of
bitcoin, the nonce is an integer between 0 and 4,294,967,296. The
resulting hash has to start with a pre-established number of zeroes. The
first miner to get a resulting hash within the desired range announces
its victory to the rest of the network. All the other miners immediately
stop work on that block and start trying to figure out the mystery
number for the next one. As a reward for its work, the victorious miner
gets some new bitcoin.

`Hash(previous nonce, nonce) = X, where`

`nonce < 4,294,967,296 && nonce > 0`

`X < certain value, and`

`X is prefixed with certain number of zeroes`

Puzzle

-   Find a number p that when hashed with the previous block’s solution
    a hash with 4 leading 0s is produced.

Simple Proof of Work Algorithm:

-   Find a number p' such that hash(pp') contains leading 4 zeroes,
    where p is the previous p'
-   p is the previous proof, and p' is the new proof

Network verifies the solution to puzzle as follows :

-   Validates the Proof: Does hash(last\_proof, proof) contain 4 leading
    zeroes?

## Implementing the Consensus Algorithm

A conflict occurs when one node has a different chain to another node.
To resolve this conflict, every nodes reach c*onsensus* with other nodes
in a network by following a rule that *the longest valid chain is
authoritative, reject others.* 

## Why is mining needed ?

One of the core concepts of Bitcoin is that it has
a **decentralized** transaction ledger. This means that every (full)
node in the network has a copy of this ledger (as opposed to VISA for
example where only one centralized party has a copy of the transaction
ledger). When new transactions have to be added to the blockchain, this
results in a problem. The nodes in the Bitcoin network need to agree
(or **reach consensus**) about a new state of the blockchain. The
problem boils down to *"Which block of transactions will we all add to
our blockchain next?"*. Now, say all of the full nodes would have your
proposed software routine that says *"I will create a new block of all
the transactions of the past 10 minutes"*. The result will be
that **different nodes will have different blockchains**. Transactions
can't be propagated instantly across the entire Bitcoin network. So a
given transaction could fall within the 10 minute time-span for some
nodes, but arrive late to other, more distant nodes. The nodes are now
in disagreement and it's unsure which blockchain is the true blockchain
of the network. So to prevent this, a consensus algorithm is needed,
which allows all the nodes in the network to agree on the next block to
add, so there is **only one version of the truth**. One node will have
to propose the next block to be added, and the other nodes will need to
be able to easily verify that the block is valid.

PoW is just one example of a consensus algorithm, and it's indeed known
to consume a lot of energy. Other consensus algorithms exist that are
more energy-efficient, e.g. PoS (Proof-of-Stake), PoC
(Proof-of-Capacity), etc. But without one of these algorithms, there is
no way of keeping **one and the same** decentralized blockchain.

  

## Lifecycle of a transaction in Blockchain visualized through different pictures

<img src="attachments/820083932/826214566.png" width="400"/><br/>

1.  Open your wallet and scan the address to which you want to send
    money.
2.  Select the amount of money and send the transaction.
3.  The wallet secures the payment so you know the sender of the money.
4.  The transaction is validated by the network and made part of the
    mining process.
5.  Mining is in progress and is done when a miner earns a bitcoin.
6.  The network validates the result of the mining process.
7.  The receiver of the money gets a confirmation of the successful
    transaction.

------------------------------------------------------------------------

![](attachments/820083932/826214617.png)

1.  There is intention to send money from A to B.
2.  The transaction is put into a block.
3.  The block is send to all members of the network.
4.  The network validates the block.
5.  The block is added to the chain.
6.  The money is moved from A to B.

------------------------------------------------------------------------

<img src="attachments/820083932/826219208.png" width="878"/><br/>

1.  Alice wants to sent 1 bitcoin to Bob.
2.  Alice uses her wallet software to achieve this.
3.  The wallet software (which can also be referred to as a client)
    searches other clients on the [P2P
    network](https://cryptohelp.ch/glossary/p2p-network/) and connects
    to them. This means it can now send and receive information from all
    connected clients.
4.  Alice confirms that she wants to send 1 bitcoin to Bob.
5.  Her client then informs all connected clients of this transaction.
6.  All connected clients inform all of their other connected clients of
    this transaction and so forth. This is called a broadcast.

# Footnotes

## Hash function

Hash functions are often used for proving that something is the same as
something else, without revealing the information beforehand. Here’s an
example.

Let’s say Alice is bragging to Bob that she knows the answer to the
challenge question in their Math class. Bob wants her to prove that she
knows the answer, without her telling him what it is. So, Alice hashes
her answer (let’s say the answer was 42) to produce this hash:

Alice gives this hash to Bob. Bob can not find out what the answer is
from this hash – but when he finds the answer himself, he can hash his
answer and if he gets the same result, then he knows that Alice did
indeed have the answer. Hashes are often used in this context of
verifying information without revealing it to the party that is
verifying.

SHA256 is always 256 bits long, equivalent to 32 bytes, or 64 bytes in
an hexadecimal string format. You can even use char(64) instead of
varchar(64) since the size won't change.

## Wallet

A wallet is a program that allows you to store and exchange your
Bitcoins, and you need it to perform a transaction. A wallet is
cryptographically protected by a pair of keys - a private and a public
key.

If a message is encrypted with public key, only the paired private key
will be able to decrypt and read the message. Similarly, on the other
way, if you encrypt a message with your private key, only the paired
public key can be used to decrypt it. When a user David wants to send
Bitcoins, he needs to broadcast a message encrypted with the private key
of his wallet, so he and only he can spend the Bitcoins he owns. Each
node in the network can cross check that the transaction request is
coming from David by decrypting the transaction request message with the
public key of his wallet.

When encrypting a transaction request with your wallet’s private key you
are generating a digital signature that is used by blockchain computers
to double check the source and the authenticity of the transaction. The
digital signature is a string of text that is the result of
a combination of your transaction request and your private key,
therefore it cannot be used for other transactions. If you change a
single character in the transaction request message the digital
signature will change, so no potential attacker can change your
transaction requests or alter the amount of Bitcoins you are sending.

To know your wallet balance, blockchain need to analyze and verify all
the transactions that ever took place on the whole network connected
to your wallet. This is because ledger in fact does not keep track of
balances, it only keeps track of every transaction that is broadcasted
within the Bitcoin network. 

## How fraud is prevented by blockchain?

<img src="attachments/820083932/825506112.png" width="400"/><br/>

## Oraclization

The blockchain does not know about temperature changes, elections,
sporting events or whether or not a consumer was shipped the correct
goods they ordered. For the blockchain then to factor outside
information, the data must be mapped from the real world to the
blockchain by some mechanism. This process of integrating data outside
the blockchain network is known as oraclization. An oracle provides a
service which integrates outside data onto the blockchain and is
required for much of the most interesting use cases of smart contracts.

# References
- https://www.coindesk.com/information/how-do-bitcoin-transactions-work/
- https://www.coindesk.com/information/how-bitcoin-mining-works/
- https://bitcoin.stackexchange.com/questions/1600/where-are-the-users-bitcoins-actually-stored/1604\#1604?newreg=934ac833da9c4d86b322046a960e4ced
- https://www.ness.com/bitcoin-block-chain-proof-of-work-and-how-they-are-all-connected/
- https://cryptohelp.ch/understanding-blockchain
- https://dev.to/damcosset/blockchain-what-is-in-a-block-48jo
- http://www.ledgerprojects.com/how-a-blockchain-works-the-proof-of-work
- https://www.danielefavi.com/sha256-hash-calculator
