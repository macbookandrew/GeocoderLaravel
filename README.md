Geocoder for Lavarel 4
======================

This package allows you to use [**Geocoder**](http://geocoder-php.org/Geocoder/)
in [**Laravel 4**](http://laravel.com/).

[![Latest Stable Version](https://poser.pugx.org/toin0u/geocoder-laravel/v/stable.png)](https://packagist.org/packages/toin0u/geocoder-laravel)
[![Total Downloads](https://poser.pugx.org/toin0u/geocoder-laravel/downloads.png)](https://packagist.org/packages/toin0u/geocoder-laravel)
[![Build Status](https://secure.travis-ci.org/geocoder-php/GeocoderLaravel.png)](http://travis-ci.org/geocoder-php/GeocoderLaravel)
[![Coverage Status](https://coveralls.io/repos/geocoder-php/GeocoderLaravel/badge.png)](https://coveralls.io/r/geocoder-php/GeocoderLaravel)


Installation
------------

It can be found on [Packagist](https://packagist.org/packages/toin0u/geocoder-laravel).
The recommended way is through [composer](http://getcomposer.org).

Edit `compose.json` and add:

```json
{
    "require": {
        "toin0u/geocoder-laravel": "~0.1"
    }
}
```

And install dependencies:

```bash
$ curl -sS https://getcomposer.org/installer | php
$ php composer.phar install
```


Usage
-----

Find the `providers` key in `app/config/app.php` and register the **Geocoder Service Provider**.

```php
'providers' => array(
    // ...

    'Toin0u\Geocoder\GeocoderServiceProvider',
)
```

Find the `aliases` key in `app/config/app.php` and register the **Geocoder Facade**.

```php
'aliases' => array(
    // ...

    'Geocoder' => 'Toin0u\Geocoder\GeocoderFacade',
)
```

Configuration
-------------

The service provider creates the following services:

    * `geocoder`: the Geocoder instance.
    * `geocoder.provider`: the provider used by Geocoder.
    * `geocoder.adapter`: the HTTP adapter used to get data from remotes APIs.

By default, the `geocoder.provider` service uses FreeGeoIP and the `geocoder.adapter` service uses the cURL adapter.
Override these services to use the adapter/provider you want.

See [the Geocoder documentation](http://geocoder-php.org/Geocoder/) for a list of available adapters and providers.


Example with Facade
-------------------

```php
<?php

// ...
try {
    $geocode = Geocoder::geocode('10 rue Gambetta, Paris, France');
    // ...
} catch (\Exception $e) {
    // Here we will get "The FreeGeoIpProvider does not support Street addresses." ;)
    echo $e->getMessage();
}
```


Changelog
---------

[See the changelog file](https://github.com/toin0u/Geocoder-laravel/blob/master/CHANGELOG.md)


Support
-------

[Please open an issues in github](https://github.com/toin0u/Geocoder-laravel/issues)


License
-------

Geocoder-laravel is released under the MIT License. See the bundled
[LICENSE](https://github.com/toin0u/Geocoder-laravel/blob/master/LICENSE) file for details.
