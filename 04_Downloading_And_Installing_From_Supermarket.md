Ready to downlad and install a cookbook from the community site?

## Download

To download a cookbook as a tar.gz archive and place it in the current working directory, use the download command.

```bash
 $ knife cookbook site download mysql
```

## Install

Installing a cookbook is similar to downloading it, but rather than saving the cookbook as a tar.gz, it extracts the cookbooks and sets up a git submodule so you can keep it up to date with the original cookbook.  See this [Stack Overflow](http://stackoverflow.com/a/15075143) for an excellent explanation.

```bash
 $ knife cookbook site install mysql
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
 $ knife cookbook site install mysql
```
