# termostato

## Comandos para crear los contenedores de docker
Pendiente pasar a docker-compose. Los puertos realmente no son necesarios al estar en una red host.
```shell
docker run -it -p 1880:1880 -d --net=host --name mynodered nodered/node-red
docker run -it -p 1883:1883 -p 9001:9001 -d --net=host --name mymqttbroker eclipse-mosquitto
docker run -it -p 8086:8086 -d -v influxdb:/var/lib/influxdb --net=host --name myinfluxdb influxdb:1.8
```

## Comandos ejecutados o tareas realizadas a mano para las pruebas

En el MQTT Broker, creamos un topic que recibirá los datos que luego se mandarán a InfluxDB.  
`mosquitto_sub -h localhost -t "prueba"`

Tenemos que crear la base de datos donde se almacenarán los datos.  
`create database prueba`

La configuración que lleva el Node-RED se adjunta en el repositorio. En Node también hay que instalar el plugin de InfluxDB en el apartado *Menu* > *Manage Palette* > *Install* > Type: __node-red-contrib-influxdb__
