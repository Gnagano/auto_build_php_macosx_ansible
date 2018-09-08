# -*- mode: ruby -*-
# vi: set ft=ruby :

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
Vagrant.configure("2") do |config|
  # The most common configuration options are documented and commented below.
  # For a complete reference, please see the online documentation at
  # https://docs.vagrantup.com.

  # Every Vagrant development environment requires a box. You can search for
  # boxes at https://vagrantcloud.com/search.
  config.vm.box = "mac"
  config.vm.network "private_network", ip: "192.168.21.10"

  config.vm.synced_folder "provision", "/Users/vagrant/provision",
    id: "provision", :nfs => true,
    # :owner => "vagrant",
    # :group => "vagrant",
    :mount_options => ["dmode=755,fmode=755"]
  #
  config.vm.provision "shell", inline: <<-SHELL
    /usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
    brew install ansible
  SHELL
  #
  # config.vm.synced_folder "." , "/vagrant", id: "vagrant_folder", :nfs => true
  #
  # config.vm.provision "ansible_local" do |ansible|
  #   ansible.playbook = "provision_local/playbook.yml"
  #   ansible.install = true
  # end
end
