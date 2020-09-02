# Strong Return on Investment (ROI)
There are two main phases for generating strong returns while operating Keep Network Nodes:
* **Network Bootstrapping with Subsidies** 
* **Network in full Production**


## Network Bootstrapping with Subsidies
There is a strong [staking reward subsidy](https://keep-network.gitbook.io/staking-documentation/keep-network-staking/staking-reward-subsidy#keep-holders-stakedrop-subsidy) for early participants that help bootstrap the Network:

|**Total KEEP [Supply](https://etherscan.io/token/0x85eee30c52b0b379b046fb0f85f4f3dc3009afec)**|**1,000,000,000 KEEP**|
| --- | --- |
| **StakeDrop Subsidies for Random Beacon**|**20,000,000 KEEP (2%)**|
| **StakeDrop Subsidies for ECDSA**|**180,000,000 KEEP (18%)**|


The Subsidies will be distributed following the schedule shown below.
<p align="center">
  <img width="600" src="https://user-images.githubusercontent.com/68167410/91521843-45c21900-e8be-11ea-83cc-0d26b0a42fc4.png">
</p>

> The mechanics of rewards distribution are further explained in this [article](https://medium.com/@ben_longstaff/crypto-yield-farmers-take-note-understanding-the-tbtc-and-keep-network-rewards-mechanics-6042e9dc5d97) by Ben Longstaff, and the distribution contract code can be found [here](https://github.com/keep-network/keep-core/pull/1863).

### The estimated Subsidy Rewards ROI are as follows:

**Random Beacon Node**

To participate as a Random Beacon Node Operator, your Minimum Investment is 90,000 KEEP; it is a significant investment and this will reduce the number of participants for this operation. 

We define two scenarios, depending on the number of Nodes that participate. It is difficult to estimate how many nodes will be on Mainnet, but based on the high initial investement, it is likely that the actual number of participants fall somewhere in between 10 and 200 Nodes.
Note that the investment is in KEEP and the rewards are in KEEP.

<p align="center">
  <img width="800" src="https://user-images.githubusercontent.com/68167410/91620068-83718100-e954-11ea-99f9-6e47559886ad.png">
</p>

**ECDSA Node**

To participate as an ECDSA Node Operator, the Minimum Investment should be 150% of the smallest tBTC Minting Unit. Bigger stakes have a higher chance of being selected for Minting. The barrier to entry is much lower as with the Random Beacon Node and there should be a bigger number of Nodes that participate.

Note that the investment is in ETH or in KEEP and the rewards are in KEEP, so the exchange rate between ETH and KEEP plays into the equation.
It is unclear how the subsidies are actually being distributed in terms of the minting/burning activity. Higher stakes are more likely to be selected. The scenarios below assume equal stakes per Node which will not be the case for sure, so this is just a guidance of what rewards could be.

The 100 tBTC Cap will be lifted once the network is up and running for a prudent time and no major issues are seen. After that, to earn rewards, it probably will be important to increase the Stake to have more chances of minting tBTC.

<p align="center">
  <img width="800" src="https://user-images.githubusercontent.com/68167410/91620194-d64b3880-e954-11ea-9c7a-c27717f0d711.png">
</p>

## Network in full Production
Fees generated for Minting/Burning while operating the Nodes will lead to an attractive return once the overall volume of transfers achieves full Production levels (up to Market Demand)

### Random Beacon Node ROI in Full Production

Below are the results for a Random Beacon Node Operator in several scenarios. The results are attractive if there is high demand for the service.

It is still to be defined what the actual Fee for the Service will be. In the [Random Beacon Staking Rewards](https://keep-network.gitbook.io/staking-documentation/keep-network-staking/keep-and-tbtc-staking-rewards#random-beacon-rewards) document it indicates that Fees could be between $10 and $50 per transaction, so we use both scenarios.
<p align="center">
  <img width="800" src="https://user-images.githubusercontent.com/68167410/91620497-c4b66080-e955-11ea-9025-21ca3a32bdf7.png">
</p>

### ECDSA Node ROI in Full Production

Here are the results for an ECDSA Node Operator in several scenarios. It is still to be defined what the actual Fee for the Service will be. In the [ECDSA Node Staking Rewards](https://keep-network.gitbook.io/staking-documentation/keep-network-staking/keep-and-tbtc-staking-rewards#t-ecdsa-tbtc-rewards) document it indicates that Fees start at 5bps (Basis Points), that means 0.05% of the Value Transferred.

The results are less attractive due to the following facts:

* The high collateral requirements (150% of the Value Transferred)
* A tBTC minted can be held for up to 6 months, with no accrual of interest during that time. 

<p align="center">
  <img width="800" src="https://user-images.githubusercontent.com/68167410/91621001-317e2a80-e957-11ea-8200-a6a1e0a553d7.png">
</p>

!> **Note for Keep Team:** We suggest to add a fee (interest) that accrues linearly with time for the investment, in addition to the fees for minting and burning, to improve return for stakers.

---
`Written & assembled by Keep Community.`
`Contributors: Ramaruro, EstebanK`
