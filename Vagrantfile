# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.provider :virtualbox do |vb|
  vb.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
  end
  config.vm.boot_timeout = 600
  config.vm.box = "ubuntu/xenial64"
  config.vm.provision "shell", inline: "apt install git"
  config.vm.provision "shell", inline: "echo 'Acquire::CompressionTypes::Order:: \"gz\";' > /etc/apt/apt.conf.d/99compression-workaround"
  config.vm.synced_folder ".", "/opt/iiab"
  config.vm.provision "shell", inline: "wget -c -P /opt/iiab/iiab/vars/ http://download.iiab.io/6.4/rpi/local_vars.yml"
end
