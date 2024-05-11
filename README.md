
# Docker Laravel Traefik 

Boilerplate for laravel projects using Traefik. It will help local development using custom url we want without doing any configurations.

## Installation in existing Laravel project

To deploy existing project place folder inside your exisitng Laravel setup and run following command

```bash
  docker compose build
  docker compose up -d
```

It will run two containers and website could be able to access from http://laravel.localhost/

## Installation in fresh Laravel project
To deploy new project run following command

```bash
  docker compose build
  docker compose up -d
  docker exec --workdir /srv/app laravel sh -c "/usr/bin/composer create-project laravel/laravel laravel"
  docker exec --workdir /srv/app laravel sh -c "rm -rf public/* && mv laravel/{.*,*} ."
```
website could be able to access from http://laravel.localhost/

## Change Host Name 

To change host name edit compose.yaml
```
 - "traefik.http.routers.laravel.rule=Host(`laravel.localhost`)"
```

change Host name from laravel.localhost to any name you want.
