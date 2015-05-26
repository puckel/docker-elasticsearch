## ElasticSearch Dockerfile


This repository contains a base **Dockerfile** of [ElasticSearch](http://www.elasticsearch.org/) for [Docker](https://www.docker.com/)'s [automated build](https://registry.hub.docker.com/u/dockerfile/docker-elasticsearch/) published to the public [Docker Hub Registry](https://registry.hub.docker.com/).

With some custom addition : plugin head and a custome elasticsearch.yml


### Base Docker Image

* Official [java:8](https://registry.hub.docker.com/_/java/)


### Installation

1. Install [Docker](https://www.docker.com/).

2. Download [automated build](https://registry.hub.docker.com/u/puckel/docker-elasticsearch/) from public [Docker Hub Registry](https://registry.hub.docker.com/): `docker pull puckel/docker-elasticsearch`

Alternatively, you can build an image from Dockerfile: `https://github.com/puckel/docker-elasticsearch/`


### Usage

    docker run -d -p 9200:9200 --name elasticsearch puckel/docker-elasticsearch

#### Attach persistent/shared directories

  1. Create a mountable data directory `<data-dir>` on the host.

  2. Edit ElasticSearch config file at `<data-dir>/elasticsearch.yml`.

    ```yml
    path:
      logs: /data/log
      data: /data/data
    ```

  3. Start a container by mounting data directory and specifying the custom configuration file:

    ```sh
    docker run -d -p 9200:9200 -v <data-dir>:/data --name elasticsearch puckel/docker-elasticsearch
    ```

After few seconds, open `http://<host>:9200` or `http://localhost:9200/_plugin/head/` to see the result.
