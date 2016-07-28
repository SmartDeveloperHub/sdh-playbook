Vagrant.configure(2) do |config|
  config.vm.define "source" do |source|
    source.vm.box = "ubuntu/trusty64"
    source.vm.provider "virtualbox" do |vb|
      vb.cpus = "2"
      vb.memory = "2048"
    end
    # glcollector
    source.vm.network "forwarded_port", guest: 5000, host: 5000
    # harvesters public port
    source.vm.network "forwarded_port", guest: 8081, host: 8081    
    source.vm.network "forwarded_port", guest: 22, host: 2224, id: "ssh"
    source.vm.network "private_network", ip: "192.168.99.101"
  end

  config.vm.define "web" do |web|
    web.vm.box = "ubuntu/trusty64"
    web.vm.provider "virtualbox" do |vb|
      vb.memory = "2048"      
    end
    # dashboards public port
    web.vm.network "forwarded_port", guest: 80, host: 8080
    web.vm.network "forwarded_port", guest: 22, host: 2222, id: "ssh"
    web.vm.network "private_network", ip: "192.168.99.102"
  end

  config.vm.define "core" do |core|
    core.vm.box = "ubuntu/trusty64"
    core.vm.provider "virtualbox" do |vb|
      vb.memory = "2048"
      vb.cpus = "2"
    end
    # agora port
    core.vm.network "forwarded_port", guest: 9009, host: 9009
    # rabbitmq
    core.vm.network "forwarded_port", guest: 5672, host: 5672
    # metrics port
    core.vm.network "forwarded_port", guest: 9004, host: 9004
    core.vm.network "forwarded_port", guest: 22, host: 2223, id: "ssh"
    core.vm.network "private_network", ip: "192.168.99.100"
  end
end
