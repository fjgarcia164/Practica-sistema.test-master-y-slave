# -*- mode: ruby -*-
# vi: set ft=ruby :

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
Vagrant.configure("2") do |config|

  config.vm.define "tierra" do |tierra|
    tierra.vm.box = "debian/bookworm64"
    tierra.vm.hostname = "tierra.sistema.test"
    tierra.vm.network "private_network", ip: "192.168.57.10";

    tierra.vm.provision "shell", inline: <<-SHELL
      sudo apt-get update
      sudo apt-get install -y bind9 bind9utils bind9-doc
    SHELL
  end

  config.vm.define "venus" do |venus|
    venus.vm.box = "debian/bookworm64"
    venus.vm.hostname = "venus.sistema.test"
    venus.vm.network "private_network", ip: "192.168.57.11";
    venus.vm.provision "shell", inline: <<-SHELL
      sudo apt-get update
      sudo apt-get install -y bind9 bind9utils bind9-doc
    SHELL
  end

end
