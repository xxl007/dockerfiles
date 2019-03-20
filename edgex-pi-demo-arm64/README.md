# EdgeX Pi Demo

- [Host Setup](#Host Setup)
- [Pi Setup](#Pi-Setup)
- [Demo](#Demo)

## Host Setup
Firstly, it needs to prepare the docker service on your host machine.

Then, start demo serviers with below steps:
1. Download host-docker-compose.yml and hivemq config file
```
wget https://raw.githubusercontent.com/byang-intel/dockerfiles/master/edgex-pi-demo-arm64/hivemq.conf
wget -O docker-compose.yml https://raw.githubusercontent.com/byang-intel/dockerfiles/master/edgex-pi-demo-arm64/host-docker-compose.yml
```

2. Modify the Pi board addr in docker-compose.yml
```
sed 's/INPUT_STREAM=.*/INPUT_STREAM=http:\/\/<your pi board ip>:49990/g' -i docker-compose.yml
```

3. Launch all serivers
```
docker-compose up -d
```

## Pi Setup
Firstly, flash any linux distrubition and enable docker.

E.g. To install ubuntu, it can refer to below link

https://wiki.ubuntu.com/ARM/RaspberryPi

When docker service is ready, run EdgeX Pi Demo with below steps:

1. Download demo docker-compose.yml
```
wget https://raw.githubusercontent.com/byang-intel/dockerfiles/master/edgex-pi-demo-arm64/docker-compose.yml
```

2. Modify the broker addr in docker-compose.yml
```
sed 's/MQTT_BROKER_ADDR=.*/MQTT_BROKER_ADDR=<your host ip>/g' -i docker-compose.yml
```

3. Launch all serivers
```
docker-compose up -d
```
If the MQTT_BROKER_ADDR is modified, it needs to re-launch the serivers
```
docker-compose restart
```

## Demo