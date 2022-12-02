# Prometheus stack

A prometheus stack example with grafana using node exporter

## Requirements

- Docker
- Swarm mode

##### optional for example

- Vagrant
- Puppet

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

## Add node to the swarm

Joining the swarm as a node/worker will replicate node-exporter and cadvisor on
this node.

#### Puppet example

Using a puppet master to apply a manifest that will make agent join the swarm
Instruction are in the puppet folder

#### Vagrant example

The Vagrantfile will lauch a centos vm
You can use the vagrant file running:

```
vagrant up
vagrant ssh master
```

install docker

```
sudo yum install -y yum-utils
sudo yum-config-manager \
    --add-repo \
    https://download.docker.com/linux/centos/docker-ce.repo
sudo yum install docker-ce docker-ce-cli containerd.io docker-compose-plugin
sudo systemctl start docker
sudo groupadd docker
sudo usermod -aG docker $USER
newgrp docker
```

If you forgot your toker get it back from master like this 
```
docker swarm join-token worker
```

From vm Join the swarm
```
docker swarm join --token <token> <ip>:<port>
```

Few moments later you will be able to see the 2 new container instances on
grafana.
Both containers exposes metrics from their http://[master ip]:[contaier port]/metrics
