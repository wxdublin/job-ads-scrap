# Juju Jobs Client

[![Latest Version](https://img.shields.io/github/release/jobapis/jobs-juju.svg?style=flat-square)](https://github.com/jobapis/jobs-juju/releases)
[![Software License](https://img.shields.io/badge/license-APACHE%202.0-brightgreen.svg?style=flat-square)](LICENSE.md)
[![Build Status](https://img.shields.io/travis/jobapis/jobs-juju/master.svg?style=flat-square&1)](https://travis-ci.org/jobapis/jobs-juju)
[![Coverage Status](https://img.shields.io/scrutinizer/coverage/g/jobapis/jobs-juju.svg?style=flat-square)](https://scrutinizer-ci.com/g/jobapis/jobs-juju/code-structure)
[![Quality Score](https://img.shields.io/scrutinizer/g/jobapis/jobs-juju.svg?style=flat-square)](https://scrutinizer-ci.com/g/jobapis/jobs-juju)
[![Total Downloads](https://img.shields.io/packagist/dt/jobapis/jobs-juju.svg?style=flat-square)](https://packagist.org/packages/jobapis/jobs-juju)

This package provides [Juju Jobs API](http://www.juju.com/publisher/spec/)
support for the [Jobs Common](https://github.com/jobapis/jobs-common) project.

## Installation

To install, use composer:

```
composer require jobapis/jobs-juju
```

## Usage

Create a Query object and add all the parameters you'd like via the constructor.
 
```php
// Add parameters to the query via the constructor
$query = new JobApis\Jobs\Client\Queries\JujuQuery([
    'partnerid' => YOUR_PARTNER_ID
]);
```

Or via the "set" method. All of the parameters documented in Indeed's documentation can be added.

```php
// Add parameters via the set() method
$query->set('k', 'engineering');
```

You can even chain them if you'd like.

```php
// Add parameters via the set() method
$query->set('l', 'Chicago, IL')
    ->set('highlight', '1');
```
 
Then inject the query object into the provider.

```php
// Instantiating an IndeedProvider with a query object
$client = new JobApis\Jobs\Client\Provider\JujuProvider($query);
```

And call the "getJobs" method to retrieve results.

```php
// Get a Collection of Jobs
$jobs = $client->getJobs();
```

The `getJobs` method will return a [Collection](https://github.com/jobapis/jobs-common/blob/master/src/Collection.php) of [Job](https://github.com/jobapis/jobs-common/blob/master/src/Job.php) objects.

## Testing

``` bash
$ ./vendor/bin/phpunit
```

## Contributing

Please see [CONTRIBUTING](https://github.com/jobapis/jobs-juju/blob/master/CONTRIBUTING.md) for details.

## Credits

- [Karl Hughes](https://github.com/karllhughes)
- [Steven Maguire](https://github.com/stevenmaguire)
- [All Contributors](https://github.com/jobapis/jobs-juju/contributors)

## License

The Apache 2.0. Please see [License File](https://github.com/jobapis/jobs-juju/blob/master/LICENSE) for more information.
