# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|

  config.vm.box = "mac"
  config.vm.network "private_network", ip: "192.168.21.10"

  config.vm.synced_folder "provision", "/Users/vagrant/provision",
    id: "provision", :nfs => true,
    :mount_options => ["dmode=755,fmode=755"]

  config.vm.provision "shell", inline: <<-SHELL
    echo "#!/bin/sh\n" \
         "brew update\n" \
         "brew install ruby\n" \
         "sudo mv /usr/local/bin/ruby /usr/local/bin/ruby2.0.0\n" \
         "sudo ln -s /usr/local/Cellar/ruby/2.5.1/bin/ruby /usr/local/bin/ruby\n" \
         "brew install ansible\n" > /Users/vagrant/provision.sh
  SHELL
        #/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
end
