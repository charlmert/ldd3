# -*- mode: ruby -*-
# vi: set ft=ruby :

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
Vagrant.configure("2") do |config|

  config.vm.box = "debian/stretch64"

  config.ssh.insert_key = true
  # config.ssh.insert_key = false
  # config.ssh.private_key_path = "/Users/charlmert/.ssh/id_rsa_vagrant"
  # config.vm.provision "file", source: "/Users/charlmert/.ssh/id_rsa_vagrant.pub", destination: "~/.ssh/authorized_keys"

  # Must specified `id: "ssh"` in order to override the default forwarded SSH port.
  config.vm.network :forwarded_port, guest: 22, host: 2229, id: "ssh"

  #config.vm.network "forwarded_port", guest: 80, host: 8080, host_ip: "127.0.0.1"

  config.vm.network "private_network", ip: "192.168.33.59"
  # config.vm.network "public_network", use_dhcp_assigned_default_route: true
  # config.vm.network "public_network", ip: "11.0.0.12"
  config.vm.synced_folder "./", "/usr/local/src/ldd3", type: 'nfs'

  #config.vm.linked_clone = true

  # Create a public network, which generally matched to bridged network.
  # Bridged networks make the machine appear as another physical device on
  # your network.
  # config.vm.network "public_network"

  # Provider-specific configuration so you can fine-tune various
  # backing providers for Vagrant. These expose provider-specific options.
  # Example for VirtualBox:
  #
  # config.vm.provider "virtualbox" do |vb|
  #   # Display the VirtualBox GUI when booting the machine
  #   vb.gui = true
  #
  #   # Customize the amount of memory on the VM:
  #   vb.memory = "1024"
  # end
  #
  # View the documentation for the provider you are using for more
  # information on available options.

  # Enable provisioning with a shell script. Additional provisioners such as
  # Puppet, Chef, Ansible, Salt, and Docker are also available. Please see the
  # documentation for more information about their specific syntax and use.
  # config.vm.provision "shell", inline: <<-SHELL
  #   apt-get update
  #   apt-get install -y apache2
  # SHELL
end
