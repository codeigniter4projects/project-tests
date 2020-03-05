# DEPRECATED

Note: This repo is deprecated as of the official release of CodeIgniter 4. Functionality,
examples, and relevant docs have been merged into the main repo. See (for example):
* <https://github.com/codeigniter4/CodeIgniter4/tree/develop/admin/starter/tests>

Existing projects should upgrade by merging the AppStarter **tests** folder.

# ProjectTests

PHPUnit testing scaffold for CodeIgniter 4 projects

## Overview

Not a module itself but a testing scaffold for CodeIgniter 4 projects,
**ProjectTests** makes it easy to setup PHPUnit tests in your projects.

To read more on Unit Testing in CodeIgniter 4 visit the
[User Guide](https://codeigniter4.github.io/userguide/testing/index.html).

## Installation

Clone or download this repo and place **src/tests** and **src/phpunit.xml.dist** in your
project root. Add the following lines to **composer.json**:
```
	"repositories": [
		{
			"type": "vcs",
			"url": "https://github.com/codeigniter4/CodeIgniter4"
		}
	],
	"minimum-stability": "dev",
	"require-dev": {
		"phpunit/phpunit" : "^7.0",
		"mockery/mockery": "^1.0",
		"codeigniter4/codeigniter4": "dev-develop"
	},
	"autoload-dev": {
		"psr-4": {
			"ProjectTests\\Support\\": "tests/_support"
		}
	},
	"scripts": {
		"test": "phpunit",
		"post-update-cmd": [
			"composer dump-autoload"
		]
	}
```

If you are using version tracking you should exclude test results by adding this to
**.gitignore**:
```
vendor/
build/
phpunit*.xml
phpunit
composer.lock
```

Examples of **composer.json** and **.gitignore** are located in the [examples/](examples/)
folder if you need a starting point.

### Paths

A number of framework and testing path are defined as constants during the
[bootstrap process](src/tests/_support/bootstrap.php). These default to the assumed locations
if you have a standard directory structure and you installed the framework via Composer.
If you move directories around or do no use Composer you will need to review these paths
and set them appropriately.

* **APPPATH**: `$paths->appDirectory`
* **ROOTPATH**: `APPPATH . '../'`
* **FCPATH**: `ROOTPATH . 'public/'`
* **WRITEPATH**: `$paths->writableDirectory`
* **SYSTEMPATH**: `$paths->systemDirectory`
* **CIPATH**: `SYSTEMPATH . '../`
* **SUPPORTPATH**: `CIPATH . 'tests/_support/`
* **PROJECTSUPPORTPATH**: *bootstrap.php directory*
* **TESTPATH**: `PROJECTSUPPORTPATH . '../`

## Updating

As this repo is updated with bugfixes and improvements you will want to update your
projects that use it. Because files need to be copied in place manually you will have to
handle updates manually by cloning or downloading this repo and merging changed files
into your project. "Watch" this repo to be notified of new releases and changes.

## Creating Tests

See the docs on [Creating Tests](docs/CREATING.md).

## Running Tests

From your package root run `composer install` (or `composer upgrade`) to install all the
required support packages, then run `composer test` to initiate the tests. Test results
and code coverage will be written to standard output and formatted log versions will go
in **build/logs/**.

## Code Coverage

See the docs on [Code Coverage](docs/COVERAGE.md).

## Module Testing

**ProjectTests** is designed to be added to applications using CodeIgniter 4 as their core
framework. If you are looking for a testing scaffold for your modular library intended to
be included into other project, check out
[Codeigniter4Projects/ModuleTests](https://github.com/codeigniter4projects/module-tests).
