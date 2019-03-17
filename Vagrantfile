# Defines our Vagrant environment
#
# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|

  # create db node
config.vm.define "slave_new" do |master|
      master.vm.provider "virtualbox"
      master.vm.box = "centos/7"
      master.vm.hostname = "webs.mylab.local"
      master.vm.network :private_network, ip: "192.168.88.8"
	  config.vm.synced_folder ".", "/home/vagrant", type: "virtualbox"
	  master.vm.provision "shell", inline: <<-SHELL
		sudo sed -i "s/PasswordAuthentication.*/PasswordAuthentication yes/g" /etc/ssh/sshd_config
		sudo systemctl restart sshd
		sudo systemctl enable sshd
	 SHELL
     end
  end