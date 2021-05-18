# Traefik

## Prerequisite

> Traefik is reverse proxy. It automically fetchs certificates from LetsEncrypt with EC384 encryption. This is just a default setting and can be adjusted anytime.

To run docker-compose up you have to adapt `.env` and run

```sh
sudo chmod 600 -R ./letsencrypt
```

and change the following strings inside the `docker-compose`:

```yaml
# Change email
- "--certificatesresolvers.mytlschallenge.acme.email=YOUR_EMAIL"
```

(I wasn't able to resolve it with a `.env` file, please feel free to contribute)

## Usage

Set the following environment variables:

```env
DOMAIN=
DASHBOARD_PASSWORD=
```

And then run

```sh
docker-compose up -d
```
