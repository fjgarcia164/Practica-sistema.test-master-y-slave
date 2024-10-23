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
    tierra.vm.network "private_network", ip: "192.168.57.103";

    tierra.vm.provision "shell", inline: <<-SHELL
      sudo apt-get update
      sudo apt-get install -y bind9 bind9utils bind9-doc
      cp /vagrant/tierraConf/named.conf.local /etc/bind/named.conf.local
      cp /vagrant/tierraConf/named.conf.options /etc/bind/named.conf.options
      cp /vagrant/tierraConf/57.168.192.rev /etc/bind/57.168.192.rev
      cp /vagrant/tierraConf/sistema.test.zone /etc/bind/sistema.test.zone
    SHELL
  end

  config.vm.define "venus" do |venus|
    venus.vm.box = "debian/bookworm64"
    venus.vm.hostname = "venus.sistema.test"
    venus.vm.network "private_network", ip: "192.168.57.102";
    venus.vm.provision "shell", inline: <<-SHELL
      sudo apt-get update
      sudo apt-get install -y bind9 bind9utils bind9-doc
      cp /vagrant/venusConf/named.conf.local /etc/bind/named.conf.local
      cp /vagrant/venusConf/named.conf.options /etc/bind/named.conf.options
    SHELL
  end

end
