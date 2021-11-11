<h1 align="center">
  <br />
  Dodger
</h1>
<h4 align="center">Be sure to :star: my configuration repo so you can keep up to date on any daily progress!</h4>
<div align="center">
  <h4>
    <a href="https://github.com/stefanDeveloper/dodger"><img src="https://img.shields.io/github/stars/stefanDeveloper/dodger.svg?style=plasticr"/></a>
    <a href="https://github.com/stefanDeveloper/dodger/commits/master"><img src="https://img.shields.io/github/last-commit/stefanDeveloper/dodger.svg?style=plasticr"/></a>
    <a href="https://github.com/stefanDeveloper/dodger/commits/master"><img src="https://img.shields.io/github/commit-activity/y/stefanDeveloper/dodger.svg?style=plasticr"/></a>
  </h4>
</div>

## Overview

This repository provides a Docker stack to easily set up your server. This includes Traefik, Portainer, Nextcloud, Homer, Openvpn, Gitlab, Wordpress, Resilio, and Seafile.

## Table Of Contents

* [Traefik](./traefik/README.md) as a reverse proxy to route your request (mandatory)
* [Wordpress](./blog/README.md) just a simple Wordpress blog page
* [GitLab](./gitlab/README.md) for coding
* [Portainer](./portainer/README.md) helps you to maintain your containers and images
* [Nextcloud](./Nextcloud/README.md) one of my favorite private clouds :heart:
* [Homer](./homer/README.md) just a landing page with links
* [OpenVPN](./openvpn/README.md) is self-explaining
* [Resilio](./resilio/README.md) allows you to sync your data with others, helpful to share backups
* [Seafile](./seafile/README.md) another cloud (not used by me anymore)

## Usage

Just clone this repository and follow each guideline inside the corresponding application folder:

```sh
git clone https://github.com/stefanDeveloper/dodger.git
```

In each of these folders you will find a `docker-compose.yml`, a `.env` file, as well as a `README.md` that describes some basics about this application.

In case you want to run applications individually, please make sure your Docker environment has a network called `proxy`. If this is not the case, please run:

```sh
docker network create proxy
```

## Prerequisite

Before running one of the applications, it is advisable to follow the [Prerequisite](./rerequisite/README.md). This guideline helps you to set up your server with some very basic settings, like Fail2Ban.

## Getting Started

tbc. Ansible configuration

## Contribution

If you face troubles starting one of these `docker-compose` files, do not hestitate to create issues or pull request.
