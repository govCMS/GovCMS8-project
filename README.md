# govCMS (Drupal 8)

## Installation

### Server Requirements

* Apache, Nginx, Microsoft IIS or any other web server with proper PHP support
* PHP 5.5.9 or higher
* MySQL 5.5.3/MariaDB 5.5.20/Percona Server 5.5.8 or higher with PDO and an InnoDB-compatible primary storage engine
* PostgreSQL 9.1.2 or higher with PDO
* SQLite 3.7.11 or higher

**Dependencies**

* [Git](http://git-scm.com/)
* [Composer](https://getcomposer.org/)
* [Node](https://nodejs.org/en/), which includes the NPM package manager

### Installing govCMS

govCMS Drupal 8 utilizes [Composer](https://getcomposer.org/) to manage its dependencies. So, before using govCMS, make sure you have Composer installed on your machine.

For a better performance, we recommend 

```
composer global require "hirak/prestissimo:^0.3"
```

#### Via Composer Create-Project

```
composer create-project --stability dev --prefer-dist govcms/govcms-project MY_PROJECT
```

Composer will create a new directory called MY_PROJECT containing a docroot directory with a full govCMS code base therein. 

```
cd MY_PROJECT
composer update
```

And you can update govCMS Distribution Core via
```
composer update govcms/govcms
```

#### Packaged installation

govCMS exists as packaged versions on both the [Github](https://github.com/govCMS/govCMS) and [Drupal.org](https://www.drupal.org/project/govcms) project pages. These compressed archives are available in both zip and tar.gz format to download and use as needed.

This is no longer the recommended method and will likely be deprecated in the future.

#### Installation from source

To develop on or patch against govCMS, the source files should be downloaded and the project built.

govCMS source may be downloaded using git

```
git clone -b 8.3.x git@github.com:govCMS/govCMS.git
```

## Development with BLT

### Local Development

No matter what local environment you choose to use, the following guidelines should be followed:

* In order to guarantee similar behavior, use Apache as your web server.
* The blt alias must be installed.
* MySQL must use mysql://drupal:drupal@localhost/drupal:3306
* Your LAMP stack must have host entry for http://local.govcms.com/ pointing to docroot
* PHP memory limit >= 2G (required by blt)

1. Enter the project root, and run the following commands in order (Run once):

```
cd MY_PROJECT
composer run-script blt-alias
source ~/.bash_profile
```

2. Update/Create local.alias.drushrc.php in drush/site-aliases

```
<?php

// Local alias.
$aliases['govcms.local'] = array(
    'root' => '/var/www/MY_PROJECT/docroot',
    'uri' => 'http://local.govcms.com',
);
```

3. Build local govCMS instance

Please make sure your host entry and MySQL database meet the above requirements.

```
blt local:setup
```

4. Visit local govCMS instance
```
http://local.govcms.com/
```

5. Sign into govCMS instance as Admin
```
drush @govcms.local uli
```

6. If you'd like to execute Behat tests from the host machine, you will need Java:
```
brew cask install java
brew install chromedriver
```

### Using Drupal VM for local development

1. Download the Drupal VM dependencies listed in [Drupal VM's README](https://github.com/geerlingguy/drupal-vm#quick-start-guide). If you're running [Homebrew](https://brew.sh/index.html) on Mac OSX, this is as simple as:

```
brew tap caskroom/cask
brew install php56 git composer ansible drush
brew cask install virtualbox vagrant
```

2. Enter the project root, and run the following commands in order (Run once):

```
cd MY_PROJECT
composer run-script blt-alias
source ~/.bash_profile
```

3. Customize example.project.local.yml to project.local.yml and run the following to build.

```
blt vm
blt local:setup
```

4. Visit local govCMS instance
```
http://local.govcms.com/
```

5. Sign into  govCMS instance as Admin
```
drush @govcms.local uli
```

6. Drupal VM Dashboard 
```
http://dashboard.local.govcms.com/
```

## Structure

### General

- **docroot** - The Drupal root. This can be either a directory or a symlink.
- **README.md** - Project documentation written in markdown.
- **blt** - Build tools.
- **composer.json** - Project specific vendor packages and repositories.
- **composer.lock** - Locked in version of vendor packages. To ensure consistency across the project.
- **.gitignore** - A list of files to be ignored by git. This is typically used for excluding local development modules and may create files to ignore that an IDE creates.

## Patching govCMS

Because govCMS is a [Drupal distribution](https://www.drupal.org/documentation/build/distributions), modules and configurations are not added directly to the codebase. Rather, they are referenced within the composer.json file.

Any alterations to Drupal core or contributed modules must have an associated [drupal.org](https://www.drupal.org) issue filed against the project in question. Modifications should be made directly to the project in question and patched into govCMS rather than made directly against govCMS.

It is a requirement for any patches to govCMS to pass all automated testing prior to manual review. The automated testing checks for PHP syntax, coding standards, build completion and runs behavioural tests. It is also desirable that additions to the codebase add behat tests to ensure no regressions occur once committed.

To submit a patch, the govCMS project should be forked and changes applied to a branch on the forked repository. Once all changes are applied, a pull request between govCMS/master and the branch of the fork may be created.


## Contributing to govCMS

All contributions to govCMS are welcome. Issues and pull requests may be submitted against the govCMS project on github where they will be addressed by the govCMS team.
