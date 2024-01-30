# Nextcloud

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
