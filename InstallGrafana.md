# Installation and Configuration of Grafana

### Install the needed packages and then install Grafana  
```
sudo apt install software-properties-common  
wget -q -O - https://packages.grafana.com/gpg.key | sudo apt-key add -  
sudo add-apt-repository "deb https://packages.grafana.com/oss/deb stable main"  
sudo apt update  
sudo apt-cache policy grafana  
sudo apt install grafana  
```

### Installation of Grafana pie chart plugin  
```
sudo grafana-cli plugins install grafana-piechart-panel  
```

### Start the Grafana server  
```
sudo systemctl start grafana-server  
```
  
### Enable the Grafana server at startup  
```
sudo systemctl enable grafana-server  
```
  
### Check Grafana server status
```
sudo systemctl status grafana-server  
```
  
If everything was done correctly, now you should be able to access Grafana endpoint in a browser page, by accessing http://IP:3000, the default port. In order to login, please use the default username *admin* and the default password *admin*. Important! Please make sure to change the password with a much stronger one. Moreover, don't forget to check if your firewall allows you to connect to your Grafana endpoint. 

After you manage to access Grafana endpoint, your first task will be to add Prometheus as a new data source. This can be done in the *Configuration* section. Then you need to define *Prometheus* as name for the data source and the URL needed is "http://localhost:9090" if your are running both Grafana and Prometheus on the same instance. If this is not the case, you will need to enter the *IP* of the machine where your Prometheus is running instead of *

In Grafana first add Prometheus as a new data source under *Configuration*. Define *"Prometheus"* as name for the data source and as URL enter "http://localhost:9090" if you are running all components (Grafana and Prometheus on the same instance). Otherwise, instead of *localhost*, you will have to enter the *IP* of the machine where Prometheus is running.
