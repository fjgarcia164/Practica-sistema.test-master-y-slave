# -*- mode: ruby -*-
# vi: set ft=ruby :

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
Vagrant.configure("2") do |config|

  # Configuración del servidor maestro (tierra.sistema.test)
  config.vm.define "tierra" do |tierra|
    tierra.vm.box = "debian/bookworm64"
    tierra.vm.hostname = "tierra.sistema.test"
    tierra.vm.network "private_network", ip: "192.168.57.10";

    tierra.vm.provision "shell", inline: <<-SHELL
      # Aquí va la instalación y configuración de BIND para el servidor maestro
      sudo apt-get update
      sudo apt-get install -y bind9 bind9utils bind9-doc
      # Aquí puedes añadir más comandos para configurar el DNS maestro
    SHELL
  end

  # Configuración del servidor esclavo (venus.sistema.test)
  config.vm.define "venus" do |venus|
    venus.vm.box = "debian/bookworm64"
    venus.vm.hostname = "venus.sistema.test"
    venus.vm.network "private_network", ip: "192.168.57.11";
    venus.vm.provision "shell", inline: <<-SHELL
      # Aquí va la instalación y configuración de BIND para el servidor esclavo
      sudo apt-get update
      sudo apt-get install -y bind9 bind9utils bind9-doc
      # Aquí puedes añadir más comandos para configurar el DNS esclavo
    SHELL
  end

  # Configuración de la red para que ambos se puedan comunicar
end
