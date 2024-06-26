# -*- mode: ruby -*-
# vi: set ft=ruby ts=2 sw=2 tw=0 et :

role = File.basename(File.expand_path(File.dirname(__FILE__)))

boxes = [
  {
    :name => "ubuntu-1604",
    :box => "bento/ubuntu-16.04",
    :ip => '10.0.0.3',
    :cpu => "50",
    :ram => "256"
  },
  {
    :name => "ubuntu-1804",
    :box => "bento/ubuntu-18.04",
    :ip => '10.0.0.4',
    :cpu => "50",
    :ram => "384"
  },
  {
    :name => "ubuntu-2004",
    :box => "bento/ubuntu-20.04",
    :ip => '10.0.0.5',
    :cpu => "50",
    :ram => "384"
  },
  {
    :name => "ubuntu-2204",
    :box => "bento/ubuntu-22.04",
    :ip => '10.0.0.6',
    :cpu => "50",
    :ram => "384"
  },  
  {
    :name => "debian-8",
    :box => "bento/debian-8",
    :ip => '10.0.1.3',
    :cpu => "50",
    :ram => "256"
  },
  {
    :name => "debian-9",
    :box => "bento/debian-9",
    :ip => '10.0.1.4',
    :cpu => "50",
    :ram => "256"
  },
  {
    :name => "debian-10",
    :box => "bento/debian-10",
    :ip => '10.0.1.5',
    :cpu => "50",
    :ram => "256"
  },
  {
    :name => "debian-11",
    :box => "bento/debian-11",
    :ip => '10.0.1.6',
    :cpu => "50",
    :ram => "256"
  },
  {
    :name => "debian-12",
    :box => "bento/debian-12",
    :ip => '10.0.1.7',
    :cpu => "50",
    :ram => "256"
  },
  {
    :name => "amazonlinux-2023",
    :box => "bento/amazonlinux-2023",
    :ip => '10.0.2.3',
    :cpu => "50",
    :ram => "256"
  },
]

Vagrant.configure("2") do |config|
  boxes.each do |box|
    config.vm.define box[:name] do |vms|
      vms.vm.box = box[:box]
      vms.vm.hostname = "ansible-#{role}-#{box[:name]}"

      vms.vm.provider "virtualbox" do |v|
        v.customize ["modifyvm", :id, "--cpuexecutioncap", box[:cpu]]
        v.customize ["modifyvm", :id, "--memory", box[:ram]]
      end

      vms.vm.network :private_network, ip: box[:ip]

      vms.vm.provision :ansible do |ansible|
        ansible.playbook = "tests/vagrant.yml"
        ansible.verbose = "vv"
      end
    end
  end
end
