# GovCMS8 Composer Project Installer
<img src="https://www.drupal.org/files/styles/grid-3/public/project-images/govcms8.png" alt="GovCMS8 logo" align="right"/>

[![Build Status](https://travis-ci.org/govCMS/GovCMS8-project.svg?branch=1.x)](https://travis-ci.org/govCMS/GovCMS8-project)

GovCMS8 is the Drupal 8-specific version of the GovCMS distribution.

[GovCMS](https://www.govcms.gov.au) is an open source web content management and hosting service, based on Drupal and developed to help agencies create modern, affordable and responsive websites, whilst making it easier to collaborate and innovate. GovCMS also helps reduce the technology and compliance burden on government agencies.  GovCMS is mananged by the Australian Government Department of Finance.

## Installation

This repository is for inclusion as part of a composer create-project installation only.

Complete installation instructions are available at the main GovCMS8 repository https://github.com/GovCMS/GovCMS8

### Troubleshooting

If you're unable to get started, please try the following before getting `composer update` to work:
* `composer require symfony/event-dispatcher:"4.3.11 as 3.4.41"`

### Quick Start

Composer will create a new directory called MY_PROJECT containing a docroot directory with a full GovCMS code base therein.

    composer create-project govcms/govcms8-project MY_PROJECT
