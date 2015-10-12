Vagrant.configure(2) do |config|
  config.vm.box = 'bento/centos-7.1'

  config.vm.hostname = 'riak'
  config.vm.network :private_network, ip: '192.168.33.10'

  config.vm.provider :virtualbox do |vb|
    vb.memory = '1024'
  end

  config.cache.scope = :box if Vagrant.has_plugin?('vagrant-cachier')

  config.vm.provision :shell, inline: 'nmcli connection reload;systemctl restart network.service'

  config.vm.provision :chef_solo do |chef|
    chef.cookbooks_path = %w(cookbooks site-cookbooks)

    chef.add_recipe 'java'
    chef.add_recipe 'datastore::riak'
    chef.json = {
      "java" => {
        "install_flavor" => "oracle",
        "jdk_version" => "7",
        "oracle" => {
          "accept_oracle_download_terms" => true
        }
      },
      "riak" => {
        "config" => {
          "nodename" => "riak@192.168.33.10"
        }
      }
    }
  end
end
