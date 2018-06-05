# ELK Deployment + Elasticsearch curator
Run the stable version of the ELK + Elasticsearch-curator with Docker and Docker Compose.

Based on the official Docker images:

* [ELK](https://www.elastic.co/guide/en/elasticsearch/reference/6.2/docker.html)


## Contents

1. [Requirements](#requirements)
   * [Host setup](#host-setup)
2. [Getting started](#getting-started)
   * [Initial setup](#initial-setup)
   * [How can I tune the ELK configuration?](#how-can-i-tune-the-elk-configuration)
   * [Bringing up the stack](#bringing-up-the-service)
   * [Elasticsearch Curator](#elasticsearch-curator)
   * [Adjustable Elasticsearch Curator params](#adjustable-elasticsearch-curator-params)
4. [Storage](#storage)
5. [Extensibility](#extensibility)
6. [TO-DO](#to-do)

## Requirements

### Host setup

1. Install [Docker](https://www.docker.com/community-edition#/download) version **1.10.0+**
2. Install [Docker Compose](https://docs.docker.com/compose/install/) version **1.6.0+**
3. Clone this repository

## Initial setup

### How can I tune the ELK configuration?

You can adjust ELK parameters editing configuration files in config directory.

## Usage

### Bringing up the service

**Note**: In case you switched branch or updated a base image - you may need to run `docker-compose build` first

Start the ELK stack using `docker-compose`:

```console
$ docker-compose up
```

You can also choose to run it in background (detached mode):

```console
$ docker-compose up -d
```

By default, the stack exposes the following ports:
* 9200: Elasticsearch node.
* 5044: Logstash node 1 TCP.
* 5601: Kibana node 1 HTTP.

**WARNING**: If you're using `boot2docker`, you must access it via the `boot2docker` IP address instead of `localhost`.

**WARNING**: If you're using *Docker Toolbox*, you must access it via the `docker-machine` IP address instead of
`localhost`

## Elasticsearch Curator

Curator is integrated into elasticsearch docker image and automated via cron task. Current schedule is: run task at 00:00 every day.

### Adjustable Elasticsearch Curator params

```
      CURATOR_LOG_LEVEL: INFO
      CURATOR_FILTER_VALUE: logstash-*
      CURATOR_UNITS: days
      CURATOR_UNIT_COUNT: 15
```


## TO-DO

* Add optimizations and e.t.c.
* Extend possibility of Elasticsearch Curator fine tuning.
* Update documentation

