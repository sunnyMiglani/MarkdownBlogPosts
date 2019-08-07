# Blockchain, Bitcoin and everything around it

Focus questions
1) What is a cryptocurrency?
2) What is blockchain?
3) What is bitcoin?
4) Why does it have any value?
5) Is it legal?

### What is a cryptocurrency?
Cryptocurrency is a virtual or digital currency that uses the field of cryptography to ensure its security. 

Cryptocurrencies are useful due to the emphasis on security, and often use the technology of blockchain to implement the different forms of security. 

The difference from cryptocurrencies and any other form of currency is the fact that cryptocurrencies are decentralized. This means that there is no central governing authority that owns "all" the currency and wallets/exchanges/transactions do not use the banking systems that normal currencies use. 

### Cryptocurrency without Blockchain:


#### IOTA - [Ref](https://www.technologyreview.com/s/609771/a-cryptocurrency-without-a-blockchain-has-been-built-to-outperform-bitcoin/)
- Called IOTA [Link](https://www.iota.org/)
- Focuses completely on using the concept of `tangles` in `directed acyclic graphs`.
- Based on cryptography, so security can be assumed/held (once verified)
- Founder is Sonstebo, who's issue was with the fact that blockchain takes too long to verify transactions.
- Solution / IOTA's main idea: The IOTA "tangle" says that to place a transaction on the blockchain, the issuer must confirm two randomly selected previous transactions, which each themselves will have 2 transactions that would be solved before being valid. 
- This allows for a web of confirmation
- IOTA hasn't been built yet, but is currently being backed by important companies.

IOTA has a goal of transforming the sharing of data: They're looking at the issues that are arising with the constant increase in the data being generated and the limits caused by both physical and computational properties at the moment. The argument IOTA presents is that a centralised agency that handles the millions of IoT devices' data would be illogical and impossible, and it makes sense to decentralise this data onto the devices themselves. 

They talk about a 'sharing economy' that promotes the use of all devices available such that the data can be shared amongst agents who require it and the users only pay for the products/devices they actually use _when they use them_ rather than pay / purchase the device all the time.  (How their solution affects these problems is unclear).

## What is blockchain?

 Blockchain is just a list of records that are connected to each other through the process of hashing. It's called a "block chain" because each record is a "block" and is connected to the rest of the "blocks" with a chain of hashes. The blocks contain the record along with a hash of the blocks that built up to it until this point. The next block will use this hash, along with the record in that block and hash the whole thing together to create the new block.

This means it's easy to verify the blockchain by taking the start of the chain and following and verifying the hashes at each block. It also means that it is quite hard to alter the information in the blocks. If someone would like to alter the information in block 1, the hash itself will change, therefore requiring the following blocks to be rehashed  











