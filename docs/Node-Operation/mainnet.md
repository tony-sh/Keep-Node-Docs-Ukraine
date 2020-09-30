# Mainnet Node Operation
## Stronger and more resilient nodes are better for everyone

**Running either KEEP nodes (Random Beacon or ECDSA) on mainnet requires a high level of diligence and responsibility!**

!>When we run a node on Mainnet we must keep in mind that we put staking and bonding assets at risk, which could be seized/slashed on our and other nodes if we don't have a properly running operation.

 
 
## Regular Devops Best Practices are essential
- Make sure your storage is redundant and replicated. 
- **Backup** your storage offsite. 
- Set everything up so that if you lose your node, you can just spin up another one and bring over the persistent storage and keep going.
- Set up **monitoring** to make sure your node is functioning and connected regularly.
- Check that it has peer connections, check that it is listening on the ports, check that it is connected to ethereum
- Monitor system metrics - cpu, ram, disk, etc.
- Have it notify you for emergencies in a way that will be able to reach you and get your attention at any hour
- Stay up to date on system updates, security vulnerability notices, keep client updates
- Process and monitor your logs, notify for high log level issues


h/t kferret

## Back Up
!>Everyone that's currently a mainnet staker, or planning on being a mainnet staker should implement this and make sure they're backing up their data properly. If you're not doing so, do it right now because there is a high chance that you will lose your ETH bond if not taken care of.

If you're running the ECDSA node, you're not just storing data, you're storing 1/3 of a multi-sig key used to sign BTC transactions. If your system is not up/available/responsive during a request for BTC (redemption of tBTC), you WILL BE AT RISK for liquidation and lose the ETH staked to that bond. The Redemption Proof (SVP proof confirming the BTC transaction) needs to be submitted within 6 hours of redemption request, the liquidation process can be triggered if not submitted in this time frame.

## Keep Backups !
Node Backups Guide

**Suprnrdy's :** [Keep Backups](https://www.notion.so/parleylabs/KEEP-BACKUPS-42a73ee62fb74c8193669c00b739265f)
- tutorial using Backblaze B2 + RClone

<p align="center">
  <img width="450" src="https://user-images.githubusercontent.com/68087535/94620605-47984700-0285-11eb-8439-7e6897b55d7f.png">
</p>


## Monitoring
**Mutedtommy's Guide has 3 parts:** 
- Original Monitoring Guide on [Medium](https://medium.com/@hr12rtk/keep-random-beacon-node-monitoring-grafana-prometheus-and-loki-4a4b669b31ea)
- Prometheus + Loki configurations on [Github](https://github.com/mutedtommy/prom-loki-configs)
- Keep ECDSA Metrics for Prometheus on [Github](https://github.com/mutedtommy/keep-metrics)

- [Automated Script on Github](https://github.com/mutedtommy/monitoring-setup-script), a shell script which automates the installation and configuration for the above guides (with cAdvisor and NodeExporter) and Loki.

**Pantsme´s Guide :**
- Monitoring & Backup for AWS on [Github](https://gist.github.com/afmsavage/7c8a9ccf085bedbc0a2880472a9ef984)

## Community Tools
- All tools mentioned in [Community Tools Section](https://estebank97.github.io/Keep-Node-Docs/#/basics/tools) are awesame.
- They provide invaluable assistance with smooth mainnet nodes operation !


