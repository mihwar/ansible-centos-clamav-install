# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  # General VM configuration
  config.vm.box = "geerlingguy/centos7"
  config.ssh.insert_key = false
#  config.vm.synced_folder ".", "/vagrant", disabled: false, create: true
  config.vm.network :forwarded_port, guest: 22, host: 1234
  config.vm.provider :virtualbox do |v|
    v.memory = 2048
    v.linked_clone = true
  end
 
  # HAProxy
#  config.vm.define "proxy" do |app|
#    app.vm.hostname = "haproxy"
#    app.vm.network :private_network, ip: "192.168.70.4"
#  end

  # Appl server
  config.vm.define "appl" do |app|
    app.vm.hostname = "host"
    app.vm.network :private_network, ip: "192.168.70.5"
  end

  # Database server
#  config.vm.defire "db" do |db|
#    db.vm.hostname = "orc-db.dev"
#    db.vm.network :private_network, ip: "192.168.60.6"
#  end

  config.vm.provision "ansible" do |ansible|
   ansible.playbook = "playbook.yml"
  end
end
