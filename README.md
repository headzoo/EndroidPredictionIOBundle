Endroid PredictionIO Bundle
===========================

*By [endroid](http://endroid.nl/)*

[![Build Status](https://secure.travis-ci.org/endroid/EndroidPredictionIOBundle.png)](http://travis-ci.org/endroid/EndroidPredictionIOBundle)
[![Latest Stable Version](https://poser.pugx.org/endroid/prediction-io-bundle/v/stable.png)](https://packagist.org/packages/endroid/prediction-io-bundle)
[![Total Downloads](https://poser.pugx.org/endroid/prediction-io-bundle/downloads.png)](https://packagist.org/packages/endroid/prediction-io-bundle)

...

[![knpbundles.com](http://knpbundles.com/endroid/EndroidPredictionIOBundle/badge-short)](http://knpbundles.com/endroid/EndroidPredictionIOBundle)

## Requirements

* Symfony
* Dependencies:
 * [`PredictionIO-PHP-SDK`](https://github.com/PredictionIO/PredictionIO-PHP-SDK)

## Installation

### Add in your composer.json

```js
{
    "require": {
        "endroid/prediction-io-bundle": "dev-master"
    }
}
```

### Install the bundle

``` bash
$ curl -s http://getcomposer.org/installer | php
$ php composer.phar update endroid/prediction-io-bundle
```

Composer will install the bundle to your project's `vendor/endroid` directory.

### Enable the bundle via the kernel

``` php
<?php
// app/AppKernel.php

public function registerBundles()
{
    $bundles = array(
        // ...
        new Endroid\Bundle\PredictionIOBundle\EndroidPredictionIOBundle(),
    );
}
```

## Configuration

### config.yml

```yaml
endroid_prediction_io:
    api_key: "Your API Key"
```

## Usage

After installation and configuration, the service can be directly referenced from within your controllers.

```php
<?php
public function recommendAction()
{
    $client = $this->get('endroid.prediction_io');

    // populate
    $client->createUser($userId);
    $client->createItem($itemId);
    $client->recordAction($userId, $itemId, 'view');

    // get recommendations and similar items
    $recommendations = $client->getRecommendations($userId, $engine, $count);
    $similarItems = $client->getSimilarItems($itemId, $engine, $count);
}
```

## Vagrant box

PredictionIO provides a [`Vagrant box`](http://docs.prediction.io/current/installation/install-predictionio-with-virtualbox-vagrant.html)
containing an out-of-the-box PredictionIO server.

## License

This bundle is under the MIT license. For the full copyright and license information, please view the LICENSE file that
was distributed with this source code.
