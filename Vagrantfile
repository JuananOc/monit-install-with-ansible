# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure(2) do |config|
    config.vm.box = "ubuntu/trusty64"

    config.vm.network :forwarded_port, host:  2222, guest: 22, id: "ssh"
    config.vm.network :forwarded_port, host:  8888, guest: 80, id: "nginx"

    config.vm.network :private_network, ip: "192.168.33.25"

    config.vm.define "monit" do |monit|
        monit.vm.hostname = "monit"

        monit.vm.provision "ansible" do |ansible|
          ansible.verbose = 'vvv'
          ansible.playbook = "ansible/watchdog_nginx.yml"
        end
    end
end
