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

The node-exporter and Cadvisor are available globally
```
http://localhost:[container_port]/metrics
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
```

##### Alertmanager web interface
```
http://localhost:9093/#/alerts
```

