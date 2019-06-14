The Prometheus configuratin file simply a `yaml` file which is broken up into a few different sections.

* The first section is called `global`, it contains settings for Prometheus which are in the global scope:

```yaml
# my global config
global:
  scrape_interval:     15s # Set the scrape interval to every 15 seconds. Default is every 1 minute.
  evaluation_interval: 15s # Evaluate rules every 15 seconds. The default is every 1 minute.
  # scrape_timeout is set to the global default (10s).
```

* The next section is called `alerting`, it contains settings for Prometheus alertmanagers which are called in the 
scenario where the `rules_files`(the next section) is evaluated and an alert is triggered:

```yaml
# Alertmanager configuration
alerting:
  alertmanagers:
  - static_configs:
    - targets:
      # - alertmanager:9093
``` 

* The next is the `rules` section which we talked about above, the interval upon which rules are evaluated is determined
at the `global` level and is controlled by the `evaulation_interval` configuration setting.

```yaml
# Load rules once and periodically evaluate them according to the global 'evaluation_interval'.
rule_files:
  # - "first_rules.yml"
  # - "second_rules.yml"
```

* The final basic section is the `scrape_configs` section. This is where we tell the Prometheus binary what endpoints we
want it to scrape or _export_ information out of.

```yaml
scrape_configs:
  # The job name is added as a label `job=<job_name>` to any timeseries scraped from this config.
  - job_name: 'prometheus'

    # metrics_path defaults to '/metrics'
    # scheme defaults to 'http'.

    static_configs:
    - targets: ['localhost:9090']
```

Putting it all together, we have a configuration file that looks something like this:

```yaml
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
    - targets: ['localhost:9090']
      labels:
        group: "prom"
```
