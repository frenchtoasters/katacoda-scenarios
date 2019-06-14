Prometheus can be run in several different ways one of the most popular ways is via a container as follows:

```bash
docker run -d --net=host \
    -v /root/promconfig.yml:/etc/prometheus/prometheus.yml \
    --name prom-server \
    prom/prometheus
```{{execute}}

Once started the [prom-server](https://[[HOST_SUBDOMAIN]]-9090-[[KATACODA_HOST]].environments.katacoda.com) is viewable 
on port [9090](https://[[HOST_SUBDOMAIN]]-9090-[[KATACODA_HOST]].environments.katacoda.com) 

## Task
Launch the above container 