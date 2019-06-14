Now that we have Prometheus up and an exporter running for it to gather metrics from its time to talk about how we query 
the metrics its gathering. The way that the Prometheus query language is designed is for metrics to follow the naming
convention that was outlined in the documentation. This allows for the queries to be interrupted very easily by anyone.

Some examples would be:

* Find specific metric with a label
`node_network_receive_packets_total{job="prometheus",group="prom"}`{{copy}}

* Find the sum of the value of all metrics matching the above query

`sum(node_network_receive_packets_total{job="prometheus",group="prom"})`{{copy}}

* Count the number of metrics returned by this query

`count(node_network_receive_packets_total{job="prometheus",group="prom"})`{{copy}}

## Task

Check out the `graph` Prometheus Server page [prom-server](https://[[HOST_SUBDOMAIN]]-9090-[[KATACODA_HOST]].environments.katacoda.com/graph)
and run some of the queries above. 
