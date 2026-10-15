# -*- mode: ruby -*-
# vi: set ft=ruby :

$install_deps = <<-'SHELL'
  apt-get install -y openjdk-17-jdk
SHELL

Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/jammy64"
  config.vm.network "private_network", ip: "192.168.100.100"
  config.vm.provider "virtualbox" do |vb|
    vb.cpus = 2
    vb.memory = 4096
  end
  config.vm.provision "shell", inline: install_deps

  config.trigger.after :up do |trigger|
  trigger.name = "Start Java"
  trigger.run = {
  inline: "cd /vagrant && chmod +x gradlew && nohup ./gradlew bootRun > /home/vagrant/app.log 2>&1 &"
}

end
