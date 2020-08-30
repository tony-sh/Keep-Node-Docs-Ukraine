# Keep Network 101

The Keep Network is a privacy solution where "keeps" hold distributed small amounts of data, such as a private key. The Random Beacon and t-ECDSA Keeps are the core technology of the network.

## What is a Keep?
A keep is up to 1MB of encrypted storage that is distributed across one or more keep providers, or members. A keep provider is one economic entity in the Keep Network; they have a stake and must participate in a signing group as a single member. 

The Keep Network's native token is KEEP. It powers the network and undergirds all the apps that are and will be built on it.

The Keep Network requires a trusted source of randomness for the process of trustless group election. Member selection for a keep is chosen at random. This trusted source of randomness takes the form of a BLS Threshold Relay, otherwise known as the Random Beacon.

## What is the Random Beacon?
At the core of Keep’s solution is the ability to keep small amounts of data (such as a private key) actually private. This is why true randomness is so important. All parties would have to collude to know what a user is working on, and collusion becomes almost impossible when member selection is truly random.

The Random Beacon is a way of generating verifiable randomness that is resistant to bad actors both in the relay network and on the anchoring blockchain, assumed here to be Ethereum. It is used to determine member selection for signing groups.

> Read more about the Random Beacon in the technical documentation.

No one knows who the signers will be – including the signers themselves – until the moment they are selected by the Random Beacon. This ensures that signers are not able to collude to steal funds or attack the network, and it’s why the true randomness supplied by the beacon is so important.

A key way tBTC, the first application built on the Keep Network, ensures trustlessness is by addressing counterparty risk. It uses a system of signers’ groups that allows tBTC to process transactions without a trusted middleman. Signer selection is therefore essential to tBTC’s proper functioning and the creation of t-ECDSA Keeps.

## What are t-ECDSA Keeps?
t-ECDSA keeps are the underlying technology of tBTC, the first application built on the Keep Network.

> Read more about tBTC in the technical documentation.

Implemented with secure multi-party computation (sMPC), t-ECDSA keeps make it possible for contracts to communicate cross-chain by signing transactions between chains with a number of geographically distributed threshold signers. T-ECDSA keeps secure the transactions with multiple individual key shares, held independently by multiple signers. 

Decentralized signing is performed with sMPC for computation on private key shares without revealing them. Responsibility for signatures is divided, requiring a threshold number of participants to create a signature using their key shares.

### Curious about plans to build other cross-chain tokens? 
There are no firm plans yet to build a bridge on other chains. However the Cross-Chain Group has had early conversations with chains like Cosmos, Zcash, and Polkadot on trustless bridge designs.

## KEEP: Keep Network Token
A balance of KEEP tokens is required in order for someone to become a member of the Keep Network. Members are eligible to earn rewards by performing work on the platform. This is the key incentive that drives constructive behavior, facilitates efficiency and trust, and promotes the adoption and growth of the Keep network.

KEEP is a work token — holding it confers the right to perform key functions on the network. Token holders must delegate a minimum amount of KEEP as collateral in order to be eligible. 

Work opportunities are awarded randomly, but over time, and the amount of work a delegator is chosen for will be proportional to the amount of KEEP delegated. For example, a person delegating 1,000 KEEP could expect, over time, to be selected for work ten times as often as someone who delegates 100 KEEP, earning fees in proportion to the work they successfully perform.

## Rewards and Slashing
The benefit KEEP tokens confer to holders is relative to the amount of stake delegated and therefore to the user’s commitment to the network. The idea is that those with more “skin in the game” reap greater rewards. 

Slashing in the Keep and tBTC systems is not designed to be punitive, and is rather to protect the security of the network from malicious behaviors. 

Continue to the next section to learn more about the specifics of rewards and slashing.

`Sourced from Keep Team's official documentation.`[Source](https://keep-network.gitbook.io/staking-documentation/)
