# Install and Config Prometheus 

### Verify Prometheus available versions
```
sudo apt-cache policy prometheus  
```

### Create your Prometheus user  
```
sudo useradd -M -r -s /bin/false prometheus  
```

### Create your Prometheus directories  
```
sudo mkdir /etc/prometheus /var/lib/prometheus  
```

### Dowload Prometheus binaries  
```
wget https://github.com/prometheus/prometheus/releases/download/v2.18.1/prometheus-2.18.1.linux-amd64.tar.gz  
```

### Extract and Install the binary  
```
tar xzf prometheus-2.43.0.linux-amd64.tar.gz  
sudo cp prometheus-2.43.0.linux-amd64/{prometheus,promtool} /usr/local/bin/  
sudo chown prometheus:prometheus /usr/local/bin/{prometheus,promtool}  
sudo cp -r prometheus-2.43.0.linux-amd64/{consoles,console_libraries} /etc/prometheus/  
```


### Setup the configuration for Prometheus
```
sudo cp prometheus-2.43.0.linux-amd64/prometheus.yml /etc/prometheus/prometheus.yml  
sudo nano /etc/prometheus/prometheus.yml  
```

### Configuration section for Prometheus scraping  
```
global:
  scrape_interval: 10s
  evaluation_interval: 15s
scrape_configs:
  - job_name: 'prometheus'
    scrape_interval: 5s
    static_configs:
      - targets: ['localhost:9090']
  - job_name: humans
    static_configs:
      - targets: ["localhost:26660"]
  - job_name: node
    static_configs:
      - targets: ["localhost:9100"]
```
        
### Set the server group and user ownership on the configuration file
```
sudo chown -R prometheus:prometheus /etc/prometheus  
sudo chown prometheus:prometheus /var/lib/prometheus  
```
  
### Create a Prometheus systemd file  - in this case, Prometheus is using 9090 as listen port
```
sudo nano /etc/systemd/system/prometheus.service  
```
Now copy the section below:  
```
[Unit]  
Description=Prometheus Time Series Collection and Processing Server  
Wants=network-online.target  
After=network-online.target  
  
[Service]  
User=prometheus  
Group=prometheus  
Type=simple  
ExecStart=/usr/local/bin/prometheus \  
    --config.file /etc/prometheus/prometheus.yml \  
    --storage.tsdb.path /var/lib/prometheus/ \  
    --web.console.templates=/etc/prometheus/consoles \  
    --web.console.libraries=/etc/prometheus/console_libraries\  
    --web.listen-address="0.0.0.0:9090"  
  
[Install]  
WantedBy=multi-user.target  
```
  
### At startup enable Prometheus  
```
sudo systemctl enable prometheus  
```
### Start service for Prometheus  
```
sudo systemctl start prometheus  
```
### Check Prometheus service status
```
sudo systemctl status prometheus  
```