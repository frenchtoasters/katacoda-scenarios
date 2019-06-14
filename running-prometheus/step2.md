# Download Prometheus

To download Prometheus you need to run the following command:

`wget https://github.com/prometheus/prometheus/releases/download/v2.9.2/prometheus-2.9.2.linux-amd64.tar.gz` {{excecute}}
 
Once you have downloaded it you need to extract it by running the following: 
 
 `tar -zxvf prometheus-2.9.2.linux-amd64.tar.gz` {{execute}}


Next we want to go ahead and create the configuration file that we desribed in the previous step like so:


<pre class="file" data-filename="promconfig.yml" data-target="replace"> 
# my global config
global:
  scrape_interval:     15s # Set the scrape interval to every 15 seconds. Default is every 1 minute.
  evaluation_interval: 15s # Evaluate rules every 15 seconds. The default is every 1 minute.
  # scrape_timeout is set to the global default (10s).

scrape_configs:
  # The job name is added as a label `job=<job_name>` to any timeseries scraped from this config.
  - job_name: 'prometheus'

    # metrics_path defaults to '/metrics'
    # scheme defaults to 'http'.

    static_configs:
    - targets: ['localhost:9090','localhost:9100']
      labels:
        group: "prom"
</pre>

## TODO

Copy the above config into the editor