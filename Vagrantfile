# -*- mode: ruby -*-
# vi: set ft=ruby :

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
Vagrant.configure(2) do |config|
  # The most common configuration options are documented and commented below.
  # For a complete reference, please see the online documentation at
  # https://docs.vagrantup.com.

  # Every Vagrant development environment requires a box. You can search for
  # boxes at https://atlas.hashicorp.com/search.
   config.vm.box = "puppetlabs/centos-7.0-64-puppet"

  # Disable automatic box update checking. If you disable this, then
  # boxes will only be checked for updates when the user runs
  # `vagrant box outdated`. This is not recommended.
  # config.vm.box_check_update = false
  

  # Create a forwarded port mapping which allows access to a specific port
  # within the machine from a port on the host machine. In the example below,
  # accessing "localhost:8080" will access port 80 on the guest machine.
 

  # Create a private network, which allows host-only access to the machine
  # using a specific IP.
   config.vm.network :private_network, ip: "10.10.10.11"
   config.vm.hostname = "docker.com"
   config.vm.network "forwarded_port", guest: 80, host: 8080

  # Create a public network, which generally matched to bridged network.
  # Bridged networks make the machine appear as another physical device on
  # your network.
  # config.vm.network "public_network"


  config.vm.synced_folder ".", "/vagrant"


   config.vm.provider "virtualbox" do |vb|
     vb.memory = "1024"
   end


  # Enable provisioning with a shell script. Additional provisioners such as
  # Puppet, Chef, Ansible, Salt, and Docker are also available. Please see the
  # documentation for more information about their specific syntax and use.
   config.vm.provision "shell", inline: <<-SHELL
     sudo yum -y update
	 
	 #Installing & Starting Docker Engine
	 sudo touch /etc/yum.repos.d/docker.repo
	 sudo echo "[dockerrepo]\nname=Docker Repository\nbaseurl=https://yum.dockerproject.org/repo/main/centos/7/\nenabled=1\ngpgcheck=1\ngpgkey=https://yum.dockerproject.org/gpg" >> /etc/yum.repos.d/docker.repo
	 sudo yum install -y docker-engine
	 sudo systemctl enable docker
	 sudo systemctl start docker 
	 
	 #Installing useful packages
	 sudo yum install -y elinks
	 
   SHELL
end
