# apt puppet module #

Manages apt configuration under Debian or Ubuntu.

## Classes ##

  * apt
  * apt::clean-cache

### apt::clean-cache ###

Variables

*$apt_clean_minutes*: cronjob minutes - default uses ip_to_cron from module "common"
*$apt_clean_hours*:   cronjob hours - default to 0
*$apt_clean_mday*:    cronjob monthday - default uses ip_to_cron from module "common"

Require:

- module common (http://github.com/camptocamp/puppet-common)

## Definitions ##

  * apt::conf
  * apt::key
  * apt::sources_list

### apt::conf ##

apt::conf{"99unattended-upgrade":
  ensure  => present,
  content => "APT::Periodic::Unattended-Upgrade \"1\";\n",
}

### apt::key ###

apt::key {"A37E4CF5":
  source  => "http://dev.camptocamp.com/packages/debian/pub.key",
}

### apt::sources_list ###

apt::sources_list {"camptocamp":
  ensure  => present,
  content => "deb http://dev.camptocamp.com/packages/ etch puppet",
}