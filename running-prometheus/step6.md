Now that you have your Prometheus server, an exporter, and have run some queries you probably are noticing that 
Prometheus is not really that pretty looking. Well have no fear `Grafana` has us covered with very nice and easy way to
visualize things much fancier for us. 

* First we need to star the `Grafana Container`

```
docker run -d \
 --net=host \
 --name grafana \
 -p 3000:3000 grafana/grafana
```{{execute}}

## Tasks

* Now that Grafana is started we can view the Dashboard at http://[[HOST_SUBDOMAIN]]-3000-[[KATACODA_HOST]].environments.katacoda.com/

* Once that page is up you will need to login with User:`admin` Password:`admin` and just set a new one after you have 
logged in. 

* After you are logged in you then just need to go to `Add data source` and select `Prometheus`. The settings that pop up
should be for `localhost:9090` as they are the Prometheus Defaults. 

* Once the data source is added you can go to the `+` button on the left hand side and select `Create -> Dashboard`. 
You should then be able select `Prometheus` as the data source and just put one of the queries we defined previously 
directly into the `query` section on the page and bam! You are visualizing Prometheus metrics in Grafana.

