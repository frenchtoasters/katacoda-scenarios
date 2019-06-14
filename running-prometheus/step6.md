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

## TODO

* Login to [grafana](http://[[HOST_SUBDOMAIN]]-3000-[[KATACODA_HOST]].environments.katacoda.com/) to work with the dashboards

* Once that page is up you will need to login with and just set a new one after you have logged in 
 ```
 User: admin
 Password: admin
 ```

* Next you just need to go to `Add data source` and select `Prometheus`. You will just need to fill in the `URL` field 
with `localhost:9090`{{copy}} _the Prometheus Defaults_ and click `Save & Test` as long as you get a 
`Data Source is working` green check mark you are good.

* Once the data source is added you can go to the `+` button on the left hand side and select `Create -> Dashboard`. 
You should then be able select `Prometheus` as the data source and just put one of the queries we defined previously 
directly into the `query` section on the page and bam! You are visualizing Prometheus metrics in Grafana.

