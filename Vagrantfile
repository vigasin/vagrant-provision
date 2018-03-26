Vagrant.configure(2) do |config|
    config.vm.box = "ubuntu/xenial64"
    config.vm.provider "virtualbox" do |v|
        v.name = "ansible-test"
        v.memory = 1024
        v.cpus = 2
    end

    config.vm.hostname = "ansible-test"
    config.vm.network :private_network, ip: "192.168.33.7"
    config.vm.provision "docker" do |d|
        d.pull_images "vigasin/provision:1.0"
        d.run "vigasin/provision:1.0",
          auto_assign_name: false,
          daemonize: false,
          restart: "no",
          args: "-e PROVISION_USER=vagrant --net host -v /home/vagrant/.ssh:/hostssh"
    end
end
