# -*- mode: ruby -*-
# vi: set ft=ruby :

base_box = "bento/ubuntu-16.04"

Vagrant.configure(2) do |config|

  config.vm.define "master", primary: true do |n|
    n.vm.box = base_box
    n.vm.network "private_network", ip: "192.168.55.10"
    n.vm.hostname = "master"

    # consul
    n.vm.network "forwarded_port", guest: 8500, host: 8500
    # mongo
    n.vm.network "forwarded_port", guest: 27017, host: 27017
    # redis
    n.vm.network "forwarded_port", guest: 6379, host: 6379
    # nginx
    n.vm.network "forwarded_port", guest: 80, host: 8080
  end

  config.vm.define "db1" do |n|
    n.vm.box = base_box
    n.vm.network "private_network", ip: "192.168.55.13"
    n.vm.hostname = "db1"
  end

  config.vm.define "node1" do |n|
    n.vm.box = base_box
    n.vm.network "private_network", ip: "192.168.55.11"
    n.vm.hostname = "node1"
  end

  config.vm.define "node2" do |n|
    n.vm.box = base_box
    n.vm.network "private_network", ip: "192.168.55.12"
    n.vm.hostname = "node2"
  end



end
