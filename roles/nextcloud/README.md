# NextCloud

To run docker-compose up you have to adapt `.env`

## Usage

Set the following environment variables:

```env
POSTGRES_PW=
REDIS_PW=
POSTGRES_PW=
DOMAIN=
```

And then run

```sh
docker-compose up -d
```

## Useful

This is a summary of useful commands to maintain your Nextcloud instance. I covered some basics, so do not expect a hollistic list of useful commands

### Backup

```sh
#!/bin/bash
cd PATH_TO_YOUR_NEXTCLOUD

# Set maintenance mode on
docker exec --user www-data nextcloud_nextcloud_1 php occ maintenance:mode --on

tar -czvg PATH_TO_YOUR_NEXTCLOUD/snapshot.file -f PATH_TO_YOUR_NEXTCLOUD/nextcloud-`date +%d-%m-%Y_%H-%M-%S`.tar.gz ./nextcloud-db ./redis ./nextcloud-www

# Set maintenance mode off
docker exec --user www-data nextcloud_nextcloud_1 php occ maintenance:mode --off
```

### Run Cron

```sh
docker exec -u www-data CONTAINER_NAME php cron.php
```

## CoTURN

Helps to integrate Nextcloud Talks, however, this part is still under investigation. Go to our CoTURN[documentation](./coturn/README.md) to get the latest information.
