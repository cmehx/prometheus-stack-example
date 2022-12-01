# Prometheus stack

A prometheus stack example with grafana using node exporter

## Requirements

- Docker
- Swarm mode

## Setup

```
docker swarm init
```

```
./boot.sh
```

## Testing

##### Grafana web interface:

Default Password in grafana/config.monitoring
name: admin
psswd: foobar

```
http://localhost:3000/
```

##### Prometheus web interface:
```
http://localhost:9090/
http://localhost:9090/alerts
```

##### Cadvisor web interface:
```
http://localhost:8080/containers/
http://localhost:8080/containers/metrics
```

##### Alertmanager web interface
```
http://localhost:9093/#/alerts
```
