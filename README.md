# DOCKER-PHP-ENV

A set of docker preconfigured images and a compose script to setup a dev environment quickly for PHP development with frameworks like [Laravel](https://laravel.com/docs).

## How to use it

1. Clone the repository.
2. Put your app source code in the src folder.
3. Start the environment with docker compose.

### Launch the service

```
# Built images
$ docker-compose build

# Start the nginx service
$ docker-compose up -d nginx

# Built the docker images and start the nginx service
$ docker-compose up -d --build nginx
$ docker-compose up -d --build caddy # if you wand to use caddy 2 webserver

# Stop and remove the containers, network and volumes
$ docker-compose down

# Stop the containers
$ docker-compose stop
```

### Run commands into services

These commands runs the service, execute the passed command, then stop the service `-rm` flag.

```
# Start and run a composer command into the composer service
$ docker-compose run --rm composer install mypackage/mypackage

# Run php-cli commands inside php-cli service
$ docker-compose run --rm php-cli make:seeder UserSeeder

# Run the queues worker in his separate service
$ docker-compose up -d queues-worker queue:work # With laravel default queues driver
$ docker-compose up -d queues-worker horizon # With laravel horizon

# Run mailhog
docker-compose up -d mailhog
```

### .env

The `.env` file contains environment vars, yout can tweek these vars to update your config to your needs.

### MySQL database volume

By default the mysql db will be stored in a docker volume to persist the db between containers starts and stops.
If you do not whant this behavior, you can remove the volume in the `docker-compose.yml` file.

## TODO

- **Add service to run meilisearch search engine
- Add service to run task scheduling service
- **Add service to run queue worker
- Add caddy 2 webserver with https
- **Add mailhog for mail testing
- Add service to run websocket service
