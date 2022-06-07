# Laravel dev docker

A development docker for every laravel project


## Features

- Build for laravel and has cli tools
- Bundle of `fpm`, `cli`, `nginx`, `mariadb`, `phpmyadmin`, `mongodb`, `redis` and `emailcatcher` containers
- PHP 5.5, 5.6, 7.0, 7.1, 7.2, 7.3, 7.4, 8.0 and 8.1 supported
- Database mariadb 10.x, mongodb 4.x ... supported
- Node 14.x, 16.x, 17.x, ... supported
- Included laravel, composer, node cli and yarn cli
- Included emailcatcher with smtp and web view
- Support for PhpStorm or VSCode + WSL2/docker-desktop setup
- Support for xdebug included check `.env` file


## Docker setup

- `git clone https://github.com/readymadehost/laravel-dev-docker.git project-docker`
- `cd project-docker`
- `mkdir project` or `git clone <some_git_repo_url> project` for existing project
- `cp .env.sample .env` and review `.env` file
- `docker-compose build` only required if you edit `docker-compose.yml` to enable build
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

Mailcatcher service is included, can be accessed using URL and can be configured using smtp:-

```
smtp://mailcatcher:1025
```


## Mongodb support

Mongodb service is disabled by default. Check `.env` and `docker-compose.yml` for more info. Mongodb can be connected using compass:-

```
mongodb://root:root@localhost:27017/?authSource=admin
```


## Phpstorm setup

Simply add remote docker-compose php cli interpreter (exec with docker-compose.yml), change path mapping and configure remote interpreter for composer, phpunit, phpcs, phpcbf, phpmd and php-cs-fixer.


## Remote container extension + vscode

With vscode's remote container extension, we can simply connect into cli container.

## Pre build docker image

- `readymadehost/laravel-dev-docker-php{PHP_VERSION}-cli:latest`
- `readymadehost/laravel-dev-docker-php{PHP_VERSION}-fpm:latest`


## Quick Link

* Easy installation of PHP extensions in official PHP Docker images
    - https://github.com/mlocati/docker-php-extension-installer

* MailCatcher
    - https://github.com/sj26/mailcatcher

* ReadyMadeHost docker hub
    - https://hub.docker.com/orgs/readymadehost