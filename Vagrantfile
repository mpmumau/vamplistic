#
# Vamplistic
#
# A Vagrant file for running a simple Apache, MySQL and PHP server.
# Type 'vagrant up' to run. See README.md for more information.
#
# File: Vagrantfile
# Author: Matthew Mumau
# Created: Aug. 27, 2017
#

Vagrant.configure("2") do |config|
    # General box configuration
    config.vm.provider "virtualbox" do |virtualbox|
      virtualbox.name = "Vamplistic.dev"
    end
    config.vm.box = "debian/jessie64"

    # Networking
    config.vm.hostname = "vamplistic.dev"
    config.vm.network "private_network", ip: "192.168.128.128"

    #Synced files
    config.vm.synced_folder ".", "/vagrant", type: "nfs"

    # Provisioner
    config.vm.provision "shell" do |s|
        s.name = "Vamplistic Shell Provisioner"
        s.keep_color = true
        s.path = "provision.sh"
        s.upload_path = "/tmp/vamplistic.sh"
    end

    config.vm.provision :shell, path: "startup.sh", run: 'always'
end
