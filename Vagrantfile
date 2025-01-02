#
# Common settings for all virtual machines
#
Vagrant.configure("2") do |config|
    config.vm.provider "virtualbox" do |vb|
      vb.memory = "4096"
      vb.cpus = 1
      vb.gui = true
      vb.customize [
        "modifyvm", :id,
        "--ioapic", "on",
        "--graphicscontroller", "vmsvga",
        "--nicpromisc2", "allow-all"
      ]
    end
  
  #
  # CentOS 8 / marutamachi
  #
    config.vm.define :marutamachi do |marutamachi|
      marutamachi.vm.box = "centos/8"
      marutamachi.vm.network "private_network", mac: "00006c000101", ip: "192.168.111.101", virtualbox__intnet: true
      marutamachi.vm.hostname = "marutamachi.example.jp"
      marutamachi.vm.provider "virtualbox" do |vb|
        vb.name = "marutamachi"
      end
      marutamachi.vm.provision "shell", inline: $remove_vmtools
      marutamachi.vm.provision "shell", inline: $common_provisioning
      marutamachi.vm.provision "shell", inline: $centos8_provisioning
    end
  
  #
  # CentOS 7 / takeyamachi
  #
    config.vm.define :takeyamachi do |takeyamachi|
      takeyamachi.vm.box = "centos/7"
      takeyamachi.vm.network "private_network", mac: "00006c000102", ip: "192.168.111.102", virtualbox__intnet: true
      takeyamachi.vm.hostname = "takeyamachi.example.jp"
      takeyamachi.vm.provider "virtualbox" do |vb|
        vb.name = "takeyamachi"
      end
      takeyamachi.vm.provision "shell", inline: $remove_vmtools_yum
      takeyamachi.vm.provision "shell", inline: $common_provisioning
      takeyamachi.vm.provision "shell", inline: $centos7_provisioning
    end
  
  #
  # Debian 10 / ebisugawa
  #
    config.vm.define :ebisugawa do |ebisugawa|
      ebisugawa.vm.box = "debian/buster64"
      ebisugawa.vm.network "private_network", mac: "00006c000103", ip: "192.168.111.103", virtualbox__intnet: true
      ebisugawa.vm.hostname = "ebisugawa.example.jp"
      ebisugawa.vm.provider "virtualbox" do |vb|
        vb.name = "ebisugawa"
      end
      ebisugawa.vm.provision "shell", inline: $common_provisioning
      ebisugawa.vm.provision "shell", inline: $set_vagrant_password
      ebisugawa.vm.provision "shell", inline: $debian_provisioning
    end

  #
  # Debian 10 / nijyo
  #
    config.vm.define :nijyo do |nijyo|
      nijyo.vm.box = "debian/buster64"
      nijyo.vm.network "private_network", mac: "00006c000104", ip: "192.168.111.104", virtualbox__intnet: true
      nijyo.vm.hostname = "nijyo.example.jp"
      nijyo.vm.provider "virtualbox" do |vb|
        vb.name = "nijyo"
      end
      nijyo.vm.provision "shell", inline: $common_provisioning
      nijyo.vm.provision "shell", inline: $set_vagrant_password
      nijyo.vm.provision "shell", inline: $debian_provisioning
    end
  
  #
  # Debian 10 / oshikoji
  #
    config.vm.define :oshikoji do |oshikoji|
      oshikoji.vm.box = "debian/buster64"
      oshikoji.vm.network "private_network", mac: "00006c000105", ip: "192.168.111.105", virtualbox__intnet: true
      oshikoji.vm.hostname = "oshikoji.example.jp"
      oshikoji.vm.provider "virtualbox" do |vb|
        vb.name = "oshikoji"
      end
      oshikoji.vm.provision "shell", inline: $common_provisioning
      oshikoji.vm.provision "shell", inline: $set_vagrant_password
      oshikoji.vm.provision "shell", inline: $debian_provisioning
    end
  
  #
  # AlmaLinux 8 / oike
  #
    config.vm.define :oike do |oike|
      oike.vm.box = "almalinux/8"
      oike.vm.network "private_network", mac: "00006c000106", ip: "192.168.111.106", virtualbox__intnet: true
      oike.vm.hostname = "oike.example.jp"
      oike.vm.provider "virtualbox" do |vb|
        vb.name = "oike"
      end
      oike.vm.provision "shell", inline: $common_provisioning
      oike.vm.provision "shell", inline: $centos8_provisioning
    end
  
  end
  
  #
  # Common provisioning for all virtual machines
  #
  $common_provisioning = <<-'SCRIPT'
  timedatectl set-timezone Asia/Tokyo
  sed -e s/^'PasswordAuthentication no'/'PasswordAuthentication yes'/ /etc/ssh/sshd_config > /tmp/sshd_config
  mv -f /tmp/sshd_config /etc/ssh/
  chmod 0600 /etc/ssh/sshd_config
  systemctl restart sshd.service
  SCRIPT
  
  #
  # Remove open-vm-tools
  #
  $remove_vmtools = <<-'SCRIPT'
  dnf -y remove open-vm-tools
  SCRIPT
  
  #
  # Remove open-vm-tools (yum command)
  #
  $remove_vmtools_yum = <<-'SCRIPT'
  yum -y remove open-vm-tools
  SCRIPT
  
  #
  # Remove open-vm-tools (apt command)
  #
  $remove_vmtools_apt = <<-'SCRIPT'
  apt -y remove open-vm-tools
  SCRIPT
  
  #
  # Set the password for the account vagrant
  #
  $set_vagrant_password = <<-'SCRIPT'
  echo 'vagrant' > pass.txt
  echo 'vagrant' >> pass.txt
  passwd vagrant < pass.txt
  SCRIPT
  
  #
  # Provisioning for CentOS8
  #
  $centos8_provisioning = <<-'SCRIPT'
  dnf -y update
  reboot
  SCRIPT
  
  #
  # Provisioning for CentOS7
  #
  $centos7_provisioning = <<-'SCRIPT'
  yum -y update
  reboot
  SCRIPT
  
  #
  # Provisioning for Ubuntu
  #
  $ubuntu_provisioning = <<-'SCRIPT'
  apt -y update
  apt -y dist-upgrade
  reboot
  SCRIPT
  
  #
  # Provisioning for Debian
  #
  $debian_provisioning = <<-'SCRIPT'
  apt -y update
  apt -y upgrade
  reboot
  SCRIPT
