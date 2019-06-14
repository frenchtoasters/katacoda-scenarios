A Prometheus Exporter is what the server scrapes to gather its information. The way this works is the Prom-Server makes 
a webrequest to the Exporter on the port that is defined for that `job`. That webrequest returns Prometheus metrics 
which are formatted in a standardized fashion as defined [here](https://prometheus.io/docs/practices/naming/). So under 
the hood the Prom-Server is just parsing that webrequest response into metrics objects. 

Have these metrics in objects allows them to be treated as traditional data types in object oriented programming. This 
is what makes Prometheus so flexible and extensible. 

So how do we run an exporter? The same way that we run the Prometheus Server, via a container as follows:

```
docker run -d \
  -v "/proc:/host/proc" \
  -v "/sys:/host/sys" \
  -v "/:/rootfs" \
  --net=host \
  --name node-exporter \
  quay.io/prometheus/node-exporter:latest 
```{{execute}}

## Task

* Launch the above container

* Verify it is up and working 

`docker ps`{{execute}}

* To view what the exporter is returning to the Prom-server:

`curl localhost:9100/metrics`{{execute}}

