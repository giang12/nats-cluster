# Docker Nats Cluster

Creates a [Docker](https://www.docker.com)-based [nats](https://nats.io/)
cluster with [docker-compose](https://docs.docker.com/compose)

## Prerequisites

Works for Linux and Mac (with the latest Docker for Mac), and uses docker
compose file syntax version 2.

- [Docker](https://www.docker.com) 1.10.0 or later
- [Docker Compose](https://docs.docker.com/compose) 1.6.0 or later
- [Ruby](https://www.ruby-lang.org)

## In the Box

Ports exposed

`nats://dockerhost.ip:422[2-n]` for clients connection

`http://dockerhost.ip:622[2-n]` HTTP management port for information reporting.

`nats://dockerhost.ip:822[2-n]` routing port for clustering

## Running

Bring up the cluster and specify that you want e.g. five brokers (the default
cluster size is three brokers) with

```
./cluster-gen 5
./cluster-up
```

This will create a `nats-compose.yml` file in the directory that will be used
by `./cluster-down` do delete the cluster (i.e. this stops and removes all data).
If you do not want to delete data, use the `docker-compose` commands directly.
