# -*- mode: ruby -*-
# vi: set ft=ruby :

# Use Vagrant.configure version 2 to configure this VM
Vagrant.configure(2) do |config|
  # The base vagrant box to use for this VM. We are going to use Ubuntu 14.04
  config.vm.box = "puphpet/ubuntu1404-x64"

  # Let's call the host something contextual
  config.vm.hostname = "tidepool-vm"

  # Port forward localhost:8080 to vm:80 (HTTP)
  config.vm.network "forwarded_port", guest: 80, host: 8080
  # Port forward localhost:8443 to vm:443 (HTTPS)
  config.vm.network "forwarded_port", guest: 443, host: 8443

  # Create a private network, which allows host-only access to the machine
  # using a specific IP.
  # config.vm.network "private_network", ip: "192.168.33.10"

  # Share the tidepool parent directory and mount it in the VMs file system
  config.vm.synced_folder "../", "/tidepool"

  # Set the memory available and number of cpus when using VirtualBox
  config.vm.provider "virtualbox" do |vb|
    vb.memory = 2048
    vb.cpus = 2
  end
  
  # Set the memory available when using Paralells
  config.vm.provider "parallels" do |v|
    v.memory = "2048"
  end

  # Provision the VM using setup_vagrant.sh - this will install all the 
  # required dependencies
  config.vm.provision :shell, :path => "setup_vagrant.sh"
end
