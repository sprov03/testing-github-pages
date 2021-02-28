---
layout: default
title: Installation
nav_order: 2
---

# Installation

## Requirements
* php > 7.0
* Laravel Framework 5.8+
* Composer

## Installing Akceli

``` sh
composer require akceli/laravel-code-generator
```

Publish the assets with the akceli publish command, it will configure your composer.json to load in the info it needs, publish Generators, Templates, and the `config/akceli.php`

``` sh
php artisan akceli:publish
```

## Bootstraping to use Akceli Conventions
This will move your Users model to the Models directory and modify the default seeder and user Factory
The seccond command will generate all of the supporting classes for the User Model
```shell script
php artisan akceli:generate bootstrap akceli
```

## Bootstraping Sanctum Api Auth
This will setup everything that needs to be setup for Sanctum to work with a fresh laravel install. For mature projects you can use bootstrap config as a Guide to complete the setup.
```shell script
php artisan akceli:generate boostrap sanctum-api
```

## Editor Issues
If you are using php storm, you will need to ignore a few directories in order to not get the multiple deffintion warning that it will yell about.
This is a flaw in PhpStrom Not fully following the same file completion that is sugested by the composer json autoloading.
The boostraping will copy files into place when needed.  This is what PhpStorm dose not like when analyzing files, but this is
not a problem with php, just the code analysis.
* /vendor/akceli/laravel-code-generator/publishable
* /akceli/bootstrap

