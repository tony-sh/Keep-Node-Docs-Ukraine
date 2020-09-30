# Manage your Nodes

This Section covers Node Management Considerations: once the nodes are set up and running you have to monitor while in operation and upgrade them whenever new contracts or new versions of the clients are deployed by the Keep Team.

## Best Practices


### Separate INFURA Accounts

Create one INFURA Project for each Node, so as to see distinct activity per project.
This is a quick and easy way to check that the Nodes are active, but should not be the main way of checking.

<p align="center">
  <img width="800" src="https://user-images.githubusercontent.com/68167410/88484551-07d77b00-cf35-11ea-974e-5dddd0162bab.png">
</p>


### Use different Virtual Private Server (VPS) per Node

Although this increases the cost of operation, if there are issues with operations or upgrades, you can distribute the risk better.

<p align="center">
  <img width="800" src="https://user-images.githubusercontent.com/68167410/88492899-be5a5080-cf73-11ea-972d-715dca658e0c.png">
</p>

## Node Health Verification

!>**@Herobrine** made this really awesome app you can run to verify Node Health: [KeepNode.app](https://keepnode.app/)

### ECDSA Node Maintenance

The main verification you have to do is that the ECDSA node is connected to Peers:

Type: `sudo docker logs ecdsa --since 5m | grep "connected"`

<p align="center">
  <img width="800" src="https://user-images.githubusercontent.com/68167410/88097681-2668fb00-cb5e-11ea-94d4-c080e20d5a15.png">
</p>

You can also check for Keep Creation, i.e. is your Node participating in the Signing of new Keeps.

Type: `sudo docker logs ecdsa 2>&1 | grep "new keep"`

<p align="center">
  <img width="800" src="https://user-images.githubusercontent.com/68167410/88484709-30ac4000-cf36-11ea-8baf-3a54b48523b2.png">
</p>

General Log Checking, searching for "connected" peers

Type: `sudo docker logs ecdsa --since 5m | grep "connected"`

<p align="center">
  <img width="800" src="https://user-images.githubusercontent.com/68167410/88487822-226a1e00-cf4e-11ea-8351-60cf0a68d968.png">
</p>


!> If running nodes on mainnet be sure to follow steps in [Mainnet Node Operation Section](https://estebank97.github.io/Keep-Node-Docs/#/Node-Operation/mainnet) and use [Community Tools](https://estebank97.github.io/Keep-Node-Docs/#/basics/tools) for node assistance. 


## Undercollateralization and Liquidation

There is a serious risk that due to relative price fluctuations of the ETH / BTC pair, your collateral (actually, the collateral of the Keep(s) that you have signed) is not sufficient and you run the risk of Liquidation.
The process is detailed in the [tBTC System Design Document](https://docs.keep.network/tbtc/index.pdf), pages 19-20

This article from Bison Trail, [Keep Active Management](https://bisontrails.co/keep-active-participation/), explains this Liquidation Process and lists several measures that can be taken to avoid this issue.

Currently, the monitoring has to be manual, i.e. verification of ETH/BTC relative price fluctuations and additions of ETH colateral. 

[Latenthero](https://discord.com/channels/590951101600235531/590951101600235533/737707953221664779) created a [Telegram Bot](https://t.me/keep_alert_bot) for alerting when the ETH available for bonding is below a user set threshold. The code for the bot can be seen and eventually repurposed [here](https://github.com/latenthero/keep-alert-bot). It is available for Testnet as of August 2020.

This document from Experience#2376 provides more details with references to the software code involved: [tBTC risk - liquidation and slashing details](https://hackmd.io/OzIeyWcfTVO69zIF67XCkg). This graph from the document explains the risks well.
<p align="center">
  <img width="800" src="https://user-images.githubusercontent.com/68167410/88967178-0975ab80-d273-11ea-9696-15f2ce8995c5.png">
</p>

h/t ssh


## Node Updates

From time to time the Keep Development Team will issue new Docker Images for both Nodes and update the relevant Ethereum Contracts.

### General Guidelines for Updates

From time to time, the Contracts in Ethereum that are used for the Keeps Management may be updated. The key Contracts that might be updated are listed in this document [Run ECDSA Keep](https://github.com/keep-network/keep-ecdsa/blob/master/docs/run-keep-ecdsa.adoc#83-authorizations) document.
In this case you have to do the following:
* Stop the Node --> `sudo docker stop ecdsa`
* Edit the configuration file that lists the contracts "config.toml" --> `nano $HOME/keep-ecdsa/config/config.toml`
* Update the Contracts and Lists of Peers as indicated by the Keep Team
  - For example,this update to contracts and List of Peers was made in June 2020 (in green)

<p align="center">
  <img width="900" src="https://user-images.githubusercontent.com/68167410/88488480-0026cf00-cf53-11ea-9ef6-cf65551f5cb1.png">
</p>

As an alternative of editing, this guide from **Papyasha** [Update Nodes](https://gist.github.com/papyasha/7d97cb53aa1153cc65b0535c2b9f23e3) shows a clean way of updating the Config files by removing and redeploying them. It also includes the link to the original deployment of the nodes with all the necessary details.

---
### September 2nd, 2020 Update (+ September 8th new docker images)
The key activities to update both nodes are the following:
* Get a New Grant for the KEEP Tokens from the Testnet Faucet:
  - https://us-central1-keep-test-f3e0.cloudfunctions.net/keep-faucet-ropsten?account= **`"Your Operator Ethereum Address"`**
* Stake your grant in the [KEEP Dapp](https://dashboard.test.keep.network/tokens/overview) (this address for Testnet)
* Authorize your Contracts in the KEEP Dapp
  - Authorize for [Random Beacon](https://dashboard.test.keep.network/applications/random-beacon)
  - Authorize for [ECDSA](https://dashboard.test.keep.network/applications/tbtc) and add ETH for Bonding
* Stop Docker Containers :
  - Make sure you use correct containers names, check them with `sudo docker ps` command.
  - For Random Beacon: `sudo docker stop keep-client`
  - For ECDSA: `sudo docker stop ecdsa` 
* Remove Current Containers :
  - For Random Beacon: `sudo docker rm keep-client`
  - For ECDSA: `sudo docker rm ecdsa`
* Pull New Docker Images :
  - For Random Beacon: `sudo docker pull keepnetwork/keep-client:v1.3.0-rc.4`
  - For ECDSA: `sudo docker pull keepnetwork/keep-ecdsa-client:v1.2.0-rc.5`
* Update Config.toml file with new contracts :
  - If running both nodes on the same VPS remember each config file is in its own folder. In this example named keep-client and keep-ecdsa.
  - Make sure you check the correct folders names with `ls` command.
  - For Random Beacon:`nano $HOME/keep-client/config/config.toml`
     - KeepRandomBeaconOperator = `"0xC8337a94a50d16191513dEF4D1e61A6886BF410f"`
     - TokenStaking = `"0x234d2182B29c6a64ce3ab6940037b5C8FdAB608e"`
     - KeepRandomBeaconService = `"0x6c04499B595efdc28CdbEd3f9ed2E83d7dCCC717"`
  - For ECDSA:`nano $HOME/keep-ecdsa/config/config.toml`
     - BondedECDSAKeepFactory = `“0x9EcCf03dFBDa6A5E50d7aBA14e0c60c2F6c575E6”`
     - Sanctioned Applications = `“0xc3f96306eDabACEa249D2D22Ec65697f38c6Da69”`
* Start Docker Containers :
  Write this as only one command and keep in mind that it may change according to the guide you used initially (e.g. the ports may not be 3919:3919).
  
  Make sure you reference the new docker images and run each in their own folder if on the same VPS !
  
  
  - For Random Beacon:
  
  
        sudo docker run -dit
        --restart always
        --volume $HOME/keep-client:/mnt      
        --env KEEP_ETHEREUM_PASSWORD=$KEEP_CLIENT_ETHEREUM_PASSWORD     
        --env LOG_LEVEL=debug     
        --log-opt max-size=100m     
        --log-opt max-file=3     
        --name keep-client     
        -p 3919:3919 
        keepnetwork/keep-client:v1.3.0-rc.4 --config /mnt/config/config.toml start
      
      
  - For ECDSA: 
  
  
        sudo docker run -d     
        --restart always     
        --entrypoint /usr/local/bin/keep-ecdsa     
        --volume $HOME/keep-ecdsa:/mnt/keep-ecdsa     
        --env KEEP_ETHEREUM_PASSWORD=$KEEP_CLIENT_ETHEREUM_PASSWORD     
        --env LOG_LEVEL=debug     
        --log-opt max-size=100m     
        --log-opt max-file=3     
        --name ecdsa 
        -p 3919:3919 
        keepnetwork/keep-ecdsa-client:v1.2.0-rc.5 --config /mnt/keep-ecdsa/config/config.toml start

* Check Logs for connection to Peers :
  - For Random Beacon: `sudo docker logs keep-client 2>&1 --since 5m | grep "number of connected peers"`
  - For ECDSA: `sudo docker logs ecdsa 2>&1 --since 5m | grep "number of connected peers"`
  - If it shows some errors first make sure that contracts are authorized in the dashboard. Sometimes you just have to do it again.

* Finally, don't forget to add some test ETH to the tBTC bonding on the Dashboard !


---
### August 7, 2020 Update
The key activities to update both nodes are the following:
* Get a New Grant for the KEEP Tokens from the Testnet Faucet:
  - https://us-central1-keep-test-f3e0.cloudfunctions.net/keep-faucet-ropsten?account= **`"Your Operator Ethereum Address"`**
* Stake your grant in the [KEEP Dapp](https://dashboard.test.keep.network/tokens/overview) (this address for Testnet)
* Authorize your Contracts in the KEEP Dapp
  - Authorize for [Random Beacon](https://dashboard.test.keep.network/applications/random-beacon)
  - Authorize for [ECDSA](https://dashboard.test.keep.network/applications/tbtc) and add ETH for Bonding
* Stop Docker Containers :
  - Make sure you use correct containers names, check them with `sudo docker ps` command.
  - For Random Beacon: `sudo docker stop keep-client`
  - For ECDSA: `sudo docker stop ecdsa` 
* Remove Current Containers :
  - For Random Beacon: `sudo docker rm keep-client`
  - For ECDSA: `sudo docker rm ecdsa`
* Pull New Docker Images :
  - For Random Beacon: `sudo docker pull keepnetwork/keep-client:v1.3.0-rc`
  - For ECDSA: `sudo docker pull keepnetwork/keep-ecdsa-client:v1.2.0-rc`
* Update Config.toml file with new contracts :
  - If running both nodes on the same VPS remember each config file is in its own folder. In this example named keep-client and keep-ecdsa.
  - Make sure you check the correct folders names with `ls` command.
  - For Random Beacon:`nano $HOME/keep-client/config/config.toml`
     - KeepRandomBeaconOperator = `"0xf417b31104631280adF9F6828ee19985BC299fdC"`
     - TokenStaking = `"0x8117632eC1D514550b3880Bc68F9AC1A76c9C67B"`
     - KeepRandomBeaconService = `"0xd83248e311DC2Ba0d2A051e86f0678d8857f6ADD`"
  - For ECDSA:`nano $HOME/keep-ecdsa/config/config.toml`
     - BondedECDSAKeepFactory = `“0xb37c8696cD023c11357B37b5b12A9884c9C83784”`
     - Sanctioned Applications = `“0x9F3B3bCED0AFfe862D436CB8FF462a454040Af80”`
* Start Docker Containers :
  - This command may change according to the guide you used initially (e.g. the ports may not be 3919:3919). Make sure you reference the new docker images and run each in their own folder if on the same VPS !
  - For Random Beacon: `sudo docker run -dit --restart always --volume $HOME/keep-client:/mnt --env KEEP_ETHEREUM_PASSWORD=$KEEP_CLIENT_ETHEREUM_PASSWORD --env LOG_LEVEL=debug --log-opt max-size=100m --log-opt max-file=3 --name keep-client -p 3919:3919 keepnetwork/keep-client:v1.3.0-rc --config  /mnt/config/config.toml start`
  - For ECDSA: `sudo docker run -d    --restart always    --entrypoint /usr/local/bin/keep-ecdsa    --volume $HOME/keep-ecdsa:/mnt/keep-ecdsa    --env KEEP_ETHEREUM_PASSWORD=$KEEP_CLIENT_ETHEREUM_PASSWORD    --env LOG_LEVEL=debug    --log-opt max-size=100m    --log-opt max-file=3     --name ecdsa -p 3919:3919 keepnetwork/keep-ecdsa-client:v1.2.0-rc    --config /mnt/keep-ecdsa/config/config.toml start`

* Check Logs for connection to Peers :
  - For Random Beacon: `sudo docker logs keep-client 2>&1 --since 5m | grep "number of connected peers"`
  - For ECDSA: `sudo docker logs ecdsa 2>&1 --since 5m | grep "number of connected peers"`
  - If it shows some errors first make sure that contracts are authorized in the dashboard. Sometimes you just have to do it again.

* Finally, don't forget to add some test ETH to the tBTC bonding on the Dashboard !

---
`Written & assembled by Keep Community.`
`Contributors: Ramaruro, EstebanK`
