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

# Run artisan commands inside php-cli service
$ docker-compose run --rm artisan make:seeder UserSeeder
```

### .env

The `.env` file contains environment vars, yout can tweek these vars to update your config to your needs.

### MySQL database volume

By default the mysql db will be stored in a docker volume to persist the db between containers starts and stops.
If you do not whant this behavior, you can remove the volume in the `docker-compose.yml` file.

## TODO

- Add service to run meilisearch search engine
- Add service to run task scheduling service
- Add service to run queue worker
