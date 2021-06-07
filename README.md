# ELK STACK WITH DOCKER SWARM (DEV) 

[![N|Solid](https://github.com/docker/classicswarm/blob/master/logo.png?raw=true)](https://nodesource.com/products/nsolid)

This stack has the following services:
  - Elasticsearch - Master node (deployed only in manager node)
  - Elasticsearch - Data node (deployed global - as many as your cluster size)
  - Elasticsearch - Coordination/Ingress Node Data node (deployed global - as many as your cluster size) 
  - Kibana - Cluster visualizer (deployed only in manager node)
  - Nginx - Reverse proxy to kibana or elasticsearch (deployed only in manager node)

### Deploy the stack

This stack must be deploy as follows:

```sh
$ env $(cat .env | xargs) docker stack deploy -c mult-node.yaml elk
```

In your .env file you should have:

```html
ES_VERSION=7.8.1
KIBANA_VERSION=7.8.1
NGINX_VERSION=1.18.0-alpine
ES_MASTER_NODES=es-master-[HOSTNAME_MANAGER_NODE]
ES_MASTER_HEAP_MEMORY=512m
ES_DATA_HEAP_MEMORY=512m
ES_COORDINATION_HEAP_MEMORY=512m
```
