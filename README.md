# powermon
Power Monitoring Set-Up for P1 (tailored for BE)
## basic setup
### create the following directories where the docker-compose file is located:
* .config
* .configmqtt
* .log
* .influxdb
* .grafana
### create a basic mqtt config
* in the .configmqtt folder, create a file mosquitto.conf which contains:
  * log_dest file /mosquitto/log/mosquitto.log
  * connection_messages false
  * listener 1883
  * allow_anonymous true
### running the compose file
* execute docker-compose up -d
### set-up grafana
* connect to your grafana instance via http://dockerhost:3000
* follow the first-run wizard
* add your influx db with the username / password defined in the docker-compose.yaml file
* your influx db is running on dockerhost:8086
### set-up node-red
* connect to node-red via http://dockerhost:1880
* add nodes to your palette - you need:
  * node-red-contrib-modbus (for SMA Monitoring)
  * node-red-contrib-influxdb
  * node-red-contrib-interval
* you can then import flows.json
* configure mqtt and the influxdb service in node-red and deploy it
* your data should now be going to influx db in 10 second intervals
### create dashboards in grafana
* you can now create dashboards to your liking in Grafana
