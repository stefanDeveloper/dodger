# Portainer

## Usage

Set the following environment variables:

```env
DOMAIN=
```

And then run

```sh
docker-compose up -d
```

## Generate the admin password

For this example, we'll use the password `superpassword`.

Use the following command to generate a hash for the password:

```sh
docker run --rm httpd:2.4-alpine htpasswd -nbB admin 'superpassword' | cut -d ":" -f 2
```

If you try to use the hashed password in this form directly in your Compose file, the following error will be raised:

`ERROR: Invalid interpolation format for "command" option in service "portainer": --admin-password 'SUPER_HASH'"`

You need to escape each `$` character inside the hashed password with another `$`:

`$$2y$$05$$dsada24rds.dsadasdw43tsdsda`