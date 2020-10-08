# Laravel dev docker

A development docker for every laravel project


## Features

- Build for laravel and has cli tools
- Bundle of `fpm`, `cli`, `nginx`, `mariadb`, `phpmyadmin`, `mongodb`, `redis` and `emailcatcher` containers
- Latest php7.4 and others coming soon...
- Latest database mariadb10, mongodb4 and other versions supported
- Latest node14.x, node13.x, node12.x, ... supported
- Included laravel, composer and node cli
- Support for laravel horizon
- Included emailcatcher with smtp and web view
- Support for PhpStorm or VSCode + WSL2/docker-desktop setup
- Support for xdebug included check `.env` file


## Docker setup

- `git clone https://github.com/readymadehost/laravel-dev-docker.git project-docker`
- `cd project-docker`
- `mkdir project` or `git clone <some_git_repo_url> project` for existing project
- `cp .env.sample .env` and review `.env` file
- `docker-compose build`
- `docker-compose up -d`
- `docker-compose exec cli bash`
- `laravel -V`


## New laravel project install

- `docker-compose exec cli bash` and make sure you are at `/var/www/project` dir
- `composer create-project --prefer-dist laravel/laravel .`
- Run bash alis `mpp` for `/root/manage-project-permission.sh`


## Notes

- Project URL: http://{localhost/any_valid_host}:8080/
- PhpMyAdmin URL: http://{localhost/any_valid_host}:8180/
- Mailcatcher URL: http://{localhost/any_valid_host}:8280/
- For more info and change, check `.env` and `docker-compose.yml`
- Manage permission inside container using bash alias `mpp` or `/root/manage-project-permission.sh`
- Mariadb default:- host: `mariadb` user: `root`, password: `root`, database: `project`
- Mongodb default:- host: `mongodb` user: `root`, password: `root`, database: `project`, authSource: `admin`

```text
- <docker_root_dir> <-- docker root dir
- <docker_root_dir>/data <-- all docker data persist
- <docker_root_dir>/nginx <-- nginx
- <docker_root_dir>/php* <-- php cli and fpm containers
- <docker_root_dir>/.env <-- docker environment configuration

- <docker_root_dir>/project <-- project root dir

- <docker_root_dir>/project* <-- added in .gitignore
- <docker_root_dir>/*.sql <-- added in .gitignore
```


## Laravel horizon support

Laravel horizon is disabled by default. Check `.env` to enable but only after your project includes horizon.


## Mailcatcher support

Mailcatcher service is included, can be accessed using URL and can be configured using smtp check `.env` for more info.


## Mongodb support

Mongodb service is disabled by default. Check `.env` and `docker-compose.yml` for more info. Mongodb can be connected using compass:-

```
mongodb://root:root@localhost:27017/?authSource=admin
```


## Phpstorm setup

Simply add remote docker-compose php cli interpreter (exec with docker-compose.yml), change path mapping and configure remote interpreter for composer, phpunit, phpcs, phpcbf, phpmd and php-cs-fixer.


## Remote container extension + vscode

With vscode's remote container extension, we can simply connect into cli container.


## For development usages

- Clone this repo and pull on update. ReadyMadeHost cli tool coming soon...


## For production usages

- Current docker setup is for development only. Planning for ReadyMadeHost coming soon...
