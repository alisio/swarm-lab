# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.define "machine1" do |machine1|
  machine1.vm.box = "centos/7"
  machine1.vm.hostname = 'machine1'
  # machine1.vm.box_url = "ubuntu/precise64"

  machine1.vm.network :private_network, ip: "192.168.56.101"

  machine1.vm.provider :virtualbox do |v|
    # v.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
    v.customize ["modifyvm", :id, "--memory", 512]
    v.customize ["modifyvm", :id, "--name", "machine1"]
  end
end

config.vm.define "machine2" do |machine2|
  machine2.vm.box = "centos/7"
  machine2.vm.hostname = 'machine2'
  # machine2.vm.box_url = "ubuntu/precise64"

  machine2.vm.network :private_network, ip: "192.168.56.102"

  machine2.vm.provider :virtualbox do |v|
    # v.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
    v.customize ["modifyvm", :id, "--memory", 512]
    v.customize ["modifyvm", :id, "--name", "machine2"]
  end
end

config.vm.define "machine3" do |machine3|
  machine3.vm.box = "centos/7"
  machine3.vm.hostname = 'machine3'
  # machine3.vm.box_url = "ubuntu/precise64"

  machine3.vm.network :private_network, ip: "192.168.56.103"

  machine3.vm.provider :virtualbox do |v|
    # v.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
    v.customize ["modifyvm", :id, "--memory", 512]
    v.customize ["modifyvm", :id, "--name", "machine3"]
  end
end

  config.vm.provision "shell", inline: <<-SHELL
    yum remove -y docker \
                    docker-client \
                    docker-client-latest \
                    docker-common \
                    docker-latest \
                    docker-latest-logrotate \
                    docker-logrotate \
                    docker-engine
    yum install -y yum-utils
    yum-config-manager --add-repo https://download.docker.com/linux/centos/docker-ce.repo
    yum install -y \
      docker-ce docker-ce-cli containerd.io \
      net-tools
    systemctl start docker
    systemctl enable docker
  SHELL
end
