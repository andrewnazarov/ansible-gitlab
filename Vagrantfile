# -*- mode: ruby -*-
# vi: set ft=ruby :

VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|

  config.vm.box = "centos/7.0"
  config.vm.box_url = "https://github.com/holms/vagrant-centos7-box/releases/download/7.1.1503.001/CentOS-7.1.1503-x86_64-netboot.box"
  config.ssh.insert_key = false
  
  config.vm.hostname = "gitlab"
  config.vm.network "private_network", ip: "192.168.33.10"
  
  config.vm.define "gitlab"

  config.vm.provider "virtualbox" do |vb|
    vb.name = "gitlab"
    vb.customize ["modifyvm", :id, "--memory", "1024"]
  end
  
  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "site.yml"
    ansible.inventory_path = "inventory"
  end
end
