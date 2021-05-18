# Homer

A simple static Homepage for quick access to our applications. For further information, please check out [Homer](https://github.com/bastienwirtz/homer)

## Usage

Set the following environment variables:

```env
DOMAIN=
DASHBOARD_PASSWORD=
```

(Traefik takes care for the authentication, in my case I just reused the password of Traefik Dashboard)

And then run

```sh
docker-compose up -d
```
