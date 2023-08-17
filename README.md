<h1 align="center">
  <br />
  Dodger
</h1>
<h4 align="center">Be sure to :star: my configuration repo so you can keep up to date on any daily progress!</h4>
<div align="center">
  <h4>
    <a href="https://github.com/stefanDeveloper/dodger"><img src="https://img.shields.io/github/stars/stefanDeveloper/dodger.svg?style=plasticr"/></a>
    <a href="https://github.com/stefanDeveloper/dodger/commits/main"><img src="https://img.shields.io/github/last-commit/stefanDeveloper/dodger.svg?style=plasticr"/></a>
    <a href="https://github.com/stefanDeveloper/dodger/commits/main"><img src="https://img.shields.io/github/commit-activity/y/stefanDeveloper/dodger.svg?style=plasticr"/></a>
  </h4>
</div>

## Overview

This repository provides a complete Docker stack to easily set up your server with Traefik, Portainer, Nextcloud, Homer, Openvpn, Gitlab, Wordpress, Resilio, Seafile, OpenLDAP, Jenkins, and Matrix.

## Supported Applications

* [Traefik](./traefik/README.md) as a reverse proxy to route your request (mandatory)
* [Wordpress](./blog/README.md) just a simple Wordpress blog page
* [GitLab](./gitlab/README.md) for coding
* [Portainer](./portainer/README.md) helps you to maintain your containers and images
* [Nextcloud](./Nextcloud/README.md) one of my favorite private clouds :heart:
* [Homer](./homer/README.md) just a landing page with links
* [Resilio](./resilio/README.md) allows you to sync your data with others, helpful to share backups
* [Seafile](./seafile/README.md) another cloud (not used by me anymore)
* [OpenLDAP](./openldap/README.md) configuration for easy usage with GUI.
* [Matrix](./matrix/README.md) Synapse server with LDAP configuration.
* [Hugo](./hugo/README.md) hugo server to deploy simple website.
* [Wazuh](./wazuh/README.md) to monitor security events of our Docker containers.

## Getting Started

Just clone this repository and follow each guideline inside the corresponding application folder:

```sh
git clone https://github.com/stefanDeveloper/dodger.git
```

In each of these folders you will find a `docker-compose.yml`, a `.env` file, as well as a `README.md` that describes some basics about this application.

In case you want to run applications individually, please make sure your Docker environment has a network called `proxy`. If this is not the case, please run:

```sh
docker network create proxy
```

