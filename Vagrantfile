Vagrant.configure('2') do |config|
  config.vm.box      = 'precise32'
  config.vm.box_url  = 'http://files.vagrantup.com/precise32.box'
  config.vm.hostname = 'rails-dev-box'

  config.vm.synced_folder "../", "/sites", type: "nfs"
  config.vm.network :private_network, ip: "192.168.50.4"

  config.vm.provision :puppet do |puppet|
    puppet.manifests_path = 'puppet/manifests'
    puppet.module_path    = 'puppet/modules'
  end

  # Melhorar desempenho
  config.vm.provider :virtualbox do |vb|
  	vb.customize ["modifyvm", :id, "--memory", "1024"]
    vb.customize ["setextradata", :id,"VBoxInternal/Devices/ahci/0/LUN#[0]/Config/IgnoreFlush", "1"]
  end
end
