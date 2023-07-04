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
* [OpenLDAP](./openldap/README.md) configuration for easy usage with GUI.
* [Matrix](./matrix/README.md) Synapse server with LDAP configuration.

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

## Getting Started


Server setup conclusion, including Fail2Ban, user authentication key pair, disable root login, disallow SSH password authentication, firewall installation, secure shared memory

### Content

* [Set up docker](#set-up-docker)
* [Update](#update)
* [Use authentication Key pair to log to your server](#Use-authentication-key-pair-to-log-to-your-server)
* [Create a non-root user with sudo privileges](#create-a-non-root-user-with-sudo-privileges)
* [Disable remote root login](#disable-remote-root-login)
* [Disallow SSH password authentication](#disallow-SSH-password-authentication)
* [Install a firewall](#install-a-firewall)
* [Secure Shared Memory](#secure-shared-memory)
* [Install Fail2ban](#Fail2Ban)

### Update

Update your server:

```sh
apt-get update

apt-get upgrade
```
Docker CE needs to be installed.

### Create a non-root user with sudo privileges

```sh
sudo adduser <username>
```
Just in case you want to create a user with sudo permissions:

```sh
sudo usermod -aG sudo <username>
```

### Use authentication Key pair to log to your server

Create a key on your local machine:

```sh
ssh-keygen -f ~/<username>-key-ecdsa -t ecdsa -b 521
```
On you server, add public key of your machine:

Either manually

```sh
umask 077 && test -d ~/.ssh || mkdir ~/.ssh

umask 077 && touch ~/.ssh/authorized_keys

vim ~/.ssh/authorized_keys
```
Or automatically

Copy SSH keys to your local machine. The `ssh-copy-id` tool is included by default in many operating systems, so you may have it available on your local system:

```sh
ssh-copy-id username@remote_host
```

Finally, we change the permissions:

```sh
chmod 700 ~/.ssh
chmod 600 ~/.ssh/authorized_keys
```

### Disable remote root login

```sh
sudo vim /etc/ssh/sshd_config
```

Change PermitRootLogin to

PermitRootLogin no

Adapt following ssh configs:

* ```ClientAliveInterval 300```

* ```ClientAliveCountMax 2```

* ```PubkeyAuthentication yes```

* ```MaxAuthTries 3```

### Disallow SSH password authentication

```PasswordAuthentication no```

Restart is required:

    sudo service ssh restart

### Install a firewall

```sh
sudo ufw allow ssh

sudo ufw allow https

sudo ufw enable

sudo ufw status verbose
```
### Secure Shared Memory

```sh
sudo vim /etc/fstab
```

Add to the bottom
```
none /run/shm tmpfs defaults,ro 0 0
```

### Fail2Ban

```sh
sudo apt-get install -y fail2ban
```

Start and enable:

```sh
sudo systemctl start fail2ban
sudo systemctl enable fail2ban
```

Set fail2ban configuration:

```sh
cp ./fail2ban/jail.local /etc/fail2ban/jail.local
```

Restart fail2ban:

```sh
sudo systemctl restart fail2ban
```

In order to check and authentication tries, check:

```sh
less +G /var/log/auth.log
```

If you want to add slack notification, follow this [introduction](https://github.com/coleturner/fail2ban-slack-action)

### Set up docker

Create network

```sh
    docker network create proxy
```

## Contribution

If you face troubles starting one of these `docker-compose` files, do not hestitate to create issues or pull request.
