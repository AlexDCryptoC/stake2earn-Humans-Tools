# HumansTools
## Monitoring Humans Validator

## Scope of this repo

This solution will allow you to monitor your Validator together with the hardware your Validator runs on. Therefore, it will help you improve your Validator's overall health and moreover, it will help you with valuable insight of what happens in the Humans network and with your machine at any point in time. 
Prometheus will act as a monitoring solution for storing time series such as metrics. 
Grafana is used to allow users to visualize the data stored in Prometheus and other sources such as Telegraf and many more. 
Alertmanager will act as a 24/7 guardian as will get you alerted on Telegram, Discord, by SMS or many other options, depending on what you choose. This can be done by defining certain thresholds, for example you can get alerted if your disk usage rate reaches 70%, or if your validator is stuck (block height is not increasing over a period of time) or even down, etc. 

The combination between all the above tools, it makes this solution a great added value and life saver when it comes to monitor and improve the overall uptime and performance of your validator.   

## Prerequisites needed
* Enable export of tendermint metrics --> please check EnableTendermintMetrics in this repo:
* https://github.com/AlexDCryptoC/stake2earn-Humans-Tools/blob/main/EnableTendermintMetrics.md
* Prometheus  --> please check InstallPrometheus in this repo: 
* https://github.com/AlexDCryptoC/stake2earn-Humans-Tools/blob/main/InstallPrometheus.md
* Node Exporter  --> please check guide InstallNodeExporter in this repo:
* https://github.com/AlexDCryptoC/stake2earn-Humans-Tools/blob/main/InstallNodeExporter.md
* Grafana  --> please check guide InstallGrafana in this repo:
* https://github.com/AlexDCryptoC/stake2earn-Humans-Tools/blob/main/InstallGrafana.md
* Humans Dashboard  --> please check this repo: 
* https://github.com/AlexDCryptoC/stake2earn-Humans-Tools/blob/main/HumansValidator.json

## Import your Humans Validator Dashboard into Grafana  
For this you will have to download the HumansValidator.json from this repo and then in Grafana go to *Dashboards* -> *Manage* -> *Import* -> *Upload JSON file* and select the HumansValidator.json to be uploaded.  
The next step will be to make sure that the right Prometheus connection has been selected and if necessary adapt the Dashboard.

## The Final Result
![stake2earn-humans-dashboard](https://github.com/AlexDCryptoC/stake2earn-Humans-Tools/assets/18679675/fc49b43a-9e3f-48ba-8e29-f16b4cf0d3cf)
