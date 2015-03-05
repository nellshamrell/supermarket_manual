You can now take several actions to browse the community cookbooks available on the Supermarket site.

## List

To see a list of all community cookbooks available from Supermarket, run the following:


```bash
 $ knife supermarket list
```

This will return lots of output similar to:


```bash
  1password                            minecraft
  301                                  mineos
  7-zip                                minidlna
  AWS_see_spots_run                    minitest
  AmazonEC2Tag                         minitest-handler
  Appfirst-Cookbook                    mirage
  CVE-2014-3566-poodle                 mlocate
  CVE-2015-0235                        mod_security
  Obfsproxy                            mod_security2
  R                                    modcloth-hubot
  Rstats                               modcloth-nad
  SysinternalsBginfo                   modman
  VRTSralus                            modules
  abiquo                               mogilefs
  acadock                              mongodb
  accel-ppp                            mongodb-10gen
  accounts                             mongodb-agents
  accumulator                          monit
  [etc]
```

## Search

Looking for a particular cookbook?  The most downloaded cookbook as of February 2015 is the mysql cookbook.  If I wanted to search for this cookbook I would use a command similar to this:

```bash
 $ knife supermarket search mysql
```

Which will return output similar to this:

```bash
  mysql:
    cookbook:             http://cookbooks.opscode.com/api/v1/cookbooks/mysql
    cookbook_description: Provides mysql_service, mysql_config, and mysql_client resources
    cookbook_maintainer:  chef
    cookbook_name:        mysql
  mysql-apt-config:
    cookbook:             http://cookbooks.opscode.com/api/v1/cookbooks/mysql-apt-config
    cookbook_description: Installs/Configures mysql-apt-config
    cookbook_maintainer:  tata
    cookbook_name:        mysql-apt-config
  mysql-multi:
    cookbook:             http://cookbooks.opscode.com/api/v1/cookbooks/mysql-multi
    cookbook_description: MySQL replication wrapper cookbook
    cookbook_maintainer:  rackops
    cookbook_name:        mysql-multi
```

Let's take a closer look at that first mysql cookbook.

## Show

To view more information about a particular cookbook, run the following:

```bash
 $ knife supermarket show mysql
```

Which will return input similar to this:

```bash
  average_rating:
  category:           Other
  created_at:         2009-10-28T19:16:54.000Z
  deprecated:         false
  description:        Provides mysql_service, mysql_config, and mysql_client resources
  external_url:       http://github.com/opscode-cookbooks/mysql
  foodcritic_failure: true
  issues_url:
  latest_version:     http://cookbooks.opscode.com/api/v1/cookbooks/mysql/versions/6.0.15
  maintainer:         chef
  metrics:
    downloads:
      total:    79275449
    versions:
      0.10.0: 927561
      0.15.0: 927536
      0.20.0: 927321
      0.21.0: 927298
      0.21.1: 927311
      0.21.2: 927424
      0.21.3: 927441
      0.21.5: 927326
      0.22.0: 927297
      0.23.0: 927353
      0.23.1: 927862
      0.24.0: 927316
```

If you want to take a look at a specific version of a cookbook, include it in the command like this:

```bash
 $ knife supermarket show mysql 0.10.0
```

Which will return output similar to:

```bash
  average_rating:
  cookbook:          http://cookbooks.opscode.com/api/v1/cookbooks/mysql
  file:              http://cookbooks.opscode.com/api/v1/cookbooks/mysql/versions/0.10.0/download
  license:           Apache 2.0
  tarball_file_size: 7010
  version:           0.10.0
```
