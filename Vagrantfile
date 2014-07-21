# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  
	config.vm.define "server1" do |server1|
  	server1.vm.box = "centos65"
    server1.vm.box_url = "http://www.lyricalsoftware.com/downloads/centos65.box"
		server1.vm.synced_folder	"./", "/vagrant", disabled: true
		server1.vm.synced_folder	"./server1", "/vagrant"
		server1.vm.network :private_network, ip: "192.168.122.50"
    server1.vm.network "forwarded_port", guest: 80, host: 8080
    server1.vm.provider "virtualbox" do |v|
      v.memory = 1024
    end
    server1.vm.provision "ansible" do |ansible|
      ansible.playbook = "ansible/rt.yml"
      ansible.verbose = "v"
    end
	end

end
