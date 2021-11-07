<!-- markdownlint-disable no-inline-html -->
<p align="center">
  <br><br>
  <img src="https://leafphp.netlify.app/assets/img/leaf3-logo.png" height="100"/>
  <h1 align="center">Leaf Anchor CSRF [BETA]</h1>
  <br><br>
</p>

# Leaf PHP

[![Latest Stable Version](https://poser.pugx.org/leafs/csrf/v/stable)](https://packagist.org/packages/leafs/csrf)
[![Total Downloads](https://poser.pugx.org/leafs/csrf/downloads)](https://packagist.org/packages/leafs/csrf)
[![License](https://poser.pugx.org/leafs/csrf/license)](https://packagist.org/packages/leafs/csrf)

> This is an experimental module. Please open an issue if you notice any bugs or malfunctions.

This package is leaf's implementation of CSRF default protection with leaf anchor. It comes separated from leaf anchor because it is not needed in every project you may build.

## Installation

You can easily install Leaf CSRF using [Composer](https://getcomposer.org/).

```bash
composer require leafs/csrf
```

## Basic Usage

After installing leaf CSRF, leaf automatically loads the CSRF package for you, so you don't need to do anything unless you want to configure the CSRF module to match your application requirements.

### Using CSRF outside of leaf

Most leaf modules can be used outside of leaf. This module is one of these global modules. If you decide to use the CSRF module outside of leaf, you will need to manually initialize the package.

```php
Leaf\Anchor\CSRF::init();
```

This function generates a token with a secret and a random hash and saves that in a session. If no session exists, the CSRF module will create a session for your app and save the token in that session,

### Config

Just like every other leaf module, this module also allows you to customize it to behave in any way you want it to behave. Also, since this module is built on the Anchor module, the config object is shared with Anchor. To set any configuration, simply call the `config` method.

**Available config:**

- **SECRET_KEY** - This is the key with which the token is saved and used in your leaf app. If this is not specified, leaf uses the name `_token` as done in other frameworks like Laravel.

- **SECRET** - This is the secret key used to encrypt the token. Leaf also has a default secret key set for you. Note that the secret key is attached to a set of unique numbers that not even leaf knows.

- **EXCEPT** - This is an array of routes that you want to exclude from the CSRF protection.

- **METHODS** - This is an array of HTTP methods to apply CSRF protection to. By default, leaf uses `["POST", "PUT", "PATCH", "DELETE"]`

```php
use Leaf\Anchor\CSRF;

CSRF::config([
  "METHODS" => ["GET"],
  "EXCEPT" => ["/"],
]);
```

Built with ❤ by [**Mychi Darko**](https://mychi.netlify.app)
