# -*- mode: ruby -*-
# vim: set ft=ruby :
Virtual = ENV['Virtual']
#ENV["LC_ALL"] = "en_US.UTF-8"
disk = './lesson6/lesson6.vdi'

Vagrant.configure(2) do |config|
	config.vm.box_version = "1804.02"
	config.vm.box="centos/7"
	config.vm.hostname = "lesson6"
	config.vm.network "private_network", ip: "192.168.11.150"
	config.vm.define "lesson6"
	config.vm.provider "virtualbox" do |vb|
		vb.gui=false
		vb.memory = 2048
		vb.cpus = 2
		vb.customize ['createhd', '--filename', disk, '--size', 1 * 1024]
		vb.customize ["storagectl", :id, "--name", "SATA", "--add", "sata" ]
		vb.customize ['storageattach', :id, '--storagectl', 'SATA', '--port', 1, '--device', 0, '--type', 'hdd', '--medium', disk]
               end
	config.vm.synced_folder ".", "/vagrant", type: "virtualbox"
end
