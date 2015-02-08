# vagrant-riak

# Requirements

* [Oracle VM VirtualBox](https://www.virtualbox.org)
* [Vagrant](http://www.vagrantup.com)

# Usage

    $ vagrant plugin install vagrant-cachier
    $ vagrant plugin install vagrant-omnibus
    $ git clone git@github.com:holidayworking/vagrant-riak.git
    $ cd vagrant-riak
    $ bundle install --path vendor/bundle --binstubs=vendor/bin
    $ bundle exec berks vendor cookbooks
    $ vagrant up

# Author

Author:: Hidekazu Tanaka (<hidekazu.tanaka@gmail.com>)