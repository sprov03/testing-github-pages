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

Once you have purchased an Akceli licence, you will be given an access token to a private repository that is configured for you.
You will then use the access token to view the composer package.

::: tip Akceli Licence
You will need to purchase an Akceli Licence if you have not already done so.
[https://akceli.io](https://akceli.io)
:::

Add the following to your `composer.json` to register the akceli repository
``` json  composer.json
    "repositories": [
        {
            "type": "composer",
            "url": "https://packages.akceli.io"
        }
    ]
```

require the package into your project: You will be prompted for username and password to authorize with the repository,
it will be the username and password used to purchase the licence.

``` sh
composer require akceli/laravel-code-generator
```
Publish the assets with the akceli pubish command, it will configure your composer.json to load in the info it needs, publish Generators, Templates, and the `config/akceli.php`

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


## Authorizing Akceli in Continuous Integration (CI) Environments

::: tip
Make Sure this is ran before you run composer install
:::

``` sh
composer config --auth http-basic.packages.akceli.io {Your Email} {Your Password}
```

## Authorizing Akceli in Chipper CI

I use Chipper CI for all of my laravel projects.  To authorize Akceli with Chipper CI, simply add akceli to the packages for your project.
[https://chipperci.com/](https://chipperci.com/)

* Repository Url: https://packages.akceli.io
* UserName: Your email
* passowrd: Your password


