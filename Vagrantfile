Vagrant.configure("2") do |config|

  config.vm.define "dockerhost" do |dockerhost|
    dockerhost.vm.box = "generic/debian12"
    dockerhost.vm.network "private_network", ip: "10.10.10.2", virtualbox__intnet: "ansible_lab"
    dockerhost.vm.hostname = "tonis-dockerhost"
    dockerhost.vm.provider :virtualbox do |vb|
      vb.customize ["modifyvm", :id, "--memory", "8096"]
      vb.customize ["modifyvm", :id, "--cpus", "4"]
      vb.name = "tonis-dockerhost"
    end
    dockerhost.vm.provision "shell", inline: <<-SHELL
      apt-get update
      apt-get install -y git fish tmux mc wget
      apt-get install -y docker.io docker-compose
    SHELL
  end


  config.vm.define "ansible" do |ansible|
    ansible.vm.box = "generic/debian12"
    ansible.vm.network "private_network", ip: "10.10.10.3", virtualbox__intnet: "ansible_lab"
    ansible.vm.hostname = "tonis-ansible"
    ansible.vm.provider :virtualbox do |vb|
      vb.customize ["modifyvm", :id, "--memory", "2048"]
      vb.customize ["modifyvm", :id, "--cpus", "2"]
      vb.name = "tonis-ansible"
    end
    ansible.vm.provision "shell", inline: <<-SHELL
      apt-get update
      apt-get install -y git fish tmux mc wget
      apt-get install -y ansible tree sshpass yamllint ansible-lint
    SHELL
  end


  config.vm.define "ubuntu" do |ubuntu|
    ubuntu.vm.box = "generic/ubuntu2304"
    ubuntu.vm.network "private_network", ip: "10.10.10.4", virtualbox__intnet: "ansible_lab"
    ubuntu.vm.hostname = "tonis-ubuntu"
    ubuntu.vm.provider :virtualbox do |vb|
      vb.customize ["modifyvm", :id, "--memory", "2048"]
      vb.customize ["modifyvm", :id, "--cpus", "2"]
      vb.name = "tonis-ubuntu"
    end
    ubuntu.vm.provision "shell", inline: <<-SHELL
      apt-get update
      apt-get install -y git fish tmux mc wget
    SHELL
  end

  
  config.vm.define "centos" do |centos|
    centos.vm.box = "generic/centos9s"
    centos.vm.network "private_network", ip: "10.10.10.5", virtualbox__intnet: "ansible_lab"
    centos.vm.hostname = "tonis-centos"
    centos.vm.provider :virtualbox do |vb|
      vb.customize ["modifyvm", :id, "--memory", "2048"]
      vb.customize ["modifyvm", :id, "--cpus", "2"]
      vb.name = "tonis-centos"
    end
    centos.vm.provision "shell", inline: <<-SHELL
      yum update -y
      yum install -y git fish tmux mc wget
    SHELL
  end


  config.vm.define "opensuse" do |opensuse|
    opensuse.vm.box = "generic/opensuse42"
    opensuse.vm.network "private_network", ip: "10.10.10.6", virtualbox__intnet: "ansible_lab"
    opensuse.vm.hostname = "tonis-opensuse"
    opensuse.vm.provider :virtualbox do |vb|
      vb.customize ["modifyvm", :id, "--memory", "2048"]
      vb.customize ["modifyvm", :id, "--cpus", "2"]
      vb.name = "tonis-opensuse"
    end
    opensuse.vm.provision "shell", inline: <<-SHELL
      zypper refresh
      zypper install -y git fish tmux mc wget
    SHELL
  end
end
