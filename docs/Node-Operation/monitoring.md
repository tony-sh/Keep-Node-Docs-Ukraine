# Monitoring and Remote Alerting

This section covers the following topics related to the Nodes Automated Monitoring, Remote Alerting and Early Warning Methods.

**Content of this Section**
- [Guides for Setting up Node Monitoring of Keep Nodes](https://github.com/Estebank97/Keep-Node-Operation/wiki/Monitoring-and-Remote-Alerting#guides-for-setting-up-node-monitoring-of-keep-nodes)
- [Discord and Telegram Bots](https://github.com/Estebank97/Keep-Node-Operation/wiki/Monitoring-and-Remote-Alerting#discord-and-telegram-bots-to-get-keep-network-stats)

## Guides for Setting up Node Monitoring of Keep Nodes
### Random Beacon Monitoring using Grafana, Prometheus, Prometheus Node Exporter, Google cAdvisor and Loki
- MutedTommy's [Keep Random Beacon | Node Monitoring | Part 1](https://medium.com/@hr12rtk/keep-random-beacon-node-monitoring-grafana-prometheus-and-loki-4a4b669b31ea) and [Part 2](https://medium.com/@hr12rtk/keep-random-beacon-node-monitoring-part-2-5cd037464a6e).
This article summarises the steps used to set up the monitoring on Keep Random Beacon node using Grafana, Prometheus, Prometheus Node Exporter, Google cAdvisor and Loki.

<p align="center">
  <img width="800" src="https://user-images.githubusercontent.com/68167410/89043879-c537e900-d30e-11ea-84ad-dfbd47592d2f.png">
</p>


### Random Beacon and ECDSA Nodes Monitoring using Elasticsearch, Logstash, and Kibana
- Guide to [Setting up an Elastic Stack Dashboard](https://www.notion.so/Setting-up-Elastic-Stack-Dashboard-14f9edc94418468bb95af40417a0332a) for Keep Random Beacon and ECDSA Nodes using Elasticsearch, Logstash, and Kibana

>The Elastic Stack — formerly known as the ELK Stack — is a collection of open-source software produced by Elastic which allows you to search, analyze, and visualize logs generated from any source in any format, a practice known as centralized logging. Centralized logging can be very useful when attempting to identify problems with your servers or applications, as it allows you to search through all of your logs in a single place. It’s also useful because it allows you to identify issues that span multiple servers by correlating their logs during a specific time frame.
>
>The [Elastic Stack](https://www.digitalocean.com/community/tutorials/how-to-install-elasticsearch-logstash-and-kibana-elastic-stack-on-ubuntu-18-04#step-4-%E2%80%94-installing-and-configuring-filebeat) has four main components:
>
> Elasticsearch: a distributed RESTful search engine which stores all of the collected data.
>
> Logstash: the data processing component of the Elastic Stack which sends incoming data to Elasticsearch.
>
> Kibana: a web interface for searching and visualizing logs.
>
> Beats: lightweight, single-purpose data shippers that can send data from hundreds or thousands of machines to either Logstash or Elasticsearch.
>
<p align="center">
  <img width="800" src="https://user-images.githubusercontent.com/68167410/89001980-816ac280-d2c1-11ea-98f2-94e0481188fc.png">
</p>


## Discord and Telegram Bots to get Keep Network Stats
There are several Bots that are being developed to be used in the [Keep Discord Channel](https://discord.com/channels/590951101600235531/709789601459339326). This is work in progress as of end of July 2020, there should be updates in the coming months.

[KEEP BOT](https://discord.com/channels/590951101600235531/709789601459339326/735597811613302855) by StateLayer 

List of bot commands 
Keep Network Bot (StateLayer)
- !keep all : Show all network stats
- !keep price: $KEEP price
- !keep volume: KEEP 24h volume 
- !keep stakers : number of stakers on the network 
- !keep holders: Amount of holders of KEEP 
- !keep staked: Amount of KEEP staked in the random beacon contract 
- !keep stakedropreserve: Amount of KEEP in the stakedrop reserve 
- !keep liquidityreserve: Amount of KEEP in the liquidity reserve 
- !keep beacontransactions: Total number of random beacon transactions
- !keep exchanges : show keep balances in exchanges
- !keep wen ICO? : (Hint, never)

Node Watcher (StateLayer)
 (possible to DM bot!)
- !watcher summary youraddress : various stats about your signing group
- !watcher ethbonded youraddress : Get the balance of ethbonded by your group
- !watcher collateralratio youraddress : collateral ratio of your group
- !watcher help : display available commands
At "youraddress", put the ethereum adress of your signing group.

tBTC Stats (pantsme)
Available commands: !supply, !txs, !holders, !tdt, !volume, !help

---
`Written & assembled by Keep Community.`
`Contributors: Ramaruro, EstebanK`
