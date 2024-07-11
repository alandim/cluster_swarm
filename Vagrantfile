# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|

  # Definição das configurações para cada máquina virtual
  config.vm.define "master" do |master|
    master.vm.box = "ubuntu/bionic64"
    master.vm.hostname = "master"
    master.vm.network "private_network", ip: "192.168.50.10"
    master.vm.provider "virtualbox" do |vb|
      vb.memory = "1024"
      vb.cpus = 1
    end
    master.vm.provision "docker", type: "shell" do |d|
      d.inline = "curl -fsSL https://get.docker.com | sh"
    end
    master.vm.provision "shell", inline: "docker swarm init --advertise-addr 192.168.50.10"
  end

  config.vm.define "node01" do |node01|
    node01.vm.box = "ubuntu/bionic64"
    node01.vm.hostname = "node01"
    node01.vm.network "private_network", ip: "192.168.50.11"
    node01.vm.provider "virtualbox" do |vb|
      vb.memory = "1024"
      vb.cpus = 1
    end
    node01.vm.provision "docker", type: "shell" do |d|
      d.inline = "curl -fsSL https://get.docker.com | sh"
    end
    node01.vm.provision "shell", inline: "docker swarm join --token <token_from_master> 192.168.50.10:2377"
  end

  config.vm.define "node02" do |node02|
    node02.vm.box = "ubuntu/bionic64"
    node02.vm.hostname = "node02"
    node02.vm.network "private_network", ip: "192.168.50.12"
    node02.vm.provider "virtualbox" do |vb|
      vb.memory = "1024"
      vb.cpus = 1
    end
    node02.vm.provision "docker", type: "shell" do |d|
      d.inline = "curl -fsSL https://get.docker.com | sh"
    end
    node02.vm.provision "shell", inline: "docker swarm join --token <token_from_master> 192.168.50.10:2377"
  end

  config.vm.define "node03" do |node03|
    node03.vm.box = "ubuntu/bionic64"
    node03.vm.hostname = "node03"
    node03.vm.network "private_network", ip: "192.168.50.13"
    node03.vm.provider "virtualbox" do |vb|
      vb.memory = "1024"
      vb.cpus = 1
    end
    node03.vm.provision "docker", type: "shell" do |d|
      d.inline = "curl -fsSL https://get.docker.com | sh"
    end
    node03.vm.provision "shell", inline: "docker swarm join --token <token_from_master> 192.168.50.10:2377"
  end

end
