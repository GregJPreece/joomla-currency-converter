# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrant configuration for Joomla Currency Converter
# Author: Greg J Preece
# Creation Date: 2019-01-10

Vagrant.configure("2") do |config|

  config.vm.box = "joomlatools/box"
  config.vm.hostname = "joomlatools"

  # VirtualBox configuration:
  config.vm.provider "virtualbox" do |vb|
    vb.name = "joomlatools"

    # Don't display the VM's output - run headless
    vb.gui = false

    # Memory and CPU:
    vb.cpus = 2
    vb.memory = "1024"
  end

end
