# A Pest plugin to add Laravel specific expectations

[![Latest Version on Packagist](https://img.shields.io/packagist/v/defstudio/pest-plugin-laravel-expectations.svg?style=flat-square)](https://packagist.org/packages/defstudio/pest-plugin-laravel-expectations)
[![GitHub Tests Action Status](https://img.shields.io/github/workflow/status/def-studio/pest-plugin-laravel-expectations/Run%20Tests?label=tests)](https://github.com/def-studio/pest-plugin-laravel-expectations/actions?query=workflow%3A"Run+Tests"+branch%3Amain)
[![GitHub Code Style Action Status](https://img.shields.io/github/workflow/status/def-studio/pest-plugin-laravel-expectations/Static%20Analysis?label=code%20style)](https://github.com/def-studio/pest-plugin-laravel-expectations/actions?query=workflow%3A"Static+Analysis"+branch%3Amain)
[![Total Downloads](https://img.shields.io/packagist/dt/defstudio/pest-plugin-laravel-expectations.svg?style=flat-square)](https://packagist.org/packages/defstudio/pest-plugin-laravel-expectations)
[![License](https://img.shields.io/packagist/l/defstudio/pest-plugin-laravel-expectations)](https://packagist.org/packages/defstudio/pest-plugin-laravel-expectations)

This [Pest](https://pestphp.com) plugin adds Laravel specific expectations to the testing ecosystem

```php
it('can check model exists', function(){
  $user = User::factory()->create();
  
  expect($user)->toExist();
});
```

## Installation

You can install the package via composer:

```bash
composer require --dev defstudio/pest-plugin-laravel-expectations
```

## Usage

The expectations added by this plugin are authomatically loaded into Pest's expectation system. They can be used along other expectations.

## Authentication Expectations

### `toBeAuthenticated()`

Assert that the given User is authenticated

```php
expect($user)->toBeAuthenticated();
 ```

### `toBeValidCredentials()`

Assert that the given credentials are valid.

```php
expect(['email' => 'test@email.it', 'password' => 'foo'])->toBeValidCredentials();
 ```

### `toBeInvalidCredentials()`

Assert that the given credentials are invalid.

```php
expect(['email' => 'test@email.it', 'password' => 'wrongpassword'])->toBeInvalidCredentials();
 ```


## Collections Expectations


### `toBeCollection()`

Assert that the value is an instance of \Illuminate\Support\Collection

```php
expect(collect[1,2,3])->toBeCollection();
 ```

### `toBeEloquentCollection()`

Assert that the value is an instance of \Illuminate\Database\Eloquent\Collection

```php
expect(User::all())->toBeCollection();
 ```


## Models Expectations

### `toBeDeleted()`

Assert the given model to be deleted.

```php
expect($model)->toBeDeleted();
 ```

### `toBeSoftDeleted()`

Assert the given model to be soft deleted.

```php
expect($model)->toBeSoftDeleted();
 ```

### `toExist()`

Assert the given model exists in the database.

```php
expect($model)->toExist();
 ```

### `toBelongTo()`

Assert the given model belongs to another one.

```php
expect($post)->toBelongTo($user);
 ```


## Database Expectations

### `toBeInDatabase()`

Assert that the given _where condition_ exists in the database

```php
expect(['name' => 'Fabio'])->toBeInDatabase(table: 'users');
 ```


## Tests

Run all tests:
```bash
composer test
```

Check types:
```bash
composer test:types
```

Unit tests:
```bash
composer test:unit
```

## Changelog

Please see [CHANGELOG](CHANGELOG.md) for more information on what has changed recently.

## Contributing

Please see [CONTRIBUTING](CONTRIBUTING.md) for details.

## Security Vulnerabilities

Please review [our security policy](../../security/policy) on how to report security vulnerabilities.

## License

The MIT License (MIT). Please see [License File](LICENSE.md) for more information.
