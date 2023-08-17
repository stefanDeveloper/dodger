# Wazuh

> Helps to monitor security events

## Usage

Please refer to the official [Wazuh documentation](https://documentation.wazuh.com/current/deployment-options/docker/index.html) when setting up for the first time.

If you plan to run Wazuh with Traefik as reverse proxy, you can apply the following patch to the Wazuh Docker single-node deployment.

```bach
git apply docker-compose.yml.diff
```

Remark: We set a static IP address to our Wazuh Manager container to reliably connect our agent (that usually runs on our host) to monitor events.