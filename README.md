# grafana-alert-with-email

Edit grafana configmap. add hte following entry to grafana.ini file.

kubectl edit configmap -n loki-stack loki-stack-grafana
~~~
    [smtp]
    enabled = true
    host = mta.brilliant.com.bd:25
    user = monitor@brilliant.com.bd
    password = Cl0ud-M0n!t0r
    skip_verify = false
    from_address = monitor@brilliant.com.bd
    from_name = Grafana 
~~~

restart the grafana pod

datasource add
~~~
name influx
http://monasca-influxdb.monasca.svc.cluster.local:8089
database: mon
user: mon_api
