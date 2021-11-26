Vagrant.configure("2") do |config|
  config.vm.provider "virtualbox" do |v|
    v.memory = 512
    v.cpus = 2
  end

  config.vm.define "web" do |apache|
    apache.vm.box = "ubuntu/trusty64"
    apache.vm.network "public_network", ip: "10.0.10.60"
    apache.vm.synced_folder "app/", "/app"
    apache.vm.provision "shell", inline: "sudo cat /app/id_rsa.pub >> /home/vagrant/.ssh/authorized_keys"
  end

  config.vm.define "banco" do |db|
    db.vm.box = "ubuntu/trusty64"
    db.vm.network "public_network", ip: "10.0.10.64"
    db.vm.synced_folder "share/", "/share"
    db.vm.provision "shell", inline: "sudo cat /share/id_rsa.pub >> /home/vagrant/.ssh/authorized_keys"
  end
end
