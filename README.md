# Currency for Laravel

This provides Laravel with currency functions such as currency formatting and conversion using up-to-date exchange rates.

- [Currency on Packagist](https://packagist.org/packages/mkraha/laravel-currency-converter)
- [Currency on GitHub](https://github.com/mkraha/LaravelCurrencyConverter)

### Composer

From the command line run:

```bash
$ composer require mkraha/laravel-currency-converter
```

### Laravel's >=5.5 Auto-Discovery

Simply install the package and let Laravel do its magic.

### Manual Setup

Once installed you need to register the service provider with the application. Open up `config/app.php` and find the `providers` key.

```php
'providers' => [

    \Raha\Currency\CurrencyServiceProvider::class,

]
```

This package also comes with a facade, which provides an easy way to call the the class. Open up `config/app.php` and find the `aliases` key.

```php
'aliases' => [

    'Currency' => \Raha\Currency\Facades\Currency::class,

];
```

### Publish the configurations

Run this on the command line from the root of your project:

```bash
php artisan vendor:publish --provider="Raha\Currency\CurrencyServiceProvider" --tag=config
```

A configuration file will be published to `config/currency.php`.

### Migration

If currencies are going to be stored in the database. Run migrate to setup the database table [see [Storage Drivers](/projects/laravel-currency/doc/storage-drivers.html)].

```bash
php artisan vendor:publish --provider="Raha\Currency\CurrencyServiceProvider" --tag=migrations
```

Run this on the command line from the root of your project to generate the table for storing currencies:

```bash
$ php artisan migrate
```

### Preset Currencies

The package comes with a set of preset currencies. To add them use the [artisan manage command](/projects/laravel-currency/doc/commands.html).

### Middleware

Once installed you need to append the middleware class within the Http kernel. This allows visitors to change the viewed currency using the query parameter `?currency=usd`.

Open up `app/Http/Kernel.php` and find the `$middleware` variable.

```php
protected $middleware = [

    \Raha\Currency\Middleware\CurrencyMiddleware::class,

]
```

> **Note:** The currency middleware uses the session to store the user selected currency, because of this the middleware will need to be added somewhere after `\Illuminate\Session\Middleware\StartSession::class`.

## Official Author Documentation

Documentation for the package can be found on [Lyften.com](http://lyften.com/projects/laravel-currency/).

## Change Log

[https://github.com/mkraha/LaravelCurrencyConverter/releases](https://github.com/mkraha/LaravelCurrencyConverter/releases)
