# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.provider :virtualbox do |vb|
    #Fixes failed DNS errors inside Vbox
    vb.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
  end
  # Fixes Vbox boot timeout failures
  config.vm.boot_timeout = 600
  # Add a bridge network interface
  config.vm.network "public_network", type: "dhcp", bridge: "eth0"
  config.vm.network "public_network", type: "dhcp", bridge: "wlan0"
  config.vm.box = "debian/stretch64"
  config.vm.provision "shell", inline: "apt install git"
  # Fixes Apt hash sum mismatch error https://blog.packagecloud.io/eng/2016/03/21/apt-hash-sum-mismatch/
  config.vm.provision "shell", inline: "echo 'Acquire::CompressionTypes::Order:: \"gz\";' > /etc/apt/apt.conf.d/99compression-workaround"
  config.vm.synced_folder ".", "/opt/iiab"
  config.vm.provision "shell", inline: "wget -c -P /opt/iiab/iiab/vars/ http://download.iiab.io/6.4/rpi/local_vars.yml"
end
