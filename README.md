<h1 align="center">
  <br />
  
  ![dodger Logo](https://github.com/stefanDeveloper/dodger/assets/18898803/baa4278f-ef46-4227-a08c-cfb8445c17a4?raw=true)
</h1>
<h4 align="center">Be sure to :star: my configuration repo so you can keep up to date on any daily progress!</h4>
<div align="center">
  <h4>
    <a href="https://github.com/stefanDeveloper/dodger"><img src="https://img.shields.io/github/stars/stefanDeveloper/dodger.svg?style=for-the-badge"/></a>
    <a href="https://github.com/stefanDeveloper/dodger/commits/main"><img src="https://img.shields.io/github/last-commit/stefanDeveloper/dodger.svg?style=for-the-badge"/></a>
    <a href="https://github.com/stefanDeveloper/dodger/commits/main"><img src="https://img.shields.io/github/commit-activity/y/stefanDeveloper/dodger.svg?style=for-the-badge"/></a>
  </h4>
</div>

## Overview

This repository provides a complete Docker stack to easily set up your server with Modsecurity, CrowdSec, and Nextcloud.

## Supported Applications

* [Crowdsec](./Crowdsec/README.md) just the best firewall handler
* [Nextcloud](./Nextcloud/README.md) one of my favorite private clouds :heart:

## Getting Started

Just clone this repository and follow each guideline inside the corresponding application folder:

```sh
git clone https://github.com/stefanDeveloper/dodger.git
```

Deploying made simple by applying Ansible Playbooks including hardening, installs and more!

Create Python virtualenv and install requirements:

```bash
python -m venv .venv
source .venv/bin/activate

pip install -r requirements.txt
```

Replace your IP address in the `inventory.yml` and run the provided Ansible playbook:

```bash
ansible-playbook dodger_deploy.yml
```
