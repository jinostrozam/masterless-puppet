# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|

  config.vm.define "demo" do |vm1|

    vm1.vm.box              = "generic/ubuntu1604"
      vm1.vm.hostname         = "demo"
      vm1.vm.box_check_update = true
  
      vm1.vm.network :private_network,
                      ip: '192.168.10.10',
                      libvirt_netmask: '255.255.255.0',
                      libvirt__network_name: 'puppet-lab',
                      autostart: true,
                      ## libvirt__domain_name: 'example.local',
                      libvirt__forward_mode: 'route',
                      libvirt__dhcp_enabled: false  
  
      vm1.vm.provision "shell", path: "scripts/vagrant_provision.sh"

      vm1.vm.synced_folder ".", "/etc/puppetlabs/code/environments/production"
    
  end
  
    config.vm.define "web01" do |vm2|

    vm2.vm.box              = "generic/ubuntu1604"
      vm2.vm.hostname         = "web01"
      vm2.vm.box_check_update = true
  
      vm2.vm.network :private_network,
                      ip: '192.168.10.20',
                      libvirt_netmask: '255.255.255.0',
                      libvirt__network_name: 'puppet-lab',
                      autostart: true,
                      ## libvirt__domain_name: 'example.local',
                      libvirt__forward_mode: 'route',
                      libvirt__dhcp_enabled: false  
  
      vm2.vm.provision "shell", :inline => <<-SHELL      
        sudo /usr/sbin/adduser --disabled-password --shell /bin/bash --gecos "User" puppet
        sudo mkdir -p /home/puppet/.ssh/
        sudo touch /home/puppet/.ssh/authorized_keys
        sudo echo "ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQDbDPM12GUdwKTA5t6/wNZ+kzDAh+qVK9p4GvS+7NNNMNjvyw+T03FXUtFqNSKVJeKGL9mox3AgblwzJYHhmEsYYrDavVgAvP3lGZeFdTA5drjqMB9q9TDqfS+g+eVjnPpjS2ehWPpsZAwVGbGxF7x86MMjBkUkGEbPWkI4fG76CawBM4ydSS/cf60eoRAdTe0tpHfJBOXbDegoTGuWAsnv+FGiRg/OxpSR9/QP35loRwVD3duMl7tbyvLx8U1tK9aWM6KbyTHD2QEjls8veBttXx4GttAhQgsbRBfidsAch5x6/aHatjRCE+jVZ86Tl/02JqG8lauAg2ppJgVyblVh puppet" | sudo tee -a /home/puppet/.ssh/authorized_keys
        sudo touch /etc/sudoers.d/10_puppet
        sudo echo "puppet ALL=(ALL) NOPASSWD: ALL" | sudo tee -a /etc/sudoers.d/10_puppet

      SHELL
       
  end
  
  config.vm.define "web02" do |vm3|

    vm3.vm.box              = "generic/ubuntu1604"
      vm3.vm.hostname         = "web02"
      vm3.vm.box_check_update = true
  
      vm3.vm.network :private_network,
                      ip: '192.168.10.30',
                      libvirt_netmask: '255.255.255.0',
                      libvirt__network_name: 'puppet-lab',
                      autostart: true,
                      ## libvirt__domain_name: 'example.local',
                      libvirt__forward_mode: 'route',
                      libvirt__dhcp_enabled: false  
  
      vm3.vm.provision "shell", :inline => <<-SHELL      
        sudo /usr/sbin/adduser --disabled-password --shell /bin/bash --gecos "User" puppet
        sudo mkdir -p /home/puppet/.ssh/
        sudo touch /home/puppet/.ssh/authorized_keys
        sudo echo "ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQDbDPM12GUdwKTA5t6/wNZ+kzDAh+qVK9p4GvS+7NNNMNjvyw+T03FXUtFqNSKVJeKGL9mox3AgblwzJYHhmEsYYrDavVgAvP3lGZeFdTA5drjqMB9q9TDqfS+g+eVjnPpjS2ehWPpsZAwVGbGxF7x86MMjBkUkGEbPWkI4fG76CawBM4ydSS/cf60eoRAdTe0tpHfJBOXbDegoTGuWAsnv+FGiRg/OxpSR9/QP35loRwVD3duMl7tbyvLx8U1tK9aWM6KbyTHD2QEjls8veBttXx4GttAhQgsbRBfidsAch5x6/aHatjRCE+jVZ86Tl/02JqG8lauAg2ppJgVyblVh puppet" | sudo tee -a /home/puppet/.ssh/authorized_keys
        sudo touch /etc/sudoers.d/10_puppet
        sudo echo "puppet ALL=(ALL) NOPASSWD: ALL" | sudo tee -a /etc/sudoers.d/10_puppet

      SHELL
       
  end

end
