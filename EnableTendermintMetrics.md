# How to enable Tendermint metrics

In order to enable the Tendermint metrics export, please go to *~/.humansd/config/config.toml* file and in the *[instrumentation]* section
you need to set the flag for Prometheus to *true* 

[instrumentation]  
prometheus = true  
prometheus_listen_addr = ":26660"
