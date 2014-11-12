# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|

  config.vbguest.auto_update = true

  config.vm.define "master" do |master|
    master.vm.box = "trusty"
    master.vm.host_name = "master"
    master.vm.network :private_network, ip: "192.168.56.102"    
    master.vm.network "public_network", :bridge => 'en0: Wi-Fi (AirPort)'
  end

  config.vm.define "func-ui-test" do |funcuitest|    
    minion.vm.box = "trusty"
    minion.vm.host_name = "func-ui-test"
    minion.vm.network :private_network, ip: "192.168.56.103"
    minion.vm.network "public_network", :bridge => 'en0: Wi-Fi (AirPort)'
    minion.vm.provision :salt do |salt|
      salt.run_highstate = true
      salt.minion_config = "./func-ui-test.conf"
      salt.minion_key = "./func-ui-test.pem"
      salt.minion_pub = "./func-ui-test.pub"
    end 
  end
  
    config.vm.define "minion" do |minion|    
    minion.vm.box = "trusty"
    minion.vm.host_name = "minion"
    minion.vm.network :private_network, ip: "192.168.56.104"
    minion.vm.network "public_network", :bridge => 'en0: Wi-Fi (AirPort)'
    minion.vm.provision :salt do |salt|
      salt.run_highstate = true
      salt.minion_config = "./minion.conf"
      salt.minion_key = "./minion.pem"
      salt.minion_pub = "./minion.pub"
    end 
  end 

end
