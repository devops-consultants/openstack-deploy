# -*- mode: ruby -*-
# vi: set ft=ruby :

$script = <<SCRIPT
yum -y install epel-release
yum -y install ansible
cd playbooks
ansible-playbook -v PrepareServer.yml
SCRIPT

Vagrant.require_version ">= 1.7.0"

Vagrant.configure("2") do |config|
  config.vm.box = "boxcutter/centos73"
  config.disksize.size = '80GB'
  config.ssh.insert_key = false

  config.vm.define "openstack" do |server|
	  server.vm.hostname = 'openstack'
    server.vm.provision "shell", inline: $script

    server.vm.synced_folder ".", "/home/vagrant/playbooks", type: 'virtualbox'

    server.vm.provider "virtualbox" do |v|
        # v.gui = true
        v.memory = 8192
        v.cpus = 2
    end
  end


end
