# DOCKER-PHP-ENV

A set of docker preconfigured images and a compose script to setup a dev environment quickly for PHP development with frameworks like [Laravel](https://laravel.com/docs).

## How to use it

1. Clone the repository.
2. Put your app source code in the src folder.
3. Start the environment with docker compose.

### Launch the containers

```
# Built the docker images and start the nginx service
$ docker-compose up -d --build nginx
```
