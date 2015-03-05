Now let's upload a cookbook to the Supermarket.  If you have a cookbook of your own you would like to use, please do!  If you'd like some guidance in creating a very basic cookbook of you own to practice uploading to the Supermarket, see [INSERT LINK HERE].

## Share

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

## Unshare

Should you ever need to unshare a cookbook from the Supermarket, you can use the "unshare" command to do so.

```bash
  $ knife supermarket unshare my_apache2_cookbook
```

This will remove your cookbook from the Supermarket site.
