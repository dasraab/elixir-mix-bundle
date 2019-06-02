[![Build Status](https://travis-ci.org/iulyanp/elixir-mix-bundle.svg?branch=master)](https://travis-ci.org/iulyanp/elixir-mix-bundle)
[![Scrutinizer Code Quality](https://scrutinizer-ci.com/g/iulyanp/elixir-mix-bundle/badges/quality-score.png?b=master)](https://scrutinizer-ci.com/g/iulyanp/elixir-mix-bundle/?branch=master)

ElixirMixBundle
===================

> Note! Starting with Symfony 4 you can use the official webpack wrapper from Symfony: [Encore](https://symfony.com/doc/current/frontend/encore/installation.html)
I also wrote a short blog post about how you can [Compile your assets with Symfony Encore](https://iulyanp.github.io/symfony/2017/06/18/symfony-encore/).

ElixirMixBundle is a Symfony bundle that integrates [Laravel Mix](https://github.com/JeffreyWay/laravel-mix). 
The purpose of the bundle is to offer the `mix()` twig function. This is exactly the same `mix()` function from Laravel 
blade template system.

### Requirements

Before you start installing this bundle you first have to ensure that Node.js and NPM are installed on your machine. 

## Installation

### Step 1: Require the bundle with composer

Open your terminal and run one of the following commands to download the bundle into your vendor directory.

If you have composer installed globally you can run:
```
$ composer require iulyanp/elixir-mix-bundle
```
Else you can go with:
```
$ php composer.phar require iulyanp/elixir-mix-bundle
```

### Step 2: Register the bundle in your AppKernel class

Register the bundle in the app/AppKernel.php file of your project:

```
<?php
/** app/AppKernel.php */

class AppKernel extends Kernel
{
    public function registerBundles()
    {
        $bundles = array(

            new Iulyanp\ElixirMixBundle\IulyanpElixirMixBundle(),
        );
    }
}
```

### Step 3: Configure the bundle
In order to be able to use the bundle you have to give it some configuration specific to your application.

```
# config/parameters.yml
parameters:
    # ...
    web_dir: "%kernel.root_dir%/../web"

# config/config.yml
iulyanp_elixir_mix:
    web_dir: "%web_dir%"
```
The `web_dir` configuration is just the public path where you want the output for your assets to be saved. I used `web`
directory from Symfony.

### Step 4: Initialize larave-mix package
If you already have installed `Node.js`, `npm` you should be all set to run:

```
$ php bin/console mix:init
```

A base `package.json` and `webpack.mix.js` file will be generated into your project root directory.

Then run `npm install` to install all the dependencies and [laravel-mix](https://github.com/JeffreyWay/laravel-mix).

### Usage
Now you can use mix() function to version a file like this:
```
<link rel="stylesheet" type="text/css" href="{{ mix('css/app.css') }}" />
```
You can find more about laravel mix usage on the [official documentation](https://github.com/JeffreyWay/laravel-mix/tree/master/docs#summary)

### License
The ElixirMixBundle is open-sourced software licensed under the [MIT license](https://opensource.org/licenses/MIT).
