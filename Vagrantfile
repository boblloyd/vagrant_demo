# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
	config.vm.network "private_network",
		ip: "192.168.33.10"
		
  config.vm.synced_folder "shared_resources/", "/home/vagrant/shared_resources"
  config.vm.define "jumpbox" do |jumpbox|
    jumpbox.vm.box = "generic/debian12"
	jumpbox.vm.network "private_network", ip: "192.168.33.99"
	jumpbox.vm.provider "virtualbox" do |v|
		v.name = "vagrant_jumpbox"
		v.memory = 4096
		v.cpus = 2
	end
  end
  config.vm.define "server" do |server|
    server.vm.box = "generic/debian12"
	server.vm.network "private_network", ip: "192.168.33.100"
	server.vm.provider "virtualbox" do |v|
		v.name = "vagrant_server"
		v.memory = 4096
		v.cpus = 2
	end
  end
  
  NodeCount = 2
  (1..NodeCount).each do |i|
	config.vm.synced_folder "shared_resources/", "/home/vagrant/shared_resources"
	config.vm.define "node-#{i}" do |node|
		node.vm.box = "generic/debian12"
		node.vm.hostname = "node-#{i}"
		node.vm.network "private_network", ip: "192.168.33.10#{i}"
		node.vm.provider "virtualbox" do |v|
			v.name = "vagrant_node#{i}"
			v.memory = 4096
			v.cpus = 2
		end
	end
  end
end