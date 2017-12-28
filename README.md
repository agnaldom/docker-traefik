<p align="center">
<img src="docs/img/traefik.logo.png" alt="Traefik" title="Traefik" />
</p>

[![Build Status SemaphoreCI](https://semaphoreci.com/api/v1/containous/traefik/branches/master/shields_badge.svg)](https://semaphoreci.com/containous/traefik)
[![Docs](https://img.shields.io/badge/docs-current-brightgreen.svg)](https://docs.traefik.io)
[![Go Report Card](https://goreportcard.com/badge/containous/traefik)](http://goreportcard.com/report/containous/traefik)
[![](https://images.microbadger.com/badges/image/traefik.svg)](https://microbadger.com/images/traefik)
[![License](https://img.shields.io/badge/license-MIT-blue.svg)](https://github.com/agnaldom/docker-traefik/blob/master/LICENSE)
[![Join the chat at https://traefik.herokuapp.com](https://img.shields.io/badge/style-register-green.svg?style=social&label=Slack)](https://traefik.herokuapp.com)
[![Twitter](https://img.shields.io/twitter/follow/traefikproxy.svg?style=social)](https://twitter.com/intent/follow?screen_name=traefikproxy)


Træfik (pronounced like [traffic](https://speak-ipa.bearbin.net/speak.cgi?speak=%CB%88tr%C3%A6f%C9%AAk)) is a modern HTTP reverse proxy and load balancer made to deploy microservices with ease.
It supports several backends ([Docker](https://www.docker.com/), [Swarm mode](https://docs.docker.com/engine/swarm/), [Kubernetes](https://kubernetes.io), [Marathon](https://mesosphere.github.io/marathon/), [Consul](https://www.consul.io/), [Etcd](https://coreos.com/etcd/), [Rancher](https://rancher.com), [Amazon ECS](https://aws.amazon.com/ecs), and a lot more) to manage its configuration automatically and dynamically.

---
. **[Overview](#overview)** .
****[Supported backends](#supported-backends)** .
**[Web UI](#web-ui)** .

---

## Overview

Imagine that you have deployed a bunch of microservices on your infrastructure. You probably used a service registry (like etcd or consul) and/or an orchestrator (swarm, Mesos/Marathon) to manage all these services.
If you want your users to access some of your microservices from the Internet, you will have to use a reverse proxy and configure it using virtual hosts or prefix paths:

- domain `api.domain.com` will point the microservice `api` in your private network
- path `domain.com/web` will point the microservice `web` in your private network
- domain `backoffice.domain.com` will point the microservices `backoffice` in your private network, load-balancing between your multiple instances

Microservices are often deployed in dynamic environments where services are added, removed, killed, upgraded or scaled many times a day.

Traditional reverse-proxies are not natively dynamic. You can't change their configuration and hot-reload easily.

Here enters Træfik.

![Architecture](https://github.com/containous/traefik/blob/master/docs/img/architecture.png)

Træfik can listen to your service registry/orchestrator API, and knows each time a microservice is added, removed, killed or upgraded, and can generate its configuration automatically.
Routes to your services will be created instantly.

Run it and forget it!


## Supported backends

- [Docker](https://www.docker.com/) / [Swarm mode](https://docs.docker.com/engine/swarm/)
- [Kubernetes](https://kubernetes.io)
- [Mesos](https://github.com/apache/mesos) / [Marathon](https://mesosphere.github.io/marathon/)
- [Rancher](https://rancher.com) (API, Metadata)
- [Consul](https://www.consul.io/) / [Etcd](https://coreos.com/etcd/) / [Zookeeper](https://zookeeper.apache.org) / [BoltDB](https://github.com/boltdb/bolt)
- [Eureka](https://github.com/Netflix/eureka)
- [Amazon ECS](https://aws.amazon.com/ecs)
- [Amazon DynamoDB](https://aws.amazon.com/dynamodb)
- File
- Rest API

## Web UI

You can access the simple HTML frontend of Træfik.

![Web UI Providers](docs/img/web.frontend.png)
![Web UI Health](docs/img/traefik-health.png)



  This is how I've managed to get this working with the LetsEncrypt automated renewal using Docker Swarm and Docker Compose V3

# Deployment

## Docker
[![Rocket.Chat logo](https://d207aa93qlcgug.cloudfront.net/1.95.5.qa/img/nav/docker-logo-loggedout.png)](https://hub.docker.com/r/rocketchat/rocket.chat/)

### Install docker
[Install Docker](https://docs.docker.com/engine/installation/)

and 

[Install Docker Compose](https://docs.docker.com/compose/install/)

```
git clone https://github.com/agnaldom/docker-traefik.git
```

```
cd docker-traefik 
```

```
docker-compose up -d
```


### Logs

```
docker-compose logs -f
```

## About  Traefik more

* [Traefik desvendadno entrypoint frontend e backend](https://churrops.io/2017/11/21/traefik-desvendando-entrypoint-frontend-e-backend/)
* [Docker load balancer com traefik e swam](https://churrops.io/2017/11/08/docker-load-balancer-com-traefik-e-swarm/)
* [Containous traefik](https://github.com/containous/traefik#overview)
* [Traefik Official](https://traefik.io/)


## License

This project is distributed under [GNU General Public License, Version 3.0](LICENSE).
