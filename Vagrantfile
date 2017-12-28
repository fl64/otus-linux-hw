Vagrant.configure("2") do |config|
  
  config.ssh.private_key_path =  ["~/.ssh/id_rsa", "~/.vagrant.d/insecure_private_key"]
  config.ssh.insert_key = false


  config.ssh.forward_agent = true

  config.vm.box_check_update = false
  config.vm.box = "centos/7" 
  config.vm.define "r0" do |r0|
    r0.vm.hostname = 'r0'
    r0.vm.network :"private_network", ip: "10.0.0.10", :name => 'vboxnet0', :adapter => 2
    r0.vm.network :"private_network", auto_config: false, virtualbox__intnet: "vlan2", :adapter => 3
    r0.vm.provision "file", source: "~/.ssh/id_rsa.pub", destination: "~/.ssh/authorized_keys"

    r0.vm.provider :virtualbox do |vb|
      vb.name = "r0"
      vb.linked_clone = true
    end

  end
  config.vm.define "r1" do |r1|
    r1.vm.hostname = 'r1'
    r1.vm.network :"private_network", ip: "10.0.0.20", :name => 'vboxnet0', :adapter => 2
    r1.vm.network :"private_network", auto_config: false, virtualbox__intnet: "vlan2", :adapter => 3
    r1.vm.network :"private_network", auto_config: false, virtualbox__intnet: "vlan4", :adapter => 4
    r1.vm.provision "shell", 
        run: "always",
        inline: "ip route delete default"
    r1.vm.provision "file", source: "~/.ssh/id_rsa.pub", destination: "~/.ssh/authorized_keys"
    r1.vm.provider :virtualbox do |vb|
      vb.name = "r1"
      vb.linked_clone = true
    end
  end
  config.vm.define "be1" do |be1|
    be1.vm.hostname = 'be1'
    be1.vm.network :"private_network", ip: "10.0.0.30", :name => 'vboxnet0', :adapter => 2
    be1.vm.network :"private_network", auto_config: false, virtualbox__intnet: "vlan4", :adapter => 3
    be1.vm.provision "shell", 
        run: "always",
        inline: "ip route delete default"
    be1.vm.provision "file", source: "~/.ssh/id_rsa.pub", destination: "~/.ssh/authorized_keys"

    be1.vm.provider :virtualbox do |vb|
      vb.name = "be1"
      vb.linked_clone = true
    end
  end
  config.vm.define "be2" do |be2|
    be2.vm.hostname = 'be2'
    be2.vm.network :"private_network", ip: "10.0.0.40", :name => 'vboxnet0', :adapter => 2
    be2.vm.network :"private_network", auto_config: false, virtualbox__intnet: "vlan4", :adapter => 3
    be2.vm.provision "shell", 
        run: "always",
        inline: "ip route delete default"
    be2.vm.provision "file", source: "~/.ssh/id_rsa.pub", destination: "~/.ssh/authorized_keys"
    be2.vm.provider :virtualbox do |vb|
      vb.name = "be2"
      vb.linked_clone = true
    end
  end
end