# Ansible

Deploying made simple by applying Ansible Playbooks including hardening, installs and more!

## Getting Started

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

