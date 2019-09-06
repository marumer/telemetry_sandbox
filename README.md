# telemetry_sandbox

This sandbox built on influxData official repository https://github.com/influxdata/sandbox with Grafana and the configuration required for Cisco XR MDT 

To pull the latest from the original subproject in sandbox use:
git pull -s subtree sandbox master


# Usefull CURL command:

 - To create a new database in Influx
curl -i -XPOST http://localhost:8086/query --data-urlencode "q=CREATE DATABASE mdt_db with duration 24h replication 1 shard duration 1h name test24h"

 - To create an Influxdb data source in Grafana for the telegraf database
curl -s 'http://admin:admin@127.0.0.1:3000/api/datasources' -X POST -H 'Content-Type: application/json;charset=UTF-8' --data-binary '{"name":"InfluxDB","type":"influxdb","access":"proxy","url":"http://influxdb:8086","password":"admin","user":"admin","database":"telegraf","basicAuth":false,"basicAuthUser":"","basicAuthPassword":"","withCredentials":false,"isDefault":false,"jsonData":{},"tlsAuth":{"tlsCACertSet":false,"tlsClientCertSet":false,"tlsClientKeySet":false}}'
