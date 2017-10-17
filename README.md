# govCMS (Drupal 8) distribution composer-based installer

## Installation

### Server Requirements

* Apache, Nginx, Microsoft IIS or any other web server with proper PHP support
* Supported PHP Version 7.1.*
* MySQL 5.5.3/MariaDB 5.5.20/Percona Server 5.5.8 or higher with PDO and an InnoDB-compatible primary storage engine
* PostgreSQL 9.1.2 or higher with PDO
* SQLite 3.7.11 or higher

**Dependencies**

* [Git](http://git-scm.com/)
* [Composer](https://getcomposer.org/)

### Installing govCMS

govCMS Drupal 8 utilizes [Composer](https://getcomposer.org/) to manage its dependencies. So, before using govCMS, make sure you have Composer installed on your machine.

For a better composer performance, we recommend

```
composer global require "hirak/prestissimo:^0.3"
```

#### Via Composer Create-Project

```
composer create-project --stability dev --no-interaction govcms/govcms8 MY_PROJECT
```

Composer will create a new directory called MY_PROJECT containing a docroot directory with a full govCMS code base therein.

> * A higher memory limit, for example 2048MB, may be required for PHP command line interface (CLI) to create the project successfully: ```php -i | grep "memory_limit"```
> * Please be sure the web server and composer use the same PHP version to avoid issues when installing the website:  
> ```php -v```

And you can update govCMS Distribution via (noting that at this stage, updating this way may break some of the dependencies within the distribution, and is generally not recommended unless you know what you're doing!)
```
cd MY_PROJECT
composer update
```
