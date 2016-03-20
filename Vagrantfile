# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrant version 1.8.1

Vagrant.configure(2) do |config|

  config.vm.box = "ubuntu/trusty64"

  config.vm.network "public_network", :bridge => "en0: Wi-Fi (AirPort)"

  config.vm.provider "virtualbox" do |vb|
    vb.memory = "1024"
  end

  config.ssh.forward_x11 = true

  $mcadiz = <<EOF
  sudo su
  useradd -m -s /bin/bash mcadiz
  echo "Defaults  editor=/usr/bin/vim" >> /etc/sudoers
  echo "mcadiz  ALL=NOPASSWD: ALL" >> /etc/sudoers
  cd /home/mcadiz && mkdir .ssh
  echo "ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQCkyBxZ2rJ89Mfnt2AxnuQ001QTxNxUdvThsUZ98QgAUogNeTTrZ/y2dBA0lKzSeiupwNgweYd0egc6wiTqUQTsOCTxR6486eBgdZ4q3/MzijaWyn6eL5npkuPjw/IIlzkrGTKjAiXCKD6rVzDOVIEFEZR74334hhX0GoPPyid4eFArSwvKAWQUI9ajObNRlNragoJOSgDyLkl0vOL6fC9U5XK9LvtifwyAGNLbZ/hcvUI1+LqJckaDmWaVhPyPBAdP+ddf0mOIk0+BwYQx57EUdp90402Nmq+a2ipXjObnuP4zmdmw+lqx7Yw+mOLGoj4nWWapx49JTEt1HZbSKlO7 mcadiz@l0st" > .ssh/authorized_keys
  chown -R mcadiz:mcadiz .ssh
  chmod 600 .ssh/authorized_keys
EOF

  config.vm.provision "shell", inline: $mcadiz

  config.vm.provision "shell", run: "always" do |s|
    s.inline = "echo `ifconfig eth1 | grep 'inet addr' | awk -F ':' '{print $2}' | awk '{print $1}'` > /vagrant/ifeth1"
    s.inline = "echo `ifconfig eth1 | grep 'inet addr' | awk -F ':' '{print $2}' | awk '{print $1}'` >> /vagrant/ansible/inventory/vagrant-vm"
  end

end
