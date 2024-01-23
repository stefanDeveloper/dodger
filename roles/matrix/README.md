# Synapse Matrix Server

To run docker-compose up you have to adapt `.env` and replace `YOUR_DOMAIN.TLD` and `YOUR_SECRET` in `nginx/` and `files`.

## Usage

Set the following environment variables:

```bash
DOMAIN=
DB_PASSWORD=
```

And then run

```sh
docker-compose up -d
```

### Bridges

> For more information, please read the official documentation of Mautrix https://docs.mau.fi/bridges/index.html

Supported bridges in this setting

- [Signal](docker-compose.signal.yaml)
- [Telegram](docker-compose.telegram.yaml)
- [WhatsApp](docker-compose.whatsapp.yaml)
