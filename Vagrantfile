Vagrant.configure("2") do |config|

  config.vm.box = "ubuntu/bionic64"

  # require plugin https://github.com/leighmcculloch/vagrant-docker-compose
  config.vagrant.plugins = "vagrant-docker-compose"

  # install docker and docker-compose
  config.vm.provision :docker
  config.vm.provision :docker_compose
  
  config.vm.provision "shell",
    inline: "timedatectl set-timezone America/Argentina/Buenos_Aires",
    run: "always"     
    
  config.vm.provision :shell, path: "update.sh"
  config.vm.provision :shell, path: "cleanup.sh"

  config.vm.provider "virtualbox" do |vb|
    vb.customize ["modifyvm", :id, "--ioapic", "on"]
    vb.customize ["modifyvm", :id, "--memory", "2048"]
    vb.customize ["modifyvm", :id, "--cpus", "2"]
    vb.customize ["modifyvm", :id, "--name", "minikube"]
  end

end
