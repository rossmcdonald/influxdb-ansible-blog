# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure(2) do |config|
  config.vm.box = "ubuntu/trusty64"
  
  BOX_COUNT = 1
  (1..BOX_COUNT).each do |machine_id|
    config.vm.define "influx#{machine_id}" do |machine|
      machine.vm.hostname = "influx#{machine_id}"
      
      machine.vm.provider "virtualbox" do |v|
        v.memory = 512
        v.cpus = 1
      end

      if machine_id == BOX_COUNT
        machine.vm.provision "ansible" do |ansible|
          ansible.playbook = "install-influxdb.yml"
          ansible.sudo = true
        end
      end
      
    end
  end
end
