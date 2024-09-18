Vagrant.configure("2") do |config|

  # Gregori-dockerhost (Ubuntu 23.04)
  config.vm.define "Gregori-dockerhost" do |dockerhost|
    dockerhost.vm.box = "generic/ubuntu2304"
    dockerhost.vm.network "public_network", ip: "10.10.10.130", netmask: "255.255.255.128"
    dockerhost.vm.hostname = "Gregori-dockerhost"
    dockerhost.vm.provider :virtualbox do |vb|
      vb.customize ["modifyvm", :id, "--memory", "8192"]
      vb.customize ["modifyvm", :id, "--cpus", "4"]
      vb.name = "Gregori-dockerhost"
    end
    dockerhost.vm.provision "shell", inline: <<-SHELL
      apt-get update
      apt-get install -y fish tmux mc wget tree git
      apt-get install -y docker.io docker-compose
      systemctl start docker
      systemctl enable docker
    SHELL
  end

  # Gregori-ansible (Ubuntu 23.04)
  config.vm.define "Gregori-ansible" do |ansible|
    ansible.vm.box = "generic/ubuntu2304"
    ansible.vm.network "public_network", ip: "10.10.10.131", netmask: "255.255.255.128"
    ansible.vm.hostname = "Gregori-ansible"
    ansible.vm.provider :virtualbox do |vb|
      vb.customize ["modifyvm", :id, "--memory", "2048"]
      vb.customize ["modifyvm", :id, "--cpus", "2"]
      vb.name = "Gregori-ansible"
    end
    ansible.vm.provision "shell", inline: <<-SHELL
      apt-get update
      apt-get install -y fish tmux mc wget tree git ansible sshpass yamllint ansible-lint
    SHELL
  end

  # Gregori-ubuntu (Ubuntu 23.04)
  config.vm.define "Gregori-ubuntu" do |ubuntu|
    ubuntu.vm.box = "generic/ubuntu2304"
    ubuntu.vm.network "public_network", ip: "10.10.10.132", netmask: "255.255.255.128"
    ubuntu.vm.hostname = "Gregori-ubuntu"
    ubuntu.vm.provider :virtualbox do |vb|
      vb.customize ["modifyvm", :id, "--memory", "2048"]
      vb.customize ["modifyvm", :id, "--cpus", "2"]
      vb.name = "Gregori-ubuntu"
    end
    ubuntu.vm.provision "shell", inline: <<-SHELL
      apt-get update
      apt-get install -y fish tmux mc wget tree git
    SHELL
  end

  # Gregori-centos (CentOS Stream 9)
  config.vm.define "Gregori-centos" do |centos|
    centos.vm.box = "generic/centos9s"
    centos.vm.network "public_network"
    centos.vm.network "private_network", ip: "10.10.10.133", virtualbox__intnet: "ansible_Gregori"
    centos.vm.hostname = "centos-Gregori"
    centos.vm.provider :virtualbox do |vb|
      vb.customize ["modifyvm", :id, "--memory", "2048"]
      vb.customize ["modifyvm", :id, "--cpus", "2"]
      vb.name = "centos-Gregori"
    end
    centos.vm.provision "shell", inline: <<-SHELL
      yum update -y
      yum install -y git fish tmux wget tree mc
    SHELL
  end

  # Gregori-opensuse (OpenSUSE Leap)
  config.vm.define "Gregori-opensuse" do |opensuse|
    opensuse.vm.box = "generic/opensuse15"
    opensuse.vm.network "public_network", ip: "10.10.10.134", netmask: "255.255.255.128"
    opensuse.vm.hostname = "Gregori-opensuse"
    opensuse.vm.provider :virtualbox do |vb|
      vb.customize ["modifyvm", :id, "--memory", "2048"]
      vb.customize ["modifyvm", :id, "--cpus", "2"]
      vb.name = "Gregori-opensuse"
    end
    opensuse.vm.provision "shell", inline: <<-SHELL
      zypper refresh
      zypper install -y fish tmux mc wget tree git
    SHELL
  end
end