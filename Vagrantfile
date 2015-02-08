Vagrant.configure(2) do |config|
  config.vm.box = 'chef/centos-7.0'

  config.vm.hostname = 'riak'
  config.vm.network :private_network, ip: '192.168.33.10'

  config.vm.provider :virtualbox do |vb|
    vb.memory = '1024'
  end

  config.cache.scope = :box if Vagrant.has_plugin?('vagrant-cachier')

  config.omnibus.chef_version = '11.18.0'
  config.vm.provision :chef_solo do |chef|
    chef.cookbooks_path = %w(cookbooks site-cookbooks)

    chef.add_recipe 'datastore::riak'
    chef.json = {
      'riak' => {
        'config' => {
          'nodename' => 'riak@192.168.33.10'
        }
      }
    }
  end
end
