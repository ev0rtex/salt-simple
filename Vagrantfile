# -*- mode: ruby -*-
# vi: set ft=ruby :

VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.box = "ubuntu/trusty64"

  config.vm.provider :virtualbox do |vm|
    vm.gui = false
    vm.customize(["modifyvm", :id, "--rtcuseutc", "on"])
  end

  #
  # Salt Master
  config.vm.define "master" do |master|
    master.vm.hostname = "salt-master"
    master.vm.network :private_network, ip: "192.168.33.10"
    master.vm.synced_folder "provision/salt", "/srv/salt"

    master.vm.provision :salt do |salt|
      salt.install_master = true
      salt.no_minion = true
      salt.install_type = "stable"
      salt.always_install = false
      salt.colorize = true
    end
  end

  #
  # Salt Minion - app
  config.vm.define "app" do |app|
    app.vm.hostname = "minion-app"
    app.vm.network :private_network, ip: "192.168.33.21"

    app.vm.provision :shell, inline: 'echo "192.168.33.10 salt" >> /etc/hosts'
    app.vm.provision :salt do |salt|
      salt.install_type = "stable"
      salt.always_install = false
      salt.colorize = true
    end
  end

  #
  # Salt Minion - db
  config.vm.define "db" do |db|
    db.vm.hostname = "minion-db"
    db.vm.network :private_network, ip: "192.168.33.22"

    db.vm.provision :shell, inline: 'echo "192.168.33.10 salt" >> /etc/hosts'
    db.vm.provision :salt do |salt|
      salt.install_type = "stable"
      salt.always_install = false
      salt.colorize = true
    end
  end
end
