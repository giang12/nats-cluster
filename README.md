# Docker Nats Cluster

Creates a [Docker](https://www.docker.com)-based [nats](https://nats.io/)
cluster with [docker-compose](https://docs.docker.com/compose)

## Prerequisites

Works for Linux and Mac (with the latest Docker for Mac), and uses docker
compose file syntax version >=3.

-   [Docker](https://www.docker.com) 1.10.0 or later
-   [Docker Compose](https://docs.docker.com/compose) 1.6.0 or later
-   [Ruby](https://www.ruby-lang.org)

## In the Box

Ports exposed

`nats://dockerhost.ip:422[2-n]` for clients connection

`http://dockerhost.ip:622[2-n]` HTTP management port for information reporting.

`nats://dockerhost.ip:822[2-n]` routing port for clustering

## Running

Usage: cluster-gen [options]
-i, --image nats specify nats image
-s, --cluster_size 3 cluster size
-c, --config /etc/nats.cfg config path

Bring up the cluster and specify that you want e.g. five brokers (the default
cluster size is three brokers) with

```
./cluster-gen -s 5
./cluster-up
```

This will create a `nats-compose.yml` file in `PWD` that will be used
by `./cluster-down` do delete the cluster (i.e. this stops and removes all data).
If you do not want to delete data, use the `docker-compose` commands directly.

# Important

The containers will only run on nodes with label `server_type=nats`
From a docker manager node, you can specify the nodes to run nats on by running
`docker node update --label-add server_type=nats {{target_node_id}}`

# Configuration

By default `nats.cfg` will be encrypted and installed, in each nats containers

!!!Edit the file to make changes or point to the desired configuration file with option
`./cluster-gen -c nats/config.cfg`
