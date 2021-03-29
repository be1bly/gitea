# -*- mode: ruby -*-
# vi: set ft=ruby : 

Vagrant.configure(2) do |config|
  config.vm.box = "centos/7"
  config.ssh.insert_key = false
  config.vbguest.auto_update = false
  
  config.vm.provider "virtualbox" do |v|
    v.name = "gitea"
    v.memory = 1024
    v.cpus = 2
  end
  
  config.vm.define "gitea" do |gitea|
    gitea.vm.hostname = "gitea"
    gitea.vm.network :private_network, ip: "192.168.10.2"
  end  

  config.vm.provision "ansible" do |ansible|
    ansible.inventory_path = "inventory/hosts"  
    ansible.extra_vars = {
      ansible_ssh_user: 'vagrant',
      ansible_ssh_private_key_file: "~/.vagrant.d/insecure_private_key"
    }
    ansible.playbook = "playbook.yml"
    ansible.become = true
  end
  
end