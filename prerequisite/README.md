# Prerequisite #

Server setup conclusion, including Fail2Ban, user authentication key pair, disable root login, disallow SSH password authentication, firewall installation, secure shared memory

## Content ##

* [Set up docker](#set-up-docker)
* [Update](#update)
* [Use authentication Key pair to log to your server](#Use-authentication-key-pair-to-log-to-your-server)
* [Create a non-root user with sudo privileges](#create-a-non-root-user-with-sudo-privileges)
* [Disable remote root login](#disable-remote-root-login)
* [Disallow SSH password authentication](#disallow-SSH-password-authentication)
* [Install a firewall](#install-a-firewall)
* [Secure Shared Memory](#secure-shared-memory)
* [Install Fail2ban](#Fail2Ban)

## Update ##

Update your server:

> ```apt-get update```

> ```apt-get upgrade```

Docker CE needs to be installed.

## Create a non-root user with sudo privileges ##

> ```sudo adduser <username>```

Just in case you want to create a user with sudo permissions:

> ```sudo usermod -aG sudo <username>```

## Use authentication Key pair to log to your server ##

Create a key on your local machine:

> ```ssh-keygen -f ~/<username>-key-ecdsa -t ecdsa -b 521```

On you server, add public key of your machine:

### Either manually ###

> ```umask 077 && test -d ~/.ssh || mkdir ~/.ssh```

> ```umask 077 && touch ~/.ssh/authorized_keys```

> ```vim ~/.ssh/authorized_keys```

### Or automatically ###

Copy SSH keys to your local machine. The `ssh-copy-id` tool is included by default in many operating systems, so you may have it available on your local system:

> ```ssh-copy-id username@remote_host```

Finally, we change the permissions:

> ```chmod 700 ~/.ssh```
> ```chmod 600 ~/.ssh/authorized_keys```

## Disable remote root login ##

> ```sudo vim /etc/ssh/sshd_config```

Change PermitRootLogin to

```PermitRootLogin no```

Adapt following ssh configs:

* ```ClientAliveInterval 300```

* ```ClientAliveCountMax 2```

* ```PubkeyAuthentication yes```

* ```MaxAuthTries 3```

## Disallow SSH password authentication ##

```PasswordAuthentication no```

Restart is required:

> ```sudo service ssh restart```

## Install a firewall ##

> ```sudo ufw allow ssh```

> ```sudo ufw allow https```

> ```sudo ufw enable```

> ```sudo ufw status verbose```

## Secure Shared Memory ##

> ```sudo vim /etc/fstab```

Add to the bottom

> ```none /run/shm tmpfs defaults,ro 0 0```

## Fail2Ban ##

> ```sudo apt-get install -y fail2ban```

Start and enable:

> ```sudo systemctl start fail2ban```
> ```sudo systemctl enable fail2ban```

Set fail2ban configuration:

> ```cp ./fail2ban/jail.local /etc/fail2ban/jail.local```

Restart fail2ban:

> ```sudo systemctl restart fail2ban```

In order to check and authentication tries, check:

> ```less +G /var/log/auth.log```

If you want to add slack notification, follow this [introduction](https://github.com/coleturner/fail2ban-slack-action)

## Set up docker ##

Create network

> ```docker network create proxy```