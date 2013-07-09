#Rails Ready
###Ruby 1.9.3 and Rails setup script for Linux and OSX
###Distros supported:
 * Ubuntu 10.04 LTS, 10.10 and 11.04
 * CentOS 5 (utilizes the Fedora EPEL repo)
 * OSX (requires XCode to be installed)

# 
###Run this on a fresh install. It WILL update your system!

###To run:
####Linux
  * `wget --no-check-certificate https://raw.github.com/johnrlive/railsready/master/railsready.sh && bash railsready.sh`

####OSX
  * `curl -O https://raw.github.com/johnrlive/railsready/master/railsready.sh && bash railsready.sh`

The script will ask if you want to build Ruby from source or install RVM

###What this gives you:
  * An updated system (Linux only)
  * Homebrew (OSX only)
  * Ruby 1.9.3 latest patch level (installed to /usr/local/bin/ruby) or RVM running 1.9.3 latest patch level
  * Imagemagick
  * libs needed to run Rails (sqlite, mysql, etc)
  * Bundler, Passenger, and Rails gems
  * Git

Please note: If you are running on a super slow connection your sudo session may timeout and you'll have to enter your password again. If you're running this on an EC2 or RS instance it shouldn't be problem.

Just install either NGINX or Apache, run passenger-install-nginx-module or passenger-install-apache-module, upload your app, point your vhost config to your apps public dir and go!

A note about RVM+passenger+nginx:
Passenger installed via RVM can't locate the OpenSSL package installed on Ubuntu. A user contributed fix is as follows:

````
rvm remove 1.9.3
rvm pkg install openssl
rvm install 1.9.3 --with-openssl-dir=$HOME/.rvm/usr
rvmsudo passenger-install-nginx-module
````

# 
####Rails Ready now supports a "plugin" type system. The distro is detected and a corresponding "recipe" file is pulled down to run the distro specific setup steps. Check the recipes dir to see if your distro is supported. If you would like to add support for a system fork the repo, write a recipe, and submit a pull request. Take a look at recipes/ubuntu.sh for an idea of what to model your recipe after.

If you use this or have any suggestions let me know joshfng@gmail.com or @joshfng on Twitter
