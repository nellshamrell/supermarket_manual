# Chef Supermarket: A Guide

Supermarket is Chef's community cookbooks site.  It is a place for Chef community members to download community cookbooks, collaborate on cookbooks, and upload cookbooks to be used by other community members.  Supermarket is also intended to make it easier to participate in Chef's open source projects through Contributor License Agreements (CLA's).

[Supermarket Announcement Blog Post](https://www.chef.io/blog/2014/03/24/chef-supermarket-the-new-community-site/)

If you are going to contribute cookbooks to Supermarket, you will need to sign a CLA.  For more information on why Chef requires CLA's and how to sign one, please see [here](https://supermarket.chef.io/become-a-contributor).

There are two versions of Supermarket available today.

### Public Supermarket

This is available at the [Chef Supermarket site](https://supermarket.chef.io/).  This is an open source project, you can find and contribute to the repo [here](https://github.com/chef/supermarket).

### Omnibus Supermarket

There is also a version of Supermarket that can be run behind a firewall.  This guide will not cover the omnibus version of Supermarket, but many of the same principles will apply.  Stay tuned for an Ommibus Supermarket guide!

## Getting Started with Supermarket

There are a few things you will need to work with Supermarket.

### Knife

You will need Knife to interact with the Supermarket.

The easiest way to get Knife (along with many other tools needed to use both Supermarket and Chef) is through the [Chef Development Kit](https://downloads.chef.io/chef-dk/).

### Knife-Supermarket

Knife-Supermarket is a plugin for Knife that makes it easy to interact with Supermarket.

Make sure you have a [knife.rb](https://docs.chef.io/config_rb_knife.html) config file setup.

If you have the Chef Development Kit (ChefDK), you can install the plugin with:

```bash
  chef gem install knife-supermarket
```

Otherwise, you can also install a gem version of this plugin through:

```bash
  gem install knife-supermarket
```
You can also use Knife-Supermarket to switch between supermarkets if you are using a private Supermarket or multiple Supermarkets.  For more information, see (knife-supermarket)[https://github.com/cwebberOps/knife-supermarket].

This guide will take you through the basics of using Knife-Supermarket.  For more information on the various commands and options, please see the full [Knife-Supermarket documentation](https://docs.chef.io/plugin_knife_supermarket.html).

## Browsing the Supermarket

You can now take several actions to browse the community cookbooks available on the Supermarket site.

### List

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

### Search

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

### Show

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

## Downloading and Installing from the Supermarket

Ready to downlad and install a cookbook from the community site?

### Download

To download a cookbook as a tar.gz archive and place it in the current working directory, use the download command.

```bash
 $ knife supermarket download mysql
```

### Install

Installing a cookbook is similar to downloading it, but rather than saving the cookbook as a tar.gz, it extracts the cookbooks and sets up a git submodule so you can keep it up to date with the original cookbook.  See this [Stack Overflow](http://stackoverflow.com/a/15075143) for an excellent explanation.

```bash
 $ knife supermarket install mysql
```

NOTE: If you receive the error "ERROR: IOError: Cannot open or read /Users/nshamrell/chef-repo/cookbooks/mysql/metadata.rb", check which version of knife you are using with:

```bash
 $ knife -v
```

If it is lower than Chef: 12.0.2, you will need to update your version of Knife.  However, if you are using Chef DK and rvm, try running this command:

```bash
 $ rvm use system
```

Then retry

```bash
 $ knife supermarket install mysql
```

## Uploading to the Supermarket

Now let's upload a cookbook to the Supermarket.  If you have a cookbook of your own you would like to use, please do!  If you'd like some guidance in creating a very basic cookbook of you own to practice uploading to the Supermarket, see the "Creating a Cookbook" section at the end of this guide.

### Share

There are a few things you'll need in place before you can upload your cookbook to the Supermarket.
First, take a look at your knife.rb configuration file.  Mine lives at .chef/knife.rb.

You will need to have lines similar to this in the config file.  If you don't already have them, please add them in.

```bash
  node_name "nellshamrell" #Replace with the login name you use to login to the Supermarket.
  client_key "#{ENV['HOME']}/.chef/client.pem" #Define the path to wherever your client.pem file lives.  This is the key you generated when you signed up for a Chef account.
  cookbook_path [ '/Users/nshamrell/Projects/my_chef_repo/cookbooks' ] #Directory where the cookbook you're uploading resides.
```

Then use this command to upload the cookbook to the Supermarket!

```bash
  $ knife supermarket share "my_apache2_cookbook" "Web Servers"
```

Notice that I defined the Supermarket category my cookbook should be in - in this case, "Web Servers".  Other categories you can use are  "Databases", "Process Management", "Monitoring & Trending", "Programming Languages", "Package Management", "Applications", "Networking", "Operating Systems & Virtualization", "Utilities", or "Other".

### Unshare

Should you ever need to unshare a cookbook from the Supermarket, you can use the "unshare" command to do so.

```bash
  $ knife supermarket unshare my_apache2_cookbook
```

This will remove your cookbook from the Supermarket site.

And there you have it, the basics of using Chef Supermarket!  Happy cooking!




## Creating a Cookbook

Let's create a basic cookbook to upload to the Supermarket site.  This cookbook will install apache2 and show a custom home page.

(This assumes you have Chef DK installed)

## Creating a Chef Repo

To create a Chef repo, run this command:

```bash
  $ chef generate repo my_chef_repo
```
Then cd into that repo

```bash
  $ cd my_chef_repo
```

## Creating a Cookbook

Since this is a cookbook we're going to upload to the Supermarket site, let's check whether a cookbook already exists with that name on Supermarket.  I want to use the name "my_apache2_cookbook", so to check whether there's already a cookbook with that name on Supermarket I run:


```bash
  $ chef generate cookbook cookbooks/my_apache2_cookbook
```

If I get back a response that "The object you are looking for could not be found", that means that cookbook name is available on Supermarket.  For the rest of this tutorial, I'll use the cookbook name "my_apache2_cookbook".

Now create a cookbook within that repo.

```bash
  $ chef generate cookbook cookbooks/my_apache2_cookbook
```

## Creating a template

Next we'll create a template for our custom home page.

```bash
  $ chef generate template cookbooks/my_apache2_cookbook index.html
```

That will create a file called index.html.erb in the cookbooks/my_apache2_cookbooks/templates/default directory path.

Now open this file with your favorite text editor, I use vim here.

```bash
  $ vim cookbooks/my_apache2_cookbook/templates/default/index.html.erb
```

And enter in some HTML to be displayed.

```bash
<html>
  <body>
    <h1>Chef Love!</h1>
  </body>
</html>
```

Then save and close the file.

## Creating a recipe

Now open up the default recipe that was created when you generated the my_apache2_cookbook.

```bash
  $ vim cookbooks/my_apache2_cookbook/recipes/default.rb
```
And insert the following content:

```bash
  package 'apache2' # Installs the apache2 package

  service 'apache2' do
    action [:start, :enable] # Starts and enables the apache2 service on boot
  end

  template '/var/www/html/index.html' do
    source 'index.html.erb' # Defines a template for the default home page at /var/www/html/index.html
  end
```

And now we have a very basic cookbook we can upload to Supermarket!
