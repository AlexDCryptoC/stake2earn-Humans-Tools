# Installation and Configuration of a Node Exporter  
 
``` 
wget https://github.com/prometheus/node_exporter/releases/download/v1.0.1/node_exporter-1.0.1.linux-amd64.tar.gz  
tar xvfz node_exporter-1.0.1.linux-amd64.tar.gz  
cd node_exporter-1.0.1.linux-amd64  
```

### Create Node Exporter systemd file  
``` 
sudo nano /etc/systemd/system/node_exporter.service  
```

### This file can be used as such or adapted to your user and group, even customized based on this file and your installation.
```   
[Unit]  
Description=Node Exporter  
After=network.target  
  
[Service]  
User=<your-user>  
Group=<your-user>  
Type=simple  
ExecStart=/home/<your-user>/node_exporter-1.0.1.linux-amd64/node_exporter  
  
[Install]  
WantedBy=multi-user.target  
```

### Start your Node Exporter  
``` 
sudo systemctl start node_exporter  
```
### Enable your Node Exporter at startup  
``` 
sudo systemctl enable node_exporter   
```
### Check Node Exporter status 
```
sudo systemctl status node_exporter  
```