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
  
  ####config.vm.synced_folder ".", "/etc/puppetlabs/code/environments/production"


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
  
    ### vm2.vm.provision "shell", path: "scripts/vagrant_provision.sh"

      vm2.vm.provision "shell", :inline => <<-SHELL      
        sudo /usr/sbin/adduser --disabled-password --shell /bin/bash --gecos "User" carlos
        sudo mkdir -p /home/carlos/.ssh/
        sudo touch /home/carlos/.ssh/authorized_keys
        sudo echo "ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQDT0IE26dvjtlPLXOwP14OmI4fMnfawJgi/O19xFRGJNoIy0nmtj35bi0qa66Xqvnbs2NqipSB/fwbt2dDt4CIJKNljNzvZZz+KCNoG6YxrZv1KvY8EoQugAGUZDTrab70sk+qhLx1MLScCVr2PakuCyJmxqEbapnhoa3Z/vPiXlAyVL1R1ncAFVsx2eodH+8Mn2Uko5nWaIPryW285tx8NkFbzxiaO8RpFkjJucVb/Ap32pVRfQhLi3T9TCWsFWKqww8vEVmbyxh6UAVc86VnTW0djiY8b8sbv+ObFBsrM4T4KHuIkFFN8+iwxGFc5JCGDigIpYsgMVHX/DcuZ8gJV carlos@ubuntu1604.localdomain" | sudo tee -a /home/carlos/.ssh/authorized_keys
      SHELL

    ### vm2.vm.synced_folder ".", "/etc/puppetlabs/code/environments/production"
    
  end

end
