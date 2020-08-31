# Risk Mitigation for Node Operators

Operating Keep Nodes imply risks, as there are Collateralization and Availability requirements that must be met to avoid being penalized.
This section covers topics related to understanding and mitigating the risks of operating a Keep Poduction System.

**Content of this Section**
- [Main Risks for Operating Keep Nodes](https://github.com/Estebank97/Keep-Node-Operation/wiki/Risk-Mitigation-for-Node-Operators#main-risks-for-operating-keep-nodes)
- [Undercollateralization Prevention](https://github.com/Estebank97/Keep-Node-Operation/wiki/Risk-Mitigation-for-Node-Operators#undercollateralization-prevention) 
- [High Availability](https://github.com/Estebank97/Keep-Node-Operation/wiki/Risk-Mitigation-for-Node-Operators#main-risks-for-operating-keep-nodes)
    - [General Considerations from the Keep Team](https://github.com/Estebank97/Keep-Node-Operation/wiki/Risk-Mitigation-for-Node-Operators#general-considerations-from-the-keep-team)
    - [Kubernetes Based Deployment](https://github.com/Estebank97/Keep-Node-Operation/wiki/Risk-Mitigation-for-Node-Operators#kubernetes-based-deployment)

## Main Risks for Operating Keep Nodes
From the currrent understanding and Operation of the Keep System in Testnet, we can see two main risks for the Operator to lose a portion or all of the funds staked to support the tBTC Bridge:
* Undercollateralization and Liquidation
* Node Downtime

The current understanding indicates that the Undercollateralization is a more acute problem than the Node Downtime. Uptime for Nodes in Testnet is high and other than upgrades to the software or issue with the VPS provider, it doesn't seem a high risk to the operation. It can also be mitigated with a redundant node installation managed with Kubernets (see below).
However, Undercollateralization seems a bigger problem as it is less controllable and there is no automated way to protect this situation yet other than manual intervention.


## Undercollateralization Prevention
We discuss this situation in detail in this same document, in the [Undercollateralization and Liquidation](https://github.com/Estebank97/Keep-Node-Operation/wiki/Manage-your-Nodes#undercollateralization-and-liquidation) section.
The main reason for this problem is the Volatility in the ETH/BTC price relationship, bringing relative price of ETH to BTC down. Alerts need to be enabled to monitor this relation to then manually add ETH for collateral.

We expect this to be a significant problem and additional automation available from the Keep Dashboard should be enabled, for example, provide reserve collateral that can be used as needed. No plans for this functionality are available as of August 2020.


## High Availability
### General Considerations from the Keep Team
The Keep Team wrote a detailed document that addresses many aspects of running a [Keep ECDSA Node](https://github.com/keep-network/keep-ecdsa/blob/master/docs/run-keep-ecdsa.adoc#run-ecdsa-keep) with high availability

>The Keep Network expects certain capabilites for each node running on the network. To help attain these capabilities consider the following criteria:
>
>* It is paramount that Keep nodes remain available to the Keep Network. We strongly encourage a stable and redundant internet connection.
>
>* A connection to a production grade self-hosted or third party Ethereum node deployment.
>
>* Persistent and redundant storage that will survive a VM or container rotation, and disk failure.
>
>* Each Keep ECDSA client running on the network requires a unique Ethereum operator account.
>
>* Each Keep ECDSA client running on the network requires a unique IP address or a unique application port running under the same IP.



### Kubernetes Based Deployment
To ensure High Availability of a Keep Production System by introducing Node Redundancy, a [Kubernetes](https://kubernetes.io/) based deployment is recommended. 
Refer to the [Kubernetes Deployment Section](https://github.com/Estebank97/Keep-Node-Operation/wiki/Deploy-your-Node#kubernetes-installation-guide-for-ecdsa-nodeode) for installation instructions. 

This detailed document from the Keep Team provides a lot of information about the ECDSA Node  [Run ECDSA Keep](https://github.com/keep-network/keep-ecdsa/blob/master/docs/run-keep-ecdsa.adoc#5-deployment-consideration)

---
`Written & assembled by Keep Community.`
`Contributors: Ramaruro, EstebanK`
