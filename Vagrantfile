# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  # Use Ubuntu 18.04
  config.vm.box = "ubuntu/bionic64"

  # Set up network port forwarding
  config.vm.network "forwarded_port", guest: 8001, host: 8001, host_ip: "127.0.0.1"
  config.vm.network "private_network", ip: "192.168.33.10"
  config.vm.hostname = "mnist"

  # Keep the VM as lean as possible
  config.vm.provider "virtualbox" do |vb|
    # Customize the amount of memory on the VM:
    vb.memory = "1024"
    vb.cpus = 2
    # Fixes DNS issues on some networks
    vb.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
    vb.customize ["modifyvm", :id, "--natdnsproxy1", "on"]
  end

  #  ######################################################################
  # Make sure that git and other dev utilities are available
  ######################################################################
  config.vm.provision "shell", inline: <<-SHELL
    apt-get update
    sudo dpkg --configure -a
    apt-get install -y git curl wget zip tree
    # Set up a Python 3 environment
    apt-get install -y python3-dev python3-pip python3-venv
    python3 -m venv venv
    apt-get -y autoremove
  SHELL

  ######################################################################
  # Add docker image
  ######################################################################
  config.vm.provision "docker" do |d|
    d.pull_images "ubuntu:18.04"
  end
end


