# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.provider "virtualbox"
  # Fixes Vbox boot timeout failures
  config.vm.boot_timeout = 600
  config.vm.box_check_update = "true"
  # You can find out your network interface name with 'lshw -class network'
  config.vm.network "public_network", type: "dhcp", bridge: [
    "enp3s0",
    "wlan0",
    "eth0",
    "eth1",
    "82579LM Gigabit Network Connection",
    "82567LM-3 Gigabit Network Connection",
    "Centrino Advanced-N 6205 [Taylor Peak]"]
  # Add a bridge network interface
  config.vm.network "private_network", type: "dhcp"
  config.vm.network "private_network", type: "dhcp"

  config.vm.provider :virtualbox do |vb|
    #Fixes failed DNS errors inside Vbox
    vb.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
  end

  # Add default IIAB testing target: Debian 9 (stretch)
  config.vm.box = "debian/stretch64"
  config.vm.provision "shell", inline: "apt-get -y install git"
  config.vm.synced_folder "#{Dir.pwd}", "/opt/iiab"
  # Setting SSH Shell default change directory to '/opt/iiab'
  config.vm.provision "shell", inline: "echo 'cd /opt/iiab' >> /home/vagrant/.profile"
  # Keep this updated with the latest local_vars.yml for the current release.
  config.vm.provision "shell", inline: "wget -c -P /opt/iiab/iiab/vars/ http://download.iiab.io/6.5/rpi/local_vars.yml"
end
