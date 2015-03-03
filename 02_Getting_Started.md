## Knife

You will need Knife to interact with the Supermarket.

The easiest way to get Knife (along with many other tools needed to use both Supermarket and Chef) is through the [Chef Development Kit](https://downloads.chef.io/chef-dk/).

## Knife-Supermarket

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

## Stove

[Stove](https://github.com/sethvargo/stove) is an alternative to knife that can also be used to interact with Chef Supermarket.  For more information, please see the [project page](https://github.com/sethvargo/stove)
