# Jenkins

> Jenkins is a CI/CD tool. I use it to automize certain tasks.

## Usage

Set the following environment variables:

```env
DOMAIN=
```

and change the volume `YOUR_SOURCE_FOLDER` to your corresponding folder if you want to run docker commands in this folder. It can be useful when you want to create automatic backups.

Finally you can start the application (without detach mode to get the token):

```sh
docker-compose up
```

Now you have to wait until Jenkins is up, next step is to unlock the session by the key you will see in the logs. However, it is easier to link the [documentation](https://hub.docker.com/_/jenkins)
